---
title: "Server Install..6.10 or 6.06 LTS"
date: 2006-11-10
forum: Server Platforms
---

### Post by FrozenPixel on 2006-11-10
Ok first I'm confused which version to download to use as the server OS, version 6.06 LTS or the latest 6.10? Does the latest have the LAMP option?

Does it make it any less of a server if I install with the GUI's? I think I'm going to have to manage our Debian server at work and if something goes wrong I think a graphical version may be easier to manage.

Thanks

---

### Post by tuxcantfly on 2006-11-10
yes, the latest (6.10) does have a lamp option. the reason you don't want to have a gui on your servers is because they take up system resources, slowing down your server, but your server will still be functional with a gui installed, only it will be slower.

---

### Post by tuxcantfly on 2006-11-10
however, if you use a gui, you will have to manually apt-get install the server packages (mysql, apache, php), because it doesn't have them preinstalled.

---

### Post by bikeboy on 2006-11-10
You can always disable the gui for general use once it's setup, then just enable it again when you need it. Best of both worlds while you learn.

---

### Post by FrozenPixel on 2006-11-10
Oh thats cool, disabling the GUI. Thank you all.

---

### Post by aurelieng on 2006-11-11
If your server is going to be used for a long time, it's maybe wiser to go for 6.06 because of its long term support.

---

### Post by FrozenPixel on 2006-11-11
:-#

---

### Post by FrozenPixel on 2006-11-11
Yes I'm going to go download 6.06 LTS right now and if I am finding it too difficult to manage I will try 6.10 with the GUI. This is not a production server so I can screw it up, which I am sure I will.;) I just threw together an older P2 machine with a 30GB harddrive to install too, so I have to figure out the partitions I will need for the install.

I want to practice so if we have any issues with our production server at work I will at least have some sort of clue rather than just tell my boss "your guess is as good as mine".

Thanks all.

---

### Post by FrozenPixel on 2006-11-11
So I successfully installed the LAMP 6.06 LTS installation and everything seemed to work well, no hiccups.

Couple of questions before I go read the guide, is there a user named 'root'? If so is that account automatically secured. It did have me create an account for myself and I was able to login and actually run the shutdown command properly.

When you install for the first time with an internet connection does it automatically update everything or do I need to update it?

And is there anything else I should be aware of? I'm going to hook it up to a hub, standalone system, set up DHCP and try to go through the steps of creating a Windows user and actually connect to the server with the users own space, sort of a mock up of our work network. I think that will be my best way to learn how to setup a server and have users connect.

---

### Post by bikeboy on 2006-11-11
The root user is disabled by default in Ubuntu. To execute a command that you would normally need root for, use "sudo" before the command. Or "sudo -s" to get a root shell. In both cases the password of the first user you created will be prompted for.

In the gui, you are usually asked for your password when it's needed. If you want to edit a text file as root using the gui the quickest way is to use ```
gksudo gedit /path/to/file
```

More info in the wiki:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by FrozenPixel on 2006-11-12
Thank you bikeboy.

---

