---
title: "how to: automatically umount cifs partitions"
date: 2006-11-05
forum: Tutorials
---

### Post by max.durden on 2006-11-05
Hi everybody, 
I'm posting a modification of a simple script originally coded by 'jferrando'
[http://www.ubuntuforums.org/showthread.php?t=171958&highlight=cifs](http://www.ubuntuforums.org/showthread.php?t=171958&highlight=cifs)
devoted to automatically umount cifs partitions in the shutdown and reboot sequence of Ubuntu (Dapper+). The main problem with the original script was that mount locations of cifs partitions had to be explicitly hardcoded in the script: I have written a simple routine which detects all mounted cifs-partition and umount them before proceeding with the other phases of the  shutdown/reboot sequences.

-----------------------------------------------------
Instructions are very simple:
uncompress archive and set 'chmod +x' on the mountcifs file   
sudo cp mountcifs /etc/init.d/ 

cd /etc/rc0.d
sudo ln -s /etc/init.d/mountcifs K02mountcifs

cd /etc/rc6.d
sudo ln -s /etc/init.d/mountcifs K02mountcifs

...that's all!
------------------------------------------------------
I've experienced problem in the shutdown of my laptop just after sharing cifs filesystems with other PCs in a VPN network... this script fixed the problem.... hope it will be useful for someone out there!

Happy Coding
Max

---

### Post by crazy___cow on 2006-11-05
Works fine for me.

---

### Post by kupajava on 2007-02-06
The script worked well and ended my CIFS VFS: No Response for cmd 50 error that would lock my sys on shutdown.

Unfortunately, now i get one at the same place that says:
"CIFS VFS: No Response for Cmd 113"

However, this error does not lock the system, it just hangs for about 5 seconds and then continues to shutdown properly. 

Any Ideas?

---

### Post by max.durden on 2007-02-13
I'm am experiencing the same problem, but at the moment I don'tknow how to fix that... 
However, I'm working on it... if i find a solution I'll post on this thread

Happy coding

Max

---

### Post by zer01 on 2007-03-07
Hi, thanks, it's very useful to me.

---

### Post by funchords on 2007-04-22
Thank you!  This solved the problem I was having in Feisty Fawn 7.04 with long delays on the 

"CIFS VFS: No Response for Cmd (various)"

Your solution worked immediately (no need to reboot after applying).  

Thanks!!

---

### Post by sanuward on 2007-04-25
this is great, thanks a lot

---

### Post by SonicSteve on 2007-04-29
Super!!
I've been living with this problem since mid way through Edgy. Problem solved! thanks

---

### Post by mattme on 2007-04-29
What does happen if you try and shutdown with cifs still mounted? If it's something bad, then this is a bug, and bugs should be fixed.

---

### Post by SonicSteve on 2007-04-30
> **mattme said:**
> What does happen if you try and shutdown with cifs still mounted? If it's something bad, then this is a bug, and bugs should be fixed.

For me it just pauses with the "no response for cmd 50 mid" error. It then continues after about 5-10 seconds and shutsdown.

You are right though, it does seem to be a bug

---

### Post by Doc Horn on 2007-05-13
thanks a lot!

---

### Post by dmizer on 2007-06-14
max.durden, this thread has been linked to on my howto for cifs here: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

thanks so much for posting a fix for this, i had been unable to find a working solution.

---

### Post by caliFrag on 2007-06-15
max thanks so much for posting this fix!

I am such a linux newbie - having never even logged into a linux machine until I decided to install Ubuntu over my old Win2kPro installation. 

the community support is unbelievable and in the past few weeks with the help of users like yourself I have been able to transform into a competent user.

This successfully removed my "no response for cmd 114 mid 11" error on shutdown/reboot.

Thanks again!

---

### Post by vmax4ever on 2007-06-15
Many thanks - finally the problem is solved.

---

### Post by Korgmatose on 2007-07-02
The script has a problem with smb/cifs-shares that contain spaces... For instance the shares on my windows-machine are called "my music" and "movies" respecively. This makes  'cut -d\  -F3'  cut in different places on the two lines (mountpoint on the second, but only "on" on the first, since "music" is seen  as the second field.)

I have resolved this by renaming the share on my windows-computer, but the script should still be made aware of this.

---

### Post by sander marechal on 2007-07-06
I have written a different init script based off /etc/init.d/sendsigs and /etc/init.d/umountnfs.sh that has two improvements over the script from the original poster:

1) It does not use `cut` so shares with spaces in them are not a problem.
2) Before unmounting the cifs shares, the script first asks all processes that are still using the shares to exit. If those processes don't exit then they will be forcefully terminated. This ensures that the unmount won't fail because there are still open files on it.

Use it in the same way as the script from the original poster: unzip the attachment and save it's content as /etc/init.d/umountcifs. Then symlink it to /etc/rc0.d/KXXumountcifs where XX is any number lower than 20 (because at K20 udev and portmap and all get shut down and unmounting cifs shares doesn't work after that).

---

### Post by shanti on 2007-07-10
> **max.durden said:**
> 
-----------------------------------------------------
Instructions are very simple:
uncompress archive and set 'chmod +x' on the mountcifs file   
sudo cp mountcifs /etc/init.d/ 

cd /etc/rc0.d
sudo ln -s /etc/init.d/mountcifs K02mountcifs

cd /etc/rc6.d
sudo ln -s /etc/init.d/mountcifs K02mountcifs

------------------------------------------------------


You may use update-rc.d to simplify the installation:

```

gunzip umountcifs.gz && chmod +x umountcifs

sudo cp umountcifs /etc/init.d/ 

sudo update-rc.d umountcifs stop 02 0 6 .
```

Don't forget ending point in the last command! ;) 

Thanks for your script!

---

### Post by dgermann on 2007-07-12
Hi--

Many thanks. This was stalling my shutdown on 7.04 for about 2 minutes, and this seems to work.

BTW, don't use these commands:> 
cd /etc/rc0.d
sudo ln -s /etc/init.d/mountcifs K02mountcifs

cd /etc/rc6.d
sudo ln -s /etc/init.d/mountcifs K02mountcifs

Instead, use these for the second script to work:
```

cd /etc/rc0.d
sudo ln -s /etc/init.d/umountcifs K02umountcifs

cd /etc/rc6.d
sudo ln -s /etc/init.d/umountcifs K02umountcifs
```

I suspect that's why it did not work for me the first time....

Oh, the update-rc.d did not work for me.

---

### Post by shanti on 2007-07-13
> **dgermann said:**
> 
Oh, the update-rc.d did not work for me.

Did you get an error?

---

### Post by phile on 2007-07-13
Does this script unmount cifs shares at logout, or only at shutdown/reboot?

Phil

---

### Post by dgermann on 2007-07-16
shanti--

Yes, I get this error message:

> usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults|multiuser [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
doug@ubuntu:/etc/init.d$ 


Thanks, shanti, for whatever light you can shed on this.

---

### Post by sander marechal on 2007-07-17
From the update-rc.d man page:

> 
System administrators are not encouraged to  use  update-rc.d  to  manage runlevels.  They should edit the links directly or use runlevel editors such as sysv-rc-conf and bum  instead.


So, don't use update-rc.d.

---

### Post by dgermann on 2007-07-17
Sander--

Ahh! Thank you very much!

So is that what that command was doing, was managing runlevels? Boy was that hard to figure from the error message I got!

Thanks!

---

### Post by sander marechal on 2007-07-17
Yeah. update-rc.d was made for the post-install scripts inside .deb packages to make it easy for applications to add/remove themselves from the /etc/rcX.d directories without tripping over themselves or having lots of duplicate post-install code in those .deb packages.

The easiest way for you is to simply symlink the things you want manually using the "ln -s" command.

---

### Post by shanti on 2007-07-18
> **dgermann said:**
> shanti--

Yes, I get this error message:

Thanks, shanti, for whatever light you can shed on this.

Probably you forgot the point at the end, i.e.
```

sudo update-rc.d umountcifs stop 02 0 6      #wrong
sudo update-rc.d umountcifs stop 02 0 6 .    #ok

```

But as for previous suggestions, you may want to use a different method to do the work.

---

### Post by Kanji_Man on 2007-07-23
I have also been wrestling with CIFS VFS errors when shutting down ubuntu while CIFS shares are mounted. I am currently running Ubuntu & Kubuntu both 7.04 Feisty Fawn 64bit. This script does seem to help however it does not work 100%. I have not thoroughly explored the reasons why sometimes I receive the errors and sometimes do not.

However, extensive googling on the topic revealed an interesting discussion on launchpad [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/90795"). By combining the information on that thread with how this script works I have come up with two simple commands that appear to work well for me.  The underlying causes of these errors may not be the same for you as they are for me however these two commands have resolved my CIFS unmounting problems on every machine I have tested them on:

```
sudo mv /etc/rc0.d/S31umountnfs.sh /etc/rc0.d/S17umountnfs.sh
sudo mv /etc/rc6.d/S31umountnfs.sh /etc/rc0.d/S17umountnfs.sh
```

Perhaps someone more experienced and knowledgable can explain the details but from what I have gathered, the underlying problem is that during ubuntu shutdown the network is stopped before the shares are unmounted.  While this script will unmount the shares before the network is stopped, a more elegant solution is to move the existing unmounting process to happen before the network is stopped.. which is what happens by moving S31 to S17.

---

### Post by sander marechal on 2007-07-23
There is a very simple reason why you cannot simply move umountnfs to S17: What about people who load system directories or home directories from a network share? unmounting those at S17 is too soon. There may still me applications running that use them.

By the way, you said the script doesn't always work. Which one? The mountcifs script posted by the creator of this thread? Or the umountcifs I posted a couple of posts above? They both work in very different ways.

---

### Post by dgermann on 2007-07-23
Sander--

Thank you!

Shanti--

Perhaps I did, but I thought I had tried to make sure it was there. In any event, tonight I get this error message:
> System startup links for /etc/init.d/umountcifs already exist

Thanks. I used the ln-s method and it seems to work.

Thanks everyone!

---

### Post by Gandhy on 2007-09-03
merci beaucoup
thanks

---

### Post by J@n on 2007-09-25
Hi All,

The gz file and the step by step from Shanti solved my problem in just under 1 minute. And I have been struggling with shutdown for a few weeks. Go figure:(

---

### Post by JawsThemeSwimming428 on 2007-09-28
I am trying to fix this issue right now. What are the correct commands to run?

---

### Post by svdb on 2007-10-04
How comes Ubuntu isn't able to unmount network drives all by itself when it shuts down entirely?  :confused: 

IMO nobody should need to Google for a script to have Ubuntu behave a little bit like a modern OS.

When I click "Shut down" or "Restart" why isn't it obvious for Ubuntu that my machine will eventually power off completely and that network drives are not needed anymore?
I'd like to understand.

---

### Post by sander marechal on 2007-10-05
It's not the OS that is at fault. It's the cifs driver.

The cifs driver does not run inside the kernel like all the other drivers but runs inside a separate daemon. Don't ask me why. Ubuntu tries to do the right thing: first shut down all applications, then unmount all network disks, then unmount all local disks. Because this daemon is a separate program, it leads to a catch-22 situation. When Ubuntu shuts down all other programs prior to unmounting, it also shuts down the cifs driver.

That means your network shares have vanished without being unmounted. When in the next step Ubuntu tries to unmount the network shares, you get an error because you don't have connection with the shares anymore.

What my script above does is quite simple. Before the step "stop all applications" it will "stop all applications that use the network shares" and "unmount cifs shares". So, you end up with:

* stop all applications using the cifs share
* unmount the cifs share
* stop all applications (also kills the cifs daemon)
* unmount other network shares
* unmount local disks

Which is the correct order.

---

### Post by svdb on 2007-10-08
Thanks for the explanation (and thanks for the script!), I can see now why things are happening this way.

Still, I find this default behaviour a serious shortcomming.

To the end user it doesn't matter who of the kernel or the driver is responsible for this issue. What they see is: windows connects flawlessly to my NAS (no matter what protocol it uses), Linux does not (unless very complicated and cryptic commands are typed in). Guess what they'll prefer... Arguing that windows is unsafe and part of a world domination plan, and such, doesn't make a point to them. They (and I) want it to "Just Work". :)

I really want to use Ubuntu, but it is clear that it doesn't allow me to do everything I did (easely) with Windows, unless I become a Linux guru... and sadly I don't have the time and energy to become one... (I prefer to spend my time with my family than to spend it on learning linux cmd lines)

I just hope some day the Ubuntu developers will put the user instead of the system in the center of their concern. I strongly believe it is the only factor which will allow people to massively migrate from windows to linux.

---

### Post by Jahkel on 2007-10-14
I agree with svdb, this could use some dev attention.  It is still not fixed in Gutsy, which makes me wonder what method is everybody else using for this shared drives?  The "Connect to server" method, which creates smb mappings is the most obvious and is handled correctly on shutdown, but is not suitable for applications that don't support the smb: protocol. :(

---

### Post by AndyQ on 2007-10-14
> **max.durden said:**
> Hi everybody, 
I'm posting a modification of a simple script originally coded by 'jferrando'


Cheers - fixed my annoying shutdown problem on my Dell 1720 running Gutsy!.

---

### Post by MattAustin on 2007-10-16
This problem is still occuring in Gutsy.

Reported as bug:
[https://bugs.launchpad.net/ubuntu/+bug/153444](https://bugs.launchpad.net/ubuntu/+bug/153444)

---

### Post by bpoteet on 2007-10-19
I'm using the umountcifs script and I'm still seeing the messages; however now after it drops to the terminal it goes back to the progress bar and then shuts down...is it actually working I wonder?

---

### Post by sander marechal on 2007-10-20
Well, the biggest annoyance that the script fixes isn't the the messages but the time it waits for a timeout. Does it shut down fast in you case? Or does it wait?

If the script doesn't work, then the most likely thing that goes wrong is that it's run too late. If you linked it as e.g. K19umountcifs in your rc.X directory, try lowering the number to e.g. K10umountcifs or even K05umountcifs. If you don't run any programs on the cifs and don't have any important directories mounted from cifs (e.g. /home) then you can probably even run it as K01umountcifs.

Experiment a bit. You'll want the script to run as late as possible without failing to work.

---

### Post by Paqman on 2007-10-22
Thanks for this script, it's worked perfectly for me!

---

### Post by bYOndo on 2007-10-30
> **sander marechal said:**
> There is a very simple reason why you cannot simply move umountnfs to S17: What about people who load system directories or home directories from a network share? unmounting those at S17 is too soon. There may still me applications running that use them.

By the way, you said the script doesn't always work. Which one? The mountcifs script posted by the creator of this thread? Or the umountcifs I posted a couple of posts above? They both work in very different ways.

Kanji was right; I experienced this behaviour:

On 7.04: the first post script worked for me without any other modification
On 7.10: the first post script did not work, dunno why, but Kanji solution worked (but I don't know if it would work without first post script, that I've already installed before modifying S30)

Anyway, it seems to cause no problem w/ my system, so thanks and cheers :)

Massimo

---

### Post by dark_harmonics on 2007-11-10
All,

I scripted the install using the code provided by the brilliant folks earlier in the post. Just thought i'd share this for the lazy fellows like me! 

Just extract and give it permissions to execute.

---

### Post by abubin on 2007-11-13
why all the trouble when you can just put the mount command into /etc/rc.local files? This file will be executed last during bootup. It works for my smbfs mount.

---

### Post by wyley.r on 2007-12-26
The following two commands should take care of unmounting Samba shares and other virtual filesystems before a shutdown or reboot.  They must be run as root; prefix them with "sudo" if you haven't set up your root account:

```

ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh

```

More explanation can be found here: 
[URL="http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/"]
**Unmount Samba filesystems before shutdown or reboot**[/URL].

Hopefully, this will avoid the need to download and install a separate script, as some other people have suggested.  All the tools you need are already built into the Debian/Ubuntu init system.

---

### Post by murmel on 2007-12-30
I just did this:

*sudo nano /etc/init.d/umountnfs.sh*
```
#! /bin/sh
#
# umountnfs.sh	Unmount all network filesystems.
#
PATH=/sbin:/bin:/usr/sbin:/usr/bin

# Write a reboot record to /var/log/wtmp before unmounting
halt -w

# Ensure /proc is mounted
test -r /proc/mounts || mount -t proc proc /proc

echo "Unmounting remote filesystems..."

#
# Read the list of mounted file systems and -f umount the
# known network file systems.  -f says umount it even if
# the server is unreachable.  Do not attempt to umount
# the root file system.  Unmount in reverse order from
# that given by /proc/mounts (otherwise it may not work).
#
unmount() {
	local dev mp type opts
	if read dev mp type opts
	then
		# recurse - unmount later items
		unmount
		# skip /, /proc and /dev
		case "$mp" in
		/|/proc)return 0;;
		/dev)	return 0;;
		esac
		# then unmount this, if nfs
		case "$type" in
		nfs|smbfs|ncpfs|**_cifs_**) umount -f "$mp";;
		esac
	fi
}

unmount </proc/mounts
```

I just added "|cifs" of the types that it should unmount and changed the symlinks in /etc/rc0.d and /etc/rc6.d from S31umountnfs to K15umountnfs. Works like a charm! (Don't forget "*sudo chmod +x /etc/init.d/umountnfs.sh*")

---

### Post by Psykotik on 2008-01-03
> **wyley.r said:**
> The following two commands should take care of unmounting Samba shares and other virtual filesystems before a shutdown or reboot.  They must be run as root; prefix them with "sudo" if you haven't set up your root account:

```

ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh

```

More explanation can be found here: 
[URL="http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/"]
**Unmount Samba filesystems before shutdown or reboot**[/URL].

Hopefully, this will avoid the need to download and install a separate script, as some other people have suggested.  All the tools you need are already built into the Debian/Ubuntu init system.
It worked for me. I prefer to create some symbolic links instead of creating/modifying files, so I tried your solution; I was inspired :)

---

### Post by JohnBoy55 on 2008-01-06
:) Thank you Max Durden. Your script worked beautifully. The implementation was pretty an 'I just believe' episode, as I really don't understand the bootup and shutdown sequence nearly as well as I should. Hopefully, someone will incorporate a fix to the distribution soon so the user isn't forced to the command line. Like it or not folks, it's the only way you'll ever pry the average computer away from Micro$oft Window$.

---

### Post by veloce on 2008-01-16
> **wyley.r said:**
> 
More explanation can be found here: 
[URL="http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/"]
**Unmount Samba filesystems before shutdown or reboot**[/URL].


This link doesn't seem to work for me, is this a temporary issue?

EDIT: was obviously temporary, is now working.  Thanks wyleyr.

---

### Post by veloce on 2008-01-16
> **wyley.r said:**
> The following two commands should take care of unmounting Samba shares and other virtual filesystems before a shutdown or reboot.  They must be run as root; prefix them with "sudo" if you haven't set up your root account:

```

ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh

```

More explanation can be found here: 
[URL="http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/"]
**Unmount Samba filesystems before shutdown or reboot**[/URL].

Hopefully, this will avoid the need to download and install a separate script, as some other people have suggested.  All the tools you need are already built into the Debian/Ubuntu init system.

In Gutsy at least, there are already links to these files in these directories, they just start with S31 rather than K15.  Tidiest option is just to change their names. I did it using "gksudo nautilus" and browsing to the directory.

---

### Post by MountainX on 2008-03-27
veloce's renaming solution seems to work in Hardy beta too.

BTW, don't use gedit if you are editing files on network shares. I kept thinking I wasn't setting up my shares correctly, but the problem was in gedit all along.

[https://bugs.launchpad.net/gedit/+bug/34813](https://bugs.launchpad.net/gedit/+bug/34813)

The diagnosis is described in these two comments here:
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/34813/comments/20](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/34813/comments/20)
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/34813/comments/40](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/34813/comments/40)

---

### Post by PaganBlasphemy on 2008-04-02
Thank you for this, I fixed my hardy installation using the rename method as well.

I wonder why this problem isn't fixed already, if it has been occurring for years and has an obvious solution?

---

### Post by landeel on 2008-05-06
My two cents here: I had to change the script to umount using 'umount -ifl blah' otherwise it would not work for me.

Edit:

Okay, I gave up on cifs. First I could only mount by IP and not by share name, wich is pretty annoying.
Then I updated my /etc/nsswitch.conf 'hosts:' to use 'wins'. This way I could mount the shares by name. But for some reason this configuration makes my computer freeze on bootup, when starting the samba daemons.
Well, then I removed 'wins' from my /etc/nsswitch.conf, and added the IPs and computer names to /etc/hosts. Not the ideal solution as IPs can change, but still it worked... until I tried to umount the shares!!!

I'm using 'fusesmb' now. I had absolutely no problems with it. It is very easy to setup, it can mount the entire network automatically.

---

### Post by elustran on 2008-05-08
> **wyley.r said:**
> The following two commands should take care of unmounting Samba shares and other virtual filesystems before a shutdown or reboot.  They must be run as root; prefix them with "sudo" if you haven't set up your root account:

```

ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh

```

More explanation can be found here: 
[URL="http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/"]
**Unmount Samba filesystems before shutdown or reboot**[/URL].

Hopefully, this will avoid the need to download and install a separate script, as some other people have suggested.  All the tools you need are already built into the Debian/Ubuntu init system.

Thanks! That's the easiest fix I've had to do all week!

---

### Post by gesders on 2008-05-16
thank you so much - what´s ubuntu without you ?

---

### Post by veera_kr on 2008-05-28
Thank You very much.It works fine for me.....

---

### Post by Aragorn2008 on 2008-07-19
> **wyley.r said:**
> The following two commands should take care of unmounting Samba shares and other virtual filesystems before a shutdown or reboot.  They must be run as root; prefix them with "sudo" if you haven't set up your root account:

```

ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh

```

More explanation can be found here: 
[URL="http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/"]
**Unmount Samba filesystems before shutdown or reboot**[/URL].

Hopefully, this will avoid the need to download and install a separate script, as some other people have suggested.  All the tools you need are already built into the Debian/Ubuntu init system.

Thanks a lot! Worked great for me! :)

---

### Post by NTolerance on 2008-07-22
Is this fix still necessary for NFS mounts in fstab?  I'm trying to ditch Samba due to very little progress being made on the "map network drives" type of feature that Windows has.

---

### Post by dmizer on 2008-07-22
> **NTolerance said:**
> Is this fix still necessary for NFS mounts in fstab?  I'm trying to ditch Samba due to very little progress being made on the "map network drives" type of feature that Windows has.

some networks require it, some do not.  your situation may require this fix, or it may not.  you won't know until you implement it.

if you're still interested in mapping samba drives, please see the second link in my sig.

---

### Post by NTolerance on 2008-07-22
> **dmizer said:**
> some networks require it, some do not.  your situation may require this fix, or it may not.  you won't know until you implement it.

if you're still interested in mapping samba drives, please see the second link in my sig.

Your how-to is great.  I've been mapping Samba shares that way for too long though.  It's a pretty messy method with having to store the password in a text file and all that.  I wish GNOME would provide a simple GUI to accomplish this task.  And fuse is just too slow.

---

### Post by rwabel on 2008-07-26
I've now tried all possibilities I've found on forums and by googling, still I always get this error message and my pc is not shutting/restarting. I need to poweroff my pc.

When I start the script manually, it unmounts my cifs and I can successfully restart or shutdown my pc

> rwabel@ubuntu:/etc/rc0.d$ ls -ll *umoun*
lrwxrwxrwx 1 root root 22 2008-07-26 14:19 K19umountcifs -> /etc/init.d/umountcifs
lrwxrwxrwx 1 root root 22 2007-01-19 03:20 S14umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx 1 root root 18 2007-01-19 03:20 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx 1 root root 20 2007-01-19 03:20 S60umountroot -> ../init.d/umountroot
rwabel@ubuntu:/etc/rc0.d$ 

Is there any fundamental mistake I did in the ordering?

---

### Post by sander marechal on 2008-07-27
> Is there any fundamental mistake I did in the ordering?

You could try lowering the umountcifs script. Try K15 or K12 or even lower. Eventually it should work when you're low enough.

---

### Post by rwabel on 2008-07-27
is k15 or k12 lower than s14?

---

### Post by sander marechal on 2008-07-27
Yes. First the K scripts are run, then the S scripts are run.

---

### Post by rwabel on 2008-07-28
It's strange, I put it as K12 and it's till not working. I can start it manually and then it successfully unmounts the cifs. 

lrwxrwxrwx 1 root root  13 2008-05-21 18:18 K01gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  17 2007-01-19 03:20 K01usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  22 2008-07-26 14:19 K12umountcifs -> /etc/init.d/umountcifs

Should I probably put it as K00 ?

---

### Post by sander marechal on 2008-07-28
Strange... perhaps there is an issue with Upstart running custom init.d scripts? I wrote it on Debian, not Ubuntu. I know that Debian's upcoming new init system needs headers added to init.d scripts.

Can you check if the script is run at all? Modify it so that it echoes out some crazy statement when run. E.g. add this somewhere at the top:

echo "LOOK AT ME!!!!!!!!!!!!!!!!!!"

Run the script manually to confirm that you see that output. Then shut down or reboot and see if you see the string (you may want to disable the boot splash so you can see the messages).

Alternatively, you could add something like this instead:

touch /home/rwabel/i-am-touched.txt

And see if that file exists after the reboot.

If you see the message (or if the file is created) then at least we know that the script is actually run.

---

### Post by rwabel on 2008-07-28
I can confirm that the script has been executet. I saw the message and the file has been created. However, the bad thing is that I got the CIFS error message before.

I got the CIFS error message and nothing happened, I clicked again on the power off button on my laptop and then I got the message from the script.

I've tried to use the script as K00, but it didn't help. Is there not a way to have that script executed even earlier?

---

### Post by rocketero2008 on 2008-08-30
I report that I have read most of the posts here in this forum concerned about the "CIFS VFS error" and I have NOT been able to get rid of it.

I switched the S31umountnfs and S40umountfs to K14umountnfs and K14umountfs and nothing changed.

