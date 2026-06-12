---
title: "32-Bit Chroot How-To"
date: 2005-04-07
forum: Tutorials
---

### Post by Crad on 2005-04-07
Most of this comes from [http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap) but I wanted to put together a cleaned up version that worked for me here  (There are typos and inaccuracies on the wiki page).

> 
**Step 1:**

[list]
[*]sudo apt-get install dchroot debootstrap
 [*]sudo mkdir /chroot/
 [*]sudo gedit /etc/dchroot.conf
 [list]
[*]Add this line: hoary     /chroot
  [/list]
 [*]sudo debootstrap --arch i386 hoary /chroot/ [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
 [*]sudo chroot /chroot/
 [*]dpkg-reconfigure locales
[/list]
**Step 2:**
In another terminal window (or by existing chroot):
[list]
[*]sudo gedit /chroot/etc/apt/sources.list
[*]Add the following lines:
[list]
[*]deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
[*]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse
[/list]
[/list]
*(We do this step because gedit has yet to be installed in the chroot environment)*

**Step 3:**
In your chrooted environment (chroot /chroot):
[list]
[*]apt-get update ; apt-get upgrade
[/list]
**Step 4:**
In another terminal window (or by existing chroot):
[list]
[*]sudo cp /etc/passwd /chroot/etc/
[*]sudo cp /etc/shadow /chroot/etc/
[*]sudo cp /etc/group /chroot/etc/
[*]sudo cp /etc/sudoers /chroot/etc/
[*]sudo cp /etc/hosts /chroot/etc/
[*]sudo gedit /etc/fstab 
[*]Add the following lines:
[list]
[*]/home           /chroot/home        none    bind            0       0
[*]/tmp            /chroot/tmp         none    bind            0       0
[*]/dev            /chroot/dev         none    bind            0       0
[*]/proc           /chroot/proc        proc    defaults        0       0
[*]/media/cdrom0    /chroot/media/cdrom0 none    bind            0       0
[*]/usr/share/fonts /chroot/usr/share/fonts none    bind            0       0
[/list]
[*]sudo mkdir /chroot/media/cdrom0
[*]sudo mount -a
[*]sudo gedit /usr/local/bin/do_dchroot
[*]Add the following:
[list]
[*] #!/bin/sh
[*] /usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` $*"
[/list]
[*]sudo chmod 755 /usr/local/bin/do_dchroot
[/list]
**Step 5:**
In a new terminal:
[list]
[*]dchroot -d
[*]sudo apt-get install synaptic
[*]sudo ln -s /usr/sbin/synaptic /usr/sbin/synaptic32
[*]exit
[*]sudo ln -s /usr/local/bin/do_dchroot /usr/local/bin/synaptic32
[*]sudo synaptic32
[/list]


At this point you should have a 32 bit environment setup with synaptic setup.  When you run synaptic32 from your main environment it will chroot execute it and all installations will be made to your 32 bit environment.  If you want to be able to easily launch 32 bit chroot apps from your 64 bit environment symlink the app name to /usr/local/bin/do_dchroot.  If you're using this as desktop system you'll probably want to use synaptic to install x, gnome, ubuntu specific themes, etc.

Please let me know of any errors, enhancements, or corrections :)

---

### Post by Crad on 2005-04-07
To get Firefox setup with Flash I did the following:

[list]
[*]Ran sudo synaptic32 (as noted in the above thread
[*]Installed mozilla-firefox
[*]dchroot -d
[*]sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
[*]sudo ln -s /usr/bin/firefox /usr/bin/firefox32
[*]exit
[*]sudo ln -s /usr/local/bin/do_dchroot /usr/local/bin/firefox32
[*]Made sure all instances of firefox are closed (you can not run both 32 and 64 bit firefoxes at the same time afaik... it just spawns a new 64 bit thread when you launch the old.
[*]firefox32
[*]Visited a site with flash on it and ran the automated firefox flash install.
[/list]

As of right now sound is not working.  If I figure out how to get the sound stuff working across the chroot, I'll post it here.

---

### Post by wmcbrine on 2005-04-07
To get sound working, you need to **mount --bind /dev /chroot/dev** (or the equivalent fstab line).

In my case, I also had to add my username to the right group to have permission to write to /dev/dsp; but that was because I was using my old Mandrake system as the chroot, and it used a different number for the audio group. For an Ubuntu chroot, you should be set already.

In another thread, someone said it was also necessary to **modprobe ioctl32** before starting the chroot. I've not found that to be the case here, but perhaps that's because my chroot is using OSS. (?)

---

### Post by wmcbrine on 2005-04-07
P.S.:

> 
sudo chmod 777 /usr/local/bin/do_dchroot

Should be 755 -- there's no reason for this script to be world-writable.

---

### Post by Crad on 2005-04-07
[QUOTE=wmcbrine]P.S.:


Should be 755 -- there's no reason for this script to be world-writable.[/QUOTE]

Fixed

---

### Post by wmcbrine on 2005-04-08
You have "/chroot" in most places, but "/var/chroot" for the fstab lines. They should be "/chroot" too.

I've followed this guide (more or less), and I can confirm that sound works just by mounting /dev. For the record, that's:

/dev            /chroot/dev      none    bind            0       0

in /etc/fstab. (However, I also killed esd long ago, just to get sound working on the 64-bit side, and set everything to alsa then; I don't know if that makes a difference.)

I now have two chroots on my system -- /old32 and /new32. :) (/old32 is where my old distro is, but I also need /new32 for more current software, like Acroread 7.) I added "-c new32" to my do_dchroot script, since I have old32 as the default.

Another thing I added is the "linux32" command (in the package of the same name). Put this before dchroot, and the 32-bit apps will think they're running under an i686 kernel -- which is necessary in some cases (mainly install scripts).

Re Flash, you can install it from Synaptic. In fact there are, confusingly, two conflicting packages. I chose the big one -- the small one is apparently just a wrapper for Macromedia's installer.

Themes are a little off for the 32-bit apps. But that could be an advantage, since it reminds me which version I'm using. :)

Now we need a list of what hasn't been ported to 64-bit. (Another thread, perhaps.)

---

### Post by Crad on 2005-04-08
[QUOTE=wmcbrine]You have "/chroot" in most places, but "/var/chroot" for the fstab lines. They should be "/chroot" too.

I've followed this guide (more or less), and I can confirm that sound works just by mounting /dev. For the record, that's:

/dev            /chroot/dev      none    bind            0       0

in /etc/fstab. (However, I also killed esd long ago, just to get sound working on the 64-bit side, and set everything to alsa then; I don't know if that makes a difference.)

I now have two chroots on my system -- /old32 and /new32. :) (/old32 is where my old distro is, but I also need /new32 for more current software, like Acroread 7.) I added "-c new32" to my do_dchroot script, since I have old32 as the default.

Another thing I added is the "linux32" command (in the package of the same name). Put this before dchroot, and the 32-bit apps will think they're running under an i686 kernel -- which is necessary in some cases (mainly install scripts).

Re Flash, you can install it from Synaptic. In fact there are, confusingly, two conflicting packages. I chose the big one -- the small one is apparently just a wrapper for Macromedia's installer.

Themes are a little off for the 32-bit apps. But that could be an advantage, since it reminds me which version I'm using. :)

Now we need a list of what hasn't been ported to 64-bit. (Another thread, perhaps.)[/QUOTE]
 Thanks, I updated and fixed the /var bit.   Sound isn't working for me, perhaps I need to set everything to alsa.  You can fix themes if you're so inclined by installing the ubuntu artwork and ubuntu base (I think).

---

### Post by remkio on 2005-04-10
The do_dchroot script was giving me problems, as parameters like:

> This\ is\ a\ filename\ with\ spaces.txt 

were translated into:

> This is a filename with spaces.txt

causing the 32-bit program (totem) to not being able to open the file.

I solved it in the following way:

```

#!/bin/sh

for arg; do
        arg=`echo $arg | sed -e 's/ /\\\ /g'`
        args=`echo $args $arg`
done

/usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` $args"

```

There should be a shorter way, however I am no expert in shell scripting.

---

### Post by dreadnought on 2005-04-10
Many thanks Crad, having followed your instructions I am now able to chroot into 32 bit hoary. I nearly gave up and returned to 32 system but am now a confirmed 64-bitter.
 \\:D/

---

### Post by gratefulfrog on 2005-04-10
I've followed the instructions at the head of this thread, but when I reach step 5, I get some problems.... then it all falls apart...

Any help?  Thanks!

```
 ~$ dchroot -d
Executing shell in 'hoary' chroot.
dchroot: chdir: No such file or directory
dchroot: Child exited non-zero.
dchroot: Operation failed.
~$
```
But the following happens without the -d option
```
~$ dchroot
Executing shell in 'hoary' chroot.
No directory, logging in with HOME=/
/$exit
logout
~$ synaptic32
(hoary) synaptic32
dchroot: chdir: No such file or directory
dchroot: Child exited non-zero.
dchroot: Operation failed.
:~$

```

---

### Post by remkio on 2005-04-10
[QUOTE=gratefulfrog]I've followed the instructions at the head of this thread, but when I reach step 5, I get some problems.... then it all falls apart...

Any help?  Thanks!

[/QUOTE]

Either reboot or mount all the partitions/links you added to fstab with

```
sudo mount /chroot/...
```

---

### Post by dreadnought on 2005-04-11
Having studied this thread and got things working ok I gather I should be able to chroot into a 32 bit Hoary system that is already installed providing I mount the partition as /chroot in my 64bit Hoary. Is this correct?

---

### Post by mips on 2005-04-11
Step5:
> reon@mamoth:~$ apt-get install synaptic
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
reon@mamoth:~$ sudo apt-get install synaptic
Password:
Reading package lists... Done
Building dependency tree... Done

,,,,,,,,,,text deleted.................


I had to add sudo xxxx to all th elines in step 5. Am I doing something wrong ?

---

### Post by Crad on 2005-04-11
[QUOTE=mips]Step5:


I had to add sudo xxxx to all th elines in step 5. Am I doing something wrong ?[/QUOTE]
 No that was correct, I updated the original.

---

### Post by mips on 2005-04-11
Crad,

Thanks for the idiot proof guide, makes life easy for us noobs.

Where to from here ?


thanks
mips

---

### Post by raid517 on 2005-04-12
Hi, I have got this pretty much working now. But one thing I don't get is how do I make desktop icons of the applications I install? Say for example I wanted to install a 32Bit version of Kaffeine (and I really do want to install a 32Bit version of Kaffeine) would I have to run it all the time as su or could I run it as an ordinary user?

I tried installing kaffeine the way that is set out above - but it failed miserably,

GJ

---

### Post by raid517 on 2005-04-12
Also, how do I install 32 bit apps in the chroot environment that are not in the repositories - or in .deb format? For example, what about real player, or flashplayer (since I can't find a site that will install it automatically) or  crossover office, or things like this?

My main interest is to have these items as desktop icons in KDE and to be able to run them as I normally do.

GJ

---

### Post by capriciousmind on 2005-04-12
Thanks for the guide.  One question though, I installed firestarter 32 bit using the method described and everything is good until I try to start it.  It says my kernel does not support ip tables does anyone know why it would say that?

---

### Post by raid517 on 2005-04-12
I'm realy not trying to be sarcastic, but maybe it really is because your kernel doesn't support IP tables?

Perhaps you should add them?

GJ

---

### Post by raid517 on 2005-04-12
Also, Is there any chance anyone could adapt this guide so that I can install a standard debian unstable distribution as my chroot environment? I ask as there are several unoffical packages I would like that are only avaiable for unstable/sid. You can potentially add these repositories to your /chroot/etc/apt/sources.list, if you are using Ubuntu as your chroot - but this is likely to cause significant problems with many applications - as you will essentially be running a mixed environment. Already I found dependency conflicts when I tried to install mplayer, when I was told that mplayer from deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main conflicted with libavcodec2 from the official Ubuntu universe repositories. I have only just learned what a huge mistake it can be to run mixed environments - as as time goes on these conflicts only tend to increase in number, until it is impossible to install anything. (Those running mixed environments may not have found this out already - but they will eventually).

There are lot's of advantages to having a pure debian unstable install as your chroot environment. Not least because of the sheer volume of packages that are avaiable (both official and unnoficial) far more indeed than can be found on the Ubuntu repositories. But more than this is the frequency of updates. I find it odd as a long term (2 years) debian user to do an apt-get dist-upgrade after a couple of days and to find zero new packages on the repositories. In the real debian world by that time there would normally have been tens of megabytes if not hundreds worth of avaiable updates.

Also if I do want to install a package that is not in synaptic and/or apt-get such as a .deb or crossover office or a crossover office (or wine) application application, or flash for firefox or whatever and I wanted an icon on my 64 bit user desktop for any 32bit application I install, can someone _please_ tell me how to do this? It seems like a big part of the guide is missing in this regard.

Can anyone offer any input at all?

GJ

---

### Post by Crad on 2005-04-12
[QUOTE=raid517]Hi, I have got this pretty much working now. But one thing I don't get is how do I make desktop icons of the applications I install? Say for example I wanted to install a 32Bit version of Kaffeine (and I really do want to install a 32Bit version of Kaffeine) would I have to run it all the time as su or could I run it as an ordinary user?

I tried installing kaffeine the way that is set out above - but it failed miserably,

GJ[/QUOTE]
 What I've been doing for that is making my own launchers manually.  I've yet to come up with anything automatic for that...  For example, I had 64-bit OOo installed, but it had lots of problems, so I installed it in the chroot.  Then I went through linked the files to stuff like oowriter32.  I then modified the launchers for OOo to point to the 32 bit ones and now I have the icons.  That won't work in every scenario and is a bit of a pain... but hey we are bleeding edge now aren't we? ;-)

---

### Post by Crad on 2005-04-12
[QUOTE=mips]Crad,

Thanks for the idiot proof guide, makes life easy for us noobs.

Where to from here ?


thanks
mips[/QUOTE]
 Was thinking of making a Wiki entry, and also it looks like figuring out some sort fo bridge to the menus on the 32 bit side would be good.

---

### Post by Crad on 2005-04-12
[QUOTE=capriciousmind]Thanks for the guide.  One question though, I installed firestarter 32 bit using the method described and everything is good until I try to start it.  It says my kernel does not support ip tables does anyone know why it would say that?[/QUOTE]
 I can't think of a reason why the chroot wouldn't see iptables if the kernel supported them.  Have you inserted the module?

gmr@gmr-dev:/proc$ sudo modprobe ip_tables
gmr@gmr-dev:/proc$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by capriciousmind on 2005-04-12
[QUOTE=raid517]I'm realy not trying to be sarcastic, but maybe it really is because your kernel doesn't support IP tables?

Perhaps you should add them?

GJ[/QUOTE]

That is what I thought at first too, but I checked synaptic and sure enough they were installed.  

Can you compile firestarter from source to use in 64 bit?

---

### Post by capriciousmind on 2005-04-12
[QUOTE=Crad]I can't think of a reason why the chroot wouldn't see iptables if the kernel supported them.  Have you inserted the module?

gmr@gmr-dev:/proc$ sudo modprobe ip_tables
gmr@gmr-dev:/proc$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination[/QUOTE]

Would I need to do this if synaptic shows the ip table package is installed ?

---

### Post by Crad on 2005-04-12
Yes, though you can just try "sudo iptables -L" to see if it's already inserted.  (That's the only reason why I issued that command after the modprobe).

---

### Post by capriciousmind on 2005-04-12
[QUOTE=Crad]Yes, though you can just try "sudo iptables -L" to see if it's already inserted.  (That's the only reason why I issued that command after the modprobe).[/QUOTE]

ok thanks, I should have thought of this earlier but can firestarter be installed from source in 64 bit?  Then I wouldnt have to go through this, and it would make more since its my base system.

---

### Post by raid517 on 2005-04-12
Damn, there are just too many problems with it. I have Kaffeine installed, but it complains that it 'can't connect to the Xserver' whenever I try to open a file. Worse still Kaffeine needs access to kernel drivers to work my TV card - and it can't see these in chroot. There is a 64Bit version of kaffeine - but all the codecs it needs to play mutimedia files and TV streams are in 32 bit - so catch22 I'm afraid.

So it's back to 32 bit for me - and pure debian sid - so I don't have to deal with all of these conflicts between custom distros and the official debian source tree.

Fortunately I've found a bleeding edge distro that will do exactly that. (Or at least it promises to). KANOTIX looks at least promising. Almost excusively debian sid - with a lot of neat features thrown in...

I think it will be a couple of years before everyone get's up to speed on 64Bit - particularly in terms of codecs. But it is at least good that some people are working on it.

GJ

---

### Post by mthaddon on 2005-04-12
[QUOTE=Crad]To get Firefox setup with Flash I did the following:

