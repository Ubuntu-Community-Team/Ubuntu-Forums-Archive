---
title: "Ubuntu Server vs Windows SBS 2003 - Help Me Get Back To Ubuntu"
date: 2009-12-18
forum: Server Platforms
---

### Post by AlexanderDGreat on 2009-12-18
Hi, after trying Ubuntu Desktop for 5 months. Plus, another 3 months using Ubuntu Server. I've switched back to Windows Small Business Server 2003.

Here's my story. We have a small construction firm and no IT staff with 20 computers (Windows XP & Ubuntu JJ) & 1 Server. We bought a wonderful package for small businesses, Windows Small Business Server (SBS) 2003. I set it up and it was great. Namely: Active Directory, File Services, Print Services, Domain Group Policies were so user-friendly, all in 1 GUI. Except ISA Server, which I didn't know how to configure.

My frustration came when the server was attacked by a virus because I inserted a USB device, my mind was flying at that moment. Then AD users were not authenticated, group policies were erased, printers crashed, usual horrible stuff.

Now, I tried Ubuntu Server. I studied about basic SAMBA, LTSP, NFS, FTP, Squid, and other necessary tools to "COPY" our previous environment. It worked great until I forgot one thing, 

--How do you pass Group Policies to computers and users?
--How do users authenticate, Active Directory style?
--How do you pass Group Policies for domain Users & Computers? (for example, 1 wallpaper for all, disabled Control Panel, Admin account, etc...)

Can you help me how to do these in Ubuntu Server if I do all computers 100% Ubuntu clients?

PS Our office does basic computing: typing, restricted Internet browsing, file, print sharing, firewall, burning dvds for presentations, instant messangers, making invoices, and watching shared videos.

PPS I've given up LTSP because of speed & performance, and of my Atom thin clients.

---

### Post by craigp84 on 2009-12-18
Hi AlexanderDGreat,

It sounds like you'd be more comfortable in SBS 2003, it probably makes more sense, in your situation, to go that route?

Just try to be careful with viruses, worms, trojans and stuff like that though because they're very common and often noone knows they are even installed while in the background they are using your computer resources for bad (often illegal) tasks.

> 
--How do you pass Group Policies to computers and users?


I think you pretty much have to use local group policies, look this up with Microsoft.

> 
--How do users authenticate, Active Directory style?


Google this one, there are too many step by step guides to repeat here.

> 
--How do you pass Group Policies for domain Users & Computers? (for example, 1 wallpaper for all, disabled Control Panel, Admin account, etc...)


Local group policies instead of domain group policies. If you ask me, local policies mean losing the #1 benefit of group policy -- the fact i can apply it to groups / classes of users & machines very easily. Maybe windows server would be best if you want to use group policies?

> if I do all computers 100% Ubuntu clients?

