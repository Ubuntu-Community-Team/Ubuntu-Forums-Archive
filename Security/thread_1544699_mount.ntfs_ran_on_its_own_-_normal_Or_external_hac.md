---
title: "mount.ntfs ran on its own - normal? Or external hack/break-in attempt?"
date: 2010-08-02
forum: Security
---

### Post by arjaydavis on 2010-08-02
Running Ubuntu 10.04 I noticed my hard disc rumbling for longer than normal and louder. Not doing anything demanding to cause hard disk activity like this so I was suspicious so I checked my process list with 'top' command in the console terminal.

At the top was mount.ntfs running. Eventually it stopped running after 20 seconds or so. At the time I have not been accessing NTFS filesystems, but I do have them.

I have a dual boot Ubuntu 10.04 and Windows 7. In Ubuntu I've mounted the Windows main C drive and on the same hard disk a partitioned drive for sharing files between the OSs.

I know mount.ntfs is a standard program but was it being run on my machine, instigated externally here?

Was the running of mount.ntfs an attempt from outside to hack into Ubuntu and the mounted Windows areas of my machine via a backdoor connection or vulnerability? 

I've restarted my machine since then.

Are there any logs I can check for malicious attempts to break in?

Thanks for your time, I hope to be a contributor here over time.

---

### Post by OpSecShellshock on 2010-08-03
Is it possible that there was a file indexing process running? That'll cause a disk to spin up a lot while it's working (usually during idle time).

---

### Post by arjaydavis on 2010-08-03
> **OpSecShellshock said:**
> Is it possible that there was a file indexing process running? That'll cause a disk to spin up a lot while it's working (usually during idle time).


good point. i hope it is that. i'll look at the settings and the logs generated - hopefully entries will be around the time i noticed that activity - then i can draw a more certain conclusion.

indexing is enabled by default, here's where to find the settings to enable/disable:
[http://en.kioskea.net/faq/2315-disabling-indexing-files-in-ubuntu](http://en.kioskea.net/faq/2315-disabling-indexing-files-in-ubuntu)

---

### Post by FuturePilot on 2010-08-03
> **arjaydavis said:**
> indexing is enabled by default, here's where to find the settings to enable/disable:
[http://en.kioskea.net/faq/2315-disabling-indexing-files-in-ubuntu](http://en.kioskea.net/faq/2315-disabling-indexing-files-in-ubuntu)

Tracker was removed from the default install a long time ago. There is no indexing by default.

---

### Post by arjaydavis on 2010-08-03
> **FuturePilot said:**
> Tracker was removed from the default install a long time ago. There is no indexing by default.

Any ideas then about original post?

Cheers!

---

### Post by cariboo on 2010-08-04
Just to make sure, you don't have your ntfs partition set to auto-mount in /etc/fstab do you?

---

### Post by p_code on 2010-08-06
Correct me if I am mistaken here, but my Ubuntu 10.04 live CD mounted my XP C:\ partition 777 R/W - BY DEFAULT and made it available to be pissed all over by nix-script-kiddies without even requiring a root login.

When I saw this I decided that the Ubuntu team knew NOTHING about security since any idiot can see that this mount alone makes it trivially easy for a malicious process to gain administration level privileges on both Windows AND Linux.

I can think of at least a half dozen ways this can be done without requiring the user to be dumb enough to grant root privileges.

 - here's one of the easiest . . .

1.  Take advantage of [THIS STUPID GNOME DEFECT]("http://ubuntuforums.org/showpost.php?p=9680466&postcount=73") to make your malicious script look EXACTLY like a collection of harmless  PDF or TXT Documents files.  (nothing suspicious in  Gzipping docs to save bandwidth on the web right?).

2.  When the unsuspecting user downloads, unzipps, and double clicks the README.FIRST doc file' (to automatically open it in their document viewer), the file which is actually a malicious script or binary launches and immediately backgrounds itself and erases any evidence while forking a convincing coverup doc from part of one of the other files to the proper document viewer. (so the unsuspecting user doesn't even know that anything is going on).

3.  In the background, the 'harmless doc file' script or binary opens WGET and downloads a nasty windows Trojan and hacked Linux Kernel (which of course is super easy thanks to total lack of web security in Ubuntu on ALL outgoing Internet connections).

4.  The next time the unsuspecting user boots MS Windows, the now totally P'WNED Microsoft Windows Kernel returns the favor and replaces vmlinuz with a hacked version which contains a nice totally undetectable kernel level rootkit.

Before some well meaning Linux Fan Boy suggests that this is just too unbelievable complicated to be a realistic attack, you might want to consider the fact that it's actually much LESS complicated than some of the tricks pulled by already known modern polymorphic viruses and trojans in Windows.

The key is that Ubuntu carelessly opens up one OS's privileged file structure to non-privileged access by users in the other OS, and thus creates a hole a mile wide that malware can crawl through, to ultimately infect BOTH systems, without even starting out with root privileges.

The 3rd generation NTFS drivers do support some cross mapping of privilege levels between MS and Linux, but apparently no one wanted to take the trouble to set it up properly, and so they just 777 your whole C: drive and turn it over to anyone who wants to hack it from Linux land. 

Stupid - really, really, Stupid.

Fortunately if you just have to have Ubuntu, but don't like the idea that it can trash your C:\ drive, there is a reasonably secure alternative.   Ubuntu runs GREAT, in a Oracle VirtualBox jail environment under Windows  XP, 7, or Vista, and if it gets trashed for any reason, by malware because you click a 'harmless doc file' for example (or if you just accidentally rm -rf something you shouldn't have), you can just restore the VirtualBox Virtual Linux VDI hard disk file from a backup very quickly. 

If your lucky and can run VirtualBox with AMD or Intel Hardware VM support and 3D pass-through enabled, you should find that both Compiz and Multimedia playback work nicely on modern hardware even when running inside the VM, so I would go that route rather that go with a "dual boot" setup.

To be perfectly frank, given some of the really dumb, totally silly, and generally CLUELESS, comments I have read in this Ubuntu security forum, I won't let Ubuntu near my C: drive in a dual boot setup, but VirtualBox provides a nice added second layer of protection, and let's you enjoy the best of both worlds without the risk.

---

### Post by FuturePilot on 2010-08-06
The live CD is different than an install in that the live CD lets you use sudo without prompting for a password. You may have been able to mount your Windows partition without a password from the live CD but that's not how it works on an install. At least without modifying fstab.

---

### Post by p_code on 2010-08-06
> **FuturePilot said:**
> The live CD is different than an install in that the live CD lets you use sudo without prompting for a password. You may have been able to mount your Windows partition without a password from the live CD but that's not how it works on an install. At least without modifying fstab.

No, I'm sorry, I thought I made it clear . . .

I did not do ANY MOUNT OPERATION WHATSOEVER!

So, on the live CD, I can confirm that Ubuntu just grabs your C:\ partition and MOUNTS IT 777 R/W 'OWNED' BY THE 'GUEST' USER BY DEFAULT!!!  (I tested this by writing some files to C:\)

