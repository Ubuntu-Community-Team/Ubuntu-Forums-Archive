---
title: "Ubuntu - Dapper, worst Ubuntu yet"
date: 2006-06-19
forum: Testimonials &amp; Experiences
---

### Post by pksings on 2006-06-19
I love the integration, the look and feel, absolutely wonderful.

I don't like the quality. Fglrx vs Xorg 7, doesn't work at all. The wireless bcm43xx module locks up my system, I had to blacklist it and use NDISwrapper. 

I let automatic updates run and saturday night it loaded 88 upgrades, that means 88 programs that were in the initial release had major enough bugs that they had to be upgraded already. That is definitely not good. Worse, one or more of them completely borked Audacity's ability to record audio.  /dev/dsp disappeared completely. It could not have been a worse time for me.....I missed being able to record something I really, really wanted, and will never be able to get..

For two days I was extolling the virtues of Linux, Ubuntu in particular, rock solid, fast, great audio workstation!  Then imagine when on the third day, I couldn't even record.....  

Very, very dissapointed is a kind and mild way of saying what I felt. 
Worse, I have to format and re-install to get back to what I used to be able to do, no fix is available and none in sight.... And it also means that I cannot allow ANY upgrades to install, I don't know which one did it. My server/workstation migration to Ubuntu is now postponed indefinitely, cannot do without audio editing/playback on it, that was it's primary reason for existence.

This is bad, very bad....

PK

Edit;  After solving all but the fglrx issue over time I am really happy with it as a distro however, it rocks!  It was just really painful getting it there....

---

### Post by Rackerz on 2006-06-19
[QUOTE=pksings]I love the integration, the look and feel, absolutely wonderful.

I don't like the quality. Fglrx vs Xorg 7, doesn't work at all. The wireless bcm43xx module locks up my system, I had to blacklist it and use NDISwrapper. 

I let automatic updates run and saturday night it loaded 88 upgrades, that means 88 programs that were in the initial release had major enough bugs that they had to be upgraded already. That is definitely not good. Worse, one or more of them completely borked Audacity's ability to record audio.  /dev/dsp disappeared completely. It could not have been a worse time for me.....I missed being able to record something I really, really wanted, and will never be able to get..

For two days I was extolling the virtues of Linux, Ubuntu in particular, rock solid, fast, great audio workstation!  Then imagine when on the third day, I couldn't even record.....  

Very, very dissapointed is a kind and mild way of saying what I felt. 
Worse, I have to format and re-install to get back to what I used to be able to do, no fix is available and none in sight.... And it also means that I cannot allow ANY upgrades to install, I don't know which one did it. My server/workstation migration to Ubuntu is now postponed indefinitely, cannot do without audio editing/playback on it, that was it's primary reason for existence.

This is bad, very bad....

PK[/QUOTE]

That's your opinion, and it's bias as is everyone elses opinion. Did you try and get support for the problems you were having?

---

### Post by WeldingMarathon on 2006-06-19
[QUOTE=pksings]I let automatic updates run and saturday night it loaded 88 upgrades, that means 88 programs that were in the initial release had major enough bugs that they had to be upgraded already.[/QUOTE]

I found that quite reassuring and at least it works - or it has done for me most of the time. I found it interesting that Dapper told me there were updates straight after installation. 

No idea how it knew, it wasn't plugged into the network when installing! I detect (sensible) kidology here.

As a comparison my SP2 XP Virtual Machine has installed nearly 200 updates so far and has tons more to come. And thats before I search out patches to Office.

But your experience is worse than mine. I just lost a day without VMWare after an update, not something I wouldn't get back.

---

### Post by livingtarget on 2006-06-20
[QUOTE=pksings]I love the integration, the look and feel, absolutely wonderful.

I don't like the quality. Fglrx vs Xorg 7, doesn't work at all. The wireless bcm43xx module locks up my system, I had to blacklist it and use NDISwrapper. 

I let automatic updates run and saturday night it loaded 88 upgrades, that means 88 programs that were in the initial release had major enough bugs that they had to be upgraded already. That is definitely not good. Worse, one or more of them completely borked Audacity's ability to record audio.  /dev/dsp disappeared completely. It could not have been a worse time for me.....I missed being able to record something I really, really wanted, and will never be able to get..

For two days I was extolling the virtues of Linux, Ubuntu in particular, rock solid, fast, great audio workstation!  Then imagine when on the third day, I couldn't even record.....  

Very, very dissapointed is a kind and mild way of saying what I felt. 
Worse, I have to format and re-install to get back to what I used to be able to do, no fix is available and none in sight.... And it also means that I cannot allow ANY upgrades to install, I don't know which one did it. My server/workstation migration to Ubuntu is now postponed indefinitely, cannot do without audio editing/playback on it, that was it's primary reason for existence.

This is bad, very bad....

PK[/QUOTE]

If you upgraded from breezy you'll find that hotplug and company has been replaced by udev. Any missing /dev/* devices are usually caused because of that. There was also a new kernel included. Most problems with kernel upgrades are people who tend to upgrade when the mirrors aren't fully populated yet.

