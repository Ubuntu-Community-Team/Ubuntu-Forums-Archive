---
title: "Home Server &amp; Samba Config."
date: 2011-04-27
forum: Server Platforms
---

### Post by XBMC old School on 2011-04-27
I want to setup my ubuntu desktop to serve/host files (pics, vids) for my media centre PC and provide a backup folder for two laptops (wife and son) over my home network.
   
  Desktop Computer as per Signature
  Laptops are Windows 7 
  Media Centre is XBMC’d ATV
   
  I guess my wish list is as follows:
   
  
[LIST]
[*]I      intend to be logged in my ubuntu desktop with a general user account. I      would like the shares to be available on the network whether I am logged      in or not. How do I structure them to do that? Where are they located and      is / the owner.
[*]I      have two laptops with Win7 and SincToy (backuptool) installed. Can share      folders be setup to only be seen and rw by the respective laptop? Can this      be done with “Users & Groups”
[/LIST]
   
  I’ve been researching this quite a bit (ubuntu forum & Youtube) but still haven’t found a tutorial that suites this. I know it is a tricky setup for a novice but I think its possible.
   
  If anyone is an authority or has network admin experience your expertise would be appreciated.

---

### Post by HermanAB on 2011-04-28
Howdy,

Why don't start simple and get something to work first?

FTP is the simplest.  Samba is the hardest.  NFS is in between.

Start with a FTP server on Linux and use the FileZilla client on Windows.  You should have that running within a few minutes.  If you cannot get it running in minutes, then getting Samba to work would be a hopeless exercise in frustration to you.  The Samba book is 3 inches thick...

---

### Post by XBMC old School on 2011-04-28
> **HermanAB said:**
> Howdy,

Why don't start simple and get something to work first?

Well i can get samba to work no problem, just not in the manner i want

> **HermanAB said:**
> Howdy,

FTP is the simplest.  Samba is the hardest.  NFS is in between.

I'm not overly familiar with ftp other than just straight file transfering. but i don't know about folder pathing. Oh OK

> **HermanAB said:**
> Start with a FTP server on Linux and use the FileZilla client on  Windows.  You should have that running within a few minutes.  If you  cannot get it running in minutes, then getting Samba to work would be a  hopeless exercise in frustration to you.  The Samba book is 3 inches  thick...

Which samba book?

---

