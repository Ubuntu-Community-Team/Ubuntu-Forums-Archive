---
title: "Converting Windows to Ubuntu Services"
date: 2012-01-20
forum: Server Platforms
---

### Post by LHammonds on 2012-01-20
_[SIZE=3]Researching Potential Solutions[/SIZE]_


[LIST]
[*]Print Server
[*]DNS Server
[*]File Server
[/LIST]
_[SIZE=3]Environment[/SIZE]_

My shop is mainly Windows servers and PCs in a Windows 2008 Active Directory domain.  I have many of my servers virtualized in VMware vSphere 4.1 on IBM BladeCenter.

I want to start offloading generic services from Windows servers to Ubuntu servers which can run better and longer while using less resources (key factor in a VM environment)

I am new to Linux but have learned enough to setup 3 specialized servers so far (Zimbra, MySQL and Nagios).

My desktop PCs (about 300) are mostly Windows XP Pro (32-bit) and Windows 7 (32-bit and 64-bit).

My printers are mainly Brother HL-5250DN (about 40), HP LaserJet 4250 (about 50) and Toshiba Studio 550 Copiers (about 20)...all configured with static IP addresses either directly on the printer or via JetDirect devices.  Nothing plugged in directly to a Server or PC.

_[SIZE=3]Questions[/SIZE]_

I'm looking for some feedback from Ubuntu Server (10.04 LTS) users that have done what I am thinking about doing.

_[SIZE=3]Print Server Questions[/SIZE]_

Since I have 32-bit and 64-bit Windows desktops, does that mandate which kind of server I use (32-bit or 64-bit)?  I prefer 64-bit servers but do not know how problematic it will be dealing with the drivers.

Is it possible to have the print server hand out the print drivers whenever a Windows OS tries to connect to it?  Similar to pre-loading 64-bit and 32-bit drivers on a Windows server so all that is needed when adding a printer is to know the correct address.
It will be a deal-breaker if our users have to fumble around and download the correct driver for the printer queue. (our users are just not that savvy)  I would like to eventually get to the point where the login script will attach the print queues they need during login so they do not have to do anything other than possibly set the default printer when going to a new PC.

Regarding permissions, almost every print queue should be freely available to anyone.  The is one exception that I know about (a color LaserJet) which might need to be restricted to a particular Active Directory group.  Is this possible like it is in Windows?  Or will it present problems to my Windows users...such as always asking for authentication?

_[SIZE=3]DNS Server Questions[/SIZE]_

We currently have a Win2008 Domain Server that must run DNS because of Active Directory (AD).  We have a backup AD server which also runs DNS.  My goal is to setup two Ubuntu servers to run DNS and keep in sync with our Active Directory server so that they know about our internal servers as well as Internet servers.  My goal is to eventually have all devices reference the two Ubuntu DNS servers in their IP configurations rather than the two Windows servers.

Is this setup going to cause more problems that what it will solve?  Such as having issues keeping in sync with the Windows AD server?  For example, if I add a new server to the domain, will all devices pointing to the Ubuntu servers, be able to resolve a new server in about 15 minutes or so?

_[SIZE=3]File Server Questions[/SIZE]_

I am really interested in this feature set because I plan to have an identical server at an offsite location running rsync to keep an identical copy of the files ready for use if the primary file server / site becomes unavailable.

Most of our file server shares are basically wide open in terms of permissions.  As long as the user is a member of the domain, they can access most locations.  However, there are some areas that are locked down based on what Active Directory group they belong to.

Can Samba handle this restricted security in the background or will it harass our users with password prompts?

Thanks,
LHammonds

PS - If this is a good place for it, I can document my server installs as I do them to help me in the event of having to do it again as well as getting feedback from pros on what I may be doing wrong or could do better.

---

### Post by CharlesA on 2012-01-20
You can integrate Samba with LDAP, so that it will authenticate to the domain, but it sounds like you are looking for more work than anything - I haven't really noticed Windows acting as a server using much more resources than a *nix server running the same service.

I go by the philosophy that if it's not broke, don't fix it. ;)

Feel free to document the installs if you want, as long as there aren't any sensitive data being posted. :)

EDIT: Check out some  [TurnKey appliances]("http://www.turnkeylinux.org/"), they might give you a better base to start with instead of starting from scratch.

---

