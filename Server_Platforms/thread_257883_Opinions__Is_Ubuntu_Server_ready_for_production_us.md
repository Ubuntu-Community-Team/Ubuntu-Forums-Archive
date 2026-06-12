---
title: "Opinions?  Is Ubuntu Server ready for production use?  Or stick with CentOS?"
date: 2006-09-15
forum: Server Platforms
---

### Post by luckylucky on 2006-09-15
I hope that this thread will see a bit of activity.  In YOUR opinion, do you think that the Ubuntu Server is ready for serious production use?  Why or why not?  

BTW, I too am a huge Ubuntu fan, and I too toot the horn for Ubuntu, saying "it Rocks" and all, but PLEASE DON'T just say that Ubuntu is the best unless you can provide a logical reason for your opinion.  Let's cut the BS and discuss the reality.  What is your opinion of the Ubuntu Server, say, in conctrast to RH or CentOS, and which would you use for a real live production server?  Why?  What "flaws" do you see in the Ubuntu Server?  Do you think that it'll be a serious contender to RedHat EL someday?


The following is a bit of text I wrote in addition to a previous post:

BTW I now use Ubuntu ~ 98%, it is my "regular" OS on 3 computers, have gotten my employees on Ubuntu, and even my primary business partner is now "getting into it". Ubuntu ROCKS! IMO it is the best desktop linux around period (especially when XGL becomes normally supported in a future release). I'm playing with Ubuntu Server to see how good it is, and have it running my home servers, however I am still using CentOS on all production servers. So far I've experienced a few inconsistencies with some programs not finding config files because debian puts them in differnt places than they expect to find them (whereas they are in the "proper" place on Fedora & CentOS (and of course RH too). I'm going to wait until Ubuntu Server is a bit more mature and gets a good reputation before putting my money on it. But none-the-less as far as Desktop distros go, after changing preferences (I'm not fond of brown), and after playing around with many distros I have settled on Ubuntu as being what I consider to be the best Desktop distro overall. Yay Ubuntu!

---

### Post by GrammatonCleric on 2006-09-15
I was in the very same seat that you are now in.  Let me first start by saying simply... Yes.  Now let me describe my office linux environment to clarify.  

When I started at my current job I was hired for my linux experience.  I was told that the distro that they used was Gentoo and that this choice was made by the person I was replacing.  Everyone in the office seemed to love Gentoo. I was fine with Gentoo I've used it before, hell I even worked with Daniel Robbins at UNM HSCCS, but never for all linux servers in a production environment. Well, what I inherited was a ton of Gentoo servers of varying versions of Gentoo (i.e. 2004, 2005, 2006.0, 2006.1) none of which have been updated or patched in a long while.  When I mentioned this to everyone in the office I recieved blank stares, simply stating "updates?" Still at this point no big deal I can simply back them up, image them, and start bringing them all in line.  True enough but do you know how long it takes to download and compile every single update package, not to mention the fact that Gentoo will upgrade packages (i.e. gcc 4.1.1) that in some cases force you to rebuild, via emerge, EVERY SINGLE PACKAGE on the server? On average the each severs is taking me 13+ hours to update?   Now I describe this because Gentoo has been described as "production ready."  I finally sat down with my boss and had a heart to heart about linux distros.  My basic concern was that I could be paid to spend a disproportionate amount of my time updating these Gentoo servers (i.e. 13 hours+) or install a dirsto that uses binary packages and update the same servers in a hour or less.  That was an easy choice for my boss. 

Now with a go head I was stuck with choosing which distro to start using.  

Red Hat? Certainly production server ready and widely supported.
Debian? Again another distro that is production ready, tons of packages available.
Suse? Yet another distro that is production ready.

It really came down to several factors.

1. Stable.
2. Easy to install from a single CD - So I can train the helpdesk staff to do it.
3. Easy and good package management.
4. Support to install some none free applications (ie. Acronis True Image, Evault, etc.)
5. Fast patch fixes.
6. Good support through the internet community.
7. Lastly, Commercial support if need be. 

Meeting all the above I decided to give Ubuntu a shot.  I've not had any regrets yet,  well except now I have time to sit in meetings.... =P



GC

---

### Post by luckylucky on 2006-09-15
Hi GramatonCleric!

Wow, now that was a great post!  Thank you!  It was informative in that you've obviously weighed your options for a serious situation and have picked Ubuntu.  If actions speak louder than words then I'd value your opinion since you've done what you've done.

Just out of curiosity, how long ago did you do that transition?  Since that time have you found that things worked well overall?  Obviously better than Gentoo, but would you say better or more-or-less equal to other options (i.e. RH, CentOS, SuSe)?

