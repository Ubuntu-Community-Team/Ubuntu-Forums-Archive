---
title: "Do NOT upgrade to 9.10"
date: 2009-10-29
forum: Testimonials &amp; Experiences
---

### Post by asuastrophysics on 2009-10-29
To anyone thinking of upgrading to Karmic early:

...Don't. It's not worth the pain. None of the commands are the same. 

```
/etc/init.d/hal restart
/etc/init.d/networking restart

```

none of the init.d commands work any more. Also, it has become increasingly difficult to stop X if you need to: 
```
jake@girdy-laptop:~$ /etc/init.d/gdm stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop gdm
jake@girdy-laptop:~$ 

```
As you can see, these commands no longer do anything. Also, expect possible touchpad regressions as HAL is changed to "udev".

Do not upgrade to Karmic early. It's always exciting to see a new release, but spare yourself the agony and don't try it early

[COLOR="Red"]**EDIT: This post was a bit overly dramatic. All in all, I am very happy with this new release. Just be smart people, and test your computer for bugs using a LiveCD first! **[/COLOR] :D

---

### Post by Major Squirrel on 2009-10-29
but the final release isn't out yet, I've been waiting for it, it's still the beta release.....

---

### Post by VertexPusher on 2009-10-29
I will update early.

---

### Post by Jive Turkey on 2009-10-29
There are instructions to re enable ctrl+alt+backspace in xkb on the release notes page.  The commands that have changed are arguably an improvement and from what I understand it makes the shell more similar to other distros.

Don't panic, learn the new commands, you'll be ok.

```
/etc/init.d/hal restart
/etc/init.d/networking restart

```
There is no more hal, you dont need to restart it. For networking try ```
$service networking restart
```

---

### Post by asuastrophysics on 2009-10-29
it's supposed to be released today. however, 4 hours early of the final release...i see a lot of work to do. not to mention i now have to re-learn the cli as that has also changed.

---

### Post by Major Squirrel on 2009-10-29
it's going to be released in 4 hours still?!

---

### Post by ndefontenay on 2009-10-29
For all problems there's a solution. And for all problems without a solution we're here as a community to find and fix them.

I don't think that threatening that Ubuntu 9.10 will blow your computer out if you install it is the right way to go.

---

### Post by caco on 2009-10-29
No sign of the new release ... have an idea of the exact time/hour :)

---

### Post by Major Squirrel on 2009-10-29
Do you guys know exactly what time karmic will be released at? and is that the same time for ubuntu studio 9.10?

---

### Post by asuastrophysics on 2009-10-29
> **ndefontenay said:**
> For all problems there's a solution. And for all problems without a solution we're here as a community to find and fix them.

I don't think that threatening that Ubuntu 9.10 will blow your computer out if you install it is the right way to go.

I'm just trying to warn users who might be thinking about upgrading early not to do it. It took me an hour and a half just to get my laptop to boot again. It's not ready yet. I'm sure it'll be great when it is bug-free, but as of right now, it's not safe yet. ;)

---

### Post by asuastrophysics on 2009-10-29
> **Jive Turkey said:**
> There are instructions to re enable ctrl+alt+backspace in xkb on the release notes page.  The commands that have changed are arguably an improvement and from what I understand it makes the shell more similar to other distros.

Don't panic, learn the new commands, you'll be ok.

```
/etc/init.d/hal restart
/etc/init.d/networking restart

```
There is no more hal, you dont need to restart it. For networking try ```
$service networking restart
```

If there is a problem with the touchpad or other integrated peripherals, how do you "refresh" them? is there another service that integrates the touchpad?

---

### Post by k3lt01 on 2009-10-29
I've been using Karmic for a week already, its been fine so far. Hitting the panic button like this hasn't really done anything to help anyone.

---

### Post by ElSlunko on 2009-10-29
Not saying you shouldn't voice your concerns and issues with Karmic, but the red flag is a bit unwarranted. I'm sure some folks will have issues installing windows 7 in the next and last few weeks, but doesn't mean they should pull it off the shelves.

---

### Post by kellemes on 2009-10-29
> **asuastrophysics said:**
> I'm just trying to warn users who might be thinking about upgrading early not to do it. It took me an hour and a half just to get my laptop to boot again. It's not ready yet. I'm sure it'll be great when it is bug-free, but as of right now, it's not safe yet. ;)

You're talking about upgrading to a BETA release!
Pretty silly to expect a BETA release to be bug-free.

---

### Post by jmore9 on 2009-10-29
I have been using the rc for about 6 days now.  This is so far the best one that has been released.  I have 0 zero problems from original 9.04 install.

To 9.10rc upgrade , to the usage i am getting today.

