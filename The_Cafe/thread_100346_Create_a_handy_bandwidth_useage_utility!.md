---
title: "Create a handy bandwidth useage utility!"
date: 2005-12-07
forum: The Cafe
---

### Post by robert_pectol on 2005-12-07
Ever wanted to see just how much network bandwidth you've consumed since bootup?  Yeah, there are apps out there to be downloaded, which can give you this info but why not create your own?  Your system already has the tools and info to do it!  Plus, it's quite simple!  Here's how I did it:
 

1. Create a text file and paste the following, *EXACTLY* as it is shown below, into it:

```

#!/bin/bash
iface=`/sbin/ifconfig | egrep -v '^lo' | cut -d ' ' -f1 | awk NF | head -n 1 | sed 's/^[ \t]*//;s/[ \t]*$//'`
results=`/sbin/ifconfig $iface | grep 'RX bytes' | awk '{$1=$1;print}'`
/usr/bin/zenity  --title "Bandwidth Useage" --info --text="$results" & &> /dev/null
exit

```

2. Save it as "bandwidth.sh" and make it executable (ex: chmod 755 /path/to/bandwidth.sh").

3. Right-click on your taskbar and select, Add to Panel --> Custom Application Launcher.  For the, "Name:" and, "Generic Name:" put," Bandwidth Useage."  For, "Comment:" put, "Total network bandwidth used" and for the, "Command:" put, "/path/to/bandwidth.sh" making sure you leave the, "Type:" set to, "Application."  You may select whatever icon you like. When you're finished, close that window and you should now have a little applet on your taskbar, which when clicked, pops up a nice little window displaying your total network bandwidth useage.  Handy!  ;) 


A couple of notes...
First, obviously the script assumes a graphical environment and relies on Zenity to create the pop-up information window.  Zenity is included by default for Gnome in Ubuntu.  For KDE, you may want to use kdialog and adjust the script accordingly.

Second, the script will display the results for the first active network interface it finds (excluding local loopback).  If you have more than 1 network interface, you'll only get results for the first one detected.

---

### Post by angrylittleman on 2005-12-07
thanks!  Worked like a champ.  Love your site as well!  I bookmarked it as I would like to try your firewall and ICS scripts when finals are over and I play around with my network some more!  Thanks again!

alm

---

### Post by robert_pectol on 2005-12-07
Thanks for the kind words!  :)

---

### Post by jeremy on 2005-12-07
if you use kde you can install knemo from the repos, it does this.

---

### Post by Sanne on 2005-12-07
Thanks Robert, this is a nice script and very useful.

Sanne

---

### Post by robert_pectol on 2005-12-08
You're welcome!  And for those who have multiple network interfaces and would like to specify the interface for which to see bandwidth useage, you can replace the long line in the script that begins with,"iface=", with the following:

```

iface=ethx

```

...where the, "x" is the interface number (such as 0, 1, 2, etc.).  iface may also be a wireless interface such as wlan0, wlan1, ra0, etc.

Enjoy!

---

### Post by robert_pectol on 2006-07-28
A new and improved version of the script is available!  It now has better formatting and also gives system uptime!  Get it here:
[http://rob.pectol.com/myscripts/bandwidth.sh.txt](http://rob.pectol.com/myscripts/bandwidth.sh.txt)

---

