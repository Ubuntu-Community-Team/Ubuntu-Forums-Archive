---
title: "samba-ad-dc.override to fix &quot;SMB/CIFS File and Active Directory Server&quot; fail to start"
date: 2015-06-19
forum: Server Platforms
---

### Post by Marc-NJ on 2015-06-19
According to this post ([http://askubuntu.com/questions/455418/samba-started-twice-on-boot-up-after-upgrade-to-14-04](http://askubuntu.com/questions/455418/samba-started-twice-on-boot-up-after-upgrade-to-14-04)), you can run "echo manual | tee /etc/init/samba-ad-dc.override" in order to create a file and fix the issue with one of the two listed "SMB/CIFS File and Active Directory Server" failing to start on initial boot.  


I followed these instructions, and it did indeed get rid of the "SMB/CIFS File and Active Directory Server" listing that was showing up as [fail] - in fact I think it got rid of both "SMB/CIFS File and Active Directory Server" listings.


However, according to the last comment on that above link, the samba-ad-dc.override could actually have other contents in it - was just wondering what else might be put in that file and what it might accomplish?


Thanks!

---

### Post by bab1 on 2015-06-19
> **Marc_Bressman said:**
> According to this post ([http://askubuntu.com/questions/455418/samba-started-twice-on-boot-up-after-upgrade-to-14-04](http://askubuntu.com/questions/455418/samba-started-twice-on-boot-up-after-upgrade-to-14-04)), you can run "echo manual | tee /etc/init/samba-ad-dc.override" in order to create a file and fix the issue with one of the two listed "SMB/CIFS File and Active Directory Server" failing to start on initial boot.  


I followed these instructions, and it did indeed get rid of the "SMB/CIFS File and Active Directory Server" listing that was showing up as [fail] - in fact I think it got rid of both "SMB/CIFS File and Active Directory Server" listings.


However, according to the last comment on that above link, the samba-ad-dc.override could actually have other contents in it - was just wondering what else might be put in that file and what it might accomplish?


Thanks!

What is the role of the Samba server in your network?  Is it to be the AD-DC or Is it to be a member server user for file shares?  How did you install Samba (tasksel or ..)?  How did you configure this server; what steps did you take?

The answer you refer to in the link is incorrect in stating this: "Per default samba active directory and domain controller service will be started in addition to smbd and nmbd"  The default is either Active Directory Domain Controller or smbd and nmbd (the file server component).  With Ubuntu, the default package install is for a standalone file server only -- no Active Directory.

Can you point out exactly what you meant by  "..according to the last comment on that above link, the samba-ad-dc.override could actually have other contents in it "  I don't see that at all.

---

### Post by Marc-NJ on 2015-06-19
> **bab1 said:**
> What is the role of the Samba server in your network?  Is it to be the AD-DC or Is it to be a member server user for file shares?  How did you install Samba (tasksel or ..)?  How did you configure this server; what steps did you take?

The answer you refer to in the link is incorrect in stating this: "Per default samba active directory and domain controller service will be started in addition to smbd and nmbd"  The default is either Active Directory Domain Controller or smbd and nmbd (the file server component).  With Ubuntu, the default package install is for a standalone file server only -- no Active Directory.

Can you point out exactly what you meant by  "..according to the last comment on that above link, the samba-ad-dc.override could actually have other contents in it "  I don't see that at all.

It is definitely not to be the AD-DC (although in the future it's possible I might want to do this so I don't want to do anything that would completely eliminate that option if at all possible).  Basically, the role is just to allow file shares.  

As far as how I installed Samba, I just did it during the initial set-up of Ubuntu 14.04.2 when it asked what packages I wanted to install - I selected openSSH server, LAMP server, Samba, and Print server.  Beyond that, I wasn't given the option to make any further selections, and when the system was fully installed it appeared to have installed Samba as an AD-DC.  I even tested by doing another fresh/clean install of Ubuntu 14.04.2 Server on a VirtualBox machine (on my Win8.1 laptop), and made the same selections during installation, and had the same thing happen after it was fully installed.

Given that, I don't see how the default package install for Samba isn't AD-DC.  I know on Ubuntu Server 12.04 it installed an older version of Samba as just a file share server, but apparently with v14.04, the default appears to be to install as AD-DC.  However, it does appear that adding that /etc/init/samba-ad-dc.override file disables the AD-DC portion of Samba - does that seem right?  

My additional question is just that according to the last comment that was made on that link ("overwriting the file if it already exists."), there seems to be an implication there that the samba-ad-dc.override file might already exist with some other contents in it (not just the word "manual") and that following those instructions would overwrite the file with a new one that just contained the word "manual" - so I was wondering what else this file might contain and what would it do with different information in it?

But also, if someone can confirm that creating this samba-ad-dc.override file with just "manual" in it will disable the AD-DC portion of Samba (but keep the file share portion of it active), that'd be great also!

Thanks!

---

### Post by bab1 on 2015-06-19
> **Marc_Bressman said:**
> It is definitely not to be the AD-DC (although in the future it's possible I might want to do this so I don't want to do anything that would completely eliminate that option if at all possible).  Basically, the role is just to allow file shares.  

As far as how I installed Samba, I just did it during the initial set-up of Ubuntu 14.04.2 when it asked what packages I wanted to install - I selected openSSH server, LAMP server, Samba, and Print server.  Beyond that, I wasn't given the option to make any further selections, and when the system was fully installed it appeared to have installed Samba as an AD-DC.  I even tested by doing another fresh/clean install of Ubuntu 14.04.2 Server on a VirtualBox machine (on my Win8.1 laptop), and made the same selections during installation, and had the same thing happen after it was fully installed.

Given that, I don't see how the default package install for Samba isn't AD-DC.  I know on Ubuntu Server 12.04 it installed an older version of Samba as just a file share server, but apparently with v14.04, the default appears to be to install as AD-DC.  However, it does appear that adding that /etc/init/samba-ad-dc.override file disables the AD-DC portion of Samba - does that seem right?  

This confirms the experience I have seen in the past when Samba is installed using the "tasksel" installer.  This is the assumption that the user wishes to install Samba as a AD-DC install.  You could have installed Ubuntu server without selecting Samba.  Then you could have installed Samba using the apt-get package manager.  This installer assumes that you are installing Samba as a stand alone file server.  In this case the ***samba-ad-dc.conf *** file is correctly configured to start the smbd and nmbd processes without starting the ***samba *** process for AD_DC.  At the present time Samba v4 can't be used as both a AD-DC and a file share server (standalone).  This is because of legacy problems and Samba.org is working on the problem.  This is noted in the introduction of the [**Samba AD-DC Howto**]("https://wiki.samba.org/index.php/Samba_AD_DC_HOWTO") at the Samba.org wiki site.

Your problem is more a matter of the package maintainer assuming that if you are installing Samba through the Ubuntu Cerver install you must want to have a Samba AD-DC.  Since you have this already installed you may not want to un-install, but that is what I would do.  For the time being the rule of thumb should be:*If you want a file server only (standalone) install Samba using this comman*```
sudo apt-get install samba
```
If you want a AD-DC you can either run the tasksel installer or use apt-get and run the appropriate script to upgrade the install to Samba AD-DC.
> 

My additional question is just that according to the last comment that was made on that link ("overwriting the file if it already exists."), there seems to be an implication there that the samba-ad-dc.override file might already exist with some other contents in it (not just the word "manual") and that following those instructions would overwrite the file with a new one that just contained the word "manual" - so I was wondering what else this file might contain and what would it do with different information in it?

But also, if someone can confirm that creating this samba-ad-dc.override file with just "manual" in it will disable the AD-DC portion of Samba (but keep the file share portion of it active), that'd be great also!

Thanks!
Unfortunately your assumptions are not correct for the current Samba v4 or specifically the package installer the Ubuntu uses to install.  You can have zero byte files.  The writer was only stating that if a file exists you can overwrite it. But that writer is wrong to begin with, so I wouldn't trust the written word anyway.  ;-)

In short Samba v4 currently allows AD_DC or file server but not both.  Plus you unfortunately used an installer that assumes you wanted a AD-DC install.  Your hack is a poor option in my opinion, but I don't know how committed you are with your install.

This is a long an complicated response so I may have not made myself clear.  If you have questions please feel free to ask!

---

### Post by Marc-NJ on 2015-06-19
Bab1 - Thank you SO much for your long and detailed response!  That's why I love forums like this - you can get so much great information from others!

So, basically, here's my follow-up question.  This server that I'm setting up is a replacement for a 12.04 that had HD corruption on it (and that I never set up in a very redundant fashion anyway - this new one has 2 x 4 TB in a RAID1 array plus a 6 TB drive for backups, plus it will have cloud backup, plus the HD's are enterprise-class, so hopefully I'm good -> although I have another topic on here about what kind of backup strategy to implement and what to back up exactly since there are gaps in my Linux knowledge).

Anyway, back to my point - I'm just in the very beginning phases of setting up this new 14.04 server, and have no data on it and very little config done.  Do you think it's worth it to just wipe it out and reinstall fresh without selecting Samba from the initial installation and then just installing it afterwards?  Or do you think I can uninstall Samba now using the appropriate commands, get it fully removed, and then reinstall it so that it functions as a stand-alone file server and not an AD-DC?  And if so, would I just use apt-get to remove it, or since I installed it using the "tasksel" installer is there some other way I should remove it initially?

And in the future, if I ever do want to move to Samba being an AD DC, I guess I'd have to run that appropriate script, right?  What are the right commands to run that script (just for my own reference for the future perhaps)?

Thanks again!

---

### Post by bab1 on 2015-06-19
> **Marc_Bressman said:**
> Bab1 - Thank you SO much for your long and detailed response!  That's why I love forums like this - you can get so much great information from others!

So, basically, here's my follow-up question...

... I'm just in the very beginning phases of setting up this new 14.04 server, and have no data on it and very little config done.  Do you think it's worth it to just wipe it out and reinstall fresh without selecting Samba from the initial installation and then just installing it afterwards?  Or do you think I can uninstall Samba now using the appropriate commands, get it fully removed, and then reinstall it so that it functions as a stand-alone file server and not an AD-DC?  And if so, would I just use apt-get to remove it, or since I installed it using the "tasksel" installer is there some other way I should remove it initially?

And in the future, if I ever do want to move to Samba being an AD DC, I guess I'd have to run that appropriate script, right?  What are the right commands to run that script (just for my own reference for the future perhaps)?

Thanks again!
Since you have a the ability to install in a VM I would try this out first to see what I say works for you.  Install Ubuntu without installing Samba.  Then install Samba via apt-get and see if you can just add file shares.  The only file you need to deal with is /etc/samba/smb.conf.  For a basic install you only need to add the share definitions at the bottom of the smb.conf file.  Read the man pages to see all the parameters available.  If you are going to use Samba professionally you need to spend some time learning what works and what doesn't.  Your experience with this issue should be a tip off.  Samba.org has an extensive listing of documents.  Do not use samba v3 docs specifically but the concept of file sharing is correct.  In fact in a general way Samba v2 the concepts are valid.  This is for ***[COLOR="#0000FF"]smbd and nmbd only.[/COLOR]***

I have never un-installed Samba v4 so I have no idea what lurks just around the corner.  If you can do a complete fresh install I would always go for that.

One last thought.  There is more incorrect info out there than correct.  Some of it is out of date and some is just plain wrong.  Read and understand all that you can find, but take it all in context and with a heavy dose of salt.

Try the new install out and let us know how it goes.

[COLOR="#0000FF"]Edit:  Google ***Samba Domain Provision*** to see how to upgrade to AD-DC.[/COLOR]

---

### Post by Marc-NJ on 2015-08-20
Hi bab1 - not sure if you are still tracking this topic, but if so, I tried to do a samba install on a virtual machine without selecting Samba file server from the tasksel, and it still seems to be putting Active Directory integration in - see here: [http://ubuntuforums.org/showthread.php?t=2291541](http://ubuntuforums.org/showthread.php?t=2291541)

Any help is greatly appreciated!

---

