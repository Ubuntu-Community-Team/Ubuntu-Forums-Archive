---
title: "Laptop Stuck In Tablet Mode [Keyboard Disabled]"
date: 2017-11-05
forum: Ubuntu/Debian BASED
---

### Post by mark.linux on 2017-11-05
The orientation sensor has malfunctioned on my laptop and is wrongly pointing out to be a tablet.
The keyboard thus has been disabled and isn't working. Also the volume button functionality is inverted as it is in tablet mode.
Same issue in windows was resolved by disabling intel integrated sensor driver.
Keyboard works just fine in grub menu. Gets disabled at lockscreen and further.
my lsmod shows this :
```
root@kaliScanner:~# lsmod
Module                  Size  Used by
intel_ishtp_hid        20480  0
cpuid                  16384  0
fuse                   98304  5
ctr                    16384  2
ccm                    20480  3
btusb                  45056  0
btrtl                  16384  1 btusb
binfmt_misc            20480  1
nls_ascii              16384  1
nls_cp437              20480  1
snd_hda_codec_hdmi     49152  1
vfat                   20480  1
fat                    65536  1 vfat
efi_pstore             16384  0
arc4                   16384  2
snd_hda_codec_conexant    24576  1
snd_hda_codec_generic    69632  1 snd_hda_codec_conexant
hp_wmi                 16384  0
snd_soc_skl            73728  0
snd_soc_skl_ipc        49152  1 snd_soc_skl
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        32768  1 snd_soc_skl_ipc
snd_hda_ext_core       24576  1 snd_soc_skl
i2c_designware_platform    16384  0
i2c_designware_core    20480  1 i2c_designware_platform
snd_soc_sst_match      16384  1 snd_soc_skl
snd_soc_core          217088  1 snd_soc_skl
snd_compress           20480  1 snd_soc_core
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
intel_rapl             20480  0
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
x86_pkg_temp_thermal    16384  0
videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
intel_powerclamp       16384  0
coretemp               16384  0
media                  40960  2 uvcvideo,videodev
hid_logitech_hidpp     32768  0
iwlmvm                253952  0
kvm_intel             196608  0
kvm                   577536  1 kvm_intel
mac80211              659456  1 iwlmvm
snd_hda_intel          40960  6
irqbypass              16384  1 kvm
rtsx_pci_ms            20480  0
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_codec_generic
snd_hda_core           77824  7 snd_hda_intel,snd_hda_codec_conexant,snd_hda_codec,snd_hda_ext_core,snd_soc_skl,snd_hda_codec_hdmi,snd_hda_codec_generic
intel_cstate           16384  0
intel_uncore          118784  0
snd_hwdep              16384  1 snd_hda_codec
intel_rapl_perf        16384  0
memstick               16384  1 rtsx_pci_ms
iwlwifi               163840  1 iwlmvm
joydev                 20480  0
evdev                  24576  30
efivars                20480  1 efi_pstore
serio_raw              16384  0
pcspkr                 16384  0
i915                 1269760  19
intel_th_gth           16384  0
snd_pcm               102400  7 snd_hda_intel,snd_hda_codec,snd_hda_ext_core,snd_hda_core,snd_soc_skl,snd_hda_codec_hdmi,snd_soc_core
cfg80211              593920  3 iwlmvm,iwlwifi,mac80211
intel_th_pci           16384  0
snd_timer              32768  1 snd_pcm
drm_kms_helper        151552  1 i915
intel_th               16384  2 intel_th_pci,intel_th_gth
iTCO_wdt               16384  0
snd                    77824  22 snd_compress,snd_hda_intel,snd_hwdep,snd_hda_codec_conexant,snd_hda_codec,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_soc_core,snd_pcm
iTCO_vendor_support    16384  1 iTCO_wdt
soundcore              16384  1 snd
sg                     32768  0
shpchp                 36864  0
drm                   348160  7 i915,drm_kms_helper
idma64                 20480  0
i2c_algo_bit           16384  1 i915
mei_me                 40960  0
mei                    94208  1 mei_me
processor_thermal_device    16384  0
intel_pch_thermal      16384  0
intel_lpss_pci         16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
ucsi                   16384  0
wmi                    16384  1 hp_wmi
ac                     16384  0
hci_uart               98304  0
btbcm                  16384  2 hci_uart,btusb
acpi_als               16384  0
btqca                  16384  1 hci_uart
btintel                16384  2 hci_uart,btusb
kfifo_buf              16384  1 acpi_als
battery                20480  0
dptf_power             16384  0
soc_button_array       16384  0
industrialio           65536  2 acpi_als,kfifo_buf
intel_vbtn             16384  0
int3403_thermal        16384  0
bluetooth             540672  7 btrtl,hci_uart,btintel,btqca,btbcm,btusb
ecdh_generic           24576  1 bluetooth
int3400_thermal        16384  0
rfkill                 24576  7 bluetooth,hp_wmi,cfg80211
acpi_thermal_rel       16384  1 int3400_thermal
int3402_thermal        16384  0
int3406_thermal        16384  0
intel_lpss_acpi        16384  0
int340x_thermal_zone    16384  3 int3402_thermal,int3403_thermal,processor_thermal_device
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
tpm_crb                16384  0
video                  40960  2 int3406_thermal,i915
intel_hid              16384  0
sparse_keymap          16384  3 intel_hid,intel_vbtn,hp_wmi
hp_wireless            16384  0
button                 16384  1 i915
acpi_pad               24576  0
efivarfs               16384  1
ip_tables              24576  0
x_tables               36864  1 ip_tables
autofs4                40960  2
hid_logitech_dj        20480  0
ext4                  593920  1
crc16                  16384  2 bluetooth,ext4
jbd2                  102400  1 ext4
crc32c_generic         16384  0
fscrypto               28672  1 ext4
ecb                    16384  0
usbhid                 49152  0
mbcache                16384  1 ext4
sd_mod                 49152  3
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
crc32c_intel           24576  2
ghash_clmulni_intel    16384  0
pcbc                   16384  0
rtsx_pci_sdmmc         24576  0
mmc_core              143360  1 rtsx_pci_sdmmc
aesni_intel           167936  2
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
psmouse               143360  0
i2c_i801               24576  0
rtsx_pci               57344  2 rtsx_pci_sdmmc,rtsx_pci_ms
mfd_core               16384  2 rtsx_pci,intel_lpss
ahci                   36864  2
libahci                32768  1 ahci
xhci_pci               16384  0
libata                233472  2 ahci,libahci
xhci_hcd              208896  1 xhci_pci
scsi_mod              212992  3 sd_mod,libata,sg
usbcore               245760  5 uvcvideo,usbhid,xhci_pci,btusb,xhci_hcd
intel_ish_ipc          20480  0
usb_common             16384  1 usbcore
intel_ishtp            40960  2 intel_ishtp_hid,intel_ish_ipc
thermal                20480  0
i2c_hid                20480  0
hid                   118784  5 i2c_hid,usbhid,hid_logitech_dj,intel_ishtp_hid,hid_logitech_hidpp
fan                    16384  0
```

