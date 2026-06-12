---
title: "Ubuntu Corporate Edition"
date: 2006-12-26
forum: The Cafe
---

### Post by leftcase on 2006-12-26
Hi Folks.

I work as a systems tech for a reasonably large organisation with a few thousand deployed desktops and a couple of hundred servers. Other than using Sun Solaris for a couple of web-servers, Microsoft solutions are used for all desktop and server roles.

I've managed to sneak Ubuntu based servers into a couple of roles like web-content-filtering and wireless routing, and I must say my experiences with Ubuntu have been largely positive and it stands up well in the roles I've deployed it in.

That said, i wouldn't deploy Ubuntu into a desktop role. What's more my bosses wouldn't let me even if I tried. Let me try to explain why...

The organisation I work for has spend a fortune on deploying Microsoft server technologies and they underpin all that it does. Active Directory to authenticate users to resources, Exchange technologies for organisation and email, File Servers for well... serving files! The list goes on and on. Microsoft Windows XP slides nicely into this organisational infrastructure without fuss because that's what it's designed to do. I can't grab a copy of Ubuntu, install it, join it to my domain, and grab my email out of the box.
 
That's not because the standards used to accomplish this are closed, they're available and doing the good majority of the stuff above is achievable in Linux. The problem is that it's not very easy to get stuff like LDAP authentication and group policy login scripts enabled in  Linux from scratch.

This is a bad thing. Because it's difficult to do and because many organisations have a heavily invested in Microsoft infrastructure there is often little chance of Linux being introduced to the desktop in enterprise. 

Introducing it to enterprise is possible though...

I've been looking at the Ubuntu projects here. Projects have been created for a range of needs, why not enterprise?

Take a look at Xandros Enterprise Desktop.  It's not a free distribution but it is penned as a Windows XP replacement. It sports some pretty good features including domain authentication, exchange server integration, logon scripts and group policy profiles. Imagine how far an Ubuntu distribution with the same out-of-the-box features would go!

I'm more than willing to help realise this concept in any way I can. Does anyone else share this idea or have any suggestions? Anyone willing to try make this happen? 

This thread seems as good a place as any to thrash this out and I've put a [wiki entry over here]("https://wiki.ubuntu.com/Enterprise") to hold anything that's needed.

<edit> One or two people seem to be having issues with the idea of an enterprise edition of Ubuntu. I think this i because they're missing the point slightly and I need to make it quite clear! To quote TLE a little later on in this thread:
[B]
When referring to Enterprise edition I mean something that is distributed freely just as any other Ubuntu deriviate, but which is especially suited for use in large companies with an existing IT infrastructure.[/B] </edit>

Looking forward to responses!

---

### Post by StarsAndBars14 on 2006-12-26
Uhoh lol. . .

Nothing says "I want to be on the receiving end of a hate filled flame war" like Ubuntu Corporate Edition.

:P

/bombshelter

---

### Post by leftcase on 2006-12-26
> **StarsAndBars14 said:**
> Uhoh lol. . .

Nothing says "I want to be on the receiving end of a hate filled flame war" like Ubuntu Corporate Edition.

:P

/bombshelter

Why though?

At the end of the day thats a pretty sad opinion to have. You are making a lot of assumptions in that statement. I for instance work for a public service organisation. The cash we spend on MS products would be much better spend on serving the people we are supposed to look after. 

The big problem is, that there is nothing out there that we can use instead of say for instance Win XP. Why is there nothing out there? Perhaps because when suggested people make comments like "Nothing says "I want to be on the receiving end of a hate filled flame war" like Ubuntu Corporate Edition." I dunno....

Forgetting the title (heck, you can call it Ubuntu super edition for all I care) what's your problem with an enterprise ready desktop distro that'll just slide into place in an existing network and save an organisation (and remember, this could be a charity or public sector enterprise) money so it can spend it on helping people?

---

### Post by StarsAndBars14 on 2006-12-26
Hang around these forums for a while and you'll see what I meant with that post.

Ubuntu's user audience has every other Linux distro beat when it comes to anti-corporate, anti-capitalist, anti-this-and-that, super-extra-crazy-left-wing ranting.  So no, I didn't want to start a flame war with you.

