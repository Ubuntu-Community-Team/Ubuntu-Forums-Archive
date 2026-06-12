---
title: "SSH and LiveCD"
date: 2008-07-10
forum: Server Platforms
---

### Post by nomexous on 2008-07-10
I have a server with no screen or keyboard. I'm able to access it through SSH from my laptop. Recently, I messed up my /etc/sudoers file. That means I can't use sudo. To fix my sudoers file, I need admin access.

Normally, I would just boot into a recovery console and edit the file. But this requires me to select the GRUB entry, which I am unable to do without a keyboard or screen. I can't borrow one, either.

I thought that I could start up my server with a LiveCD and SSH into. Then I would mount my hard drive and edit /etc/sudoers so it works. Unfortunately, the regular Ubuntu LiveCD doesn't have SSH installed by default. So, I thought a custom LiveCD would do well. I've already tried remastersys backup inside a virtual machine, but it doesn't allow commandline-only systems.

So basically, I'm looking to create a LiveCD which I can SSH into (remember, blank passwords cause problems), and which doesn't run X. I'd appreciate it if anyone could point me in the right direction.

---

### Post by RealPSL on 2008-07-10
Not to answer your question with a question but what about booting from a Live USB key instead. Do those allow you to install additional components since it is r/w. That might give you more options.

---

### Post by shp on 2008-07-10
Dont know if this helps but...

[http://www.knoppix.net/wiki/Headless_Knoppix](http://www.knoppix.net/wiki/Headless_Knoppix)

---

### Post by Dr Small on 2008-07-10
I completely understand your situation. The problem is, getting a livecd that has an SSH server installed on it already. SliTaz is one, but it boots to JWM or something, and has the SSH server start automatically, if I am not mistaken.

You could check it out and see if you could use it for your needs. I can think of no Ubuntu LiveCD that does this by default, nor any simple LiveCD that just fulfills this task.

---

### Post by Sef on 2008-07-11
Moved to Server Platforms.

---

### Post by nomexous on 2008-07-11
> **RealPSL said:**
> Not to answer your question with a question but what about booting from a Live USB key instead. Do those allow you to install additional components since it is r/w. That might give you more options.Unfortunately, no. My headless server is an older computer, and doesn't support booting USB devices.> **shp said:**
> Dont know if this helps but...

[http://www.knoppix.net/wiki/Headless_Knoppix](http://www.knoppix.net/wiki/Headless_Knoppix)Thanks, but unfortunately I don't have any floppy disks. :-(> **Dr Small said:**
> I completely understand your situation. The problem is, getting a livecd that has an SSH server installed on it already. SliTaz is one, but it boots to JWM or something, and has the SSH server start automatically, if I am not mistaken.

You could check it out and see if you could use it for your needs. I can think of no Ubuntu LiveCD that does this by default, nor any simple LiveCD that just fulfills this task.SliTaz is a no go. There's a screen that sits there just waiting for you to select a language before it'll boot up. Without a keyboard, it'll just wait forever. Plus, it has X, and X will fail without a monitor.

---

### Post by Dr Small on 2008-07-11
Well you could try to remaster the "Miniubuntu" that is nothing more than a Command Line LiveCD of Ubuntu. You would have to try to remaster it to add OpenSSH Server to it and configure the network on it, so when you boot it, you would be able to SSH into it.

[http://kmandla.wordpress.com/2007/11/29/miniubuntu-710-at-last-a-command-line-ubuntu-live-cd/](http://kmandla.wordpress.com/2007/11/29/miniubuntu-710-at-last-a-command-line-ubuntu-live-cd/)
[http://minibuntu.crealabs.it/](http://minibuntu.crealabs.it/)

(Thanks to K.Mandla for helping me find those links ;))

Dr Small

---

### Post by nomexous on 2008-07-11
Problem fixed. It turns out remastersys was the right way.

How to create a LiveCD you can SSH into:
1.) Create a virtual machine and install a minimal, non-X version of Ubuntu.
2.) Be sure to set a username and password you will remember.
3.) Install and configure SSH.
4.) Install remastersys.
5.) Run remastersys with the backup option. ("sudo remastersys backup")
6.) Test the disc in the virtual machine. When it boots up, it will say "User not known to the underlying authentication module." (This is under remastersys version 2.0-5; it may or may not be fixed in later versions.) Ignore this error. Using the user that you set up, try SSHing into your virtual machine from your host machine. If it works, burn the image to disk. You can then go ahead and do whatever you need to do.

Using this method, you simply need to put the CD in the drive, and boot up the server. There's no need for a keyboard or screen at all. The GRUB menu sits for 30 seconds before automatically selecting the first entry and booting up your LiveCD. Wait 2 or 3 minutes to make sure the system is fully up, and then you can go ahead and SSH into the machine.

---

