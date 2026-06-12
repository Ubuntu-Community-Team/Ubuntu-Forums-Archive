---
title: "Synaptic, et al., will not authenticate"
date: 2011-11-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sgage on 2011-11-14
I thought I'd try a nice fresh install of Precise from yesterday's Daily. I find that programs that require root priveleges will not authenticate when launched from the launcher or the dash. These include synaptic, jockey, update manager, etc.

The authentication dialog comes up, but after entering the password, it is not recognized.

All of them work fine if started from a commandline with gksu <whatever>. 

What to do?

---

### Post by effenberg0x0 on 2011-11-14
> **sgage said:**
> I thought I'd try a nice fresh install of Precise from yesterday's Daily. I find that programs that require root priveleges will not authenticate when launched from the launcher or the dash. These include synaptic, jockey, update manager, etc.

The authentication dialog comes up, but after entering the password, it is not recognized.

All of them work fine if started from a commandline with gksu <whatever>. 

What to do?

I tried both the examples you mentioned and, weirdly, none of them even asked for a password. So I created a .desktop to launch nautilus as root using gksu. It worked OK. So I can't really reproduce what you are seeing there. Are you running a GUI session with the machine default user (uid 1000) or a guest / other user session?

---

### Post by sgage on 2011-11-14
> **effenberg0x0 said:**
> I tried both the examples you mentioned and, weirdly, none of them even asked for a password. So I created a .desktop to launch nautilus as root using gksu. It worked OK. So I can't really reproduce what you are seeing there. Are you running a GUI session with the machine default user (uid 1000) or a guest / other user session?

This is just a completely un-tweaked fresh install, running as a regular user, Unity 3D. The problem occurs in Unity 2D and Gnome Shell as well. Also Gnome Classic.

---

### Post by philinux on 2011-11-14
> **sgage said:**
> I thought I'd try a nice fresh install of Precise from yesterday's Daily. I find that programs that require root priveleges will not authenticate when launched from the launcher or the dash. These include synaptic, jockey, update manager, etc.

The authentication dialog comes up, but after entering the password, it is not recognized.

All of them work fine if started from a commandline with gksu <whatever>. 

What to do?

Just booted in to check.

Synaptic works just as expected.
Jockey and update manager dont need a password. UM would if there were new installs.

Maybe if you start synaptic from the CLI without gksu and see if any clues.

---

### Post by ventrical on 2011-11-14
Software Center just died with most recent omnibus.

[B]EDIT: Belay my last. This was on a compromised install.

All is well with SC.

[/B]

---

### Post by floydsp on 2011-11-14
Mine 12.04 alt install requires log in root....regular login pass word
does not work
Had to create root passwd and then works fine

Had to use alt download cause daily build live Precise will not install
giving error when it goes to set up partitions

floydsp

---

### Post by sgage on 2011-11-15
> **floydsp said:**
> Mine 12.04 alt install requires log in root....regular login pass word
does not work
Had to create root passwd and then works fine

Had to use alt download cause daily build live Precise will not install
giving error when it goes to set up partitions

floydsp

Ah ha! Mine was also an alternate install. I had also had an issue with the live CD with partition setup.

I will try another live CD install today, and if it still doesn't work, simply create a root password for the time being.

---

### Post by robert shearer on 2011-11-21
> **sgage said:**
> Ah ha! Mine was also an alternate install. I had also had an issue with the live CD with partition setup.

I will try another live CD install today, and if it still doesn't work, simply create a root password for the time being.

How did that go..?
I too am having the failure to authenticate when starting synaptic other than from cli with gksu.

> Mine was also an alternate install. I had also had an issue with the live CD with partition setup.
Ditto.....

any fix other than reinstalling..?

---