### Post by LHammonds on 2012-01-21
CharlesA, thanks for the reply and insight.  I actually started with  TurnKey way back when I started looking for a replacement option for our  aging Exchange server.  I tried to make their Zimbra appliance work but  had issues with it.  When looking at the Zimbra forums, they  pretty-much ignore anything from Turnkey as an unsupported (by them)  platform.  I began to research how to build a working Zimbra solution in  a manner that their company "could" support if we decided to go with  them and wanted support.  Thus, the reason I chose Ubuntu Server 10.04  LTS.  Through trial and error, I learned how to setup a working solution  and  _[shared  my results on their forums]("http://www.zimbra.com/forums/installation/53227-my-notes-installing-zimbra-7-1-3-ubuntu-server-10-04-3-lts.html")_.

I also had MySQL installed on my local Win7 PC and used it as the  database for our Intranet (WordPress).  Anytime my PC rebooted (MS  Autoupdates) or turned off (lost power), the Intranet would become  unavailable and freak some people out for a little while.  Since I had  some experience with setting up Ubuntu and making backups with it, I  added another Ubuntu Server, setup MySQL and moved over the WordPress  and PhpBB databases.  Backup and auto-purging of old backups have been  working like a dream.  I have yet to document this solution (might do it  here)

I then stumbled upon Nagios for network monitoring. I have had  monitoring packages like SolarWinds in my budget proposals for 6 years  now...always getting killed due to tight budget constraints.  After a  bit of investigation and trials, I decided to give it a go and my boss  likes the initial results.  We found an improperly configured router and  another one that was freaking out causing mild networking problems but  not enough for anyone to call about it.  I am still reading some books  about it but have  _[started  a documentation thread]("http://support.nagios.com/forum/viewtopic.php?f=7&t=4605")_ on their forums.

If I can reduce the amount of Windows servers (and hopefully reduce  their overall consumed resources), that will also reduce the software  licensing costs.  We have new servers that will be coming online so  being able to use existing OS licenses as well as our backup licenses  (DoubleTake), that could save a pretty penny.

We have an offsite location that is not being used for anything other  than a backup repository for our Windows servers.  It is designed to be  our disaster recovery site so there is a LOT of horsepower sitting there  doing nothing.  I could make use of these resources with Unbuntu in  such a way that it would be a much better and faster disaster recovery  than DoubleTake.  Granted, we mainly just have DT-Backup licenses rather  than the cost prohibitive DT-Availability licenses.  The DoubleTake  system requires a LOT of babysitting and hand-holding to keep it running  or it can quickly become messed up and unusable although it is no fault  of the servers or network connectivity.  I have had zero problems with  Ubuntu keeping in sync with the backup server and I have it configured  to notify me about the slightest problem.

A large part of the reason why I want an Ubuntu file server is that I  trust the backup solution much more than DoubleTake and Microsoft's  volume shadow copies for revision restores.

The DNS servers are just a recent thought.  We have most all servers and  services on a subnet configuration I'd rather get rid of and transition  to a new subnet.  This just seemed like a good idea to have 2  additional DNS servers running at the same time while we re-configure  everything to use the new DNS IP addresses.  Don't ask about why I want  to get rid of the subnet I inherited...just know it was setup by people  who had no idea about IP addresses at the time.  ;)

In terms of resources consumed, I've seen a significant reduction in  what is required when comparing Windows and Ubuntu servers...at least  from what I have done so far.

MySQL - 0.5 GB RAM allocated.  Typically using 20%
Nagios - 1.0 GB RAM allocated.  Typically using 35%
Zimbra - 4.0 GB RAM allocated.  Typically using 50%

MS Exchange - 3.0 GB RAM.  Typically using 75%
MS WebServer - 4.0 GB RAM allocated.  Typically using 45%
MS SQL Server 1 - 6.0 GB RAM allocated.  Typically using 40%
MS SQL Server 2 - 4.0 GB RAM allocated.  Typically using 50%

My next Ubuntu server will probably be a web server and I'll bet it will require / use a lot less than the Microsoft counterpart.

From my experience, many Windows servers will continue to consume more  and more RAM over time...which is why I don't let any of them stay up  for more than 30 days.  Memory leaks in the OS or the applications they  run seem to be common place.  Unix servers don't seem to have that  problem nearly as bad.  My ESX servers tend to run for hundreds of days  without problem.  The only time I have to reboot them is just for  upgrades.  The Zimbra server has been running for over a month and I  don't see any reason to reboot him yet and he has a ton of services /  features being utilized compared to that of Windows servers.

I may be green in the *nix world but it seems to be a better solution  than Windows in various situations.  Granted, I am not looking to  replace everything because that simply is not possible / practical.  I  am just looking to find better and more stable alternatives to Microsoft  when it is practical.

