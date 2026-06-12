---
title: "Help with server - phpMyAdmin and remote desktop access, etc"
date: 2006-08-11
forum: Server Platforms
---

### Post by zachtib on 2006-08-11
I've gotten my 64bit server set up and its been fine for webhosting, but im trying to set up some other stuff as well.

First off, remote desktop, vnc, or whatnot.

I'd like to install xubuntu-desktop, but I don't want it running all the time.  Whenever I access it, i'd like for it ask for a user/pass, like a g/k/xdm login screen, and then start a session.

phpMyAdmin

I have it installed, but I want phpMyAdmin to only be accesible from localhost, hense the remote desktop.  Esentially, the user would vnc into the box, then open a webbrowser to use phpmyadmin.

Samba server

I have this installed and have one share on /pub but was wondering if there is an easy way to set up a share of home directories that woudl require a login.  for instance, if I went to \\cervantes\home, it would ask for user/pass and show my home folder, and another user would get their folder, etc.  Not as important, sftp essentially can do this fine.

Source server

If anyone knows of any good howtos for a 64bit server, a link would be appreciated.

Cmd line torrents

exactly what it says, just a way to ssh in, start a torrent, then log out and have it continue downloading



I don't expect anyone to go into detail on any of these, just a link to a howto or a nudge in the right direction would be help enough.  I'll keep searching in the meantime

Thanks,

Zach

---

### Post by foxylad on 2006-08-12
Installing Xwindows just so you can browse PHPAdmin on localhost seems like cracking a nut with a sledgehammer - it'll work, but the disk, memory and processing power used would be very wasteful - using resources your server should be using for serving.

I'd examine the thinking that led you to this configuration - I imagine you are concerned about security with PHPAdmin, and like the convenience of a desktop. 

I'd agree with you on the first point - I'd frown on exposing PHPAdmin to the internet because it is difficult to limit password attempts to a web application, and if someone does crack your password they get full access to your server. But you may be able to lock down PHPAdmin so it is only exposed to your machine - you need a fixed IP address for this. If you don't have a fixed IP address, Google for PHPAdmin security measures you can apply - many smart people have this problem, and I'm sure there are a number of good solutions. This will give you a GUI without the expense of XWindows.

Or you could do what most server admins do - learn the command line interface (shock horror!). It really isn't that difficult, and you will find that most operations you want to do on the server are described with the CLI anyway - I've never seen instructions for setting the initial mysql admin password described using a GUI, for instance - it's always "Use mysqladmin...".

I've just installed a new 64-bit server, and the good news is that Ubuntu makes it exactly the same as a 32-bit server. I can't think of a single thing I've done differently because it is 64-bit. So you shouldn't really need a 64-bit resource, unless you are a developer writing applications the depend heavily on 64-bit features.

Finally CLI bit-torrent clients - never used them, but there are plenty around. Google is your friend.

---

### Post by zachtib on 2006-08-14
> **foxylad said:**
> Installing Xwindows just so you can browse PHPAdmin on localhost seems like cracking a nut with a sledgehammer - it'll work, but the disk, memory and processing power used would be very wasteful - using resources your server should be using for serving.

I'd examine the thinking that led you to this configuration - I imagine you are concerned about security with PHPAdmin, and like the convenience of a desktop. 

I'd agree with you on the first point - I'd frown on exposing PHPAdmin to the internet because it is difficult to limit password attempts to a web application, and if someone does crack your password they get full access to your server. But you may be able to lock down PHPAdmin so it is only exposed to your machine - you need a fixed IP address for this. If you don't have a fixed IP address, Google for PHPAdmin security measures you can apply - many smart people have this problem, and I'm sure there are a number of good solutions. This will give you a GUI without the expense of XWindows.

Or you could do what most server admins do - learn the command line interface (shock horror!). It really isn't that difficult, and you will find that most operations you want to do on the server are described with the CLI anyway - I've never seen instructions for setting the initial mysql admin password described using a GUI, for instance - it's always "Use mysqladmin...".

I've just installed a new 64-bit server, and the good news is that Ubuntu makes it exactly the same as a 32-bit server. I can't think of a single thing I've done differently because it is 64-bit. So you shouldn't really need a 64-bit resource, unless you are a developer writing applications the depend heavily on 64-bit features.

Finally CLI bit-torrent clients - never used them, but there are plenty around. Google is your friend.

Yes, google is great, but I like to go for recommendations before I go poking around.  Also, I would consider myself very proficient at using the command line in linux, and have elinks set up, but for the way phpadmin works, i'd like a GUI for it, which is why I don't want the session to continue, I only want it running X while I'm logged into it, thus not wasting resources all the time.  Can phpMyAdmin be used over the command line?

(btw, after being up for many months, i realized that on my old server, all one had to do was tack /phpMyAdmin/ on the end of the url and they would access the admin panel without need for a user/pass.... oops, hence im a little worried about security this time around.)

My server does of course have a static IP address, but perhaps rather than only allowing from localhost, only allow connections from other computers at my house...

---

