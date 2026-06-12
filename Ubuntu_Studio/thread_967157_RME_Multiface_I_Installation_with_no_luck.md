---
title: "RME Multiface I Installation with no luck"
date: 2008-11-01
forum: Ubuntu Studio
---

### Post by wilowilo on 2008-11-01
Hi,

I have been searching all the threads about getting my Soundcard to work
with Ubuntu studio 8.04 on my laptop as well as on my PC with a pcmcia adapter. It did work like a charm under XP. 
I don't need the latest new gear if what I have is still working fine.

I've tried every advice given on any English, French, Italian and German site as well as RME's official site, but so far with no luck.
Maybe the only advantage is that I'm a bit past a newbie by now after 7 days of perseverance!

The card does get recognised (I can send the details from terminal later on) but the box still gives an error message. Also I might have missed some details that are obvious once you understand them.

Anybody willing to give an A-Z explanation/installation guide?

Thanx,

---

### Post by ttoine on 2008-11-01
Hey,

First of all, install alsa-firmware and alsa-tools-gui packages.

Just go in the main menu editor, and add a new shortcut called "HDSPLoader", command "hdsploader". Then run it, it will load the external box. Then run HDSPConf to set up the frequency, etc... and HDSPMixer to activate sound levels.

You will have sound, and you will be able to use it with Jack. Enjoy.

Toine

PS : I own a Multiface II and it sounds great with Linux.

---

### Post by wilowilo on 2008-11-02
Thanx ttoine for your help, but it doesn't work for me (see result in green)! By the way, I'm from Albertville, but let's stick to english!
So far I've tried everything on the following links:

[http://ubuntuforums.org/showthread.php?t=759878](http://ubuntuforums.org/showthread.php?t=759878)
[http://www.linuxmao.org/tikiwiki/tiki-view_forum_thread.php?comments_parentId=2499&topics_threshold=0&topics_offset=1&topics_sort_mode=commentDate_desc&topics_find=&forumId=2](http://www.linuxmao.org/tikiwiki/tiki-view_forum_thread.php?comments_parentId=2499&topics_threshold=0&topics_offset=1&topics_sort_mode=commentDate_desc&topics_find=&forumId=2)
[http://www.rme-audio.de/forum/viewtopic.php?id=1058](http://www.rme-audio.de/forum/viewtopic.php?id=1058)
[http://www.google.com/search?q=site%3Alalists.stanford.edu%2Flad+multiface](http://www.google.com/search?q=site%3Alalists.stanford.edu%2Flad+multiface)
[http://www.linuxjournal.com/article/7024](http://www.linuxjournal.com/article/7024)
[http://www.google.com/search?client=opera&rls=en&q=install+multiface+%2Bubuntu&sourceid=opera&ie=utf-8&oe=utf-8](http://www.google.com/search?client=opera&rls=en&q=install+multiface+%2Bubuntu&sourceid=opera&ie=utf-8&oe=utf-8)

Do I have to downgrade the Hammerfall's firmware?

My results:

willem@willem-laptop:~$ sudo lsmod |grep hdsp
snd_hdsp               52772  0 
snd_hwdep              10500  1 snd_hdsp
snd_pcm                78596  5 snd_hdsp,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_rawmidi            25760  3 snd_hdsp,snd_mpu401_uart,snd_seq_midi
snd                    56996  23 snd_rtctimer,snd_hdsp,snd_hwdep,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11400  4 snd_hdsp,snd_via82xx,snd_via82xx_modem,snd_pcm



Terminal data:
snd_hdsp               52772  0 
snd_hwdep              10500  1 snd_hdsp
snd_rawmidi            25760  3 snd_hdsp,snd_mpu401_uart,snd_seq_midi
snd_pcm                78596  5 snd_hdsp,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd                    56996  23 snd_rtctimer,snd_hdsp,snd_hwdep,snd_via82xx,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11400  4 snd_hdsp,snd_via82xx,snd_via82xx_modem,snd_pcm


willem@willem-laptop:~$ hdsploader
hdsploader - firmware loader for RME Hammerfall DSP cards
Looking for HDSP + Multiface or Digiface cards :
Card 0 : VIA 82C686A/B rev40 with Cx20468 at 0x1400, irq 10
Card 1 : VIA 82XX modem at 0x1800, irq 10
Card 2 : RME Hammerfall DSP at 0x24000000, irq 9
Upload firmware for card hw:2
Hwdep ioctl error on card hw:2 : Input/output error.

2nd startup with box connected:

[COLOR="DarkGreen"]
hdsploader - firmware loader for RME Hammerfall DSP cards
Looking for HDSP + Multiface or Digiface cards :
Card 0 : VIA 82C686A/B rev40 with Cx20468 at 0x1400, irq 10
Card 1 : VIA 82XX modem at 0x1800, irq 10
Card 2 : RME Hammerfall DSP at 0x24000000, irq 9
Upload firmware for card hw:2
Unable to open file '/lib/firmware/hdsploader/multiface_firmware_rev11.bin' for reading
[/COLOR]



willem@willem-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
usb_storage            73664  1 
libusual               19108  1 usb_storage
snd_rtctimer            4640  1 
ipv6                  267780  8 
binfmt_misc            12808  1 
savage                 33920  2 
drm                    82452  3 savage
af_packet              23812  4 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
vboxdrv                68504  0 
ppdev                  10372  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
aes_i586               33536  0 
dm_crypt               15364  0 
dm_mod                 62660  1 dm_crypt
lp                     12324  0 
joydev                 13120  0 
snd_hdsp               52772  0 
snd_hwdep              10500  1 snd_hdsp
pcmcia                 40876  0 
video                  19856  0 
output                  4736  1 video
snd_via82xx            29464  3 
gameport               16008  1 snd_via82xx
ndiswrapper           192920  0 
snd_via82xx_modem      16264  0 
snd_ac97_codec        101028  2 snd_via82xx,snd_via82xx_modem
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  5 snd_hdsp,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_mpu401_uart         9728  1 snd_via82xx
snd_seq_dummy           4868  0 
evdev                  13056  6 
serio_raw               7940  0 
psmouse                40336  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  3 snd_hdsp,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
battery                14212  0 
via_ircc               27796  0 
ac                      6916  0 
button                  9232  0 
snd_seq                54224  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
irda                  203068  1 via_ircc
vt8231                 17164  0 
crc_ccitt               3072  1 irda
yenta_socket           27276  2 
snd                    56996  23 snd_rtctimer,snd_hdsp,snd_hwdep,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0 
i2c_viapro              9876  0 
via_agp                11136  1 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         11400  4 snd_hdsp,snd_via82xx,snd_via82xx_modem,snd_pcm
i2c_core               24832  1 i2c_viapro
agpgart                34760  2 drm,via_agp
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
soundcore               8800  1 snd
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  5 
pata_acpi               8320  0 
ata_generic             8324  0 
floppy                 59588  0 
pata_via               13316  2 
uhci_hcd               27024  0 
libata                159344  3 pata_acpi,ata_generic,pata_via
via_rhine              26632  0 
mii                     6400  1 via_rhine
usbcore               146028  5 usb_storage,libusual,ndiswrapper,uhci_hcd
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

With hope for a life without Windows!,

W

---

### Post by wilowilo on 2008-11-27
Finally solved the problem!
I didn't know there was a alsa-firmware version specially made for
Ubuntu! That did the final job!
Still you need to get and install alsa-tools from the alsa website.
Activate with hdsploader
For newbies (more newbie than me ;-)  ) I strongly recommend [http://www.psychocats.net](http://www.psychocats.net), where you can find a to the point order of essential stuff to start out.

---

### Post by sem on 2009-02-10
Hi 

Could you please tell me the name of that special alsa-firmware loader for Ubuntu studio ?

Thanks in advantage  :KS

/Sem

---

