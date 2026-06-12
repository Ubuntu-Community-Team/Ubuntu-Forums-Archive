---
title: "Administrating many Ubuntu desktop computers?"
date: 2008-01-18
forum: Server Platforms
---

### Post by johann_p on 2008-01-18
I am wondering about whether Ubuntu could be the right choice as the OS for a medium-size installation with several dozen to hundreds of desktop computers (several servers in addition, but those are not really the issue here).

The following things should be possible for this:
* Create some script or configuration files that provide a standard-installation that differs from what the default installation does - automate it so that only at specific points manual intervention is needed.
OpenSuse has the option to save all the responses given to the installer in a config file that can then be used at later installations to automate the process. Is this possible in Ubuntu?

* Make it easy to perform the same installation and configuration steps on groups of computers. Essentially the administrator should be able to install packages, perl cpan packages, ruby gems, separate software so that the very same actions are taken on all or a group of the computers automatically (it wouldnt be feasable that he goes around and reapeats the same steps on dozens or hundreds of computers)

* Don't let end users mess with the configuration: in order to make that many computers administrateable, end users should not be able to do any configuration changes unless explicitly authorized by the administrator. This includes especially the update-manager:

* updates should be carried out by the administrator only: there should be no notification of security updates or similar on the desktop of end-users. The administrator should be able to easily do security updates on all the computers simultanously and automatically.

* Use a server-based authentification scheme and allow users to share server-based resources like raid storage, printers, etc. while these resources should be administrateable centrally. So if a new user is added, it should be automatically added to all computers and have the same rights on all of them. If a new printer is added to the network, it should get configured in an identical manner on all computers etc.

* Make dist-upgrade in a painless manner: I am a bit concerned about this one since I had been using Ubuntu privately for quite a while now (on several computers) and ALWAYS had problems with the dist-upgrade. This would of course be totally unacceptable in a situation with many centrally administrated computers.

Can somebody point me in the right direction for how all this is supported in Ubuntu or tell me if it is supported at all?

I am talking about this on a more theoretical level for now as we are still in the planning phase and not sure about the OS to go with, but in order to make a decision for any OS, all thses issues must be demonstratable on a small sample installation here.

---