I haven't found any aps or any commands that i use that are that different from before.

All in all i would say the ease of use has gotten better not worse as you claim.  But there always some thing new to with every release, what ever OS it is.

---

### Post by Zzl1xndd on 2009-10-29
> **jmore9 said:**
> I have been using the rc for about 6 days now.  This is so far the best one that has been released.  I have 0 zero problems from original 9.04 install.



It has been pretty much the same for me.

---

### Post by bashphoenux on 2009-10-29
when is the release expected ??
can i upgrade on the existing 9.04 ?? If so wats the command ??

---

### Post by HereInOz on 2009-10-29
when it is available as an upgrade, there will be a note at the top of the Upgrade Manager to that effect.  From memory the command line is:

sudo apt-get dist-upgrade

---

### Post by anewguy on 2009-10-29
I personally don't mind the shift to a more "common" command set, etc., as long as everything is well documented.  I have had headaches since 8.04 (I think) with changes to udev rules and no corresponding notifications in the release notes.  I'm hoping 9.10 is better in that regard.

As far as your problems, well, each new OS release does come with its' share of inherent problems.  Even waiting a while for the release to settle in doesn't get rid of things.  It's more a matter of what effects the whole, and that the release has covered those.

Dave :)

---

### Post by philinux on 2009-10-29
> **asuastrophysics said:**
> If there is a problem with the touchpad or other integrated peripherals, how do you "refresh" them? is there another service that integrates the touchpad?

For the touchpad look in Sys>prefs>mouse.

I seem to remember when testing Gf lappy that it was disabled by default on the livecd and upon install.

That being the tapping aspect of it. It moves the mouse around ok.

---

### Post by jmore9 on 2009-10-29
to upgrade i used

ALT + F2

then enter into the box that appears

update-manager -d

I followed the recommended actions during the upgrade with no problems

---

### Post by Zoot7 on 2009-10-29
> **asuastrophysics said:**
> To anyone thinking of upgrading to Karmic early:

...Don't. It's not worth the pain. None of the commands are the same. 

```
/etc/init.d/hal restart
/etc/init.d/networking restart

```

none of the init.d commands work any more. Also, it has become increasingly difficult to stop X if you need to: 
```
jake@girdy-laptop:~$ /etc/init.d/gdm stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop gdm
jake@girdy-laptop:~$ 

```
As you can see, these commands no longer do anything. Expect no touchpad support, no usability, and your personal profile to no longer work. 

Do not upgrade to Karmic early. It's always exciting to see a new release, but spare yourself the agony and don't try it early
This is exactly the reason I'll be installing it upon a spare hard drive. Jaunty with kernel 2.6.31 is working flawlessly for me at the moment, although the Beta of Karmic did work pretty much perfectly aswell.

---

### Post by lavinog on 2009-10-29
> **asuastrophysics said:**
> but as of right now, it's not safe yet. ;)

```

safe != bug free

```

Did you check to see if any bug reports have been filed for your issues?  If there is a major issue that you want to warn others about, launchpad would probability be a better place to get the word out at the moment.

---

### Post by ancientpaint on 2009-10-29
> **jmore9 said:**
> to upgrade i used

ALT + F2

then enter into the box that appears

update-manager -d

I followed the recommended actions during the upgrade with no problems


I used this method to upgrade about 36 hours ago and everything is working great.

---

### Post by humphreybc on 2009-10-29
I've been on the Karmic RC for about a week now, and I have to say, it's more stable and faster than the Jaunty final release.

I'm completely up to date with my updates, so with only a couple of hours to go until the final release, I'd say i'm running 99.99% of the final release of Karmic, and it's great!

---

### Post by Paddy Landau on 2009-10-29
To anyone running Windows, I recommend that you wait a 2-3 months to let the dust settle before upgrading to a new version.

I would recommend the same for any business or critical computer running Mac or Linux.

For playing around, of course, just go ahead and upgrade... provided that you back up first (I recommend [CloneZilla]("http://clonezilla.org/") or [PartImage]("http://www.partimage.org/") for hassle-free restoring).

---

### Post by bruno9779 on 2009-10-29
> **asuastrophysics said:**
> I'm just trying to warn users who might be thinking about upgrading early not to do it. It took me an hour and a half just to get my laptop to boot again. It's not ready yet. I'm sure it'll be great when it is bug-free, but as of right now, it's not safe yet. ;)

I did upgrade early, and I am fine with the changes: by upgrading (1 week) early I get more time to learn the changes.

I love the look and feel of the new Ubuntu. Finally a decent selection of wallpapers and themes, and so many little improvements.

Way to go !!!!!!

