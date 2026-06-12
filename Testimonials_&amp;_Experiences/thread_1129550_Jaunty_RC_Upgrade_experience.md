---
title: "Jaunty RC Upgrade experience"
date: 2009-04-18
forum: Testimonials &amp; Experiences
---

### Post by VastOne on 2009-04-18
My experience:

Stable 2nd computer that started with Gutsy->Hardy->Intrepid, all upgraded with the RC and then with the actual release...

Through all this, nothing but smooth sailings...

Upgraded to Jaunty RC yesterday and was fine with everything except nVidia and X failed to install because there was a "newer version: already in place. No issue as the upgrade worked and everything appeared to be fine, through multiple reboots with the exception being that nVidia X manager would not save the settings I had setup. Every time I rebooted, I would have to go back to nVidia X Server and change from 1024*768 to 1680*1050 and be fine again.

This morning I woke up to a completely dead Xorg and no matter what tools I tried ( all of them) they all failed.

At this point I decided to quit troubleshooting and reinstall with a complete ext4 setup.

Every thing is running perfectly. nVidia is now setup and working correctly, compiz and emerald are perfect, and the machine (AMD64 btw) is running better than it ever has.

I think we can expect many install and upgrade issues with Jaunty, but when all is ironed out, it is a pretty awesome setup.

I would highly recommend that everyone make sure they have a seperate home partition before upgrading...

My 2 cents and a little more used soapbox....

VastOne

---

### Post by wolfen69 on 2009-04-18
> **VastOne said:**
> 
I would highly recommend that everyone make sure they have a seperate home partition before upgrading...


upgrading *any* OS can lead to problems. i always do fresh installs, and can sleep at night. ;)

---

### Post by juancarlospaco on 2009-04-19
**To Upgrade OS :**
-Remove all Non-Oficial packages
-Delete all .* files in $HOME
-sudo apt-get clean
[I]
And runs smooooth and fine...[/I]

---

### Post by monkeyKata on 2009-04-19
> **juancarlospaco said:**
> **To Upgrade OS :**
-Remove all Non-Oficial packages
-Delete all .* files in $HOME
-sudo apt-get clean
[I]
And runs smooooth and fine...[/I]

So, for example, it's best to remove those files such as .bash-history, .bash-logout, .dmrc, .esd_auth, .gksu.lock, .gtk-bookmarks, .profile...?

And get rid of any packages not installed from the official repos?

Will this really facilitate the upgrade process?  I'm going to be upgrading as well and won't be able to back up the majority of my stuff, so I'm looking into the most sure-fire way.  Any other tips or opinions?

Thanks for this info!

---

### Post by thunk77 on 2009-04-19
> **monkeyKata said:**
> So, for example, it's best to remove those files such as .bash-history, .bash-logout, .dmrc, .esd_auth, .gksu.lock, .gtk-bookmarks, .profile...?

And get rid of any packages not installed from the official repos?

Will this really facilitate the upgrade process?  I'm going to be upgrading as well and won't be able to back up the majority of my stuff, so I'm looking into the most sure-fire way.  Any other tips or opinions?

Thanks for this info!


So, that's like a ... fresh install? :P

---

### Post by wolfen69 on 2009-04-19
> **thunk77 said:**
> So, that's like a ... fresh install? :P

if you are going to do all that, you might as well do a fresh install. plus, an upgrade can take longer to do than reinstalling, and there is no guarantee of it going well. time for the upgrade fanboys to jump in..... :rolleyes:

---

### Post by Marlonsm on 2009-04-19
I upgraded to Jaunty and things aren't actually working very well.

The system is still usable, but with Intrepid it was working better.
But during my upgrade, almost everything that could go wrong, went wrong. For example During the download/install my internet stopped working many times, so I actually had to run the upgrade manager 5 times before the internet didn't stop working during the upgrade. I'm also running Ubuntu with Wubi, so it also helps me getting problems with upgrades...

I'm just waiting until thursday, so I can download the final release and do a clean install.

---

### Post by fjf on 2009-04-19
My upgrade went fine coming from ubuntustudio 8.10.  No problems at all.  Amazing.

---