### Post by jeffus_il on 2008-01-18
[LIST]
[*]You can make you own installation disk from your installation.
[*]  Use desktop locking facilities to deny access to certain features.
[*] You may have an installation problem if the hardware differs lots from computer to computer, if you can standardize on hardware  it could be simple.
[*] You can manage your own repository, thereby controlling updates.
[*] Avahi Zeroconf will automatically pick up added services on your network.
[*] Centralized authorization can be done through NIS or LDAP, see : [http://www.linuxjournal.com/article/7334](http://www.linuxjournal.com/article/7334)[/LIST]

---

### Post by johann_p on 2008-01-18
> **jeffus_il said:**
> You can make you own installation disk from your installation, and use desktop locking facilities to deny access to certain features. You may have an installation problem if the hardware differs lots from computer to computer, if you can standardize on hardware  it could be simple.
Can you point me to some documentation or similar about how to do this right? 

I was wondering what the best place is to learn about how to administer Ubuntu in a situation where one has to keep a number of ideantical end-user desktop running and up-to-date?

---

### Post by jeffus_il on 2008-01-18
[LIST]
[*]You can make you own installation disk from your installation. Try this : [http://uck.sourceforge.net/](http://uck.sourceforge.net/)
[*]  Use desktop locking facilities to deny access to certain features. (Look at the Gnome Lockdown Editor)
[*] You may have an installation problem if the hardware differs lots from computer to computer, if you can standardize on hardware  it could be simple.
[*] You can manage your own repository, thereby controlling updates. [http://www.go2linux.org/aptoncd-create-your-debian-ubuntu-repository-on-CD-or-ISO](http://www.go2linux.org/aptoncd-create-your-debian-ubuntu-repository-on-CD-or-ISO)
[*] Avahi Zeroconf will automatically pick up added services on your network.
[*] Centralized authorization can be done through NIS or LDAP, see : [http://www.linuxjournal.com/article/7334](http://www.linuxjournal.com/article/7334)[/LIST]

---

### Post by johann_p on 2008-01-18
> **jeffus_il said:**
> [LIST]
[*]You can make you own installation disk from your installation. Try this : [http://uck.sourceforge.net/](http://uck.sourceforge.net/)
[*]  Use desktop locking facilities to deny access to certain features.
[*] You may have an installation problem if the hardware differs lots from computer to computer, if you can standardize on hardware  it could be simple.
[*] You can manage your own repository, thereby controlling updates.
[*] Avahi Zeroconf will automatically pick up added services on your network.
[*] Centralized authorization can be done through NIS or LDAP, see : [http://www.linuxjournal.com/article/7334](http://www.linuxjournal.com/article/7334)[/LIST]

Thanks for all these hints, but does that mean that what I originally had in mind is not possible (except for the custom-made installation disk)?

The biggest issue is how to keep all these computers in sync. These will be computers used by a group of developers and all of them should be able to do everything on each of the computers.

It will happen frequently that some new package needs to be installed, be it an Ubuntu package or something from cpan or a ruby gem, or a R package etc.

In all these cases it would be necessary for the admin to run some command on all these machines -- my question was whether there is any support or automatism to let the administrator do this automatically and systematically in a documented way instead of logging into each machine and doing it manually or with self-hacked scripts?

Is there any documented system support for remotely and/or automatically doing all these administrative steps on many PCs in parallel or in sequence?

---

### Post by jeffus_il on 2008-01-18
> **johann_p said:**
> Thanks for all these hints, but does that mean that what I originally had in mind is not possible (except for the custom-made installation disk)?

The biggest issue is how to keep all these computers in sync. These will be computers used by a group of developers and all of them should be able to do everything on each of the computers.

It will happen frequently that some new package needs to be installed, be it an Ubuntu package or something from cpan or a ruby gem, or a R package etc.

In all these cases it would be necessary for the admin to run some command on all these machines -- my question was whether there is any support or automatism to let the administrator do this automatically and systematically in a documented way instead of logging into each machine and doing it manually or with self-hacked scripts?

Is there any documented system support for remotely and/or automatically doing all these administrative steps on many PCs in parallel or in sequence?

If you build your own sofware repository on a server machine on your network, you can configure the automatic updating facility on each machine to only access your repository, not the ubuntu servers and mirrors on the internet, thereby controlling what applications are getting updated. (just like ubuntu controls the applications that we update on our installed versions, it is not difficult, just open a tool like synaptic, look at the repositories, look at the different levels e.g. universe, main, multiverse, the mechanism which you can implement can be viewed online againt the ubuntu repositories, all well tested at a world wide level.

---

### Post by scorp123 on 2008-01-18
> **johann_p said:**
>  * Create some script or configuration files that provide a standard-installation that differs from what the default installation does - automate it so that only at specific points manual intervention is needed.  [https://help.ubuntu.com/6.10/ubuntu/installation-guide/hppa/automatic-install.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/hppa/automatic-install.html)
Or you could use "RemasterSys", e.g. you install a "pilot client" the way you wish, create a bootable image with RemasterSys, and every client would be identical to the "pilot client" if installed from that CD or DVD:
[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)

> **johann_p said:**
>  * Make it easy to perform the same installation and configuration steps on groups of computers. Essentially the administrator should be able to install packages, perl cpan packages, ruby gems, separate software so that the very same actions are taken on all or a group of the computers automatically (it wouldnt be feasable that he goes around and reapeats the same steps on dozens or hundreds of computers)  RHEL has very nice features in that regard. But you asked about Ubuntu. How about this: [http://sourceforge.net/projects/clusterssh/](http://sourceforge.net/projects/clusterssh/)
ClusterSSH is in the repos (package "clusterssh") and it's OK for issueing commands to let's say a dozen or so machines at the same time. A more elaborate method would be this:
[http://www.cfengine.org/](http://www.cfengine.org/)

> **johann_p said:**
>  * Don't let end users mess with the configuration:  Standard users can't do that anyway. Just don't add any users to the "admin" group on each Ubuntu installation and they can't use "sudo", they can't get into the "root" account, they can't add, remove or update software ... Per default the first user account that you define during a standard Ubuntu installation is automatically added to the "admin" group, all following users are not anymore. So when I install an Ubuntu machine, the first user I define is the "System Administrator" 'sysadmin' account (and because that account can get into "root" the normal users don't know the password here), all other users which were added later are not members of the "admin" group and therefore can't mess with the system in any way (they can change their wallpapers ... but even that could be locked down if you want to).

> **johann_p said:**
>  end users should not be able to do any configuration changes unless explicitly authorized by the administrator.  Wrong. In a corporate environment end-users have no business whatsoever touching the system configuration ever. That's the job of the IT staff and the system administrators.

> **johann_p said:**
>  This includes especially the update-manager: * updates should be carried out by the administrator only: there should be no notification of security updates or similar on the desktop of end-users.  Non-admin users never ever get to see this thing. It doesn't even pop-up in their default desktop. (... last time I checked ...)

> **johann_p said:**
>   The administrator should be able to easily do security updates on all the computers simultanously and automatically.  A customer company I recently did work for had Debian on their desktops. Their PC's do "apt-get update && apt-get upgrade" automagically during system boot. Voila, done. Your admin can write such a script once and then deploy it on all clients, and they would then auto-update themselves every time the user turns on their machine Monday morning ...

I did the same thing with my wife's PC so I don't have to bother with checking her machine for missing updates :)

> **johann_p said:**
>  * Use a server-based authentification scheme  You want LDAP. There are various possibilities here, both "free + opensource" and "non-free + closed source". Free solutions:
- OpenLDAP, [http://www.openldap.org](http://www.openldap.org)

Also check out this tutorial here:
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

Same tutorial on "How to forge" (looks better here IMHO):
[http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10](http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10)

Related tutorials:

[https://help.ubuntu.com/community/AutofsLDAP](https://help.ubuntu.com/community/AutofsLDAP)
[http://www.howtoforge.com/linux_ldap_authentication](http://www.howtoforge.com/linux_ldap_authentication)
[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

Other free solutions (based on OpenLDAP):
[http://directory.fedoraproject.org/](http://directory.fedoraproject.org/)

Non-free solutions:

[http://www.sun.com/software/products/directory_srvr_ee/index.jsp](http://www.sun.com/software/products/directory_srvr_ee/index.jsp)
[http://www.novell.com/products/edirectory/](http://www.novell.com/products/edirectory/)
[http://www.redhat.com/directory_server/](http://www.redhat.com/directory_server/)

> **johann_p said:**
>  and allow users to share server-based resources like raid storage, printers, etc. while these resources should be administrateable centrally. So if a new user is added, it should be automatically added to all computers and have the same rights on all of them. If a new printer is added to the network, it should get configured in an identical manner on all computers etc.  See above. SAMBA for file sharing, LDAP for user account management and authentication.

> **johann_p said:**
>  * Make dist-upgrade in a painless manner:  Wrong. In a corporate environment you don't do that. Never ever. Unless the OS's on the machines become so hopelessly outdated that the users can't work on them anymore. There should be a "Lifecycle management" in place where you clearly define what's too old and what's not, when does get what replaced with what, and when will new software and OS versions be introduced or not ... 

That's exactly why some companies pick distros such as RHEL or SLES ... Those distros don't change every few weeks or months, they stay the same over several years. And for a company that's *good*, because it means *stability*

> **johann_p said:**
>  This would of course be totally unacceptable in a situation with many centrally administrated computers.  Exactly, and that's why you don't do such distro upgrades (e.g. from Gutsy => Hardy). This needs proper planning.

Getting the machines to automatically download the latest patches can be very much scripted and automated though. There are examples on the web on how to do this.

Hope this posting helped.

---

### Post by jeffus_il on 2008-01-18
[LIST]
[*]You can make you own installation disk from your installation. Try this : [http://uck.sourceforge.net/](http://uck.sourceforge.net/)
[*]  Use desktop locking facilities to deny access to certain features. (Look at the Gnome Lockdown Editor)
[*] You may have an installation problem if the hardware differs lots from computer to computer, if you can standardize on hardware  it could be simple.
[*] You can manage your own repository, thereby controlling updates. [http://www.go2linux.org/aptoncd-create-your-debian-ubuntu-repository-on-CD-or-ISO](http://www.go2linux.org/aptoncd-create-your-debian-ubuntu-repository-on-CD-or-ISO)
[*] Avahi Zeroconf will automatically pick up added services on your network.
[*] Centralized authorization can be done through NIS or LDAP, see : [http://www.linuxjournal.com/article/7334](http://www.linuxjournal.com/article/7334)[/LIST]

---

### Post by jeffus_il on 2008-01-18
Most of all, you have this forum backing you! (thanks scorp123!)

---

### Post by Mingos on 2008-01-18
You might want to consider using disk-images. I haven't used them myself, but I recently talked to someone who does, and it sounded quite good:

Every desktop has a separate / and /home partition and they made an image of / with all the configuration they need. 

The /home partition is backed up every night to a central server and when they want to change something in the system (e.g. install something), they test it first, then make a new image, which is sent out to the desktops during the night.

He even told me that when someone calls them with a problem, they don't bother looking at it: they just renew the image (which takes about ten minutes).

As I said, i dont know the technical details on how exactly they've done it, but since you're still in the planning phase, it may be useful.

---

### Post by scorp123 on 2008-01-18
> **Mingos said:**
>  You might want to consider using disk-images.  Not necessary. You can just boot the client over the internal LAN, e.g. via a PXE or TFTP server.

Full disk images are a waste of space and bandwidth because they also contain those parts of the disk which don't contain any data.

> **Mingos said:**
>  Every desktop has a separate / and /home partition and they made an image of / with all the configuration they need.  See my posting above. You'd do that maybe for the absolutely first installation of the "pilot client" (the prototype). All following client installations are an exact copy of that one, so I don't need a disk image of every client computer. I just need a copy of the prototype and that's it. All the other machines are identical to this one, so there is nothing to copy anyway.

All that is left to do is to implement a nice network backup solution which gets each user's /home directories and stores them someplace safe.

> **Mingos said:**
>  ... and when they want to change something in the system (e.g. install something), they test it first, then make a new image, which is sent out to the desktops during the night.  There are commercial solutions such as Novell's ZenWorks which do that:
[http://www.novell.com/products/zenworks/](http://www.novell.com/products/zenworks/)
[http://www.novell.com/products/zenworks/desktops/](http://www.novell.com/products/zenworks/desktops/)

Or you use free tools such as "cfengine" and do it that way.

> **Mingos said:**
>  He even told me that when someone calls them with a problem, they don't bother looking at it: they just renew the image (which takes about ten minutes).  That depends I guess :)  If the problem is OS related, then yes, just give the user a working OS image again and you're done. But if the problem is in the user's file somewhere somehow then doing a full-reset won't help you. And don't even think about completely resetting a user's settings ... he will hate you forever and working in an environment where everybody hates the IT staff is no fun. It's contra-productive. So always be on good terms with your users. :)

> **Mingos said:**
>  As I said, i dont know the technical details on how exactly they've done it  If I had to guess: I'd say they use Novell ZenWorks. What you described at least pretty much sounds like it. And the nice thing is it works with a wide range of client OS'es.

---

### Post by Mingos on 2008-01-18
>  Full disk images are a waste of space and bandwidth because they also contain those parts of the disk which don't contain any data. 

You're right, but I don't know if they used full images or maybe something like PartImage, which creates images only containing data, not empty space

>  You'd do that maybe for the absolutely first installation of the "pilot client" (the prototype). All following client installations are an exact copy of that one.

Yes, that's what I meant, maybe I wasn't clear. 

> 
That depends I guess :)  If the problem is OS related, then yes, just give the user a working OS image again and you're done. But if the problem is in the user's file somewhere somehow then doing a full-reset won't help you.

True, but you can  rule out a system error and you also have a backup of the /home partition from the night before, so you can focus on that.

>  If I had to guess: I'd say they use Novell ZenWorks. What you described at least pretty much sounds like it. And the nice thing is it works with a wide range of client OS'es.

I believe they're only using free tools, but I could be wrong of course :-)

---

### Post by scorp123 on 2008-01-18
> **Mingos said:**
>  I believe they're only using free tools, but I could be wrong of course :-) Oh, nice! Can you ask your friend a little more about their setup and which tools / projects etc. they're using? I guess this would be interesting to many folks here coming to this thread! :)

---

### Post by koenn on 2008-01-18
> **johann_p said:**
> 
* Create some script or configuration files that provide a standard-installation that differs from what the default installation does - automate it so that only at specific points manual intervention is needed.
OpenSuse has the option to save all the responses given to the installer in a config file that can then be used at later installations to automate the process. Is this possible in Ubuntu?


here's an intro to (scripted) automatic custom setups. 
[http://users.telenet.be/mydotcom/howto/linux/ubuntuexpert.htm](http://users.telenet.be/mydotcom/howto/linux/ubuntuexpert.htm)
[http://users.telenet.be/mydotcom/howto/linux/automatic.htm](http://users.telenet.be/mydotcom/howto/linux/automatic.htm)

I don't like disk images really, they only work well if you can standardise your hardware.

---

### Post by koenn on 2008-01-18
> **johann_p said:**
> 
* Make it easy to perform the same installation and configuration steps on groups of computers. Essentially the administrator should be able to install packages, perl cpan packages, ruby gems, separate software so that the very same actions are taken on all or a group of the computers automatically (it wouldnt be feasable that he goes around and reapeats the same steps on dozens or hundreds of computers)

I don't know how this is done in real life, but on the few computers I have around the house, I do things like
```

## copy files, eg scripts or other stuff you want on each computer
for TARGET in $(cat list_of_computers); do
    scp  /path/to/file  user@$TARGET:/path/to/destination
done

```
```

## execute commands remotely, eg apt-get or scripts
$USER="root"
for TARGET in $(cat list_of_computers) ; do
        ssh $USER@$TARGET << eof
                apt-get update
                apt-get -y upgrade
                ##
                cd /tmp
                wget http://intranet/scripts/customscript
                ./customscript
eof
done

```
you'll be prompted for a password, You can avoid that by setting up ssh with host-based authentication (key pairs).
If you create groups by maintaining a number of lists with the member computers in it, I think it's quite possible to get remote administration and software distribution organized with some scripts and some text files. Again, the more you standardisz, the easier it gets to maintain.

---

### Post by mmichalik on 2008-01-18
You can always us LTSP on Ubuntu.

Here is a brief description of it off of [www.ubuntu.com/products/WhatIsUbuntu/serveredition](www.ubuntu.com/products/WhatIsUbuntu/serveredition)

Ubuntu Server edition includes thin client support using LTSP (Linux Terminal Server Project). LTSP-5, the latest release, offers a simple installation and easy maintenance. All the data is stored on the server, which will substantially diminish the cost of updating individual workstations and help to ensure their security. Notable benefits of Ubuntu's thin client support are:

    * Simplified management: manage all clients from one system. Install new software, change their configuration, or even upgrade to a new version on the server, and all clients are instantly up to date. There is only one backup to take for all clients.
    * Fully automatic installation and setup: installing a thin client server is as easy as installing a single desktop system, and once it's finished, new clients can be added with no additional administration on the server
    * Lower TCO through shared resources: Common high-powered desktop workstations sit idle most of the day consuming power and costing your organization money. With a high-powered server and low-cost thin clients, you can get great performance and save money. Need higher performance? Just upgrade the server, and all clients instantly benefit.
    * Quick failure recovery: If a client system fails, simply swap in a new one and continue working. No configuration is required, and all of the user's data and settings are intact.
    * Locally attached devices: Users can access printers, cameras, iPods, USB sticks and other devices connected directly to the thin client.

---

### Post by scorp123 on 2008-01-18
> **koenn said:**
>  scp  /path/to/file  user@$TARGET:/path/to/destination  Not good. Your "scp" command there totally ignores file permissions. And if you copy a file which in fact is a symbolic link your "scp" up there will make sure that you don't get a symbolic link on your target system but rather the full file ... again. Which is probably not intended (that's why sometimes symbolic links are used so you don't have the same file taking up filesystem space twice when it's only really needed once ...)

If you do something like that it would be better to use "rsync". This would have the advantage that only missing or updated files get copied, and not the whole thing. Your "scp" command up there would always copy the entire truck load ... which isn't really bandwidth friendly. That's maybe OK if you copy stuff from and to 5 or so PC's around your house, but if you sync 300 systems like that on a corporate LAN then us system admins will go berserk on you and skin you alive. :)

So it's better to use "rsync" ... if at all:
```
rsync -avz  /path/to/local/source/files/*  user@remotesystem:/path/to/remote/destination/files

```

Also, if you need systems to be identical you can tell the package manager to do that for you. Read here:
[http://linuxmint.com/forum/viewtopic.php?p=25955#p25955](http://linuxmint.com/forum/viewtopic.php?p=25955#p25955)

You might mostly be interested in this section there:
**"Step 3: Our package selections"**
--and--
**"How to restore your package selections"**

Basically those few simple commands there will help you easily create two identical systems by telling one system to save all its package catalogue to a file and telling the other system to go and read that catalogue and then install the same packages that were present on that first system.

Armed with those few commands and a fast Internet connection you can clone a PC in a couple of minutes.

And if you don't have a fast Internet connection, you could still use programs such as **"AptOnCD"** or **"RemasterSys"**.
[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)
[http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html](http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html)

With those two packages too you can install one PC and then clone the rest with the help of those CD or DVD's (so you don't have to download the same packages again and again and again from your Internet link).

---

### Post by thk on 2008-01-18
While I'd like to say "yes," Ubu is not ready for this sort of application. LDAP is [severely broken]("https://launchpad.net/ubuntu/+bugs?field.searchtext=ldap&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=") in Gutsy. Working LDAP clients upgraded from feisty will hang on boot. The bug is in the Debian LDAP packages and there is a patch available. Its the most outrageous hack I've seen in a long time. Until Ubu has a fully integrated and supported directory server, its near useless in a large network environment.

Your best bet might be the Linux Terminal Server Project which has had some decent integration with Ubu. Netboot the clients off a server image and have apps run local on the clients.

---

### Post by koenn on 2008-01-19
> **scorp123 said:**
> Not good.
You're jumping to conclusions. In that scp example I meant to illustrate how you can get a file to a number of computers easily - be it a certain customized configuration file, a script to be executed later by cron, or whatever. I trust the OP is intelligent enough to 'man scp' and read up on scp switches, eg those that deal with permissions, and work out the details. 

for syncing  directories, multiple files, symlinks etc, rsync is indeed a better alternative, but the advantage that rsync only copies delta doesn't do much for something you copy only once.

---

### Post by Mingos on 2008-01-19
> **scorp123 said:**
> Oh, nice! Can you ask your friend a little more about their setup and which tools / projects etc. they're using? I guess this would be interesting to many folks here coming to this thread! :)

I only talked to him once, so calling him a friend would be a bit overstated :-) but I'll try and contact him.

---

### Post by HermanAB on 2008-01-19
With a little bit of effort, you can do everything you want to do.  Linux machines requires less administration than Windows machines, which is why no-one bothered to make a Linux equivalent of Active Directory - it simply isn't needed.

You can do central authentication with NIS which is LDAP, which is exactly the system that MS used to build the AD wizard on.

You can also manage machines very easily using Webmin, so between NIS and Webmin, you have AD.

---

### Post by UbuWu on 2008-01-19
Landscape would be perfect for most of this. It is still in beta, but you could sign up for the testing program:

[http://www.canonical.com/projects/landscape](http://www.canonical.com/projects/landscape)

---

### Post by mmichalik on 2008-01-21
UbuWu, that's pretty amazing and JUST what I am looking for!

Thanks for putting that out here.

---

### Post by johann_p on 2008-01-21
Thank you for the landscape pointer, that looks very interesting. I hope it will become available soon.

---

### Post by scorp123 on 2008-01-21
> **johann_p said:**
> Thank you for the landscape pointer, that looks very interesting. I hope it will become available soon. RHEL 5 already has something like this in place :)

But me too would like to have "Landscape" for my many Ubuntu installations. :)

---

### Post by Mingos on 2008-01-25
> **scorp123 said:**
> Oh, nice! Can you ask your friend a little more about their setup and which tools / projects etc. they're using? I guess this would be interesting to many folks here coming to this thread! :)

If you're still interested, this is a summary of how they do it (it's a bit different then I remembered):

They keep their /home partitions on a central server, which gets mounted through pam_mount. Which basically means the desktop boots normally until the login screen and after login /home is mounted from the server. They use Samba, because they still have a few Windows machines on their network.

The desktops are setup, so that they can bootup from the network through PXE-boot. The user has a few seconds to hit the keyboard and then it boots from the network. If they don't do that, it will boot normally from the harddisk.

When a desktop boots from the network, they have a script in place which copies an image of the partition from the server to the desktop, using dd. That takes about 5 minutes.

For installation and upgrading they have a seperate desktop, on which they
test things first. When everything's OK, they make a new image which can be spread around the network.

---

### Post by scorp123 on 2008-01-25
> **Mingos said:**
> If you're still interested, this is a summary of how they do it  ... . Thanks, I thought it must be something like this. I am working on something similar at the moment. :)

---