Also I have read about a file in /etc/init.d called "umountcifs" but in Uubuntu hardy 8.04.1 is not there.

So meantime until I find a fix, I have disabled the windows mount share in the /etc/fstab file.

I am using smb4k for now to mount my windows shares until someone fix for good this issue.

---

### Post by sander marechal on 2008-08-31
umountcifs is a script that I wrote myself. There's a link to it earlier in this thread. Also, you can find it at [http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/](http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/)

---

### Post by rwabel on 2008-08-31
> **rocketero2008 said:**
> I report that I have read most of the posts here in this forum concerned about the "CIFS VFS error" and I have NOT been able to get rid of it.

I switched the S31umountnfs and S40umountfs to K14umountnfs and K14umountfs and nothing changed.

Also I have read about a file in /etc/init.d called "umountcifs" but in Uubuntu hardy 8.04.1 is not there.

So meantime until I find a fix, I have disabled the windows mount share in the /etc/fstab file.

I am using smb4k for now to mount my windows shares until someone fix for good this issue.

Does it work if you manually start the script? For me it does, but it doesn't work with the K12 or something like that. It get's started, but it doesn't work. :-(

---

### Post by rocketero2008 on 2008-09-01
> **rwabel said:**
> Does it work if you manually start the script? For me it does, but it doesn't work with the K12 or something like that. It get's started, but it doesn't work. :-(

I downloaded the 'umountcifs' script and placed in /etc/init.d and created symlinks in /etc/rc0.d and /etc/rc6.d as K19umountcifs but somehow it DID NOT fix the CIFS VFS problem while restarting ubuntu.

I don't know if is because I'm using UBUNTU 8.04.1 HARDY as the script was tested on earlier version of Ubuntu.

I'm still stuck with this error but will keep trying other alternatives

---

### Post by rwabel on 2008-09-01
but you can start it manually from the console. Then you should be able to restart ubuntu without any problems. This would show that the script is working

---

### Post by sander marechal on 2008-09-02
> **rocketero2008 said:**
> I downloaded the 'umountcifs' script and placed in /etc/init.d and created symlinks in /etc/rc0.d and /etc/rc6.d as K19umountcifs but somehow it DID NOT fix the CIFS VFS problem while restarting ubuntu.

Did you try it as K12umouncifs or even as K01umountcifs?

---

### Post by usererror on 2008-09-04
I did a script like this:

```

umount /path/to/cifs/share
umount /path/to/cifs/share2

```

and named it "S38umount-cifs" and placed it in /etc/init.d/ with a symlink in /etc/rc6.d/ and that works just great.

Is that not best practice?  I'm not a programmer...but it seems to work...now my box literally reboots instantly.

---

### Post by casperfelix on 2008-09-12
> **max.durden said:**
> Hi everybody, 
I'm posting a modification of a simple script originally coded by 'jferrando'
[http://www.ubuntuforums.org/showthread.php?t=171958&highlight=cifs](http://www.ubuntuforums.org/showthread.php?t=171958&highlight=cifs)
devoted to automatically umount cifs partitions in the shutdown and reboot sequence of Ubuntu (Dapper+). The main problem with the original script was that mount locations of cifs partitions had to be explicitly hardcoded in the script: I have written a simple routine which detects all mounted cifs-partition and umount them before proceeding with the other phases of the  shutdown/reboot sequences.

-----------------------------------------------------
Instructions are very simple:
uncompress archive and set 'chmod +x' on the mountcifs file   
sudo cp mountcifs /etc/init.d/ 

cd /etc/rc0.d
sudo ln -s /etc/init.d/mountcifs K02mountcifs

cd /etc/rc6.d
sudo ln -s /etc/init.d/mountcifs K02mountcifs

...that's all!
------------------------------------------------------
I've experienced problem in the shutdown of my laptop just after sharing cifs filesystems with other PCs in a VPN network... this script fixed the problem.... hope it will be useful for someone out there!

Happy Coding
Max

Works 100% for me in Hardy Heron un-mounting a little NAS drive.:biggrin::biggrin:

---

### Post by rwabel on 2008-09-20
since I did a clean 8.10 installation, I no longer suffer from this issue

---

### Post by Crash87ss on 2008-09-21
> **wyley.r said:**
> The following two commands should take care of unmounting Samba shares and other virtual filesystems before a shutdown or reboot.  They must be run as root; prefix them with "sudo" if you haven't set up your root account:

```

ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh

```

More explanation can be found here: 
[URL="http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/"]
**Unmount Samba filesystems before shutdown or reboot**[/URL].

Hopefully, this will avoid the need to download and install a separate script, as some other people have suggested.  All the tools you need are already built into the Debian/Ubuntu init system.

:popcorn: Worked like a charm in Mythbuntu 8.04.1  Thanks to all!

---

### Post by davidryder on 2008-09-23
Thanks!!

EDIT: It worked perfectly. I no longer get any errors of any sort. I wonder if this is a bug in Samba/CIFS or Ubuntu.

---

### Post by svance5 on 2008-09-29
In my cifs umoun script I had to do a lazy umount for cifs, otherwise I always seem to get a device busy response.

umount -l <path>

---

### Post by Huoliuhi on 2008-09-29
thanks a lot , bump up up up!!

---

### Post by @once on 2008-10-01
Absolutely fantastic!
Thanks.

---

### Post by changlinn on 2008-10-02
I cannot believe this is still a bug in Hardy. I remember logging this issue back in the days of Dapper Drake, we are back to another LTS and it is still there, why can't they just put this script in is beyond me.

---

### Post by sander marechal on 2008-10-02
> **changlinn said:**
> why can't they just put this script in is beyond me.

Apathy, probably. Ubuntu is waiting for Debian to fix it. Over at Debian, the init guys and cifs guys are blaming eachother, so nothing gets fixed. See [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=431966](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=431966)

---

### Post by jcottier on 2008-10-06
> **wyley.r said:**
> The following two commands should take care of unmounting Samba shares and other virtual filesystems before a shutdown or reboot.  They must be run as root; prefix them with "sudo" if you haven't set up your root account:

```

ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh

```

More explanation can be found here: 
[URL="http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/"]
**Unmount Samba filesystems before shutdown or reboot**[/URL].

Hopefully, this will avoid the need to download and install a separate script, as some other people have suggested.  All the tools you need are already built into the Debian/Ubuntu init system.

This worked for me in Gutsy, but after an update to Hardy 8.4.1 it broken again. The links are still there in rc0.d and rc6.d. Any ideas?

---

### Post by niall.ingram on 2008-10-06
Script worked first time. No more hang ups or delays on shuting down. Thanks

---

### Post by Axel B on 2008-10-13
The script worked perfectly the first time.

Thank you very much !

---

### Post by mk1_yea on 2008-10-15
it sucks to register.. took me >5 minutes to complete everything.. hope it works.

---

### Post by ounas on 2008-10-21
Thanks

:guitar:

---

### Post by ad_267 on 2008-10-31
> **rwabel said:**
> since I did a clean 8.10 installation, I no longer suffer from this issue

I'm still having this problem with 8.10 (clean install).

---

### Post by Loki3000 on 2008-11-10
My laptop connected to the router by WI-FI. I was trying fix from this thread, but error stil there.
I change priority to
```

K01umountnfs
K02kdm

```
but it's not working too. Think that KNetworkManager was closed before shutdown scripts runs.
Any solutions are welcome:)

my version: kubuntu 8.10

---

### Post by michaelzap on 2008-11-18
> **ad_267 said:**
> I'm still having this problem with 8.10 (clean install).

+1

I had fixed this with a script in Hardy, but I'd rather do it the "right" way now.

---

### Post by dtcostelloe on 2008-11-30
The script worked great for me as well.  Thanks!  (Great instructions too.)

---

### Post by jpneron on 2008-12-16
> **wyley.r said:**
> The following two commands should take care of unmounting Samba shares and other virtual filesystems before a shutdown or reboot.  They must be run as root; prefix them with "sudo" if you haven't set up your root account:

```

ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh

```

More explanation can be found here: 
[URL="http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/"]
**Unmount Samba filesystems before shutdown or reboot**[/URL].

Hopefully, this will avoid the need to download and install a separate script, as some other people have suggested.  All the tools you need are already built into the Debian/Ubuntu init system.
Simple, elegant, and it works (Intrepid Ibex).

Thanks.

---

### Post by antaresteleko on 2008-12-19
Thanks Max, 

I had the same problem, and your solution works perfectly for me. The shutdown process is now clean and fast.

antaresteleko.

---

### Post by nicolasavru on 2008-12-23
> **wyley.r said:**
> The following two commands should take care of unmounting Samba shares and other virtual filesystems before a shutdown or reboot.  They must be run as root; prefix them with "sudo" if you haven't set up your root account:

```

ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh

```

More explanation can be found here: 
[URL="http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/"]
**Unmount Samba filesystems before shutdown or reboot**[/URL].

Hopefully, this will avoid the need to download and install a separate script, as some other people have suggested.  All the tools you need are already built into the Debian/Ubuntu init system.

Got rid of some of the errors, but not all. I changed it to K02umountnfs (from K15umountnfs) and not it works great.

Thank you very much.

---

### Post by bpituley on 2008-12-24
The solution works - thank you - but I'm going to echo other users who wonder why this kind of command line intervention is even required.

---

### Post by sander marechal on 2008-12-24
Because nobody is taking responsibility for the bug. The initscripts people blame smb and vice-versa. See the upstream bug report: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=431966](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=431966)

---

### Post by 11ni17ge29 on 2008-12-24
there are four kinds of jewelry,[wholesale jewelry](http://www.jewelryol.com/),[fashion jewelry](http://www.jewelryol.com/),[handmade jewelry](http://www.jewelryol.com/) and [costume jewelry](http://www.jewelryol.com/) ,which one do you like ?

---

### Post by anibalojeda on 2008-12-26
> **sander marechal said:**
> Because nobody is taking responsibility for the bug. The initscripts people blame smb and vice-versa. See the upstream bug report: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=431966](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=431966)

I just took a look at the bug report, very annoying.. this problem does not exist in other distros (slackware, mandriva, centos) i tested their latest versions.. 
Is possible to package this solution in a dep file & submit this as a package for other to use ?
Would be accepted ? 

this small things should be fixed.

thanks for the one that came with the soluton. 

by the way im using mine at K03:
update-rc.d umountcifs.sh stop 03 0 6 

works perfect

---

### Post by tonynonumber on 2008-12-30
Thanks one more time Max, this cured the problem for me (in U8.10).

---

### Post by mvdv95 on 2009-01-01
Aslo thanks from me Max, I was mounting my networkdrives today and faced the same problem at shutdown.  It's fixed perfectly with your script.

---

### Post by gersoid on 2009-01-11
Worked fine on 8.10 (earlier solutions not so successful) - thanks

What has to happen so that this is automatically part of 9.04 ?

---

### Post by sander marechal on 2009-01-11
> **gersoid said:**
> What has to happen so that this is automatically part of 9.04 ?

This bug needs to be solved: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=431966](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=431966)

---

### Post by Jebedai on 2009-01-14
Agreed this bug needs to be fixed but this script worked so well!!! Thanks everyone for posting this much needed help. I used it last night and it doesnt give me any more errors when unmounting my samba drives.:guitar:

---

### Post by phumpeti on 2009-01-15
Worked like a charm for me too!

---

### Post by lingenfr on 2009-01-19
max, thanks for this. It is too bad that after two years, your fix has not been incorporated. Hopefully, the 8-year-olds will quit bickering and just apply the fix. FWIW, I agree with the developer who said this is not an smbfs problem.

---

### Post by kirkytullins on 2009-01-25
Thanks Max ! it solved my umount cifs hang in 8.10 as well !

I still think canonical should somehow automate this though.

Cheers

---

### Post by trgz on 2009-01-25
worked a treat (in Intrepid)

---

### Post by david916 on 2009-01-26
> **wyley.r said:**
> The following two commands should take care of unmounting Samba shares and other virtual filesystems before a shutdown or reboot.  They must be run as root; prefix them with "sudo" if you haven't set up your root account:

```

ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh

```

More explanation can be found here: 
[URL="http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/"]
**Unmount Samba filesystems before shutdown or reboot**[/URL].

Hopefully, this will avoid the need to download and install a separate script, as some other people have suggested.  All the tools you need are already built into the Debian/Ubuntu init system.


Hi,
These 2 simple lines worked just so nicely, in my case.....BTW, I had this issue on Intrepid (freshly installed), but not on Hardy(other station)..
Anyway...now it's fixed. thx for great job, wyley.r.

david916

---

### Post by dchost on 2009-03-06
The problem is fixed. Oh yeah!! Thanks for sharing....:D

---

### Post by KiDQUiCK on 2009-03-08
Hey guys,
I tried Max's script recently with no joy... then i found this thread which is a much simpler solution and works perfectly!

