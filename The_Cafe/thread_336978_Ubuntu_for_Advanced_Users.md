---
title: "Ubuntu for Advanced Users"
date: 2007-01-12
forum: The Cafe
---

### Post by Yfrwlf on 2007-01-12
My biggest complaint with Ubuntu, which is a small complaint really (Ubuntu rocks!), is it's lack of advanced administration tools out of the box.  For users who wish to configure a firewall or mess with Apache server options, you have to install additional programs in order to do this.  Many people might think that's a pretty poor complaint and I agree to some extent.  If you need them, they are there and you can install them thanks to the very nice and big software repository of Debian/Ubuntu.  I believe a lot of users would want to do things like manage their firewall though, so I wanted to ask what the Ubuntu community thinks about having an "advanced tools" section in the menu which could contain such tools that would be installed by default.  Forgive me if some of these things are already installed, or if this thread has already been rehashed before (though I looked for similar threads).  I know some advanced tools are but not others.

I think some users would like to see a firewall program, a partition program, sever configuration programs, bootloader config, etc etc.  Some of these things may be installed by default already, but it would be nice seeing others as well.  I use Firestarter for my Ubuntu firewall.  I do have to say that the lack of advanced features out of the box is one reason I enjoy a default Fedora Core install over Ubuntu.

Again, a small complaint perhaps, but I think installing more advanced tools and putting them in their own little "advanced" section may not be a bad idea and might attract more advanced users more easily as well as the beginner users.  Just a suggestion :)

I'm sure one problem with this is space, though, and trying to fit it all on one CD.

---

### Post by G Morgan on 2007-01-12
Last line says it all. Perhaps there's room for a meta-package that pulls in the tools you mention. Maybe an automatix style script to turn on and off the various tools and pull them in via apt.

//edit - perhaps you should set up a wiki page like the corporate edition guy did with a list of what you want in total.//

---

### Post by Hendrixski on 2007-01-12
What is the benefit of doing this out of the box?  An advanced user can easily download these, or create their own Ubuntu ISO image that has them pre-installed, or a script that will automatically get all of them.  New users would be scared by too many features.

besides, really really advanced users are probably using Gentoo... because, you know: **If it moves, compile it!**

---

### Post by Johnsie on 2007-01-12
It's very easy for an "advanced user" to download those programs. Ubuntu is aimed to be easy to use and also needs to fit on a CD. Adding non-essential packages isn't the best way to fill the CD.

---

### Post by majesticturkey on 2007-01-12
KISS: Keep It Simple, Stupid.

If you add all this configuration stuff out of the box, it causes a lot of confusing dialog and options, that are unnecessary. For every person that wants a certain advanced config option, there's a dozen people happy just the way things are. Advanced users should add the usability they want, developers shouldn't bog their programs down with excess usability.

Make sense?

---

### Post by OrangeCrate on 2007-01-12
^, KISS is a good philosophy. Besides, an "advanced user" is generally just a user that has an overwhelming need to tweak things until they break.

---

### Post by daz4126 on 2007-01-12
> **Hendrixski said:**
> An advanced user can easily download these, or create their own Ubuntu ISO image that has them pre-installed



Sorry to hijack this thread, but how would somebody go about creating their own ISO image or Ubuntu, are there any tutorials anywhere?

thanks,

DAZ

---

### Post by spockrock on 2007-01-12
> **daz4126 said:**
> Sorry to hijack this thread, but how would somebody go about creating their own ISO image or Ubuntu, are there any tutorials anywhere?

thanks,

DAZ

The best and easiest tool is reconstructor, imho...... its amazing....

---

### Post by pebo on 2007-01-12
> **OrangeCrate said:**
> ^, KISS is a good philosophy. Besides, an "advanced user" is generally just a user that has an overwhelming need to tweak things until they break.

Have to disagree, I'm a refugee from SuSE, and the one thing I miss is the mighty YAST, where just about all the configuration tools you can think of are under one roof.

---

### Post by daz4126 on 2007-01-12
> **spockrock said:**
> The best and easiest tool is reconstructor, imho...... its amazing....

Thanks for that, is it in the repos?

DAZ

---

### Post by speedman on 2007-01-12
Advanced users don't need their hands held and are quite capable of using apt-get, vi, etc. etc..

SM

---

### Post by spockrock on 2007-01-12
> **daz4126 said:**
> Thanks for that, is it in the repos?

