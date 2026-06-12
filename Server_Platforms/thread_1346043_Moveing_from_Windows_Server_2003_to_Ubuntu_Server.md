---
title: "Moveing from Windows Server 2003 to Ubuntu Server"
date: 2009-12-04
forum: Server Platforms
---

### Post by sbussy89 on 2009-12-04
I currently have a Windows server up and running with Windows Server 2003. I would like to change this to a Linux server, simply because I want to learn more about Linux servers now that I am fairly familiar with windows servers. My big questions are as follows:

Currently I have uTorrent running with the WebUI, and I would say this is about 90% of what I use my server for. Will I be able to set up this or a similar system on Ubuntu server?

I have an external hdd that I converted from FAT32 to NTFS for premissions reasons with my windows server (I have it set up to do a directory listing, and I needed to make it NTFS to set up permissions). Will it be a pain in the @$$ to convert this back to FAT32, and once I do so is it easy to set up the same directory listings with permissions? I do have some experience with Linux, so I am familiar with chmod, but I wasn't sure if this would carry over to web directory listings.

Lastly, does anyone have a good tutorial for installing the newest version? I have found a lot of tutorials for older versions, but nothing newer than 8.04. If nothing much has changed I could just use one of these, but if not a tutorial would be nice.

I know this is a huge wall of text, but any help is much appreciated!

---

### Post by lykwydchykyn on 2009-12-04
> **sbussy89 said:**
> I currently have a Windows server up and running with Windows Server 2003. I would like to change this to a Linux server, simply because I want to learn more about Linux servers now that I am fairly familiar with windows servers. My big questions are as follows:

Currently I have uTorrent running with the WebUI, and I would say this is about 90% of what I use my server for. Will I be able to set up this or a similar system on Ubuntu server?

I have no torrent experience myself, but I know that there are several torrent programs for Linux, both GUI and command-line.  I'm sure you'll be able to find something.
> 
I have an external hdd that I converted from FAT32 to NTFS for premissions reasons with my windows server (I have it set up to do a directory listing, and I needed to make it NTFS to set up permissions). Will it be a pain in the @$$ to convert this back to FAT32, and once I do so is it easy to set up the same directory listings with permissions? I do have some experience with Linux, so I am familiar with chmod, but I wasn't sure if this would carry over to web directory listings.

No need to convert back to FAT32, Linux speaks NTFS just fine.  In fact, if you want to work with permissions and so forth, FAT32 won't work for you.  The filesystem itself doesn't support permissions, so no OS will be able to do that.

If you intend to stick with Linux, it would be ideal to convert it to something else like ext3/4 or jfs, but that would involve reformatting, there is no conversion process for something like that.

> 
Lastly, does anyone have a good tutorial for installing the newest version? I have found a lot of tutorials for older versions, but nothing newer than 8.04. If nothing much has changed I could just use one of these, but if not a tutorial would be nice.

I know this is a huge wall of text, but any help is much appreciated!

Most of the essentials won't change. You might check howtoforge.com, they seem to get a regular update of the "how to install ubuntu" whenever a new version comes out.

---

### Post by Meatshield on 2009-12-04
For torrenting, give Transmission a look. It has command line, web-based and GUI components so you can install/configure what you need depending on how you use it (I personally do all my torrenting via a web interface, but I'm on the go a lot).

As stated above NTFS is just fine. You may have to mount it, but that's just a quick google search for the command to do that.

The install is designed to be as user friendly as possible. It will walk you though partitioning the hard drive, setting up user accounts, etc, so you shouldn't have an issue if you can install Windows.

Since this is your first Linux box, I will give you a few hints:
- separate your /home directory and put it on its own partition. All your personal files go in /home, and if you place it on a separate partition you can reinstall the underlying OS without needing to backup all that data.
- Get friendly with man pages and google. Man (manual) pages list all the command-line arguements, etc for a program. You can run them with 'man <command>' in the command line. Google of course usually links to this forum, but there are a LOT of published guides and discussions so if you run in to an issue, I guarantee you someone has had it and fixed it before.

If you do that, you'll have a much more pleasant time with Linux. And as always this forum is here to help you, so if you get stuck and can't find anything, there is someone here who can help :)

---

### Post by buntunoob on 2009-12-04
As much as your torrenting, To keep the bad men away I might Suggest a ip blocklist, heres the gui one that I use, not sure about a cli one thou [http://www.ubuntugeek.com/ipblock-graphical-ip-blocker.html](http://www.ubuntugeek.com/ipblock-graphical-ip-blocker.html)
 
webbased torrents...
Torrentflux [http://tf-b4rt.berlios.de/](http://tf-b4rt.berlios.de/)
Deluge [http://deluge-torrent.org/](http://deluge-torrent.org/)
Transmission [http://www.transmissionbt.com/](http://www.transmissionbt.com/)
Azureus [http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)

---

### Post by windependence on 2009-12-04
You would be wise to stay with the 8.04 LTS release anyway. Latest and greatest isn't always the best. The LTS is supported for 5 years, and unlike Windows where they make you pay for basically a service pack (Windows 7), Ubuntu allows you to update your components and OS as new things come out so in effect you have the new release if your system is up to date (unless the kernel changes). The LTS release will be more stable and more widely supported for third party applications also, and truly you aren't missing anything.

-Tim

---

