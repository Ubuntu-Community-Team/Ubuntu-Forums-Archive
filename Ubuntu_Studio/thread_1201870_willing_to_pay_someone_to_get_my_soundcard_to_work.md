---
title: "willing to pay someone to get my soundcard to work properly"
date: 2009-07-01
forum: Ubuntu Studio
---

### Post by Magick93 on 2009-07-01
Hi

I am so frustrated - and have wasted so much time - on trying to get my X-fi sound card to work. While I do have audio from Totem, Flash and Rhythym Box (using OSS) I do not have midi - and apparently midi with X-fi is not supported/unavailable with OSS. So the only option is using ALSA. I have repeated tried to get ALSA to work with the x-fi card but cannot get any sound at all.

is there anyone who has the skills to fix this issue, and how much would it cost??

---

### Post by ibuclaw on 2009-07-01
> **Magick93 said:**
> Hi

I am so frustrated - and have wasted so much time - on trying to get my X-fi sound card to work. While I do have audio from Totem, Flash and Rhythym Box (using OSS) I do not have midi - and apparently midi with X-fi is not supported/unavailable with OSS. So the only option is using ALSA. I have repeated tried to get ALSA to work with the x-fi card but cannot get any sound at all.

is there anyone who has the skills to fix this issue, and how much would it cost??

I could walk you through a possible solution that may rectify your issue for the "hole-in-pocket" price of **£0.00** :)

Here seems to be the thread you want to look at on these forums: [http://ubuntuforums.org/showpost.php?p=3504186&postcount=1](http://ubuntuforums.org/showpost.php?p=3504186&postcount=1)

If the "easy" way doesn't work, I am more than happy to walk you through the "hard" way.

Regards
Iain

---

### Post by Magick93 on 2009-07-01
Hi Iain

Thanks for the positive reply.

I do have my card working using OSS, however midi is not working and I do need this as my goal is to make 'music' (in quotes as some people may not consider my noice to be music). 

So I must using ALSA, though I do not know for sure if it will work with midi.

The guide that you link to says "Note: if you never compiled a kernel before, then maybe this howto is not suited for you. " This puts me off some what as I am a novice, plug and play (plug and pray) kinda guy.

I probably should try recompiling the kernel (whatever that means) but I just need to collect my mind. I'm used to windows, and almost every evening after work for the past month trying to get my super home music studio working - and havent produced any sounds (I'm sure my neighbours dont mind). Also, I dont want to screw up the working sound that I do currently have - it took long enough to get flash and audio to work.

But if youre willing to walking me thru the daunting process - then I will give it a go!

---

### Post by ibuclaw on 2009-07-01
OK ... just before I go into anything drastic, can I ask a few things.

[LIST=1]
[*]Do you have **freepats** installed?
[*]Do you have **timidity** installed?
[/LIST]

Regards
Iain

---

### Post by Magick93 on 2009-07-01
Drastic - yes I get the feeling I'm heading that way.

Yes I have both of those installed.

---

### Post by ibuclaw on 2009-07-01
> **Magick93 said:**
> Drastic - yes I get the feeling I'm heading that way.

Haha
> 
Yes I have both of those installed.

And what applications are you using/wanting to have MIDI setup in?

---

### Post by Magick93 on 2009-07-01
Fruityloops and various VST plugins.

I had Fruityloops working using the onboard soundcard (with midi) but I found I had to disable this card if I was to use the X-fi card.

---

### Post by ibuclaw on 2009-07-01
> **Magick93 said:**
> Fruityloops and various VST plugins.

I had Fruityloops working using the onboard soundcard (with midi) but I found I had to disable this card if I was to use the X-fi card.
Ah, that would pose some issues.

