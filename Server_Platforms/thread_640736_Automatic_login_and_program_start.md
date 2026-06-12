---
title: "Automatic login and program start"
date: 2007-12-14
forum: Server Platforms
---

### Post by zac1333 on 2007-12-14
I have an Ubuntu 5.10 headless server that runs on-hold music for a phone system using mplayer from a command line.  Here's what I'm looking for:

1.  Have a certain user be logged in automatically when the machine starts.
2.  Have the mplayer command run automatically once the user is logged in.

I want all of this to happen so that if I hook up a monitor to the computer I can see the mplayer running.  If that isn't possible, I'm ok with that.

Please advise.  My google searches so far have not yielded what I want to accomplish.

---

### Post by tgilber1 on 2007-12-21
To select a user to have automatic login:

1.  From panel, select #System#Administration#Login Window
2.  From Login Window dialog, select Security tab
3.  Select "Enable Automatic Login" checkbox
4.  Select user from drop-down list
5.  Click "Close" button to save changes

Note:  "Automatic Login" is a security breach

To start up mplayer automatically during login:

1.  From the panel, select #System#Preferences#Sessions
2.  Should open to Startup Tab, if not, select Startup Tab
3.  Click add button
4.  Name field:  Populate the name of program
5.  Command field:  Populate absolute pathname of file (mplayer) to startup
6.  Comment field:  [optional] Populate a description of the program

Lastly, you can add options to the mplayer command to play specific files, locations, videos, etc.  Check out "man mplayer"

---

### Post by zac1333 on 2007-12-26
This server is terminal only, so I don't have a GUI to perform the functions that you described.

---

### Post by FakeOutdoorsman on 2007-12-26
> 2. Have the mplayer command run automatically once the user is logged in.
Commands in **.bash_profile** will be executed by Bash once the user logs in.

---

### Post by qpieus on 2007-12-29
For the auto login, try the rungetty program:

sudo apt-get install rungetty

Then you need to modify the /etc/inittab file. Go to this section of the /etc/inittab file
```
# /sbin/getty invocations for the runlevels.
#
# The "id" field MUST be the same as the last
# characters of the device (after "tty").
#
# Format:
#  <id>:<runlevels>:<action>:<process>
#
# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty
```

and modify the first getty so the line looks like this:

```
1:2345:respawn:/sbin/rungetty tty1 --autologin *username*
```

This hack was adapted from debian, but since you are using ubuntu 5.10 it should work the same. Note that ubuntu 6.10 and later don't use inittab during boot, they use upstart instead, so this won't work for 6.10 and later.

---

### Post by cenwesi on 2008-03-24
so how to make this work on Gutsy/Hardy?  This is exactly what i want to do... i need to run an application for HTPC?, i really don't need gnome

---

### Post by Andre_44 on 2008-04-22
Same here. *bump*

---

### Post by cenwesi on 2008-04-23
Still can not believe the guru's out there don't have answer for this.

---

### Post by kerry_s on 2008-04-23
it doesn't work with edgy on, because they switched to upstart, which uses /etc/event.d/*

---

### Post by cenwesi on 2008-04-23
I guess i should have been more specific... I run Gutsy & Hardy

---