I tried blacklisting drivers 
```
blacklist nfc
blacklist pn533
blacklist hid_sensor_hub
blacklist hid_sensor_rotation
```

None of the solutions have worked. 
Any usb keyboard works just fine.
Any help is greately appreciated.

---

### Post by #&amp;thj^% on 2017-11-05
Please use Code tags and not Quote tags for long outputs.
Thanks!
What version are you using?
```
lsb_release -a
```

---

### Post by mark.linux on 2017-11-05
Sure, I was debating which one to use. Until I ended up with the first I saw lol.
```
:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Kali
Description:    Kali GNU/Linux Rolling
Release:    kali-rolling
Codename:    kali-rolling


```

---

### Post by #&amp;thj^% on 2017-11-05
> **mark.linux said:**
> Sure, I was debating which one to use. Until I ended up with the first I saw lol.
```
:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Kali
Description:    Kali GNU/Linux Rolling
Release:    kali-rolling
Codename:    kali-rolling


```
Yikes my Kali usage is a bit rusty, I defer to some one more experienced in this matter. :D

---

### Post by howefield on 2017-11-05
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by mark.linux on 2017-11-05
> **howefield said:**
> Thread moved to the "*Ubuntu/Debian BASED*" forum.

Hiya, I am using a dual boot with ubuntu and kali linux too. 
Same problem both places. Thats why I posted the thread there.
I can switch the os if you like. 
Those threads have awfully slow response rates.

