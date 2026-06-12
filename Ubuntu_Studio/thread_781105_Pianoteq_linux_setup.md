---
title: "Pianoteq linux setup?"
date: 2008-05-04
forum: Ubuntu Studio
---

### Post by ethanay on 2008-05-04
Hi all,

does anyone use Pianoteq under Ubuntu?  If so, what is your hardware/software setup?  What issues have you encountered?

I was about to purchase a full-fledged digital piano, but after hearing Pianoteq, I am much more inclined to explore this route seriously.

tia
ethanay

edit: almost forgot my hardware setup!
dell xps m1330 laptop, intel c2d @ 1.5ghz, 2gb ram, intel integrated audio ("High Definition Audio 2.0")

---

### Post by Stochastic on 2008-05-05
according to the Linux VST Database, it's a go!
[http://ladspavst.linuxaudio.org/?q=node/2284](http://ladspavst.linuxaudio.org/?q=node/2284)

---

### Post by thorgal on 2008-05-05
Hello,

I am the author of the comment left on the ladspavst site ("Nice Stuff ..."). I have to say, this is an amazing piece of software. I run it without problems, also as a VSTi through dssi-vst. If you want to hear something a bit different from expert pianists demonstrating or promoting the soft, you can hear me using it there :

[http://www.mattashton.com/Mecano_AutumnaticPlay.mp3](http://www.mattashton.com/Mecano_AutumnaticPlay.mp3)
(I am not Matt Ashton, he was just kind enough to host my mp3). The music was composed by Dirk Polak, the leader of an old post-punk band from Holland called Mecano ("All Rights reserved blabla"). The interpretation is mine.

I am not a 'virtuose', I learned playing by myself so 
forgive my amateurish playing but the sound is just cool! I am very happy to have purchased such a VSTi.

---

### Post by ethanay on 2008-05-05
This is very good news.  Thorgal, that is a nice, solid performance (haven't heard the original, so can't comment on interpretation).  I enjoyed listening.  You don't have to be a virtuoso to make good music.

So this is what I am envisioning:

midi controller > laptop (pianoteq and/or sequencer/notation) > outboard powered sound system

or does it need an external interface?  if so:

midi controller > external interface > laptop > external interface > outboard sound system

does an external interface introduce or improve latency and/or sound quality issues?

do i need wineasio installed regardless of whether i am working with a windows-based program through wine?

---

### Post by thorgal on 2008-05-06
hello! thanks for your nice comments :) I am more into guitar, bass and drumming but my piano skills improve slowly with time ... too slowly maybe ...

Anyway, this is what I can tell you :

Pianoteq comes in two formats at least : VSTi plugin and standalone app.

* The standalone app requires wineasio. Then you start it like any other .exe :
wine $HOME/.wine/drive_c/Program\ Files/Pianoteq/Pianoteq22.exe

If you're lucky, it will start without a glitch. If you're not, it will start all right but the GUI will not show up due to a wine bug (depends on your wine version). Without the GUI, it is almost useless.

* the VST plugin does not require wineasio IF you use a linux native VST host like FST or DSSI-VST. If you use a windows vst host through wine (vsthost.exe, savihost.exe, or other more complex hosts like Reaper), then wineasio is unavoidable.

I use it personally with dssi-vst and it works great. I want a linux native vst host because wineasio has proven unstable to me. I also use dssi-vst with Addictive Drums by XLN Audio and this has changed my music production for the MUCH MUCH better! SO I would advise you to get dssi-vst working.
The only drawback is that you have a little display issue. The standalone app GUI shows you the velocity of each note you hit on the keyboard in a graphical way in realtime. For some reasons, dssi-vst is buggy in that respect but that's a very minor thing since the GUI is nicely working for all the rest. There are advantages in using the standalone app (menu more versatile) but I think the VSTi version sounds better. I don't know why ...

Anyway, the funny thing about the standalone app is that it will connect to your MIDI hardware as soon as you start it, you have nothing to do, not even a manual connection in qjackctl. And anyway, you couldn't choose to do a manual connection because pianoteq does not even show up in the qjackctl MIDI tab. Maybe it is due to some issue with wineasio and MIDI or my wine audio config.

But as a VSTi, it will show up like any MIDI jack client and you can disconnect it if you want via the standard connection window in qjackctl. This makes the VSTi option more interesting to me. And it has been super stable with dssi-vst. I can run it at buffer size 128, period 2 and SR of 96kHz, no sweat, no xrun. But YMMV, my studio PC is highly customized in many ways (RAM, CPU and OS tuning ...) + my external gears are top quality (RME stuff). And a last by the way, I am not using ubuntu but debian sid.

---

### Post by ethanay on 2008-05-06
thanks again.

follow this [link]("http://www.forum-pianoteq.com/viewtopic.php?pid=1639") to the thread i started on the pianoteq forums for more discussion about hardware.  very informative (to me at least)

---

### Post by ethanay on 2008-05-08
I've downloaded and tried it and the stand-alone started "without a hitch!"  Pretty cool!  What is the advantage with the VSTi plugin?  Is it that it can be used in conjunction with a sequencer, while the standalone is simply for piano sound production?

I haven't bought an external sound card yet.  The sound has a low-quality midi type feel to it, with this high-pitch phase thing happening over single notes and groups of notes together that sounds very fake.  Is this my laptop sound card or the Pianotech software?  I don't want to invest in a $$ firewire card if it's the software!

---

### Post by thorgal on 2008-05-08
great it works out of the box :)
mmm ... what is your sound system (speakers, etc) ?
the default presets are sounding great in my studio so I would think, rather than the software, it is more your audio system. I don't really know without listening to something that came out of your system. What do you think about the sound in my mp3 ? does it render like what you described ?
To be fair, I tweaked my own pianoteq setting and then remastered a bit with jamin. So you could play around with the numerous parameters to achieve a sound you like. You should also download the pianoteq add-ons. Some of them I quite interesting, reproducing 100 year's old piano models, etc.

Regarding the VSTi vs standalone version, I don't know why but as I said, it seems like the VSTi sounds a bit better (?) and I like to run it through dssi-vst because it behaves like a true JACK client that I can connect / disconnect at will in the qjackctl MIDI tab. For some reasons, the standalone app does not show up there so it is ALWAYS connected to my MIDI hardware. A bit lame when I want to use another soft synth and disconnect pianoteq.

But yeah, just tell about your audio setup before anything else.

---

### Post by ethanay on 2008-05-08
right now I am trying it just with the laptop integrated audio (see 1st post) through headphones connected directly.

Your recorded piece sounded very nice.  I still hear it a little, but it is much more subtle and easy to ignore/miss, which tells me it is mainly the fault of the intel hda audio processor.

I just ordered:
Echo Audiofire2 interface
Tapco Mix.60 (for preamp)
Behringer B2031A studio monitors

Have you noticed a significant performance decrease with "multicore rendering" enabled in Pianoteq?  see [this post](http://www.forum-pianoteq.com/viewtopic.php?pid=1655) at the Pianoteq forums

---

### Post by thorgal on 2008-05-08
I did not fiddle around with this setting so I just tried it. It does not affect the CPU load (I have a Core 2 Duo E6600, 2x2.4 GHz). But the funny thing is, I checked with 'top' while playing and each time the top screen was refreshed, I could hear a small "blip" (not an xrun, just a short noise). If I disable this multicore rendering (back to default setting), the blip is gone. But the CPU load is the same.

By the way, congrats for your new gears, they will help improving your experience :)

