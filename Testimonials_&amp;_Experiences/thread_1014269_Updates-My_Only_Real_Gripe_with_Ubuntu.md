---
title: "Updates-My Only Real Gripe with Ubuntu"
date: 2008-12-17
forum: Testimonials &amp; Experiences
---

### Post by bobnutfield on 2008-12-17
Hello Everyone,

I know I will find a fix for this eventually, but I have to admit that it is getting tiresome "fixing" something that gets broken with a large update.  The most recent 41 updates (today) included a number of puse audio updates and of course now sound is broken.  There is at least one other thread currently that complains about these same updates (which included nm) breaking their wireless.  This is at least the fourth time since installing 8.10 that a large set of updates has damaged an otherwise working system, requiring sometimes considerable time to fix.  This seems to be a fairly recent development because in all the years I have been using Ubuntu, I don't recall this being an issue.

Now, I am a reasonably experienced user (not an expert), but for all the new people just trying out the newest Ubuntu, things like this could be a deal breaker.

I apoligize and I know I will get some biting responses, but I right now I am just a little frustrated that yet again I have to fix something that wasn't broken before an update.  I guess I just needed to vent.

By the way, just in case anyone else has the issue, all the usual commands to test sound work as usual, just no sound.  When clicking the test button, I get:

> "audiotestsrc wave=sine freq=512 !
Failed to connect to stream"

Not the whole error, but enough to investigate.  And the Sound Preferences GUI freezes and has to be forced to close.

I will dig around and find an answer, but if some kind soul knows the answer to this and can save me a few hours, I would be very appreciative.

---

### Post by oldos2er on 2008-12-17
Not a biting response (certainly not intended that way), but I learned a long time ago to turn off automatic updates because of their tendency to break things that weren't previously broken. No one's twisting our arms to update, right? Usually a quick read of the forums here will let me know when it's relatively safe to update. FWIW.

---

### Post by SunnyRabbiera on 2008-12-17
yeh the ubuntu updater isnt that careful, thats why I like using mint :D

---

### Post by halitech on 2008-12-17
whats the output of```
aplay -l
```

---

### Post by redandgreen on 2008-12-17
Ouch. I refused to install the pulseaudios, and now they're just going to sit there and fester in my update manager :( 

(is there a way of getting rid of them?)

When I was trying to get skype to work, I ended up uninstalling pulseaudio entirely, and putting on something called esound. I've had no problems since. Though granted, 'since' has been about a week. Here's a [_link_]("http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/"), in case it helps.

---

### Post by chrisod on 2008-12-17
FWIW, this problem is not unique to Ubuntu. A Windows update a couple of weks ago blue screened my wife's computer. I had to update a driver to get it functional again.

---

### Post by halitech on 2008-12-17
> **chrisod said:**
> FWIW, this problem is not unique to Ubuntu. A Windows update a couple of weks ago blue screened my wife's computer. I had to update a driver to get it functional again.

that is why I never trusted microsoft with a driver update

---

### Post by earthpigg on 2008-12-17
i didn't read all the replies, but here is the solution i use:

dont update.

```
ep@ep-laptop:~$ uptime
 03:31:29 up 37 days,  6:45,  2 users,  load average: 0.85, 0.76, 0.85
ep@ep-laptop:~$ 
```

just press ctrl+alt+backspace once a week, and never download updates.


ubuntu 8.10 or 8.04 without updates is still a helluva lot more secure than most systems, so security isn't really an issue... you are still a **_much_** harder target than most systems just by using linux.

and if specific evil spy guys are going specifically after you? then you shouldn't be using ubuntu to begin with ;)

who goes after linux users when trying to steal credit card info, etc...?

---

### Post by juanoleso on 2008-12-17
> **chrisod said:**
> FWIW, this problem is not unique to Ubuntu. A Windows update a couple of weks ago blue screened my wife's computer. I had to update a driver to get it functional again.

same and

> **halitech said:**
> that is why I never trusted microsoft with a driver update

+1