Another major factor is that we have transitioned from physical servers  to virtual servers using VMware's vSphere Enterprise Plus 4.1.  Starting with vSphere  5.0, they have completely changed the licensing model in a way that  would be cost prohibitive for us to upgrade anytime soon.   If we do,  I'd imagine we will have "unmanaged" servers outside the vSphere  envelope so having hardened servers that can run for long periods of  time would be very beneficial in that situation.

Another factor is malware and the human factor.  It is becoming harder  for our users to spot malware cleverly disguised as genuine software and  thus can unleash havok on internal systems.  Microsoft is a clear and  easy target for such malware.  The shear amount of malware that has  entered our systems through the use of Internet Explorer and Outlook is  staggering.   We cannot afford to be a 100% homogenous site.  Although  we do not see the use of Macs on our network, out PC guy has Macs at his  house and every time we hear about another virus attack here or abroad,  he always comments saying "Macs not affected" which is true...they are  based on Unix.

Yes, I could re-implement Windows servers for everything I am talking  about and most-certainly it would be easier (less work) on my part since  I am a certified Windows and MSSQL DBA.  However, I want a more  diversified system, better stability, better features for my customers.   I believe Linux has a place and can fill that role.  I am just new to  it and would like to avoid potential will-never-work situations that may  not be documented that well...for obvious reasons.  That is why I am  asking these questions on these forums.  It is a bit of a letdown to  hear Ubuntu cannot utilize hardware better than Windows...but I'm also  certain it is not a simple yes, no question either.  There are many  factors to take into account.  One of them being that Ubuntu doesn't have to waste any resources on a GUI...unlike 100% of Windows servers.

I may be wrong but I feel as though Linux has reached a point where it  can be feasible to make a play for the server field in companies.  I  have been watching the virtual environment for a long time and only  recently felt it has matured enough to the point we could make it our  primary platform for all our servers...and it turns out I was right and  we got it implemented at just the right moment.  For companies to  embrace Linux solutions, there needs to be clear documentation on how to  do things...such as the planning, installation, migration, maintenance  and upgrades.  I hope the tutorials I write will help in that area.  The  more knowledgeable people that help straighten me out on areas I mess  up will only help the documentation effort.

LHammonds

---

### Post by HermanAB on 2012-01-22
Howdy,

Just gradually replace services with Linux.  Printing for example is no problem at all - any Linux system with CUPS is all you need.  

Linux makes all printers look like postscript printers, so from Windows, you can usually use any available postscript driver and it will work with any printer. 

As for Active Directory, make a virtual machine for a Windows 2003 server and be done with it.

---

### Post by aquarius18 on 2012-01-22
> **HermanAB said:**
> Howdy,

Just gradually replace services with Linux.  Printing for example is no problem at all - any Linux system with CUPS is all you need.  

Linux makes all printers look like postscript printers, so from Windows, you can usually use any available postscript driver and it will work with any printer. 

As for Active Directory, make a virtual machine for a Windows 2003 server and be done with it.

May I suggest Zentyal as your server(s) - from memory the url is zentyal.org

---

### Post by LHammonds on 2012-01-22
> **aquarius18 said:**
> May I suggest Zentyal as your server(s) - from memory the url is zentyal.org
[Zentyal  Office]("http://www.zentyal.com/en/server/office/") looks like a great place to start.  Thanks for sharing...I  had no idea this existed.
 
:popcorn:

The [Zarafa]("http://www.zarafa.com/content/editions") groupware product doesn't seem to stack up very well against [Zimbra]("http://www.zimbra.com/products/compare_products.html") for my site so I think I'll stick with converting MS Exchange to Zimbra.  Many other Zentyal products are very interesting and will require some research and testing.

---

### Post by SeijiSensei on 2012-01-23
I think you'll have to keep Windows DNS since it's so embedded in the AD infrastructure.  It also provides both forward and reverse lookups for all machines by default.  

That said, if you want to have Linux boxes handle name service requests from your clients, you can make them slaves for the domains hosted on the AD servers and tell the clients to use those Linux servers via DHCP.  Using DNS forwarding for this doesn't help, since the AD servers will still be handling the name-service requests.  

Basically you just need the BIND configuration for a caching nameserver, then add slave entries to /etc/named.conf for domain.name and the appropriate in-addr.arpa reverse domain(s).  Something like this:

```

zone "example.com" {
    type slave;
    masters { ip.of.ad.server1; ip.of.ad.server2; };
};

```

You'll need to tell the AD servers to let the Linux boxes be their slaves.

