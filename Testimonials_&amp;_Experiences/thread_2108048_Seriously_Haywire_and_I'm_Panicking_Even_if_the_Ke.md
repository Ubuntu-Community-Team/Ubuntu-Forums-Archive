---
title: "Seriously Haywire and I'm Panicking Even if the Kernel Isn't"
date: 2013-01-23
forum: Testimonials &amp; Experiences
---

### Post by Mark_in_Hollywood on 2013-01-23
I was all set to post this in General Help, knowing that when too many [problems]("http://ubuntuforums.org/showthread.php?t=2107837") appear at the same time, a fresh re-install is probably the best solution. I was going to post this as a warning to others. The bug report I saw about the [xfce-alsa]("http://askubuntu.com/questions/65764...nd-with-amixer") had only 18 others reporting a problem. Not a high priority item there. The Thunderbird not being called from the panel is the type of flaw I live with. I can get the email from the /Menu/Internet/Thunderbird. Yet, it's a nuisance when (this user) has to learn a new routine. And my MythTV install is just too new to believe that I had all the kinks straightened out. But, taken as all the 3 problems, coming on the heels of each other, I was panicked.

[CENTER]But Sometimes, "It Just Works". Read the Ramblings of a non-geek user.[/CENTER]

After 2 or 3 days of configging MythTv, I could finally watch tv. Then, because the sound was too loud, I opened the Multi-media/Audio Mixer. And put a link to the applet on my desktop. I did not know about F10-F11 at that moment. That caused a serious amount of hard disk time; well over 2 to 3 minutes of constant disk LED activity and sound. After the icon was installed on my Xubuntu/XFCE desktop; I moved the Master Volume sliders up and down and the volume changed accordingly. Then I looked at the Select Controls option. There I saw Headphones option. Since I listen to TV with headphones, I added that icon. I moved the Headphone sliders up and down, unchained them to make sure all was A-OK, tested, chained them again. It just worked. I then muted the Headphones. Sound muted. I then un-muted the headphones. SOUND GONE.

Sound was gone is VLC, Rhythmbox, MythTV and web-based (I use Chrome) apps like Internet Radio Station. This happened late last night. I was pretty tired, having spent half the day setting up MythTV.

Screwier and screwier. I wanted to check email before I went to bed, so I clicked my panel: Mail Reader. It brought up a strange error message I had never seen before. Thunderbird could not be called from there. I shut the 'puter off and next morning, my former: beautiful, flawlessly working Precise Pangolin (ver. 12.04) LTS, would not properly boot; it hung. I use ALT-SysRq R-E-I-S-U-B-K and was able to re-boot and somethings appear better now.

First: Update Manager came onscreen and had about 60 meg of updates. Those were Mozilla Firefox and Google Chrome browsers. I had no other programs/apps open, so I clicked "Install Updates". Another error message came onscreen. It said I had no space (or room) in / (root). That was odd because I looked at that about 2 weeks ago and thought I had 2 to 3 gig of / as open space. I did this in contemeplation of removing the 60 gig that Win7 uses. I wanted that extra 60 gig for MythTV recorded tv shows. I have a 400 gig drive and have about 200 gig of free space total. That includes all Windows7 partitions and my Ubuntu with [COLOR="Red"]/[/COLOR], [COLOR="red"]/home[/COLOR] etc. With both OS's I still have 200 gig of unused, free space. But, because Update Manager said [COLOR="red"]/[/COLOR] (root) was full and that I should use use apt-get clean and empty the Trash to make disk space for the updates, I called Disk Usage Analyzer and had it run "Scan Filesystem". Usually that app populates the data in under a minute or two. Today, the little round cursor spins and spins and hasn't stopped yet.

This Morning: I'm hesitating to install the Firefox and Chrome updates mentioned above. I don't want to crash the OS.

mark@Lexington-19:/$ sudo fdisk -l
Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf3e1e104

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   143566847    71680000    7  HPFS/NTFS/exFAT
/dev/sda3   *   143572905   174176729    15301912+  83  Linux
/dev/sda4       174176791   781417664   303620437    5  Extended
/dev/sda5       174176793   764420894   295122051   83  Linux
/dev/sda6       764420958   781417664     8498353+  82  Linux swap / Solaris

and

mark@Lexington-19:/$ sudo df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3        15G   12G  1.7G  88% /
udev           1000M  4.0K 1000M   1% /dev
tmpfs           403M  992K  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1007M  3.1M 1004M   1% /run/shm
/dev/sda1       100M   25M   76M  25% /media/System_Reserved
/dev/sda2        69G   53G   17G  77% /media/sda2
/dev/sda5       278G   65G  199G  25% /home


So my memory of how much free space on / was close. Yet, how could Update Manager report that / had insufficient space? Upon emptying the Trash (using the Empty Trash option - right click on Trash icon on my desktop) and running sudo apt-get clean, I returned to Update Manager and the Manager ran and installed the updates. Seemingly without any problems. Update Manager closed and no E(rror) or W(arning) reported.

Next:

mark@Lexington-19:~$ sudo aptitude install -f
[sudo] password for mark: 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

So, that makes me think the Firefox and Chrome updates are good to go.

Last night: 

After adding and then removing the Volume Control icon, I called MythTV. I called (ran) Multimedia/MythTV Frontend. I had just finished configging Myth during the last few days. I had set the theme to a nice blue color and then, after whatever made this mess (ALSA? Mixer Applet? MythTV?, not enough empty space?), MythTV Frontend launched and opened in the default greenish-brownish color. I saw a screen I had never seen before. It asked for the Country and Language I used. When I responded to that, and clicked Finish, the full-screen MythTV window closed and immediately re-opened with the same screen about Country and Language. One Endless Loop. I played with as much of that as I could and then had to issue the ALT-SysRq R-E-I-S-U-B-K command to shut down the computer.

Even though a re-boot (cold boot) did nothing to help last night; The next morning I called MythTV. The endless loop of Country-Language was gone. The sound is back, although I may have done something screwy there, too by:

for i in $(amixer |grep -o \'.*\'); do amixer set $i unmute; done

which UN-mutes every audio device that has a mute option. This line was criticized by someone as unmuting 80 devices, but I have my sound back and I'll work out the fine details as needed.

Linux isn't flawless. But sometimes: "It Just Works".

---