OK, I see what you mean, the blip I hear is actually corresponding to a spike in the CPU load. I checked with a graphical display of the system perf. But it seems to me that it's some sort of interference with other processes (like display refreshing). If nothing else is running, it sounds fine and again, top did not report a higher load. But do you need this multicore rendering ?

---

### Post by ethanay on 2008-05-09
do you use the real-time kernel or 64-bit or generic?  Right now I am just switching from "ondemand" to "performance" cpu scaling modes and it seems to help a little. 

I installed the rt kernel and it broke hibernate for some reason -- even when I boot the generic kernel.  So I removed it for the time being and hibernate seems fixed again.

I got wineasio to work, but it sucks on my sound card -- xruns (what are they, anyway) create constant popping/skipping sound.  However, the latency in between the xruns is much less :)

Next I will try to get dssi-vst to work.  I am waiting on the arrival of the Audiofire2 in order to test for sure.

---

### Post by thorgal on 2008-05-09
I use a realtime kernel (2.6.24.3-rt3) that I built up myself. Remember, I use debian sid, not ubuntu.

Concerning xruns, they are due to buffer under or overrun. Your soundcard cannot cope with the buffer size because it was not designed to do so or some other things interfere with it. You said that right now, you were using the onboard intel HDA. Run jackd with n = 3 if you had not done that before.
You should also look into IRQ sharing and IRQ thread priorities. If it's a laptop, you could have hard time to reassign IRQs, it could even be that the laptop mobo has no IO-APIC mode. If the onboard chip shares its interrupt with say the graphics or network chip or USB controllers, you will run into IRQ conflicts, which is a major cause of xruns. 

The ideal case :
- make sure your sound chip uses its own interrupt without sharing it
(check with 'cat /proc/interrupts' what is going on with interrupts)
- use realtime kernel
- set /etc/security/limits.conf appropriately for accessing RT privileges
- use a neat script called 'rtirq' to set the priority of the relevant IRQ threads (this only works if you use a realtime kernel)

Don't use bloated desktop environment (compiz-fusion, KDE, GNOME). I use openbox and tweaked it so that it looks like KDE. Disable 3D acc, maybe 2D acc as well. The intel GPU is using PCI access and in my case (PCI HDSP sound card) it can cause a few issues. In your case (USB device), issues will come from other considerations.

Know that USB devices always use CPU cycles, while firewire devices don't.
They are more expensive but more reliable. If you are serious about music production, it's worth the investment. If it's just a hobby, you should do fine with USB stuff but don't expect it to be rock solid with extreme performance.

---

### Post by ethanay on 2008-05-09
interrupts:

$ cat /proc/interrupts
           CPU0       CPU1       
  0:     987742     106298   IO-APIC-edge      timer
  1:       3559        736   IO-APIC-edge      i8042
  8:       6779         19   IO-APIC-edge      rtc
  9:         31         25   IO-APIC-fasteoi   acpi
 12:    1565891     179055   IO-APIC-edge      i8042
 14:        337         53   IO-APIC-edge      libata
 15:          0          0   IO-APIC-edge      libata
 16:     366274      38679   IO-APIC-fasteoi   i915@pci:0000:00:02.0
 18:          3          2   IO-APIC-fasteoi   ohci1394
 19:         90         13   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb4, uhci_hcd:usb5
 20:      25403       1849   IO-APIC-fasteoi   uhci_hcd:usb2, uhci_hcd:usb6, HDA Intel
 21:          1          0   IO-APIC-fasteoi   ehci_hcd:usb3, uhci_hcd:usb7
 22:          5          6   IO-APIC-fasteoi   sdhci:slot0
217:     646242     695820   PCI-MSI-edge      iwl3945
218:         40         62   PCI-MSI-edge      eth0
219:      57892       7291   PCI-MSI-edge      ahci
NMI:          0          0   Non-maskable interrupts
LOC:     182513     538011   Local timer interrupts
RES:     794994     896022   Rescheduling interrupts
CAL:        577        704   function call interrupts
TLB:       8341       5816   TLB shootdowns
TRM:          0          0   Thermal event interrupts
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0
-----------------------
errors trying to compile dssi-vst:

/dssi-vst-0.6$ make
g++ -shared -Wl,-Bsymbolic -g3 -Ivestige -Wall -o dssi-vst.so dssi-vst.cpp remotevstclient.o  -L. -lremoteplugin -lasound
In file included from dssi-vst.cpp:12:
/usr/include/dssi.h:28:28: error: alsa/seq_event.h: No such file or directory
dssi-vst.cpp:14:33: error: alsa/seq_midi_event.h: No such file or directory
In file included from dssi-vst.cpp:12:
/usr/include/dssi.h:307: error: ‘snd_seq_event_t’ has not been declared
/usr/include/dssi.h:321: error: ‘snd_seq_event_t’ has not been declared
/usr/include/dssi.h:359: error: ‘snd_seq_event_t’ has not been declared
/usr/include/dssi.h:375: error: ‘snd_seq_event_t’ has not been declared
dssi-vst.cpp:48: error: ‘snd_seq_event_t’ has not been declared
dssi-vst.cpp:74: error: ISO C++ forbids declaration of ‘snd_midi_event_t’ with no type
dssi-vst.cpp:74: error: expected ‘;’ before ‘*’ token
dssi-vst.cpp:117: error: ‘snd_seq_event_t’ has not been declared
dssi-vst.cpp: In constructor ‘DSSIVSTPluginInstance::DSSIVSTPluginInstance(std::string, long unsigned int)’:
dssi-vst.cpp:176: error: ‘m_alsaDecoder’ was not declared in this scope
dssi-vst.cpp:176: error: ‘snd_midi_event_new’ was not declared in this scope
dssi-vst.cpp:182: error: ‘snd_midi_event_no_status’ was not declared in this scope
dssi-vst.cpp: In destructor ‘virtual DSSIVSTPluginInstance::~DSSIVSTPluginInstance()’:
dssi-vst.cpp:217: error: ‘m_alsaDecoder’ was not declared in this scope
dssi-vst.cpp:218: error: ‘snd_midi_event_free’ was not declared in this scope
dssi-vst.cpp: At global scope:
dssi-vst.cpp:357: error: ‘snd_seq_event_t’ has not been declared
dssi-vst.cpp: In member function ‘void DSSIVSTPluginInstance::runSynth(long unsigned int, int*, long unsigned int)’:
dssi-vst.cpp:362: error: ‘m_alsaDecoder’ was not declared in this scope
dssi-vst.cpp:369: error: ‘snd_seq_event_t’ was not declared in this scope
dssi-vst.cpp:369: error: ‘ev’ was not declared in this scope
dssi-vst.cpp:382: error: ‘snd_midi_event_decode’ was not declared in this scope
dssi-vst.cpp: At global scope:
dssi-vst.cpp:666: error: ‘snd_seq_event_t’ has not been declared
make: *** [dssi-vst.so] Error 1

---

### Post by ethanay on 2008-05-09
thank you so much for your suggestions!  this is quickly becoming complicated...I would like to return to basics before proceeding further and get your opinion on how to move forward...

in the end, I want to be able to:
1) Play piano w/my keyboard through pianoteq w/good sound quality
2) record audio directly produced from pianoteq, meaning
----a. record/sequence midi events while playing piano through pianoteq, and save as midi files
----b. record pianoteq playback of midi events/midi file as uncompressed audio
----c. edit further in audacity to produce results like your mp3 :)

I am used to step (c), have experience editing.  But (a) and (b) I lack any experience.  I'm not even sure what midi sequencer to use.