---

### Post by LHammonds on 2012-01-30
Thanks SeijiSensei.  That is exactly what I'm looking to do.  Let the AD server be the primary DNS but DHCP point to various Ubuntu DNS servers that are slaves to the AD server.  Nothing directly querying the AD DNS other than the Ubuntu DNS servers.

I'm hoping to have an Ubuntu DNS server at each physical location and setup DHCP to hand out DNS based on location.  Such as City #1 DNS getting the City #1 DNS server as the primary and a City #2 DNS as secondary DNS.  Then clients in City #2 getting City #2 DNS server as primary and City #1 DNS as secondary and so on.  This will allow DNS lookups to be handled onsite rather than going over the WAN or Internet.

--------------------------

I've been playing around with the CUPS printing and initial tests are going VERY well.  I have setup each kind of printer/copier that we have and printing works better than Windows!  For example, we have one problem child printer which is the HP LaserJet P4014n.  Windows wants to install the "suite" of HP drivers in order to work properly.  Even then, anytime we look at the printer properties, it wants to re-install the drivers for some-odd reason.  Using the drivers that ships with Windows that most-closely matches the printer seems to work best (and doesn't have the problem mentioned).  I can pick additional tray options without any problems too.

I plan on using logon scripts to automatically setup whatever printer the users are assigned to.  The script checks to see which group they belong to and then installs printers based on the group.

Here are the magical command-lines I am using to install the printers via the login script (NOTE: These are just the command-lines to attach a pre-existing print driver to the CUPS print queue...not the selection logic in the login script):

NOTE: 192.168.100.23 = Ubuntu Print server (substitute the real IP when you see this IP since it is just an example)

```

## Add a print driver and attach it to the CUPS print queue

## HP LaserJet P4014n for Windows XP
rundll32 printui.dll,PrintUIEntry /b "CITY1-OFFICE1-FRONTDESK" /x /n "required but unused" /if /f %windir%\inf\ntprint.inf /r "http://192.168.100.23:631/printers/CITY1-OFFICE1-FRONTDESK" /m "HP LaserJet 4000 Series PCL6"

## HP LaserJet P4014n for Windows 7 (NOTE: Available print driver names are different than XP)
rundll32 printui.dll,PrintUIEntry /b "CITY1-OFFICE1-FRONTDESK" /x /n "required but unused" /if /f %windir%\inf\ntprint.inf /r "http://192.168.100.23:631/printers/CITY1-OFFICE1-FRONTDESK" /m "HP LaserJet P4014/P4015 PCL6"

## HP LaserJet 4250N for Windows XP
rundll32 printui.dll,PrintUIEntry /b "CITY1-OFFICE2-FIRSTMED" /x /n "required but unused" /if /f %windir%\inf\ntprint.inf /r "http://192.168.100.23:631/printers/CITY1-OFFICE2-FIRSTMED" /m "HP LaserJet 4000 Series PCL6"

## HP LaserJet 4250N for Windows 7 (NOTE: Available print driver names are different than XP)
rundll32 printui.dll,PrintUIEntry /b "CITY1-OFFICE2-FIRSTMED" /x /n "required but unused" /if /f %windir%\inf\ntprint.inf /r "http://192.168.100.23:631/printers/CITY1-OFFICE2-FIRSTMED" /m "HP LaserJet 4250 PCL6"

## Brother HL-5250DN for Windows XP
rundll32 printui.dll,PrintUIEntry /b "CITY2-OFFICE1-RECEPT" /x /n "required but unused" /if /f %windir%\inf\ntprint.inf /r "http://192.168.100.23:631/printers/CITY2-OFFICE1-RECEPT" /m "Brother HL-2460"

## Brother HL-5250DN for Windows 7 (NOTE: Available print driver names are different than XP)
rundll32 printui.dll,PrintUIEntry /b "CITY2-OFFICE1-RECEPT" /x /n "required but unused" /if /f %windir%\inf\ntprint.inf /r "http://192.168.100.23:631/printers/CITY2-OFFICE1-RECEPT" /m "Brother HL-5250DN Series"

```

---

### Post by mcarrara on 2012-01-31
Our network seems to be much like yours, about 250 computers half XP half Windows 7.  After trying for a few months to get my head around LDAP I gave up and installed a Windows 2008 server as an AD controller.

I could NOT get Ubuntu's DNS to work with AD.  It worked fine before, but never with AD.  We used Microsoft's implementation of DNS.  DHCP works very well on Ubuntu and it plays well with the MS DNS.