Firstly, it may not Linux or your soundcard that may be at fault, but WINE itself.
Having a quick look at the [AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4304"), FL Studio 6.0 seems to be better working version, and is confirmed as "Platinum" whilst running under "WINE 1.1.15". Which is a development version, and isn't downloadable via the Ubuntu repositories. But you can get via [WINE's own hosted server.]("http://www.winehq.org/download/deb")

Secondly, I do not know how good such software via WINE is at handling music/audio. If they do work fine, I wouldn't expect them to run well at low latencies.

Have you tried any Linux native alternative software? A good example is **lmms** (Linux MultiMedia Studio), which has VST support too.

```
sudo apt-get install lmms lmms-vst
```

Regards
Iain

---

### Post by Magick93 on 2009-07-01
The problem is OSS - it doesnt support x-fi and midi. 

using AlSA and my onboard soundcard with midi - and WINE - it was working.

Fruityloops is working now - with audio only - with the X-fi card.

So, my next step is to see if I can get the x-fi to work with ALSA and hopefully the midi will work too. 

If not, its back to windows - and I dont want to have to do that.

But seeing as I had both audio and midi working with the onboard soundcard I think there is a good chance it can work with the X-Fi

---

### Post by sgx on 2009-07-02
> **Magick93 said:**
> The problem is OSS - it doesnt support x-fi and midi. 

using AlSA and my onboard soundcard with midi - and WINE - it was working.

Fruityloops is working now - with audio only - with the X-fi card.

So, my next step is to see if I can get the x-fi to work with ALSA and hopefully the midi will work too. 

If not, its back to windows - and I dont want to have to do that.

But seeing as I had both audio and midi working with the onboard soundcard I think there is a good chance it can work with the X-Fi
I would hunt down an older used maudio 24/96 pci card, full linux support, great sound, real midi i/o. I have read where new ones no longer work out of the box.

In the meantime, do the command  lsmod  and compare its output to this,
keeping a lookout for snd_seq, and related sound modules. the command

modprobe snd_seq

 can be used to load it if it's not there, mpu401 things are midi core items. (the ice1712 is just maudio stuff) Items in the left column are used by the ones on the right side, the number between tells how many modules rely on a given module. (snd, last on the list, has 21 other items that rely on it)

sound-related output from the lsmod  command:
Note: the copy/paste formatting is not presented correctly in this forum, lacking the spaces you will see in your output, but the info is there.)

snd_pcm_oss            36800  0
snd_mixer_oss          14048  1 snd_pcm_oss
snd_ice1712            57892  5
snd_ice17xx_ak4xxx      3616  1 snd_ice1712
snd_ak4xxx_adda         8320  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              8032  1 snd_ice1712
snd_ac97_codec         97892  1 snd_ice1712
snd_pcm                70660  5 snd_pcm_oss,snd_ice1712,snd_ac97_codec
snd_timer              20168  2 snd_seq,snd_pcm
snd_page_alloc          8456  1 snd_pcm
ac97_bus                1824  1 snd_ac97_codec
snd_i2c                 5184  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         7040  1 snd_ice1712
snd_rawmidi            20544  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          7212  5 snd_seq_midi,snd_seq_dummy,snd_seq_oss,snd_seq,s
nd_rawmidi
snd                    51812  21 snd_seq_oss,snd_seq,snd_pcm_oss,snd_mixer_oss,s
nd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm,snd_timer,snd_i2c,s
nd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               7072  1 snd

Cheers

---

### Post by Magick93 on 2009-07-03
Hi

Thanks for the help. I am reluctant to purchase new hardware - but I am considering it.

The output from that command is:
Module                  Size  Used by
isofs                  39844  0 
udf                    87716  1 
crc_itu_t              10112  1 udf
xt_limit               10116  8 
xt_tcpudp              11008  10 
ipt_LOG                13700  8 
ipt_MASQUERADE         10752  0 
xt_DSCP                11264  0 
ipt_REJECT             11136  1 
nf_conntrack_irc       13220  0 
nf_conntrack_ftp       15652  0 
xt_state               10112  6 
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
oss_usb               117132  3 
oss_sbxfi              37104  9 
oss_hdaudio           143076  3 
osscore               561844  3 oss_usb,oss_sbxfi,oss_hdaudio
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
iptable_nat            13700  0 
nf_nat                 25876  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      21388  9 iptable_nat,nf_nat
nf_conntrack           72008  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
iptable_mangle         10880  0 
iTCO_wdt               19108  0 
iptable_filter         10752  1 
iTCO_vendor_support    11652  1 iTCO_wdt
ip_tables              19472  3 iptable_nat,iptable_mangle,iptable_filter
ppdev                  15620  0 
x_tables               23044  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
psmouse                61972  0 
parport_pc             40100  1 
intel_agp              34108  0 
snd_page_alloc         17032  0 
serio_raw              13316  0 
pcspkr                 10496  0 
parport                42220  3 lp,ppdev,parport_pc
usbhid                 42336  0 
nvidia               7233756  36 
agpgart                42696  2 intel_agp,nvidia
usb_storage            99520  0 
floppy                 64324  0 
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