[http://blog.avirtualhome.com/2008/03/10/ubuntu-shutdown-problem-cifs-related/](http://blog.avirtualhome.com/2008/03/10/ubuntu-shutdown-problem-cifs-related/)

Enjoy

---

### Post by Mindzai on 2009-03-24
Worked for me on 8.10, but only after I set umountcifs to K00!

---

### Post by PapaRaven on 2009-03-26
9.04, and it works just swell.  I don't suppose I would need this if HFSplus volumes could be shared out over NFS, but they can't.  -Something to do with HFSplus not running at the kernel level.  Hence smb.

Anyway thanks from 2009 back to 2006; hacking your system is what Linux is all about!  There's no hack like an old hack.  etc. etc.

---

### Post by fi5ban on 2009-03-27
> **usererror said:**
> I did a script like this:

```

umount /path/to/cifs/share
umount /path/to/cifs/share2

```

and named it "S38umount-cifs" and placed it in /etc/init.d/ with a symlink in /etc/rc6.d/ and that works just great.

Is that not best practice?  I'm not a programmer...but it seems to work...now my box literally reboots instantly.

I like this way. If I manually  unmount the network drive then shutdown there are no issues

I spent 2 months getting ubuntu to connect to may landrv. opensuse and fedora did but not through fstab yet, so if you can help here that give ubuntu a fighting chance to be the os of choice

---

### Post by seismofish on 2009-04-07
On my system (Intrepid), rc scripts are run with /bin/sh rather than /bin/bash so the array syntax in umountcifs was failing and I was still getting the error messages on shutdown/restart.

I've changed the "stop" routine in the script to
```
stop() {
    echo "Unmounting samba-cifs filesystems..."
    mount -t cifs | cut -d\  -f3 | xargs -L 1 umount -l
}
```
(which should work in both bash and sh) and it now works perfectly.

I'm fairly new to Ubuntu so I'll apologise in advance if there was a more obvious solution.

---

### Post by anibalojeda on 2009-04-12
on my laptop using 9.04 developmnet version i had to change the order of rc scripts

umountnfs.sh is om k01 then gdm on k02 than usplash to k03

K01umountnfs.sh -> ../init.d/umountnfs.sh
K02gdm -> ../init.d/gdm
K03usplash -> ../init.d/usplash

every other order of script will fail on this laptop using wlan.

this was my only solution.

---

### Post by Consciously on 2009-04-12
very awesome it works good great job

---

### Post by smolty on 2009-04-24
> **wyley.r said:**
> The following two commands should take care of unmounting Samba shares and other virtual filesystems before a shutdown or reboot.  They must be run as root; prefix them with "sudo" if you haven't set up your root account:

```

ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh

```

More explanation can be found here: 
[URL="http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/"]
**Unmount Samba filesystems before shutdown or reboot**[/URL].

Hopefully, this will avoid the need to download and install a separate script, as some other people have suggested.  All the tools you need are already built into the Debian/Ubuntu init system.

This worked for me in hardy and intrepid, doesn't seem to be working in 9.04 though. Any ideas???

---

### Post by diana.artemis on 2009-04-24
> **anibalojeda said:**
> on my laptop using 9.04 developmnet version i had to change the order of rc scripts

umountnfs.sh is om k01 then gdm on k02 than usplash to k03

K01umountnfs.sh -> ../init.d/umountnfs.sh
K02gdm -> ../init.d/gdm
K03usplash -> ../init.d/usplash

every other order of script will fail on this laptop using wlan.

this was my only solution.

I have used sander marechal's umountcifs script for ages now, and it runs perfectly on my 8.04 and 8.10 machines.  But I upgraded a laptop to 9.04 this morning (with sander marechal's script still set up as before), and got the CIF VFS error.  And I've spent all day trying to find a fix, changing the priority of the umountcifs script as high as K01, and trying out various other methods, all to no avail.

The only thing that has worked is anibalojeda's solution of changing the order of the rc0.d and rc6.d links from the default order, which is
K01gdm
K02usplash
(no Kxxumountnfs.sh)

TO this new order:
K01umountnfs.sh
K02gdm
K03usplash

Clearly the Ubuntu devs have changed something about the way the init.d / rc scripts work.  (I haven't had time today to investigate what's gone on with Jaunty.)  But I'm very grateful to Anibal for the fix!  (though I've no idea why it works, and haven't checked if it has any unwanted effects elsewhere.  Does anyone who understands this stuff better than me have any comments on issues with changing the order as above?)

This CIFS unmounting bug should have been fixed years ago, but it's still plaguing us all.

Thanks very much, Anibal!  Now I can get back to doing some work, instead of messing around with the OS!

---

### Post by dmizer on 2009-04-24
> **diana.artemis said:**
> I have used sander marechal's umountcifs script for ages now, and it runs perfectly on my 8.04 and 8.10 machines.  But I upgraded a laptop to 9.04 this morning (with sander marechal's script still set up as before), and got the CIF VFS error.  And I've spent all day trying to find a fix, changing the priority of the umountcifs script as high as K01, and trying out various other methods, all to no avail.

The only thing that has worked is anibalojeda's solution of changing the order of the rc0.d and rc6.d links from the default order, which is
K01gdm
K02usplash
(no Kxxumountnfs.sh)

TO this new order:
K01umountnfs.sh
K02gdm
K03usplash

Clearly the Ubuntu devs have changed something about the way the init.d / rc scripts work.  (I haven't had time today to investigate what's gone on with Jaunty.)  But I'm very grateful to Anibal for the fix!  (though I've no idea why it works, and haven't checked if it has any unwanted effects elsewhere.  Does anyone who understands this stuff better than me have any comments on issues with changing the order as above?)

This CIFS unmounting bug should have been fixed years ago, but it's still plaguing us all.

Thanks very much, Anibal!  Now I can get back to doing some work, instead of messing around with the OS!

