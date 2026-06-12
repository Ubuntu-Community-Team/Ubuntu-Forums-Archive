---
title: "Solaris vs ubuntu"
date: 2009-11-24
forum: The Cafe
---

### Post by pythonscript on 2009-11-24
What's your opinion on openSolaris? I'm hoping to run it on my laptop (to test out) but I just want to know what people think. Of course, if you see any blatant hardware problems I might run into... I'd appreciate those as well. Thanks!

---

### Post by jrusso2 on 2009-11-24
It will be nice if they can ever get as good as hardware and software support as Linux.

---

### Post by Irihapeti on 2009-11-24
I've never done anything more than run it from a liveCD, so can't really comment. However, I did find an online hardware compatibility checker which looks interesting. More details here: [http://www.sun.com/bigadmin/hcl/hcts/device_detect.jsp](http://www.sun.com/bigadmin/hcl/hcts/device_detect.jsp)

---

### Post by HermanAB on 2009-11-24
If Solaris works on your laptop then it will be fine, since it is just Gnome with a different scheduler underneath it.  However, that is a very big if and Solaris very likely won't work properly.

---

### Post by shadylookin on 2009-11-24
I thought it used too many resources and the repos were definitely lacking. It had a nice looking default look to it, but nothing to write home about.

---

### Post by angryfirelord on 2009-11-24
Right now it's still a bit behind, but it could become a serious contender once hardware support picks up and the package management gets better.

---

### Post by kpholmes on 2009-11-24
i have opensolaris installed on my laptop and i like it alot. most things on the command line still work coming from the linux side, but if you dont use the cli on solaris then you wont notice a difference. anyways i like it alot

---

### Post by jowilkin on 2009-11-24
I run it on my fileserver so that I can use ZFS as the filesystem and I often wish I had gone with Linux with a different filesystem or ZFS on BSD.

The repos are extremely lacking and there are several different package managers with their own different repos. This is getting somewhat better as they seem to be standardizing somewhat around IPS.  Compared to most linux distros though, package management is a mess.

The other problem is that even though programs that can't be found on the repos should compile on solaris, they don't.  There are just some minor differences between solaris and linux that cause compiles to break and require patching.

Hardware compatibility is also lacking, try out the live cd to see if your laptop is supported.  I haven't tried solaris on a laptop, so not sure how that will work out.

Over all, I would advise against OpenSolaris at this point in time for annything other than a server with known to work hardware that will run applications that have already been packaged for OpenSolaris.

---

### Post by mivo on 2009-11-24
If anyone wants to try it, they have a Live CD at opensolaris.org and will also mail you a free CD if your bandwidth is limited or you want a real CD for another reason.

---

### Post by MasterNetra on 2009-11-24
Last time I tried it, the live CD didn't even have a gui option to shutdown or logout just the install lol. Apparently from what I heard Ubuntu > Solaris still.

---

### Post by KiraLexi on 2009-11-24
Solaris is cool if you're running a server (or a SPARC workstation) but running it as a generic x86 desktop is pretty uncomfortable. there are a lot of really unfinished bits, especially when it comes to packaging, and hardware support is **very** lacking.

Nexenta is coming along well though. I think in the long run that will be the primary variant of Solaris on the x86 desktop.

---

### Post by SunnyRabbiera on 2009-11-25
Solaris looks good but unfortunately I think it will die out soon, Oracle has not done anything good for no one.

---

### Post by joey-elijah on 2009-11-25
I used to have it installed in a VB.... then i had it installed on my EeePC... i like opensolaris... sorta.

BUT OMG DOES IT BOOT SLOW.

---

### Post by franklinchang on 2009-11-25
someone help?
another question
my ubuntu can't read NAS files?version 8.04:popcorn::popcorn:

---

### Post by slakkie on 2009-11-25
We run Solaris at work (server installs only). Works like a charm. Be sure to install pkg-get: [http://www.bolthole.com/solaris/pkg-get.html](http://www.bolthole.com/solaris/pkg-get.html)

---

### Post by jimi_hendrix on 2009-11-25
> **jrusso2 said:**
> It will be nice if they can ever get as good as hardware and software support as Linux.

if i recall, it is source code compatible with linux.

---

### Post by handy on 2009-11-25
I thought I had better put this one in here for the benefit of gn2:

Whatever you do, DO _***NOT***_ TRY ARCH!

---

### Post by kk0sse54 on 2009-11-25
I've tried OpenSolaris several times and while overall it's quite nice, hardware support is lacking and the software selection available through their repos is quite small. Besides with ZFS available for FreeBSd I didn't see any point in keeping it around.

---

### Post by jespdj on 2009-11-25
> **joey-elijah said:**
> I used to have it installed in a VB.... then i had it installed on my EeePC... i like opensolaris... sorta.

BUT OMG DOES IT BOOT SLOW.
And it not only boots slow on a slow netbook like an Eee PC, it also boots slow on any other computer.

I don't see why anyone would want to use OpenSolaris, unless you have some very specific piece of software or hardware that you'd need it for. For general use on a desktop or laptop, OpenSolaris does not have any advantages above Linux. Its hardware support is much worse than on Linux. It runs the GNOME desktop, so not a real difference with for example Ubuntu there.

---

### Post by mivo on 2009-11-25
[QUOTE=jespdj;8384463I don't see why anyone would want to use OpenSolaris ... It runs the GNOME desktop, so not a real difference with for example Ubuntu there.[/QUOTE]

For increasing one's experience and knowledge. The Gnome desktop is just an interface, and what matters is what beneath it. I don't use it actively, but I have played with it, and thought it was an interesting experience. It fully supports my main desktop's hardware (all relatively new and state of the art components), though it doesn't have a driver for my netbook's wireless adapter. Then again, no Linux distro seems to have one that works OOTB without rolling a kernel either. (Not looking into this before was one of my bigger mistakes, though I'm okay with XP on it, but it's still a nagging issue.)

---

### Post by Metallion on 2009-11-25
> **SunnyRabbiera said:**
> Solaris looks good but unfortunately I think it will die out soon, Oracle has not done anything good for no one.

Amen to that!

Ex-Oracle employee here who recently and happily handed in his resignation after seeing how they work.

---

### Post by jrusso2 on 2009-11-25
> **SunnyRabbiera said:**
> Solaris looks good but unfortunately I think it will die out soon, Oracle has not done anything good for no one.

IF they let Solaris die what would their sparc hardware run?  I don't see this happening.  Solaris is the number one OS for running huge corporate databases with Oracle.

---

### Post by toupeiro on 2009-11-25
> **jrusso2 said:**
> IF they let Solaris die what would their sparc hardware run?  I don't see this happening.  Solaris is the number one OS for running huge corporate databases with Oracle.

They're already showing that they have no interest in further developing SPARC.  Oracle will destroy the sun microsystems portfolio..

As for those who say OpenSolaris is gnome with a different scheduler ... wow... its quite a bit more than that.

So a real solaris versus ubuntu debate needs a little more ground rules.  On the desktop, I think ubuntu is the clear winner.  I also run opensolaris, and I really, really enjoy it.  I've been debating whether or not I will run it as my main OS rather than Lucid when Lucid is available.  If you want to start comparing server platforms, they are much, much closer in comparison, but I would say for the availability of ZFS, DTrace and many other tools that Solaris has that linux never will, Solaris is a better Server OS.  All those same tools are in Desktop OS as well, but yes, the hardware support for Open Solaris Desktop is lacking in comparison to ubuntu, which has had more desktop development, quite a bit longer, than OpenSolaris.  I beg to say, however, that OpenSolaris was never designed with netbooks in mind, while ubuntu completely spun a new netbook version, so people, you need to be realistic when you make your comparisons..

---

### Post by blur xc on 2009-11-25
What does OpenSolaris offer that Linux does not?  I mean, why would I want to go w/ them instead of a popular Linux distro?

Thanks,
BM

---

### Post by RiceMonster on 2009-11-25
> **blur xc said:**
> What does OpenSolaris offer that Linux does not?  I mean, why would I want to go w/ them instead of a popular Linux distro?

Thanks,
BM

Look at the post above yours

---

### Post by blur xc on 2009-11-25
> **RiceMonster said:**
> Look at the post above yours

Yup, he must have been writing his about the same time I was writng mine and just beat me...

BM

---

### Post by toupeiro on 2009-11-25
> **blur xc said:**
> What does OpenSolaris offer that Linux does not?  I mean, why would I want to go w/ them instead of a popular Linux distro?

Thanks,
BM

Its all about choice and alternatives.  You run Linux, or open solaris because you want to, not because you have to.  Your reasons for wanting to should always be your own.  Curiosity, for some, is a good enough reason on its own.  It doesn't matter why we tell you you should want to run Linux or Opensolaris.  If you're curious about something, you have the freedom without cost to experiment.

---

### Post by #11u-max on 2009-11-25
> **jrusso2 said:**
> It will be nice if they can ever get as good as hardware and software support as Linux.
*laughs* if only you knew...

to the OP, solaris is a more hands on experience that is more fufilling once the system has the necessary tools.

---

### Post by gn2 on 2009-11-25
> **handy said:**
> I thought I had better put this one in here for the benefit of gn2:

Whatever you do, DO _***NOT***_ TRY ARCH!

Last paragraph: [http://ubuntuforums.org/showpost.php?p=8379229&postcount=105](http://ubuntuforums.org/showpost.php?p=8379229&postcount=105)

Back on topic, if Solaris has all the applications you need and will run on your hardware it is superb.

---

### Post by Zoot7 on 2009-11-25
I had to use Sun Solaris in my last job temporarily. It's not much of an issue get used to if you know your way around Linux.
The major deficit for it I think is Hardware and Software support.

---

### Post by toupeiro on 2009-11-25
> **Zoot7 said:**
> I had to use Sun Solaris in my last job temporarily. It's not much of an issue get used to if you know your way around Linux.
The major deficit for it I think is Hardware and Software support.

Sun solaris (8, 9, and even 10) and Opensolaris are pretty different...

---

### Post by handy on 2009-11-25
> **gn2 said:**
> Last paragraph: [http://ubuntuforums.org/showpost.php?p=8379229&postcount=105](http://ubuntuforums.org/showpost.php?p=8379229&postcount=105)

Thank you for that gn2. :)

I have been away for 10 days & so haven't been able to get at a computer as often as usual, so I had missed the post you linked to above. (Apart from the fact that it was hidden from me anyway.)

I can now happily remove you from my ignore list, as I often find good value in your input here in the forum, & I have been missing out somewhat for a while.

All the best. ;)

---

### Post by NoaHall on 2009-11-25
Why are you comparing Solaris VS Ubuntu anyway? It would be better to have Solaris VS GNU/Linux.

---

### Post by Velnias on 2009-11-26
This is incomparable!

OpenSolaris is only partly free - for security and all updates you need to pay min $324 per year.

OpenSolaris is abandonware - it is testing platform for next Solaris and there is no such think as "OpenSolaris" in Oracle's future.

OpenSolaris has great Solaris server features, but as desktop is like Linux was 10 years ago - you can have issues with sound, screen resolution, flash, apps not working etc...

---

### Post by toupeiro on 2009-11-26
> **Velnias said:**
> This is incomparable!

OpenSolaris is only partly free - for security and all updates you need to pay min $324 per year.

OpenSolaris is abandonware - it is testing platform for next Solaris and there is no such think as "OpenSolaris" in Oracle's future.



Oh please!  It's as much abandonware as Fedora or OpenSUSE.  or as much as Karmic is to the next LTS release.  And I've been running it since it was released and never paid a cent for a security update or an update otherwise.. Before this thread goes 100% the way of a bad tabloid, lets try to focus on reality a bit.  This is as bad as people who hear the word linux and think its a windows virus..

---

### Post by Zoot7 on 2009-11-26
> **toupeiro said:**
> Sun solaris (8, 9, and even 10) and Opensolaris are pretty different...
Oh. :) Well if I'm honest I've never used Opensolaris.

---

### Post by Velnias on 2009-11-26
Oh, sorry, if it hurts you. 
Lets be clear - how you get security updates for OpenSolaris 2008.11 or OpenSolaris 2009.6 ?
And any written or spoken fact, that Oracle will continue OpenSolaris development ?

PS please share information may you have, to stop trolls! and sorry for my English.

---

### Post by toupeiro on 2009-11-26
> **Velnias said:**
> Oh, sorry, if it hurts you. 
Lets be clear - how you get security updates for OpenSolaris 2008.11 or OpenSolaris 2009.6 ?
And any written or spoken fact, that Oracle will continue OpenSolaris development ?

PS please share information may you have, to stop trolls! and sorry for my English.

pkg image-update?  This will tell me if I have any pre-requisites to update individually before I can do a full image update.  Also, the regular package manager will do any security updates for software I have installed.

Are you talking about the OpenSolaris KERNEL??  If you want the absolute latest development updates, then you can freely add the development opensolaris repositories.  You seem to think that because opensolaris has a subscription plan that it MUST mean they are keeping their most critical security vulnerability updates from you, they are not.  Basically what your support means, is that they will give you access to development repositories for security patches that range from low to critical, and give you a support contract with them.  Guess what, Redhat, SuSE, and even Canonical, have the exact same contracts.  If you're running ubuntu, get a broken patch and call canonical, you think they wouldn't charge you for that?   

Is solaris less open than Linux about their security updates?  Absolutely! they limit the majority of their non-critical patches to security rollups which you can get with that image-update command when they are available. However, give me one example where a dangerous opensolaris kernel exploit was discovered and it impacted the entire opensolaris community because Sun wouldn't release the patch to those who didn't pay for it.  Let me save you the effort, it never happened!  Even on solaris 10 systems, they provide security rollups without having to pay for them.  I just recently experienced this with a solaris 10 system I support at work.  Look at the kernel ubuntu is running right now, now look at the latest kernel available on kernel.org..  What do you know, they aren't the same either..  Again, be realistic.  No major distro that implies its stable runs on the latest kernel available patch to current.  Just because Opensolaris isn't as open as linux doesn't mean its riddled with security holes that can't be fixed unless you pay for it.

The solaris kernel and the linux kernel are two very different beasts.  If you want to see every waking event of the development of a kernel because you don't trust Sun, maybe opensolaris isn't for you.  Windows is DEFINITELY not for you. :P

T

OpenSolaris update process in 2009.06:

```
root@opensolaris:~# pkg image-update -v
WARNING: pkg(5) appears to be out of date, and should be updated before
running image-update.

Please update pkg(5) using 'pfexec pkg install SUNWipkg' and then retry
the image-update.
root@opensolaris:~# pkg install SUNWipkg
DOWNLOAD                                    PKGS       FILES     XFER (MB)
Completed                                    3/3     113/113     0.49/0.49 

PHASE                                        ACTIONS
Removal Phase                                  28/28 
Install Phase                                  12/12
Update Phase                                 227/227 
root@opensolaris:~# pkg image-update -v
Creating Plan / Before evaluation:      
UNEVALUATED:
+pkg:/entire@0.5.11,5.11-0.111:20090518T052643Z
+pkg:/SUNWipkg-brand@0.5.11,5.11-0.111:20090826T185654Z

After evaluation:
pkg:/entire@0.5.11,5.11-0.111:20090514T145840Z -> pkg:/entire@0.5.11,5.11-0.111:20090518T052643Z
pkg:/SUNWipkg-brand@0.5.11,5.11-0.111:20090508T161021Z -> pkg:/SUNWipkg-brand@0.5.11,5.11-0.111:20090826T185654Z
Actuators:

None
DOWNLOAD                                    PKGS       FILES     XFER (MB)
Completed                                    2/2         2/2     0.00/0.00 

PHASE                                        ACTIONS
Removal Phase                                  10/10 
Install Phase                                    1/1
Update Phase                                   20/20

A clone of opensolaris exists and has been updated and activated.
On the next boot the Boot Environment opensolaris-1 will be mounted on '/'.
Reboot when ready to switch to this updated BE.


---------------------------------------------------------------------------
NOTE: Please review release notes posted at:

http://opensolaris.org/os/project/indiana/resources/relnotes/200906/x86/
---------------------------------------------------------------------------

```

---

### Post by Velnias on 2009-11-27
And where are security updates? You just made minor system update, without SECURITY UPDATES.
And by the way, I found this in OpenSolaris forum:

Re: OpenSolaris: insecure or unstable ?
Posted: Oct 19, 2009 8:03 AM
"...The repo layout - security updates go to /support and /dev, but not /release,
so they're only free if you're willing to follow development builds..." 
-Alan Coopersmith- alan dot coopersmith at sun dot com Sun Microsystems, Inc. - X Window System Engineering


Development builds may be stable and secure, but this clearly not release. So how you keep your OpenSolaris safe without paying $324/year ?

---

### Post by toupeiro on 2009-11-27
> **Velnias said:**
> And where are security updates? You just made minor system update, without SECURITY UPDATES.
And by the way, I found this in OpenSolaris forum:

Re: OpenSolaris: insecure or unstable ?
Posted: Oct 19, 2009 8:03 AM
"...The repo layout - security updates go to /support and /dev, but not /release,
so they're only free if you're willing to follow development builds..." 
-Alan Coopersmith- alan dot coopersmith at sun dot com Sun Microsystems, Inc. - X Window System Engineering


Development builds may be stable and secure, but this clearly not release. So how you keep your OpenSolaris safe without paying $324/year ?

As I've told you already, if you **want** the absolute latest security updates without wanting to pay for them or be supported by Sun Microsystems, add the dev repo's. If you **want** to wait until they are more thorougly tested (as most production systems do) and still don't want to pay for support, then wait 6 months.  If its something that **needs** to come out sooner than six months due to the security risk, it does. If you **need** the patches as soon as they are released, and you need to be supported by sun due to the nature of your system, pay the money..  Even with the dev repos added, you still can choose which updates to apply if you want to, so if you are really that interested in being secure without paying money, you probably already know the patch you need.

The update I did was a kernel patch, it added a completely new line into grub, which is proof that if warranted, Sun is going to release patches without you having to pay for them.  I did not have the dev repos added to this system.  For anything non-critical or value-added, sun is going to test them, and roll them into their six month release cycle.  This is no different than what any other linux company does with their enterprise versions of their OS, the only difference is sun is doing this with their open source version.  

Your problem is simple.  You don't trust sun to release updates, and you don't trust opensolaris because its not like linux.  Ergo, don't run opensolaris.  You wanted to know how to get security updates in opensolaris without paying for them, I show'ed you. You've yet to give me one example where an opensolaris system was compromised due to the patch release nature of Sun for their OS so your claim has no credit whatsoever. You still get security updates for 100% of the open source components as soon as they are released, which is where most of the exploits would come from anyway.  I've supported  Solaris servers for over 7 years.  The support model changed a great deal with Solaris 10, for the better.  A patch bundle for solaris 10 was just released in october with all the critical patches and non-critical patches rolled up together.  I didn't have to pay anything at all to get this patch bundle.  The same model applies to OpenSolaris that applied to solaris 10. SOLARIS!=LINUX. You imply that opensolaris is unsafe, only because the updates don't come to you in a fashion you're used to. You can wordsmith it all you want, I don't really care.

---

### Post by pythonscript on 2009-11-27
> **handy said:**
> I thought I had better put this one in here for the benefit of gn2:

Whatever you do, DO _***NOT***_ TRY ARCH!

I currently use Arch on my laptop, along with Ubuntu and Windows 7, and I quite like it. It's a tad difficult to first set up and configure, but I must say it works like a charm once you get there. 

> **#11u-max said:**
> *laughs* if only you knew...

to the OP, solaris is a more hands on experience that is more fufilling once the system has the necessary tools.

That was the main reason I thought about giving it a try, which was also one of the reasons I looked at arch (the sometimes-bloated nature of ubuntu and the lightning speed of Arch were also factors, of course) so maybe it'll be something good to try in a virtual environment first. 

Thanks for all the responses!

---

### Post by Velnias on 2009-11-27
Its not important, what I like or trust, so lets compare, for example, simple security update "Ubuntu vs OpenSolaris":

_Subject:_ **Firefox Multiple Vulnerabilities CVE-2009-1563**
Rated as : Critical
Remotely Exploitable : Yes
Locally Exploitable : Yes

*Multiple vulnerabilities have been identified, which could be exploited by attackers to manipulate or disclose certain data, bypass security restrictions or compromise a vulnerable system. These issues are caused by errors in Firefox.*

In Ubuntu its simple - auto update in a few days.

In OpenSolaris, there is 3 possibilities:

1-pay for support and get auto-updates (not verified by me, but should be normally).
2-upgrade the whole system to developers build snv_128 (its not the same OpenSolaris, its beta of OpenSolaris), not to mention, that dev builds are rolled out and accessible to everyone only every 2 weeks; so, if unlucky, your updates are delayed for two weeks.
3-wait till new release (2010.02) and upgrade.

So, it is quite a different! and not in OpenSolaris favor.

---

### Post by toupeiro on 2009-11-27
> **Velnias said:**
> Its not important, what I like or trust, so lets compare, for example, simple security update "Ubuntu vs OpenSolaris":

_Subject:_ **Firefox Multiple Vulnerabilities CVE-2009-1563**
Rated as : Critical
Remotely Exploitable : Yes
Locally Exploitable : Yes

*Multiple vulnerabilities have been identified, which could be exploited by attackers to manipulate or disclose certain data, bypass security restrictions or compromise a vulnerable system. These issues are caused by errors in Firefox.*

In Ubuntu its simple - auto update in a few days.

In OpenSolaris, there is 3 possibilities:

1-pay for support and get auto-updates (not verified by me, but should be normally).
2-upgrade the whole system to developers build snv_128 (its not the same OpenSolaris, its beta of OpenSolaris), not to mention, that dev builds are rolled out and accessible to everyone only every 2 weeks; so, if unlucky, your updates are delayed for two weeks.
3-wait till new release (2010.02) and upgrade.

So, it is quite a different! and not in OpenSolaris favor.

<Deleted>
I've said my piece on this, and I am tired of repeating myself.  You aren't addressing any of the questions I've asked you or the points I've made, so I'm not going to debate a rollout methodology between Ubuntu and OpenSolaris with you if you're going to be calling one insecure and basing that solely on your opinion.  Use what you want.  You can add the dev repos, or you can patch firefox any day of the week you want to, at any time, its open source software.  The dev repos have the patch you are referring to, and you can simply update that component.

---

### Post by pythonscript on 2009-11-28
I didn't realize this would lead to such heated responses... let's try to keep it civil, why don't we?

---

