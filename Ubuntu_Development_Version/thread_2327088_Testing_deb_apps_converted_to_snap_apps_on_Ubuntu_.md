---
title: "Testing deb apps converted to snap apps on Ubuntu &amp; flavours"
date: 2016-06-07
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2016-06-07
snap find now shows Krita in its list of snaps. Krita is a KDE app. Canonical engineers are experimenting snapping various deb apps that can be used as templates to help other people snap other applications and push them into the snap store. I have heard that VLC will soon be in the snap store.

I think that it will be useful to test these snap apps on the family of Ubuntu desktop environments. Here is a screenshot of the Krita snap on Unity 7.

[ATTACH=CONFIG]269464[/ATTACH]

Regards

---

### Post by ventrical on 2016-06-07
Just for fun I am going to try and run it in Libertine on unity8 and see what happens.

Regards..

---

### Post by ventrical on 2016-06-07
Nope! It does not show up in unity8 .. . I filed a bug against libertine. The funny thing is that with yak, the raw beast on the plains of tibet, I am getting x11-apps icon but no Legacy Apps icon in unity8, but on Xenial I get legacy-apps icon  but they don't work.

krita did work in standard ubuntu unity.

I am going to try x11-apps and krita on xenial with unity8 ppa.

edit:

x11-apps does not show up in unity8 . krita runs on unity/xenial.No wild yak, no wild squirrel, no banana.

regards..

---

### Post by grahammechanical on 2016-06-10
Xubuntu 16.04 with the Krita snap installed

---

### Post by ventrical on 2016-06-10
What desktop is that running on? Certainly not unity8?

---

### Post by grahammechanical on 2016-06-10
I have given up on Unity 8 for the time being. I am working my way through the flavours to prove that snap apps install on the desktop environments of the flavours. I choose Krita because it is a KDE app that was recently snapped by Michael Hall as a way of finding out how to improve snapcraft. So, far I have Krita installed in Ubuntu Unity 7 & Xubuntu Xfce.

I am doing this on 16.04 because these snaps are supposed to be for 16.04.

I am looking for a snap that I can download and that will re-program my brain so that I know how to use these apps without needing to learn anything. :) The snaps are installing and running but do I know how to use these applications? If I do not use them, what have I proved?

Being serious for a moment, what I would really like is a Unity 8 snap that can be installed on Ubuntu snappy core. If very minimal versions of the desktop environments were snapped then Ubuntu snappy core would be the foundation of a transactional snappy minimal install. I have heard that it is unrealistic to snap ubuntu-desktop. The package would be very large. I assume that the same could be said about xubuntu-desktop and the others. But what about very minimal versions of these desktop environments with all the utilities also as snaps? That could be a future build it yourself version of Ubuntu and the flavours.

Did I say I was being serious? Dreaming more like it.

Regards.

---

### Post by mikodo on 2016-06-10
Dreaming? 

Whoever dreamed before the 80's, one could send letters over the telephone. (faxes). 

Ubuntu Community provided LXD with mini-install < GPG signatures > user download hypervisor on their machine > users install snaps specific for use.

[https://lists.ubuntu.com/archives/snapcraft/2016-June/000129.html](https://lists.ubuntu.com/archives/snapcraft/2016-June/000129.html)

---

### Post by ventrical on 2016-06-10
> **grahammechanical said:**
> 
Being serious for a moment, what I would really like is a Unity 8 snap that can be installed on Ubuntu snappy core. 

Did I say I was being serious? Dreaming more like it.

Regards.

This is where LXD is supposed to come in. Don't you remember the experiments we (I) did? I can install Midnight Commander and Htop and run that from Snappy core command line. Have not tried it since. Maybe I should.

regards..

---

### Post by ventrical on 2016-06-10
> **mikodo said:**
> Dreaming? 

Whoever dreamed before the 80's, one could send letters over the telephone. (faxes). 

Ubuntu Community provided LXD with mini-install < GPG signatures > user download hypervisor on their machine > users install snaps specific for use.

[https://lists.ubuntu.com/archives/snapcraft/2016-June/000129.html](https://lists.ubuntu.com/archives/snapcraft/2016-June/000129.html)

I was just thinking the same thing.

---

### Post by mikodo on 2016-06-11
> **mikodo said:**
> Ubuntu Community provided LXD with mini-install < GPG signatures > user download hypervisor on their machine > users install snaps specific for use.[https://lists.ubuntu.com/archives/snapcraft/2016-June/000129.html](https://lists.ubuntu.com/archives/snapcraft/2016-June/000129.html)

Please excuse me Graham, for hi-jacking your thread. I cannot get this off my mind today. It could be the future of Community Ubuntu and its' flavours.

Let me use Xubuntu as an example to, separate it from being confused with Ubuntu Snappy Core. But, one could use the Ubuntu OS as the example too.

1) Xubuntu devops put together the next rendition of Xubuntu in a LXD container. Test it untill they believe it to be stable to push to the masses of users.

2) Make this new hypervisor available to be pulled/pushed to users. (I don't know what exists for this except that, I know virtualization is used for this sort of thing across many machines today). Make it secure with GPG Handshakes. So, users would feel safe to use it just as they do with Repository installs to bare-metal as we have now.

3) Have an ever growing community driven collection of Snap Packages within the Ubuntu Snappy Core Repository to, replace debs.

4) Users would install Snaps as they were available and install debs using dpkg when they were not.

