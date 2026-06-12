---
title: "My Teacher Confused Me..."
date: 2008-09-19
forum: The Cafe
---

### Post by kevin11951 on 2008-09-19
I was talking to my teacher about putting Ubuntu on one of our school computers as a demo for the kids, and when I asked him if i could, he responded "You can't put Linux on ANY school computers, because its no where near as secure as windows"

???:confused::confused::confused:

I'm just a little confused here?

---

### Post by kevin11951 on 2008-09-19
also, anybody know of any PDFs or web sites with security info about Linux (Preferably Ubuntu)?

---

### Post by doas777 on 2008-09-19
> **kevin11951 said:**
> I was talking to my teacher about putting Ubuntu on one of our school computers as a demo for the kids, and when I asked him if i could, he responded "You can't put Linux on ANY school computers, because its no where near as secure as windows"

???:confused::confused::confused:

I'm just a little confused here?

your teacher has no idea what she/he is talking about.

many consider [this]("http://www.debian.org/doc/manuals/securing-debian-howto/") to be a very good guide to locking down an debian system (like ubuntu).

all you really need to do to secure a ubuntu to equal the security of a windows box with Norton Internet Security is to install it. ubuntu ships with 0 network ports open by default. it is largely immune to most common malwares, and has a secure process model, that prevents bad code from doing much.

basically with ubuntu, the only way you can get bad software on you box is by installing it with the sudo command (something most sane people would not do). 

most likely the teacher just didn't trust you to set up the box (and they may be an idiot to boot), so I'm not sure corroborating evidence will help much, but good luck.


fight the power,
frank

---

### Post by RedPandaFox on 2008-09-19
> **doas777 said:**
> your teacher has no idea what she/he is talking about.

fight the power,
frank

+1 ask him/her what experience they have had with Linux, can garentee its very little

---

