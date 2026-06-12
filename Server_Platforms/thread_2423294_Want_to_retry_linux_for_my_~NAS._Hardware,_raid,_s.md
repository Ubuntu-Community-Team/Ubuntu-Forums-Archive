---
title: "Want to retry linux for my ~NAS. Hardware, raid, smb share."
date: 2019-07-20
forum: Server Platforms
---

### Post by fusk on 2019-07-20
I tried linux some years ago, and it didn't go well. Nothing worked out like i wanted it, and things that took 20 secs in windows i spend 2 days bouncing from forum to terminal getting it sorted until i gave up.
This time i'm gonna ask the questions first before i format everything.
I have a small headless machine in the closets that kinda runs like a NAS, except it's not, but kinda as it also runs some desktop applications. So, no, NAS dedicated distros won't work, i tried.
The machine is a 200GE, 8gb memory & LSI SAS card in IT mode. 3 ssd's and 3 hdd's. It's running teamviewer for remote sessions when needed. Pfsense router runs openvpn, subnet is allowed access to smb share through windows firewall.

I need to create two raids and a smb share that does not require login, and allows traffic from VPN subnet. OS is installed on one of the ssd's.
1x ssd as boot drive.
2x ssd in raid0, possibly with a custom cluster size of 1mb, not sure if relevant on linux file systems.
3x hdd in raid0, this volume is the smb share.

Any assist is much appreciated.

---

### Post by mikewhatever on 2019-07-20
Hmm..., that's a lot of stuff to assist with. It's not going to be an easy project, unless you are not relatively proficient in linux distro administration. In case you know how to do it all in Windows in 20 seconds, Ubuntu would probably not be worth the learning curve.

---

### Post by him610 on 2019-07-20
>  NAS dedicated distros won't work
Did you try either *freenas* or* nas4free*?

---

### Post by fusk on 2019-07-20
> **mikewhatever said:**
> Hmm..., that's a lot of stuff to assist with. It's not going to be an easy project, unless you are not relatively proficient in linux distro administration. In case you know how to do it all in Windows in 20 seconds, Ubuntu would probably not be worth the learning curve.
In windows creating raid is just a few clicks through disk management. Creating smb share, changing user rights and edit firewall to allow traffic from VPN subnet is also fairly easy. All that would take like 5-10 min to do.
But i kinda wanted to run it natively so i didn't have to run a linux vm on the machine, not that it isn't working fine. People just keep telling me i should switch because it uses less resources etc. etc.

And if i can just get over the hurdle of creating the raids and a working smb share, then the rest i either know or can figure out. What i learned the first i tried linux for this machine, was that creating raids and smb shares was a major pain in the butt. Hoping those things might be easier today considering both are widely used.

> **him610 said:**
> Did you try either *freenas* or* nas4free*?
Yes i have tried. Those are primarily nas systems, and can't run desktop programs as well. My system isn't only a "nas", but also a "nas".

---

### Post by fusk on 2019-07-20
I'm unsure, maybe this belongs in the general help forum?

---

### Post by deadflowr on 2019-07-20
> I'm unsure, maybe this belongs in the general help forum?
There is a better place
*Thread moved to **Server Platforms***

The experts of what you want frequent here.

---

### Post by fusk on 2019-07-20
> **deadflowr said:**
> There is a better place
*Thread moved to **Server Platforms***

The experts of what you want frequent here.

Alright, thank you.

---

### Post by TheFu on 2019-07-20
Nothing has changed in the way RAID and samba are properly configured.  It you want point-n-click, stay with Windows.

---

### Post by lammert-nijhof on 2019-07-20
Use the ZFS file system on Ubuntu for the storage SSDs and HDDs, it is magnificent and so easy to set up. I use it in Raid-0 configuration with all different HDDs, different in size and different in throughput.
Boot from ext4 for the moment. Currently it is somewhat more manual work to boot from ZFS, but I think that support for the installer has been planned for Ubuntu 19.10 in October.

---

### Post by mastablasta on 2019-07-22
OpenMediaVault is a nice Debian based NAS with a GUI.

aside from ZFS there is also BTRFS which has a lot of same features and osme that are different.

---

### Post by fusk on 2019-07-22
The reason i thought about ubuntu this time is because of the available support. Last time i tried another popular distro, and everything went sideways. I think ubuntu lts is the safer bet.

---

### Post by mastablasta on 2019-07-23
well Debian has good support and is well documented. especially for server there are some good tips that work on Ubuntu server. in so is CentOS (RedHat) on which Nethserver (another NAS GUI) is based.

---

### Post by fusk on 2019-07-26
One thing to note, my initial intention was to use ubuntu desktop. The reason thread was moved to server was because of the stuff i wanted to do, i did not consider creating a raid or smb share "server" features. I'd like to keep the desktop as i am defiantly not experienced enough to control everything through ssh, or am going to utilize most of the features server offer. This is just a hobby thing i do in my spare time, i'm not learning linux through school or work which would accelerate the process.

---

### Post by TheFu on 2019-07-26
> **fusk said:**
> One thing to note, my initial intention was to use ubuntu desktop. <snip>
This is just a hobby thing i do in my spare time, i'm not learning linux through school or work which would accelerate the process.

Exactly. Hence my post above.

---

### Post by mastablasta on 2019-07-29
> **fusk said:**
> One thing to note, my initial intention was to use ubuntu desktop. The reason thread was moved to server was because of the stuff i wanted to do, i did not consider creating a raid or smb share "server" features. I'd like to keep the desktop as i am defiantly not experienced enough to control everything through ssh, or am going to utilize most of the features server offer. This is just a hobby thing i do in my spare time, i'm not learning linux through school or work which would accelerate the process.


well, we are saying you intentions are misguided. though if you really like desktop on server, then Zentyal (based on Ubuntu) default install will provide you with desktop as well as a webgui interface to access server via browser. zentyal was made to replace windows small business server. so it should do what you want via GUI. but i have to say it has been a while since i gave it a go. they ar enot consumer oriented but more business oriented.

i was saying that if you really need a point and click interface, then go with a webgui. i listed a few distros that are easy to use. you install them, then you remove the monitor and access the server through your browser. if you bought a NAS it would work in a same way. Openmediavault and Nethserver offer an easy to use webgui access to your server while at the same time they are based on rock solid OS (Debian and Centos/RedHat). there are others others as well.

you can also just add Ajenti WebGUI to Ubuntu server - again it will be clicky click for most stuff.

RAID (if you use software mdadm) is done at the beginning. RAID0 is almost useless (one disk breaks and you lose all data). RAID doesn't guard against data corruption or loss of data. it only guards against disk failure (so that the OS can still run even if one disk is out of action for example). and the 0 doesn't even do that.

---

