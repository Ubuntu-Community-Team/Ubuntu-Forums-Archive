---
title: "ubuntu replacing nt4 &amp; backoffice server?"
date: 2006-03-03
forum: Server Platforms
---

### Post by Cable Dog on 2006-03-03
Background:

I tried a few distro's a couple years ago when IP masquerade came out.  Command line interface ok once you are proficient, but point and click with help file definately saves me a lot of time reading.  Only familiar with Apache and Samba to the degree I got it setup and working once.  Server compromised (not to mention dated) and I have to reinstall something.  I am a typical hardcore gamer / power user looking for enterprise server benefits from my home with low cost (ubunta rates a 10 there) and easy administration.   

Services I Need:

User Authentication and share management on Linux compared to NT groups?

DNS - Linux equivalent?

Dynamic DNS - Currently I run a shareware ddns app as a service in NT.  Anyone use anything similiar for Linux?

Internet Information Server - Apache probably included.  Is the setup fairly easy or will I be reading man pages?  Can I securely share my www root on my local?

FTP - Linux equivalent?  Can I securely share my FTP folder to windows clients on my local?

Exchange Server 5.5 - Linux equivalent?  Is it easy to secure or am I going to have to delete 60-100 unwanted emails out of my outbound que everyday?  Are there spam filters, webmail access, and easy administration?

SQL Server - Set up MySql once and its probably included or other?

Centralized File Sharing with Windows XP & 98SE clients - I recall doing some reading when I tried Samba a few years ago... has it gotten easier?  Has it improved?

Network Administration - I am not a full time network adminstrator and my servers are probably easy targets for experienced malicious users.  Will ubuntu help me in this area with any built in firewalls or other security enhancements?

I am trying to decide if ubuntu will meet my needs (which are pretty basic for a server and small network) or do I need to spend $xxx for a different linux product?  A linux server appliance would be nice but I am not spending $xxxx.  Any feedback appreciated.  If I'm in the wrong forum flame away.

---

### Post by Cable Dog on 2006-03-03
I forgot to ask about VPN in my original post.  Is it included?

---

### Post by garyng on 2006-03-03
I have done all the above with debian(and I believe similar in ubuntu or fedora or suse or any major distro).

However, all would require you to read and manually do them one by one mostly through text editor.

So if you want a simple "user friendly" solution, pay the $$$ and get what MS offered, W2K or 2003 + exchange.

Though I would say that Lotus Domino(which has free trial version) is much better than Exchange :-)

---

### Post by LordHunter317 on 2006-03-04
[QUOTE=Cable Dog]User Authentication and share management on Linux compared to NT groups?[/quote]Samba can function as a NT4 PDC equivalent.  If you want unified users/groups across multiple linux machines, you have to do LDAP/KerberosV.  Not fun to setup.

> DNS - Linux equivalent?BIND.

> Dynamic DNS - Currently I run a shareware ddns app as a service in NT.  Anyone use anything similiar for Linux?It depends on your DDNS provider but several exist

> Internet Information Server - Apache probably included.  Is the setup fairly easy or will I be reading man pages?  Can I securely share my www root on my local?You will  be reading Apache documentation at some point.  And I fail to see what the webserver has to do with the latter.

> FTP - Linux equivalent?  Can I securely share my FTP folder to windows clients on my local?Yes, but why?  

> Exchange Server 5.5 - Linux equivalent?Not strictly.  If you just want email, postfix+IMAP server gets you there.

>  Is it easy to secure or am I going to have to delete 60-100 unwanted emails out of my outbound que everyday?Only if you break it.

>   Are there spam filters, webmail access, and easy administration?Yes, yes, and depends on what you mean.  Exchange 5.5 is hardly easy to adminster correctly.

> SQL Server - Set up MySql once and its probably included or other?This isn't so easy, most applications can only use a few DBMSes, if that.

> Centralized File Sharing with Windows XP & 98SE clients - I recall doing some reading when I tried Samba a few years ago... has it gotten easier?  Has it improved?Configuring it isn't any easier, but its far better performing.

---

### Post by Cable Dog on 2006-03-04
Thank you for the detailed reply LordHunter317.  Very helpfull.  There are so many app options it really helps to narrow down what packages I should be focusing on.

I'll read up on LDAP/KerberosV - I am assuming it will do group policies for windows clients in addition to linux?  Or will I still need NT4 for a PDC?  What is the linux equivalent to active directory?

