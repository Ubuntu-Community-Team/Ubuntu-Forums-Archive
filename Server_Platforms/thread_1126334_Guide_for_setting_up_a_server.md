---
title: "Guide for setting up a server?"
date: 2009-04-15
forum: Server Platforms
---

### Post by NobleRooster on 2009-04-15
Hello all, I recently realized I have an old gateway desktop lying around and thought it would be pretty awesome if I could set it up as my own personal server.

The truth is though, I have no idea how to go about doing this.  I know Ubuntu has a server version, but is the Ubuntu server user friendly and easy to use?  Also, it's kind of an older desktop and maybe has like a 1+ GHz processor in it, will this run alright as a simple, small, personal server?  Is there other versions of Linux server software I should dwell into instead of Ubuntu?

Thanks,
-Justin B.

---

### Post by dmizer on 2009-04-15
Well, what kind of server? Your computer should be capable of hosting a variety of services including but not limited to:

SSH server
File server
Media server
Mail server
VPN server
HTTP server

What do you want to do? Once you know that, then it's easy to find tutorials.

---

### Post by HighCommander540 on 2009-04-15
Not only that, but Ubuntu server edition is built to automate installation of the types of servers that dmzier listed above. All you have to do is pop in the disk and follow the on-screen instructions and Ubuntu will set it all up for you.

---

### Post by daboroe on 2009-04-15
@NobleRooster: If you give me some time I might be able to write a guide for you on how to set up the services that dmizer stated. Those servcices should not cause you alot of usage unless you have loads of users connecting and using it.

---