### Post by Bakon Jarser on 2008-09-19
[http://www.linuxsecurity.com/](http://www.linuxsecurity.com/)

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by shazbut on 2008-09-19
Reminds me of the saying:
"Those that can, do.  Those that can't, teach."

Apologies to any teachers reading this. I had plenty of good teachers during school/uni that encouraged independent thought, but also a few without any knowledge outside of their narrow syllabus.

---

### Post by Brunellus on 2008-09-19
Secunia reports on vulnerabilities for windows xp pro:

[http://secunia.com/advisories/product/22/?task=statistics](http://secunia.com/advisories/product/22/?task=statistics)


and for Ubuntu:

[http://secunia.com/advisories/product/18611/?task=statistics](http://secunia.com/advisories/product/18611/?task=statistics)

Note the difference in patched vulnerabilities.  Note also the severity of most Windows vulnerabilities--those 'system access' ones will get you every time!

To be fair, Vista is a lot better than XP, but not by much:

[http://secunia.com/advisories/product/13223/?task=statistics](http://secunia.com/advisories/product/13223/?task=statistics)

---

### Post by OutOfReach on 2008-09-19
[QUOTE=doas777]
your teacher has no idea what she/he is talking about.[/QUOTE]

^

---

### Post by akiratheoni on 2008-09-19
> **Brunellus said:**
> Secunia reports on vulnerabilities for windows xp pro:

[http://secunia.com/advisories/product/22/?task=statistics](http://secunia.com/advisories/product/22/?task=statistics)


and for Ubuntu:

[http://secunia.com/advisories/product/18611/?task=statistics](http://secunia.com/advisories/product/18611/?task=statistics)

Note the difference in patched vulnerabilities.  Note also the severity of most Windows vulnerabilities--those 'system access' ones will get you every time!

To be fair, Vista is a lot better than XP, but not by much:

[http://secunia.com/advisories/product/13223/?task=statistics](http://secunia.com/advisories/product/13223/?task=statistics)

Those are really good links.

Keep in mind that there are some bugs that Microsoft has refused to fix and instead told users of I think it was NT 4.0 to upgrade to NT 5.0 if they want the bug fixed. Guess what, that just means more money for Microsoft. Also, the fastest time between the discovery of a bug and its solution for Microsoft was... I believe 10 days? For the WMF vulnerability. But compare to FOSS: on average, it takes less than a day. Actually I'm looking at my report that I wrote (back in May so things may have changed) but it says less than eight hours. That's the average, too. Not the fastest time. Average. Granted it might mean that a bug took four hours to provide a solution then another bug 12 hours, but that's still a LOT less than Microsoft's FASTEST bugfix.

---

### Post by eragon100 on 2008-09-19
Could he be talking aboutt he fact that if a student clicks on reboot and selects recovery mode from the grub menu, he is taking directly to a root terminal withhout being asked for a password, where he can simply type rm --rf / and the computer is gone?

---

### Post by JetskiDude911 on 2008-09-19
You also have to stop and think it may not be up to your teacher. 

I don't agree with the reason, but I would think the IT department would want all the computers to be the same. I know I would. If they're all Ubuntu that'd be ok, but ideally in a computer lab you'd want all the computers to be the same (hardware and software wise). This just makes it easier when it comes time to update or re-image the computers. 

As for security, Faronics does make a version of Deep Freeze for Linux (mainly for SUSE). Really all you'd need to do is install it, make a generic user, and slap Deep Freeze on it.

---

### Post by cardinals_fan on 2008-09-19
> **eragon100 said:**
> Could he be talking aboutt he fact that if a student clicks on reboot and selects recovery mode from the grub menu, he is taking directly to a root terminal withhout being asked for a password, where he can simply type rm --rf / and the computer is gone?
That's a fault/feature with Ubuntu, not Linux in general.

---

### Post by akiratheoni on 2008-09-19
> **eragon100 said:**
> Could he be talking aboutt he fact that if a student clicks on reboot and selects recovery mode from the grub menu, he is taking directly to a root terminal withhout being asked for a password, where he can simply type rm --rf / and the computer is gone?

Or the fact that you can pop in a LiveCD of Linux in any computer (Windows or not) and delete all of the files?

Even if you removed the recovery mode from GRUB, can't you just edit GRUB at boot and add the 'single' parameter to boot into single user mode? It worked great when I pulled a random computer from the shelves in my computer class and it had CentOS on it... I was able to login and everything because of single user mode ;) I had to catalog the computers because they're being shipped off to middle schools.

---

### Post by Tatty on 2008-09-19
> **akiratheoni said:**
> Or the fact that you can pop in a LiveCD of Linux in any computer (Windows or not) and delete all of the files?

Even if you removed the recovery mode from GRUB, can't you just edit GRUB at boot and add the 'single' parameter to boot into single user mode? It worked great when I pulled a random computer from the shelves in my computer class and it had CentOS on it... I was able to login and everything because of single user mode ;) I had to catalog the computers because they're being shipped off to middle schools.

But surely if you wanted to deploy ubuntu in a school you would want to edit menu.lst to prevent the grub menu from appearing at all, so no one would have a chance to mess with it.

You would also want to change the BIOS boot order to boot from the HDD first, to stop someone trying to boot with a liveCD. Then you would want to password protect the BIOS to prevent anyone changing this. Then the only way someone is going to get around that is by physically opening the computer and removing the battery for a short while.

---

### Post by RiceMonster on 2008-09-19
Don't waste your time on it. In the end, you're really not going to gain a lot by getting any Linux distro on one of your school's computers anyway.

---

### Post by toupeiro on 2008-09-19
> **RiceMonster said:**
> Don't waste your time on it. In the end, you're really not going to gain a lot by getting any Linux distro on one of your school's computers anyway.
+1

If you  are really passionate about wanting ubuntu in your school, do it the right way.  Forget what your teacher says, you need to take it higher than a teacher.  Taking it to a Dean or principal may get you a station in a library. But, if you get turned down, leave it at that.

---

### Post by Vince4Amy on 2008-09-19
We just did it anyway, on a machine in our sixth form area.  They didn't mind so long as we didn't hose the NTFS partition. 

Mandriva our initial Distro on there did but testdisk solved that problem.

---

### Post by Bakon Jarser on 2008-09-19
> **RiceMonster said:**
> Don't waste your time on it. In the end, you're really not going to gain a lot by getting any Linux distro on one of your school's computers anyway.

-1

You never gain anything if you don't try.  And maybe you will gain a lot.  Maybe you'll end up converting 2 or 3 people to linux.  Maybe one of those people will be responsible for purchasing computers someday and they will choose linux machines.  Not trying is the only way you can really fail.

[QUOTE=Thomas Edison]“I haven't failed, I've found 10,000 ways that don't work”[/QUOTE]

---

### Post by billgoldberg on 2008-09-19
> **eragon100 said:**
> Could he be talking aboutt he fact that if a student clicks on reboot and selects recovery mode from the grub menu, he is taking directly to a root terminal withhout being asked for a password, where he can simply type rm --rf / and the computer is gone?

I doubt it. It's pretty obvious the teacher hasn't got a clue what linux really is. 

That being said, if you deploy Ubuntu on public computers, you remove that feature.

That feature is great for home users, that's why it is there.

---

### Post by stimpack on 2008-09-19
Those that can, do.
Those that can't, teach.

---

### Post by t0p on 2008-09-19
I have seen it said before that Linux is insecure because it is open source - since anyone can read the source, hackers can pore over it and find vulns.  The people who say this are promoting the security model of *security through obscurity*.

Just in case your teacher is an advocate of security through obscurity, I advise you go google the term before you speak to him.  Then you'll be able to shoot him down before he can say "nondisclosure".

---

### Post by darrelljon on 2008-09-19
Ask your teacher to explain the difference between least user privilege on Windows and Linux.
Also how to make malware executable on Windows and Linux.
Chances are they won't be able to answer.

Based on them answering "Linux is nowhere near as secure as Windows" rather than "You are not allowed" they sound ignorant more than genuinely opposed.

I don't agree with other posters who seem to want to give up. I think you should persist in debunking Linux myths and misinformation and you might raise awareness of Linux in the process. Use Live CDs and dual boots.

@eragon100; You can wipe the hard disk with greater ease in Windows. If the BIOS is locked and password-protected to boot from HDD (or CD drive removed) and GRUB parameters are disabled then Linux is way more secure. And in Windows XP I think some user settings are stored on the local hard disk (unlike Linux).

---

### Post by NovaAesa on 2008-09-19
> **stimpack said:**
> Those that can, do.
Those that can't, teach.
And those that can't teach, teach PE (physical education). :lolflag:

---

### Post by leg on 2008-09-19
Our IT manager takes pretty much the same stance and states things like "I don't trust it on my network" & "I can't garauntee the security of the network" etc etc. What he really means is I am comfortable with what I have and don't want the headache of having to change things.

---

### Post by saulgoode on 2008-09-19
> **kevin11951 said:**
> I was talking to my teacher about putting Ubuntu on one of our school computers as a demo for the kids, and when I asked him if i could, he responded "You can't put Linux on ANY school computers, because its no where near as secure as windows"

Perhaps you could ask the teacher if you could donate a computer specifically intended for running GNU/Linux (or perhaps the school has an "obsolete" Windows machine that could be used). Such a computer need not be connected to the school's network, would pose no security threat, and would still serve its intended "demo" purpose.

---

### Post by darrelljon on 2008-09-19
That's a great idea. Push for an independent unconnected (to the network) Linux machine, if you have the space. Maybe use Edubuntu.

---

### Post by clanky on 2008-09-19
It very much depends what your teacher meant by security, most people talk about security in terms of someone being able to gain access to your computer remotely to either access confidential information or to infect your computer with some sort of malware, but in a school they may think security in terms of being able to limit what students can do.  

Not saying that Windows is better or worse at doing this, but just pointing out that your teacher might not have been talking about virus protection.

---

### Post by Mr. Picklesworth on 2008-09-19
> **Brunellus said:**
> Secunia reports on vulnerabilities for windows xp pro:

*snip*

Note the difference in patched vulnerabilities.  Note also the severity of most Windows vulnerabilities--those 'system access' ones will get you every time!

I really liked Microsoft's own survey on this:
[http://dylanmccall.blogspot.com/2008/01/ubuntu-linux-606-red-hat-enterprise.html](http://dylanmccall.blogspot.com/2008/01/ubuntu-linux-606-red-hat-enterprise.html)

(Hope nobody minds the self-link; I just like my version of the graph better).

---

### Post by ShanghaiTeej on 2008-09-19
I'm sure the teacher joke is all in good fun, but if you only knew what kind of things teachers "do"and the percentage of teachers who quit after their first year, you wouldn't be poking fun at teachers.  Sorry, had to defend my profession.

As for installing Ubuntu on a school computer:  I'm all for having Linux installed on school computers because of its low cost, stability and freedom clauses, but you have to understand that schools need to have every computer function properly!  If I take a class to the computer lab and one student has problems with any computer, it's precious time knocked off of the things I want them to work on (ie interface issues, not booting correctly, not being able to save their work on the network and etc...).  Not to mention that I am unavailable for helping other students with their classwork because I'm working on a computer problem.  Now, I detest Windows and would love to have Ubuntu replace it, but if you only knew the amount of IT problems in schools today, you would want everything to be streamlined as well.

I'm rooting for Ubuntu, but a total proponent of schools having working comptuers rather than experiementing (this does not mean I think Windows is more stable).

PS - Poster:  Oh yeah, I think the teacher was either trying to deflect your question or truly does not the how Windows is less secure than Linux.

---

### Post by Dr Small on 2008-09-19
Linux is inhertantly more secure than Windows, out of the box (so to speak).

---

### Post by Jeabo on 2008-09-19
What kind of teacher is this person? Is it in computer science or programing perhaps?

---

### Post by timcredible on 2008-09-19
your teacher is a just a person - and as such, can't know everything (nobody does).  hopefully he/she knows more about the subject they teach than they do about computers.  if it's a computer class, then that's sad.....

---

### Post by god0fgod on 2008-09-19
My computing teacher doesn't have a clue sometimes lol. He is also an IT teacher.

---

### Post by Changturkey on 2008-09-19
Windows is only 50% secure with Common Sense 2009 installed.

---

### Post by kevin11951 on 2008-09-19
> **timcredible said:**
> your teacher is a just a person - and as such, can't know everything (nobody does).  hopefully he/she knows more about the subject they teach than they do about computers.  if it's a computer class, then that's sad.....

guess what... it is a computer class...

"intro to computer maintenance" to be exact.

---

### Post by kevin11951 on 2008-09-19
> **ShanghaiTeej said:**
> I'm sure the teacher joke is all in good fun, but if you only knew what kind of things teachers "do"and the percentage of teachers who quit after their first year, you wouldn't be poking fun at teachers.  Sorry, had to defend my profession.

As for installing Ubuntu on a school computer:  I'm all for having Linux installed on school computers because of its low cost, stability and freedom clauses, but you have to understand that schools need to have every computer function properly!  If I take a class to the computer lab and one student has problems with any computer, it's precious time knocked off of the things I want them to work on (ie interface issues, not booting correctly, not being able to save their work on the network and etc...).  Not to mention that I am unavailable for helping other students with their classwork because I'm working on a computer problem.  Now, I detest Windows and would love to have Ubuntu replace it, but if you only knew the amount of IT problems in schools today, you would want everything to be streamlined as well.

I'm rooting for Ubuntu, but a total proponent of schools having working comptuers rather than experiementing (this does not mean I think Windows is more stable).

PS - Poster:  Oh yeah, I think the teacher was either trying to deflect your question or truly does not the how Windows is less secure than Linux.

actually, I work with my school IT (after hours) to fix computer problems.

and i don't want Ubuntu on ALL the computers, that would be impossible, just one lab of them

---

### Post by Riffer on 2008-09-19
> **stimpack said:**
> Those that can, do.
Those that can't, teach.

As a man who worked in industry for years, went back to school in his late 30's and now has been teaching for almost 15 years, I find that remark hurtful and misleading.  I can tell you that the hardest job I've ever done is teaching and for the most part quite thankless.

Yes, as in society as a whole, some teachers are quite clueless.  In fact some shouldn't be in the profession. But having said that the majority of us work very hard in very difficult situations and are worthy of your respect.

---

### Post by cardinals_fan on 2008-09-19
> **Bakon Jarser said:**
> -1

You never gain anything if you don't try.  And maybe you will gain a lot.  Maybe you'll end up converting 2 or 3 people to linux.  Maybe one of those people will be responsible for purchasing computers someday and they will choose linux machines.  Not trying is the only way you can really fail.
And converting a couple people to Linux is a gain in what way?
> **Changturkey said:**
> Windows is only 50% secure with Common Sense 2009 installed.
Your common sense must be defective.  Mine renders Windows as close to 100% as you can get with any OS :)

---

### Post by aysiu on 2008-09-19
While it's entirely possible your teacher is a Microsoft shill, it's also possible he's simply misinformed.

Instead of being obnoxious or argumentative about it, you can simply ask him why he thinks that: "It hasn't been my experience that Linux is more insecure than Windows. What has your experience with Linux security been like? Can you show me a few of the tricks you've employed to secure Windows and to secure Linux?"

---

### Post by Bucky Ball on 2008-09-19
Teacher needs to go back to school as student! :)

Aysiu has the right approach.

---

### Post by Teamgeist on 2008-09-20
show him/her this:

[http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/)

---

### Post by Chame_Wizard on 2008-09-20
> **Teamgeist said:**
> show him/her this:

[http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/)

this site rules [IMG]http://i.fok.nl/s/worshippy.gif[/IMG]

---

### Post by cardinals_fan on 2008-09-20
> **Teamgeist said:**
> show him/her this:

[http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/)
That site always seemed strange to me.  "Keep an eye on the weather"?  Give me a break.

---

### Post by Prospero2006 on 2008-09-20
> **RiceMonster said:**
> Don't waste your time on it. In the end, you're really not going to gain a lot by getting any Linux distro on one of your school's computers anyway.

I disagree.
[http://www.neisd.net/imak/computerlabpage/history.html](http://www.neisd.net/imak/computerlabpage/history.html)

---

### Post by Bucky Ball on 2008-09-21
Prospero2006, that is just a really cool story well told. :)

---

### Post by init1 on 2008-09-21
Yeah I've had tech teachers tell me that they use "Windows 2003" at home, that browser history is the same thing as cache, and that Apache is an operating system for servers.

---

### Post by Riffer on 2008-09-21
> **Bucky Ball said:**
> Prospero2006, that is just a really cool story well told. :)

It is, I'm actually jealous, to have an Admin who is very supportive and willing to look outside of the box.

Right now in my district they're throwing out PIII with 256 RAM, because they aren't good enough to run Windows well.  Yet most classroom hasn't a basic "student" comp that does simple web searches and word processing.

---

### Post by Bucky Ball on 2008-09-21
In contrast and one reason I am touched by Prospero2006's tale is I'm at uni and they have a 'Desktop Excellence' program happening in IT at the moment. The plan is to rollout brand new, identical machines running the latest version of Vista across the entire campus! In the fine print, they will make available Linux Red Hat and Mac machines if staff or students apply (and that only after I emailed to point out a few holes in this plan). I have always attempted to do all my computing at home, even when using Windows, as I like reliablity. Using the studios and audiolab last year was like a lucky dip. Better off building one at home (or trying). So will be sticking to library computers for the catalogue as usual anyhow.

For an institution that is supposed to be forward thinking and prides itself on its IT and music tech departments (among other things), how the hell could all those creative, diverse thinkers imagine that this plan is cutting edge or anything to boast about when institutions worldwide are seeing the benefits of opensource? Actually presents the uni as a bit behind the times to me. But money talks, huh. Well, it ain't sayin' much! :evil: :-k

---

### Post by Prospero2006 on 2008-09-21
Thanks for comments!

---

### Post by lukjad on 2008-09-21
Once, at the very beginning of my Ubuntu life, a classmate told me that Linux was not a secure OS, it was just unknown. He made me scared for a while (1/2 an hour) and then I remembered running Windows 98 on my PC with 40 AV/Anti-spyware programs and still getting infected and I just ignored him. :-)

Try to show your teacher a live CD. If that doesn't impress the teacher enough to let you continue, move on. There will be other times for you to talk or even other people who are more responsive.

---

### Post by cardinals_fan on 2008-09-21
> **lukjad007 said:**
> 
Try to show your teacher a live CD. If that doesn't impress the teacher enough to let you continue, move on. There will be other times for you to talk or even other people who are more responsive.
Definitely SliTaz.

---

### Post by lukjad on 2008-09-21
Why is that? I would have thought that TEENpup would be a better choice.

---

### Post by cardinals_fan on 2008-09-21
> **lukjad007 said:**
> Why is that? I would have thought that TEENpup would be a better choice.
SliTaz is fast, simple, and elegant.

---

### Post by lukjad on 2008-09-21
Ah. does it play movies and music? Open text docs?

---

### Post by cardinals_fan on 2008-09-21
> **lukjad007 said:**
> Ah. does it play movies and music? Open text docs?
The new cooking version includes MPlayer.  A text editor is included, and AbiWord is available through Tazpkg.

By the way, the new iso (including MPlayer) is 28 megabytes.

---

### Post by lukjad on 2008-09-21
*Whistles*

---

### Post by SirBismuth on 2008-09-23
> **leg said:**
> Our IT manager takes pretty much the same stance and states things like "I don't trust it on my network" & "I can't garauntee the security of the network" etc etc. What he really means is I am comfortable with what I have and don't want the headache of having to change things.

I am glad that our IT Manager has the opposite view.  And, he is also a Linux fan.  Our firewall, webserver, and mail server are all linux-based machines, I always say to protect the end-users with Windows from themselves :D

His idea is to eventually roll-out Linux company wide, with Windows running in VirtualBox for those apps that don't work in Linux.

B

---