We use Samba on three servers for file storage and have no problems.  Once you understand permissions in Linux world everything works.

We use Cups to print to 11 printers, after a bit of work configuring them they work fine.  However I could not get drivers to automatically download like they do in Windows.  You have to manually select them when installing a printer.

I also use Amanda for network backups.  Now there is a poorly documented finicky program.  However after a few weeks of work I got it to backup all of our servers.

Hopes this helps you.

Mark

---

### Post by SeijiSensei on 2012-02-01
> **mcarrara said:**
> I could NOT get Ubuntu's DNS to work with AD.  It worked fine before, but never with AD.  We used Microsoft's implementation of DNS.  DHCP works very well on Ubuntu and it plays well with the MS DNS.

Can you recall what the DNS problem was?  Would the AD server not allow the Ubuntu slaves to transfer the domain?  Do you get errors on the Ubuntu side like this?

```
transfer of 'example.com/IN' from 10.10.1.10#53: failed while receiving responses: REFUSED
```

If so, you need to tell the AD server to [allow zone transfers]("http://www.youtube.com/watch?v=0X730icPC6s") to the Ubuntu slaves.

---

### Post by LHammonds on 2012-02-01
> **mcarrara said:**
> Our network seems to be much like yours, about 250 computers half XP half Windows 7.  After trying for a few months to get my head around LDAP I gave up and installed a Windows 2008 server as an AD controller.Yes, if you have a Windows environment, you are best to go with a Windows AD server.  Everything I've read about this makes me think that Linux / LDAP is not quite ready to take the place of a Windows AD server.  Close, but not quite yet.

> **mcarrara said:**
> We use Samba on three servers for file storage and have no problems.  Once you understand permissions in Linux world everything works.I miss the days of having Novell 3.11 file and print servers...they were so rock solid.

> **mcarrara said:**
> We use Cups to print to 11 printers, after a bit of work configuring them they work fine.  However I could not get drivers to automatically download like they do in Windows.  You have to manually select them when installing a printer.Correct, that is why I chose to use print drivers that ALREADY ship with the OS and thus no external media is required and nobody has to physically mess with it either.  See my command-line examples above.  The awesome part about CUPS printing is that you do not HAVE to use the exact print drivers on your clients.  If your print queue was pointing to an HP LaserJet 4250, it would still print correctly even if your client PC was using a Brother or Toshiba print driver!  You may not be able to control specific hardware functions like picking which tray but it will print using the default settings because as long as it is postscript, the print queue will take the print job and pass it to the print driver (which should be the correct print driver on the Ubuntu server) and it will simply work.  I tried it with various odd-ball drivers.  Printing works great.  The main thing is the ability of the client PC to control hardware-specific features such as tray number...which is why I try to pick a print driver (that Windows already has) that is "close" to the printer model.  I then check it out by printing with specific options such as picking a tray number to see if it handles it correctly.  My prior post shows the (client) drivers I found to work with the specific printers.  Keep in mind that the Ubuntu server has the exact driver for the printer though.

I wanted to know about what print drivers that Windows ships with that would work (compatible) with a specific Brother printer which is newer than Windows.  Everything I could read (manual, FAQ, google) would only mention compatibility with the OS and use of the device-specific drivers.  So I thought I'd get a professional answer and called Brother customer service support.  All I got was "you need to install the driver for that specific printer" and that "no other Brother print driver is compatible."  I found that hard to swallow because we have AIX print queues setup to send HP LaserJet 4 commands and the queue works no matter what version of HP or Brother we have hooked up.

Long story short, sometimes trial-n-error is the only way to get the answer you seek.  For me, I have a solution in place that "professionals" said would not work...although I know these people are told what to say to handle the 99% of users that cannot find their way out of a wet paper bag.

> **mcarrara said:**
> I also use Amanda for network backups.  Now there is a poorly documented finicky program.  However after a few weeks of work I got it to backup all of our servers.I looked at Amanda and Bacula and as you noticed, they just about require certification in that application to setup properly...something of which I don't have time to do.  I use Double-Take RecoverNow and Double-Take Availability along with Microsoft Volume ShadowCopy to keep mirrored servers updated at a remote site.  Backing up the files at the remote site is dead simple because the servers are not "online" and anything can be used to back them up.  No need for application-specific backup agents to be installed everywhere. ;)  For Linux servers, the rsync command works wonders when applied with a bit of scripting mojo. ([Example with Zimbra server]("http://www.zimbra.com/forums/230526-post10.html"))

LHammonds

---