To be honest, after seeing what the LIVE CD was doing, I didn't have any desire to check out the 'Full Install' option without the protection of a VM environment, but from what others are reporting, it sounds like Ubuntu 10.04 will also happily automount your C:\ partition 777 R/W after a full install (I'm not sure if this happens after you click in Nautilus or at boot up???).

In any case, since these newby 'live cd' guest users are potentially the least  experienced, and therefore MOST likely to fall for some stupid web site telling them something like "To keep your MS Windows C:\ drive safe from Ubuntu, be sure to do a rm -rf (or mv to dev/nul, or any of 50 other less obvious things) on their Windows C:\ mount point.

This is REALLY REALLY REALLY BAD! [-X

Sounds, like it's time for Ubuntu 10.05  :oops:

BTW after discovering the above, I thought it might be a good idea to report this to the Ubuntu desktop 'Security Team' leader, only to discover that although Ubuntu has a Myth TV team (got to have TIVO on Ubuntu), a "I :heart: Ubuntu" team (hey, maybe they have free tee-shirts!) , and even a Womens outreach team (got to make sure we don't have Non-PC PC's) we apparently do not have a dedicated 'Security Team' to look after desktop users.   

There is a team to work on more secure Ubuntu *servers* (probably a good idea based on what I've seen so far), but not a dedicated team for desktop user security.  SAD, really, really, SAD :cry:

---

### Post by FuturePilot on 2010-08-06
I have never seen the live CD mount any Windows partition on its own. If it's doing that for you then it may be a bug but it is certainly not a feature.

---

### Post by cariboo on 2010-08-06
Please quit being so dramatic, the **Live CD** does mount windows partitions automagically, as well as any other partitons it finds. 

Most of what you have written has been covered many times before. I would suggest you don't base your opinion on the Live Cd, either install ubuntu on a test machine, or install it in a VM.

I would also suggest you check out all the [security resources]("https://help.ubuntu.com/search.html?cof=FORID:9&cx=004599128559784038176:vj_p0xo-nng&ie=UTF-8&q=security&sa=Search") available in the Ubuntu help wiki. Out of the box, an Ubuntu install is just as secure as any of the many Linux distro's.

---

### Post by p_code on 2010-08-06
> **FuturePilot said:**
> I have never seen the live CD mount any Windows partition on its own. If it's doing that for you then it may be a bug but it is certainly not a feature.

Try opening Nautilus and looking, it may be the action of opening the file browser that automounts the partition.  If so, it must mount right when Nautilus opens, because it was the fact that the right hand pane in Nautilus was displaying my C:\ volume name that alerted me in the first place.

In any case, I can confirm that if you startup the standard Install/Live CD and select the 'Tryout Umbuntu' trial session, then Nautilus definitely has R/W access to the Windows C:\ partition without an explicit mount command or fstab change.

---

### Post by FuturePilot on 2010-08-06
> **p_code said:**
> because it was the fact that the right hand pane in Nautilus was displaying my C:\ volume name that alerted me in the first place.


Are you sure it's actually mounted? It will list all drives and partitions but it doesn't mount anything. Running
```
mount
```
will show you everything that is currently mounted.

---

### Post by OpSecShellshock on 2010-08-06
I don't think I've ever seen anyone mention this before, which I think would have come up if it were actually mounting the drives on its own with those permissions. Honestly though, people boot their C: drives in Windows every day while connected to the internet, leaving them for all practical purposes in the same wide open state with no option to set it otherwise if they actually want to be able to use a web-aware application, so even if that's what's really happening then the functional risk level has made, at most, a lateral move.

---

### Post by p_code on 2010-08-06
> **OpSecShellshock said:**
> I don't think I've ever seen anyone mention this before . . . 

Welcome to the new millennium, with a generation of 6 billion plus USERS who USE, USE, USE (while happily assuming that someone else is minding the store) and about 12 people who actually CREATE (and DO mind the store).

Ok, that's a little harsh and just a bit of an exaggeration, but a decade ago when the web was first hitting it's prime, I was constantly amazed at the obscure areas of human endeavor that you could find information about on the web.   If you could dream it up, someone else had already spent days, months, or even YEARS figuring it all out and publishing their results.

These days, time, and time, and time again, I have just the opposite experience, i.e. "I can't believe that NO ONE ON THE PLANET has noticed this problem and done anything about it."

As to your point about Windows boxes running with the C:\ drive mounted, I appreciate the fact that you didn't go too far over the top with silly Linux Fanboy anti Microsoft rants about how "'Windowz is totaly inseekewr", because that saves me the trouble of pointing out that dating all the way back to XP, Windows has been locked down about as well as Linux when it comes to permissions (in fact in absolute fairness, Windows has a more sophisticated system with even more permission options than Linux)

The trouble in most cases is simple -

1. Most people in MS Win environments run as root (admin)
2. Because, most people are stupid (at least when it comes to computers)
[COLOR=Red]
[/COLOR][COLOR=Red]Getting back to the more immediate topic at hand . . .[/COLOR]

[COLOR=Red]* Yes, Ubuntu _DOES_ mount the Windows system partition with no protections.[/COLOR]
[B]
[COLOR=Red]* Yes, this IS A PROBLEM.[/COLOR][/B]

How would you like it if Windows 7 mounted the Linux Boot partition with full R/W access to 'everyone' then bypassed it's normal firewall protections to specifically let windows user scripts open random web connections to anywhere on the planet and **** all over 'vmlinuz' (but NOT of course on any of it's own system files) ?

Would that be OK?

---

### Post by OpSecShellshock on 2010-08-06
Well, if it's true then maybe a bug report is the way to go. Anyone with Windows installed should be able to reproduce the issue without any trouble (assuming it's the same image on the live CD).