DAZ
nope go here the debs are there, I mean it is designed to created your own custom ubuntu live discs.
[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

---

### Post by Brunellus on 2007-01-12
Ubuntu for advanced users?

Debian Sid.

---

### Post by Bohemie on 2007-01-12
But there are avarage users that wants to change their firewall settings. for example to setup the amule client. when a user want to allow some port or some thing there is no firewall program for it in ubuntu and he don't know any program name to do that or he knows nothing about apt at all. in this situation people starts to think that ubuntu is not able of changing the firewall settings.

---

### Post by darkhatter on 2007-01-12
> **Hendrixski said:**
> What is the benefit of doing this out of the box?  An advanced user can easily download these, or create their own Ubuntu ISO image that has them pre-installed, or a script that will automatically get all of them.  New users would be scared by too many features.

besides, really really advanced users are probably using Gentoo... because, you know: **If it moves, compile it!**

its built into the new kernel....

---

### Post by Yfrwlf on 2007-01-12
> **pebo said:**
> Have to disagree, I'm a refugee from SuSE, and the one thing I miss is the mighty YAST, where just about all the configuration tools you can think of are under one roof.

That's what I'm talking about.  I also really loved the plethora of system configuration tools that exists in Suse.  That's like THE thing that makes Suse shine, really.  Fedora has many of those tools as well but fewer, and Ubuntu is very lacking with them but also nicer in ways that Suse is not. :)

---

### Post by Yfrwlf on 2007-01-12
> **Bohemie said:**
> But there are avarage users that wants to change their firewall settings. for example to setup the amule client. when a user want to allow some port or some thing there is no firewall program for it in ubuntu and he don't know any program name to do that or he knows nothing about apt at all. in this situation people starts to think that ubuntu is not able of changing the firewall settings.

That's really what I was trying to get at.  I do think there are a lot of users who would want to do some things like configuring firewalls and it took me a while to find out about Firestarter.  I'm quite sure I tried looking up "firewall" but it didn't come up in the list.  Perhaps that is the real problem here and one that should be tackled?  I don't have access to a Ubuntu install (Kubuntu, but not Ubuntu) to try this out again.

---

### Post by Yfrwlf on 2007-01-12
> **Brunellus said:**
> Ubuntu for advanced users?

Debian Sid.

That's comparing apples to oranges.  Ubuntu is a much easier system.  I'm mearly suggesting the addition of a few system tools for users wanting to use them, or an easier way for these users to find them.

When I was looking for a firewall, I had difficulty.  It would be nice indeed when you needed programs to put in the kind of program like browser, or firewall, and they would come up.  You're going to say "it already does", but I could have sworn I tried for firewall, and couldn't get anything in the search until I tried Firestarter specifically.  I think "browser" does pull up at least some of the browsers.  Only have access to Adept through Kubuntu otherwise I'd try this again. :)

I'm suggesting that perhaps finding software could be made easier for new users who are migrating from Windows to Linux and do not know the names of the programs they need yet.

There are a variety of ways this issue could perhaps be smoothed out for new users even further than it is already.  Ubuntu is fantastic for new Linux users and the progress on it is wonderful.  It's goal, however, is ease of use and attracting new users, so in that intrest I am suggesting that there may be room for improvement here, but I don't know how it would be best improved if it can be, hence this thread. :)

P.S.  Maybe I should have named this thread "Ubuntu for Slightly Less-than-new Users" ;)  (Even though I myself am a vetran to Linux, but didn't know about Firestarter or Shorewall and tried searching for firewall GUIs through Ubuntu's package manager first, before researching on the intarwebz, only to find out that I think both (?) are available through the autoinstaller but I just had to type in their names specifically.)

---

### Post by Polygon on 2007-01-12
well a lot of the "simplicity" of ubuntu comes from gnome.

and i consider myself a semi linux power user, and i dont see what else to have in synaptic. The option to add custo repos is there, to mark for installation / removal / upgrade / force upgrade / etc is all there, but maybe there is something im missing

and yeah, if you really want to have this, why not create it? create a meta package with all the administration tools needed, and then upload it to the ubuntu repos. That way people can install it with a simple "apt-get install packagenamehere"

ubuntu is only on a cd... so there is not much space for anything else besides whats on there now. Maybe on the dvd....

---

### Post by Sunnz on 2007-01-13
You can just use the server edition which would install LAMP and iptables automatically, right?

---

### Post by darweth on 2007-01-13
Hrm.  Should I be using a firewall for a typical desktop system with Ubuntu?  I always ran one on Windows but that is an insecure dangerous beast of an OS.  Is it necessary to incorporate one here too?

---

### Post by maniacmusician on 2007-01-13
if you ever communicate with Windows computers, which you probably do (this includes sending files over email) you should use a virus scanner and firewall. Even if they dont affect you, you might still have the viruses on your disc. Wouldn't want to accidentally pass them onto a windows user :)

---