### Post by monkeyKata on 2009-04-19
> **wolfen69 said:**
> if you are going to do all that, you might as well do a fresh install. plus, an upgrade can take longer to do than reinstalling, and there is no guarantee of it going well. time for the upgrade fanboys to jump in..... :rolleyes:

Yeah, I hear ya.  Thing is I probably won't have a chance to backup the majority of my files so I can't consider a fresh install too seriously at the moment.  I'll see what the good word is the day it's released then try upgrading as normal.  My internet connection is very stable.

It's good to see that some people have not had any problems upgrading.

And I know I've asked this before... but anyone upgrade sticking with ext3 and still notice a difference in speed and responsiveness?  How is it overall?

---

### Post by longtom on 2009-04-20
Sorry for chipping in - but while the topic is hot.

If I do a clean install of 9.04 on a fresh partition and have a dual or triple boot (in my case 8.10, 9.04 and XP), can I copy my Evolution Mail and Thunderbird details over to my 9.04 installation and "violá". it will all be there?

I reckon this would be the most painless way to make sure, nothing gets lost.  I'll have a fresh installation on ext4 (yes wolfen69, I'm 'listening' to you ;)), and I have still all my data from the 8.10 version to fall back to until I am comfortable all is working the way I want it.

Anything I overlooked?

---

### Post by Perfect Storm on 2009-04-20
> **juancarlospaco said:**
> **To Upgrade OS :**
-Remove all Non-Oficial packages
-Delete all .* files in $HOME
-sudo apt-get clean
[I]
And runs smooooth and fine...[/I]

Might as well do a clean install like the other people said, if you don't have gigs of stuff you havn't backup'ed.




I always do clean Install - also to see the changes they made for Ubuntu by default, and too many upgrades can slow the OS.
Regarding Upgrades, no matter which OS it can go dearly wrong. Especially if you made alot of tweaks, custom changes, edit this and that. 
As mention before alot of third party software/libs installed can also make it messy.

Another thing. It's a little on your own risk to make an upgrade to a non-stable release. ;)

---

### Post by WhiskyChris on 2009-04-20
> **longtom said:**
> If I do a clean install of 9.04 on a fresh partition and have a dual or triple boot (in my case 8.10, 9.04 and XP), can I copy my Evolution Mail and Thunderbird details over to my 9.04 installation and "violá". it will all be there?

I don't know about thunderbird but I've recently transferred all my evolution stuff as easy as File - Backup Settings on old, and File - Restore Settings on new. Calendar, tasks, email accounts etc etc all migrated nice and painlessly!!

---

### Post by ukripper on 2009-04-20
I didnt have any problem doing clean install of Jaunty on 3 machines everything detected out of the box for nv and ati cards. Upgrade may cause problems on nv or ati cards so i would suggest doing clean install and better option is to use EXT4 instead of EXT3 during installation.

Overall Jaunty RC 10/10 from me:popcorn:

---

### Post by VastOne on 2009-04-20
> **ukripper said:**
> I didnt have any problem doing clean install of Jaunty on 3 machines everything detected out of the box for nv and ati cards. Upgrade may cause problems on nv or ati cards so i would suggest doing clean install and better option is to use EXT4 instead of EXT3 during installation.

Overall Jaunty RC 10/10 from me:popcorn:

This is precisely what I tried to convey in the original post.  My upgrade went flaky after initially looking good but the clean wipe and install new with EXT4 is perfect.

Thank you for clarifying as some of the suggestions on this thread is scary....

VastOne

---

### Post by wolfen69 on 2009-04-20
> **longtom said:**
> Sorry for chipping in - but while the topic is hot.

If I do a clean install of 9.04 on a fresh partition and have a dual or triple boot (in my case 8.10, 9.04 and XP), can I copy my Evolution Mail and Thunderbird details over to my 9.04 installation and "violá". it will all be there?


sorry for what? you are entitled.

all you have to do is backup your hidden config files (just the ones you want) in the home folder. then pop them back in after the install. all i backup is my .mozilla and .thunderbird files. i don't worry about losing personal files, as i keep them on separate drives. (and then backed up 2 more times)

---

