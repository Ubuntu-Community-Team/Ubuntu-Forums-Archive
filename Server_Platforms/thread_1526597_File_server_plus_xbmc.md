---
title: "File server plus xbmc"
date: 2010-07-08
forum: Server Platforms
---

### Post by xhaggotx on 2010-07-08
Hello
I am looking for what my best solution would be for the problem I am having.

I have one pc that I am wanting to use as a file server that can also run a torrent downloader so will need to be given the torrents to download from time to time and accessed for general management of the files on it.
But this box is also downstairs right next to one tv in the house so would also like to be able to install something like xbmc on it.
Will I just have to install ubuntu server edition and then set up all the shares for that and the bit torrent client, then set up how to log in from another computer. And then install xbmc on it too?
If not, what else will I need to do?

Sorry if this seems a bit of a simple question, this is the first time I am setting this stuff up

---

### Post by garfonzo on 2010-07-08
Well, with Ubuntu Server edition, you don't get a GUI. So, even if you've got the box hooked up to the TV the server edition will have nothing to output (such as XBMC). 

You may be better off installing the desktop edition so that you can install XBMC to output to the TV. With the desktop edition, you will still be able to set up the shares and the torrent down-loader so that shouldn't be an issue. 

Hope this helps.

---

### Post by xhaggotx on 2010-07-08
I understand what you are saying but reading the wiki for xbmc it says to do a minimal install of it to compile it in ubuntu server. So if I did that would I still be able to access all the server facilities?
Also whichever route I choose (server or desktop ubuntu) would I be able to access the server/desktop remotely while someone else was using xbmc to watch something? I'm guessing that it is possible, that would pretty much be the point of a server, so if so, how?

---

### Post by jmlude_93 on 2010-07-11
I'm currently doing almost the exact thing that you're describing.  I have a single pc that is running 10.04 Server as well as XBMC for my htpc.

I wanted the OS to be as lightweight as practical so I installed the server version, then I installed XFCE without the recommended applications.  This basically gave me a working GUI to start from, but absolutely nothing else.  From this point, I just started installing everything I wanted: video driver, XBMC, and a few other misc programs.  

I really like the setup, but I have to admit that getting everything to work took a lot more time than when I was just running a desktop version.  It's easy forget just how much Ubuntu is doing for you with the desktop version.  Once you have to do everything yourself, it makes you appreciate how much is involved.

BTW, my server is running NFS, Samba, PureFTP, and SSH; all of which can be accessed while XBMC is running.

IMHO, if you have the hardware to not worry about how much resources the OS takes up, I would recommend going with the desktop version, especially if you plan to use this as a true htpc.  If you're using older hardware, or just want a lightweight OS than the server version works great, but be prepared to spend a lot more time getting it to act like a htpc.

---

### Post by gobbledigook on 2010-07-12
hi! 

i've was running xbmc on my server for about a year, but with 10.04 i've moved over to the desktop version, simply because it was easier to start multiple programs on start-up without xbmc starting in windowed mode!

When i was running ubuntu server i had a minimal KDE desktop with fluxbox, was pretty cool, except after a reboot i had to manualy start a vnc session in order to run utorrent under wine... 

Currently i use 10.04 desktop - i only have a single core AMD 64 processor and 2 gig of ram and it handles the full desktop ok. this box also runs a fileserver, samba share, wesite, handles torrent and nzb downloads, acts as a pxe server and ftp server, records webcasts for me etc... i do 99.9% of my admin through ssh.

I found it way easier to set up xbmc after adding it as a start-up application and configuring after reboot - otherwise for some reason it would "forget" the video settings for the TV!! 

you can set utorrent (as well linux clients - transmission/rtorrent) to scan certain folders for .torrents so after you drop a file into that folder it picks it up and starts downloading it :)

my recommendation would be that unless you are prepared for a lot of headache getting it set up, use the desktop install and set xbmc as a startup application - that way you can configure it for full screen etc after and are still able to ssh into the box to admin.

---

