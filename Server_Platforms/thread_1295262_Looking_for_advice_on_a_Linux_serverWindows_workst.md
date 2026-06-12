---
title: "Looking for advice on a Linux server/Windows workstation network"
date: 2009-10-19
forum: Server Platforms
---

### Post by Vunutus on 2009-10-19
I currently have my network set up and working fine. It consists of one Ubuntu server and about 5 Windows XP workstations. The server runs some pretty basic services for the whole network (MySQL database, apache for intranet, and Samba for file services).

As I said, the network is functioning and working fine, but my problem here is that it just doesn't seem "streamlined". Currently, when I want to add a new system/user to the network, I have to set up their computer, pull down a pre-configured XP clonezilla image, then make several tweaks on the system to get it up and going (adding their user to both the workstation and server, mapping network drives, etc etc).

I've never really dealt with Windows networking before, so I was hoping someone could provide me with some resources to learn about directory services/SSO/roaming profiles/whatever? It's fairly easy to find guides for doing this on a Windows server (which makes sense), but I'm attempting to do this with a Linux (and specifically Ubuntu) server.

Also, it it even feasible to make a seamless transition from my current setup to a more streamlined/standardized one, or is this one of the things where I'll have to bring down the network and work over the weekend?

---

### Post by Pnuts on 2009-10-19
I believe what your looking for is a Windows AD setup.  =[


I think you can take care of having to create multiple accounts by setting up ldap and samba in a domain. This way users could authenticate to the server and it would not matter which desktop they logged on with. You would need to recreate all users once set-up though.

This is an old how-to: [http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10) that I know of, might want to google around fomr something newer or maybe check the official server guide.

I do not know if its possible to auto map drives or not, or set-up roaming profiles.

-Pnuts

---

### Post by Lars Noodén on 2009-10-20
Here is the ubuntu guide to setting up Samba, it should get you started in your migration:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

and some tips on working with the legacy components
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
[http://www.howtoforge.com/ubuntu-9.04-samba-server-integrated-with-active-directory](http://www.howtoforge.com/ubuntu-9.04-samba-server-integrated-with-active-directory)

---

### Post by Vunutus on 2009-10-21
> **Lars Noodén said:**
> Here is the ubuntu guide to setting up Samba, it should get you started in your migration:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

and some tips on working with the legacy components
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
[http://www.howtoforge.com/ubuntu-9.04-samba-server-integrated-with-active-directory](http://www.howtoforge.com/ubuntu-9.04-samba-server-integrated-with-active-directory)

Unfortunately the Ubuntu guide only goes into file/print services, which I've already configured. Nothing else is covered.

After reading a number of guides, I've come to the conclusion that this is much harder than I anticipated. 

I'm going to narrow my goal down to one specific task: I want Windows users on the network to be able to log in with the username and password they have on the Linux server. They can already do this with samba shares, but how do I accomplish this for the whole system?

---

### Post by Lars Noodén on 2009-10-21
> **Vunutus said:**
> I want Windows users on the network to be able to log in with the username and password they have on the Linux server. They can already do this with samba shares, but how do I accomplish this for the whole system?

I'm not sure if I'm interpreting the problem correctly.  

Samba is a separate system.  On the linux server, you have at least two authentication options, /etc/passwd and samba (which itself has separable components).

For the windows users, they use samba to authenticate in your environment in general.  To let them also log in to the linux server (via ssh) then try pointing PAM to samba.    
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/pam.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/pam.html)

If that was the right guess, then the various services (e.g. sudo) will also have to be adjusted for samba authentication.

Secret: there is no whole system.  It is an illusion.

---

### Post by Pnuts on 2009-10-21
This may be exactly the guide your looking for, although it was written for an older version of Ubuntu.

[https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows](https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows))

---

### Post by lykwydchykyn on 2009-10-21
It's just my opinion, but personally I'd steer clear of roaming profiles unless your users absolutely need it.  If the users are at the same workstation the majority of the time, it's just not worth the headache.

If you just want to save yourself some setup/drive mapping/etc., I'd update that WinXP image with some time savers like login scripts and so forth.  For instance, you can set up a generic user account the way you like it, then copy the contents of the user's directory to "C:\Documents and Settings\default user" (It's a hidden folder that basically acts like /etc/skel on *nix).

If you can be very specific about the things you want to do, there are ways of doing them I can almost guarantee, and it's probably simpler than you think.

---

### Post by whoop on 2009-11-07
Most complete up-to-date tutorial on this topic (although written for ubuntu 7.10):
[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)

We need up to date documentation, please **vote**: 
[http://brainstorm.ubuntu.com/idea/22151/](http://brainstorm.ubuntu.com/idea/22151/)

---

