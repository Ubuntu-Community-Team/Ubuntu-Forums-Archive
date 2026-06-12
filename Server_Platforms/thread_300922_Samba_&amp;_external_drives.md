---
title: "Samba &amp; external drives"
date: 2006-11-16
forum: Server Platforms
---

### Post by riverman on 2006-11-16
I have a Western Digital MyBook 250gb usb drive plugged into my Ubuntu file server. The drive is mounted on a sub-directory of my home folder, and accessed through Samba from my laptop. I've found that my laptop only shows 2.6gb free for the Samba share, which is the free space on my internal hard disk, not on the MyBook. Can anyone explain why this might be, and help me to get access to my whole MyBook via Samba?

My /etc/samba/smb.conf file is, shall we say, 'rudimentary' and pretty much copied from an example I found online, but it doesn't need to be complicated as this is a private, home network. The relevant sections are:

[global]
workgroup = MSHOME
security = share
encrypt passwords = true
passdb backend = tdbsam

...

[mybook]
path = /home/james/mybook
comment = MyBook private
read only = no
guest ok = no
force user = james
force group = james

Thanks :)

---

### Post by riverman on 2006-11-16
Actually, I should say that I think I've fixed this. It seems that the problem only happened when I accessed my MyBook from a samba share on a higher level (I have a samba share on my home folder, and going into that and *then* into my MyBook caused the problem). Accessing the MyBook share directly seems to work just fine, with a full 200-odd gbs free :) Apologies for the valuable forum space taken up :)

Just to sum up, then, the problem occured in the following case:

share [home]
path = /home/james

MyBook mounted on /home/james/mybook, but that directory appeared not to have much space in it when view through share [home].

However, accessing the MyBook mountpoint directly on share [mybook] (path = /home/james/mybook) showed the full free space on the MyBook drive.

Not sure why this is as it is, so if anyone could enlighten me I'd be most grateful.

---

