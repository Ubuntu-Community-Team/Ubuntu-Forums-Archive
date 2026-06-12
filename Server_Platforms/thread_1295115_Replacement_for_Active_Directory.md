---
title: "Replacement for Active Directory"
date: 2009-10-19
forum: Server Platforms
---

### Post by Deniska on 2009-10-19
Hi all. At first - sorry for my poor english.
I know - there are a lot of threads in this forum about open source replacement for AD. There are guides for ebox, mandriva directory server, fedora (389) directory server, openldap server etc. At brainstorm.ubuntu.com i've found ideas about implementing installation of such services (openldap + samba + etc) through tasksel menu.
I'm interesting - is this feature planned? If yeas - in which version of server distributive it will appear? Is there are any ETA? What devs thinking about integrating in server platform a replacement for AD? What functionality they wish to implement?
For me, most important AD directory service feature is only single sign on point and joining windows machine in a domain. This can be replaced by OpenLDAP + Samba, but i don't know how will replication works and how roaming profiles can be implemented. Also, i still can't find good tools for replacement of ad - users and computers, ad - domains and trusts, etc tools. For other AD features replacements can be found. For example, [Cfengine](http://en.wikipedia.org/wiki/Cfengine) or something else instead of Group Policies.
Atm i just can't migrate from windows to ubuntu because i can't easily setup flexible directory service. ): I'm looking for multidomain structure, PDC & BDC, easy replication and administration.

Sorry if this information is published somewhere else. I can't find it on a ubuntuforums.org/ubuntu.com.

---

### Post by Lars Noodén on 2009-10-20
AD is a closed source copy (slightly broken) of kerberos+ldap+ a tool like a tool like [puppet](http://packages.ubuntu.com/jaunty/puppet) or [radmind](http://rsug.itd.umich.edu/software/radmind/). 

Samba is available right now.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)


