---
title: "raw1394 permissions"
date: 2011-04-26
forum: Ubuntu Studio
---

### Post by swiftoid on 2011-04-26
Hi everyone. I've spent about 6 hours searching t'interweb for a solution to this, and I'm stumped. I was wondering if anyone here could help. Basically I've got my firewire soundcard (alesis IO26) to work ok on ubuntu, the only problem is I have to "sudo" every program that uses it. I've followed all the instructions posted around the web, and many others. I even temporarily made myself owner of /dev/raw1394, but that didn't help. I'm running ubuntu studio 10.10 64-bit, but I've also tried on plain ubuntu 10.10. My current permissions setup is:

> james@ubuntu:~$ ls -l /dev/raw1394
crw-rw-rw- 1 root audio 171, 0 2011-04-26 21:29 /dev/raw1394
james@ubuntu:~$ groups
james adm disk dialout fax cdrom floppy tape audio dip video plugdev fuse netdev lpadmin admin sambashare

So in theory I have complete access. But unless I sudo ffado I get this:
> 00823041321: Fatal (devicemanager.cpp)[ 191] initialize: No firewire adapters (ports) found.
In other words ffado can't access the port. If I do sudo it, it reads the port fine and I'm even able to play music.
Can anyone help? I'm completely lost.

The issue here is not ffado's support of my IO 26 (technically not supported although it works). It's that despite being in the same group as /dev/raw1394 ("audio"), ffado can't access it unless it's run with sudo.

Thanks

---

### Post by jejeman on 2011-04-26
Looks youre using the old firewire stack. So, have you tried this method from this instructions: [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

Ubuntu 10.04 (Lucid Lynx) and 10.10 (Maverick Meerkat)

Everything should just work if you paste this in your terminal, and reboot:

```
echo 'KERNEL=="raw1394", GROUP="video", MODE="0664"' |
sudo tee /etc/udev/rules.d/50-raw1394.rules
&& sudo restart udev
```
You should change the group from video to audio.

---

### Post by swiftoid on 2011-04-26
Hi, thanks for your help. Unfortunately I've already tried that - it didn't work. :(
Any other ideas?

---

### Post by bluesscream on 2011-04-26
After all you might be on the new firewire stack. Then you'd have to add a group named 'firewire' with your user as member. Give it a try, this can't break nothing.

---

### Post by Pablo_F on 2011-04-26
I suggest you take a look at the terminal output of "ffado-diag".

---

### Post by swiftoid on 2011-04-28
Thanks for your suggestions guys. Unfortunately they didn't really work :( I still can't use firewire. Just to be clear, I'm running a fresh install from the latest .ISO - not a patched older install. This is my first time trialing linux in years.

I seem to go through this cycle. Every two years or so I think, "maybe I can finally switch to linux this year, maybe it's finally in a liveable state!" Then I waste a whole week trying to make it work right, get sick of it and resign myself to waiting another couple of years. I think that's just happened again.

It seems that some overzealous volunteer in charge of security rules around here has decided that letting me access my own firewire port would constitute a major breach of security. I mean, why would I want to use firewire anyway?

If ubuntu was designed primarily for server/multi-user environments then I could understand this rule, kind of. But ubuntu is manly a single user enviroment. Why make such stupid security procedures, and then make them near-impossible to over-ride without years of experience working with linux?

Sorry. I'm ranting - I did just waste 10 hours of my life (read: 10 hours of pay) trying to overcome a pointless security rule.

Don't get me wrong, I love the idea of community driven open-source movements - I've even contributed time and code to several myself over the years. I really appreciate all the work all the volunteers have put in to get linux to it's current state. I just think it needs a bit more work before I'm ready to switch.

If I had the time, I would switch anyway and contribute to making it better  - helping debug and improve projects. But unfortunately right now I need an environment where I can work easily without wondering if I'll need to break off for 10 hours just to overcome one near-un-documented security rule. Maybe in the future I'll switch when linux is a little more user-friendly, and donate some resources then - when I know I'll get something back in return; a day-to-day usable operating system.

Thanks for your help once again. Sorry to rant.

Jamie

---

