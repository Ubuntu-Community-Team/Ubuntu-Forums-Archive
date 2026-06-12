---
title: "BEST ubutnu 10.04lts desktop automated deployment"
date: 2010-08-25
forum: Server Platforms
---

### Post by andrewuy8888 on 2010-08-25
vote on the best automated deployment for 10.04 lts desktop!

have 50units identical pc's, one pdc (openldap, bind, dhcp) and  one fs (nfs server).

thinking of installing just one pc with all the updates, program addons and stuff, then thinking of:

disk image the disk and copy to the rest of the 49units and just edit the host name and activate the etho by

 sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.rules.old

would this be ok? i mean there will be no problem if users authenticate an stuff?

give your insights and recommendations.

thank you very much!

* why disk image way? coz i don't really have the space :)

---

### Post by scorp123 on 2010-08-25
50 or more desktops?

That's where I'd use a Sun/Oracle VDI setup. With this you can spit out 100's of cloned desktops in a few seconds. And yes, Ubuntu 10.04 is officially supported too. I have university customers who use this, e.g. they give their 1000+ students Ubuntu desktops via the "Sun Ray" thinclients ... or the soft-clients (you can install a soft-client on Mac OS X or Windows; the Windows version will work tip top on Linux if you use WINE); so you don't even need to sit at a thin-client; having the soft-client or any RDP-capable program on your own laptop will be sufficient as well. 

Advantage: no license costs apart from the server software and the students can login anywhere they like and "hotdesk" into their running session, criss-cross all over the campus.

Sun/Oracle have a wiki where all the installation steps are explained in great details:

[http://wikis.sun.com/display/VDI3dot2/Home](http://wikis.sun.com/display/VDI3dot2/Home)

I have a test-setup running on ordinary PC's:
1 x Dual-Core AMD system acting as LDAP and file server
2 x Quad-Core Intel system, each with 12 GB RAM acting as hypervisor and storage server

That setup has enough firepower to serve about 10 to 15 Linux desktops.

---

### Post by kuda on 2010-08-26
clonezilla??

---

### Post by andrewuy8888 on 2010-08-26
@[scorp123]("http://ubuntuforums.org/member.php?u=109288") very very interesting, vdi for linux!  who would have thought!  have to check it out, thank you very much for sharing! :D

@kuda will check out clonezilla too, i think it's like ghost but free, gonna check it out!


if you guys still any have other recommendations, please do post, i know there are others that are in the same situation.

thank you very much!

---

### Post by arrrghhh on 2010-08-26
Yea, depending on your requirements I'd say either clonezilla or the VDI solution.

Clonezilla is great, it can multicast the images to 40+ machines (depending on server & network setup)

---

### Post by andrewuy8888 on 2010-08-26
@[arrrghhh]("http://ubuntuforums.org/member.php?u=323523") ok, please correct me if i'm wrong. process would be.

1. have a working openldap, nfs server, dhcp, dns network setup
2. setup a clonezilla server.
3. install a ubuntu 10.04 lts desktop machine with all the updates, software add ons and so forth.
4. clone that machine under clonzilla
5. multicast to all pc's that have no os yet
6. change their hostnames (under /etc/hosts) and get their individual eth0 working.

do i have the steps right?

thank you!!!

---

### Post by arrrghhh on 2010-08-26
I believe so... you may or may not have to change more than the hostname, but I can't think of anything else off the top of my head.  I've honestly never deployed that many workstations at once - and we always deploy WinXP workstations ;)

---

### Post by scorp123 on 2010-08-27
> **andrewuy8888 said:**
> @[scorp123]("http://ubuntuforums.org/member.php?u=109288") very very interesting, vdi for linux!  who would have thought!  have to check it out, thank you very much for sharing! :D 

In case you'd want to try it out:

Oracle VDI is fully functional, even without license code or anything. So you can create an "Oracle Online account" (free), and then download the software and play with it. The license is such that after 60 days you'd need to purchase a license or otherwise remove the software again ... And to be honest: those licenses are not exactly cheap in any way (hey, we're talking about Oracle ... :D ). 

It sort of gets cheaper the more desktops you need to serve out. 50 desktops is about the number where the license and associated hardware costs ***may*** be cheaper than 50 shiny new PC's. Below ~50 desktops VDI (doesn't really matter from which vendor) definitely is too expensive and new PC's would definitely be cheaper. I have had several projects with Oracle VDI and VMware View ... and seriously: below 50 seats you don't need to bother with VDI, the license costs will kill you.

Oracle VDI uses Solaris 10 as OS (needs to be downloaded separately!) underneath and it absolutely needs a directory server, be that Microsoft AD or some sort of LDAP. There is a quickie tutorial on how to get a LDAP server really fast:
[http://blogs.sun.com/whitemencantjump/entry/why_does_sun_vdi3_mandates](http://blogs.sun.com/whitemencantjump/entry/why_does_sun_vdi3_mandates)

Of course ... any LDAP will work. You can use Fedora DS, Mandriva DS, any OpenLDAP on any OS ... You just need to have one. Depending on what LDAP (or AD?) implementation you use you will need to adjust some filters too. Explanation is here:
[http://wikis.sun.com/display/VDI3dot2/How+to+Edit+the+LDAP+Filters+and+Attributes](http://wikis.sun.com/display/VDI3dot2/How+to+Edit+the+LDAP+Filters+and+Attributes)

Why does it use Solaris 10? In one word: **ZFS.** That's how and why it can serve out 100's of clones so fast. You create a master image, you convert it into a template (it's all explained in the Wiki), then you hit the "Clone" button .... and woooooosh, ZFS does its wonders and everybody gets a desktop.

As I said, for 50 or more desktops I'd consider such a solution. As far as I know Oracle VDI is the only solution & vendor that supports Linux VM's as desktop OS; all others like Citrix and VMware are 100% focused on Windows and support Windows only.

---