To be constructive, at one point I was using ALSA until I got my pulseaudio fixed [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=789578").  In gnome, system > preferences > sounds change all the dropdowns from autodetect to ALSA.  Don't know how to do it in KDE or other.

---

### Post by Dr Small on 2008-12-17
> **oldos2er said:**
> Not a biting response (certainly not intended that way), but I learned a long time ago to turn off automatic updates because of their tendency to break things that weren't previously broken. No one's twisting our arms to update, right? Usually a quick read of the forums here will let me know when it's relatively safe to update. FWIW.
I absolutely agree. Whether on Arch or Ubuntu, I never update unless it's something I specifically told it to upgrade. It causes too many things to go wrong (at least, the chance of it), and I'm tight on bandwidth anyhow, so I just never update software.

---

### Post by arizonalarry2 on 2008-12-17
I really wish I saw this thread before I installed those updates a couple of hours ago LOL :-P

---

### Post by |{urse on 2008-12-17
+1 to not updating, If it aint't broke don't fix it. I stopped at gutsy and am very happy with ubuntu.

---

### Post by bobnutfield on 2008-12-18
Well, thankfully all the responses were understanding and thoughtful.  But, I have to disagree (at least as far as my experience and usage goes) about not upgrading.  I use a number of distros concurrently and I have found that if I don't keep up with the updates, once an update comes along that is critical I am not prepared for it and usually have to just re-install.  The one exception to that is Slackware, which I use quite frequently as my file server at home.  It only gets security updates and what I application I choose to update.

I DO read the update information thoroughly before updating, and if there is a large number of applications being updated at the same time I check the forums thoroughly before doing the updates.

As I said in my opening post, I was able to fix it rather quickly (just disabled Pulse audio and reinstalled the sound modules).  But at the time, I was frustrated as this had occurred a few others times since Intrepids release.  I shouldn't really complain because I have the knowledge to fix whatever goes wrong usually (and become smarter because of it), and the devs work very hard for a FREE operating system that is in my opinion the best thing since sliced bread.

So, thanks for all the replies, and please pardon my opening rant.

---

### Post by doublewitt on 2008-12-18
So far, I have had no problems with the updates. Nothing has been dammaged in my system as described in the above posts. 

However, the only "gripe" I have is the DOWNLOAD speed for Ubuntu updates - it almost crawls while other downloads from the net drive at incredible speeds because of my high speed internet connection. Whatever I choose to download will *download* extremely fast - but those Ubuntu updates really lag behind. Some of those files are so tiny (less than half a meg) and take so long to get through. Is there something I should know about these updates...? Is there a way to change this situation...?

**I sure would appreciate any tips or advice**...

---

### Post by simtaalo on 2008-12-18
check your sources, i always get good speeds. as good as my 10meg connection allows for :)

---

### Post by doublewitt on 2008-12-24
I don't really understand what to do to improve the update download speed... anybody out there, please...??? ):P

---

### Post by TWO on 2008-12-24
> **doublewitt said:**
> I don't really understand what to do to improve the update download speed... anybody out there, please...??? ):P

Change your update source to a different server. Chances are you'll find one that is quicker.

Also, with regard to the main thread. Just don't use Pulseaudio. I don't know what they were playing at with including it as standard, but I couldn't play any sound with the damn thing selected when I upgraded, so I just select ALSA in all the drop down menus in sound preferences.

If they were going to include it, they could have at least ensured that it worked properly...

---

