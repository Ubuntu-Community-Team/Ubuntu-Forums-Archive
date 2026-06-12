---
title: "Screwed up hostname on 6.06 LTS"
date: 2006-11-13
forum: Server Platforms
---

### Post by FrozenPixel on 2006-11-13
Hello, bit of a dilemna here.

Ok I not only edited the hostname in:

/etc/host

where I added: 
127.0.0.1     localhost.localdomain localhost
192.168.0.100 myserver.example.com   myserver

but also I went and changed

/etc/hostname

and this is where I screwed up. Instead of just entering:
myserver.example.com

I went -
#myserver
myserver.example.com

And now I can't get back in to correct the problem, I keep getting:

sudo: unable to lookup #myserver

Now what should I do, reinstall??

Ubuntu Server 6.06 LTS with LAMP

Thanks

---

### Post by r0ydster on 2006-11-14
> **FrozenPixel said:**
> And now I can't get back in to correct the problem, I keep getting:

sudo: unable to lookup #myserver


Are you connected to the box via your network??

I'd say log onto the console and edit the file that way - it's gotta be one line:

r0ydster@server$: cat /etc/hostname
server.domain.org

Delete the #myserver line and save the file - make sure it's a 1 line file.

A quick way to do it:

sudo echo server.domain.com > /etc/hostname

Hope this helps,

Mike

---

### Post by FrozenPixel on 2006-11-14
Hello,

I was logged in locally and not through any other programs like Putty or anything if that's what you are referring too.

I tried the last command but gives me a permission error. Actually because of my screw up it does not even allow me to shutdown or restart because of the messed up hostname.

In fact upon logon I tried to execute the command:
sudo -s

to access the shell but no luck, fails again on the #myservername.

Because I am learning I have no problem reinstalling but that would really be an extreme scenario since if this was a real production server it wouldn't be an option in that case.

So trying to resolve the problem through the knowledge here I figured would be best.

I'm at work right now so won't be able to try your other suggestion till I get home.

Thanks

---

### Post by Iowan on 2006-11-14
May need to reboot into recovery mode (via **grub**.

---

### Post by FrozenPixel on 2006-11-14
I didn't realize there was a recovery mode, thanks for that tip Iowan, I will go search on how to do that.

---

### Post by hardin0341 on 2007-03-19
Months later, and here I am in the same predicament. I have screwed up my hostname and I cannot access anything due to the "permission" problem listed above as well as the error with "gethostname()".

I wish I knew if the "safe mode" helped. I assume a reinstall is inevitable. 

Nice to know I'm not the only one. Also, the root cause of me trying to mess with the hostname was because the domain was not being recognized. 

Beginner getting my feet wet,

Thanks!

---

### Post by ColdCanuck on 2007-03-19
Have you tried to boot into single user mode (recovery mode). 

I believe "safe mode" is something you find on a Windows box <grin> and single user mode is anything but safe. Single user mode will let you run as root and allow you to do the edits described upthread, and fix the issue.


Good Luck

---

### Post by Nikron on 2007-03-19
It's not really 'safe mode' it's 'recovery mode' =P  Anyway, if you haven't figured it out yet, you get to it by hitting escape when grub is counting down.

---

