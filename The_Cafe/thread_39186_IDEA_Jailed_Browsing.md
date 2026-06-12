---
title: "IDEA: Jailed Browsing"
date: 2005-06-03
forum: The Cafe
---

### Post by jdong on 2005-06-03
These days, I'm too busy to be script-hacking for pleasure, but for those with that kind of time, consider this suggestion:


Well, we've recently seen how Firefox vulnerabilities can touch your home directory. We also see other apps (GAIM, xchat) that could possible have similar vulnerabilities. What's the best way of protecting against this?

Well, the Fedora answer would be tight SELinux policies against these potentially vulnerable apps. We don't have SELinux in Hoary, so we'll need to think of another solution:


How about a simple workaround: jailed browsing. Does Firefox REALLY need to access your documents or photo collection? Does xchat REALLY need access to your Firefox profile directory and cache?

A script that uses dchroot to run browsers and network apps in a chroot jail (owned by the user) would be interesting. Probably mounting a readonly --bind for /usr and other binary locations, and a read-write --bind folder to "share files" between the jail and the original user's home directory.


Interesting project to attempt... :)

---

### Post by UbuWu on 2005-06-03
This is actually one thing I have never understood about computers. Why can a small problem or bug in one program lead to your whole system being insecure....

---

### Post by benplaut on 2005-06-03
[QUOTE=UbuWu]This is actually one thing I have never understood about computers. Why can a small problem or bug in one program lead to your whole system being insecure....[/QUOTE]

if that program has read (and/or write) privileges to your hard disk, it could be used as a doorway in

---

### Post by poofyhairguy on 2005-06-03
[QUOTE=jdong]These days, I'm too busy to be script-hacking for pleasure, but for those with that kind of time, consider this suggestion:


Well, we've recently seen how Firefox vulnerabilities can touch your home directory. We also see other apps (GAIM, xchat) that could possible have similar vulnerabilities. What's the best way of protecting against this?[/QUOTE]


Personally? I keep my most important stuff where nothing with home access can touch. My pictures, music, etc. Everything I treasure I only give root access to and I never run as root, don't even have a root account made. I use gksudo to do everything I need when I need to do things to these files.

They can all be played/viewed fine without sudo which is what I want to do with most of the data most of the time. The rest of the time, it feels nice to know that my home user could commit hari-kari and nothing would happen to what I treasure. One of my favorite things about Linux.

---

### Post by jdong on 2005-06-03
[QUOTE=UbuWu]This is actually one thing I have never understood about computers. Why can a small problem or bug in one program lead to your whole system being insecure....[/QUOTE]

Because filesystem permissions are not granular enough?

I highly suggest you guys go to a bookstore and take a look at the introduction chapters in O'Reilley's **SELinux** book (small, Hacks-sized book with LOTS of good info).


Specifically, programs should operate on the principle of least priviledge. Traditional UNIX/LINUX user/group/world permissions don't cut it, because if an application is compromised, it would at least have user permissions.


For example:

When apache is running PHP scripts, should it **really** need access to /etc/passwd?

When Firefox is running as a normal user, does it REALLY need access to all the user's files, plus /etc/passwd and friends?

If you're running cdrecord as suid root, it should ONLY get root access to the CD-RW devices, right?




SELinux (and Immunix and grsec) provide this fine-grained control, but require lots of tweaking. Ubuntu's getting SELinux soon (Fedora-style Targeted policies), so I'm excited to see that :)

---

### Post by UbuWu on 2005-06-04
[QUOTE=benplaut]if that program has read (and/or write) privileges to your hard disk, it could be used as a doorway in[/QUOTE]

I know how it works, I just never understood why it was possible and why systems couldn't be more secure even if a program had a bug/security issue. SELinux seems to be a good thing. Will it be in breezy? Or a later release...?

---

### Post by Moobert on 2005-06-04
[QUOTE=jdong]When apache is running PHP scripts, should it **really** need access to /etc/passwd?[/QUOTE]
That really depends on how doggy your php coding is :)
> When Firefox is running as a normal user, does it REALLY need access to all the user's files, plus /etc/passwd and friends?
/etc/passwd would needs to hardware broken, no ? plus youd need something like ssh running to do major damage. But iptables only allowing known ips would fix that.
> If you're running cdrecord as suid root, it should ONLY get root access to the CD-RW devices, right?
thats true enough.. but k3b runs as a normal user and does the same iirc.
> SELinux (and Immunix and grsec) provide this fine-grained control, but require lots of tweaking. Ubuntu's getting SELinux soon (Fedora-style Targeted policies), so I'm excited to see that :)

