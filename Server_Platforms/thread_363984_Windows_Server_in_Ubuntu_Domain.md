---
title: "Windows Server in Ubuntu Domain"
date: 2007-02-17
forum: Server Platforms
---

### Post by vba_djs on 2007-02-17
I have an Ubuntu Server 6.06 (Samba 3.0.22) as the primary domain controller for my network.  This is the only server on the network.  I have less than 10 Windows XP Professional workstations.

We are looking at an accounting program that utilizes Microsoft SQL Server as the data store.  

If I get another server to load Windows Server 2003 and MSSQL, will I still be able to use Ubuntu as the PDC, or will the WIndows Server insist becoming the PDC?

If the two servers can co-exist, will the users have to log onto each server separately, or can Windows 'trust' the Ubuntu logon?

Thanks.

---

### Post by jonathan.lees on 2007-02-17
By default Server 2003 is not a PDC, it has to be configured.  If two servers exist, server 2003 cannot trust your ubuntu server as you need Active directory for trusts to exist and for that you'll need to make the Server 2003 a PDC.

---

### Post by igknighted on 2008-02-29
> **jonathan.lees said:**
> By default Server 2003 is not a PDC, it has to be configured.  If two servers exist, server 2003 cannot trust your ubuntu server as you need Active directory for trusts to exist and for that you'll need to make the Server 2003 a PDC.

Sorry to revive a thread this old, but I actually have a question about going the other way.  We have a windows server 2003 PDC running right now, with about a hundred users that I have no interest in migrating.  We also have a Novell Netware 3.11 server (IPX and everything... this is a dinosaur).  Currently, all our computers log into the windows domain and the Novell server by logging in to the Netware client at boot, and their windows domain logins are the same as their netware logins.

Here's the catch... the novell server is getting the boot, and we really don't want to pay for another windows server 2003 license, and while netware is an option, we are looking at our linux alternatives.  I want the new server to do essentially what the OP wanted, but I am open to using the windows server as the domain controller since the users and groups already exist there.  I would rather the new linux box take over the PDC duties, but it has to play nice with the windows 2003 server.

The ideal use case is this:  John logs into his computer.  He types his username/password to enter the domain, and has access to the windows 2003 server and the linux fileserver

In order to leave windows as the PDC and move the files from netware to linux, would simply recreating the files in a folder shared by samba do the trick (ie, can the windows server PDC set who has rights to this)?  Or do i need something fancy like an openldap server to do this?

