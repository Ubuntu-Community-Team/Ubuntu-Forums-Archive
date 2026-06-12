---
title: "Creating cloud server with 2 hdd"
date: 2020-01-07
forum: Server Platforms
---

### Post by kulmanrenato on 2020-01-07
Hi!
Currently i have a wd red 1tb for a media server and i would like to buy a wd red 3tb for the media storage. 
What i would like to do is to use the 1tb hdd for a cloud server and copy these files to the 3tb drive which also serves as the media storage.
As i read its raid 1 that should do the job, but is it possible to configure it to a partition of the 3tb drive or just the whole thing?

---

### Post by SeijiSensei on 2020-01-07
Is the server physically co-located at an ISP? My cloud servers are all virtual machines at Linode. I haven't rented space at an ISP for over a decade or longer.

You can bind a 1 TB drive to a 1 TB partition on a larger drive to create a RAID 1 with mdadm.

---

### Post by kulmanrenato on 2020-01-07
No,  its just an old laptop that i did not use for a while running under my desk.
Then its gonna work as i imagined, 
Thank you :)

---

### Post by TheFu on 2020-01-07
> **kulmanrenato said:**
> Hi!
Currently i have a wd red 1tb for a media server and i would like to buy a wd red 3tb for the media storage. 
What i would like to do is to use the 1tb hdd for a cloud server and copy these files to the 3tb drive which also serves as the media storage.
As i read its raid 1 that should do the job, but is it possible to configure it to a partition of the 3tb drive or just the whole thing?

First, be careful buying 3TB sized HDDs. Odd sized HDDs have a poor reliability history.  Check out some backblaze reliability reports. [https://www.backblaze.com/b2/hard-drive-test-data.html](https://www.backblaze.com/b2/hard-drive-test-data.html) is a place to start. They make quarterly reports, but have changed out smaller sized HDDs for larger ones every few years.  Think they buy 12TB disk now, so you'll want to look back 3 yrs or so to find 3TB disk data.

RAID is NOT what you want if you just need to copy a bunch of files over.  Use rsync for that.

"Cloud server" is extremely vague. What, exactly, do you want it to accomplish?  

A few options:
* want to have a platform that provides IaaS, so that containers and VMs can be loaded onto it. oVirt, KVM, Proxmox, Boxes ...
* want to run just a web server?  [https://help.ubuntu.com/lts/serverguide/web-servers.html](https://help.ubuntu.com/lts/serverguide/web-servers.html)
* want to run a server like what you'd get using cpanel from some cloudy service provider? web, email, ftp (bad idea).  [https://www.howtoforge.com/tutorial/perfect-server-ubuntu-18.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/](https://www.howtoforge.com/tutorial/perfect-server-ubuntu-18.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/)
* want to  learn about self-hosting all sorts of webapps?  [https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign)
* want to run something like owncloud or nextcloud or seafile or .... there are 10 others.  I use nextcloud, but only allow access to it via a self-hosted VPN due to security worries.  [https://www.techrepublic.com/article/how-to-install-nextcloud-16-on-ubuntu-18-04/](https://www.techrepublic.com/article/how-to-install-nextcloud-16-on-ubuntu-18-04/) are some instructions.  These aren't the ones I followed, but are newer.  
* probably 50 other options not listed.  Through **ssh**, so many things are possible that most other "cloud" services aren't really needed.

There are all sorts of options for setting up different systems.  snaps, flatpaks, containers, VMs, docker, or straight package installs with manual configurations.

I am a little concerned about any plans to use USB3 connected storage for anything that isn't backups or streaming.  USB connections are not the same as eSATA, SATA, or SCSI connections.

Whatever you do, please do backups, versioned, daily, automatic, backups.

---

### Post by kulmanrenato on 2020-01-07
Thank you for the tip, it was really useful :)
I would like to use it for Cloud storage so something like owncloud or nextcloud. Right now it functions as a torrent server, plex media server, openvpn server and gonna install pihole if i figure out what the hell is wrong with it. (But the last 2 has nothing to do with the hdd-s)
The cloud storage is mostly for storing school, files, family photos and whatever my family wants to use it for, but not storing any sensible data on it. Probably i would even backup those files to my main computer sometimes.

---

### Post by TheFu on 2020-01-07
> **kulmanrenato said:**
> Thank you for the tip, it was really useful :)
I would like to use it for Cloud storage so something like owncloud or nextcloud. Right now it functions as a torrent server, plex media server, openvpn server and gonna install pihole if i figure out what the hell is wrong with it. (But the last 2 has nothing to do with the hdd-s)
The cloud storage is mostly for storing school, files, family photos and whatever my family wants to use it for, but not storing any sensible data on it. Probably i would even backup those files to my main computer sometimes.

Running everything inside the same OS install is NOT a best practice.  OpenVPN should be separate.  pi-hole should be separate.  When it comes time to upgrade plex, you'll wish it was separate.  That's where using virtual machines or at least containers come in.

My nextcloud install has read-only access to media files.  I don't trust it to have read-write access for video, music, photos. Actually, any documents stored inside it are copies too.  But I do love that nextcloud has a video chat server, so we can all hop onto the same machine for a quick video chat or audio chat.  It is really handy when I'm overseas and want to check in with the wife+kids.

---

### Post by kulmanrenato on 2020-01-07
Well, now i feel stupid not thinking about virtual machines, considering how much i messed up my pi before. I messed it up already enough to think about a clean install. I am going to check how to set up the virtual machines tomorrow. 
Should i just do a clean install and basically run everything on separated virtual machines and do daily backups of the main OS? 

Maybe i am not even going to copy the files between the HDD-s just use it as a backup storage so i have more space.

Thanks you very much, you helped me a lot :)

---

### Post by TheFu on 2020-01-07
Raspberry Pis don't support virtualization last time I checked.  Really want an intel with VT-x support or an AMD with AMD-v support to do virtual machines.

Plus sufficient RAM.  And don't load a desktop ubuntu for each VM. That is a waste. Only load the smallest ubuntu server you can stand, then manage it over ssh.

---

### Post by kulmanrenato on 2020-01-07
I never tried with pi, but at least i should have think about this before. 
I just checked and my computer supports kvm.
I dont want to run anything with desktop, i want to learn how to do this stuff without a gui. 

I read a little bit about it, but i am not sure how to handle the media files. 
I am thinking about storing the data on the host and create a samba share so the virtual machines can acces it.
Is there a better way to do it or this would be fine?

---

### Post by TheFu on 2020-01-07
Dont' use samba for unix-to-unix sharing. Use NFS and use read-only NFS if you can for anything that is internet facing.

---