You can recreate /dev/dsp manually, but this is rather tough - trust me. For example search google for "mknod /dev/dsp" and that'll put you into that direction. I assume you've tried restarting as some nodes might get recreated then AFAIK.

88 upgrades, no big deal. Did you know that gnome 2.14.2 was released and put in dapper? That'll be where most of the packages came from.

I don't like the way you put it, dapper is definitly not the worst ubuntu. You just have a bad match of hardware (read: ati/wifi), hopefully you'll have better support in edgy. I've heared the new .17 kernel is going to have many a improvement for wifi users.

---

### Post by nocturn on 2006-06-20
[QUOTE=Rackerz]That's your opinion, and it's bias as is everyone elses opinion. Did you try and get support for the problems you were having?[/QUOTE]

Regardless of his specific problems, I too was amazed to see two batches of updates land on dapper, one 50+ packages and the second 89 packages.  None of the updates have a description attached BTW.

I was already on Dapper since flight 6, and it feels a bit like the development cycle just continued after the release...  I'm wondering at this point if the six week delay wasn't too short to get everything ready for LTS.

I don't think Dapper is the worst Ubuntu, I love the polish, the new icons etc, but I was disappointed by the presence of 2 showstopper bugs (DVD burning/mounting and printing) and the very large batches of updates so short after the release.

---

### Post by nocturn on 2006-06-20
[QUOTE=livingtarget]
I don't like the way you put it, dapper is definitly not the worst ubuntu. You just have a bad match of hardware (read: ati/wifi), hopefully you'll have better support in edgy. I've heared the new .17 kernel is going to have many a improvement for wifi users.[/QUOTE]

I understand, and I though I had few regressions myself, it seems that Dapper broke a lot of hardware that was working on Breezy.  I don't know what causes this (the new kernel?), but for users that are affected by it, it's pretty annoying.

---

### Post by livingtarget on 2006-06-20
Yeah you're making a valid point. I believe they tried to do just a bit too much with dapper and ended up delaying it. I think there were also some problems upstream (Cups) that weren't very stable.

So we'll get newer packages but perhaps not as stable as they should've be. I remember frglx package was ugraded in the last few weeks with a new version. 

Like all regressions they'll usually get fixed by the next iteration.

Also keep in mind i'm rather blessed with a stable system, so perhaps i'm biased O:) .

---

### Post by nocturn on 2006-06-20
[QUOTE=livingtarget]Yeah you're making a valid point. I believe they tried to do just a bit too much with dapper and ended up delaying it. I think there were also some problems upstream (Cups) that weren't very stable.

So we'll get newer packages but perhaps not as stable as they should've be. I remember frglx package was ugraded in the last few weeks with a new version. 

Like all regressions they'll usually get fixed by the next iteration.

Also keep in mind i'm rather blessed with a stable system, so perhaps i'm biased O:) .[/QUOTE]


To be honest, I'm blessed with two systems upgraded from Breezy without major issues.  But I'm hit by the DVD/CD writing bug (though only partially).

But if cups upstream was broken and the Breezy version worked, we should have stayed at that version to make things work.

If Dapper was just a normal release like Breezy was, it would be good (not nearly a revolution as Warty->Hoary, but good).  
For LTS, it falls a bit short though... and I'm waiting to upgrade my server to it until the dust settles a bit.

---

### Post by pksings on 2006-06-20
[QUOTE=Rackerz]That's your opinion, and it's bias as is everyone elses opinion. Did you try and get support for the problems you were having?[/QUOTE]
Yes, I did look for support, I searched the forums, all of them and read through at least 30 pages of posts looking for anything that would help and found nothing.  

I also completely removed all .386 kernels, my /boot did not have room for any more. I am running .686 only and now my /dev/dsp has returned.  A day too late unfortunately..  

Fglrx still doesn't work, there are 40 or more posts some of which ultimately succeeded and some of which like me simply it just doesn't work for even though it loads, initializes and "should" work. I'm out of time to mess with it..

Wifi with ndiswrapper is fine, works just fine, no issues whatsoever.  

My statement that it is the "worst" is based on my initial 4.10 install which was flawless in every regard, everything worked with no issues whatsoever. My upgrade to 5.10, which also was flawless, compared to my failed upgrade to Dapper, which made the system unusable  and then my attempts to install from the live CD which also was unusable as I couldn't find a way to re-use my existing filesystem layout. So I had to format and re-install from scratch. And upon which I had serious issues. As a direct comparison, it's the worst yet for me. By far the most trouble to get working. 

That being said, let's put credit where it is due. It is awesome once it's working...   After running the "Automatix" installs this is an excellent distro, excellent integration, all my functionality requirements for me to do my work functions are met, everything I need to be productive.  Good show!!

It's fast, it's beautiful, and for me it is still my distro of choice.

But no, I will not recommend it to my non-techie friends. They will never be able to fix the stuff I have had to fix and I will be forced to do it for them, time I do not have to "donate" to the cause.

PK

---