PS: my /home is on a different partition, I don't see what could go wrong

---

### Post by phillw on 2009-10-29
As always, before you do **anything** to your system .. TAKE A BACKUP !!!

You don't need anything special.. a simple tar command will backup all areas you want.

There is an excellent thread here ....

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

Mine, for example, is ..

```

cd /
sudo tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/media --exclude=/mnt --exclude=/sys --exclude=/home/phillw/Desktop/PhillzMuzic --exclude=/tmp /

```the excludes ... /proc, lost+found, sys not needed for a backup
/media - stops backups of any cd's or dvd's you've acicidently left in a drive !!
/mnt - stops other mounted drives (e.g. a windows partition
/home/phillw...Muzic - My Music folder (4GB in size, it has it's own DVD backup)
/tmp - not needed.
/backup.tgz - the backup file itself.

If, like me, you have additional things added to your system, this thread would be a good one to follow to get a list of everything you've added ...

[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

Just doing my back-up ready for 9.10 :-)    I feel like a kid on christmas morning. I ran 9.10RC in LiveCD mode yesterday to check my wireless etc was all working.

Also, don't forget to export your saved passwords and bookmarks from FireFox and Pigin !!

Phill.

---

### Post by yeats on 2009-10-29
> To anyone running Windows, I recommend that you wait a 2-3 months to let the dust settle before upgrading to a new version.

I completely agree with this.  I would probably add most Ubuntu users to that as well.  I've learned the hard way over the last two releases that it's wise not to upgrade immediately.  Let the remaining bugs shake out and let some workarounds to common issues get developed :-).

(I'll mention that I've been running Karmic in VirtualBox very happily for months...)

---

### Post by MrWES on 2009-10-29
> **asuastrophysics said:**
> I'm just trying to warn users who might be thinking about upgrading early not to do it. It took me an hour and a half just to get my laptop to boot again. It's not ready yet. I'm sure it'll be great when it is bug-free, but as of right now, it's not safe yet. ;)


I upgraded to the RC without issue. As usual.

~Bill

---

### Post by revanb on 2009-10-29
If you have the disk space to spare try the following:

* Have a seperate partition for your home directory.
* Have a partition for your current active Linux
* Have a partition for your new version of Linux

Install to the partition for the new Linux, once you are happy with it you start using it as default. By the next upgrade you install into the first partition...That way they overlap, and you can fall back if needed. I have not needed to fall back, but I could.

---

### Post by twright on 2009-10-29
Frankly I have been wanting it to switch to something more sensible than /etc/init.d/ and hal for ages. Different != broken

---

### Post by Cringer on 2009-10-29
I would love to be able to upgrade, but as many people who have amd64 combined with nVidia graphics have found out, that since Karmic was in Beta things have gone down hill. Alpha six installed fine for me, the RC release won't install at all and since it has only been a week and the bug report is still wide open at canonical with more additions every day I don't expect any change with this final release. 

[Bug 422536] Re: EDAC amd64: WARNING: ECC is NOT currently enabled by    the BIOS. Module will NOT be loaded.


The funny thing is most of these people don't have the option in their BIOS to control ECC. Updating BIOS did nothing to help. All very odd. Sure wish I still had a copy of Alpha 6 though.

---

### Post by dawynn on 2009-10-29
As with many others -- been using Karmic for months.  I installed on three separate computers.  One, a P3 level, one a P4 Athlon Classic (early P4 level), and the other a dual-core laptop.

Did Karmic have its issues?  Yes.  Just as with each release.  But each can be overcome.  And in each case, I used a combination of forum searches / posts, and launcpad searches / posts to resolve the issues.

Everyone's computer is different.  What is a problem for you, may not be for 90% of the community.  The other 10% have either solved the problem and posted an answer, or will be grateful to you if you help them solve it.  

How you use your computer is unique.  Just because you're used to administrating your computer using the cli or a particular interface, doesn't mean everyone does.  Much of the community uses the GUI tools provided for system administration.  And with Linux, it seems that for every action you could do, there's a dozen system tools you could use to do it.

Approach Linux as a learning experience.  What may have been the "best" tool for one install, may be superceded by some other tool.  Projects fail, others rise up.  Instead of sending out a general panic, learn about the new tools / new ways of doing things.

Use multiple partitions.  That's been stated before.  If one upgrade fails, you have something to fall back on, and you have a platform that you can chroot from.

Assume good intent from the developers.  If the release even made it to Beta mode, than there must be developers that *are* successfully using the release.  If it made it to RC (Release Candidate), that there are *many, many* developers and users that are successfully using the new system.  They've worked around their problems, and their systems work just fine.  

Then go back to learning mode -- how is your computer different, and why doesn't it work?  Search the forums and launchpad.  If you can't find the solutions for your problems, then raise your voice -- not in a blind panic mode, but specifically about your computer and your work experience.

---

### Post by louieb on 2009-10-29
:popcorn: every release has  things that need work 

> Different != brokenNo but the System Monitor in Karmic is acting strange. 

Going through several release upgrades has taught me one thing - **[SIZE=2][SIZE=3]Have a working backup[/SIZE] [/SIZE]**- or do you feel lucky

---

### Post by dalee on 2009-10-29
Hi,

Yeah, I'd back up Cringer about the amd64 and nVidia graphics. Be very, very cautious about upgrading. It's very broken for me too. I won't be upgrading to Karmic anytime soon.

dalee

---

### Post by CharlesA on 2009-10-29
I'm downloading the desktop edition now, and will install it on a spare machine at home, I expect it to install fine.

A huge ONOEZ Don't install isn't helping anyone.

Bugs happen, bugs get squashed.

EDIT: The Nvidia things are worrying me, since my server runs a NVIDIA graphics card, but since I'm not going to upgrade said server, it won't hurt me. :-P

---

### Post by vgrisham on 2009-10-29
I've been using Ubuntu since Dapper Drake (6.06). With the exceptions of Hardy and Jaunty, each was buggy when it first came out. I'm running Karmic on my home computer, but for the time being, I'm sticking with Jaunty on my laptop. [The ECC bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422536") described earlier that affects 64-bit users is annoying (lots of error messages upon login) and pervasive (look at the list of users affected!) but it has not led to any stability issues for me. The system notification area is also buggy, with tray applets being duplicated and some icons showing with drawing errors (checkgmail for instance).

Anyway, I learned a while ago to wait a month or so after each release, and that has served me well. Karmic will get it's kinks ironed out. In the meantime, I'm content with Jaunty Jackalope, which IMHO is the best release to date.

---

### Post by Roger Allott on 2009-10-29
Although unnecessarily alarmist, the title of this thread may be sage advice.

As I understand it, Karmic will utilise the ext4 filesystem and Grub2 (I've no idea what they are, but they sound good!), and an upgrade to Karmic from Jaunty will not be able to benefit from these.

Best option, apparently, is to install from a fresh download rather than upgrade.

---

### Post by vgrisham on 2009-10-29
Jaunty uses ext4 as well, though not by default. You can upgrade your existing Jaunty install to ext4, and I'm using it right now. Grub2 makes the boot up process cleaner looking (no more gobs of text flashing by; just a nice black screen with white ubuntu logo), but it boots slower than Jaunty on my PC.

---

### Post by Mornedhel on 2009-10-29
> **asuastrophysics said:**
> To anyone thinking of upgrading to Karmic early:

...Don't. It's not worth the pain. None of the commands are the same. 

```
/etc/init.d/hal restart
/etc/init.d/networking restart

```

none of the init.d commands work any more. Also, it has become increasingly difficult to stop X if you need to: 
```
jake@girdy-laptop:~$ /etc/init.d/gdm stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop gdm
jake@girdy-laptop:~$ 

```
As you can see, these commands no longer do anything. Expect no touchpad support, no usability, and your personal profile to no longer work. 

Do not upgrade to Karmic early. It's always exciting to see a new release, but spare yourself the agony and don't try it early

Duh. If you read the release notes ([http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)), you'd notice two things :

* HAL is deprecated
* The booting process is being converted to Upstart

So if you're planning on not upgrading until these "issues" have been resolved, you won't -- ever -- upgrade. Not to Karmic, not to Lucid, not to any modern distribution since transitioning away from init scripts is on the planning for most.

Did you even *try* "service gdm stop" ? Says to right there.

Now of course there will be issues with a distribution released today. It hasn't been tested as thoroughly as the previous version, obviously. Some things will probably be broken. "Don't upgrade if your current system is working and you don't need any of the new features" is the standard rule.

But you just picked two bugs (HAL and init -> Upstart) that really are features.

---

### Post by winotree on 2009-10-29
I upgraded with a clean install from Jackalope 9.04 to Koala 9.10 Beta, used it for one week, and everything was just fine.  I have since done the same with the release candidate (RC) and [after another week] everything was just fine.  I mean it -- no problems, no issues -- it works as well as any stable release of any distribution I've tried recently.  BTW did I mention that everything was just fine!?!  ;)  :D

---

### Post by phillw on 2009-10-29
Being the devout coward I am ;)  I booted with 9.10RC  LiveCD and had a good play with disks, wireless etc...

All went well.

But, yeah ..... Check it with LiveCD make sure your screen, wireless, network, disks etc are working okay and backup !!!

Phill.

---

### Post by lavinog on 2009-10-29
> **louieb said:**
> 
No but the System Monitor in Karmic is acting strange. 


Is it just system monitor that does this?  What if you disable desktop effects?  Are you using a nVidia card?

The screen corruption issues I had with my ATI card in jaunty are now gone in karmic.

---

### Post by MrWES on 2009-10-29
> **revanb said:**
> If you have the disk space to spare try the following:

* Have a seperate partition for your home directory.
* Have a partition for your current active Linux
* Have a partition for your new version of Linux

Install to the partition for the new Linux, once you are happy with it you start using it as default. By the next upgrade you install into the first partition...That way they overlap, and you can fall back if needed. I have not needed to fall back, but I could.

You use the same /home partition for both versions?

---

### Post by AlanR8 on 2009-10-29
Just to add my 2 pence/cents to the thread....

Been using Karmic since Alpha 3 on a Sony Vaio Laptop. EVERYTHING just works fine! Yes there were a few early network manager issues when connecting to mobile broadband but they were fixed a while ago. Keyboard mouse and touchpad....all work, sound works, video works, webcam works (small tweak), what else is there....

Oh yes. Since installing blueman (in karmic repos) I can now connect my Nokia Navigator (3.5g) directly to the web over bluetooth!

My opinion...best release yet!!!

---

### Post by lavinog on 2009-10-29
> **MrWES said:**
> You use the same /home partition for both versions?

You can, but the problem is that your user config files are located in home, and slight differences in releases could cause a problem.

I like to start a new home partition when I update, and just move my stuff over.  This helps get rid of the obsolete config files.
I also have a partition dedicated to storing files that don't change often, like my pictures, music, and iso files.  I just symlink the folders to my home profile.  This lets me keep my home partition relatively small.

---

### Post by MockY on 2009-10-29
> **AlanR8 said:**
> Just to add my 2 pence/cents to the thread....

Been using Karmic since Alpha 3 on a Sony Vaio Laptop. EVERYTHING just works fine! ...... sound works ..... what else is there....


Does the internal mic work as well? I'm installing right now so I guess I'm about to find out myself, but it sure would be nice if it did.

---

### Post by MockY on 2009-10-29
> **MockY said:**
> Does the internal mic work as well? I'm installing right now so I guess I'm about to find out myself, but it sure would be nice if it did.

Quoting myself, but now once I have installed it, out of the box, the internal mic does not work. The external one works but not the internal one. And I was really hoping this issue would be fixed... *sigh*

---

### Post by louieb on 2009-10-29
> **lavinog said:**
> Is it just system monitor that does this?  What if you disable desktop effects?  Are you using a nVidia card? 
System Monitor and the  notification area is all I've seen so far.  

IBM T30 laptop. ATI radon 7500 graphics. Desktop effects disabled.  

Not a show-stopper - just going to keep up with the updates and see if the issue gets fixed.  Laptop dual boots Karmic and Jaunty.  Still haven't decided which will get used.

---

### Post by asuastrophysics on 2009-10-29
> **bruno9779 said:**
> I did upgrade early, and I am fine with the changes: by upgrading (1 week) early I get more time to learn the changes.

I love the look and feel of the new Ubuntu. Finally a decent selection of wallpapers and themes, and so many little improvements.

Way to go !!!!!!

PS: my /home is on a different partition, I don't see what could go wrong

It isn't too bad since I've gotten used to it. I still don't have scrolling capability on my touchpad. 

But that new splash screen looks f**king awesome! :popcorn:

---

### Post by pizza-is-good on 2009-10-29
I downloaded Karmic this morning.
Created a LiveUSB later on the day and tried it.
Works very nice on me.

Will be doing a fresh install of it sometime this weekend.

It has a very nice, shiny, and modern look to it. Don't know why anyone would not want it...:popcorn:

---

### Post by asuastrophysics on 2009-10-29
> **Mornedhel said:**
> Duh. If you read the release notes ([http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)), you'd notice two things :

* HAL is deprecated
* The booting process is being converted to Upstart

So if you're planning on not upgrading until these "issues" have been resolved, you won't -- ever -- upgrade. Not to Karmic, not to Lucid, not to any modern distribution since transitioning away from init scripts is on the planning for most.

Did you even *try* "service gdm stop" ? Says to right there.

Now of course there will be issues with a distribution released today. It hasn't been tested as thoroughly as the previous version, obviously. Some things will probably be broken. "Don't upgrade if your current system is working and you don't need any of the new features" is the standard rule.

But you just picked two bugs (HAL and init -> Upstart) that really are features.

Yeah I tried "service gdm stop". That works brilliantly! but for some reason, "service gdm start" didn't work. Puzzling...

---

### Post by twright on 2009-10-29
> **asuastrophysics said:**
> Yeah I tried "service gdm stop". That works brilliantly! but for some reason, "service gdm start" didn't work. Puzzling...
Just try sudo start gdm

---

### Post by asuastrophysics on 2009-10-29
> **twright said:**
> Just try sudo start gdm

I reckon it didn't start because of the following message I got after downloading & installing the synaptics touchpad utility:

"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

So, after making this modification in /etc/X11/xorg.conf, I got some weird message after issuing "service gdm start", "sudo start gdm", and "startx"

The messages I got were slightly misleading. The real problem was my edit of the xorg.conf file. But I learned something from this:
**In these later editions of Ubuntu, almost no editing of the xorg.conf file is necessary. If you do need to edit it, do so with caution and make a backup. ** :D

Also: Don't install the synaptic utility. It seems to be a little outdated at the moment. lol

---

### Post by twright on 2009-10-29
You should undo that modification or delete xorg.conf completely; gsynaptics in not much use anymore and shmconfig is dangerous in any case. Anyway, good if you can get it working.
> **asuastrophysics said:**
> I reckon it didn't start because of the following message I got after downloading & installing the synaptics touchpad utility:

"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

So, after making this modification in /etc/X11/xorg.conf, I got some weird message after issuing "service gdm start", "sudo start gdm", and "startx"

The messages I got were slightly misleading. The real problem was my edit of the xorg.conf file. But I learned something from this:
**In these later editions of Ubuntu, almost no editing of the xorg.conf file is necessary. If you do need to edit it, do so with caution and make a backup. ** :D

Also: Don't install the synaptic utility. It seems to be a little outdated at the moment. lol

---

### Post by Vanishing on 2009-10-29
> **asuastrophysics said:**
> To anyone thinking of upgrading to Karmic early:

...Don't. It's not worth the pain. None of the commands are the same. 

```
/etc/init.d/hal restart
/etc/init.d/networking restart

```

none of the init.d commands work any more. Also, it has become increasingly difficult to stop X if you need to: 
```
jake@girdy-laptop:~$ /etc/init.d/gdm stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop gdm
jake@girdy-laptop:~$ 

```
As you can see, these commands no longer do anything. Also, expect possible touchpad regressions as HAL is changed to "udev".

Do not upgrade to Karmic early. It's always exciting to see a new release, but spare yourself the agony and don't try it early

[COLOR="Red"]**EDIT: This post was a bit overly dramatic. All in all, I am very happy with this new release. Just be smart people, and test your computer for bugs using a LiveCD first! **[/COLOR] :D

been using since toolchain, and tbh i actually enjoyed it..

---

### Post by 3rdalbum on 2009-10-30
I don't believe the change back to Init scripts is going to be pushed as an "update" :-)

I've been running Ubuntu 9.10 on most of my computers since the beta. I even ran an alpha version earlier on. It's an excellent release, but let's hope some more updates come soon.

---

### Post by dentharg on 2009-10-30
Been using Karmic since Alpha 2. No problems whatsoever. Have been living happily since then :)