FYI, I'm actually the boss in my company (actually 50% partner).  I've got a full time server guy handling our servers (all web servers - we're decentralized).  For the past few months I've had my server guy teach me all about linux & now servers.  The goal is for me to know how to do pretty much everything he does - not to replace him, but partially because I am fascinated with linux, but also because this is the only aspect of our business that has been a "black box", and if he were ever to leave, die, quit, get fired, whatever, then we'd be screwed.  I believe that it's good to have experts working specific jobs, but as an owner I should be able to be a "jack of all trades" to handle anything that comes up.  But again a heavy reason for learning all this is because I have a passion for it.

All my computers have been changed over to linux now (actually now settled on Ubuntu).  I've been tinkering with linux for over a year, but have adopted it fully a few months ago.  I doubt that I'll ever go back to being a full time windows user again.  

Lately I've been learning the servers side of linux, which I'm blown away with how cool it all is, and my eyes are open wide to numerous business applications and fascinating possibilities that I've never even realized possible before!  My only wish is I discovered it earlier to implement the features it has to offer for my businesses.  I can't believe that more businesses don't take advantage of all that it has to offer (which I'm sure would revolutionize many smaller companies if they only knew what it could do).  My server guy & I have been playing around with Ubuntu in addition to him teaching me CentOS (his favorite server distro, but I understand why he likes it).  I'm actually the one who introduced him to Ubuntu and he has grown to love it too, for Desktop use.  We're experimenting with Ubuntu for servers.  What strikes me about it is that I personally find it much easier to work with.

Bottom line is that I'm just curious whether it can be implemented with confidence for web servers.  I kind of prefer it from a pragmatic use perspective so far, also from an ethical perspective (though CentOS is perfectly legal, somehow I feel that it's borderline immorral since it's a Red Hat knock off), and just overall of all the linux distros it's the one I've got a "warm fuzzy" for.

---

### Post by GrammatonCleric on 2006-09-15
Hi luckylucky,

Glad I could be of some help to you.    Like you I have the Ubuntu bug and I think it has spead to support staff in my shop.  They're all playing with it and installing it on their home systems, laptops, and servers.  =)

Let me try to answer your quesitons.
[B][I]
 "how long ago did you do that transition"   [/I][/B]

We are still in the process moving the servers over but there are only a few more to do.  Mind you the reason for taking our time is the various functions that we use linux servers for (i.e. smtp spam/content filtering/antivirus gateways, file servers intergrated into AD, Web servers, SQL servers, etc..).  Acronis True Image & G4U are both lifesavers!!! 

[I]"[B]Since that time have you found that things worked well overall"

[/B][/I] Very well.  Like I stated I now can spend less time building and maintaining servers. 
[B][I]
"Obviously better than Gentoo, but would you say better or more-or-less equal to other options (i.e. RH, CentOS, SuSe)?"[/I][/B]

At a previous shop I used Redhat ES and Fedora.  The only thing that I disliked (and still do) was RedHat's package managment and the enless dependancy issues encountered with it.  I opted to use apt on fedora boxes but since we paided for ES support I left them using the default package manager.  I will say I did like the ES web portal that Redhat let's you  basically push updates to the servers registered with them.  I also disliked the 3-5 cd swap that you need to do to install Fedora or RH ES, that is unless you have servers that have DVD ROM's.  With that said I like Ubuntu install and manage process a little better.  Now if Ubuntu had a web portal where I could manage all the servers either managed through them or something that I could host internally...that would be SO nice.  =)

[B][I]"Bottom line is that I'm just curious whether it can be implemented with confidence for web servers. I kind of prefer it from a pragmatic use perspective so far, also from an ethical perspective (though CentOS is perfectly legal, somehow I feel that it's borderline immorral since it's a Red Hat knock off), and just overall of all the linux distros it's the one I've got a "warm fuzzy" for."

[/I][/B]Not knowing your environment I can't really say the Ubuntu will be "the" answer for you.   It's working very well for me and I'm really please with it.   Being an audiophile I kinda view Linux like stereo equipment, what sounds amazing to me may not be your cup of tea.  You may like more bass response or sound stage presence but the nice thing about linux is you can have a VERY nice system without going into debt to get it. =)


Well I hope I was of a little help to you.   If you have any other questions please feel free to send me a message through this form...

GC

---

### Post by hkgonra on 2006-09-15
I am still a flat out linux noob but let me put my two cents in. I am currently shopping for e-mail server software for my company. There are several new ones out there that have some VERY cool ajax features, zimbra & Scalix are my two favs. Currently they do not support ubuntu in fact not even debian. 
I realize this is just a small consideration but I wonder how many other server software packages are out there for different things that servers normally do , that have no ubuntu packages ? 
Just something to think about.

---

### Post by rastilin on 2006-09-15
I know that Zimbra and Scalix both support linux. Even if there isn't a deb prepared for ubuntu, it just means it'll be a bit harder to install them, but they will run.

EDIT: I should mention one more thing. I also used to use gentoo and I switched away for precisely the same reason given previously. Eventually I relaized I spent a disproportionately large amount of time doing system maintainance.

---