### Post by TVAbuntu on 2008-12-24
> **redandgreen said:**
> ...sit there and fester in my update manager :( 

(is there a way of getting rid of them?)


I too would love to know a way to get rid of unwanted updates from the update-manager.

---

### Post by SteveNorman on 2008-12-24
I'm not a fan of them either. I get scared when I do hit update. I wish there was a way that conflicting software could detect each other. As far as faster updates go,,I am using the New Zealand  seeder, as it seems to be the fastest for my connection. Seems strange tho, as I live in Seattle.

---

### Post by armandh on 2008-12-25
lucky me
no update trouble
so far fixing has not been breaking
if it happens I will likely adopt the wait first or
leave well enough alone

---

### Post by doublewitt on 2008-12-25
> **TWO said:**
> Change your update source to a different server. Chances are you'll find one that is quicker.

How do I change the update SOURCE...?

---

### Post by lancest on 2008-12-25
Go to System/Administration/Software sources. On the first tab it says 'Ubuntu software'. Where is says 'Download from' click to change to another mirror. I found this to be VERY HELPFUL to increase update download speeds. You can try different mirrors to find the fastest. The closest isn't necessarily the fastest also.

---

### Post by enoughsaid05 on 2008-12-26
Try changing from pulseaudio to alsamixer and see if it works. I think alsamixer is still there? (though i dunno how this is to be done, i am still a newbie)

Or wait for the new package and see how things goes. I had problems with update manager as well. There was once it removed my open office and I did not have office suit for days!

---

### Post by 3rdalbum on 2008-12-26
I used the Proposed repository with the intent that if I get any fixes for bugs I'm suffering, then I'll get them first; and if I get more problems I'll notify the developers immediately so the new updates don't get into the main repository.

I installed the Pulseaudio and kernel updates when they were in Proposed, with no problems. The kernel update forced me to reinstall my custom wireless driver, as I expected, but the inbuilt wireless driver still worked.

I don't think you can criticise Ubuntu for the problems you've just had. Their voluntary testers didn't report any problems with the packages when they were in Proposed, so the developers pushed them to the community.

---

### Post by mdsmedia on 2008-12-26
> **SteveNorman said:**
> ,I am using the New Zealand  seeder, as it seems to be the fastest for my connection. Seems strange tho, as I live in Seattle.
Is that a suburb of Auckland?

---

### Post by kspncr on 2008-12-27
I just blindly install all the updates and nothing has broken yet!

---

### Post by solwic on 2008-12-27
> **kspncr said:**
> I just blindly install all the updates and nothing has broken yet!

+1.  I've never had an update break anything.  I know it's always possible, but I don't use any weird software, either...so I guess I'm safe with the basics (firefox, thunderbird, amarok, openoffice3, etc.).  :)

---

### Post by zugu on 2008-12-28
PulseAudio is obviously not ready for large-scale deployement. The issues it causes are already proverbial.

Why are they shipping it in this unstable state? Why is beta-quality software inflicted upon casual users? Don't they have QA or something?

I mean, I can understand Fedora, living on the bleeding edge, with no respect for stability or backwards compatibility, all in the name of progress (though they never hide it), but Ubuntu? C'mon!

---

### Post by albinootje on 2008-12-28
> **earthpigg said:**
> 
dont update.
---cut---
ubuntu 8.10 or 8.04 without updates is still a helluva lot more secure than most systems, so security isn't really an issue...

If you're using Ubuntu on the desktop (If not just only by yourself, then with trusted other users together), and you're not offering any public services, then there are at least two things you *should* definitely upgrade whenever there's a security update for it :

1) your web-browser (Firefox, Galeon, Midori, links2 etc.)
2) flash-player

And of course anything else that you use to communicate over the internet deserves your (upgrade) attention.

A few months ago a dangerous problem in almost all web-browser was found.
Adobe asked more time before releasing more information about it.

