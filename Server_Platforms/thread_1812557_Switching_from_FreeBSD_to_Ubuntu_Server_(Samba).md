---
title: "Switching from FreeBSD to Ubuntu Server (Samba)"
date: 2011-07-26
forum: Server Platforms
---

### Post by mallen324 on 2011-07-26
Hello all,

Sometime in the next few weeks the office I just started working in wants me to switch their file server over to Ubuntu, from FreeBSD. I am a little scared of doing this, seeing as how I came into this job with no documentation of the network/hardware that I will be primarily working with. Does anyone have any useful tips/links that would be relevant to my task? So far, I have copied over the following files from the FreeBSD server:

/usr/local/etc/smb.conf
/usr/local/etc/smbldap-tools/smbldap_bind.conf
/usr/local/etc/smbldap-tools/smbldap.conf
/usr/local/etc/ldap.conf
/usr/local/etc/ldap.secret

I've made an Ubuntu samba server before, so I was kind of off-put by those file locations on the FreeBSD server. Any suggestions would greatly appreciated. 

Thanks!

---

### Post by ratcheer on 2011-07-26
New job? No documentation? Major server migration? You are going to be in a world of $#!&

Tim

---

### Post by brighty22 on 2011-07-26
^This. Can I suggest mirroring the BSD server first? :D

---

### Post by mallen324 on 2011-07-27
Yeah, I knew I was in for it once I noticed the lack of documentation. Well, the way it is set up is that there are two servers that need to be switched over. One being their main production samba server, the other just replicating the data for redundancy. I was going to backup all the data on the main server and work on switching over the redundant server to Ubuntu first. Then, I would make that the PDC (once its functioning), and then change over the old production server to Ubuntu and make that the data replication server. 

Does anyone see any flaws in this idea? I realize that this is going to be a stressful project....

---

### Post by ratcheer on 2011-07-27
Will you have other good production backups while the other server is being converted? If yes, then your plan sounds workable.

Tim

---

### Post by mallen324 on 2011-07-27
> **ratcheer said:**
> Will you have other good production backups while the other server is being converted? If yes, then your plan sounds workable.

Tim

By production backups, Im guessing you mean another data replication server making backups. In that case no. I think I am going to make a new backup daily (at the end of the day) on the main production server until the new production server is ready to roll out. Hopefully that will be feasible with the equipment/hardware I got.

---

### Post by mallen324 on 2011-08-09
So I plan on going through with this plan relatively soon, possibly depending on feedback. Anyways, I have these files copied off of the main samba server:

/usr/local/etc/smb.conf
/usr/local/etc/smbldap-tools/smbldap_bind.conf
/usr/local/etc/smbldap-tools/smbldap.conf
/usr/local/etc/ldap.conf
/usr/local/etc/ldap.secret

Can you guys think of any other files That I should just copy over from the main server to the new one that would make this any easier? Am I missing something obvious since a ldap backend (offsite, and not sure if backend is the right terminology) is involved?

---

### Post by tekknoir on 2011-08-09
Try to keep both systems up and running and when you can connect to the new samba server and worked out all the issues you can hopefully on need to change the hostname and IP address.

I use ubuntu 10.04/samba because it has LVM, I have software and hardware RAID, and software seems to be the better choice.  Alot of options for upgrading when samba shares are on a LV RAID partition.   I only lose 3% cpu for software RAID5 over the hardware RAID5.

---

### Post by mallen324 on 2011-08-09
Thanks for the tips. Did you say there should be no need to change the hostname and IP address? Sorry if I am being mislead from a typo. 

I was thinking this would need a new hostname and IP address. I figure that would reduce conflicts, once it was plugged into the actual network. I know that would require some lines to be changed in the files mentioned above. Ill go through them and see if it's obvious what needs to change.

Will I have any problems with the LDAP server not accepting requests from this new samba server?

---

### Post by mallen324 on 2011-08-09
While doing further research, I came across 'Zentyal":

[URL="http://www.zentyal.com/"]
http://www.zentyal.com/[/URL]

Are you guys familiar with this? It looks pretty promising. Should I just stick with the basics and administer via command line, or put make up on the server and have a nice webGUI? Think it might create more headaches than fix?

---

### Post by headvampyre@hotmail.co.uk on 2011-08-09
I'd say administer it via SSH, or if you want a web interface, dont be ripped off by Zentyal and use Webmin. LDAP should be easy to intergrate with samba, and I'll do what I can to help you with that :)

---

### Post by mallen324 on 2011-08-10
Thanks, headvampyre!

I think I'll keep it simple, and just have the basics for a while. Once I feel comfy, then maybe I'll install a webgui. No need to do it all at once.I appreciate your offer for help, that goes for everyone here. I guess I'll just make a new thread when it actually comes down to the problems that I'll (inevitably) run into once I start.

---

