---
title: "Could not access PID file for nmbd"
date: 2010-01-16
forum: Server Platforms
---

### Post by ronin8600 on 2010-01-16
I have an Ubuntu 9.10 server and I recently noticed that when it starts up I see the following displayed 

* Starting init crypto disks..
* Could not access PID file for nmbd

I don't know where the message "Could not access PID file for nmbd"  it doesn't appear to be coming from samba because samba is starting later in the startup.  I've had no issues with samba and I can restart samba with no issues.

Is this something to be concerned about?  I noticed it started after I upgraded my samba server.

---

### Post by pcjunkie on 2010-01-16
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/462169](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/462169)

Bug 

I have been getting this too

---

### Post by ronin8600 on 2010-01-17
Thanks for the information.

---

### Post by OriTheEep on 2010-01-29
> **ronin8600 said:**
> I have an Ubuntu 9.10 server and I recently noticed that when it starts up I see the following displayed 

* Starting init crypto disks..
* Could not access PID file for nmbd

I don't know where the message "Could not access PID file for nmbd"  it doesn't appear to be coming from samba because samba is starting later in the startup.  I've had no issues with samba and I can restart samba with no issues.

Is this something to be concerned about?  I noticed it started after I upgraded my samba server.

I've just seen this message, too. Not sure what I should check; so far I haven't noticed anything not working.

---

### Post by Neill_R on 2010-02-24
I am seeing this message when I shut down from the GNome desktop. My system goes to a cli screen and this message appears before a login prompt appears and then the whole machine shutsdown and powers off.

---

### Post by Wlo on 2010-02-24
Same happening here - can't reboot into recovery console :<

Any ideas if I can do anything other than reinstall my system?

---

### Post by nu c on 2010-02-26
I don't know if this will help
but at the start up screen on your computer you have a short time as it changes from bios to grub to press esc and go into recovery mode . The exact point is just before the bios screen disappear, but not while it is still selectable, trial and error. This is the solution i am using, I still have a problem with the graphics.

---

### Post by Jose Catre-Vandis on 2010-04-04
This has just cropped up on my PC too, was hanging on bootup just before the login screen (slim). Wouldn't work in recovery mode, told me about the nmbd pid but wouldn't let me do anything about it so CTRL-ALT-DEL was necessary.

Found that by removing quiet and splash from the grub boot entry I could boot up OK again

---

### Post by hbbk on 2010-05-12
> **Jose Catre-Vandis said:**
> This has just cropped up on my PC too, was hanging on bootup just before the login screen (slim). Wouldn't work in recovery mode, told me about the nmbd pid but wouldn't let me do anything about it so CTRL-ALT-DEL was necessary.

Found that by removing quiet and splash from the grub boot entry I could boot up OK again

I had almost the same problem of "Could not access PID file for nmbd" (except that I could enter a root shell) and removing only splash option in /boot/grub/menu.lst solved it, I don't know what splash is for but this is a real strange bug :)

---

### Post by brsabini on 2010-08-03
My server 9.1 always stop after showing this message. But, after I reset (press the reset button) the server, it goes back to normal.
So, everyday I have to turn on the server, wait until this message appear then reset the server to make the server back to normal.

---

