---
title: "Using Ubuntu or Opensoure alternative to Windows/Active Directory"
date: 2006-04-27
forum: Server Platforms
---

### Post by big-hed on 2006-04-27
Hi i have a network setup currently using Windows Server for Directory Services for approx 5 XP clients.  

As some of you may already know im fed up using and dealing with Windows problems so im considering a complete move to opensource or unix/linux. Its not a massive scale project so bear in mind i wanna keep costs to a minimum.  

To do this i want to move the server first. Basically its currently used for directory services, Access Database Server (which im trying at present to move to a complete mysql solution), file server, print server and central backup point. 

the thing  i wanna ask you guys is! Can i use ubuntu for this or what other system can i use to do this. i should have said i would still like to keep the Windows XP clients for the time being until i have more time to train them to use linux first.

Also can Access still be used on Ubuntu or linux someway that my clients can still use Access while i finish the MySQL crossover????

Please help guys as i hate WINDOWS!

---

### Post by mjm115 on 2006-04-27
Sure, you can use ubuntu to set up a server.  [Here]("http://www.howtoforge.com/samba_setup_ubuntu_5.10") is a nice tutorial that can show you how to set it up with Ubuntu.  If you browse through the site, it will show you how to set up DNS, FTP, Mail, etc.

I hope this helps.

---

### Post by LordHunter317 on 2006-04-27
Tbe short answer:  Nothing can really replace AD, or has feature-parity with it.  You'll need to keep a Windows Server around for that.  Some stuff can be offloaded (DNS, DHCP) if you really want it to be.

>  Access Database Server (which im trying at present to move to a complete mysql solution),There is no such thing as an Access Database Server, Access just uses files.  You can't do this.  Access and MySQL are not equivalent programs.

You had better do some more research on your current platform because it's clear you lack the understanding about it to recommend a migration to anything.

---

### Post by behemot on 2006-04-27
big-hed,
I presume that you are in charge of administering small network that consits of a   Windows server and 5 XP workstations.  I understand that the MS Active Directory is already deplyed and all workstations are members of the domain.

In order to rip some benefits from AD you should run it on larger network. For small network like yours AD is just in my humble opinion a big pain in the neck.
Also, without functional backup dommain controller, your users may lose access to their profiles if your primary server ever goes down.

I think that Samba and Fedora Directory Server would answer your needs, but migration process may be a little taxing.  It is certainly not as easy as runnig the AD wizard, so be ready for few bumps in the road.

Please list all the features from AD that you need and I will try to point you to resources and howto's.

---

### Post by sgla1 on 2006-04-27
[QUOTE=LordHunter317]
There is no such thing as an Access Database Server, Access just uses files.  You can't do this.  Access and MySQL are not equivalent programs.
[/QUOTE]

I know that Micro$oft bashing is a popular sport around here, but in re. access you are mistaken.  Access is a true relational database.  It has native support for foreign keys, which mySQL does not unless you specify the InnoDB engine.  Because of its graphic schema builder, access is used in many shops for rapid application development.  The sql is then ported over to mySQL for production.

The problem with access is that it scales poorly, but in a shop with 5 users it might be adequate.

In order to move Linux into the workplace, it's important that we tell the truth and check our facts carefully.

---

### Post by LordHunter317 on 2006-04-27
[QUOTE=sgla1]I know that Micro$oft bashing is a popular sport around here, but in re. access you are mistaken.[/quote]No, I'm not.  Link me to a page on microsoft.com about 'Access Database Server'.  No such thing exists.  Access stores all it's data in ***a single file.***

>   Access is a true relational database.That's questionable  It's support for joins is completely unacceptably poor.  But how is this relevant?  I never said it wasn't.

> It has native support for foreign keys, which mySQL does not unless you specify the InnoDB engine. Referential Integrity in Access is optional and can be toggled off whenever one desires.  But again, how is this relevant?

> The problem with access is that it scales poorly, but in a shop with 5 users it might be adequate.No, Access has way more problems than just that.

> In order to move Linux into the workplace, it's important that we tell the truth and check our facts carefully.Which you've totally failed to do, whilst demonstrating a failure to read as well.

I'm the only MS apologist (god I hate saying that) in this thread.

---