I am using my laptop -- it is my only computer and multi-purpose.  Mainly it is for word processing/e-mail/music.

It is sounding like I need a 2nd setup in order to do the audio/midi/pianoteq stuff well (eliminating unnecessary processes, interrupts, etc).  Is there a way to keep my current settings and have a 2nd boot or login option that I have customized for audio/midi? i.e., simple graphics, no internet/wifi, sparse desktop with few or no default daemons/processes running, etc.

I appreciate your input in this matter
ethanay

---

### Post by thorgal on 2008-05-09
I understand it can sound complicated and tedious. I know all this because I built up a PC from scratch for the sole purpose of producing music (it is not a hobby for me, I am fulltime on it). It required a lot of reading beforehand and trials and errors, e.g. I started with ubuntu-studio and wiped it out after a couple of weeks, behaving too weird. I then installed 64studio (32 bit version) and realized it was good old debian (I administrate a few debian boxes so I am in my environment with it) so I upgraded it to sid and recompiled my own kernel without all the "crap" built up by default in the distro kernel. My studio PC became stability incarnated :)

So, anyways, you can see that your audio chip is sharing IRQ with other things. But it may not matter because these USB dev are maybe not in use (unlike networking, etc).

So you could start by installing an alternative kernel (realtime) and even go through the exercise of compiling it although I would avoid it at the beginning. Then, it can become tricky to boot with alternative set of services and graphical options. The desktop choice is easy because gdm or kdm offers you the choice at login time. The tricky thing is to get the right xorg options if for some reasons you need stuff like 3D acc when you boot normally and want it disabled when you boot the rt kernel. So be sure to know what you really need and what fancy stuff you can ignore. Networking is not an issue if 1- it doesn share the audio interrupt 2- its IRQ thread has a lower priority. From your ouput, your mobo is IO-APIC (more than 16 interrupts) so you can use a program called irqbalance (check in the synaptic package manager) but maybe it can also run on non APIC platform, I am not an expert when it comes to these low level stuff.

I forgot : your compilation problem indicates that you need the alsa development files. In synaptic, make a name search on "alsa dev" or "asound dev" and install the dev packages related to the non dev packages already installed on your system.

---

### Post by ethanay on 2008-05-10
Thanks for the suggestions! dssi-vst is now compiled and installed (I've been using checkinstall instead of make install to allow me to undo!).  After quite a bit of troubleshooting, I have been able to run Pianoteq.dll!  However, no sound yet as my controller is not here and set up.

As for the rest, I will wait for my soundcard to arrive in order to check performance and latency with my current setup and get jackd configured properly.  I am hoping I can get away with not modifying much other than turning off a few programs, switching from ondemand to performance cpu.

If I cannot get acceptable latency/performance with the new soundcard, then I will try again the specific realtime kernel, and hope it doesn't break hibernate for me.  Does the kernel require configuring beyond installation, or can I just install it, boot from it and notice an immediate improvement in audio latency (all else being equal)?

---

### Post by thorgal on 2008-05-11
hello!
If you install an RT kernel and if you have your PAM security configured properly (tweak in /etc/security/limits.conf), you should notice a dramatic reduction of xruns, not to say no more xruns. Then it depends on IRQ thread priority fine-tuning (the rtirq script does that automatically for you), the amount of stuff that runs in the bg, etc. If you tweak your machine to perform at very low latency (depends on audio hardware as well), you can get down to ~ 1 millisecond latency. I can run my studio PC at buf size 64, period 2, sample rate 96kHz ... but I don't need it because I am
1- doing hardware monitoring (I am barely using software effects or instruments)
2- not doing live stuff.

When I program a drum line, I do not need low latency. When I play the drum from rosegarden together with music tracks from ardour (all jack transport slaves), there's a tiny noticeable latency but this is not a problem to me. When I record the drum in ardour, I switch to a lower latency setting so I don't have to realign stuff but for editing, playback, etc, I don't need it. Of course, when I play the piano for my own pleasure, I need low latency so I switch to a reasonably low latency setting (buf size 128 is good enough).

PS: when I come to think of it, there is a neat alternative for you (double system). If you have enough disk space or even a second hard disk, you could easily install 64studio but share the /home partition with ubuntu. Therefore, you would save all your data in a common place but could choose to boot a different OS for audio work with RT kernel, interrupt tweaking, low latency framework, xorg options, etc. If you know about partitioning hard drives, mounting partitions, etc, it is rather straightforward. In  fact, it's exactly what I would do if I were you :)

---

### Post by ethanay on 2008-05-12
hah, that may work perfectly!  that way I don't have to mess with my current ubuntu setup and have multiple kernels (always seems to mess something up).

do you have an idea about how much space I need to be safe?  right now my root partition is 10gb and my Ubuntu install currently is 3.7gb. -- can I divide that in half (5gb for ubuntu, 5gb for 64studio) safely, or should I make more room?  it seems to me 10gb is about safe...

---

### Post by thorgal on 2008-05-12
please post the screen output of 

sudo fdisk -l /dev/sda

(I assume you only have one HD and its device node is /dev/sda since it is a laptop)

When I see what you got there, I can advise you better.

---

### Post by ethanay on 2008-05-12
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000321a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1175     9438156   83  Linux
/dev/sda2           14072       14593     4192965    5  Extended
/dev/sda3            1176       14071   103587120   83  Linux
/dev/sda5           14072       14593     4192933+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by thorgal on 2008-05-12
thanks!
I forgot to ask :
- output of 'df -h'
- output of 'cat /etc/fstab'

Then I'll propose a partition scheme for you and how you can do it.
By the way, you seem to have way too much swap - 4G! How much RAM do you have ?

---

### Post by ethanay on 2008-05-13
haha, I have only 2gb ram.  Every source I have read has suggested ~2*ram in order to ensure space for hibernation, although it seems my swapfile is never used while doing normal work.  Do you have a different perspective?  I have just downloaded the live cds of 64studio and gparted and am excited to get it set up maybe later this week.

```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.0G  3.5G  5.1G  41% /
varrun               1009M  232K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   48K 1009M   1% /dev
devshm               1009M  240K 1009M   1% /dev/shm
lrm                  1009M   38M  972M   4% /lib/modules/2.6.24-16-generic/volatile
/dev/sda3              99G   40G   54G  43% /home
gvfs-fuse-daemon      9.0G  3.5G  5.1G  41% /home/ethan/.gvfs
```

about 1/2 of /dev/sda3 is video that I need to burn to dvd and archive, so that will free ~20gb.  But I am still ripping the rest of my music collection.

```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=357e0135-b21d-4213-a7b9-3c9e1128e26d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=5841a39a-e9fb-42d0-b444-96317ab73c15 /home           ext3    relatime        0       2
# /dev/sda5
UUID=2d405a37-d8ea-47cc-97d6-19fc4e5919ac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0   0
```

---

### Post by thorgal on 2008-05-13
thanks, I'll get back to you later.

PS: the 2*ram for the swap is an old thing that does not make too much sense nowadays. For everyday desktop apps (email, netsurfing, office tools), 0.5GB is plenty. I am sure you can read about it if you google more ;) 
In my studio PC, I have 2GB swap (I have 4G RAM) because I do use memory extensive apps but YMMV. My choice was almost random because it turned out that I only had that space left when I partitioned my OS HD. 2GB never gave me a problem. I am sure it is already too much.

---