---

### Post by asuastrophysics on 2009-10-30
Are any of you guys having performance regressions on synaptics touchpads? 

Just wondering if this bug was Acer Laptop specific, or touchpad specific. 

I have lost scrolling capabilities on my synaptics touchpad, and there isn't an option in System -> Preferences -> Mouse for scrolling capabilities. 

Anyone else share this issue?

---

### Post by jsc_moraga on 2009-10-30
> **Mornedhel said:**
> Duh. If you read the release notes 
Did you even *try* "service gdm stop" ? Says to right there.


I don't know if he did, but I did, and it doesn't work. Got any other ideas? I read the upstart page and there is no documentation on how a user should work with it, just on how to implement it as a developer.

jsc

---

### Post by k3lt01 on 2009-10-30
> **asuastrophysics said:**
> Are any of you guys having performance regressions on synaptics touchpads? 

Just wondering if this bug was Acer Laptop specific, or touchpad specific. 

I have lost scrolling capabilities on my synaptics touchpad, and there isn't an option in System -> Preferences -> Mouse for scrolling capabilities. 

Anyone else share this issue?Actually, on my Ubuntu system the touch pad is working as it should however my sisters laptop which the exact same model as mine except she uses Windows XP has terrible trouble with the touchpad.

---

### Post by Mornedhel on 2009-10-31
> **jsc_moraga said:**
> I don't know if he did, but I did, and it doesn't work. Got any other ideas? I read the upstart page and there is no documentation on how a user should work with it, just on how to implement it as a developer.