[list]
[*]Ran synaptic32 (as noted in the above thread
[*]Installed mozilla-firefox
[*]dchroot -d
[*]ln -s /usr/bin/firefox /usr/bin/firefox32
[*]exit
[*]ln -s /usr/local/bin/do_dchroot /usr/local/bin/firefox32
[*]Made sure all instances of firefox are closed (you can not run both 32 and 64 bit firefoxes at the same time afaik... it just spawns a new 64 bit thread when you launch the old.
[*]firefox32
[*]Visited a site with flash on it and ran the automated firefox flash install.
[/list]

As of right now sound is not working.  If I figure out how to get the sound stuff working across the chroot, I'll post it here.[/QUOTE]


I tried this, and I have verified that I have the 32bit version of firefox running, but I get the following message:

LoadPlugin: failed to initialize shared library /home/mthaddon/.mozilla/plugins/libflashplayer.so [libXmu.so.6: cannot open shared object file: No such file or directory]

I've checked that the file exists:

ls -l /home/mthaddon/.mozilla/plugins/libflashplayer.so
-rwxr-xr-x  1 mthaddon mthaddon 2096844 2004-05-20 07:34 /home/mthaddon/.mozilla/plugins/libflashplayer.so

Any idea what's happening here?


---------------------------------

Resolution:

Found out I needed to install libxmu6 - fixed the problem. Now have 32bit firefox version running nicely.

Thanks, Tom

---

### Post by skwashd on 2005-04-13
[QUOTE=gratefulfrog]I've followed the instructions at the head of this thread, but when I reach step 5, I get some problems.... then it all falls apart...

Any help?  Thanks!

```
 ~$ dchroot -d
Executing shell in 'hoary' chroot.
dchroot: chdir: No such file or directory
dchroot: Child exited non-zero.
dchroot: Operation failed.
~$
```
But the following happens without the -d option
```
~$ dchroot
Executing shell in 'hoary' chroot.
No directory, logging in with HOME=/
/$exit
logout
~$ synaptic32
(hoary) synaptic32
dchroot: chdir: No such file or directory
dchroot: Child exited non-zero.
dchroot: Operation failed.
:~$

```[/QUOTE]

I had the same problem, easy to fix.  Just add this bit which is missing from the instructions:

Step 4
$ sudo gedit /etc/fstab
  Add the following lines:
  <snip />
$** sudo mount -a**
$ sudo gedit /usr/local/bin/do_dchroot

---

### Post by wmcbrine on 2005-04-13
> **raid517]I have Kaffeine installed, but it complains that it 'can't connect to the Xserver' whenever I try to open a file.[/quote]
That's what happens when /tmp isn't mounted in the chroot (mount --bind /tmp /chroot/tmp, or via fstab).

> Worse still Kaffeine needs access to kernel drivers to work my TV card - and it can't see these in chroot.
If you mean, it can't see the devices, you need to mount --bind /dev /chroot/dev (see my post above). If you mean it can't see the modules, don't worry said:**
> There is a 64Bit version of kaffeine - but all the codecs it needs to play mutimedia files and TV streams are in 32 bit
I'm not familiar with kaffeine, but that doesn't sound right. I can tell you, I run 64-bit MPlayer, VLC and Xine here, and they can play almost everything with only their native (64-bit) codecs.

---

### Post by minuo on 2005-04-13
A bit of googling about no sound from flash with chroot (and esd) led to this:

[http://lists.debian.org/debian-amd64/2005/03/msg00337.html](http://lists.debian.org/debian-amd64/2005/03/msg00337.html)

To sum it up, flash looks for /usr/lib/libesd.so.1 (in chroot), so, symlink (in chroot) /usr/lib/libesd.so.0 to /usr/lib/libesd.so.1 and now I have sound.  FWIW, I do have esound installed on chroot, but I'm not sure if its needed and I did modprobe snd-ioctl32 per a comment earlier in this thread...also not sure if that is needed.

Hope that helps anyone wanting sound with flash+chroot+esd

--m

---

### Post by Crad on 2005-04-13
[QUOTE=skwashd]I had the same problem, easy to fix.  Just add this bit which is missing from the instructions:

Step 4
$ sudo gedit /etc/fstab
  Add the following lines:
  <snip />
$** sudo mount -a**
$ sudo gedit /usr/local/bin/do_dchroot[/QUOTE]
 Thanks, updated!

---

### Post by Crad on 2005-04-13
[QUOTE=minuo]A bit of googling about no sound from flash with chroot (and esd) led to this:

[http://lists.debian.org/debian-amd64/2005/03/msg00337.html](http://lists.debian.org/debian-amd64/2005/03/msg00337.html)

To sum it up, flash looks for /usr/lib/libesd.so.1 (in chroot), so, symlink (in chroot) /usr/lib/libesd.so.0 to /usr/lib/libesd.so.1 and now I have sound.  FWIW, I do have esound installed on chroot, but I'm not sure if its needed and I did modprobe snd-ioctl32 per a comment earlier in this thread...also not sure if that is needed.

Hope that helps anyone wanting sound with flash+chroot+esd

--m[/QUOTE]
 This worked for me as well, thanks!

---

### Post by dimatrod on 2005-04-15
> Step 1:

    * sudo apt-get install dchroot debootstrap
    * sudo mkdir /chroot/
    * sudo gedit /etc/dchroot.conf
          o Add this line: hoary /chroot
    * sudo debootstrap --arch i386 hoary /chroot/ [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
    * sudo chroot /chroot/
    * dpkg-reconfigure locales

On the sudo chroot/chroot command, it would tell me "command not found".  Anyone knows why?

Edit: Nevermind, I found out it is chroot /chroot.

---

### Post by dimatrod on 2005-04-16
Can anybody please give me their clean do_dchroot please?  Mine apparently didn't come up....

---

### Post by dimatrod on 2005-04-16
When I get to step 5 and enter dchroot -d, it gives me the folowing message:
```
diego@jarkorpc:~$ dchroot
dchroot: Invalid input line /etc/dchroot.conf:12
dchroot: Error reading config file '/etc/dchroot.conf'.
```

Any ideas?

---

### Post by raid517 on 2005-04-16
[QUOTE=wmcbrine]That's what happens when /tmp isn't mounted in the chroot (mount --bind /tmp /chroot/tmp, or via fstab).


If you mean, it can't see the devices, you need to mount --bind /dev /chroot/dev (see my post above). If you mean it can't see the modules, don't worry; only the kernel needs to see them.

I'm not familiar with kaffeine, but that doesn't sound right. I can tell you, I run 64-bit MPlayer, VLC and Xine here, and they can play almost everything with only their native (64-bit) codecs.[/QUOTE]
Thanks. Just one thing though, is there a way to install official Debian unstable in my chroot directory?

I would just prefer this as there are a much wider range of applications for Debian unstable, they are updated more frequently and I can use debian unstable unofficial repositories without worrying that later down the line I am going to run into some kind of dependency conflict or other. (Running a mixed environment from different repositories is never a good idea. For those who have no discovered this yet, sooner or later you will end up running into unresolvable dependancy issues).

I assume it is just a case of changing the address in the intitial instructions? But what address should I use?

GJ

---

### Post by Sam on 2005-04-17
Thank you Crad for this how to, it worked well ! Also thank you mthaddon for your note about libxmu6.

Great work ! :-)

---

### Post by St-Ex on 2005-04-19
> I can tell you, I run 64-bit MPlayer, VLC and Xine here, and they can play almost everything with only their native (64-bit) codecs. 

Very interesting... I have been trying to get Mplayer installed through synaptic, but no luck; there is still this pbm of dependencies. Would you be kind enough to tell me how you got it working?

Cheers,  ;-)

---

### Post by Crad on 2005-04-20
[QUOTE=St-Ex]Very interesting... I have been trying to get Mplayer installed through synaptic, but no luck; there is still this pbm of dependencies. Would you be kind enough to tell me how you got it working?

Cheers,  ;-)[/QUOTE]
 I use mplayer in the chroot, but vlc works just fine in 64 bit mode.  I've only run divx stuff through it (as I just got the sound working).  I installed it via synaptic.

---

### Post by St-Ex on 2005-04-20
>  I use mplayer in the chroot 

I'll have a go myself... :neutral:


EDIT:

No luck... How did you get it to work?
Thx.

---

### Post by Daz_Man on 2005-04-20
having problems half way through step 4 of the instructions. i get to the part before it says "sudo mount -a", but when i run this command it says "mount: mount point /chroot/media/cdrom0 does not exist". i have looked in the /chroot/media folder but there is nothing in there. have i forgot to do something?

---

### Post by Crad on 2005-04-20
[QUOTE=Daz_Man]having problems half way through step 4 of the instructions. i get to the part before it says "sudo mount -a", but when i run this command it says "mount: mount point /chroot/media/cdrom0 does not exist". i have looked in the /chroot/media folder but there is nothing in there. have i forgot to do something?[/QUOTE]
 comment out the line in /etc/fstab for /chroot/media/cdrom0 then.

---

### Post by Crad on 2005-04-20
[QUOTE=St-Ex]I'll have a go myself... :neutral:


EDIT:

No luck... How did you get it to work?
Thx.[/QUOTE]
 I installed mplayer via synaptic32 (read using the dochroot bit).  I tested in dchroot -d before making the symlinks.  if you run mplayer via comandline in dchroot -d what kind of errors do you get?

---

### Post by tlepes on 2005-04-20
[QUOTE=Crad]To get Firefox setup with Flash I did the following:

[list]
[*] *...some other stuff about chroots...* 
[*]sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
[*]*...more clipped stuff regarding chroots...* 
[/list]
[/QUOTE]

Thanks!  You are awesome.  I have been looking for that nugget of knowledge.  I have not had sound working in my Hoary Firefox and Flashplayer at all until now.  I had given up on it for a while, even.  I am just running Hoary 32bit for now but have an AMD64 and was poking in here for tips on 32bit app support before I dive in.

I get sound in Firefox now!  What a nice surprise!

Peace,
Tim

---

### Post by Ephack on 2005-04-22
First of all: THANK YOU!  :) It's really very helpfull and thanks to you I can now view flash animations on my Ubuntu64.

My only remark is that I can have both version of Firefox working at the same time: it won't work if I make a Gnome launcher, but if I launch firefox32 from the shell, a new window of firefox32 appears, even if firefox64 is already runing

My next problem is for the sound... But I have already problems on my 64bits system, so I'm not sure I have any chance to have it to work in the chroot... Nobody spoke of OSS... Did somebody already try with it?

---

### Post by amarra on 2005-04-24
Hi to all,

this is my first message in the Ubuntu Forums after my registration. :)
I've a suggestion for this excellent HOWTO.
I think that it may be useful to add the following line in the /etc/fstab

/usr/share/fonts  /chroot/usr/share/fonts   none   bind  0   0

so that fonts from the 64 bit environment become available to the 32 bit chrooted environment. My 32 bit Firefox won't list all the fonts on my system before.
I hope this can be useful to someone.
Bye

---

### Post by downtime on 2005-04-24
this is somewhat of an addition to amarra's post. i'm trying to use some Windows apps with cxoffice in a 32bit chroot. the apps themselves run fine, but the fonts i have installed in the 64bit userspace don't show up. that makes perfect sense, but i can't figure out how to get the fonts installed in the 32bit chroot. has anyone gotten this working or even have some suggestions on getting it working?

---

### Post by dmatrix on 2005-04-25
Thanks Crad and everyone else that helped with this thread. I have updated the Cedega/Ubuntu Wiki page with all the modified details from this thread and the previous Wiki page.

[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu)

---

### Post by CospeFogo on 2005-04-26
Thanks for the guide. It's very clear and straightforward. However, I couldn't get the Flash plugin working in firefox32. I visited one site that required the plugin, made the automatic firefox plugin install, and when the page reloaded, the plugin was still missing. 

I have also tried to restart the browser and every time the installation ended apparently successfully, but it never appeared.

Any tips for me?

---

### Post by mthaddon on 2005-04-26
See my earlier post (page 3 I think). Basically, I'd recommend starting it from a console and seeing what error message you get:




I tried this, and I have verified that I have the 32bit version of firefox running, but I get the following message:

LoadPlugin: failed to initialize shared library /home/mthaddon/.mozilla/plugins/libflashplayer.so [libXmu.so.6: cannot open shared object file: No such file or directory]

I've checked that the file exists:

ls -l /home/mthaddon/.mozilla/plugins/libflashplayer.so
-rwxr-xr-x 1 mthaddon mthaddon 2096844 2004-05-20 07:34 /home/mthaddon/.mozilla/plugins/libflashplayer.so

Any idea what's happening here?


---------------------------------

Resolution:

Found out I needed to install libxmu6 - fixed the problem. Now have 32bit firefox version running nicely.

Thanks, Tom

---

### Post by CospeFogo on 2005-04-26
That´s the exact error message I get. Am I supposed to install libxmu6 inside the chroot?

Thanks a lot.

---

### Post by dmatrix on 2005-04-26
Yes. Take a look here for an updated version.

[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap_on_AMD64](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap_on_AMD64)

---

### Post by Ephack on 2005-04-26
[QUOTE=CospeFogo]Thanks for the guide. It's very clear and straightforward. However, I couldn't get the Flash plugin working in firefox32. I visited one site that required the plugin, made the automatic firefox plugin install, and when the page reloaded, the plugin was still missing. 

I have also tried to restart the browser and every time the installation ended apparently successfully, but it never appeared.

Any tips for me?[/QUOTE]
 It didn't work for me too this way. But as mentionned in a previous post in this topic, it works using the package flashplayer-mozilla. At least, it worked on my Ubuntu Hoary... :)

And for my sound problem? Did anybody succeed in usind sound in a chroted environment with OSS server?

---

### Post by CospeFogo on 2005-04-26
Worked like a charm. Sound also. No configuration was needed at all, I just ran synaptic32 and selected libxmu6.

Thanks a lot.

---

### Post by DutchLau on 2005-04-27
Admins, this should be a "Sticky" thread please  :-P 

Excellent "Howto"! Clean, clear, concise! Great job,

Cheers, DutchLau

---

### Post by St-Ex on 2005-04-28
> I installed mplayer via synaptic32 (read using the dochroot bit). I tested in dchroot -d before making the symlinks. if you run mplayer via comandline in dchroot -d what kind of errors do you get? 

Thx for your reply, Crad; unfortunately I was away...
Here are the errors I get if I tape gmplayer in dchrrot -d; if I 
tape mplayer, I only get the help lines...


[HTML]vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : Aucun fichier ou répertoire de ce type
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: Aucun fichier ou répertoire de ce type
Failed to open LIRC support.
You will not be able to use your remote control.

Gtk-WARNING **: Impossible de localiser le module chargeable dans module_path : « libbluecurve.so »,
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.[/HTML]

---

### Post by hiddenleaves on 2005-04-28
Hi. The HOWTO looks excellent but unfortunately I can get no further than halfway through Step 1.

When running the command "sudo debootstrap --arch i386 hoary /chroot/ http://archive.ubuntu.com/ubuntu" it gets as far as "I: extracting libc6-i686..." then stops. Nothing crashes or anything, but the setup process only ever gets this far.

Any ideas anyone?

Thanks...

---

### Post by idn on 2005-05-05
Great, thanks alot, works great, but if i wanted to remove it would all i have to do is delete the /chroot/ dir or would more steps be required.

Just there may be space issues for me.

---

### Post by daniele on 2005-05-05
The same happened also to me.

daniele@bsdx:~$ dchroot -d
Executing shell in 'hoary' chroot.
dchroot: chdir: No such file or directory
dchroot: Child exited non-zero.
dchroot: Operation failed.
daniele@bsdx:~$

But, since my home directory links to /usr/home (FreeBSD issue),
I just have to change the current dir to another location

daniele@bsdx:~$ cd /
daniele@bsdx:/$ dchroot -d
Executing shell in 'hoary' chroot.
daniele@bsdx:/$

Now it works fine !

cheers
daniele

---

### Post by Sam on 2005-05-09
[QUOTE=Crad]
<snip />

**Step 4:**
In another terminal window (or by existing chroot):
[list][*]sudo cp /etc/passwd /chroot/etc/
[*]sudo cp /etc/shadow /chroot/etc/
[*]sudo cp /etc/group /chroot/etc/
[*]sudo cp /etc/sudoers /chroot/etc/
[*]sudo cp /etc/hosts /chroot/etc/
[/list]<snip />[/QUOTE]
Why not make symlinks instead of copying the files ? The changes aren't reflected to the chroot environnement...

---

### Post by flex447 on 2005-05-10
I tried to set up the 32bit chroot and when I added my cdrom in fstab to /chroot/media/cdrom0 and I went into the chroot enviroment with dchroot -d I couldnt access my cdrom drive.

---

### Post by Crad on 2005-05-12
[QUOTE=Sam]Why not make symlinks instead of copying the files ? The changes aren't reflected to the chroot environnement...[/QUOTE]
 Because when you're in your chroot env, they will symlink to themselves.

---

### Post by Crad on 2005-05-12
[QUOTE=amarra]Hi to all,

this is my first message in the Ubuntu Forums after my registration. :)
I've a suggestion for this excellent HOWTO.
I think that it may be useful to add the following line in the /etc/fstab

/usr/share/fonts  /chroot/usr/share/fonts   none   bind  0   0

so that fonts from the 64 bit environment become available to the 32 bit chrooted environment. My 32 bit Firefox won't list all the fonts on my system before.
I hope this can be useful to someone.
Bye[/QUOTE]
 Thanks, added!

---

### Post by sud_crow on 2005-05-12
Hi, 
This is my first post in the forum, i used your tutorial and worked almost perfectly :)

Here is a tip for those who want to share partitions with Windows.

Mounting FAT32 partitions in the CHROOT enviroment

**Here is my #CHROOT section at /etc/fstab, this goes in the 64bit enviroment fstab**
```

## CHROOT!
/home /chroot/home none bind 0 0
/tmp /chroot/tmp none bind 0 0
/dev /chroot/dev none bind 0 0
/proc /chroot/proc proc defaults 0 0
#/media/cdrom0 /chroot/media/cdrom0 none bind 0 0
/mnt/win1    /chroot/mnt/win1 none bind,umask=0000,dmask=0000,uid=0002,gid=users,users 0 0
/mnt/win2    /chroot/mnt/win2 none bind,umask=0000,dmask=0000,uid=0002,gid=users,users 0 0
/mnt/win0    /chroot/mnt/win0 none bind,umask=0000,dmask=0000,uid=0002,gid=users,users 0 0

```


Now the problems.


Cant get audio to work, mPlayer displays this error:
[quote="mplayer"]
Could not open/initialize audio device -> no sound
[/quote]

Also, i cant get XMMS to work on 64bit
I get this error: 
> 
libmikmod.so.2: no se puede abrir el fichero del objeto compartido: No existe el fichero o el directorio


That means, **"cant open the file of the shared object: the file doesnt exist or the directory."**

This is not a translation error, thats the message, as confusing as it sounds. (at least for me)

so i sayd well, i make him run in 32bit mode (i dont know if MP3 works in 64bit, i guess it does), but  ](*,) i have no sound! and besides that, the thing freezes at the first file i try to play with it...


This are the issues im having... so, any ideas??
Thanks for all the work done here!

---

### Post by Sykil on 2005-05-13
Hrm...
> 
sykil@ubuntu:~$ sudo apt-get install dchroot debootstrap
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package dchroot


---

### Post by Fascination on 2005-05-18
When I try to run "apt-get update ; apt-get upgrade" in chroot for the first time, it throws up;

