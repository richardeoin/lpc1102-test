all: Parts.md schematic board

Parts.md: parts
	ruby ./partslist/parts.rb

schematic: lpc1102_test.sch.pdf lpc1102_test.sch.png
board: lpc1102_test.brd.pdf lpc1102_test.brd.png

.PHONY: clean
clean:
	rm Parts.md
	rm lpc1102_test.sch.pdf
	rm lpc1102_test.sch.png
	rm lpc1102_test.brd.pdf
	rm lpc1102_test.brd.png

#
# PNG from .sch
#
%.sch.png: %.sch
	rm -f $@
	eagle -C "export image $@ 300; display all; quit" $<
#
# PDF from .sch
# 1 page lanscape
#
%.sch.pdf: %.sch
	rm -f $@
	eagle -C "print -1 landscape file $@; quit" $<
#
# PNG from .brd
# Ratsnest, maximum dpi
#
%.brd.png: %.brd
	rm -f $@
	eagle -C "ratsnest; export image $@ 1800; display all; quit" $<
#
# PDF from .brd
# -1 limits to one page
#
%.brd.pdf: %.brd
	rm -f $@
	eagle -C "ratsnest; print 100 -1 file $@; quit" $<