I just tried it:

```
sudo service gdm stop
```

shuts down gdm successfully and drops me to a console login.

I logged in the console session and typed

```
sudo service gdm start
```

and I was back into X.

I think you can probably use most of the "/etc/init.d/blah" commands you were used to, just replace "/etc/init.d/blah" by "service blah". Some services are still implemented as init scripts, even on a fresh Karmic install. If you've upgraded from a Jaunty install, it is possible that not everything was transitioned to Upstart.

Sorry for my cranky first post there, but it was obvious the OP hadn't bothered to read any documentation before ranting on how a new release was *different* from the previous.

---

### Post by Zoot7 on 2009-10-31
I managed to install my nVidia driver fine yesterday using
```
sudo /etc/init.d/gdm stop 
```
and starting gdm like that again.

Is it just me?

---

### Post by Mornedhel on 2009-10-31
> **Zoot7 said:**
> I managed to install my nVidia driver fine yesterday using
```
sudo /etc/init.d/gdm stop 
```
and starting gdm like that again.

Is it just me?

/etc/init.d/gdm (as well as a bunch of other entries in /etc/init.d) seems to be symlinked to /lib/init/upstart-job.

---

### Post by asuastrophysics on 2009-10-31
> **Mornedhel said:**
> /etc/init.d/gdm (as well as a bunch of other entries in /etc/init.d) seems to be symlinked to /lib/init/upstart-job.