That problem basically showed a design-flaw with web-browsing in general.
[http://www.securityfocus.com/news/11535](http://www.securityfocus.com/news/11535)

The Firefox add-on no-script is a solution for that.
It's a bit cumbersome to use at first, but I like it a lot!

---

### Post by albinootje on 2008-12-28
> **doublewitt said:**
> How do I change the update SOURCE...?

The poster meant repositories.
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
See the "Managing Repositories" section.

---

### Post by solwic on 2008-12-28
> **zugu said:**
> PulseAudio is obviously not ready for large-scale deployement. The issues it causes are already proverbial.

Why are they shipping it in this unstable state? Why is beta-quality software inflicted upon casual users? Don't they have QA or something?

I mean, I can understand Fedora, living on the bleeding edge, with no respect for stability or backwards compatibility, all in the name of progress (though they never hide it), but Ubuntu? C'mon!

Well yeah, but 8.10 gave us a new *theme*!  <insert appropriate level of sarcasm here>

---

### Post by zugu on 2008-12-28
> **jrock612 said:**
> Well yeah, but 8.10 gave us a new *theme*!  <insert appropriate level of sarcasm here>

And next versions will give us a neat new notification system. Seriously, I wonder on what criteria Mr. Shuttleworth (or whoever's in charge) sets these priorities.

---

### Post by solwic on 2008-12-28
> **zugu said:**
> And next versions will give us a neat new notification system. Seriously, I wonder on what criteria Mr. Shuttleworth (or whoever's in charge) sets these priorities.

That's the point:  I'm not sure there *is* a criteria.  :P

Ah well, I guess it still beats the alternative, which I'm sure Mr. Shuttleworth and the wonderful developers of Ubuntu know all too well.  There's a psychology to consumerism, even if what you're consuming doesn't have a monetary price tag.  They know what people will go for, and what they won't...and it's obvious that people like me will live without the eye candy just to keep using Ubuntu because it surely beats the hell out of going back to Windows.  

Even another Linux distro is kind of out of the question; none of the others are as popular or well supported as Ubuntu.  

Ah well...I still like Ubuntu.  :)

---

### Post by albinootje on 2008-12-28
> **jrock612 said:**
>  Ah well, I guess it still beats the alternative, which I'm sure Mr. Shuttleworth and the wonderful developers of Ubuntu know all too well. 

I'm a bit puzzled..
Are you referring to Mr. Shuttleworth's remark about wanting to make Ubuntu better than MacOSX in two years time ?

Concerning the various problems that people see while upgrading software in Ubuntu, I think a much easier bug-reporting system could be very useful.

Something like a crash-agent reporting tool.

There's so many different hardware pieces to support.
And so many different BIOS-es too (Think about power-management and software needing to deal with that).

How can we, Ubuntu users, make the next step in getting more hardware-vendors to become Linux-friendly.
I think the netbook popularity is already making a good step there.

---

### Post by solwic on 2008-12-28
> **albinootje said:**
> I'm a bit puzzled..
Are you referring to Mr. Shuttleworth's remark about wanting to make Ubuntu better than MacOSX in two years time ?


No, but did he really say that?  Ubuntu better than Mac OSX in 2 years?  That's a tall order.  Hope he pulls it off.

I was simply saying that there's no rush to fix the lingering issues like no desktop effects support for ATI users because it's pretty clear that people will deal with it if it means not going back to Windows.  It's the same reason Windows users always go back - yeah there's virii and malware and the like, but everything *works*.  You can find Windows software all over the web, every hardware vendor makes drivers for Windows, all the big software (Adobe, for instance, or nearly every game company) design their apps for Windows....

Same thing.  Once you're hooked to Linux, and you realize the benefits, it's safe to assume that you'll put up with a few things not working because the benefits (from your perspective) far outweigh the problems.  Thus, why bother making properly functioning drivers for ATI cards?  There's no need, as long as they cover the basics...most people will either suffer through or go buy an nVidia card. 

Don't get me wrong...I love Linux.  I have nothing but Ubuntu installed on my PC, and I don't use VBox or Wine for Windows apps anymore.  I'm just saying...why fix it if there's no repercussion for *not* fixing it?

And while I obviously couldn't prove this, I would place a bet on the idea that if everyone who uses ATI with Linux suddenly quit using Linux and quit buying anything that supports Linux until the ATI driver problem was fixed...there'd be a properly functioning open source driver for ATI video cards within a week.  Again...can't prove it, but I'd bet on it....  :P

---

### Post by albinootje on 2008-12-28
> **jrock612 said:**
> No, but did he really say that?  Ubuntu better than Mac OSX in 2 years?  That's a tall order.  Hope he pulls it off.

I didn't read it properly before, but here's a link :
[http://www.theregister.co.uk/2008/07/23/shuttleworth_apple_challenge/](http://www.theregister.co.uk/2008/07/23/shuttleworth_apple_challenge/)

>  And while I obviously couldn't prove this, I would place a bet on the idea that if everyone who uses ATI with Linux suddenly quit using Linux and quit buying anything that supports Linux until the ATI driver problem was fixed...there'd be a properly functioning open source driver for ATI video cards within a week.  Again...can't prove it, but I'd bet on it....  :P

I hope you're right :| :D

---

### Post by solwic on 2008-12-28
> **albinootje said:**
> I didn't read it properly before, but here's a link :
[http://www.theregister.co.uk/2008/07/23/shuttleworth_apple_challenge/](http://www.theregister.co.uk/2008/07/23/shuttleworth_apple_challenge/)


Says he wants to do it.  Suggests that he's working on it. 

I hope they pull it off.  Save me a couple thousand dollars on that new iBook I wanted.  :P

Cheers for the link.  :)

---

