---
title: "Missing Command Prompt"
date: 2017-07-02
forum: Server Platforms
---

### Post by mikenjenni on 2017-07-02
Hello,

I have Ubuntu Server 16.04 installed and use it as a home theater PC. I usually access my server via my Windows laptop with PuTTY which works just fine.

However, I recently connected a monitor directly to my server and noticed that it no longer displays a command prompt after a boot sequence. After the boot sequence is complete, it just sits there showing the last boot command. It does NOT give me a login prompt!

Therefor, I cannot do any administration directly from my server, I can ONLY use my laptop via PuTTY.

I have Googled and searched various message boards and cannot find out why my server no boots to the command prompt any more.

Anyone have any ideas on how to get my command prompt to display again?


Thanks in advance!!

Mike

---

### Post by TheFu on 2017-07-02
Try a different virtual terminal - <ctnl><alt>-1 ... thru 9.
That should display a login prompt.  Might need to hit <enter> a few times to get the prompt.

---

### Post by mikenjenni on 2017-07-03
Hi @TheFu....I tried every combination of ctrl+alt 1-9....and every other key on the keyboard. The ONLY that that I noticed is that ctrl+alt F2-F12 will clear my screen and then ctrl+alt F1 takes me back.

Here's a screenshot of what I am seeing.
[https://drive.google.com/open?id=0B_Kd3TeFxhpRdk1vejB6dTNrV3c](https://drive.google.com/open?id=0B_Kd3TeFxhpRdk1vejB6dTNrV3c)

I just cannot get my server to display a command prompt.

---

### Post by TheFu on 2017-07-03
TL;DR - try an older kernel.

I had something like that happen a few weeks ago after getting a corrupted kernel download.  Basically my keyboard wasn't working with that kernel. Neither did the mouse.  I remembered the kernel error - it provided a suggested fix, which I dutifully did and continued.  That fix didn't actually fix anything. It just forced the bad bits to be used.

The solution was to go into the advanced line in Grub during boot and pick an older kernel.  That allowed me to try an fix the newer kernel - which failed after following advice found via google. A newer kernel was released the following day, which did come down clean and has been working.  

I can't/won't see image. Sorry.

---

### Post by mikenjenni on 2017-07-27
So, I'm coming back to this thread again for assistance. I do not think it's a kernel issue. Everything else works just fine. The keyboard works...I just can't get a login prompt to appear directly on my server...I have no issues connecting to my server via ssh using putty from my windows laptop...It's just my server does not boot to a command prompt like it used to.

Through some additional research, I found something that could be the cause of my problem (but I'm not sure).

I use Webmin to manage my server and went to the "Bootup and Shutdown Services" and see several different varieties of the getty service (console-getty.service, getty-static.service, getty.target, [email]getty@tty1.servic[/email]e, etc)...None which are running..nor do they list any commands in the startup file.

Is getty what controls the command prompt to appear within Ubuntu 16.04 Server? If so...is there a way to "fix" getty? Or maybe a command to uninstall getty and then reinstall again?

Anyone that can help would be greatly appreciated!

Thanks!

---

### Post by cariboo on 2017-07-28
It looks like some service may not be starting, if you have a keyboard connected try Ctrl-c. I had that happen on one of my servers and Ctrl-c stop the service from loading, and it went to a login prompt. Using journalctl allowed me to track down what the problem was. This is assuming your system is using systemd.

---

### Post by Paul Weaver on 2017-08-04
All my 16.04 servers show a black screen by default on startup, pressing Alt-Right or Alt-Left a few times shows other screens (one appears to be dmesg or similar)

I've noticed it on a few machines, but as I install from a pxeboot I don't see the console 99% (or more) of the time

---

### Post by Paul Weaver on 2017-09-12
i'm guessing nobody else has come across this, it's constant. The boot screen doesn't show tty1 through tty6, but instead tty7, which consists of a single line of /dev/vda1: clean, I believe the cause of this is an ubuntu specific kernel parameter 'vt.handoff=7'

[https://help.ubuntu.com/community/vt.handoff](https://help.ubuntu.com/community/vt.handoff)

However I've fixed this by removing 'quiet splash' from /etc/default/grub in the install process. I have a preseed file including the following line

```

d-i preseed/run string run.sh

```

And the contents of that file contain:

```

#!/bin/sh -e
echo "Start run.sh preseed runscript" >> /var/log/syslog

echo "sed -e 's/quiet splash//' -e 's/^#GRUB_TERMINAL/GRUB_TERMINAL/' -i /target/etc/default/grub" >> /usr/lib/finish-install.d/01Grub
echo "[ -x /target/usr/sbin/update-grub ] && /bin/in-target /usr/sbin/update-grub || true" >> /usr/lib/finish-install.d/01Grub
chmod 755 /usr/lib/finish-install.d/01Grub

```

Which solves my problem

---