hey how exactly are they symlinked? I tried this:
```
jake@girdy-laptop:~$ sudo /etc/init.d/gdm restart
[sudo] password for jake: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart gdm
jake@girdy-laptop:~$ 

```
but can't seem to get it to work. although i think my upgrade failed...

---

### Post by solwic on 2009-10-31
> **asuastrophysics said:**
> ...but can't seem to get it to work. although i think my upgrade failed...

Most likely.  Upgrades are known for their epic fails.  :P

Good luck.

---

### Post by lazycamel on 2009-11-01
It worked (almost) perfectly from the get-go for me.

Apart from the fact that despite spending hours and hours researching and trying different things, I haven't been able to get the nvidia drivers working perfectly since 8.04 - ie. no compiz, no pretty desktop effects. On 8.04 I managed it by manually configuring the graphics card and display in xorg.conf.

On a clean install of 9.04 more headaches but at least I finally got the full selection of available screen resolutions, but no compiz. And with 9.10, more graphics weirdness, as it makes the desktop larger than my screen for some reason on every startup, for no apparent reason.

I've given up trying to get desktop effects to work. A nice but in the end superficial feature.

Apart from that, 9.10 is perfect. The update procedure is very well done as well.

---

### Post by Shelton2142 on 2009-11-01
I used Wubi to get Karmic and I haven't noticed much of anything wrong at all, save for some bug report that shows up once in a while talking about a kernel problem, but then nothing happens. I've never used any Linux OS before, so I don't really know what to look for. I can't use command line either.

