---
title: "Nautilus as root - No Global Menu"
date: 2012-01-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-01-20
I don't have any option in the Global Menu when I run Nautilus as root. Therefore I have no way to access these options (and their sub-options): File, Edit, View, History, Go, Bookmarks, Help. 

All I can do is what's available in the right-click context menus.

---

### Post by Buntumatic on 2012-01-20
So what. Do not run Nautilus as root. There is no need to run Nautilus as root. Period.

---

### Post by effenberg0x0 on 2012-01-20
Why answer at all? I run whatever I want, in any way I want, in my PC.

Kind Regards,
Effenberg

---

### Post by Buntumatic on 2012-01-20
Right, if you open your home for drug dealers you will be punished. Agree?
If you compromise your box and it is connected to the internet it becomes a platform for cyber-criminals. 

The two stupidest things a computer user can do is:

Running X as root;
using computer as root.

Do not do it. It is not up for discussion. It is a good practice established long time ago.

---

### Post by effenberg0x0 on 2012-01-20
I am not a newbie and am completely aware of everything you said. But it's up to me when and/or why use any resource. 

My question is why the global menu doesn't show now, because it did in the past. If you can't answer that, just don't answer anything.

---

### Post by ventrical on 2012-01-20
> **effenberg0x0 said:**
> I don't have any option in the Global Menu when I run Nautilus as root. Therefore I have no way to access these options (and their sub-options): File, Edit, View, History, Go, Bookmarks, Help. 

All I can do is what's available in the right-click context menus.

Yep. same here .. do you think there may be a switch for that ? ie; #nautilus -<switch>

---

### Post by BC59 on 2012-01-20
Has to do with the privileges. You changed something and you don't remember it. Maybe removing .ICEauthority and .Xauthority?

---

### Post by effenberg0x0 on 2012-01-20
> **ventrical said:**
> Yep. same here .. do you think there may be a switch for that ? ie; #nautilus -<switch>

