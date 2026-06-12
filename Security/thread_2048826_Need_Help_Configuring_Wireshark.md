---
title: "Need Help Configuring Wireshark"
date: 2012-08-27
forum: Security
---

### Post by w201 on 2012-08-27
Greetings-

Trying to set up wireshark to capture traffic in my home network, but I'm getting an error message. First off, I used the following code to set up wireshark so as NOT to run as root:

> $ sudo -s 
# sudo apt-get install libcap2-bin
# groupadd -g wireshark 
# usermod -a -G wireshark myusername 
# chmod 750 /usr/bin/dumpcap 
# setcap cap_net_raw,cap_net_admin=eip /usr/bin/dumpcap
The error message I get when I startup the application is:

> Couldn't run /usr/bin/dumpcap in child process: Permission denied

Any help to sort this out would be greatly appreciated!

---

### Post by Ms. Daisy on 2012-08-27
Try this:
[https://blog.wireshark.org/2010/02/running-wireshark-as-you/](https://blog.wireshark.org/2010/02/running-wireshark-as-you/)

---

### Post by w201 on 2012-08-27
Hey Ms. Daisy,

Actually, those are the commands I tried originally that got me the error message. This is probably worth mentioning, but when I ran those commands, I change one line:

groupadd -g wireshark 
to
groupadd  wireshark 

because the original command was asking for a value, so I just removed the -g and I was able to add the group wireshark. I don't know if this would cause the problem I'm experiencing, but wanted to mention it nevertheless.

---

### Post by CyberpathicGhost on 2012-08-27
And once you run the commands, setting up the group and adding yourself etc..

Log out and once logged back in it works at that point.

---

### Post by w201 on 2012-08-27
> **CyberpathicGhost said:**
> And once you run the commands, setting up the group and adding yourself etc..

Log out and once logged back in it works at that point.

I've tried logging out, logging back in, rebooting, but I still get the same error message.

---

### Post by CyberpathicGhost on 2012-08-27
I used the commands from this page:

[http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/)

They are a bit different than those posted.

You can also try running Wireshark as sudo just to see it work, as a test.

terminal: sudo wireshark

---

### Post by w201 on 2012-08-27
Do you know how I can undo the changes I made by running those commands, I'd hate to run additional commands and risk really fing up system files. 

If I run it as sudo, I get this error message:
> Lua: Error during loading:
 [string "/usr/share/wireshark/init.lua"]:45: dofile has been disabledBut once I exit out, it works. But I really need to get this errors squared away.

---

### Post by CyberpathicGhost on 2012-08-27
I'm just a novice. I haven't had any trouble with this aspect of the setup. But I have had to reinstall Ubuntu two or three time in the short while I've been using it. I tend to not mess with the OS, these days, after the installation. So far so good. Good luck.

---

### Post by w201 on 2012-08-27
No problem. Anyway, thanks for trying. I'm actually trying to run this on linux mint maya, it's a fresh install, so I could always do a quick reinstall. But I hate to get into the habit of re-installing systems whenever I run into a problem.

---

### Post by CyberpathicGhost on 2012-08-27
In my defense, practice makes perfect. :lolflag:

But I agree with your method too. However at this point for me reinstalling can be way, way faster. Not knowing the correct questions, my speed of learning and the way in which I compound my problems all conspire against me. 

Da Buddha, recommended from my past life.

---

### Post by Colo993 on 2012-08-27
I've recently installed Ubuntu 12.04 and Wireshark.  Due to issues with a video driver I had to install Ubuntu again.  Both times I used the following procedure to fix the permissions issues with Wireshark:

[http://tryout-chen.blogspot.com/2011/01/ubuntu-enable-wireshark-capturing.html](http://tryout-chen.blogspot.com/2011/01/ubuntu-enable-wireshark-capturing.html)

After following the procedure and logging out/in Wireshark runs without error and I can capture on my Ethernet and WiFi interfaces.

Good luck!

Colo993

---

### Post by w201 on 2012-08-27
Hey colo, I actually got it working after trying out the instructions that CyberpathicGhost posted.

BTW- thanks to CyberpathicGhost for that! I basically ran the commands like it was the first time and that did it. No error messages and I didn't even have to do a fresh install :guitar:

---

### Post by midpeter444 on 2012-09-24
I faced the same problems (on Xubuntu 11.10) as the OP.  The original blog those instructions are from ([https://blog.wireshark.org/2010/02/running-wireshark-as-you/](https://blog.wireshark.org/2010/02/running-wireshark-as-you/)) has two unfortunate errors in the section of how to set up dumpcap using Linux capabilities, rather than making dumpcap as setuid.

Error 1: forgot to chgrp of /usr/bin/dumpcap to the wireshark group
Error 2: didn't add 'eip' to both capability settings.  

Here's how the instructions should read:
[FONT=Courier New]$ sudo su - root 
# sudo apt-get install libcap2-bin
# groupadd wireshark 
# usermod -a -G wireshark gerald 
# chmod 750 /usr/bin/dumpcap
# chgrp wireshark /usr/bin/dumpcap    
# setcap 'CAP_NET_RAW+eip CAP_NET_ADMIN+eip' /usr/bin/dumpcap

[/FONT]Note: on modern Ubuntu's you probably don't need to install libcap2-bin.  I already had it.

---

