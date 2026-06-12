---
title: "Music"
date: 2008-02-17
forum: Server Platforms
---

### Post by Holmes89 on 2008-02-17
Is there a way that I can host my music on a server and then access it through iTunes? I specifically want it to be iTunes because I like the player and I want to get a macbook in the future. I have a bunch of music I want to migrate, is there a way I can have my server host this music and iTunes think it's shared music?

---

### Post by gfg on 2008-02-17
Any mediaplayer supporting  DAAP should be able to do this. I'm not very familiar with all the available mediaplayers, but I know for sure that Rhythmbox support this.

---

### Post by lluisanunez on 2008-02-17
I do this with FrostWire --a Java based P2P program. There may be other solutions, though...

---

### Post by faulkes on 2008-02-17
This really isn't a server issue IMO.

However, AFAIK, you would need to setup a shared drive (via samba) and then share that with the network, such that any other pc/laptop/macbook etc.. could see the files.

Faulkes

---

### Post by StooJ on 2008-02-17
> **faulkes said:**
> This really isn't a server issue IMO.

However, AFAIK, you would need to setup a shared drive (via samba) and then share that with the network, such that any other pc/laptop/macbook etc.. could see the files.

Faulkes

I use an Xubuntu server as a file & media server, so I'd be interested in unifying things as well.

The problem with merely sharing music via Samba is that each media library has to be updated every time I add music to the server, and across each OS (and each music programme installed on each OS)

With a triple boot (Ubunutu, XP & Vista) running Amarok, Exaile, Winamp & iTunes, it becomes a bit of a pest to keep all the libraries current.
Add a second PC and a laptop...

A shared SAMBA drive coupled with a single media library database hosted on a music server would be an ideal solution for me, and I'm pretty sure there are plenty of others who would appreciate the same thing.

Since I'm using a server to share my music across the network, a daemon programme would be favourite, rather than something running on top of X.

---

### Post by Holmes89 on 2008-02-17
Is there anything that will allow me to connect over a long distance? i.e. outside my home network? I have a static IP address so can I do that?

---

### Post by empthollow on 2008-02-17
The most commonly used service for that is ftp.  I recommend vsftpd.

---

### Post by faulkes on 2008-02-17
> **StooJ said:**
> I use an Xubuntu server as a file & media server, so I'd be interested in unifying things as well.

The problem with merely sharing music via Samba is that each media library has to be updated every time I add music to the server, and across each OS (and each music programme installed on each OS)

With a triple boot (Ubunutu, XP & Vista) running Amarok, Exaile, Winamp & iTunes, it becomes a bit of a pest to keep all the libraries current.
Add a second PC and a laptop...

A shared SAMBA drive coupled with a single media library database hosted on a music server would be an ideal solution for me, and I'm pretty sure there are plenty of others who would appreciate the same thing.

Since I'm using a server to share my music across the network, a daemon programme would be favourite, rather than something running on top of X.

This is more directly related to a server, the OP's question revolved mainly around iTunes.

Currently, I'm not aware of any daemon which would be able to feed/update multiple applications across multiple OS's on an automatic basis.  I.e. you start iTunes and it automatically gets a new list of added media to it's library.

I agree completely that having to update numerous applications with new media additions would be very tedious.  The only thing I can think of would be to standardize the application you use on each client, such as using VLC.

Faulkes

---

### Post by Holmes89 on 2008-02-17
I guess I'm not making it clear about what I need. I don't want to waste all of my hard drive space on my laptop on audiobooks and the like. So I wanted a centralized location that I could connect iTunes with (because that is my preferred media player) so I don't think an FTP is what I'm looking for. Does that make sense?

---