> root@balamb:/# apt-get update ; apt-get upgrade
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages
  Temporary failure resolving 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/multiverse/binary-i386/Packages.gz)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/binary-i386/Packages.gz)  Temporary failure resolving 'archive.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

Any ideas regarding why it cant find the servers? If I try to go on, when it gets to the stage where I enter; "sudo mount -a" it replies;

> mount: mount point /chroot/usr/share/fonts does not exist


---

### Post by Fascination on 2005-05-18
Just had a thought; could it be anything to do with the fact that I have an alcatel speedtouch usb modem? It has to be set up with additional drivers on a fresh install - would this mean that it would need to be set up on the new 32bit chroot?

---

### Post by Heliode on 2005-05-18
Hmm... just a thought: could a procedure similar to this be used to install a Ubuntu system from scratch from a live-cd like Knoppix, much in the same way you would install Gentoo? Could be nice for people who like having an optimized system!

---

### Post by zaro on 2005-05-19
There is such thing alredy.
[Debian From Scratch](http://people.debian.org/~jgoerzen/dfs/html/)

---

### Post by fritzi7 on 2005-05-19
[QUOTE=Crad]comment out the line in /etc/fstab for /chroot/media/cdrom0 then.[/QUOTE]

Shouldn't you just not forget to create the directory /chroot/media/cdrom0

The same happens with the mounting point for /media/cdrom0, so you have to add
"sudo mkdir /chroot/media/cdrom0" to your guide before mounting the whole lot or am I completely wrong?

By the way, @crad: thanks a lot fo ryour brilliant guide

---

### Post by fritzi7 on 2005-05-19
>  mount: mount point /chroot/usr/share/fonts does not exist

Just create the directory of the mounting point before executing the mount-command:

sudo mkdir /chroot/usr/share/fonts

---

### Post by Fascination on 2005-05-19
Thats worked, but what about the apt-get isssue? When I go to run gedit in the next step it cant find it (because of course its not installed in chroot as the apt-get didnt work)

---

### Post by caravela on 2005-05-21
HI i Would like to add some things that i found while i installed my chroot.
this code ```
#!/bin/bash
for arg; do
        arg=`echo $arg | sed -e 's/ /\\\ /g'`
        args=`echo $args $arg`
done
/usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` $args"
``` 

doesn't work well with some filenames for example if it has a "(" it will not work
solution: ```
#!/bin/bash
for arg; do
        arg=`echo $arg | sed -e 's/ /\\\ /g'`
        args=`echo $args $arg`
done
/usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` \"$args\""
``` 
added a \" before and after the $args
Also iam pretty sure that for is useless and that this line will work
```
#!/bin/bash
/usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` \"$@\""
```

---

### Post by zxc on 2005-05-21
```
root@ubuntu:/# sudo apt-get upgrade
sudo: unable to lookup ubuntu via gethostbyname()
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packag es (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Pa ckages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_restricted_bi nary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Pa ckages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary -i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_bi nary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/m ain Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security _main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/r estricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-se curity_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/u niverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-secu rity_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/m ultiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-se curity_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
root@ubuntu:/# postdrop: warning: unable to look up public/pickup: No such file or directory

``` 

I get that  :-?

---

### Post by benkong2 on 2005-05-24
did you mkdir /chroot
 [-X

---

### Post by Fascination on 2005-05-27
Yep. I followed the instructions to the letter.

---

### Post by wisu on 2005-05-31
[QUOTE=Crad]
Please let me know of any errors, enhancements, or corrections :)[/QUOTE]
 because my system authencticates to an LDAP server

I added libpam-ldap libnss-ldap using synaptic32 
followed the ncurse configuration gui

copied the following configs to the chroot env
/etc/pam.d/sudo
/etc/pam.d/common-account
/etc/pam.d/common-password
/etc/pam.d/common-session
/etc/nsswitch.conf

thats it... it works for me... Thx Crad

---

### Post by tseliot on 2005-06-17
[QUOTE=Crad] If you want to be able to easily launch 32 bit chroot apps from your 64 bit environment symlink the app name to /usr/local/bin/do_dchroot. [/QUOTE]

What does this mean? can you write this step by ste, please?

Thanks (Sorry I'm a newbie)

---

### Post by FLeiXiuS on 2005-06-17
Oh boy, so where to start with this one.  I'm guessing it's just a huge problem with the repo's.  I hope so :-P.  As kassetra already knows I've 

$ time `rm -Rf /`

Several times just to releive my frustration.  Well turns out, there's a problem install postfix when it's downloaded off the repo's.  It'll get to configuring then all hell breaks loose.  

```

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
postalias: warning: valid_hostname: misplaced delimiter: x0ne.hsd1.md.comcast.net.
postalias: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: x0ne.hsd1.md.comcast.net.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1

```

Not to sure why it's having a hard time with me.  I blame comcast most of all :-p.

Anyways, I've been through several attempts to limit what problems could be causing this solution, no methods have worked so far.


All help would be appreciated!  Thank you.

---

### Post by joekr on 2005-06-18
Guide worked like a charm...

I've got a 32bit Firefox rocking the web with flash plugin!

Next, I'm going to install WINE & DVD Decrypter!

---

### Post by skylark on 2005-06-19
Doh,

installation fails step1 for me:
$ sudo apt-get install dchroot debootstrap
Reading package lists... Done
Building dependency tree... Done
Package debootstrap is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package debootstrap has no installation candidate

I've got universe enabled in my /etc/apt/sources.list ... am I missing something?

Edit: Fixed it - I needed to uncomment more lines in my sources.list, sorry.

---

### Post by lukus001 on 2005-06-20
I've been able to install 32bit firefox, realplayer etc.. via this chroot method, but realplayer lacks a lot of codecs...

is there anything "special" thing you need to do, to get the codecs running on to realplayer 32?

---

### Post by skylark on 2005-06-21
I managed to set this up, and have firefox, flash, totem-xine, and the java plugin working fine. My realplayer install sort of works but has major issues (lockups etc) when playing streams. 

I think this chroot ideas is good - but what I would really like to do is set it up so that I dont have to share any partitions except maybe /dev with the chroot environment. That is - create a "chroot jail" where firefox and all the plugins reside. This would be really secure... only problem is I don't know how to get the Xwindows stuff working this way (I run into permission issues).

Anyone have any ideas?

---

### Post by Red_Menace on 2005-06-22
Anyone know of a guide that explains what all of this does, step by step?  I'd like to know what I'm doing.  I'm pretty green when it comes to linux.

---

### Post by mizunoX on 2005-06-23
I followed all of the instructions from the first post, then I installed firefox as per the second post.

My problem is that when I run firefox32 it loads the 64 bit version...
I tried removing both versions of firefox, the installing just the 32bit version with synaptic32.  Guess what?  When I load firefox32, it's still showing as the 64bit one!

Can someone tell me what I'm doing wrong?

Thanks in advance!

*edit*  nevermind, it was the 32bit version.  I was seeing AMD64 in help/about and it was throwing me off.   Everything works perfectly, thanks for the how-to!

---

### Post by joekr on 2005-06-23
**Does anyone know how I would be able to enable hardware acceleration within the chroot environment?**

[Please follow the link and help me out :D](http://ubuntuforums.org/showthread.php?p=225962#post225962)

---

### Post by filemanager on 2005-07-06
I'm just a little confused. Does this turn your amd64 system into a 32bit system, or does it allow you to install 32bit software *as well as* 64bit software?

Also, aside from firefox and that, how do you install other 32bit programs, just normally as their documentation says?

---

### Post by ngolian on 2005-07-11
I use this in /usr/local/bin/do_chroot :

#!/bin/sh
exec /usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` `for i in "$@"; do echo -n '"'$i'" '; done`"

This way I can pass exotic characters in my command lines eg the brackets in Firefox's -remote command syntax and ampersands in URLs.

---

### Post by Crad on 2005-08-02
[QUOTE=filemanager]I'm just a little confused. Does this turn your amd64 system into a 32bit system, or does it allow you to install 32bit software *as well as* 64bit software?

Also, aside from firefox and that, how do you install other 32bit programs, just normally as their documentation says?[/QUOTE]
 It allows you to have 32 bit binaries and libraries in your 64 bit system so you can execute programs that dont have well working 64-bit binaries, like say OOo.

---

### Post by gordyt on 2005-08-04
[QUOTE=mthaddon]
...
LoadPlugin: failed to initialize shared library /home/mthaddon/.mozilla/plugins/libflashplayer.so [libXmu.so.6: cannot open shared object file: No such file or directory]
...
Resolution:

Found out I needed to install libxmu6 - fixed the problem. Now have 32bit firefox version running nicely.
[/QUOTE]

Tom thank you for posting this!  I had just setup the chroot environment on my machine yesterday afternoon and was  having the exact same problem.  

Regards,
--gordon

---

### Post by pobstil on 2005-08-20
Hey I found this thread hoping to answer my questions, but havn't quite got it. Now I'm wondering if you can answer them for me.

I'm trying to set up a webserver, in which my mates can host their own websites. So I want to setup a user for them, so they can logon remotely via ssh, and have their website hosted in their home directory. But want I don't want them to be able to access the rest of the system. Even though I know they can't do anything because they wont have root permissions, I just want them to be able to access their home folder, and just their home folder. I thought I could do this my chrooting their user, can anyone expand on this, help me out, or point me in the right direction? Thanks in advance for any hints and tips. :)

---

### Post by rvleeuwen on 2005-08-22
For me it was necesarry to add non-network local to the access control list
of X (i use debian amd64/testing/unstable btw)

Add the following:

    * #!/bin/sh
    * xhost + local:
    * /usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` $*"

---

### Post by greyhound4334 on 2005-08-26
Has anyone gotten the acrobat reader plugin to work with the chroot 32-bit firefox?

I've installed the plugin, and it shows up with "about:plugins", but when I click on a link to a pdf file I just get a blank window.

Anyone do this successfully?  Any tips/tricks?

Thanks!

---

### Post by tseliot on 2005-08-26
[QUOTE=greyhound4334]Has anyone gotten the acrobat reader plugin to work with the chroot 32-bit firefox?

I've installed the plugin, and it shows up with "about:plugins", but when I click on a link to a pdf file I just get a blank window.

Anyone do this successfully?  Any tips/tricks?

Thanks![/QUOTE]
It worked great for me. I installed it in (the chrooted) Synaptic.

---

### Post by zarathustra on 2005-08-31
I'm trying to install something on Wine but I can't see any files on the CD in my 32 bit environment.

---

### Post by lestial on 2005-09-03
well as you can see this is my first post here. i'm loving this distro / community because through you guys i actually have my ati card working lol. i'm trying to set up the 32 bit environment as per this guide.. but i'm getting these errors.




Errors were encountered while processing:
 postfix
 at
 mailx
 mutt
 postfix-tls
 ubuntu-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
jimbo@ubuntu:~$ sudo ln -s /usr/sbin/synaptic /usr/sbin/synaptic32
jimbo@ubuntu:~$ exit
exit
jimbo@ubuntu:~$ sudo ln -s /usr/local/bin/do_dchroot /usr/local/bin/synaptic32
jimbo@ubuntu:~$ sudo synaptic32
(hoary) synaptic32

(synaptic32:28009): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

any help would be appreciated, i'm all aquiver at the idea of finally being able to leave behind windows. if i can get this 32 bit setup.. set up, then wow working.. i wouldn't need windows for anything anymore :)

---

### Post by tear on 2005-09-07
I get this massage and it's starting to irritate me


```

$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate

```

---

### Post by draugen on 2005-09-07
instead of:

```

# sudo cp /etc/passwd /chroot/etc/
# sudo cp /etc/shadow /chroot/etc/
# sudo cp /etc/group /chroot/etc/
# sudo cp /etc/sudoers /chroot/etc/
# sudo cp /etc/hosts /chroot/etc/

```

you can use:
```

# sudo mount --bind  /etc/passwd /chroot/etc/passwd
# sudo touch /chroot/etc/shadow
# sudo mount --bind /etc/shadow /chroot/etc/shadow
# sudo mount --bind /etc/group /chroot/etc/group
# sudo mount --bind /etc/sudoers /chroot/etc/sudoers
# sudo mount --bind /etc/hosts /chroot/etc/hosts

```

with the appropriate entries in /etc/fstab of course.

then changes from the 64bit host system will be propagated to the 32bit chroot.

And for installing debian sid in the chroot:
# debootstrap --arch i386 sid /chroot <url-to-local-debian-mirror>

hope this helps :)

---

### Post by Ephack on 2005-09-08
[QUOTE=tear]I get this massage and it's starting to irritate me

Hello Tear!
Perhaps you should re-do steps 2 and 3. Seems as if you did'nt update apt.

---

### Post by trinaryouroboros on 2005-09-20
I firstly want to thank you all for making a fantastic guide to setting up this hybrid.

To reward those whose efforts contributed to troubleshooting this firefox32 install, I have a simple trick to get sound working in Flash, provided you followed the first post's steps to set it up.

Close Firefox first, then from terminal (root or chroot doesn't matter) type:

killall esd

Start firefox32 from chroot, and voila! SOUND is back!

---

### Post by trinaryouroboros on 2005-09-20
[QUOTE=draugen]instead of:

```

# sudo cp /etc/passwd /chroot/etc/
# sudo cp /etc/shadow /chroot/etc/
# sudo cp /etc/group /chroot/etc/
# sudo cp /etc/sudoers /chroot/etc/
# sudo cp /etc/hosts /chroot/etc/

```

you can use:
```

# sudo mount --bind  /etc/passwd /chroot/etc/passwd
# sudo touch /chroot/etc/shadow
# sudo mount --bind /etc/shadow /chroot/etc/shadow
# sudo mount --bind /etc/group /chroot/etc/group
# sudo mount --bind /etc/sudoers /chroot/etc/sudoers
# sudo mount --bind /etc/hosts /chroot/etc/hosts

```

with the appropriate entries in /etc/fstab of course.

then changes from the 64bit host system will be propagated to the 32bit chroot.

And for installing debian sid in the chroot:
# debootstrap --arch i386 sid /chroot <url-to-local-debian-mirror>

hope this helps :)[/QUOTE]

[http://ubuntuforums.org/showthread.php?p=361939&posted=1#post361939](http://ubuntuforums.org/showthread.php?p=361939&posted=1#post361939)

killall esd

restart firefox32 - sound is back.

---

### Post by trinaryouroboros on 2005-09-21
[QUOTE=Crad]At this point you should have a 32 bit environment setup with synaptic setup.  When you run synaptic32 from your main environment it will chroot execute it and all installations will be made to your 32 bit environment.  If you want to be able to easily launch 32 bit chroot apps from your 64 bit environment symlink the app name to /usr/local/bin/do_dchroot.  If you're using this as desktop system you'll probably want to use synaptic to install x, gnome, ubuntu specific themes, etc.

Please let me know of any errors, enhancements, or corrections :)[/QUOTE]

I have an issue with this chroot. I've modified the fstab slightly, in the first post, here's the only add's :

#

    * /media/cdrom0 /chroot/media/cdrom0 none bind 0 0
    * /media/cdrom1 /chroot/media/cdrom1 none bind 0 0
    * /usr/share/fonts /chroot/usr/share/fonts none bind 0 0

# sudo mkdir /chroot/media/cdrom0
# sudo mkdir /chroot/media/cdrom1

Now after reboot, I can access cdrom0 and cdrom1 just fine with my normal interface:

root@w0-rm-h0-l3:/media # cd cdrom0
root@w0-rm-h0-l3:/media/cdrom0 # ls
autorun.exe    DirectX7        _INST32I.EX_  Readme.txt        _sys1.cab
autorun.ico    Docs            ip.cfg        _Setup.dll        _sys1.hdr
autorun.inf    Dsetup.dll      Ip.exe        Setup.exe         Tapsplash640.bmp
ConfigINI.exe  dxMedia.exe     _ISDel.exe    SETUP.INI         _user1.cab
data1.cab      Eaukhelp.hlp    lang.dat      setup.ins         _user1.hdr
data1.hdr      Eula.txt        layout.bin    SetupInstall.exe
DATA.TAG       FinalSetup.exe  os.dat        setup.lid

But, when I try to access these drives from chroot :

root@w0-rm-h0-l3:/media/cdrom0 # chroot /chroot
root@w0-rm-h0-l3:/ # cd /media
root@w0-rm-h0-l3:/media # cd cdrom0
root@w0-rm-h0-l3:/media/cdrom0 # ls
root@w0-rm-h0-l3:/media/cdrom0 #

Nada, zip, zilch.

What am I doing wrong here? There's got to be some way to get the cdroms to be recognized and mountable in the chroot here...

---

### Post by Sockpuppet on 2005-09-27
[QUOTE=Crad]
 /usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` $*"
[/QUOTE]

I don't quite understand this. Using this and calling "do_dchroot firefox --verbose", the script will call

/usr/bin/dchroot -d "do_dchroot firefox --verbose"

so it will call do_dchroot in the chrooted directory, which isn't there.

Is there some bit I am missing?

---

### Post by Sockpuppet on 2005-09-27
[QUOTE=Crad]
Made sure all instances of firefox are closed (you can not run both 32 and 64 bit firefoxes at the same time afaik... it just spawns a new 64 bit thread when you launch the old.
[/QUOTE]

Yes, you can. You have to modify /usr/lib/mozilla-firefox/firefox for this. The PING_STATUS will determine if  the script uses an existing browser running on the X server or if it starts a new one, It's enough to add these two lines:

```
diff -c5 /usr/lib/mozilla-firefox/firefox /chroot/usr/lib/mozilla-firefox/firefox
*** /usr/lib/mozilla-firefox/firefox    2005-09-22 20:02:48.000000000 +0200
--- /chroot/usr/lib/mozilla-firefox/firefox     2005-09-28 01:53:55.000000000 +0200
***************
*** 367,376 ****
--- 367,379 ----
      DISPLAY="${CMDLINE_DISPLAY}" ${MOZ_PROGRAM} -remote 'ping()' \
          > /dev/null 2>&1
      PING_STATUS=$?
  fi
  
+ # force standalone start
+ PING_STATUS=2
+ 
  echo_vars PING_STATUS
  
  # Clean user profile if we are not trying to use the running instance and only
  # if the check was successful (status 2)
  if [ "${REMOTE}" -eq 0 ] && [ "${TRY_USE_EXIST}" -eq 0 ] && [ "${PING_STATUS}" -eq 2 ]; then
```

I have also added a diversion of the .mozilla folder in /etc/fstab to make sure that the two browsers are not interfering with each other

```
/home/sockpuppet/.mozilla32 /chroot/home/sockpuppet/.mozilla none bind 0 0
```

For that, one has to mkdir ~/.mozilla32, of course.

One bad thing about the [the "remote" call used by the Mozilla shellscripts]("http://www.mozilla.org/unix/remote.html") to find an existing browser instance is that one cannot tell if it is talking to the 32 or the 64 bit browser.

So I still need to find out how one can make sure that clicks in other applications will always be opened by the 64 bit browser.

---

### Post by Sockpuppet on 2005-09-27
[QUOTE=Sockpuppet]Yes, you can.[/QUOTE]

Problem is, of course, that now the two browsers look absolutely identical. (In my case, there is  one difference: German menus for 64 bit and English for 32 bit, but that's too subtle to notice it while working with it.)

Is there any way I can force a colour scheme onto firefox, so that I can run the 32 bit firefox with a different menu / background colour?

---

### Post by Sockpuppet on 2005-09-27
[QUOTE=Sockpuppet]Is there any way I can force a colour scheme onto firefox, so that I can run the 32 bit firefox with a different menu / background colour?[/QUOTE]

I have "solved" this now by using a suitably ugly firefox theme for the 32 bit version to tell them apart. But I don't really like this, so I will try to find a way to change the application's GTK colour theme through the console.

Also, the firefox callup script needs to be changed to identifying the 32 and the 64 bit apps on the system. Right now, I can close the 64 bit version and if I then try to restart it, "remote ping" will find the already running 32 bit version and open a new window there.

---

### Post by benkong2 on 2005-09-30
I have an amd64 with breezy installed and have run into the following problem:

I took these steps:
# sudo apt-get install dchroot debootstrap
# sudo mkdir /chroot/
# sudo gedit /etc/dchroot.conf

    * Add this line: hoary /chroot

# sudo debootstrap --arch i386 hoary /chroot/ [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
# sudo chroot /chroot/

now when I get to the sudo chroot /chroot/

I get this error:
"chroot: cannot run command `/bin/bash': No such file or directory"
all goes well until I execute this command the chroot dir is in the / directory I tried cd /chroot/ then issuing the command got the same error.

Since all others have had such great success I know it must be my error.

Thanks for any help.

---

### Post by benkong2 on 2005-09-30
Hey thanks nevermind I figured it out. bad on me I did not place a space between the hoary /chroot/ and the http: stuff so debootstrap made my directory structure /chroot/http:/archive/ubuntu/com/ubuntu/ then I got the normal directory structure.

So I did a:
cd /http:/archive/ubuntu/com/ubuntu/ 
sudo mv * /chroot/
sudo rm -drf /chroot/http:

after that all worked well now I am after flash-macromedia. Which BTW is the only reason I needed to do this in the first place.

Thanks for what I know would have been a great answer.

---

### Post by kb_ganesh on 2005-10-02
i work from behind a proxy server..so, i guess you can add a section in the first post mentioning how to first set the proxy settings for wget(which is used by the 4th step, namely
sudo debootstrap --arch i386 hoary /chroot/ [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) )..which involves editing ~/.wgerc to include these lines..
```
http_proxy = <proxy_addy>
use_proxy = on
wait = 15

```
 i dont think anyone would use wget at all what with d4x and synaptic to do all the work..just a thought..(came out of personal experience :) )

---

### Post by alesdoc on 2005-10-08
in my laptop the howto does'nt work. If i write:

[HTML]dchroot -d[/HTML]

i receive

[HTML]Executing shell in 'breezy' chroot.[/HTML]

but if i give [HTML]sudo apt-get install synaptic[/HTML]

i receive nothing...so i can't proceed with the howto.

if i write [HTML]exit[/HTML]

i receive this:

[HTML]dchroot: Child exited non-zero.
dchroot: Operation failed.
[/HTML]

i've added [HTML]snip /[/HTML]

ideas?

---

### Post by vox on 2005-10-10
Thanks for the howto :)  Have one problem tho. When trying to run a 32bit app from within the 64bit environment, i get this error:

vox@Hagalaz:~$ vlc32
(breezy) cho /usr/local/bin/vlc32 | sed 's|^.*/||'
bash: cho: command not found

but if i run it from within the 32bit enviro, it works fine. What've i done wrong? :)

***Edit***

Gah ok. this was an issue with the joe editor.  I'll go crawl back under my rock now.. :)

---

### Post by perfektion on 2005-10-11
i don't find howto erase messeges.
so i cant erase this.
so i type is instad.

---

### Post by puiphooey on 2005-10-12
Hey nice FAQ. Maybe you want to add an addendum. If you want to do this with an ATI graphics card and use propreitary drivers, you have to add this to your do_dchroot:
> #!/bin/sh

xhost + local:
/usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` $*"

And if you want 3d Acceleration after making sure your /dev is mounted correctly, install (k/x)ubuntu-desktop through synaptic32.

---

### Post by Duali on 2005-10-18
I have followed the how-to almost trought, but when I try to install synaptic I get this:

```

teppo@kotikone:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  synaptic: Depends: libapt-pkg-libc6.3-5-3.9
            Depends: libfontconfig1 (>= 2.2.1) but it is not going to be installed
            Depends: libglade2-0 (>= 1:2.5.1) but it is not going to be installed
            Depends: libgtk2.0-0 (>= 2.6.0) but it is not going to be installed
            Depends: libpango1.0-0 (>= 1.8.1) but it is not going to be installed
            Depends: libvte4 (>= 1:0.11.12) but it is not going to be installed
            Depends: libxft2 (> 2.1.1) but it is not going to be installed
            Depends: scrollkeeper but it is not going to be installed
E: Broken packages
teppo@kotikone:~$

```

Any ideas? Oh, and I have breezy installed so I have changed hoary -> breezy during the how-to

---

### Post by puiphooey on 2005-10-19
O and another nice addendum:
> #!/bin/sh

xhost + local:

temp=`echo $0 | sed 's|^.*/||'`
command=`echo $temp | sed 's/32/ /'`

for arg; do
        arg=`echo $arg | sed -e 's/ /\\\ /g'`
        args=`echo $args $arg`
done

/usr/bin/dchroot -d "$command $args"

This verison doesn't require you to create another symlink in the chroot, something I found annoying.

---

### Post by jtinel on 2005-10-19
[QUOTE=Duali]I have followed the how-to almost trought, but when I try to install synaptic I get this:

```

teppo@kotikone:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  synaptic: Depends: libapt-pkg-libc6.3-5-3.9
            Depends: libfontconfig1 (>= 2.2.1) but it is not going to be installed
            Depends: libglade2-0 (>= 1:2.5.1) but it is not going to be installed
            Depends: libgtk2.0-0 (>= 2.6.0) but it is not going to be installed
            Depends: libpango1.0-0 (>= 1.8.1) but it is not going to be installed
            Depends: libvte4 (>= 1:0.11.12) but it is not going to be installed
            Depends: libxft2 (> 2.1.1) but it is not going to be installed
            Depends: scrollkeeper but it is not going to be installed
E: Broken packages
teppo@kotikone:~$

```

Any ideas? Oh, and I have breezy installed so I have changed hoary -> breezy during the how-to[/QUOTE]

Exact same problem here.  I believe I have followed the instructions exactly, with the exception of changing hoary to breezy wherever it appeared.

Any suggestions are appreciated.
Thanks,
jt

---

### Post by feight on 2005-10-20
Having problems, to start, I'm running Breezy as well. I cannot get the chroot to install with or without changing hoary to breezy in the commands, in both cases, even after deleting and recreating the /chroot/ folder I get stuck at...
```
I: Checking component main on http://archive.ubuntu.com/ubuntu...
```
for several several minutes.

EDIT: Nevermind, apparently I was more patient the last time I did this, not used to the lack of information on progress.

---

### Post by feight on 2005-10-20
[QUOTE=jtinel]Exact same problem here.  I believe I have followed the instructions exactly, with the exception of changing hoary to breezy wherever it appeared.

Any suggestions are appreciated.
Thanks,
jt[/QUOTE]

I had the same problem as well, until I realized that at the step where you edit the chroot sources.list I didn't replace hoary with breezy.

---

### Post by feight on 2005-10-20
I have a 32bit chroot made up of breezy... only problem is, due to my want to trailblaze I've run into a snag. Firefox32 runs fine... but I can install the macromedia flash plugin a dozen times and restart the computer and it keeps insisting I don't have it and the flash movies don't run.

[COLOR="Red"]EDIT: Well, overlooking the obvious, I installed flashplayer-mozilla... long story short, problem solved. I just wish I knew why installing the application through firefox didn't work like it has the last few chroots I've attempted.[/COLOR]

---

### Post by !nkubus on 2005-10-20
WOW that trick is really nice. You saved me, now I can play my games, flash sites, and quicktimes movies... well not aaaallll of them but a lot of them :)

---

### Post by Navyblue on 2005-10-25
I have been in following the how to. I am running Breezy, but still following the Hoary chroot, as someone here recommends to follow word by word unless I know what I am doing. Anyway when I reached the final step of  "sudo synaptic32", I get this:

```

(hoary) synaptic32
bash: synaptic32: command not found
dchroot: Child exited non-zero.
dchroot: Operation failed.

```

At the step of "sudo apt-get install synaptic", it doesn't seem to work. I got this message:

```

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_SG:en",
        LC_ALL = (unset),
        LANG = "en_SG.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: syntax error: unknown group `postdrop' in statusoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Any clue?

Thanks :)

---

### Post by cmo on 2005-10-28
I'm having the same problem as Navyblue, except my locale settings are set to en_GB.

Any ideas....

Cheers

cmo

Update:  I've matched the locale settings with the system settings and it seems to get past that error, but now it's stuck on:

[COLOR="Navy"]Preconfiguring packages ...
dpkg: syntax error: unknown group `postdrop' in statusoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/COLOR]
while installing synaptic.

Any ideas?

Cheers

cmo

---

### Post by Navyblue on 2005-10-28
I have installed  a couple more of locale and the locale error message went away as well. Now I got the same message as CMO.

Btw, I also get the same error at "apt-get upgrade"

Does anyone still looking at Hoary forum except for those who are looking for an answer?

---

### Post by gk_jam on 2005-11-08
I'm a total newbie to Linux, just got set up with Breezy and trying to follow this howto. In Step 1, first few commands go good, until

sudo chroot /chroot/

When I do that, the terminal pops up this message:

chroot: cannot run command `/bin/bash': No such file or directory

I look inside my /bin and there's a file bash. Anyone know why it's doing this, and how to fix?

---

### Post by Ephack on 2005-11-09
Hello gk_jam! I've experienced the same problem while installing my chroot. What I did it simply delting the whole /chroot directory and doing everything again from the beginning. And it worked! I've no idea where the problem came from and if you have the same, but for me it worked ike that...

Good luke ;)

