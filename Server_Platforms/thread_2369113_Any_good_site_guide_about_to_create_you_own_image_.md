---
title: "Any good site guide about to create you own image share site?"
date: 2017-08-18
forum: Server Platforms
---

### Post by cazz on 2017-08-18
Hi
Right now I have a forum that I have some members to share funny stuff and information.
But lately we start to use a close Facebook group and it works great too.

But I still like to have some place so I can easy upload images to easy share on the facebook (I like to control my own pictures)
But also let my friends create a account to easy upload image to show to us.

I have look at some free but it feel they are too sophisticated to use. I just want to create a account, upload image, share the image address to friends.

is ok if it can resize the image but that all. I don't need so much more.

So is that any good system I can use that also have a easy step by step guide how to install and use?

---

### Post by LHammonds on 2017-08-18
I'm guessing you fell pray to the photobucket problem too in regards to sharing images via embedded links.

I setup a MediaGoblin site for that very reason...I like to host my own images, video, ascii art, 3D models, etc.

Here is a step-by-step guide on how to install [MediaGoblin on Ubuntu Server](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=223).  Whether you consider it "easy" or not depends on your skill level with Ubuntu command line.  However, I did work out the necessary steps to get 'er working.

LHammonds

---

### Post by cazz on 2017-08-18
ohh it looks nice, thanks for the guide.
well when I mean "easy" I mean easy to use the system
I almost always use terminal when I work with linux.

---

### Post by mastablasta on 2017-08-21
what you describe can be achieved nicely using owncloud or nextcloud.

if you want to specialise the site in media (e.g. only for pics and videos) then Piwigo gallery is also an option.

all of these are relatively easy to install and maintain (administer). good documentation & guides are also available.

another option is seafile, but i am not sure how good their pcitures support is.

i use owncloud for sharing pictures with close familly. occasionally i want to show certain pics to someone else, and i would give them the link i then set to expire in a week or so. ther eis no reason for continued access to non users.

---

### Post by TheFu on 2017-08-21
Nextcloud has a gallery addon that works well, if the bandwidth available matches the resolution of the photos.  Outside my LAN, I find it a little slow with full-sized images. I do not trust nextcloud enough to make it available on the internet without a VPN required. Plus, the last nextcloud update was painful - it forced a manual change in the DBMS characterset used.  All prior updates have been handled through the web interface, so this one was a big deal.

If you want a client-side way to securely share files, photos, chat, and a little email system, then look at RetroShare. Everyone has to load the program on their machine, follow a wizard to setup their PKI and share those keys within the group.  Then people join a group and RestroShare handles all the encryption between the different end points.  At least 1 person in the group needs to open a router port for inbound use.  RetroShare is for groups that want a little more security AND control over who can join and who can share without an overload having control outside the group.  I've only played with it a little, so don't take this as a raving endorsement. The main person would need to run it on a desktop/server, not a laptop.  [http://retroshare.net/](http://retroshare.net/)

Honestly, I use an old Perl CGI script for my public photo gallery that has been modified and extended over the years. Unfortunately, it doesn't work with IE, or at least it didn't last time I tried, but that was long ago.

If I were setting things up again and using an external VPS for the site, I'd use nextcloud.  If hosting on my own network, well, I'd mandate a VPN with individual certs and use Nextcloud.

---

### Post by cazz on 2017-08-21
Thanks for the all replay

I do use Nextcloud on another server but was thinking just to use it for my personal use.
I have try a little with chevereto that have a free version and got it to work, going to use it a little now to see how good it is.

---

