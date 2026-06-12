---
title: "Installing Xfce4 on Ubuntu Server 6.06 lts"
date: 2008-04-16
forum: Server Platforms
---

### Post by wildman4god on 2008-04-16
I am a student in the cisco networking acadamy, and I am helping to set up our lab. They want a linux server, so I installed ubuntu 6.06 Lts but there is no GUI and I have no clue how to use a CLI. I need to install Xfce4 for a GUI and we don't yet have access to the internet. The reason for this is at the Job corps. we need to have every network connection approved by a commitee in texas and for them to approve the server we need to have it running first. I have the Gui on a flash drive and we can burn cds so using the Cli how do I install Xfce4. Please Help.

---

### Post by hyper_ch on 2008-04-16
what do you want a gui for on the server anyway?

---

### Post by cdenley on 2008-04-16
```

sudo apt-get install xfce4

```

If you want the full desktop environment
```

sudo apt-get install xubuntu-desktop

```

---

### Post by wildman4god on 2008-04-16
we need a GUI because the people that have to approve it need to see what it can do and a cli means nothing to them, and the teacher requested one because we need to use it but haven't yet learned the cli.
and the commands you gave me won't work because as i have said we can't get internet untill the server is approved and we need the gui to get it approved, like i said i have the file i need on a flash drive but i don't know how to get it on the server with the cli.

---

### Post by cdenley on 2008-04-16
To show what a server "can do", you need clients. If you need to demonstrate what it can do without internet, you would need to create an isolated network. You can install xubuntu if you need xfce4, but I'm not sure the xubuntu install disc would have the server packages you need, but I think you can install packages from the server install disc with xubuntu. You can also put packages on a cd from a computer with internet using aptoncd. Are you allowed to use the internet if you boot to a livecd?

> 
like i said i have the file i need on a flash drive but i don't know how to get it on the server with the cli. 

If you need a file off the flash drive, you need to mount it
```

sudo mkdir /media/usb
sudo mount /dev/sda1 /media/usb
cp /media/usb/myfile ~

```
Replace /dev/sda1 with the path to your usb's filesystem. You can find it with "sudo fdisk -l". If the "file" you are referring to is a package, you probably don't have the dependencies installed and won't be able to install it.

---

### Post by wildman4god on 2008-04-16
It is a tarball xfce-4.4.2-src.tar what eles do i need?

---