[http://www.canonical.com/projects/landscape](http://www.canonical.com/projects/landscape)

Cheers,

-c

---

### Post by cdenley on 2009-12-18
Linux does not have Active Directory functionality for Windows clients. You can't expect Linux do be a drop-in replacement for a Windows server in a Windows environment. They have been implementing AD features into the next version of samba, but it has been in development for a long time.
[http://wiki.samba.org/index.php/Samba4](http://wiki.samba.org/index.php/Samba4)

---

### Post by AlexanderDGreat on 2009-12-18
Hi @craigp84 - Thanks for reading my thread.

@cdenley - Thanks also.

So it means, there will be no AD and GPO for a 100% ALL Ubuntu Environment? I love Ubuntu and FOSS so much I just couldn't let them go.

I'm thinking of dumping our 20 Windows XP machines and replace them with 20 Ubuntu machines & 1 Ubuntu Server and to copy the "Windows SBS 2003 production environment".

PS So the GPO is the deal-breaker? :(

---

### Post by cdenley on 2009-12-18
> **AlexanderDGreat said:**
> 
So it means, there will be no AD and GPO for a 100% ALL Ubuntu Environment? I love Ubuntu and FOSS so much I just couldn't let them go.


As craigp84 suggested, for maintaining clients in a 100% ubuntu environment, look at lanscape. I never tried it before, but I believe it provides similar functionality to active directory and group policies except with an ubuntu environment.

---

### Post by lykwydchykyn on 2009-12-18
> **AlexanderDGreat said:**
> Hi @craigp84 - Thanks for reading my thread.

@cdenley - Thanks also.

So it means, there will be no AD and GPO for a 100% ALL Ubuntu Environment? I love Ubuntu and FOSS so much I just couldn't let them go.

I'm thinking of dumping our 20 Windows XP machines and replace them with 20 Ubuntu machines & 1 Ubuntu Server and to copy the "Windows SBS 2003 production environment".

PS So the GPO is the deal-breaker? :(

It's been a while since I researched this, but I seem to remember reading in the Samba guide that some limited support for policies was possible if you create policy objects with the local policy editor.  Can't remember, I may be talking crazy.

I think it's important though to stop and remember that things like AD and GPO are just tools, and the better question is what you accomplish with those tools and if it can be accomplished another way.  What do you do with GPOs?  What all does your AD encompass?  Just logins, or email as well?  How tightly controlled is your network?

If you really want to get away from Windows but have an out-of-the-box directory/policy solution, there's also Novell eDirectory with ZenWorks.  It runs on most major operating systems, and covers a lot of the same functionality. It's not free, open-source, or even cheaper, but we use at my work to manage around 700-800 users over a county-wide WAN.  It's probably overkill for 20 machines, though.

---

### Post by AlexanderDGreat on 2009-12-18
> I think it's important though to stop and remember that things like AD and GPO are just tools, and the better question is what you accomplish with those tools and if it can be accomplished another way. What do you do with GPOs? What all does your AD encompass? Just logins, or email as well? How tightly controlled is your network?

Thanks for this.

I guess I'll just have to research on my own what really "works" for our environment. I was just thinking if there was an easier, integrated way of working with Ubuntu in a SOHO environment with 20 computers.

---

### Post by lykwydchykyn on 2009-12-19
> **AlexanderDGreat said:**
> Thanks for this.

I guess I'll just have to research on my own what really "works" for our environment. I was just thinking if there was an easier, integrated way of working with Ubuntu in a SOHO environment with 20 computers.

I asked some Debian admins once what sorts of tools are used for large deployments, and the consensus seemed to be that large Linux deployments are often done with thin clients -- something like you can do with LTSP.

That said, I think the tools are out there to do a 'fat client' network, but I haven't seen anything as straightforward or integrated as AD.  There are lots of LDAP solutions for centralized login, and many services can authenticate against LDAP.  I believe there is a policy tool for GNOME, not sure if profiles can be enforced via LDAP or SAMBA or some such.

Hope that gives you some places to look.

---

### Post by AlexanderDGreat on 2009-12-19
@lykwydchykyn - I've tried LTSP, but it was too slow for my standards. I evaluated the documentation if I can reach it for my level, I liked it, and deployed it to 10 computers as a test.

But overtime, it got too difficult that I'm beginning to do things, way out of my league, I guess it's the price you pay for Ubuntu being "free". I got scared, backed off while it was early, we don't have an IT. The policy editor for GNOME is the gconf-editor, right?

Thanks for understanding my situation. So I think my final solution for our basic SOHO (copy MS SBS 2003) would be:

Set up 1 Server (32bit) Intel C2D e7400, 4 gb RAM for basic SAMBA, CUPS, FTP, SQUID, SSH, APT-CACHE or APT-PROXY (I'm currently researching on this), Just Add Users For Authentication of file sharing, (not LDAP - too hard for me), Free VMServer (in case my clients need to use a Windows XP machine) they will do it via the localhost:8222, setup a UFW (will still learn firewalls), various cron jobs for system maintenance, LAMP (for internal website),

Set up 20 computers all Intel Atom 330, 2gb RAM (Ubuntu OS), 80gb HD, no DVDroms: will disable USB Mounting (via GCONF-EDITOR, if possible?), Set Up Proxy Server to restrict web browsing to certain sites, setup An Admin/Root Account to be used by me, and their user accounts will be their names, Use Mozilla Thunderbird (for email), OpenOffice, GIMP, Instant Messaging via Pidgin or the new one in Karmic, use Server VMServer WinXP via Firefox (for IE our supplier's website is only compatible with IE), uninstall Torrent Programs, whew...

Can you pls. comment on our environment, if I've missed anything important, or if you can recommend something useful, Appreciate a lot your help a lot Open-Source-Friends. :)

---

### Post by lykwydchykyn on 2009-12-19
If you want to save some work doing all this on 20 workstations, here are a few options:

 - cfengine or puppet -- these are systems for controlling many systems at once.  Honestly, though, I never got my head around using either, so it may be too complicated.  But you can do about anything sysadmin-wise with this.

 - webmin -- also allows you to do pretty much any kind of sysadmin task through a web interface, and features a "cluster" feature which is really easy to use, so you can do mass uninstall/install, system tweaks, updates, etc.

 - G4L -- great disk-imaging program, if you want to go that route.

 - netboot installer -- this takes a little reading up on, but if you get a PXE server up and running the  netboot installer and combine that with an apt-mirror, you can install systems in no time flat.  You can use a pre-seed file to create an installation template.  

Also, don't forget that one of Linux's advantages is modularity.  A lot of the "lock down" features you get through group policy or other third-party security software on Windows is obviated on Linux by the fact that you can just rip out a part of the software stack and replace it with something less functional.

I don't know if the software I mentioned is over your head or not, but it's worth looking into.  And never forget, once you learn how to set something up with free software, you've freed yourself from paying for that functionality ever again.  This isn't just saving you one SBS license, it's saving you a lifetime of server licenses.

EDIT: oh yeah, you might want to look into running IE in wine, if you only need XP to access a single website.  Much more efficient and doesn't require maintaining a virtual XP install.

---

### Post by kewlrichie on 2009-12-19
You can sort of do this but it's going to i lnvolved some manual work. Samba3 can be a NT style PDC and you can do GP manually checkout this link [http://www.opensourcehowto.org/how-to/samba/samba-primary-domain-controller-with-group-policies.html]("http://www.opensourcehowto.org/how-to/samba/samba-primary-domain-controller-with-group-policies.html") 
there is samba4 that's not fully done from what I remember but there are guides check the samba wiki for a universal guide and google "samba4 active directory ubuntu" and you get page with a guide also check it out.

---

### Post by AlexanderDGreat on 2009-12-20
@lykwydchykyn - wow, those are ALL great links! You're right, once I study them, they're a lifetime investment and savings, thank you for keeping my hopes up.

@kewlrichie - thanks for the link as well.

---

### Post by headvampyre@hotmail.co.uk on 2010-08-17
okay, i have another idea. if you really want to use active directory with ubuntu, it is possible with likewise-open. you can authenticate via active directory, be it a windows dc or a samba4 dc, heres a link to the packages in ubuntus repos (lucid) [http://packages.ubuntu.com/search?keywords=likewise-open&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=likewise-open&searchon=names&suite=lucid&section=all) try it, im not sure if it supports poicies as im currently running samba4 in a windows network but am planning on deploying ubuntu.

---

### Post by beetlejuice321 on 2010-08-17
I believe that Linux has a ways to go with providing tools to small businesses (even large businesses).  As you mention its not like small businesses have IT departments to customize these systems for them.  And large organizations do not want to spend a lot of money managing shares, users/groups, printing, and authentication.  That's also why they choose Active Directory, just because its simple and that makes sense.

I also support small businesses and would love nothing more then to be able to provide my clients with a Linux server that could do simple things for them.  I can set up the server, but wouldn't it be nice if they can manage the simple tasks themselves?  They can do this with Microsoft, but not with Linux.

Here is an example:

[LIST]
[*]Use LAMP for Website (Internet/Intranet).
[*]Use Samba to create a file shares.
[*]Use LDAP for authenticating of user, but also other applications can authenticate against this Linux server running LDAP.  (NOTE: LDAP is optional for a small business).
[*]Project and Communication Tools such as Zimbra or OSS Groupware services.
[/LIST]

Note: Most small businesses use hosted Email Management solutions now days like Zimbra (open source), Google Apps, Exchange Hosted services for Email/Calendar/Document collaboration. So most likely a small business server will not need email support.

Some tools I have found so fare are these Linux Distro's which specialize in providing an out of the box Small Business Distro.

**SME Server**
[http://wiki.contribs.org/Main_Page](http://wiki.contribs.org/Main_Page)

**EBox Server (Based on Ubuntu)**
[http://www.ebox-platform.com/](http://www.ebox-platform.com/)

These appear to be steps in the right direction, but I still find that its difficult for users to manage their server.  For example managing shares can be cumbersome compared to Active Directory and ACL.  Users cannot simply "Right-Click" on a share and view the security properties to see who has access and change access to shares (assuming they have this access).  This is one of my main frustrations with working with Linux (and Samba by extension) as a viable business file server option!  

Now if there were simple alternatives to changing file permissions I would be open to them...but I have heard of none yet.

---

### Post by SteveHillier on 2010-08-31
> **lykwydchykyn said:**
> I think it's important though to stop and remember that things like AD and GPO are just tools, and the better question is what you accomplish with those tools and if it can be accomplished another way.  What do you do with GPOs?  What all does your AD encompass?  Just logins, or email as well?  How tightly controlled is your network?


Just making this comment on the way through.  
I have always thought of MS GPO and LPO sytems in this very simple way.  The policies act on the Windows registry by changing the values associated with certain keys and thus via GPOs you can give the registry keys certain values depending on which group that users is associated with.  
You just have to remember the precedence order of policy objects (which is not the most simple) to understand what is the resultant set of effective policies.  It is this aspect which cause administrators the greatest headaches when you change a setting that seems to have no effect.
Understanding the POs work on the Windows registry changing configuration settings makes it easy to see the complexity required when you want to manipulate Linux configuration files in a simlar way.

---

### Post by y@w on 2010-09-01
+1 on Ebox.

---