Of course, the next thing to consider is whether such a situation can be exploited remotely. If not, then it's probably best to put this under the scope of the basic risks that come with physical access. It's certainly worth testing, both with and without a hardware firewall in the middle. Then, of course, all the suggestions about the use of the live CD for conducting sensitive tasks need to stop (it shouldn't have been suggested in the first place, but actively creating additional risk probably changes the urgency a bit).

---

### Post by FuturePilot on 2010-08-06
If you could please, boot the live CD, don't do anything else but open a terminal and run
```
mount
```
and post the output here.

---

### Post by p_code on 2010-08-06
> **FuturePilot said:**
> If you could please, boot the live CD, don't do anything else but open a terminal and run
```
mount
```and post the output here.

I did this test, and the culprit seems to be the GNOME environment automounter

Prior to opening Nautilus, and selecting my C:\ drive there is no mount showing up. (though it does show as available with the volume name being listed, so the automounter has accessed it, just not mounted it)

After opening the drive folder in Nautilus, the mount command does show a "default_priviliges" mount to /dev/sda2 [my C:\ partition] with the mount owner 'ubuntu' having FULL ACCESS RIGHTS [R/W everything]

who am i   ->  shows that the guest user is 'ubuntu'  so a script running after the above mount takes place can delete your entire C:\ partition - no problem.

The mount seems to be persistent, and could still be accessed after several minutes of no activity, so I'm not sure if there is a timeout.

Since someone already pointed out that the Live CD's 'Try Ubuntu' option lets it's default user 'ubuntu' do pretty much ANYTHING without having to answer to a 'root' privilege prompt, the fact that the Windows C: file system is not initially mounted is probably not much help (because in this environment, a malicious script could just mount it for you).

I guess the 'Team Ubuntu' team leader figured that since Vista had this really bad rap for  bugging you with security prompts every five minutes, they would try to win over stupid gen-z users with ultra short attention spans by showing that Ubuntu wouldn't bug you with ANY of that 'dumb seekwurity  stuff' like Vista.

Can't say it impresses me much though . . .

---

### Post by FuturePilot on 2010-08-07
> Prior to opening Nautilus, **and selecting my C:\ drive** there is no mount showing up.
Which proves my point that simply booting the live CD does not mount anything because

> After opening the drive folder in Nautilus, the mount command does show a "default_priviliges" mount to /dev/sda2 [my C:\ partition] with the mount owner 'ubuntu' having FULL ACCESS RIGHTS [R/W everything]
when **you** open the drive **you** are mounting it. Nothing is automatically doing it.

> The mount seems to be persistent, and could still be accessed after several minutes of no activity, so I'm not sure if there is a timeout.
Mounts do not time out.

---

### Post by p_code on 2010-08-07
> **FuturePilot said:**
> Which proves my point that simply booting the live CD does not mount anything because . . .


when **you** open the drive **you** are mounting it. Nothing is automatically doing it.


Mounts do not time out.

I went out of my way to accommodate you and run the console level tests you requested, because I thougt you were interested in a real conversation about this, not some silly "U see Linux is jus perfec aferawll" slap-down.

So let's try to put this back on a technical level  . . .

1. Something in the 'Try Umbuntu' environment  is indeed automatically mounting my C:\ partition R/W with ZERO protections, just as I originally stated.  In this case _Nautilus_ is mounting it transparently as soon as the user clicks on the folder (which anyone is likely to do when they see that it is showing up  already displayed in Nautilus).  This is happening because of the way _Ubuntu_ is configured, not because I explicitly gave permission to 'mount' anything.

2. More importantly, you completely ignored my last point ->  that because of the total lack of proper security in the Live CD's 'Try Ubuntu' environment, it _doesn't matter_ whether the Win C:\ partition gets mounted automatically, because a malicious script using the default 'ubuntu' account_ can mount it for you_.

3. Lastly, If you are going to correct someone on minor technical points, perhaps you should configure a few systems yourself and try to learn a little about your subject before you make silly statements like 'mounts do not time out'.  This only applies to static mounts in fstab or made with the standard mount command.  Since what we are looking at here is more of a transparent 'automount' type situation, it's quite reasonable to speculate about a possible timeout, since such timeouts _ARE_ a standard feature of the built in autofs automount  in Linux (duhhh).

---

### Post by OpSecShellshock on 2010-08-07
Still though, how is a malicious script going to get onto the live CD in the first place? If it doesn't, then where is it going to run from during a live CD session?

---

### Post by FuturePilot on 2010-08-07
> **p_code said:**
> I went out of my way to accommodate you and run the console level tests you requested, because I thougt you were interested in a real conversation about this, not some silly "U see Linux is jus perfec aferawll" slap-down.

So let's try to put this back on a technical level  . . .

1. Something in the 'Try Umbuntu' environment  is indeed automatically mounting my C:\ partition R/W with ZERO protections, just as I originally stated.  In this case _Nautilus_ is mounting it transparently as soon as the user clicks on the folder (which anyone is likely to do when they see that it is showing up  already displayed in Nautilus).  This is happening because of the way _Ubuntu_ is configured, not because I explicitly gave permission to 'mount' anything
I have never said, and I never will say, that Linux is perfect. No OS is perfect. The point is Ubuntu automatically mounting the Windows partition is not accurate. When you double click on the drive it gets mounted. That is the way Nautilus works. It's like that with any live CD environment.

> 2. More importantly, you completely ignored my last point ->  that because of the total lack of proper security in the 'Try Ubuntu' environment, it _doesn't matter_ whether the Win C:\ partition gets mounted automatically, because a malicious script using the default 'ubuntu' account_ can mount it for you_.
This goes for any OS. Don't download and/or run untrusted code.

> 3. Lastly, If you are going to correct someone on minor technical points, perhaps you should configure a few systems yourself and try to learn a little about your subject before you make silly statements like 'mounts do not time out'.  This only applies to static mounts in fstab or made with the standard mount command.  Since what we are looking at here is more of a transparent 'automount' type situation, it's quite reasonable to speculate about a possible timeout, since such timeouts _ARE_ a standard feature of the built in autofs automount  in Linux (duhhh).
I have configured many, many desktop and server systems. Yes the thought did cross my mind that network file systems can time out but in the case of NFS for example it's not really a time out if it was hard mounted. Instead it will just wait for the server to respond again. But network file systems are a whole different topic which is why I didn't mention it. Back on topic. Time outs may be a standard feature in autofs but Ubuntu does not use autofs to mount things. It is not an automount if you initiate it. When you click on the partition in Nautilus it means you have every intention to view what is on there.

---

### Post by tubezninja on 2010-08-07
I'm just curious here.... but, how is this any different from how Windows mounts the C drive?  You boot into Windows, you get a C drive and can manipulate files.  Even if password protected, it's possible to take the drive, boot into another install of windows wehre one has admin rights and take ownership of the drive.

---

### Post by p_code on 2010-08-08
> **scaredpoet said:**
> I'm just curious here.... but, how is this any different from how Windows mounts the C drive?  You boot into Windows, you get a C drive and can manipulate files.  Even if password protected, it's possible to take the drive, boot into another install of windows wehre one has admin rights and take ownership of the drive.

Lots of differences.

When you are running inside Windows, the system is locked down with a full set of file system permissions, plus selinux style Kernel level locks on some critical files, that won't let you mess with them even as root (admin)

Also contrary to your comment, unlike Linux, Windows can be configured so that root on one machine is NOT able to screw with another installations file system, because there are unique cryptographic tokens that can be used to prevent this.

Sure, it's true that if you boot into a recovery environment, you can screw with or even reformat the file system in both Windows and Linux, but the key point here is THAT'S NOT WHAT THE USER IS SIGNING UP FOR.

What they think that they are signing up for is to take the 'Ubuntu' system for a harmless test drive.

So, I'm guessing they will be a little put out, if they end up WITH THEIR C:\ WINDOWS PARTITION DELETED.

As to the question of how a malicious file would get onto their system, via the web of course, which is fully enabled on the live CD.

That's not even necessary.  In reality to create a world of trouble, all that would have to happen is an exchange like this in any of a thousand or more 'support forums'  . . .

[COLOR=Blue]Newby-

"Hey, I really like this Ubootooo stuff, but I am not ready to install it yet, and the Live CD thingy is a pain, because it forgets everything on every re-boot.   So I was worder'n if there is a way to make it remember my settings and stuff, without going the full install route???[/COLOR]
[COLOR=Magenta]
[/COLOR][COLOR=Magenta]BADGUY-

Sure, no prob, Ubuntu can use a little space on your C:\ Drive for that.   

You just have to enable it by telling Ubuntu to (rm)ember your settings on C:\

Open a  console window inside Ubuntu like this ... then tell it to (rm)ber your settings like this . . .

rm -rf  [the guys C:\ partition mount point]
[/COLOR][B][SIZE=2][COLOR=Red]
Obviously this will really (rm)ove the guys entire C:\ partition destroying Windows. 
[/COLOR]
[/SIZE][/B]

---

### Post by cariboo on 2010-08-08
You talk as if this is a very common occurence, I've been a member here for four years, and haven't seen or heard of this happening. Yes it could happen, but it is a very rare ocurrence. You'd think with over 12 million unique installs, it would have happened to someone by now, and they would have made a lot of noise about it.

This sounds more like something a couple of kids would do to each other, than a real life situation.

---

### Post by JBAlaska on 2010-08-08
Please don't feed the windoze troll :P

---

### Post by tubezninja on 2010-08-08
> **p_code said:**
> Lots of differences.

When you are running inside Windows, the system is locked down with a full set of file system permissions, plus selinux style Kernel level locks on some critical files, that won't let you mess with them even as root (admin)

That's not been my experience, but all right, let's let that slide for a minute...


> Also contrary to your comment, unlike Linux, Windows can be configured so that root on one machine is NOT able to screw with another installations file system, because there are unique cryptographic tokens that can be used to prevent this.

Actually, I was asking a question, not arguing.  But let's let that one slide too...

So what you're saying is, somehow... linux, ubuntu in particular, has some magical ability to get past these cryptographic keys and allow anyone to fiddle with what is supposed to be a protected file system?

If that's the case, then I would be inclined to raise the alarm with Microsoft.  It doesn't seem very secure to me if the easy way around is just boot into linux, unless I'm misunderstanding you here.



> Sure, it's true that if you boot into a recovery environment, you can screw with or even reformat the file system in both Windows and Linux, but the key point here is THAT'S NOT WHAT THE USER IS SIGNING UP FOR.

But that isn't what they're automatically going to get either.  The ubuntu Live CD doesn't automatically start ripping things out of the Windows systems directories. It just gives you access to the drive.  The assumption made... which by the way, is the SAME assumption that Microsoft makes... is that a person booting into linux has sufficient knowledge of what they're doing.

You're also glossing over the fact that all of these **OMG HORRIBLE** scenarios you're discussing requires one thing to get it all started: physical access to the computer, to put the CD in and boot it.


> What they think that they are signing up for is to take the 'Ubuntu' system for a harmless test drive.

Is that not what they're getting?  No malicious code is included with the CD.  There's no malware there waiting in the wings, ready to attack.

You are basing your assumption on there being a 100% chance that the machine is going to be taken over by a hacker the moment someone does a live session of ubuntu, and that's just not the case.

> So, I'm guessing they will be a little put out, if they end up WITH THEIR C:\ WINDOWS PARTITION DELETED.

Right, because the FIRST thing I do when I boot into linux is gksudo a gparted session and start formatting away. :rolleyes:

> As to the question of how a malicious file would get onto their system, via the web of course, which is fully enabled on the live CD.

Which is the same vector that any windows user, any mac user, or any native linux installation has to contend with.  This is different... how?


I was gonna quote that obnoxiously-formatted scenario you described, but it's, well, obnoxiously formatted.  So I'm just going to say this: there is the unfortunately potential for a troll to provide malicious information in these or any other support forums.  Nothing that you describe is a problem specific to ubuntu.  

In ALL such cases the first line of defense is the user, who must be cautious and know what they are doing, and verify that they any advice they get is legitimate.  And the second line of defense are the moderators who find and delete such posts and take action as appropriate.

The bottom line here is, you are making a mountain out of a molehill.  I really haven't seen any other platform do things much differently, nor have we seen any users come to us in a tizzy because a LiveCd session caused their system to somehow get compromised or ruined. 

But if you don't like this and disagree with it, and truly feel it is such a huge security risk, then you have every right NOT to put the CD in your system, and try the bevy of other solutions out there.  Or, stick to Windows. And if you feel that makes you more secure somehow, more power to you.

---

### Post by arjaydavis on 2010-08-09
Can anyone definitively answer my original question - i.e. what caused mount.ntfs to run on its own? It does seem to happen arbitrarily, at random, still does it now.

**Responses here gone off on tangent...**
(The discussion here has gone off into a, perhaps too passionate, tangent about the merits of Windows and Ubuntu sharing file systems on the same machine, a purposeful discussion in its own right but not really answering my original question. It's hard to pick out the facts as the responses are unstructured, so I've tried to structure mine with summary headings. Forgive if this sounds ungrateful though :) )