### Post by spockrock on 2007-01-13
umm..... I just use the firewall on my router, most often hardware firewalls are 1000x better then software firewalls, I have never used firestarter, but firewalls like zonealarm or other application based firewalls are pretty much ineffective.  If you have an old computer just sitting around you could also try something like smoothwall, which is nifty.  But if you are using a router, thats more then enough, as along as you dont put yourself on say the DMZ.

---

### Post by darweth on 2007-01-13
Yeah.  I know routers are more effective.  I am still plugged directly into the modem though.  Oops... Shouldn't say that on these forums!  Bad people will get me!

---

### Post by spockrock on 2007-01-13
I don't think saying that here will get your computer 'haxed' however if you feel insecure then use a firewall.....

---

### Post by darweth on 2007-01-13
I was joking. :P

---

### Post by spockrock on 2007-01-13
silly me.....

---

### Post by h2gofast on 2007-01-13
Ubuntu for advanced users, I think it's called debian  ;)


Really though, why spend extra time configuring stuff when ubuntu does it for you.

---

### Post by spockrock on 2007-01-13
> **h2gofast said:**
> Ubuntu for advanced users, I think it's called debian  ;)


Really though, why spend extra time configuring stuff when ubuntu does it for you.

QFT....I used debian and I hated configuring and setting everything up.....

---

### Post by Tomosaur on 2007-01-13
An advanced user would know that you technically don't NEED to install anything more than comes with Ubuntu to reconfigure stuff.

---

### Post by Wight_Rhino on 2007-01-13
> **Tomosaur said:**
> An advanced user would know that you technically don't NEED to install anything more than comes with Ubuntu to reconfigure stuff.

Exactly right:) 

"Configuration Tools" are for folk who just ***think*** they are advanced users:D

---

### Post by Enverex on 2007-01-13
> **spockrock said:**
> QFT....I used debian and I hated configuring and setting everything up.....

I have to argue with this, I think I qualify as an Advanced user, but I changed from the more "complicated" distros simply because I was getting sick of having to configure everything all the time and spend so long figuring out "how" to do so, where and what breakages are going to end up occurring anyway. Just because I know how to do something it doesn't mean I want to spend all my time doing it...

---

### Post by Tomosaur on 2007-01-13
> **Enverex said:**
> I have to argue with this, I think I qualify as an Advanced user, but I changed from the more "complicated" distros simply because I was getting sick of having to configure everything all the time and spend so long figuring out "how" to do so, where and what breakages are going to end up occurring anyway. Just because I know how to do something it doesn't mean I want to spend all my time doing it...

Exactly, I used to deliberately break things so I'd have an excuse to mess around with them to see how they worked. Not just software mind, it was a common sight to find me popping clocks off walls and unscrewing them, trying to put them together again bit by bit. It's not likely I'm overly interested in mechanics or stuff like that, I just like the challenge. Although I'm of the belief that everyone should learn as much as they can, and learn how things work whenever the opportunity arises, I certainly don't think anyone should do it any more than is necessary to understand it. It's much less time consuming to just let the Ubuntu installer 'do it's thing', for example, than sitting there reconfiguring every little thing it wants to ask me about.

---

### Post by Yfrwlf on 2007-01-14
> **Tomosaur said:**
> An advanced user would know that you technically don't NEED to install anything more than comes with Ubuntu to reconfigure stuff.

If you're running Apache, you want extra security and you want to make sure all ports are blocked except for the ones you need.  If you aren't running Apache, you may just want a way to make sure certain ports are open so that you can use certain applications.  Ubuntu and most other distros as far as I know all have firewalls on them already, your iptables.  However, configuring iptables is very complicated, so using a simple tool to do it for you is much nicer.  I do not know what what Ubuntu sets for the default iptable configuration, so correct me if I'm wrong, but there are programs, like Azureus for example, which need ports open and it will not be able to communicate until you open them up.  File transfers, servers, all sorts of reasons why you need to be able to control your firewall.

Am I right or wrong about this? :confused:

---

### Post by Enverex on 2007-01-14
> **Yfrwlf said:**
> If you're running Apache, you want extra security and you want to make sure all ports are blocked except for the ones you need.  If you aren't running Apache, you may just want a way to make sure certain ports are open so that you can use certain applications.  Ubuntu and most other distros as far as I know all have firewalls on them already, your iptables.  However, configuring iptables is very complicated, so using a simple tool to do it for you is much nicer.  I do not know what what Ubuntu sets for the default iptable configuration, so correct me if I'm wrong, but there are programs, like Azureus for example, which need ports open and it will not be able to communicate until you open them up.  File transfers, servers, all sorts of reasons why you need to be able to control your firewall.

Am I right or wrong about this? :confused:

You don't need a GUI for this, you don't even need X. I run a headless Linux server and the only way to access it is via text commands on SSH.

---

