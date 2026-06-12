---
title: "Windows Server 2003 Migration to Ubuntu Server"
date: 2009-09-24
forum: Server Platforms
---

### Post by gforster on 2009-09-24
I currently have Windows Server 2003 providing Active Directory/GPO policies and a domain controller to about 15 Windows 2000 computers at our school. This is the way it was left to me a year ago. I have had headache after headache with this server. first with Exchange email which suddenly stopped working. I didn't have the knowledge to fix it, so I migrated everyone to google apps. Then I found that many other settings were very wrong for our environment and I have been weeding through those. 

I have been using ubuntu on my personal computers for the last 3 or 4 years and am quite comfortable with it. I set up our computer lab of 30+ computers with ubuntu and it has been a wonderful transition (a few bumps along the way, but no big deal).

However, I have no experience with ubuntu as a server. I have only the last year of experience with Windows as a server.  I am not a true network administrator, but I am the most knowledgeable one on the staff, so I have been volunteered.

Here is what we need our server to do: (1) provide a domain for our windows clients to connect to, (2) be a file server, (3) allow our network multi-function network printer to be shared to all network computers, (4)allow that same multi-function printer (scanner function) to store its scanned files (5) allow that same multi-function printer (fax function) to store its faxes.  I also need to make this transition as seamless as possible - as in I don't want anyone to even notice that a transition has been made. 

I know this all can be done - I just don't know how. Is this something that is within my limited knowledge? Is this something I need official Canonical support for?

Thanks for all of your help! Let me know if I need to clarify anything.

---

### Post by HermanAB on 2009-09-24
It cannot necessarily be done seamlessly.  Some things need to be done the Unix Way.

Go to the Samba project page and read the Official Howto: [http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/)  That will give you an understanding of the limitations.

