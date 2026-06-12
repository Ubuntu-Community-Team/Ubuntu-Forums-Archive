---
title: "Can new Ubuntu8.10 connect to MS Exchange 2007"
date: 2008-10-05
forum: Server Platforms
---

### Post by tanveer on 2008-10-05
HI all,

I haven't found any thing yet which will enable ubuntu connect with Exchange 2007. Is the new version of ubuntu 8.10 have that option in evolution to connect with exchange 2007?

thanks in advance.

---

### Post by cariboo on 2008-10-06
Apparently openchange is available in the repositories.

Jim

---

### Post by tanveer on 2008-10-06
Hi thanks for reply.
Does Openchange is open source exchange alternative and I have to make a dedicated one with openchange so that it can communicate with MS exchange and users go through by it to MS Exchange?

---

### Post by angel12 on 2008-10-07
do what huh?

openchange is in the repositories, but not the evolution plugin, they are waiting on a re-write of the evolution license for its compatibility to gpl-v3 to release a binary.

---

### Post by jbg7474 on 2008-10-10
Where can one find information about that progress?  Last I saw was here: [http://johnnyjacob.wordpress.com/2008/07/11/evolution-exchange-2007-mapi-provider-changes-in-schedule-and-more/](http://johnnyjacob.wordpress.com/2008/07/11/evolution-exchange-2007-mapi-provider-changes-in-schedule-and-more/).  That site seems to indicate that the license issues are a thing of the past.  Did something new come up, or is it just a matter of doing the rewrite?

---

### Post by RichTJ99 on 2008-10-11
I would also be interested in finding out how to make exchange 2007 work with Ubuntu.

---

### Post by cariboo on 2008-10-11
You could have a look here:

[http://www.gnome.org/projects/evolution/](http://www.gnome.org/projects/evolution/)

to find out what the progress is.

Jim

---

### Post by Ghilteras on 2008-10-25
> **cariboo907 said:**
> You could have a look here:

[http://www.gnome.org/projects/evolution/](http://www.gnome.org/projects/evolution/)

to find out what the progress is.

Jim

nothing there that i can see tells or defy that evolution will be able to use openchange in intrepid

---

### Post by HermanAB on 2008-10-25
Exchange servers usually have IMAP enabled, so any mail client will work.  However, if you want to use shared calendars, then you need the Binari Connector or some such to make it work.

---

### Post by braverock on 2008-10-31
There is a branch of the Evolution code that supports Exchange 2007, but development on that branch seems to be slow to non-existent.  If you have Exchange 2003 or earlier, the evolution-exchange packages will work, but if you have Evolution 2007, it seems that you would need to download and compile the evolution-exchange code from SVN.

Regards,

  - Brian

---

### Post by koruptid on 2008-10-31
The current (non-free) guaranteed to work solution is to install Office 2007 via Crossover Office (by a company called "CodeWeavers")

unfortunately Microsoft interoperability is a weak point in many places due to Microsoft's notoriously poor documentation and general hostility toward FOSS.

---

### Post by jmccartie on 2008-10-31
> **braverock said:**
> but if you have Exchange 2007, it seems that you would need to download and compile the evolution-exchange code from SVN.


Any chance there's a walkthrough on this?  (I'm worried about breaking my existing install of Evolution) </noob>

---

### Post by shrinkpad on 2009-01-21
Bumping this up again....

Anyone have any later info on the status of the openchange evo plugin?

The openchange.org sites news page does not say to much and the only files found in the rep's of intrepid are;

openchangeclient - Command-line client for the MAPI (Exchange/Outlook) protocol
openchangeproxy - Experimental MAPI (Exchange/Outlook) proxy
openchangeserver - Experimental MAPI (Exchange/Outlook) server

But no evolution plugin?

---

### Post by Ghilteras on 2009-02-04
I too would like to know why there still isnt any evo pluging for exchange 2007 in the repositories.. 

was it postponed till Jaunty?

---

### Post by ncubede on 2009-02-04
I'd be very surprised if this works well.  Outlook 2007 is not awarded a Silver medal in the Codeweavers compatibility list, so let's better not suggest this. Outlook 2003/2000 work mostly. See

[http://www.codeweavers.com/compatibility/browse/name/?letter=o;](http://www.codeweavers.com/compatibility/browse/name/?letter=o;)

> **koruptid said:**
> The current (non-free) guaranteed to work solution is to install Office 2007 via Crossover Office (by a company called "CodeWeavers")

unfortunately Microsoft interoperability is a weak point in many places due to Microsoft's notoriously poor documentation and general hostility toward FOSS.

---

### Post by ncubede on 2009-02-04
There is no chance until GNOME evolution 2.26, and even then someone would have to complete the code first. See:
[http://mail.gnome.org/archives/desktop-devel-list/2008-November/msg00221.html](http://mail.gnome.org/archives/desktop-devel-list/2008-November/msg00221.html)

> **Ghilteras said:**
> I too would like to know why there still isnt any evo pluging for exchange 2007 in the repositories.. 

was it postponed till Jaunty?

---

### Post by HDave on 2009-02-06
I been following this closely for over a year.  The openchange client project (the also have a server) seems to be in pretty good shape.

The evolution MAPI plug-in that is built on the openchange client is still pretty rough.  It is still on Gnome's roadmap for 2.26 due to be included in Jaunty come April...but they have a ton of bugs to fix.  In my opinion, it will not surprise me one little bit if this is delayed until Ubuntu 9.10.

Unfortunately for us, the nightly builds of the evolution MAPI plug-in are only for Red Hat and Suse, not Ubuntu 8.10.  I found a package for Debian somebody is regularly building, but the dependencies cannot be fulfilled on Intrepid...too many conflicts.  Using alien on the RPM also failed.

Bottom line, until some brave sole figures out how to compile on intrepid, we have no way to really take it for a test drive.

---

### Post by inphektion on 2009-02-06
Well here's for hoping something ends up in jaunty that at least pretends to work...
Crossover office doesn't for outlook.  Basically unuseable.  
The best solution right now is running a complete windows vm solely for outlook 2007.  And thats a horrible solution yet it IS the best one right now.  

The openchange looks great but we need the plugin done for evolution.

---

### Post by RichTJ99 on 2009-02-06
Out of curiousity, have you tried outlook 2003 with Crossover?  It works very well.  

I dont really like Outlook 2007 on any machine as it is slllloooooow as heck. It has nice features but it takes forever to get from one email to the next, Outlook 2003 works great & works with Exchange 2007.  

Im interested in why your using Outlook 2007 (or just preference)?

---

### Post by HDave on 2009-02-06
I've been using Outlook 2003 with crossover for the past 9 months...its been working like a champ provided:

1) you also install IE6 in the bottle
2) you don't use MS word as your email editor

Two easy work-arounds to the instability problems.  Really works pretty well.

Edit:  I connect to an exchange server 2007 backend FWIW

---

### Post by inphektion on 2009-02-06
i'm using outlook 2007 for a few reasons:
1. you can have exchange 2007 NOT play nice with outlook 2003 as far as the public contacts and offline address book are concerned as 2007 handled these in a different way.  You can have exchange 2007 retain backwards compatibility with 2003 but since all our users are windows we did not maintain that compatibilty.
2. in exchange 2007 we use unified messaging.  The unified messaging options and features you get in outlook 2007 (play on phone, confg fwd, vm access, etc) simply don't exist in outlook 2003.
3.  We have a mail retention policy that uses managed email folders.  These don't work at all on outlook 2003.
4.  Personally I like the auto preview of attachements in outlook 2007 and the to-do bar, I use color categories and OOF none of these features existed in outlook 2003.

So no, I don't want to go back to outlook 2003, I'd continue using 2007 in a VM before I did that.  I need a win vm anyway so it isn't a huge problem i'd just prefer to have the evolution plug-in so I had another good way to check mail in case i didn't already have the vm booted up.

---

### Post by aaroncirillo on 2009-02-11
I built a system in a chroot. I compiled evolution 2.25 and all of it's dependencies. I built libmapi and evolution-mapi. It works great. I can connect to my company's exchange 2007 servers.

---

### Post by jbg7474 on 2009-02-12
> **aaroncirillo said:**
> I built a system in a chroot. I compiled evolution 2.25 and all of it's dependencies. I built libmapi and evolution-mapi. It works great. I can connect to my company's exchange 2007 servers.

This is huge.  Let me see if I understand you.  You built a version of evolution that connects with exchange 2007 and works well?  And this is running on Ubuntu 8.10?

Is it possible to get this worked into a repository somewhere or to post directions so others can do it?

---

### Post by johnnylavah on 2009-03-05
> **jbg7474 said:**
> This is huge.  Let me see if I understand you.  You built a version of evolution that connects with exchange 2007 and works well?  And this is running on Ubuntu 8.10?

Is it possible to get this worked into a repository somewhere or to post directions so others can do it?

did you get it working?

---

### Post by tanveer on 2009-03-05
jbg7474, 

Please let us all know how you did it so that others can get help from you on this.

---

### Post by jbg7474 on 2009-03-09
> **johnnylavah said:**
> did you get it working?

No, I never saw any response from aaroncirillo, whom I was quoting.  He was the one who said he got it working--I was asking him to confirm and help the rest of us!

---

### Post by tanveer on 2009-03-09
Sorry my mistake. 
But the question is still on the table. 
Does 9.04 will come up with some solutions of it?

---

### Post by Submatrix on 2009-03-09
> **jbg7474 said:**
> This is huge.  Let me see if I understand you.  You built a version of evolution that connects with exchange 2007 and works well?  And this is running on Ubuntu 8.10?

Is it possible to get this worked into a repository somewhere or to post directions so others can do it?

Seems like he may have followed this guide:

[http://www.go-evolution.org/Compiling_Evolution_from_SVN](http://www.go-evolution.org/Compiling_Evolution_from_SVN)

Which I don't have the courage to try this evening. What do you think?

---

### Post by jmarks on 2009-03-11
I have been following this thread with great interest.
However, this:
> Seems like he may have followed this guide:

[http://www.go-evolution.org/Compilin...ution_from_SVN]("http://www.go-evolution.org/Compiling_Evolution_from_SVN")
  looks really hard, because a) the how-to document is not finished and b) interpreting error messages during the compile is not for the faint-of-heart.
It is also unclear from aaroncirillo's provocative post 4 weeks ago: 
> I built a system in a chroot. I compiled evolution 2.25 and all of it's dependencies. I built libmapi and evolution-mapi. It works great. I can connect to my company's exchange 2007 servers.       whether s/he followed this guide.
I hope more experienced people with development systems will give this a whirl and feed back to the rest of us.

---

### Post by HDave on 2009-03-11
As soon as a Jaunty alpha or beta is using Gnome 2.26, then I think we Ubuntu users will get all of this handed to us on a silver platter.

Exchange 2007 connectivity via MAPI on Evolution is slated for Gnome 2.26.

---

### Post by doudar on 2009-03-12
> **HDave said:**
> As soon as a Jaunty alpha or beta is using Gnome 2.26, then I think we Ubuntu users will get all of this handed to us on a silver platter.

Exchange 2007 connectivity via MAPI on Evolution is slated for Gnome 2.26.

I hope so. My laptop is going to melt if I have to keep an XP VM running much longer just for outlook!

---

### Post by johnnylavah on 2009-03-13
> **doudar said:**
> I hope so. My laptop is going to melt if I have to keep an XP VM running much longer just for outlook!

i am running outlook 2003 and connecting to a 2007 exchange server through [WiNE]("http://www.winehq.org/")

---

### Post by HDave on 2009-03-13
I'v been using both wine (crossover) and a VM for the past 18 months...neither is really satisfactory....

Crossover is only semi-stable....and I can't get VMWare to bridge to my dial-up mobile EVDO wireless.... (sigh) :(

---

### Post by Brazen on 2009-03-13
Yeah, Jaunty is going to include MAPI support for Evolution.  I would suggest you try out the latest Alpha of Jaunty to see if you can connect to Exchange 2007 and file any bugs you encounter so they can get fixed before the final release.

---

### Post by jmarks on 2009-03-13
> I'v been using both wine (crossover) and a VM for the past 18 months...neither is really satisfactory.I have been trying to run Outlook 2003 to connect to my exchange server 2007 under crossover and cannot get it to work. I have created a win2000 bottle, installed outlook 2003 with sp3, and installed IE 6 as suggested. I have reconfigured the win2000 bottle as winXP in order to enable RDP. I have set up my email account using http.
I am authenticating (as instructed by my University) to be mutually authenticated by msstd:
Despite all this, I cannot get authenticated.
I am reduced to using our web interface which is unsatisfactory.
I will try virtualbox next, but it seems crazy that I can't get outlook 2003 to connect at all.

Any suggestions would be much appreciated, either for CrossOver or for VirtualBox.
thanks to all.

---

### Post by doudar on 2009-03-22
Any updates from somebody testing this in Jaunty?

---

### Post by jbg7474 on 2009-03-23
> **doudar said:**
> Any updates from somebody testing this in Jaunty?

Alright, I just updated to Jaunty Alpha 6 from Intrepid.  The install was not bump free--python did not install correctly, so I don't know if that had an effect on anything else.  Opened Evolution, clicked on Help, About, and it reported version 2.26.

Joy!  However, when I went to do an exchange email account, I got the same old error about needing to be an exchange 2003 server.  I didn't see any MAPI or openchange options.  Perhaps I need to load a plugin or something?

Disappointed.

Edit: Discovered that I had to manually select the evolution-mapi package in Synaptic.  Installed that and Exchange MAPI is now available as a server type (after restarting Evolution).  Of course now I'm having authentication problems--I'll need to try this again at work where I'm on the domain.  I may also have this bug: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/333855](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/333855).

It would appear, though, that Jaunty Alpha 6 has what you need to connect to Exchange 2007, at least in theory.

Edit2: Just updated Jaunty to Beta.  Evolution is still crashing when I attempt to create a MAPI account.  :(

Edit3: In case anyone is paying attention, the crashing bug is still not fixed.  Here is a link to the best bug report: [https://bugs.launchpad.net/ubuntu/+source/evolution-mapi/+bug/338982](https://bugs.launchpad.net/ubuntu/+source/evolution-mapi/+bug/338982)

---

### Post by jbg7474 on 2009-04-08
Partial fix--it appears that if you input the IP address of the Exchange server rather than the server name, it works!

I now have access to my Exchange 2007 account on Jaunty beta.

---

### Post by oshndoc on 2009-04-08
> **jbg7474 said:**
> Partial fix--it appears that if you input the IP address of the Exchange server rather than the server name, it works!

I now have access to my Exchange 2007 account on Jaunty beta.

I am paying attention and I love your last post. At last there is light a the horizon. Now to the first step. Change to Jaunty, or should I wait until 4/23 for the official release?

---

### Post by jbg7474 on 2009-04-08
> **oshndoc said:**
> I am paying attention and I love your last post. At last there is light a the horizon. Now to the first step. Change to Jaunty, or should I wait until 4/23 for the official release?

Tough call, however, Evolution is crashing like crazy on me now that I am on the Exchange server.  Opening Calendars kills it pretty quickly.  I haven't dug up the bug report for that yet.  I might wait a little longer if I were you.  I hope that some more bugs get fixed in evolution.

There are still a few other weird things with Jaunty, and I am getting 100MB or more of updates nearly every day.  But I think I am a little happier with Jaunty than I was with Intrepid.  Seems to work out a little better with my machine.  Upgrading to Intrepid from Hardy was mucho painful.

---

### Post by jbg7474 on 2009-04-09
Looks like the best information is available on this bug report, which also has a link to the Gnome bug report: [https://bugs.launchpad.net/ubuntu/+source/evolution-mapi/+bug/338982](https://bugs.launchpad.net/ubuntu/+source/evolution-mapi/+bug/338982)

I can get my mail, but as noted in the comment from Steve Carl, reply doesn't seem to work because the GAL is not working yet.

Calendar is also not working at all.  My tasks show up, but the notes show up as separate tasks with a cryptic name so there's no way to match them up to their task.  My notes show up, but I haven't tested whether I can enter new notes or not.  Contacts show up, but Evolution goes into an endless search that eventually gobbles up all memory.

In short, it's getting close, but we're not there yet.  Not sure whether all this will be fixed before 4/23.

---

### Post by rabside on 2009-06-09
any news abount exchange integration?

---

### Post by Xirtambus on 2009-08-25
I can now connect to my Exchange 2007 server through thunderbird with davmail. It works in the same way the first plugin did, through OWA. :KS

---

### Post by pavelchjen on 2009-09-02
Yes. would be interesting

---

