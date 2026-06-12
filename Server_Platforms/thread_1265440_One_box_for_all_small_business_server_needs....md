---
title: "One box for all small business server needs..."
date: 2009-09-13
forum: Server Platforms
---

### Post by Vladimir_BG on 2009-09-13
Hello everyone.

By education and personal preference, I'm an economist. Recently, by chance I became an admin for MS based servers and workstations.

As I'm in Serbia, most companies are small to medium size, and WILL NOT pay for more than one box for the job. And it has to do everything.

Be a gateway, firewall, router, DNS, DHCP, file server, web server, mail server, active directory(don't exatly know the open source alternative but something that allows centalized administration) and sometime even a news server...

Amount of users per company goes from 4-5 to 70-80.

So far, I've been deploying Windows small business server 2003 or Server 2003 r2 standard with tweeks for bigger companies.

The cost of software plus the cost of CALs is sometimes very prohibitive, and I belive that Linux based solution will be more stable. 

I've played around with SME server, but would like something that offers costumizations for users and machines trough rules and policies like active directory allows.

So, in the end, I tought about making a "standardized" deployment based on ubuntu server(8.04 LTS) in a virtual machine, using paravitualization to minimize performance penalties and deploy it on client hardware.

What are you oppinions on the idea?

Now, I have little experience with Linux. How easy is it to set up and administer the described server?

What's the bay way of setting up all these server roles?

Thanks for you time and effort for help on this subject.

---

### Post by tlarkin on 2009-09-14
Well a few options here....

You can look at Enterprise Linux, Like RedHat or SuSe, while not free they are a lot cheaper than Windows.  SuSe got bought out by Novell a few years back and they integrated eDirectory into Linux.

Of course, there is Unix and Free BSD and the Berkley database which supports LDAP.

Apple, releases Darwin, their open source version of OS X which is built off of Unix and free, and runs Open Directory which allows for some directory services.

As for every other service mentioned (DHCP, DNS, Firewall, etc) this can be accomplished by several other ways to save money.  You can convert a desktop into a smooth wall router, which will give you lots of security services, and any server you set up can run everything else.

Really, your main restrictions will be not on the server side, but on the client management side.  Linux servers can't managed Windows clients, so it really depends on what you want to do.   Well, except Novell SuSe Linux I think can actually manage Windows clients but that is something you would have to look into.

---

### Post by windependence on 2009-09-14
This can be done in one box using virtualization, what I call a "datacenter in a box", but I think you would need far more expertise than you have currently, and you need to understand that Linux servers are administered from the command line as a general rule. Ubuntu Server does not even come with a GUI installed and Canonical does not recommend it. I am not saying it's hard, just a large learning curve for average person new to Linux/Unix. You would also need a good amount of RAM in the box to run everything including the host machine.

-Tim

---

### Post by scorp123 on 2009-09-14
> **Vladimir_BG said:**
>  Be a gateway, firewall, router, DNS, DHCP, file server, web server, mail server, active directory(don't exatly know the open source alternative but something that allows centalized administration) and sometime even a news server... Since you're a beginner (no offence intended here .... i izvinjavam se u napred ;) ) I think you might find OpenSUSE 11.1 very easy.

You can get it from here for free:
[http://software.opensuse.org/](http://software.opensuse.org/)

I don't know too much about Serbia but I suppose getting stuff via Internet is not a big deal anymore? Even in the most rural corners of Bosnia we have ADSL now, even for a flat rate. So I suppose getting tons of updates and what not is not an issue?

So in that case you could go for the OpenSUSE CD-release.

On the other hand I personally always prefer to get the OpenSUSE DVD-release. That DVD simply has everything and this might be an advantage if getting on-line is a problem.

So why do I recommend OpenSUSE over Ubuntu ... Frankly, because I think that as a server OS that is supposed to do "a little bit of everything" OpenSUSE makes a better job at being "beginner-friendly". Last but not least because of SUSE's one-stop setup and config program "***yast***".

Screenshot:
[IMG]http://files.opensuse.org/opensuse/en/thumb/9/93/Gtk-yast.jpg/600px-Gtk-yast.jpg[/IMG]

"***yast***" will easily allow you to setup all the things you mentioned in your posting. It's very easy and it's almost always "point and click". So the *"culture shock"* that you will definietly run into if you're only used to Windows will remain rather limited, so you should not find it too hard to use this.

Doing all those things on Ubuntu is of course possible too. And frankly Ubuntu offers the far wider selection of packages, alternatives and possibilities and what not ... But: For someone who is only used to Windows this will be too hard to handle, I think.

Hence my recommendation ... Start with OpenSUSE ... And when you get fed up with it and tired of its hand-holding, you will be ready to move on to something else.

Last but not least, maybe you should take this Linux quiz:
[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

The quiz will recommend a Linux distribution for you based on your answers. I suggest you then download this distribution and install it somewhere (e.g. a laptop or a desktop PC?) and try to use it exclusively. **Using Linux is the best way to learn it.** And that will also make it easier for you to administrate Linux servers.

---

### Post by tlarkin on 2009-09-14
I don't think any open source free Linux distros support robust directory services, and if the OP needs client management they will have to go with a Windows box to manage them.  Linux servers can't give windows boxes group policy.

---

### Post by abaden on 2009-09-14
What are you using Active Directory for? If you're just using it as a way to store/share files, then you could run a samba server instead. But if you're using it to deliver applications and manage user accounts, then you're probably stuck with it, at least for now. 


Alex

---

### Post by windependence on 2009-09-14
> **tlarkin said:**
> I don't think any open source free Linux distros support robust directory services, and if the OP needs client management they will have to go with a Windows box to manage them.  Linux servers can't give windows boxes group policy.

Well you can't get ALL the functionality, but you CAN get it close. If you use SuSE as has been suggested, they have some tools that do a pretty good job of user control.

-Tim

---

### Post by tlarkin on 2009-09-16
> **windependence said:**
> Well you can't get ALL the functionality, but you CAN get it close. If you use SuSE as has been suggested, they have some tools that do a pretty good job of user control.

-Tim

Open SuSe has zero to do with SuSe Enterprise (owned by Novell) and Noveell integrated their eDirectory into SuSe Enterprise.  So, yes, perhaps SLED and SLES could be feasible cheaper solutions, however, the free open source ones won't cut it if the OP needs to push apps, policy, and manage the desktop.  SLES will have zen (apps and imaging) and the Novell client for authentication and the eDirectory for managing users, groups and containers.

Really, in my professional opinion, Open Source Linux servers are really meant for stand alone servers in the Enterprise world.  Things like web services, file sharing, or for specific 1 box functions, and enterprise Linux is meant for client management, deploying policy, virtualization, and other things you would need when managing many computers on a network.

---

### Post by Johnsie on 2009-09-16
Hi, I'm a professional programmer. What we do is simple:

Install VMWare Esxi which is a very thin operating system:

[http://www.vmware.com/products/esxi/](http://www.vmware.com/products/esxi/)


This allows you to have more than one operating system running on the machine at a time. Each operating system is run in a virtual machine on the same computer. For example one of our machines is running Ubuntu Server and Freebsd at the same time.

ESXi can be managed remotely and is really easy to use. It's about as easy to install as Ubuntu.


In terms of Active Directorry stuff... There is nothing on Linux that meets the quality of Exchange Sever/Outlook. I've spent alot of time trying different solutions and always go back to the the fact that Windows is simply better at this. Having ESXi allows to you have the benifits of Ubuntu server and Windows server on the same machine but in the most efficient way.

---

### Post by tlarkin on 2009-09-16
> **Johnsie said:**
> Hi, I'm a professional programmer. What we do is simple:

Install VMWare Esxi which is a very thin operating system:

[http://www.vmware.com/products/esxi/](http://www.vmware.com/products/esxi/)


This allows you to have more than one operating system running on the machine at a time. Each operating system is run in a virtual machine on the same computer. For example one of our machines is running Ubuntu Server and Freebsd at the same time.

ESXi can be managed remotely and is really easy to use. It's about as easy to install as Ubuntu.

Virtual servers are great, but you need a hefty machine to run multiple OSes and multiple services for a large number of users.

For example, my institution I work for has 15,000 computers (both PC and Macs) and probably 25,000+ users.  1 virtual server would choke and die if I tried running everything off of it.

I know you probably know this, but you have to scale it.

---

### Post by Johnsie on 2009-09-16
Yes, I should've pointed out that ESXi doesn't run on most whiteboxes and expects a bit of poke from the hardware.

I don't think a large institution would be running its stuff off just one box, but alot of small-medium sized companies would usually have just one a very small number of servers. Here we spread some of the load out by using whiteboxes as print servers.

---

### Post by scottuss on 2009-09-16
I would not recommend Suse as an "easy to use" distro. For people with little experience of Linux who need a server fast, use Ubuntu Desktop and install everything via a GUI. Then, learn the command line and eventually migrate to a leaner, faster more effective server install such as Ubuntu Server or similar.

Every time I've ever used yast it has messed up and has been terribly slow.

---

### Post by tlarkin on 2009-09-18
> **scottuss said:**
> I would not recommend Suse as an "easy to use" distro. For people with little experience of Linux who need a server fast, use Ubuntu Desktop and install everything via a GUI. Then, learn the command line and eventually migrate to a leaner, faster more effective server install such as Ubuntu Server or similar.

Every time I've ever used yast it has messed up and has been terribly slow.

SuSe is the only Linux distro (the Enterprise version) I know that supports Windows boxes and management via eDirectory.  It may be the only non MS alternative to managing machines.

---

### Post by ukripper on 2009-09-18
Strange no one mentioned openLDAP (for PDC) + samba server.

Check this link - [http://www.howtoforge.com/ubuntu-9.04-samba-server-integrated-with-active-directory](http://www.howtoforge.com/ubuntu-9.04-samba-server-integrated-with-active-directory)

---

### Post by scorp123 on 2009-09-18
> **scottuss said:**
>  I would not recommend Suse as an "easy to use" distro. You got to be kidding. 

> **scottuss said:**
>  For people with little experience of Linux who need a server fast, use Ubuntu Desktop and install everything via a GUI. Yeah right .... Like SLES and OpenSUSE don't have GUI's??? ](*,)

> **scottuss said:**
>  Then, learn the command line  Isn't that a contradiction to what you posted yourself? If someone requires a server really fast then there is no time to mess with learning command line stuff. Like it or not but then something like SLES or OpenSUSE are the best choices because you can go ahead, use "yast" and be productive in no time. Ubuntu is great as desktop distro ... but as server distro you really have to know what you do or else you will be wasting lots of time. For a beginner this is not really an option.

> **scottuss said:**
>  Every time I've ever used yast it has messed up  Only happens if you manually mess with stuff. You have to do everything via "yast" and let it handle the config files. Manually touching stuff here is a big "no" or else strange scary things happen.

> **scottuss said:**
>  and has been terribly slow. SuSE 10 was horribly slow, yes. But not so anymore. OpenSUSE 11.1 and SLES 11 are actually very fast and should not be slower than Ubuntu on the same hardware.

---

### Post by windependence on 2009-09-18
> **tlarkin said:**
> Open SuSe has zero to do with SuSe Enterprise (owned by Novell) and Noveell integrated their eDirectory into SuSe Enterprise.  So, yes, perhaps SLED and SLES could be feasible cheaper solutions, however, the free open source ones won't cut it if the OP needs to push apps, policy, and manage the desktop.  SLES will have zen (apps and imaging) and the Novell client for authentication and the eDirectory for managing users, groups and containers.

Did I say OpenSuSE? No, I didn't, someone else did.

> **tlarkin said:**
> Really, in my professional opinion, Open Source Linux servers are really meant for stand alone servers in the Enterprise world.  Things like web services, file sharing, or for specific 1 box functions, and enterprise Linux is meant for client management, deploying policy, virtualization, and other things you would need when managing many computers on a network.

Then what are you doin on the Ubuntu forum? I too, do this professionally in large enterprises and yes it's frustrating to be on the SERVER forum and have people whining about not having a GUI, but I don't see how this is helping the OP at all. 

IMHO, he is trying to make chicken salad out of chicken *****. No, you can't run 15,000 users from a small VM box, but you CAN run quite a but of VMs and user traffic with a reasonbly powered box for a smal business. I think that's what he is trying to do. If not, then the guy is out of luck.

-Tim

---

### Post by windependence on 2009-09-18
> **Johnsie said:**
> Hi, I'm a professional programmer. What we do is simple:

Install VMWare Esxi which is a very thin operating system:

[http://www.vmware.com/products/esxi/](http://www.vmware.com/products/esxi/)


This allows you to have more than one operating system running on the machine at a time. Each operating system is run in a virtual machine on the same computer. For example one of our machines is running Ubuntu Server and Freebsd at the same time.

ESXi can be managed remotely and is really easy to use. It's about as easy to install as Ubuntu.


In terms of Active Directorry stuff... There is nothing on Linux that meets the quality of Exchange Sever/Outlook. I've spent alot of time trying different solutions and always go back to the the fact that Windows is simply better at this. Having ESXi allows to you have the benifits of Ubuntu server and Windows server on the same machine but in the most efficient way.

This is exactly what I do, but I do use server class hardware (mostly off lease used). You can run a surprising number of servers in one box including all the networking right in the box.

-Tim

---

### Post by tlarkin on 2009-09-18
> **windependence said:**
> Did I say OpenSuSE? No, I didn't, someone else did.



Then what are you doin on the Ubuntu forum? I too, do this professionally in large enterprises and yes it's frustrating to be on the SERVER forum and have people whining about not having a GUI, but I don't see how this is helping the OP at all. 

IMHO, he is trying to make chicken salad out of chicken *****. No, you can't run 15,000 users from a small VM box, but you CAN run quite a but of VMs and user traffic with a reasonbly powered box for a smal business. I think that's what he is trying to do. If not, then the guy is out of luck.

-Tim


I said that a server would work for his 10 to 80 users per a building, but if he needs features of SMS and Active Directory Linux won't do it.  In those environments really, open source *nix servers are typically best used as a stand alone server.

I was also stating the Enterprise Linux distros (like SuSe and Redhat) offer support that other open source Linux distros do not offer, so they are more geared towards running in those environments.  I would much rather deploy that, than say Debian or Ubuntu or anything else if it was in a large production environment.  I would like to have that level of enterprise support.

---

### Post by scorp123 on 2009-09-18
> **windependence said:**
> You can run a surprising number of servers in one box including all the networking right in the box. Provided that the sizing is done right and the hardware can handle it.

But I am not so sure that this applies to OP ...?

---

### Post by scorp123 on 2009-09-18
> **tlarkin said:**
>  I would much rather deploy that, than say Debian or Ubuntu or anything else if it was in a large production environment.  I would like to have that level of enterprise support. Bingo.

And let's face it: A brainless chicken could operate SLES or OpenSUSE. You just need to remember one command: "yast".

Operating a Debian and/or Ubuntu server requires some skills, and OP already said that he was a "beginner".

---

### Post by AlexanderDGreat on 2009-09-20
Hi, we have the same situation.

I've deployed Windows 2003 SBS with 12 workstations in our company before, but switching over to Linux, I needed a Windows SBS equivalent.

I searched online and I'm currently on the path of LTSP server, doing PXE boot on our Ubuntu Intel Atom machines.

I'm doing this because our workstations are just using basic computing like: youtube, imeem, YM, email, typing, printing, burning dvds, and watching movies mov, avi, mp4, plus, terminal servers save massive electricity.

By the way guys, I'm also very NEW to Linux, but I agree with ukripper:

> **ukripper said:**
> Strange no one mentioned openLDAP (for PDC) + samba server.

Check this link - [http://www.howtoforge.com/ubuntu-9.04-samba-server-integrated-with-active-directory](http://www.howtoforge.com/ubuntu-9.04-samba-server-integrated-with-active-directory)

Anyway, here's my humble setup now: I'm doing an SMB server with file sharing, I've also configured LTSP server.

Here's what I want to accomplish next:

An "Active Directory" so everyone can list their printers and be used by everybody.

Thanks.

---

### Post by scorp123 on 2009-09-20
> **AlexanderDGreat said:**
>  An "Active Directory" so everyone can list their printers and be used by everybody. Wouldn't CUPS be sufficient for this?

---

### Post by Vladimir_BG on 2009-09-20
I appriciate all the feedback.

Seems I'm stuck with MS solutions for now.

I really need the ability to set group policies and deploy software trough AD.

If it waren't for that, I'd use SME server. It does the routing, mail, file sharing and similar stuff and is simple to deploy. I was hoping someone may have had some experience setting an all-in-one server with ubuntu.

Small businesses would really benefit from an all-in-one solution for a whitebox, and MS would price their (very) buggy software more resonably and work harder on making it better.

---

### Post by AlexanderDGreat on 2009-09-20
> **scorp123 said:**
> Wouldn't CUPS be sufficient for this?

Forgive me for being an idiot, but can CUPS handle all printers scattered around in different workstations?

If yes, can you pls. teach me how?

The only way I did this before in MS SBS was listing the printer in the AD, and getting that AD printer information in other workstations.

Thanks. =)

PS Sorry to step on your thread Vladimir_BG. =\

---

### Post by tlarkin on 2009-09-20
CUPS cannot manage printers in the way you want. 

Like I said earlier, SuSe Enterprise Linux does this.  iPrint for printer management and deployment.  eDirectory for your directory services.  Zen for PXE boot and imaging, app deployment and policy deployment.

---

### Post by AlexanderDGreat on 2009-09-20
Hi tlarkin, I looked at the SUSE Linux Enterprise Server, how much does it cost? I can't seem to find it in the website.

Thanks.

---

### Post by ukripper on 2009-09-20
> **AlexanderDGreat said:**
> Forgive me for being an idiot, but can CUPS handle all printers scattered around in different workstations?

If yes, can you pls. teach me how?

The only way I did this before in MS SBS was listing the printer in the AD, and getting that AD printer information in other workstations.

Thanks. =)

PS Sorry to step on your thread Vladimir_BG. =\

Why not use webmin to manage your cups print server. check this link - [http://www.fsa-blast.org/Webmin/PrinterAdministration](http://www.fsa-blast.org/Webmin/PrinterAdministration)

Webmin has more than 55 modules which actually extends much more functionality than active directory can and makes any linux/unix server's administration easy.

---

### Post by tlarkin on 2009-09-20
> **AlexanderDGreat said:**
> Hi tlarkin, I looked at the SUSE Linux Enterprise Server, how much does it cost? I can't seem to find it in the website.

Thanks.

You know, I honestly do not know as I don't write the checks at work.

Google gave me this as the result

[http://www.amazon.com/gp/product/B000HS3ETO](http://www.amazon.com/gp/product/B000HS3ETO)

I know that MS Server starts at $1,000 for the first tier, and I think it has limited user support.

---

### Post by AlexanderDGreat on 2009-09-21
OK, thanks, I'll try CUPS.

---

### Post by AlexanderDGreat on 2009-09-21
@Vladimir - found this article, might be useful:

[http://commons.oreilly.com/wiki/index.php/Ubuntu_Hacks/Small_Office/Home_Office_Server](http://commons.oreilly.com/wiki/index.php/Ubuntu_Hacks/Small_Office/Home_Office_Server)

---