Alternatively get the Mandriva Corporate Server, which does most everything you want at the click of a mouse: [http://www2.mandriva.com/linux/server/](http://www2.mandriva.com/linux/server/)

---

### Post by Lars Noodén on 2009-09-24
I would start looking at Samba.  

And at [bash](http://steve-parker.org/sh/sh.shtml).  Knowing your way around the shell interface means you can take advantage of a UI that has been developed and streamlined in production for decades.  It also means that anything and everything you do can be turned into a script and automated.  It also means that you can connect in all kind of adverse situations including dreadfully slow network connections.  

But for right now, look around the net for Samba tutorials.  It will allow many of the tasks you are looking for.  Keep in mind that "AD" is simply a crippled combination of kerberos, ldap and a tool like puppet or radmind. 

 [http://www.samba.org/](http://www.samba.org/)
 [http://packages.ubuntu.com/jaunty/samba](http://packages.ubuntu.com/jaunty/samba)

The closest real world analogy to servers is a box of Lego blocks.  You put together the pieces you choose to make what you want.  Or look around for something that someone else has done and look at the pieces to see how it was put together.

---

### Post by openfly on 2009-09-24
I hate to say it, but your use case would be best met by Active Directory.

---

### Post by Lars Noodén on 2009-09-24
AD is a problem because of incomplete and broken standards which the Windows clients expect.  Samba4, which is now part of Ubuntum, deals with that better since winning the lawsuit:

[http://www.computerworld.com.au/article/273515/active_directory_comes_linux_samba_4](http://www.computerworld.com.au/article/273515/active_directory_comes_linux_samba_4)


The Samba component of this document might help.

[http://www.opensourcehowto.org/users-howto/samba/howto-replace-adexchange-with-sambazimbra.html](http://www.opensourcehowto.org/users-howto/samba/howto-replace-adexchange-with-sambazimbra.html)

And

[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

---

### Post by openfly on 2009-09-24
Lars, in theory you are correct.  In practice samba is far from rock solid, and since it's primary function is interfacing with microsoft products it's adherence to standards with worth exactly zero.  

AD is easier to configure and manage than Samba for the size of deployment he is talking about, and it will be less likely to break.  That's not a slight against Samba, AD has the benefit of not being a target of unfair business practices... and the benefit of being the dominant supported platform across the board in this area.  That's hard to beat.

I mean lord knows I hate to admin windows systems... it's a pain in the ****, but AD really is the correct choice for this use case.

---

### Post by gforster on 2009-09-24
I wonder if it makes any difference that I am hoping to eventually switch the windows 2000 desktops that the teachers have over to ubuntu. I have implemented many open source programs on their computers. There is one proprietary program that is necessary for entering grades, but it works well under wine and they are moving the program to become web-based and drop the desktop program. 

My biggest concerns are for file serving (this doesn't seem to be a huge problem) and working with the varying functions of our multi-function copier (Ricoh MP 5500).

I understand it won't be perfectly seamless, but I want to do the best I can.

---

### Post by openfly on 2009-09-24
Well samba has made strides... I've not seen it deployed across a +100 client environment in several years so maybe it's gotten better.  It used to have random file corruption problems.

1st Question:

Are you planning on doing roaming profiles?

2nd Question:

I haven't worked with a Ricoh in years and I tend not to deal with printers... BUT I know a lot of printers have functionality for things like scanning to ftps... or receiving faxes to them.  You can script cron jobs to populate or collect ftp based services and then integrate that into the fileshare.   So all faxes show up in a share drive called "incoming faxes"  or something to that effect.

Also I believe those printers ( if they are big enough and do things like job control ) can be integrated with LDAP to provide copy access and the sort.  Problem is, a lot of them are all... "AD is the only supported directory..."

I see the printer as being your biggest concern depending on what features are used.

I'd focus on researching that if I were you.

---

### Post by gforster on 2009-09-24
I do not see a need for roaming profiles as we do not currently use them. Just so long as one can login with the same username and password on any computer within the network.  I will have to do some research on the printer as well. It really seems to be the only critical thing to us having a server at this point anyway.

---

### Post by openfly on 2009-09-24
Okay here's my concern with using Samba as a PDC

from Samba 3.0 Docs

> 
Acting as a Windows 2000 active directory domain controller (i.e., Kerberos and Active Directory). In point of fact, Samba-3 does have some Active Directory domain control ability that is at this time purely experimental. Active directory domain control is one of the features that is being developed in Samba-4, the next generation Samba release. At this time there are no plans to enable active directory domain control support during the Samba-3 series life-cycle. 


You can deploy Samba as an NT style domain.  Yay.  You can even deploy Samba as an AD style domain as a member server.... and hope it works.  BUT!  If you attempt to use Samba as a PDC in an AD domain, you will be unable to join windows AD systems... and it will likely fail.

You may not want AD now.  But what happens a year from now when you deploy a cisco ip telephony solution and you need an AD server to sync address books against.  Or some similar event.

My suggestion...

Deploy a Windows 2003 AD server.  Join the Ubuntu system to that domain as a member server.  Run the domain off the ubuntu system.  Keep the Windows AD server as the PDC and maintain some level of scalability for future projects.

---

### Post by koenn on 2009-09-24
> **openfly said:**
> I hate to say it, but your use case would be best met by Active Directory.
I see nothing in the OP's question that requires AD - except maybe his pseudo-requirement of "provide a domain for our windows clients to connect to" - but with 1 server doing everything there's no need for any sort of domain

---

### Post by koenn on 2009-09-24
> **openfly said:**
> 
You may not want AD now.  But what happens a year from now when you deploy a cisco ip telephony solution and you need an AD server to sync address books against.  Or some similar event.

If today he's migrating away from Windows Server and AD, 
hopefully 1 year from now he'll have the good sense to pick an IP telephony solution that does not depend on  Windows + AD.

---

### Post by openfly on 2009-09-24
koenn the world is not always black and white...  more shades of grey.  cisco may be able to cut them a deal w/ their networking gear that makes a ton of financial sense.  

and market share wise, almost every app built with support for a directory service is AD ready... but so many are not tested / supported on anything else especially in the bizarre world of custom educational software.

---

### Post by koenn on 2009-09-24
> **openfly said:**
> koenn the world is not always black and white...  more shades of grey.  cisco may be able to cut them a deal w/ their networking gear that makes a ton of financial sense.  

I know al about shades of grey. and colors too.  :)

These are not merely technical or financial decisions. It's about long term vision and sound business choices : by abandoning his win+AD environment today, the OP has created an opportunity to move away from vendor lock-in and towards open standards. That's going to be beneficial because he'll be able to choose future solutions based on their merits or their value for money ratio rather than their compatibility with the vendor-specific interfaces of a proprietary infrastructure. 

Of course  a niche such as educational software me limitd his choices, but in stuff like directory services, network protocols, ip telephony, etc, open standards and open interfaces beat short term (and hypothetical) discounts any time.

---

### Post by openfly on 2009-09-24
koenn I'm a firm believer in finding the right tool for the job.  And while it's always important to keep, protect, and try to live by our ideals... sometimes it's not necessarily the best solution for your employer.

sometimes it is.

and at the end of the day OP needs to try to make a decision on what he will recommend.  

My opinion I stand by.  But I recognize that there are different views on where value lies in making a decision like this.  All things being equal I would likely support the open and standardized solution every time.

I don't think that all things are equal here though.

---

### Post by koenn on 2009-09-24
> **openfly said:**
> koenn I'm a firm believer in finding the right tool for the job. 

yeah, so am I. And in a case for 15 pc's and 1 file- and printing server, active directory is not the right tool, it's overkill.

Note that in the it's still an MS recommended & best practice to always have at least 2 Domain controllers per domain, so implementing AD in this case would also be the *technically* wrong choice.


Besides that, a move away from vendor lock-in has nothing to do do with ideals, it's plain common sense.

---

### Post by openfly on 2009-09-24
Well the ubuntu box would be the second domain controller.  slaved though it may be, it would avoid the primary concern of an outage with the PDC.  if you lose all your domain controllers on a domain you have to reboot all the client systems and it takes a while to sort out resulting errors and anger.

You are going to need two domain controllers regardless.

And I dunno if you've worked with AD, but the interface is pretty idiot proof for a 15 machine system.  LDAP + Samba for a new user of Ubuntu would be a pretty steep learning curve.

---

### Post by koenn on 2009-09-24
> **openfly said:**
> Well the ubuntu box would be the second domain controller.  slaved though it may be, it would avoid the primary concern of an outage with the PDC.  if you lose all your domain controllers on a domain you have to reboot all the client systems and it takes a while to sort out resulting errors and anger.

I understood the OP was looking to replace the windows server, not add a linux server to it. Running a Linux server as an AD domain controller alongside a windows DC is just creating unnecessary complexity (and would require Samba 4, most likely). In this case, you'd run the linux server as a stand-alone/domain member and make it use the domain accounts.


> **openfly said:**
> 
And I dunno if you've worked with AD, but the interface is pretty idiot proof for a 15 machine system.  LDAP + Samba for a new user of Ubuntu would be a pretty steep learning curve.

I've been working with AD on a daily basis since 2002. 
Yes, it's pretty simple if you're only using it to manage user accounts for 15 PC's. But functionally, that is not different from an NT4-style domain, and Samba alone would do just fine. The one-time effort of setting it up is negligible  - the OP could probably hire someone to do it for him for less than half of the costs of licenses and CALs for his windows server.

---

### Post by openfly on 2009-09-24
> **koenn said:**
> I understood the OP was looking to replace the windows server, not add a linux server to it. Running a Linux server as an AD domain controller alongside a windows DC is just creating unnecessary complexity (and would require Samba 4, most likely). In this case, you'd run the linux server as a stand-alone/domain member and make it use the domain accounts.


I dunno I thought it would give him the flexibility of administering his domain via a Linux system while preserving the ability for applications and infrastructure to make use of "supported" connections to a real AD controller.

I am pretty sure Samba 3 can act as a slave controller in an AD domain.  Not 100% but I remember reading a lot about that when it first came out.  

My understanding is that Samba cannot act as a PDC in an active directory domain to date due to problems reverse engineering kerberos tickets "miscellaneous" data fields.  There was a bunch of proprietary microsoft protocol stuff being wedged in there that was the source of the "hey your kerberos tickets aren't spec compliant and therefore not standard" complaints.  Their AD tickets were causing MIT and Heimdal systems to choke in cross realm trusts... and they'd sue Samba if they attempted to reverse engineer the miscellaneous data.  My understanding is that Open Directory reversed it and then either settled out of court or got microsoft's blessing on what they did.

Eitherway, Samba really isn't built for handling NTLM auth on a windows client network in a domain by itself.   

Please correct me if I am wrong, my experience here is a bit dated.  I'd love to here this is no longer the issue.

The other concerns I faced last I used Samba was a lack of proper byte locking support in files... which could result in file corruption if two people opened the same word / excel doc at the same time and started editing.


> **koenn said:**
> 
I've been working with AD on a daily basis since 2002. 
Yes, it's pretty simple if you're only using it to manage user accounts for 15 PC's. But functionally, that is not different from an NT4-style domain, and Samba alone would do just fine. The one-time effort of setting it up is negligible  - the OP could probably hire someone to do it for him for less than half of the costs of licenses and CALs for his windows server.

The printer server functionality ( IPP - Internet Printing Protocol ) is going to be WAY easier with AD.  You can push the driver sets to the clients from there easy peasy.

Consultants are always a good call when you are out of your depth.

---

### Post by koenn on 2009-09-24
> **openfly said:**
> I dunno I thought it would give him the flexibility of administering his domain via a Linux system while preserving the ability for applications and infrastructure to make use of "supported" connections to a real AD controller.
"administering his domain via a Linux system " - I don't quite understand what that's supposed to mean 
And what applications etc etc - so far he's only looking at file- and printer sharing 

> **openfly said:**
> 
The printer server functionality ( IPP - Internet Printing Protocol ) is going to be WAY easier with AD.  You can push the driver sets to the clients from there easy peasy.
There are many ways to share printers and many wasy to deploy drivers; You're making assumptions to justify the use of AD. 



> **openfly said:**
> 
I am pretty sure Samba 3 can act as a slave controller in an AD domain.  Not 100% but I remember reading a lot about that when it first came out.  

My understanding is that Samba cannot act as a PDC in an active directory domain ....

There are no slaves, PDC's, BDC's ... in Active Directory Domains, all domain controllers are equal and interchangeable (except for the fact that only 1 holds the role of Schema Master). So a Samba AD Domain Controller would have to be an AD Domain Controller. To my knowledge Samba 3 can be used as an NT4 PDC or BDC, or as an AD Domain member, but not an AD DC. 
Whether that has anything to do with the Kerberos issues you mention, I don't know.

As to the file locking issues you mention, I've been running 2 samba file servers in an AD domain for close to 2  years now, with posix ACL and domain accounts for 150 users in a win 2003 AD Domain, and never saw any of the issues you mention ...

---

### Post by openfly on 2009-09-24
I'm going to stick with AD being the easier interface for network printing management.  You know it is too.

As for domain management... it's a toss up.  I think the UI for AD is nice for Directory Services management... adding / deleting users, systems, printers.  Setting permissions... the day to day.

But I think the linux solution will be better for automation.  Powershell is no replacement for unix.

So it's hard for me to say which is better over all from the administrative point.

I've not had a chance to read through the release notes on samba4 and basically everywhere I've worked in the past 5 years has been either E-dir or AD.  

My biggest gripe with AD is setting permissions on directory structures takes forever.  E-dir handles permissioning of directory structures WAY WAY better.

Samba has similar problems to AD in this respect.

But if your client base is 15 users it's hardly worth it to even have a domain controller.

=/

You could go either way at that point.  But, I still say AD will be easier for a newbie, and that there will be less compatibility issues with AD.

---

### Post by koenn on 2009-09-24
Seeing that we started with this
> **gforster said:**
>  about 15 Windows 2000 computers 
> **openfly said:**
> I hate to say it, but your use case would be best met by Active Directory.

and we ended up with 
> **openfly said:**
>  But if your client base is 15 users it's hardly worth it to even have a domain controller.
I think I made my point.



and the OP can make up his own mind based on the arguments presented in the discussion.

---

### Post by gforster on 2009-09-24
Wow, so much to think about. Thank you for the good discussion. I love having to think through the different options. 

It makes me ask myself why we have a domain controller. I have no idea why - it was just set that way before I was ever here. Like I said earlier - I am decently proficient on the desktop, but when it comes to networking I am out of my league. I can basically follow the discussion, but have a limited understanding of networking and the roles/purposes of the different types of servers.

Can you recommend any specific resources where I might learn more? I'd love to take some classes, but am afraid I simply don't have the time.

---

### Post by foremannz on 2009-09-24
Windows 2003 and Active Directory are great to have if you already have them - in terms of compatability, seemless authentication and support, its pretty hard to beat.  As much as I hate microsoft, you cannot ignore the shear software support and integration available.

As for setting up security over shared folders, create a usergroup for group based permissions, assign permissions for your files and folders to the group name, then assign usernames to the groups - makes admin of them a heap easier in the long run.  You can also replicate permissions assigned to the current folder to subfolders and files with a tick.

As for printers, I used Kix script for remote adds and removes of printers based on usergroup permissions under Windows Server - was pretty easy too!

I would still persevere with Windows Server at present, but the more applications become web hosted, the less dependancy there will be on the operating system.

---

### Post by JonRohan on 2009-09-24
For 15 desktops you may as well have a Linux box with local users (forget AD stuff) and have the users log onto a PC with the same local username and password on the Linux server. 

Keep it simple. Your printer however, could be a different story. 

The other option would be to reload the Windows 2003 server and setup AD from scratch. For 15 users it will work with little effort and I assume of no extra cost as you already have licensing?

---

### Post by foremannz on 2009-09-24
> **JonRohan said:**
> For 15 desktops you may as well have a Linux box with local users (forget AD stuff) and have the users log onto a PC with the same local username and password on the Linux server.
Would that mean you would have to create a user account for each user on each computer they are going to use?  If so, thats 1 less thing you have to do with a microsoft network if all the client computers are microsoft and joined to the domain

---

### Post by JonRohan on 2009-09-24
I made the assumption that most users will only use one computer. If not then that is not practical at all as you've stated.

---

### Post by foremannz on 2009-09-24
Yeah, under a perfect world, everyone would have their own computer, but unfortionately users want to access any and all the computers, then when they change their password, everything turns to crap unless the logins all authenticate to a single company account list like Active Directory.

---

### Post by Lars Noodén on 2009-09-25
> **koenn said:**
> If today he's migrating away from Windows Server and AD, 
hopefully 1 year from now he'll have the good sense to pick an IP telephony solution that does not depend on  Windows + AD.

The IP telephony solution to look for, both for quality and function as well as being open source would be [Asterisk](http://www.asterisk.org/).  
[http://www.asterisk.org/](http://www.asterisk.org/)

Asterisk PBX / VoIP is extensible and integrates nicely with many other tools.

The opportunity to move away from vendor lock-in and towards open standards is not going to go lightly because of push from Microsoft representatives or proxies.  They will do what they can to saturate, diffuse or confuse the issue.  That includes drowning discussions in blather.  It would not be unwarranted for the OP to expect a call to the boss' boss from one of them soon.  Because once the OP can get use FOSS to return to a situation where technologies are evaluated based on their merits or their value for money ratio rather than origin from a specific vendor, the Microsoft infrastructure goes out the door.

AD is not magic.  It's one way of many of doing things.  It seems a broken copy of NDS, using broken pieces of Kerberos and LDAP.  Roaming accounts and single sign-on has been available in multiple forms since before Microsoft even decided to begin to copy NDS.  The one advantage of AD is that it is a gateway to Samba, which then leads the rest of the infrastructure back to high tech.

---

### Post by openfly on 2009-09-25
> **Lars Noodén said:**
> Because once the OP can get use FOSS to return to a situation where technologies are evaluated based on their merits or their value for money ratio rather than origin from a specific vendor, the Microsoft infrastructure goes out the door.

AD is not magic.  It's one way of many of doing things.  It seems a broken copy of NDS, using broken pieces of Kerberos and LDAP.  Roaming accounts and single sign-on has been available in multiple forms since before Microsoft even decided to begin to copy NDS.  The one advantage of AD is that it is a gateway to Samba, which then leads the rest of the infrastructure back to high tech.

Lars, while I too believe in a true meritocracy when it comes to evaluating solutions, I believe that you have made a bit of an implied false accusation.  Microsoft infrastructure does have it's merits.  AD for instance as an all in one authentication, file / print sharing, and directory service beats the ever loving crap out of anything Linux based.  Now I won't go after Sun One, because my understanding is Sun One can actually compete with AD.  And I'll say that E-dir as a single product.. may be the most effective directory service on the planet.

I love open source, and open standards make everyones lives easier... but when you start deploying these guys in scale you realize their benefits.

With AD you have an all in one, relatively simple interface to Kerberos / LDAP / Samba feature sets... as well as custom integration with windows PCs.   Linux doesn't have that.  And to be honest the SPNEGO support throughout windows products allows for kerberos deployment across the network FAR more easily than GSSAPI / SASL ( via GSSAPI ) authentication.  In fact, I'd dare say that FOSS devs chronically overlook kerberos integration.  I mean mod_auth_kerb is a steaming pile of fecal matter.  PHP's concept of kerberos auth is a single module hidden in the svn repot for horde and not updated in something like 5 years.

If you are going to claim that Microsoft's implementation of Kerberos / NIS / Samba is broken... I'd like to throw that back in your face.  FOSS solutions are on the whole a lot more broken.

Samba is lacking a bunch of key functionality and has serious problems mimicking the growing changes in AD domains.  It also simply doesn't scale well at all thus... no one using it.  And in terms of mimicking samba functionality without samba.... NFS wasn't kerberized until NFSv4.  And they stole most of their code from Andrew Filesystem... which OH MY GOD will burn some serious neural ganglia if you ever get stuck deploying that.    

Kerberized OpenLDAP is a giant pain.  Try it out sometime.  Something like 90% of the documentation on it is either grossly out of date, or completely fabricated.  Actually what's really awesome was at one point SASL had docs on how kerb5 auth worked... that had been written prior to the actual support being incorporated... so the docs were COMPLETELY WRONG.  

Oh and in terms of Microsoft having "broken" kerberos... that's an argument.  The miscellaneous field exists in the RFC spec.  The only concern is whether they are allowed to exceed specific ticket sizes... and I think they've got a valid point about their tickets not being too overbearingly large and truthfully I think it was originally a design decision.

If you think that tech people the world over are swayed entirely by the efforts of sales reps you are sorely mistaken.  The simple fact is, sometimes FOSS apps suck even more than pay apps.  Linux isn't some pinnacle of success and all that is right in technology.  Linux itself has a completely busted TCP/IP stack that Linus refuses to do anything about.  In fact 2.6.1-2.6.2x were pretty much broken *** steaming piles of fecal matter.  If you don't believe me just read -AC release notes on them... SCARY stuff.

In short, get down off your high horse mate.  Stop believing the hype and look at the solutions based on their ACTUAL merits.  Not your crazy misconceptions concerning them.  AD beats the ever loving crap out of any FOSS application or applications working in tandem that exist to mimic it's functionality.  I wish that weren't the case but they have the money, the test environments, and the people to make this stuff happen and FOSS does not.

---

### Post by koenn on 2009-09-25
> **gforster said:**
> 
It makes me ask myself why we have a domain controller. 
Because you also had MS Exchange - you can't run MS Exchange without Active Directory - they're so integrated it"s actually scary.

The thing with AD is, it comes with windows server at no extra cost, so it's easy to decide to just go and use it, because it makes some things easier (eg a central UI for managing user and computer configs, the luxury of centrally managed accounts to facilitate free seeting, ... ) 

The downside is that every AD domain is unique - if your Domain controller crashes beyond repair (and you have only on DC), you"ll either have to recover the DC on new hardware (with possibly loads of hardware issues to work through cause the system you've backed up is configured for different hardware), or build a new domain from scratch and work through a load of issues with domain accounts that suddenly become invalid because they refer to accounts in the old, now non-existant domain. If you only have to deal with NTFS ACL's that's still doable. When you're dealing with AD-integrated services such as Exchange or an MS SQL in AD Integrated mode, this can be quite a challenge.

---

### Post by Lars Noodén on 2009-09-27
> **koenn said:**
> Because you also had MS Exchange - you can't run MS Exchange without Active Directory - they're so integrated it"s actually scary.
...
If you only have to deal with NTFS ACL's that's still doable. When you're dealing with AD-integrated services such as Exchange or an MS SQL in AD Integrated mode, this can be quite a challenge.

Yes, vendor lock-in is a real PITA.  It's possible to write a book about all the problems brought in by MS Exchange.  It gets harder to get out from a test of MS products when MS marketeers and in-house proxies won't ever mention the tools being copied, especially the top of the line tools.  

If there is a MS Exchange infection, that can be cleared up using [Kolab](http://www.kolab.org/) or [Citadel](http://www.citadel.org/).  There are others, too, like Zimbra or OpenGroupware.  These four are modular and use standards so they are easy to install, set up, or replace.

---

### Post by JonRohan on 2009-09-27
> **koenn said:**
> Because you also had MS Exchange - you can't run MS Exchange without Active Directory - they're so integrated it"s actually scary.

The thing with AD is, it comes with windows server at no extra cost, so it's easy to decide to just go and use it, because it makes some things easier (eg a central UI for managing user and computer configs, the luxury of centrally managed accounts to facilitate free seeting, ... ) 

The downside is that every AD domain is unique - if your Domain controller crashes beyond repair (and you have only on DC), you"ll either have to recover the DC on new hardware (with possibly loads of hardware issues to work through cause the system you've backed up is configured for different hardware), or build a new domain from scratch and work through a load of issues with domain accounts that suddenly become invalid because they refer to accounts in the old, now non-existant domain. If you only have to deal with NTFS ACL's that's still doable. When you're dealing with AD-integrated services such as Exchange or an MS SQL in AD Integrated mode, this can be quite a challenge.

Doing a system state backup on your domain controller with other full system backups will negate most of the problems you have mentioned with AD. Yes it will be a slight PITA to restore exchange ontop of a new DC but it is by no means impossible.

---

### Post by koenn on 2009-09-27
> **JonRohan said:**
> Doing a system state backup on your domain controller with other full system backups will negate most of the problems you have mentioned with AD. Yes it will be a slight PITA to restore exchange on top of a new DC but it is by no means impossible.
yes, I know.
and  how many of those " small business I'm not scared of computers so I got to play sysadmin" people know what a system state backup is ? Or that on Technet  there are  instructions to restore exchange but they better have read them * before* a problem occurs ... ?

---

### Post by JonRohan on 2009-09-27
> **koenn said:**
> yes, I know.
and  how many of those " small business I'm not scared of computers so I got to play sysadmin" people know what a system state backup is ? Or that on Technet  there are  instructions to restore exchange but they better have read them * before* a problem occurs ... ?

They would soon learn. ;)

Similarly the same logic would apply for Linux in this particular case. If I’ve understood correctly the OP is not a Linux server expert. 

Therefore, what if the Linux system managing centralized authentication as discussed breaks, and the “small business I'm not scared of computers so I got to play sysadmin" person does not know how to perform Linux backups and restores? 

The end result is the same, if the person in charge of the network cannot backup correctly they are going to struggle restoring data. Whether they are running Windows, Linux, Unix and or OSX.

---

### Post by koenn on 2009-09-27
> **JonRohan said:**
> They would soon learn. ;)

Similarly the same logic would apply for Linux in this particular case. If I&#8217;ve understood correctly the OP is not a Linux server expert. 

The difference would be that most people who are a bit computer savvy, have heard about backups. And a simple file backup of a linux server would almost always be sufficient to restore a server.



Apart from that, you do have a point, all to often people assume that "being good with computers" automatically makes someone "good at system administration"

---

### Post by HermanAB on 2009-09-27
For a bunch of Windows machines, you have to use ADS. Samba version 4 is not a decent substitute (yet).
  
"The downside is that every AD domain is unique"

Major Tip: The best way to deploy ADS is on VMware.

---

### Post by kewlrichie on 2009-09-27
Hey guys I have been looking into this option also and with the how/to on samba4 wiki looks pretty do-able there is even a ubuntu 9.04 guide. I will post the links

[http://wiki.samba.org/index.php/Samba4/HOWTO](http://wiki.samba.org/index.php/Samba4/HOWTO)

and 

[http://wiki.samba.org/index.php/Samba4/HOWTO/Ubuntu_Server_9.04](http://wiki.samba.org/index.php/Samba4/HOWTO/Ubuntu_Server_9.04)

so what do you guys think
rich

---

### Post by HermanAB on 2009-09-27
It will probably work for a small number of WinXP clients.

---

### Post by openfly on 2009-09-28
I still say you'd be better off sticking to AD.

---