I got the version 185 Nvidia driver and it's running almost perfectly. I've got basic visual effects running, and I have yet to notice any real problems. I even turned on the flashy effects for a minute and they worked just fine. Now the only thing bothering me is that all the text on my screen is way too small. I can't seen to get the large text option that you can select at bootup to work once I'm in my desktop.

---

### Post by rockney on 2009-11-02
Worst mistake I've made in a while ... darn it.  Sure would have thought going from a new 9.04 "straight-up" installation to 9.10 would have gone better.

The 9.10 upgrade trashed a newly-built 9.04 with DTC and a lot of work setting things up.  Lost 2 weeks of work - boss will not be happy - besides working all weekend to "finish it"!

---

### Post by running_rabbit07 on 2009-11-02
> **rockney said:**
> Worst mistake I've made in a while ... darn it.  Sure would have thought going from a new 9.04 "straight-up" installation to 9.10 would have gone better.

The 9.10 upgrade trashed a newly-built 9.04 with DTC and a lot of work setting things up.  Lost 2 weeks of work - boss will not be happy - besides working all weekend to "finish it"!

Running APTonCD periodically helps prevent things like that from being major problems.

---

### Post by Paddy Landau on 2009-11-02
> **rockney said:**
> Lost 2 weeks of work - boss will not be happy - besides working all weekend to "finish it"!
That's why I always make a full partition or disk backup with [CloneZilla]("http://clonezilla.org/") before running risky things like upgrades.

Worst case: I lose a couple of hours while I restore, and I can go do something else while I'm waiting for the restore to finish.

Moral: Back up first!

---