### Post by Iowan on 2006-04-27
[QUOTE=sgla1]  Because of its graphic schema builder, access is used in many shops for rapid application development.  The sql is then ported over to mySQL for production.[/QUOTE]In our plant, Access is used for development, but for large, multiuser projects, it gets converted to MS SQLServer (or whatever the name is - it's NOT mySQL).

---

### Post by big-hed on 2006-04-28
Ok guys! I have made a mistake in saying 'Access Database Server' but no point fighting about it.  Id appreciate your help more than arguing over this.

Basically i mean a windows server which runs MS Access as a backend with Access on the clients connecting to it.

Do any of you know can i run Xen on ubuntu and install windows as a virtual server, would this still allow me to run my clients for a while until changing over to linux completely?? 

Dont get me wrong in that i do use windows quite a lot and it has some really good features but now that ive used linux for a while i feel it is much more reliable and cost effective for our purpose.

---

### Post by LordHunter317 on 2006-04-28
[QUOTE=big-hed]Basically i mean a windows server which runs MS Access as a backend with Access on the clients connecting to it.[/quote]No, you're still not understanding.  ***No such thing exists.***  Access runs entirely on the machine running it.   The most you can do is put the file on a fileshare.  That's all the serving you can do with Access: server its files.  The DB is completely handled on the machine(s) running Access.

> Do any of you know can i run Xen on ubuntu and install windows as a virtual server, would this still allow me to run my clients for a while until changing over to linux completely?? You could, or VMWare server.

> Dont get me wrong in that i do use windows quite a lot and it has some really good features but now that ive used linux for a while i feel it is much more reliable and cost effective for our purpose.I'm honsetly not convinced that's the case.

---

### Post by behemot on 2006-04-28
[QUOTE=LordHunter317]
I'm honsetly not convinced that's the case.[/QUOTE]

LordHunter317,
Are you not convinced that:

A: He is using Windows quite a lot
B: Windows has some realy good features
C: He's been using linux for a while now
D: Linux is more reliable and cost effective
E: All of the above

I am convinced that he has now all his Access files and his backup on this server.  Think about those poor five XP users before you plant any xen or vmware ideas in big-hed.

And I admire your knowledge and your input to this community.

---

### Post by LordHunter317 on 2006-04-30
[QUOTE=behemot]LordHunter317,
Are you not convinced that:

A: He is using Windows quite a lot
B: Windows has some realy good features
C: He's been using linux for a while now
D: Linux is more reliable and cost effective
E: All of the above[/quote]D, for what Active Directory provides.

My real concern is I think he doesn't clearly understand what it is providing him and what features he's using of it, and what his server is really being used for.  And you can't plan a migration to any platform without knowing exactly what you're doing now.

---

### Post by Fatjoint on 2006-05-01
> 
My real concern is I think he doesn't clearly understand what it is providing him and what features he's using of it, and what his server is really being used for. And you can't plan a migration to any platform without knowing exactly what you're doing now.


I'd have to agree with you on this, and I believe that you're trying to get the point across to the OP that he needs to break down what he is doing to effectively make a battle plan for migration.

OP, please spec out exactly what services that your server is providing in detail.  I think it will be much easier to suggest a plan moving forward from that.

---

### Post by big-hed on 2006-05-02
Well, if you want me to be more definitive as to services the current Windows Server provides are:

1. Active Directory Services - storing user details/logon scripts etc
2. File Server - the main priority is a central Microsoft Access Database that users access to add/edit records all day.
3. Print Server
4. DNS
5. DHCP
6. Remote Services

I know this can all be done using Ubuntu so why are you guys (Lordhunter etc) so negative about going this route???

---

### Post by behemot on 2006-05-02
big-hed,
Now, since you listed all the requirements...

There are many ways to meet your needs.
This is one possible order of things.
I would work through your list bottom-up.

You need DHCP, name resolution and remote access to your network.
There are special Linux distributions designed just to do that.  My preferred one is ipcop  [www.ipcop.org](www.ipcop.org)

It takes old PC and about 30 min to setup.
It would be a great firewall and DHCP server.  
Accrding to ipcop devs, (who are experts), running DNS on the firewall is not recomended.  You do not realy need to run DNS server on your network.  All you need is DNS proxy and UI to modify host file on your IPCop.  All this is included in this distro.

For remote access you could have a look at ipcop addon section.  There is a openvpn addon available.  It works as a charm and it is no-brainer to setup the windows client. You just need to follow documentation.

Now you need print and win-dos file server.
Both components (cups and samba) are in repos.
There is a great tutorial available:
[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

It should take very little time to put all this together.
It can be done!  Just don't blame people who wanted to help you.
If your first post resembled the last people would come up with many great options and suggestions.

---

### Post by big-hed on 2006-05-02
behemot and everyone else, i do appreciate your help and thanks for it but its not really a good start for a linux newbie. I fully admit maybe i didnt put it all into appropriate words but id like to think you guys are more positive than saying i dont entirely know what im doing.  Well forget the probs now lets move onto better things! and i'll be glad to have you help me in future..

---

### Post by LordHunter317 on 2006-05-02
[QUOTE=big-hed]Well, if you want me to be more definitive as to services the current Windows Server provides are:

1. Active Directory Services - storing user details/logon scripts etc[/quote]Is that all you're using it for?  Do you use GPOs at all?  What about software deployment?  You need to be more specific and make sure you're 110% certain about exactly everything you're using AD for.

> I know this can all be done using Ubuntu so why are you guys (Lordhunter etc) so negative about going this route???Because it actually can't, as I said originally.  You cannot get feature-parity with Active Directory unless you move to a full Novell solution: NDS and Zenworks.  Not free, either.

> I fully admit maybe i didnt put it all into appropriate words but id like to think you guys are more positive than saying i dont entirely know what im doing.Suggesting that you're going to replace Access with MySQL (you cannot) make it hard to believe otherwise.  It's also still not clear you've fully taken stock of what you're using your current tools for.  I say this because it's relatively easy in Active Directory to use things you don't realize you're using, especially if you deploy or have made changes in an ad-hoc manner.

My real concern is that you haven't told us everything you're really using this machine for, thus you cannot plan a migration.  My guess is that you actually cannot migrate, because most people in this situation cannot.  They're using features that have no equivalents on the Linux solutions right now.

[quote=behemot]Accrding to ipcop devs, (who are experts), running DNS on the firewall is not recomended. You do not realy need to run DNS server on your network. All you need is DNS proxy and UI to modify host file on your IPCop. All this is included in this distro.[/quote]You have to run a DNS server though if you want sane name resolution for Windows filesharing.  WINS isn't attractive, neither is using broadcast resolution especially.

---

### Post by behemot on 2006-05-02
[QUOTE=big-hed] i do appreciate your help and thanks for it but its not really a good start for a linux newbie. .[/QUOTE]

Now we are talking

[http://www.ubuntuforums.org/forumdisplay.php?f=73](http://www.ubuntuforums.org/forumdisplay.php?f=73)

---

### Post by LordHunter317 on 2006-05-02
Linking him there is senseless.  The proper place for his problem is here.  He'll get proper, detailed help (I've done this several times before, and can post examples) as soon as we can identify he can actually make the transition.

---

### Post by behemot on 2006-05-02
[QUOTE=LordHunter317]

You have to run a DNS server though if you want sane name resolution for Windows filesharing.  WINS isn't attractive, neither is using broadcast resolution especially.[/QUOTE]

I would not bother with DNS server for such a tiny network, but it is my just my personal opinion.

;)

---

### Post by nobu on 2006-05-08
I asked myself this very same question.  Is their anything out there in the Linux world that can basically do what Windows Active Directory Network can do.  And I came up with sort of an answer.

To replace Active Directory use Fedora Directory Server....not the best and not an all in one solution but will get the job done.  You will get a single sign on and you can also have Windows Machines login to the Directory Server as well.  Short comings, you have no group policy and as open source projects goes this one is not well developed at the moment....But it is MultiMaster and it is much easier to work with compared to OpenLDAP.

Okay now if you want something like group policy I would recommend to use an all KDE environment.  You can use a tool call the Kiosk Admin Tool which basically lets you set Desktop Policy depending on user or group.  It is not as sophisticated as AD Group Policy but it does provide a lockdown policy for any specific computer that is on your network on a KDE environment.

And as a workstation I would recommend using SUSE.  Their LDAP Client is the easiest to use and they have tried to make the transition for Windows users as easy as possible.

For email server use Citadel Email Server.  You can find out about it at citadel.org.  Of all the email server that are open source this one is not the best....but it sure is the easiest to set up.  It took me less than 30 minutes to get it working.  And as an email client I would suggest Kontact.  You not only get email, you also get a calendar, todo list, contact, Journal, News feeds...all in one package.

These are the basic elements that you can use to change to an all linux open source network.  The hardest out of all these is probably setting up Fedora Directory Server.  Then is basically trying to find out how all these pieces work together....This is not Microsoft Plug and Play.

Now to come back to the questions of how ubuntu relates to this.....well for me not much....I haven't quite found an easy ldap client for Ubuntu.....however their is a howto at the Fedora Directory Server site on how to install FDS on ubuntu.  The greatest thing about Ubuntu is its ease of installation and of Updating your system.  Something that the other distros lack unless your willing to pay for.

---