**Default housekeeping activity? Where setup?...**
Is it a standard default housekeeping activity that Ubuntu performs. If so where would I look in the system to find out where/when it is run? crontab? for cronjob. Any other places that would cause it to be triggered. If I can find this out then I believe I can be fairly sure that it is not instigated externally, i.e. a hacker breaking into my system and running it.

**A little more detail on my setup...**
/windows mounted from Ubuntu which gives access to Windows NTFS C drive from Ubuntu and also /localshare which is a separate NTFS partition. I set these up in to partitioning stage in the Ubuntu install, installing Ubuntu on my machine which already had Windows 7. Sure you might pass judgement on this as to whether it is a good idea as the tangent discussion might indicate. I'm thinking of my setup as a learning exercise, to see what's possible, to try out things. But put that aside for a moment and try to help with the original question please.

**No apparent problems with Windows after mount.ntfs running, but can I be sure?...**
Booting into my Windows on the same machine seems unaffected by the mount.ntfs activity while in Ubuntu. A Norton full scan shows no issues. That is not to say there definitely aren't issues, as if it was a malicious attacker running mount.ntfs in Ubuntu, it is possible that they inserted malware into the Windows partition "under the radar" of Norton or Windows itself.

So, original question then: i.e. what caused mount.ntfs to run on its own? Was it accessing my NTFS partitions? any definitive answers?

---

### Post by OpSecShellshock on 2010-08-09
Yeah, sorry about that. Anyway, I notice that one of the more recent questions pertaining to your issue got kind of buried; cariboo907 had asked if there was an entry to mount the disk in the fstab file. There'd be some options in there that could lead to automatic mounting, though I can't say why it would be different than it was before you noticed this.

Another possibility is that it's being mounted in user space, which doesn't necessarily increase resource usage but does make it visible in top.

Did anything on your system change between when you set it up and when you noticed the high usage? Is it possible it had been happening all along?

---

### Post by arjaydavis on 2010-08-09
> **OpSecShellshock said:**
> cariboo907 had asked if there was an entry to mount the disk in the fstab file.


Thanks for replying...

