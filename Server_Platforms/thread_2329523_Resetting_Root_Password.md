---
title: "Resetting Root Password"
date: 2016-07-02
forum: Server Platforms
---

### Post by njstevenson86 on 2016-07-02
Currently trying to get a server back up and running at work. The problem is no one is able to get into the root account, all the passwords that were normally used on other boxes, or were written down have not worked. I have little to no experience working with linux, I just go to google and try to figure it out. I found these instructions: [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword) but I wasn't able to get it to work, and not sure what I am doing wrong. 

This is what I get when I get to the screen that allows me to select my boot method. 

GRUB 2.02 Beta 2-9 beta2-9ubuntu 1.3 

This is a pic I snapped of what I get when I go to edit the loading parameters.

[https://drive.google.com/file/d/0B00TxIor-m-ETjBmMFh2RVE4MDQ/view?usp=sharing](https://drive.google.com/file/d/0B00TxIor-m-ETjBmMFh2RVE4MDQ/view?usp=sharing)

It says it's loading Ubuntu 14.04 if I recall correctly when it gets to the login screen. 

How do I get into the system at this point?

---

### Post by howefield on 2016-07-02
Thread moved to the "*Server Platforms*" forum.

---

### Post by lisati on 2016-07-02
> **njstevenson86 said:**
> The problem is no one is able to get into the root account, <snip>

Are you referring to the "root" account, as found with many other *nix systems, or are you referring to the Administrative acccount?

With Ubuntu, the "root" account is usually disabled by default, and anything that would normally require administrative privileges is achieved with the help of tools such as ["sudo"]("https://help.ubuntu.com/community/RootSudo").

---

### Post by Graham_Willis on 2016-07-02
However, if it is about the administrative account, in GRUB boot menu go to the line starting with

```
module     /vmlinuz
```

then go to the word 

```
ro
``` 

delete this word and put there 

```
rw init=/bin/bash
```

then Ctrl-X and you should be in single user mode.

---

### Post by njstevenson86 on 2016-07-02
Allegedly the username on this account is root, and it acts as the admin/superuser access. Either way currently have none of the credentials that we have saved will get us into this box.

---

### Post by MAFoElffen on 2016-07-03
Ubuntu, like any other Linux, Unix, amd BSD system follows the same Unix inherited premise that physical control is a level of security... and (security wise) assumes that if you have physical control of the server, then you have control.

In Ubuntu, Yes, even though we recommend not setting a password to root, if you set a password to root, then it is there. Even previous to a root password being set, the root account ***always*** exists. The account is not disabled, as aniother poster commented. Other distro's that do commonly use root as a user, recommend implementing root jail as a security method...

For Security sake, it is not commonly discussed, but like I said, physical control is security (even with Win Server)--- meaning if you have physical control, you must have authorization to do what you want. It could be abused, but you do not need to be paranoid by it, it is a fact of life. 

This has to be done with a direct attached keyboard (not through ssh). On Boot, just past the BIOS messages, press the <left-shift> button. The default on the grub menu is only 2 seconds, so be timely. At the grub menu, <arrow-down> to the advanced option selection > Select > Recovery menu option > At Recovery Menu, select Networking (will remount the filesystem in r/w), then root prompt...

At the root prompt CLI, you then then use CLI to reset your user passwords via the CLI "passwd" command. <-- That is no secret to Sys Admin's and is in most doc's, if you dig deep enough. So I am not giving away any secrets.  

If your previous Sys Admin implemented not to show the Recovery menu items in the Grub Boot Menu, as a security measure to deter someone from getting to a root prompt at the physical control level, then ask me and I'll tell you how to get around that.

---

### Post by njstevenson86 on 2016-07-05
I have physical access to the server. When I boot and try to load the recovery menu it asks for the root password. 

Steps taken:

Advanced > Boot Recovery Mode > 
It asks me for the Root password for maintenance or Control-D to proceed

Also tried the RW option on the default loading option, as well as the advanced loading option. 

I am suspecting the previous sysadmin did disable things to prevent physical access.

Edit: so when I see the boot, I'm seeing something about /bin/bash does not exist when trying to do the rw init=/bin/bash/ method

Edit 2: 

Alright so first thing I found out that the recovery mode option under advanced did not have recovery in the launch parameters, it was actually an exact copy of the normal launch parameters. So I appended recovery nomodeset to the end of that line, was able to follow your instructions up until the point when I tried to access the root prompt and it was still asking me for the root maintenance password. 

Is there another setting that I should be using rather than nomodeset that would let me bypass this?

Second: went back to try to do the rw init=/bin/bash on the linuz line as instructed, when it boots I get an error that it cannot find the directory, then it locks up at a few lines after that and doesn't do anything.

---

### Post by Graham_Willis on 2016-07-05
If using **rw init=/bin/bash** complains about bash being non-existent, perhaps it is just not installed (or removed). But you wrote about using "**rw init=/bin/bash/" **in your post, so if it was not a typo, you can try with the trailing slash removed.
However, if bash is not installed, you can try with **rw init=/bin/sh** . 
Second thing, if you have physical access to the machine, you are (almost) bound to get into root account at last. Try the following procedure: 

[http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/](http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/)

If it doesn't succeed, please let us know.

---

### Post by njstevenson86 on 2016-07-05
That was a typo. I've tried rw init=/bin/bash as well as rw init=/bin/sh. Both threw errors and then locked up through the boot sequence. I'm in the process of trying to get a version of ubuntu installed on a usb drive and booting from that.

Edit: The place it locks up on reads: random: nonblocking pool is initialized

After that, it just stops, doesn't do anything, and I don't have CLI.

---

### Post by njstevenson86 on 2016-07-06
Was able to get in late yesterday. 

The howtogeek article was helpful, but didn't get me all the way. The system refused to mount the directory because of filesystem issues. Not sure what was causing it. What I was able to do was using the ubuntu live CD gui is use the nautilus command, get into the etc folder, blank the root password then get into the system.

---

### Post by MAFoElffen on 2016-07-06
Just got back in... So if you look at post #3 of the sticky in my sigline... is that how you got it (a chroot)?

---

