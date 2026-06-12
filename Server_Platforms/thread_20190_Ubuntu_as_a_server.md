---
title: "Ubuntu as a server?"
date: 2005-03-15
forum: Server Platforms
---

### Post by quiet_core on 2005-03-15
I am fairly new to linux, I have tried it a couple times only to return to M$ each time.  However, I installed Ubuntu on my desktop and am liking it.  I plan on running a server and was wondering if Ubuntu would be a good choice for a low-end pc server?

The pc it'll be running on is a p2 233, 4G hd, and 64mb ram.

---

### Post by jdonnell on 2005-03-15
I'm running two ubuntu servers at the moment. One is a subversion/internal web server and the other is just a web server. If a million dollars is on the line I'd probably go with something that has a longer track record, but ubuntu works great for me. The reason I came to ubuntu was my frustration with redhat as a server. I still have a redhat 9 server and there is no real upgrade path other than reinstalling a newer version. My hope is that ubuntu will upgrade smoothly from warty to hoary. I'm sold if it does.

---

### Post by az on 2005-03-15
[QUOTE=quiet_core]I am fairly new to linux, I have tried it a couple times only to return to M$ each time.  However, I installed Ubuntu on my desktop and am liking it.  I plan on running a server and was wondering if Ubuntu would be a good choice for a low-end pc server?

The pc it'll be running on is a p2 233, 4G hd, and 64mb ram.[/QUOTE]


What do you want to do?

I run drupal (a CMS) on a 200Mhz p1 with 1.5 Gig HD and 64 meg of ram.  It is surprisingly fast at serving dynamic pages.  It uses php4, mysql and apache2.  (all on the same box)

I had to install webmin from the tarball since it was easier to do that than play around with the root user account.  As well, the drupal debian packages are screwy when it comes to apache2 (they depend on apache1.3!)  They are also old.  Again, I just got the latest from the drupal website.

That box also was my router, too.

---

### Post by streetbmx on 2005-03-16
I run ubuntu warty on my home server. its an old vaio, 300mhz  64mb ram, 9gb hd. runs smooth. mostly use it for bittorrent. runs apache2, php, mysql with torrentflux  :neutral: . still looking for a different web based torrent client.

---

### Post by jayded on 2005-03-16
[QUOTE=jdonnell]... I still have a redhat 9 server and there is no real upgrade path other than reinstalling a newer version...[/QUOTE]

Not true my friend.

I have a server thats been running for years its gone from RH8 -> RH9 -> FC1 -> FC2 -> FC3 

You just have to know how to do a dist upgrade with YUM  :D

---

### Post by quiet_core on 2005-03-16
I'll probably be running it as a simple webserver with LAMP.  I don't see any other use at the moment.

---

### Post by Myles3 on 2005-03-16
Right now I am running a 5 year old dell P3 with only 256k of Ram and it is work great with plone. I have tried Red Hat 7.3, 9 and Fedora 1, 2 and ubuntu is the best for my system