### Post by ethanay on 2008-05-13
.5gb seems small for hibernate.  The minimum recommendation I have seen for a laptop to hibernate is swap=ram.  Ram data is usually compressed on the hdd so shouldn't be greater than RAM.  Theoretically, it seems possible that hibernate can fail with swap=ram if ram+swap use > 100% ram and hibernate doesn't compress enough to make up the difference.  So maybe something 4gb > swap > 2gb for a laptop w/hibernate.

thanks, I look forward to your suggestions!

---

### Post by thorgal on 2008-05-18
hello!

You allocated 100GB for you /home. You may want to shrink it by about 15GB.
There is a very easy way to manipulate partitions in a graphical way but you will have to login as root from gdm or kdm, whatever login manager you use. From there, you will call a program called gparted.

Once in gparted, you will see your existing partitions.
To my mind, a decent partition scheme would be :

HD of 120 GB :

/dev/sda1 12GB : ubuntu root partition
/dev/sda2 12GB : 64studio root partition
/dev/sda5 95GB : /home partition
/dev/sda6 1GB  : swap 

i.e. the home partition is not a primary one. I think linux can boot from non primary partition. If so, just shrink your existing /dev/sda3 to free about 15GB using gparted AS ROOT after you have unmounted the /home partition (login as root in gdm!), and jump directly to the paragraph called 64STUDIO below. If you want to move your partitions around, you can go through the long and trickier guide starting just here. Good luck :)


*** REPARTIONING things so that all OSs are on primary partitions and pure data on logical partitions.

A way to achieve this :

0- You need to know the root password. I know ubuntu is copying OS-X style when it comes to administrating the machine (all through sudo). As an old debian user, I think it sucks. So if you don't know the root password in ubuntu, you will do this in a terminal :

sudo passwd root

and then choose a password for root. That's all it takes to have a working root password, not some random crap chosen by the ubuntu installer that you  would have no chance to know.

Back to business.
 
as root, in a terminal (type su and then root password when prompted):
-------------------------
you current swap is on /dev/sda5 so let's turn if off and remove it.

swapoff /dev/sda5

cfdisk /dev/sda

in cfdisk, highlight /dev/sda5, delete, and write new partition table to disk. Quit cfdisk and reboot. You may see some complaints about swap not turned on, never mind that.

Now, login as root, not as normal user, in gdm or kdm. You may need to allow this in gdm because gdm is rather paranoied. The utility to set this up is gdmsetup or something like that (that you would invoke after you log in as yourself), or you can invoke it from the login manager itself before logging in (look at menu items in gdm). 

