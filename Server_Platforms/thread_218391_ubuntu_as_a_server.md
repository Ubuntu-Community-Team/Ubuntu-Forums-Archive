---
title: "ubuntu as a server"
date: 2006-07-18
forum: Server Platforms
---

### Post by MaximB on 2006-07-18
hello !
I'm learning MSCE (don't like MS - it's just for work !)
and I want to know more about how ubuntu server works
1.is there an active directory ?
2.is there a group policy ?
3.is there delegation of control ?
4.what about more premmision options ?
5.how does it work as a domain controler ?
6.how it integrates with win2003 server ?
7.is there a GUI for every/most of the terminal commands ?
8.more stuff you cal tell me ?

I would be glad to see real answers and not **just** links
thanks ahead !!!

---

### Post by inthewayboy on 2006-07-18
1.is there an active directory ?

Active Directory is based off of LDAP, which is supported in several OS's. OpenLDAP is the most popular one I've heard of, but I have no experience with it personally.

2.is there a group policy ?

Depends...are you wanting to use the GPO on a Windows client or a linux client. Almost all GPO's boil down to registry settings, so while there is no built-in GPO function in linux, you could get the same results be constructing scripts to edit the clients registry. If you are looking for something to use on a linux client then I have no idea.

3.is there delegation of control ?

Got me there

4.what about more premmision options ?

Permission options maybe? NTFS has several unique but similar security options in regards to the file system. cygwin for instance can somewhat translate a unix file permission into an NTFS file permission so it should be possible at some level.

5.how does it work as a domain controler ?

Never done it myself but I hear you can do this with SAMBA, which is like the opensource equivalent to Microsoft "File and Print Sharing". If you configure it right you can have it be similar in features to an NT4 domain. But since there is no built-in support for Active Directory I don't think you can build a full domain without some form of Active Directory support coming from a Windows Server.

6.how it integrates with win2003 server ?

Agian, never used it but there is a component in Windows Server for unix compatibilty that should help with this. It doesn't mean everything works but it does help get through some of the bigger issues.

7.is there a GUI for every/most of the terminal commands ?

Don't know, but from what I do know you should really get comfortable with the terminal commands. More so than windows you will be operating from a terminal in most cases, and in some cases that may be your only option.

8.more stuff you cal tell me ?

Get some form of virtual machine technology (VMWare Server is great and free!) and setup a 2K3 server and an ubuntu server. Then play...and destroy, and rebuild...best way to learn in my opinion. Then you can actually see what is involved without holding two or more machines hostage.

Good luck!

---

### Post by oly on 2006-07-18
you need to look into ldap samba and wpkg you can actually deploy software and edit registry entries and various other things with wpkg.

[http://www.digitaloctave.com/files/server/PDC-Server1.0.tar.gz](http://www.digitaloctave.com/files/server/PDC-Server1.0.tar.gz)

will hopefully setup a samba PDC with openldap for you and wpkg is quite easy to figure out.

that should get you started i am actually using this setup for a 250 machine network.

---

### Post by fdamstra on 2006-07-18
> **MAXDDARK said:**
> hello !
I'm learning MSCE (don't like MS - it's just for work !)
and I want to know more about how ubuntu server works
It sounds like you want to use Ubuntu as a Domain Controller.  IMO, you'd be better off using Windows for a DC.  Yes, you can do it with Linux/Samba/LDAP, but if that's all you're after, it's the wrong tool for the job.

> 
1.is there an active directory ?
2.is there a group policy ?
These are Microsoft concepts.  There is software that will integrate Linux with AD, and even push policies to Windows clients, but that's not really what's meant by a "Linux Server".

> 4.what about more premmision options ?
The permissions generally aren't as granular as in a Windows domain.  In most common linux systems, you'll be limited by user and group permissions on files and programs.  (Though, there are a variety of projects that make Linux permissions far more granular, they just aren't common (yet?))

> 5.how does it work as a domain controler ?
6.how it integrates with win2003 server ?
From what I hear, it integrates acceptably well.  I've never done it myself, and don't see the purpose.  What you'll save in licensing costs, you'll easily use up in administrator time and training.  If all you want is a Windows Domain Controller, then use Windows.

If, instead, you're looking for a web server, dhcp server, firewall, email server, ... the list goes on.  In those areas, I think linux beats the pants off Windows.

> 7.is there a GUI for every/most of the terminal commands ?
In general, Linux/UNIX admins don't put GUI's on their servers.  It's needless overhead.  It eats up system resources, increases patch time, potentially increases security vulnerabilities, and introduces unneeded complexity into your server.

That said, GUI tools do exist to do most everything, if you should choose that route.  Also, some admins really like [webmin]("http://www.webmin.com/"), which provides nearly full control all through an easy to use web interface.  Personally, the security implications of giving that much power to a web application bother me.  But it's very popular, very powerful, and very easy to use.

> I would be glad to see real answers and not **just** links thanks ahead !!!
What are your goals?  Having a goal in mind will make learning Linux a lot more pleasant.  Otherwise, you install a system and think, "What do I do now?"  Installing linux is not a task in itself.  Do you want to make a webpage?  Do you want to make a streaming audio server?  Do you want to learn to program?

---

### Post by MaximB on 2006-07-19
thanks for the replys...
honestly - I expected from linux to be more then what you told me
"can't be a good DC" , "no delegation" , "no GPO" and the list goes on..
yes I know all of thouse things are MS things but it really makes life easier and you got more options.

I don't want to make a domain at the moment
I just learning MCSE that all
and I heard only good about linux servers so I had to ask thouse questions.

---