But those things aside, I have no problem with what you're seeking to accomplish.  I think it would be a great help to companies that are getting off the ground and need to watch their expenditures.  And you're right about the charity thing as well. . .a whole lot of stuff could be bought/given/done with money that would ordinarily go toward XP corporate licensing for 100 or so computers.

---

### Post by Stemp on 2006-12-26
Very good idea Leftcase...

---

### Post by leftcase on 2006-12-26
> **StarsAndBars14 said:**
> Hang around these forums for a while and you'll see what I mean.

Ubuntu's user audience has every other Linux distro beat when it comes to anti-corporate, anti-capitalist, anti-this-and-that, super-extra-crazy-left-wing ranting.

You know what, I think you and I are using the word corporate in different ways.

To clarify, I'm using the word in this meaning...

Corporate, from the Latin corpor&#257;tus, past participle of corpor&#257;re, to make into a body, Belonging to an association of employers and employees ie: describing an organisation.

Any 'Ubuntu Corporate' distribution has nothing whatsoever to do with capitalism or politics. It refers to the creation of a distribution which is able to be deployed within an organisation with ease to replace current coporate MS technologies. You'll often find products in IT described as being a 'corporate' solution. This has no regard to political orientation.

Hope that's clear. Just so I don't get flamed of course :)

---

### Post by leftcase on 2006-12-26
Just a thought, but would Ubuntu Enterprise Edition more accurately describe the idea that I'm trying to get across?

---

### Post by Somenoob on 2006-12-26
Great idea leftcase. I would have no problem with such an edition, and would like to see it put into action.

---

### Post by Arisna on 2006-12-26
Maybe.  We'd probably end up calling it something like Busibuntu, though, to keep with the current naming convention. :P

I'm anti-lots-of-things myself, but I like this idea because it would speed the process of relegating Microsoft to obsolescence.

---

### Post by nalmeth on 2006-12-26
Do you mean like Impi Linux? 

Or do you mean a free-as-in-beer enterprise distro?

---

### Post by JNowka on 2006-12-26
This sounds like a good idea.  The basic plan sounds stable.  Though the people who decide to join in would have to be willing to put in alot of time.   If you ever wanted to get something like this going, I feel you would have to light the fire under peoples butts.  Initially you would have to direct everyone, and make the plans.  Make sure everyone follows through, etc.  Remember almost all the software you will need is in the repo's.  You will need to decide which packages best match those that run on your own  servers, then you will need to make, setup, install, and config scripts to setup everything right, so that it just works.  You will need to decide which GUI you will use, seeing that mostly these people would be Windows oriented I would suggest KDE.  Good idea, but I feel it would be alot of work to get it started.  And remember, when finially opened up for final release, it would have to incorporate the spirit of Ubuntu, and be made available for free.

---

### Post by nalmeth on 2006-12-26
And for the record, not all posters here denominate themselves left-of-center and are anti-coporate. You could say pretty much everyone is anti-monopolistic though.

Now that I re-read, I think you mean a freely available business-place distro? Not a bad idea.

Busy-buntu is a great name too!

---

### Post by leftcase on 2006-12-26
> **Arisna said:**
> Maybe.  We'd probably end up calling it something like Busibuntu, though, to keep with the current naming convention. :P

I'm anti-lots-of-things myself, but I like this idea because it would speed the process of relegating Microsoft to obsolescence.

Busibuntu... Hmmm I like the sound of that lol! 

In regard to replacing Microsoft desktop, indeed - If something like this existed it'd certainly put a dent in the MS desktop market if it was well made and easy to use!

---

### Post by leftcase on 2006-12-26
Just to make this absolutely clear. What I'm suggesting is a business ready distribution available at no cost that plugs into the current space in a corporate infrastructure occupied by Windows XP...

Also to make it clear, it isn't something I have built and ready for upload, but is indeed as suggested something which would require input and development. I'm suggesting a project concept and I'm willing to help in any way I can, but I'm not distro developer, I'm a systems admin so I can't do this alone.

