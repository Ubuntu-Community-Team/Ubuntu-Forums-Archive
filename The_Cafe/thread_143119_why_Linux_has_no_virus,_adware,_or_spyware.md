---
title: "why Linux has no virus, adware, or spyware?"
date: 2006-03-11
forum: The Cafe
---

### Post by cnbiz850 on 2006-03-11
Can anyone please elaborate or rationalize it as to why Linux has no such things?  IMO, Linux perhaps is just lucky now because it is relatively small.

---

### Post by Dark Nations on 2006-03-11
There be tons of infecting crud for linux. But it requires the person using the computer to be a moron long enough to use root mode.

---

### Post by Stormy Eyes on 2006-03-11
[QUOTE=cnbiz850]Can anyone please elaborate or rationalize it as to why Linux has no such things?  IMO, Linux perhaps is just lucky now because it is relatively small.[/QUOTE]

There's plenty of malware for Linux. However, most of it depends on the user being a complete moron.

---

### Post by Darkness3477 on 2006-03-11
I was told by someone that because of the way the file system is set up with Linux distros, it becomes hard to make a virus. And also the fact you need to  compile the source code first....

Dunno if thats right, but it is what I was told.

---

### Post by banjobacon on 2006-03-11
[QUOTE=Dark Nations]There be tons of infecting crud for linux. But it requires the person using the computer to be a moron long enough to use root mode.[/QUOTE]
You don't need to be root to *run* spy/adware.

---

### Post by mstlyevil on 2006-03-11
[QUOTE=cnbiz850]Can anyone please elaborate or rationalize it as to why Linux has no such things?  IMO, Linux perhaps is just lucky now because it is relatively small.[/QUOTE]

There are actually viruses for Linux but they are rare. Linux is by default run at a more secure permission level than Windows. As long as you run as a regular user, malware can not install on the root unless you tell it to. Linux ask for permission before anything is installed whereas a Windows box does not unless you set up limited user accounts first. Linux is just harder to infect but it is not impossible as some would want you to believe. You should practice good security no matter what operating system you run or you are putting yourself at risk of infection.

---

### Post by Stormy Eyes on 2006-03-11
[QUOTE=Darkness3477]I was told by someone that because of the way the file system is set up with Linux distros, it becomes hard to make a virus. And also the fact you need to  compile the source code first....

Dunno if thats right, but it is what I was told.[/QUOTE]

There's a little more to it. You don't have to compile shell scripts, Perl scripts, etc. If I sent you a malicious Perl script, you would have to either do the following:
```
chmod +x evil.pl
mv evil.pl /usr/local/bin/evil.pl
evil.pl
```
or
```
perl ./evil.pl
```
Now, if you run a script that some stranger emailed to you without first checking to make sure it's kosher, then you deserve the consequences.

---

### Post by Robgould on 2006-03-11
Linux can have viruses.

---

### Post by Darkness3477 on 2006-03-11
True.... But I always check the source code of things. Understandibly I sometimes don't understand it as well as I would like (I'm still learning to code, and rather slowly, too) but I don't open things from people I don't trust.

---

### Post by Iandefor on 2006-03-11
It's a combination of Linux user setups tending to have a more secure default, and the fact that almost nobody writes malware for Linux.

---

### Post by Dark Nations on 2006-03-11
Isn't it true that Microsoft Windows is a virus? I've heard it said dozens of times over the years.

---

### Post by mstlyevil on 2006-03-11
[QUOTE=Dark Nations]Isn't it true that Microsoft Windows is a virus? I've heard it said dozens of times over the years.[/QUOTE]

We could really live without the MSFT bashing. Try to stay on topic.

---

### Post by Iandefor on 2006-03-11
[quote=Dark Nations]Isn't it true that Microsoft Windows is a virus? I've heard it said dozens of times over the years.[/quote] Now, now, let's not hijack the thread ;)...

---

### Post by Stormy Eyes on 2006-03-11
[QUOTE=Dark Nations]Isn't it true that Microsoft Windows is a virus?[/QUOTE]
Please save the Microsoft bashing for the ricer kiddies at the Gentoo Forums.

---

### Post by mrgnash on 2006-03-11
[QUOTE=Darkness3477]I was told by someone that because of the way the file system is set up with Linux distros, it becomes hard to make a virus. And also the fact you need to  compile the source code first....