### Post by houstonbofh on 2006-09-16
I too have a few Ubuntu servers out in the wild.  I chose them at first because I was doing a lot with the desktop.  With 2 different systems I would always be looking in the wrong place for the box I was on. :D
The big plus I see is the way Ubuntu handles packages and updates.  Other than the recent X debacles, I can set the servers to auto-update and forget them.  This is something I would not do with some other distributions.

---

### Post by sitedesign on 2006-09-16
> **GrammatonCleric said:**
>  Now if Ubuntu had a web portal where I could manage all the servers either managed through them or something that I could host internally...that would be SO nice.  =)
GC

Have you tried webmin? It's a very nice web based admin system.
[www.webmin.com](www.webmin.com)
it has a facility to manage lots of servers from a central control panel then cluster update the servers as required.

Regards Peter King

---

### Post by GrammatonCleric on 2006-09-16
Yup tried and use Webmin for some things but what I was refering to was something more like Red Hat's [Enterprise Systems Management]("http://www.redhat.com/rhn/").   Basically a central managment portal that all your servers connect to that allows you to administer them from a single location (this includes pushing security updates, log collection, services control, etc). Also simialar to [VMWare's VirtualCenter]("http://www.itnews.sk/buxus_dev/images/2005/iw0605_tech_virt_obr_5_b.jpg") .

GC

---

### Post by quad3d@work on 2006-09-16
I am currently working for a company that consists mainly Solaris servers (we do some HEAVY java stuff) and quite a few Redhat servers as well. It really depends on your company size... my company is fair sized and I think in many cases company are willing to shell out money for OS support instead of getting their hands dirty. Last time I talked to CIO I asked why don't we get some of the in-house applications to run on Linux... his response was "We did tried, but Linux box crashes left and right causing us more time to fix it. Solaris box just don't have a single problem." I am a little unsure why that's the case I can only assume that our development team optimized a large code base for Solaris...

Now... my CIO have expressed the ideas to sysadmins that they want to slowly migrate those Redhat box to Fedora. I think the reason is most sysadmins are used to how Redhat works and probably don't want to bother learning another distro. I'm not a sysadmin in the company but I deployed a Ubuntu server for my own section hosting our section webpage and wiki. My director is amazed with Munin monitoring... because we don't have much a tool like that to monitor our main production servers (Solaris), or just no sysadmins wants to learn how RRDTool works. We are currently having some load issues and no one really knows how 'sar' works in Solaris.

I also managed two live servers for one of my friend's webhosting company. Before I took over they were running on Debian Sarge... let me tell you... him and another sysadmin (RHCE certified) had that server in very bad setup. Allowing everyone to have SSH access, qmail worked about half of the time, AWStats was hacked and server became a zombie. I pulled their backup server down, installed Debian Sarge, setup it and migrated everything over. Server is up for just about a year now... rock solid and everything works.

I recently pulled the old server out and installed Ubuntu server on it. Why? because I had good experience deploying it for my section at my primary job. My home server box (mainly just NFS and Samba) runs on Ubuntu server as well. Matter fact I'm going to datacenter today and stick that blade server back in. Though I have good success with it at my primary job, since this is a 'live' server, I'm still very cautious about a lot of stuff. Therefore, on my desktop I VMWared a copy of Ubuntu server and I am going to test it in VMWare first before I deploy it. Because this server is going to host a lot of domains as well.

My .02 is yes, I think Ubuntu server is ready for prime time. But if you are really anal you maybe should look into Debian. Their apps are a little outdated but it's proven to work almost always.

---

### Post by skali on 2006-09-16
Hi 

I selected Linux when i need to deploy a windows 2003 server at a client side. We first deployed a windows nt server that eventually decided to be upgraded to windows 2003. However, the cost to upgrade including software and hardware + client licenses was the major reason. So after doing a meeting with my boss, aggreed to do Linux.

I surely agree with the GrammatonCleric regading the factors he mentioned when deciding which distro to use. I was already using Ubuntu at home, so decided to give it a try. And guess what its running fine.

One thing that the Ubuntu Team must do is to provide the [COLOR="Red"]**Server Installation Packages**[/COLOR] on the CD along with the **[COLOR="Red"]Base Packages[/COLOR]** as with Fedora, SuSe, Debian etc. This is the thing that i like most  about other distors as you need only the installation media only....

It won't make any differences as these guys did distributed **2 CDs** with the **5.10 version.** I guess it would be good for those administrators where downloading packages every time is no fessible due to in-adequate bandwidth limitations.

---

### Post by lamego on 2006-09-17
> One thing that the Ubuntu Team must do is to provide the Server Installation Packages on the CD along with the Base Packages as with Fedora, SuSe, Debian etc. This is the thing that i like most about other distors as you need only the installation media only....
The Ubuntu Server CD does include the most common server packages.

---

### Post by GrammatonCleric on 2006-09-18
Well it's not the perfect solution to to the central server console that I was refering to but it comes close.

[http://www.openqrm.org/](http://www.openqrm.org/)

GC

---