Hey Ventrical,
JBicha already reported. Just found it. It's an environment variable...
See [https://bugs.launchpad.net/indicator-appmenu/+bug/592842](https://bugs.launchpad.net/indicator-appmenu/+bug/592842)

I wonder why a respected developer would want to use Nautilus as root, since user Buntumatic said it very clear that it would be stupid and is forbidden.

---

### Post by effenberg0x0 on 2012-01-20
> **BC59 said:**
> Has to do with the privileges. You changed something and you don't remember it. Maybe removing .ICEauthority and .Xauthority?

Hi, it seems that $UBUNTU_MENUPROXY is not exported for root.

**EDIT:**
Confirmed. You can see the variable for standard users but not for root. Exporting it for root "fixes" it.
```
$ echo $UBUNTU_MENUPROXY
libappmenu.so

```

---

### Post by BC59 on 2012-01-20
I cannot reproduce it because I don't use global menu.

To delete the global menu and retrieve the normal window menu:

```
sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qt
```

---

### Post by Buntumatic on 2012-01-20
> **effenberg0x0 said:**
> I am not a newbie and am completely aware of everything you said. But it's up to me when and/or why use any resource. 

My question is why the global menu doesn't show now, because it did in the past. If you can't answer that, just don't answer anything.

Not newbie? But only newbies have inevitable urge to run things as root. I remember when I was a noob I wanted to run things as root, too. Just setting all the permissions properly felt too cumbersome. It was back in 1996, didn't take long until I started understand the security model of UNIX. Grow up. The whole POSIX security is built on principle 'default denied'. In other words, never elevate your rights without a good reason. "It's my box I do whatever I want" is not a valid reason, it just displays immaturity and lack of understanding of basics.

---

### Post by effenberg0x0 on 2012-01-20
> **BC59 said:**
> I cannot reproduce it because I don't use global menu.

To delete the global menu and retrieve the normal window menu:

```
sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qt
```

Yes, it has been my option too for the machines I use. I'm not a fan of the global menu..

---

### Post by philinux on 2012-01-20
> **Buntumatic said:**
> Right, if you open your home for drug dealers you will be punished. Agree?
If you compromise your box and it is connected to the internet it becomes a platform for cyber-criminals. 

The two stupidest things a computer user can do is:

Running X as root;
using computer as root.

Do not do it. It is not up for discussion. It is a good practice established long time ago.

Unless I missed something, it can happen, gksu nautilus has always been used when necessary. This is not X as root or logging in as root.

 [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by effenberg0x0 on 2012-01-20
> **Buntumatic said:**
> Not newbie? But only newbies have inevitable urge to run things as root. I remember when I was a noob I wanted to run things as root, too. Just setting all the permissions properly felt too cumbersome. It was back in 1996, didn't take long until I started understand the security model of UNIX. Grow up. The whole POSIX security is built on principle 'default denied'. In other words, never elevate your rights without a good reason. "It's my box I do whatever I want" is not a valid reason, it just displays immaturity and lack of understanding of basics.


It's not about understanding what I do as a user. It's about understanding all the possibilities and behaviours that will affect all users. It's called testing.

---

### Post by effenberg0x0 on 2012-01-20
> **philinux said:**
> Unless I missed something, it can happen, gksu nautilus has always been used when necessary. This is not X as root or logging in as root.

 [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

Hi Phil, no, of course you did not miss anything. A lot of people use it. It seems like a change in the default behaviour, that will be responsible for some amount of threads after release. I thought it was a bug, but it looks like a design choice (not exporting the needed env var).

Regards,
Effenberg

---

### Post by BC59 on 2012-01-20
Looks like a bug. You could fill a bug report. It's not critical, but it's a bug.

---

### Post by effenberg0x0 on 2012-01-20
> **BC59 said:**
> Looks like a bug. You could fill a bug report. It's not critical, but it's a bug.

I will +1 on it, as it's already reported. Someone mentioned in a duplicate that, when launching gparted, you also get no global menu. Now that would characterise the thing as a bug, as we need gparted to run as root...

[B]EDIT:
[/B]Just tested it, it's true. But the menu gets moved to default placement, so it actually doesn't limit the user's options but just breaks the desired visual standard.

---

### Post by ventrical on 2012-01-20
> **Buntumatic said:**
> Not newbie? But only newbies have inevitable urge to run things as root. I remember when I was a noob I wanted to run things as root, too. Just setting all the permissions properly felt too cumbersome. It was back in 1996, didn't take long until I started understand the security model of UNIX. Grow up. The whole POSIX security is built on principle 'default denied'. In other words, never elevate your rights without a good reason. "It's my box I do whatever I want" is not a valid reason, it just displays immaturity and lack of understanding of basics.

Hey .. were just beta testing here...ya know .. I mean I have 8 PCs and I know what I'm getting into when I'm BETA testing. No reason to pee in effenbergs porridge if he wants to rip a machine.

---

### Post by cariboo on 2012-01-20
Maybe to get past some of the misunderstandings, we should say:

>  when running nautilus with elevated privileges there is no global menu

---

### Post by mc4man on 2012-01-20
First of all there is a somewhat recent 'prevailing' opinion that nautilus should not be browsed as root, can look up a link that implies that. Plus read between the lines concerning the removal of nautilus-gksu

Putting that aside, the issue in 12.04 is that when nautilus is being browsed as root the GM is still probably being used, it just can't be displayed in the panel (ie the bug report which is somewhat old.

What should happen is the nautilus menu be returned to the root nautilus window which is not occurring. _This is a new behavior in 12.04_

---

### Post by philinux on 2012-01-20
TBH I'm not a fan of global menus on a desktop pc. Especially with a 22" monitor. Too much mouse.

---

### Post by mc4man on 2012-01-20
here is a new report, most likely in order - 

Already reported
Will be ignored
Won't fix, 'stop browsing as root'
Will be fixed

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/919416](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/919416)

---

### Post by Buntumatic on 2012-01-20
If it looks like a duck, swims like a duck, and quacks like a duck, then it probably is a duck.

If it speaks like a noob, thinks like a noob, and acts like a noob, then it probably is a noob.

Of course, I realize a horse does not understand why pooping during parade is not appreciated, as a noob does not understand why following certain conventions is absolute necessity. There really is not much one can do about it, you either grow up or you don't.

Testing is a lame excuse, BTW. Testing unnecessary functions is as good as testing how long can you drive on the wrong side of the road without crashing into somebody. Worthless.

---

### Post by cariboo on 2012-01-20
The more people that click the affects me button, the more likely that the bug will be fixed.

---

### Post by Buntumatic on 2012-01-20
Where is the bug? Developers have taken action to stop noob abuse before, this may just be another case.

---

### Post by effenberg0x0 on 2012-01-20
> **Buntumatic said:**
> If it looks like a duck, swims like a duck, and quacks like a duck, then it probably is a duck.

If it speaks like a noob, thinks like a noob, and acts like a noob, then it probably is a noob.

Of course, I realize a horse does not understand why pooping during parade is not appreciated, as a noob does not understand why following certain conventions is absolute necessity. There really is not much one can do about it, you either grow up or you don't.

Testing is a lame excuse, BTW. Testing unnecessary functions is as good as testing how long can you drive on the wrong side of the road without crashing into somebody. Worthless.

I've already been warned to keep it civil. I won't discuss with you. 
Again: This is testing. We can't limit our tests to what would be expected from an experienced user. We must try all procedures the average users will try and verify what happens in each case. Look at older threads, previous development cycles, and you'll verify that. Members, moderators and some of our regulars already answered to the thread with opinions that differ from yours, and still your pushing for a fight. Every now and then we get a HaX0R dude like this in here that tries, as hard as possible, to start a flame war. I won't fall for that.

Kind regards,
Effenberg

---

### Post by kaldor on 2012-01-20
> **Buntumatic said:**
> Right, if you open your home for drug dealers you will be punished. Agree?
If you compromise your box and it is connected to the internet it becomes a platform for cyber-criminals. 

The two stupidest things a computer user can do is:

Running X as root;
using computer as root.

Do not do it. It is not up for discussion. It is a good practice established long time ago.

Difference between this and the su command? I use nautilus as root if it is more efficient than a CLI for what I need to get done. And the boogeyman still hasn't eaten me.

@ OP: was wondering about this myself today.

---

### Post by fjgaude on 2012-01-20
> **Buntumatic said:**
> If it looks like a duck, swims like a duck, and quacks like a duck, then it probably is a duck.

If it speaks like a noob, thinks like a noob, and acts like a noob, then it probably is a noob.

Of course, I realize a horse does not understand why pooping during parade is not appreciated, as a noob does not understand why following certain conventions is absolute necessity. There really is not much one can do about it, you either grow up or you don't.

Testing is a lame excuse, BTW. Testing unnecessary functions is as good as testing how long can you drive on the wrong side of the road without crashing into somebody. Worthless.

A person with ubuntu is open and available to others, affirming of others, does not feel threatened that others are able and good, for he or she has a proper self-assurance that comes from knowing that he or she belongs in a greater whole and is diminished when others are humiliated or diminished, when others are tortured or oppressed. -- Archbishop Desmond Tutu, 1999

Nelson Mandela explained Ubuntu as follows: “A traveller through a country would stop at a village and he didn't have to ask for food or for water. Once he stops, the people give him food, entertain him. That is one aspect of Ubuntu but it will have various aspects. Ubuntu does not mean that people should not address themselves. The question therefore is: Are you going to do so in order to enable the community around you to be able to improve?"

---

### Post by xyzzyman on 2012-01-20
How is using elevating nautilus temporarily any different than using gedit to edit a file? I'm assuming effenberg is running nautilis as root via su/gksu, and not actually logged in as root. I think he was being accused of unlocking the root account and running as a root user and that's not the case.

---

### Post by effenberg0x0 on 2012-01-20
> **xyzzyman said:**
> How is using elevating nautilus temporarily any different than using gedit to edit a file? I'm assuming effenberg is running nautilis as root via su/gksu, and not actually logged in as root.

Hey xyzzyman,
Yes, of course. Considering the default install wouldn't allow root to login, I keep it that way in testing machines. As Cariboo pointed out a couple posts above, I shouldn't use the "as root" but "with elevated privileges", to be clearer.

---

### Post by jbicha on 2012-01-20
effenberg, thanks for opening a new bug report. It might be useful if you install older versions of nautilus and identify in what version the behavior changed. It could even be a change in gtk+3.0. It just depends on how much time you want to spend trying to pinpoint the problem.

---

### Post by effenberg0x0 on 2012-01-20
> **jbicha said:**
> effenberg, thanks for opening a new bug report. It might be useful if you install older versions of nautilus and identify in what version the behavior changed. It could even be a change in gtk+3.0. It just depends on how much time you want to spend trying to pinpoint the problem.

Hi JBicha, 
Sure, I can work on it by Monday. I'll use some VMs based on outdated ISOs and update them with a focus on Nautilus versions.

Thanks,
Effenberg

---

### Post by kurt18947 on 2012-01-20
> **xyzzyman said:**
> How is using elevating nautilus temporarily any different than using gedit to edit a file? I'm assuming effenberg is running nautilis as root via su/gksu, and not actually logged in as root. I think he was being accused of unlocking the root account and running as a root user and that's not the case.

And opening Nautilus using "gksu-nautilus" and not having full functionality can be a bother for desktop users.  Copying some Thunderbird files to a backup drive requires sudo privileges for instance, or copying files from removable drives when a file belongs to one user but I want to copy it to another user account.  I never log on as root but need nautilus to work with elevated  privileges periodically.  I'll go click the "me too" button.

---

### Post by xyzzyman on 2012-01-20
> **kurt18947 said:**
> And opening Nautilus using "gksu-nautilus" and not having full functionality can be a bother for desktop users.  Copying some Thunderbird files to a backup drive requires sudo privileges for instance, or copying files from removable drives when a file belongs to one user but I want to copy it to another user account.  I never log on as root but need nautilus to work with elevated  privileges periodically.  I'll go click the "me too" button.

I use gksu nautilus all the time (honestly most of the time i type sudo as i'm just used to it in terminal), but I was curious why some people thought that was wrong, when it seems like a different circumstance than logging in as root.

---

### Post by cariboo on 2012-01-20
Until this thread came up, I didn't know that the global menu didn't show when running nautilus with privilege escalation. I normally use:

```
sudo mc
```

when I need to move/copy files to another location I don't have the proper permissions for.

---

### Post by mc4man on 2012-01-20
> **xyzzyman said:**
> I use gksu nautilus all the time (honestly most of the time i type sudo as i'm just used to it in terminal), but I was curious why some people thought that was wrong, when it seems like a different circumstance than logging in as root.

I use once & a while with no apparent ill effect, normally thru the nautilus or python ext. 
There have been a number of comments recently here & elsewhere to avoid browsing in nautilus as root, maybe they aren't referring to gksu, never made really clear.(jbicha said that recently though again maybe not referring to gksu?

I thought this comment over the summer was straightforward though it could just be 1 nautilus dev's opinion 
[https://bugzilla.gnome.org/show_bug.cgi?id=654184](https://bugzilla.gnome.org/show_bug.cgi?id=654184)

Additionally the nautilus gksu extension has been removed, maybe for an extension issue, maybe not. (The extension does still work ok & was never added to a 'master' bug on extensions that was created with the use of gnome/nautilus 3

Anyway this issue has nothing to do with correct or not, simply a breakdown in what 'should' happen in a root window where the GM doesn't work

---

### Post by VMC on 2012-01-20
Interesting, midnight-commander.org came up as a suspicious site. I proceded anyway. I haven't used mc in years.

In Fedora16, there's no gksu, so we use alias's "sudo nautilus /". When global failed I just a terminal and gksu nautilus that way.

---

### Post by effenberg0x0 on 2012-01-20
> **VMC said:**
> Interesting, midnight-commander.org came up as a suspicious site. I proceded anyway. I haven't used mc in years.

In Fedora16, there's no gksu, so we use alias's "sudo nautilus /". When global failed I just a terminal and gksu nautilus that way.

Just as a side note, if you guys feel like trying it, I have replaced Midnight Commander for gnome-commander and tux-commander, both available in the repos.

---

### Post by RambJoe on 2012-01-21
This is nothing to do with nautilus, it affects ANY program that runs as root.

Try it on gedit, GParted etc.

Can't wait for the people calling me a noob for running GParted as root.

---

### Post by philinux on 2012-01-21
> **RambJoe said:**
> This is nothing to do with nautilus, it affects ANY program that runs as root.

Try it on gedit, GParted etc.

Can't wait for the people calling me a noob for running GParted as root.

Ha +1.

It's the same in Oneiric I think.

---

### Post by tlcstat on 2012-01-21
Greetings,
It amazes me that a simple question "Can you tell me how to get back my global menu when I run root nautilus" can turn into a debate on running nautilus as root. The purpose of the question is to get an answer not to debate whether a user that has linux running on thumb drives, usb hard drives, PCs, Laptops, and who knows what else should be using root. And PS the entire discussion under this context is probably confusing to a newbie. I use root all of the time and if you don't like it then start a new thread. I'm getting bored with sorting through all of this mickey mouse jazz trying to find the answer to the post question. It takes 20 minutes to reinstall Ubuntu and most of us have more than enough experience doing that. So enough already!!!
tlcstat

PS: Most of us MS crossovers aren't afraid of a little ole virus.

---

### Post by ventrical on 2012-01-21
Yeah .. this is Beta Testing. I mean - we can't treat our installs like they are some kind of glass menagerie. If we do not try different exploits on various apps in the many various way presented, then , as Beta Testers  we are not worth our salt. So all those weaknesses from previous  distros will be inherited by Precise, or , at least attributed to it.

---

### Post by VMC on 2012-01-21
> **tlcstat said:**
> Greetings,
It amazes me that a simple question "Can you tell me how to get back my global menu when I run root nautilus" can turn into a debate on running nautilus as root.  The purpose of the question is to get an answer not to debate whether a user that has linux running on thumb drives, usb hard drives, PCs, Laptops, and who knows what else should be using root. And PS the entire discussion under this context is probably confusing to a newbie. I use root all of the time and if you don't like it then start a new thread. I'm getting bored with sorting through all of this mickey mouse jazz trying to find the answer to the post question. It takes 20 minutes to reinstall Ubuntu and most of us have more than enough experience doing that. So enough already!!!
tlcstat

PS: Most of us M$ crossovers aren't afraid of a little ole virus.

+1 !

Someone ask a question and gets an opinion. That's almost as bad as answering a question with a question.

I never log in as root, but use gksu to root many times to do some tasks. In fact the Mint developers made an icon that gksu's to the root terminal, right on the desktop.

---

### Post by mc4man on 2012-01-21
There are 2 bugs here - one more relevant to thread title - root windows can't use the global menu.
That bug is longstanding & likely to remain so.

The other semi-relevant is that in the current 12.04 nautilus, when it's opened as root there is no menu at all when there should be in the nautilus window itself.
The menu was there in A1, broke along the way.
Whether there is any issue using a root nautilus browser isn't relevant to the bug so I removed the line mentioning that from the report.

( - if needing to set a couple of the handy preferences for the root browser that can be still be done thru root gsettings though I've only found a couple to be useful & would caution against mucking around there otherwise
(show adv. perms, include a delete, use location instead of the currently borked light-theme breadcrumbs is about it here

---

### Post by VMC on 2012-01-21
I would be satisfied if the context open file/directory as root would work. I tried the mentioned ppa and [this one]("http://www.upubuntu.com/2011/12/how-to-open-files-folders-as-root-from.html"), or [this one]("http://ubuntuguide.net/add-open-as-root-to-filefolder-right-click-menu-in-ubuntu"). It just doesn't work for me.

---

### Post by mc4man on 2012-01-21
> **VMC said:**
> I would be satisfied if the context open file/directory as root would work. I tried the mentioned ppa and [this one]("http://www.upubuntu.com/2011/12/how-to-open-files-folders-as-root-from.html"), or [this one]("http://ubuntuguide.net/add-open-as-root-to-filefolder-right-click-menu-in-ubuntu"). It just doesn't work for me.

That shouldn't be an issue - 
For the old nautilus-gksu extension

go here and download the .deb for your arch
[http://packages.ubuntu.com/oneiric/nautilus-gksu](http://packages.ubuntu.com/oneiric/nautilus-gksu)

After the download finishes right click on > extract here
Once extracted browse the extracted folder to where i show in screen1, grab the .so & put it in 

> /usr/lib/nautilus/extensions-3.0
(you have permission to use gksu nautilus to do so or use a mv command. Then restart nautilus or log out/in

For the ppa just add, I used 
sudo add-apt-repository ppa:nae-team/ppa

Then in synaptic just install the package in screen 2
Or go directly to the ppa, dl the package & use gdebi on it - 
edit - here
[https://launchpad.net/~nae-team/+archive/ppa/+packages](https://launchpad.net/~nae-team/+archive/ppa/+packages)

Re-edit - 
you can have both "Open as Root" (ppa), & "Open as Administrator" installed at same time, then take your pick or leave, whatever

---

### Post by VMC on 2012-01-21
I saw some posts on the subject in the past few days, but wasn't sure who knew. Now I know. Thanks!

Edit: The [**_amd64 deb_**]("http://packages.ubuntu.com/oneiric/amd64/nautilus-gksu/filelist") I downloaded doesn't have extensions 3.0:


/usr/lib/nautilus/extensions-1.0/libnautilus-gksu.so
/usr/lib/nautilus/extensions-2.0/libnautilus-gksu.so

---

### Post by mc4man on 2012-01-22
> **VMC said:**
> I saw some posts on the subject in the past few days, but wasn't sure who knew. Now I know. Thanks!

Edit: The [**_amd64 deb_**]("http://packages.ubuntu.com/oneiric/amd64/nautilus-gksu/filelist") I downloaded doesn't have extensions 3.0:


/usr/lib/nautilus/extensions-1.0/libnautilus-gksu.so
/usr/lib/nautilus/extensions-2.0/libnautilus-gksu.so
Correct - you need to take the libnautilus-gksu.so from one of the above folders & put it in your extensions 3.0 folder

---

### Post by VMC on 2012-01-22
Ok, it now works. I was confusing the deb folders with the actual folder to place it in. Simple, heh. That trick isn't blogged anywhere. Actually my Mint install already has it.

---

### Post by mc4man on 2012-01-22
> **VMC said:**
> Ok, it now works. I was confusing the deb folders with the actual folder to place it in. Simple, heh. That trick isn't blogged anywhere. Actually my Mint install already has it.
The main diff is that  in 11.10 is the package is available/installable [but was never rebuilt to work with gtk3]("https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/817383"), naut3 ect. (One of those bugs that gets ignored because there is nothing to be 'fixed'
So the workaround would be to install, then  cp, mv or link the installed .so in/to the 3.0 extension dir. where it would be found &  used.

As of 12.04 the package is no longer being built so rather than install or try to install a  libnautilus-extension1 package in 12.04 which uses  libnautilus-extension1a,  you can simply  put the .so into the proper extension dir. where atm, it continues to work fine. No need to install the package at all.

The one from the ppa is a new python-nautilus extension that should continue to be fine down the road if for some reason the .so stops working

---

### Post by tlcstat on 2012-01-22
Greetings,
Thank you MC4MAN, this is a good one.
tlcstat

---

### Post by grahammechanical on 2012-01-22
When I first saw this thread I did not think that it had relevance to me. Until now.

Did you people know that if the tilde character ( ~ ) is put on the end of a file extension then that file becomes effectively a hidden file?

I have been trying to create another background slide show by editing the relevant scripts. I have been wondering why I have been getting duplicate background images in the User Interface side panel. I found out that sudo gedit creates a backup copy by simply putting the tilde character on the end of the file extension of the copy and gnome-control-panel sees this as a genuine script and so reads two scripts instead of one.

No problem. Just use sudo nautilus to delete the extra file. I did this the other month and it worked. Only this time sudo nautilus could not see the backup copy because it was not set to show hidden files and I could set it to show hidden files, could I.

It took me more than a day to notice that standard nautilus could see them. So I have to use sudo rm in a terminal.

So, I would say, what is the point of having GUI applications that can run with administrator privileges it they do not have the necessary menu items available? The standard applications can see these files but cannot move, copy or edit them.

So, I think that not having those menu items either in the global menu or on the application top panel is a serious bug or design flaw, whatever you want to call it. This problem certainly bugged me!

Regards.

---

### Post by tlcstat on 2012-01-22
Greetings,

original by grahammechanical
> So, I think that not having those menu items either in the global menu or on the application top panel is a serious bug or design flaw, whatever you want to call it. This problem certainly bugged me!

I wouldn't call it a bug. The linux crowd have been infamously command line operators [not saying theres anything wrong with that]. I think the omission of a root menu was a concession to the slackware hold-overs [not implying that anyone here is a slackware hold-over]. The developer probably didn't want to insult their dignity by including a menu. They didn't project that myself a M$ user would be coming over to Ubuntu and needing a menu. Call it a sin of omission rather than a bug [not implying that the developers are sinners, its a figure of speech].
tlcstat

---

### Post by mc4man on 2012-01-22
> **grahammechanical said:**
> 
So, I think that not having those menu items either in the global menu or on the application top panel is a serious bug or design flaw, whatever you want to call it. This problem certainly bugged me!

Regards.
The menus not showing in the sudo nautilus window is likely just a bug, it did show earlier in 12.04, something broke it. *the in app window does show in other sudo windows.
So hopefully it will be fixed

Ot. a bit - 
if you want to show hidden files in a sudo nautilus - 


```
sudo gsettings set org.gnome.nautilus.preferences show-hidden-files true
```

---

### Post by xyzzyman on 2012-01-22
> **mc4man said:**
> The menus not showing in the sudo nautilus window is likely just a bug, it did show earlier in 12.04, something broke it. *the in app window does show in other sudo windows.
So hopefully it will be fixed

Ot. a bit - 
if you want to show hidden files in a sudo nautilus - 


```
sudo gsettings set org.gnome.nautilus.preferences show-hidden-files true
```

Shouldn't ctrl+h still work?

---

### Post by effenberg0x0 on 2012-01-22
> **xyzzyman said:**
> Shouldn't ctrl+h still work?
Maybe to set it as the default behaviour? I've noticed it hides my dotfiles in new instances, even after ctrl+h in the primary instance.

Just a note: We are going through a phase in which our desktop paradigms were broken: Using composition as the default, new scrollbars, the application menu, etc. This are very basilar stuff. It's ok and good to change, but I'm not sure they really thought through all the potential ramifications of the global panel / app menu change when they implemented it... I mean, look at the things we are discussing in this thread, which were caused by what was primarily a GUI design decision.

April is starting to feel just too close now.

Regards,
Effenberg

---

### Post by mc4man on 2012-01-22
> Maybe to set it as the default behavior? 

Certainly & just as a convenience, which is what gksu nautilus or either of the 2 extensions are.

Same could be said for enabling the delete context option  for a sudo nautilus, shift+delete still works.

 Haven't been inclined to set up an install to see where the menu in the sudo naut window stopped working, though did ck. on a A1 live session where it was still there. Because naut,gtk3 & gail require an upgraded glib couldn't really ck. on the live session, glib upgrades require a restart which obviously isn't possible. 
(though I did do anyway followed by a log out/in which had the odd effect of having both a Global & in window menu for a user naut, the sudo still kept the in window one.

---

### Post by grahammechanical on 2012-01-23
Thank you people. I knew someone would pass on a useful tip. Ctrl+h it is. I have also made a note of the other command. Oh, by the way, I now have four slide shows in my User Interface panel and only crashed Compiz twice. I am feeling pleased with myself. Now for number 5. The background images from Lucid.

Regards.

---

### Post by mc4man on 2012-01-28
As far as the menu returning to a sudo nautilus window was fixed in recent gtk/gail-3-0 upgrades
> 
gtk+3.0 (3.3.10-0ubuntu3) precise; urgency=low

  [ Lars Uebernickel ]
  * debian/patches/043_ubuntu_menu_proxy.patch:
    - don't try to show the global menu when the menuproxy module wasn't
    loaded


---

### Post by nm_geo on 2012-01-28
> **mc4man said:**
> As far as the menu returning to a sudo nautilus window was fixed in recent gtk/gail-3-0 upgrades

Thanks mc4man..  That worked for me too.

---