This does sound useful though, good to see ubuntus getting it :)

---

### Post by Lovechild on 2005-06-04
Why mock around with jailing, instead focus on getting SELinux and other security technologies integrated with Ubuntu, hopefully as fast as possible.. Linux as it stands right now is hopelessly insecure by design let's just fix it.. okay?

---

### Post by ubuntu_demon on 2005-06-04
[QUOTE=Lovechild]Why mock around with jailing, instead focus on getting SELinux and other security technologies integrated with Ubuntu, hopefully as fast as possible.. Linux as it stands right now is hopelessly insecure by design let's just fix it.. okay?[/QUOTE]
 Maybe jailing of applications can be made part of SELinux ???

---

### Post by UbuWu on 2005-06-04
Looks like it is almost ready: [https://www.ubuntulinux.org/wiki/SELinux](https://www.ubuntulinux.org/wiki/SELinux)

---

### Post by Lovechild on 2005-06-04
[QUOTE=UbuWu]Looks like it is almost ready: [https://www.ubuntulinux.org/wiki/SELinux](https://www.ubuntulinux.org/wiki/SELinux)[/QUOTE]

To the best of my knowledge, SELinux will not be integrated in Breezy - which means 6.04 is the soonest we can have an Ubuntu release with even near the same level of security that Fedora has shipped in 2 releases now (FC3 and FC4, the latter to be released on 14th of June - not counting FC2 which was the first FC with SELinux).

It simply seems to me that Ubuntu doesn't concern itself with making a more secure desktop, which is sad - Colin Walters of RedHat (and Rhythmbox) fame did a lecture on SELinux and GNOME[1] at this years GUADEC, so I would expect SELinux to stay governing what userspace can do to an even greater degree in the future. I was hoping that everyone would board the train and work together making Linux better.

[1] [http://stream.fluendo.com/archive/6uadec/Colin_Walters_-_SELinux_And_GNOME.ogg](http://stream.fluendo.com/archive/6uadec/Colin_Walters_-_SELinux_And_GNOME.ogg)

---

### Post by UbuWu on 2005-06-04
It is actually listed in breezygoals, although as low priority.
[http://udu.wiki.ubuntu.com/UbuntuDownUnder/BreezyGoals](http://udu.wiki.ubuntu.com/UbuntuDownUnder/BreezyGoals)

---

### Post by Lovechild on 2005-06-04
[QUOTE=UbuWu]It is actually listed in breezygoals, although as low priority.
[http://udu.wiki.ubuntu.com/UbuntuDownUnder/BreezyGoals](http://udu.wiki.ubuntu.com/UbuntuDownUnder/BreezyGoals)[/QUOTE]

A) security should be a major goal
B) [http://www.ubuntuforums.org/showpost.php?p=189375&postcount=124](http://www.ubuntuforums.org/showpost.php?p=189375&postcount=124) see item 1

Conclusion: Breezy probably won't have SELinux, also Ubuntu doesn't prioritize proactive security.

---

### Post by ubuntu_demon on 2005-06-04
I hope it will be in breezy. At the moment I don't have any reason to assume it will not make breezy :)

this page is editted 6 days ago and shows that they are quite far :
[https://www.ubuntulinux.org/wiki/SELinux](https://www.ubuntulinux.org/wiki/SELinux)

---

### Post by Lovechild on 2005-06-04
[QUOTE=demon666_nl]I hope it will be in breezy. At the moment I don't have any reason to assume it will not make breezy :)

this page is editted 6 days ago and shows that they are quite far :
[https://www.ubuntulinux.org/wiki/SELinux](https://www.ubuntulinux.org/wiki/SELinux)[/QUOTE]

I especially like:

"Policy configuration to be re-worked, now it's just fine tuning and dancing around it. Needs to Conflict & Replace selinux-policy-default"

That sounds like something the RH engineers would have said during the FC2 cycle, the policy is a major part of the work and finetuning it takes a long time, as history showed. I'll believe Breezy will have SELinux up and working when I see it merged and enabled.. Loronzo will have a hard few months shaking the bugs out of the system. 

(For anyone who thinks it'll be easy, I referer to Dan Walsh's FUDCon talk about SELinux)

---

### Post by jdong on 2005-06-04
Well, I don't think SELinux will show up in Breezy, at least not FC3/FC4 quality.


But I hope the kernel & base infrastructure will be ready, so at least the Backports Team can have fun with this. :)

---

### Post by Lovechild on 2005-06-04
[QUOTE=jdong]Well, I don't think SELinux will show up in Breezy, at least not FC3/FC4 quality.


But I hope the kernel & base infrastructure will be ready, so at least the Backports Team can have fun with this. :)[/QUOTE]

Nothing personal jdong, but I for one don't entirely trust backports to implement a thing like SELinux, for official support SELinux support thus 6.04 Cowardly Cobras (or whatever the name will be) will be the earliest.. and I suspect to make it work correctly Loronzo will need at least an entire cycle to hammering it down so it needs to be a major goal for said development cycle.
Remember SELinux was on the development plan for Hoary as well, abide as a minor goal, and nothing happened (but hey we don't expect miracles.. Hoary was leaps and bounds better than Warty in so many ways it's unfunny).

I'll have my hopes that Breezy++ will implement it and have it working, for now I'll reinstall Fedora Core to follow the FC5 cycle, which was just opened, which incidently promises even more SELinux and fun stuff like an init system rewrite. Can't wait to play with all the new toys.

---

### Post by jdong on 2005-06-04
> **Lovechild]Nothing personal jdong, but I for one don't entirely trust backports to implement a thing like SELinux[/quote]
No, I wouldn't use my SELinux on mission-critical servers, but at least it gives us a way to play with it a bit. :)
> 
, for official support SELinux support thus 6.04 Cowardly Cobras (or whatever the name will be) will be the earliest.. and I suspect to make it work correctly Loronzo will need at least an entire cycle to hammering it down so it needs to be a major goal for said development cycle.
Yeah said:**
> 
Remember SELinux was on the development plan for Hoary as well, abide as a minor goal, and nothing happened (but hey we don't expect miracles.. Hoary was leaps and bounds better than Warty in so many ways it's unfunny).

Well, SELinux shouldn't be something that rushed. Think about FC2 ;)

> 
I'll have my hopes that Breezy++ will implement it and have it working, for now I'll reinstall Fedora Core to follow the FC5 cycle, which was just opened, which incidently promises even more SELinux and fun stuff like an init system rewrite. Can't wait to play with all the new toys.
Yep. I have Fedora on my second partition, too. It's always interesting what they're doing.

---

### Post by Lovechild on 2005-06-04
I'll just remind you that in the previous post I didn't count FC2 as being SELinux enabled.. it was just... interesting. My machine wouldn't even boot out of the box with SELinux enabled.

One day we should default to a strict policy but moving slowly towards that using targeted policy is a good thing, we don't want stuff to break to much, which will cause people to disable it entirely.

I think Ubuntu can do SELinux in one cycle since they can learn and reuse from Fedora.

---

### Post by Curlydave on 2005-06-04
This seems like a step in the wrong direction.

---

### Post by Lovechild on 2005-06-04
[QUOTE=Curlydave]This seems like a step in the wrong direction.[/QUOTE]

More security is wrong?

---

### Post by poofyhairguy on 2005-06-04
[QUOTE=Lovechild]More security is wrong?[/QUOTE]

It is if it detracts from more important stuff. I mean, the reason Breezy (and maybe the release after it) would lack SE Linux because it is a HUGE (as in you must change your entire distro) task to add it. Considering that Ubuntu lacks things like a graphical installer, a usplash, and lots of other things Fedora or whatever takes for granted. I would personally rather them add a lot of small improvements (while waiting for Fedora to hammer out SE Linux making the transition easier in the long run) then rework the distro to add stuff really only servers need right now.

I mean its cool Fedora has it. Fedora is definately more on the edge than Ubuntu. But that isn't always a good thing. SE Linux is still very new and if Ubuntu gets on now it has to waste development time hammering out its problems. Fedora has SE Linux now because Red Hat forks from it to make their server distro.  If I remember correctly from Core 3 (the week and a half I used it) running with SE Linux turned on slowed everything down. Hopefully that will be fixed in future Fedora, but until that is it isn't in Ubuntu's best interest to pick it up. I and many others will never use it if it cuts down speed too much. I'd rather reinstall a hacked box then run slower everyday it worked (its an odds thing, the odds of an Ubuntu desktop box getting hacked is smaller than the odds of winning the lottery).

I bet if you ran a poll that said:

"Do you want Breezy to have a new secuity system that you don't understand so that things can be theoretically safer but definately slower?"

or 

"Do you want better laptop support, a GraphicalInstaller, Xen, better mono and a new startup tool (things that are currently higher priorities for Breezy than SE Linux)"

I think most would pick the latter. I know I would. I run Ubuntu as a desktop, who cares about security that much? I mean, as long as there are no viruses, malware most are happy. SE Linux is for the server and for the future, hopefully the kernel will incorporate it and the next Ubuntu will get it be default.  Otherwise desktop users want OS toys, as much as can be got. Only so much development to go around.

---

### Post by Lovechild on 2005-06-04
The slowdown caused by SELinux today is very low, RedHat worked hard on optimizing the SELinux code, it started out in FC2 being about a 10% slowdown, these days I really have to strain myself to notice it. And SELinux isn't just safer in theory, of course the more work that is put into "jailing" userspace apps the more visible the advantages is.. I imagine that e.g. we could kill off everything remotely spyware-like, before it becomes a problem.

As for the items on that list you presented:

uSplash supposedly was nearly finshed but was to late for inclusion in Hoary, so I don't think that'll be hard in terms of development time. But yes, this should be a major focus as well, scrollingtext boot is just so.. 90's

A graphical installer, yes that would be nice - I don't see how that excludes SELinux, as I understand there's already quite a bit of work completed for this - I don't entirely agree it's more important than focusing on good security but most users would probably say it is.. Security should just work thus users won't notice it unless it fails, a text installer is harder to miss :)

Better Mono, tseng is working hard on that one... he's a great guy (and Brandon if you read this, us old BMG guys were really thankful for all the help you gave us... you rock! - I definately owe you a beer)

I don't really think we need Xen, ubuntu is primarily a desktop distro, I doubt many desktop users need Xen - at least untill Vanderpool chips arrive and we can, hopefully, run Windows using Xen.. I doubt 95% of the users would bother at least for anything but fun.

Startup tool, do you mean a new init system - I assume we could rip Initng or something like that.. hopefully this will be an LSB/Fd.o type work where distros work together instead of everyone reinventing the wheel - I would really rather wait a cycle and get it done right and universal. Fedora does seem to have this aim for FC5 as well, so cooperation might be an option.

Laptop support, I assume you mean software suspend, ACPI and that sort of thing, which currently is sorta iffy in the kernel. Upstream is working on this as well, look at gnome-power-manager (a cool project.. plug plug plug..)

I think security is a worthwhile investment of time, but I agree it's not the end-all goal, of course we should get user visible changes in, like an installer of great graphical goodness and beauty.

Of other items could be mentioned:

Translation, usability, integration and transistioning tools - now those would be nice long term goals (aside security *cough*)

*wow now I feel very guilty for complaining so much and not providing any help - in the end actually helping out is the best way to get stuff done.. however I'm far from smart enough to make SELinux work*

---

### Post by poofyhairguy on 2005-06-04
I like you Lovechild. You are very reasonable. You show the best side of Fedora fans (and heck Linux fans in general).

[QUOTE=Lovechild]The slowdown caused by SELinux today is very low, RedHat worked hard on optimizing the SELinux code, it started out in FC2 being about a 10% slowdown, these days I really have to strain myself to notice it. And SELinux isn't just safer in theory, of course the more work that is put into "jailing" userspace apps the more visible the advantages is.. I imagine that e.g. we could kill off everything remotely spyware-like, before it becomes a problem.[/QUOTE]

If viruses and spyware come, I think the kernel will get on board. No need for Ubuntu to trial blaze on a what is mostly a server issue today.

As for the items on that list you presented:


> uSplash supposedly was nearly finshed but was to late for inclusion in Hoary, so I don't think that'll be hard in terms of development time. But yes, this should be a major focus as well, scrollingtext boot is just so.. 90's


I have tried out the Ubuntu splash and it is pretty nice. If this isn't added to Breezy I'm going to be pretty upset.

> A graphical installer, yes that would be nice - I don't see how that excludes SELinux, as I understand there's already quite a bit of work completed for this - I don't entirely agree it's more important than focusing on good security but most users would probably say it is.. Security should just work thus users won't notice it unless it fails, a text installer is harder to miss :)

It only excludes SE Linux because it deserves the developer's time more.

> Better Mono, tseng is working hard on that one... he's a great guy (and Brandon if you read this, us old BMG guys were really thankful for all the help you gave us... you rock! - I definately owe you a beer)

This is the BIG one for me and many others. If in Breezy we can apt-get beagle and then have it work without a lot of hassle I personally don't care if anything else is done (besides new gnome of course).

> I don't really think we need Xen, ubuntu is primarily a desktop distro, I doubt many desktop users need Xen - at least untill Vanderpool chips arrive and we can, hopefully, run Windows using Xen.. I doubt 95% of the users would bother at least for anything but fun.

Yeah, I'm not that hot on Xen either. The desire for it will grow if it can turn into a free VMware (not in cards I don't think).

> Startup tool, do you mean a new init system - I assume we could rip Initng or something like that.. hopefully this will be an LSB/Fd.o type work where distros work together instead of everyone reinventing the wheel - I would really rather wait a cycle and get it done right and universal. Fedora does seem to have this aim for FC5 as well, so cooperation might be an option.

I wished the projects cooperated more honestly. But one way or another this is a VERY needed addition to Breezy.

> Laptop support, I assume you mean software suspend, ACPI and that sort of thing, which currently is sorta iffy in the kernel. Upstream is working on this as well, look at gnome-power-manager (a cool project.. plug plug plug..)

Also there is talk that Mark is trying to get some Ubuntu specific broadcom drivers so that all those airport cards can work. That would be cool.

> I think security is a worthwhile investment of time, but I agree it's not the end-all goal, of course we should get user visible changes in, like an installer of great graphical goodness and beauty.

Ubuntu pretty much goes in this order for Breezy:

Workstation
Desktop
Thin Client
Server
Educational?

Fedora seems to go like this:

Server
Workstation
Desktop
etc..

But I could be wrong.

---

### Post by TravisNewman on 2005-06-04
I'd put Workstation above Server for Fedora-- RedHat Enterprise is the big Server bad boy.

But while I've learned a few things and changed my views on some things by this thread, I DO miss the original intended idea. I'd love to see jailed browsing!

---

### Post by poofyhairguy on 2005-06-04
[QUOTE=panickedthumb]I'd put Workstation above Server for Fedora-- RedHat Enterprise is the big Server bad boy.
[/QUOTE]

Isn't the enterprise version forked from Fedora though? I though Fedora was the Sid, RHEL was its Sarge (in debian terms). If Red Hat plans to base its money making server distro off of Fedora then how can Fedora not make that the main priority? Always seemed obvious to me. Thats why Fedora has all the great server stuff.

I could be wrong.

As far as jailed browsing.....the whole point would be if Firefox started acting bad security wise like IE does. So that brings up the question: what nasty security risks have you run across when using Firefox in Linux. If those exist we need to make a good solution for each!

---

### Post by UbuWu on 2005-06-04
Well I don't really have all the technically knowledge needed, but about jailed browsing: that would be great! I have as far as I can remeber never saved a webpage in firefox, so it doesn't need any chance to do something I don't want with my files. And if you actually need to save some webpage to disk, my solution would be for firefox to collect the data, and then saying to gnome, I have this data, save it to a file, so gnome shows a save file dialog to save the file. No need for firefox itself to have any write permissions to my home directory except for its own settings, and especially not without any user intervention! But then again I don't know about all the technical stuff involved...

---

### Post by Lovechild on 2005-06-05
Where as Ubuntu seems to be targeted at single user desktops (sudo hell anyone?  ](*,) ), Fedora is granted more targeted at being a workstation OS, the new Fedora Directory server thing sorta proves this.. nothing wrong with that I like Fedora on my singleuser desktop it works very well.

I don't see a problem with that, but I do hope that seeing as Ubuntu and Fedora are targetting basically the same market, we could see some more cooporation between Ubuntu and the newly formed Fedora Foundation.

---

### Post by Lovechild on 2005-06-05
[QUOTE=poofyhairguy]
As far as jailed browsing.....the whole point would be if Firefox started acting bad security wise like IE does. So that brings up the question: what nasty security risks have you run across when using Firefox in Linux. If those exist we need to make a good solution for each![/QUOTE]

One of the reasons we need a MAC for such things is that the issue is more complex that such. We want to retrain functionality and integration but eliminate security risks. Right now basically your webbrowser has complete read/write/execute access to all of your home dir... WHY?

This is a fundamental design flaw, the mozilla foundation (and who ever writes applications to be honest) should ship a policy that says "I need to access these specific files and nothing else - these are the rights I require", instead of just assuming that it can do what ever it damn well pleases. This isn't secure by design, if there's a way for someone to hijack the webbrowser (and there is, just look at.. *cough* IE *cough*) they can wreck everything in your homedir.. sound like fun?

MAC is a way to grant us that finegrained control, whereas jailing is sorta the brute way to just contain the problem (we still allow you to do everything you damn well please, but at least you can only do it to these parts of the system). One leads to better design, the other leads to no improvement in design - both should however fix the problem.

Not to mention that AFAIK, escaping a jail is perfectly possible.

---

