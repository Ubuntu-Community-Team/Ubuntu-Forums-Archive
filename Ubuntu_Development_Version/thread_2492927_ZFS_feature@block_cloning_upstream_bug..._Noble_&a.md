---
title: "ZFS feature@block_cloning upstream bug... Noble &amp; Mantic"
date: 2023-11-27
forum: Ubuntu Development Version
---

### Post by MAFoElffen on 2023-11-27
This affects both Mantic and Noble: 
[https://github.com/openzfs/zfs/pull/15571](https://github.com/openzfs/zfs/pull/15571)
[https://www.theregister.com/2023/11/27/openzfs_2_2_0_data_corruption/](https://www.theregister.com/2023/11/27/openzfs_2_2_0_data_corruption/)

The ZFS pool feature: "feature@block_cloning" was released in Mantic (zfs-linux 2.2.0). It is the same currently in Noble. It is not the root cause of the bug (was in code from long ago), but that feature being enabled uncovered it. If you look at the pool properties of that feature in Mantic and Noble (so far) bpool is disabled. rpool that feature is enabled...

There is a CVE filed on it, as with Security, the concern was data integrity. 
RE: [https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-49298](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-49298)

I filed a bug on it at Launchpad, 
RE: [https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2044969](https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2044969)
so they are looking for the patch with was approve late this afternoon, and built tonight. I also proposed that zfs-linux version 2.2.1 was released on Nov 21, 2023, and that version be pushed through for Noble, so we can test and verify it here in the DEV Cycle for Noble. The Bug Report, because it has a recommendation to deal with the CVE-2023-49298, is marked as a Security Concern, so is marked as private.

---

### Post by TheMTtakeover on 2023-11-28
Thanks for submitting the bug report. Do you know if 2.2.1 get pushed to Mantic as well? I'm currently on Mantic trying to figure out the best way to proceed.

---

### Post by #&amp;thj^% on 2023-11-28
Here is how sets currently
```
 zfs-dkms | 2.1.2-1ubuntu3         | jammy/universe           | all
 zfs-dkms | 2.1.5-1ubuntu6~22.04.2 | jammy-security/universe  | all
 zfs-dkms | 2.1.5-1ubuntu6~22.04.2 | jammy-updates/universe   | all
 zfs-dkms | 2.1.9-2ubuntu1         | lunar/universe           | all
 zfs-dkms | 2.1.9-2ubuntu1.2       | lunar-security/universe  | all
 zfs-dkms | 2.1.9-2ubuntu1.2       | lunar-updates/universe   | all
 zfs-dkms | 2.2.0~rc3-0ubuntu4     | mantic/universe          | all
 zfs-dkms | 2.2.0-0ubuntu1~23.10   | mantic-proposed/universe | all
 zfs-dkms | 2.2.0-0ubuntu3         | noble/universe           | all
 zfs-dkms | 2.2.1-0ubuntu1         | noble-proposed/universe  | all

```
Sorry
Also some info found on Noble: [https://ubuntuforums.org/showthread.php?t=2492886&p=14167098#post14167098](https://ubuntuforums.org/showthread.php?t=2492886&p=14167098#post14167098)

---

### Post by TheMTtakeover on 2023-11-28
That's disappointing. It looks like 2.2.1 is only proposed for noble currently

---

### Post by #&amp;thj^% on 2023-11-28
Indeed, lets hope for the best on Mantic though, it's still early enough for it to get pushed there, but will they?
EDIT: I had nothing to lose now so I reinstalled Noble with proposed enabled.
Updated and dist-upgrade with:
```
apt policy zfs-dkms
zfs-dkms:
  Installed: 2.2.0-0ubuntu3
  Candidate: 2.2.0-0ubuntu3
  Version table:
     2.2.1-0ubuntu1 100
        100 http://archive.ubuntu.com/ubuntu noble-proposed/universe amd64 Packages
        100 http://archive.ubuntu.com/ubuntu noble-proposed/universe i386 Packages
 *** 2.2.0-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu noble/universe i386 Packages
        100 /var/lib/dpkg/status

```
First reboot was good.
Now this is where I lost it yesterday>>>No Cold Boot! bpool zapped.
Today after a couple of reboots, still good. Now I shut down for 15 minutes, and still good here.
NOTE: This is just me keeping notes, not suggested or advised.
Now I will slowly put it through what I did to it yesterday
EDIT2: Shutdown for 1 hr still good

---

### Post by MAFoElffen on 2023-11-28
I would think that at least the patch, since connected to CVE-2023-49298, that would need to be backported back through 20.04 LTS. Albeit, the new feature introduced into 23.10 uncovered the underlying bug, but it existed before then, so needs to be applied to all supported versions of Ubuntu & it's flavors. That goes for ESM supported as well.

The feature@block_cloning didn't exist for 22.10 and earlier, but the underlying bug did. Uncovered was that the code was from 2012.

Once that patch is backported, then no-one will need to make any changes to their installed pools.

In proposed? I should try to edit the sources in the installer process (under the covers) so it turns on "proposed" in Noble to installer before it creates the pools, so that it installs as zfs-linux 2.2.1 and start testing it...

We can override it in the autoinstall early commands, but because the new installer rsyncs the system from a install image in the Snap, then I would have to add it again in late commands. And i have a bug turned in on the Late Commands not working, and that patch is still in test, in the ubuntu-desktop-installer beta channel. Oh well, more testing to do to try to figure that out. I'm sure there is a way. 

I'm thinking maybe if I use "Try", change the LiveEnv's source.list to proposed temporarily, just to install zfs-linux 2.2.1 to the LiveEnv, then change it back, that when the installer goes to install it, it will see newer there and skip that part and continue... Then after the install, mount target, change the sources list to proposed temporarily again to install that as 2.2.1 again to the installed instance... Before the first boot. Hopefully. LOL.

Downloading today's Daily to try that...

---

### Post by TheMTtakeover on 2023-11-28
Looks like the patch is completed.

[https://github.com/openzfs/zfs/issues/15526#issuecomment-1830741676](https://github.com/openzfs/zfs/issues/15526#issuecomment-1830741676)

---

### Post by MAFoElffen on 2023-11-28
Tested on today's Noble desktop daily (2023.11.28)

For sources.list
```

sudo echo "deb http://archive.ubuntu.com/ubuntu/ noble-proposed main restricted universe" >> /etc/apt/sources.list

```
In terminal in LiveEnv:
```

sudo apt update
sudo apt install -y zfsutils-linux=2.2.1-0ubuntu1 libnvpair3linux=2.2.1-0ubuntu1 libuutil3linux=2.2.1-0ubuntu1 libzfs4linux=2.2.1-0ubuntu1 libzpool5linux=2.2.1-0ubuntu1

```
During the install, I could see that it had copied zfs utils of version 2.2.0. After the install, Before rebooting, I renistalled the proposed zfsutils-linux and all it's dependencies at version 2.2.1-0ubuntu1, BUT...

After reboot, the ZFS module is still:
```

mafoelffen@noble-d05:~$ sudo dmesg | grep 'ZFS: Loaded module'
[    2.451653] ZFS: Loaded module v2.2.0~rc3-0ubuntu4, ZFS pool version 5000, ZFS filesystem version 5

```
Which was rsync'ed from the Snap image or built during the installation process becasue the version rsync'ed from inside the Snap image were the earlier version(?)

I had to renable proposed sources, to install zfs-dkms=2.2.1-0ubuntu1, which then saw that it needed to be signed, so asked for a password for mokutil to enroll the key... (Which is actually something the Noble installer itself is skipping over and I have a bug filed on...)

Then 
```

mafoelffen@noble-d05:~$ sudo dmesg | grep 'ZFS: Loaded module'
[sudo] password for mafoelffen: 
[    2.209880] ZFS: Loaded module v2.2.1-0ubuntu1, ZFS pool version 5000, ZFS filesystem version 5

mafoelffen@noble-d05:~$ sudo zpool get feature@block_cloning
NAME   PROPERTY               VALUE                  SOURCE
bpool  feature@block_cloning  disabled               local
rpool  feature@block_cloning  active                 local

```
Test: Was a waste of time. Everything in the Noble test Case is now ZFS Version 2.2.1, but the canned script still creates the pools as/under 2.2.0. How do I know that? because rpool has that feature enabled on rpool. In 2.2.1, that feature was disabled as it's default.

Conclusion: That is not going to change until they update the install image inside Snap 'ubuntu-desktop-installer'... 

### But, the good side of this, 1fallen and I can test and verify ZFS 2.2.1 so it can get pushed from proposed to main for Noble.

---

### Post by #&amp;thj^% on 2023-11-28
Dang this cold boot failed, I hope no one else is doing what I did....you was warned.

---

### Post by MAFoElffen on 2023-11-28
@1fallen -- You have a PM...

LOL. ??? What did you do?

They lied about 2.2.1's property defaults. feature@block_cloning was still default set to enabled. i created a dpool and it was set to enabled. I destroyed it, and had to explicitly add
```

-o feature@block_cloning=disabled

```
to disable it.

That is going to have to be added to the canned ZFS scripts in the creation of rpool.

Mine is still working... Do I need to post the details of what I did to get it installed as?

---

### Post by aljames2 on 2023-11-28
Really appreciate all the work you all are doing, getting out there ahead of the train clearing the tracks for us.  Wish I could help, thanks again!

---

### Post by #&amp;thj^% on 2023-11-28
> **MAFoElffen said:**
> @1fallen -- You have a PM...

LOL. ??? What did you do?

They lied about 2.2.1's property defaults. feature@block_cloning was still default set to enabled. i created a dpool and it was set to enabled. I destroyed it, and had to explicitly add
```

-o feature@block_cloning=disabled

```
to disable it.

That is going to have to be added to the canned ZFS scripts in the creation of rpool.

Mine is still working... Do I need to post the details of what I did to get it installed as?

Gaul Dang it and you just know i wanted to use use other words ;)
It works just fine, I had my Dock turned off, but i'm still good here .....Woot Woot
Heading to my PM booth now, over and out.
```
dmesg | grep 'ZFS: Loaded module'
[    5.614641] ZFS: Loaded module v2.2.0~rc3-0ubuntu4, ZFS pool version 5000, ZFS filesystem version 5

```
```
zpool status
  pool: bpool
 state: ONLINE
config:

	NAME                                    STATE     READ WRITE CKSUM
	bpool                                   ONLINE       0     0     0
	  c2a655e8-146a-492f-8fd4-76fce0243100  ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
config:

	NAME                                    STATE     READ WRITE CKSUM
	rpool                                   ONLINE       0     0     0
	  191e900b-c1d7-4a1b-9374-c0a8c30d72b4  ONLINE       0     0     0

errors: No known data errors

```
And \```
pro fix CVE-2023-49298
CVE-2023-49298: 
OpenZFS through 2.1.13 and 2.2.x through 2.2.1, in certain scenarios
involving applications that try to rely on efficient copying of file data,
can replace file contents with zero-valued bytes and thus potentially
disable security mechanisms. NOTE: this issue is not always security
related, but can be security related in realistic situations. A possible
example is cp, from a recent GNU Core Utilities (coreutils) version, when
attempting to preserve a rule set for denying unauthorized access. (One
might use cp when configuring access control, such as with the
/etc/hosts.deny file specified in the IBM Support reference.) NOTE: this
issue occurs less often in version 2.2.1, and in versions before 2.1.4,
because of the default configuration in those versions.
 - https://ubuntu.com/security/CVE-2023-49298

No affected source packages are installed.

&#10004; CVE-2023-49298 does not affect your system.

```
EDIT: This from over nite, is still working

---

### Post by TheMTtakeover on 2023-12-01
2.2.2 has been released

[https://github.com/openzfs/zfs/releases/tag/zfs-2.2.2](https://github.com/openzfs/zfs/releases/tag/zfs-2.2.2)

---

### Post by MAFoElffen on 2023-12-01
Yes, but: [https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2044969](https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2044969)

Even though I have that Linked to the CVE, no one has even triaged that. (I feel like it's being ignored...) Maybe they are still on holiday?

Released, but will take awhile to get downstream. The CVE link should speed that up. I noted that in the Bug report.

I don't know what else to do to get it pushed along "harder".

---

### Post by pgjensen on 2023-12-01
There's a PPA for mantic with zfs 2.2.2, but be warned that I couldn't cleanly upgrade from my mantic 2.2.0~rc3 version and ran into some weird issues with processes getting killed, including my logins.  I ultimately had to rollback.  If anyone has a test system they could give it a shot.

[https://launchpad.net/~satadru-umich/+archive/ubuntu/zfs-experimental/](https://launchpad.net/~satadru-umich/+archive/ubuntu/zfs-experimental/)

---

### Post by TheMTtakeover on 2023-12-02
> **MAFoElffen said:**
> Yes, but: [https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2044969](https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2044969)

Even though I have that Linked to the CVE, no one has even triaged that. (I feel like it's being ignored...) Maybe they are still on holiday?

Released, but will take awhile to get downstream. The CVE link should speed that up. I noted that in the Bug report.

I don't know what else to do to get it pushed along "harder".

Yeah, I expected more activity on it honestly. Timelines have been given for FreeBSD, Proxmox, and Truenas, but nothing on the Ubuntu front. It looks like 2.2.2 is still keeping block duplication off. Since my pool was created on 23.10 I have block duplication on. I feel like at this point I need to blow the whole pool away and start over to be safe. Unfortunate timing for me, I just switched to ZFS like a month ago because I felt like I was missing out on all the data integrity features. Almost wishing I would have stuck with ntfs and drivepool at this point.

---

### Post by #&amp;thj^% on 2023-12-02
Wow, I just have a hard time with all of this ignoring form Ubuntu's side:
```
aur/zfs-dkms 2.2.2-1 
```
It's been ready for Arch fir a few days now. (Along with those already mentioned above)
I feel really bad for the users who got caught up in this very evil update.
This dose not set well for Ubuntu. :(
I see where in the bug report MAFoElffen reported it came in on Noble last nite.

---

### Post by MAFoElffen on 2023-12-02
> **1fallen said:**
> Wow, I just have a hard time with all of this ignoring form Ubuntu's side:
```
aur/zfs-dkms 2.2.2-1 
```
It's been ready for Arch fir a few days now. (Along with those already mentioned above)
I feel really bad for the users who got caught up in this very evil update.
This dose not set well for Ubuntu. :(
[COLOR=#ff0000]I see where in the bug report MAFoElffen reported it came in on Noble last nite.[/COLOR]
I reported that zfs-linux 2.2.2 was released upstream at OpenZFS, so that they get their heads out of their <<Censored>> and wake up.

I don't know what else to do. I want to do more and be more invloved. I asked around about personally getting involved with helping ZFS on Ubuntu... Somewhere that makes a difference. I ended up at a dead end. So I do what I can.

I had joined as a member of the Launchpad Group: "Native ZFS Users Group" Team... But I don't see where anything there really makes any kind of difference with anything at all. The group's email is at zfsonlinux.org, and I don't even see anything there that mentions that groups at all. And nothing that points back to Launchpad or Ubuntu.

Any ideas?

---

### Post by #&amp;thj^% on 2023-12-02
> **MAFoElffen said:**
> I reported that zfs-linux 2.2.2 was released upstream at OpenZFS, so that they get their heads out of their <<Censored>> and wake up.
My bad, I was hoping it was coming down the line soon.
> **MAFoElffen said:**
> 
I don't know what else to do. I want to do more and be more invloved. I asked around about personally getting involved with helping ZFS on Ubuntu... Somewhere that makes a difference. I ended up at a dead end. So I do what I can.

I had joined as a member of the Launchpad Group: "Native ZFS Users Group" Team... But I don't see where anything there really makes any kind of difference with anything at all. The group's email is at zfsonlinux.org, and I don't even see anything there that mentions that groups at all. And nothing that points back to Launchpad or Ubuntu.

Any ideas?

Dude your doing the best anyone has done in a long time, you show great effort and skill 100% all the time.
Idea's??? You really don't want to ask me. LOL I would most certainly incur an infraction. ;)

---

### Post by MAFoElffen on 2023-12-03
@1fallen --

Actually, I just sent you a PM asking if you would  want to review a tutorial for work-arounds for ZFS: Spefically needed  right now for unistalling zfs-dkms, and still survive. 

After  sending it, I got a better idea-- To publish it (them) in the Ubuntu  Wiki pages, so we can just refer people to them, instead of typing it  over and over again...

Either that, or maybe better, I could just put it on my GitHub, then we still have control over the edits and who does what to it.

EDIT: Ideas still rolling around in my head. That zfs-dkms bug is gaining momentum. Not by Launchpad staff, but unfortunately by other users that are affected by that bug!!! We both got clear of that. But other's do not have our skills to survive from what we did. You know, to get around the: "Do not do this at home. These individuals have Nomex underwear..." disclaimer.

---

### Post by #&amp;thj^% on 2023-12-03
Got the PM and I'm on board with the New Idea.....Go Team. ;)

---

### Post by MAFoElffen on 2023-12-03
I created the Repo with the draft: [https://github.com/Mafoelffen1/OpenZFS-Ubuntu-Admin/blob/main/README.md](https://github.com/Mafoelffen1/OpenZFS-Ubuntu-Admin/blob/main/README.md)

I can later add more of my ZFS Instructions for recovering ZFS from a LiveUSB and what to do if dumped to the intramfs & maintenance prompts... That should save us a lot of retyping for ZFS support issues later.

---

### Post by MAFoElffen on 2023-12-03
That doc is done, enough for reviews and further testing. I did try it out on a few test-cases.

Going to try it a few more different ways, to see if there is a way to not dump out to the root maintenance prompt.

It's still going to dump out to a maintenance prompt, but most of that is unneeded.

---

### Post by MAFoElffen on 2023-12-03
I got busy. 

RE: [https://github.com/Mafoelffen1/OpenZFS-Ubuntu-Admin/tree/main](https://github.com/Mafoelffen1/OpenZFS-Ubuntu-Admin/tree/main)

While in the mode, I created 5 ZFS support tutorials. I know I got tired and there is some spelling and such mistakes. I would appreciate some eyes to help me spot those.

---

### Post by MAFoElffen on 2023-12-04
My reported bug: [https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2044969](https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2044969)

Was now marked as a duplicate to this Bug: [https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2044657](https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2044657)

Please join that bug as "Also Affects Me"

---

### Post by #&amp;thj^% on 2023-12-05
Today's updates brought in:
```
libcairomm-1.16-1            1.16.2-7            1.18.0-1                       52 KB  
  libnvpair3linux              2.2.0-0ubuntu3      2.2.1-0ubuntu1                 61 KB  
  libuutil3linux               2.2.0-0ubuntu3      2.2.1-0ubuntu1                 52 KB  
  libxklavier16                5.4-4build2         5.4-5                          44 KB  
  libzfs4linux                 2.2.0-0ubuntu3      2.2.1-0ubuntu1                224 KB  
  libzpool5linux               2.2.0-0ubuntu3      2.2.1-0ubuntu1                1.4 MB  
  xdg-desktop-portal           1.18.0-1ubuntu1     1.18.2-1ubuntu1               299 KB  
  zfs-dkms                     2.2.0-0ubuntu3      2.2.1-0ubuntu1                2.4 MB  
  zfs-initramfs                2.2.0-0ubuntu3      2.2.1-0ubuntu1                 25 KB  
  zfs-zed                      2.2.0-0ubuntu3      2.2.1-0ubuntu1                 68 KB  
  zfsutils-linux               2.2.0-0ubuntu3      2.2.1-0ubuntu1                550 KB  
```
```
apt policy zfs-dkms   
zfs-dkms:
  Installed: 2.2.1-0ubuntu1
  Candidate: 2.2.1-0ubuntu1
  Version table:
 *** 2.2.1-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu noble/universe i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by MAFoElffen on 2023-12-05
For Mantic or Noble?

Jammy got nothing...

@1fallen... You got me thinking about going live, physically to Noble on the ThinkPad.... Just do not know if I want to risk all these scripts and code only residing on this laptop. I could always back those up before I do.

---

### Post by #&amp;thj^% on 2023-12-05
> **MAFoElffen said:**
> For Mantic or Noble?

Jammy got nothing...

@1fallen... You got me thinking about going live, physically to Noble on the ThinkPad.... Just do not know if I want to risk all these scripts and code only residing on this laptop. I could always back those up before I do.

It's been pretty reliable so far for me, outside the current zfs-dkms drama. I push it kind of hard in regards to drivers and such....I'm pretty happy with it currently.
Note to other readers, as you see all is good, until it's not, testing is and will always be "User Beware"

---

### Post by MAFoElffen on 2023-12-06
RE: [https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2044657](https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2044657)

The  bug has been assigned, priorities, and fixes are forthcoming very soon for all. Will  hit Mantic first. Mantic just got the commit about a minute ago. 

Then to Noble, Lunar & Jammy.... Then further mention of other backports after that is done.
```

"Multiple data corruption issues in zfs"

Affects            Status           Importance         Assigned to     Milestone
&#8203;zfs-linux (Ubuntu) Status tracked in Noble
Xenial             Confirmed        Low                Unassigned
Bionic             Confirmed        Medium           &#8201; Unassigned
Focal              Confirmed        Medium             Unassigned
Jammy              Confirmed        High               Dimitri John Ledkov
Lunar              Confirmed        Medium             Dimitri John Ledkov
Mantic             In Progress      High             &#8201; Dimitri John Ledkov
Noble              Fix Committed    Undecided          Dimitri John Ledkov

```
It's moving fast now!!!
```

mafoelffen@noble-d05:~$ apt list -a zfsutils-linux
Listing... Done
zfsutils-linux/noble-proposed 2.2.2-0ubuntu1 amd64
zfsutils-linux/noble,now 2.2.1-0ubuntu1 amd64 [installed]

```
I see zfs-linux 2.2.2 was built at launchpad 11 hours ago, and that zfsutils-linux-2.2.2-0ubuntu1 is in Noble proposed now

---

### Post by MAFoElffen on 2023-12-06
With Noble Proposed enabled, do:
```

sudo apt install -y zfsutils-linux=2.2.2-0ubuntu1 libnvpair3linux=2.2.2-0ubuntu1 libuutil3linux=2.2.2-0ubuntu1 libzfs4linux=2.2.2-0ubuntu1 libzpool5linux=2.2.2-0ubuntu1
sudo apt install -y zfs-zed=2.2.2-0ubuntu1 zfs-initramfs=2.2.2-0ubuntu1

```
Then turn off Proposed...

Now testing:
```

mafoelffen@noble-d05:~$ uname -r
6.5.0-9-generic
mafoelffen@noble-d05:~$ lsb_release -d
No LSB modules are available.
Description:    Ubuntu Noble Numbat (development branch)
mafoelffen@noble-d05:~$ apt list zfsutils-linux --installed
Listing... Done
zfsutils-linux/noble-proposed,now 2.2.2-0ubuntu1 amd64 [installed]
N: There is 1 additional version. Please use the '-a' switch to see it

```

---

### Post by #&amp;thj^% on 2023-12-06
> **MAFoElffen said:**
> With Noble Proposed enabled, do:
```

sudo apt install -y zfsutils-linux=2.2.2-0ubuntu1 libnvpair3linux=2.2.2-0ubuntu1 libuutil3linux=2.2.2-0ubuntu1 libzfs4linux=2.2.2-0ubuntu1 libzpool5linux=2.2.2-0ubuntu1
sudo apt install -y zfs-zed=2.2.2-0ubuntu1 zfs-initramfs=2.2.2-0ubuntu1

```
Then turn off Proposed...

Now testing:
```

mafoelffen@noble-d05:~$ uname -r
6.5.0-9-generic
mafoelffen@noble-d05:~$ lsb_release -d
No LSB modules are available.
Description:    Ubuntu Noble Numbat (development branch)
mafoelffen@noble-d05:~$ apt list zfsutils-linux --installed
Listing... Done
zfsutils-linux/noble-proposed,now 2.2.2-0ubuntu1 amd64 [installed]
N: There is 1 additional version. Please use the '-a' switch to see it

```

Dang you beat me to it :P
```
apt list zfsutils-linux --installed
Listing... Done
zfsutils-linux/noble-proposed,now 2.2.2-0ubuntu1 amd64 [installed]
N: There is 1 additional version. Please use the '-a' switch to see it

```
And I was able to shed zfs-dkms
```
apt policy  zfs-dkms
zfs-dkms:
  Installed: (none)
  Candidate: 2.2.1-0ubuntu1
  Version table:
     2.2.2-0ubuntu1 100
        100 http://us.archive.ubuntu.com/ubuntu noble-proposed/universe amd64 Packages
        100 http://us.archive.ubuntu.com/ubuntu noble-proposed/universe i386 Packages
     2.2.1-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu noble/universe i386 Packages
        100 /var/lib/dpkg/status

```
I'm running with proposed a little longer.......NOTE Not advised.

---

### Post by MAFoElffen on 2023-12-06
LOL. When i uninstalled 'zfs-dkms' this morning from my Noble test-case before installing the zfs-linux 2.2.2 packages, I got hit where I had to import bpool on the boot to go on.

'zfs-dkms' has got some very deep roots into 'something' there!

---

### Post by #&amp;thj^% on 2023-12-06
> **MAFoElffen said:**
> 
'zfs-dkms' has got some very deep roots into 'something' there!
Indeed with likes of, data checksums, compression, encryption, snapshots, and more.

---

### Post by #&amp;thj^% on 2023-12-07
EDIT: This is on Noble no jammy here to test on. Update from yesterday, All the new zfs related from yesterday broke my boot, couldn't even find my bpool.
Differences with mine I ran "zfs-dkms" and was very stable on that.
Not able to solve it, I imported my rpool to another drive, re-installed imported rpool back to my install, I never enabled proposed this time, and have "zfs-dkms 2.2.1" I'll just wait for the natural progression to come in.
Just a heads up....

---

### Post by MAFoElffen on 2023-12-07
Look at this tidbit:
```

mafoelffen@noble-d05:~$ apt-cache show zfsutils-linux
Package: zfsutils-linux
Architecture: amd64
Version: 2.2.2-0ubuntu1
Priority: extra
Section: admin
Source: zfs-linux
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian ZFS on Linux maintainers <pkg-zfsonlinux-devel@alioth-lists.debian.net>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 1760
Provides: zfsutils
Pre-Depends: init-system-helpers (>= 1.54~)
Depends: libnvpair3linux (= 2.2.2-0ubuntu1), libuutil3linux (= 2.2.2-0ubuntu1), libzfs4linux (= 2.2.2-0ubuntu1), libzpool5linux (= 2.2.2-0ubuntu1), python3, libblkid1 (>= 2.16), libc6 (>= 2.38), libssl3 (>= 3.0.0), libudev1 (>= 183), libuuid1 (>= 2.16)
Recommends: zfs-zed
Suggests: nfs-kernel-server, samba-common-bin (>= 3.0.23), zfs-initramfs | zfs-dracut
Conflicts: zfs, zfs-fuse
[COLOR=#ff0000]Breaks:[/COLOR] openrc, spl (<< 0.7.9-2), spl-dkms (<< 0.8.0~rc1), [COLOR=#ff0000]zfs-dkms (>> 2.2.2-0ubuntu1...), zfs-dkms (<< 2.2.2-0ubuntu1)[/COLOR]
Replaces: spl (<< 0.7.9-2), spl-dkms
Filename: pool/main/z/zfs-linux/zfsutils-linux_2.2.2-0ubuntu1_amd64.deb
Size: 550502
MD5sum: 81b0baf1721d54afeb96a9f2abc8ba09
SHA1: 54534a481c6e0fa0856dcea8c544d8fee0d549e0
SHA256: 18e494137f45f01cfdd67d1b1781e5743b2499fd8e0fdea9aab9123f58eb53df
SHA512: a88f1d630df482bebabc6a35f594b24f4ea35de1b016238c52540f172735b9edbf72c4a1123db06cfcdc1d2f5f1145d7122507012975339d94190e89b94ba476
Homepage: https://zfsonlinux.org/
Description-en: command-line tools to manage OpenZFS filesystems
 OpenZFS is a storage platform that encompasses the functionality of
 traditional filesystems and volume managers. It supports data checksums,
 compression, encryption, snapshots, and more.
 .
 This package provides the zfs and zpool commands to create and administer
 OpenZFS filesystems.
Description-md5: e0d1624ff402201471b9a32e9cb71f16
Task: ubuntu-live, xubuntu-live, ubuntukylin-live, ubuntu-mate-live, ubuntu-budgie-live, ubuntucinnamon-live

```

---

### Post by MAFoElffen on 2023-12-08
I asked last night, in the combined bug grouping, if we should file a new bug against zfs-dkms, because of what I found in 2.2.2 for zfsutuils-linux versus zfs-dkms.

@ 1fallen -- I keep mentioning (there) that 2.2.2 blew you out against any access to your pools, and that you had to revert back to 2.2.1 (plus zfs-dkms). They really need to know what happened there, so they can check that out and get things corrected. If they do not know, how are they going to be able to fix that? Right?

---

### Post by #&amp;thj^% on 2023-12-08
> **MAFoElffen said:**
> I asked last night, in the combined bug grouping, if we should file a new bug against zfs-dkms, because of what I found in 2.2.2 for zfsutuils-linux versus zfs-dkms.

@ 1fallen -- I keep mentioning (there) that 2.2.2 blew you out against any access to your pools, and that you had to revert back to 2.2.1 (plus zfs-dkms). They really need to know what happened there, so they can check that out and get things corrected. If they do not know, how are they going to be able to fix that? Right?

Not quite, This broke "my" bpool:
```
zfsutils-linux=2.2.2-0ubuntu1 libnvpair3linux=2.2.2-0ubuntu1 libuutil3linux=2.2.2-0ubuntu1 libzfs4linux=2.2.2-0ubuntu1 libzpool5linux=2.2.2-0ubuntu1
```
and today...knock on wood this is stable on my end:
```
apt policy zfs-dkms
zfs-dkms:
  Installed: 2.2.2-0ubuntu1
  Candidate: 2.2.2-0ubuntu1
  Version table:
 *** 2.2.2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu noble/universe i38
```
EDIT: Ok this has been running for a few hours now, with 2 reboots and I'm now taking it offline for a cold bootup.
it will powerdown for around an hour for a good "Cold Boot" that seems to be the gremlin on my end.

---

### Post by #&amp;thj^% on 2023-12-08
Happy to report, both Intel and AMD machines both survived a Cold Boot
Information on today's upgrades:
```
The following packages will be upgraded:
  cracklib-runtime distro-info-data firmware-sof-signed fonts-opensymbol fwupd gimp
  gimp-data gir1.2-libosinfo-1.0 gir1.2-libvirt-glib-1.0 gjs grub-common grub-pc
  grub-pc-bin grub2-common isc-dhcp-client isc-dhcp-common libadwaita-1-0 libass9
  libauthen-sasl-perl libbpf1 libcairomm-1.0-1v5 libcrack2 libdbusmenu-glib4
  libdbusmenu-gtk3-4 libdecor-0-0 libdecor-0-plugin-1-gtk libffi-dev libffi8
  libffi8:i386 libfido2-1 libfwupd2 libgeotiff5 libgimp2.0 libgjs0g libimath-3-1-29
  libimath-dev libmysofa1 libnvpair3linux libosinfo-1.0-0 libosinfo-l10n libproj25
  libpython3.12-minimal libpython3.12-stdlib libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk3 libreoffice-help-common libreoffice-help-en-us libreoffice-impress
  libreoffice-math libreoffice-style-colibre libreoffice-style-elementary
  libreoffice-style-yaru libreoffice-uiconfig-calc libreoffice-uiconfig-common
  libreoffice-uiconfig-draw libreoffice-uiconfig-impress libreoffice-uiconfig-math
  libreoffice-uiconfig-writer libreoffice-writer libudisks2-0 libuno-cppu3
  libuno-cppuhelpergcc3-3 libuno-purpenvhelpergcc3-3 libuno-sal3 libuno-salhelpergcc3-3
  libuutil3linux libv4l-0 libv4lconvert0 libvirt-glib-1.0-0 libvirt-glib-1.0-data
  libzfs4linux libzpool5linux mawk osinfo-db proj-bin proj-data python3-gssapi
  python3-libvirt python3-uno python3-update-manager python3-zeroconf python3.12
  python3.12-minimal sbsigntool seabios systemd-hwe-hwdb ubuntu-keyring udisks2
  uno-libs-private update-manager update-manager-core ure usb.ids zfs-dkms
  zfs-initramfs zfs-zed zfsutils-linux
102 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 189 MB of archives.
After this operation, 64.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```
Back in the saddle again Wee Dogies.

---

### Post by MAFoElffen on 2023-12-09
I'm wondering if what it says in apt-cache show as zfsutils-linux breaking zfs-dkms is just wrong output. Because it seems to be working for you right? With those two being installed ad coexisting together???

---

### Post by MAFoElffen on 2023-12-10
All my machines are all now out from under zfs-dkms'es grip. The easiest was my new workstation. I think because if was crashing because of intel-i915-dkms, maybe zfs-dkms could completely get it's tentacles as deep into it.

After I got it removed and rebooted, that machine just booted up normally. That one never dumped any of it's pools at all. I decided to remove intel-i915-dkms. The Intel Graphics Support Team? I have lost faith in them. They have not contacted me at all since they changed personnel on that support case. I don't know what that means for Noble with that.

---

### Post by #&amp;thj^% on 2023-12-10
> **MAFoElffen said:**
> I'm wondering if what it says in apt-cache show as zfsutils-linux breaking zfs-dkms is just wrong output. Because it seems to be working for you right? With those two being installed ad coexisting together???

It was working just fine, but not wanting to push that luck button too many times, I too got rid of it.
You seen already In my last PM...;)
```
apt policy zfsutils-linux zfs-dkms
zfsutils-linux:
  Installed: 2.2.2-0ubuntu1
  Candidate: 2.2.2-0ubuntu1
  Version table:
 *** 2.2.2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
zfs-dkms:
  Installed: (none)
  Candidate: 2.2.2-0ubuntu1
  Version table:
     2.2.2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu noble/universe i386 Packages

```
I had a super long shutdown with zfs.zed.service.
From here all I can do now is push forward..

---

