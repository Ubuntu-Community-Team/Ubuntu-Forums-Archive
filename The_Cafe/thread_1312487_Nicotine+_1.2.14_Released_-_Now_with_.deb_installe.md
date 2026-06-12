---
title: "Nicotine+ 1.2.14 Released - Now with .deb installer!"
date: 2009-11-03
forum: The Cafe
---

### Post by OffHand on 2009-11-03
Hi guys and gals,

We have released (the source of) Nicotine+ version 1.2.14 recently , but since a few days we have a .deb installer made by one of our devs. 


[Mirror 2]("http://dl.getdropbox.com/u/291902/nicotine_1.2.14-1_i386.deb")

32bit and  64bit universal installer. Needs testing.

[Mirror]("http://dl.dropbox.com/u/291902/nicotine_1.2.14-1_all.deb") 

Enjoy! Report bugs if you find any  :popcorn:

---

### Post by Eisenwinter on 2009-11-12
I  use Arch, and have grabbed the svn version of Nicotine+ (1.2.15svn) from the AUR.

When I download entire folders, it downloads the files into my big /Music directory, not into /Music/album_name_folder/. Why is this?

I looked at the "Downloads" settings, and found no option which may be used to configure that.

It does point to download to /Music, which is what I've always used, since it's my music directory. Maybe this is the problem?

I can still "mv file* /albumdir", or something, but it'll be more comfortable if Nicotine already downloaded all the files into that album.

---

### Post by BrMBr on 2009-11-12
Great news!

I wonder where the x86_64 .deb is... :sad:

---

### Post by OffHand on 2009-11-12
> **Eisenwinter said:**
> I  use Arch, and have grabbed the svn version of Nicotine+ (1.2.15svn) from the AUR.

When I download entire folders, it downloads the files into my big /Music directory, not into /Music/album_name_folder/. Why is this?

I looked at the "Downloads" settings, and found no option which may be used to configure that.

It does point to download to /Music, which is what I've always used, since it's my music directory. Maybe this is the problem?

I can still "mv file* /albumdir", or something, but it'll be more comfortable if Nicotine already downloaded all the files into that album.

Please file a bug report [here]("http://www.nicotine-plus.org/newticket")

---

### Post by OffHand on 2009-11-12
> **BrMBr said:**
> Great news!

I wonder where the x86_64 .deb is... :sad:

You can probably use the deb on a 64bit OS as well  ;)

---

### Post by BrMBr on 2009-11-12
> **OffHand said:**
> You can probably use the deb on a 64bit OS as well  ;)

No, I can't. :(

[IMG]http://i36.tinypic.com/33cmdcg.png[/IMG]

---

### Post by Eisenwinter on 2009-11-12
> **OffHand said:**
> Please file a bug report [here]("http://www.nicotine-plus.org/newticket")
I have just found out this isn't a bug. Nicotine+ acts as it should.

See, I have both Incomplete Downloads and Complete Downloads folders set to my /Music partition.

This results in the files being downloaded to /Music separately, as they are incomplete.

Once a file download has been completed, it is moved to the album's folder.

Previous versions of Nicotine did not act this way, which is why I was really confused at first.

Thanks for your help.

---

### Post by OffHand on 2009-11-12
> **BrMBr said:**
> No, I can't. :(

[IMG]http://i36.tinypic.com/33cmdcg.png[/IMG]

I'll ask the dev if he can make it compatible with 64bit

p.s. SVN should run just fine though.

---

### Post by OffHand on 2009-11-12
> **Eisenwinter said:**
> I have just found out this isn't a bug. Nicotine+ acts as it should.

See, I have both Incomplete Downloads and Complete Downloads folders set to my /Music partition.

This results in the files being downloaded to /Music separately, as they are incomplete.

Once a file download has been completed, it is moved to the album's folder.

Previous versions of Nicotine did not act this way, which is why I was really confused at first.

Thanks for your help.
Glad you sorted it! :popcorn:

---

### Post by BrMBr on 2009-11-12
> **OffHand said:**
> I'll ask the dev if he can make it compatible with 64bit

p.s. SVN should run just fine though.

Thanks a lot! Just lemme know :D

---

### Post by OffHand on 2009-11-12
Can anyone test this version?

I need someone with 32bit system and a 64bit system.

[Mirror]("http://dl.dropbox.com/u/291902/nicotine_1.2.14-1_all.deb")

---

### Post by BrMBr on 2009-11-12
Worked here (x86_64)!

Thanks a lot!!! :KS

---

### Post by venator260 on 2009-11-12
Not sure if anyone else is experiencing this or not, but mirror #1 downloads a 6.3K file, instead of the 1.1MB file that will actually install Nicotine+ 1.2.14

---

### Post by JoZ3 on 2009-11-25
tnx a lot, work very very fine in my ubuntu 9.10 x64 ;)

---

### Post by earthpigg on 2009-11-25
so.

what exactly is this program?

assume i know nothing about it.

because i do not.

---

### Post by Eisenwinter on 2009-11-25
It's a client for the soulseek file sharing server.

---

### Post by earthpigg on 2009-11-25
> **Eisenwinter said:**
> It's a client for the soulseek file sharing server.

soooo, assuming i was only familiar with the .torrent and lime/frostwire filesharing networks and meta-networks...

anything special or unique here?

---

### Post by Uncle Spellbinder on 2009-11-25
Anyone know if there is there a repo?

---

### Post by docus on 2009-12-12
> **earthpigg said:**
> soooo, assuming i was only familiar with the .torrent and lime/frostwire filesharing networks and meta-networks...

anything special or unique here?

Soulseek (which Nicotine+ is based on) was originally set up as a network for people to share IDM and other more obscure genres of music.  It's expanded a lot now and these days you can find all sorts on it.  It's still a fantastic place to hunt down those elusive tunes.  It's one of the first things I install.

I haven't tried Frostwire yet - I didn't want to have to install java...  Is it good?  What kind of stuff is on it?

---

### Post by Eisenwinter on 2010-01-04
I'm using version 1.2.15svn.

For some unknown reason, I am only able to "fully" connect to the OLD server (port 2240).

When I connect to the NEW server (port 2242), it says "Logging in... Logged in, getting the list of rooms...".
The rooms then appear, but that's it.

I can't do anything else. Can't join rooms, can't search files, I don't even see myself as being online in my buddy list, despite Nicotine showing my status as "Online" in the statusbar.

This only started happening around 10 hours ago. 

On the old server, I'm able to connect, get the list of rooms, search, download, see myself online in the buddy list, and so on.

There are no error messages for the new server, at all, which makes this all even more confusing.

Any idea what may be causing this?

EDIT:

Version 1.2.12 tested, the new server fails there as well.

I don't see anything on the soulseek website regarding "down time" or "server failures" or something. What could be causing this?

---

