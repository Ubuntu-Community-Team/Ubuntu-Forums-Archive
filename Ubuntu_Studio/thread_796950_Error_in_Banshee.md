---
title: "Error in Banshee"
date: 2008-05-16
forum: Ubuntu Studio
---

### Post by Gatita78 on 2008-05-16
Hi,
I just installed Banshee and Hipod but in both programs I got and error with DBus.

I got the following error in Banshee:

DBus is not available
Your environment is not properly setup to use DBus.Please fix your or run Banshee through dbus-launch. Failure to do so may cause problems at the later time in Banshee during this instance.
Unable to open the session message bus.

I installed Banshee using adept installer.

Somebody Help me!!

---

### Post by fazavon on 2008-05-16
apt-get install ubuntu-restricted 

I think that is the one.. 

if that does not help DBus is typical your sound..

Does your sound work in other places I.E. when browsing the net, when you turn on the machine, when you log in?

---

### Post by Gatita78 on 2008-05-16
I tried to run the command apt-get install ubuntu-restricted  but I got the following message:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntu-restricted

and I don't have problems with my sound.

---

### Post by Stochastic on 2008-05-17
Yeah, Ubuntu-Restricted is a repository, not a package; you can't install ubuntu-restricted, you can only enable it (add that particular repository to your list of software sources).  I don't really understand what fazavon was attempting to get you to do.

If you're receiving d-bus errors then there is probably some major issue with your machine.  Try running ```
strace -o bansheeLog.txt banshee
``` and list the errors you see.

Also, you may want to post this in the Multimedia & Video forum rather than the Multimedia Production forum as Banshee is a playback device.  I've never heard of Hipod (and google results didn't offer many software results either) so I don't know what to make of that nugget.

---

### Post by Gatita78 on 2008-05-17
Hi,
I ran the command strace -o bansheeLog.txt banshee

I got the output bansheeLog.txt, but the file is big I am not what to do with it, but I can post the console output:
-------------------------------------------------------------------------
[FONT="Courier New"][SIZE="3"][SIZE="1"]userl@USER-PC:~$ strace -o bansheeLog.txt banshee
Warning: [5/17/2008 2:24:09 PM] (DBus is not available) - Your environment is not properly set up to use DBus. Please fix your environment or run Banshee through dbus-launch. Failure to do so may cause problems at a later time in Banshee during this instance.

Unable to open the session message bus.
System.Exception: Unable to open the session message bus. ---> System.ArgumentNullException: Argument cannot be null.
Parameter name: address
  at NDesk.DBus.Bus.Open (System.String address) [0x00000]
  at NDesk.DBus.Bus.get_Session () [0x00000] --- End of inner exception stack trace ---

  at NDesk.DBus.Bus.get_Session () [0x00000]
  at Banshee.Base.DBusPlayer.FindInstance () [0x00000]
  at Banshee.BansheeEntry.DetectInstanceAndDbus () [0x00000]
Warning: [5/17/2008 2:24:10 PM] (Could not connect to D-Bus) - D-Bus support will be disabled for this instance: Unable to open the session message bus.
Debug: [5/17/2008 2:24:12 PM] (Loading audio profiles) - /usr/share/banshee/audio-profiles
Debug: [5/17/2008 2:24:13 PM] (Default player engine) - GStreamer 0.10
Debug: [5/17/2008 2:24:13 PM] (Audio CD Core Initialized) -
Debug: [5/17/2008 2:24:13 PM] (Testing device for DAP support) - /org/freedesktop/Hal/devices/volume_uuid_edec4bf1_c8c1_42d3_bb32_097090fe4fdb
Debug: [5/17/2008 2:24:13 PM] (DAP has not been added) - /org/freedesktop/Hal/devices/volume_uuid_edec4bf1_c8c1_42d3_bb32_097090fe4fdb
Warning: [5/17/2008 2:24:13 PM] (Power Management Call Failed) - Cannot find GNOME Power Manager: Unable to open the session message bus.[/SIZE][/SIZE][/FONT]

------------------------------------------------------------------------
Hipo:
Hipo iPod Management Tool
Rank: 
Package: hipoiPod Management Tool
Hipo is an application that allows you to manage the data of your iPod, Hipo is written in C# using Mono, GTK#, the cute ipod-sharp library and for tag editing it uses taglib-sharp.
Hipo is NOT a music playback software, for that you can use Banshee, Rhythmbox or Muine.

--------------------------------------------------------------------------
Also I am not sure how can I change the post from Multimedia production to Multimedia & Video.


Thanks for the reply

---

### Post by what4893 on 2008-06-03
I found a temporary fix for this DBus error. If you can't run dbus-launch it turns out that this application has been moved into the dbus-x11 package so do: sudo apt-get install dbus-x11. When that completes you should be able to run: dbus-launch banshee. Now something that happened to me was my music wasn't in Banshee when I fired it up. After that I installed the gnome-power-manager package and relaunched Banshee using the same dbus-launch banshee and all my music that I previously imported while I had the DBus error message was back. Very perplexing. It appears that dbus-x11 maybe needed as a dependency for banshee. If you haven't imported any music into Banshee while having the DBus error message you shouldn't HAVE to install gnome-power-manager.

---

