---
title: "Ubuntu CE 3.3 install bug fixes"
date: 2007-12-16
forum: Ubuntu Christian Edition
---

### Post by ohneclue on 2007-12-16
I downloaded version 3.3 Ubuntu CE and found that the e-sword files could not be installed with the scripts in the CE ISO file.  I believe I have identified the problem and have a found a work-around.

The following information may help those of you who know your way around Linux.   The installation scripts hide the details and all the error messages, so it is not easy to tell why Ubuntu CE won't install the e-sword packages.

The e-sword site is not permitting files to be downloaded directly via wget in the installation shell scripts.  Perhaps this worked in the past, but does not today.

Here is an example.  The main e-sword program file should download OK with the command "wget http://www.e-sword.net/files/setup785.exe".  However, the e-sword redirects the request, via an http header "Location" command, to download "http://www.e-sword.net/downloads.html" instead.  This is OK if you are using a browser as you can click on the download button and get the real file.  However, with wget and a script all you get is the "downloads.htlm" file which is NOT the program file you wanted.

The work-around is to fool the e-sword site into thinking the wget command is loading the program file from the "downloads.html" page.  If you change the wget command in the installation script to "wget --referer=http://www.e-sword.net/downloads.html http://www.e-sword.net/files/setup785.exe" it works.

The same problem exists in ALL the installation scripts for bibles, etc.  For instance bibles need "--referer=http://www.e-sword.net/bibles.html" to correctly download any of the bible files.

The e-sword is a fine product and I am glad to have a way to run it on Linux.  Thanks for all the hard work on Ubuntu CE and i am looking forward to future releases.

---

### Post by tlie on 2008-02-09
thanks to you ohneclue for the workaround.

FYI, in case you'd like to fix all scripts using Linux command in the terminal

if you go to this folder /usr/local/apps/esword4linux/esword4linux_module_manager/ and type the following, it will fix all the 74 install shell scripts:
  sed -i -e 's/http:\/\/www\.e-sword/--referer=http:\/\/www\.e-sword.net\/downloads.html http:\/\/www\.e-sword/' */*/*

tlie

---