### Post by Yfrwlf on 2007-01-14
> **Enverex said:**
> I have to argue with this, I think I qualify as an Advanced user, but I changed from the more "complicated" distros simply because I was getting sick of having to configure everything all the time and spend so long figuring out "how" to do so, where and what breakages are going to end up occurring anyway. Just because I know how to do something it doesn't mean I want to spend all my time doing it...

Exactly.  Remember that computers are there to do the computing for you so you won't have to.  While you don't want to remove the power of the command line tools, believe it or not, telling someone who's trying to, say, set up an FTP server that they "shouldn't use a GUI for doing so because then they will never learn how it really works" is a poor argument.  While learning everything about computers is great, you shouldn't *always* have to.  Things CAN just work, and everyone here should know that since that's what makes Ubuntu one of the most popular Linux distros.  Sometimes the computer needs to be smarter, sometimes the user needs to be.

Any way, I guess most people here don't think that configuring even a firewall is necessary at least not out of the box.  There are a few other system configuration tools that I liked on Suse and Fedora that Ubuntu doesn't have at least by default but in some cases not at all.  I thought I'd suggest possibly adding a few more tools into Ubuntu and if they were in their own little "advanced" section and out of the way I don't think it'd confuse new users and I think it'd only be a good thing really, but if the Ubuntu devs don't think it's necessary then so be it.  They aren't that necessary, after all, and at least most of the tools are available in the repositories if you need them. :mrgreen:

---

### Post by Yfrwlf on 2007-01-14
> **Enverex said:**
> You don't need a GUI for this, you don't even need X. I run a headless Linux server and the only way to access it is via text commands on SSH.

For configuring open ports?  Don't you have to edit the iptables to do that normally, or are the iptables for much more advanced stuff instead of just port blocking?

---

### Post by speedman on 2007-01-14
Read the subject "Ubuntu for ADVANCED Users".

If you are truly an advanced Linux user you don't need your hand held.  Most of the comments in this thread would apply to intermediate users at best.

SM

---

### Post by Enverex on 2007-01-14
> **Yfrwlf said:**
> For configuring open ports?  Don't you have to edit the iptables to do that normally, or are the iptables for much more advanced stuff instead of just port blocking?

Yes, and you do that by editing the IPTables configuration file. You'll find there is a command line way of doing anything server related (plus most other things) on Linux. Why waste RAM running an entire X server, Window Manager and GUIs when you can do it without any of them?

---

### Post by Sunnz on 2007-01-14
Well for any 'real' server, you would normally run them 'headlessly' and be ssh'ing them anyway - using cli is way efficient than gui on ssh unless you get like fibre optic connection all the way to you server from your desktop/workstation.

---

### Post by Yfrwlf on 2007-01-17
> **speedman said:**
> Read the subject "Ubuntu for ADVANCED Users".

If you are truly an advanced Linux user you don't need your hand held.  Most of the comments in this thread would apply to intermediate users at best.

SM

You're right, too late to change the topic, too. :)  Well I hope the devs will at least consider possibly including some kind of firewall configuration tool after a default installation for intermediate users then.  That's the main tool I think intermediate users may want to use.  But, it's not that huge of a deal except for the fact that I don't think *any* firewall program is available in the normal add/remove software menu.  Firestarter I think is only available in the Synaptic Package Manager.  Perhaps if you're intermediate you should know about Synaptic any way tho..

---

### Post by dca on 2007-01-17
I'm kinda' lazy.  If I use 6.06LTS Server Ed on a headless wanna-be server (more like a PC w/ a couple HDDs), the first thing I'll do is install that Webmin utility dealie and access it from my laptop's web browser...
 
People I would consider advanced Linux user(s) would be people that play Linux admin in the real world.  In our data room we have tons of headless IBM server(s).  More than quite a few run Linux.  There's one admin for so many servers.  Those guys are power-users.  
 
...and indeed.  The concept of advanced user or power user is relative.  The people I know generally stick to one Linux distro (most of the time Fedora) and go from there.  Odd thing is the Linux admin(s) I know don't really know anything about Ubuntu or Xenwalk or any other foreign distro(s) because their exposure has always been to RHEL and SuSE...

---

### Post by Sunnz on 2007-01-17
Well any Windows/Mac use would have to install their own firewall even for "power users" so suck it!!!

I mean, we should think about this more carefully... if we were to include every app that an 'intermediate' user might want? Don't we have Fedora (Core) for this purpose?

---

### Post by Brunellus on 2007-01-17
> **Sunnz said:**
> Well any Windows/Mac use would have to install their own firewall even for "power users" so suck it!!!

I mean, we should think about this more carefully... if we were to include every app that an 'intermediate' user might want? Don't we have Fedora (Core) for this purpose?
No.  for that purpose, we have Debian.

---

