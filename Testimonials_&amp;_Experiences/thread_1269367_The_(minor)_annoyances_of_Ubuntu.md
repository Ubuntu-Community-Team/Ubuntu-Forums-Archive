---
title: "The (minor) annoyances of Ubuntu"
date: 2009-09-18
forum: Testimonials &amp; Experiences
---

### Post by cguy on 2009-09-18
Let me start by saying that I find Ubuntu as the best distro out there; well, it suits me best...

However there are minor annoyances that don't ever seem to be solved.

**Example number 1:**
They never settle on one mount point for the disks.
/mnt/sdaX
/media/sdaX
/media/mnt%sda%X
/mnt/diskX
Every new coming distro changes the damn path.
Yes, I know how to solve it in about 1 minute but it's annoying nonetheless.

**Example number 2:**
Brasero and K3B. I always want to check for write errors after a burn, but whether these programs pull the CD back in after ejecting it is a matter of luck.

It worked in Hardy, didn't work in Intrepid, it worked in Jaunty but then stopped working in Jaunty after a reinstall.
I'm talking about the exact same system (hardware wise), whether updated or not (software wise)


**Example number 3:**
I have a FAT32 partition. Does changing file permissions work flawlessly? Again, a matter of luck.

Thanks for reading.

---

### Post by scragar on 2009-09-18
The first one I think is a matter of defaults, it used to be everything was mounted in /media so it would appear on the dekstop, then it got added to the places menu, so they changed to /mount and the name changed, then they got moved back to /media because people complained.

The last one is down to how the FAT file system works, it doesn't have perms like ubuntu does, changing perms for it's contents doesn't always work, there's no way to change that.

I have no defence for the second one, it annoys me too.

---

### Post by cguy on 2009-09-18
Yes, I realize that FAT has issues and I'll redo my partition table as soon as I back up everything (>100GB), but why isn't there the certainty that file permissions will either work or will not?
I know the potential of it to work is there, because it did, but it never stays the same even between reinstalls of the same version of Ubuntu.

---

### Post by Eric Warren on 2009-09-18
Hmmmm, no comment...

---

### Post by HappyFeet on 2009-09-18
.............

---

### Post by HappyFeet on 2009-09-18
...........

---

### Post by cguy on 2009-09-18
Number 1 is a strong reality, so you either are extremely stupid or didn't do 40+ installs of different versions of Ubuntu; or both.

Number 2 is not MY problem and MY problem only; read scragar's reply and do a google search on the issue.

Number 3, do a Google search and see the hundreds of reports of the issue.

Congratulations on overreacting and making a fool of yourself.

---

### Post by HappyFeet on 2009-09-18
...........

---

### Post by cguy on 2009-09-18
I just stated some recurring problems that annoy me at Ubuntu. Did I say 'Ubuntu sux' and whine?
I did not!

And you come like an uptight nerd and flame. Is the fanboysm so strong?

Does anyone who matters to the development take notice and maybe work on them? If so then it's great; if not, too bad.
I didn't post for your fanboy-flaming pleasure.

> Permission problems are basically a thing of the past.
> Nice try. I could hand select issues from other OS's too.
Is it a thing of the past or a current hand picked problem?

