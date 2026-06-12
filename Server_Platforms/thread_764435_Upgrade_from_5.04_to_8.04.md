---
title: "Upgrade from 5.04 to 8.04"
date: 2008-04-23
forum: Server Platforms
---

### Post by thorndike on 2008-04-23
Good evening all,

I have two servers still running 5.04 because of the support for the old megaraid raid driver that was removed in 5.10 on.  It now appears the 8.04 is using the correct driver as it recognizes the RAID on the development server.

I would like to know if there is an upgrade path that I can follow to bring these boxes up to current LTS levels.  My main concern in installing the 'in-between' versions which don't support the RAID and then getting up to 8.04.  I assume that since it is hardware RAID there will be no problem, but since these are production servers I need to get the procedure down correctly on the development box.

Any and all help would be greatly appreciated.

Thorndike

---

### Post by tamoneya on 2008-04-23
following the upgrade method is going to be very unsupported and iffy.  I would recommend that you just do a reinstall from scratch.  If you try the upgrade from 5.04 you are just asking for problem.

---

### Post by analoog on 2008-04-24
yeah like said above, this is asking for problems.

Maybe it's an idea (that I would test before doing, so that you don't mess up the production server) to upgrade to 6.06. Ubuntu-server is supported till 2011 with the 6.06 (dapper drake) release (and the normal ubuntu till 2009). 
I'm not sure of this (so you have to test!) but I don't think an upgrade will remove a driver that is currently used by the system??

If you want the LTS release it's best to start from scratch.

---

### Post by thorndike on 2008-04-25
I appreciate all the information.  I figured that I would have to do a clean install.  

The servers in question are set as Domain Servers via Samba.  If I do a complete reinstall I know I can copy my smb.conf file over, but what about the smbpasswd file and the passwd file?  Will I have to go to each XP PC and reconnect to the new domain?  If I do that, I am going to lose the domain profiles on each PC thus making more work for me and my clients VERY unhappy.

Thoughts?

Thorndike

---

### Post by XioNoX on 2008-04-25
if you do a upgrade to 6.06 and then to 8.04, and if your raid driver is in the kernel and if you keep your configuration files, you should be able to upgrade without too many problems (specially if you don't have exotic packages)

---

### Post by p_quarles on 2008-04-26
Actually, the answer is definitely no. In order to upgrade to any version after 5.04, you would first have to upgrade to 5.10, which is no longer supported. Because there are no repositories for the 5.10 release, there isn't an upgrade path.

---

### Post by nanog on 2008-04-27
Upgrade paths smushgrade paths.

Just edit your sources to dapper and sudo apt-get dist-upgrade.

---

### Post by p_quarles on 2008-04-27
> **nanog said:**
> Upgrade paths smushgrade paths.

Just edit your sources to dapper and sudo apt-get dist-upgrade.
I assume that in making this suggestion, you are also pledging to be around to help should this lead to any serious problems. Right? If not, please don't recommend completely unsupported procedures.

---

### Post by Brazen on 2008-04-28
Why not just set up a BDC and promote it to a PDC?

This might be a good time to switch to using an LDAP backend, and also to using virtual machines instead of installing your servers directly onto hardware.  Also, be careful just copying over your smb.conf as some options may have changed and some defaults may have changed.  Most likely, and changes would not a detrimental affect on using your existing smb.conf, but I would still thoroughly read over the smb.conf man page and double-check all entries.

---

### Post by Oldsoldier2003 on 2008-04-28
> **Brazen said:**
> Why not just set up a BDC and promote it to a PDC?

This might be a good time to switch to using an LDAP backend, and also to using virtual machines instead of installing your servers directly onto hardware.  Also, be careful just copying over your smb.conf as some options may have changed and some defaults may have changed.  Most likely, and changes would not a detrimental affect on using your existing smb.conf, but I would still thoroughly read over the smb.conf man page and double-check all entries.

+1 This is the best suggestion in my opinion. By setting up a BDC and testing it , then promoting it to PDC you remove a lot of risk and minimize the potential for downtime.

---

### Post by thorndike on 2008-04-29
Interesting ideas...

I like the sound of BDC to PDC...  That would add my development server into the rotation which isnt a perfect solution, but doable as long as I am able to migrate the original servers back into production.  I have never done this before, but will have to browse the SAMBA docs to see what is involved.

---

### Post by rendon on 2008-04-29
I've only read the first page here, and I don't know where you're at with this now, but I just wanted to throw in my 2 cents about this topic as I have a little experience.

I have upgraded both a laptop and a server from aprx 5~6 to 7.10 and they were both horrible experiences.  I wouldn't want to imagine going from 5 to 8.  Even if you upgrade to Feisty first, you might find things get trickier after that, something dramatic seemed to change after Feisty, I was reading forums all day long about this for a while, everyone seemed to agree that previous upgrades were easy, but after Fiesty it got weird for a lot of people.

I would recommend taking the extra time needed to do a clean install.

---

