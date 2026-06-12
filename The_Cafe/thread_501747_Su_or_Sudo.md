---
title: "Su or Sudo"
date: 2007-07-15
forum: The Cafe
---

### Post by ThinkBuntu on 2007-07-15
First, I'm sure that most responses will be for sudo, as that's the Ubuntu way of doing things. But who here uses su as opposed to sudo? Does anyone exclusively log in as root, and dodge the whole dilemma? Lately I've taken to only using su, as I always turned off the sudo timeout (security reasons) and there's really little difference between using su and sudo for timeliness without the timeout. Once you take yourself out of the sudoers file, you have the benefit of blocking any administrator access with your own password, but have the increased risk of needing to enter the root password from your own account, which could possibly be recorded somehow.

So, sudo or su?

---

### Post by etank on 2007-07-15
I always use sudo with Ubuntu but I also set it up for use on other distros I use as well.

---

### Post by AndyCooll on 2007-07-15
Sudo everytime. It's just so easy to use.

And doesn't "sudo -s" get past the timeout?

:cool:

---

### Post by Freddy on 2007-07-15
I want my su :).

---

### Post by RAV TUX on 2007-07-15
> **ThinkBuntu said:**
> First, I'm sure that most responses will be for sudo, as that's the Ubuntu way of doing things. But who here uses su as opposed to sudo? Does anyone exclusively log in as root, and dodge the whole dilemma? Lately I've taken to only using su, as I always turned off the sudo timeout (security reasons) and there's really little difference between using su and sudo for timeliness without the timeout. Once you take yourself out of the sudoers file, you have the benefit of blocking any administrator access with your own password, but have the increased risk of needing to enter the root password from your own account, which could possibly be recorded somehow.

So, sudo or su?

[CENTER][SIZE=6][COLOR=DarkRed]***[FONT=Georgia]SUPER USER BABY[/FONT]***[/COLOR][/SIZE][SIZE=6][COLOR=DarkRed][I][B][FONT=Georgia]![/FONT] ;-)
[/B][/I][SIZE=1]http://en.wikipedia.org/wiki/Superuser[/SIZE][/COLOR][/SIZE] [/CENTER]

---

### Post by regomodo on 2007-07-15
sudo all the time

@ etank. That's a funky bean counter

---

### Post by a12ctic on 2007-07-15
Can't say I've used su sense my old debian counter strike server in like 1999. when i was still an uber linux noobie.

---

### Post by starcraft.man on 2007-07-15
Never had any reason to change from sudo...

---

### Post by yatt on 2007-07-15
I use su.

---

### Post by smartboyathome on 2007-07-15
I use a combination. When I am typing more than 1 line, I use su. Otherwise, i use sudo.

---

### Post by bonzodog on 2007-07-16
Running Zenwalk, I use su.

But I could see where sudo was useful.

---

### Post by Afoot on 2007-07-16
When I know I'm gonna do a couple of commands, I'll use su, otherwise sudo.

---

### Post by Cope57 on 2007-07-16
I use a Root Terminal...
gksu /usr/bin/x-terminal-emulator

I only have to give the root password once during the session. Since I rarely reboot, unless upgrading the kernel, sessions can last quite a long time.

---

### Post by ThinkBuntu on 2007-07-16
> **Cope57 said:**
> I use a Root Terminal...
gksu /usr/bin/x-terminal-emulator

I only have to give the root password once during the session. Since I rarely reboot, unless upgrading the kernel, sessions can last quite a long time.

Spooky!

---

### Post by roachk71 on 2007-07-16
When I use GNOME, sudo works fine. But if this command is used from within a Konsole session, the system administration GUIs refuse to work (kdesu won't start for them.)

In the case of a KDE session, I bring up the command line and use 'kdesu konsole' instead when I need a root terminal.

---

### Post by matthinckley on 2007-07-16
I use sudo and if I'm going to need root access for multiple commands i run 'sudo -i'

---

### Post by rickyjones on 2007-07-16
One liners, generally just use sudo. If I'm doing a little more administration I'll open up a bash shell as root (sudo bash) and use that terminal for the time being.

-Richard

---