> **1fallen said:**
> Yikes my Kali usage is a bit rusty, I defer to some one more experienced in this matter. :D

I am dual booting and selecting whichever gets fixed first. I can switch over to ubuntu if you wish.
Currently I have 2 os installed after switching over from windows.
Kali + Ubuntu

---

### Post by #&amp;thj^% on 2017-11-05
> **mark.linux said:**
> I am dual booting and selecting whichever gets fixed first. I can switch over to ubuntu if you wish.
Currently I have 2 os installed after switching over from windows.
Kali + Ubuntu

Is this a Lenovo?
And dose this show any output from the terminal:
```
acpi_listen
```
If so paste it back here.

---

### Post by mark.linux on 2017-11-05
> **1fallen said:**
> Is this a Lenovo?
And dose this show any output from the terminal:
```
acpi_listen
```
If so paste it back here.

Ahan, its giving a command not found error.
It's an hp envy x360.
It worked fine on ubuntu before the motherboard fried, After fixing it, the sensor is faulty and all distros have same issue,so I have to use windows occasionally xD

---

### Post by #&amp;thj^% on 2017-11-05
You never answered if it was a Lenovo.

---

### Post by mark.linux on 2017-11-05
Yup, I did.
Also I tried the fix for lenovo yoga with screen rotate, didn't work. :(

---

### Post by #&amp;thj^% on 2017-11-05
It did not show until just now.:?:
So you have tried this then ?:
On Ubuntu run:

```
xinput disable "$(xinput -list | awk -F'[=\t]' '/ELAN/{print $3}')"
```
Might work for Kali too but I don't know for sure.

---

### Post by #&amp;thj^% on 2017-11-05
> **1fallen said:**
> It did not show until just now.:?:
So you have tried this then ?:
On Ubuntu run:

```
xinput disable "$(xinput -list | awk -F'[=\t]' '/ELAN/{print $3}')"
```
Might work for Kali too but I don't know for sure.
EDIT: I just remembered a friend had told me to tilt the whole laptop towards me slightly, and voila! So far it has worked every time.
HP's have become a living nightmare for Linux Trouble Shooting. (Just My 2 cents worth :))

---

### Post by mark.linux on 2017-11-05
> **1fallen said:**
> EDIT: I just remembered a friend had told me to tilt the whole laptop towards me slightly, and voila! So far it has worked every time.
HP's have become a living nightmare for Linux Trouble Shooting. (Just My 2 cents worth :))

Absolutely. But the very fact that something like windows has a fix for it and linux doesn't yet is kinda surprising!
Disabling a sensor and forcing desktop mode should get the job done afterall!
```
# xinput disable "$(xinput -list | awk -F'[=\t]' '/ELAN/{print $3}')"
unable to find device 


```
```
# xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech K230                               id=9    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; HP Wide Vision HD                           id=10    [slave  keyboard (3)]
    &#8627; Intel Virtual Button driver                 id=11    [slave  keyboard (3)]
    &#8627; Intel Virtual Button driver                 id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=15    [slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                         id=16    [slave  keyboard (3)]
    &#8627; Logitech K230    

```

---