Dunno if thats right, but it is what I was told.[/QUOTE]

The first statement is pretty spot-on. The majority of Linux desktop users, particularly with Debian flavours, download their applications from repos - for obvious reasons, the risk of viral infection is substantially lower than for the average Windows user downloading software from here, there and everywhere. I think the fact that Linux users are using mostly open-source (e.g: free) software they're less likely to resort downloading 'cracked' applications from P2P networks.

Add to that the fact that even the commercial/user-installed applications we use are installed to our /home/username directory (e.g ~/.RealPlayer) and are usually self-contained binaries without access to sensitive system areas.

---

### Post by Leo_01 on 2006-03-11
[QUOTE=Iandefor]It's a combination of Linux user setups tending to have a more secure default, and the fact that almost nobody writes malware for Linux.[/QUOTE]
Write virus for Win 32 and you shall burn!
Write virus for the big apple and you will be cursed!
Write virus for Linux and you will be most hated man on earth!

---

### Post by ice60 on 2006-03-11
[QUOTE=Dark Nations]Isn't it true that Microsoft Windows is a virus? I've heard it said dozens of times over the years.[/QUOTE]
you obviously know nothing about computer security, lol

i noticed you haven't bothered replying to the thread you started about securing your Dad's PC [here](http://www.ubuntuforums.org/showthread.php?t=142760). i would have helped you secure the computer but i can't be bothered now. anyway, i don't beleive you really want to secure it anyway.

---

### Post by Iandefor on 2006-03-11
Oh, and as an aside, here's an article about a Linux virus:

[http://www.eweek.com/article2/0,1895,1936666,00.asp](http://www.eweek.com/article2/0,1895,1936666,00.asp)

---

### Post by Jucato on 2006-03-11
Hmm... I'm just curious and all but...
How do spyware/adware really work and how will it be able to infect a Linux system?
(I'm less worried about viruses because I do not install stuff outside of reliable sources. Even KDE-Look/KDE-Apps stuff I take with a grain of salt)

---

### Post by DigitalDuality on 2006-03-11
My take on it...

1.  FIrst off, Linux only makes up about 3-5% of the computers on the net.  (Even though this does include 60-70% of web servers are Linux/BSD).  The majority is simply windows.  You want it to spread.  Why write for a minority OS?

2.  Security practices of users.  Even Linux noobs, tend to know a bit more about computers than the average person.  We all tend to practice safer surfing and installs of apps.

3.  Built in security to Mac and Linux/BSD variants.  WIndows is the only OS where you have full admin/root rights from first boot.  Rarely do people actually use the "power user" or other options in Windows.  This is a huge advantage.

4.  IE being interwoven into the OS has to be about the worst idea of all time, not to mention IE 6 and below (in terms of security) is a piece of crap.  And no, this is not MS bashing.  It's fact. Viruses don't infect operating systems.  It infects software. So ... dont imbed software as part of the OS! Especially an app that's main use is accesing the internet.

---

### Post by cnbiz850 on 2006-03-12
Why can't you get virus, spyware, etc. by clicking on links in, say, Firefox on Linux the same way as on Windows?

---

### Post by mstlyevil on 2006-03-12
[QUOTE=cnbiz850]Why can't you get virus, spyware, etc. by clicking on links in, say, Firefox on Linux the same way as on Windows?[/QUOTE]

Because Linux requires a package manager to install software. You would still have to give your password to give it permission to install.

---

### Post by cnbiz850 on 2006-03-12
[QUOTE=mstlyevil]Because Linux requires a package manager to install software. You would still have to give your password to give it permission to install.[/QUOTE]

Can't the spyware etc. be a browser "live-in" or plug-in? Javascripts or java applets can be saved without much of your knowledge if you don't pay particular attention, right? Why can't those be spyware etc? Aren't Linux users over confident on that while because of that they are under more danger of being infected?

---

### Post by Jucato on 2006-03-12
That was what I was thinking about, too. I generally set Konqueror to ask my permission everytime a Javascript is going to be run. What would happen if I allowed Java/Javascript globally, and that script had malicious code or code to install spyware? or something like that... (guess it's getting pretty obvious that I have so little knowledge about security, viruses, and malware :D )

---

### Post by mstlyevil on 2006-03-12
[QUOTE=cnbiz850]Can't the spyware etc. be a browser "live-in" or plug-in? Javascripts or java applets can be saved without much of your knowledge if you don't pay particular attention, right? Why can't those be spyware etc? Aren't Linux users over confident on that while because of that they are under more danger of being infected?[/QUOTE]

Some linux users are over confident as are many Mac users. Browser pluggins still will be contained to the browser or the home directory and can be easily removed since they can not be installed on the root file system. The same would apply for javascript. The fact of the matter is that there is very little spyware/malware written for a linux system. Even if someone managed to write some it is limited in what it can do because of the stricter permissions in most Linux distros. Now if the user is running as root, they are fair game to having their system borked. Most Linux users rarely or never run as root making writing spyware a difficult chore.

---

### Post by jpkotta on 2006-03-12
I'm no expert, but I believe that Java and JavaScript are sandboxed so that they really can't access your system.  That is, they can't install software, but ActiveX can, which is one reason why IE is a security nightmare.

---

### Post by jpkotta on 2006-03-12
I always wonder about these discussions about "Linux is better, because you run as a user, not as root."  In many ways, this is true, of course.  But all of *my* data is accessible by me.  If I get infected by a malicious program that deleted my $HOME, then so what if the rest of my system is untouched?  I lost all of *my work* (or at least what I didn't backup), not some programs that were easily reinstalled...

So make sure you back stuff up and make sure sensitive information is encrypted.

---

### Post by briancurtin on 2006-03-12
hey heres a question ive never seen before

---

### Post by mstlyevil on 2006-03-12
[QUOTE=jpkotta]I always wonder about these discussions about "Linux is better, because you run as a user, not as root."  In many ways, this is true, of course.  But all of *my* data is accessible by me.  If I get infected by a malicious program that deleted my $HOME, then so what if the rest of my system is untouched?  I lost all of *my work* (or at least what I didn't backup), not some programs that were easily reinstalled...

So make sure you back stuff up and make sure sensitive information is encrypted.[/QUOTE]

Nothing beats practicing good security habbits and regular backups. You can make windows use the same permission levels but most Windows users don't bother.

---

### Post by Jucato on 2006-03-12
So it's possible that a malicious java/javascript/whatever code would be able to affect your $HOME (for example, delete some stuff there), since it doesn't need root permissions?

---

### Post by Lovechild on 2006-03-12
There are a number of reasons why Linux doesn't have these problems:

We are not enough of a desktop marketshare for the malware writers to target us, yet.

Everybody on Linux generally installs packages using their package manager, thus from their vendor and all serious distributions MD5SUM check and sign their packages.  So no inserting packages with backdoors on random warezsites and expecting that a certain amount of users would be dumb enough to try this.

Linux has better general security, in Fedora (the distro I know the best thus I use that in my example) we have a default restrictive firewall, all programs talking to the world are jailed with SELinux and there are multiple stack protection schemes in place - exploiting such a system requires a great deal more work than a Windows box.

Linux users as a general rule are more security aware, although Linux has become easier - most people who use it have a certain amount of knowledge and thus know not to randomly install stuff off the web. 

Fixes for Linux exploits are generally issued quickly, for such critical flaws that allow remote users to take over your box, FC3 had an average rate of pushing fixes of less than a day. Windows in the same period not only had 3 times the amount of critical bugs reported took on average 46 days to fixed them as well. This works in the malware writers favor because the longer a hole is known and a fix isn't to be expected fully deployed for a while this is a great way to enter the system. 46 days translates into an eternity when you factor in the system propagation down the userbase is slow. 

The past couple of years security has really taken the mainstream coders with storm, not just Microsoft have actually begun thinking of problems in terms of code safety. But everyone has, UNIX has always been a more secure model by design and UNIX coders have a lot of experience hardening code as the most crictal machines have historically been UNIX boxes. This translates into years of being ahead of the game. I'd wager that our code is on the average better in terms of security because this is an issue well known to us.

---

### Post by mrgnash on 2006-03-12
[QUOTE=jpkotta]I always wonder about these discussions about "Linux is better, because you run as a user, not as root."  In many ways, this is true, of course.  But all of *my* data is accessible by me.  If I get infected by a malicious program that deleted my $HOME, then so what if the rest of my system is untouched?  I lost all of *my work* (or at least what I didn't backup), not some programs that were easily reinstalled...

So make sure you back stuff up and make sure sensitive information is encrypted.[/QUOTE]

Don't forget that you can modify the permissions of files and directories with chmod. If you wanted to protect your /home/username/work/ folder for example:

```
sudo chmod -R 640 /home/username/work/
```

Or something along those lines anyway. That way, a malicious program/script/whatever still needs root permission in order to nuke your sensitive information :)

---

### Post by Jucato on 2006-03-12
[QUOTE=mrgnash]Don't forget that you can modify the permissions of files and directories with chmod. If you wanted to protect your /home/username/work/ folder for example:

```
sudo chmod -R 640 /home/username/work/
```

Or something along those lines anyway. That way, a malicious program/script/whatever still needs root permission in order to nuke your sensitive information :)[/QUOTE]

Hmm... let me review my chmod. That will give the user/owner read-write (no exectute) permissions, group read (no write-exectute) permissions, and others no permissions at all, right?

Question: Java/Javascript running on your browser would be considered by the system as "user" or "others"? :confused:

---

### Post by mrgnash on 2006-03-12
Yep that's right. As for your second question.. I don't know, I *assume* that it would be classed as 'other' but I'm not 100% on that.

---

### Post by tseliot on 2006-03-12
[QUOTE=cnbiz850]Can anyone please elaborate or rationalize it as to why Linux has no such things?  IMO, Linux perhaps is just lucky now because it is relatively small.[/QUOTE]
If you are interested in that feature (spyware and viruses) you can always require it in Dapper's wishlist :p 

We need to compete with Vista after all :p 


Just kidding, eh.. (win users don't flame me :) )

---

### Post by Toxicity999 on 2006-03-12
[QUOTE=tseliot]If you are interested in that feature (spyware and viruses) you can always require it in Dapper's wishlist :p 

We need to compete with Vista after all :p 


Just kidding, eh.. (win users don't flame me :) )[/QUOTE]

Better yet.... LEt's invest millions of dollars into such a feature! :D 

Hah... joking aside... Sure you CAN exploit a Linux system, just the same as a windows system. But the major differenced lay in default permission settings, and the fact that everyone and their brothers daughter uses windows. And said daughter is probably 9 years old writing code to exploit windows. *cough* That point being it just has more focus from the "I WILL DESTROY YOU!" Community y'know?

---

### Post by TrendyDark on 2006-03-12
[QUOTE=Robgould]Linux can have viruses.[/QUOTE]

Don't go PhD on us here. . .wow. lol :p 

Is there a place where you can find a list of viruses that infect linux systems?

---

### Post by curtis on 2006-03-12
What about a chrooted browser?
That would in theory stop stuff such as that.. but would also increase space needed for libaries and cause other issues...

---

### Post by dabear on 2006-03-12
[QUOTE=curtis] but would also increase space needed for libaries a[/QUOTE]
Wouldn't it be possible to symlink to the needed libraries to avoid this?

---

### Post by ssam on 2006-03-12
[QUOTE=curtis]What about a chrooted browser?
That would in theory stop stuff such as that.. but would also increase space needed for libaries and cause other issues...[/QUOTE]

i have wondered about that, or running the browser as a different user. i imagine that firefox is probably the most dangerous thing most users user (not because its poorly writen or anything like that, but because its a large complex applications that deals with lots of untrusted data, has several built in intepreted languages etc). i think it would be relatively simple to write a firefox extension that sent spam, logged all your web passwords or posted your banks log in cookies somewhere.

i suppose you would get problems if the user wanted to save/download a file. there would probably need to be a script for copying the downloaded file out of the chroot and putting it somewhere useful. this might defeat the original purpose of the chroot.

as for reasons that there are few viruses on linux: i like the theory that there are windows programmers who get frustrated with the closedness of the system. they want to implement some feature but with out seeing the windows source they can't. they get frustrated and start to hate windows. now you have a competent programmer who wants to break windows.

on linux the top programmers face no barriers. any agression towards things not working can be channelled into bug fixing.

---

### Post by Krigl on 2006-03-12
Sadly, I can't provide link but I've read that there's about 60 000 viruses for Windows, about 40 for Macs and the same for Linux. Not to mention that Linux and Macs viruses work mostly in laboratories. Even if you compare the percents of people using them against number of Win machines it's obvious that for Linux you need more than some stupid vBScript. Rather some script kiddie will try to own or DDoS Linux box but viruses are minor threat, assuming that you're not moron and have some healthy security and browsing habits etc. etc. like everyone before me already mentioned. One quote by the guy who's been using comps "since they were made of wood" and who had clean Winbox with IE, Outlook etc. without antiviruses and firewall: "You just need to use the brains between your ears. If someone can't do it then only holy water can help him - full bathtub and drown'im to spare him from suffering."

---

### Post by knalle on 2006-03-12
[QUOTE=Lovechild]Linux users as a general rule are more security aware, although Linux has become easier - most people who use it have a certain amount of knowledge and thus know not to randomly install stuff off the web. 
[/QUOTE]

hahaha, and while you guys are wasting time on this discussion a real security scandal is unfolding in ubuntu under your nose:

[https://launchpad.net/distros/ubuntu/+bug/34606](https://launchpad.net/distros/ubuntu/+bug/34606)

---

### Post by Iandefor on 2006-03-12
[quote=knalle]hahaha, and while you guys are wasting time on this discussion a real security scandal is unfolding in ubuntu under your nose:

[https://launchpad.net/distros/ubuntu/+bug/34606]("https://launchpad.net/distros/ubuntu/+bug/34606")[/quote] What scares me is the fact that an error which leaves the root password in cleartext seems to be classified as "normal" in terms of severity.

---

### Post by knalle on 2006-03-12
[QUOTE=Iandefor]normal[/QUOTE]

no thats me, i sat the priority to normal because i was afraid this is was know issue and i would be yelled at by the zealots

---

### Post by Iandefor on 2006-03-12
[quote=knalle]no thats me, i sat the priority to normal because i was afraid this is was know issue and i would be yelled at by the zealots[/quote] Oh, ok. That explains it :-).

---

### Post by kittycatsexycat on 2006-03-12
does that mean that at the moment no ones computer is safe...?:-#

---

### Post by knalle on 2006-03-12
[QUOTE=kittycatsexycat]does that mean that at the moment no ones computer is safe...?:-#[/QUOTE]

looks like all ubuntu breezy 5.10 installations and all installations upgraded from breezy 5.10 can have this problem, check yourself

```
grep -r yourpassword /var
```

---

### Post by Iandefor on 2006-03-12
[quote=kittycatsexycat]does that mean that at the moment no ones computer is safe...?:-#[/quote] Only people using Breezy- silly people like me using Dapper aren't affected.

---

### Post by ssam on 2006-03-12
[QUOTE=knalle]hahaha, and while you guys are wasting time on this discussion a real security scandal is unfolding in ubuntu under your nose:

[https://launchpad.net/distros/ubuntu/+bug/34606](https://launchpad.net/distros/ubuntu/+bug/34606)[/QUOTE]

no problem on my my computer. i had a good look through to mentioned files and not found my password. i used a default in install. are there specific things you need to do to make this happen? if anyone has this problem on there computer, they should set this bug to confirmed.

PS:
you guy should check your ~/bash_history after doing this and delete all the line that contain your password (and dont forget that when you save it nano or gedit will most likely keep the old version as bash_history~)

---

### Post by knalle on 2006-03-12
[QUOTE=ssam]no problem on my my computer[/QUOTE]

ah, but then its false alarm then, and those that found the password on their computers is just lying to be interesting ([http://ubuntuforums.org/showthread.php?t=143334)](http://ubuntuforums.org/showthread.php?t=143334)).

i'll close the bug and say that SSAM can confirm that this bug is a false alarm

---

### Post by ssam on 2006-03-12
[QUOTE=knalle]ah, but then its false alarm then, and those that found the password on their computers is just lying to be interesting ([http://ubuntuforums.org/showthread.php?t=143334)](http://ubuntuforums.org/showthread.php?t=143334)).

i'll close the bug and say that SSAM can confirm that this bug is a false alarm[/QUOTE]

i am sorry if i sounded like i was denying this. it does seem quite serious, and i am definatly not accusing anyone of lying.

i have seen plenty of bugs that affect only a small number of people, or that only happen in odd circumstances. it seems not to effect me, so maybe it only effects some users.

my request that someone confirms it is so that it gets noticed by the developers. setting the severity higher will help too. this is a major security bug. but i'd like to know if this effects only a small minory, or a vast majority.

---

### Post by dragonfoundry on 2006-03-12
I must admit as an ex windows user its took some getting used to that I dont have to run anti spyware, etc. it felt like I was walking down the road in the nude to begin with! :) 

The more I use Linux the more it is apparent that it is designed with security high on the agenda with the implementation of permissions. Nothing is bullet proof but I feel happier running Linux

I will still be doing backups though - security paranoia hasnt quite worn off ;)

---

### Post by mstlyevil on 2006-03-12
[QUOTE=dragonfoundry]I must admit as an ex windows user its took some getting used to that I dont have to run anti spyware, etc. it felt like I was walking down the road in the nude to begin with! :) 

The more I use Linux the more it is apparent that it is designed with security high on the agenda with the implementation of permissions. Nothing is bullet proof but I feel happier running Linux

I will still be doing backups though - security paranoia hasnt quite worn off ;)[/QUOTE]

Don't ever ever let the security paranoia wear off. Always practice good security habbits no matter what OS you run because none are absolutely impenetreble.

---

### Post by knalle on 2006-03-12
[QUOTE=ssam]my request that someone confirms it is so that it gets noticed by the developers. setting the severity higher will help too. this is a major security bug. but i'd like to know if this effects only a small minory, or a vast majority.[/QUOTE]

[https://launchpad.net/distros/ubuntu/+bug/34606](https://launchpad.net/distros/ubuntu/+bug/34606)

its confirmed now

---

### Post by OffHand on 2006-03-12
[QUOTE=knalle][https://launchpad.net/distros/ubuntu/+bug/34606](https://launchpad.net/distros/ubuntu/+bug/34606)

its confirmed now[/QUOTE]
I confirmed it and set the priority higher.

---

### Post by knalle on 2006-03-12
[QUOTE=subsonic_shadow]I confirmed it and set the priority higher.[/QUOTE]

good, hopefully this should be very easy to fix, just a script that kills the logfile

---

### Post by lordofkhemenu on 2006-03-12
[quote=jpkotta]I always wonder about these discussions about "Linux is better, because you run as a user, not as root." [/quote]
Unless of course, you are using Linspire...:p

---

### Post by mstlyevil on 2006-03-12
[QUOTE=lordofkhemenu]Unless of course, you are using Linspire...:p[/QUOTE]

Be nice. You can secure Linspire just as you can any other Linux distro if you create a user account during the install.

---

### Post by Jucato on 2006-03-12
Excuse me... but...
In the bug report, it was mentioned that a security patch was uploaded to fix this...
Being an ignoramus in security and patching... where can I get this patch and how can I patch my system? :D

---

### Post by jpkotta on 2006-03-16
[QUOTE=ssam]i have wondered about that, or running the browser as a different user. i imagine that firefox is probably the most dangerous thing most users user (not because its poorly writen or anything like that, but because its a large complex applications that deals with lots of untrusted data, has several built in intepreted languages etc). i think it would be relatively simple to write a firefox extension that sent spam, logged all your web passwords or posted your banks log in cookies somewhere.

i suppose you would get problems if the user wanted to save/download a file. there would probably need to be a script for copying the downloaded file out of the chroot and putting it somewhere useful. this might defeat the original purpose of the chroot.

as for reasons that there are few viruses on linux: i like the theory that there are windows programmers who get frustrated with the closedness of the system. they want to implement some feature but with out seeing the windows source they can't. they get frustrated and start to hate windows. now you have a competent programmer who wants to break windows.

on linux the top programmers face no barriers. any agression towards things not working can be channelled into bug fixing.[/QUOTE]

It's interesting that you say this.  I just finished Steven Levy's *Hackers: Heros of the Computer Revolution*, which contains a related anecdote.  I've just returned the book to the library, so this is from memory, and I'll get some details wrong.  

In the 60s and 70s, hackers at MIT wrote a time-sharing operating system for their computers called ITS (Incompatible Time-Sharing System, a pun on CTS, the Compatible TS).  There were many other TSs around, and the hackers would delight in crashing them, mostly because they didn't like the idea of the system implementing things like user accounts, passwords, and other restrictions (you'd have to read the book to understand where they were coming from with this), but also because of the challenge.  So for their TS, the hackers implemented a command, literally something like "crash_system", that would make it trivial to crash the system.  Because it was that easy to do, no one bothered to do it.


[QUOTE=mrgnash]Don't forget that you can modify the permissions of files and directories with chmod. If you wanted to protect your /home/username/work/ folder for example:

```
sudo chmod -R 640 /home/username/work/
```

Or something along those lines anyway. That way, a malicious program/script/whatever still needs root permission in order to nuke your sensitive information :)[/QUOTE]

No, it doesn't.  That's the point I was making: if you have access to your files, then any program that you run will too.  Personally, I set my umask to 0077, so *only* I have permission to my files by default.  But this wouldn't prevent me from doing "rm -rf $HOME", nor would it prevent any program I run from doing that.  Thus: backup and encrypt.

BTW, that will make the work dir unlistable.  I usually use find and chmod files and directories separately.

---

### Post by strabes on 2007-07-25
Since when did everyone on ubuntuforums become a jerk? Are digg users starting to use linux and bringing their attitudes, pride, and superiority complexes with them?

---

### Post by vexorian on 2007-07-26
hmmm tons of nonsense in this thread.

- Java and javascript are typically in sandboxes (at least with firefox, konqueror, etc ) THEY CANNOT MESS WITH YOUR INSTALLATION ...
- Windows is less secure by design, not by the lack of exposure, and I am talking about all users running on root all the time, or the fact that it only takes you to insert an USB disk to make windows run code, or the fact that internet explorer's plugin system is not sandboxed , etc ,etc ,etc , etc... And the most fun is the one in which even a non administrator app can install itself so next time windows boots it runs as administrator is fun enough (won't ellaborate since I don't want more of those viruses nearby my computer)

Oh, and hide the extensions of files but determine wheter  a file is executed by double click or opened by a program depending on the extension, and allow people to add the icon of an wmv file to an executable file...

And the delete stuff thing: Yes a virus can clean your /home/ folder!, but now stop and think, how much harm to the world can a virus do if it is unable to join stealth mode? It needs to hide itself from the user so the user can then pass the infection to other computers, any virus that instanlty wipes your home partition will only harm you and be unable to be a problem. (you should have made a backup anyways)

Seriously, the worst windows malware are not viruses that want to eat your files, but viruses/etc that spy on you and also convert your computer into a mail server or make sure you watch a lot of porn ads or tries to listen to your credit card number.

And security through limited number of users is A MYTH , apache is far more used than ISS but ISS is the one most exploited, there goes a good counter example.

---

### Post by astromech on 2007-07-26
Anyone use the linux antivirus programs? Ever find anything? Please let us know!

---

### Post by frodon on 2007-07-26
> **astromech said:**
> Anyone use the linux antivirus programs? Ever find anything? Please let us know!Strange, some like to revive such old threads, last post before the revive more than one year ago !

Antivirus are only needed/useful when your computer is a server which communicate with windows computers, so if you don't want to send files with viruses to windows computers you need an antivirus on your linux system, this is the only case where an antivirus is useful on linux.

---

### Post by slimdog360 on 2007-07-26
because linux sucks

---

### Post by Billy_McBong on 2007-07-26
> **slimdog360 said:**
> because linux sucks
[COLOR="Blue"]
why would you say this on a Linux forum?[/COLOR]

---

### Post by LaRoza on 2007-07-26
> **Billy_McBong said:**
> [COLOR="Blue"]
why would you say this on a Linux forum?[/COLOR]
...or any forum?

I don't think he was serious, but I am not sure.

---

### Post by Sporkman on 2007-07-26
> **ssam said:**
> PS:
you guy should check your ~/bash_history after doing this and delete all the line that contain your password (and dont forget that when you save it nano or gedit will most likely keep the old version as bash_history~)

:lol: I was thinking the same thing.

---

### Post by Sporkman on 2007-07-26
> **vexorian said:**
> - Java and javascript are typically in sandboxes (at least with firefox, konqueror, etc ) THEY CANNOT MESS WITH YOUR INSTALLATION ...


Whenever I visit a web page that tries to load a java applet, Firefox give me a big loud warning saying that a java applet can read & destroy data...

---

### Post by Sporkman on 2007-07-26
> **Billy_McBong said:**
> [COLOR="Blue"]
why would you say this on a Linux forum?[/COLOR]


Perhaps he makes his living writing viruses, adware, or spyware.

---

### Post by unregistered-user on 2010-03-23
I got one, I was bored so I wrote one up and put it on my (very) old computer (had the same version of ubuntu) to put it out of its misery. But the chances of you getting one online is very unlikely.

---

### Post by overdrank on 2010-03-23
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