once you are logged in as root through gdm, open a terminal and unmount the /home partition (/home is only needed for non root user of course, so it's safe to unmount it when logged in as root) :

umount /home

then fire up 'gparted'

select the home partition and resize it to just above what it already contains, hopefully less than half of the partition size itself. Apply the operation and wait until completetion.

Great, that should leave you quite a lot of free space now.

Let's now create a new partition on /dev/sda5 :
in the terminal, cfdisk /dev/sda
create new partition, make it linux type, size larger than your existing /home data amount but leave 1GB free for future swap (or 2GB if you are paranoied about hibernation), and start this new partition right after the prior partition (not from the end of the HD). Write changes to partition table and quit. Then reboot again. You should now have /dev/sda5 available (check with df -h in a terminal).

Let's now recreate some swap :
cfdisk /dev/sda
create new partition of 1 (or 2) GB, from disk end (swap can be placed wherever so this is just psychological) of linux swap type, write changes to disk, quit and reboot.

so now we're gonna format these 2 new partitions but check that they do exist before anything else. In a terminal as root :

fdisk -l /dev/sda

will list existing partitions.

OK, if /dev/sda5 and /dev/sda6 are there, let's proceed further.
mkfs.ext3 /dev/sda5 (if you want ext3 as the filesystem)
mkswap /dev/sda6
swapon /dev/sda6

now let's copy your data from /dev/sda3 to /dev/sda5 :

mount /dev/sda5 /mnt
cp -a /home/* /mnt

wait about 30mn (YMMV), have some fun. When it's done, check that all was copied as you wanted because _we_gonna_delete_the_old_home_partition_!!!

umount /mnt  

Log out as yourself and log in again as root through gdm or in console mode (e.g. Ctrl+Alt+F2).

in the terminal :

umount /home
cfdisk /dev/sda
delete /dev/sda3
write changes to partition table
quit
reboot

now, you should login as root in gdm because we will use gparted again.
your partition table should now be :
/dev/sda1  ubuntu root
/dev/sda5  new partition with copied data from deleted /dev/sda3
/dev/sda6  swap

fire up gparted
select /dev/sda5 and choose resize / move. We want to make it about 90 or 95GB so we need to expand it to the left but leave about 12GB for the future 64studio install between /dev/sda1 and /dev/sda5. Apply the changes and wait a bit. gparted will take care of everything, moving the data, fsck'ing and so on. When it is done, you should have /dev/sda1 then 12GB of free space, then /dev/sda5 then swap on /dev/sda6. Note that you can also shrink /dev/sda1 to 12GB if you have less stuff on this partition and are not planning on adding more but you have to do this from another OS because /dev/sda1 should be modified in an UNMOUNTED state (so use live DVD or USB booted OS).

Now, you will have to modify /etc/fstab so you can mount /dev/sda5 as your new home partition. Locate the relevant line in /etc/fstab and replace /dev/sda3 by /dev/sda5. Same with swap and /dev/sda6 if it is mentioned in there. Ubuntu likes to use some weird ID's instead of physical device name. You can safely use the latter so don't hesitate to kick out the long ID string and write /dev/sda5 instead. Save changes.

Now, in a terminal, try mount /home. Now /dev/sda5 should be mounted as /home and all your precious data should be there as you would expect.

The next step is to login as yourself and see that everything is normal. Your data is there, and swap is on and all this effort has resulted in a system that looks exactly the same from the user point of view.

64STUDIO:
------------

OK. if you made it so far without any problems, you can install 64studio in the free remaining space. When you do so, just install it in one big partition spanning the whole free space and do not declare a new swap area. Create the exact same user as in ubuntu! this is important. After installation, and if grub did not mess up at installation, you should see 2 OS choice at boot start. Select 64studio in recovery mode, type your root password when asked. Then edit your /etc/fstab so that /home points to /dev/sda5. That's the trick to make it common with ubuntu. Make sure that 64studio is using the same swap (it should by default). That's it :)

If you are unfamiliar with these things, I would recommend you print my post and ask a more knowledgeable friend to go through this.

If you truly love piano playing, then it is worth it ;)

---

### Post by ethanay on 2008-05-19
wow, thank you for the suggestions.  i will post back with results.

> If you truly love piano playing, then it is worth it 

yes, definitely.  I am very excited to get this up and running. :)

---

### Post by ethanay on 2008-05-20
ok, haha, here's the update:

I followed your instructions, with the main trouble area being unable to let go of /home even when logged in as root, so I just used live cds (installation and gparted) to do the tasks.  Took extra long because gparted decided to do each function two times = about 5 hrs of partitioning (ok, I have plenty of work to do off the computer!).

the, after all that work, I did something really stupid and completely destroyed my Hardy install! (=gksudo nautilus, dir=/, select all, modify permissions....). But the reason was that permissions had already changed and did not allow me to view / at all as a normal user!  It was late and I obviously wasn't thinking :P but I just reinstalled and reconfigured Hardy.

I have successfully installed 64studio and now have a dual boot setup!, and have some issues with 64studio:
1) generally, even though it is gnome, it is very different!
2) seems to be using a generic vesa driver rather than my X3100 intel graphics card driver
3) no internet/networking (install kept saying that no network card was installed)
4) no sound with built in sound card yet

I have been spoiled by Ubuntu at least automatically detecting everything (especially internet!)...so am unsure how to proceed.  I'm sure it is relatively straightforward stuff...once I figure out what it  is.

---

### Post by thorgal on 2008-05-21
> **ethanay said:**
> ok, haha, here's the update:
hello! so you were adventurous enough ... respect! ;)

> **ethanay said:**
> 
I followed your instructions, with the main trouble area being unable to let go of /home even when logged in as root,

now that's really strange! I did that kind of partition moving around not long ago to install a triple boot system on a laptop (Ubuntu - OSX86 - WinXP) and I had to completely modify the partition table and free a lot of space because winXP and osx won't boot from logical parts but from primary.
Unmounting /home was a matter of writing umount /home in the terminal and press enter ... don't get it. Did it say 'device busy' or something ?

> **ethanay said:**
> 
 so I just used live cds (installation and gparted) to do the tasks.  Took extra long because gparted decided to do each function two times = about 5 hrs of partitioning (ok, I have plenty of work to do off the computer!).

wow! another strange thing. Gparted worked exactly as I expected it to work.

> **ethanay said:**
> 
then, after all that work, I did something really stupid and completely destroyed my Hardy install! (=gksudo nautilus, dir=/, select all, modify permissions....). But the reason was that permissions had already changed and did not allow me to view / at all as a normal user!  It was late and I obviously wasn't thinking :P but I just reinstalled and reconfigured Hardy.

haha! something quite unexpected! :lol: but couldn't you restore permissions from the live DVD ? something like 'chmod -R +r "path-to-your-mounted-hardy"' ?

> **ethanay said:**
> 
I have successfully installed 64studio and now have a dual boot setup!, and have some issues with 64studio:


OK, let's try to figure this out :

> **ethanay said:**
> 
1) generally, even though it is gnome, it is very different!

OK, you're a gnome user. I cannot help you there. I've always been using KDE since the redhat 5 days or something like that ...

> **ethanay said:**
> 
2) seems to be using a generic vesa driver rather than my X3100 intel graphics card driver

all right, my studio PC is using an intel GPU, something with 3000 in its name (X3000 I think, the mobo chips belong to the intel965 serie). SO in a terminal as root, you will do this for me :

dpkg -l xserver-xorg-video* | grep ii

If I believe correct, 64studio will have installed a bunch of xorg video drivers. The one you want is 'xserver-xorg-video-intel'.
If you have it installed, it's a matter of modifying your /etc/X11/xorg.conf. Edit it with your favorite text editor (mine is emacs) AS ROOT. For reference, here is the device section in mine :

Section "Device"
        Identifier      "Videocard0"
        BoardName       "Intel G965"
        VendorName      "Intel Integrated Graphics Controller"
        Busid           "PCI:0:2:0"
        Driver          "intel"
        Screen          0
        Option          "NoAccel" "true"
        Option          "DRI"         "false"
EndSection

You can see I disabled all h/w acc, even 2D


> **ethanay said:**
> 
3) no internet/networking (install kept saying that no network card was installed)

this one should be fairly easy, even though I do not understand why it did not configure it. Did you have an internet connection during installation ? I never had any issue with debian based systems when it comes to internet. So to make things clear, I suppose you are talking about ethernet and NOT wireless. If you only have a wireless LAN, you are on your own. I never use wireless, I find it to be a pollution for my close environment and my time spent with OS tweaking / fixing / debugging (I have enough issues with my girlfriend's beloved wireless network ...)

Now, give me the output of the terminal command 'lspci'.
If you have an intel based mobo, I suspect you would have this one :

 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)

Could be different though. Anyway, then you will give me the output of 'dmesg | grep eth' after you had booted to ubuntu (because it works in ubuntu you said). Most likely, you will just need to load the kernel module called e1000. It should be among the kernel modules. So as root, you would do : modprobe e1000
Then you would inspect what happened with 'dmesg | tail -n 20'

> **ethanay said:**
> 
4) no sound with built in sound card yet

... you're talking about the intel HDA ? strange again. The first time I installed 64studio in my PC, before I turned it to debian sid, it detected the onboard chip (intel-hda) which I have disabled in the bios since then, to free an interrupt). I believe the ALSA module for intel hda is included in the kernel package but I cannot say for sure because I never use it. IIRC, the ALSA module is called snd-intel-hda. To be sure, boot in ubuntu and type 'lsmod | grep hda' to see if it is loaded.

> **ethanay said:**
> 
I have been spoiled by Ubuntu at least automatically detecting everything (especially internet!)...so am unsure how to proceed.  I'm sure it is relatively straightforward stuff...once I figure out what it  is.

hehe, spoiled is the word but that's because ubuntu tries to be an alternative to windows with everything working OOB. Fair enough :) If computers are now shipped with ubuntu preinstalled, you would expect such flawlessness, together with positive updates that do not break it. But linux was created and written by a big bunch of hackers, unlike windows. To make it as smooth as commercial OSes that have been around for decades is quite a challenge ;)

I do think though that going through these tweaks will make you learn a bit more about the tool (laptop) you bought. As my primary school teacher kept saying : "a good worker is the one that knows his tools well" ;)

---

### Post by ethanay on 2008-05-21
> **thorgal said:**
> hello! so you were adventurous enough ... respect! ;)

Unmounting /home was a matter of writing umount /home in the terminal and press enter ... don't get it. Did it say 'device busy' or something ?
yes! that's exactly what it said!  i think in order to get around it i would have had to boot as root, as it seems to mount the /home partition early and keep it mounted until shutdown/reboot.

> wow! another strange thing. Gparted worked exactly as I expected it to work. 
in the end it did it's job well. but what i think happened was a combination of operator error plus gparted doing stupid things:  i select a partition/space to modify, enter the screen to modify, but then press cancel.  instead of cancelling, it kept the operation even though no changes were recorded.  so gparted was unnecessary in changing a 75gb partition to a...75gb partition (that's a lot of data to move for nothing).

> haha! something quite unexpected! :lol: but couldn't you restore permissions from the live DVD ? something like 'chmod -R +r "path-to-your-mounted-hardy"' ?
no, i tried that.  it was a blanket of a single permissions state across the entire hdd and all partitions (except swap..).  i was actually locked INTO gnome b/c i was "ethan" and every file on the harddrive was owned by root and couldn't even be read by me...hahaha.  something destroyed the initramfs and i could no longer boot into the os after shutting down...so i recovered my previous data from live cd and reinstalled...fortunately i have learned to keep detailed installation notes so it was a straightforward process to setup again and is actually nice to have a clean install with less "unsure tweaking" in the history!


> I do think though that going through these tweaks will make you learn a bit more about the tool (laptop) you bought. As my primary school teacher kept saying : "a good worker is the one that knows his tools well" ;)

yes, i am definitely feeling much more confident, especially w/making mistakes. it is slowly and steadily becoming a more straightforward task for install/setup as i understand how the system works.

my computer isn't with me right now, so from memory:

i spent some time late last night poking around in 64studio, and ended up breaking it by trying to manually install xserver-xorg-video-intel from lenny which completely messed up all 64studio package dependencies (whoops...).  video-intel was not present at all in default install -- instead my card was detected as an older intel i8xx-i945 (using i810 driver).  915resolution was also installed and giving an error (because it WAS properly detecting my chipset as unsupported :)   

also, raid and broadcom drivers were installed by default, and giving errors (because no hardware exists for them).  so it seems there were some hardware detection issues, although not sure why (64studio dvd md5sum = ok).  are you running 2.0 or 2.1?  i was also getting repository errors w/64studio testing enabled.

ethernet works even though install told me there was no network card (driver = tg3, same as ubuntu)! although it was really slow to respond (fullspeed throughput, but slow 5-10sec response time to new requests).  need ipw3945 drivers though.

snd-intel-hda was also installed (all normal sound packages w/lsmod), but debian was still telling me that no card was present.  upgrade to 64studio 2.1 fixed that problem and allowed sound playback, but there was still no sound output.

i am going to reformat the 64studio partition and reinstall cleanly, with an ethernet connection up and running, and see if anything is different.  if not, i will post back w/detailed update.

---

### Post by thorgal on 2008-05-21
wow! sounds like you're having a lot of iss... I mean fun ;)
Maybe it's the way you describe it but really, I did not expect you would have that much trouble! 

64studio installed no problem in my home made PC but that was a long time ago (Sept or Oct 2007) and I kept the original 64studio install only one day because it was just good old debian with an rt kernel. OK, to be fair, I am sure there is more to it than that, I don't mean to diminish the work done by the 64studio team. But I upgraded to debian sid after one day. My PC has been running debian "unstable" sid since then, I upgraded a few times, compiled my own kernel for best performances and things work just fine. My original suggestion that you could install 64studio was to prevent you from going the hard debian way and compiling your own kernel. Coming from ubuntu, you may be a bit uncomfortable with debian "geekish" (or debianish) routine. Since I'm a long time unix and linux user so it is perfectly fine with me but I cannot just assume it's the same for all ubuntu users. I do hope you will get what you seek out of this process :)
If 64studio is giving you issues, upgrade to debian sid, don't hesitate. It will probably disturb some packages but as soon as you can boot it and log in, these issues should be minor. I will check this thread from time to time if you have any questions.

---

### Post by ethanay on 2008-05-23
I just tried Jacklab Audio Distribution with high hopes for minimal out-of-box setup.  Install froze at the very last step (hardware detection and setup).  So I retried without acpi and was able to boot.  It forced my video to vesa 800x600 and wouldn't let me change the resolution even.  No internet even through wired interface, for some reason.  And both KDE and E17 are alien to me.

I will give 64studio another try, and if that doesn't work, will upgrade to SID (do I just add the repository to sources.list?), as long as I can keep a realtime kernel.

If none of this still works, my last option is just dual boot by installing a minimal Ubuntu again with rt-kernel -- doesn't it contain the same optimizations?

---

### Post by thorgal on 2008-05-23
> **ethanay said:**
> 

I will give 64studio another try, and if that doesn't work, will upgrade to SID (do I just add the repository to sources.list?), as long as I can keep a realtime kernel.

yep.

> **ethanay said:**
> 
If none of this still works, my last option is just dual boot by installing a minimal Ubuntu again with rt-kernel -- doesn't it contain the same optimizations?
it should, good idea.

---

### Post by ethanay on 2008-05-23
Good news!  I have 64studio 2.1 running and stable with wireless and built-in audio working (8.5ms latency so far) and even the multimedia hotkeys working (mute, volume, play, etc).  I haven't hooked up my keyboard, but I got a software synth playing through jack already. I am using xorg-vesa drivers forced to native resolution. 

I just have to do a last bit of basic setup and the real issues come:

Set up FFADO drivers for Echo Audiofire2
Install Wine and WineASIO
Install a VST host
Install Pianoteq and Encore 4.5.5
Native Linux apps: MuseScore, Canorus, jEdit+Lilypond

Here is where my concern is: should I really be using 64-bit when everything I run is 32-bit?  Does this just reduce performance and complicate setup?

I think it is this reason that I don't have access to Wine in the repositories...?

EDIT:  I just saw your old post -- you installed the 32-bit version!  This perhaps explains some of the package and setup difficulties!  Oh well...time to start over again :) ....but now I know what to do at least, so the 32-bit reinstall should go much quicker

---

### Post by thorgal on 2008-05-25
hehe, well spotted :)
if you want to use VST ... you can forget about running at 64 bit ...
but you seem to be getting there, that will be rewarded in time by some nice piano sound coming out of your speakers in realtime :)

---

### Post by ethanay on 2008-05-26
success! partially...

ok, so I have dssi-vst 0.7 working with Pianoteq and my built in soundcard

here are some things that i need to do:
1) reduce x-runs (currently ~1 every 30 seconds)
2) wineasio for some reason isn't recognized at all by pianoteq/wine as a sound configuration option, although it compiles and installs successfully...
3) compile ffado drivers to use with my echo audiofire2

jackdmp settings:
realtime: yes, priority: 0
frames: 128
buffer: 3
force 16 bit: yes

/etc/modprobe.d/hda-intel settings:
```
options snd-hda-intel position_fix=1
```

recommended by [http://linux-audio-music.blogspot.com/2008/05/improved-realtime-audio-with-intel-hda.html](http://linux-audio-music.blogspot.com/2008/05/improved-realtime-audio-with-intel-hda.html)
```
options snd-hda-intel model=ref position_fix=1 enable=1 index=0
```

although i'm not sure what the difference means...

i am using jackdmp instead of jack, so maybe that is an issue...
also, would disabling networking while working on sound help?

```
$ cat /proc/interrupts
           CPU0       CPU1
  0:    1944813          1   IO-APIC-edge      timer
  1:       8415          1   IO-APIC-edge      i8042
  8:          0          0   IO-APIC-edge      rtc
  9:         20         21   IO-APIC-fasteoi   acpi
 12:    1331924          2   IO-APIC-edge      i8042
 14:      46002          1   IO-APIC-edge      ide0
 17:     136277          1   IO-APIC-fasteoi   ipw3945
 18:          2          1   IO-APIC-fasteoi   ohci1394
 19:          0          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb7
 20:         15          1   IO-APIC-fasteoi   uhci_hcd:usb2, uhci_hcd:usb4, ehci_hcd:usb5
 21:     399864          1   IO-APIC-fasteoi   uhci_hcd:usb3, uhci_hcd:usb6, HDA Intel
 22:          0          0   IO-APIC-fasteoi   sdhci:slot0
218:          0          2   PCI-MSI-edge      eth1
219:       9797      21787   PCI-MSI-edge      libata
NMI:          0          0
LOC:     287560     800497
ERR:          0
MIS:          0

```

---

### Post by thorgal on 2008-05-26
hey Ethanay, almost there :)
your networking is decoupled from your sound processing so it's not an issue.
What you need is to tweak the IRQ thread priority.

Get hold of two things : irqbalance and rtirq. I think they are in the sid repos. Here is my /etc/default/rtirq conf :

```

#!/bin/sh
#
# Copyright (c) 2004-2007 rncbc aka Rui Nuno Capela.
#
# /etc/default/rtirq
#
# Configuration for IRQ thread tunning,
# for realtime-preempt enabled kernels.
#
# This program is free software; you can redistribute it and/or modify it
# under the terms of the GNU General Public License version 2 or later.
#

# IRQ thread service names
# (space separated list, from higher to lower priority).
RTIRQ_NAME_LIST="rtc snd i8042"

# Highest priority.
RTIRQ_PRIO_HIGH=99

# Priority decrease step.
RTIRQ_PRIO_DECR=2

# Whether to reset all IRQ threads to SCHED_OTHER.
RTIRQ_RESET_ALL=1

# On kernel configurations that support it,
# which services should be NOT threaded
# (space separated list).
RTIRQ_NON_THREADED="rtc snd"

# Process names which will be forced to the
# highest realtime priority range (99-91)
# (space separated list, from highest to lower priority).
RTIRQ_HIGH_LIST="softirq-timer softirq-hrtimer"

```

irqbalance does not take any config.


Regarding the performance, don't forget what I said : USB devices require CPU cycles, and your onbaord chip shares its interrupt with the USB controller. 

Now, for the not so good part, the intel HDA chip is a bit problematic with RT operations and jackd. This is what I gather from many different linux audio forums. The kernel module option (position_fix) is triggering a workaround for some timing  inaccuracy. You may get some more info from the jackaudio mailing list or the alsa forums. 

Wine stuff :

you should be aware that you need to have wine configured properly for audio operations. So fire up 'winecfg', go to the audio tab and only select ALSA. Don't select jack. It is to ensure that wineasio will work with MIDI (if I understood correctly, could mean something else though).

Regarding, wineasio, don't forget to register the compiled library. In a terminal as yourself, do the following :

regsvr32 /usr/lib/wine/wineasio.dll.so

or wherever you have the so file.

One thing that is not clear. You outboard device is USB, isn't it ? or is it firewire or PCMCIA ?

By the way, one last thing : use jackd. You don't really need jackdmp. I think Stéphane Letz should be more clear about it for people using MP procs. I thought originally that  because I use a Core 2 Duo proc, jackdmp would performe better. But from what I understood from him, the way I work with my PC studio does not take advantage from the MP capability of jackdmp. I use the latest jack svn version. And it works very nice. I can run VSTi's with a very small buffer size (64) at  96kHz. But I don't do this because the latest ardour is a bit unstable with this setting. I run at buf size 256 most of the time and I have no problems.

---

### Post by ethanay on 2008-05-27
more good news!

I clobbered the wineasio problem:  completely uninstalled pianoteq, wineasio, wine, removed the .wine folder

uninstalled jackdmp, libjackmp and reinstalled jackd for good measure

reinstalled wine
reinstalled wineasio
"regsvr32 /usr/lib/wine/wineasio.dll.so"
ran winecfg to detect alsa audio
reinstalled Pianoteq

and was able to select wineasio! I have to start pianoteq without jackd running otherwise it won't start at all (freezes) -- but i can start with jackctl already open, so it is relatively easy to start/stop when adding pianoteq.  so I now have pianoteq vst and pianoteq standalone working well for maximum flexibility.  this is very good.  there seem to be less xruns with jackd even though it uses more processor (~1.5x's as much as jackdmp).

so it was either a jackdmp/wineasio error, or a problem with typing "regsvr32 wineasio.dll."  If that is the wrong command, then it shouldn't give a message, "driver successfully registered" when it doesn't actually register a driver!!

ok, i will follow your steps for the irq tuning for maximum performance.

my external audio card is firewire:  echo audiofire2.  ffado.org lists it as "fully supported."  i have already plugged the card in and it is recognized by the firewire bus, so i just need to successfully compile ffado and it should work.

my keyboard hooks up via usb successfully, so really ffado seems to be the last software/hardware interface component!  other than that, i have to buy a few balanced 1/4" cords > audiofire2 > mixer > speakers.  i am also installing seq24 0.8.7 to use with Pianoteq vst, to record midi and also export midi to audio using pianoteq to process the sound.

---

### Post by thorgal on 2008-05-27
sounds good ... except for the jackd freeze, don't get it. Which version of wineasio are you using ? I've had small issues with 0.7.3 and downgraded to 0.5. I've heard there's a newer version but I rarely use wineasio so I don't really care (I use dssi-vst most of the time, the 0.7 version works really nice, was updated to the newer jackd API).

---

### Post by ethanay on 2008-05-27
sorry -- I was unclear about that.  Pianoteq freezes, jackd continues to run fine :)  so I just have to start Pianoteq, which starts jackd.  If I want to stop/start again, then I have to reload Pianoteq.  But that is only with the standalone.

I am using dssi-vst 0.7, wineASIO 0.7.4.  so far haven't noticed issues with WineASIO

---

### Post by ethanay on 2008-05-30
Ok, rtirq was installed by default...here are the settings:

```
#!/bin/sh
#
# Copyright (c) 2004-2007 rncbc aka Rui Nuno Capela.
#
# /etc/default/rtirq
#
# Configuration for IRQ thread tunning,
# for realtime-preempt enabled kernels.
#
# This program is free software; you can redistribute it and/or modify it
# under the terms of the GNU General Public License version 2 or later.
#

# IRQ thread service names
# (space separated list, from higher to lower priority).
RTIRQ_NAME_LIST="rtc snd usb i8042"

# Highest priority.
RTIRQ_PRIO_HIGH=90

# Priority decrease step.
RTIRQ_PRIO_DECR=5

# Whether to reset all IRQ threads to SCHED_OTHER.
RTIRQ_RESET_ALL=0

# On kernel configurations that support it,
# which services should be NOT threaded 
# (space separated list).
RTIRQ_NON_THREADED="rtc snd"

# Process names which will be forced to the
# highest realtime priority range (99-91)
# (space separated list, from highest to lower priority).
# RTIRQ_HIGH_LIST="softirq-timer"
```

---

### Post by thorgal on 2008-05-30
do you see the last line ? it is commented out on purpose because it does not want to assume that you are running a RT patched kernel. If you run such a kernel, uncomment this line.

Another thing, because you don't use a USB audio device, remove the usb from the list of prioritary dev classes. And turn on SCHED_OTHER for anything that is not relevant for non audio processing (see my rtirq conf above for inspiration).

---

### Post by ethanay on 2008-06-01
ok, I have some questions about the differences and meanings:

1) ```
# IRQ thread service names
# (space separated list, from higher to lower priority).
RTIRQ_NAME_LIST="rtc snd usb i8042"

```

should this include firewire? how do i do that?

2) mine:```
# Highest priority.
RTIRQ_PRIO_HIGH=90

```

yours:```
# Highest priority.
RTIRQ_PRIO_HIGH=99

```

Does this mean that your system can assign irqs that have 9 priority levels higher than mine?  So I should increase my value to 99 to ensure maximum priority for audio/midi processes?

3) mine:```
# Priority decrease step.
RTIRQ_PRIO_DECR=5

```

yours:```
# Priority decrease step.
RTIRQ_PRIO_DECR=2

```

I'm not sure what this does...

4) mine:```
# Whether to reset all IRQ threads to SCHED_OTHER.
RTIRQ_RESET_ALL=0

```

yours:```
# Whether to reset all IRQ threads to SCHED_OTHER.
RTIRQ_RESET_ALL=0

```

not sure what this does...my guess is enabling it helps to free up high priority irq values when necessary...? is this correct?

5) mine:```
# Process names which will be forced to the
# highest realtime priority range (99-91)
# (space separated list, from highest to lower priority).
RTIRQ_HIGH_LIST="softirq-timer"

```

yours:```
# Process names which will be forced to the
# highest realtime priority range (99-91)
# (space separated list, from highest to lower priority).
RTIRQ_HIGH_LIST="softirq-timer softirq-hrtimer"

```

ok, so i should uncomment this to help move processes to high priority.  what is "softirq-hrtimer"?  is it something i should add?

ps do you have a place i could send you a small audiofile?  i made a few recordings with pianoteq :D
using dssi-vst and jack time machine (very nice little program).  i am still figuring out midi sequencing...

---

### Post by thorgal on 2008-06-01
> **ethanay said:**
> ok, I have some questions about the differences and meanings:

1) ```
# IRQ thread service names
# (space separated list, from higher to lower priority).
RTIRQ_NAME_LIST="rtc snd usb i8042"

```

should this include firewire? how do i do that?



not sure about firewire but your /proc/interrupts had this service : ohci1394 at IRQ 18, which, if I'm not wrong, is firewire. See what the PID of this IRQ-thread corresponds to. In a shell, type (copy/paste my command):

chrt -p `pgrep IRQ-18`

and check what priority it is set to. If it is SCHED_OTHER or a low SCHED_FIFO (50 or below), then replace usb by ohci1394 in the rtirq conf file, rerun /etc/init.d/rtirq and check again the thread priority.

> **ethanay said:**
> 
2) mine:```
# Highest priority.
RTIRQ_PRIO_HIGH=90

```

yours:```
# Highest priority.
RTIRQ_PRIO_HIGH=99

```

Does this mean that your system can assign irqs that have 9 priority levels higher than mine?  So I should increase my value to 99 to ensure maximum priority for audio/midi processes?

yeah, I just boosted the priority to the max I could think of (did not try 100 though).

> **ethanay said:**
> 
3) mine:```
# Priority decrease step.
RTIRQ_PRIO_DECR=5

```

yours:```
# Priority decrease step.
RTIRQ_PRIO_DECR=2

```

I'm not sure what this does...

not all threads will be assigned the max priority you set above. There will be a decrementation of the priority for the various threads at stake. Here, you just configure the step by which you decrement priorities. SO instead of jumping from 90 to 85 to 80, etc, I set mine to jump from 99 to 97 to 95, etc.

> **ethanay said:**
> 
4) mine:```
# Whether to reset all IRQ threads to SCHED_OTHER.
RTIRQ_RESET_ALL=0

```

yours:```
# Whether to reset all IRQ threads to SCHED_OTHER.
RTIRQ_RESET_ALL=0

```

not sure what this does...my guess is enabling it helps to free up high priority irq values when necessary...? is this correct?

mine is set to 1, you have a typo here. It is to set all other threads that do not participate in the audio proc (for exemple network, etc) to SCHED_OTHER, a non prioritary schedule.

> **ethanay said:**
> 
5) mine:```
# Process names which will be forced to the
# highest realtime priority range (99-91)
# (space separated list, from highest to lower priority).
RTIRQ_HIGH_LIST="softirq-timer"

```

yours:```
# Process names which will be forced to the
# highest realtime priority range (99-91)
# (space separated list, from highest to lower priority).
RTIRQ_HIGH_LIST="softirq-timer softirq-hrtimer"

```

ok, so i should uncomment this to help move processes to high priority.  what is "softirq-hrtimer"?  is it something i should add?

I added it myself without exactly knowing if it would help. I just noticed in the process list (ps xa) that each CPU core has a softirq timer and a softirq hrtimer so I speculated that it wouldn't hurt to add it.

> **ethanay said:**
> 
ps do you have a place i could send you a small audiofile?  i made a few recordings with pianoteq :D
using dssi-vst and jack time machine (very nice little program).  i am still figuring out midi sequencing...


aegirr at gmail dot com


MIDI sequencing : what have you tried so far ?

---

### Post by ethanay on 2008-06-01
alright, i will send you a sample first take as celebration for getting things up and running :D (hooray!)

output of "chrt -p 'pgrep IRQ-18':
pid 947's current scheduling policy: SCHED_FIFO
pid 947's current scheduling priority: 50

so i will add ohci1394 to rtirq.  should i actually keep "usb" in the priority services list if i connect my midi keyboard via usb to my computer?

as far as sequencers, i am learning to use seq24 for fun (it is a great little amazing program), but am trying to get MusE working for song-length "midi performance recording"

---

### Post by thorgal on 2008-06-02
sounds cool, all this sweat finally pays off :)
about the USB, I don't really know, I don't use my digital piano through USB but through standard MIDI sockets. Try first without USB in the priority list. I doubt that it should cause problems.

Muse is cool, I tried it a few times. You can also look into many other sequencers. I find rosegarden to be very usable but I am not doing any MIDI multitracking with it, just single tracking with drum sequences. WHen I play the piano, I am not saving to MIDI but directly to audio (have not composed any serious songs with piano sequences yet).

---

### Post by ethanay on 2008-06-02
ok, i just broke 64studio trying to install ffado and so backed up my personal files and erased the 64studio partition.

not sure whether to try again but i need firewire support, and there was no way for me to upgrade to jackd 0.109.2 without breaking the entire system and it wouldn't let me reinstall anything because the sound apps depended on libjack0 0.103.x

back to the drawing board???
:(

---

### Post by thorgal on 2008-06-02
wow! that's a bit sad. How do you say it broke your OS ? it sounds a bit drastic to me. Isn't ffado only a piece of lib or driver ?

---

### Post by ethanay on 2008-06-02
I think maybe I will try a stripped-down Ubuntu 8.04 with rt-kernel...it is at least familiar...do you have suggestions?

---

### Post by thorgal on 2008-06-02
... not an obvious solution in mind ... if I had had access to your laptop, I would have upgraded your 64studio to debian sid ...

if you go the ubuntu studio road, I don't really know but from what I gather here and there, I would try Gutsy first, see if it works, if not upgrade to Hardy ... what a pain ... 

You know what ? I remember the first times I was fiddling around all this things. I only had a laptop and it was a lot of pain, never got it to work as I wanted! having a dedicated PC for music prod is another story ... much less pain I must say. But I guess you are not looking into this, you only want to play piano.

---

### Post by ethanay on 2008-06-03
hi Thorgal,

i appreciate all the help you've given, and i don't want to bug you too much more...i've learned a lot through this process, though!  so that is a positive (despite all the frustrations).   i installed another Ubuntu and tried the rt kernel and basic irq setup, but there are a few buggy things (e.g., jackd not using tmpfs?? so as soon as i start recording to disk huuuuuge xruns!).

fortunately, 64studio might still have me [covered]("http://64studio.com/node/586"), so i am excited that maybe i will be able to benefit from more of a "sid" situation and still help give back to 64studio at the same time.

again, i appreciate all the energy you've put into helping me, i've learned a lot from it (and will keep learning...).

---

### Post by ethanay on 2008-06-07
just as an update, I have 64studio running again, updated to 3.0beta (lenny repos).  SID is just a small leap away, but this is really close to the the current 8.04 package versions of Ubuntu and has good support for my current hardware.

I am only hoping I can get my firewire card working...! (might be [hardware incompatibility]("http://forum.notebookreview.com/showthread.php?t=73829")...)

---

### Post by thorgal on 2008-06-07
Cool :)

did you get my email about Sidux ? I heard about it yesterday only but it is debian sid for audio prod (as far as I could get from what I quickly read). But 64studio is probably more stable so if it works well, stick to it :)

---

### Post by ethanay on 2008-06-08
haha, yes, I don't think I will randomly abandon 64studio now that I have 3.0beta set up :P

for the time being, I am DONE with deleting and reinstalling operating systems...

---

### Post by ethanay on 2009-12-22
since Ubuntu 9.10 supports adequate real-time performance for Pianoteq without needing a specialized real-time kernel, and there is a native Linux version of Pianoteq available, I consider this thread solved,

---