But why did I say Hundreds and not thousands or hundreds of thousands? (I certainly didn't count them.) Because noone in the whole world would ever read that much, which doesn't mean that the problem is not there. But you don't seem to think since you pick on a stupid word. I bet that you have an overinflated ego which doesn't to have a real basis. You may be good with Linux but, based on the way that you react, you are as stupid as a rock.


By ignoring the issues Ubuntu would have never become one of the greatest distros.
Luckily, the devs are not stupid, head in the clouds uptight nerds.

---

### Post by Tamlynmac on 2009-09-18
> cguy
But why did I say Hundreds and not thousands or hundreds of thousands? (I certainly didn't count them.) Because noone in the whole world would ever read that much, which doesn't mean that the problem is not there. But you don't seem to think since you pick on a stupid word. I bet that you have an overinflated ego which doesn't to have a real basis. You may be good with Linux but, based on the way that you react, you are as stupid as a rock.


By ignoring the issues Ubuntu would have never become one of the greatest distros.
Luckily, the devs are not stupid, head in the clouds uptight nerds. 	


Based on your last statement you know the devs. Why would you post here if your familiar with the devs? Odd.

I doubt this thread is going anywhere and hope that the mods close it before the thread becomes a full blown name calling contest. Another quality example of the T&E section.

May I suggest we take the high road and not participate in this type of thread, as it (IMHO) reflects negatively on the forum. Perpetuating this type of thread may only serve to inspire others.

Just my $0.02

---

### Post by cguy on 2009-09-18
No, I do not know the devs, but the fact that they work on fixing problems rather than ignoring their existence proves my conclusion.

Speaking of the trend of T&E forum, this is yet another proof that every negative comment about Ubuntu causes some guys to pop up and accuse the OP that he can't solve problems, that he should go back to MS and so on.

There's always someone who hasn't had a specific problem or he ignored it and then pretends everything is perfect for him and turns to insults and all.
This is not the way of evolution.

---

### Post by Viva on 2009-09-18
I don't see anything wrong with the OP, I don't think he is one of those who did not put an effort to solve his problems, neither do I think he is a troll. Really, some of you are targeting the wrong guy and I don't see the point of the *Go back to windows* seeing that he admits these are only minor annoyances. Reserve those comments for trolls and WUMs(even better, don't reply to the flame baits and use the report function):popcorn:

---

### Post by jrothwell97 on 2009-09-18
> **cguy said:**
> **Example number 1:**
They never settle on one mount point for the disks.
/mnt/sdaX
/media/sdaX
/media/mnt%sda%X
/mnt/diskX
Every new coming distro changes the damn path.
Yes, I know how to solve it in about 1 minute but it's annoying nonetheless.
True.

> **cguy said:**
> **Example number 2:**
Brasero and K3B. I always want to check for write errors after a burn, but whether these programs pull the CD back in after ejecting it is a matter of luck.

It worked in Hardy, didn't work in Intrepid, it worked in Jaunty but then stopped working in Jaunty after a reinstall.
I'm talking about the exact same system (hardware wise), whether updated or not (software wise)
This is rather odd behaviour. Try searching Launchpad for similar bug reports... I don't think I've experienced that (although Brasero refuses to work at all with my drive.)

> **cguy said:**
> **Example number 3:**
I have a FAT32 partition. Does changing file permissions work flawlessly? Again, a matter of luck.
This, I think, is partly due to the fact FAT doesn't support permissions... but still, Ubuntu's handling of this leaves a lot to be desired.

> **HappyFeet said:**
> How come I have not experienced any of the "minor" issues you have? After 40+ installs, you would think I would have come across one of those issues. I have not. *You* fail.
For the *final time*... whether or not *you* have encountered X issue in your Y installs of/years of using Ubuntu is irrelevant in this case. The OP has a problem with these, and is even reasonable enough to stay with Ubuntu despite them.

(Disclaimer: personally, I've also experienced some FAT issues, specifically when trying to configure NFS to share from a FAT filesystem.)

> **cguy said:**
> Speaking of the trend of T&E forum, this is yet another proof that every negative comment about Ubuntu causes some guys to pop up and accuse the OP that he can't solve problems, that he should go back to MS and so on.

There's always someone who hasn't had a specific problem or he ignored it and then pretends everything is perfect for him and turns to insults and all.
This is not the way of evolution.
This is true, and it's a rather disturbing trend that I've noticed lately towards looking upon Ubuntu with brown-tinted glasses, which is a slippery slope to fanboy-ism.

Again: if you've not experienced a problem, **it does not mean no-one else has** and **is not an excuse to accuse the person of trolling**. Also, Ubuntu is better than Windows (and, arguably, Mac OS X,) but it ain't perfect.

**edit**: Viva (not t0p - damn me and my mixing up of personae!) beat me to most of what I was going to say. I agree with him on this (probably *only* on this, but hey ho) - it is clear as day that the OP is not trolling.

---

### Post by Viva on 2009-09-18
t0p?:-k

---

### Post by jrothwell97 on 2009-09-18
> **Viva said:**
> t0p?:-k

Damn... sorry :oops:

Fixed.

---

### Post by running_rabbit07 on 2009-09-18
> **HappyFeet said:**
> I'm just tired of people that could not compute their way out of a wet paper bag. 

Windows is calling you. Can you feel it? :P Steve Ballmer needs a new pair of shoes. Can you help a brother out?

+1

If you have a problem ask for help. If you know a workaround to a bug. File a bug report with the workaround noted so that the devs can a permanent change. 

:-({|=

> **cguy said:**
> he ignored it and then pretends everything is perfect for him and turns to insults and all.

If it is ignorable, then is it a problem? People ignore their system slowing down to do virus scans, but do they consider it a problem? I they did, we'd have even more Linux people.

---

### Post by Garrovick on 2009-09-18
The only thing that anoys me is the lack of the ability of Linux to use advanced mp3 tagging.  But then we do have to down load bootleg code to use plain old music mp3s.   And bootleg code for commercial DVDs.

---

### Post by jrothwell97 on 2009-09-19
> **running_rabbit07 said:**
> If it is ignorable, then is it a problem? People ignore their system slowing down to do virus scans, but do they consider it a problem?

Yes, they do.

But they still use Windows, for whatever reason they do.

A bug is a bug, no matter how minor and ignorable.

---

