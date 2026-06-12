---
title: "Apache 2 configuration on Ubuntu 7.04 LAMP server?"
date: 2007-09-05
forum: Server Platforms
---

### Post by jusatry on 2007-09-05
Hi all,

I am very new to linux.  I spent this past weekend fooling around with different ubuntu (and other) distros on a spare system I have with the hopes of doing two things:

1) setting up a file server with web and ftp interfaces for easy centralization of all my various media files

2) setting up a mythtv box for PVR usage.

I tried knoppmyth, mythbuntu, fiesty 7.04 and 7.04 server; and settled on server (mostly because it was the only one I could get to work ;-) ).  So I am still in text only mode, but I was able to share my usb drives out using samba and configure the box with a static ip address.  Woooohooo.

So here is my situation:

I installed apache, and i edited the config file to add localhost as a the servername. I also edited the default file in the sites-available folder to test my configuration.

I was able to see the default site from another computer on the network.  Awesome!

Here's the problem:  I tried to use the usb drive folder i used for the fileserver in samba as the "'site directory" in the default file, and i get an "access denied" error from apache web.  I have chmod'd the folder (its in my /mnt/ directory), and i have mounted the usb drive as read/write.

What am I missing?  Is it not possible to have the apache server see a mounted folder?!?

Thanks so much for your thoughts.

---

### Post by stuartt on 2007-09-06
I'm not totally clear on what you are trying to do but it sounds like you need to run chown on the folder. The /var/www directory is the default directory for apache2's web root. It is set to root:root. I'd suggest you chown the directory you want to use to the same and see if that helps.

Just fyi, some things that confused me:
> "I edited the config file to add localhost as a the servername"
You shouldn't need to edit anything to get localhost to work.
> I tried to use the usb drive folder i used for the fileserver in samba as the "'site directory"
Why would you want to do this? The more you start messing with the default settings (esp. since you are new to linux) the worse off you are going to be.

Be aware that setting up a PVR can be quite tricky.If you were unable to install the regular version of Ubuntu or mythbuntu you will probably have a heck of a time with this. Just warning you.

---

### Post by fuzz500 on 2007-10-15
here we go again.... ME TOO. I have the same problem... I setup LAMP on  my ubuntu 7.04 and [http://localhost/](http://localhost/) works. Great. Now i want to put the webroot directory or a link to a directory on a USB memory stick, so I can carry my development files from work to home. 

But for some reason, this doesn't work. I tried two ways. 1. I set the apache webroot to /media/memorexUFD/htdocs (path to the directory on my memory stick) and 2. restored default apache webroot and put a symlink from there to the memory stick ... 

result: when you try to access the directory via symlink in the web browser ([http://localhost/apache2-default/htdocs](http://localhost/apache2-default/htdocs)) you get a "403-You don't have permission to access /apache2-default/htdocs on this server."

I then tried to set the owner of the /htdocs directory on the usb stick to "root" and nothing happens... you can't seem to do that. It seems that the usb stick is invisible to the root user??? Looking for ideas.. anyone??

Update

I did some research and found out a few things. The memory stick has a FAT file system on it, and therefore has no Acess Control Lists or file security settings at all. The way it works is that when the stick is mounted, a umask is set on the mount command, which sets the access rights for the entire file tree being mounted. I couldn't get it to work properly, but essentially you have to put a line in your fstab so that it will mount with the desired file permission. Good Luck out there!

---

