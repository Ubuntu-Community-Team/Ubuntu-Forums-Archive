---
title: "Home Media Linux Server"
date: 2011-11-24
forum: Server Platforms
---

### Post by XBMC old School on 2011-11-24
Hey all,

I'm going to replace my desktop next year and was contemplating throwing my old tower into my crawl space as a 

1) fast headless media server 
2) larger family (extended) as a backup accessed using DDNS.
3) print and scantool server
4)Maybe Network Security
5) maybe mail server
*assuming mixed PCs on network linux/unix, Mac & Win

How do i start? I'm assuming ubuntu server minimal based. Any tips from beginner users that just configured one? Guides, tips and tuts? Are there and **Don'ts**?

---

### Post by Lars Noodén on 2011-11-24
Look at SSH for headless operation.

For file sharing look at SSHFS or [Samba](https://help.ubuntu.com/community/Samba).

For a print server look at CUPS.

---

### Post by littlegreiger on 2011-11-24
For media server duties it depends on what kind of clients you're going to be serving (pcs, tvs, game consoles, etc.) and what kind of media. 

**Video**

For Windows pcs you can just share out the folders via samba and that should do it for, use NFS for Mac/Linux pcs.

For newer tvs or other upnp clients I'd check out [MiniDLNA]("http://sourceforge.net/projects/minidlna/"), I'm currently using it to stream to my Samsung TV. The only downside with it is it doesn't transcode your files so you have check your specific player for file format compatibility. Another upnp client that I've used in the past that supports transcoding is [MediaTomb]("http://mediatomb.cc/"). If you have a larger media collection you'll want to put the database into MySQL instead of the standard SQLite one.

For game consoles I only have experience with the XBox 360 and Playstation 3. For the XBox I found that Mediatomb works the best and for the PS3 I've used [PS3 media server]("http://ps3mediaserver.blogspot.com/") and have no big complaints about it.

**Music**

I haven't really played with audio streaming that much as I just share out my music folder via Samba and play it with native clients on my pcs. However, some to look at are [Subsonic]("http://www.subsonic.org/pages/index.jsp"), [Ampache]("http://ampache.org/") and [Jinzora]("http://en.jinzora.com/").

And I second using SSH for headless control and Samba for local file sharing.

---

### Post by XBMC old School on 2011-11-24
Server hosting requirements:
 
1) An XBMC PC at my TV so filesharing is sufficient. 
 
2) An Xbox360 so i would like to share a music library for gaming. i have about 5TB of storage so having a select library for game play is fine.
 
3) A Windows laptop
 
5) And possibly facilitate smartphones as backups or mailservers or whatever features i can do with the server.
 
6) And again, a friend of mine has a Netgear (w/ tomato router) that uses DDNS to setup internet accessible shares.
 
My server hardware specs are listed in my signature

---

### Post by littlegreiger on 2011-11-24
Here's my 2 cents about your requirements

1) Filesharing via Samba will work.

2) If you only want to share a small audio library I'd just use MiniDLNA, I forgot it could do audio as well and it's extremely simple to setup.

3) What do you want to do in regards to the windows laptop? Back it up? Just access files from the server?

5) I only have experience with android smartphones and don't really interface it much besides using [ConnectBot]("https://market.android.com/details?id=org.connectbot&hl=en") for SSH access. I guess you could use a Samba share as a target for backups. I don't really have any experience with mailservers so I can't speak to that. 

6) To setup DDNS I would recommend doing it on your router. Most newer commercial routers offer dynamic DNS as an option and it is straight forward to setup. Then you'd have to forward ports to your server for your shares to be accessible. I would, however, advise against opening your Samba shares to the internet. I'd recommend looking at things like SSHFS as Lars mentioned or tunnelling SAMBA over SSH, which is a real pain. Or you could use SFTP or SCP if you're comfortable with those.

---

### Post by XBMC old School on 2011-11-24
Maybe Headless is the wrong term. I mean remote desktop accessible. 

Is having all these different types of sharing functions conflicting? 

I guess i would like to start with a minimal install of ubuntu / gentoo. Is that sensible? I would like to have everything none essential stripped out of it. Or am i setting myself up for problems?

---

### Post by Lars Noodén on 2011-11-25
> **XBMC old School said:**
> I guess i would like to start with a minimal install of ubuntu / gentoo. Is that sensible? I would like to have everything none essential stripped out of it. Or am i setting myself up for problems?
That's the right way to do it.  You can get their by either using the server version or else get the alternate CD and choose to install a "Command Line System".

---