### Post by ugm6hr on 2009-04-15
Look for ideas here: [http://lifehacker.com/5162026/best-home-server-software](http://lifehacker.com/5162026/best-home-server-software)

I'm sure the comments have plenty of options outside the top 5.

I recommend FreeNAS for home server use, unless you need a print server or want an internal calendar server.

Check out the link in my signature (FreeNAS Home Server) if you want.

---

### Post by NobleRooster on 2009-04-15
I'm really wanting one that I could maybe host a personal small, very little traffic, website off of and have somewhere to host just random media that I may have.  I really don't know much about them, like what all it takes, but I've always heard that servers with Linux are good.

---

### Post by hictio on 2009-04-15
I'd say the very first thing you should do is reading this [Ubuntu Server Guide](https://help.ubuntu.com/8.10/serverguide/C/)

And then, here are just a couple of ideas:

- [How to Setup a Dedicated Web Server for Free](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)
- [Enhancing Your Ubuntu Server](http://net.tutsplus.com/tutorials/other/enhancing-your-ubuntu-server/)
- [Ubuntu neub: Cool stuff to do with a home server?](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/529007966931?r=529007966931#529007966931)

---

### Post by ugm6hr on 2009-04-16
> **NobleRooster said:**
> I'm really wanting one that I could maybe host a personal small, very little traffic, website off of and have somewhere to host just random media that I may have.  I really don't know much about them, like what all it takes, but I've always heard that servers with Linux are good.

FreeNAS would do this, as long as the personal website does not require anything special other than PHP.  It isn't designed to be used with databases, so most content management systems, wiki software and blogging software (apart from pivotlog, tiddlywiki, dokuwiki and lion wiki and perhaps others) won't work.  As long as your router can forward ports, this should be no problem (which also applies to any Linux server).

Its media hosting functions are excellent, and easy to use.  In fact, this is one of its primary designed purposes.  It has FUPPES UPnP media server built-in, if you want to serve media to XBOX 360 / PS3, but can also easily share using SMB (Windows sharing) without any need to manually configure any settings (i.e. no more difficult than in Windows).

It is based on FreeBSD rather than Linux, which is another open source UNIX-based OS.  Its main benefits are: it is very small and lightweight (requires 96-128MB RAM only); it can be installed on a portable USB drive; it does not require any UNIX / BSD knowledge at all to use; all the functions it has can be accessed directly from a web browser on any networked PC.  The downside is that if you decide you want more features in the future, it is not readily expansible, unlike a full-blown Linux "distro" (i.e. version) like Ubuntu or Mandriva (or even FreeBSD itself).

If your computer boots from USB, and you have a spare USB stick (128MB-2GB), give it a try.  It will only take a few minutes to set up, and that should be long enough to decide if you can use it or not.

---

### Post by Funkydonut5000 on 2009-04-16
I found myself asking this very question when I first made the linux leap from Windows.  Hell, I'm still leaping.  I've only been using ubuntu for a month and I've enjoyed every second (even the extremely frustrating ones).

I would recommend getting your feet wet with a simple file share using ubuntu Desktop and Samba.  That way you can use a combination of GUI and terminal to ease the Windows withdraw.  There's plenty of file sharing How To's that community members were nice enough to contribute.  This one broke it down real nice for me.  I picked it up while I was using MINT before I switched to ubuntu.  The principles are the same.

[http://www.kwdesign-consulting.com/feedback-dl.html](http://www.kwdesign-consulting.com/feedback-dl.html)

Hope it helps.  And read the new user guide.  Great stuff.

---

### Post by NobleRooster on 2009-04-17
> **ugm6hr said:**
> FreeNAS would do this, as long as the personal website does not require anything special other than PHP.  It isn't designed to be used with databases, so most content management systems, wiki software and blogging software (apart from pivotlog, tiddlywiki, dokuwiki and lion wiki and perhaps others) won't work.  As long as your router can forward ports, this should be no problem (which also applies to any Linux server).

Its media hosting functions are excellent, and easy to use.  In fact, this is one of its primary designed purposes.  It has FUPPES UPnP media server built-in, if you want to serve media to XBOX 360 / PS3, but can also easily share using SMB (Windows sharing) without any need to manually configure any settings (i.e. no more difficult than in Windows).

It is based on FreeBSD rather than Linux, which is another open source UNIX-based OS.  Its main benefits are: it is very small and lightweight (requires 96-128MB RAM only); it can be installed on a portable USB drive; it does not require any UNIX / BSD knowledge at all to use; all the functions it has can be accessed directly from a web browser on any networked PC.  The downside is that if you decide you want more features in the future, it is not readily expansible, unlike a full-blown Linux "distro" (i.e. version) like Ubuntu or Mandriva (or even FreeBSD itself).

If your computer boots from USB, and you have a spare USB stick (128MB-2GB), give it a try.  It will only take a few minutes to set up, and that should be long enough to decide if you can use it or not.

That sounds like it may be best for me.  I was thinking of installing cutenews, which is a blogging/news software, but if I'm not mistaken it only ues PHP.  Would Ubuntu server allow me to use something like Cutenews, MoveableType, etc. as well setup a small media server?  Sorry I'm asking a lot of questions, like I said I'm just not absolutely sure about what will work and won't work yet. ;)

---

### Post by ugm6hr on 2009-04-17
> **NobleRooster said:**
> That sounds like it may be best for me.  I was thinking of installing cutenews, which is a blogging/news software, but if I'm not mistaken it only ues PHP.  Would Ubuntu server allow me to use something like Cutenews, MoveableType, etc. as well setup a small media server?  Sorry I'm asking a lot of questions, like I said I'm just not absolutely sure about what will work and won't work yet. ;)

If Cutenews only requires PHP, as its website suggests, it should be OK with FreeNAS webserver.  

As for Ubuntu: Movabletype is in the repos since Intrepid ([http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=movabletype](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=movabletype)) so should be easy enough.  Perhaps the most common media server option would be mediatomb, although simple Samba sharing may be good enough for you.

Essentially, it is difficult to envisage any home server function that couldn't be accomplished by Ubuntu, although it will require a bit of learning.  FreeNAS, on the other hand, is much simpler to use (i.e. essentially no learning curve required), but far more limited.

---

### Post by bemental on 2010-07-20
It's been mentioned elsewhere in the forums, but there is an EXCELLENT guide for server setup @ [http://woodel.com/](http://woodel.com/).

I learned a lot over the course of a few days delving in and just following the guide.

Check it out.

---