---

### Post by scrooge_74 on 2006-12-26
> **leftcase said:**
> Just to make this absolutely clear. What I'm suggesting is a business ready distribution available at no cost that plugs into the current space in a corporate infrastructure occupied by Windows XP...

Also to make it clear, it isn't something I have built and ready for upload, but is indeed as suggested something which would require input and development. I'm suggesting a project concept and I'm willing to help in any way I can, but I'm not distro developer, I'm a systems admin so I can't do this alone.

If your place of work was more open to these kinds of ideas it would be a great testing place, for any large business oriented Ubuntu Edition. But from what you said, in order to test anything you will have to hide your test desktop in a far corner of the basement, under a staircase behind boxes or something like that.

From my experience if the top manager is not involve, understand the concepts and wants to do it.  You are very unlikely to be able to do much where you are currently employed

---

### Post by Burgundavia on 2006-12-27
There is absolutely no need to have a separate Enterprise edition. It might be shocking, but 95% of what "enterprise" users want is the same as home users. That being said, there are a bunch of things that Ubuntu needs to do to make it fit better in the large deployment space. Part of that project is being taken on by the Ubuntu Directory ([https://launchpad.net/people/ubuntu-directory](https://launchpad.net/people/ubuntu-directory)) team, but we need more people.

Corey

---

### Post by aktiwers on 2006-12-27
I love the Idea! I wish you luck leftcase, and hope you get some support. I dont have enough time, but if I had, I would help out with this!

Good Luck!
I will be watching the progress of this project..

---

### Post by 3rdalbum on 2006-12-27
I've always thought that if Ubuntu was going to be taken seriously as an enterprise distribution, it would HAVE to have out-of-the-box (or nearly) support for all the things you've listed, which are available in SLED. Good luck - if I didn't know nothing about the subject and wasn't already starting a distro project of my own, I'd probably put my hand up for your team!

---

### Post by leftcase on 2006-12-27
> **Burgundavia said:**
> There is absolutely no need to have a separate Enterprise edition. It might be shocking, but 95% of what "enterprise" users want is the same as home users.

Corey

Hi there, respectfully, I disagree...

I'm an enterprise user and I know that many many enterprise users want something that quite simply works out of the box. They do not want to fiddle around getting it working. They want to install it and have it work immediately!

Until Ubuntu does that it will not be taken seriously by enterprise in my honest opinion

---

### Post by kripkenstein on 2006-12-27
As mentioned in the original post, Xandros is a 'plug-in' solution for replacing Windows XP. They worked very hard on that. SUSE also has capabilities in that area. Ubuntu, on the other hand, is focusing on other areas - the next release will have 3D desktop effects, something the home/hobbyist user would want. So Canonical/Ubuntu just don't seem very interested in the Enterprise desktop market, as of yet (while they ARE interested in the Enterprise server market).

Perhaps in time this will change. But I doubt if this will happen without the drive coming from Mark Shuttleworth himself; for now, this is not present.

---

### Post by leftcase on 2006-12-27
> **kripkenstein said:**
> As mentioned in the original post, Xandros is a 'plug-in' solution for replacing Windows XP. They worked very hard on that. SUSE also has capabilities in that area. Ubuntu, on the other hand, is focusing on other areas - the next release will have 3D desktop effects, something the home/hobbyist user would want. So Canonical/Ubuntu just don't seem very interested in the Enterprise desktop market, as of yet (while they ARE interested in the Enterprise server market).

Perhaps in time this will change. But I doubt if this will happen without the drive coming from Mark Shuttleworth himself; for now, this is not present.

Fair enough - shame though!

With vista looming on the horizon I image that lots of enterprise organisations will be looking towards other options to replace their aging fleet of XP machines over the next few years. Ubuntu Enterprise could help fill that gap I reckon...

Chris

---

### Post by MrHorus on 2006-12-27
> **leftcase said:**
> Fair enough - shame though!

With vista looming on the horizon I image that lots of enterprise organisations will be looking towards other options to replace their aging fleet of XP machines over the next few years. Ubuntu Enterprise could help fill that gap I reckon...

Chris

You forget how slowly enterprise orginisations operate.

Mine (a finance company) is only JUST rolling out XP across our sites :)

---

### Post by leftcase on 2006-12-27
> **MrHorus said:**
> You forget how slowly enterprise orginisations operate.

Mine (a finance company) is only JUST rolling out XP across our sites :)