Regarding postfix & IMAP - yes I am just looking for email.  Is there a more popular app or is this the one I should read up on?  My main priority for email is preventing my domain from getting blacklisted so to speak.

Hope this question isn't to far off base for this forum.  Regarding SELinux... Is unbuntu the way to go or should I consider Fedora for free selinux?  I was looking at ubuntu SELinux page yesterday and it looks like they are still working on the majority of it for this dist.

The reason I asked about ftp & www root on the local is I only want my administrator group to be able to drop and drag new content on my local.  From your reply I gather this is probably a samba & LDAP configuration issue.

I was impressed with this site:
[http://yolinux.com/TUTORIALS/LinuxTutorialInternetSecurity.html#SECURITY](http://yolinux.com/TUTORIALS/LinuxTutorialInternetSecurity.html#SECURITY)
Would you recomend any others?

Thanks

---

### Post by LordHunter317 on 2006-03-04
[QUOTE=Cable Dog]I'll read up on LDAP/KerberosV - I am assuming it will do group policies for windows clients in addition to linux?[/quote]No, it won't.  If you want to control Windows clients, setup Samba to run as an NT4 PDC.  You can then setup all your machines, including your Linux ones, to authenticate from that server.

> Or will I still need NT4 for a PDC?  What is the linux equivalent to active directory?There isn't, strictly speaking.  LDAP/KerberosV will handle the authentication and centralized login part, but nothing can properly do AD-level GPOs and all sorts of Windows features.

FWIW, at it's core, AD is based on LDAP and Kerbereos.  When you learn about those, you can figure out where the boundaries are pretty quickly, I'd reckon.

> Regarding postfix & IMAP - yes I am just looking for email.  Is there a more popular app or is this the one I should read up on?It's what I do, yes.

> Regarding SELinux... Is unbuntu the way to go or should I consider Fedora for free selinux? You should consider neither, and pretend SELinux doesn't exist.  FC and RHEL have SELinux policies, but they're still poor enough in quality to be useless.  They require all sorts of extra configuration to get working and don't provide substantial security gains.

---

### Post by Cable Dog on 2006-03-04
Thanks garyng for your feedback.  I would definately agree with you I would spend less time migrating to 2k or 2003.  I still have a learning curve hurdle with active directory if I were to go that route.  I really think in the long run I will be better off moving to linux even if I got to do a lot of reading and spend six months+ tinkering.  There is a server hardware issue at hand as well.  And I am probably like most others, my servers are my hand me downs.  Which would really date my machines going to 2k or 2003.

---

### Post by Cable Dog on 2006-03-04
Thanks again LordHunter317.

Final questions. 

Will ubuntu be a good dist. for me? 

Are all the packages I need included in the ISO?

---

### Post by garyng on 2006-03-04
[QUOTE=Cable Dog]Thanks garyng for your feedback.  I would definately agree with you I would spend less time migrating to 2k or 2003.  I still have a learning curve hurdle with active directory if I were to go that route.  I really think in the long run I will be better off moving to linux even if I got to do a lot of reading and spend six months+ tinkering.  There is a server hardware issue at hand as well.  And I am probably like most others, my servers are my hand me downs.  Which would really date my machines going to 2k or 2003.[/QUOTE]

Learning linux is good and it needs to be learnt only once that can be helpful in the future to replicate the same to other work environments. 

What I just wanted to say was that Windows server actually are very good for the functions you mentioned and the price is reasonable if you count in the time factor.

BTW, I personally think that debian is better for these server tasks comparing to ubuntu and if you ever want to run proprietory stuff like Oracle,  redhat/suse would be even better as there are more supports you can find. I once have trouble installing sybase on debian. 

The mentioned features are all in ubuntu main, i.e. the ISO but that is not a big issue as you can always pull from the net using apt.

The only thing I believe is not in standard ubuntu is VPN, assuming you want simple client interface from Windows machine. You can run things like openvpn but that requires you to install it on every client. I opt for MS PPTP which is there for every Windows since 98(?). It is said to be less safe but is good enough for me.

You would need a kernel module to support it that I believe is not in main, probably in universe/multiverse.

---

### Post by Ptero-4 on 2006-03-05
Cable. Most of what you need is in the ISO. And if you need something else just use apt. Ubuntu have a pretty complete repository.

---

### Post by Cable Dog on 2006-03-05
Thanks garyng and ptero-4 for the followup.  I know which modules I will be reading up on.  Only thing left is the doing.  I'll probably have a silly question in the future when I am ready to pull my hair out and throw the server across the room at some point during this migration.  Till then...

---

