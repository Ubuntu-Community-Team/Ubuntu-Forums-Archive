---
title: "Get Canon Printer to scan with DD, kern 19, current"
date: 2019-02-10
forum: Ubuntu Development Version
---

### Post by Kris_M on 2019-02-10
I just put up DD a few days ago and though I could get my Canon Pixma TS6020 All-in-One to print, it couldn't find the scanner(this was no prob with 18.10 and previous).  These instructions are very close to what I did to get it to work: In it I give you the link I found long ago using the European drivers which also suggests some added libraries which are needed. I repeated those in the instructions.

>                          [FONT=Liberation Serif][SIZE=3]**printer installation ( I have a Canon TS6020)**[/SIZE][/FONT]
  [FONT=Liberation Serif][SIZE=3]I hear this will work for just about any Canon printer.[/SIZE][/FONT]
  [FONT=Liberation Serif][SIZE=3]Turn off and unplug USB cable on printer. <--------[/SIZE][/FONT]
[FONT=Liberation Serif][SIZE=3]TS6020[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3][https://tutorialforlinux.com/2018/11/20/how-to-install-canon-pixma-ts6010ts6020-driver-on-ubuntu-gnulinux/2/](https://tutorialforlinux.com/2018/11/20/how-to-install-canon-pixma-ts6010ts6020-driver-on-ubuntu-gnulinux/2/)[/SIZE][/FONT]
  [FONT=Liberation Serif][SIZE=3]sudo apt update[/SIZE][/FONT]
  [FONT=Liberation Serif][SIZE=3]sudo apt install libxml2 libglade2-0 libpng3 libtiff5 &#8211; couldn&#8217;t locate 3[/SIZE][/FONT]
  [FONT=Liberation Serif][SIZE=3]sudo apt install libgtk2.0-0[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]TS6040 [/SIZE][/FONT] 
 [FONT=Liberation Serif][SIZE=3]download 2 debs&#8230; (one for printer, one for scanner built in to printer)(these can be found on European site and some US sites)[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]Extract 2 debs to **/tmp**[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]In /tmp, in printer deb, open in terminal and sudo ./install.sh[/SIZE][/FONT]
[FONT=Liberation Serif][SIZE=3]It will ask you to connect printer and turn it on and press enter on computer. <-------[/SIZE][/FONT]
[FONT=Liberation Serif][SIZE=3]After it installs, you can print.[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]Turn off printer and unplug USB. <----------[/SIZE][/FONT]
[FONT=Liberation Serif][SIZE=3]In /tmp, in scan deb, [/SIZE][/FONT][FONT=Liberation Serif][SIZE=3][FONT=Liberation Serif][SIZE=3]open in terminal and [/SIZE][/FONT]sudo ./install.sh[/SIZE][/FONT]
[FONT=Liberation Serif][SIZE=3]It will install scangearmp2.[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]In terminal, type scangearmp2 &#8211; it will start scanning for a scanner &#8211; immediately plug in printer USB and turn printer on, tap scan in touchscreen, choose scan to computer, NOW computer will recognize it. Now you can scan stuff.[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]To create an icon on desktop, find scangearmp2 in /usr/bin , copy it, choose desktop, choose select.[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]Not sure these instrs are complete, but close.[/SIZE][/FONT]
  

---

