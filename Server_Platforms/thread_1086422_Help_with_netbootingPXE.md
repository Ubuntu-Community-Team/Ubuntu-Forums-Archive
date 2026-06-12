---
title: "Help with netbooting/PXE"
date: 2009-03-04
forum: Server Platforms
---

### Post by Sneezer on 2009-03-04
Hello all, new here and fairly new to Ubuntu.

I have setup an Ubuntu Server Edition box and have installed and configured it to my exact needs. It's perfect (for me). I am wondering how it would be possible to create an image of this box and use it for booting through a PXE across 30 other boxes.

I don't need help setting up the PXE or anything like that, I just need help figuring out how I can mirror the identical setup of one box onto others through the network (PXE) as the servers do not have any CD drives.

Any and all help is widely appreciated!

Thanks.

P.S.: USB Thumb Drive installation would also be awesome!

---

### Post by e30drift on 2009-03-04
Good news, I did got my working and used this guide...
[https://help.ubuntu.com/community/Installation/Netboot]("https://help.ubuntu.com/community/Installation/Netboot")

I have my Ubuntu 8.10 server running DNS and DHCP and it hosts my Ubuntu 8.10 desktop installer files for the network install.

good luck!

---

### Post by koenn on 2009-03-04
> **Sneezer said:**
> 
I have setup an Ubuntu Server Edition box and have installed and configured it to my exact needs. It's perfect (for me). I am wondering how it would be possible to create an image of this box and use it for booting through a PXE across 30 other boxes.

I don't need help setting up the PXE or anything like that, I just need help figuring out how I can mirror the identical setup of one box onto others through the network (PXE) as the servers do not have any CD drives.

cool project.
you could probably use your existing server as a basis for creating a modified installer, or figure out how to clone your server's disks over the network after a pxe boot, but that sounds way to complicated to me. Besides, some stuff is really hardware-specific so such an arrangement wouldn't work if your servers aren't identical. And you would still have post-installation work to unique things like hostnames and static IP addresses.

I'd do it this way:
1- PXE boot a standard installer e.g like so: [http://users.telenet.be/mydotcom/howto/linux/diskless01.htm](http://users.telenet.be/mydotcom/howto/linux/diskless01.htm)

2- configure pxe so that it boots the installer with a preseed file from the network (http). This provides a hands-free, customizable installation, and there are some tricks the generate a preseed file that mimics an existing system

notes: [http://users.telenet.be/mydotcom/howto/linux/automatic.htm](http://users.telenet.be/mydotcom/howto/linux/automatic.htm)

3- let the preseed file execute a command when the installation is completed. Let this command be something like
wget [http://mywebserver/mypostinstallscript](http://mywebserver/mypostinstallscript) && ./mypostinstallscript ; or
wget [http://mywebserver/mypostinstallscript](http://mywebserver/mypostinstallscript) && [trick to run mypostinstallscript after reboot];

this post-install-script can include any command that you need to run to configure the server but couldn't include in the preseed. You might want to change the hostname, or so ...

if your post-installation tasks involve any editing of config files, you can replace them with commands like echo "something to add" >> whatever.conf ; or search and replace statements like sed -i s/old/new/g;.

You could also just  wget (copies of) the custom config files from your web server.


I've tried every step separately, I've never tried the entire combo, but I'm pretty sure it can be made to work. Additional advantage over cloning: once it's set up, maintenance is merely a matter of keeping your scripts/files/... up to date.

---

### Post by Sneezer on 2009-03-04
I couldn't create an image, so I'll have to do a basic install and then I will probably write a script to automatically configure them for me.

Would anyone be able to help with doing a 8.10 installation through USB?

I know I can install TO a USB, would it be possible to install THROUGH a USB stick?

Thanks all for the help thus far! :]

---

