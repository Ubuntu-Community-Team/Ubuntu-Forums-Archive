---
title: "change runlevel"
date: 2011-02-15
forum: Server Platforms
---

### Post by slaz on 2011-02-15
Hi, 

I installed Ubuntu Sever 10.10, then installed the desktop on that. I would like to change it so when it boots up, it will boot to the terminal not the desktop. After googling, I see that if I make a file called inittab in the etc directory, and put the following line of code in -
 id:3:initdefault:

I changed this to 2 since the runlevel for ubuntu server is that, did a reboot and still boots to the desktop interface.  Am I missing something here?

Thanks,
Slaz

---

### Post by sisco311 on 2011-02-15
Ubuntu uses [Upstart]("http://upstart.ubuntu.com/"). If you want to disable the display manager, then use the **text** kernel parameter. Edit the file **/etc/default/grub** and replace the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with **GRUB_CMDLINE_LINUX_DEFAULT="text"** and generate a new Grub config file:
```
sudo update-grub
```

---

### Post by cariboo on 2011-02-15
I would suggest you remove gdm, that way you don't have to change any run levels, and if you do need a desktop, just type:

```
startx
```

at the prompt.

---

### Post by lunatico on 2011-03-14
> **cariboo907 said:**
> I would suggest you remove gdm, that way you don't have to change any run levels, and if you do need a desktop, just type:

```
startx
```

at the prompt.

Can you elaborate a bit more on this please?

Do you mean:
```
sudo apt-get remove gdm
```
?

This will also remove ubuntu-desktop and I'm afraid I'll be left with no GUI if I do this.

I was going to use bum but gdm already appears unselected. Weird.

---

### Post by egpetrich on 2011-03-15
"startx" is the command to start X Windows. You enter it from the command prompt after logging in to the console. (I don't know what would happen if you tried to execute this from an SSH login. I suspect it will complain and not run.)

There was [another thread on this topic]("http://ubuntuforums.org/showthread.php?t=1699028") just a week ago. While following that thread, I found [another thread even further back]("http://ubuntuforums.org/showthread.php?t=1305659"). (Seems like a popular question.) Several people reported having problems with sound after removing the "gdm" package and starting the desktop with "startx".

Personally, I'd recommend using the GRUB2 method to suppress "gdm". I think it avoid potential dependency problems, and it seems fairly easy to revert if you decide you'd rather have "gdm" running all of the time.

---

### Post by saphil on 2011-07-28
What is the grub2 method?

for the record, if you are shelling into a server with ssh, startx will grumble and fail. :-(

---

### Post by lkjoel on 2011-07-28
> **lunatico said:**
> ...
This will also remove ubuntu-desktop and I'm afraid I'll be left with no GUI if I do this.
...
ubuntu-desktop is just a metapackage that installs all components of Ubuntu and keeps them up to date.
You will still have a GUI if you remove it.

---

