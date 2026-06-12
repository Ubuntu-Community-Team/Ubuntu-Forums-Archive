---
title: "Home Use Server Ideas Please"
date: 2007-06-14
forum: Server Platforms
---

### Post by quietas on 2007-06-14
I'm setting up a server with an extra P3 800 I have sitting around gathering dust. It will be specifically for home use file storage currently, I have a Dlink router handling the DHCP, firewall, and whatnot. I've been gathering huge amounts (500+gb) of files on my desktop and the drives are getting a bit full. I want to get them off and more accessible on a dedicated machine.

I've basically had it running a Samba server on Ubuntu 6.10 a while. It sits there with a 500gb and 250gb drive serving up files and that's it. Basically a NAS device that sucks more power. The connecting client computers are a Vista desktop, XP Pro desktop, XP Pro Laptop, XP Home Laptop, Ubuntu 7.04 laptop, and whatever friends bring over (Mac & XP mainly).

I don't really need to do more ISP type function since my webpage/email/domain are hosted by 3rd party services, but I want to maximize my capabilities at home. It'll be headless with a few 250-500gb drives in it, not mass power, but enough I think.

Current usage ideas:
[LIST]
[*]File storage based on user/pass
[*]Network storage that is open to all
[*]Music storage writable by specific users, readable to all
[*]Firefly Itunes compatible server for that music (mt-daapd)
[*]Movie file and DVD image storage, sharable via mt-daapd also?
[*]Backup of each computer, specific directories per user
[/LIST]

What else can/should I do? Also what is going to be the easiest way to do so?

Recently I saw the new Windows Home Server and it seems to fit the bill exactly, but I boycott MS as much as possible, plus I can't use it on my own hardware once the beta time is over. At least according to current propaganda. UbuntuHomeServer has a project that just started, but I don't see a lot of activity yet. I like the idea, but I'll put something in place while that project evolves.

---

### Post by nutz on 2007-06-14
you could load waste on it and use it for file sharing and secure messaging

---

### Post by nutz on 2007-06-14
[http://waste.sourceforge.net/](http://waste.sourceforge.net/)

---

### Post by Chayak on 2007-06-14
You could always put IMAP or POP on it and use getmail4 (I prefer because of ssh options) to download all your email to your home server and connect to that from within your own network.  I have a number of accounts and it's handy to have the server get all of them and I only have to connect to my account on it to get them.  Then as you get more advanced you can add anti-spam and even OCR anti-spam.

---

### Post by BLTicklemonster on 2007-06-14
It is my desire to have an Ubuntu box on my network solely for the purpose of storing music and files.


But I have never gotten to where I could share a folder with a windows machine without a password. I have no need for security here on this network, and I'm not about to go setting up a shared machine that people have to enter passwords just to make a playlist and listen to music.

Good luck.

---