### Post by #&amp;thj^% on 2017-11-05
> **mark.linux said:**
> Absolutely. But the very fact that something like windows has a fix for it and linux doesn't yet is kinda surprising!
Disabling a sensor and forcing desktop mode should get the job done afterall!
```
# xinput disable "$(xinput -list | awk -F'[=\t]' '/ELAN/{print $3}')"
unable to find device 


```
```
# xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech K230                               id=9    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; HP Wide Vision HD                           id=10    [slave  keyboard (3)]
    &#8627; Intel Virtual Button driver                 id=11    [slave  keyboard (3)]
    &#8627; Intel Virtual Button driver                 id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=15    [slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                         id=16    [slave  keyboard (3)]
    &#8627; Logitech K230    

```

I feel your pain here...but lets be clear though, All Hardware/Firmware for these Machines are written for Microsoft only....
So in other words the kernel teams have to resort to Reverse engineering, also called back engineering for these Types of Machines.
Linux is never on their mind or goal. If you were to go to their forums you would either get ignored or a hard suggestion to Use Windows.
Don't kill the Messenger I just Donate my time to try and help when I can.
I'll see if I can fix that code for the right Hardware...But probably not tonight.

---

### Post by mark.linux on 2017-11-05
> **1fallen said:**
> I feel your pain here...but lets be clear though, All Hardware/Firmware for these Machines are written for Microsoft only....
So in other words the kernel teams have to resort to Reverse engineering, also called back engineering for these Types of Machines.
Linux is never on their mind or goal. If you were to go to their forums you would either get ignored or a hard suggestion to Use Windows.
Don't kill the Messenger I just Donate my time to try and help when I can.
I'll see if I can fix that code for the right Hardware...But probably not tonight.
Yes absolutely, so deleting them must be easier on Linux right? The software on windows causes the problem and deleting it worked. 
Thank you for your help sir!

---

### Post by #&amp;thj^% on 2017-11-06
No luck with any hacks I've been trying.
To many side effects>>>These Newer HP's are not worth the trouble they now present for Linux!! :(
I'm not a windows user at all so I don't know how well they work with Microsoft OS's, (8 & 8.1 * 10)

---

### Post by Majkee(SK) on 2018-08-31
Hi All,

this is my first ask for help after 8 years with Ubuntu.

Im fighting more than 5 hours with keyboard disable similar to this thread.
On my Lenovo Yoga S1 (type: 20C0) keyboard disable on normal position. I have to rotate notebook to me more then 10° and keyboard works back. Same the keybard backlight.

 Im using Kubuntu 18.04 with kernel 4.15. 
I used Kubuntu 14.04 to 17.04  on this notebook without any issue. Problem appears with 17.10 I think. I was able to fix  it on old installation, but cannot remember what was a solution (my  bad). Now, NTB is reinstalled for my wife and I cannot fix it again :( 





acpi_listen (when I rotate with notebook) gives:

> video/tabletmode TBLT 0000008A 00000001 K
video/tabletmode TBLT 0000008A 00000000 K

xinput - list

> 
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB OPTICAL MOUSE                         id=9    [slave  pointer  (2)]
&#9116;   &#8627; ELAN Touchscreen                          id=10   [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 EC Pen stylus                 id=12   [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=14   [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                     id=15   [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 EC Pen eraser                 id=17   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera: Integrated C           id=11   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=13   [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                    id=16   [slave  keyboard (3)]


I laready tried:


blacklist hid_sensor_*
blacklist hid_sensor_hub
blacklist thinkpad_acpi

(after blacklist acpi_listen shows nothing, but keyboard disable in same way as before)

Also I tried some actions with xinput to enable keyboard, when tablet mode enable but this not work at all.

I I founded similar problem due to new kernel:
[https://forums.linuxmint.com/viewtopic.php?t=261844](https://forums.linuxmint.com/viewtopic.php?t=261844)

or problem with libinput starting from 1.9.x
[https://bugs.freedesktop.org/show_bug.cgi?id=103561](https://bugs.freedesktop.org/show_bug.cgi?id=103561)

Unfortunatelly, Im unable to downgrade libinput due to dependecies. It is possible to use old packages (from 16.10) with 18.04?
How achieve the downgrade?

Best solution should be disabling tablet mode at all in my kernel, but I cannot get this working with blacklist.

Thank you for any help from community!

Regards,

Majkee

---

