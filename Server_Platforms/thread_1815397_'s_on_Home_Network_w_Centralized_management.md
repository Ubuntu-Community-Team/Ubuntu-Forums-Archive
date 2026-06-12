---
title: "??'s on Home Network w/ Centralized management"
date: 2011-07-31
forum: Server Platforms
---

### Post by grunge09 on 2011-07-31
I have 2 Ubuntu Workstaions, and one Windows XP Workstation.  

Hub:
8 port unmanaged gigabit switch all pc's running gigabit networking.

Server:
AMD 6000+
4 GB RAM
30 gb boot os drive
2 1.5tb drives in RAID mirroring. 

NAS File backup:

5u Rack Mount Commercial Box
16 x 250gb SATA HD's (two RAID 5 array's each with a hot spare drive so 1.39TB per array)
Freenas 0.68 on USB Flash Drive.  
currently using RSYNC from each worksta once a week to do a updated modefified files backup, not  a full one)

Worrksta 1:

amd 965 3.4ghz
4 gb ram
500 gb hd
Ubuntu 10.10

Worrksta 2:

amd 965 3.4ghz
2 gb ram
320 gb hd
Ubuntu 10.10

Worrksta 3:

amd 6000+
2 gb ram
2x250 gb hd (onboard Bios raid 1) 
Win XP Pro

Also have:

My TV DVR box:

Mythbuntu Backend Server
AMD 965 3.4GHz
2 GB RAM
500 GB HD
HVR-2250

Living Room DVR Box:

Mythbuntu Frontend Server
Cpq 2.4GHz 
1 GB RAM
40 GB HD

Might have myth boxes on separate old 10/100 hub to minimise network traffic.

I have been looking at Zentyal and ClearOS as they have more of a web interface to configure and monitor things.  Not to say I won't use Ubuntu Server and no GUI.  

My goals are:

A. have centralised management, I really don't need Lamp Server,or FTP. just File and printer sharing.  

B. make backups easier instead of going to each worksta and manually starting a backup (reason for this is my 16 drive raid array rackmount box is friggin loud and I only have that on for backups)

C. Is it possible to have user log on to server from client boxes and have their server /home dir show up as local /home dir?  Does it work and if so does it slow the network down? So if a worksta breaks down I can install a replacment machine add it to the server network (I guess its called a domain) not losing any network /home data.  

D; Want to have file folders shared with user authentication (sounds like samba not NFS right)

E. I see I could use Likewise-open5 to make it easy for me to join linux worksta's to Windows PDC.  Does it work to join gto Linux PDC?   Should I use Likewise at all.

F; Would I need Ldap and Samba for this on Ubuntu Server?  I know there is a stop by step on Ubuntu Wiki for installing Ldap and Samba.  

Am I on the right track, please advise, thanks.

---

### Post by CharlesA on 2011-07-31
A: I think you can use Webmin on Ubuntu, but I haven't used it since 9.04.

B: You can write a script to do the backup and use cron to run it daily. That shouldn't be a problem.

C: I suppose you could do that with an entry in fstab, but I'm not quite sure how it would work.

---