5) The testing of newer iterations of Snap and Deb libraries would be done in the LXD environment to, have newer stable Snaps available for being pulled/pushed to the users that is isolated from Xubuntu so as, to not break the current OS install for users.

6) Eventually we reach, "Transactional, image-based delta updates for the systems and applications that can always be rolled back".

Then, we would have "the way of the future" now, going at "warp speed 9". 

Now, someone play, California Dreamin' :)


[http://www.ubuntu.com/cloud/snappy](http://www.ubuntu.com/cloud/snappy)

---

### Post by grahammechanical on 2016-06-11
Lubuntu 16.04. The Krita snap app installed. First we need to install snapd because unlike Xubuntu it is not part of the default install. Then a restart is needed to put any installed snaps into the menu system. This restart is only needed the first time.

I have heard that someone is working on snapping leafpad the text editor for Lubuntu. Xubuntu's text editor is mousepad which is built from leafpad. Once the leafpad snap is complete it can be used as a template for snapping mousepad. And so things move forward little by little.

---

### Post by grahammechanical on 2016-06-15
Libreoffice 5.2.0 beta as a snap package

[https://skyfromme.wordpress.com/2016/06/14/libreoffice-5-2-0-beta2-as-a-snap-package/](https://skyfromme.wordpress.com/2016/06/14/libreoffice-5-2-0-beta2-as-a-snap-package/)

And it works

> graham@Ub1604:~$ snap list
Name         Version               Rev  Developer  Notes
libreoffice  5.2.0.0.beta2         x1              devmode
ubuntu-core  16.04+20160531.11-56  122  canonical  -


Screen shot of Writer 5.2.0 beta alongside Calc 5.1.3.2

[ATTACH=CONFIG]269592[/ATTACH]

It is the full Libreoffice suite. So, it is a massive download.  

Regards.

---

### Post by 6975 on 2016-06-15
Maybe I've to hunt .snap, .appimage package along with .deb from now on.
Great that it's finally become cross distribution distro. 
Even snapd available on Debian sid, Arch based, rpm based distros.

---

### Post by vasa1 on 2016-06-15
> **grahammechanical said:**
> Libreoffice 5.2.0 beta as a snap package
... It is the full Libreoffice suite. So, it is a massive download.  
...
That's great news! How massive? Maybe I'll give it a go. Which flavor, if that's important, did you install it on?
If I do, I'll try it on Lubuntu 16.04 (Openbox session).

Q: why the external link, isn't the author a Canonical insider? Shouldn't the snap be available via *snap find* and *sudo snap install ...*?

---

### Post by grahammechanical on 2016-06-15
The download is greater than 1 GB. If I am reading the numbers correctly. It included ubuntu core snap as this was a clean install of Ubuntu 16.04. Canonical engineers are testing the boundaries of snapcraft by doing experiments like this. They have sessions with anyone who wants to join in on something called snappy playpen.

[https://developer.ubuntu.com/en/blog/2016/06/08/snappy-playpen-kickoff-highlights/](https://developer.ubuntu.com/en/blog/2016/06/08/snappy-playpen-kickoff-highlights/)

The stuff they are working on goes into a git repository. But there is nothing stopping anyone snapping whatever deb package they like. I think they are finding their way. Nothing is set in stone. 

Regards.

P.S. The command to launch this Libreoffice snap version is

```
/snap/bin/libreoffice
```

[URL="https://github.com/ubuntu/snappy-playpen"]https://github.com/ubuntu/snappy-playpen


[/URL]

---

### Post by mc4man on 2016-06-15
> **vasa1 said:**
> That's great news! How massive? 
1GiB download, 4 GiB installed

---

### Post by vasa1 on 2016-06-15
> **mc4man said:**
> 1GiB download, 4 GiB installed
Oh! I'll go for it all the same. No shortage of space but the download will take some time. Starting soon ...

---

### Post by Bashing-om on 2016-06-15
Sure to be more snaps coming .
[http://www.omgubuntu.co.uk/2016/06/snap-to-be-universal-linux-package-format](http://www.omgubuntu.co.uk/2016/06/snap-to-be-universal-linux-package-format)

[INDENT][INDENT]making the future
[/INDENT][/INDENT]

---

### Post by ventrical on 2016-06-16
[SIZE=2]And if you want to build your own snaps with snapcraft..[/SIZE]
> 

               [FONT=Ubuntu]Hi everybody[/FONT][FONT=Ubuntu]
 [/FONT][FONT=Ubuntu]
 Just a brief note to say (with apologies :) that we have aliased this list to [/FONT][EMAIL="snapcraft@lists.snapcraft.io"][FONT=Ubuntu]snapcraft@lists.snapcraft.io[/FONT][/EMAIL][FONT=Ubuntu], please do update your address books![/FONT][FONT=Ubuntu]
 [/FONT][FONT=Ubuntu]
 [/FONT][[FONT=Ubuntu]http://snapcraft.io[/FONT]]("http://snapcraft.io")[FONT=Ubuntu]  is the new home for all snappy crafters. We thought it would be  appropriate to find a neutral space on the interwebs to celebrate the fact at snaps should now work, unmodified, on Arch, CentOS, Debian,  Elementary, Fedora, Gentoo, RHEL, SUSE... and of course the whole family  of *buntu's.[/FONT][FONT=Ubuntu]
 [/FONT][FONT=Ubuntu]
 snapd packages have landed in those distros or been submitted for  inclusion, instructions are on the site, and I'm delighted to say that  all the ISVs that I've talked to who are moving to snaps for IoT or the  desktop or the cloud, are very excited to have those snaps "Just Work" on all these other Linux distros too. We all know that  snaps are fantastic, it's wonderful to be confident that a great snap  can be used and appreciated by users regardless of their preference for  Linux distro. This is a once in a lifetime opportunity to defragment Linux apps, we're proud to be part of it and  open to sharing the benefits with everyone else who makes Linux  possible.[/FONT][FONT=Ubuntu]
 [/FONT][FONT=Ubuntu]
 Mark[/FONT][FONT=Ubuntu][/FONT]


---

### Post by vasa1 on 2016-06-16
> **mc4man said:**
> 1GiB download, 4 GiB installed
How do you get 4 GiB installed? What I downloaded is 1 GiB and /var/lib/snapd/snaps/libreoffice_x1.snap is also 1 GiB. Is there some place else to look?

---

### Post by mc4man on 2016-06-16
> **vasa1 said:**
> How do you get 4 GiB installed? What I downloaded is 1 GiB and /var/lib/snapd/snaps/libreoffice_x1.snap is also 1 GiB. Is there some place else to look?
Have a look at /snap/libreoffice/100001/usr/local/lib/libreoffice/program  - here the .so's total about 3.2 GiB
(- though not sure that it occupies that much space, a bit mysterious...

Edit: this does seem to add up though - 
```
cd /snap/libreoffice/100001/usr/local/lib/libreoffice/program && ls -lA
```

---

### Post by grahammechanical on 2016-06-16
This Libreoffice snap has just been down-sized. This post explains why the down load size is so large and also that a smaller sized snap package is now available.

[https://skyfromme.wordpress.com/2016/06/16/a-third-of-a-libreoffice-snap/](https://skyfromme.wordpress.com/2016/06/16/a-third-of-a-libreoffice-snap/)

Regards.

---

### Post by mc4man on 2016-06-16
So it looks like all those .so's are 'there', but maybe not really?
Ex. below  - lo  installed, then removed. The used space in / doesn't  change by the amount reported by ls.
 ```
$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
udev             3985760        0   3985760   0% /dev
tmpfs             801016     9776    791240   2% /run
/dev/sda6      368329824 83883828 265712892  24% /
tmpfs            4005068      328   4004740   1% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs            4005068        0   4005068   0% /sys/fs/cgroup
/dev/sda1         262144    61500    200644  24% /boot/efi
cgmfs                100        0       100   0% /run/cgmanager/fs
tmpfs             801016       76    800940   1% /run/user/1000
/dev/loop0       1040000  1040000         0 100% /snap/libreoffice/100001

doug@doug-HP-Pavilion-Notebook:~$ sudo snap remove libreoffice
Done

doug@doug-HP-Pavilion-Notebook:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
udev             3985760        0   3985760   0% /dev
tmpfs             801016     9776    791240   2% /run
/dev/sda6      368329824 82843840 266752880  24% /
tmpfs            4005068      328   4004740   1% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs            4005068        0   4005068   0% /sys/fs/cgroup
/dev/sda1         262144    61500    200644  24% /boot/efi
cgmfs                100        0       100   0% /run/cgmanager/fs
tmpfs             801016       76    800940   1% /run/user/1000

```

---

### Post by vasa1 on 2016-06-16
> **grahammechanical said:**
> This Libreoffice snap has just been down-sized. This post explains why the down load size is so large and also that a smaller sized snap package is now available.

[https://skyfromme.wordpress.com/2016/06/16/a-third-of-a-libreoffice-snap/](https://skyfromme.wordpress.com/2016/06/16/a-third-of-a-libreoffice-snap/)

Regards.
Thanks! Will try that instead.

```
07:17 PM ~ $ df
Filesystem     1K-blocks      Used Available Use% Mounted on
udev             1984912         0   1984912   0% /dev
tmpfs             400864      6396    394468   2% /run
/dev/sda6      219476804  35291040 173013876  17% /            <<<<<<
tmpfs            2004320         0   2004320   0% /dev/shm
tmpfs               5120         4      5116   1% /run/lock
tmpfs            2004320         0   2004320   0% /sys/fs/cgroup
/dev/loop1         66432     66432         0 100% /snap/ubuntu-core/122
/dev/loop0       1040000   1040000         0 100% /snap/libreoffice/x1
/dev/loop3         66304     66304         0 100% /snap/ubuntu-core/109
/dev/loop2         12416     12416         0 100% /snap/pen/1
cgmfs                100         0       100   0% /run/cgmanager/fs
tmpfs             400864         8    400856   1% /run/user/1000
/dev/sdb1      488384532 125847612 362536920  26% /media/vasa1/TOSHIBA EXT
07:17 PM ~ $ sudo snap remove libreoffice
[sudo] password for vasa1: 

Done
07:18 PM ~ $ df
Filesystem     1K-blocks      Used Available Use% Mounted on
udev             1984912         0   1984912   0% /dev
tmpfs             400864      6396    394468   2% /run
/dev/sda6      219476804  34248488 174056428  17% /            <<<<<<
tmpfs            2004320         0   2004320   0% /dev/shm
tmpfs               5120         4      5116   1% /run/lock
tmpfs            2004320         0   2004320   0% /sys/fs/cgroup
/dev/loop1         66432     66432         0 100% /snap/ubuntu-core/122
/dev/loop3         66304     66304         0 100% /snap/ubuntu-core/109
/dev/loop2         12416     12416         0 100% /snap/pen/1
cgmfs                100         0       100   0% /run/cgmanager/fs
tmpfs             400864         8    400856   1% /run/user/1000
/dev/sdb1      488384532 125847612 362536920  26% /media/vasa1/TOSHIBA EXT
07:18 PM ~ $ 

```

---

### Post by zika on 2016-06-16
You've got me contaiged and I'm not sorry... VLC is now snap instead of .deb... ;)

---

### Post by vasa1 on 2016-06-16
> **mc4man said:**
> Have a look at /snap/libreoffice/100001/usr/local/lib/libreoffice/program  - here the .so's total about 3.2 GiB
(- though not sure that it occupies that much space, a bit mysterious...

Edit: this does seem to add up though - 
```
cd /snap/libreoffice/100001/usr/local/lib/libreoffice/program && ls -lA
```

For me, it's */snap/libreoffice/_x1_* and running **ncdu** from within */snap/libreoffice* gives me 1.3 GiB with the low-fat version and from within */snap/libreoffice/_x1_/usr/local/lib/libreoffice/program*, **ncdu** gives me ~450 MiB for 598 items.

---

### Post by mikodo on 2016-06-16
Assuredly a lofty statement. Nevertheless, the promise of this for all desktops in the future, excites:

[https://insights.ubuntu.com/2016/06/14/universal-snap-packages-launch-on-multiple-linux-distros/](https://insights.ubuntu.com/2016/06/14/universal-snap-packages-launch-on-multiple-linux-distros/)

“Ubuntu MATE is delighted to be participating in the snappy initiative, with a goal of eventually snapping the complete MATE desktop. 
Collaborating with Ubuntu developers and other community contributors is a great way to share experiences and best practice,” said Martin Wimpress 
project lead of Ubuntu MATE.

---

### Post by mc4man on 2016-06-16
Finally get it to some extent. The files seen there (/snap/) for any installed snap are only 'there' while the snap is mounted. Whether they actually exist in fact when the snap is mounted or just representative, -  no clue.
In other words snaps seem to be squashfs mounted as loop devices. So if one had 25 snaps totaling 10 GiB that show as 35 GiB when mounted  does one need the extra 25 GiB available/ (I'm guessing not.. but don't know really.  

(- atm vlc is only good for silent vids that are in the ~/snap/vlc/3 folder

---

### Post by vasa1 on 2016-06-17
> **grahammechanical said:**
> This Libreoffice snap has just been down-sized. This post explains why the down load size is so large and also that a smaller sized snap package is now available.

[https://skyfromme.wordpress.com/2016/06/16/a-third-of-a-libreoffice-snap/](https://skyfromme.wordpress.com/2016/06/16/a-third-of-a-libreoffice-snap/)

Regards.The 1 GiB version got a lot of stick here: [https://www.phoronix.com/forums/forum/phoronix/latest-phoronix-articles/878423-playing-around-with-ubuntu-s-snaps-on-fedora](https://www.phoronix.com/forums/forum/phoronix/latest-phoronix-articles/878423-playing-around-with-ubuntu-s-snaps-on-fedora). 

The 1 GiB download also provoked a running argument about bandwidth and ISPs and nationalities and whatever. 

Only in comment #69 did someone called mhall119 attempt a partial clarification.

And in comment #92 someone called popey posted the information about the 287 MiB version.

And someone called markshuttle appears by comment #95 :)

---

### Post by grahammechanical on 2016-06-17
I knew it was a mistake. From the beginning I knew it was a mistake but no one would listen. Freedom of speech. Once, people get the idea that they are free to speak whatever they like then nothing will stop them from speaking such utter nonsense. 

mhall119 = Michael Hall = Canonical community manager. popey = Alan Pope = Canonical Community team. Both are programmers and are co-hosts of the Ubuntu community Q & A every Tuesday on Ubuntu on Air. Also co-hosting the Q & A are Daniel Hobach and David Planella. I think it was Michael Hall who snapped Krita.

 markshuttle = who he? :)

Joking aside, There is an issue with snaps that we are going to have to get used to or find a work around. It is the inability to access folders/files on other partitions. This Libreoffice snap does not present the usual file open dialog. 

I tried Tools>Options>General>Open/Save Dialogs>untick Use Libreoffice dialogs hoping that would present a nautilus open dialog but it made the Open icon inactive and when I used File>Open Libreoffice blinked out of existence.

On the other hand, it will let you access and online storage service. Which I do not have. So, I cannot test that.

I am going to experiment with symlinks to see if that is a method for accessing documents on my Data partition. I am certain that these things will be sorted out in time. But for now it is time to experiment and become frustrated.

Regards.

---

### Post by ventrical on 2016-06-17
> **mc4man said:**
> Finally get it to some extent. The files seen there (/snap/) for any installed snap are only 'there' while the snap is mounted. Whether they actually exist in fact when the snap is mounted or just representative, -  no clue.
In other words snaps seem to be squashfs mounted as loop devices. So if one had 25 snaps totaling 10 GiB that show as 35 GiB when mounted  does one need the extra 25 GiB available/ (I'm guessing not.. but don't know really.  

(- atm vlc is only good for silent vids that are in the ~/snap/vlc/3 folder

I can run vids from USB drive but get no sound and this:

```


ventrical@ventrical-MS-7798:~$ vlc
VLC media player 3.0.0-git Vetinari (revision ca134b9)
shm_open() failed: Permission denied
[0000000001ab26c8] pulse audio output error: PulseAudio server connection failure: Connection refused
ALSA lib conf.c:3750:(snd_config_update_r) Cannot access file /usr/share/alsa/alsa.conf
[0000000001ab9e08] dbus interface error: Failed to get service name org.mpris.MediaPlayer2.vlc: Connection ":1.127" is not allowed to own the service "org.mpris.MediaPlayer2.vlc.instance15121" due to AppArmor policy
[00000000019e0d28] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
MESA-LOADER: failed to get param for i915

(process:15121): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Gtk-Message: Failed to load module "unity-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
XmbTextListToTextProperty result code -2
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
XmbTextListToTextProperty result code -2
XmbTextListToTextProperty result code -2
XmbTextListToTextProperty result code -2
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
XmbTextListToTextProperty result code -2
XmbTextListToTextProperty result code -2
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
[00007f16705c0718] chain filter error: Too high level of recursion (2)
[00007f16705c0288] core filter error: Failed to create video filter2
[00007f16705c0718] chain filter error: Too high level of recursion (2)
[00007f16705c0288] core filter error: Failed to create video filter2
[00007f16705c0718] chain filter error: Too high level of recursion (2)
[00007f16705c0288] core filter error: Failed to create video filter2
[00007f16705beaf8] core filter error: Failed to create video filter2
[00007f16705c0718] chain filter error: Too high level of recursion (2)
[00007f16705c0288] core filter error: Failed to create video filter2
[00007f16705c0718] chain filter error: Too high level of recursion (2)
[00007f16705c0288] core filter error: Failed to create video filter2
[00007f16705c0718] chain filter error: Too high level of recursion (2)
[00007f16705c0288] core filter error: Failed to create video filter2
[00007f16705beaf8] core filter error: Failed to create video filter2
[00007f16705c0718] chain filter error: Too high level of recursion (2)
[00007f16705c0288] core filter error: Failed to create video filter2
[00007f16705c0718] chain filter error: Too high level of recursion (2)
[00007f16705c0288] core filter error: Failed to create video filter2
[00007f16705c0718] chain filter error: Too high level of recursion (2)
[00007f16705c0288] core filter error: Failed to create video filter2
[00007f16705beaf8] core filter error: Failed to create video filter2
[00007f167062af08] core vout display error: Failed to create video filter2
[00007f167062af08] core vout display error: Failed to adapt decoder format to display
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
[00007f16704bf078] chain filter error: Too high level of recursion (2)
[00007f16704bc9b8] core filter error: Failed to create video filter2
[00007f16704bf078] chain filter error: Too high level of recursion (2)
[00007f16704bc9b8] core filter error: Failed to create video filter2
[00007f16704bf078] chain filter error: Too high level of recursion (2)
[00007f16704bc9b8] core filter error: Failed to create video filter2
[00007f16704af7c8] core filter error: Failed to create video filter2
[00007f16704bf078] chain filter error: Too high level of recursion (2)
[00007f16704bc9b8] core filter error: Failed to create video filter2
[00007f16704bf078] chain filter error: Too high level of recursion (2)
[00007f16704bc9b8] core filter error: Failed to create video filter2
[00007f16704bf078] chain filter error: Too high level of recursion (2)
[00007f16704bc9b8] core filter error: Failed to create video filter2
[00007f16704af7c8] core filter error: Failed to create video filter2
[00007f16704bf078] chain filter error: Too high level of recursion (2)
[00007f16704bc9b8] core filter error: Failed to create video filter2
[00007f16704bf078] chain filter error: Too high level of recursion (2)
[00007f16704bc9b8] core filter error: Failed to create video filter2
[00007f16704bf078] chain filter error: Too high level of recursion (2)
[00007f16704bc9b8] core filter error: Failed to create video filter2
[00007f16704af7c8] core filter error: Failed to create video filter2
[00007f1670001e58] core vout display error: Failed to create video filter2
[00007f1670001e58] core vout display error: Failed to adapt decoder format to display
[00007f167407b628] core video output error: video output creation failed
[00007f167406fa88] core decoder error: failed to create video output
ALSA lib conf.c:3750:(snd_config_update_r) Cannot access file /usr/share/alsa/alsa.conf
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM default
[0000000001ab26c8] alsa audio output error: cannot open ALSA device "default": No such file or directory
[0000000001ab26c8] core audio output error: module not functional
[00007f167400fc98] core decoder error: failed to create audio output
[00007f167400fc98] core decoder error: buffer deadlock prevented
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
XmbTextListToTextProperty result code -2
XmbTextListToTextProperty result code -2
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
XmbTextListToTextProperty result code -2
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
XmbTextListToTextProperty result code -2
Cannot find EGLConfig, returning null config
Unable to find an X11 visual which matches EGL config 0
Could not initialize OpenGL for RasterGLSurface, reverting to RasterSurface.
XmbTextListToTextProperty result code -2
XmbTextListToTextProperty result code -2
XmbTextListToTextProperty result code -2
[0000000001af3148] core playlist export error: could not create playlist file /snap/vlc/3/usr/share/vlc/ml.xspf.tmp15121: Read-only file system
QObject::~QObject: Timers cannot be stopped from another thread
ventrical@ventrical-MS-7798:~$ 

```

---

### Post by grahammechanical on 2016-06-17
I have worked out how to access documents on my Data partition from this Libreoffice snap app.

I finally decided to list the data partition in fstab which I managed to do at my third attempt. And now the Libreoffice file open dialog will let mt drill through the folder structure until it get to /mnt/Data and from there into the folder on the Data partition.

---

### Post by ventrical on 2016-06-17
I didn't have that problem . Either that or I'm missing somthing :)

---

### Post by vasa1 on 2016-06-17
grahammechanical posted about the LO5.2 snap not seeing other partitions. I see that as well. /media wasn't seen. My ntfs partition wasn't seen. My Windows OS partition wasn't seen.

Now, I'm on the Openbox session of Lubuntu (no session manager). I'm not sure which de's grahammechanical tried. Ventrical is using Unity and has such no problems.

Could the DE (or session manager) somehow be a factor?

PS: I asked about the appropriate place to give feedback on the LO5.2 snap and BM suggested #snappy on freenode IRC.

---

### Post by ventrical on 2016-06-18
> **vasa1 said:**
> grahammechanical posted about the LO5.2 snap not seeing other partitions. I see that as well. /media wasn't seen. My ntfs partition wasn't seen. My Windows OS partition wasn't seen.

Now, I'm on the Openbox session of Lubuntu (no session manager). I'm not sure which de's grahammechanical tried. Ventrical is using Unity and has such no problems.

Could the DE (or session manager) somehow be a factor?

PS: I asked about the appropriate place to give feedback on the LO5.2 snap and BM suggested #snappy on freenode IRC.

I'll try it on Lubuntu and xubuntu.

---

### Post by ventrical on 2016-06-18
> **vasa1 said:**
> grahammechanical posted about the LO5.2 snap not seeing other partitions. I see that as well. /media wasn't seen. My ntfs partition wasn't seen. My Windows OS partition wasn't seen.

Now, I'm on the Openbox session of Lubuntu (no session manager). I'm not sure which de's grahammechanical tried. Ventrical is using Unity and has such no problems.

Could the DE (or session manager) somehow be a factor?

PS: I asked about the appropriate place to give feedback on the LO5.2 snap and BM suggested #snappy on freenode IRC.

ahhh .. it is running 5.1 from terminal .. yet the snap is installed

```

ventrical@ventrical-MS-7798:~$ sudo snap list
[sudo] password for ventrical: 
Name         Version               Rev  Developer           Notes
audovia      3.2.2                 9    songbuilder         -
gnuchess     1.0                   2    tomechangosubanana  -
htop         2.0.1                 16   maxiberta           -
krita        3.0-snap12            3    krita               -
libreoffice  5.2.0.0.beta2         x1                       devmode
tpad         1.1                   4    caozhen             -
ubuntu-core  16.04+20160419.20-55  109  canonical           -
vlc          daily                 3    caldav              -
webdm        0.17                  21   canonical           -
x11-apps     1                     2    chadmiller          -

```

---

### Post by ventrical on 2016-06-18
> **grahammechanical said:**
> 

P.S. The command to launch this Libreoffice snap version is

```
/snap/bin/libreoffice
```

[URL="https://github.com/ubuntu/snappy-playpen"]https://github.com/ubuntu/snappy-playpen


[/URL]

@vasa

Ahhh.. I had to take a backstep. Ok .. seeing same thing you guys are.

Regards..

---

### Post by vasa1 on 2016-06-18
> **ventrical said:**
> @vasa

Ahhh.. I had to take a backstep. Ok .. seeing same thing you guys are.

Regards..Thanks for checking. I think that's information the people making the snap will appreciate!

I mentioned it at [http://webchat.freenode.net/?channels=snappy](http://webchat.freenode.net/?channels=snappy)

---

### Post by mc4man on 2016-06-18
If you want it to work with sound & local files then atm install with --devmode option

---

### Post by grahammechanical on 2016-06-18
If snaps and debs are to co-exist on a system then the snap version will need unique icons. This Libreoffice snap will load from the command line and then take over the Libreoffice icon in the launcher but otherwise those launcher icons will launch the deb version.

In the future a default install may bring in snappy packaged versions in the same way that the default install today brings in deb packaged versions. I have never installed a beta version of Libreoffice before. If this was a deb packaged beta version would it replace the existing version?

Regards.

P.S. I am not sure if any confusion I have is due to the packaging or the design changes in the version 5.2.

---

### Post by mc4man on 2016-06-18
> **grahammechanical said:**
>  If this was a deb packaged beta version would it replace the existing version?

Regards.
If it used the same name(s) then yes. (package & installed file locations
An example of 2 co-existing .debs would be browsers like firefox & firefox-trunk. The later uses firefox-trunk as package name & */firefox-trunk/* locations, ect.

---

### Post by ventrical on 2016-06-18
> **grahammechanical said:**
> If snaps and debs are to co-exist on a system then the snap version will need unique icons. This Libreoffice snap will load from the command line and then take over the Libreoffice icon in the launcher but otherwise those launcher icons will launch the deb version.

In the future a default install may bring in snappy packaged versions in the same way that the default install today brings in deb packaged versions. I have never installed a beta version of Libreoffice before. If this was a deb packaged beta version would it replace the existing version?

Regards.

P.S. I am not sure if any confusion I have is due to the packaging or the design changes in the version 5.2.

Executing libreoffice from terminal will bring up the deb installed version on the unity desktop. 

You have to use (as you had already posted)

```

/snap/bin/libreoffice

```

There is a big problem with x11-apps (snap) and Unity8 (libertine) . If you have libertine installed on unity8 and have already created containers and have populated the containers with deb packages or x apps like gedit or firefox then x11-apps has this fancy icon that shows up in Unity8 and the Legacy Apps icon (in unity8) associated with libertine is gone. Then when you click x11-apps icon all the apps and containers are there. So I am experimenting with trying to get libreoffice to run on top of unity8-mir. The idea is to not install x11-apps (snap) because they all run under Legacy Apps  (libertine)just fine.

Just a note: Here is what mark says.

> 
[SIZE=2]I can say for sure that a snap won't install in a container - it's a
 limitation we'll address in this cycle - but have you tried outside the
 container?
 
 Mark
[/SIZE][SIZE=2]

Well .. this is true to some extent, however the x11-apps (snap) DOES run on Unity8 and then manages the containers. I will, however , try to run libreoffice (snap) on unity8 using the click terminal provided.

So.. I am just alerting everyone that if you have a unity8 desktop running on yakkety or xenial  with libertine containers then do not install x11-apps (snap) because it will break libertine  (Legacy Apps) scope to some extent .. but the apps will still run.

Regards..

[/SIZE]

---

### Post by grahammechanical on 2016-06-18
I have just been reading this

[https://developer.ubuntu.com/en/blog/2016/06/15/snapd-208-universal-snaps-and-desktop-interfaces/](https://developer.ubuntu.com/en/blog/2016/06/15/snapd-208-universal-snaps-and-desktop-interfaces/)

and coming to snapd is a snap run command. That would be nice.

---

### Post by mc4man on 2016-06-18
In unity this will be an issue (atm) as the unity launcher uses .desktop names, not location/name.
So using vlc as ex.

if only a snap is installed then vlc 3.0 can be pinned to the launcher & clicking on will open it.
Once or if the repo vlc is installed then the launcher icon will open the repo vlc as the unity setting is simply - 
application://vlc.desktop 
Not sure why they're not using a unique name for snap installed .desktops

---

### Post by mc4man on 2016-06-18
> **mc4man said:**
> 
Not sure why they're not using a unique name for snap installed .desktops
Not really that simple though part of a potential issue.

From what I see atm in _Unity_, using vlc as sample - 
When a snap app is first run  the default applications folders are parsed for .desktop files, specifically the Exec= line, looking for the app's binary name.
If found,  then that .desktop  is used/displayed in the launcher. When subsequently clicked on it opens the binary it was installed with, typically the .deb version.

If no .desktop with the binary name on the Exec= line is found then the .desktop that came with the snap is used. If one chooses to pin that to the launcher then a local .desktop is written to ~/.local/share/applications using the same name as the .desktop the .deb version would install. It will work fine with it's _no path_ Exec= line, (ex.,  Exec=vlc),  to launch the snap app up to a point. 

That point is if afterwards the .deb version is installed then that .desktop is still used but now will launch the .deb version, not the snap as Exec=vlc will open the first vlc binary found (typically in /usr/bin from .deb install

(- currently from a user side can be gotten around by creating 2 different name .desktops, one for the .deb version, one for the snap. The snap's .desktop would need a full path Exec= line
I'd suspect this will be fixed in some fashion at some point.

---

### Post by ventrical on 2016-06-20
> **grahammechanical said:**
> I have just been reading this

[https://developer.ubuntu.com/en/blog/2016/06/15/snapd-208-universal-snaps-and-desktop-interfaces/](https://developer.ubuntu.com/en/blog/2016/06/15/snapd-208-universal-snaps-and-desktop-interfaces/)

and coming to snapd is a snap run command. That would be nice.

todays updates ...

```

Setting up sysv-rc (2.88dsf-59.6ubuntu1) ...
dpkg: dependency problems prevent configuration of ubuntu-core-launcher:
 ubuntu-core-launcher depends on snap-confine; however:
  Package snap-confine is not installed.

dpkg: error processing package ubuntu-core-launcher (--configure):
 dependency problems - leaving unconfigured
Setting up initscripts (2.88dsf-59.6ubuntu1) ...
Setting up libk5crypto3:amd64 (1.14.2+dfsg-1ubuntu1) ...
Setting up suru-icon-theme (14.04+16.10.20160620.1-0ubuntu1) ...
dpkg: dependency problems prevent configuration of snapd:
 snapd depends on ubuntu-core-launcher (>= 1.0.23); however:
  Package ubuntu-core-launcher is not configured yet.

dpkg: error processing package snapd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-snappy-cli:
 ubuntu-snappy-cli depends on snapd; however:
  Package snapd is not configured yet.

dpkg: error processing package ubuntu-snappy-cli (--configure):
 dependency problems - leaving unconfigured
Setting up libkrb5-3:amd64 (1.14.2+dfsg-1ubuntu1) ...
Setting up qtdeclarative5-ubuntu-settings-components:amd64 (0.7+16.10.20160617-0ubuntu1) ...
Setting up ubuntu-system-settings (0.4+16.10.20160609-0ubuntu1) ...
Setting up libgssapi-krb5-2:amd64 (1.14.2+dfsg-1ubuntu1) ...
Setting up libcups2:amd64 (2.1.4-1) ...
Setting up libcupsmime1:amd64 (2.1.4-1) ...
Setting up cups-daemon (2.1.4-1) ...
Setting up libcupsppdc1:amd64 (2.1.4-1) ...
Setting up libcupsfilters1:amd64 (1.9.0-2) ...
Setting up libcupsimage2:amd64 (2.1.4-1) ...
Setting up cups-filters-core-drivers (1.9.0-2) ...
Setting up cups-client (2.1.4-1) ...
Setting up libcupscgi1:amd64 (2.1.4-1) ...
Setting up cups-filters (1.9.0-2) ...

Setting up cups-browsed (1.9.0-2) ...
Setting up cups-ppdc (2.1.4-1) ...
Setting up cups-core-drivers (2.1.4-1) ...
Setting up cups-bsd (2.1.4-1) ...
Setting up cups (2.1.4-1) ...
Updating PPD files for cups ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 ubuntu-core-launcher
 snapd
 ubuntu-snappy-cli
ventrical@ventrical-System-Product-Name:~$ 

```


regards..

edit:

and

```

sudo apt-get install -f

```

```

The following additional packages will be installed:
  snap-confine
The following NEW packages will be installed:
  snap-confine
0 upgraded, 1 newly installed, 0 to remove and 122 not upgraded.
3 not fully installed or removed.
Need to get 0 B/15.4 kB of archives.
After this operation, 61.4 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 928278 files and directories currently installed.)
Preparing to unpack .../snap-confine_1.0.30_amd64.deb ...
Unpacking snap-confine (1.0.30) ...
Setting up snap-confine (1.0.30) ...
Installing new version of config file /etc/apparmor.d/usr.bin.snap-confine ...
Setting up ubuntu-core-launcher (1.0.30) ...
Setting up snapd (2.0.9+16.10) ...
Setting up ubuntu-snappy-cli (2.0.9+16.10) ...
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2016-06-20
I was able to download and install the libreoffice.snap via the click terminal on unity8 desktop.

When I tried to run,

```

/snap/bin/libreoffice

```

I got:

```

cannot pivot_root to the new root filesystem. errmsg: Permission denied

```


then ran in home directory and :

```

Failed to open display
javaldx:Could not find a java Runtime Environment
Warning: failed to read path from javaldx

```

---

### Post by grahammechanical on 2016-06-21
The Krita snap on Ubuntu Mate. snapd is installed by fault.

---

### Post by vasa1 on 2016-07-09
A post re. making one's own AppImages was moved from here to its own thread: [http://ubuntuforums.org/showthread.php?t=2330215](http://ubuntuforums.org/showthread.php?t=2330215)

---

### Post by Chanath on 2016-07-10
> **vasa1 said:**
> A post re. making one's own AppImages was moved from here to its own thread: [http://ubuntuforums.org/showthread.php?t=2330215](http://ubuntuforums.org/showthread.php?t=2330215)

That's OK. It was just info. My interest is in creating (or at least understand) how to create snaps from a deb package. Any info on that is highly appreciated.

---

