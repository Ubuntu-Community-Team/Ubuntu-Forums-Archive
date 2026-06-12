---
title: "Switching from FREENAS to ubuntu server"
date: 2010-06-20
forum: Server Platforms
---

### Post by nman729 on 2010-06-20
So, I've been using freenas for the passed few months and it has been  GREAT. But I cant seem to get the PS3 media server working. So I want to  try out Ubuntu server. However, I would like to see if there is anyone  else in the same boat who has tried both, can you give me some feedback?

Basically  there are only a few things I need to do with it
1. Web UI - this is  essential because there is no head on it
2. Transmission bit torrent
3.  NUT or the ability to be compatable with my ups unit
4. SSH
5.  Samba, ability to share the drive with windows machines
6. Software  raid
7. PS3 media server

---

### Post by nman729 on 2010-06-27
Bump?

---

### Post by garfonzo on 2010-06-27
> **nman729 said:**
> So, I've been using freenas for the passed few months and it has been  GREAT. But I cant seem to get the PS3 media server working. So I want to  try out Ubuntu server. However, I would like to see if there is anyone  else in the same boat who has tried both, can you give me some feedback?

Basically  there are only a few things I need to do with it
1. Web UI - this is  essential because there is no head on it
2. Transmission bit torrent
3.  NUT or the ability to be compatable with my ups unit
4. SSH
5.  Samba, ability to share the drive with windows machines
6. Software  raid
7. PS3 media server

I also started with FreeNAS but had to give it up because I was having difficulty with the Web GUI. I moved to Ubuntu Server and am very glad I did. I don't have all the same needs as you, but I'll speak to the ones I can. My Ubuntu Server is headless and sits in the garage connected to my LAN.

1) Webmin is a package you can install onto your Ubuntu server which will allow a web interface for all administrative tasks. I use it, but I actually started with only a command line interface through an SSH window via Putty. 
2) Never used it, but I've heard of people using it with success.
3) I have an APC UPS which works well. I think that most (if not all) APC products work with the apc package (I can't remember the name, but I set it up and it works). 
4) Installed be default I think. I login via a Putty session on my Vista box. 
5) My Ubuntu server shares with 3 WinXP boxes and my Vista machine. All through Samba and all set up as network drives on the respective windows machine. It was a bit tricky to set up (for me) but now that it works, its great. 
6) Never did this. I was going to for back ups, but went with Rsync instead which works great. 
7) Never used.

Hope this helps somewhat.

---