Youch lol :D

---

### Post by MrHorus on 2006-12-27
> **leftcase said:**
> Youch lol :D

Well it's a financial services company.

There are lots of bespoke applications that simply do not exist outside of these four walls and as a result, there is a LONG testing an acceptance procedure and XP isn't rolled out until they are sure that existing applications will work.

It's a pain but I suspect the same is true for any large enterprise.

---

### Post by Cows on 2006-12-27
Everything that everyone said above is true. I personally think that since Ubuntu is a free to use OS & Distro it should remain free if they were to make a Enterprise Server. I doubt that Ubuntu will keep the Enterprise Edition free since all the other Distros keep there Enterprise Editions at high prices. This is a very good idea of making a Enterprise Edition.

PS: I just switched from Win XP to Ubuntu =].

---

### Post by TLE on 2006-12-27
> **leftcase said:**
> Just to make this absolutely clear. What I'm suggesting is a business ready distribution available at no cost that plugs into the current space in a corporate infrastructure occupied by Windows XP...

Also to make it clear, it isn't something I have built and ready for upload, but is indeed as suggested something which would require input and development. I'm suggesting a project concept and I'm willing to help in any way I can, but I'm not distro developer, I'm a systems admin so I can't do this alone.

I don't think the problem is that the Ubuntu community is specially hostile, but I think that too many Linux users have tried to join a distribution, which promised to be free, only to experience that a differentiation is made later, and that you can only have the best version if you pay for it. Hence the hostility towards words like Coporate or Professional Edition. Just make sure you make it clear what it is that you mean, if you try to rally people for this project.

