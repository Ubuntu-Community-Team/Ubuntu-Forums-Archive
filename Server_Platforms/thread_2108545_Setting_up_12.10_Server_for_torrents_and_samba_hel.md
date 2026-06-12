---
title: "Setting up 12.10 Server for torrents and samba help"
date: 2013-01-24
forum: Server Platforms
---

### Post by RandomP on 2013-01-24
I have googled myself to exhaustion trying to figure out a good way to set this up. 

What I would like to do:
Set up a server that primarily functions as a torrent server with a samba share to easily share the downloaded files with my Windows computers.

I have a fresh install of Ubuntu 12.10 Server edition (x64) with OpenSSH, LAMP Stack and Samba. I chose those as they will probably be the most useful to me and my plans for the server, other than having it torrent.

Most of the guides I have found included setting up virtual machines on the server... That is not something I want to do unless I really, really have to. I want to keep things as simple as possible.

So, my question is, is there a guide, or perhaps just an outline of how I can go about setting this up? I would prefer a setup with rtorrent + webui, but any client will do so long as it supports magnet links and has a webui.

Note: I do not have a gui (gnome, etc) on the server itself and do not want one.

If this is in the wrong section, I apologize, multimedia seemed like the most relevant place to put it.

---

### Post by howefield on 2013-01-26
Thread moved to the "*Server Platforms*" forum.

---

### Post by thnewguy on 2013-01-26
Ideally, I think you will want to use Transmission as the bittorrent client. it supports both command line and web interfaces. [http://www.transmissionbt.com/](http://www.transmissionbt.com/) You could set up the Transmission web interface for control and have it save all of your downloaded torrents in the Samba share. Ubuntu has some good documentation on configuring Samba shares here: [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by donniezazen on 2013-01-26
Install Transmission
```
apt-get install transmission-cli transmission-common transmission-daemon
```

Create folders if you don't have them
```
mkdir downloading        # incomplete downloads
mkdir complete           # completed downloads/seeding torrents
```

Add your user to Transmission' group
```
usermod -a -G debian-transmission $USER
```

Change group ownership of folder you created or had
```
chgrp -R debian-transmission $folders
```

Give group permissions to write in folders
```
chmod -R 775 $folders
```

[Edit Transmission's config]("https://trac.transmissionbt.com/wiki/EditConfigFiles")
```
vim /etc/transmission-daemon/settings.json
```

Reload
```
/etc/init.d/transmission-daemon reload
```

Open port 9091

Transmission should be available @

[http://localhost:9091](http://localhost:9091)

---

### Post by RandomP on 2013-01-26
Thanks for the responses guys. 

> **donniezazen said:**
> 
Change group ownership of folder you created or had
```
chgrp -R debian-transmission $folders
```
At this point I get:

```
chgrp: missing operand after `debian-transmission'
Try `chgrp --help' for more information.
```
I am not sure why.

---

### Post by donniezazen on 2013-01-27
> **RandomP said:**
> Thanks for the responses guys. 


At this point I get:

```
chgrp: missing operand after `debian-transmission'
Try `chgrp --help' for more information.
```
I am not sure why.

Replace all $folders with your actual folders.

```
chgrp -R debian-transmission downloading
```

You should most definitely do Google search before executing any command on your system and not blindly execute codes.

---

### Post by RandomP on 2013-02-03
> **donniezazen said:**
> Replace all $folders with your actual folders.

```
chgrp -R debian-transmission downloading
```

You should most definitely do Google search before executing any command on your system and not blindly execute codes.

I tried to check the command, but Google came up with nothing and there is nothing I can lose on this server either. If something borks up, I can easily just wipe the drive and reinstall Ubuntu server. 

That reload command does not work though, the one that does is:
```
reload transmission-daemon
```

Many thanks for your help in helping me set up transmission. Working great now.

I have an external NTFS drive connected, it is dev/sdb1, what would be the location of that drive if I wanted to download torrents onto it? I have been googling, but nothing has come up. Is it just media/external?

---

### Post by donniezazen on 2013-02-03
I am not sure what **reload transmission** does.

These commands are same and should work flawlessly. These are used to reload transmission. If you use restart then Transmission will reset your edited config.
```
sudo service transmission-daemon reload
```
```
sudo /etc/init.d/transmission-daemon reload
```

For your drive. Format it using what ever GUI you have Gparted or Windows. Then mount that drive in a folder somewhere. For example.

```
mkdir /media/usbdrive
```
```
mount /dev/sdb1 /media/usbdrive
```

You may want to add an fstab entry to make sure you load the external drive at same location every time you reboot your server.

[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by RandomP on 2013-02-04
> **donniezazen said:**
> I am not sure what **reload transmission** does.

These commands are same and should work flawlessly. These are used to reload transmission. If you use restart then Transmission will reset your edited config.
```
sudo service transmission-daemon reload
```
```
sudo /etc/init.d/transmission-daemon reload
```

For your drive. Format it using what ever GUI you have Gparted or Windows. Then mount that drive in a folder somewhere. For example.

```
mkdir /media/usbdrive
```
```
mount /dev/sdb1 /media/usbdrive
```

You may want to add an fstab entry to make sure you load the external drive at same location every time you reboot your server.

[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Thanks a bunch man. Got it running how I want it. I would mark this thread as solved, but I cannot seem to be able to edit the original post.

---

