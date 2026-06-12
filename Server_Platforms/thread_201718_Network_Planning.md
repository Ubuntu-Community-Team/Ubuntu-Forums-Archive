---
title: "Network Planning"
date: 2006-06-22
forum: Server Platforms
---

### Post by JGJones on 2006-06-22
I'm currently a linux administrator for a charity that's quite very short of money. I started a short time ago.

This is the current network setup:

6 main offices scattered all over UK with 1 in Northern Ireland. Each office have a server.

They all run Debian Sarge.

They all are setup as basic NT Domain style network using Samba, all desktops with their own roaming profiles.

The email system was previously exim4 with uw-imapd, although I have recently changed it to use postfix with dovecot (changing from mbox files to a maildir structure). This was done as the previous email system was extermely unreliable with many emails being delayed for weeks or even getting dropped completely. This had a serious effect on the charity's business. Since the change to postfix, it's all working very well now. Email access is via IMAP/SMTP - no POP3. I've also introduced the use of Mailscanner for spam and virus scanning for emails.

For emails - all servers get their aliases list from a server via a cron job.

They all also are the DNS and DHCP servers although DNS isn't very well configured on them and will be fixed.

File sharing also was very poor with many problems due to misconfiguration of Samba - this was fixed as well.

Most of the servers had no form of any backup whatsoever despite that some of them had a backup drive etc.

Naturally that meant to start with my job was to fix and fix and fix. Now that the servers have been mainly fixed, patched, band-aided and updated and is now working as intended, and security issues dealt with (ie before I started you could ssh in as root for example!)

This means I can now start planning what is the next step for all of the servers and their function.

One of the most requested function is that all staff want an "Out of Office Autoreply" for their emails - can this be done with postfix and how easily can it be done? What's the software that allows for this?

Next I'll like to introduce a VPN connecting all offices to each other and allow the sharing of a "national" folder - to keep it secure rather than sending files etc via emails (which means a file easily become hopelessly outdated with different offices having different version). One is a straightforward VPN link, accessing all files in one office (all offices currently have a 2Mbs/256Kbs ADSL connection, but they all are getting upgraded to 8Mbs/800Kbs - the 800Kbs upload will help a bit there since most documents aren't that big and the national folder won't get accessed that much for the 800Kbs upload to become a bottleneck too much).

Alternatively I could go with a groupware solution - perhaps something like egroupware? This could be kept on a leased server from a hosting company such as 1and1.co.uk (comes with unlimited bandwidth) - that'll solve the bandwidth issue and might help with some centralised file-sharing (and one server to download it all regularlly for backup purpose).

Or there's the iFolder? The Enterprise server edition have been made freely available now for iFolder.

I've thought about using Novell, but as mentioned - the charity is extremely short of money.

Finally - I've been wondering...for Windows - it's quite easy to get a PC that can logon to a domain - setup username/password on server. Add PC to samba's list. Done. Then anyone can logon to that Windows machine. But what about Linux? How can I do the same for Ubuntu - where I'll install it and tweak it so that when a user comes to the machine, they have to enter their username and password and log on just like with Windows? I admit I'm not sure how I could do this? One idea was to just rsync the passwd file with the server - but this means the /home is on the PC (for Windows - the roaming profiles ensure that all documents are saved onto the server and be included in backup - after all, no matter how much one teach the user to use a network drive, a lot end up using My Documents or their desktop - but as roaming profile, at logoff, it get synced to the server.

The reason for this is that I'll like to introduce some Linux clients - for staff that basically only do email, word processing etc - in those cases, Ubuntu will serve their needs very well. It'll also make it much easier to keep it up to date (that's another problem with Windows...a lot have Firefox 1.0.7 which have quite a lot of security exploits, anti-virus licencing have expired (and you guessed it...no cash! So a lot are using AVG-Free Edition but that's really licenced for home use only and ClamAV doesn't do on-accesss scanning yet. As you can imagine - it's VERY hard to update all Windows machine across a country. It'll be much easier with Linux clients and save the company money. Windows will continue to be used naturally as there are some applications that need Windows.

Hope you lot can provide helpful suggestions :) Summary of this waffle can be this:

1. Groupware - pro/con and which solution?
2. Logon for Ubuntu (just like for Windows) - how?
3. "Out of Office Auto-reply" for emails
4. VPN solution (or should I look into iFolder since Novell have now made the Enterprise version freely available)

---