If you wont to run a simple server in ubuntu use [xampp](http://www.xampp.org) and get rid of gnome and install fluxbox as your graphic interface.

---

### Post by daniels on 2005-03-16
Upgrades from warty->hoary are fully supported, yeah.

---

### Post by jdonnell on 2005-03-16
[QUOTE=jayded]
You just have to know how to do a dist upgrade with YUM  :D[/QUOTE]

Is it simple? Does it break things? 

Care to give me a link that explains how to do it?

---

### Post by theantix on 2005-03-16
[QUOTE=quiet_core]I am fairly new to linux, I have tried it a couple times only to return to M$ each time.  However, I installed Ubuntu on my desktop and am liking it.  I plan on running a server and was wondering if Ubuntu would be a good choice for a low-end pc server?

The pc it'll be running on is a p2 233, 4G hd, and 64mb ram.[/QUOTE]

I run Ubuntu on a few servers myself, and I find it to be quite stable.  One big problem with it though is that many common server applications are unsupported, which means that security patches are not necessarily applied.  However in many cases (every case I am personaly aware of) they *ARE* picked up and applied anyhow, even to software only available in Universe.

One thing though, Ubuntu is geared to run as a desktop system.  Some things quite baffled me at first, such as that postfix only listens to localhost by default.  That one had me scratching my head for a few hours as I couldn't figure out why mail delivered locally but not from a remote workstation.  :-)  All in all though, Ubuntu has been good to me as a server distribution.

---

### Post by garyng on 2005-03-16
debian sarge is better for server, I would say. Though I am still trying out debootstrap a hoary as server. The problem with ubuntu is, it is very desktop centric in its package dependency.

For example, I like to use GNOME on my server through VNC(sometimes, not always). But this is not possible in ubuntu as its requires Xorg but my server is under colinux(Xorg crash it during install). This can also be true for many headless servers.

It surprise me that guys behind ubuntu think in "Window" way.  X server as it is designed can be at the "terminal" and why would GNOME need to have it on the same machine where GNOME is on ? They don't depends on each other.

---

### Post by Myles3 on 2005-03-16
[QUOTE=daniels]Upgrades from warty->hoary are fully supported, yeah.[/QUOTE]

How did you upgrade to hoary thought apt-get or installing it again

---

### Post by garyng on 2005-03-16
[QUOTE=Myles3]How did you upgrade to hoary thought apt-get or installing it again[/QUOTE]

change /etc/apt/sources.list to point to hoary instead of warty, then

apt-get update
apt-get dist-upgrade

---

### Post by theantix on 2005-03-16
[QUOTE=garyng]debian sarge is better for server, I would say. Though I am still trying out debootstrap a hoary as server. The problem with ubuntu is, it is very desktop centric in its package dependency.

For example, I like to use GNOME on my server through VNC(sometimes, not always). But this is not possible in ubuntu as its requires Xorg but my server is under colinux(Xorg crash it during install). This can also be true for many headless servers.

It surprise me that guys behind ubuntu think in "Window" way.  X server as it is designed can be at the "terminal" and why would GNOME need to have it on the same machine where GNOME is on ? They don't depends on each other.[/QUOTE]

Ubuntu doesn't require you to install X or Gnome, when you boot off the CD type in "linux custom" and you'll get just a base system to work with.  That may be poorly documented for the warty warthog release, hopefully the developers do a better job of advertising how to install it for servers for the Hoary release.

I would say that Sarge would make a great release for a server as soon as it goes stable.  They seem to be on the cusp of going stable with Sarge very soon now, and when they do it will probably make for a very good server platform.  Of course I've thought that Sarge was on the cusp of going stable for at least a year now... :-)

---

### Post by garyng on 2005-03-16
ah, you misunderstood me.

I am testing hoary through the "debootstrap" route, so I don't have a CD to begin with and "linux custom" is no where to be seen after a debootstrap. 

[http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html](http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html)
mentions how to install warty the uncoventional(debootstrap) way.

However, "base-config new" pulled in the whole desktop by default including X which gives me BSOD on my colinux session. "base-config" is fine though(which is what I used to do on debian).

But after close examination(I want to try the new GNOME as well, yes it is not straightly for server), I found that the ubuntu desktop package needs XOrg server.

Yes, it is possible to install most of the stuff without X(or GNOME) but I just wanted to run GNOME as well on my testing server which is impossible under ubuntu(for my case at least) . I can do this on sarge. Fluxbox, XFCE4 are all fine though under ubuntu. Beside, there is a legitimate use of GNOME on server without X, an application server serving my very old Pentium machines. 

Please don't take this as a trash to ubuntu, just issues that I have encountered. Of course, even headless server nowadays would have some form of graphic device(do they?) but I still think GNOME(or any other graphic desktop) don't need to depend on a X server on the same machine.

---

### Post by az on 2005-03-16
"But after close examination(I want to try the new GNOME as well, yes it is not straightly for server), I found that the ubuntu desktop package needs XOrg server.

Yes, it is possible to install most of the stuff without X(or GNOME) but I just wanted to run GNOME as well on my testing server which is impossible under ubuntu"


It is easy as pie.

Install with the custom option

Run aptitude and select ubuntu-desktop (if you want to go about it that way)
Search through your selected-to-be-installed packages (in green) for the Xserver packages and any package you do not want to be installed and press minus (-)  You will be left with the selection of packages that can be installed without the x server,  Press g to go,

Also, I beleive that Hoary will include a greater number of server packages in the supported main repository than Warty.

---

### Post by garyng on 2005-03-17
[QUOTE=azz]"But after close examination(I want to try the new GNOME as well, yes it is not straightly for server), I found that the ubuntu desktop package needs XOrg server.

Yes, it is possible to install most of the stuff without X(or GNOME) but I just wanted to run GNOME as well on my testing server which is impossible under ubuntu"


It is easy as pie.

Install with the custom option

Run aptitude and select ubuntu-desktop (if you want to go about it that way)
Search through your selected-to-be-installed packages (in green) for the Xserver packages and any package you do not want to be installed and press minus (-)  You will be left with the selection of packages that can be installed without the x server,  Press g to go,

Also, I beleive that Hoary will include a greater number of server packages in the supported main repository than Warty.[/QUOTE]


I am not sure that can be done. In debian(ubuntu) terms, ubuntu-desktop depends on XOrg X server(not any equivalent say VNC) so no Xorg, there would be no desktop(or GNOME).

---

### Post by az on 2005-03-17
Yes, it can be done.

Ubuntu-desktop will bring in all the packages, but unflagging Xorg will unflag some (including the ubuntu-desktop metapackage) but the rest (what you want) will still be there.

---

### Post by theantix on 2005-03-17
[QUOTE=azz]Also, I beleive that Hoary will include a greater number of server packages in the supported main repository than Warty.[/QUOTE]

That has been my experience as well, though as I said earlier even their unsupported "universe" programs seem to get security fixes applied quite quickly.

---

### Post by az on 2005-03-17
"even their unsupported "universe" programs seem to get security fixes applied quite quickly."

I think that applies to packages that have been added to Hoary.  They just update the Warty version, too...

---

### Post by garyng on 2005-03-17
ok, got it(first time to use aptitude, it does have this advantage of tick things out that apt-get  doesn't).

Just in case those want to try the same(to install ubuntu under colinux). The following things need to be ticked out :

1. Xorg X server
2. hotplug
3. cdparanoia
4. anything related to power management

All the above can break colinux.

Now, does anyone know how to tell GNOME to not use the HAL stuff ? I remove hotplug(thus hal stuff that depends on it) and GNOME bark every time it launch, though it can still continue.

---

### Post by davej on 2005-03-18
I am looking for a distro that I can use as a server. I need to be able to access files stored on the hard drive from a Win XP box and I need it to support a DDS3 SCSI tape drive. The ability to backup the XP box as well would be an advantage.

---

### Post by jdonnell on 2005-03-18
You should start a new thread for new topics. 

[QUOTE=davej] I need to be able to access files stored on the hard drive from a Win XP box[/quote]
There are a few ways of doing this. Samba is probably the best.

> 
 and I need it to support a DDS3 SCSI tape drive. 
I have no clue about this. Hopefully someone else will be able to help you with this one.

> The ability to backup the XP box as well would be an advantage.
You could probably setup something with samba for this as well, but I'm not sure.

---

### Post by garyng on 2005-03-18
[QUOTE=davej]I am looking for a distro that I can use as a server. I need to be able to access files stored on the hard drive from a Win XP box and I need it to support a DDS3 SCSI tape drive. The ability to backup the XP box as well would be an advantage.[/QUOTE]

That seems to be too broad a requirement, but anyway :

1. You can either use samba server or Apache2 with WebDav, both allows you to access files on *nix from modern window box.

2. From linux perspective, a SCSI tape is no more than yet another SCSI block device.  The SCSI adaptor is more important, what brand is it. 

3. what do you mean by backup XP box ? Just have each XP box export(share) the data they want to backup then have a cron job on the *nix which mount through smb/cifs then tar/rsync the whole thing over. There can be zillion ways to do this kind of thing, it is a matter of how fancy you want.

---

### Post by davej on 2005-03-18
[QUOTE=garyng]

2. From linux perspective, a SCSI tape is no more than yet another SCSI block device.  The SCSI adaptor is more important, what brand is it. 
[/QUOTE]

ok thanks - it's an adaptec 2940 - I have SCO experience (from a while ago), is there a mkdev scsi and a mkdev tape type command?

[QUOTE=garyng]

3. what do you mean by backup XP box ? Just have each XP box export(share) the data they want to backup then have a cron job on the *nix which mount through smb/cifs then tar/rsync the whole thing over. There can be zillion ways to do this kind of thing, it is a matter of how fancy you want.[/QUOTE]

It's only one XP box and I just want to pick up personal files so using a share should be ok

thanks for your reply.

---

### Post by garyng on 2005-03-18
I believe it is "mknod" but standard scsi don't need that, they are all populated by the distro.

---

