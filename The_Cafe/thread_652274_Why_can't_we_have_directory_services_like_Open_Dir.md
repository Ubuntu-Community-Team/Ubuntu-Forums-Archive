---
title: "Why can't we have directory services like Open Directory (for mac) in Linux?"
date: 2007-12-28
forum: The Cafe
---

### Post by tymiles on 2007-12-28
Why do we not have anything like Open Directory on Linux? 

Open Directory is Apple's implementation of Open Ldap on Mac OS X server. 

Please read below what Open Directory can do and how you can support Windows, Linux and Mac machines using it. 

Please let me know what you think and if there is something out there that can work as well as OD that I am missing. 

Thanks. :-) 

[http://en.wikipedia.org/wiki/Apple_Open_Directory](http://en.wikipedia.org/wiki/Apple_Open_Directory)

[http://www.macdevcenter.com/pub/a/mac/2007/06/01/discover-the-power-of-open-directory.html](http://www.macdevcenter.com/pub/a/mac/2007/06/01/discover-the-power-of-open-directory.html)

[http://images.apple.com/server/macosx/docs/Open_Directory_Admin_v10.5.pdf](http://images.apple.com/server/macosx/docs/Open_Directory_Admin_v10.5.pdf)

(The reason I am pointing out OD is that it uses open source software as it's core)

---

### Post by SunnyRabbiera on 2007-12-28
I thought we did, at least up until now

---

### Post by BDNiner on 2007-12-28
What about the offerings from Novell? We use Netware and Console One to run all our directory services. May not be as feature rich as Active Directory which we are moving away from but does the job none the less. I like the web services from iManager, that way i don't have to log into the server every time i was to reset a password, or increase someone's share drive space.

---

### Post by mmichalik on 2007-12-28
OpenLDAP does basically the same thing, doesn't it?

[http://www.openldap.org/](http://www.openldap.org/)

I am not familiar with the Apple implementation but, I have set up several LDAP servers and integrated them into windows networks and they have worked seamlessly.

---

### Post by rickyjones on 2007-12-28
> **tymiles said:**
> Why do we not have anything like Open Directory on Linux? 

Open Directory is Apple's implementation of Open Ldap on Mac OS X server. 

Please read below what Open Directory can do and how you can support Windows, Linux and Mac machines using it. 

Please let me know what you think and if there is something out there that can work as well as OD that I am missing. 

Thanks. :-) 

[http://en.wikipedia.org/wiki/Apple_Open_Directory](http://en.wikipedia.org/wiki/Apple_Open_Directory)

[http://www.macdevcenter.com/pub/a/mac/2007/06/01/discover-the-power-of-open-directory.html](http://www.macdevcenter.com/pub/a/mac/2007/06/01/discover-the-power-of-open-directory.html)

[http://images.apple.com/server/macosx/docs/Open_Directory_Admin_v10.5.pdf](http://images.apple.com/server/macosx/docs/Open_Directory_Admin_v10.5.pdf)

(The reason I am pointing out OD is that it uses open source software as it's core)

If you want to authenticate Windows/Linux computers against an OpenLDAP directory w/ SAMBA I wrote a tutorial on how to do it.

[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

-Richard

---

### Post by tymiles on 2007-12-28
Thanks everyone. :-) This is good. let me answer a couple of things. 

1. Edirectory is pretty good. Problem for my question is that Edirectory is not open source. Open Directory uses Open Ldap at it's source. So it's something that Linux could look at and copy more easy. 
 

2. Thank you Ricky I have read your doc before. It works well but in reality it's too much work. Also with Open Directory I can manage things point in click out the box like:

Logins
Folder and file access
Home folders
Automount share points
Mail account settings
Managed client information
Group management
GPO's 
Managed network views
Active Directory (you can add Active Directory servers to an Open Directory domain. You can use an OD server as a DC or BDC) 
Network Information System (NIS)
Masters and Replicas
Relays and Cascading Replication
Fail over 
Single Sign On Kerberos
Machine Policies
And more. 

It's easy to set up point and click like AD. I don't want to edit files and know about schemas etc. 

The reason I am bringing this up though because I know it can be done if there was a focus on it in the Linux community. 

3. Open Ldap is good by it's self, Fedora DS is even better. But none of them can do what I listed about out the box without a lot of work.

---

### Post by rickyjones on 2007-12-28
> **tymiles said:**
> Thanks everyone. :-) This is good. let me answer a couple of things. 

1. Edirectory is pretty good. Problem for my question is that Edirectory is not open source. Open Directory uses Open Ldap at it's source. So it's something that Linux could look at and copy more easy. 
 

2. Thank you Ricky I have read your doc before. It works well but in reality it's too much work. Also with Open Directory I can manage things point in click out the box like:

Logins
Folder and file access
Home folders
Automount share points
Mail account settings
Managed client information
Group management
GPO's 
Managed network views
Active Directory (you can add Active Directory servers to an Open Directory domain. You can use an OD server as a DC or BDC) 
Network Information System (NIS)
Masters and Replicas
Relays and Cascading Replication
Fail over 
Single Sign On Kerberos
Machine Policies
And more. 

It's easy to set up point and click like AD. I don't want to edit files and know about schemas etc. 

The reason I am bringing this up though because I know it can be done if there was a focus on it in the Linux community. 

3. Open Ldap is good by it's self, Fedora DS is even better. But none of them can do what I listed about out the box without a lot of work.

I fully agree with all of your points, which is sort of the mentality that I hoped others would get on their own and from my tutorial. The Linux community needs to have something just as easy and ready to use if you want to be highly considered in the corporate world, or even fully considered by small business.

Just my honest opinion there.

-Richard

---

### Post by toupeiro on 2007-12-28
> **rickyjones said:**
> I fully agree with all of your points, which is sort of the mentality that I hoped others would get on their own and from my tutorial. The Linux community needs to have something just as easy and ready to use if you want to be highly considered in the corporate world, or even fully considered by small business.

Just my honest opinion there.

-Richard

Just a little clarification here.  

The Linux community *does* have something easier and just as ready to use, and here's another kicker, its free!  what you are looking for is a GUI tool like Active Directory Users and Computers, Active Directory Sites and Services, and Group Policy Modeling. (three different tools, notice, not one)  

Active Directory domain controllers require Windows 2000 or better.  Windows Server 2003 is required if you want it to be ""fully functional"" and native, which means no NT4 Domain or 2k AD domain controllers whatsoever.  There is elevated concerns as well, with Active Directory Integrated DNS, that grossly pollutes a DNS tree and complicates replication.  

Open LDAP, NIS and several other UNIX/Linux domain and directory models are, in my opinion, far easier, more flexible, and more comprehensible than Active Directory from an admin point of view.  I've a pretty extensive background with Migrating between Netware and AD and maintaining multi-site Active Directory domains, and believe me, if Windows would only behave better in a non-microsoft domain or directory model, I doubt many people would waste much time with Active Directory. (and to clarify, in AD, you do have to know, and modify schema's as well.  If you haven't yet, consider yourself lucky)

As for GUI tools, I'm a CLI guy, so I can't give you much direction here.  I always felt like administration from the CLI was much more efficient.  I did 90% of my Active Directory administration from the CLI in Windows because it was so much more efficient.   I like to script, schedule, and automate whenever possible and thats just a pain to do with GUI tools unless they have that functionality specifically built in. (not many do)

---

### Post by tymiles on 2007-12-29
Out the box there is no way to install a version of Linux and set up a small business or enterprise network like you can with Windows 2003. Add Windows, Macs and even Linux now with Likewise. In an hour I can have PC's managed, servers rolled out and replicated and user accounts set up in AD or on the Mac in OD. (In Linux using EDirectory you can do the same) 

Using the CLI is cool for admins if they want to learn it. But it sucks for workflow and sucks even more for small business. 

For instance how do you handle single sign on for things like SBC, Citrix out the box and easy. How do you handle password resets, new user account creation, moving users between groups etc when you have a help desk. 

Using the MMC snap in for AD or using the workgroup manager in OD it's easy to set up for help desk staff. 

The main thing is set up. You install Windows 2003 server, after the install is done, boom the wizard comes up asks you if you want to set up AD, in non tech terms it walks you through how to set up DNS, AD your domain etc. Set up users, done. Add your Mac, Windows and Linux workstations (Linux using likewise) and you have a working manages network with replication of data. No sweat, a 10 year old could do it. 

With Linux (Even using Novell Open Workgroup suite) it's a bear. Which is why Linux does not sell in this space. Xandros has done a good job of being close but I found that the Xandros system does not use Ldap on the backend and does not replicate user data. Primary server goes down and your workgroup is down. 

Linux would be great in this space. Ubuntu would be hot if they had something comparable to OR or AD!

As far as AD and DNS goes, you don't use the Windows DNS as the primary DNS, you just use that for AD related tasks but have BIND servers be your primary DNS for things out side of AD. 

In a big network yes you have to do things like change schema's etc. But for small business you don't. 

And you are right about Windows acting better in non MS domain model. But Windows has 75% or more of the desktop market at this time so you have to support Windows somewhere in your network most times. Now Apple has addressed this with their Open Directory server that uses all open source software that is available to Linux. While not perfect its very easy to use with Linux, Unix, Macs and Windows. You can do file sharing using NFS and Samba right out the box no fiddling (Very easy to follow admin manual) set up your OD servers as Samba PDC's and BDC's to Windows machines with master, client replication etc.

---