### Post by ronacc on 2011-11-21
the fix to the installer crashing when partitioning is here [http://ubuntuforums.org/showthread.php?t=1874553](http://ubuntuforums.org/showthread.php?t=1874553) post # 6

---

### Post by robert shearer on 2011-11-21
> **ronacc said:**
> the fix to the installer crashing when partitioning is here [http://ubuntuforums.org/showthread.php?t=1874553](http://ubuntuforums.org/showthread.php?t=1874553) post # 6

Thanks,
If you refer to this...
> Temporary workaround
change #! /bin/sh to #! /bin/bash in /lib/partman/choose_partition/60partition_tree/do_option
Ignore Crashes... It's Worked for me !!!
then I may need a little more guidance as to when and where to run this during the install..?? 

Which is why I used the alternate disc as at least it would install **and** the candidate has only a cd drive so the live oversize image needing a dvd is not an option. :(

Frustrating that both install mediums have show-stopping bugs...:(

Any fix for the failure to authenticate on the already installed 12.04 would be welcome... :)

Cheers, Bob.

---

### Post by ronacc on 2011-11-21
can't help with the authenticate problem I do not have that on my precise install , it works fine .

on the when to do the edit during install , when the live cd (or usb stick ) boots select try ubuntu without installing the after the desktop loads but BEFORE running install ubuntu bring up a term and enter ```
 sudo gedit 
``` just enter return when it asks for a password , it is blank for the installer . then in gedit open  /lib/partman/choose_partition/60partition_tree/do_option  and add a ba infront of the sh in   #! /bin/sh  changing it to   #! /bin/bash   and save it . then you can run install ubuntu ( from the desktop icon ) and it won't crash when partitioning . do not reboot or the edit will be lost ,it is only in memory no burned to the cd .

---

### Post by robert shearer on 2011-11-21
Thank you, ronacc..!
 That's superbly explained and more than adequate to get me there, most appreciated.  :D

Edit.. reinstalled from live daily image via usb flash-drive and permissions problem is fixed...!
Many thanks to ronacc et al...:D:D

---

### Post by sgage on 2011-11-22
I did a fresh install of PP from the LiveCD this morning, and still have the same problem with authentications.

Any idea what's going on?

---

### Post by effenberg0x0 on 2011-11-22
> **sgage said:**
> I did a fresh install of PP from the LiveCD this morning, and still have the same problem with authentications.

Any idea what's going on?

On a fresh install? This is very odd...

Try this:

```
echo -e "[Desktop Entry]\nName=Test\nComment=A test\nExec=/usr/bin/gksu /usr/bin/update-manager\nIcon=user-home\nTerminal=false\nType=Application\nStartupNotify=true\nCategories=GNOME;GTK;Utility;Core;\nMimeType=inode/directory;application/x-gnome-saved-search;\nX-GNOME-Bugzilla-Bugzilla=GNOME\nX-GNOME-Bugzilla-Component=general\nX-GNOME-Bugzilla-Version=3.2.1\nX-Ubuntu-Gettext-Domain=gksu" | tee $HOME/.local/share/applications/mytest.desktop

unity --replace &

```Dash / Search / Run test, try to auth on gksu

cat /var/log/auth.log and /var/log/syslog to see if there's anything of use in it, some lead for us to understand what's going on there.

---

### Post by effenberg0x0 on 2011-11-22
Are you somehow added to root user group?
```
$ groups $(whoami)
```How's your /etc/sudoers? it should have this:
```
root    ALL=(ALL:ALL) ALL
%admin ALL=(ALL) ALL
%sudo    ALL=(ALL:ALL) ALL
#includedir /etc/sudoers.d (commented line and it's an empty dir, just a readme file there)
```Is your user UID:GID 1000 or more? 
```
$ sudo cat /etc/passwd | grep $(whoami)
ahsl:x:1001:1001:Alvaro,Leal,,:/home/ahsl:/bin/bash
```Is /bin/bash pointing to dash?
```
ls -la /bin/bash
```Is your ~/.bashrc normal (like, you're not sudoing or su'ing inside it)?
Another possibility: Any chance you added youself to the sudo group? If you're part of it, you can run whatever with no sudo needed.

---

### Post by sgage on 2011-11-22
> **effenberg0x0 said:**
> Are you somehow added to root user group?
```
$ groups $(whoami)
```How's your /etc/sudoers? it should have this:
```
root    ALL=(ALL:ALL) ALL
%admin ALL=(ALL) ALL
%sudo    ALL=(ALL:ALL) ALL
#includedir /etc/sudoers.d (commented line and it's an empty dir, just a readme file there)
```Is your user UID:GID 1000 or more? 
```
$ sudo cat /etc/passwd | grep $(whoami)
ahsl:x:1001:1001:Alvaro,Leal,,:/home/ahsl:/bin/bash
```Is /bin/bash pointing to dash?
```
ls -la /bin/bash
```Is your ~/.bashrc normal (like, you're not sudoing or su'ing inside it)?
Another possibility: Any chance you added youself to the sudo group? If you're part of it, you can run whatever with no sudo needed.

Thanks for all your suggestions - I'm on the go right now and don't have time to experiment. The stock synaptic launcher points to something called synaptic-pkexec, which seems to be the problem. A simple gksu synaptic from a command line works fine.

I will try to experiment tomorrow...

---

### Post by effenberg0x0 on 2011-11-22
> **sgage said:**
> Thanks for all your suggestions - I'm on the go right now and don't have time to experiment. The stock synaptic launcher points to something called synaptic-pkexec, which seems to be the problem. A simple gksu synaptic from a command line works fine.

I will try to experiment tomorrow...

I'll have a look at it later too, see if I can reproduce the behavior. (fixed under advice of robert shearer)

---

### Post by robert shearer on 2011-11-22
Fixed, to avoid confusion ....:)
> I'll have a look at it later too, see if I can reproduce the behaviour.

---

### Post by effenberg0x0 on 2011-11-22
> **robert shearer said:**
> Fixed, to avoid confusion and embarrasment....:)

LOL. So, I just found out I can't reproduce. I'll depend on the wife for that :(
I need a proof reader. Multitasking plus typing fast in English is hard...

---

### Post by mc4man on 2011-11-22
New installs like from today will show issues with policykit - it's going to want the "root" password for many actions. (as seen does not affect sudo
Ex. attached for synaptic though not limited to synaptic

Easily temp fixed by editing affected actions in /usr/share/polkit-1/actions/*, setting where needed from 'auth_admin_keep' or 'auth_admin' to 'yes' on the <allow_active> line(s)  or quite permanently  thru a .pkla or 2 that removes the need to auth altogether

( a little early here to put useful .pkla's in place - would never know this bug existed if they were, but will soon.


Edit: - solved by adding myself to the admin group,(/etc/group), the install failed to do so

---

### Post by effenberg0x0 on 2011-11-22
> **mc4man said:**
> New installs like from today will show issues with policykit - it's going to want the "root" password for many actions. (as seen does not affect sudo
Ex. attached for synaptic though not limited to synaptic

Easily temp fixed by editing affected actions in /usr/share/polkit-1/actions/*, setting where needed from 'auth_admin_keep' or 'auth_admin' to 'yes' on the <allow_active> line(s)  or quite permanently  thru a .pkla or 2 that removes the need to auth altogether

( a little early here to put useful .pkla's in place - would never know this bug existed if they were, but will soon.


Edit: - solved by adding myself to the admin group,(/etc/group), the install failed to do so

Looking here, I couldn't find anything visibly wrong with my policies. I don't have any problem with su. But it intrigues me that sgage is seeing this after a clean install. 

When you mention your install failed to add you to admin group: Hasn't happened to me, but I have seen some reports in which UID 1000 is not on admin, lpadmin, etc. I'm wondering how/where this is happening. Do you have any lead (something different during install, any warning message, etc)? If sgage confirms to be in sudo or root group, as I suspect, we have to find out how this is happening - it would be a serious one to report and fix asap.

---

### Post by mc4man on 2011-11-22
Not all that up on group stuff - 
this is the relevant from a fresh install tonight where root password was being requested for several actions
> [noparse]lpadmin:x:116:doug
ssl-cert:x:117:
admin:x:118:[/noparse]

When adding my username(doug) then the normal password prompt was shown & things could be done as expected
[noparse]admin:x:118:doug[/noparse]

simile is a : with an x

---

### Post by effenberg0x0 on 2011-11-22
> **mc4man said:**
> Not all that up on group stuff - 
this is the relevant from a fresh install tonight where root password was being requested for several actions


When adding my username(doug) then the normal password prompt was shown & things could be done as expected
admin:x:118:doug

simile is a : with an x

Yes, because on /etc/sudoers you have to be part of admin to properly sudo. Well, this is clearly wrong. I'll try some installs to see if I can spot what's going on.

**EDIT: **Just remembered I had a PP64VM installed today and checked it:


$ groups ahsl
```
ahsl : ahsl adm dialout cdrom plugdev lpadmin admin sambashare

```It's correct... There's some other condition triggering it.

---

### Post by ronacc on 2011-11-22
could it have something to do with the way you ran the installer ? I used the amd64 desktop cd and on boot chose try without installing and ran the installer from the desktop icon , I did notice that after clicking on the Icon it asked for authentication before the installer ran , that is new to me .during install I chose manual ( something else ) partitioning , also I did not encrypt my /home . I do not have the authenticate problem and have not had it on any of my installs of the daily's . perhaps if we compare notes we can find something in common that those who have the problem did .

---

### Post by mc4man on 2011-11-22
Maybe i'll do a new one, never too attached to any dev install anyway

(on a side note - the current iso's apport can't use 'ubuntu-bug' (no gnome-open

This is possibly the relevant section from the installer (ubiquity) log

> Nov 23 00:23:32 ubuntu user-setup: Shadow passwords are now on.
Nov 23 00:23:33 ubuntu user-setup: Adding user `doug' ...
Nov 23 00:23:33 ubuntu user-setup: Adding new group `doug' (1000) ...
Nov 23 00:23:33 ubuntu user-setup: Adding new user `doug' (1000) with group `doug' ...
Nov 23 00:23:33 ubuntu user-setup: Creating home directory `/home/doug' ...
Nov 23 00:23:33 ubuntu user-setup: Copying files from `/etc/skel' ...
Nov 23 00:23:34 ubuntu user-setup: addgroup: The group `lpadmin' already exists as a system group. Exiting.
Nov 23 00:23:34 ubuntu user-setup: Adding group `sambashare' (GID 124) ...
Nov 23 00:23:34 ubuntu user-setup: Done.
Nov 23 00:23:34 ubuntu user-setup: Adding user `doug' to group `adm' ...
Nov 23 00:23:34 ubuntu user-setup: Adding user doug to group adm
Nov 23 00:23:34 ubuntu user-setup: Done.
Nov 23 00:23:34 ubuntu user-setup: Adding user `doug' to group `cdrom' ...
Nov 23 00:23:34 ubuntu user-setup: Adding user doug to group cdrom
Nov 23 00:23:34 ubuntu user-setup: Done.
Nov 23 00:23:34 ubuntu user-setup: Adding user `doug' to group `dip' ...
Nov 23 00:23:34 ubuntu user-setup: Adding user doug to group dip
Nov 23 00:23:34 ubuntu user-setup: Done.
Nov 23 00:23:35 ubuntu user-setup: Adding user `doug' to group `lpadmin' ...
Nov 23 00:23:35 ubuntu user-setup: Adding user doug to group lpadmin
Nov 23 00:23:35 ubuntu user-setup: Done.
Nov 23 00:23:35 ubuntu user-setup: Adding user `doug' to group `plugdev' ...
Nov 23 00:23:35 ubuntu user-setup: Adding user doug to group plugdev
Nov 23 00:23:35 ubuntu user-setup: Done.
Nov 23 00:23:35 ubuntu user-setup: Adding user `doug' to group `sambashare' ...
Nov 23 00:23:35 ubuntu user-setup: Adding user doug to group sambashare
Nov 23 00:23:35 ubuntu user-setup: Done.
Nov 23 00:23:35 ubuntu user-setup: Adding user `doug' to group `sudo' ...
Nov 23 00:23:35 ubuntu user-setup: Adding user doug to group sudo
Nov 23 00:23:35 ubuntu user-setup: Done.

---

### Post by mc4man on 2011-11-22
> **ronacc said:**
> could it have something to do with the way you ran the installer ? I used the amd64 desktop cd and on boot chose try without installing and ran the installer from the desktop icon , I did notice that after clicking on the Icon it asked for authentication before the installer ran , that is new to me .during install I chose manual ( something else ) partitioning , also I did not encrypt my /home . I do not have the authenticate problem and have not had it on any of my installs of the daily's . perhaps if we compare notes we can find something in common that those who have the problem did .

this current was todays iso - 
i386
try first
did the partman edit
clicked on desktop icon, already have forgotten if auth was requested, will pay attention next time
manual install
no encryption

---

### Post by ronacc on 2011-11-22
well we did everything the same except for the arch . I'll try a new install tomorrow , my last was the 18th , maybe this came up after that .

---

### Post by robert shearer on 2011-11-22
Yesterdays daily here... 
i386
try first
did the partman edit
clicked on desktop icon,  auth was requested,
manual install
no encryption


Runs fine,
no authentication errors, all good.

The only odd thing was the iso I downloaded was shown as 701Mb on the download page but was 735Mb downloaded. Md5sum check was correct.

---

### Post by mc4man on 2011-11-22
Did a redo, same iso
(didn't request auth for anything which isn't unexpected, the live cd has a .pkla that bypasses policykit

Same deal, no username added to admin group
[filed a bug ]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/893842")though bugs on ubiquity, while sometimes useful, many time are just a bit more internet debris

Ot.
I'm a big fan of 'mutlipath' except when the paths are boring, then I prefer easiest for Me. The removal of nautilus-gksu, well, just don't get it.
(can be installed from OO & linked or copied to enable. 
Have never seen any issue with except a comment from a nautilus dev who basically said nautilus should never be run in a root browser, period.

---

### Post by ronacc on 2011-11-24
finally got yesterdays daily installed and it as mc4man says .must have happened with a recent update my install from the 18th was not that way .

---

### Post by effenberg0x0 on 2011-11-24
Are you guys seeing it on the x86 iso? I can't see this when I install x86-64.

---

### Post by philinux on 2011-11-24
> **effenberg0x0 said:**
> Are you guys seeing it on the x86 iso? I can't see this when I install x86-64.

Synaptic is ok here on 64 bit but update manager hung. Had to xkill it.

---

### Post by mc4man on 2011-11-24
Did a 64 bit install last night with the 11/23 image  - same deal
(could see it right after the install finished by opening the new partition so went ahead & edited it before rebooting

---

### Post by philinux on 2011-11-24
> **mc4man said:**
> Did a 64 bit install last night with the 11/23 image  - same deal
(could see it right after the install finished by opening the new partition so went ahead & edited it before rebooting

Ah so it's related to the new images not getting /etc/group set up correctly.

Mine's a 11.10 install upgrade to 12.04. Still update manager won't authenticate.

---

### Post by ronacc on 2011-11-24
my 64bit install from yesterdays .iso (nov 23 ) also does not have me added to admin .

---

### Post by philinux on 2011-11-24
> **ronacc said:**
> my 64bit install from yesterdays .iso (nov 23 ) also does not have me added to admin .

I guess sudo from cli works ok because of correctly set up sudoers?

---

### Post by mc4man on 2011-11-24
There are current issues with both update-manager & Software-center, probably the same.
Even if you override the auth thru a .pkla they will only work once, after that the only way to get to work again is delete their folders in ~/
(.cache & maybe.config ) & do a full restart, they then work once

I believe the issue is known, filed a bug on the Sc crash but it got duped to a private bug so have no idea what's up.
(would certainly expect this to be sorted by A1

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/894126](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/894126)

If you are running an upgrade tester or recent image fresh you may want to turn on apport & associate .crash files with apport though there are 2 long standing crashes that can be ignored

---

### Post by jppr on 2011-11-24
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/893842](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/893842)

---

### Post by ronacc on 2011-11-24
yes sudo from cli OK gksudo from cli NO .

---

### Post by cariboo on 2011-11-24
Merged two threads on the same subject.

---

### Post by effenberg0x0 on 2011-11-26
Is [this]("http://ubuntuforums.org/showthread.php?t=1886965") an example of an install that eventually got the user out of the admins group or messed up /etc/sudoers? I find it very hard to believe that such a beginner managed to change root's passwd or it's own user groups.

**EDIT: **
The help advice he got was to reinstall Ubuntu, so we'll never know what went down now. In a couple  more posts he will loose access to his window partition, etc. Great advice. 
It's a shame  people with more than 2 thousand posts couldn't direct him to boot in  recovery and unset root password, fix user password and groups, check/fix sudoers. One cut&paste line could fix things for him...

---

### Post by ventrical on 2011-11-26
> **effenberg0x0 said:**
> Is [this]("http://ubuntuforums.org/showthread.php?t=1886965") an example of an install that eventually got the user out of the admins group or messed up /etc/sudoers? I find it very hard to believe that such a beginner managed to change root's passwd or it's own user groups.

**EDIT: **
The help advice he got was to reinstall Ubuntu, so we'll never know what went down now. In a couple  more posts he will loose access to his window partition, etc. Great advice. 
It's a shame  people with more than 2 thousand posts couldn't direct him to boot in  recovery and unset root password, fix user password and groups, check/fix sudoers. One cut&paste line could fix things for him...

I seen that.  Its hard to catch everything ;)

---

### Post by effenberg0x0 on 2011-11-26
> **ventrical said:**
> I seen that.  Its hard to catch everything ;)

Yeah... I usually lurk the General Help section and PM the guys that have interesting issues to help them get up and running but also get the info I need. But weekend helpers are bored and fast. Anyway, they should put some sort of a "Trusted Helper Badge" Gif on users/members than actually know Linux.

---

### Post by effenberg0x0 on 2011-11-26
> **ventrical said:**
> I seen that.  Its hard to catch everything ;)

Yeah... I usually lurk the General Help section and PM the guys that have interesting issues to help them get up and running but also get the info I need. But weekend helpers are bored and fast. Anyway, they should put some sort of a "Trusted Helper Badge" Gif on users/members than actually know Linux. Current status icons as well as post counts are misleading to the newbie.

---

### Post by mc4man on 2011-11-26
In any event - the 'issue' with the latest images not adding the installer (first user) to the admin group has been fixed.

The admin group is no longer being used, Administrator accounts are now just using the sudo group. Policykit & some other packages have been adjusted to account for this and also allow the admin group as per the individual policies

If one uses a custom .pkla then probably better to start using, 
Identity=unix-group:sudo

---