I dont see the modprobe snd_seq anywhere. What does it do, and how can I install it?

---

### Post by sgx on 2009-07-03
Hi, modprobe is a command to load a kernel module.

After looking at your output, I think your root user should first use the ubuntu sound-card configuration utility, if you have done that, I would open synaptic, and install/update everything with alsa, libalsa, libalsa2 in the title, inluding (alsa-oss things) then, have the root user run the alsaconf command, which will run a little gui, and ask you which sound device to configure for alsa.

Then run the lsmod command again, and compare the output. Save the current output in a textfile for reference. If there is no snd_seq in the output, run the command

modprobe snd_seq

and test your setup. The command:

man modprobe

will give you basic info on using modprobe.
I forgot if you disabled the onboard sound in the bios, but that will help. 

Cheers

---

### Post by Magick93 on 2009-07-04
Hi

Thanks sqx

I installed/reinstalled as you suggested, and now I get this:

anton@anton-desktop:~$ modprobe snd_seq
FATAL: Module snd_seq not found.
FATAL: Error running install command for snd_seq


And yes I have disabled the onboard soundcard in the bios.

---

### Post by sgx on 2009-07-04
> **Magick93 said:**
> Hi

Thanks sqx

I installed/reinstalled as you suggested, and now I get this:

anton@anton-desktop:~$ modprobe snd_seq
FATAL: Module snd_seq not found.
FATAL: Error running install command for snd_seq


And yes I have disabled the onboard soundcard in the bios.

[https://help.ubuntu.com/community/alsa-oss](https://help.ubuntu.com/community/alsa-oss)

this is the help-page for the app that unites oss and alsa. I always install this. If you install this, then have root run the alsaconf 
utility, then run the lsmod command and look for snd_seq and related modules.
If its not there, run modprobe snd_seq  yet again, and if there is still the same error, I would install a different and standard kernel, because this is a pretty common thing to have in a basic sound setup.
Cheers

---

### Post by neu2buntu on 2009-07-06
some things to try
(1) run the modprobe snd_seq as sudo modprobe snd_seq
(2)install aconnectgui to see if it can connect your midi through alsa
(3)try pulseaudio in your >system>preferences>sound and choose your soundcard as "device:"
(4)install qjackctl and use it to link your programs  (also install patchage)
(5)install asoundconf-gtk (this is gui to choose default soundcard)
(6)check this post for a solution [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
(7) upgrade alsa to latest version (can be found in above post)
i have ordered an usb-soundcard of ebay and hopefully it will be plug and play ...

---

### Post by rotten777 on 2009-07-07
You should pick up a USB midi adapter and save yourself the hassle. They're supported better.

---

### Post by Magick93 on 2009-07-08
OK it seems that MIDI is not going to to work with the X-Fi soundcard.

So I have two options - ditch linux and return back to windows. I dont want to have to do this. But it is an option. Or look at purchasing another soundcard.

Can anyone recommend a good highend soundcard - for making music - that will run on Linux?

---

### Post by sgx on 2009-07-08
I have the maudio 24/96, works great, no hassles, has midi, digital and analog i/o, 

revision B 2003 chip labeled: VT1712 0420CD 2HC0409583

(I should get spares off ebay!)

and maudio delta 44 should work out-of-the-box, not sure if it has midi ports. Try to get used ones that are older revisions, from people who are upgrading. I have read the newest ones no longer work, but
can't prove it. Several soundcards using a similar envy24 chip also work. 
Terratec Sixfire Audiotrak MAYA 1010, some Philips and Mad Dog brand models
Cheers

---

