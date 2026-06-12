---
title: "Help creating a media/file server"
date: 2012-02-12
forum: Server Platforms
---

### Post by Eezyville on 2012-02-12
Hello friends,

I am trying to create a server to store all my files in one central location. I would also like to create this server to improve my skills in using linux and networking. This server has to be able to keep my files (media and documents) in a secure location and serve as a media server as well. I would like to stream my media files over the internet to my PCs, my PS3, and my family's PC in a different city, if that is possible. Also is it possible to stream music to my Android phone? A few more things as well. Can I build it to allow it to download and store my emails and allow my two PCs access those emails? Can I have it as a central location where I download my torrent files to. I would like to open a torrent in one of my PCs and have the file download to the server. Any links to How-Tos would be appreciated.

Thanks

---

### Post by matt_symes on 2012-02-12
Hi

> **Eezyville said:**
> Hello friends,

I am trying to create a server to store all my files in one central location. I would also like to create this server to improve my skills in using linux and networking. This server has to be able to keep my files (media and documents) in a secure location and serve as a media server as well. I would like to stream my media files over the internet to my PCs, my PS3, and my family's PC in a different city, if that is possible. Also is it possible to stream music to my Android phone? A few more things as well. Can I build it to allow it to download and store my emails and allow my two PCs access those emails? Can I have it as a central location where I download my torrent files to. I would like to open a torrent in one of my PCs and have the file download to the server. Any links to How-Tos would be appreciated.

Thanks

Mediatomb is the streaming server i use on my server. Any uPNP device can see it over wireless or a wired connection. You can configure it using a broswer.

I have only used it on my internal LAN; never over the Internet. I have not even investigated it over the Internet. Should be possible but consider security of the entire server.

For bit torrents on my server i use rtorrent. You can configure it so that any torrent files that get put in a directory will be picked up by rtorrent and downloaded (using inotify i think).

If i download a torrent file onto a client PC, i then SCP the file to the server rtorrent directory and rtorrent will start downloading it. There are other ways to do this but this is my preffered method.

My advice for a headless server administration is SSH. SCP uses SSH and, as long as you are comfortable with the command line, is the best way to administer a server from anywhere in the world. Use all the standard precautions with SSH though such as keys, non standard ports and limiting the number of connections in a time period (fail2ban) (etc). Set up your firewall correctly.

I assume you don't want a resource hogging GUI on your server ?

Setting up e-mail should not be a problem.

I want to re-iterate; if you are going to expose your server to the net then be very carfull to ensure it is locked down as much as possible. Read all the security stickies and posts here and in other places before port forwarding your router.

Test it on your home network first.

...and don't forget the other benefit of a home server.... It's very, very easy to back up all your files ;).

Kind regards

---

### Post by Eezyville on 2012-02-12
matt_symes,

Thank you for your advice. I will investigate all options and start setting up my media server for just my local network. Once I understand the security I will set it up for media streaming over the internet.

Again thanks,

---

### Post by kentish on 2012-02-13
Hi Eezyville

You might want to consider [Open Media Vault]("http://openmediavault.org/") (OMV) rather than an ubuntu server. I've used an Ubuntu server for a few years but have recently swap to OMV as I really like the web interface and the available [plug ins]("https://code.google.com/p/omv-plugins/downloads/list") - MYSQL, DLNA, CUPS, uTorrent etc It's based on Debian so you should feel at home! 

I use SubSonic for my music streaming - [http://www.subsonic.org]("http://www.subsonic.org")

OMV also has an FTP server if want to share documents

It's all web driven so I run it on a headless server and it take care of all my needs. The only downside is that it need the storage device to it's self so you can;t partition a large drive down. I'm testing it with a 4gig compact flash card in a CF to IDE adapter.

Hope this helps.

BTW I loved my ubuntu server and I learnt so much but now days I have a family and not much time hence why easy of set up is a must for me.

Kentish

---

### Post by hoodwink55 on 2012-02-13
Another avenue to look down might be Plex media server. It would work for both locally and remote streaming of all your media.

---

### Post by kentish on 2012-02-13
Just thought as you have a Playstation 3, this might be of interest - [ps3mediaserver]("http://code.google.com/p/ps3mediaserver/") on Google Code

---

### Post by Lars Noodén on 2012-02-13
If you want to share files over LAN or WAN, then [SSHFS](http://www.linuxjournal.com/article/8904) is very easy.  Since it works over [SFTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/) it is also very secure.  

For streaming you could look at VideoLAN, Icecast2, or FFMPEG.

---

### Post by definingmoment on 2012-02-13
I developed [ServeStream]("http://sourceforge.net/projects/servestream/") for streaming media to my Android phone. I use this in conjunction with [GNUMP3d]("http://www.gnu.org/software/gnump3d/") however it should realistically work with with any media server, especially ones that server up HTML pages with links (like GNUMP3d).

---

### Post by FakeOutdoorsman on 2012-02-14
Whatever you decide to do I recommend regular backups (in addition to RAID if you like) if your data is particularly important to you. There are many ways to do this and it can be performed automatically. I use a video server at work that contains 18 TB of video files and hard drive failure occurs more often than I expected but the redundancy has saved the data.

---

### Post by tommyleinen on 2012-02-14
I am trying to do a similar thing using netbook on ubuntu netbook remix. Having trouble with attached storage but plan to use mediatomb for streaming. I think there is an app for android called mediastream which picks up upnp. Let us know how you get on!

---

### Post by Mia1990 on 2012-02-14
+1 for Open Media Vault. Myself i use Ubuntu server but i store all kinds of stuff on my server.

---

### Post by tommyleinen on 2012-02-15
Will have a look at Open Media Vault and test it out as I can't seem to get UNR set up the way I need, cheers :)

---

