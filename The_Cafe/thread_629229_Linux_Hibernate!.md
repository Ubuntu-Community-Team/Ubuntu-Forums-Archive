---
title: "Linux Hibernate!"
date: 2007-12-02
forum: The Cafe
---

### Post by khurrum1990 on 2007-12-02
Does hibernate work for anyone? Why can't Linux developers solve this problem? Microsoft solved their ages back, even OS X running on top of freeBSD kernel can hiberate. What is Apple doing that we don't, I know OS X runs on fewer hardware, but there method of hibernate is different then ours and apparently it works.

---

### Post by tageiru on 2007-12-02
> **khurrum1990 said:**
> Does hibernate work for anyone?
Yes
> **khurrum1990 said:**
> Why can't Linux developers solve this problem?
[http://www.osnews.com/story.php/17689/Bill-Gates-on-Making-ACPI-Not-Work-with-Linux/](http://www.osnews.com/story.php/17689/Bill-Gates-on-Making-ACPI-Not-Work-with-Linux/)

Not the whole answer, but an interesting fact none the less.
> **khurrum1990 said:**
> even OS X running on top of freeBSD kernel

False

---

### Post by NovaAesa on 2007-12-02
Hibernate kind of works. When I turn on again, my internet doesn't work though which is a deal breaker for me.

I would have really liked to hibernate then boot into Windows (for when I feel the urge to do some serious gaming) then restart and unhibernate back into Ubuntu but alas it looks like I'm stuck with reboots.

---

### Post by x0as on 2007-12-02
Never worked for me, which is why I've kept xp my laptop.

---

### Post by aimran on 2007-12-02
IMO screw hibernate. Fast bootups ftw.

---

### Post by khurrum1990 on 2007-12-02
First of all I don't get what Bill Gates could have possibly done thats stops us from developing a method of hibernate that works. Second if Linux doesn't improve this one little thing then even though people may install Linux on desktops where hibernate doesn't matter, but on laptops people r only going to use Windows.

---

### Post by pelle.k on 2007-12-02
Hibernate works for me. I think you phrased it badly, since hibernate probably fails on less computer than it works on. Nevertheless, it's a pain in the *** when it doesn't!
As usual, it's the industry ACPI standards and specifications that is to blame, for the most part. Often, bad drivers can screw it up too, but many linux drivers are reverse engineered, because the specs aren't available to the kernel developers.

[edit]microsoft has the advantage of being *the* testbed for most manufacturers, and so hibernate and suspend often work as a result of that.[/edit]

---

### Post by khurrum1990 on 2007-12-02
Quote:
Originally Posted by khurrum1990:
"even OS X running on top of freeBSD kernel"
False

What is false about this? Is it that OS X does not run on top of freeBSD kernel or does OS X does have problems with sleep?

---

### Post by Mateo on 2007-12-02
It's a major problem, almost a deal breaker for laptops.

---

### Post by tageiru on 2007-12-02
> **khurrum1990 said:**
> Quote:
Originally Posted by khurrum1990:
"even OS X running on top of freeBSD kernel"
False

What is false about this? Is it that OS X does not run on top of freeBSD kernel or does OS X does have problems with sleep?

OS X uses the Darwin kernel, not the FreeBSD kernel. You probably confused the kernel with userland as OS X uses the FreeBSD userland.

As for how Microsoft affects Linux hibernation it seems like many implementations of ACPI doesn't follow the the public specification. Whether that is because of lazy manufacturers or fowl play is not clear, but the mail from Gates suggests the latter.

---

### Post by khurrum1990 on 2007-12-02
> **tageiru said:**
> OS X uses the Darwin kernel, not the freebsd kernel. It uses the freebsd userland however.

Yeah u were right I kept forgetting, but still OS X has no problems with sleep even on Intel Macs. What r they doing right? Linux has hibernate troubles on Intel Macs as well.

---

### Post by xeth_delta on 2007-12-02
> **khurrum1990 said:**
> First of all I don't get what Bill Gates could have possibly done thats stops us from developing a method of hibernate that works. Second if Linux doesn't improve this one little thing then even though people may install Linux on desktops where hibernate doesn't matter, but on laptops people r only going to use Windows.

This is of course my personal choice, but I would not use windows even if hibernate did not work on my laptop.

That being said, Hibernate and software suspend both work on my laptop. It is Core 2 Duo Macbook, second generation. I run Ubuntu Feisty Fawn with a Gutsy Kernel.

These problems, for instance hibetnation are solved as time goes on. The Feisty kernel did not allow me to suspend or hibernate. I recompiled a newer version and later just used the gutsy kernel, in both cases it worked.

Most of the times these problems are associated with several drivers / modules not supporting suspend/hibernation properly, and in many cases work-arounds are possible until a permanent fix is done.

A way to identify the affected module is to disable them and then try to suspend. If that doesn't work, then start without  the graphical interface and suspend from the comand line, eliminating one by one possible problematic modules. There can be some candidates such as modules for network / wireless cards, sound cards, modem.

It might help if we know what modules your system uses. Can you please post the specs of your machine? Please, also post, between code tags, the output of:

```
lsmod
lspci
lsusb
dmesg
cat /var/log/messages
```

Xeth

---

### Post by khurrum1990 on 2007-12-02
Even though I really wasn't asking for help, but hey why not?
I am on a Macbook right now the machine I am talking about is:
A Gigabyte motherboard Intel P4 2.7ghz
1.5gb of ram
realtek ac'97 sound card
lan
lg dvd-rw
80gb hard disk
XFX Geforce 6200 512 mb AGP
I am running kernel 2.6.22-12 on that machine I think and not the latest 2.6.22-14 cause on that nothing works and there has been a bug report.

lsmod:
Module                  Size  Used by
xt_limit                3584  8
ipt_LOG                 7552  8
ipt_MASQUERADE          4608  0
ipt_TOS                 3200  0
ipt_REJECT              5760  1
nf_conntrack_irc        8088  0
nf_conntrack_ftp       11136  0
xt_state                3456  6
xt_TCPMSS               5888  0
xt_tcpmss               3200  0
xt_tcpudp               4224  10
binfmt_misc            12936  1
rfcomm                 42136  4
l2cap                  26240  11 rfcomm
vboxdrv                60080  0
ppdev                  10244  0
pppoe                  15680  2
pppox                   4872  1 pppoe
speedstep_lib           6404  0
cpufreq_userspace       5280  0
cpufreq_powersave       2688  0
cpufreq_conservative     8072  0
cpufreq_ondemand        9612  0
cpufreq_stats           7232  0
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
video                  18060  0
sbs                    19592  0
container               5504  0
button                  8976  0
ac                      6148  0
dock                   10656  0
battery                11012  0
af_packet              24840  2
ppp_generic            29332  6 pppoe,pppox
slhc                    7552  1 ppp_generic
lp                     12580  0
snd_intel8x0           34972  1
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_mpu401              9640  0
gspca                 608336  0
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            33152  0
snd_mpu401_uart         9600  1 snd_mpu401
videodev               29312  1 gspca
v4l2_common            18432  1 videodev
snd_seq_midi            9600  0
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
analog                 13344  0
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
hci_usb                18332  2
gameport               16776  1 analog
bluetooth              57060  7 rfcomm,l2cap,hci_usb
v4l1_compat            15364  1 videodev
parport_pc             37412  1
parport                37448  3 ppdev,lp,parport_pc
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               6221648  36
serio_raw               8068  0
pcspkr                  4224  0
psmouse                39952  0
agpgart                35016  1 nvidia
snd                    54660  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401,snd_pcm,snd_seq_oss,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
i2c_sis96x              6404  0
i2c_core               26112  2 nvidia,i2c_sis96x
shpchp                 34580  0
pci_hotplug            32704  1 shpchp
ipv6                  274020  10
evdev                  11136  4
iptable_nat             8708  0
nf_nat                 20140  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19724  8 iptable_nat
nf_conntrack           65288  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               6936  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_mangle          3840  0
iptable_filter          3968  1
ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16260  11 xt_limit,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,xt_TCPMSS,xt_tcpmss,xt_tcpudp,iptable_nat,ip_tables
ext3                  133768  2
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
8139too                27776  0
sg                     36764  0
sr_mod                 17828  0
cdrom                  37536  1 sr_mod
sd_mod                 30336  4
floppy                 60004  0
8139cp                 25088  0
mii                     6528  2 8139too,8139cp
ehci_hcd               36108  0
ohci_hcd               22916  0
usbcore               138248  5 gspca,hci_usb,ehci_hcd,ohci_hcd
pata_sis               15236  3
ata_generic             8452  0
libata                124528  2 pata_sis,ata_generic
scsi_mod              147084  4 sg,sr_mod,sd_mod,libata
thermal                14344  0
processor              31944  1 thermal
fan                     5764  0
fuse                   47124  1
apparmor               40600  0
commoncap               8320  1 apparmor

lspci:
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

lsusb:
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 093a:2471 Pixart Imaging, Inc.
Bus 001 Device 001: ID 0000:0000

Dmesg is messed up cause that computer just started firestarter.

---

### Post by xeth_delta on 2007-12-02
Ok, I will have more time to look at it tomorrow evening, but I guess it might be possible to get it working after some tinkering.

Of course, the usual recommendation of making a back-up of important information, just in case.

As a starting point you could try starting without the graphical interface, in the most basic state possible. There should be less modules loaded, which you can check with **lsmod**.

Try to suspend from the command line:
```
sudo echo 3 > /proc/acpi/sleep
```
or
```
sudo echo -n mem > /sys/power/state
```

Try to wake up (keys, bower button, etc), if it does not you can start unload modules with **rmmod**, for instance let's say you want to unload **nvidia**

```
sudo rmmod nvidia
```

Try again. This might be laborious, but in the end, you could end up identifying the problematic module.

Have a look at this thread, might be useful, even though it concerns a thinkpad: [http://ubuntuforums.org/showthread.php?t=200082&highlight=echo+%2Fproc%2F+suspend]("http://ubuntuforums.org/showthread.php?t=200082&highlight=echo+%2Fproc%2F+suspend")

If you want to try suspend to disk, too, I think this is what you have to do:
```
echo 4 > /proc/acpi/sleep
```
[http://ubuntuforums.org/showthread.php?t=65457&highlight=echo+%2Fproc%2F+suspend]("http://ubuntuforums.org/showthread.php?t=65457&highlight=echo+%2Fproc%2F+suspend")

After a failed suspend - wake up, information should be written to /var/log/messages. Can you please post the output, but please, do use the code tags ( # button in the posting page ), it makes it easier to read.

Xeth

---

### Post by khurrum1990 on 2007-12-02
Hey wow thanks, I will try this as soon as my family leaves the computer alone.

---

### Post by Sporkman on 2007-12-02
> **tageiru said:**
> fowl play

Don't duck the issue.

---

### Post by 23meg on 2007-12-02
[QUOTE=khurrum1990]Does hibernate work for anyone? Why can't Linux developers solve this problem?[/QUOTE]

ACPI, lack of drivers, lack of specifications.

[QUOTE=khurrum1990]What is Apple doing that we don't, [/QUOTE]

Manufacturing their own hardware that they can and do test extensively.

---

### Post by Palmyra on 2007-12-02
Nope, doesn't work for me.  Neither suspend or hibernate work for me, but I recall a time they did (probably with Dapper).  But then again, Oceana was, at that time, still at war with Eurasia.  I am not quite sure if it is now at war with Eurasia or Eustasia.

---

### Post by thisllub on 2007-12-02
I modify GRUB to add ACPI=off
Then my laptop boots.
After it boots I find the hald storage polling process and kill it.
That stops the 20 second hang every few minutes.

---

### Post by beercz on 2007-12-02
I have an HP Compaq nx7400 laptop running gutsy.

I have got hibernate to work well (very useful for me).

I have not got suspend to work though (suspend not that useful for me so I haven't really bothered)

When I was running feisty on the same machine I had both suspend and hibernate working, using uswsp (or whatever it was - can't quite remember) - which I think has been removed in gutsy.

Really could do with better power management though.

---

### Post by ssam on 2007-12-02
when linux devs have good access to hardware info they can do amazing things. look up the power management systems on the OLPC

---

### Post by xeth_delta on 2007-12-02
> **ssam said:**
> when linux devs have good access to hardware info they can do amazing things. look up the power management systems on the OLPC

Really good point ssam

---