### Post by solwic on 2009-11-02
> **paddy landau said:**
> that's why i always make a full partition or disk backup with [clonezilla]("http://clonezilla.org/") before running risky things like upgrades.

Worst case: I lose a couple of hours while i restore, and i can go do something else while i'm waiting for the restore to finish.

Moral: Back up first!

+1. I'd give you an applauding smiley, but it's not working for me.  :P

---

### Post by phillw on 2009-11-03
> **Paddy Landau said:**
> That's why I always make a full partition or disk backup with [CloneZilla]("http://clonezilla.org/") before running risky things like upgrades.

Worst case: I lose a couple of hours while I restore, and I can go do something else while I'm waiting for the restore to finish.

Moral: Back up first!

+1 also, although I use a little tar script to do mine 

```
sudo sh backup.sh
```And the script is from .... [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

(my actual script is in my blog )

As one of the people on here has in their sig. ** If you don't backup your important data, your data is obviously not important.**

My 'user' data is frequently backed up (~home), my entire system when I'm going to perform 'brain-surgery' on it.

::deep sigh::  Whilst I'm sorry your upgrade / install didn't go well for you - I still pull my hair out at people not backing stuff up.

My abc of preparing is in my 9.04-->9.10 Blog.  If it saves one person from not taking a backup, it'll have been worth it.

Phill.

---

### Post by asuastrophysics on 2009-11-03
> **Mornedhel said:**
> If you've upgraded from a Jaunty install, it is possible that not everything was transitioned to Upstart.
In theory everything should be, even on a 9.04-9.10 upgrade. It depends on whether or not the upgrade went successfully, which in my case, it didn't due to loss of an internet connection halfway through.

> **Mornedhel said:**
> Sorry for my cranky first post there, but it was obvious the OP hadn't bothered to read any documentation before ranting on how a new release was *different* from the previous.
By documentation, did you mean this?
```
jake@jake-laptop:~$ service gdm stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm stop

```
Because this is it, there is no official Ubuntu doc about this. I googled it. Nothing. Just a message in terminal. If you know of one, please let me know. Otherwise, see my new CLI commands reference thread below:
[http://ubuntuforums.org/showthread.php?t=1305179](http://ubuntuforums.org/showthread.php?t=1305179) 

Furthermore, as you can see (the above code output was a snapshot from my old broken upgrade) it didn't matter what I told terminal to do. Even the correct command would spew out the same message. So I did read the documentation, it just didn't work. 

It would be nice if it were easier to detect a broken upgrade. As of now, symptoms of one can consist of almost anything, from a blank screen to a borked version of terminal.

---

### Post by Paddy Landau on 2009-11-04
> **phillw said:**
> ... I use a little tar script to do mine
For data backup, I use two things: On-line backup ([SpiderOak]("https://spideroak.com/") has proved cheap and reliable with an occasional hiccough), and [rdiff-backup]("apt:rdiff-backup").

Both provide differential backups (meaning that the backups, after the initial one, are very fast, and you can restore old versions of files).

That way I have three backups (including my CloneZilla backup), one of them off-site.

---

### Post by JayKay3000 on 2009-11-04
No problems here. Even with the internet dropping out half way through it quite happily picked up where it left off.

I will get around to a clean install just to start from a clean slate.

I think there may be some errors because of the loss of connection but the os is working as I would expect.

I keep important documents on my other hard drives/partitions and use a small partition for the os which contains applications or stuff I don't care for loosing like I dunno... wallpapers and I have a usb drive for really important backup (even if it has blown 2 cases in about 2 years) and have xp and ubuntu on seperate hard drives in their own partitions so a clean install is just a matter of copying the crap off one drive to another.

However this is all from practice having lost important data in the past, getting annoyed, blaming my system when I should have prepared my self for a failure as a pc can be unpredictable and can potentially fail any time and will almost always fail at the worst possible time when you need it most.

Never assume something will 'just work' even with an os, even in modern times there are still glitches and there is so much hardware which means there is a high potential for problems with so much old and new hardware always being released and changed.

The moral is to Prepair to fail or fail to prepare.

---

### Post by Mornedhel on 2009-11-04
> **asuastrophysics said:**
> By documentation, did you mean this?
```
jake@jake-laptop:~$ service gdm stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm stop

```
Because this is it, there is no official Ubuntu doc about this. I googled it. Nothing. Just a message in terminal. If you know of one, please let me know.

Sure, here you are: [http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)

The page mentions Upstart and HAL. My point was, you were complaining about new features being introduced in Karmic, when it *was* documented that there would be changes. The links point to the projects' homepages, too, which in turn contain their respective documentation (this includes Upstart).

---