If you have some spare time, perhaps you could test this: [http://ubuntuforums.org/showthread.php?t=1128729](http://ubuntuforums.org/showthread.php?t=1128729)

---

### Post by diana.artemis on 2009-04-25
> **dmizer said:**
> If you have some spare time, perhaps you could test this: [http://ubuntuforums.org/showthread.php?t=1128729](http://ubuntuforums.org/showthread.php?t=1128729)

That was one of the fixes I tried while attempting to get Jaunty to shut down gracefully.  I'm afraid it didn't work for me.

The only fix that worked was to put umountnfs.sh before everything else in the shutdown sequences in rc0.d and rc6.d

As I say, I don't really understand why this is necessary.  Apparently, CIFS is not in the kernel, but runs as a daemon.  So Network Manager (or perhaps WPAsupplicant) gets shut down earlier, and disconnects the CIFS shares before they are unmounted.  Then CIFS starts to close down, and attempts to unmount the shares that are no longer connected - hence the CIFS VFS error.

So you'd think that all you'd need to do was raise the kill priority of umountcifs or umountnfs.sh, or lower the priority of the network shutdown, so that the CIFS unmount occurs first (and that's the effect of the fix you refer to above.)

But I couldn't find anyway of getting this to work, other than putting umountnfs.sh first, which is very puzzling.  That's what makes me think the devs have changed something else that makes the init.d / rc arrangements not work as expected.

---

### Post by kaiben on 2009-04-25
Hi all, i've updated my netbook yesterday to jaunty and have the same problem. But for me also the 'put umountnfs.sh at first" approach does not work. I can only shutdown normally if i call umountnfs.sh by hand and shutdown afterwards. File permissions seems to be ok, i have absolutely no idea why /etc/rc0.d/K01umountnfs.sh should not be called or should not work. Any idea?

Cheers Kai

---

### Post by diana.artemis on 2009-04-25
> **kaiben said:**
> Hi all, i've updated my netbook yesterday to jaunty and have the same problem. But for me also the 'put umountnfs.sh at first" approach does not work...

Just to be clear, did you include the changes to gdm and usplash, too?

K01umountnfs.sh
K02gdm
K03usplash

Or did you leave them as they were (K01gdm; K02usplash)?  If so, you might try adjust them, too.  

Other than that 'trial-and-error' tweak, I've no idea what to suggest I'm afraid.  (Like you, I did resort to unmounting 'manually', with a little script that I ran before shutting down;  but it's a pain to have to do that sort of thing.)

---

### Post by kaiben on 2009-04-25
Yes, i changed all three scripts.

---

### Post by diana.artemis on 2009-04-26
> **kaiben said:**
> Yes, i changed all three scripts.

Mmmm...  Sorry, I can't suggest anything else.

First, it's very odd that Sander Marechal's umountcifs script has stopped working in Jaunty.  Secondly, it's very odd that changes to the priority of the 'stop' in rc0.d and rc6.d are not working as expected.

Given this has just appeared, I'm wondering whether it's something to do with the new Upstart in Jaunty, which now controls the boot and shutdown processes. 

(I notice that Sander Marechal mentioned such a possibility in this thread last year, here
[http://ubuntuforums.org/showpost.php?p=5474861&postcount=65](http://ubuntuforums.org/showpost.php?p=5474861&postcount=65)
and I'm guessing the changes just introduced may have messed up the fixes involving external scripts in some way)

But I'm way out of my depth now.  Let's hope someone who really understands this stuff can make sense of what's going on, and find a permanent fix for this longstanding bug, which has been plaguing Ubuntu for three years:
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/42121](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/42121)

---

### Post by veloce on 2009-04-26
Strange, I have umountnfs.sh as k15 (i.e. it runs third).

This has been running fine and has not been affected by the upgrade to Jaunty.

---

### Post by diana.artemis on 2009-04-27
Update on this issue with Jaunty.  I'd upgraded an old Dell Inspiron laptop from Intrepid, and that was the machine on which the umountcifs script stopped working.

I've just done a clean install of Jaunty on this laptop, and on an old Compaq PC.  I installed the script on both.

The desktop shut down fine with umountcifs being called at K02 in rc0.d and rc6.d;  but the laptop - with exactly the same set up - suffered the CIFS VFS error.

Importantly, the desktop has a PCI network card, but the laptop has a PCMCIA wifi card.  The problem is clearly to do with a difference in the relative positions in the shutdown sequence that the shares are unmounted and different types of interface are closed.

So I tried setting umountcifs to K00 on the laptop.  It shuts down OK now (though there is a brief flicker out to a terminal during the GUI shutdown sequence - probably something to do with putting umountcifs before gdm.)

Hope this helps someone with their investigations.

---

### Post by dmizer on 2009-04-27
> **diana.artemis said:**
> Update on this issue with Jaunty.  I'd upgraded an old Dell Inspiron laptop from Intrepid, and that was the machine on which the umountcifs script stopped working.

I've just done a clean install of Jaunty on this laptop, and on an old Compaq PC.  I installed the script on both.

The desktop shut down fine with umountcifs being called at K02 in rc0.d and rc6.d;  but the laptop - with exactly the same set up - suffered the CIFS VFS error.

Importantly, the desktop has a PCI network card, but the laptop has a PCMCIA wifi card.  The problem is clearly to do with a difference in the relative positions in the shutdown sequence that the shares are unmounted and different types of interface are closed.

So I tried setting umountcifs to K00 on the laptop.  It shuts down OK now (though there is a brief flicker out to a terminal during the GUI shutdown sequence - probably something to do with putting umountcifs before gdm.)

Hope this helps someone with their investigations.

Are you using network-manager to manage your wireless connection? Network-manager starts your network in userspace, so when you log off, your network connection (and thereby your share connection) terminates. You may be successful by running the unmount script during your session logout: [http://ubuntuforums.org/showthread.php?t=252935](http://ubuntuforums.org/showthread.php?t=252935)

---

### Post by diana.artemis on 2009-04-28
> **dmizer said:**
> Are you using network-manager to manage your wireless connection? Network-manager starts your network in userspace, so when you log off, your network connection (and thereby your share connection) terminates. You may be successful by running the unmount script during your session logout: [http://ubuntuforums.org/showthread.php?t=252935](http://ubuntuforums.org/showthread.php?t=252935)

I just realised this issue occurs on both my laptops (not just the one with PCMCIA wifi interface).  So, yes, I use network-manager for the wifi.  But I'm afraid I don't know enough about bash scripts to follow your advice.  The thread you pointed to suggests adding the script to the end of /etc/gdm/PostSession/Default;  but I don't really feel confident about where or how to add umountcifs to this:

```
#!/bin/sh

PATH="/usr/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

exit 0
```
I'd be grateful for any suggestions!  :-)

(And then I guess it would also be necessary to revert the priorities in rc0.d and rc6.d to the defaults?)

---

### Post by diana.artemis on 2009-04-28
> **dmizer said:**
> ...Network-manager starts your network in userspace, so when you log off, your network connection (and thereby your share connection) terminates...

Dmizer >>> Isn't that why 

K01umountnfs.sh
K02gdm
K03usplash

works -- because it makes the nfs unmount *before* gdm shuts down?  So what's the 'risk' of shutting down like that, rather than running the umountcifs script?  

Is it that the script checks whether any processes are using the mounted shares, and, if so, kills them before unmounting?  What happens if they're still running when the shares are unmounted?  Possible loss of data, I guess;  but is that actually likely to happen in most real-world shutdowns by the user?

Sorry to ask so many questions, but I don't know much about these processes, and am trying to get some inkling of what's going on here.

---

### Post by dmizer on 2009-04-28
Well, you said it's NOT working. That's why K01umountnfs.sh, K02gdm, and K03usplash /should/ work.

As to the /etc/gdm/PostSession/Default, try putting your unmount script at the very top like so:
```
#!/bin/sh
[COLOR="Red"]Your umount script here[/COLOR]

PATH="/usr/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

exit 0
```

If worst comes to worst, it's easy enough to revert that file. If that doesn't work, please post the contents of your /etc/fstab if you've posted it before, I missed it.

---

### Post by diana.artemis on 2009-04-28
> **dmizer said:**
> Well, you said it's NOT working. That's why K01umountnfs.sh, K02gdm, and K03usplash /should/ work.

As to the /etc/gdm/PostSession/Default, try putting your unmount script at the very top like so...

Thanks for your reply.  I should have been clearer - the K01/K02/K03 set up as above does indeed work fine.  And I could actually live with that.

But I wasn't sure how 'safe' it is (from the point of view of data loss/corruption during the shutdown).  As I understand it, the umountcifs script actually checks for processes using the shares, and kills them before unmounting the shares;  but I don't think umountnfs.sh does that, so I assumed it relied on some other script to look after that first?  Is that so, or is it safe to leave the K01umountnfs.sh / K02gdm / K03usplash set up to do the job safely?

Not being sure about this, I thought I'd try to get the umountcifs script working properly on my wifi machines, and that's why I came back with the questions above.  

Thanks very much for your suggestion about hacking /etc/gdm/PostSession/Default.  Do you reckon that would be a better method?  If so, I'll put the rc0. and rc6.d scripts back in the right order, and try the hack, when I've got a few minutes.

---

### Post by dmizer on 2009-04-28
Hacking /etc/gdm/PostSession/Default shouldn't be necessary for cifs. For NFS, just add the "soft" option to your nfs fstab line. Then it can unmount normally during shutdown even if the network is not active.

Like this:
```
server.mydomain.com:/files /files nfs [COLOR="Red"]soft[/COLOR],rsize=8192,wsize=8192,timeo=14,intr
```

FYI from man nfs:
```
       soft / hard    Determines the recovery behavior of the NFS client after
                      an NFS request times out.  If neither option  is  speci&#8208;
                      fied  (or if the hard option is specified), NFS requests
                      are retried indefinitely.  If the soft option is  speci&#8208;
                      fied,  then  the  NFS  client fails an NFS request after
                      retrans retransmissions have been sent, causing the  NFS
                      client to return an error to the calling application.

                      [B]NB:  A  so-called  "soft"  timeout can cause silent data
                      corruption in certain  cases.  As  such,  use  the  soft
                      option only when client responsiveness is more important
                      than data integrity.  Using NFS over TCP  or  increasing
                      the value of the retrans option may mitigate some of the
                      risks of using the soft option.[/B]
```
Emphasis mine.

For example (default is 3):
```
server.mydomain.com:/files /files nfs soft,retrans=6,rsize=8192,wsize=8192,timeo=14,intr
```

---

### Post by diana.artemis on 2009-04-28
> **dmizer said:**
> Hacking /etc/gdm/PostSession/Default shouldn't be necessary for cifs. For NFS, just add the "soft" option to your nfs fstab line....

I am only using CIFS (not NFS).  And umountnfs.sh looks after all the relevant file systems, including CIFS as the following relevant fragment of the umountnfs.sh script indicates:

```

...
case "$FSTYPE" in
  nfs|nfs4|smbfs|ncp|ncpfs|cifs|coda|ocfs2|gfs)
    DIRS="$MTPT $DIRS"
      ;;
   proc|procfs|linprocfs|devfs|devpts|usbfs|usbdevfs|sysfs)
     DIRS="$MTPT $DIRS"
      ;;
esac
...

```

So I guess I won't bother hacking /etc/gdm/PostSession/Default!

Many thanks for your thoughtful and instructive replies.

---

### Post by kaiben on 2009-04-28
I've had the problem that linking /etc/init.d/umountnfs.sh to /etc/rc0.d/K01umounntfs.sh does not work for my jaunty install on an Asus EEEPC 901.

Calling it from /etc/gdm/PostSession/Default works instead!

Many thanks for the advice.

Cheers Kai

---

### Post by pajarraco on 2009-05-06
Thanks kaiben, I used jaunty and this finally fix the error.

I put this line on my /etc/gdm/PostSession/Default file

```
/etc/init.d/umountnfs.sh
```

after the line ```
exit 0
```

and it fix.

---

### Post by patrickes on 2009-05-17
Thanks! worked great for me, all errors gone......

---

### Post by gutomezencio on 2009-05-20
> **pajarraco said:**
> Thanks kaiben, I used jaunty and this finally fix the error.

I put this line on my /etc/gdm/PostSession/Default file

```
/etc/init.d/umountnfs.sh
```

after the line ```
exit 0
```

and it fix.
Hello Pajarraco!

It worked 100% in Ubuntu Jaunty!

Thanks!

---

### Post by veloce on 2009-05-20
In Jaunty, I'm now having the opposite problem.  When I start my laptop not connected to the network I get a long delay and error messages while it tries to mount the cifs partitions.

Is there a similar work around for this?

---

### Post by dmizer on 2009-05-20
> **veloce said:**
> In Jaunty, I'm now having the opposite problem.  When I start my laptop not connected to the network I get a long delay and error messages while it tries to mount the cifs partitions.

Is there a similar work around for this?

That's probably worth a new thread ;)

---

### Post by veloce on 2009-05-20
> **dmizer said:**
> That's probably worth a new thread ;)

Yeah, I wondered.  I'll do that now.

---

### Post by desmane on 2009-05-24
works for me, thanks dude!

---

### Post by Karaden on 2009-06-10
Just chipping in to say that sander marechal's script worked great for me on Jaunty - thanks! :)

---

### Post by error420 on 2009-06-11
Thank you. This works great!

---

### Post by racecarpete on 2009-06-12
Hi, I am running Jaunty and after getting samba working nicely and automounting my shares, I now have the hang on shut down.

I tried the steps in the first post regarding

```
ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh
```

That did not work.  Then I did the fix posted by pajarraco but that also did not work.

If I put the line after the "exit 0" as he instructed, I get the following error.

```
acpid:exiting
[43988.264014] cifs vfs: No response for cmd 114 mid 279
```

I then put the line after the #!/bin/sh per this thread [Mount Samba shares with utf8...]("http://ubuntuforums.org/showthread.php?t=288534&highlight=fstab+auto+mount")

and instead I get this error on shut down.

```
[5966.192029] cifs vfs: No response for cmd 114 mid 1828
```

Can someone please lend a hand?

Thanks,
Peter

---

### Post by dmizer on 2009-06-12
racecarpete, please post your current /etc/init.d/umountnfs.sh.

Also, please post your /etc/fstab.

---

### Post by racecarpete on 2009-06-12
here is the contents of /etc/init.d/umountnfs.sh

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          umountnfs
# Required-Start:
# Required-Stop:     umountfs
# Should-Stop:       $network $portmap nfs-common
# Default-Start:
# Default-Stop:      0 6
# Short-Description: Unmount all network filesystems except the root fs.
# Description:       Also unmounts all virtual filesystems (proc, devfs,
#                    devpts, usbfs, sysfs) that are not mounted at the
#                    top level.
### END INIT INFO

PATH=/sbin:/usr/sbin:/bin:/usr/bin
KERNEL="$(uname -s)"
RELEASE="$(uname -r)"
. /lib/init/vars.sh

. /lib/lsb/init-functions

case "${KERNEL}:${RELEASE}" in
  Linux:[01].*|Linux:2.[01].*)
	FLAGS=""
	;;
  Linux:2.[23].*|Linux:2.4.?|Linux:2.4.?-*|Linux:2.4.10|Linux:2.4.10-*)
	FLAGS="-f"
	;;
  *)
	FLAGS="-f -l"
	;;
esac

do_stop () {
	# Write a reboot record to /var/log/wtmp before unmounting
	halt -w

	# Remove bootclean flag files (precaution against symlink attacks)
	rm -f /tmp/.clean /var/lock/.clean /var/run/.clean

	#
	# Make list of points to unmount in reverse order of their creation
	#

	exec 9<&0 </etc/mtab

	DIRS=""
	while read DEV MTPT FSTYPE OPTS REST
	do
		case "$MTPT" in
		  /|/proc|/dev|/dev/pts|/dev/shm|/proc/*|/sys|/lib/init/rw)
			continue
			;;
		  /var/run)
			if [ yes = "$RAMRUN" ] ; then
				continue
			fi
			;;
		  /var/lock)
			if [ yes = "$RAMLOCK" ] ; then
				continue
			fi
			;;
		esac
		case "$FSTYPE" in
		  nfs|nfs4|smbfs|ncp|ncpfs|cifs|coda|ocfs2|gfs)
			DIRS="$MTPT $DIRS"
			;;
		  proc|procfs|linprocfs|devfs|devpts|usbfs|usbdevfs|sysfs)
			DIRS="$MTPT $DIRS"
			;;
		esac
		case "$OPTS" in
		  _netdev|*,_netdev|_netdev,*|*,_netdev,*)
			DIRS="$MTPT $DIRS"
			;;
		esac
	done

	exec 0<&9 9<&-

	if [ "$DIRS" ]
	then
		[ "$VERBOSE" = no ] || log_action_begin_msg "Unmounting remote and non-toplevel virtual filesystems"
		umount $FLAGS $DIRS
		ES=$?
		[ "$VERBOSE" = no ] || log_action_end_msg $ES
	fi
}

case "$1" in
  start)
	# No-op
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop|"")
	do_stop
	;;
  *)
	echo "Usage: umountnfs.sh [start|stop]" >&2
	exit 3
	;;
esac

:
```

---

### Post by dmizer on 2009-06-12
Sorry, my mistake.

I need these two:
/etc/gdm/PostSession/Default
/etc/fstab

---

### Post by racecarpete on 2009-06-12
and here is the contents of /etc/fstab.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=dc16b410-df18-4027-b33b-6b478e709b99 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=fecd4896-127f-4bde-baf4-38f03c1d12e0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//192.168.1.254/music /media/Server-Music cifs credentials=/root/.smbcredentials,_netdev,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.254/photos /media/Server-Pictures cifs credentials=/root/.smbcredentials,_netdev,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.254/videos /media/Server-Videos cifs credentials=/root/.smbcredentials,_netdev,iocharset=utf8,file_mode=077,dir_mode=077 0 0
//192.168.1.254/sagetv /media/Server-SageTV cifs credentials=/root/.smbcredentials,_netdev,iocharset=utf8,file_mode=077,dir_mode=077 0 0
//192.168.1.254/software /media/Server-Software cifs credentials=/root/.smbcredentials,_netdev,iocharset=utf8,file_mode=077,dir_mode=077 0 0 
//192.168.1.254/users /media/Server-Users cifs credentials=/root/.smbcredentials,_netdev,iocharset=utf8,filed_mode=077,dir_mode=077 0 0
```

---

### Post by racecarpete on 2009-06-12
OK, here is the contents of /etc/gdm/PostSession/Default

```
#!/bin/sh
/etc/init.d/unmountnfs.sh

PATH="/usr/bin/X11:/usr/X11R6/bin:/opt/X11R6/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

exit 0

```

---

### Post by mfrerebeau on 2009-06-12
Script giving on this post resolve my problem perfectly!
Thanks a lot !

For information I'm on Ubuntu 8.10 Intrepid Ibex with some samba links on my server shared folders.

---

### Post by dmizer on 2009-06-12
racecarpete, is 192.168.1.254 a Linux samba server?

---

### Post by racecarpete on 2009-06-12
It's a windows server. I'm automounting the windows shares on my desktop.

---

### Post by G. Freeman on 2009-07-08
> **max.durden said:**
> Hi everybody, 
I'm posting a modification of a simple script originally coded by 'jferrando'
[http://www.ubuntuforums.org/showthread.php?t=171958&highlight=cifs](http://www.ubuntuforums.org/showthread.php?t=171958&highlight=cifs)
devoted to automatically umount cifs partitions in the shutdown and reboot sequence of Ubuntu (Dapper+). The main problem with the original script was that mount locations of cifs partitions had to be explicitly hardcoded in the script: I have written a simple routine which detects all mounted cifs-partition and umount them before proceeding with the other phases of the  shutdown/reboot sequences.

-----------------------------------------------------
Instructions are very simple:
uncompress archive and set 'chmod +x' on the mountcifs file   
sudo cp mountcifs /etc/init.d/ 

cd /etc/rc0.d
sudo ln -s /etc/init.d/mountcifs K02mountcifs

cd /etc/rc6.d
sudo ln -s /etc/init.d/mountcifs K02mountcifs

...that's all!
------------------------------------------------------
I've experienced problem in the shutdown of my laptop just after sharing cifs filesystems with other PCs in a VPN network... this script fixed the problem.... hope it will be useful for someone out there!

Happy Coding
Max

Thanks, works

---

### Post by michaelzap on 2009-07-08
Folks might consider trying the GVFS method as well:
[http://ubuntuforums.org/showpost.php?p=7453309&postcount=1](http://ubuntuforums.org/showpost.php?p=7453309&postcount=1)

It's working beautifully for me so far. The only issue that I've encountered is that programs run as root don't have access to these mounted shares. But all-in-all this seems like a much more graceful and less kludgey way to mount the same shares consistently.

---

### Post by jorb on 2009-07-21
The original link containing the script isn't working: [http://www.ubuntuforums.org/showthread.php?t=171958&highlight=cifs](http://www.ubuntuforums.org/showthread.php?t=171958&highlight=cifs)

am i doin it wrong?

---

### Post by mmorris on 2009-07-25
Hello, 

I followed pajarraco instructions and it did not work on Ubuntu 9.04.  However, if you place ```
/etc/init.d/umountnfs.sh
``` **before** the line ```
exit 0
``` it works.

Mike


> **pajarraco said:**
> Thanks kaiben, I used jaunty and this finally fix the error.

I put this line on my /etc/gdm/PostSession/Default file

```
/etc/init.d/umountnfs.sh
```

after the line ```
exit 0
```

and it fix.

---

### Post by DAKnn on 2009-08-07
**[COLOR=Red]do not need any scripts![/COLOR]** :D

just only small modifications:

[COLOR=Green]# cifs client workaround
modprobe cifs
echo 0 > /proc/fs/cifs/OplockEnabled[/COLOR][COLOR=Silver]


source: [http://blog.dhampir.no/content/cifs-vfs-no-response-for-cmd-n-mid](http://blog.dhampir.no/content/cifs-vfs-no-response-for-cmd-n-mid)[/COLOR]

---

### Post by schirpich on 2009-08-08
> **DAKnn said:**
> **[COLOR=Red]do not need any scripts![/COLOR]** :D

just only small modifications:

[COLOR=Green]# cifs client workaround
modprobe cifs
echo 0 > /proc/fs/cifs/OplockEnabled[/COLOR][COLOR=Silver]


source: [http://blog.dhampir.no/content/cifs-vfs-no-response-for-cmd-n-mid](http://blog.dhampir.no/content/cifs-vfs-no-response-for-cmd-n-mid)[/COLOR]

I think this is a different issue.  The one you linked seems to be for a file transfer issue.  The problem we are having here is when shutting down, network mounts are failing to unmount properly.

---

### Post by GeeF on 2009-08-18
Hi,

I just hacked a little script you can archive, as I think this bug will be in Ubuntu for at least 5 more years. It just automates, what a human would do ^^

```

#!/bin/bash
FIX=$(cat <<EOF
#!/bin/bash
/etc/init.d/umountnfs.sh
EOF
)
echo "$FIX" >> ./Default
more +2 /etc/gdm/PostSession/Default >> ./Default
sudo mv ./Default /etc/gdm/PostSession/Default
echo "done..."

```It's really just for you, when you want to archive this and reinstall quite often...etc...etc

---

### Post by pvdsar on 2009-09-04
I'm using Jaunty.

The solutions I've seen so far:
1) Adding an extra CIFS umount script (/etc/init.d/mountcifs) and linking to it as /etc/rc0.d/K02mountcifs and /etc/rc6.d/K02mountcifs
2) Moving the calls /etc/rc?.d/K15umountmfs to K02 or even K01
3) Adding /etc/init.d/umountnfs.sh to /etc/gdm/PostSession/Default 
4) The GVFS method: Adding a script to Gnome startup that mount the shares by using the gvfs-mount command.

Solution nr 1 puzzled me because the already available script /etc/init.d/umountnfs.sh is capable of umounting CIFS shares. Why then add another script that does the same?

Solution nr 2 doesn't work for me. Logs indicated that the network was already shutting down before the umount was performed.

Solution nr 3 came close: The umountnfs.sh call was done very early, but unfortunately, again looking at the logs, Gnome apparently was **at the same sime** shutting down the network. Seeing that other people have reported success with this solution I can only assume that wireless networks (my case) are shut down earlier than wired networks.

Solution nr 4: Haven't tried that, because I want the mount shares accessible for every one and mounted on any directory I desire.

So I had to come up with another solution that uses the gnome-power-cmd script. 
You may not like it, but it works for me:

[LIST]
[*]Add a button to the Gnome panel (or use a keyboard shortcut) that calls a script that calls "sudo /etc/init.d/umountnfs.sh" and "/usr/bin/gnome-power-cmd shutdown".
[*]Obviously you'll have to edit the sudoers file (sudo visudo): 
Add at the end of the file the line: "peter   ALL=NOPASSWD: UMOUNTNFS" (replace "peter" with your account name)
Earlier in the sudoers file add: "Cmnd_Alias     UMOUNTNFS = /etc/init.d/umountnfs.sh"
[/LIST]

The script I came up with:

#!/bin/bash
echo -n "Do you really want to shutdown? Press 'y' to confirm. "
read -n 1 answer
echo ""
if [[ "$answer" = "y" ]]
then
  echo "Goodbye!"
  sleep 1
  sudo /etc/init.d/umountnfs.sh >/tmp/do_shutdown.sh.log 2>&1
  /usr/bin/gnome-power-cmd shutdown
else
  echo "Phew! That was close!"
fi

---

### Post by Yougo on 2009-09-09
ok, i finally solved the CIFS VFS issue, by reordering the shutdown order to 

K01umountnfs.sh
K02gdm
K03usplash

in both /etc/rc0.d and /etc/rc6.d like it says way back in this thread

it shuts down like lightning now 8)

just one minor problem...
the shutdown splash won't kick in. 
i do prefer function over pretty, but the feeling i broke something nags me :(

anyone know how to fix this one?

---

### Post by derrick1985 on 2009-09-10
> **Yougo said:**
> ok, i finally solved the CIFS VFS issue, by reordering the shutdown order to 

K01umountnfs.sh
K02gdm
K03usplash

in both /etc/rc0.d and /etc/rc6.d like it says way back in this thread

it shuts down like lightning now 8)

just one minor problem...
the shutdown splash won't kick in. 
i do prefer function over pretty, but the feeling i broke something nags me :(

anyone know how to fix this one?
Can you please provide a more elaborate post on how you were able to solve this problem? I am having the same problem with my install, and it is really quite annoying.

---

### Post by dmizer on 2009-09-10
> **derrick1985 said:**
> Can you please provide a more elaborate post on how you were able to solve this problem? I am having the same problem with my install, and it is really quite annoying.

Have you tried any of the more recent solutions (something given in the last few pages). If not, please look under the troubleshooting section in the CIFS howto in my sig.

---

### Post by Yougo on 2009-09-11
> **derrick1985 said:**
> Can you please provide a more elaborate post on how you were able to solve this problem? I am having the same problem with my install, and it is really quite annoying.



i read about implementing new scripts, but as there seem to be scripts already available, just not in the right order, i chose to change that. the problem seems to be that NetworkManager -who manages the wireless connection- shuts down before network drives are unmounted. this order can be changed:

i'm using Ubuntu 9.04, and will explain what i did, using GUI. (more lengthy, but could help those who like some visual confirmation) if you want to do this via command-line, you can look back up in this thread

- i pressed ALT-F2, and typed "gksu nautilus" to run Nautilus as root. this is needed to get read/write acces to files and folders mentioned below.
- i browsed to /etc

from here i could go two ways:

**1: add a command in the file /etc/gdm/PostSession/Default:**

- browse to /etc/gdm/PostSession. there should be a file called Default. double click it, and press the button that says Display.
the file is opened in Gedit

now add the command like below:
```

#!/bin/sh
[COLOR="Red"]/etc/init.d/umountnfs.sh
exit 0[/COLOR]

PATH="/usr/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

exit 0
```
now save the file and close Gedit

from what i understand, this will make GDM run the unmount script right after you choose to log out. can't get much sooner than that. good thing about this method is that it happens whenever you log out, either for simply ending your session of Gnome, for rebooting or for shutdown.
bad thing is that it puts a command where it doesn't really belong, and only applies to your Gnome session.

proceed to "Next step: testing"

**Method 2: change the order of tasks during shutdown and reboot**
everything that needs to happen for your computer to shut down or reboot is collected in two folders: /etc/rc0.d (for shutdown) and /etc/rc6.d (for reboot) 
the only real difference between these two folders is the last command, which says what the computer must do in the end, reset or power down.

all the files in these folders are symbolic links that point towards scrips in the folder /etc/init.d They are numbered from K01 up and from S01 up. these numbers determine the order. what i did was:

- browse to /etc/init.d and select the file umountnfs.sh

- choose Edit>Make Link. a symbolic link is made.
 
- move that link to /etc/rc6.d 

- rename the link to K01umountnfs.sh
this will make the unmount script the first thing your computer does during reboot.

- rename K01gdm to K02gdm

- rename K02usplash to K03usplash

the unmount script is also seen as S31umountnfs.sh. as S15wpa-ifupdown (shutdown wired network)happens before that (S15 is lower than S31) this could be a problem too.

- rename K31umountnfs.sh to K14umountnfs.sh

so now etc/rc6.d should contain: 
K01umountnfs.sh
K02gdm
K03usplash
...
S14umountnfs.sh
S15wpa-ifupdown

note that i only changed things in /etc/rc6.d, not in rc0.d. this means i only changed things for reboot, not for shutdown. as the folders are the same upto the last command, you can look in rc0.d to see how things were before.

proceed to "Next step: testing"

**Next step: testing**

restart your computer to see the effect. no real worries, the worst that could happen is a hangup. in that case a hard reset should get you going :)

if Method 2 doesn't solve things, or makes matters worse, you can look in rc0.d for how to put things back.
if succes, you can apply the same changes in rc0.d to change your shutdown order aswell

for me either method seemed to work for the CIFS VFS error.
HOWEVER
this is where my new problem rises: 
**this tinkering seems to have borked my usplash on both shutdown and reboot :(**
 i tried putting everything back in place, but it stays gone! i do see a slight flicker right before powerdown, like the computer
runs all the scripts, and after that starts usplash for a split second, and shuts down :confused:

---

### Post by AlexanderDGreat on 2009-09-11
Adding /etc/init.d/unmountnfs.sh after #!/bin/sh in /etc/gdm/PostSession/Default worked for me.

What if I don't not use gdm? Will this still work?

---

### Post by Yougo on 2009-09-11
looking at the path, i think /etc/gdm/PostSession/Default" belongs to gdm specific. like i mentioned, that's a downside of inserting a command where it doesn't really belong. 

i'm not near a *buntu pc right now, so i can't check.

try looking for /etc/kdm/PostSession/Default or /etc/xfce/PostSession/Default

just a hunch, maybe things are that easy...

---

### Post by dmizer on 2009-09-11
> **AlexanderDGreat said:**
> Adding /etc/init.d/unmountnfs.sh after #!/bin/sh in /etc/gdm/PostSession/Default worked for me.

What if I don't not use gdm? Will this still work?

Both Ubuntu and Xubuntu use gdm. Kubuntu uses a different dm, but it's really easy to do in Kubuntu: [http://ubuntuforums.org/showpost.php?p=7365942&postcount=934](http://ubuntuforums.org/showpost.php?p=7365942&postcount=934)

If you're using anything else, you're not likely to encounter this problem.

---

### Post by Yougo on 2009-09-11
so... any idea wat went wrong with my usplash, and how to fix it?
help would be appreciated, as i am at a loss.

i put everything back to the way it was before, so now i do get the CIFS error again (not a bad thing, at least i know how to fix this now), but usplash didn't come back to me.

---

### Post by dmizer on 2009-09-11
> **Yougo said:**
> so... any idea wat went wrong with my usplash, and how to fix it?
help would be appreciated, as i am at a loss.

i put everything back to the way it was before, so now i do get the CIFS error again (not a bad thing, at least i know how to fix this now), but usplash didn't come back to me.

"exit 0" means "end of program", so anything following "exit 0" is ignored.

```
#!/bin/sh
/etc/init.d/umountnfs.sh
[COLOR="Red"]**exit 0**[/COLOR]

PATH="/usr/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

exit 0
```
The script terminates after reading the red highlighted line. Remove that line, and your usplash should return.

---

### Post by Yougo on 2009-09-11
between my last post and now, that's what i figured out aswell. i misread a post that said to put in Exit 0. ...on closer look it said to put the unmount script before the existing exit 0. (note to self: don't read long threads late at night)

anyways, no joy.

as a last resort i replaced the K02usplash symlink with a freshly created one, and bingo usplash lives!
i'm quite sure i didn't change the symlink's properties... guess it went stale from all the renaming or something :confused:

---

### Post by anibalojeda on 2009-10-11
Someone an idea on how to umount cifs on karmic?
rc0 & rc6 has changed on karmic.

the is no usplash & everything is starting on K20. I have tried making the link K01 as for jauntyu  but this doest work.

This cifs umount think is becoming anoying on ubuntu. Debianished distros are the only linux distro having this cifs issue.

any tip on karmic?

---

### Post by dmizer on 2009-10-11
> **anibalojeda said:**
> Someone an idea on how to umount cifs on karmic?
rc0 & rc6 has changed on karmic.

the is no usplash & everything is starting on K20. I have tried making the link K01 as for jauntyu  but this doest work.

This cifs umount think is becoming anoying on ubuntu. Debianished distros are the only linux distro having this cifs issue.

any tip on karmic?

Is there no /etc/gdm/PostSession/Default file? That's what's been working most consistently.

---

### Post by anibalojeda on 2009-10-14
> **dmizer said:**
> Is there no /etc/gdm/PostSession/Default file? That's what's been working most consistently.

Not working either as mounting the shares on boot from fstab.

---

### Post by dmizer on 2009-10-14
> **anibalojeda said:**
> Not working either as mounting the shares on boot from fstab.

Are you using Gnome? What's your current mount line in /etc/fstab?

---

### Post by anibalojeda on 2009-10-14
> **dmizer said:**
> Are you using Gnome? What's your current mount line in /etc/fstab?

Using gnome. I've following a karmic bug related to this.

The bus was fixed yesterday & is still not working for me:
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/447649?comments=all](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/447649?comments=all)

A sample of my fstab:
```
\\ipaddress\dir1 /home/user/dir1 cifs credentials=/passwdfile,rw,iocharset=utf8,user,uid=1000,gid=1000,file_mode=0770,dir_mode=0770 0 0
\\ipaddress\dir2 /home/user/dir2 cifs credentials=/passwdfile,rw,iocharset=utf8,user,uid=1000,gid=1000,file_mode=0770,dir_mode=0770 0 0
```

This has been working on the last 2 ubuntu releases. 

CIFS shares are always tricky on ubuntu ;-)

I will make a new bug report tonight as requested on bug 447649

---

### Post by dmizer on 2009-10-14
Okay, and if you edit your /etc/gdm/PostSession/Default file so it looks like the following one, you still have the problem?

```
#!/bin/sh
[COLOR="Red"]/etc/init.d/umountnfs.sh[/COLOR]

PATH="/usr/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

exit 0
```

Sorry, I don't want to seem condescending, I'm just making sure all my bases are covered so I can be prepared for 9.10 when it's released.

---

### Post by anibalojeda on 2009-10-19
> **dmizer said:**
> Okay, and if you edit your /etc/gdm/PostSession/Default file so it looks like the following one, you still have the problem?

```
#!/bin/sh
[COLOR="Red"]/etc/init.d/umountnfs.sh[/COLOR]

PATH="/usr/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

exit 0
```

Sorry, I don't want to seem condescending, I'm just making sure all my bases are covered so I can be prepared for 9.10 when it's released.


The mounting on boot issue is a bug on Karmic, see [https://bugs.launchpad.net/bugs/451432](https://bugs.launchpad.net/bugs/451432)

I wil check what you just send for the shuting down, since ive been able to workaround the issue (see bug i reported)

---

### Post by dmizer on 2009-10-19
> **anibalojeda said:**
> The mounting on boot issue is a bug on Karmic, see [https://bugs.launchpad.net/bugs/451432](https://bugs.launchpad.net/bugs/451432)

I wil check what you just send for the shuting down, since ive been able to workaround the issue (see bug i reported)

This particular thread has nothing to do with problems mounting during boot. Only problems with mounting during shutdown.

---

### Post by anibalojeda on 2009-10-19
> **dmizer said:**
> This particular thread has nothing to do with problems mounting during boot. Only problems with mounting during shutdown.

Yes it does, the original name was "cifs share not mounting on boot"
Had to do with slashes \\

---

### Post by dmizer on 2009-10-19
> **anibalojeda said:**
> Yes it does, the original name was "cifs share not mounting on boot"
Had to do with slashes \\

The edit history of this thread shows nothing about a title change, and your first post in this thread mentions nothing about mounting, only unmounting:
> **anibalojeda said:**
> Someone an idea on how to [COLOR="Red"]umount[/COLOR] cifs on karmic?
I was only trying to answer your question regarding the unmount problem. My apologies if I misunderstood.

If you're having trouble with the mount working at boot, all you need to do is add a mount command to /etc/rc.local. That usually fixes the problem for most people. The "not mounting at boot" problem occurs as a result of networking not being available when the machine is booting. This happened because gnome moved to network-manager as their networking tool. network-manager only works in userspace unless it's configured otherwise.

---

### Post by anibalojeda on 2009-10-20
> **dmizer said:**
> The edit history of this thread shows nothing about a title change, and your first post in this thread mentions nothing about mounting, only unmounting:

I was only trying to answer your question regarding the unmount problem. My apologies if I misunderstood.

If you're having trouble with the mount working at boot, all you need to do is add a mount command to /etc/rc.local. That usually fixes the problem for most people. The "not mounting at boot" problem occurs as a result of networking not being available when the machine is booting. This happened because gnome moved to network-manager as their networking tool. network-manager only works in userspace unless it's configured otherwise.


No prob, dont have to apologies ;-) the name changed of the bug report. I reported this bug ;-)
Getting back again where we started. The last option you sent me to umount cifs share on de gdm config works perfect on Karmic, only with 1 cifs share mounted. Now having 4 shares at the time it hangs again. I will take a look tonight & comeback. We will get this solved.

---

### Post by Levomatic on 2009-10-20
worked perfectly for me (CrunchEEE CrunchBang based on Ubuntu Jaunty)
thanks very much Max!

---

### Post by Maddog Battie on 2009-11-02
Sorry to bring this thread up again but I'm still having problems here after trying various of the methods suggested.

I'm running 9.10 on a laptop and I'm connecting via wireless to a NAS box. I'm mounting a couple of shares off the NAS box using fstab as below:

```
//myxerver/colin /home/colin-backup smbfs iocharset=utf8,credentials=xxx,uid=1000,gid=1000 0 0
//myxerver/work /home/work smbfs iocharset=utf8,credentials=xxx,uid=1000,gid=1000 0 0

```

This works great and I can remove these easily using:
sudo /etc/init.d/umountnfs.sh

So I know I have a script that will successfully remove the shares and if I manually run this, I can shutdown the computer in seconds.

So I went to /etc/rc0 and rc6 and renamed the umount script as follows:
lrwxrwxrwx 1 root root 22 2009-11-02 18:00 K01umountnfs.sh -> ../init.d/umountnfs.sh

But it still locks up when trying to shutdown.

I've tried putting the above line in the /etc/gdm/PostSession/Default file but this causes the window manager to lock when shutting down and it never goes to the black screen. Manually running the script works fine though...

Can anybody help?

Cheers,

MdB

---

### Post by anibalojeda on 2009-11-02
> **Maddog Battie said:**
> Sorry to bring this thread up again but I'm still having problems here after trying various of the methods suggested.

I'm running 9.10 on a laptop and I'm connecting via wireless to a NAS box. I'm mounting a couple of shares off the NAS box using fstab as below:

```
//myxerver/colin /home/colin-backup smbfs iocharset=utf8,credentials=xxx,uid=1000,gid=1000 0 0
//myxerver/work /home/work smbfs iocharset=utf8,credentials=xxx,uid=1000,gid=1000 0 0

```

This works great and I can remove these easily using:
sudo /etc/init.d/umountnfs.sh

So I know I have a script that will successfully remove the shares and if I manually run this, I can shutdown the computer in seconds.

So I went to /etc/rc0 and rc6 and renamed the umount script as follows:
lrwxrwxrwx 1 root root 22 2009-11-02 18:00 K01umountnfs.sh -> ../init.d/umountnfs.sh

But it still locks up when trying to shutdown.

I've tried putting the above line in the /etc/gdm/PostSession/Default file but this causes the window manager to lock when shutting down and it never goes to the black screen. Manually running the script works fine though...

Can anybody help?

Cheers,

MdB

Same here.. this issue is keeping me for upgrade my main desktop. CIFS share became a pain in the as.. on ubuntu.

I try almost everything but it will hang on shutdown, no matter what.

rc0 and rc6 has changed a little bit on 9.10 & dont understand why such a change inside a version. As i dont understand why the ubuntu team JUST doest come with a proper fix for this whole CIFS shutdown thing, we are making all kind of fixs but nothing properly done. This has been an ages discussion on the Debian list..

is time to fix this without all kind of manual tricks.

On every other distro cifs get umounted without any manual trick.

---

### Post by Maddog Battie on 2009-11-02
As a temp solution I've added a link to sudo /etc/init.d/umountnfs.sh next to the shutdown button so I can click on that before hitting shutdown. Very much a cludge but it seems to work.

If someone can come up with a better solution for 9.10 then please, please let me/us know.

---

### Post by Alabamaschalk on 2009-11-16
Hi!
 
I put that script 

#!/bin/bash
umount.cifs /path/to/share
 
in /etc/rc0.d 
 
made it executable and named it K01umount.
 
Now I did not got the error so far.
 
Hope that helps somebody.

---

### Post by diana.artemis on 2009-11-17
> **dmizer said:**
> Okay, and if you edit your /etc/gdm/PostSession/Default file so it looks like the following one, you still have the problem?

```
#!/bin/sh
[COLOR="Red"]/etc/init.d/umountnfs.sh[/COLOR]

PATH="/usr/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

exit 0
```

Sorry, I don't want to seem condescending, I'm just making sure all my bases are covered so I can be prepared for 9.10 when it's released.

I've just done a clean install of Karmic on a Dell Inspiron 6400 laptop, and I mount one CIFS partition that's on a Maxtor network drive (as well as five NFS partitions on a ReadyNAS).  None of the code you give above appears in the Karmic version of /etc/gdm/PostSession/Default.  Here's what's in the Karmic version:

```
#!/bin/sh

exit 0
```
Inserting /etc/init.d/umountnfs.sh there did not remove the CIFS error problem for me.  For now, I'm using the same cludge as Maddog Battie: "As a temp solution I've added a link to sudo /etc/init.d/umountnfs.sh next to the shutdown button so I can click on that before hitting shutdown."

This appears to deal with the CIFS error.  (There's still some other glitch in the shutdown, but this looks like it may be to do with the encrypted /home partition.  Anyway, it's another issue, I think.)

(The long-running blame swapping between the Debian developers and the NM developers about this mess shows up the worst side of free software:  damn the users, what matters is which developers are to blame and should therefore back down.  Adolescents!  I just wish the Ubuntu devs would sidestep the silliness, and hack this for us.)

---

### Post by dmizer on 2009-11-17
> **diana.artemis said:**
> Inserting /etc/init.d/umountnfs.sh there did not remove the CIFS error problem for me.

Well, that's no good.

Did you try the fix posted by Alabamaschalk in post [184](http://ubuntuforums.org/showpost.php?p=8331451&postcount=184)?

---

### Post by diana.artemis on 2009-11-17
> **dmizer said:**
> ...Did you try the fix posted by Alabamaschalk in post [184](http://ubuntuforums.org/showpost.php?p=8331451&postcount=184)?I've just tried it.  I don't get a CIFS error;  but the shutdown throws me out to tty1, hangs for a while with a flashing cursor, and then runs through the text-based shutdown to the system halt.

What with the interminable 'hang', it takes about as long as waiting for the CIFS error to time out.  So not a success, I fear. 

I can't see anything in the logs (though I admit I don't know much about this, and might not notice even if the problem were logged!).  I must say, however, that Karmic does not seem to shut down gracefully.  Even without a CIFS share mounted, the shutdown sometimes pops out to a text screen, with obscure messages such as

init: statd main process ended, respawning.

(There are a couple of recent bug reports about this.)

Anyway, as I don't really make that much use of the CIFS share any more, I'm tempted to cut my losses, and not mount it on this laptop (until this whole issue gets fixed in Lucid???  Don't hold your breath.)

Thanks for troubling to reply, and so fast, too.  You've really been a great help to everyone in this thread, and I benefited greatly from your work on Jaunty and earlier releases.  Many thanks!

[edit1:  Just realised that statd is to do with NFS, and I guess the issue may be another symptom of NM closing the network before the shares are unmounted.  Rats!]

[edit2:  Since abandoning CIFS, and just using NFS for shares on Raid5 4Tb NAS I've had no further shut-down problems.  Simples!]

---

### Post by Maddog Battie on 2009-11-24
Ok, I've managed to come up with a better work around.

Instead of mounting the directory using fstab, I've mounted it using gvfs-mount at the start of the script that does my back-up. When I shut down the laptop, gvfs mounts are unmounted before the wireless is switched off and everything exits cleanly.

Stage 1: Manually setup a network share. (File browser: File->Connect to server)

Stage 2: Run gvfs-mount -l to see what name is used.

Stage 3: From then on run gvfs-mount share_name to mount and gvfs-mount -u share_name to unmount.

I hope that is useful to somebody.

---

### Post by Alabamaschalk on 2009-11-29
Dear all,
I have to admit that the fix I posted earlier does not work every time like other users already experienced.
I found out that the shutdown works perfectly with the fix when I do not run Firefox in the session.
Wheb I run Firefox the shutdown hangs again.
May be some of you folks can use this information.

regards

---

### Post by kaiben on 2009-12-04
Oh no! I upgraded yesterday to karmic and this problem again! Will the Ubuntu team never fix this?!

Has anybody logged a bug already?

---

### Post by diana.artemis on 2009-12-04
> **kaiben said:**
> Oh no! I upgraded yesterday to karmic and this problem again! Will the Ubuntu team never fix this?!

Has anybody logged a bug already?

This is a long-standing Debian issue, with internal arguments about whose 'fault' it is paralysing any action to fix it.  See, for example, 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=431966](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=431966)

or

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=481252](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=481252)

Look at the dates;  and if you have the time and patience to investigate a bit more you'll find it's been going on for years longer.  (Free software at its worst.)

---

### Post by ubradford on 2009-12-06
I found a fix for the CIFS VFS error issue during shutdown & reboot.  It works on Karmic while using wireless. I posted it here:
[http://ubuntuforums.org/showthread.php?p=8449027#post8449027](http://ubuntuforums.org/showthread.php?p=8449027#post8449027)

---

### Post by Alabamaschalk on 2009-12-06
It really works great now!:D
 
Thanks Dude!

---

### Post by akhilbehl on 2010-01-18
Hey All,

I have had this problem too. I am working presently on Karmic and access network from wireless and wired connections at different times.

I tried three different solutions for this problem:
1. The one given here: [http://ubuntuforums.org/showthread.php?t=1347340](http://ubuntuforums.org/showthread.php?t=1347340)
2. The one given by dmizer here: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
3. And the one given here: [http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)

However none of the solutions fixed my problem. I read in one of the posts that the real problem was to run the /etc/init.d/umountnfs.sh before the system is killed.

This gave me the simple idea, since I always have a terminal open, I wrote this bash function:

function bringdown()
    {
        sudo /etc/init.d/umountnfs.sh && sudo shutdown -h now
    }

This simply solves my problem.

However I was thinking of a more generic solution. I have never tried scripting. I was wondering if there can be a more elegant and generic solution to this. I have an idea, someone please let me know if this is feasible.

We  can create a script which runs this function `bringdown' as given above (preferable without the need for a sudo password prompt [perhaps using a credentials file or using editing visudo]) and put this in the $PATH of each user, so that one can simply call the run dialog and bring the system down.

Please let me know if writing such a script is possible and easy. I am willing to learn and do homework if any is needed. :)

Thanks for reading the long post. Hoping for some replies.

---

### Post by zcorpion on 2010-01-27
> **Maddog Battie said:**
> As a temp solution I've added a link to sudo /etc/init.d/umountnfs.sh next to the shutdown button so I can click on that before hitting shutdown. Very much a cludge but it seems to work.

If someone can come up with a better solution for 9.10 then please, please let me/us know.




Im a new to linux, and ubutnu are new for me. Im a former windows user.
So culd you give me a step by step howto make a link next to the shutdown button??

---

### Post by microscott on 2010-02-27
After spending a day working out how create fixed icons on the desktop that mount shares as and when needed i discovered this same problem when shutting down, it's just taken me another day to find a solution.

I can't believe the complexity of the solutions given in this thread, and not one would work on 'Kinky' (9.10). This has obviously vexed a lot of people so I feel bound to share this with you all.

[http://archive.lug.boulder.co.us/Week-of-Mon-20001030/006266.html](http://archive.lug.boulder.co.us/Week-of-Mon-20001030/006266.html)

add a line in /etc/gdm/PostSession/Defaults

```
umount -a -t cifs
```

Simples!

you dont even need sudo.

I hope this helps some people.

And in case you were wondering about my initial project here it is:

```

#!/bin/bash

# author: Scott Mills - 27th Feb 2010

####################################################################################

# reasons for this script:
# 1. mounting at boot increases start-up time
# 2. network folders not always available at boot
# 3. unable to play video & audio from smb share
# 4. desktop launchers for fstab mounted volumes tend to appear in random positions
# 5. allows for custom geometry of browser window
# 6. browsing to smb shares creates extra items in nautilus tree
# 7. nautilus folder icon can be customised

# requirements
# 1. create mount exception in sudoers with visudo
# 2. mount-point folders must exist (in /media)
# 3. share name must be same as folder name
# 4. credentials file should exist (smb)
# 5. use config editor to turn off 'volumes visible' (optional)

# automatic umount on logout (prevents hang at shutdown)
# 1. open /etc/gdm/PostSession/Default as root
# 2. add the line > umount -a -t cifs

# usage
# mnt <share name> [--geometry=<width>x<height>+<left>+<top>]

# example
# create custom application launcher
# enter as command ./mnt tunes --geometry=1018x593+0+56 (assuming in ~)

# result
# mounts share 'tunes' in /media/tunes
# opens large browser window in middle of screen (1024x768) in /media/tunes

####################################################################################

# check for no args
if [ "$1" = "" ]
then
    echo "No value given"
    exit
fi

# is volume in the list of mounted volumes
a=`sudo mount | grep $1`

if [ "$a" == "" ]
then    # no?, then mount
    # seperate case for windows needed
    if [ $1 == "windows" ]
    then
        sudo mount -t ntfs-3g /dev/sda1 /media/$1 \
        -o rw,user,locale=en_GB.UTF-8
    else
            sudo mount -t cifs //192.168.0.253/$1 /media/$1 \
        -o user,rw,credentials=smb 
    fi

    # check again (see if mounted)
    a=`sudo mount | grep $1`
    # if entry for $1
    if [ "$a" != "" ]
    then
        echo $1" successfully mounted."
        # open in file manager
        nautilus /media/$1 $2
    else
        zenity --info --title "Mount Volume" --text "Failed to mount "$1"."
    fi
else    # inform
    echo $1" already mounted."
    # open in file manager
    nautilus /media/$1 $2
fi

```

---

### Post by microscott on 2010-02-27
Hmm...

it also appears to need this:

ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh

and a '-f'  for the umount helps speed things up

---

### Post by microscott on 2010-02-27
I give up!

A couple of reboots and it's as it was.

easier to just do umount -a in terminal.

:frown:

---

### Post by 5ulo on 2010-05-12
I got an amateur solution... two launchers :) It's not the best solution, but it works for me at 100%
[http://howto.blbosti.com/2010/05/umount-cifs-problem-reboot-and-shutdown/](http://howto.blbosti.com/2010/05/umount-cifs-problem-reboot-and-shutdown/)

---

### Post by Odihmv on 2010-06-03
Just perfect! Thanks!


> **max.durden said:**
> Hi everybody, 
I'm posting a modification of a simple script originally coded by 'jferrando'
[http://www.ubuntuforums.org/showthread.php?t=171958&highlight=cifs](http://www.ubuntuforums.org/showthread.php?t=171958&highlight=cifs)
devoted to automatically umount cifs partitions in the shutdown and reboot sequence of Ubuntu (Dapper+). The main problem with the original script was that mount locations of cifs partitions had to be explicitly hardcoded in the script: I have written a simple routine which detects all mounted cifs-partition and umount them before proceeding with the other phases of the  shutdown/reboot sequences.

-----------------------------------------------------
Instructions are very simple:
uncompress archive and set 'chmod +x' on the mountcifs file   
sudo cp mountcifs /etc/init.d/ 

cd /etc/rc0.d
sudo ln -s /etc/init.d/mountcifs K02mountcifs

cd /etc/rc6.d
sudo ln -s /etc/init.d/mountcifs K02mountcifs

...that's all!
------------------------------------------------------
I've experienced problem in the shutdown of my laptop just after sharing cifs filesystems with other PCs in a VPN network... this script fixed the problem.... hope it will be useful for someone out there!

Happy Coding
Max

---

### Post by imota on 2010-08-26
I realize this is an older topic but I have tried every single suggestion on here to no avail, on Ubuntu Lucid 10.04 x64 desktop.

I found a solution to my problem, after 3 days of debugging and searching the net so I thought I'd share it here.

I have the combination of a M$ Server08 with authenticated shares that I'd like to mount on startup (all entries on my fstab), which worked great. The problem was at shutdown...

My /etc/fstab looks like:

```
#WINDOWS SERVER SHARES
//192.0.0.212/user	/media/user cifs credentials=/etc/samba/.smbcredentials,file_mode=0777,dir_mode=0777 0 0
//192.0.0.212/ITEngShare	/media/ITEngShare cifs credentials=/etc/samba/.smbcredentials,file_mode=0777,dir_mode=0777 0 0
//192.0.0.212/EngineerShare	/media/EngineerShare cifs credentials=/etc/samba/.smbcredentials,file_mode=0777,dir_mode=0777 0 0
//192.0.0.212/ITEngShare/ScannedDocs	/media/ScannedDocs cifs credentials=/etc/samba/.smbcredentials,file_mode=0777,dir_mode=0777 0 0
```

I was getting the CIFS VFS cmd 50 errors on shutdown or reboot. I tried:

[LIST]
[*] Using Max Durden's script at the beginning of the post
[*] Changing the shutdown order of my scripts (rc0.d and rc6.d)
[*] Adding the umount -a command to my /etc/gdm/PostSession/Default
[*] Changing my umountfs.sh to a number smaller than my wpa-ifupdown
[*] Using various different scripts found in various other sources for this problem
[/LIST]

I also was using network-manager for gnome, which a lot of people mentioned as being one of the culprits for the system hang during shutdown and reboot.

Finally I installed wicd and removed network manager; That solved the shutdown issue (although I am not convinced that my drives are being properly unmounted due to the sheer speed of shutdown... Someone might be able to shed light on this one?), but it created a new problem: Nothing was getting mounted at startup, due to the fact that wicd will not connect to the network until well into the GDM session has started.

So the solution was simple: Add the network information manually to /etc/network/interfaces. That causes ifup to pick it up during bootup before fstab is read, hence giving me consistent results.

Just add your interface to the file /etc/network/interfaces. In my case I added to the bottom of the file (static IP):

```
auto eth0
iface eth0 inet static
address 192.0.0.208
netmask 255.255.255.0
gateway 192.0.0.253
dns-nameservers 192.0.0.212
```

I hope this helps others that are frustrated by this seemingly  overlooked issue with Ubuntu.

Edit: 

I forgot to add my rc0.d and rc6.d as they stand today:

```
lrwxrwxrwx 1 root root  19 2010-08-25 11:49 K20mono-xsp2 -> ../init.d/mono-xsp2
lrwxrwxrwx 1 root root  17 2010-08-25 09:22 K20postfix -> ../init.d/postfix
lrwxrwxrwx 1 root root  14 2010-08-26 13:40 K20wicd -> ../init.d/wicd
lrwxrwxrwx 1 root root  19 2010-08-23 11:26 K74bluetooth -> ../init.d/bluetooth
-rw-r--r-- 1 root root 353 2009-09-07 14:58 README
lrwxrwxrwx 1 root root  29 2010-08-23 11:26 S10unattended-upgrades -> ../init.d/unattended-upgrades
lrwxrwxrwx 1 root root  22 2010-08-23 11:26 S15wpa-ifupdown -> ../init.d/wpa-ifupdown
lrwxrwxrwx 1 root root  18 2010-08-23 11:26 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx 1 root root  17 2010-08-23 11:26 S30urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root  20 2010-08-23 11:26 S35networking -> ../init.d/networking
lrwxrwxrwx 1 root root  22 2010-08-26 11:32 S40umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx 1 root root  20 2010-08-23 11:26 S60umountroot -> ../init.d/umountroot
lrwxrwxrwx 1 root root  14 2010-08-23 11:26 S90halt -> ../init.d/halt
```

---

### Post by guimenez on 2010-10-07
Unfortunately here doesn't work :(

i've made all the process you mentioned but it happens the same. sometimes i can logoff
and sometimes not :(

i'm using pam_mount.conf.xml to mount shares because i'm using the username and password from my server.
My machine as for about 60 users and i don't want to use credentials

i don't know what can i do

can you help me?

using: Ubuntu 10.04 LTS

---

### Post by edubidu on 2010-10-28
great!
I had the following msg with ubuntu 10.04 Lucid Lynx on shutdown:

(the ubuntu ..... screen appeared and hanged, message appeared when pressing [Esc])
[HTML]Deconfiguring network interfaces  
[/HTML]Your script works!!

thanks!

---

### Post by deckoff on 2011-05-01
No luck here after upgrading to 11.04. Any recent cure??

---

### Post by peterhorlings on 2011-10-02
I'm using 11.04 and still had this OLD problem with a FreeNAS SMB/CIFS share. Both scripts mentioned at the beginning of the thread worked for me. Currently I'm using the second script which has been added on page 2 of this thread.
A big thank you to max.durden and sander marechal.

---

### Post by bodo bootlin on 2011-11-05
Great solution! Obviously still or again necessary in Kubuntu 11.10. Works fine for me. Since I needed quite some time to find this post I only reply to add some of the keywords I was initially using.

Kubuntu shutdown and restart problem samba cifs share over WLAN

I am not a geek so I may be allowed to wonder why the order of shutting down things has not been generally changed since the beginning of this thread.

Regards

---

### Post by zcacogp on 2011-12-15
Many thanks, as expressed before - this script worked well for me too. Thank you max.durden and sander marechal. 

Have to say that I echo Bodo Bootlin's comments; this seems to have been an issue for some time, and hasn't been fixed in the standard distro. 


Oli.

---