---

### Post by legout on 2005-11-11
Hi this is a very long thread;-) and i won´t read all that is written there.

So is there a howto in the wiki, or can anybody tell me where i can find the completly howto in the forums?

THANKS

Legout

---

### Post by Snifffurt on 2005-11-14
Hi

I've made symbolic Links to the files in etc in stead of copying them. It works at a glance, and makes syncing of the files at changes obsolete.

```

user@host:/chroot/etc$  pwd
/chroot/etc
user@host:/chroot/etc$  sudo ln -s /etc/passwd passwd
user@host:/chroot/etc$  sudo ln -s /etc/shadow shadow
user@host:/chroot/etc$  sudo ln -s /etc/group group
user@host:/chroot/etc$  sudo ln -s /etc/sudoers sudoers
user@host:/chroot/etc$  sudo ln -s /etc/hosts hosts

```

Regards

Snifffurt

(Edited)

Oups.... This seems **not** to be working. Today FF and Acroread didn't start out of the 32Bit chroot. After changing back the links they where working again....

---

### Post by pjs_flyer on 2005-11-15
Excellent guide - works well in Breezy too.

Quick (and probably dumb) question, though.  Having installed the chroot environment, everything seems to be replicated in my chroot environment, including all the stuff in home, so I've got copies of all of the documents, pdfs, spreadsheets etc that I use in my 64bit breezy.  Given that I only use the chroot environment for firefox (and potentially other "troublesome" apps), is it safe to delete these copy documents from my chroot environment?  And is there anything else that can be deleted wholesale?

Cheers

P

---

### Post by Ephack on 2005-11-15
Euh... I would'nt do that pjs!

Your /chroot/home directory is not a copy, but a link to /home. I didn't do the test, but if I'm not wrong, if you empty your /chroot/home directory, you will have an also empty /home directory, which is probably not your intention :p

---

### Post by pjs_flyer on 2005-11-16
Said it was a dumb question - lucky I asked! Thanks Ephack!

---

### Post by nalmeth on 2005-11-18
ok, i am running breezy, and am not sure if anybody will even read this, but I followed the exact same procedures, replacing 'hoary' with 'breezy'. Everything was successful up to step 5.

here is my /etc/dchroot.conf:
# /etc/dchroot.conf
#
# This file configures the chroots that users can access with the 'dchroot'
# command.  Input lines consist of a description and a path separated by
# whitespace.  If more than one input line is present the first will be the
# default chroot.

# Example : the following line enables a chroot called 'stable'
# located at /chroot/stable

#stable /chroot/stable
#breezy /chroot

and here is what happens when executing dchroot -d:

nalmeth@ubuntu:~$ dchroot -d
dchroot: No chroots found in config file '/etc/dchroot.conf'.

any ideas?

thanks in advance!

---

### Post by Snifffurt on 2005-11-18
Hi

[QUOTE=nalmeth]
and here is what happens when executing dchroot -d:

nalmeth@ubuntu:~$ dchroot -d
dchroot: No chroots found in config file '/etc/dchroot.conf'.


any ideas?
[/QUOTE]

I think you should comment out a chroot, otherwihse dchroot will not know where to chroot to:

```

# /etc/dchroot.conf
#
# This file configures the chroots that users can access with the 'dchroot'
# command.  Input lines consist of a description and a path separated by
# whitespace.  If more than one input line is present the first will be the
# default chroot.

# Example : the following line enables a chroot called 'stable'
# located at /chroot/stable

#stable /chroot/stable
breezy /chroot
```

HTH

Best Regards

Snifffurt

---

### Post by Jeffj on 2005-11-30
jjm@moped:~$ dpkg-reconfigure locales
/usr/sbin/dpkg-reconfigure must be run as root

---

### Post by Jeffj on 2005-11-30
In another terminal window (or by existing chroot):
did you mean exiting?

---

### Post by rplantz on 2005-12-05
All seemed to go well, but acroread32 doesn't work. I need to dchroot first.

I have ```

bob@robert:~$ ls -l /usr/local/bin/
total 8
lrwxrwxrwx  1 root root 25 2005-12-04 20:38 acroread32 -> /usr/local/bin/do_dchroot
-rwxr-xr-x  1 root root 62 2005-12-04 20:18 do_dchroot
lrwxrwxrwx  1 root root 25 2005-12-04 20:25 synaptic32 -> /usr/local/bin/do_dchroot
bob@robert:~$ cat /usr/local/bin/do_dchroot
#!/bin/sh
/usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` $*"

```

When I do
```

sudo synaptic32

```
it runs, but ```

bob@robert:~$ acroread32
(breezy) acroread32
bash: acroread32: command not found
dchroot: Child exited non-zero.
dchroot: Operation failed.

```

However, ```

bob@robert:~$ dchroot -d
Executing shell in 'breezy' chroot.
bob@robert:~$ acroread
bob@robert:~$

```
works fine.

I'm confused.

Edit on 12/6/05

Okay, I figured it out. I needed to link app_name32 to app_name. That is
```

bob@robert:~$ dchroot -d
Executing shell in 'breezy' chroot.
bob@robert:~$ which acroread
/usr/bin/acroread
bob@robert:~$ cd /usr/bin/
bob@robert:/usr/bin$ sudo ln -s acroread acroread32
bob@robert:/usr/bin$ exit
exit
bob@robert:~$ acroread32

```

and it works!

---

### Post by Ferrat on 2005-12-09
Hmm I figure it's a update problem or something but at the last step I get

```

holo@Holokauston:~$ sudo synaptic32 
(hoary) synaptic32
bash: synaptic32: command not found
dchroot: Child exited non-zero.
dchroot: Operation failed.
holo@Holokauston:~$

```

Tried redoing update and install but that won't override and stops.


----------------

Think I found it 

Running 
```

sudo debootstrap --arch i386 hoary /chroot/ http://archive.ubuntu.com/ubuntu

```

I get an error after unpacking it all

```

I: Extracting whiptail...
I: Extracting zlib1g...
I: Installing core packages...
W: Failure trying to run: chroot /chroot dpkg --force-depends --install var/cach e/apt/archives/base-files_3.1.0ubuntu3_i386.deb var/cache/apt/archives/base-pass wd_3.5.9_i386.deb

```

Any ideas?

--->> NVM got it work, had missed to replace the horay with breezy ^^

---

### Post by rplantz on 2005-12-17
[QUOTE=gk_jam]I'm a total newbie to Linux, just got set up with Breezy and trying to follow this howto. In Step 1, first few commands go good, until

sudo chroot /chroot/

When I do that, the terminal pops up this message:

chroot: cannot run command `/bin/bash': No such file or directory

I look inside my /bin and there's a file bash. Anyone know why it's doing this, and how to fix?[/QUOTE]

Same thing happened to me. Then I realized that in the command
```

 sudo debootstrap --arch i386 breezy /chroot/ http://archive.ubuntu.com/ubuntu

```
I had left out the space between "/chroot/" and "http://..." because I was viewing the text in a proportional font. A copy and paste revealed my error.

After my error, the ls /chroot command showed
```

http://archive.ubuntu.com/ubuntu

```

I deleted the entire /chroot/ directory and started over again. When done correctly,  the last line read:
```

I: Base system installed successfully.

```
and I see (in another terminal):
```

bob@ubuntu:~$ ls /chroot
bin   dev  home   initrd  media  opt   root  srv  tmp  var
boot  etc  http:  lib     mnt    proc  sbin  sys  usr
bob@ubuntu:~$

```