[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
[http://www.howtoforge.com/ubuntu-9.0...tive-directory](http://www.howtoforge.com/ubuntu-9.0...tive-directory)

---

### Post by drumbug1 on 2009-10-20
You can't find anything right now because there is no "drop in" replacement for Microsoft Active Directory.

It sounds like you've seen bits and pieces of what exists....  a great deal of it is 'build your own' solutions or other non-free start-ups that don't have widespread use (not that there's anything wrong with that).

At the moment nothing is officially announced/planned from Ubuntu/Canonical.

The closest is the official "server guides" which have small how-to sections for Network Authentication, Samba Shares, etc (but not a complete solution like you're looking for):

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html) (8.04 LTS)
[https://help.ubuntu.com/9.04/serverguide/C/index.html](https://help.ubuntu.com/9.04/serverguide/C/index.html) (9.04)

---

### Post by Lars Noodén on 2009-10-21
> **drumbug1 said:**
>  a great deal of it is 'build your own' solutions 

Dude, that's what AD is a copy of, with two degrees of separation.  The late, great NDS was what AD appears to be trying to copy directly.  Although, NDS was relatively fast and scalable, and much, much more interoperable and easy to deploy.  

The maker of MS Windows didn't come out with managed directory services untill 2003 or so, way behind the closed source world and close to a decade behind the open source world.   Ultimately, with the maker of MS Windows moving the interoperability goal posts constantly, the only option is a complete migration back to open standards, if not also open source.

Putting the pieces together is not a big deal, just not as common due to marketing and harassment of non-MS sites.

---

### Post by drumbug1 on 2009-10-21
> **Lars Noodén said:**
> Dude, that's what AD is a copy of, with two degrees of separation.....

<<SNIP>>

Putting the pieces together is not a big deal, just not as common due to marketing and harassment of non-MS sites.

Lars - I'm with you 100%.  I'm not sure if you thought I was implying that nothing was "as good" as AD - by no means.  AD *is* a broken rip off of much older technologies.  

My intent was to answer the original poster's question by saying that there is no "one" accepted solution similar to AD.

I fully believe that *everything* AD can do.... you can do on Linux/UNIX/etc (albeit a little differently in some instances).
:-D :-D :-D :-D

---

### Post by rickyjones on 2009-10-21
> **Lars Noodén said:**
> The maker of MS Windows didn't come out with managed directory services untill 2003 or so, way behind the closed source world and close to a decade behind the open source world.   Ultimately, with the maker of MS Windows moving the interoperability goal posts constantly, the only option is a complete migration back to open standards, if not also open source.

Microsoft had Active Directory in Windows 2000 Server. Before that was the older style NT Domain, where you had a Primary domain controller and Backup domain controllers.

> 
Putting the pieces together is not a big deal, just not as common due to marketing and harassment of non-MS sites.
In my opinion it is kind of a big deal, and so far I have yet to see a 100% Open source implementation that rivals Active Directory. I've tried to piece it together, and I can get something that works, but it more difficult to manage and has less redundancy then an Active Directory domain.

I await the day where there is a fully open-source directory services system that rivals, and beats, Microsoft's Active Directory :)

Thanks,
Richard

---

### Post by lykwydchykyn on 2009-10-21
Reality check here folks.

Most people could stumble through setting up an Active Directory knowing nothing whatsoever, and manage to get basic functionality out of it.  Can't say the same for the various LDAP solutions out there.  Not that I'm a genius, but I spent a fair amount of time years back trying to find a workable AD-like solution for Linux and never actually managed to get anything working.  

Samba 4 is targeted to be a drop-in Active Directory replacement.  Read about it here: [http://wiki.samba.org/index.php/Samba4](http://wiki.samba.org/index.php/Samba4)

And, for the record, NDS is not dead, it's just called eDirectory.  Still in use in many places (including where I work).  And it runs on Linux, if you choose.

---

### Post by drumbug1 on 2009-10-21
> **lykwydchykyn said:**
> Reality check here folks.

Most people could stumble through setting up an Active Directory knowing nothing whatsoever, and manage to get basic functionality out of it.  Can't say the same for the various LDAP solutions out there.  Not that I'm a genius, but I spent a fair amount of time years back trying to find a workable AD-like solution for Linux and never actually managed to get anything working.  

Samba 4 is targeted to be a drop-in Active Directory replacement.  Read about it here: [http://wiki.samba.org/index.php/Samba4](http://wiki.samba.org/index.php/Samba4)

And, for the record, NDS is not dead, it's just called eDirectory.  Still in use in many places (including where I work).  And it runs on Linux, if you choose.

Samba 4 looks *very cool*.  I installed it 6 months or so ago and was able to join a WinXP Pro machine with little trouble.  It's still in development and not ready for production use - currently with no announced release date.  

Here's the how-to I used:

[http://wiki.samba.org/index.php/Samba4/HOWTO](http://wiki.samba.org/index.php/Samba4/HOWTO)

Another interesting thing to watch for is the OpenChange Server, a planned MS Exchange clone (which is planned to work with Samba 4).  It's not fully implemented yet, but there is a howto included in the source download to setup (for development/testing) what's currently available.  It's also interesting to note that Ubuntu Server lists OpenChange library support "to enable Ubuntu system to interact with Exchange servers: libraries, command line tools and evolution plugin." that makes me think that Ubuntu would be interested in using the full OpenChange Server once it's ready.

Here's the Ubuntu Features list mentioning OpenChange libraries:
[http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs/whatsnew#msexchange](http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs/whatsnew#msexchange)

Here's the how-to:
[http://websvn.openchange.org/filedetails.php?repname=openchange&path=%2Ftrunk%2Fdoc%2Fhowto.txt](http://websvn.openchange.org/filedetails.php?repname=openchange&path=%2Ftrunk%2Fdoc%2Fhowto.txt)

On the Ubuntu side there are community rumblings to push for something that (like lykwydchykyn put it) most admins could "stumble through":

[http://brainstorm.ubuntu.com/idea/2179/](http://brainstorm.ubuntu.com/idea/2179/) (note that there's also 6 duplicates on the brainstorm site for similar ideas).

UPDATE:  I also just found out about Zivios today - they support Ubuntu 8.04 LTS... I'm going to be giving this a go in the next day or to.  Looks like it integrates with OpenLDAP, BIND, Kerberos, Apache, Squid, Samba, Asterix, MySQL, Postfix, Cyrus, ClamAV etc....  This could be another option for the OP to look into.

[http://www.zivios.org](http://www.zivios.org)

---

### Post by Deniska on 2009-10-23
Guys, sorry for my silence - i don't recieve notices about replies in topic.
Big thanks for your answers and spent time.
The main problem for me in search of AD alternatives is easy administration, flexibility, stability and easy deployment. Most of alternative realization of directory services are unstable or in beta stage of development (like samba 4). If i wish use some product in corporate network, i must do it fast. And administrative interface of directory services and other services like mail, proxy, ftp etc must be simple and comfortable for other administrators. In best case - they all can be integrated in unified tools (like MMC - Microsoft Management Console - with snap-ins for different services).
So.. if there are no such solutions - i'll be waiting for samba 4. (: I'm still interesting what devs are planned about directory service (and other services) implementation and integration.
Thank you all again. Now i'll start with migration of workstation from winxp to ubuntu/kubuntu and some services like mail to ubuntu server.

---

### Post by whoop on 2009-11-07
I think this technology is crucial for linux adoption. The documentation on this is scattered, out-of-date or incomplete. This is the most complete tutorial I could find: [http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)
It was written for ubuntu 7.10 (although it luckily works with 8.04, most part).

Documentation needs to updated and refined, please **vote**:
[http://brainstorm.ubuntu.com/idea/22151/](http://brainstorm.ubuntu.com/idea/22151/)

---

### Post by frk2 on 2009-12-03
Zivios is supposed to be an AD-like interface for managing opensource infrastructures. Its meant to be all-encompassing like AD so it would need to handle your NTP/DNS/DHCP/CA/Ldap/Kerberos all by itself. The API is left open so people can develop plugins for their own solutions - we currently have a tested Squid and 'Mail' solution plugin. 

Developing a Firewall and a Asterisk plugin at the moment. Comments are welcome!

[as you may have realized, im a developer at Zivios.org]

Thanks for your interest. After 5 years of consulting we REALLY wanted to give our clients/admins something that will make sure that mundane support calls are reduced.

---

### Post by Deniska on 2009-12-03
**frk2**, thanks a lot for the information. I'll test Zivios ASAP, if it met my requirements i'll drop AD and switch to pure OSS.

---

### Post by munky99999 on 2009-12-03
The reason business-enterprise computers are nearly 60% windows is pretty much solely because of active directory.

Samba can pretend to be an NT domain controller. However that's just plain sad.local.
Samba4 is still alpha and they are getting to the point being windows 2000 domain or so.

That's just so far behind it's sad. Microsoft afaik recently let the samba team in on the code of active directory. Why? BEcause they are getting so far ahead. They might just be considered sole dominate force in the field.

The FOSS community needs to get behind 1 AD alternative and blast it. However we just cant seem to do it. Just look at the thread. There's what? 5 different ones being suggested? Which are fairly equivalent with each other.

MY vote for the best one. Probably edirectory with [SUSE_Linux_Enterprise_Server]("http://en.wikipedia.org/wiki/SUSE_Linux_Enterprise_Server")

My futuresight however thinks [Apache's Directory server]("http://directory.apache.org/") Will be the one to bet the farm on.

---

### Post by lykwydchykyn on 2009-12-04
> **munky99999 said:**
>  Microsoft afaik recently let the samba team in on the code of active directory. Why? BEcause they are getting so far ahead. 
I kinda thought it was because the EU antitrust commission made them, but I'm not clear on that.
> 

MY vote for the best one. Probably edirectory with [SUSE_Linux_Enterprise_Server]("http://en.wikipedia.org/wiki/SUSE_Linux_Enterprise_Server")


eDirectory is a great system.  How about Novell makes it FOSS so it can run on anything, not just SUSE and a short list of alternatives?  How about Novell makes FOSS clients for it so it can be ported to any OS/distro, not just the ones sold by Novell corporate partners?  

Then I bet the FOSS community would actually get behind it.  Kind of hard for the FOSS community to be supportive of a solution that's (a) proprietary and (b) only works with Windows and two commercial linux distros. :(

---

### Post by frk2 on 2009-12-04
eDirectory is just that - its a directory server. AD is far more than a simplistic directory server as it provides you complete identity management. FDS or even openldap can replicate most of edirectory features. The reason AD is far ahead is due to tight integration with other applications such as exchange, the windows desktop, ISA, etc. Unless we have a platform for such integration we can never compete with AD. On top AD is dead simple (almost) to setup compared with any of the above and comes as a 'out of the box' solution. 

Samba4 is nice but its limited to windows. With Zivios we wanted to come up with a equivalent solution for Linux desktops as well. Atleast thats the idea. We might even look at using Samba4 as the base at a future stage. 

I believe that in the windows space - that is with windows desktops one can never hope to beat AD. its THEIR product. Whatever we do our AD-clone will always remain a hack job. Also the cost differential (once you have already paid for the desktops) is minimal with AD - its basically free. Our idea is to have a competing solution (featurewise) using Linux based desktops and a complete OSS architecture. I dont think any CIO will get a thump on the back for saving the $20-$25 AD CAL after spending $400+ on a windows desktop!!!

---

### Post by Lars Noodén on 2009-12-04
> **munky99999 said:**
>  Microsoft afaik recently let the samba team in on the code of active directory. Why?

@ munky99999 : if you got paid to write that, please [disclose the employer and nature of your work](http://www.washingtonpost.com/wp-dyn/content/article/2006/12/11/AR2006121101389.html).  

@ lykwydchykyn : AD's main selling point is more lock-in and your recollection is correct.  MS was forced to disclose the protocols because its leaders had been using them to illegally stifle competition:

[Samba Team Receives Microsoft Protocol Documentation -Updated 2Xs](http://www.groklaw.net/articlebasic.php?story=20071220124013919) from 2007.

[Want to meet four men who dared to fight MS -- and won?](http://www.groklaw.net/articlebasic.php?story=20070919214307459) from 2007.  

Again, at the bottom AD copies NDS from Novell, but has lots of hooks and tie-ins to make it hard and confusing to deal with.  For example, the clock synchronization on regular computers happens via NTP.  Windows has some apparently fake ntp support, but the real clock synchronizaton is tied into AD.  On regular computers, authentication is handled by Kerberos, on Windows it is attempted by AD, though might still be possible to install kerberos (it got hard after Win2000).  Groups: LDAP vs AD.

---

### Post by lykwydchykyn on 2009-12-04
> **frk2 said:**
> eDirectory is just that - its a directory server. AD is far more than a simplistic directory server as it provides you complete identity management. FDS or even openldap can replicate most of edirectory features. The reason AD is far ahead is due to tight integration with other applications such as exchange, the windows desktop, ISA, etc. Unless we have a platform for such integration we can never compete with AD. On top AD is dead simple (almost) to setup compared with any of the above and comes as a 'out of the box' solution. 

Samba4 is nice but its limited to windows. With Zivios we wanted to come up with a equivalent solution for Linux desktops as well. Atleast thats the idea. We might even look at using Samba4 as the base at a future stage. 

I believe that in the windows space - that is with windows desktops one can never hope to beat AD. its THEIR product. Whatever we do our AD-clone will always remain a hack job. Also the cost differential (once you have already paid for the desktops) is minimal with AD - its basically free. Our idea is to have a competing solution (featurewise) using Linux based desktops and a complete OSS architecture. I dont think any CIO will get a thump on the back for saving the $20-$25 AD CAL after spending $400+ on a windows desktop!!!

You're forgetting that Novell has a whole host of products that integrate with eDirectory (GroupWise, Zenworks, etc).  And third-party support isn't too bad, though it isn't up there with AD (but that's to be expected, I guess).  

But like I said, it's all proprietary.  If it were open, I suspect the "gaps" between it and AD could be rectified, but I don't think that'll ever happen.  Novell has pretty much adopted the "FOSS with proprietary value-add" business model, and eDirectory is one of their few cash cows as far as I can see.

I think your idea is great, I hope it works out well.  I'll be keeping an eye on Zivios.

---

### Post by munky99999 on 2009-12-04
> I kinda thought it was because the EU antitrust commission made them, but I'm not clear on that.
I really have no idea what got them to open it up. Doesnt really matter much.

> eDirectory is a great system. How about Novell makes it FOSS so it can run on anything, not just SUSE and a short list of alternatives? How about Novell makes FOSS clients for it so it can be ported to any OS/distro, not just the ones sold by Novell corporate partners?

Then I bet the FOSS community would actually get behind it. Kind of hard for the FOSS community to be supportive of a solution that's (a) proprietary and (b) only works with Windows and two commercial linux distros.
I agree completely. If they did this. It would certainly make them the lead. I hwoever see edirectory being pretty old and they've already somewhat embraced FOSS as it is. So I have a feeling they just dont want to make it open source... or cant perhaps due to some contracts that exist. I dunno. I just have a feeling it's more likely to have active directory from microsoft going open source then edirectory at this point.


Or perhaps Microsoft rolls its own linux distro which has open source active directory. Hahah


> @ munky99999 : if you got paid to write that, please disclose the employer and nature of your work. 
@ Lars Noodén First of all. FTC has no authority over me. I am not american. Furthermore... it's kinda public record the samba team got invited by microsoft to see the code. To answer your question. No I didnt get paid to write anything. I dont even have a job right now. The extent of my IT job experience is working sales in a store in the computer department. Then on the other side I pretty much hate microsoft. So um ya.

---

### Post by senor_smile on 2009-12-05
This may not be exactly what the OP is looking for, but it's sure worth a mention.  
[http://www.howtoforge.com/using-ebox-as-windows-primary-domain-controller](http://www.howtoforge.com/using-ebox-as-windows-primary-domain-controller)

That's a tutorial on using ebox's Samba PDC GUI feature to allow single sign on for windows boxes, controls acl's and manage file shares from the box.  I have tried ebox at a previous version with not a lot of luck, but this tutorial shows that it's possible to do all this with ease! If this works,  I'll finally be able to recommend an option other than buying windows 2003/2000.

---

### Post by hayasou on 2009-12-06
I think we should stay away from opening the endless topic of how evil Microsoft is. After all, we are on the Ubuntu Forums...so we all know that. Yet, that seems to be a good way of diverging when we don't have a straight answer.

Few facts: First MS OS that featured AD was Windows 2000 Server in 2000.
AD was actually "tried out" before that in MS Exchange Server 5.5.
AD is not a copy of NDS, it's a Microsoft proprietary implementation of the X.509 protocol (LDAP).
AD is actually not a huge deal by itself. What most people value about it is:

1. The tight integration of it with a whole bunch of other types of servers such as: Mail and Collaboration(MS Exchange), Database (MS SQL), Web (IIS and ASP.NET), DNS, DHCP, File&Print....The list goes on as basically any Microsoft product (and there are sooooo many they now work on through aquisitions, etc.) works with AD for user authentication at least.  

2. It's easy to install, configure and maintain. Of course you could argue that there's nothing difficult in changing text in a config file and I agree. Yet, most people seem to be able to get and AD server up and running (including DNS) in about 20 minutes.

Why Microsoft can offer all that and most FOSS server doesn't? Simple. Microsoft pours a bucket of 100$ bills/day into this and the FOSS does not.

The answer is dual: Yes, all this can be achieved with FOSS, including the integration but it's not gonna be cake. The pieces are out there but there's not even 1 complete tutorial or document on how to achieve this. You'll need to choose the pieces YOU WANT and put them together. But this is the beauty of using FOSS. You don't like gedit? No problem. There are about a billion other projects that do the same. That comes at the cost that no one spends efforts to "pre-integrate" them for you.

In the end I would see value in any Linux Distro putting together something like that on their "server" line. I would be the first to stop installing any more windowses.

I also think this would bring anyone who does it into a large market with very few competitors. (In fact I think MS ADS and Novell eDirectory are currently holding the DS market but MS beats Novell by far because they integrate it with a ....load of other server and desktop apps).

In case anyone is wondering, no, I do not work for Microsoft :). I am just trying to look at this whole thing with objectivity and cold blood. There is no single software that has no flaws and MS and Linux are no exceptions. I know many people whom are still throwing the word BSOD every time they talk about MS. But in all fairness this happens a lot less often than it used to and also in all fairness everyone seems to be completly oblivious to the fact that there is also the "kernel panic". BTW...who came up with that? 

And finally, I was here to ask the same question. Anyone knows a way( a software or platform or a tutorial) to achieve Authentication, Mail, Collaboration, Web, DNS integration a la ADS using FOSS? Please let me know.

---