### Post by LordHunter317 on 2006-06-22
Well, the first thing I would do ( and I know this is hard for non-profits) is get some redundancy going.  Spread your services out over several boxes per-site.  

> **JGJones]One of the most requested function is that all staff want an "Out of Office Autoreply" for their emails - can this be done with postfix and how easily can it be done? What's the software that allows for this?[/quote]There are several pieces of software, look in APT.  Delivering the support to the client in a user-friendly manner may be the hard part.

> Next I'll like to introduce a VPN connecting all offices to each other and allow the sharing of a "national" folder - to keep it secure rather than sending files etc via emails (which means a file easily become hopelessly outdated with different offices having different version).Make sure this will actually be used for collaboration.  I prefer e-mail for most tasks, unless I'm collaborating in real-time, because it gives me versioning for free.


> Alternatively I could go with a groupware solution - perhaps something like egroupware?The only thing I can say of any of the groupware solutions is that they're all vastly inferior to sharepoint.  You'll have to evaluate them on your own, likely.

> But what about Linux? How can I do the same for Ubuntu - where I'll install it and tweak it so that when a user comes to the machine, they have to enter their username and password and log on just like with Windows?There's four main ways:[list][*]Use NIS.  This would likely be a PITA to sync with Samba.[*]Use winbindd.  The downside here is that UIDs will not be synced across machines (i.e., bob could have UID 100 on machine 1 and UID 101 on machine two).  This is a problem because NFS and the CIFS driver expect UIDs to be identical across machines.[*]Start using LDAP for account management and make everyone talk to the LDAP server.  This will be a pain to deploy: you'll want a LDAP server in every office replicating with each other.  You'll also want to make sure each LDAP server is authortative for it's own office (i.e., it stores the accounts for the people who work there): this may mean changes to the DNS infrastructure and such.  You'll then need to convert Samba to use LDAP as it's password store as well.  This solves the UID sync issue and is the correct low-cost option.  It will take a lot of your time though.  Use Fedora Directory Server, OpenLDAP is a joke.  Finally, consider Kerberos for actually handling the password authentication said:**
> Convert to using Active Directory and make everything dependent on that.  This requires some work in AD, but is a viable solution.  And, it makes management of your Windows clients far eaiser and more flexiable.[/list]

> but this means the /home is on the PCSo NFS or CIFS mount /home.  You should be doing that anyway.

[quote] (for Windows - the roaming profiles ensure that all documents are saved onto the server and be included in backup - after all, no matter how much one teach the user to use a network drive, a lot end up using My Documents or their desktop - but as roaming profile, at logoff, it get synced to the server.This isn't wise.  You generally don't want to incldue My Documents in the roaming profile: it means a lot of crap gets copied that may never get used.  GPO allows you to set where 'My Documents' should be redirected to, use that.

> It'll also make it much easier to keep it up to date (that's another problem with Windows...Windows is a lot eaiser to keep up to date if you have real admin tools, which means Windows Server.

---

### Post by LordHunter317 on 2006-06-22
I didn't mention it, but the deployment rules for LDAP also apply to AD pretty much equally.  AD also costs more.  If you're getting along fine without the extra managment features, it may not be worth the cost.

---

### Post by JGJones on 2006-06-26
Ok thanks for that. I've already known that doing some of those would be easier using Windows, but one quote we got for converting to Windows would cost in excess of £30K. The benefits from this would only benefit me, but not the staff generally so it's a no no. Plus it's a charity with little money for IT (which is why Linux is used, it doesn't cost them anything apart from having IT staff, which they would still need for Windows anyway)

Thanks for the tip about Fedora Directory Service I'll certainly take a look into that. 

Furthermore I've been looking into using Dameware for client management...I've used it in one job and it was extremely useful, that should take care of client management ;). Will be using the 30 days trial to see if it works and then it's a question of begging for money to purchase it.

---

### Post by LordHunter317 on 2006-06-26
[QUOTE=JGJones]Ok thanks for that. I've already known that doing some of those would be easier using Windows, but one quote we got for converting to Windows would cost in excess of £30K.[/quote]That seems possibly, but I'd assume that would include converting to Exchange (not necessary) and perhaps more CALs then you need.  But I don't know your business so it could be on the spot.

> Thanks for the tip about Fedora Directory Service I'll certainly take a look into that. If you do an LDAP rollout (looks like sooner or later you must) it really is the way to go.  It will run on Ubuntu, with some coaxing to install it.  There are guides out there.

---

