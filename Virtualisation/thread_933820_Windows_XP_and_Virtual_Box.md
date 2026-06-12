---
title: "Windows XP and Virtual Box"
date: 2008-09-29
forum: Virtualisation
---

### Post by c4n75p34k1337 on 2008-09-29
Hi, I'm new to the whole Linux and uBuntu concept. I just made the switch a couple days ago. YAY ME! Anyways I've been doing some reading and managed to get Virtual Box up and running with USB support and everything. However when I try to do Windows Update on my Guest OS in Virtual Box. All of the updates fail. Like every single one... So I was hoping someone could help me out...

P.S: Can someone please go over how they enabled USB in Virtual Box because I'm not exactly sure I did it right. 

P.P.S: Oh yeah, before I forget would someone lead my into a guide for beginners on how to use the Terminal. Which I hear it the core of every Linux distro. Please don't make it to complicated I'm only 13 yrs. old. 

-Thank You

---

### Post by c4n75p34k1337 on 2008-09-29
Can anyone help me on this???

P.S: Sorry for Double Post, but I really need an answer to this question.

---

### Post by snova on 2008-09-29
It's probably a networking issue. You have to configure VirtualBox to allow the guest OS to connect through the host OS's internet connection, but I don't know how to do that yet, as I've never done it.

If you can plug in a USB device and have the guest OS recognize it, it's properly configured :). I don't remember what I did, sorry.

You don't really need to know the terminal. It's really handy and really fast, but it's not necessary. On the other hand, a lot of instructions here will be given in the form of commands, so maybe you should learn a little...

Quick rundown: In a terminal, you type the names of programs and it runs them. There are little utilities to do just about everything for you, many with very cryptic names. Learning the CLI is a matter of finding out the names of these programs and how to manipulate them to do slightly different things.

---

### Post by Bakon Jarser on 2008-09-29
I have no idea but I would try autopatcher. 

[http://www.autopatcher.com/](http://www.autopatcher.com/)

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by Cope57 on 2008-09-29
Did you install VirtualBox Open Source Edition (OSE) or regular VirtualBox?
It makes a BIG difference.

[Setting up USB on Ubuntu](http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04)

Basically, you just have to tell Ubuntu that a group called usbusers should have read and write access to all usb devices.

1. Create a group called usbusers

2. Add yourself to this group

3. Edit the file /etc/udev/rules.d/40-permissions.rules (for this, you must have administrative privileges)

    3.1 Search for the following lines

```
    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb_device",                    MODE="0664"
```

    3.2 Change them to the following

```
    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb_device", GROUP="usbusers", MODE="0664"
```

4. Restart your PC

5. You should now have write access to all usb devices.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - 

I do not know which version you installed, but all the documentation for [VirtualBox is on their website]("http://www.virtualbox.org/").

---

### Post by binbash on 2008-09-30
for USB devices work you have to go virtualbox.org and download 2.x version, not the one in repos.

---

### Post by Bakon Jarser on 2008-09-30
> **binbash said:**
> for USB devices work** easily** you have to go virtualbox.org and download 2.x version, not the one in repos.

There fixed that for you.  It is possible to get USB to work with the repo version although it is a lot easier to download the Innotek closed source version.

---

### Post by c4n75p34k1337 on 2008-09-30
I think I downloaded the regular version. Do I have to use Open Source edition in order to use Windows Updates? Does anyone else who uses VirtualBox experience this error?

---

### Post by fraterm on 2008-10-24
> **c4n75p34k1337 said:**
> Hi, I'm new to the whole Linux and uBuntu concept. I just made the switch a couple days ago. YAY ME! Anyways I've been doing some reading and managed to get Virtual Box up and running with USB support and everything. However when I try to do Windows Update on my Guest OS in Virtual Box. All of the updates fail. Like every single one... So I was hoping someone could help me out...

P.S: Can someone please go over how they enabled USB in Virtual Box because I'm not exactly sure I did it right. 

P.P.S: Oh yeah, before I forget would someone lead my into a guide for beginners on how to use the Terminal. Which I hear it the core of every Linux distro. Please don't make it to complicated I'm only 13 yrs. old. 

-Thank You

Try these instructions to configure networking properly

[https://help.ubuntu.com/community/VirtualBox#Networking](https://help.ubuntu.com/community/VirtualBox#Networking)

The same document in a different section has instructions for USB too.  

What you need to know about the terminal is more accurately learning about the bash shell.  It's very similar visually to the cmd.exe command prompt "shell" in windows / dos, except there are a larger number of commands and a more logical syntax. I guess you could think of a shell scripting language as being almost Perl in terms of what it lets you do.

DIR = ls
CD = cd 
DEL = rm
DELTREE = rmdir

---

