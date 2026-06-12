---
title: "iTunes/iPod server questions, need to know before I move my server over"
date: 2009-09-20
forum: Server Platforms
---

### Post by derrick1985 on 2009-09-20
I am getting an older computer in a couple of days and I want to turn it into a server. My original plan is to turn it into a VPN server, and possibly a LAMP so I can test out my website before I upload it to my hosting provider. I was also, thinking about using it as my central location for music.

I have a few questions though that I can't seem to find an answer to. 

1) Right now, all my music is stored on an external NTFS formated drive, will Ubuntu server (no GUI) be able to read AND write to the NTFS formatted drive, or will I have to format over to fat32 or similiar?

2) Will I still be able to use iTunes to sync my iPods, because I know my wife will not tolerate having to use Linux (lol) or would I be better off sticking with my current setup (library file stored on a network share).

3) Adding music to iTunes, will I be able to do it through the iTunes GUI like normal, or am I going to be copying/pasting it to a share that I make on the server?

4) I will have to use some sort of dynamic DNS service to track my IP back to an address, is there a way for Ubuntu server to do this through a package, and more importantly, find my WAN IP address and not use my LAN IP address?

Thanks,

---

### Post by rmb938 on 2009-09-20
1) I am pretty sure it will be able to read and right to it but I am not 100% sure
4) yes. there is a no-ip package that works with the no-ip system

I am not sure what you mean on questions 2 and 3. You are using itunes on windows right now?

---

### Post by derrick1985 on 2009-09-21
> **rmb938 said:**
> 1) I am pretty sure it will be able to read and right to it but I am not 100% sure
4) yes. there is a no-ip package that works with the no-ip system

I am not sure what you mean on questions 2 and 3. You are using itunes on windows right now?

Yes. I have three PC's in my house, my wife who uses XP and iTunes for her music and iPod syncing, the Desktop which uses again, iTunes (and what I currently sync to) and my laptop which I use Rhythmbox or exaile on right now.

---

### Post by openfly on 2009-09-21
> 
I am getting an older computer in a couple of days and I want to turn it into a server. My original plan is to turn it into a VPN server, and possibly a LAMP so I can test out my website before I upload it to my hosting provider. I was also, thinking about using it as my central location for music.


Be careful with cpu utilization.

> 
I have a few questions though that I can't seem to find an answer to.


Well they tend to be a matter of opinion in some cases, so the only answer is experience.

> 
1) Right now, all my music is stored on an external NTFS formated drive, will Ubuntu server (no GUI) be able to read AND write to the NTFS formatted drive, or will I have to format over to fat32 or similiar?


It should be possible, but not necessarily recommended.  My first question would be how much data are we talking here.  If you have a 1TB disk, an older system may choke attempting to produce or read a 1TB partition.  I'd recommend swapping the filesystem to ext3.  It's readable in windows and linux fairly well.  Any ext2 driver for windows will work on ext3 as it's usually fully backwards compliant. 

> 
2) Will I still be able to use iTunes to sync my iPods, because I know my wife will not tolerate having to use Linux (lol) or would I be better off sticking with my current setup (library file stored on a network share).


Linux would fail at syncing iphones and ipod touches entirely.  Yes you'd have to use windows or mac to sync.

> 
3) Adding music to iTunes, will I be able to do it through the iTunes GUI like normal, or am I going to be copying/pasting it to a share that I make on the server?


Biggest issues will be with multiple users accessing the same fileshare.  You'll want to use Samba.  Permissions being set changed and files being moved renamed or removed may become a hassle.  But I doubt it.  If there's a mac involved you may run into some issues with wanting AFP.  Older mac OSX builds failed samba pretty hard.  

> 
4) I will have to use some sort of dynamic DNS service to track my IP back to an address, is there a way for Ubuntu server to do this through a package, and more importantly, find my WAN IP address and not use my LAN IP address?


Ubuntu will have no idea what your wan ip is if you are using nat.  The easiest thing to do would be to screen scrape a "what is my IP address" website.  Heck you could post your own site to readback where a user is coming from.  That would be a pretty simple script.  Then you could easily run an update script against a dyndns system... or against a dns system.  I don't know what level of skill you are at with scripting though.  What is your router?  How do you do dyndns now... if you do at all?  

> 
Thanks, 

Good Luck

---

### Post by derrick1985 on 2009-09-21
> 
It should be possible, but not necessarily recommended.  My first question would be how much data are we talking here.  If you have a 1TB disk, an older system may choke attempting to produce or read a 1TB partition.  I'd recommend swapping the filesystem to ext3.  It's readable in windows and linux fairly well.  Any ext2 driver for windows will work on ext3 as it's usually fully backwards compliant. 

Depends. The drive right now is only an external 80GB, so no choking required. I might add a 200GB drive that is currently in my Windows system depending on if I can find a web based only torrent program that I can run from the server as well.

> 

Linux would fail at syncing iphones and ipod touches entirely.  Yes you'd have to use windows or mac to sync.


You say iPhones and iPod touches, what about the iPod classic or the original shuffle?

[/quote]
> Biggest issues will be with multiple users accessing the same fileshare.  You'll want to use Samba.  Permissions being set changed and files being moved renamed or removed may become a hassle.  But I doubt it.  If there's a mac involved you may run into some issues with wanting AFP.  Older mac OSX builds failed samba pretty hard.   
ok, there are no MACS currently on the system, so this shouldn't be too big of a deal hopefully.


> Ubuntu will have no idea what your wan ip is if you are using nat.  The easiest thing to do would be to screen scrape a "what is my IP address" website.  Heck you could post your own site to readback where a user is coming from.  That would be a pretty simple script.  Then you could easily run an update script against a dyndns system... or against a dns system.  I don't know what level of skill you are at with scripting though.  What is your router?  How do you do dyndns now... if you do at all?  

It's a dlink DIR-655, and as for scripting, no experience. I currently don't do too much with dyndns, but if it came down to it, I could just use one of my Windows PC's to report back the WAN IP address using their program. 


> Good Luck

Thanks,

---

### Post by openfly on 2009-09-21
I don't know how the dyndns app works, but it may get tricked into reporting the LAN address as well ( though my guess is they poll their own server for that info cause they do this stuff professionally ).  Odds are that'd be fine though.

200 and 80 gig disks should not be a problem.

Shuffle worked in everything.. I used to use winamp to manage mine... had a great interface for it.  I know there were ipod sync apps in linux for shuffle and some of the earlier ipods.  I never used them though.

---

### Post by trundlenut on 2009-09-21
With dynamic DNS sssuming you only have one router and therefore one internet connection WAN and LAN doesn't matter.  You are after the IP of your router and you will need to set up port forwarding on the router to forward web traffic to your LAMP server (normally port 80, but this may be blocked by your ISP).  If you have to use a non standard port then for people to connect to it they would need to use youdomain:8080 or whatever port you choose to use.

If you look on the dnydns website there are instructions for a linux client to update dyndns with your dynamic IP, also some routers have that capability built in, which is useful

---

