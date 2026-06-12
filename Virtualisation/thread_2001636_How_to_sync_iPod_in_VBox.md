---
title: "How to sync iPod in VBox??"
date: 2012-06-11
forum: Virtualisation
---

### Post by cyberphrog on 2012-06-11
I'm having difficulty getting an XP Vbox to recognize an iPod when I plug it onto the usb cable. The device list doesn't capture the iPod when I plug it in and I haven't found a way yet.  I'm sure I'm missing something obvious, but too much of a novice to know.  If there's a tutorial available, I could use the help (I don't use VBox very much..).

---

### Post by thomasw_lrd on 2012-06-11
There are a couple of different things.  Here is what works for me.

Open up the vbox control panel, and click on the settings for your virtual machine.  Click on the usb tab.

Clcik on usb with the green plus button.  (The text box at the bottom says Adds a new USB fitler with all fields set .....host PC.)  

Add the ipod to the usb filters.  The checkbox next to it should be automatically checked.  If you always want the ipod to be in the vm when it's open, leave the box marked, otherwise unmark it.

---

