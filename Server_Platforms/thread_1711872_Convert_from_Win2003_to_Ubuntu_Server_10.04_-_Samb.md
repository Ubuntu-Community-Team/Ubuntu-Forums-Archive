---
title: "Convert from Win2003 to Ubuntu Server 10.04 - Samba questions"
date: 2011-03-21
forum: Server Platforms
---

### Post by GiSWiG on 2011-03-21
I know, I know. Question is probably here somewhere, but you try searching these forums and Google for something samba security...

I have a Win2003 server for my home network and looking to switching Ubuntu. Currently my main share is one Public folder and in there I have Photos, Music and Videos. Here's how security is setup. 

5 users, me, wife, son daughter and media center user 'couchpotato' (perfect isn't it). So here's the current layout with security (no groups)...

> Public - me, wife full access - son, daughter, couchpotato read access (would love if there is a way to setup so they can only see these below when in Public)
___> Music - me, wife - full - son, daughter, couchpotato read only with some folder not accessible (lyrics) 
___> Pictues - same as music
___> Videos - same as music
_> all other files/folders - me, wife full, son, daughter, couchpotato read access

What I would like
> Public - me, wife full, rest unviewable except...
___> Music - me,wife - full; rest viewable
___> Pictures - me,wife - full; rest viewable
___> Videos - me,wife - full; rest viewable

So except me,wife, everyone only sees Music, Pictures, Videos when going into the Public share. I don't want to create separate shares for Music, Pictures, Videos as I have enough drive letters-to-shares in Windows. Eventually, Media Center goes mythTV and my PC goes linux (laptops are already using LinuxMint)

So I can see, on the file system directly, this would require permissions with two groups (or multiple users) and probably involving ACLs (will figure that one out.)

How would I set this up in smb.conf?
If you have links to this info, that would be great too unless you can spit it out fast.

Thanks

---

### Post by wongo888 on 2011-03-22
So if your Win2003 set up is working, why wouldn't you just use that? More time to spend with the family.

---

### Post by GiSWiG on 2011-03-22
If you must know, my wife works nights, kids are in bed at 8:30p so I got time from there till about 11-12. It's also a learning experience to improve my skills. I also want to squeeze more performance out of it. I host a Minecraft server for me and a few friends and on an identical machine with Ubuntu, I get less lag. I've tried lots of tweaks, but no go. And it's my VPN server. 

Otherwise, (not to be mean) I'm looking for answers to my questions, not why I'm doing it.

---

### Post by GiSWiG on 2011-03-23
To narrow it down, I'm going to have to use ACLs on the file structure. Is there anyway to have samba use that? No group/user parms and if possible, no need for 'smbpassword -a USER'?

---