---

### Post by draven on 2005-12-20
[me@host ~]$ sudo apt-get install dchroot debootstrap
Reading package lists... Done
Building dependency tree... Done
Package dchroot is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dchroot has no installation candidate

Am I the only one with this problem?

My source.list contains

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

Do I need any others?

---

### Post by John Mytton on 2005-12-20
Thanks for this - now I can get my wine on!

(The windows emulator, that is...)

---

### Post by draven on 2005-12-21
Packages are in Universe from /etc/apt/sources.list

[QUOTE=draven][me@host ~]$ sudo apt-get install dchroot debootstrap
Reading package lists... Done
Building dependency tree... Done
Package dchroot is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dchroot has no installation candidate

Am I the only one with this problem?

My source.list contains

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

Do I need any others?[/QUOTE]

---

### Post by draven on 2005-12-21
In order to get FF32 and Flash working I had to manually install Flash by copying the files to the plguins dir. Then using synaptic32 I installed libXmu-dev.


**EDIT:**

Now I'm having a problem where I can't close any TABS in FF. If I hit the red X, use right-click // close-tab it just won't close. I can open new ones though. It works in the 64bit FF but not the chroot 32bit. It also reports no errors in the console.

---

### Post by Randomskk on 2006-01-09
Heh. Just a brief post, but if you have made the chroot and decide you want to get rid of it, it seems taking out the new lines in fstab, doing mount -a and then rm -rf /chroot really isn't the best idea.
I ended up wiping my /home, /tmp, /dev etc. 
After that I just went su, rm -rf /, because I always wanted to try that, but yeah.

Ooops. >.<.

---

### Post by wishyjr on 2006-01-10
hiya, ran through your HOWTO and it seems to have worked! cheers! i did get this error when running sudo mount -a though:
[mntent]: warning: no final newline at the end of /etc/fstab

can anyone tell me what this means?

also, im trying to run stuff with wine but im getting an error that looks like this:

paul@ubuntu:~$ wine /DATA/stuff/Brain.exe
(breezy) wine /DATA/stuff/Brain.exe
wine: cannot find '/DATA/stuff/Brain.exe'
dchroot: Child exited non-zero.
dchroot: Operation failed.

any ideas? thank you.

---

### Post by Damburger on 2006-01-11
[QUOTE=wishyjr]hiya, ran through your HOWTO and it seems to have worked! cheers! i did get this error when running sudo mount -a though:
[mntent]: warning: no final newline at the end of /etc/fstab

can anyone tell me what this means?

also, im trying to run stuff with wine but im getting an error that looks like this:

paul@ubuntu:~$ wine /DATA/stuff/Brain.exe
(breezy) wine /DATA/stuff/Brain.exe
wine: cannot find '/DATA/stuff/Brain.exe'
dchroot: Child exited non-zero.
dchroot: Operation failed.

any ideas? thank you.[/QUOTE]

I'm guessing its because the file in quest isn't in the 32 bit directory structure

I'm having a related problem - I want to know how I can directly execute a program using wine and chroot, in a single command. The path name of the program I want to wine has spaces in it, but for some reason the "s get stripped out in the process.

---

### Post by wishyjr on 2006-01-11
cheers. yeah, i thought that not long after i'd posted my question.

regarding yours though, about executing stuff directly through chroot, i used this:

sudo ln -s /usr/local/bin/do_dchroot /usr/local/bin/wine

it seems to work, but then again i havent tried it out yet. :) i can get xwine to run through it though.

---

### Post by werewolves on 2006-01-21
[QUOTE=Navyblue]I have been in following the how to. I am running Breezy, but still following the Hoary chroot, as someone here recommends to follow word by word unless I know what I am doing. Anyway when I reached the final step of  "sudo synaptic32", I get this:

```

(hoary) synaptic32
bash: synaptic32: command not found
dchroot: Child exited non-zero.
dchroot: Operation failed.

```

At the step of "sudo apt-get install synaptic", it doesn't seem to work. I got this message:

```

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_SG:en",
        LC_ALL = (unset),
        LANG = "en_SG.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: syntax error: unknown group `postdrop' in statusoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Any clue?

Thanks :)[/QUOTE]


Anyone have a solution for this yet?  I am having exactly the same issues.

**EDIT:**
no idea why but I decided to try changing all 'hoary' references to 'dapper' and it worked fine, and I have FireFox 1.5 :)

---

### Post by tartarin on 2006-01-26
```

sarac@zenc:~$ dchroot -d
Executing shell in 'hoary' chroot.
sarac@zenc:~$ sudo apt-get install synaptic
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  defoma docbook-xml fontconfig laptop-detect libatk1.0-0 libexpat1
  libfontconfig1 libfreetype6 libglade2-0 libglib2.0-0 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libjpeg62 libpango1.0-0 libpango1.0-common
  libpng12-0 libscrollkeeper0 libtiff4 libvte-common libvte4 libx11-6
  libxcursor1 libxext6 libxft2 libxi6 libxinerama1 libxml2 libxrandr2
  libxrender1 libxslt1.1 perl perl-modules scrollkeeper sgml-base sgml-data
  ttf-bitstream-vera ucf xlibs-data xml-core xorg-common
Suggested packages:
  defoma-doc psfontmgr x-ttcidfont-conf dfontmgr docbook docbook-doc
  docbook-dsssl docbook-xsl libfreetype6-dev ttf-kochi-gothic ttf-kochi-mincho
  ttf-thryomanes ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp
  ttf-arphic-gkai00mp ttf-arphic-bkai00mp perl-doc libterm-readline-perl-perl
  sgml-base-doc perlsgml doc-html-w3 opensp libxml2-utils debhelper
  x-window-system-core x-window-system
Recommended packages:
  libft-perl libatk1.0-data libglib2.0-data hicolor-icon-theme gksu deborphan
  libgnome2-perl
The following NEW packages will be installed:
  defoma docbook-xml fontconfig laptop-detect libatk1.0-0 libexpat1
  libfontconfig1 libfreetype6 libglade2-0 libglib2.0-0 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libjpeg62 libpango1.0-0 libpango1.0-common
  libpng12-0 libscrollkeeper0 libtiff4 libvte-common libvte4 libx11-6
  libxcursor1 libxext6 libxft2 libxi6 libxinerama1 libxml2 libxrandr2
  libxrender1 libxslt1.1 perl perl-modules scrollkeeper sgml-base sgml-data
  synaptic ttf-bitstream-vera ucf xlibs-data xml-core xorg-common
0 upgraded, 42 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/19.4MB of archives.
After unpacking 70.7MB of additional disk space will be used.
Do you want to continue [Y/n]?
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: syntax error: unknown group `postdrop' in statusoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
sarac@zenc:~$

```

I also have this unknown group 'postdrop' error. Upto that point everything went well. Has anyone solved this problem? [-o<

---

### Post by tartarin on 2006-01-26
[QUOTE=tartarin]```

sarac@zenc:~$ dchroot -d
Executing shell in 'hoary' chroot.
sarac@zenc:~$ sudo apt-get install synaptic
Password:
Reading package lists... Done
Building dependency tree... Done
.
..
...
After unpacking 70.7MB of additional disk space will be used.
Do you want to continue [Y/n]?
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: syntax error: unknown group `postdrop' in statusoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
sarac@zenc:~$

```

I have found a solution to this problem but i'm not sure why something like this happened.

My /var/lib/dpkg/statoverride file is like this:
hplip root 755 /var/run/hplip
----

but if i cat /chroot/var/lib/dpkg/statoverride i get (i have no idea why):
root postdrop 02555 /usr/sbin/postqueue
postfix postdrop 02710 /var/spool/postfix/public
root postdrop 02555 /usr/sbin/postdrop
-------

When i delete the lines that has postdrop postfix groups or users the problem solved. 

One alternative might be adding group and user
addgroup postdrop
adduser postfix

I have no idea what will be the impacts, or is it safe to do this, but i could install the synaptic after these edits.

---

### Post by o_O on 2006-01-30
Ok, so I'm having trouble with getting synaptic32 to run in the chrooted environment. I followed this guide step by step, only replacing all instances of "hoary" with "breezy", and when I run the synaptic32 command, it just shows the following: 

```

username@ubuntu:~$ sudo synaptic32
(breezy) synaptic32
bash: synaptic32: command not found
dchroot: Child exited non-zero.
dchroot: Operation failed.

```

I tried to mount the directories one by one, simlinking them... Nothing worked. 

This is a copy of my /etc/fstab file, just in case it's needed:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults	0       0
/dev/sda6       /media/sda5     vfat    iocharset=utf8,umask=000   0       0
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdc        /media/usb0     auto    rw,user,noauto  0       0

#dchroot

/home /chroot/home none bind 0 0
/tmp /chroot/tmp none bind 0 0
/dev /chroot/dev none bind 0 0
/proc /chroot/proc proc defaults 0 0
/media/cdrom0 /chroot/media/cdrom0 none bind 0 0
/usr/share/fonts /chroot/usr/share/fonts none bind 0 0

```

Any ideas?

[Off-topic] P.S: BTW, "iocharset=utf8,umask=000   0       0" doesn't seem to work for my FAT32 partition, since it sets permissions to 555 which doesn't let anyone write to it. I can't chmod nor chown it, not even as root... So what gives? [/Off-topic]

Thanks in advance for any help that you may provide.

---

### Post by Alabama_Man on 2006-01-31
my usb-gamepad only works with a generic driver(2 buttons, 2 axis!!!) in chroot, although it works perfect in my normal enviroment. In jscalibrator thc console gives this error message:
Failed to set joystick /dev/js0 correction values: Invalid argument
does anybody know how to fix this?

---

### Post by exp(x) on 2006-02-09
[QUOTE=Alabama_Man]my usb-gamepad only works with a generic driver(2 buttons, 2 axis!!!) in chroot, although it works perfect in my normal enviroment.[/QUOTE]
I have the same problem with my xbox controller. If you figure anything out, post here.

---

### Post by pvgorp on 2006-02-14
Hi all,
I've followed your instructions but cannot apt-get install anything after "dchroot -d".

The system complains:
> dpkg: syntax error: unknown user `postfix' in statusoverride file

Have I missed something?  Note that I'm using shadowed passwords.

Thanks for your advice,
Pieter Van Gorp

---

### Post by pvgorp on 2006-02-14
I solved the problem by creating a user 'postfix' in group 'postdrop':
adduser --ingroup postdrop postfix

This was suggested in another thread. 

Cheers,
Pieter.

---

### Post by jrblevin on 2006-02-28
In response to the perl locale problems mentioned earlier (perl: warning: Setting locale failed), installing language-pack-en-base seemed to fix it for me.

---

### Post by jinxed on 2006-03-07
n00b question:
Everthing went well... even ran synaptic, but after restarting my machine, I can't run anything using X. Here's my output...
```
(synaptic:11343): Gtk-WARNING **: cannot open display:
```
Any ideas?

:???:

---

### Post by jinxed on 2006-03-07
[QUOTE=jinxed]n00b question:
Everthing went well... even ran synaptic, but after restarting my machine, I can't run anything using X. Here's my output...
```
(synaptic:11343): Gtk-WARNING **: cannot open display:
```
Any ideas?

:???:[/QUOTE]

Nevermind... I'm a moron :oops: 

forgot to use the -d option...

---

### Post by mune on 2006-03-11
I have been reading this looooong thread but I haven't found any answer to my (simple) problem.

I applied the how-to and it worked fine (btw  GREAT thanks a lot).

My problem is that the 32 bit applications (such as firefox32) are in english and not in my own language (as all other apps).

Does anybody have a tip?

Thanks

Fede

---

### Post by mune on 2006-03-17
I can live with en_US messages.

I had big big huge problem: all the applications x32 couldn't print. Now it is worse.

I thought "I do a smart thing: I install cups+gnome-cups-manager, in the 32 environment and I'll be allset".:-D 

I end up that I can't print from the original 64 bit environment and I still can't print from the x32 application.:evil: 

What can I do, now?

Thanks

Fede

---

### Post by DragonOrta on 2006-04-02
When ever I run "dpkg-reconfigure locales" and select and of the en_US locales, I get this error.
> root@dragon64:/# dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_CTYPE to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_MESSAGES to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_ALL to default locale: No such file or directory

I've also tried setting to a different english, such as GB, but I still get that error.

---

### Post by slim_chiply on 2006-04-08
[QUOTE=mune]I can live with en_US messages.

I had big big huge problem: all the applications x32 couldn't print. Now it is worse.

I thought "I do a smart thing: I install cups+gnome-cups-manager, in the 32 environment and I'll be allset".:-D 

I end up that I can't print from the original 64 bit environment and I still can't print from the x32 application.:evil: 

What can I do, now?

Thanks

Fede[/QUOTE]

I had the same problem.  I found that there were 2 different problems not allowing me to print.  The first: upgrading my kernel to  2.6.12-10-amd64-generic caused all printing to stop.  I reverted to the previous kernel ( 2.6.12-9-amd64-generic) and printing started again.  

The second problem was printing in my chroot.  I saw on another thread that I should also install cupsys-bsd in my chroot environment.  That seems to have solved the problem of not printing.

---

### Post by BjornHaland on 2006-04-09
Error:
```
I have no name!@shapeir:/# dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_NO:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Config.pm line 16.
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 66.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (Can't locate Term/ReadLine.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/FrontEnd/Readline.pm line 5.)
debconf: falling back to frontend: Teletype
dpkg-query: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory
/usr/sbin/dpkg-reconfigure: locales is not installed
I have no name!@shapeir:/#

```](*,)
Could be this is just too much for me right now, but I gave it a try.
It would be great if someone knew what this is, and I'd appreciate any help.
But I'm willing to let it go for now anyway - do I have to uninstall this whole thing, or can I keep it here? And what steps do I have to take in order to uninstall it? Thank you.'

Oh btw, I'm using Dapper Drake, is there an incompatibility issue, perhaps?

---

### Post by DragonOrta on 2006-04-09
Ok, fixed the last error by changing it to Breezy, but now I'm getting > W: Failure trying to run: chroot /chroot mount -t proc proc /proc


after I run 

