---
title: "Ubuntu Server User Management"
date: 2005-09-30
forum: Server Platforms
---

### Post by ztrek7 on 2005-09-30
I am getting ready to set up a test server with some test clients to see if I can get some of our users applications to run properly and if I can go with a linux server / client setup. My question:

What is the recommended setup for user authentication and control? 

Windows has Active Directory which lets me handle all users at a central location, manage printers, software, security settings, etc. 

What way are you supposed to do it in linux?

I searched the net, some articles suggest NIS. But, from reading, doesn't that just synchronize EVERY user name and password to ALL machines? Doesn't sound to secure to me and introduces overhead. Changes are not immediate either.

Others suggest openLDAP. But that is just for user name and pass management right? What about security, software, settings, etc? How about a nice GUI?

About file sharing.. . Should I go with SAMBA or NFS?

Antivirus? Is there a centrally managed AV server like symantec?

How about printer management? Does NFS do that or do I go with SAMBA tied to LDAP server?

Anything I am forgetting???

Any guidance would be great!

PS - I could not find the "HOWTO's" forum to see if this has been covered. How about a link to it?

Jeremy

---

### Post by Beernut on 2005-10-01
[QUOTE=ztrek7]
What is the recommended setup for user authentication and control? 
Windows has Active Directory which lets me handle all users at a central location, manage printers, software, security settings, etc. 
What way are you supposed to do it in linux?[/QUOTE]
[http://us5.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html#id2543061](http://us5.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html#id2543061)
Sound like your still going to have windows clients so you want to be looking at Samba.
[QUOTE=ztrek7]Others suggest openLDAP. But that is just for user name and pass management right? What about security, software, settings, etc? How about a nice GUI?[/QUOTE]
[http://us5.samba.org/samba/GUI/](http://us5.samba.org/samba/GUI/)
[QUOTE=ztrek7]About file sharing.. . Should I go with SAMBA or NFS?[/QUOTE]
For Windows file sharing you need to use SAMBA.
[QUOTE=ztrek7]Antivirus? Is there a centrally managed AV server like symantec?[/QUOTE]
[http://www.clamav.net/abstract.html#pagestart](http://www.clamav.net/abstract.html#pagestart)
[QUOTE=ztrek7]How about printer management? Does NFS do that or do I go with SAMBA tied to LDAP server?[/QUOTE]
I might be wrong but for Windows printing you need to use SAMBA.
So SAMBA seems to be the answer I bought the book using Samba which is excellent it's also available online.  [http://www.oreilly.com/catalog/samba/chapter/book/index.html](http://www.oreilly.com/catalog/samba/chapter/book/index.html)

---

### Post by LordHunter317 on 2005-10-01
[QUOTE=ztrek7]What is the recommended setup for user authentication and control?[/quote]This pretty much depends on your setup.  If you're already using Active Directory and don't intend on ever replacing it (and you probably shouldn't) then you have two logical paths:[list=1][*]For machines where no network mounting will occur between Windows machines, and users cannot get shell accounts, use winbind.[*]Otherwise, you need to add the UNIX schema (RFC 2307), the eaisest way is to simply install SFU on your schema master, and use ldap and kerberos to authenticate off of AD.  Use Kerberos for authentication, and LDAP for Gecos retreival[/list]

> What way are you supposed to do it in linux?In a pure Linux environment?  With LDAP and Kerberos, same as AD.  

> I searched the net, some articles suggest NIS.It's old hat.

> But, from reading, doesn't that just synchronize EVERY user name and password to ALL machines?Essentially.

> Doesn't sound to secure to me and introduces overhead.I'm not aware of any huge security issues besides the fact it requires a trusted internal network (so does NFS, so that's not new) and all network authentication solutions have overhead. 

> Others suggest openLDAP. But that is just for user name and pass management right?Well, you can stuff whatever you want in the LDAP server, but tools to use it are limited.

> What about security, software, settings, etc?You don't.  Linux doesn't really have GPO equivalents (GNOME has some limited equivalence via gconf).  However, cfengine can be used to enforce as many things as you want.

> How about a nice GUI?No awesome ones exist for any of this.

> About file sharing.. . Should I go with SAMBA or NFS?Samba.  NFS should only be used if you need the out-and-out performance or if you're dealing with other, older Unicies.

> Antivirus? Is there a centrally managed AV server like symantec?For?  Linux doesn't have a lot of viruses, and the majority of the AV solutions are really intended for scanning Windows files, not anything else.

> How about printer management? Does NFS do that or do I go with SAMBA tied to LDAP server?You use CUPS, generally.

Being more specific about what/why you're trying to do here would be helpful.

---

### Post by ztrek7 on 2005-10-02
Good stuff guys. 

You (LordHunter) suggest keeping active directory. Do most organizations do this, and just use *nix boxes for particular, specific purpose servers (SQL, File Server, Print Server, etc) and not use them for authentication and leave that to windows? We have like 25 servers, 1 scounix, and one red hat 7. One uses old, old, old program for a particular office, and the other is for panic alarm system. The rest of the servers, windows controls.

My purpose for this is to increase my knowledge of linux on the server side. I feel like I have learned a GREAT deal on the personal side, (still learning, not the linux guru yet:) and want to know the server stuff as well. I am the type to learn by doing, so, I have the equipment, and was going to set up a miniture network, test some of our applications to see if they work, how the IT management would  be, how the user experience would be, and to see if it would be a viable option to replace some OS's on some servers and clients. 

I dont forsee replacing them all, but, if I can knock off 100 - 200 clients, a couple servers, it would be a nice tick on my accomplishments list.

I should probably start another thread for this, but, do you have to have a windows cal for a linux box if it just uses it for authentication? 

Anyone know of some sort of spreadsheet for TCO savings from switching to linux?
thanks,

jeremy

---

### Post by LordHunter317 on 2005-10-03
[QUOTE=ztrek7]You (LordHunter) suggest keeping active directory. Do most organizations do this, and just use *nix boxes for particular, specific purpose servers (SQL, File Server, Print Server, etc) and not use them for authentication and leave that to windows?[/quote]Unless they're a pure UNIX shop, yes.  Active Directory is a must if you have Windows clients, because of all the features it provides you.  Also, it's administration tools are superior to pretty much any other directory solution, UNIX or otherwise.

> I should probably start another thread for this, but, do you have to have a windows cal for a linux box if it just uses it for authentication?If you're doing per-device CAL, I believe yes.  I'm not an expert on all of the licensing details for Windows however, so you may want to talk to someone with more experience.

---

