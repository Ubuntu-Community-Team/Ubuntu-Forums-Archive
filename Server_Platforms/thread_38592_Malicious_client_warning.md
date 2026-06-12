---
title: "Malicious client warning"
date: 2005-06-01
forum: Server Platforms
---

### Post by hakkapeliitta on 2005-06-01
This morning my computer has couple warning messages.

#1. "Warning! Could not grab your mouse. A malicious client may be eavesdropping on your session."

#2. "Changing user Please enter your password to run /usr/sbin/firestarter"

What cause this? Is it some rootkit or has someone cracked my box? I tried to run chkrootkit and it gave this:

#eth0: PACKET SNIFFER(/sbin/dhclient3[6959], /usr/sbin/pppd[7646])

Then I installed rkhunter and it gave me this:

#* Filesystem checks
#  Checking /dev for suspicious files...                      [ OK ]
#   Scanning for hidden files...                               [ Warning! ]
#---------------
# /dev/.udev.tdb
#/dev/.udevdb /etc/.pwd.lock
#---------------
#Please inspect:  /dev/.udevdb (directory)

Can you please tell me what to do now.

---

### Post by LordHunter317 on 2005-06-01
[QUOTE=hakkapeliitta]This morning my computer has couple warning messages.

#1. "Warning! Could not grab your mouse. A malicious client may be eavesdropping on your session."

#2. "Changing user Please enter your password to run /usr/sbin/firestarter"

What cause this? Is it some rootkit or has someone cracked my box? I tried to run chkrootkit and it gave this:

#eth0: PACKET SNIFFER(/sbin/dhclient3[6959], /usr/sbin/pppd[7646])

Then I installed rkhunter and it gave me this:

#* Filesystem checks
#  Checking /dev for suspicious files...                      [ OK ]
#   Scanning for hidden files...                               [ Warning! ]
#---------------
# /dev/.udev.tdb
#/dev/.udevdb /etc/.pwd.lock
#---------------
#Please inspect:  /dev/.udevdb (directory)

Can you please tell me what to do now.[/QUOTE]
 I don't know what gives you those messages, but everything reported by the rootkit scanners is perfectly normal.

---

### Post by vague- on 2005-06-02
The first message is generated when the Gnome password entry box is incapable of taking focus of the mouse.  If you want to cause this deliberately, you can play with the menus quickly after launching an application that provides one.

The second message probably means that Firestarter needs to perform a task as root and wants you to elevate it's privileges.  For example, it needs to modify some of your rules.

The first message I am reasonably sure of, the second is an educated guess.

---