[INDENT]There is absolutely no need to have a separate Enterprise edition. It might be shocking, but 95% of what "enterprise" users want is the same as home users. That being said, there are a bunch of things that Ubuntu needs to do to make it fit better in the large deployment space. Part of that project is being taken on by the Ubuntu Directory ([https://launchpad.net/people/ubuntu-directory](https://launchpad.net/people/ubuntu-directory)) team, but we need more people.

Corey[/INDENT]

Maybe this could be accomplished by a package/program instead? A application that helps you install and configure everything for coporate use easily? If it is possible it would certainly save some work.

---

### Post by leftcase on 2006-12-27
> **TLE said:**
> 
Maybe this could be accomplished by a package/program instead? A application that helps you install and configure everything for coporate use easily? If it is possible it would certainly save some work.

Quite possibly, if the solution was a simple plugin that did the lot, that would certainly be interesting.

---

### Post by OffHand on 2006-12-27
I see your point but it is not a matter of enterprise or not. If an idea is good enough and high in demand it will be (or should be put in) put in Ubuntu. That way it will be available for both home users and cooperate bizz.

---

### Post by dasunst3r on 2006-12-27
The packages are out there, so the issue on hand, I suppose, is the bundling thereof.  There is a *server* edition out there, so we don't really need a "Corporate Edition," but rather expand on the server edition.

---

### Post by Cows on 2006-12-27
> **TLE said:**
> I don't think the problem is that the Ubuntu community is specially hostile, but I think that too many Linux users have tried to join a distribution, which promised to be free, only to experience that a differentiation is made later, and that you can only have the best version if you pay for it. Hence the hostility towards words like Coporate or Professional Edition. Just make sure you make it clear what it is that you mean, if you try to rally people for this project.

[INDENT]There is absolutely no need to have a separate Enterprise edition. It might be shocking, but 95% of what "enterprise" users want is the same as home users. That being said, there are a bunch of things that Ubuntu needs to do to make it fit better in the large deployment space. Part of that project is being taken on by the Ubuntu Directory ([https://launchpad.net/people/ubuntu-directory](https://launchpad.net/people/ubuntu-directory)) team, but we need more people.

Corey[/INDENT]

Maybe this could be accomplished by a package/program instead? A application that helps you install and configure everything for coporate use easily? If it is possible it would certainly save some work.

If that is true then don't you think that it would be easier to just edit the Ubuntu Desktop Edition and just save it as a new Ubuntu called Ubuntu Enterprise Edition.. it will still be free but this one will contain more stuff that relate to businesses. At the end you will have Ubuntu Desktop/Server/Enterprise Editions.

---

### Post by leftcase on 2006-12-27
After a PM from someone asking if help was needed on this 'project', I added a section to the wiki page for potential contributors. Although as of the moment there is no actual project in existence, it'd certainly help to see what skills are available so we can all decide whether its worth moving forward.

If you have a yearning desire to help make this idea a reality then feel free to add your details there.

[https://wiki.ubuntu.com/Enterprise](https://wiki.ubuntu.com/Enterprise)

---

### Post by OffHand on 2006-12-27
If you want this to succeed, it will have to be an official Canonical release with commercial support.

---

### Post by leftcase on 2006-12-27
> **OffHand said:**
> If you want this to succeed, it will have to be an official Canonical release with commercial support.

Fair comment, but at the mo this idea is only in the early stages of being thought about, never mind development.

Part of the consultation that occurs in these formative stages is to establish issues like the one you have raised. This is all highly dependent on what form getting Ubuntu into a enterprise ready situation takes.

If it consisted (for example - please don't read to much into this!) as an addon package which allowed you to configure dapper for active directory and exchange integration and set open office up to support MS Office file format, then support would be natively included in the distro ie dapper.

In the 'configuration script' scenario, support would be provided as usual as the packages used would likely be a part of Ubuntu in any-case.

---

### Post by 23meg on 2006-12-27
> **OffHand said:**
> If you want this to succeed, it will have to be an official Canonical release with commercial support.
And for it to be an official version, certain features in the regular Ubuntu would have to be taken out of it and moved in to the enterprise version. Technically, this would be quite an undertaking, and I don't see any benefit coming from such a split.

It would also cause some confusion, since Canonical has so far repeatedly emphasized that there will never be a separate enterprise version like Fedora / RHEL or OpenSUSE / SLED.

---

### Post by Hex_Mandos on 2006-12-27
Mark Shuttleworth has said repeatedly that there'll be no official Ubuntu "Enterprise Edition" or such. However, he bought [Impi Linux]("http://www.impi.org.za/"), and turned it into pretty much that. I think they even have a way for you to buy a customized edition of Impi to precisely suit your needs.

---

### Post by maddog39 on 2006-12-27
>  I've been looking at the Ubuntu projects here. Projects have been created for a range of needs, why not enterprise?
The answer is simple really. Ubuntu is an Open Source distro and the project heavily believes in the Open Source principles. They simply refuse to offer something that's proprietary.

---

### Post by TLE on 2006-12-27
I'll reiterate for leftcase. When he writes enterprise edition he means something that is distributed freely just as any other Ubuntu deriviate, but which is especially suited for use in large companies with an existing IT infrastructure.

To Leftcase. Maybe you should edit  the original post and explain this. It seems to be a reoccuring misunderstanding.

---

### Post by Cows on 2006-12-27
exactly what i said before. you can make a few tweaks to the desktop edition and make it a enterprise edition while still being free.

---

### Post by Swab on 2006-12-27
I've been thinking we need integration into existing Windows domains for a long time.
 
The installer should just ask if you want to join a domain, I've spent too long messing around getting Ubuntu to authenticate against AD, and function correctly as a domain member.  If all of this could be done out of the box it would go a long way to making Ubuntu a viable option for many organisations.

---

### Post by leftcase on 2006-12-27
Ooops double post.

---

### Post by leftcase on 2006-12-27
> **TLE said:**
> 
To Leftcase. Maybe you should edit  the original post and explain this. It seems to be a reoccuring misunderstanding.

I have done that mate :D

---

### Post by r71cuda on 2007-01-09
> **Swab said:**
> I've been thinking we need integration into existing Windows domains for a long time.
 
The installer should just ask if you want to join a domain, I've spent too long messing around getting Ubuntu to authenticate against AD, and function correctly as a domain member.  If all of this could be done out of the box it would go a long way to making Ubuntu a viable option for many organisations.

Hi everyone, newbie here, after reading this entire thread, I have to agree with this one. I am an IT manager for a local government and we are a complete Windows shop, with 2003 server, 2003 Exchange, Windows XP Pro & Office 2003. I want to try and move atleast some of my users if not all eventually off of Microsoft's products to a good Linux alternative and I think what is being asked throughout this thread is to modify the EXISTING desktop version to incorporate the options of joining a Windows domain and so forth. I by no means know anything about the Linux product but so far I have not found one I can install out of the box and configure easily to communicate with my Windows network. To be able to install a Linux desktop out of the box and have it work with a Windows domain LAN & Exchange would be HUGE!

---

### Post by kripkenstein on 2007-01-09
> **r71cuda said:**
> Hi everyone, newbie here, after reading this entire thread, I have to agree with this one. I am an IT manager for a local government and we are a complete Windows shop, with 2003 server, 2003 Exchange, Windows XP Pro & Office 2003. I want to try and move atleast some of my users if not all eventually off of Microsoft's products to a good Linux alternative and I think what is being asked throughout this thread is to modify the EXISTING desktop version to incorporate the options of joining a Windows domain and so forth. I by no means know anything about the Linux product but so far I have not found one I can install out of the box and configure easily to communicate with my Windows network. To be able to install a Linux desktop out of the box and have it work with a Windows domain LAN & Exchange would be HUGE!

Few Linux distros can do this - I believe the only ones are Xandros and SUSE. While neither is free of cost, they are much cheaper than Windows, so you may want to give them a try. Both have free download trial versions, so you can just check and see how well it integrates into your existing Windows network.

---

### Post by r71cuda on 2007-01-09
Yeah, I have the SUSE SLED 10 version and still do not have it setup on our network (although I have not spent a ton of time with it either), but out of the box it does not appear to automatically integrate or ask to integrate with a Windows domain.

---

### Post by kripkenstein on 2007-01-09
> **r71cuda said:**
> Yeah, I have the SUSE SLED 10 version and still do not have it setup on our network (although I have not spent a ton of time with it either), but out of the box it does not appear to automatically integrate or ask to integrate with a Windows domain.

Well, Xandros's latest release was supposed to do that very easily - so they say, at least. It does look slick but I don't have a Windows network to test it on. So perhaps give that a shot, it might work.

---

### Post by degel3030 on 2009-10-02
Old post, I know, but this is something that is needed and our company certainly hopes something like this will become a reality. Here is a link to help [https://help.ubuntu.com/community/CorporateUbuntu](https://help.ubuntu.com/community/CorporateUbuntu) but a full distro would be fantastic, heres hoping for 10.04 LTS !!!!!

---

### Post by oasit on 2012-11-01
[FONT=Vorgabe feste Breite,Courier New,Courier,Feste Breite][SIZE=2](this [SIZE=2]announcement is from Thorsten R[SIZE=2]hau[/SIZE][/SIZE])
[/SIZE][/FONT]
At UDS-R in Copenhagen, a group of people met twice  to discuss use of Ubuntu inside the enterprise. This group decided to  take a three-pronged approach to moving forward. 
[LIST]
[*]We have started a new team on Launchpad for people interested in this topic. You'll find that [on the Launchpad site.]("https://launchpad.net/%7Eenterprise-ubuntu") Please go to the team page, log in, and join!
[*]We will be using the mailing list on the Launchpad page to carry on our discussions. The address of the mailing list is [EMAIL="enterprise-ubuntu@lists.launchpad.net"]enterprise-ubuntu@lists.launchpad.net[/EMAIL]
[*]We will be working [on the existing wiki page]("http://https://wiki.ubuntu.com/Enterprise") to make the information current and to grow the information there.
[/LIST]


Regards,
Michael

---

### Post by howefield on 2012-11-01
Old thread back to sleep.,

Feel free to start afresh.

---

