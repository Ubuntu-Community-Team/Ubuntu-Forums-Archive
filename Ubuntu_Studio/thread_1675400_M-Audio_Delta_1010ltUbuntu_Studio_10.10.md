---
title: "M-Audio Delta 1010lt/Ubuntu Studio 10.10"
date: 2011-01-25
forum: Ubuntu Studio
---

### Post by stagekraft on 2011-01-25
Hey All, I'm a complete newbie to Ubuntu Studio, I started reading about  it last month and got a wild hair up my butt that I was going to build a  new home studio (I've been pinging tracks on an old 4-track  porta-studio for years). I had a spare PC that I stuck a new hard drive  in and did a fresh install of Ubuntu Studio v.10.10, then I bought two  M-Audio Delta 1010lt PCI cards (found them pretty cheap on ebay), and  installed them on this PC, so at this point I should have a working  16-track system.

Aside from the learning curve of an unfamiliar  Operating System, I'm also muddling through all the Audio software that  installs with Ubuntu Studio (trying to figure out what I really need to  get started).

It looks to me that all I really need to record  analog audio  is Jack and Ardour (and ALSA drivers, but I'm assuming  this was setup during the initial install), but there seems to be some  confusion (in my head) on how to assign the 16 real analog inputs (from  the 2 Delta 1010lt cards) to the software inputs in Ardour.

When I  start Jack, I get an error message that it could not "connect to Jack  server as a client", but after I start Ardour then Jack shows an active  connection. Is this normal? should I be starting Ardour first?

Once  I get to the "connections" screen in Jack I see "System" and "Ardour"  listed in both the "readable clients" and "writable clients" sides of  the screen, and it looks like the "System" should refer to the real I/O  of my sound cards, and "Ardour" refers to the software I/O of Ardour?

What  confuses me at this point is that under readable "System"  it shows  capture_1 through 12, where I think I should see 16 (or 2 banks of 8, as  each card has 8 analog inputs). Like wise on the writable "System" side  I see playback_1 through 10, where again I think I should see 16 (or 2  banks of 8 as each card has 8 analog outputs).

I can only assume that I missed something, somewhere, but I'm not sure what......

Has  anyone out there in Forum land had any direct experience with the  M-Audio Delta 1010lt cards (used in the Ubuntu Studio environment,  instead of their intended Windoze or Mac environment)?

Any help would be appreciated,   

John

---

### Post by Pablo_F on 2011-01-25
Hi, 

> It looks to me that all I really need to record analog audio is Jack and Ardour (and ALSA drivers, but I'm assuming this was setup during the initial install),

Yes. You can also use plugins inside ardour. You can connect other jack-aware apps to and from ardour and to and from "system". See jackaudio.org

> When I start Jack, I get an error message that it could not "connect to Jack server as a client", but after I start Ardour then Jack shows an active connection. Is this normal? should I be starting Ardour first?

Not sure about what could not connect to jack server, can you show the message window of qjackctl? Anyway, your audio card and ardour could connect to jack server, so don't worry for this, I would say.

> Once I get to the "connections" screen in Jack I see "System" and "Ardour" listed in both the "readable clients" and "writable clients" sides of the screen, and it looks like the "System" should refer to the real I/O of my sound cards, and "Ardour" refers to the software I/O of Ardour?

...to the real (and not so real) I/O of your soundcard (not soundcards). Normally, jack uses one soundcard at a time. System is the generic name for the soundcard that jack is using. Anyway, see below.

> What confuses me at this point is that under readable "System" it shows capture_1 through 12, where I think I should see 16 (or 2 banks of 8, as each card has 8 analog inputs). Like wise on the writable "System" side I see playback_1 through 10, where again I think I should see 16 (or 2 banks of 8 as each card has 8 analog outputs).

jack is seeing one audio card . 8 analog capture ports + capture digital ports? + ? Not sure. Search the internet. I know there is some internal mixing in that card that explains the rest of the available ports. You can access the internal mixer by means of an alsa tool called *envy24control*. You use envy24control to set the ADC and DAC levels as well.

To have multiple soundcards as a unique alsa virtual interface, you have to do some work. See here: 

[http://www.jrigg.co.uk/linuxaudio/ice1712multi.html](http://www.jrigg.co.uk/linuxaudio/ice1712multi.html)

Cheers! Pablo

---

### Post by sgx on 2011-01-25
[http://ubuntuforums.org/showthread.php?t=1674355](http://ubuntuforums.org/showthread.php?t=1674355)

This was for a recent chat about mAudio Delta44, just basic ideas that
can be used for most soundcards, and some particulars
for mAudio products.
1010s are NICE! :)

---

### Post by nealos on 2011-01-25
Hey John!  Welcome to the exciting world of Linux and the even more challenging and wonderful world of Linux audio recording!  I'm only a bit ahead of you in experience with only one 1010lt card using 64Studio but I really want to add another card and switch to Ubuntu.  Needless to say, I'll be interested in your progress.  Thank you Pablo_F and SGX for the info and links.  I shall be studying.  Just glancing over things, getting a two card configuration looks way more involved than I had imagined.

Good luck!

-Neal

---

### Post by stagekraft on 2011-01-26
Thanks to all for the input, Pablo, it sounds like you have a pretty good grasp of the configuration stuff. The link you posted was interesting reading (and as the author suggested, I read it several times), but even after reading it, I still don't get it all...... and this falls back on my lack of experience with linux.....

I'm assuming that I could cut & paste his example into the text editor, and name the file .asoundrc
but what do I do with it? I assume that ALSA needs to read this configuration, but does it replace an existing file somewhere? is there a specific folder that it needs to go in?

I know I could go back to one card, but hey, I already have two, and if I can get it to work, all the better!

Again, thanks for the input, sorry for being such a naive newbie......

John

---

### Post by cchhrriiss121212 on 2011-01-26
I would just like to say first that what you want to achieve here will not be a point and click away, you are looking at dozens of hours setup and tweaking, in addition to the time it will take for you to understand how Linux audio works. If that is OK with you then read on.
> I'm assuming that I could cut & paste his example into the text editor, and name the file .asoundrc
but what do I do with it? I assume that ALSA needs to read this configuration, but does it replace an existing file somewhere? is there a specific folder that it needs to go in?An .asoundrc file goes in your home folder like this:
/home/username/.asoundrc
The example shown in that link is for a different card so I don't think it would work if you were to just copy and paste. And you don't even have one card working so I would forget about using two for the time being.
> 
What confuses me at this point is that under readable "System" it shows capture_1 through 12, where I think I should see 16 (or 2 banks of 8, as each card has 8 analog inputs). Like wise on the writable "System" side I see playback_1 through 10, where again I think I should see 16 (or 2 banks of 8 as each card has 8 analog outputs).The Delta series will always show up with 12 ports in jack regardless of how many you actually have, I have no idea why. 

What you should aim for first is to get jack going. It will help if you could post some terminal output. Go to Accessories>Terminal and paste in this and press enter:
```
aplay -l && lspci -v && cat ~/.jackdrc
```
And also post the contents of the jack message window after you start it up.

---

### Post by Pablo_F on 2011-01-26
> 
I'm assuming that I could cut & paste his example into the text editor, and name the file .asoundrc... is there a specific folder that it needs to go in?

Yes, as Chris said, the folder must be your home directory, /home/username/.

Create a new text file called *.asoundrc* with that content. Note that files and directories beginning with a dot are hidden by default. 

> but what do I do with it? I assume that ALSA needs to read this configuration, but does it replace an existing file somewhere? 

No, it does not replace any text-based configuration.

Normally and currently, with a soundcard fully supported by alsa (e.g., a single m-audio pci) .asoundrc file is not needed. The alsa driver is enough. This is a further configuration and you don't have to do anything to tell the alsa driver to read that file. Well, maybe restart the computer.

Oh, wait, you might want to read this:

[http://alsa.opensrc.org/index.php/.asoundrc](http://alsa.opensrc.org/index.php/.asoundrc)


> The example shown in that link is for a different card so I don't think it would work if you were to just copy and paste. And you don't even have one card working so I would forget about using two for the time being.

I don't think so. The example is for a card like yours (well, maybe the non LT, but that shouldn't matter here). He already has a card working, I mean, jackd starts and he sees ardour and the default card (one of the m-audio's) in qjackctl connections.


To somehow complete the guide:

jackd (jack daemon) is the jack server, a process which runs on the background. qjackctl (aka Jack Control) is a GUI front-end which is used by many people to configure and start the jack server. 

> jackd can be started using the following command-line syntax:

$ jackd -R -d alsa -C multi_capture -P multi_playback

In recent version, you don't need the -R option to have jack in realtime mode. Do a:

jackd -V

to know your jack version. jackdmp 1.9.x is jackd2.  

Realtime mode is strongly recommended, so you can have low latency with no xruns. In order to be able to run jackd in realtime mode, you must have the rtprio and memlock privileges enabled. Check with the command *ulimit -r -l* Anyway, you can have realtime mode in jack with a generic kernel (many people have been confused about this). This is a must read:

[http://jackaudio.org/faq](http://jackaudio.org/faq)

Anyway, in qjackctl, the suggested command above is achieved by writing down *multi_capture* and *multi_playback* in the "Input Device" and "Out Device" fields, respectively, leaving the "Interface" field as (default). 

Cheers, Pablo

---

### Post by stagekraft on 2011-01-27
weee-ha......

I think I'm getting close........

I went back to;

[http://www.jrigg.co.uk/linuxaudio/ice1712multi.html](http://www.jrigg.co.uk/linuxaudio/ice1712multi.html)

and read it some more........

this time I tried the alternate .asoundrc file for running 2 or 3 delta 1010's, and started JACK from the command line using;

jackd -R -d alsa -C capture16 -P playback16 -p1024

BUT, before I started JACK, I modified the ALSA configuration as shown farther down in the above link, listed under "**Alternative to envy24control** ", I copied his example of the asound.state file, named it asound.state.delta1010x2, and ran it from the command line using;

alsactl -f asound.state.delta1010x2 restore

Now, when I open JACK with the qjackctl (Jack Control), I see 16 inputs and 16 outputs in the connections window.

I was able to patch the 16 inputs to Ardour, and the Stereo Mix from Ardour back to two outputs.

At this point though, I just have my PC freestanding at my desk, the real proof will be when I drag it out to my music room (a small insulated room out in my shed), and hook up some mics and instruments to the inputs and send the outputs to my amp/monitors.

I'll report back any success or failures later.

Thanks to everyone for their suggestions......

John

---

### Post by Pablo_F on 2011-01-27
Well done! 

You won't be alone. Check this: 

[http://ardour.org/node/3248](http://ardour.org/node/3248)

Cheers! Pablo

---

### Post by tgalati4 on 2011-01-27
Makes my Pentium II, 300 Mhz machine with an M-audio Delta66 seem rinky-dink, but it works well for 2-hour church concert recordings using dynabolic.

---

### Post by sgx on 2011-01-28
> **tgalati4 said:**
> Makes my Pentium II, 300 Mhz machine with an M-audio Delta66 seem rinky-dink, but it works well for 2-hour church concert recordings using dynabolic.
Get a 2 or 3 ghz P4 from the Goodwill or local pc recycler, probably
$30-50, or some will trade for labor. :guitar: I'm also a Dynebolic fan.

---

### Post by stagekraft on 2011-02-01
Well, I finally got a chance to hook my system up, and after playing with some levels in envy24control I have sound going in and sound coming out, that's a good sign.

but, what I record has a lot of dropouts, so I guess this is related to the xrun stuff and this is where the magic tweaking begins.......... can anybody point me in the right direction?

also, although I used the previously mentioned script to start envy24control to get my I/O from both cards, the envy24control gui still just shows the I/O of one card, so I'm not sure how I'm going to set levels and such for all the channels.

any help would be appreciated, John

---

### Post by Pablo_F on 2011-02-01
> also, although I used the previously mentioned script to start envy24control to get my I/O from both cards, the envy24control gui still just shows the I/O of one card, so I'm not sure how I'm going to set levels and such for all the channels.

Supposedly, the script loads sane settings and you don't need to manipulate DAC and ACD levels once they are set. Anyway, you can always invoke envy24control for the second card like this (counting is zero based):

envy24control -c 1

For command line tools, you normally get instructions with man. Try:

man envy24control

> 
but, what I record has a lot of dropouts, so I guess this is related to the xrun stuff and this is where the magic tweaking begins.......... can anybody point me in the right direction?

Take a look at linuxmusicians wiki. What jackd settings are you trying (*cat ~/.jackdrc* will suffice in lieu of a qjackctk setup screenshot) and what is the output of *cat /proc/interrupts*

Cheers, Pablo

---

### Post by stagekraft on 2011-02-09
been busy the past week, just got back to working on this....................

Pablo, you asked me a couple questions last week;

  > What jackd settings are you trying (*cat ~/.jackdrc* will suffice in lieu of a qjackctk setup screenshot) and what is the output of *cat /proc/interrupts*

When I do "[I]cat ~/.jackdrc", I get the following;
  
/usr/bin/jackd -p 128 -R -P 60 -T -d alsa -C hw:0,0 -P hw:0,0 -n 2 -r 48000 -p 1024
  
which is different from the command line I use to start jackd, which is;
  
/usr/bin/jackd -R -d alsa -C capture16 -P playback16 -p1024
  
when I run [/I]qjackctl there is a checkbox to save settings to  .jackdrc, but despite this being checked it always saves the former even  though I start jackd with the latter......... I've tried deleting,  overwriting, renaming, .jackdrc but it alway comes back with these  settings. Does this make sense? What am I missing?

Now so far as the "*cat /proc/interrupts", I get;*

john@stagekraft:~$ cat /proc/interrupts
           CPU0       CPU1       
  0:         44          0   IO-APIC-edge      timer
  1:          2          2   IO-APIC-edge      i8042
  7:          0          0   IO-APIC-edge      parport0
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          3          3   IO-APIC-edge      i8042
 14:       3880       4062   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:         95        667   IO-APIC-fasteoi   uhci_hcd:usb5, ICE1712
 17:        106         86   IO-APIC-fasteoi   ICE1712
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 19:       5918       1472   IO-APIC-fasteoi   ata_piix, uhci_hcd:usb3
 23:         83         83   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
 42:         23       1276   PCI-MSI-edge      eth0
 43:         77        742   PCI-MSI-edge      i915
NMI:          0          0   Non-maskable interrupts
LOC:      20101      26316   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:       1264       2237   Rescheduling interrupts
CAL:         75         63   Function call interrupts
TLB:        338        348   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          2          2   Machine check polls
ERR:          1
MIS:          0


Not sure what it all means, but you asked for it.........


Now, getting back to the link to John Rigg's webpages, he talks about  problems using his multi-card setup with the Realtime -rt kernel, and  adds that users "are  likely to get better results with a non-rt kernel with CONFIG_PREEMPT=y".   What does this all mean?

I thought I read somewhere (but of course I can't seem to find it back),  that the -rt kernel is part of more current releases of Ubuntu Studio,  and older versions were non-rt, Can anyone verify this for me? If so,  does this mean I may have better luck using an older distro of Ubuntu  Studio?

Thanks in advance to all,

John

---

### Post by Pablo_F on 2011-02-09
> When I do "cat ~/.jackdrc", I get the following;

/usr/bin/jackd -p 128 -R -P 60 -T -d alsa -C hw:0,0 -P hw:0,0 -n 2 -r 48000 -p 1024

which is different from the command line I use to start jackd, which is;

/usr/bin/jackd -R -d alsa -C capture16 -P playback16 -p1024

when I run qjackctl there is a checkbox to save settings to .jackdrc, but despite this being checked it always saves the former even though I start jackd with the latter......... I've tried deleting, overwriting, renaming, .jackdrc but it alway comes back with these settings. Does this make sense? What am I missing?

Hi,

When you start jackd from the command line, nothing is saved to ~/.jackdrc. The "jackd command" that is written to this file is the one that results from the configuration through the qjackctl gui (Jack Control, Setup, Configurations). See the screenshot, something of the sort will work for you. However, if you want to start jackd from the command line, don't bother with qjackctl setup or ~/.jackdrc. Sorry if I misslead you, but me and most people use qjackctl to set the jackd command (and for a few more things).

All in all, I don't see anything wrong with your jackd comand (I mean, what you are using from a terminal).

However, look at this:

16: 95 667 IO-APIC-fasteoi uhci_hcd:usb5, ICE1712
17: 106 86 IO-APIC-fasteoi ICE1712

One of your M-audio's (here identified as ICE1712, which must be the name of the chip, IIRC) is sharing IRQ number with an USB bus. This is far from ideal...

I don't own two m-audio's so that I can try to reproduce the problem and make tests.

> he talks about problems using his multi-card setup with the Realtime -rt kernel, and adds that users "are likely to get better results with a non-rt kernel with CONFIG_PREEMPT=y"

Note that very knowledgeable linux users tend to be "distro-neutral", many don't use ubuntu and they often compile their own customised kernels. Terminology is overwhelming and sometimes cause of confusions but you will realise. 

I recommend you go ask John for suggestions. You might need a rt kernel after all (which allows you to give hardware priority to the ICE1712's even if they share IRQ number with another hardware device. You can't do this with a generic kernel or a low-latency kernel). If you install an rt kernel, you need to install and configure the rtirq script as well. See [http://www.rncbc.org/drupal/node/107](http://www.rncbc.org/drupal/node/107) 

Oh, wait, of course, before attempting this, try with the so called low-latency kernel or -preempt kernel, which is the kernel that John is refering to, I think. (this kernel configuration CONFIG_PREEMPT=y is applied on both of them, I think. I am not sure).

Just in case, you are scratching your head here:
[https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel](https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel)

The bad news is that ubuntu(studio) 10.10 does not have rt or low-latency / preempt kernels precompiled in the official repos... 

I recommend you give tango studio a try (google for it). It is based on ubuntu 10.04. You have rt in the official repos (so installing it is very easy). What's more, tango studio uses a low_latency kernel by default and it gets rid of pulseaudio, an audio server that you definitely don't need (unless you want to have "system sounds" in your studio).

Of course, you will need to hack again an .asoundrc, but apart form that, it will run fine, hopefully.

Cheers, Pablo

---

### Post by stagekraft on 2011-03-04
Hey All.....

Well after a couple months of banging my head on the wall, trying every setting I thought was going to fix my problem, I finally had a revelation. After sifting through all the great information everyone here was providing (special thanks to pablo), I finally decided that my problems had to be hardware related. The PC I was using was fairly new with lots of bells and whistles, running an Intel dual core cpu. The PC only had two pci slots and one was sharing irq with some usb.

So just to try something, I took my older "home" PC, with three pci slots, running a single core P4 cpu, and swapped drives and my soundcards around (of course the biggest headache was getting Windows to accept a drastic change of hardware), Ubuntu Studio fired right up on the older PC.....

I ran "cat /proc/interrupts" and saw my two soundcards sitting on irq's 17 & 18 all by themselves.

I ran my script that sets ALSA up to use both soundcards, started jackd, and then Ardour.

At first I thought the whole thing had locked up because the terminal window I had open from starting jackd was just still, and I was used to seeing it constantly scrolling..... But then I realized it was doing just what it was supposed to do, running solid and steady....

I hooked up a mic and did a little test recording, playback was flawless, no xruns, no dropouts, just working like I envisioned when I started this project a couple months ago.

Interestingly enough, when I played back some test recordings I had previously made that were full of dropouts, they played back without dropouts, so does this mean that the xruns and dropouts are playback related glitches and not recording glitches?

Of course, while getting one track to record was a milestone, the proof will be how well it handles all 16 inputs at once.

I'm sure I'll be back here soon, looking for answers about post production stuff....

Regards,
John

---

### Post by Pablo_F on 2011-03-04
Hi!

This is good news! :)

> Interestingly enough, when I played back some test recordings I had previously made that were full of dropouts, they played back without dropouts, so does this mean that the xruns and dropouts are playback related glitches and not recording glitches?

It could be both. Also, not every reported xrun is audible, at least for me when I was a beginner and had a few.

For future recordings, Ardour has a nice feature in Options -> Misc Options -> Create marker at xrun location. This way you can go and check the sound if you happen to have one while you are recording. You can also just choose "Stop recording on xrun". 

EDIT:

The ardour forum and mailing list are better places to ask about ardour and post-production. 
 
Cheers, Pablo

---

