---
title: "Broadcasting with Ubuntu or openSUSE?"
date: 2010-07-08
forum: The Cafe
---

### Post by Groucho Marxist on 2010-07-08
After I earn my broadcasting degree, I'm considering the possibility of starting up a professional web-radio station with the intention of using FOSS to accomplish this goal. With that being said, which OS should I choose for servers, on-air broadcasting and office use? OpenSUSE has piqued my interest, although Ubuntu is also promising. I realize this is speculation, but I would like to carefully research this before I make any final decisions.

---

### Post by NightwishFan on 2010-07-08
My opinion is that you should focus on the release schedules and support of the distributions in question rather than end user features, as most distros run tasks equally well. You may like the LTS type releases of Ubuntu since you can predict several years of support and make it easy to target your software infrastructure and development for it. Both distributions I have used and highly recommend, but being an Ubuntu user you can see which one I prefer. I hope this is of help to you.

---

### Post by Yarui on 2010-07-08
Either would do fine, it's just whatever you prefer.  I would recommend trying them both out in whatever way is possible and decide which you like better.  I personally like Ubuntu better, but that's an unfair judgment considering I have barely used any form of SUSE linux.

---

### Post by Groucho Marxist on 2010-07-08
> **NightwishFan said:**
> My opinion is that you should focus on the release schedules and support of the distributions in question rather than end user features, as most distros run tasks equally well. You may like the LTS type releases of Ubuntu since you can predict several years of support and make it easy to target your software infrastructure and development for it. Both distributions I have used and highly recommend, but being an Ubuntu user you can see which one I prefer. I hope this is of help to you.

I agree about the release cycles; with some distros, it can be maddening to anticipate when to upgrade. I think my mom has a fairly recent computer she wanted to get rid of; I'll install openSUSE on it (instead of the virtualized copy I'm running right now) and compare the two. 

Thanks for the help!

---

### Post by cariboo on 2010-07-08
Have a look at this [article]("http://http://tldp.org/LDP/LG/issue96/hughes.html") in the Linux Gazette, it should be helpful.

---

### Post by Yarui on 2010-07-08
> **NightwishFan said:**
> My opinion is that you should focus on the release schedules and support of the distributions in question rather than end user features, as most distros run tasks equally well. You may like the LTS type releases of Ubuntu since you can predict several years of support and make it easy to target your software infrastructure and development for it. Both distributions I have used and highly recommend, but being an Ubuntu user you can see which one I prefer. I hope this is of help to you.
This is a good point, when you are running a server the release scheduling is a very important thing to consider.  Many people prefer using a distro with a rolling release, which basically means they don't ever have any full package releases, they just release updated parts as they create them.  A lot of users who prefer this feel that it is less work to keep everything running because you just have to do a bit of tweaking as you go instead of having to completely reinstall the OS and then reconfigure all the new versions of software.

If this sounds like something that interests you, look into what distros have a rolling release system.  I don't know of any that don't have a very difficult initial installation and configuration process, so that may not end up being what you want to look for.

Ubuntu has a 6 month release cycle and openSUSE has an 8 month release cycle.  Personally I don't think that is enough of a difference to let that be your sole reason for your choice.

---

### Post by Yarui on 2010-07-08
> **cariboo907 said:**
> Have a look at this [article]("http://http://tldp.org/LDP/LG/issue96/hughes.html") in the Linux Gazette, it should be helpful.
That link is broken, it seems to have an extra http// in it.

---

### Post by Groucho Marxist on 2010-07-09
> **Yarui said:**
> This is a good point, when you are running a server the release scheduling is a very important thing to consider.  Many people prefer using a distro with a rolling release, which basically means they don't ever have any full package releases, they just release updated parts as they create them.  A lot of users who prefer this feel that it is less work to keep everything running because you just have to do a bit of tweaking as you go instead of having to completely reinstall the OS and then reconfigure all the new versions of software.

If this sounds like something that interests you, look into what distros have a rolling release system.  I don't know of any that don't have a very difficult initial installation and configuration process, so that may not end up being what you want to look for.

Ubuntu has a 6 month release cycle and openSUSE has an 8 month release cycle.  Personally I don't think that is enough of a difference to let that be your sole reason for your choice.

I agree about the rolling releases; that should not be the only factor in the decision. I've just discovered [Rivendell]("http://www.rivendellaudio.org/index.shtml"), a professional FOSS radio automation suite for the openSUSE platform. Does anyone here know of something like this for Ubuntu?

---

### Post by NightwishFan on 2010-07-09
Seems like it is possible for 32-bit Ubuntu. (Probably a way for 64-bit as well.)
[http://rivendell.tryphon.org/wiki/index.php/Install_Rivendell_on_Ubuntu](http://rivendell.tryphon.org/wiki/index.php/Install_Rivendell_on_Ubuntu)

OpenSUSE probably offers this as well, however Ubuntu includes a Realtime Kernel that always worked very well for me.

[http://packages.ubuntu.com/lucid/linux-rt](http://packages.ubuntu.com/lucid/linux-rt)

Here are some links.
[http://en.opensuse.org/Sound-concepts](http://en.opensuse.org/Sound-concepts)
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

### Post by Yarui on 2010-07-09
> **Groucho Marxist said:**
> I agree about the rolling releases; that should not be the only factor in the decision. I've just discovered [Rivendell]("http://www.rivendellaudio.org/index.shtml"), a professional FOSS radio automation suite for the openSUSE platform. Does anyone here know of something like this for Ubuntu?
Yeah, it's definitely not the only thing that you should look at.  All the distros have plenty to offer.  You can find plenty of lists about the differences that can help point you in the right direction.  The following was one of the first links that really helped me figure out what distros I was most interested in:

[http://distrowatch.com/dwres.php?resource=major](http://distrowatch.com/dwres.php?resource=major)

There was another article that I found really helpful but I can't seem to find it now.  When I first started to get serious about Linux, I was really confused about the differences between distros and a bit intimidated by the sheer number of choices, but eventually I figured out that they are all pretty similar and the best way of deciding what works best for you is to just try out some distros.

Since you already have your sights set on Ubuntu and openSUSE, you might as well try those out.  If you decide later that you want something that those don't offer, like the rolling releases, you can look at some other distros, but for now there is no harm with going with the ones that immediately interested you.  Ubuntu is great, and I haven't used anything SUSE based very much, but I'm sure openSUSE is an equally great OS.  You can just choose one and give it a shot, or if you have the resources to try them both out at the same time on seperate machines or on partitions of the same machine, then you may want to give that a shot.

---

### Post by NightwishFan on 2010-07-09
Virtualbox or a live cd is a great way to try out a distro.

---

### Post by Yarui on 2010-07-09
> **NightwishFan said:**
> Virtualbox or a live cd is a great way to try out a distro.
That's true.  That's a possibility I never think to suggest because I don't really mind jumping in and installing a new distro.  I have plenty of extra space to install experimental distros on, though.

---

