---
title: "server install on laptop doesn't install pcmcia support"
date: 2011-01-12
forum: Server Platforms
---

### Post by n8izn on 2011-01-12
I am installing Ubuntu Server 10.10 on and old Dell Laptop. The network connection is an Xircom PCMCIA card. 

During install, the computer sees and interacts via the network just fine. For example, I can ping the gateway. Also, the command "lspcmcia" works and show the Xircom card.

When I reboot, however, there is no network access, and the "lspcmcia" command is not there. When I try "lspcmcia" the OS helpfully tells me that I can "apt-get" pcmciautils, but, without network access, that fails.

I tried adding the install cdrom to apt using "apt-cdrom" and then tried to "apt-get" pcmciautils and it got further, installing some dependencies, but acted like it still was unable to locate the pcmciautils package.

And suggestions?

Thank you in advance.

---

### Post by n8izn on 2011-01-13
Well, after too much time, and too late at night, I solved the problem myself. It required exactly one, 33 KB package file that wasn't on the server install CD:

pcmciautils_014-4ubuntu4_i386.deb

1) I manually resolved the pcmciautils' dependencies, which were on the CD. 

2) I then downloaded the package to another computer.

3) While still in (yet another) install-from-the-CD mode, I transferred the file to the target laptop using busy box's wget. Remember, I did have operational networking while in the install mode.

4) I rebooted (completing the system install) and then I installed the package with dpkg.

5) I rebooted again and it now works!

To the Ubuntu Server maintainers: It was an educational endeavor for me, but was the install disk so tight that you couldn't fit a 33 KB file on it? Especially a file that affects the system's ability to download other files? Just a thought.

---

### Post by muflames on 2012-07-15
Just to add to this. In Ubuntu server 12.04 you need only use dpkg to install pcmciautils. Once you are done with this most cards should work right out of the box.

Cheers,
Muflames

---