**yes there is (in my previous post you'll read that i* deliberately set ubuntu to mount Windows C and another NTFS partition during the Ubuntu install process*** (but this still doesn't explain why it apparently randomly decides to run mount.ntfs on its own, when I haven't gone near those partitions via Ubuntu...), here's my /etc/fstab:


```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
/dev/sda3       /boot           ext4    defaults        0       2
# /localshare was on /dev/sda7 during installation
UUID=CCD233CDD233BB12 /localshare     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /windows was on /dev/sda2 during installation
UUID=A8445BA7445B76D2 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
/dev/sda6       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0
```      



> **OpSecShellshock said:**
> 
There'd be some options in there that could lead to automatic mounting, though I can't say why it would be different than it was before you noticed this.


Take a look above and see if those options are in my /etc/fstab

> **OpSecShellshock said:**
> 
Another possibility is that it's being mounted in user space, which doesn't necessarily increase resource usage but does make it visible in top.


**How would I check mounting in user space - and, still, why would it do it?...**
How would I check that? And what would trigger it to do it and when? I certainly notice my hard drive rumbling during mount.ntfs running - in fact that is what alerted me to it - and to run 'top'. When mount.ntfs finally stops running the rumbling of the hard drive stops, which would discount the theory about the resource usage; less hard drive activity is required.

> **OpSecShellshock said:**
> 
Did anything on your system change between when you set it up and when you noticed the high usage? Is it possible it had been happening all along?

**All *seems* fine...**
Not that I know of, all seems fine, but is it? As said in previous post, when booted into Windows and ran Norton scan, no issues were picked up. That is not to say there weren't any as malicious code could circumvent these protections, especially once hacked into Ubuntu - as Norton itself would not be running, not Windows, so it's possible that once hacked into Ubuntu, there is less protection for the Windows partition. I certainly want to be wrong.

**Summary of this post: Paranoia? But - just want to know why mount.ntfs runs on its own without user triggering it**
The above could actually be hysterical paranoia, a sentiment perhaps shared by some other posters here for sure as you have read. At the end of the day, what I just want to know is why mount.ntfs stated running of its own accord, on its own, without me accessing my NTFS partitions. The chances are, it is probably not sinister, but I am trying to understand what my system is doing.

---

### Post by FuturePilot on 2010-08-09
> At the end of the day, what I just want to know is why mount.ntfs stated running of its own accord, on its own, without me accessing my NTFS partitions.
But you did access them in a way. By putting them in fstab they are automatically mounted when you boot. mount.ntfs is the process that allows you to mount and access NTFS partitions. It's going to be running any time you have an NTFS partition mounted.

---

### Post by p_code on 2010-08-09
> **FuturePilot said:**
> But you did access them in a way. By putting them in fstab they are automatically mounted when you boot. mount.ntfs is the process that allows you to mount and access NTFS partitions. It's going to be running any time you have an NTFS partition mounted.

What makes you think HE had anything to do with it ???

------------- edit ----------------

I'm re-editing this post to try to make it a little clearer exactly what I think the issues are, and to explain to the original poster arjaydavis what happened in his case.

In simple language -

1.  arjaydavis - The reason your NTFS partitions are being automatically mounted at boot time is because they are being called out for mounting in the /etc/fstab file by Ubuntu.  

2.  The reason Ubuntu did this is because, as you yourself said, _you told Ubuntu to do this during the install._

3.  Yes, in this case there is indeed a reason that this particular users NTFS partitons are being mounted, but my point is that this doesn't really matter in the end, since even if he hadn't explicitly mounted his NTFS windows partitions, the bad guys are free to do so anyway!

4.  arjaydavis is also concerned that this could have compromised his security, and I have pointed out that this is a reasonable concern, since the standard 'default_permissions' mount gives 777 permissions which make it trivial to compromise BOTH the Windows OS and then the Linux OS using a ping-pong virus that uses the poor security of Ubuntu to compromise Windows, and then uses the now-compromised Windows install to break back into Linux.

5.  YES THIS CAN ALSO HAPPEN TO USERS OF DUAL BOOT SYSTEMS THAT DO NOT EXPLICITLY MOUNT THEIR WINDOWS NTFS OR FAT32 PARTITIONS.


Due to a really nasty security hole in Ubuntu's handling of Windows NTFS (or FAT32) file system mounts, it's really easy for a malicious script to bypass the user entirely, and mount your MS Windows partitions, and either install malware, or simply delete them entirely.

To test this, I took a brand new serial ATA drive, formated it and wrote a few hundred Megs of Data to it in Windows XP, then installed it as /dev/sdb1 in an Ubuntu 10.04 box that had never had anything but it's own root and swap mounted.

[COLOR=SeaGreen][COLOR=Blue]Test #1 -  Run 'mount' from an xterm console to see if drive is mounted at boot-up

Test Result #1 - On boot-up, the drive is not mounted by default (so far, so good, right? stay tuned, things get worse . . . )[/COLOR]

[/COLOR]
[COLOR=Magenta][COLOR=Blue]Test #2  Can FAT or NTFS drive partitions be arbitrarily mounted by any user

Test Result #2 - YES Nautilus will mount FAT or NTFS partitions R/[COLOR=Blue]W 777 for anyone anytime [/COLOR][/COLOR][COLOR=Blue] [COLOR=Red]
(_NOT GOOD _ - Ubuntu provides no easy option to prevent this)[/COLOR][/COLOR][/COLOR][COLOR=Red]
[/COLOR]

[COLOR=Red][COLOR=Blue]Test  #3 - Can a malicious script bypass the user and mount FAT or NTFS Windows partitons?

Since, for this test, my NTFS drive was configured as /dev/sdb1 

a malicious script would only have to issue the following command -[/COLOR]
[B][COLOR=Black]
gvfs-mount -d /dev/sdb1[/COLOR][/B]

[COLOR=Blue]Ubuntu complains about a half dozen different ways about permissions [COLOR=Red]THEN GOES AHEAD AND MOUNTS THE PARTITION!!![/COLOR]

No 'privilege escalation' password prompt, no warning to user, NO NOTHING (if the script is running in the background, you won't know anything at all is going on unless you notice a slight blip of hard drive activity as the drive is mounted).[/COLOR]

Test Result #3  YES a totally unprivileged malicious user script can totally bypass root access (or any other privilege escalation) and mount _any_ FAT or NTFS Windows OS partitions as R/W 777 (which could allow the installation of a Windows Trojan root kit in the Win OS, leading ultimately to possible root level privilege escalation in BOTH Windows and Linux environments)[/COLOR]

Bottom line-

1.  This doesn't just happen if you explicitly mount your NTFS partitions.

2.  It doesn't just happen in the 'Try Ubuntu' Live CD environment, it also effects the standard hard disk install.

3.  You don't even need to interactively mount your NTFS partitions in Nautilus.

4.  If you have a dual boot environment, YOU don't need to do ANYTHING, except let the bad guys fool you into clicking on a malicious script  and your box is totally pwned. (quite easy to do, since Gnome conveniently lets an attacker make a script look like a totally harmless JPG,  PDF, TXT file etc.) 
[B]
[SIZE=2]Guys, seriously, given that totally non-privileged user scripts can use this vulnerability to completely bypass Ubuntu's security, don't you think it's time to stop making excuses and start looking at how we can fix this???[/SIZE][/B]

---

### Post by arjaydavis on 2010-08-10
> **p_code said:**
> 
2.  The reason Ubuntu did this is because, as you yourself said, _you told Ubuntu to do this during the install._


> **FuturePilot said:**
> But you did access them in a way. By putting them in fstab they are automatically mounted when you boot. mount.ntfs is the process that allows you to mount and access NTFS partitions. It's going to be running any time you have an NTFS partition mounted.

**...But What about mount.ntfs activity after boot time? (Without my consciously accessing them - e.g. by 'cd /windows' then 'ls' etc.)**
What I don't understand is why the hard disk starts rumbling with activity ***some time after*** the machine has booted, and that the 'top' command issued in a terminal shows mount.ntfs at the top of the process table - having most activity - at the same time the rumbling occurs - therefore likely the cause of the hard disk activity. Your points about it mounting at boot time are reasonable deductions but don't cover this situation. Sorry, I don't think I had made it clear as to when the activity that concerns me occurs: I'm concerned about mount.ntfs running of its own accord randomly some time after booting.

**More questions to help that aim of understanding why mount.ntfs seems to run on its own, some time after booting:**

[LIST]
[*]Is there anything in that /etc/fstab screen dump that I posted that would cause mount.ntfs to run on its own accord some time after booting?

[*]Would cronjobs be another place to look?

[*]Where else would trigger mount.ntfs to run?

[*]Can I tell if my system has been compromised? Are there firewall logs (presumably some attackers would cover their tracks though)

[*]When mount.ntfs is running as described in my situation, can I see what it is doing, what it is accessing? How do I do that?
[/LIST]

As said before it might well be an innocent activity but I do agree with p_code's side discussion about the whole arrangment of security (or lack of) between Ubuntu and NTFS partitions belonging to Windows operating system on same machine.
Thanks for your input it is appreciated.

---

### Post by OpSecShellshock on 2010-08-10
Well the mount.ntfs process was clearly causing the drive itself to spin up excessively. However, this is more likely due to an error of some kind than to something malicious (as there's no evidence of malicious activity provided at the moment). The mounting of the disk would have to be enabled locally, one way or the other (which is to say that a locally logged-in user would need to navigate to the folder or enable its contents to be displayed in some fashion--despite what anyone might say about this being done by a malicious web script, the fact remains that a locally logged in legitimate user is ultimately the one running the browser and, therefore, this theoretical script).

A quick check of high cpu usage with mount.ntfs suggests that the issue is occurring across several distributions of Linux, and appears to most often be associated with large files being transferred or copied from the ext formatted drives to the NTFS drives. It also happens when a Linux session is active using an ext partition, but files are being transferred from one NTFS partition to another NTFS partition during that session.

At the time of the issue, how long had your Linux session been active? Was there any kind of backup process started several hours earlier, or had you been accessing a large or potentially large amount of data from the NTFS partition some time earlier in the session? Have you checked the messages log for the date and time of the issue? It can be displayed from System-->Administration-->Log File Viewer.

---

### Post by arjaydavis on 2010-08-10
> **OpSecShellshock said:**
> 
At the time of the issue, how long had your Linux session been active?


About an hour or even less, but at least a few minutes after booting.

> **OpSecShellshock said:**
> 
Was there any kind of backup process started several hours earlier,


No.

> **OpSecShellshock said:**
> 
 or had you been accessing a large or potentially large amount of data from the NTFS partition some time earlier in the session?


No. During the sessions where the issue occured, i.e. within Ubuntu, I had never accessed the NTFS partitions.

> **OpSecShellshock said:**
> 
Have you checked the messages log for the date and time of the issue? It can be displayed from System-->Administration-->Log File Viewer.

No, not yet, but that sounds useful, what I am looking for regarding what was actually happening. I'll have a look when I'm next using the system...

---

### Post by FuturePilot on 2010-08-10
> **arjaydavis said:**
> **...But What about mount.ntfs activity after boot time? (Without my consciously accessing them - e.g. by 'cd /windows' then 'ls' etc.)**
What I don't understand is why the hard disk starts rumbling with activity ***some time after*** the machine has booted, and that the 'top' command issued in a terminal shows mount.ntfs at the top of the process table - having most activity - at the same time the rumbling occurs - therefore likely the cause of the hard disk activity. Your points about it mounting at boot time are reasonable deductions but don't cover this situation. Sorry, I don't think I had made it clear as to when the activity that concerns me occurs: I'm concerned about mount.ntfs running of its own accord randomly some time after booting.

**More questions to help that aim of understanding why mount.ntfs seems to run on its own, some time after booting:**

[LIST]
[*]Is there anything in that /etc/fstab screen dump that I posted that would cause mount.ntfs to run on its own accord some time after booting?

[*]Would cronjobs be another place to look?

[*]Where else would trigger mount.ntfs to run?

[*]Can I tell if my system has been compromised? Are there firewall logs (presumably some attackers would cover their tracks though)

[*]When mount.ntfs is running as described in my situation, can I see what it is doing, what it is accessing? How do I do that?
[/LIST]

As said before it might well be an innocent activity but I do agree with p_code's side discussion about the whole arrangment of security (or lack of) between Ubuntu and NTFS partitions belonging to Windows operating system on same machine.
Thanks for your input it is appreciated.

Install iotop and run it when the disk activity occurs. Arrow over to the Disk Read and Disk Write columns. It will list the exact process that is reading or writing. Hopefully that will shed more light on what exactly is doing it because I have a feeling it's not the mount.ntfs process itself.

> **p_code said:**
> 
3.  Yes, in this case there is indeed a reason that this particular users NTFS partitons are being mounted, but my point is that this doesn't really matter in the end, since even if he hadn't explicitly mounted his NTFS windows partitions, the bad guys are free to do so anyway!
No they aren't. When you try to mount a Windows partition you get this:
[IMG]http://stashbox.org/973361/Screenshot-Authenticate-1.png[/IMG]


> 5.  YES THIS CAN ALSO HAPPEN TO USERS OF DUAL BOOT SYSTEMS THAT DO NOT EXPLICITLY MOUNT THEIR WINDOWS NTFS OR FAT32 PARTITIONS.
No it can't. See screenshot.

> Due to a really nasty security hole in Ubuntu's handling of Windows NTFS (or FAT32) file system mounts, it's really easy for a malicious script to bypass the user entirely, and mount your MS Windows partitions, and either install malware, or simply delete them entirely.

To test this, I took a brand new serial ATA drive, formated it and wrote a few hundred Megs of Data to it in Windows XP, then installed it as /dev/sdb1 in an Ubuntu 10.04 box that had never had anything but it's own root and swap mounted.

[COLOR=SeaGreen][COLOR=Blue]Test #1 -  Run 'mount' from an xterm console to see if drive is mounted at boot-up

Test Result #1 - On boot-up, the drive is not mounted by default (so far, so good, right? stay tuned, things get worse . . . )[/COLOR]

[/COLOR]
[COLOR=Magenta][COLOR=Blue]Test #2  Can FAT or NTFS drive partitions be arbitrarily mounted by any user

Test Result #2 - YES Nautilus will mount FAT or NTFS partitions R/[COLOR=Blue]W 777 for anyone anytime [/COLOR][/COLOR][COLOR=Blue] [COLOR=Red]
(_NOT GOOD _ - Ubuntu provides no easy option to prevent this)[/COLOR][/COLOR][/COLOR][COLOR=Red]
[/COLOR]
Non-admin user gets this:
[IMG]http://stashbox.org/973377/Screenshot-Authenticate.png[/IMG]

> Test  #3 - Can a malicious script bypass the user and mount FAT or NTFS Windows partitons?

Since, for this test, my NTFS drive was configured as /dev/sdb1 

a malicious script would only have to issue the following command -
[B]
gvfs-mount -d /dev/sdb1[/B]

Ubuntu complains about a half dozen different ways about permissions [COLOR=Red]THEN GOES AHEAD AND MOUNTS THE PARTITION!!![/COLOR]

I get the same prompt as seen if my first screenshot.

> Test Result #3  YES a totally unprivileged malicious user script can totally bypass root access (or any other privilege escalation) and mount _any_ FAT or NTFS Windows OS partitions as R/W 777 (which could allow the installation of a Windows Trojan root kit in the Win OS, leading ultimately to possible root level privilege escalation in BOTH Windows and Linux environments)
I fail to see how that could lead to root lever privilege escalation in Linux.

> **[SIZE=2]Guys, seriously, given that totally non-privileged user scripts can use this vulnerability to completely bypass Ubuntu's security, don't you think it's time to stop making excuses and start looking at how we can fix this???[/SIZE]**
My screenshots seem to disagree. But if you really think it's a problem then go file a bug report.

---

### Post by cariboo on 2010-08-10
I just fired up the only multi-boot system I have, clicked on the Windows partition in nautilus, the Windows partition was mounted, but the permissions are 40700:

```
me@mcleese:/media$ ls -l
total 8
drwx------ 1 me me 8192 2010-08-06 13:57 E428DEE228DEB332
```

which means that only the user that mounted the drive has read/write access to the drive, it is not world read/write, as p_code asserts. I've included a screenshot.

---

### Post by p_code on 2010-08-10
> **cariboo907 said:**
> I just fired up the only multi-boot system I have, clicked on the Windows partition in nautilus, the Windows partition was mounted, but the permissions are 40700:

```
me@mcleese:/media$ ls -l
total 8
drwx------ 1 me me 8192 2010-08-06 13:57 E428DEE228DEB332
```

which means that only the user that mounted the drive has read/write access to the drive, it is not world read/write, as p_code asserts. I've included a screenshot.

Thanks for the correction, I was mixed up on the permissions being 777 because in testing I also did mounts from /etc/fstab to duplicate the original posters configuration.

The Gnome mounter does seem to be mounting all files 40700, but that is a distinction without any real difference, because 40700 gives that user a big fat 7 (Read, Write, or Execute) for the entire NTFS or FAT partition, which of course will let you do ANYTHING you want, and more importantly from a system security point of view will also let a malicious script running as your user do anything IT WANTS.

Even if you don't mount the drive in Nautilus, Ubuntu will happily give ANY user script running in your name the same unlimited Read/Write/Execute privileges after it mounts the partition for you.   

Ubuntu will also happily do the same for any other user who happens to boot up the system.


FuturePilot -

Your screen shots look a little different, are you running KDE, XFCE, LXDE ?

I did say _**Ubuntu**_  (not Kubuntu, Xubuntu, Lubuntu, or Upurwazunto :wink:)

If the KDE (or XFCE or LXDE) variations don't share this issue, then that's all well and good, but let's not use that to try to delibertly deceive users of the mainstream Ubuntu distro into thinking that there is not a problem here. 

But I think that you were perfectly aware of this distinction, and your cynical 'If you are still convinced . . .  comment, makes it seem like you are angry with me for finding this issue in the mainstream Ubuntu distro, when you should be overjoyed that we now have a chance to tighten up the security.
[COLOR=Red][B][SIZE=2]
For the record, I just did a forced update on the base _Ubuntu_ 10.04.1 to 10.04.2 and a Nautilus is still not requiring any kind of password authentication on mounts, and a malicious script can still silently mount and infect or destroy an NTFS partition with no prompt or warning to the user whatsoever.[/SIZE][/B][/COLOR]

---

### Post by DrMelon on 2010-08-10
> **p_code said:**
> 

1.  Take advantage of [THIS STUPID GNOME DEFECT]("http://ubuntuforums.org/showpost.php?p=9680466&postcount=73") to make your malicious script look EXACTLY like a 

Whoa whoa whoa, am I mistaken in thinking this is Open Source Software? No? Then why don't you contribute to the project and fix it yourself? You'd be benefitting thousands.

---

### Post by FuturePilot on 2010-08-10
> **p_code said:**
> 
FuturePilot -

Your screen shots look a little different, are you running KDE, XFCE, LXDE ?

I did say _**Ubuntu**_  (not Kubuntu, Xubuntu, Lubuntu, or Upurwazunto :wink:)


But I think that you were perfectly aware of this distinction, and your cynical 'If you are still convinced . . .  comment, makes it seem like you are angry with me for finding this issue in the mainstream Ubuntu distro, when you should be overjoyed that we now have a chance to tighten up the security.


I am using the standard _**Ubuntu**_. Nothing else.
I have no problem with people finding problems.

---

### Post by cariboo on 2010-08-10
It seems Ubuntu does a better than either Kubuntu or PCLinuxOS. Kubuntu asks for authorization before mounting the Windows partition with 777 permissions, PCLinuxOS doesn't ask for permission, and automagically mounts all the partitions it finds, Linux partitions are mounted 755, and the Windows partition was mounted with 777 permissions.

---

### Post by p_code on 2010-08-10
> **FuturePilot said:**
> I am using the standard _**Ubuntu**_. Nothing else.
I have no problem with people finding problems.

Sorry for the misunderstanding, I think the confusion comes from the fact that you were talking about a totally non-admin capable user, and I was talking about the DEFAULT user that Ubuntu creates for single user desktops (that is non-root but allowed to escalate privileges to root level temporarily for admin purposes)

As you know the DEFAULT user in a single user Ubuntu install is non-root, but must be admin-capable.   

This is because someone HAS to be able to do admin, and if you could delete that capability from your account when you are the only user, you would literally have no way to turn it back on.

Since about 99% of the users leave their account set to this default arrangement, they will see the same behavior that I described.

I did try a number of ways to fix this using already available settings.  I tried disabling the 'mount external storage devices' in my default user profile but that did nothing. 

I also noticed that the "user space mounting using FUSE" without a prompt option was already turned OFF, and would have thought that that would have had some effect, but this option also does nothing.


I would be interested in hearing others opinions, but from my perspective, these options should work, and while they are at it, a general rework of the Gnome Mount controls might be in order.

At a minimum, I'd like to see a per user setting for each user to allow  -

1.  Option to allow this user to mount internal or external CD/DVD drives (no password confirmation needed).

2.  Option to allow this user to mount external removable R/W drives (SCSI, USB drives, floppy etc). (no password confirmation needed)

3  Option to allow this user to mount internal IDE or SATA foreign Operating System Partitions (i.e. Windows  FAT, NTFS )

In the case of FAT/NTFS system partitions, I strongly feel that even authorized users should always be prompt to confirm their password at least on the initial mount, but then they should have a check-box option to check at that time to allow them the option to automount the same partition in future sessions without the password prompt if desired (which would make it more convenient for those that are less concerned about security)

Also, a really useful option would be to allow the admin to have the option to specify a specific folder as the 'root node' of the mount _origin_ on the FAT or NTFS partition.

So, for example, the admin could preset the user's mount permissions, to only allow limited NTFS or FAT access such that they could only mount their own MS Windows side HOME/USER_FOO folder (and sub-folders) on their Linux side's /home/usr/foo/windows mount point)

This last option would really make a Dual Boot Multi User box work the way it should, i.e. with each separate user having access to their own resources across the O.S. boundary, but NOT to files or folders of other users. 

Just a thought . . .

Again to FuturePilot, sorry for making assumptions about your configuration that were not the case, but I didn't notice that you were using a setup other than the default Ubuntu single user setup.  

For users that _are_ still using the default Gnome Desktop setup, you might want to be vigilant about your windows partitions, since the default setup will definitely allow bad guys to access any Windows FAT or NTFS partitions without your authorization.  (either by mounting them in a script if they are not mounted, or by just accessing with full Read/Write permission if they are already mounted).

---

### Post by FuturePilot on 2010-08-10
> **p_code said:**
> Sorry for the misunderstanding, I think the confusion comes from the fact that you were talking about a totally non-admin capable user, and I was talking about the DEFAULT user that Ubuntu creates for single user desktops (that is non-root but allowed to escalate privileges to root level temporarily for admin purposes)


No, I tested both the default user (the one with sudo privileges) and a non-admin desktop user. In both cases I was prompted for a password.

---

### Post by p_code on 2010-08-11
> **FuturePilot said:**
> No, I tested both the default user (the one with sudo privileges) and a non-admin desktop user. In both cases I was prompted for a password.

That's really interesting, because that doesn't seem to be what I (and some others) are seeing with the standard Ubuntu 10.04 out of box Gnome install.

Can you think of anything you might have done that would explain this (for example did you set a root account password?)

:popcorn:

---

### Post by FuturePilot on 2010-08-11
> **p_code said:**
> That's really interesting, because that doesn't seem to be what I (and some others) are seeing with the standard Ubuntu 10.04 out of box Gnome install.

Can you think of anything you might have done that would explain this (for example did you set a root account password?)

:popcorn:

Honestly I can't. I did not set a root password nor have I modified any of the default settings with regards to permissions or Policykit.

---

### Post by OpSecShellshock on 2010-08-11
Regarding the topic at hand, I had a thought. FuturePilot mentioned in an earlier comment that it may not have been mount.ntfs itself that was responsible for the high resource usage. Is it possible that the problem involved some user process that ordinarily does write to that partition, but it couldn't do so precisely because it wasn't mounted? It's certainly not unheard of for a task that is repeatedly trying and failing to do something to drive up CPU use by not stopping when it happens. If it was trying to operate on multiple files and had to fail through all of them it might cause such a problem. If the process trying to write to the non-mounted drive was not graphical then there might not even be any obvious way of knowing (such as how the window is greyed out on a graphical program).

---

### Post by arjaydavis on 2010-08-11
Folks, thanks for your follow ups - my (latest) responses - to those, quoting you, in detail, below:

Summary of your follow ups and my responses:

[LIST]
[*]FuturePilot: I will try your suggestion to run iotop to see more file access activity by mount.ntfs

[*]FuturePilot: I don't think I see password prompts when I try to deliberately access NTFS partitions when browsing Ubuntu GUI via 'Computer' (reminder to others: original question is about why mount.ntfs runs of its own accord without deliberate user access.), so...

[*]p_code: I think I see what you're getting - i.e. not being asked for passwords (but I will check)

[*]cariboo907: I will see what my permissions are and compare with yours
[/LIST]


Now, those responses in detail...


> **FuturePilot said:**
> Install iotop and run it when the disk activity occurs. Arrow over to the Disk Read and Disk Write columns. It will list the exact process that is reading or writing. Hopefully that will shed more light on what exactly is doing it because I have a feeling it's not the mount.ntfs process itself.


OK I will try iotop.

> **FuturePilot said:**
> 
No they aren't. When you try to mount a Windows partition you get this:
[IMG]http://stashbox.org/973361/Screenshot-Authenticate-1.png[/IMG]


> **FuturePilot said:**
> 
Non-admin user gets this:
[IMG]http://stashbox.org/973377/Screenshot-Authenticate.png[/IMG]


> **FuturePilot said:**
> No, I tested both the default user (the one with sudo privileges) and a non-admin desktop user. In both cases I was prompted for a password.

I don't think I get either of these prompts if deliberately I browse to the /windows or /localshare NTFS partitions on my machine. (Note that the original question was about why mount.ntfs is apparently being triggered on its own, without such deliberate user activity).

So my experience is more like this:

> **p_code said:**
> That's really interesting, because that doesn't seem to be what I (and some others) are seeing with the standard Ubuntu 10.04 out of box Gnome install.

Can you think of anything you might have done that would explain this (for example did you set a root account password?)

:popcorn:

Regarding access permissions of NTFS partition from Ubuntu...

> **cariboo907 said:**
> I just fired up the only multi-boot system I have, clicked on the Windows partition in nautilus, the Windows partition was mounted, but the permissions are 40700:

```

me@mcleese:/media$ ls -l
total 8
drwx------ 1 me me 8192 2010-08-06 13:57 E428DEE228DEB332
```

which means that only the user that mounted the drive has read/write access to the drive, it is not world read/write, as p_code asserts. I've included a screenshot.

That would be interesting for me to do the same and see what my permissions are.

---

### Post by FuturePilot on 2010-08-11
> **arjaydavis said:**
> 
I don't think I get either of these prompts if deliberately I browse to the /windows or /localshare NTFS partitions on my machine. (Note that the original question was about why mount.ntfs is apparently being triggered on its own, without such deliberate user activity).


That is because yours are already mounted via fstab. I do not have mine set up in fstab.

---

### Post by arjaydavis on 2010-09-30
Thanks FuturePilot for suggesting installing and running iotop:
[http://ubuntuforums.org/showpost.php?p=9702962&postcount=36](http://ubuntuforums.org/showpost.php?p=9702962&postcount=36)

This revealed that the original "problem" is associated with the updatedb.mlocate and it running mount.ntfs. updatedb.mlocate is top of the list on disk usage and presumably is using mount.ntfs to access the disk.

I think this is related to the Software Update Manager, as an update notification window appears around about the same time that the high disk activity, as reported in the original post, occurs.

Still not sure why updatedb.mlocate uses mount.ntfs to mount the disk and indeed why it is looking at the NTFS partition.

A quick google search shows discussions about the necessity/frequency of updatedb.mlocate running so often. So it looks like it is a feature rather than anything sinister.

Comments?

---