And if I used something like Mandriva Directory Server ([http://mds.mandriva.org](http://mds.mandriva.org)) or Fedora Directory Server, could these handle the domain controller duties and play nice?  Could it all be handled by one login?  Are these services fairly simple to manage, compared to netware and AD?

EDIT: oops, thought this was in the server sub-forum... requesting it be moved now...

---

### Post by astrotech226 on 2008-02-29
> **igknighted said:**
> 
In order to leave windows as the PDC and move the files from netware to linux, would simply recreating the files in a folder shared by samba do the trick (ie, can the windows server PDC set who has rights to this)?  Or do i need something fancy like an openldap server to do this?

I actually have a similar setup, but Windows 2003 doesn't do any domain control.  Just terminal services.  The only problem I see with your setup is I didn't see you mention a backup domain controller anywhere.

There would be nothing wrong with your Win2k3 server being the PDC, but if it goes down, it will basically render your linux server useless unless you have another Windows BDC somewhere.  And Linux can't be a BDC to an Active Directory domain.

If your Linux server becomes the PDC, you really should set up a second Linux server for a BDC and use some database backend of your choosing like open-ldap.

But the minimum you would need to do what you described would be to leave the Windows as the PDC, set up Linux as a file server and simply join the domain and set up a few smb.conf parameters.

---

### Post by igknighted on 2008-03-03
This would still leave me in the same boat as above, correct?  If the windows domain controller goes down, I wont have access to the linux file server.  Given the choice between the two, wouldn't I rather have linux as the PDC as it needs far less downtime?

On the other hand... what if I had a primary and backup domain controller in linux (be it FDS, MDS or openldap), and made the windows server simply a resource on that network or a standalone server with available shares?  Could I control access to the resources on this server from the linux domain, or would windows server 2k3 not like this?

Also, since we have a server 2k3 license and all the necessary CALs, would we be able to add a second server 2k3 license without buying more CALs?  Would adding another 2k3 server (linux bias aside) be enough of an easier transition to justify the purchase of the MS license?

---

### Post by astrotech226 on 2008-03-03
Being a long time Linux user, I would tell you do install the two Linux servers and never look back.  Unfortunately, this approach doesn't work for everyone.  There's a few questions you need to ask yourself before attempting it.

1.  Even though Linux is extremely stable, you will experience some type of problem at some point in time.  Are you going to be able to handle this situation if it arises?  If you can and are gone on vacation, is someone else there capable?
2.  Is management going to buy into the fact that you are going to use open source software in the back end?  This can be a hard battle to win.
3.  If you are currently using AD in your domain, your capabilities are going to be a little different when switching to Linux.  Group policy and others like that have "things" you have to deal with or work around.  Any of the negative usually is extremely minor (can be dealt with scripts) compared to what you gain.

If you aren't scared at this point, then I would definitely try it.  If you have Linux for your PDC and BDC, your Win2k3 server will behave just fine with it.

---

### Post by igknighted on 2008-03-03
Thank you, you've been very helpful.

I personally would feel confortable handling any situation on the linux boxes (lots of experience with Desktop linux and a working knowledge of the LAMP server, but very little file/directory experience), but would be the only one with experience.  On the other hand, no one in the office really understands windows/AD and we use only a fraction of its capabilities I am sure and call HP who sold us our server any time there is an issue.  Since we are building this machine ourselves, we would need to pay extra for support either way and would have at least some in-house linux experience, which I would pass on to my lone IFS cohort.

Given all that, I am leaning towards the linux PDC/BDC options.  I want to keep this as user friendly as possible so most user/group management tasks can be done without any CLI experience, and this is why I keep bringing up the Fedora Directory Server and the Mandriva Directory Server (due to the MMC and graphical tools that Fedora's DS has), not to mention that (sorry Ubuntu) I will likely go with a Red Hat based distro (more of where my experience is, as well as support).  Do you hae a particular guide that you recommend for setting up a linux box as a domain controller?

---

### Post by astrotech226 on 2008-03-04
> **igknighted said:**
> Do you have a particular guide that you recommend for setting up a linux box as a domain controller?

It sounds like you have a good environment to implement this.  I used the official samba documentation for my first few installs.

[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/]("http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/")

How many users do you have?  How many PC's and servers (and what do they do)?  If you give us an idea of your environment, I (or someone else here) can give you some ideas on what other aspects of your network can be improved by doing this.  Printing is a major one.  There are some pretty amazing things you can do with this when you are done.

---

### Post by jonabyte on 2008-03-04
> **vba_djs said:**
>  
If I get another server to load Windows Server 2003 and MSSQL, will I still be able to use Ubuntu as the PDC, or will the WIndows Server insist becoming the PDC?


If you get Windows Server 2003 standard, it will not be a pdc by default. BUT if you get the Windows SBS 2003, it will be setup to be the pdc by default and I believe it is difficult to change it, if not impossible.

---

### Post by astrotech226 on 2008-03-04
Windows servers don't want to be PDC or BDCs without you specifically enabling it.  All you have to do is boot them up and join them to your new domain.

---

### Post by igknighted on 2008-03-04
> **astrotech226 said:**
> It sounds like you have a good environment to implement this.  I used the official samba documentation for my first few installs.

[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/]("http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/")

How many users do you have?  How many PC's and servers (and what do they do)?  If you give us an idea of your environment, I (or someone else here) can give you some ideas on what other aspects of your network can be improved by doing this.  Printing is a major one.  There are some pretty amazing things you can do with this when you are done.

We have about 100 pc's and/or users.  In reality it is a little less (maybe as 70 currently), but as far as planning purposes we are using about 100 as the guide.  We have a basic router/gateway, a static IP network, (currently (although being replaced) a netware 3.11 server which is our main file server, it holds nearly everything file related, a windows 2k3 server acting as domain controller and running our shop management software (global shop solutions, it's a Pervasive SQL database) as well as some other software that wants to be on windows as opposed to the netware server (an HR suite for example).  Aside from that is an ancient mail server that is also looking to be replaced (probably again by something open source, hopefully zimbra, but maybe something less complex).  There are some shared printers (the massive copy/fax/scan machines), but I haven't dealt with them personally.  Most users have their own printers attached to their computers, and would probably not be too happy if we took them away.

Aside from that, it's just a mixed bag of everything from Windows XP Pro to Windows 95 clients.  Don't laugh too hard... these machines do next to nothing, so its hardly worth the cost and effort to upgrade them.  In fact the only reason we have upgraded many is that the old color printers are dying, and we can no longer get new color printers to work with them.

Does anyone have any experience with novell's groupwise and edirectory products?  I want to be able to put together a few options, both commercial and supported as well as more community driven.  We are in the process of testing a Zimbra server out and so far people have been impressed.  We are not coming from an exchange environment, but would love the shared calendering and other features, but anything that combines the directory and email features into one, simpler control panel would be ideal.

---

### Post by igknighted on 2008-03-04
> **jonabyte said:**
> If you get Windows Server 2003 standard, it will not be a pdc by default. BUT if you get the Windows SBS 2003, it will be setup to be the pdc by default and I believe it is difficult to change it, if not impossible.

We have Windows Server 2k3 currently running as a domain controller, and do not have (or plan to buy) SBS.

Out of curiosity, if Windows Server is no longer the domain controller, do  we still need to pay for CALs to access it as a standalone server, or as a resource on the linux-controlled domain?

---

### Post by astrotech226 on 2008-03-05
> **igknighted said:**
> 
Does anyone have any experience with novell's groupwise and edirectory products?  I want to be able to put together a few options, both commercial and supported as well as more community driven.  We are in the process of testing a Zimbra server out and so far people have been impressed.  We are not coming from an exchange environment, but would love the shared calendering and other features, but anything that combines the directory and email features into one, simpler control panel would be ideal.

I don't have experience with these products, but I can tell you this.  If you can use openldap as your back end, much of this gets pretty simple.

Ldap can store all sorts of information for each user.  When a user changes a password in Windows, samba can also set the linux password.  This becomes a big deal because they have now also set their email/groupware/proxy passwords.  If you run apache web servers and need to restrict directories using htaccess (or php for that matter), you can restrict based on the ldap users, groups and passwords.  It's pretty slick.

I've looked at Zimbra and it looks pretty nice.  Also looks like you might be able to use ldap and do your Windows and Linux user/group administration right from it's gui.  Here's a link on how it works.

[http://wiki.zimbra.com/index.php?title=UNIX_and_Windows_Accounts_in_Zimbra_LDAP_and_Zimbra_Admin_UI#Creating_Linux_and_Samba_groups_using_Zimbra_Admin_UI]("http://wiki.zimbra.com/index.php?title=UNIX_and_Windows_Accounts_in_Zimbra_LDAP_and_Zimbra_Admin_UI#Creating_Linux_and_Samba_groups_using_Zimbra_Admin_UI")

---

### Post by astrotech226 on 2008-03-05
> **igknighted said:**
> 
Out of curiosity, if Windows Server is no longer the domain controller, do  we still need to pay for CALs to access it as a standalone server, or as a resource on the linux-controlled domain?

I'm not well versed on this any more so maybe someone else can clarify this.  But if I remember correctly, if a computer attaches to that Windows server to print, access files or use it for terminal services, you need a cal.

---

### Post by igknighted on 2008-03-05
> **astrotech226 said:**
> I don't have experience with these products, but I can tell you this.  If you can use openldap as your back end, much of this gets pretty simple.

Ldap can store all sorts of information for each user.  When a user changes a password in Windows, samba can also set the linux password.  This becomes a big deal because they have now also set their email/groupware/proxy passwords.  If you run apache web servers and need to restrict directories using htaccess (or php for that matter), you can restrict based on the ldap users, groups and passwords.  It's pretty slick.

I've looked at Zimbra and it looks pretty nice.  Also looks like you might be able to use ldap and do your Windows and Linux user/group administration right from it's gui.  Here's a link on how it works.

[http://wiki.zimbra.com/index.php?title=UNIX_and_Windows_Accounts_in_Zimbra_LDAP_and_Zimbra_Admin_UI#Creating_Linux_and_Samba_groups_using_Zimbra_Admin_UI]("http://wiki.zimbra.com/index.php?title=UNIX_and_Windows_Accounts_in_Zimbra_LDAP_and_Zimbra_Admin_UI#Creating_Linux_and_Samba_groups_using_Zimbra_Admin_UI")

Thank you, this looks very intriguing.  My only concern is that it asks for Samba to be on a different box than the Zimbra LDAP/PDC... could that other box act as a backup controller as well?  Two new servers we can do, but I really don't want to have to recommend three new servers, as we would start to lose the price benefit versus another windows server license.

---

### Post by astrotech226 on 2008-03-06
> **igknighted said:**
> Thank you, this looks very intriguing.  My only concern is that it asks for Samba to be on a different box than the Zimbra LDAP/PDC... could that other box act as a backup controller as well?  Two new servers we can do, but I really don't want to have to recommend three new servers, as we would start to lose the price benefit versus another windows server license.

If you have the right equipment with enough RAM, CPU and fast drives, you might be OK running it on the same machine.  Like you said, maybe stagger them so the PDC is on the other server and BDC is running on the Zimbra one.  You'd really have to install and try it out.

The other option would be to go to something lighter for the email portion.  There's a little more management overhead but it can mostly be scripted.  Try something like Cyrus IMAP.  I really like it because each email is saved as it's own file so it's easy to backup, restore and sync to other servers.  I hear that many people have great luck with Courier IMAP.  With these, you'll lose the single point gui.  But there's ways around that with scripts and using the User Manager for Domains in Windows if you wanted.

---

