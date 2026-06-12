---
title: "I messed up my server"
date: 2006-04-18
forum: Server Platforms
---

### Post by Hanj on 2006-04-18
I was trying to set up proftpd on my server (running breezy), and since I'm quite noob-ish when it comes to groups and permissions and such in *nix, I did this:
```

usermod -G ftp hannes

``` where ftp is a group I created and hannes is my only user on that computer. What I didn't know was that this removed me from all other groups, including sudoers.](*,)  So now I get this every time I try to use sudo:
> hannes is not in the sudoers file.  This incident will be reported. Searching this forum, I found that rebooting into recovery mode and editing /etc/sudoers would fix this, but the problem is that I currently don't have physical access to the server, I can only reach it by ssh. 

So what I'm wondering is:
1. Is there any way to get back my sudo permissions without having to reboot the machine?
2. How would I add a user to a group without taking away sudo permissions? Would "usermod -G ftp sudoers hannes" work? (I know I could rtfm for this, but I just thought I'd ask while I'm at it so I don't screw up again ;) )

---

### Post by localzuk on 2006-04-18
You need to restart the computer into failsafe mode (at the grub loader screen press escape and select the failsafe kernel from the list). You will then boot to a root terminal where you can re-add groups to yourself.

---

### Post by Hanj on 2006-04-18
Ok, that's what I suspected.

---

### Post by fredbear7232 on 2006-04-18
One other quick thing to mention Hanj, (because I did the same darn thing too, and said heck with it and reinstalled) if you want to add new groups, but keep the existing ones, use:

adduser <username> <groupname>

It'll keep the pre-exisiting user groups, plus add whatever group you specify. Not sure if it allows you to add multiple groups, that I haven't tried. Just do one at a time to be safe.. :)

---

### Post by Hanj on 2006-04-18
Thanks for the tip, fredbear7232. That looks like a better way to do it :)

---