### Post by Holmes89 on 2008-02-17
I found this: [http://onlyubuntu.blogspot.com/2008/01/howto-setup-itunes-compatible-media.html](http://onlyubuntu.blogspot.com/2008/01/howto-setup-itunes-compatible-media.html)
do you think I could set this up so I can access it from anywhere?

---

### Post by StooJ on 2008-02-17
Faulkes is on the money, Holmes.

When storing your music in a central place, the first thing to do is make sure clients (your other computers) can see the files.
In a cross-platform environment, your best bet is to share the server's music folder with SAMBA.
You'll find a great guide to setting that up here:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Next, media programmes seem to like files that appear to be locally stored, so you should mount your Samba share as a mapped network drive on the other machines. I'll need to check how to do this in OS X (can't remember off the top of my head) but it's easy in Windows (My computer -> Tools menu -> Map Network Drive ) and just involves editing fstab in ubuntu.
Automatically mounting SMB shares in linux on startup:
[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

Once you have mounted or mapped your network drives, you'll be able to point itunes directly to the shared folder, and it will treat the songs like local media.

For accessing media remotely, I came across this on some google travels today.
[http://www.simplifymedia.com/](http://www.simplifymedia.com/)
 There is an alpha linux version available, but I've not tried it.

> **faulkes said:**
> 
I agree completely that having to update numerous applications with new media additions would be very tedious.  The only thing I can think of would be to standardize the application you use on each client, such as using VLC.
Faulkes

That would be the best idea, but my flatmates use & abuse the media library too, and have their own favourite clients :(
I will keep searching.

Edit: Firefly looks very interesting though!

---

### Post by IcarusR on 2008-02-17
> **Holmes89 said:**
> I found this: [http://onlyubuntu.blogspot.com/2008/01/howto-setup-itunes-compatible-media.html](http://onlyubuntu.blogspot.com/2008/01/howto-setup-itunes-compatible-media.html)
do you think I could set this up so I can access it from anywhere?

Holmen89 this should work. I have a Squeeze Box connected to my stereo which inturn connects to my server which has Slimserver installed (very similar to mt-daapd). 

mt-daapd is now known as firefly, check the forums at [http://forums.fireflymediaserver.org/]("http://forums.fireflymediaserver.org/")
there is quite a lot of info about firefly & iTunes. If you want further info why not join & ask on that forum.

Icarus

---

### Post by Holmes89 on 2008-02-17
Okay I might do that actually, it does seem like the best idea. I did however post something in the Firefly forums to see what they could do. Thanks for all of the help.

---

### Post by Holmes89 on 2008-02-18
Okay so this was the response I got on the Firefly Forums
> The Daap protocol is only seen by devices on the local network. There are ways around this limitation.

One way is to use Hamachi, which is a very easy to configure software based VPN. All devices that join the same VPN network with Hamachi will appear to each other as being on the same subnet. Hamachi can run on Ubuntu.

But from what I'm reading the samba thing seems like it would work the best for me because I can use it for more than just music and won't have to install a bunch of crap on my computer. Thanks for all of the help.

---

### Post by StooJ on 2008-02-18
Only working on the same network is an iTunes limitation :(

Blame Apple.

I have Hamachi installed on a Windows computer and it works great for stuff like LAN multiplayer games etc

---

### Post by Holmes89 on 2008-02-19
Ok I'm going to do the Samba thing and thanks for the guide, the only thing that I could see as an issue is how do I make it accessable from outside my LAN? Is there a special port number for SAMBA or do I have to do something else?

---

### Post by faulkes on 2008-02-19
> **Holmes89 said:**
> Ok I'm going to do the Samba thing and thanks for the guide, the only thing that I could see as an issue is how do I make it accessable from outside my LAN? Is there a special port number for SAMBA or do I have to do something else?

Typically, samba is not reachable outside of a local lan situation.

If you are looking to be able to do so, you would likely require a vpn based solution such as PPTP (which linux supports).

The Security forum would likely be able to help you with more specifics regarding that.

Faulkes

---

### Post by palintheus on 2008-02-19
Have you considered something like Ampache or gnump3d

[http://www.ampache.org/](http://www.ampache.org/)
[http://www.gnu.org/software/gnump3d/](http://www.gnu.org/software/gnump3d/)

---

