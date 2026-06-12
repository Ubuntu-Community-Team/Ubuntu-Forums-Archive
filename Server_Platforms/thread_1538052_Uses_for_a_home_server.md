---
title: "Uses for a home server?"
date: 2010-07-24
forum: Server Platforms
---

### Post by metalf8801 on 2010-07-24
I'm trying to figure out all the things I can do with a home server. If you have a home server what do you use it for? Also, are there other to uses a home server that you heard about but haven't tried yet? 


I would really like as complete of a list as possible 
Thank you 
Dan

---

### Post by arrrghhh on 2010-07-24
Really?  Are you just unsure what you want to do with your server?!?  Alrighty, I guess I'll bite.

-Apache web server
Allows access to manage torrents remotely, among other things like WebKeePass - I use that to manage all of my online passwords.
-PS3MediaServer - priceless for me, I watch a ton of TV shows and movies on my PS3 using this service.
-MPD - constantly playing music, so I can just flip my amp to that input whenever, and I have music :D  In conjunction with MusicPlayerMinion, perfect music solution for my entire house.
-rtorrent/rutorrent/rssdler (w/showrss) - mentioned earlier, manage torrents remotely, automatically adds new torrents when new shows are released.
-Samba/NFS - so I can share all the files with others in the house!

Currently, I'd like to try and get an IR reciever hooked up to the server and hopefully with lirc I can get my Harmony remote to control MPD so I don't have to have another PC to control the music!  Toyed with Zimbra, but I don't really need anything that fancy, so I've just stuck with Google.

---

### Post by Iowan on 2010-07-24
The [Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html") has a list of some of the things a server can do - and (sometimes) how to set them up.

---

### Post by lisati on 2010-07-24
I use mine to dish out web pages (see sig) and for email. 

Running your own email server gives you some options for keeping spam out that aren't so easily done with a regular email client such as Evolution or Thunderbird.

---

### Post by YesWeCan on 2010-07-24
[QUOTE=metalf8801]If you have a home server what do you use it for? [/QUOTE]
Hi Dan. Mine is used for...
an Apache2 web page server
an openVPN tap server for "road warrior" access so a Windows client can do networking with Windows PCs on the home LAN.
a family photograph database
a complete email service (fetchmail, postfix, dovecot)
an internet gateway for remote clients that need to be seen by websites to be at home.
a Netbeans/Java/MySQL programming platform

It could be used for many, many things. Eg: a high-speed router and internet gateway. What else can a Ubuntu home server be used for? Your imagination is the limit. :cool:

---

### Post by JohnnyVW on 2010-07-25
Mine is used to share printers (Laserjet 6L and Deskjet 952c), files/backup and music (Jinzora) between my computer, my wife's computer (Windows), my work laptop, or any guests that come by with a laptop.  It's pretty basic, it's only on our local lan, but very useful (and fun!).

---

### Post by HermanAB on 2010-07-26
85 Gigs of Ogg files and growing.  Using Edna as a simple maintenance free music organizer:

[http://edna.sourceforge.net/](http://edna.sourceforge.net/)

Works like a charm.

---

### Post by andrew.46 on 2010-08-02
Usenet is far from dead and an excellent idea is to use a proxy NNTP server such as Leafnode 2:

[Howto] Setup and use Leafnode-2 with the newsreader slrn
[http://ubuntuforums.org/showthread.php?t=676837](http://ubuntuforums.org/showthread.php?t=676837)

Works with most usenet clients, not just slrn...

Andrew

---

### Post by amauk on 2010-08-02
Ignoring the obvious (fileserver, webserver, mailserver, etc.)

LTSP (for diskless clients)
Phone/VoIP PBX
Game server (host your own LAN parties)

---

### Post by hometoast on 2010-08-02
I currently use mine to house my media library. It also runs SickBeard and sabnzbd+ to keep the media library filled. 
I also backup my PC and laptop's $HOME to it.
I have apache with gallery2 installed to house family photos.
I sometimes use it to "[fold]("http://folding.stanford.edu/")" on.

(My home server Ubuntu 10.04, AMD Phenom II X 940 BE, 4 GB ddr2-1066 ram, 1 500 GB + 4x1TB Raid 5 mdadm array)

---

### Post by ahbart on 2010-08-02
Apache for testing websites, sabnzbd+ (usenet), backup via unison (for now), and of course caching apt repositories (useful if you use more then one ubuntu pc).
Oh, and testing groupware servers, like egroupware, Zarafa, Zimbra and OpenXchange.

My server: 2Gb, 250Gb, P4-2,2Ghz, Ubuntu, 10.04, via ssh and sftp.
(ssh -C -Y -p portnumber user@ip-address)

---

### Post by stlsaint on 2010-08-02
> **HermanAB said:**
> 85 Gigs of Ogg files and growing.  Using Edna as a simple maintenance free music organizer:

[http://edna.sourceforge.net/](http://edna.sourceforge.net/)

Works like a charm.

+10 on edna. I just recently added edna to my home server list. I also run proxmox virtualization which allows me to use multiple containers(vps) and turn 2gb of ram into enough to do whatever, web server, media server, mail server, ssh, backups/syncing, all running at once. Also for overall application testing. Truly servers are very robust and you can do whatever you put your mind on! :popcorn:

---

### Post by metalf8801 on 2010-08-02
> **lisati said:**
> I use mine to dish out web pages (see sig) and for email. 

Running your own email server gives you some options for keeping spam out that aren't so easily done with a regular email client such as Evolution or Thunderbird.

Whats sig? when I google sig I'm getting a lots of different results

---

### Post by arrrghhh on 2010-08-02
> **metalf8801 said:**
> Whats sig? when I google sig I'm getting a lots of different results

He means "look at my signature" with the "see sig" comment...

---

### Post by quietas on 2010-08-02
Scan through this thread. [http://ubuntuforums.org/showthread.php?t=1075599](http://ubuntuforums.org/showthread.php?t=1075599)

Myself and others listed out what we are using our home servers for and there a ton of suggestions.

---

