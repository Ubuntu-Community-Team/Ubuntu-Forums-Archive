---
title: "Printer STAR SP700(SP712) USB - Memory Switching"
date: 2015-10-06
forum: Ubuntu/Debian BASED
---

### Post by mahendra3 on 2015-10-06
Need help, printer STAR SP700(SP712) USB interface, driver installed successfully, but when try to print document was very slow.
I'm running on ZORIN OS 10 32bit.
I've read the manual, that is issue if using USB interface, slow print speed, and must run a script to do a memory switching (I don't really understand about memory switching in printer).
But this is the file, setup_for_linux.sh

#!/bin/sh
#
# Memory Swtich Setting Script for TSP650/TSP700II
#
# How to use:
#
# 1) Set TSP650, TSP700II as a Default printer
# 2) Copy this script (setup_for_linux.sh) and linux.dat into home folder.
# 3) Execute Termnal, then input "./setup_for_linux.sh" and return Enter key.
# 4) After execution, printer will print self test.
#    Please verify print result of <C> line in "-- Memory Switch --" part.
#    3rd digit of the <C> line should be set to "1".
#
#    Sample: 
#        <C> 0010000000000000 0200
#
lpr -o raw linux.dat
#
#
# Note:
# If you can not set SP650/TSP700II as a default printer, refer to the following
# procedure.
#
# 1) Using following command, printer queue lists, print queue names,
#    and default printer will be displayed.
#
#    $ lpstat -p -d
#
#    dispaly example:
#       star-no-power-mac-g4:~ star$ lpstat -p -d       
#       printer TSP651__STR_T_001_ is idle.  enabled since Jan 01 00:00
#       printer TSP743II__STR_T_001_ is idle.  enabled since Jan 01 00:00
#       system default destination: TSP743II__STR_T_001_
#
#    "TSP651__STR_T_001_" and "TSP743II_STR_T_001_" are printer queue name.
#
# 2) Use following commands to set the selected printer.
#    Input printer queue names into "Printer-queue name" according to "$ lpstat -p -d command".
#
#    $ lpr -o raw linux.dat -P "Printer-queue name"
#
#    Example
#       star-no-power-mac-g4:~ star$ lpr -o raw linux.dat -P TSP651__STR_T_001_
#
# 2008/03/27 Star Micronics co.,ltd.

 Please find attached, my test print result (before and after running script - nothing changed and no <C> line)

I already try run the script, but nothing changed, the print speed still slow...
Really need advice, just bought this printer a week ago, and have no solution for this..

Thanks in advance.

---

### Post by slickymaster on 2015-10-06
*Moved to the ***Ubuntu/Debian BASED*** sub-forum*

---