sudo debootstrap --arch i386 breezy /chroot/ [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

This is with an Athlon X2.

---

### Post by BoyOfDestiny on 2006-04-10
Ok script works and is fully tested. It makes chrooting trivial.
[http://www.ubuntuforums.org/showpost.php?p=904320&postcount=1](http://www.ubuntuforums.org/showpost.php?p=904320&postcount=1)

---

### Post by mystictim on 2006-04-17
Thanks for making chrooting so straight forward. There was one problem I couldn't access my cd drive in the chroot. I think this is becouse when the cd drive is used it's mounted over the binding "/media/cdrom0 /chroot32/media/cdrom0 none bind 0 0" in fstab effectivly hiding this binding.
I made the cd drive accessible in the chroot by mounting the cdrom drive on /chroot/media/cdrom0 (instead of /media/chdrom0) and then makeing /media/cdrom0 a symlink to /chroot/media/cdrom0.
To do this remove or comment out the following line from fstab[LIST]
[*]  /media/cdrom0 /chroot/media/cdrom0 none bind 0 0[/LIST]then modify the line for the cdrom device to:[LIST]
[*]      /dev/hdc        /chroot/media/cdrom0   udf,iso9660 user,noauto     0       0[/LIST]Make sure that /chroot/media/cdrom0 is part of the file group cdrom[LIST]
[*]      ~$ sudo chgrp cdrom /chroot/media/cdrom0[/LIST]Then make the symlink[LIST]
[*]      ~$ sudo ln -s /chroot/media/cdrom0 /media/cdrom0[/LIST]This worked for me hope it helps anyone with a similar problem.

---

### Post by ivantorresjmz on 2006-04-24
I have the same problem and also I'm working with Dapper Drake (AMD64). I've got stuck in same place. I tried twice without any luck. Does some one got it running with dapper?

Thanks!

[QUOTE=BjornHaland]Error:
```
I have no name!@shapeir:/# dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_NO:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Config.pm line 16.
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 66.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (Can't locate Term/ReadLine.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/FrontEnd/Readline.pm line 5.)
debconf: falling back to frontend: Teletype
dpkg-query: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory
/usr/sbin/dpkg-reconfigure: locales is not installed
I have no name!@shapeir:/#

```](*,)
Could be this is just too much for me right now, but I gave it a try.
It would be great if someone knew what this is, and I'd appreciate any help.
But I'm willing to let it go for now anyway - do I have to uninstall this whole thing, or can I keep it here? And what steps do I have to take in order to uninstall it? Thank you.'

Oh btw, I'm using Dapper Drake, is there an incompatibility issue, perhaps?[/QUOTE]

---

### Post by incubus on 2006-04-25
This worked for me:
[http://ubuntuforums.org/showthread.php?t=83315&page=2&highlight=file+directory+locale%3A+set+LC_CTYPE+default]("http://ubuntuforums.org/showthread.php?t=83315&page=2&highlight=file+directory+locale%3A+set+LC_CTYPE+default")

(the last suggestion)

incubus

---

### Post by ivantorresjmz on 2006-04-25
Many thanks Incubus, it worked just fine!!! :D 

[QUOTE=incubus]This worked for me:
[http://ubuntuforums.org/showthread.php?t=83315&page=2&highlight=file+directory+locale%3A+set+LC_CTYPE+default]("http://ubuntuforums.org/showthread.php?t=83315&page=2&highlight=file+directory+locale%3A+set+LC_CTYPE+default")

(the last suggestion)

incubus[/QUOTE]

---

### Post by searden on 2006-04-30
It works until i get to installing synaptic, then this happens:

searden@ubuntuamd64:~$ dchroot -d
Executing shell in 'hoary' chroot.
searden@ubuntuamd64:~$ sudo apt-get install synaptic Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  defoma docbook-xml fontconfig laptop-detect libatk1.0-0 libexpat1
  libfontconfig1 libfreetype6 libglade2-0 libglib2.0-0 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libjpeg62 libpango1.0-0 libpango1.0-common
  libpng12-0 libscrollkeeper0 libtiff4 libvte-common libvte4 libx11-6
  libxcursor1 libxext6 libxft2 libxi6 libxinerama1 libxml2 libxrandr2
  libxrender1 libxslt1.1 perl perl-modules scrollkeeper sgml-base sgml-data
  ttf-bitstream-vera ucf xlibs-data xml-core xorg-common
Suggested packages:
  defoma-doc psfontmgr x-ttcidfont-conf dfontmgr docbook docbook-doc
  docbook-dsssl docbook-xsl libfreetype6-dev ttf-kochi-gothic ttf-kochi-mincho
  ttf-thryomanes ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp
  ttf-arphic-gkai00mp ttf-arphic-bkai00mp perl-doc libterm-readline-perl-perl
  sgml-base-doc perlsgml doc-html-w3 opensp libxml2-utils debhelper
  x-window-system-core x-window-system
Recommended packages:
  libft-perl libatk1.0-data libglib2.0-data hicolor-icon-theme gksu deborphan
  libgnome2-perl
The following NEW packages will be installed:
  defoma docbook-xml fontconfig laptop-detect libatk1.0-0 libexpat1
  libfontconfig1 libfreetype6 libglade2-0 libglib2.0-0 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libjpeg62 libpango1.0-0 libpango1.0-common
  libpng12-0 libscrollkeeper0 libtiff4 libvte-common libvte4 libx11-6
  libxcursor1 libxext6 libxft2 libxi6 libxinerama1 libxml2 libxrandr2
  libxrender1 libxslt1.1 perl perl-modules scrollkeeper sgml-base sgml-data
  synaptic ttf-bitstream-vera ucf xlibs-data xml-core xorg-common
0 upgraded, 42 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/19.4MB of archives.
After unpacking 70.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: syntax error: unknown group `postdrop' in statusoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

Any suggestions? i guess i'm pretty screwed without it as i'll get dependancy probs when i try to install other apps in chroot.

---

### Post by exp(x) on 2006-05-04
I just installed some updates today in the 64-bit environment, and now the chroot is dropping network packets like crazy. I have had to switch back to 64-bit firefox.

---

### Post by leris on 2006-06-04
[QUOTE=searden]It works until i get to installing synaptic, then this happens:

searden@ubuntuamd64:~$ dchroot -d
Executing shell in 'hoary' chroot.
searden@ubuntuamd64:~$ sudo apt-get install synaptic Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  defoma docbook-xml fontconfig laptop-detect libatk1.0-0 libexpat1
  libfontconfig1 libfreetype6 libglade2-0 libglib2.0-0 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libjpeg62 libpango1.0-0 libpango1.0-common
  libpng12-0 libscrollkeeper0 libtiff4 libvte-common libvte4 libx11-6
  libxcursor1 libxext6 libxft2 libxi6 libxinerama1 libxml2 libxrandr2
  libxrender1 libxslt1.1 perl perl-modules scrollkeeper sgml-base sgml-data
  ttf-bitstream-vera ucf xlibs-data xml-core xorg-common
Suggested packages:
  defoma-doc psfontmgr x-ttcidfont-conf dfontmgr docbook docbook-doc
  docbook-dsssl docbook-xsl libfreetype6-dev ttf-kochi-gothic ttf-kochi-mincho
  ttf-thryomanes ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp
  ttf-arphic-gkai00mp ttf-arphic-bkai00mp perl-doc libterm-readline-perl-perl
  sgml-base-doc perlsgml doc-html-w3 opensp libxml2-utils debhelper
  x-window-system-core x-window-system
Recommended packages:
  libft-perl libatk1.0-data libglib2.0-data hicolor-icon-theme gksu deborphan
  libgnome2-perl
The following NEW packages will be installed:
  defoma docbook-xml fontconfig laptop-detect libatk1.0-0 libexpat1
  libfontconfig1 libfreetype6 libglade2-0 libglib2.0-0 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libjpeg62 libpango1.0-0 libpango1.0-common
  libpng12-0 libscrollkeeper0 libtiff4 libvte-common libvte4 libx11-6
  libxcursor1 libxext6 libxft2 libxi6 libxinerama1 libxml2 libxrandr2
  libxrender1 libxslt1.1 perl perl-modules scrollkeeper sgml-base sgml-data
  synaptic ttf-bitstream-vera ucf xlibs-data xml-core xorg-common
0 upgraded, 42 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/19.4MB of archives.
After unpacking 70.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: syntax error: unknown group `postdrop' in statusoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

Any suggestions? i guess i'm pretty screwed without it as i'll get dependancy probs when i try to install other apps in chroot.[/QUOTE]

Not sure if you've worked it out, but after beating my head in and trolling countless forums (in german is where i found the answer), I've found that under /chroot/var/lib/dpkg/statoverride (a text file), there are some references there that dpkg doesn't find.

Therefore, I backed up the file, and removed ALL entries in it.  Worked after that. I also read somewhere that you could do dpkg --clean or something along those lines, but my version of dpkg did not support any command similar to that.

Hope it helps.

---

### Post by holomorph on 2006-06-05
on step 3, apt-get update complains about being unable to verify signatures (and similarly apt-get install complains about not being able to authenticate packages); this doesn't actually hurt anything, but can be confusing.  doing 'apt-get install gnupg' and then apt-get update will make these go away.

---

### Post by dysphoros on 2006-06-07
[QUOTE=BjornHaland]Error:
[code]I have no name!@shapeir:/# dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_NO:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
[/QUOTE]

I got rid of this error by executing:

$ sudo cp /var/lib/locales/supported.d/local /chroot/var/lib/locales/supported.d/

Then run dpkg-reconfigure locales again.  I don't know about the rest of the errors though.

Sheldon

---

### Post by bforbes on 2006-06-09
I can't get past this point:

> 
bforbes@ben:~$ sudo debootstrap --arch i386 breezy /chroot/ [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
I: Retrieving Release
I: Retrieving Packages
I: Validating Packages
I: Checking component main on [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)...

It just sits there not doing anything. What can I do to fix this?

EDIT: Never mind, it finally worked. Now I have to work out what to do with this chroot.

---

### Post by bforbes on 2006-06-09
Now I have another problem. I compiled mplayer with the Win32 codecs, but there doesn't seem to be any video_out devices. How do I install them in the chroot?

Here's the output from "mplayer -vo help" in the chroot:
> 
Available video output drivers:
        fbdev   Framebuffer Device
        fbdev2  Framebuffer Device
        vesa    VESA VBE 2.0 video output
        cvidix  console VIDIX
        null    Null video output
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame


Here's the list I get outside the chroot:
> 
Available video output drivers:
        xv      X11/Xv
        x11     X11 ( XImage/Shm )
        xover   General X11 driver for overlay capable video output drivers
        gl      X11 (OpenGL)
        gl2     X11 (OpenGL) - multiple textures version
        dga     DGA ( Direct Graphic Access V2.0 )
        sdl     SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
        ggi     General Graphics Interface (GGI) output
        fbdev   Framebuffer Device
        fbdev2  Framebuffer Device
        aa      AAlib
        caca    libcaca
        dxr3    DXR3/H+ video out
        directfb        Direct Framebuffer Device
        dfbmga  DirectFB / Matrox G200/G400/G450/G550
        null    Null video output
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        png     PNG file
        jpeg    JPEG file
        gif89a  animated GIF output
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame


---

### Post by norv on 2006-06-10
Great howto, got 32-bit firefox, flash, mplayer working in chroot dapper inside dapper amd64. Thanx Crad!
I have another OS on other partitions, how can I get the chroot to see these partitions?

Here is my /etc/fstab:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda10      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

#debian sid
/dev/sda3	/mnt/pan64root	ext3	rw,user,noauto	0	0
/dev/sda5	/mnt/pan64usr	ext3	rw,user,noauto	0	0
/dev/sda6	/mnt/pan64var	ext3	rw,user,noauto	0	0
/dev/sda9	/mnt/pan64home	ext3	rw,user,noauto	0	0

#chroot
/home		/chroot/home	none	bind		0	0
/tmp		/chroot/tmp	none	bind		0	0
/dev		/chroot/dev	none	bind		0	0
/proc		/chroot/proc	proc	defaults	0	0
/media/cdrom0	/chroot/media/cdrom0 none bind 	0	0
/usr/share/fonts /chroot/usr/share/fonts none bind	0	0

```

I want the chroot to be able to see /dev/sda9, my debian home partition.

---

### Post by bforbes on 2006-06-10
I'd try:


1. Add to fstab:
> 
/dev/sda9 /chroot/mnt/pan64home none bind 0 0

2. Get into the chroot
3. Add the mount point /mnt/pan64home

Because the chroot doesn't know about anything outside unless you tell it.

---

### Post by norv on 2006-06-10
Thanx, I tried that, here is the result:
```

norbreezy@norbreezy:~$ dchroot -d
Executing shell in 'dapper' chroot.
norbreezy@norbreezy:~$ mount /mnt/pan64home
mount: can't find /mnt/pan64home in /etc/fstab or /etc/mtab
norbreezy@norbreezy:~$ exit
exit
dchroot: Child exited non-zero.
dchroot: Operation failed.
norbreezy@norbreezy:~$ mount /chroot/mnt/pan64home
mount: only root can mount /dev/sda9 on /chroot/mnt/pan64home
norbreezy@norbreezy:~$ sudo mount /chroot/mnt/pan64home
mount: Not a directory
norbreezy@norbreezy:~$ ls -ln /chroot/mnt
total 4
drwxr-xr-x 2 0 0 4096 2006-06-10 17:20 pan64home
norbreezy@norbreezy:~$

```
Any ideas?

---

### Post by bforbes on 2006-06-10
Okay, I got it to work on mine. Don't bind the device to the chrooted mount point, bind the normal mount point to the chrooted mount point:
> 
/mnt/pan64home /chroot/mnt/pan64home none bind 0 0


---

### Post by bforbes on 2006-06-10
I got my mplayer problem to work. Before compiling, I installed libx11-dev and libxv-dev.

Now I'm having issues with Firefox. I installed the latest Firefox in the chroot, and got flash working on it, but whenever I run normal Firefox after running chrooted Firefox, it checks for compatibility updates for my extensions, then loads up the "Latest Firefox" page. It also happens the other way round, ie, running chrooted Firefox after normal Firefox.

Can I get rid of this behaviour? I tried disabling all the update options but that doesn't change anything.

---

### Post by norv on 2006-06-12
Thanx bforbes, still can't get it to work..
```
norbreezy@norbreezy:~$ mount /dev/sda9
norbreezy@norbreezy:~$ mount /mnt/pan64home
mount: according to mtab, /mnt/pan64home is mounted on /mnt/pan64home
mount failed
norbreezy@norbreezy:~$ mount /chroot/mnt/pan64home
mount: according to mtab, /mnt/pan64home is mounted on /mnt/pan64home
mount failed
norbreezy@norbreezy:~$ ls /mnt/pan64home
bookmarks.html house lost+found norv ubuntu
norbreezy@norbreezy:~$ dchroot -d
Executing shell in 'dapper' chroot.
norbreezy@norbreezy:~$ ls /mnt/pan64home
norbreezy@norbreezy:~$ exit
exit
norbreezy@norbreezy:~$

```
What mount command should I use, should I be trying the mount command from within the chroot? That gives me a "no fstab or mtab" error..
```
norbreezy@norbreezy:~$ dchroot -d
Executing shell in 'dapper' chroot.
norbreezy@norbreezy:~$ more /etc/fstab
# UNCONFIGURED FSTAB FOR BASE SYSTEM
norbreezy@norbreezy:~$
norbreezy@norbreezy:~$ exit

```

---

### Post by bforbes on 2006-06-12
No, all the mounting has to be done from outside the chroot. Use the instructions I posted above, doing everything from fstab. Then outside the chroot do "sudo mount -a" to mount everything. Inside the chroot it should be mounted fine.

EDIT:

To clarify:

1. Add to fstab outside the chroot:
> 
/mnt/pan64home /chroot/mnt/pan64home none bind 0 0

2. Get into the chroot
3. sudo mkdir /mnt/pan64home
4. Get out of the chroot
5. sudo mount -a

---

### Post by norv on 2006-06-13
Sorry bforbes, looks like I'm a dumbass.
I have:
a) /dev/sda9, mount-point,  /mnt/pan64home
b) /mnt/pan64home, mount-point /chroot/mnt/pan64home
c) sudo mount -a does not mount /dev/sda9 (because of noauto option???)
d) /chroot/mnt/pan64home exists
e)chroot still cannot see inside pan64home
f) I have to mount /dev/sda9 specifically to see into pan64home from outside chroot
g) chroot still cannot see inside pan64home

As shown in this snippet:
```

norbreezy@norbreezy:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda10      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

#debian sid
/dev/sda3       /mnt/pan64root  ext3    rw,user,noauto  0       0
/dev/sda5       /mnt/pan64usr   ext3    rw,user,noauto  0       0
/dev/sda6       /mnt/pan64var   ext3    rw,user,noauto  0       0
/dev/sda9       /mnt/pan64home  ext3    rw,user,noauto  0       0

#chroot
/home           /chroot/home    none    bind            0       0
/tmp            /chroot/tmp     none    bind            0       0
/dev            /chroot/dev     none    bind            0       0
/proc           /chroot/proc    proc    defaults        0       0
/media/cdrom0   /chroot/media/cdrom0 none bind  0       0
/usr/share/fonts /chroot/usr/share/fonts none bind      0       0

/mnt/pan64home  /chroot/mnt/pan64home   none    bind    0       0
norbreezy@norbreezy:~$ sudo mount -a
norbreezy@norbreezy:~$ ls /mnt/pan64home
norbreezy@norbreezy:~$ ls /chroot/mnt
pan64home
norbreezy@norbreezy:~$ dchroot -d
Executing shell in 'dapper' chroot.
norbreezy@norbreezy:~$ ls /mnt/pan64home
norbreezy@norbreezy:~$ exit
exit
norbreezy@norbreezy:~$ mount /dev/sda9
norbreezy@norbreezy:~$ ls /mnt/pan64home
bookmarks.html  house  lost+found  norv  ubuntu
norbreezy@norbreezy:~$
norbreezy@norbreezy:~$ dchroot -d
Executing shell in 'dapper' chroot.
norbreezy@norbreezy:~$ ls /mnt/pan64home
norbreezy@norbreezy:~$

```

---

### Post by bforbes on 2006-06-14
Okay, without using "sudo mount -a" I did this:

1. Remove the fstab line binding /mnt/pan64home to /chroot/mnt/pan64home
2. sudo umount /mnt/pan64home;sudo umount /chroot/mnt/pan64home
3. mount /mnt/pan64home
4. mount -o bind /mnt/pan64home /chroot/mnt/pan64home

Then it should all be good.

---

### Post by norv on 2006-06-14
**Yes!** Got it! Thank you very much for all your help **bforbes**!

---

### Post by bforbes on 2006-06-15
No problem.

---

### Post by chrestomanci on 2006-06-23
I have setup a chroot as described and it is mostly working, however I have found that I can't run commands that have spaces in the pathnames. For example if I run a command:
```
mplayer32 "/home/david/My holiday video.avi"
```
Then 32 bit mplayer complains about not being able to find the files "/home/david/My" "holiday" or "video.avi"

It looks like the quoted pathname is getting unquoted by the do_dchroot script:

[QUOTE=Crad]
Add the following:
#!/bin/sh
/usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` $*"
[/QUOTE]

I am planning to re-write the do_dchroot script (in perl) to correctly handle spaces in filenames, but I wondered if anyone else has allready solved the problem so I don't have to.

---

### Post by cesera on 2006-07-02
[QUOTE=chrestomanci]
It looks like the quoted pathname is getting unquoted by the do_dchroot script:

I am planning to re-write the do_dchroot script (in perl) to correctly handle spaces in filenames, but I wondered if anyone else has allready solved the problem so I don't have to.[/QUOTE]

On page 5 of this thread: [http://ubuntuforums.org/showpost.php?p=426504&postcount=6](http://ubuntuforums.org/showpost.php?p=426504&postcount=6)

---

### Post by jakedh on 2006-07-07
](*,) 
I have a 32 bit subsystem working...to some extent. It has been the cause of many headaches and it's getting to the point where I can't justify using it. Since I have only one application which actually needs a 64 bit environment it would seem like a better idea to install a 64 bit subsytem on a 32 bit base. So here's the querstion:
Can I do the exact opposite of what is described in this thread? I need support for a single 64 bit app in a 32 bit base system. I don't want to nuke my HDD without some confidence in this. It's this or back to M$ :( 
I have a PIV Xeon (64 bit).

---

### Post by rancio on 2006-07-08
hello, this is my first post in this forum, i'm new in this linux thing too..
i made all the steps in the guide... (pretty good for noobs like me) 
but when i do $ dchroot -d  y get teh following message:

```

Executing shell in 'hoary' chroot.
su: Authentication service cannot retrieve authentication info.
(Ignored)
```

I get this message as a common user and as root.. after it appears once, i can't switch users..

what did i do wrong?

thanx

---

### Post by keoghan on 2006-07-12
Thanks for this how to, I just used it on a dapper setup with a little substitution (dapper for hoary) and it worked great!

Also used the fstab entries for passwd, shadow, group etc. Everything seems to be working fantastically.

Good Stuff!

K

---

### Post by cesera on 2006-07-25
Thank you for this howto. It works well for me (on dapper). I have however one little problem. I have some of my home directories on seperate partitions, and even though I have added:
```
/home /chroot/home none bind 0 0
```
to my /etc/fstab file I cannot enter the home directories that are on seperate partitions (mounted on /home/<user>), but the home directories that are just normal directories on /home work fine, any idea what causes this?
 
PS. just tested some other partitions mounted within the directory structure, and I don't seem to be able to cross the mount-point boundary from within the chroot environment.

---

### Post by chrestomanci on 2006-07-26
> **cesera said:**
> Thank you for this howto. It works well for me (on dapper). I have however one little problem. I have some of my home directories on separate partitions, and even though I have added:
```
/home /chroot/home none bind 0 0
```
to my /etc/fstab file I cannot enter the home directories that are on separate partitions (mounted on /home/<user>), but the home directories that are just normal directories on /home work fine, any idea what causes this?

The solution is to create similar chroot mounts for each mounted partition on your system, so in your case a section of your /etc/fstab might look like this:

```

# Separate mounts for each user's home dir
/dev/sdb1   /home/alice     ext3    none    0   2
/dev/sdb2   /home/bob       ext3    none    0   2
/dev/sdb3   /home/charles   ext3    none    0   2
/dev/sdb4   /home/david     ext3    none    0   2

# Chroot mount points so that users can access their files using 32bit chroot programs
/home/alice     /chroot/home/alice     none bind    0   0
/home/bob       /chroot/home/bob       none bind    0   0
/home/charles   /chroot/home/charles   none bind    0   0
/home/david     /chroot/home/david     none bind    0   0

```

You will also need to create a chroot mount point for each removable device that you want to use. Also if you have more than one chroot environment setup you will need to create a set of these mount points for each environment.

Needless to say this is all a bit of a pain if you have loads of partitions and several chroot environments. I am working on a script to automate the process.

---

### Post by cesera on 2006-08-21
I used the 32-bit chroot successfully for a while and then came to a point where I didn't need it anymore. So I removed the /chroot from my system, this took a lot longer than I expected so I cancelled it and looked what was happening. To my horror I realised that my home directory was mounted within /chroot (I had forgotten about this) and was now mostly empty. (Thankfully I had a backup.)

Moral of the story: umount everything mounted within /chroot before removing it. (Maybe it is wise to add a warning to the howto, in case there are other idiots like me out there.)

---

### Post by flygin on 2006-08-26
symlink an application to chroot including man pages, doc folders, menu (!), icons and .desktop file

check it out here:

[http://www.geocities.com/thierryguy/](http://www.geocities.com/thierryguy/)

---

### Post by fireandlight27 on 2006-08-31
Works great for me under Dapper.  Thanks for the great how-to.  The one thing I've noticed that doesn't work is mail-to links.  Clicking on a mail-to link has no effect.  Is there a way to fix this without installing a mail client in the chroot?

---

### Post by chrestomanci on 2006-08-31
> **fireandlight27 said:**
> Works great for me under Dapper.  Thanks for the great how-to.  The one thing I've noticed that doesn't work is mail-to links.  Clicking on a mail-to link has no effect.  Is there a way to fix this without installing a mail client in the chroot?

Not easily. Unfortunately this is a bit of a thorny problem.

When you click on a mailto: link, your web browser attempts to start an email program so that you can compose and send your mail message. The problem is that programs running inside the chroot cannot see outside it, so they cannot access your mail program.

As you suggest, one solution would be to install a mail client inside the chroot, and to configure your browser inside the chroot to use it. There would be some problems with this, one is that the mail client inside the chroot might confuse your normal one if they are both running at the same time and try to access the same locally stored folders. If the mail client has its own separate set of folders, then your mail messages would not all be together, and if you where looking for a message you sent some time ago, you would have to look in both mail clients. Both these problems can be solved by keeping your mail folders on an IMAP server, and having both clients talk to that server.

Also, the mail client would not be able to see your copy of sendmail, though this is unlikely to be a problem as most clients default to sending mail using TCP/IP sockets rather than calling sendmail directly.

An alternative solution would be to find a way to invoke programs in the parent system from within the chroot. It should be fairly easy to write a script that uses remote procedure calls to achieve this by calling out of the chroot to a listener running in the host OS. I don’t know if such a script or program is available. If you can’t find one, and you are competent at programming you might consider writing one yourself and posting it here.

There is also a third issue if you are sending mailto links the other way, (from a browser in the host OS, to a mail client in the chroot). Currently when the do_chroot script passes program arguments to the chroot, it does not protect special characters from being interpreted by the shell, so a command line such as: 
```
thunderbird ‘john.doe@example.com’
```
Will get messed up because the quote and @ symbols are special and will be cause errors. [Puiphooey](http://ubuntuforums.org/member.php?u=45533) has posted an alternative version that protects spaces but not any other special character. I am currently working on a do_chroot replacement to fix this and other issues.

---

### Post by feldegast on 2006-09-27
i found that you need to do the following before synaptic will install within the chroot.

apt-get install locales

---

### Post by Iesos on 2006-10-29
Hi.
Made the update to edgy a few days ago. And my chroot broke down. Now I'm trying to get it back up, by doing this guide again. But I get this error trying to enter chroot:
```
$ sudo chroot /chroot/
Password:
/bin/bash: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /bin/bash)
/bin/bash: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.3.4' not found (required by /bin/bash)
```

Anyone know anything about it?

---

### Post by ronelly on 2006-11-02
> **lestial said:**
> well as you can see this is my first post here. i'm loving this distro / community because through you guys i actually have my ati card working lol. i'm trying to set up the 32 bit environment as per this guide.. but i'm getting these errors.




Errors were encountered while processing:
 postfix
 at
 mailx
 mutt
 postfix-tls
 ubuntu-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
jimbo@ubuntu:~$ sudo ln -s /usr/sbin/synaptic /usr/sbin/synaptic32
jimbo@ubuntu:~$ exit
exit
jimbo@ubuntu:~$ sudo ln -s /usr/local/bin/do_dchroot /usr/local/bin/synaptic32
jimbo@ubuntu:~$ sudo synaptic32
(hoary) synaptic32

(synaptic32:28009): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

any help would be appreciated, i'm all aquiver at the idea of finally being able to leave behind windows. if i can get this 32 bit setup.. set up, then wow working.. i wouldn't need windows for anything anymore :)


hi,
I am having the same problem. did you manage to solve it? I appreciate any help!
thanx,
ronny

---

### Post by Funzo22 on 2006-11-02
> **Iesos said:**
> Hi.
Made the update to edgy a few days ago. And my chroot broke down. Now I'm trying to get it back up, by doing this guide again. But I get this error trying to enter chroot:
```
$ sudo chroot /chroot/
Password:
/bin/bash: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /bin/bash)
/bin/bash: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.3.4' not found (required by /bin/bash)
```

Anyone know anything about it?


I solved this problem quite simply by reinstalling my whole chroot system, I guess this solution wont work for you if you have spent time configuring it or whatever, but if your chroot'd environment is relatively empty just do this:

```
sudo rm -r /chroot
```

and follow the guide again but replace all instances of breezy with edgy and voila a working chroot environment with edgy

---

### Post by Joybin on 2006-11-26
> **chrestomanci said:**
> Currently when the do_chroot script passes program arguments to the chroot, it does not protect special characters from being interpreted by the shell

You can use this shell script as do_chroot to protect most special characters, except for continuous backslashes.
```
#!/bin/sh
args="`echo $0 | sed 's|^.*/\(.*\)\(32\)*$|\1|'`"
for arg; do
    args="$args `echo $arg | sed 's|\([^-_a-zA-Z0-9]\)|\\\\\1|g'`"
done
/usr/bin/dchroot -d "$args"
```

---

### Post by petriborg on 2006-12-14
Here is an update to make the whole do_dchroot process easier.

```

#!/bin/sh
args="`echo $0 | perl -e '$_=<>; s/^.*\/(.*?)(32)?$/\1/; print; '`"
for arg; do
    args="$args `echo $arg | sed 's|\([^-_a-zA-Z0-9]\)|\\\\\1|g'`"
done
if [ -e /usr/bin/linux32 ]; then
    /usr/bin/linux32 /usr/bin/dchroot -d "$args"
else
    /usr/bin/dchroot -d "$args"
fi

```

Because of the change in do_dchroot step five becomes simpler:
[LIST]
[*] dchroot -d
[*] sudo apt-get install synaptic
[*] [COLOR="Red"]sudo ln -s /usr/sbin/synaptic /usr/sbin/synaptic32 (DELETE, NO LONGER NEEDED)[/COLOR]
[*] exit
[*] sudo ln -s /usr/local/bin/do_dchroot /usr/local/bin/synaptic32
[*] sudo synaptic32
[/LIST]

This is a small change to the regex to allow this. This makes one assumption, the 64 bit program is not visible from within the 32bit chroot - which would make sense, after all we just spent all that time making a seperate area for the 32 bit programs! If there is no 32 at the end of the name it will ignore it and try and launch the program in the chroot anyway. The corrected handling of 32 required a non-greedy operator which I don't think seds can do (which is why it now uses perl).

I also added a check for linux32 for those that need to do compiling in the chroot, this should automatically run the chroot with linux32 in front if it exists.

---

### Post by petriborg on 2006-12-17
On a side note, you can *also* add another detail, under Dapper, if you add a file named "debian_chroot" to the /chroot/etc directory, the default profile will append the content of the file at the start of the PS1 variable. For example, if you put "dapper32" in the file it displays: (dapper32)petri@linuxbox:~$

How cool is *that*

---

### Post by hacktorious on 2007-01-29
I followed the directions from this thread.  I am running the sudo synaptic32 command and getting the following error message:

scott@zeus:~/downloads/BasicStamp$ sudo synaptic32
I: [edgy chroot] Running command: &#8220;synaptic32 &#8221;

(synaptic32:29339): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.


Does anyone know what is going wrong here and how I can fix it?  Thanks.

I am running Kubuntu 6.10.

---

### Post by babwe on 2007-02-07
im running Ubuntu 6.06 LTS on a 64-bit pc
getting this error in step 1 line 5
Failure trying to run: chroot /chroot dpkg --force-depends --install var/cache/apt/archives/base-files_3.1.0ubuntu3_i386.deb var/cache/apt/archives/base-passwd_3.5.9_i386.deb
dont know what t do 

note: Im trying to run xchat with support of [http://fish.sekure.us/](http://fish.sekure.us/). cant get that t run on the pc :(

---

### Post by gbajosh on 2007-02-08
HI!

I am very new to Linux, but am enjoying learning about it.  When I try to do this I get this

josh120@josh120-desktop:~$ sudo apt-get install dchroot debootstrap
Password:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dchroot


Whenever I try to apt getupdate it never connects.  Same with Add/remove, it says "Downloading 1/35" and does nothing.  I have been working on this 1 problem for a few days now and am lost.

PLEASE HELP!

Thanks so much

---

### Post by kragen on 2007-02-20
hey, nice guide - worked a treat for me, simply had to install an extra package to get around a locale problem, but apart from that it was plain sailing :D

two things:

1) All my apps look ugly :P How do I go about installing gtk themes in the chroot, is there any way to get the chroot to use the same themes as the rest of my desktop via another fstab mount point or something similar?

EDIT: Answered my own question here: [http://www.ubuntuforums.org/showthread.php?t=307194](http://www.ubuntuforums.org/showthread.php?t=307194)

2) someone else earlier mentioned using "sudo mount --bind /etc/passwd /usr/chroot32/passwd" etc... as a neater way than simply copying all the required files, I'm a perfectionist and woud quite like to do this :P but all I get is:

```
mount: mount point /usr/chroot32/passwd does not exist
```

Should this work? I've seen this in another guide, so I'm geusing there is a way of making it work...

Thanks :)

---

### Post by cibercol on 2007-03-11
:lolflag: [http://lambda-complex.blogspot.com/2006/11/configurando-chroot-de-i386-en-una.html](http://lambda-complex.blogspot.com/2006/11/configurando-chroot-de-i386-en-una.html)
correction for locales problem

---

### Post by dukeleto on 2007-03-14
Hi all,

my chroot edgy32 under edgy 64 works, except I am unable to install dbus; I get an error
stating that "/etc/init.d/dbus start" fails; has anyone come across this or does anyone have an idea of what to do? dbus is kinda necessary for what I wanted to do!
many thanks,

Olivier

---

### Post by petriborg on 2007-03-17
> **kragen said:**
> 

2) someone else earlier mentioned using "sudo mount --bind /etc/passwd /usr/chroot32/passwd" etc... as a neater way than simply copying all the required files, I'm a perfectionist and woud quite like to do this :P but all I get is:

```
mount: mount point /usr/chroot32/passwd does not exist
```

Should this work? I've seen this in another guide, so I'm geusing there is a way of making it work...

Thanks :)

Sorry Kragen, no you can't do that, mount will only do that for folders to my knowledge.

---

### Post by hacktorious on 2007-03-17
I believe you have to copy your /etc/passwd into the same location in your chroot32 environment.

---

### Post by THEBIGEYE on 2007-04-22
when i input this command 
sudo gedit /etc/dchroot.conf
gedits says this is a directory so i cannot add the line hoary/chroot
is this an error in the direction everyone else seems to have this working also the reason i am trying to do this because i am having trouble printing after upgrading to feisty AMD64 from edgy i386 where i could print no problem so i want to see if it the 64 bit archutecture has anyone tryed this and does it work i will post if it works as a workaround

---

### Post by gavintlgold on 2007-04-26
Uhh.. I did this, but I don't need it anymore. What steps should I take to remove it? Deleting /chroot ? Uninstalling some programs?

Thanks for the help. (I am using nspluginwrapper for firefox so I don't need it anymore).

---

### Post by shame on 2007-04-27
You just need to delete the chroot directory you used but VERY IMPORTANT!  Unmount everything first or it will delete the stuff that is mounted in it, such as your home directory.

---

### Post by gavintlgold on 2007-04-27
I'm sorry, but what commands would that be, and would I need to run

dchroot -d

first?

thanks

---

### Post by Soverign on 2007-06-25
umm I have a feeling I'm being very noobish here...but i have a problem on the first step...

sudo debootstrap --arch amd64 hoary /chroot/ [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
I: Retrieving Release
E: Failed getting release file [http://archive.ubuntu.com/ubuntu/dists/hoary/Release](http://archive.ubuntu.com/ubuntu/dists/hoary/Release)

(arch i386 returns the same)

and the next line returns:

sudo chroot /chroot/
chroot: cannot run command `/bin/bash': No such file or directory

Help would be GREATLY appreciated!! :)

---

### Post by p1977p on 2007-07-14
does the chroot use the pdnsd installed in the 64 bit environment? if not, how do i set it up in the chroot? The networking is very slow in chroot as comp. to that in the 64 bit environment. i tried installing it via synaptic 32-- downloads fine, but it gives an error :"failed to start pdnsd"


(Running 64bit Xubuntu feisty on AMD64 laptop)

---

### Post by alvare on 2007-08-11
sorry but I'm new in this and i don't understand this part:

> sudo debootstrap --arch i386 hoary /chroot/ [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

i copied it into the terminal and it says

> I: Retrieving Release
E: Failed getting release file [http://archive.ubuntu.com/ubuntu/dists/hoary/Release](http://archive.ubuntu.com/ubuntu/dists/hoary/Release)

can you explain me what  to do?

---

### Post by digitec on 2007-08-22
Hello, try as follow:

Step 1:

    sudo apt-get install dchroot debootstrap
    sudo mkdir /chroot/
    sudo gedit /etc/dchroot.conf
          Add this line: feisty /chroot
    sudo debootstrap --arch i386 feisty /chroot
    sudo cp /var/lib/locales/supported.d/local /chroot/var/lib/locales/supported.d
    sudo chroot /chroot
    dpkg-reconfigure locales

Step 2:
In another terminal window (or by existing chroot):

    sudo gedit /chroot/etc/apt/sources.list
    Add the following lines:
          deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
          deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

(We do this step because gedit has yet to be installed in the chroot environment)

Step 3:
In your chrooted environment (chroot /chroot):

    apt-get update ; apt-get upgrade

Step 4:
In another terminal window (or by existing chroot):

    sudo cp /etc/passwd /chroot/etc/
    sudo cp /etc/shadow /chroot/etc/
    sudo cp /etc/group /chroot/etc/
    sudo cp /etc/sudoers /chroot/etc/
    sudo cp /etc/hosts /chroot/etc/
    sudo gedit /etc/fstab
    Add the following lines:
           /home /chroot/home none bind 0 0
           /tmp /chroot/tmp none bind 0 0
           /dev /chroot/dev none bind 0 0
           /proc /chroot/proc proc defaults 0 0
           /media/cdrom0 /chroot/media/cdrom0 none bind 0 0
           /usr/share/fonts /chroot/usr/share/fonts none bind 0 0
           <snip />
     sudo mkdir /chroot/media/cdrom0
     sudo mkdir /chroot/usr/share/fonts
     sudo mount -a
     sudo gedit /usr/local/bin/do_dchroot
     Add the following:
           #!/bin/sh
          exec /usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` `for i in "$@"; do echo -n '"'$i'" '; done`"

     sudo chmod 755 /usr/local/bin/do_dchroot

Step 5:
In a new terminal:

     dchroot -d
     sudo apt-get install synaptic
     sudo ln -s /usr/sbin/synaptic /usr/sbin/synaptic32
     exit
     sudo ln -s /usr/local/bin/do_dchroot /usr/local/bin/synaptic32
     sudo synaptic32

---

### Post by TechZilla on 2007-08-28
why exactly are we chrooting in the first place??? to run 32-bit appz???

i use flash 32 on my 64-bit firefox via nspluginwrapper

skype via 32-bit libs and that new getlibs script

i dont use java but im almost pretty sure that there is a better non chroot way.....

chrooting is overkill

---

### Post by allorder on 2007-09-15
I did everything in the howto

when I do ./rolauncher game load and then I got a black screen with error: out of range ??

---

### Post by innocenceisdeath on 2007-10-01
How do I actually install 32 bit apps now I've set this up? :confused:

Ahhh help! Ever since I did this, my CD/DVD drive won't mount! Is there anything I can do?

---

### Post by brandom on 2008-08-18
Brilliant - thank you for these instructions!  Now I have a fully working 32-bit environment on my 64-bit MacBook Pro.  I was at my wits end dealing with problems compiling programs that had to be compiled in a 32-bit environment, and now those problems are gone!

You rock!  :guitar:

---

### Post by musta78 on 2008-08-26
I have problems with step 5.

When I type in sudo apt-get install synaptic in terminal
[I]
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (2)[/I]

So I tried to run apt-get update, but no luck!

Anyone?

---

### Post by lprophetl on 2008-10-07
thx gonna use it to compile 32 bit progs then install on my 64 bit system. see if it works

---

### Post by tharkban on 2008-10-28
I mostly followed these instructions, but of course updated them for using Intrepid.  I also fixed the locale problem that this tutorial leaves you with.  I'm sure this is all in the thread, but I don't care to search through it, so I'm bumping this solution.

There were some things missing from the instructions and they were
needlessly complicated, so I made my own.  This is how I setup a
32 bit chroot jail in ubuntu (intrepid specifically).

There are exactly three times in these instructions where the distribution
being used (intrepid) is mentioned.  To use a different (possibly newer version,
or a debian version) change those three places to the next distribution codename.
For the next version of ubuntu replace all instances (3) of intrepid with jaunty.

To install proprietary codecs use the following lines:

su
echo "## Medibuntu
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free" >> /etc/apt/sources.list
aptitude update
aptitude install medibuntu-keyring
aptitude update
aptitude install w64codecs # for AMD64 systems
aptitude install w32codecs # for 32 bit i386 systems


To install the 32 bit chroot jail use the following:

cd /
su
aptitude install schroot debootstrap
mkdir /chroot/
cd /chroot
debootstrap --arch=i386 intrepid /chroot [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu)
unalias cp
cp /var/lib/locales/supported.d/* /chroot/var/lib/locales/supported.d/
cp -f /etc/apt/sources.list /chroot/etc/apt/
cp -f /etc/passwd /chroot/etc/
cp -f /etc/shadow /chroot/etc/
cp -f /etc/group /chroot/etc/
cp -f /etc/sudoers /chroot/etc/
cp -f /etc/hosts /chroot/etc/
echo "##chroot
/home  /chroot/home       none    rbind  0  0
/dev   /chroot/dev        none    rbind  0  0
/etc   /chroot/etc/.root  none    bind   0  0
/proc  /chroot/proc       none    rbind  0  0
/media /chroot/media      none    rbind  0  0
/mnt   /chroot/mnt        none    rbind  0  0
/tmp   /chroot/tmp        none    rbind  0  0" >> /etc/fstab
mkdir /chroot/etc/.root
mount -a
chroot /chroot
[INDENT]  dpkg-reconfigure locales
  apt-get update
  apt-get upgrade
  apt-get install aptitude mplayer firefox
  apt-get install w32codecs flashplugin-nonfree

  # ...[/INDENT]

exit

---

### Post by el_chupacabra on 2008-12-20
Wow, this really worked. You are great. I think this should be moved to the first topic. I almost closed the window and then thought let's take a look at the last posts. :)

Great job! Thanks a lot! I managed to run Lightscribe Simple Labeler on my 64bit intrepid with your help. \\:D/

---

### Post by shirsch on 2009-01-09
I have fought my way to a working schroot installation, but there are two lingering issues I'm hoping to get help with:

One:

I'm seeing an explosion of bind mounts in the root environment's /proc/mounts file.  Looks like every schroot session is creating new ones and never cleaning them up.

Two:

My home directory is automounted from NFS and I simply cannot figure out how to bind mount the root environment's /net directory such that it appears in the chroot session.  All documentation for bind mounting seems to be aimed at developers who already understand it intimately and simply need a reminder of syntax.  For folks coming in fresh, it's just a lot of handwaving and jargon with few concrete examples - IMHO.

Is there a mailing list for schroot that anyone knows of?

Update 6/3/2009:

It does not appear possible to bind mount autofs controlled mount points.  I ended up having to start a second instance of the automounter from inside the chroot.  There is no way to have this happen automatically, since the various schroot scripts execute prior to the kernel chroot() call.  I discussed adding capability for this with the maintainer, but he didn't feel it was something he wanted to see in the code.  Ended up hacking it in for myself.

The explosion of mounts results from abended chroot sessions.  Wrote a little script to remove them automatically.

---

### Post by cibercol on 2009-06-02
> **Crad said:**
> Most of this comes from [http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap) but I wanted to put together a cleaned up version that worked for me here  (There are typos and inaccuracies on the wiki page).



At this point you should have a 32 bit environment setup with synaptic setup.  When you run synaptic32 from your main environment it will chroot execute it and all installations will be made to your 32 bit environment.  If you want to be able to easily launch 32 bit chroot apps from your 64 bit environment symlink the app name to /usr/local/bin/do_dchroot.  If you're using this as desktop system you'll probably want to use synaptic to install x, gnome, ubuntu specific themes, etc.

Please let me know of any errors, enhancements, or corrections :)
line ---> dpkg-reconfigure locales     change for:

from main 
line1 ---> cp /var/lib/locales/supported.d/local /chroot/var/lib/locales/supported.d/
line2 ---> dpkg-reconfigure locales

it's ok now.

---

### Post by mavaddat on 2009-06-04
Can someone tell me how to actually enter into the 32-bit environment? I've followed all the instructions on this tutorial, yet it is still utterly unclear how I run or compile 32-bit programs. I do ```
sudo chroot /chroot/
``` and run ```
uname -a
``` but all I get is ```
Linux mavaddat-desktop 2.6.24-23-generic #1 SMP Wed Apr 1 21:43:24 UTC 2009 x86_64 GNU/Linux
```. Doesn't this mean I'm not in a 32-bit environment?

It's all very frustrating. I just want a command line (shell) prompt that allows 32-bit compilation. (I know about the '-m32' flag in gcc, but my make depends on objects that are already pre-compiled as 64-bit).

I'm getting errors when linking. Here's my terminal output:```
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.4/../../../libgdbm.so when searching for -lgdbm
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.4/../../../libgdbm.a when searching for -lgdbm
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libgdbm.so when searching for -lgdbm
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libgdbm.a when searching for -lgdbm
/usr/bin/ld: skipping incompatible /usr/lib/libgdbm.so when searching for -lgdbm
/usr/bin/ld: skipping incompatible /usr/lib/libgdbm.a when searching for -lgdbm
/usr/bin/ld: cannot find -lgdbm
collect2: ld returned 1 exit status
make[1]: *** [obj/manager] Error 1
```

---

### Post by TSJason on 2009-06-04
```
uname -a
``` but all I get is ```
Linux mavaddat-desktop 2.6.24-23-generic #1 SMP Wed Apr 1 21:43:24 UTC 2009 x86_64 GNU/Linux
```. Doesn't this mean I'm not in a 32-bit environment?

This just means that you're running a 64-bit kernel - which should support the 32-bit environment.

---

### Post by mavaddat on 2009-06-04
> 
This just means that you're running a 64-bit kernel - which should support the 32-bit environment.Thanks, Jason. But shouldn't it be running the 32-bit kernel of the 32-bit environment? I thought that was the point. Also, is it true that ```
sudo chroot /chroot/
``` is the proper way to get into a 32-bit environment (with this tutoral)? How do I check to make sure I'm in the new environment and not the old one?

---

### Post by TSJason on 2009-06-07
mavaddat,

You might be confusing a chroot with a virtual environment. The chroot is simply an environment running within your 64-bit system. The kernel does not change. If you bootstrap with the "--arch i386" then the chroot only contains i386 libraries and as such will only be able to execute the 32-bit binaries. The 64-bit kernel supports 32-bit backwards compatibility which is why we can do this sort of chroot. We could not, for instance, create a 64-bit chroot in a system running a 32-bit kernel.

To test, you should just try building a small 32-bit application from the chroot and they check the libraries that are linked in. There should only be the 32-bit ones there.

If you're looking for a fully 32-bit install (kernel and all), I might suggest taking a look at the free VirtualBox software - or VMWare server 2 (which is free with registration at the vmware site).

---

### Post by mavaddat on 2009-06-07
> **TSJason said:**
> [...]You might be confusing a chroot with a virtual environment. [...]Yes, I definitely was having now read your post. (I am new to Linux. Can you tell?)

All this [FONT="Courier New"]chroot[/FONT] business is only a *means to an end* for me to compile a program I'm trying to get going. The error I run into is this:```
Linking obj/manager .....
============================
gcc -g -m32 -O3 -Wall -Wno-format -I/usr/include/gdbm -I../common -m32 -lpthread -lm -lgdbm -o obj/manager obj/benManagement.o obj/benMetadata.o obj/benSortedArray.o obj/manager.o obj/managerConfig.o obj/managerlib.o obj/metadata.o obj/metadata_db_ndbm.o obj/revBlockMap.o ../common/obj/blockmap.o ../common/obj/compatible.o ../common/obj/err.o ../common/obj/fllib.o ../common/obj/freeloader_comm.o ../common/obj/HashList.o ../common/obj/LinkList.o ../common/obj/logger.o ../common/obj/md5.o ../common/obj/metadata_common.o ../common/obj/parser.o ../common/obj/QBlockMap.o ../common/obj/queue.o ../common/obj/sha1.o ../common/obj/utility.o
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.4/../../../libgdbm.so when searching for -lgdbm
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.4/../../../libgdbm.a when searching for -lgdbm
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libgdbm.so when searching for -lgdbm
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libgdbm.a when searching for -lgdbm
/usr/bin/ld: skipping incompatible /usr/lib/libgdbm.so when searching for -lgdbm
/usr/bin/ld: skipping incompatible /usr/lib/libgdbm.a when searching for -lgdbm
/usr/bin/ld: cannot find -lgdbm
collect2: ld returned 1 exit status
make[1]: *** [obj/manager] Error 1
```And I'm not sure what to do with it. It seems like the 32-bit program doesn't like my 64-bit object files. What can I do about that? I would appreciate any help you might be able to provide.

---

### Post by TSJason on 2009-06-07
mavaddat,

 It seems to me that you're probably just missing some required library. Offhand, I would try installing that dev package inside your chroot environment. For instance:

```

sudo apt-get install libgdbm-dev

```

---

### Post by mavaddat on 2009-06-08
> **TSJason said:**
> It seems to me that you're probably just missing some required library. Offhand, I would try installing that dev package inside your chroot environment. For instance:```
sudo apt-get install libgdbm-dev
```I tried this, but it doesn't seem to work. I do ```
sudo chroot /chroot/
``` and then```
sudo apt-get install libgdbm-dev
```but it tells me:```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgdbm-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```Then I run [FONT="Courier New"]make[/FONT] on the program I'm trying to compile, and it tells me```
Linking obj/manager .....
============================
gcc -g -m32 -O3 -Wall -Wno-format -I/usr/include/gdbm -I../common -m32 -lpthread -lm -lgdbm -o obj/manager obj/benManagement.o obj/benMetadata.o obj/benSortedArray.o obj/manager.o obj/managerConfig.o obj/managerlib.o obj/metadata.o obj/metadata_db_ndbm.o obj/revBlockMap.o ../common/obj/HashList.o ../common/obj/LinkList.o ../common/obj/QBlockMap.o ../common/obj/blockmap.o ../common/obj/compatible.o ../common/obj/err.o ../common/obj/fllib.o ../common/obj/freeloader_comm.o ../common/obj/logger.o ../common/obj/md5.o ../common/obj/metadata_common.o ../common/obj/parser.o ../common/obj/queue.o ../common/obj/sha1.o ../common/obj/utility.o
collect2: ld terminated with signal 11 [Segmentation fault]
/usr/bin/ld: i386:x86-64 architecture of input file `obj/benManagement.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `obj/benMetadata.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `obj/benSortedArray.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `obj/manager.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `obj/managerConfig.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `obj/managerlib.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `obj/metadata.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `obj/metadata_db_ndbm.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `obj/revBlockMap.o' is incompatible with i386 output
```I'm really clueless about what to do.

---

### Post by TSJason on 2009-06-08
mavaddat,

Out of curiosity, what are you trying to compile and have you done a "make clean" since the source was put into your chroot?

---

### Post by baghery.farhad on 2009-07-10
I have installed it, and it works great!

But now I wanna install Oxford Dictionary, after "dchroot -d" and running ./installation.sh returns this error: 
> #./installation.sh
Verifying archive integrity... All good.
Uncompressing OALD7..........................
This installation doesn't support glibc-2.1 on Linux / x86_64

Please contact Loki Technical Support at [email]support@lokigames.com[/email]
The program returned an error code (1)
#
Why returns this error? how fix it?

---

### Post by nefurimu on 2009-07-12
I seem to have the all to common issue immediately after dchroot -d, however mine seems... slightly different unless I haven't paid that much attention.
Upon trying to install synaptic, I get the following issue:
```

nefurimu@Malakim:~$ dchroot -d
W: Failed to change to directory &#8216;/home/nefurimu&#8217;: No such file or directory
W: Falling back to directory &#8216;/&#8217;
I: [intrepid chroot] Running shell: &#8216;/bin/bash&#8217;
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

nefurimu@Malakim:/$ dchroot
bash: dchroot: command not found
nefurimu@Malakim:/$ dchroot -d
bash: dchroot: command not found
nefurimu@Malakim:/$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
synaptic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up dbus (1.2.4-0ubuntu1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
The system user `messagebus' already exists. Exiting.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
invoke-rc.d: initscript dbus, action "start" failed.
dpkg: error processing dbus (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of dbus-x11:
 dbus-x11 depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing dbus-x11 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg: dependency problems prevent configuration of policykit:
 policykit depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing policykit (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg: dependency problems prevent configuration of hal:
 hal depends on dbus (>= 0.61); however:
  Package dbus is not configured yet.
 hal depends on policykit (>= 0.7); however:
  Package policykit is not configured yet.
dpkg: error processing hal (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on dbus (>= 0.90); however:
  Package dbus is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of policykit-gnome:
 policykit-gnome depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 policykit-gnome depends on policykit; however:
  Package policykit is not configured yet.
 policykit-gnome depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
dpkg: error processing policykit-gnome (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of gnome-mount:
 gnome-mount depends on hal; however:
  Package hal is not configured yet.
 gnome-mount depends on policykit-gnome; however:
  Package policykit-gnome is not configured yet.
dpkg: error processing gnome-mount (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgnome2-vfs-perl:
 libgnome2-vfs-perl depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-vfs-perl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgnome2-perl:
 libgnome2-perl depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome2-perl depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnome2-perl depends on libgnomeui-0 (>= 2.22.0); however:
  Package libgnomeui-0 is not configured yet.
 libgnome2-perl depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnome2-perl depends on libgnome2-vfs-perl (>= 1.00); however:
  Package libgnome2-vfs-perl is not configured yet.
dpkg: error processing libgnome2-perl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgnomevfs2-extra:
 libgnomevfs2-extra depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomevfs2-extra (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 dbus
 dbus-x11
 policykit
 hal
 libgnomevfs2-0
 policykit-gnome
 gnome-mount
 libgnome2-0
 libbonoboui2-0
 libgnomeui-0
 libgnome2-vfs-perl
 libgnome2-perl
 libgnomevfs2-extra
E: Sub-process /usr/bin/dpkg returned an error code (1)
nefurimu@Malakim:/$ ...sigh

```Most of it is just repetitive nonsense, but being a pretty large nub, I hardly begin to assume it might not be relevant. The big issue it just at the bottom. I soooo hope that code tags are how you make posts shorter....

Anyone else encounter this? I'm trying to do a 32-bit intrepid on a 64-bit jaunty... so I wonder if there is anything else I should keep in mind (or should I just downgrade to breezy, which seems to have worked for people?)

EDIT: and just to prove myself a nub, I found it worked the second time (after a few hours), without doing anything differently... oh well... thanks anyway

---

### Post by kiers on 2010-08-19
interesting discussion!
I don't however see use of "jail" command/utility, as in
[http://manpages.ubuntu.com/manpages/lucid/man2/jail.2freebsd.html](http://manpages.ubuntu.com/manpages/lucid/man2/jail.2freebsd.html)
????

is it better to use chroot or the jail utility for firefox?

---

### Post by v0lle85 on 2010-09-18
Hi!

On my System I found it necessary to also add an additional entry for /dev/pts in my /etc/fstab. Otherwise Synaptic failed executing vte_terminal_forkpty().

---

### Post by emoguitarist06 on 2010-09-28
Does the original post in this forum still apply to [COLOR="Red"]**Lucid 64 bit?**[/COLOR]

I ask this because all of the post were prior to 10.04 and I know there was a lot of changes in 10.04 and I am personally not a linux guru so I just don't know.

My intent is to run [COLOR="Red"]**pcsx2**[/COLOR]

---

### Post by Exüberance on 2011-06-07
> **emoguitarist06 said:**
> Does the original post in this forum still apply to [COLOR=Red]**Lucid 64 bit?**[/COLOR]

I ask this because all of the post were prior to 10.04 and I know there was a lot of changes in 10.04 and I am personally not a linux guru so I just don't know.

My intent is to run [COLOR=Red]**pcsx2**[/COLOR]

Yes, it does work. Just replace every instance of "hoary" with "lucid" and do this:
**sudo cp /var/lib/locales/supported.d/* /chroot/var/lib/locales/supported.d/**
just before the last line of step 1.

Whenever I use the chroot, I get the message **bash: pkg-config: command not found**, but it still works fine.

---

### Post by YannBuntu on 2011-07-11
Dear all,
I have a related question, maybe one of you could know the answer? [http://ubuntuforums.org/showthread.php?p=11035079#post11035079](http://ubuntuforums.org/showthread.php?p=11035079#post11035079)

---

### Post by dave01945 on 2011-07-18
hi hopefully someone can help everything seems to be working in chroot except my home directory is encrypted and is not mounted properly in the chroot enviroment.

the only files i can see in chrooted home directory are the "access private data" files not the decrypted home folder contents.

i have also read elsewhere i need to change "bind" to "rbind" to the home directory in fstab i have done this but still no luck accessing home folder in chroot.

---

### Post by dave01945 on 2011-07-18
solved my own problem just needed to change the entry in fstab to be specific to username instead of the whole home directory.

so fstab in now "/home/dave /chroot/home/dave none rw,rbind 0 0" instead of "/home /chroot/home none rw,rbind 0 0"

---

### Post by dave01945 on 2011-07-18
just restarted and now the same problem cant access home folder from from chroot really don't understand this any help would be greatly appreciated

---

### Post by dave01945 on 2011-07-19
solved it now i believe the problem was fstab was mounting the home directory before it was decrypted so i removed the entry from fstab and added a mount command to ~/.config/autostart so it mounts after the home directory is decrypted

---

### Post by fatriff on 2011-11-22
And the near 7 year old thread lives to see another day..

---

### Post by mfumbesi on 2013-08-21
Thanks for this used, it mostly works. I used i386 *precise* instead of the *hoary* option.
Just struggling to install ROS and synaptic32.
Thank you.

---

