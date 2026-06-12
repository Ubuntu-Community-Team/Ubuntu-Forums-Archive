---
title: "svn server"
date: 2008-06-12
forum: Server Platforms
---

### Post by KingTermite on 2008-06-12
Hi all. I hope this is the best sub-forum for this..it was hard trying to determine what sub-forum would fit best.


I am not a sys-admin, I'm a software developer. I have been asked to set up an svn server as a pilot to determine if we might want to switch from Microsoft Vss to SVN.

I will be getting a dedicated PC for it hopefully.

Specs:

Plan is to host source code files on Linux box with SVN and used by clients on the Windows side.

Hosting source code, for now only 2 medium-large sized projects (probably 350-500 source files total).

Will probably serve about 5-10 users right now (some local, some in Europe). 

If we end up switching to SVN, we're looking at about 20-30 projects (about 10-12 active) and about 20-30 users (probably only 10-15 active regularly).

1st Q:
What *buntu?

I've only used Ubuntu desktop at home (and a relative newbie at that).

Do I need to get the server version or will desktop work fine?

If desktop is ok, the server will likely not need to be accessed often, so should I use Xubuntu as its more lightweight? I'm ok with doing it one way now as it won't serve too heavy of a load, and then doing something "hardier" later if we decide to use it.


Lastly (and most importantly)
Are there any good tutorials for setting this up? 

Are there any things that are unique to serving on Linux and clients being on Windows?

Any help/advice is appreciated.

---

### Post by PacketCollision on 2008-06-12
Hello, and welcome to the world of Ubuntu server admin.

The standard way to use SVN is to have it served by the Apache webserver.  Any machine built in the last few years should be totally fine any normal svn access.

As far as using server vs. desktop, there is no reason why you can't use a desktop variant of Ubuntu for your server, but the X-Windows system is unnecessary bloat if your're not going to be using it as a workstation.  Personally, I would recommend using server and just following the instructions in the tutorials below, but if you are more comfortable with one of the desktop flavors, it really won't be a performance hit unless you're doing *really* taxing things on the box.

There are no issues with running the SVN server on a Linux box and having Windows clients.  If you have Linux *clients* however, be careful about line returns.  SVN migh take care of this automagically though.

Try one of these tutorials:
[http://ubuntuforums.org/showthread.php?t=51753](http://ubuntuforums.org/showthread.php?t=51753)
[http://www.howtogeek.com/howto/ubuntu/install-subversion-with-web-access-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-subversion-with-web-access-on-ubuntu/)

Good luck!

---

### Post by KingTermite on 2008-06-12
Thanks for the input.

For now, I think I'm going with normal Ubuntu desktop as its what I know and doesn't sound like it will be a serious performance hit (didn't expect it to be). If we do use it full-time in the future and I deem otherwise then, I can consider other options.


Any good tutorials for installing that anyone can point me to?

---

