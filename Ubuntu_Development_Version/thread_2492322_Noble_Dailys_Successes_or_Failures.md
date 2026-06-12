---
title: "Noble Dailys: Successes or Failures?"
date: 2023-11-07
forum: Ubuntu Development Version
---

### Post by MAFoElffen on 2023-11-07
I have been having successful installs from Noble Server amd64 iso's...

But, so far, not from the other dailies yet:
Ubuntu Desktop 24.04 amd64, [https://bugs.launchpad.net/subiquity/+bug/2042893](https://bugs.launchpad.net/subiquity/+bug/2042893)
Budgie Desktop 24.04 amd64, [https://bugs.launchpad.net/subiquity/+bug/2042893](https://bugs.launchpad.net/subiquity/+bug/2042893)
Ubuntu Server 24.04 S390X, [https://bugs.launchpad.net/subiquity/+bug/2042883](https://bugs.launchpad.net/subiquity/+bug/2042883)

Has anyone had any luck on these or others yet? Like Lubuntu, Xubuntu, or other arches?

I admit, I haven't tried the arm64 daily yet...

EDIT: Also: There seems to be a problem I haven't reported yet on QEMU QXL and Noble Desktop, But i haven;t figured out whether that is on KVM or Noble yet,  One thing is that current KVM still uses Ubuntu 23.10 templates... QXL crashes Noble Xorg, but is fine if I set the VM's to VGA instead of QXL, so that makes my unsure what to file that against...

---

### Post by #&amp;thj^% on 2023-11-07
I'm down-loading this one now for a KVM: [https://cdimage.ubuntu.com/xubuntu/daily-minimal/20231107/](https://cdimage.ubuntu.com/xubuntu/daily-minimal/20231107/)
I'll post back

---

### Post by MAFoElffen on 2023-11-07
@1fallen --
From you signature --> You know what that looks like? LOL
> Debian [COLOR=#ff0000]Unstable FreeBSD[/COLOR] or [COLOR=#FF0000]Debian Unstable[/COLOR], FreeBSD
Please try it as VGA, so that QXL/Xorg crashing (until I figure out where to file that) is not a distraction for that...

---

### Post by #&amp;thj^% on 2023-11-07
> **MAFoElffen said:**
> @1fallen --
From you signature --> You know what that looks like? LOL

Please try it as VGA, so that QXL/Xorg crashing (until I figure out where to file that) is not a distraction for that...

Copy That..

---

### Post by MAFoElffen on 2023-11-07
I filled the KVM bug as this, because it is globally a Noble Bug, not just with the installer. It happens with all Noble: [https://bugs.launchpad.net/ubuntu/+source/spice-vdagent/+bug/2042979](https://bugs.launchpad.net/ubuntu/+source/spice-vdagent/+bug/2042979)

---

### Post by #&amp;thj^% on 2023-11-07
I'll add myself as well, see screenshots

---

### Post by Claus7 on 2023-11-07
Hello,

I haven't been able to install amd64 iso of ubuntu using vb. I do not remember having a pending cd image for ubuntu in the past though. I suppose that the OP tried to install desktop amd from pending iso and failed. I suppose that subiquity undergoes a great modification and revamping until is ready for a LTS release. I didn't even have the privilege for the installation to finish or report any bugs since it just froze. I will try again and let you know.

Regards!

---

### Post by Claus7 on 2023-11-07
Hello,

I downloaded the latest amd iso and added > 4GB of ram. The black screen which prompts for installation of ubuntu showed up. I selected it and proceeded with the full installation. Even though at some moment I was informed that I had to either wait or force quit the installation, after quitting, I enabled it anew. After some moments installation failed with the error: install failed crashed with CalledProcessError
edit: checked with the OP and found out that it is the same error, so mentioned it at launchpad as well

Regards!

---

### Post by MAFoElffen on 2023-11-07
Seems like all the Noble builds, except for the Server amd64, are stuck at this bug: [https://bugs.launchpad.net/subiquity/+bug/2042893](https://bugs.launchpad.net/subiquity/+bug/2042893), which was since yesterday.

Going to spin up a Noble server arm64, and see if it is good or not...

---

### Post by Irihapeti on 2023-11-07
I tried in QEMU/KVM with both QXL and VGA. Both crashed.

---

### Post by ajgreeny on 2023-11-08
Just tried a daily of Xubuntu Noble Desktop using KVM on my Xubuntu 22.04 host and got exactly the same problems as 1fallen at post #6.
I haven't had time yet to investigate further details of this though I used virtio video rather than QXL or VGA though I will try the other video settings when I have time and report back.

Bug for this filed at [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2043046](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2043046)

I have just tried again on another computer but still using KVM/QEMU.
However this time using VGA as the video but again the installer crashed with exactly the same errors configuring apt.

---

### Post by VMC on 2023-11-08
> **ajgreeny said:**
> Just tried a daily of Xubuntu Noble Desktop using KVM on my Xubuntu 22.04 host and got exactly the same problems as 1fallen at post #6.
I haven't had time yet to investigate further details of this though I used virtio video rather than QXL or VGA though I will try the other video settings when I have time and report back.

I didn't have those issues, but I installed on hard drive only.

---

### Post by lammert-nijhof on 2023-11-09
I use Virtualbox and the installation of Ubuntu 24.04 froze in the form with the user data. I also installed Budgie. Mate, Xubuntu and Unity and that all worked fine, because by default they still seem to use the old installer.

---

### Post by catuliuf on 2023-11-09
In my case stay working on real machine (xubuntu)

[https://i.imgur.com/hqcKZe3.png](https://i.imgur.com/hqcKZe3.png)

:KS

---

### Post by ajgreeny on 2023-11-09
I updated my iso file of Xubuntu-desktop using zsync and reinstalled using the updated iso an hour ago (20:00hrs UTC, Nov 9) once more using KVM/QEMU.
Whatever the problem was with yesterday's iso has now been fixed and the installation proceeded without a difficulty and seems to run with no problems; early days but looking good at the moment!

---

### Post by MAFoElffen on 2023-11-09
Crossing fingers. Downloading my batch of Daily ISO's to test right now.

EDIT: Got past that problem, but the Ubuntu installer image crashed during the "installing system" stage, with a "file not found" error: [https://bugs.launchpad.net/subiquity/+bug/2042717](https://bugs.launchpad.net/subiquity/+bug/2042717)

Didn't matter what option I tried with it... It failed with a file not found error.

---

### Post by Irihapeti on 2023-11-09
Just tried with Ubuntu. No luck. Possibly a different error, which I've reported as a new bug .

---

### Post by Irihapeti on 2023-11-10
Xubuntu install at least is working.

---

### Post by MAFoElffen on 2023-11-10
20231110 Build for Ubuntu Desktop fails at same place today, but...

*** 'debootstrap', as of last night, now has 'noble' as a valid distribution option for it. Last week, that hadn't been added yet. At least I can test some manual Noble Ubuntu installs... LOL. Having a problem getting some of those to boot from my recipe's on the early tests of that so far.

Dang. Still waiting on a working Ubuntu Desktop ISO, so I can start testing the Desktop autoinstall.yaml examples on Noble...

---

### Post by ajgreeny on 2023-11-10
I've just installed the 20231110 build of Xubuntu in KVM/QEMU and once again there were no difficulties or problems and the system is running fine.

---

### Post by corradoventu on 2023-11-11
> **MAFoElffen said:**
> 
EDIT: Got past that problem, but the Ubuntu installer image crashed during the "installing system" stage, with a "file not found" error: [https://bugs.launchpad.net/subiquity/+bug/2043146](https://bugs.launchpad.net/subiquity/+bug/2043146)
Didn't matter what option I tried with it... It failed with a file not found error.
I'm unable to see your bug, may by is PRIVATE? If yes please change to Public.
I had the same problem so filed 2 bugs: [https://bugs.launchpad.net/subiquity/+bug/2043256](https://bugs.launchpad.net/subiquity/+bug/2043256)
and [https://bugs.launchpad.net/subiquity/+bug/2043274](https://bugs.launchpad.net/subiquity/+bug/2043274)
[https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/289514/testcases/1761/results](https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/289514/testcases/1761/results)

---

### Post by MAFoElffen on 2023-11-12
It was marked as a duplicate to this, which is the active one (edited above): [https://bugs.launchpad.net/subiquity/+bug/2042717](https://bugs.launchpad.net/subiquity/+bug/2042717)

Yesterday morning, they said they released a fix for it in ubuntu-desktop-installer, but testing today, it still gets the same crash and error, in exactly the same place.

---

### Post by MAFoElffen on 2023-11-12
Just did more followup test-cases on the Ubuntu Server ISOs:
AARCH64 iso now installs. No problems found.
S390X iso is still broken. Fails during the install, after the system is copied over, during the config stage.

---

### Post by corradoventu on 2023-11-15
Today I installed successfully from ISO: Ubuntu 24.04 "Noble Numbat" - Daily amd64 (20231115.1)
The install crashed but installed system works fine [https://bugs.launchpad.net/subiquity/+bug/2043577](https://bugs.launchpad.net/subiquity/+bug/2043577) 
I found two strange things:
a lot of messages booting the install medium
/var/log/installer is empty
... see comments in the bug.

 Edit: crash was due to a temporary problem on Italian mirror, repeating install was successful.

---

### Post by Claus7 on 2023-11-15
Hello,

installation was in the end successful. I chose both hellenic language and hellenic keyboard and during installation I saw many errors appearing so I had the chance to report a couple of bugs, one being the same from mantic days. In order to proceed, I had to activate the english keyboard under settings. Irrespective of the errors, installation went fine. I chose the full installation option. 

Regards!

---

### Post by sudodus on 2023-11-15
I cannot install [Ubuntu Desktop with encryption](https://bugs.launchpad.net/subiquity/+bug/2043585) (new bug), but I can install [Lubuntu with encryption](https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/2043301) (squashed bug).

Please try to install Ubuntu Desktop with encryption, and if you are also affected, please add yourself as 'affected' in the bug report (to confirm it and add heat which improves the chances to get it solved).

---

### Post by Claus7 on 2023-11-16
Hello,

> **sudodus said:**
> I cannot install [Ubuntu Desktop with encryption](https://bugs.launchpad.net/subiquity/+bug/2043585) (new bug), but I can install [Lubuntu with encryption](https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/2043301) (squashed bug).

Please try to install Ubuntu Desktop with encryption, and if you are also affected, please add yourself as 'affected' in the bug report (to confirm it and add heat which improves the chances to get it solved).

I opened vb and tried to install anew noble, yet now during installation to enable LVM and encryption (is this the correct procedure?). Installation failed as *sudodus* mentions, yet the error that appeared is the following: install failed crashed with CallProcessError: a bug that I and other users came across before. I marked the bug mentioned from *sudodus* as affecting me though, since installation failed, whereas the other installation attempted went fine. In this case when asked I chose the english setup.

Regards!

---

### Post by MAFoElffen on 2023-11-17
I tested the Ubuntu Desktop install scripts... I was successful with Vanilla, LVM, & ZFS. Failed with LVM encrypted.

I retested Server for IBM S390X, still broken. That got me thinking... I did a debian-upgrade (via sources.list) to Noble on it, and it worked, all except for openssh-server, that package is broken for Noble for arch S390X. That makes sense, now, why the Live Image in that arch has no ssh! LOL.

I haven't tried any of the pre-installed images yet. Or the iso's for AARCH builds for arm64...

I filed a bug on the installer for the Welcome app... I noticed this error, no matter which script successfully installed, during the first boot... That during that process, the Welcome app hangs, becomes unresponsive, throws an error saying it is unresponsive, asking the user if they want to kill it or wait. If you choose wait, it recovers and continues.
RE: [https://bugs.launchpad.net/subiquity/+bug/2043838](https://bugs.launchpad.net/subiquity/+bug/2043838)

If you get that, please mark that it also affects you...

This is a left-over from Mantic, as the current Mantic installer, many users are reporting this happening to them also. If they fix that, that can be backported to Mantic.

---

### Post by Claus7 on 2023-11-17
Hello,

> **MAFoElffen said:**
> ...That during that process, the Welcome app hangs, becomes unresponsive, throws an error saying it is unresponsive, asking the user if they want to kill it or wait. If you choose wait, it recovers and continues.
...

I did notice it, yet I didn't pay so much attention. This is because in newer versions of ubuntu I hear the fans a lot while trying to install under virtualbox, so I suppose that this is because it requires much amount of computer resources in order to work: all in all the installation has become harder I guess. Indeed system requirements have increased, yet until the welcome screen appears, it takes a lot of time. Installation has serious lags, unless more than one cpu is dedicated to vb. Always I increase RAM as well in order to aid the process. 

Regards!

---

### Post by ajgreeny on 2023-11-17
I've just a few minutes ago updated a previous Xubuntu-24.04 iso using zsync and once again it installs in KVM/QEMU without any problems or difficulty.

---

### Post by sudodus on 2023-11-17
> **MAFoElffen said:**
> That during that process, the Welcome app hangs, becomes unresponsive, throws an error saying it is unresponsive, asking the user if they want to kill it or wait. If you choose wait, it recovers and continues.
RE: [https://bugs.launchpad.net/subiquity/+bug/2043838](https://bugs.launchpad.net/subiquity/+bug/2043838)

If you get that, please mark that it also affects you...


Yes, I noticed it too, and I've marked that it also affects me.

---

### Post by corradoventu on 2023-11-21
Installer hangs again [https://bugs.launchpad.net/subiquity/+bug/2044101](https://bugs.launchpad.net/subiquity/+bug/2044101) [https://bugs.launchpad.net/subiquity/+bug/2043915](https://bugs.launchpad.net/subiquity/+bug/2043915)

---

### Post by Frogs Hair on 2023-11-21
I have had installer crashes on Ubuntu and Ubuntu Budgie. Kubuntu and Ubuntu Unity have installed without issue.

---

### Post by corradoventu on 2023-11-22
Crash again: [https://bugs.launchpad.net/subiquity/+bug/2044239](https://bugs.launchpad.net/subiquity/+bug/2044239)

---

### Post by MAFoElffen on 2023-11-22
On 2023.11.22 I'm back to crashing on a CalledProcessError: [https://bugs.launchpad.net/subiquity/+bug/2044288](https://bugs.launchpad.net/subiquity/+bug/2044288)

I now we get this error occasionally since Dev testing 22.04, 23.04, 23.10... I think this is the first time for Noble? IDK

S390X Server is still stuck at the same crash, no progress.

---

### Post by Irihapeti on 2023-11-23
20231123 actually completed an install without doing anything weird. Well, OK, those error messages are still there at the beginning, but they don't seem to stop anything.

---

### Post by corradoventu on 2023-11-23
Also for me the install today was successful: [https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/290311/testcases/1761/results](https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/290311/testcases/1761/results)
For the error messages at the beginning I'm curious about so I opener a bug: [https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/2044376](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/2044376)

---

### Post by MAFoElffen on 2023-11-23
Me too... Except... A weird thing going on with mine on if SecureBoot is being recognised or not... or if recognized previously.

Here is the test-case scenario... This VM was installed on with SecureBoot 'previously', so the key is already marked as trusted, so the installer does not present the MokUtil panel "for a password" to enroll the key into the BIOS on the reboot... That part is correct. But since it didn't kick that part of the installer off, it skips Hardware Enable Encryption (Greyed Out) option, in the advanced install options...

Let me clear the CMOS of the VM and try that again... to confirm that is what is going on before I file a bug on that.

If so, then there is just a problem with the stepped logic where it determines if that option is valid or not. It should be valid:[INDENT]sb-state = SecureBoot Enabled, TPM present. 
sb-key enrolled should not be a determining factor for that install option itself.
[/INDENT]

---

### Post by MAFoElffen on 2023-11-27
I filed a bug on what I described in post #38. On fresh, with secureboot enabled and a TPM 2.0, it does not request for the MOKutil password to enroll the key for SecureBoot, and the option toe Hardware Backed Encryption stays grayed out.
RE: [https://bugs.launchpad.net/subiquity/+bug/2044902](https://bugs.launchpad.net/subiquity/+bug/2044902)

I can see where they "might" have turned off TPM backed encryption, because I did file bugs on that at Launchpad for Mantic... Maybe. But SecureBoot still needs to be there for Noble LTS or it will never pass the CIS / STIG certification.

---

### Post by Irihapeti on 2023-11-27
I'm noticing that the "no or incorrect timezone" bug is back, whether on bare metal or VM. Is that something peculiar to me (and maybe my ISP), or is anyone else seeing it?

Also, I'm noticing that subiquity (Ubuntu and Budgie) seem to pick up on the fact that the Acer laptop is a BIOS machine, but Xubuntu (ubiquity?) doesn't and still creates an EFI partition. Does an EFI partition actually do anything on a BIOS machine, or does it simply take up space?

---

### Post by corradoventu on 2023-12-01
Today I installed from ISO dated 20231201 and the installation used installer 1276 while 1278 exists. In previous installations if a new installer was available the new one was loaded on the fly. now no longer?

---

### Post by MAFoElffen on 2023-12-03
I mentioned that in my bug report on the Hardware Backed Encryption... In what I reported in that bug report, I guess I really should have split that up into 3 Separate Bug Reports:

[LIST]
[*]Hardware Backed Encyption option stays grayed out = Not available 
[*]SecureBoot process not triggered for mokutil key enrollment 
[*]Newer git version check/refresh process not triggered. 
[/LIST]

I'm thinking to correct that, we probably need to file bugs on the other two, as separate bugs, since they are actually 3 separate issues, and link it to that original bug that mentioned it, so they can get dealt with individually... ad so that they do not lose track of what else needs to be corrected. 

Sorry. In hindsight, that would be the right thing to do with those. Do you want me to go back and do that? Or since you noticed that, can you do that?

---

### Post by MAFoElffen on 2023-12-04
Noble S390X Server daily added the app's panel back into the installer.... 

Seeing that added back in, I was hopeful.

But it still crashes at the same exact point, after the system is added to the disk, after the keyboard config, and during the system configuration.  

Dang.

---

### Post by ajgreeny on 2023-12-04
Just installed Xubuntu iso from today, Dec. 4th 2023, this time on a real hard disk alongside my jammy install using my old and unused focal partition, not as a VM in KVM/QEMU.
Everything went faultlessly and now all I need to do is create symbolic links to the data folders (not the hidden configuration folders in my separate / home partition).
Xubuntu seems to be working without any major problems as far as I can see unlike some of the other versions from those available.

---

### Post by Irihapeti on 2023-12-04
I ran into an odd one with Xubuntu install yesterday (NZ time). I was testing the auto-resize and found that it only would let me choose the bootable SD card in the laptop card reader and not the main drive. I didn't notice that it was trying to install to the SD card until it was too late. Fortunately, it didn't do anything that I couldn't recover from, but I do wonder if this is something of a disaster waiting to happen if someone has forgotten that they have another drive connected.

This happened on the old Acer travelmate 4740 that my son gave me, so it might affect only me, but I can't assume that. I've reported it as a bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2045535](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2045535)  Please mark as affected if you come across it.

---

### Post by ajgreeny on 2023-12-05
Having installed Noble Xubuntu alongside my Jammy Xubuntu as I mentioned in post #44, I attempted to get the Jammy grub back to take over the boot process by running from the Jammy install ```
sudo grub-install /dev/sda
``` which worked fine with no errors.
However, on rebooting the computer went straight to the UEFI firmware page and did not get to grub.  I thought I understood better than I obviously do how to change the active grub from one OS to the other but I think I was wrong. Any thoughts.

I can still boot either OS from grub in Noble which I returned to using efibootmgr but having tried efibootmgr to change the boot order back to Jammy I still can not get the Jammy grub version back.
I also can not get changes in Noble's **/etc/default/grub** for the **GRUB_DEFAULT=** to work in spite of updating grub after the edit.
Annoying but not disastrous.  

I shall next try Boot-Repair Advanced to see where that gets me and if all is still strange I shall perhaps re-install Jammy or just live with the Noble grub.

---

### Post by MAFoElffen on 2023-12-05
> **ajgreeny said:**
> Having installed Noble Xubuntu alongside my Jammy Xubuntu as I mentioned in post #44, I attempted to get the Jammy grub back to take over the boot process by running from the Jammy install 
```

[COLOR=#ff0000]sudo grub-install /dev/sda
[/COLOR]
```
 which worked fine with no errors.

That was the command to install Grub as Legacy BIOS.

For UEFI that would have been:
```

grub-install --target=x86_64-efi --efi-directory=/boot/efi \
    --bootloader-id=ubuntu --recheck --no-floppy

```
Oh well. LOL

You can change the boot order in the ESP via efibootmgr...
```

sudo efibootmgr -v

```
Getting what is currently set, then using the "-o" option...

---

### Post by ajgreeny on 2023-12-06
Thanks for that MAFoElffen. I did search and thought I had found a post from oldfred, my guru in such things, saying that the command I used still worked in UEFI as well as legacy BIOS.
I will search again to try and find that post.

None of that explains why editing the /etc/default/grub file in Noble then running update-grub is doing nothing to change the default system booting. Nor does it explain why using efibootmgr which i did in the way you show to get back to my previous setting is not working. 

I will boot back to Jammy later when on that machine and try the command you show.
If that doesn't work I'll try boot-repair and failing that will just reinstall Jammy which is a relatively quick job.

---

### Post by ajgreeny on 2023-12-06
Hooray!

Your command worked and I am now back with my original Jammy install managing grub and the booting of the computer as I wanted.
Thank you for passing on this command to me.

Otherwise I am not finding any major problems so far in Noble but of course, it's very early days and things may, probably will go wrong as we move forward.

---

### Post by Frogs Hair on 2023-12-06
Was finally able to get passed the installer crash when entering the password by installing in safe graphics mode. The fix released some time ago didn't work for me with Ubuntu and the Budgie flavor. I had no problem with Kubuntu and U-Unity.

---

### Post by MAFoElffen on 2023-12-06
> **Frogs Hair said:**
> Was finally able to get passed the installer crash when entering the password by installing in safe graphics mode. *[COLOR=#ff0000]The fix released some time ago didn't work for me[/COLOR]* with Ubuntu and the Budgie flavor. I had no problem with Kubuntu and U-Unity.
Past 'fix' for safe-graphics? 

Please remind me which 'work-around' that was. For which GPU on your hardware?

I'm curious...

---

### Post by ajgreeny on 2023-12-06
Shutting my Xubuntu Noble laptop lid will not suspend the system in spite of the settings for this to happen in Power-manager.
Unfortunately the system freezes when I open the lid requiring a REISUB to get it rebooted again.
Here's the inxi output admittedly from my Jammy install, but the same hardware.
I will update with the inxi output from Noble later.
```
inxi -Fzx
System:
  Kernel: 5.15.0-89-generic x86_64 bits: 64 compiler: gcc v: 11.4.0
    Desktop: Xfce 4.16.0 Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: Notebook product: W54_55SU1,SUW v: N/A
    serial: <superuser required>
  Mobo: Notebook model: W54_55SU1,SUW serial: <superuser required>
    UEFI: American Megatrends v: 4.6.5 date: 05/29/2014
Battery:
  ID-1: BAT0 charge: 53.9 Wh (100.0%) condition: 53.9/93.2 Wh (57.8%)
    volts: 12.7 min: 11.1 model: Notebook BAT status: Full
CPU:
  Info: dual core model: Intel Core i3-4100M bits: 64 type: MT MCP
    arch: Haswell rev: 3 cache: L1: 128 KiB L2: 512 KiB L3: 3 MiB
  Speed (MHz): avg: 798 high: 799 min/max: 800/2500 cores: 1: 798 2: 798
    3: 799 4: 799 bogomips: 19952
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel 4th Gen Core Processor Integrated Graphics
    vendor: CLEVO/KAPOK driver: i915 v: kernel bus-ID: 00:02.0
  Device-2: Acer BisonCam NB Pro type: USB driver: uvcvideo bus-ID: 3-8:3
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: i915 resolution: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel HD Graphics 4600 (HSW GT2)
    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: Yes
Audio:
  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio
    vendor: CLEVO/KAPOK driver: snd_hda_intel v: kernel bus-ID: 00:03.0
  Device-2: Intel 8 Series/C220 Series High Definition Audio
    vendor: CLEVO/KAPOK driver: snd_hda_intel v: kernel bus-ID: 00:1b.0
  Sound Server-1: ALSA v: k5.15.0-89-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Wireless 7260 driver: iwlwifi v: kernel bus-ID: 02:00.0
  IF: wlp2s0 state: up mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: CLEVO/KAPOK driver: r8169 v: kernel port: e000 bus-ID: 03:00.1
  IF: enp3s0f1 state: down mac: <filter>
  IF-ID-1: virbr0 state: down mac: <filter>
Bluetooth:
  Device-1: Intel Bluetooth wireless interface type: USB driver: btusb v: 0.8
    bus-ID: 3-7:2
  Report: rfkill ID: hci0 rfk-id: 0 state: down bt-service: not found
    rfk-block: hardware: no software: no address: see --recommends
Drives:
  Local Storage: total: 465.76 GiB used: 269.08 GiB (57.8%)
  ID-1: /dev/sda vendor: HGST (Hitachi) model: HTS545050A7E380
    size: 465.76 GiB
Partition:
  ID-1: / size: 19.52 GiB used: 12.34 GiB (63.2%) fs: ext4 dev: /dev/sda2
  ID-2: /boot/efi size: 196.9 MiB used: 19.9 MiB (10.1%) fs: vfat
    dev: /dev/sda1
  ID-3: /home size: 417.81 GiB used: 256.72 GiB (61.4%) fs: ext4
    dev: /dev/sda3
Swap:
  ID-1: swap-1 type: file size: 947.5 MiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 48.0 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 216 Uptime: 20m Memory: 7.67 GiB used: 1.75 GiB (22.8%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 2243 Shell: Bash
  v: 5.1.16 inxi: 3.3.13

```

---

### Post by MAFoElffen on 2023-12-06
@ajgreeny --

Could you please rerun that from Noble so I can compare what it is using as drivers and how it is seen?

---

### Post by Frogs Hair on 2023-12-07
> **MAFoElffen said:**
> Past 'fix' for safe-graphics? 

Please remind me which 'work-around' that was. For which GPU on your hardware?

I'm curious...
 
No, there was a fix released for the installer crash at the adding password phase of the installation which didn't work for me. After many attempts I tried safe graphics mode and was finally able to complete the installation. The workaround came to mind when the screen-shot tool caused the installer to crash and I thought it maybe graphics related.

---

### Post by ajgreeny on 2023-12-07
Here's the output of inxi -Fzx from Noble to compare with the output in post #52 which was from Jammy.

I've searched bur so far can't find any obvious reason for the problem of the laptop lid closure not suspending as Jammy does.
```
inxi -Fzx
System:
  Kernel: 6.5.0-9-generic arch: x86_64 bits: 64 compiler: N/A Desktop: Xfce
    v: 4.18.1 Distro: Ubuntu 24.04 (Noble Numbat)
Machine:
  Type: Laptop System: Notebook product: W54_55SU1,SUW v: N/A
    serial: <superuser required>
  Mobo: Notebook model: W54_55SU1,SUW serial: <superuser required>
    UEFI: American Megatrends v: 4.6.5 date: 05/29/2014
Battery:
  ID-1: BAT0 charge: 53.9 Wh (100.0%) condition: 53.9/93.2 Wh (57.8%)
    volts: 12.7 min: 11.1 model: Notebook BAT status: full
CPU:
  Info: dual core model: Intel Core i3-4100M bits: 64 type: MT MCP
    arch: Haswell rev: 3 cache: L1: 128 KiB L2: 512 KiB L3: 3 MiB
  Speed (MHz): avg: 800 min/max: 800/2500 cores: 1: 800 2: 800 3: 800 4: 800
    bogomips: 19955
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel 4th Gen Core Processor Integrated Graphics
    vendor: CLEVO/KAPOK driver: i915 v: kernel arch: Gen-7.5 bus-ID: 00:02.0
  Device-2: Bison BisonCam NB Pro driver: uvcvideo type: USB bus-ID: 3-8:3
  Display: x11 server: X.Org v: 21.1.7 driver: X: loaded: modesetting
    unloaded: fbdev,vesa dri: crocus gpu: i915 resolution: 1920x1080~60Hz
  API: EGL v: 1.5 drivers: crocus,swrast platforms:
    active: gbm,x11,surfaceless,device inactive: wayland
  API: OpenGL v: 4.6 compat-v: 4.5 vendor: intel mesa v: 23.2.1-1ubuntu4
    glx-v: 1.4 direct-render: yes renderer: Mesa Intel HD Graphics 4600 (HSW
    GT2)
Audio:
  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio
    vendor: CLEVO/KAPOK driver: snd_hda_intel v: kernel bus-ID: 00:03.0
  Device-2: Intel 8 Series/C220 Series High Definition Audio
    vendor: CLEVO/KAPOK 8 driver: snd_hda_intel v: kernel bus-ID: 00:1b.0
  API: ALSA v: k6.5.0-9-generic status: kernel-api
  Server-1: PipeWire v: 0.3.85 status: active
  Server-2: PulseAudio v: 16.1 status: off (using pipewire-pulse)
Network:
  Device-1: Intel Wireless 7260 driver: iwlwifi v: kernel bus-ID: 02:00.0
  IF: wlp2s0 state: up mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: CLEVO/KAPOK driver: r8169 v: kernel port: e000 bus-ID: 03:00.1
  IF: enp3s0f1 state: down mac: <filter>
Bluetooth:
  Device-1: Intel Bluetooth wireless interface driver: btusb v: 0.8 type: USB
    bus-ID: 3-7:2
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter> bt-v: 4.0
    lmp-v: 6
Drives:
  Local Storage: total: 465.76 GiB used: 265.7 GiB (57.0%)
  ID-1: /dev/sda vendor: HGST (Hitachi) model: HTS545050A7E380
    size: 465.76 GiB
Partition:
  ID-1: / size: 19.52 GiB used: 8.37 GiB (42.9%) fs: ext4 dev: /dev/sda4
  ID-2: /boot/efi size: 196.9 MiB used: 19.9 MiB (10.1%) fs: vfat
    dev: /dev/sda1
Swap:
  Alert: No swap data was found.
Sensors:
  System Temperatures: cpu: 49.0 C mobo: N/A
  Fan Speeds (rpm): N/A
Info:
  Processes: 208 Uptime: 2m Memory: total: 8 GiB available: 7.66 GiB
  used: 925.2 MiB (11.8%) Init: systemd target: graphical (5) Compilers: N/A
  Packages: 1630 Shell: Bash v: 5.2.15 inxi: 3.3.31

```

---

### Post by #&amp;thj^% on 2023-12-07
ajgreeny I see from jammy
```
Swap:
  ID-1: swap-1 type: file size: 947.5 MiB used: 0 KiB (0.0%) file: /swapfile
```
and Noble:
```
Swap:
  Alert: No swap data was found.
```

---

### Post by ajgreeny on 2023-12-07
@1fallen.
Had not noticed that and I'm surprised that I missed it!
I used the **Something Else** option when installing using what had been my Focal partition to avoid any mistakes or overwriting of my jammy partition but forgot that a swapfile is apparently added only if you use the **Use Whole Disk** method.
The system does suspend if I choose that from the logout/shutdown dialogue and also from a keyboard shortcut I have added using the Pause/Break key, otherwise unused on my machines.
I shall add a swapfile and see where that takes me if I can find how to do so easily; never done it before as I've never needed to do so because it's always been created when installing the system.
I wonder if this is another Noble problem not yet seen by others.

---

### Post by #&amp;thj^% on 2023-12-07
@ajgreeny, if that don't help, what are your power settings set as ie:
[s]```
  gsettings set org.gnome.settings-daemon.plugins.power lid-close-ac-action 'suspend'
```
Possible setting values instead of suspend are:
```
'blank', 'suspend', 'shutdown','hibernate', 'interactive', 'nothing', 'logout'
```[/s]
Never mind that one 
```
gsettings set org.gnome.settings-daemon.plugins.power lid-close-ac-action 'suspend'No such schema &#8220;org.gnome.settings-daemon.plugins.power&#8221;

```

---

### Post by MAFoElffen on 2023-12-08
LOL. You do need a swap (of some type) if you intend to do a suspend. The Laptop lid-switch action defaults to suspend. 

Can you create a swap partition or file? And put it in fstab?

Otherwise... I think it's org.gnome.settings-daemon.plugins.power.lid-close-battery-action and org.gnome.settings-daemon.plugins.power.lid-close-ac-action ... and the valid options are: blank, suspend, shutdown, hibernate, interactive, nothing, & logout.

---

### Post by ajgreeny on 2023-12-08
Haven't been on the laptop for a while now but the question remains - why was no swapfile created when I installed?
There is nothing in the installer regarding swap other than creating a swap partition. My Jammy on the same hard disk uses swapfile not a partition and I just assumed a swapfile would be created automatically in this Noble system.

Another bug maybe which I should report?

---

### Post by corradoventu on 2023-12-08
Installing Ubuntu Noble reusing an existing partition the installer creates a swap file also if on my PC exist a swap partition. The old installer was able to recognize and use automatically the swap partition.
```
corrado@corrado-n8-nn-1201:/$ ls
bin   cdrom  etc   lib    lost+found  mnt  proc  run   snap  swap.img  tmp  var
boot  dev    home  lib64  media       opt  root  sbin  srv   sys       usr
corrado@corrado-n8-nn-1201:/$ 

```

---

### Post by ajgreeny on 2023-12-08
> **corradoventu said:**
> Installing Ubuntu Noble reusing an existing partition the installer creates a swap file also if on my PC exist a swap partition. The old installer was able to recognize and use automatically the swap partition.
```
corrado@corrado-n8-nn-1201:/$ ls
bin   cdrom  etc   lib    lost+found  mnt  proc  run   snap  swap.img  tmp  var
boot  dev    home  lib64  media       opt  root  sbin  srv   sys       usr
corrado@corrado-n8-nn-1201:/$ 

```
So why didn't my install create the swapfile I was expecting?
Is this related to me using Xubuntu and not Ubuntu perhaps?

---

### Post by corradoventu on 2023-12-08
Xubuntu uses the old installer Ubiquity while Ubuntu uses the new ubuntu-desktop-installer completely rewritten in snap format so the logic may be different.

---

### Post by MAFoElffen on 2023-12-09
@ajgreeny -- I would report it. 

If the install was from one of the automated, canned install scripts... But you said you used "other" in the partitioner right?

Not sure of... At a certain point, the installer changed with swap, where it created swap files by default, instead of the swap partition. But if you created manually, it had internal logic that recognized that there was "something" swap related there, so it only applied one at a time. Not sure if using the manually partitioner overrode that. Because before, the logic was there to recognize if there was swap there or not in the 'checks'.

That doesn't seem like it saw that there was not. That is my guess there.

I always created a swap partition. Just old-school I guess. That and performance was still better with a swap partition rather than swap file. Dang, I'm going in circles.

I would report it anyways. Better for it to get nixed, than overlooked because we didn't mention it, right? Especially since this is LTS.

---

### Post by este.el.paz on 2023-12-09
et al:

haven't been following the thread, just passing through . . . I'm running my Lubuntu install in mantic right now.  I usually edit the sources list to move up in iteration, I'm assuming "noble" is the next option . . . is noble at "alpha" level or it's "pre-alpha"??

---

### Post by #&amp;thj^% on 2023-12-09
Right now I'd have to say "pre-alpha" It's not due until April 2024

---

### Post by este.el.paz on 2023-12-09
> **1fallen said:**
> Right now I'd have to say "pre-alpha" It's not due until April 2024


@1fallen:

Thanks for the fast reply . . . well, April isn't that far away . . . .  : - )  I'm OK with Mantic, it seems to be "steadying down" on my machine, today booting it up didn't spin up the GPU to subsonic speeds as it seemed to be doing only last week . . . it's more quiet.

But, then, I do like fresh horsies . . . better part of valor these days seems to be to wait for "alpha" level product . . . too much going on with the multi-boot machine as it is, keeping the various "plates" operational.  Might be a couple of months and then check out the "noble" offering . . . .

---

### Post by MAFoElffen on 2023-12-09
Hardware back encryption is still not offered, and the Installer still doesn't recognize if SecureBoot is enabled (I split that out to it's own bug report: [https://bugs.launchpad.net/subiquity/+bug/2046036](https://bugs.launchpad.net/subiquity/+bug/2046036)). But that is the flutter installer...

And... LVM Encrypted install still crashes for me. At least now it gets past the Security Key panel before it crashes. LOL ([https://bugs.launchpad.net/subiquity/+bug/2046050](https://bugs.launchpad.net/subiquity/+bug/2046050))

Are those working on the other flavor's besides Ubuntu? Or is that the same and not working with those either?

---

### Post by #&amp;thj^% on 2023-12-09
> **MAFoElffen said:**
> Hardware back encryption is still not offered, and the Installer still doesn't recognize if SecureBoot is enabled (I split that out to it's own bug report). But that is the flutter installer...

And... LVM Encrypted install still crashes for me. At least now it gets past the Security Key panel before it crashes. LOL

Are those working on the other flavor's besides Ubuntu? Or is that the same and not working with those either?

I can't remember, but my Xubuntu on the Intel X! is encrypted but that one is a sed to Noble install, but it works.
```
 sudo dmsetup status
cryptoswap: 0 4194304 crypt 
keystore-rpool: 0 991232 crypt
```

---

### Post by MAFoElffen on 2023-12-09
Oh dang. I forgot to add the bug report here: [https://bugs.launchpad.net/subiquity/+bug/2046036](https://bugs.launchpad.net/subiquity/+bug/2046036)

If you do an install with SecureBoot Enabled and it doesn't see that, please go there and indicated "also affects me", so that it gets changed to confirmed.

---

### Post by #&amp;thj^% on 2023-12-09
> **MAFoElffen said:**
> Oh dang. I forgot to add the bug report here: [https://bugs.launchpad.net/subiquity/+bug/2046036](https://bugs.launchpad.net/subiquity/+bug/2046036)

If you do an install with SecureBoot Enabled and it doesn't see that, please go there and indicated "also affects me", so that it gets changed to confirmed.

What I see so far:
> Lost something?

This page does not exist, or you may not have permission to see it.



I'm logged in

---

### Post by MAFoElffen on 2023-12-09
Dang. LOL. 

I converted it from 'private security' to 'public security', so that others can join in.

I seem to forget that checking the "security risk" checkbox creates bugs as "Private".

---

### Post by ajgreeny on 2023-12-09
Launchpad bug created regarding the failure of swapfile creation as suggested in post #64 following my post #57.
[https://bugs.launchpad.net/ubuntu/+bug/2046049](https://bugs.launchpad.net/ubuntu/+bug/2046049)
Not much detail so far as I'm not using that laptop at present but I will add more as I use that machine.

---

### Post by MAFoElffen on 2023-12-09
@ajgreeny --

So how was that installed... Via the "others" & in the partitioner right?

If I can try to recreate that, to verify that problem, then join it, and possibly get that toggled to confirmed... I have some time this afternoon.

---

### Post by ajgreeny on 2023-12-10
OK,  here goes.

The computer, a Clevo laptop which runs Ubuntu family systems very well, had a 20G partition with Xubuntu 20.04 and a second 20G partition with Xubuntu 22.04. I have used a separate /home partition for many years but during development I do not use that on the new installations but use symbolic links from that existing /home partition's folders to the user's home folder data partitions in the new system; both use the same username. I do not use any of the existing hidden configuration folders in the existing /home.

I never booted to the 20.04 system once I was satisfied that 22.04 was fully dependable so decided on Dec 4th to replace that 20.04 partition with the Dec 4th 24.04 system installed with an iso which I zsync updated from a previous iso version; I keep my iso versions up to date that way all through development.5

I chose the **Something Else** at partitioning and used the 20.04 partition as a new / partition for 24.04. I have no swap partition and the 22.04 system uses a swapfile without a problem.

I had expected the new 24.04 system to create a swapfile automatically but that did not happen and I did not notice that for some time when discussing things in this thread, thanks to 1fallen.

The 24.04 system runs well for such an early stage in development and I do not use it for resource hungry activities; it was only the failure of suspending when closing the laptop lid that led to this situation requiring the bug I posted.

I will add this detail to the bug later rather than now on this Android tablet.

---

### Post by corradoventu on 2023-12-10
I just installed from Ubuntu 24.04 LTS "Noble Numbat" - Daily amd64 (20231210)
The ISO contains ubuntu-desktop-installer 1276 while 1278 is available so I successfully installed using both:
[https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291424/testcases/1761/results](https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291424/testcases/1761/results)

---

### Post by sudodus on 2023-12-10
> **MAFoElffen said:**
> Hardware back encryption is still not offered, and the Installer still doesn't recognize if SecureBoot is enabled (I split that out to it's own bug report: [https://bugs.launchpad.net/subiquity/+bug/2046036](https://bugs.launchpad.net/subiquity/+bug/2046036)). But that is the flutter installer...

And... LVM Encrypted install still crashes for me. At least now it gets past the Security Key panel before it crashes. LOL ([https://bugs.launchpad.net/subiquity/+bug/2046050](https://bugs.launchpad.net/subiquity/+bug/2046050))

Are those working on the other flavor's besides Ubuntu? Or is that the same and not working with those either?

Lubuntu Noble with the installer Calamares works with LUKS encryption:

```

tester@tester-satelliteproc85019w:~$ lsblk -e7 -o model,name,size,fstype,label,mountpoints /dev/sda                                                  
MODEL                  NAME                                            SIZE FSTYPE      LABEL MOUNTPOINTS                                            
KINGSTON SV300S37A120G sda                                           111,8G                                                                          
                       &#9492;&#9472;sda1                                        111,8G crypto_LUKS                                                              
                         &#9492;&#9472;luks-c1e44bf6-08ba-4878-b804-9568b857c22a 111,8G ext4              /var/snap/firefox/common/host-hunspell
                                                                                              /snap
                                                                                              /
tester@tester-satelliteproc85019w:~$ 

```

Edit: 

This system is installed in BIOS mode (alias CSM alias legacy mode). Some week ago I tested also in UEFI mode, and it works there too, and if I remember correctly, there is also an EFI system partition (unencrypted) in that case.

---

### Post by MAFoElffen on 2023-12-10
@ajgreeny -- I changed the bug to file against ubiquity, instead of Ubuntu, since it is the old installer... I used today's Xubuntu Daily. I installed in 3 different test-cases, noted there, in that bug. Status has now changed to confirmed, and filed against Ubiquity... It does recognise if a swap partition exists already and reuses it, but doesn't create any swap file.

The Xubuntu installer did recognize the SecureBoot state, whereas the Ubuntu installer is not doing that. So that is only wrong on the Ubuntu and Bungie installers... so in ubuntu-desktop-installer.

---

### Post by MAFoElffen on 2023-12-10
Which brings up a good information FYI on reporting installer bugs...

SubiuityUbuntu Server Ubuntu Desktop
[TABLE="class: grid, width: 500, align: left"]
[TR]
[TD]Flavor(s)[/TD]
[TD]Installer to File Bug against[/TD]
[/TR]
[TR]
[TD]Ubuntu Server & Desktop, Bungie[/TD]
[TD]Subiquity[/TD]
[/TR]
[TR]
[TD]Xubuntu, Kubuntu[/TD]
[TD]Ubiquity[/TD]
[/TR]
[TR]
[TD]Lubuntu[/TD]
[TD]Calamares[/TD]
[/TR]
[/TABLE]







AFAIK, if there are bugs in the installer itself, you file the bug against the installer used for that flavor. I'm not sure of what the other flavors not listed here are. I'm assuming most likely Ubiquity(?)

So if I get something not working as expected, or something "missing", where it expected doesn't result in what happens... That doesn't always general a crash report to file a bug, so I do thta manually. I file a bug report, for example, like this:
```

ubuntu-bug subiquity

```
That will collect all the pertinent files, logs and information related to that installer for upload. Then upload any crash reports (if any) from /var/crash, and in the description... Usually with these sections
[LIST]
[*]Noble <flavor> daily <date> 
[*]Expected Results 
[*]What that resulted in instead, in which section of the installer (So they can see were that happens when they recreate it.) 
[*]How to recreate the problem. 
[/LIST]

^^^ That seems to work for them (so far) to be able to find out what is wrong, and get a good start on resolving those problems. From my past experience as a maintenance programmer, I know if I were in their place, I would appreciate that information.

@ajgreeny -- It didn't upload any information from your machine to that bug... To do that, if you do this in this format, then it will do that and not cause that to get marked as incomplete, because it is missing those:
```

# syntax: apport-collect <bug_number>
apport-collect 2046049

```

---

### Post by ajgreeny on 2023-12-10
I tried several times to file my bug against ubiquity but was each time notified that there was no such package in Ubuntu in spite of saying this was using Xubuntu not Ubuntu.
I was far too busy with family matters to try to forward this, so gave up trying, even though I was certain that ubiquity was the problem. I then received the email notification that the bug was accepted, partly perhaps, following your post, now added to the bug.

---

### Post by #&amp;thj^% on 2023-12-10
> **sudodus said:**
> Lubuntu Noble with the installer Calamares works with LUKS encryption:

```

tester@tester-satelliteproc85019w:~$ lsblk -e7 -o model,name,size,fstype,label,mountpoints /dev/sda                                                  
MODEL                  NAME                                            SIZE FSTYPE      LABEL MOUNTPOINTS                                            
KINGSTON SV300S37A120G sda                                           111,8G                                                                          
                       &#9492;&#9472;sda1                                        111,8G crypto_LUKS                                                              
                         &#9492;&#9472;luks-c1e44bf6-08ba-4878-b804-9568b857c22a 111,8G ext4              /var/snap/firefox/common/host-hunspell
                                                                                              /snap
                                                                                              /
tester@tester-satelliteproc85019w:~$ 

```

Edit: 

This system is installed in BIOS mode (alias CSM alias legacy mode). Some week ago I tested also in UEFI mode, and it works there too, and if I remember correctly, there is also an EFI system partition (unencrypted) in that case.
Xubuntu also is good with  Ubiquity installer and  LUKS encryption, Secure Boot
```
lsblk -e7 -o model,name,size,fstype,label,mountpoints /dev/nvme0n1p2
MODEL NAME         SIZE FSTYPE      LABEL      MOUNTPOINTS
      nvme0n1p2      2G crypto_LUKS            
      &#9492;&#9472;cryptoswap   2G swap        cryptoswap [SWAP]

```

---

### Post by MAFoElffen on 2023-12-10
> **ajgreeny said:**
> I tried several times to file my bug against ubiquity but was each time notified that there was no such package in Ubuntu in spite of saying this was using Xubuntu not Ubuntu.
I was far too busy with family matters to try to forward this, so gave up trying, even though I was certain that ubiquity was the problem. I then received the email notification that the bug was accepted, partly perhaps, following your post, now added to the bug.
That is because, after the install, the package from the installer doesn't exist on the installed instance. That is where I make a decision on what I want to fill something on or against. A lot of times, IDK, so I'll ask here, if anyone here has any ideas about what to file some things against.

For installer issues, I'll starting to fill things out in the ISO tracker, then I'll re-fire up the installer ISO in "try" mode, and file it from there.  That way it sees the installer package, and collects information on "that' Daily Installer image, it's image version, etc.

Or I'll go to a bug in a certain package I want to file something against, use the link on the upper right where it says "File a Bug", start a new one, then upload files.

Though sometimes, I admit, sometimes I'll just file it against "anything" that I know is installed, that might be close, and what I suspect, try to explain it, and hope that they can figure it out. Some times I just do not know. LOL. Dang. We try.

---

### Post by ajgreeny on 2023-12-11
Another Xubuntu 24.04 installation problem that I've just come across.
An attempt to install on another Clevo laptop with an iso downloaded Dec 10th has now shown a failure to install grub.
This is a UEFI install on a 256G nvme disk which had 22.04 installed and working well.

The 24.04 installation appeared to go well until the grub installation when it errors saying "grub installation failed; this is a fatal error".

Following that I have successfully installed other distros in the Ubuntu family but repeated tries with Xubuntu 24.04 still failed at the same point.

No bug raised for this yet but will do so if newer iso files continue to give this same problem.

---

### Post by MAFoElffen on 2023-12-11
Hmm.

Noble Server Daily doesn't recognize SecureBoot being enabled either. Installed, but hung on the reboot, right at the end of the cloud-int. 

I know that the Desktops installed for Secureboot and enrolled the mok keys on the reboot since 20.04 LTS...

I do not remember that for previous Server Edition's installer or not. (If that panel and process was was there or not?) 

Actually, after thinking about that, I spun up a 22.04.3 server Edition installer, let it refresh to newest, and it didn't have that process, I do not know why. It also installed, did not enroll any key on reboot, but then it booted successfully(?). 

I reported it anyways. I filed it as separate bug, than the one for Desktop Edition: [https://bugs.launchpad.net/subiquity/+bug/2046107](https://bugs.launchpad.net/subiquity/+bug/2046107) As it is for Server Edition, I'm not sure if it is really a bug or not, and I'm not sure if that process was ever there. I don't remember if it was or not.

---

### Post by ajgreeny on 2023-12-11
Just downloaded today's Xubuntu 24.04 Desktop iso (Dec 11th 2023) by using zsync on the iso file from two days ago and installed it again on the same Clevo machine that failed to install grub yesterday.
Today everything worked as it should when I installed using the whole nvme disk and installed grub and also created the swapfile as it should.  The system is running very well and manages to suspend successfully at the moment.

However I used the same USB to reinstall this newer iso on my first laptop, overinstalling the version I originally mentioned several days ago. As this is a dual boot system with Jammy on one partition an Noble on another I this time used the Something Else option in order to reuse the partition I put Noble on a few days ago.

As this had worked properly only 2 hours previousy I expected the same to happen again.
Regrettably not!
At least grub was installed successfully but once again no swapfile was created so I added a new swap partition using gparted.

It seems likely from this that creation of a swapfile depends on how the partitions are used/created, and maybe a swapfile is created only if it is a full disk install without manual use of any existing partitions.

I shall update my bug on this when I have the time to do so.

---

### Post by guiverc on 2023-12-12
I'll give a warning for anyone *playing* with Lubuntu *noble* ISOs on a *dual boot* machine where they value data!  (ie. non-QA only hardware).

If you have started an install which could be destructive (*partition changes such as resize etc*), do **NOT** make any change to the lubuntu-installer-prompt window & click apply; the apply will cause the app to restart your session which will *kill* calamares & thus you risk damage if it was doing something at the time.

This has been reported here - [https://bugs.launchpad.net/ubuntu/+source/lubuntu-installer-prompt/+bug/2046100](https://bugs.launchpad.net/ubuntu/+source/lubuntu-installer-prompt/+bug/2046100)

Other Lubuntu specific *known* (*recent*) issues are

- lubuntu-installer-prompt language ([https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/2046099](https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/2046099))
- if you do a minimal install (*which installs without snap/snapd and NO WEB BROWSER*), you don't have anything to complete the `xdg-open` process started with tools like `ubuntu-bug`

None of these worry me (*at this early stage*), but I'm posting here because the FIRST I list could be destructive to data you value (*if used on a machine with data you value*).

---

### Post by Irihapeti on 2023-12-12
I noticed that calamares changed the partition table on my old Acer Travelmate from GPT to MBR, which didn't entirely impress me. I think (from memory) that this was an entire-disk install. Is this likely to cause problems or just me being picky? i.e. is it worth reporting?

---

### Post by MAFoElffen on 2023-12-12
> **Irihapeti said:**
> I noticed that calamares changed the partition table on my old Acer Travelmate from GPT to MBR, which didn't entirely impress me. I think (from memory) that this was an entire-disk install. Is this likely to cause problems or just me being picky? i.e. is it worth reporting?
I would report it... And before the next install use "try" and zero the disk to start fresh...

This is what I do for ZFS test-cases, because there was a bug with Mantic where the new installer, on erase and ___ failed if ZFS existed on the disks previously to a new install, because it failed on their function zfs_erase(). I recommended a patch to correct that, but just in case, I zero the disks anyways on fresh installs.

Find the target disk
```

ls -l /dev/disk/by-id/

```
Note that disk and use that here...
```

DISK=/dev/disk/by-id/<unique_disk_id>
blkdiscard -f $DISK
wipefs -a $DISK
sgdisk --zap-all $DISK

```
All traces of anything will be gone...

I also do some test-cases where I will first do "Try", and Add either an MS-DOS or GPT partition table, then start the installer...

At least previous to Noble:
If the installer starts in BIOS mode and the disk has an GPT partition table, it should keep that and add a bios_boot partition, where I see if it will honor that. then install Grub2 to boot as Legacy. If it starts in UEFI mode, and has an MS-DOS partition, then it should add an ESP partition, and boot as UEFI.

AFAIK, it should be the same now. Or has things changed for Noble? I haven't heard anything different to that.

---

### Post by Irihapeti on 2023-12-12
> **MAFoElffen said:**
> I would report it... And before the next install use "try" and zero the disk to start fresh...

<snip>

Thanks, that sounds like a good idea. I'll give that a go later on.

---

### Post by guiverc on 2023-12-13
> **Irihapeti said:**
> I noticed that calamares changed the partition table on my old Acer Travelmate from GPT to MBR, which didn't entirely impress me. I think (from memory) that this was an entire-disk install. Is this likely to cause problems or just me being picky? i.e. is it worth reporting?

I agree with MAFoElffen, reports get noticed (*if for no other reason that it appears in lots of our intrays*). 

I've never seen, and can't recall of any mention of a partition type changing (MBR to GPT), except via creation of a new partition table (ie. *full disk install which is the default for calamares*) where GPT is the default for a EFI detected system (*a pic of the manual can be see [here]("https://manual.lubuntu.me/stable/_images/partitioning.png"); note the EFI top left of the info area (ignore progress panel far-left) near top of screen*)

---

### Post by Irihapeti on 2023-12-13
I've run a few tests, and it seems that calamares is the only one that changes the partition table type to mbr. I even tried with a mbr disk (the rest of the disk unallocated) in  a UEFI VM with Ubuntu (subiquity) and it left the partition table type alone. It still (as far as I can tell) was able to create a UEFI boot.

So I don't know quite what to think, and it's getting a bit late here for serious brain work, so I'll leave it for tonight.

---

### Post by guiverc on 2023-12-13
@irihapeti

For me to just run some simple tests to try and re-create the MBR->GPT change, can you provide some details as to what install method you used.

[B]

UBUNTU STUDIO TESTERS please note



[/B]I noted this on IRC (#ubuntu-bugs-announce), but its possible that users booting a *live* system of Ubuntu Studio *noble* for QA may discover it isn't working, due to 

[https://bugs.launchpad.net/ubuntu/+source/livecd-rootfs/+bug/2046386](https://bugs.launchpad.net/ubuntu/+source/livecd-rootfs/+bug/2046386)

(*an issue in switching to ubuntu-desktop-installer*).

---

### Post by Irihapeti on 2023-12-13
@guiverc
Actually, the change was the other way around: GPT partition table being changed to MBR. The disk could either have existing content, such as the install of another flavour that I was overwriting, or just have the GPT partition header and the rest of it unallocated. It didn't seem to make any difference. In the installer, I used the "Erase disk" option.

---

### Post by guiverc on 2023-12-13
> **Irihapeti said:**
> In the installer, I used the "Erase disk" option.

The ERASE DISK option with calamares means you want to create a new partition table; so your boot mode would be expected to set the partition table being used (I believe).  Your old partition table type has no bearing on this, as you've elected to ERASE DISK & create a new partition table.

If EFI hardware is detected, I'd expect it to use GPT by default 
If BIOS hardware is detected, I'd expect it to use MBR by default.

You can tell how your machine was recognized by calamares by looking top left of the window ([https://manual.lubuntu.me/master/_images/partitioning.png](https://manual.lubuntu.me/master/_images/partitioning.png) looking top left of the white background section; to left of storage.device)

Please note:  *The rules I've outlined with regards EFI/BIOS are as I recall them; I cannot guarantee that detail is accurate; but I believe it to be. I did extensive testing on this many cycles ago, but I doubt its changed on our much newer version of calamares. Sorry i can't recall if disk capacity (40gb, 80gb, 250gb etc)  is also involved in this decision.*

---

### Post by Irihapeti on 2023-12-13
I suppose then, what confuses me is that all the other installers' equivalent option (erase disk and install k/x/ubuntu) doesn't do anything to the partition table type.

---

### Post by guiverc on 2023-12-14
> **Irihapeti said:**
> I suppose then, what confuses me is that all the other installers' equivalent option (erase disk and install k/x/ubuntu) doesn't do anything to the partition table type.

I started my testing in the *cosmic* cycle (18.10), thus Lubuntu had already [started] using the calamares installer; and I just learnt what it did. Whilst I then spent half my time testing my[then] *favorite* Xubuntu, and Lubuntu (*the two flavors that still provided i386 images*) I just accepted differences as partition setup is done by the installer itself.  Calamares was not built to be consistent with prior Ubuntu installers, unlike say ubuntu-desktop-installers taking over from older ubiquity.

Some calamares documentation can be read [here]("https://calamares.io/docs/partitions/") (*manual partitioning*) which says the installer defaults to GPT, but does mention how to switch that to BIOS/mbr. I have found the *summary* screen easy enough though to check what it'll do, and thus any differences to my intended partitioning layout easy to detect (*minor exceptions being mostly bug related*)

IF HOWEVER, you consider it a problem, please raise a bug report; and suggest we make calamares consistent with other flavors.

(FYI:  If you were to use the *unofficial *Xubuntu *noble* ISO that the xubuntu devs were talking about creating (*as a** proof of concept using calamares**; I can't recall if it was actually created but I thought it was; IRC discussions a few days ago*) I suspect it would respond identically to the official Lubuntu ISOs)

---

### Post by Irihapeti on 2023-12-14
I think that this is an issue that would probably not even be noticed by many people in the real world. They want to install Lubuntu, may not actually be clear whether their machine is BIOS or UEFI, and don't really care as long as the thing works. In other words, it's just tinkerers like me who are even going to notice anything unusual, and I don't think I'm the kind of user the devs have in view. :)

A long-winded way of saying that I'm being a bit fussy over something that, in the larger scheme of things, isn't that important?

---

### Post by MAFoElffen on 2023-12-14
Maybe I might have a bit of a different perspective on that. Since I have worked with Yann on Test-Disk, Boot-Info,  Boot-Repair since around 2012... (too long) this is what I was taught, and the way things  have been. There are constraints that Windows follows, that do not exist  for Grub2 (& Linux)... But then again, there are some rules for  Grub2 also, that are just a bit more open...

quiverc -- In that link, I read that as "if there were no partition table" that Calamares leans towards GPT... But to stay like the the other installers, and how I've historically done some of my test-cases to confirm that "as explained a few posts back"... That link does not really differ from what I explained in Post #88, but...--> If you set a partition type and choose "Erase All and Install ___." ...

That the installer should, (in it's rule-based logic)
[LIST]
[*]if it does not see a partition table, choose a partition table type based on the boot mode (prefer GPT). 
[*]if there is a partition table type set, honor the user's choice of partition table type, and use it. 
[/LIST]
There are reasons to honor a User's decision, rather than override it.

If it overrides the decision, then, what was told to me about the other installers, that is considered a bug.

Take this example... On the Forum: We often tell users the benefits of using a GPT partition table, over using an MS-DOS partition table type. Can be over 2TB and boot. Can have more than 4 primary partitions, etc... We tell the user, just to create a new partition of type GPT and to choose "Erase all" in the installer. That the installer will honor that and make the right decisions from there. See where Calamares not honoring that overrides, not just that decision, but the ability to do that?

[HR][/HR]
So if not considered currently as a Bug for Lubuntu, in respect to how Calamares does that... based on that reasoning, I believe it should be considered a Bug. Right? Or do you think there is reasoning for overriding that, and taking the ability to do that away?

---

### Post by sudodus on 2023-12-14
I  tested right now with Lubuntu Noble (iso file dated Dec 13) in a Toshiba Satellite Pro C850-19W to **install using the whole drive**

- in UEFI mode, when there is an MSDOS partition table in the internal drive
- in BIOS mode, when there is a GUID partition table (GPT) in the internal drive

In both cases the partition tables were switched, so Calamares forces

- a GUID partition table (GPT) in the internal drive when installing in UEFI mode
- an MSDOS partition table in the internal drive when installing in BIOS mode

I agree that this should be reported as a bug. I would accept this behaviour when there is no partition table on the internal drive, but when there is already a partition table, it should be kept, because the user might have selected it before starting the installer.

An alternative is to set GPT by default, but give the user the *option to select* an MSDOS partition table (in Calamares).

---

### Post by #&amp;thj^% on 2023-12-14
> **sudodus said:**
> I  tested right now with Lubuntu Noble (iso file dated Dec 13) in a Toshiba Satellite Pro C850-19W to **install using the whole drive**

- in UEFI mode, when there is an MSDOS partition table in the internal drive
- in BIOS mode, when there is a GUID partition table (GPT) in the internal drive

In both cases the partition tables were switched, so Calamares forces

- a GUID partition table (GPT) in the internal drive when installing in UEFI mode
- an MSDOS partition table in the internal drive when installing in BIOS mode

I agree that this should be reported as a bug. I would accept this behaviour when there is no partition table on the internal drive, but when there is already a partition table, it should be kept, because the user might have selected it before starting the installer.

An alternative is to set GPT by default, but give the user the *option to select* an MSDOS partition table (in Calamares).

+1
And I do come in peace :)
No wars just facts ;)

---

### Post by guiverc on 2023-12-14
> **MAFoElffen said:**
> 
quiverc -- In that link, I read that as "if there were no partition table" that Calamares leans towards GPT... But to stay like the the other installers, and how I've historically done some of my test-cases to confirm that "as explained a few posts back"... That link does not really differ from what I explained in Post #88, but...--> If you set a partition type and choose "Erase All and Install ___." ...

That the installer should, (in it's rule-based logic)
[LIST]
[*]if it does not see a partition table, choose a partition table type based on the boot mode (prefer GPT). 
[*]if there is a partition table type set, honor the user's choice of partition table type, and use it. 
[/LIST]
There are reasons to honor a User's decision, rather than override it.

If it overrides the decision, then, what was told to me about the other installers, that is considered a bug.

[HR][/HR]
So if not considered currently as a Bug for Lubuntu, in respect to how Calamares does that... based on that reasoning, I believe it should be considered a Bug. Right? Or do you think there is reasoning for overriding that, and taking the ability to do that away?

I personally, I guess as a technical user, would prefer what you  			 				 					[ 						 							 						 					]("https://ubuntuforums.org/member.php?u=1044547") 				 				 					 						 	[**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547") &  				 					[ 						 							 						 					]("https://ubuntuforums.org/member.php?u=346442") 				 				 					 						 	[**[COLOR=#C61919][B]Irihapeti**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=346442") have stated, as if I've made a decision (in the past) I would expect an installer to use it; but I have no problem with it due to the "Erase disk" & its creation of a new partition table with that selection. Here it's maybe because I'm still trying to get myself out of habit of using MBR I've I've used since the 80s, but GPT is really the better alternative in modern hardware.

I tend to accept things if I can see *logic* behind the decision; I do see GPT as better thus had no issue with their preference. When I wanted a MBR partitioned install (*in my QA; I try and pretend I'm an imaginary user and create a system that meets an expected need occasionally*), I've had no issues (*thus far*) in creating one; but if I did, then I'd for sure be filing a bug, and myself working out a workaround should a end-user encounter that issue so they're not waiting.

With calamares, a bug report would mean on launchpad (*for tracking mostly*), then upstream with calamares on github; which is easier given our code on *noble* isn't old. I've rarely done this, but have found them pretty responsive.

FYI:  When it comes to workarounds with partitioning; as end-users are  using installers rather infrequently; I've often suggested users use a  partitioning tool such as *KDE Partition Manager* (or *gparted*) to create their partitioning first; then use the installer to just select where they want things to go (*in their already partitioned system*). At least for me, as I'm using partitioning tools far more regularly (*making changes*) than installs, I've always seen this as less risky; this maybe influencing me here.

---

### Post by MAFoElffen on 2023-12-14
I confirmed it: [https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291705/testcases/1701/results](https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291705/testcases/1701/results)

I filed it: [https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/2046500](https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/2046500)

It  was the right thing to do. Iripetti and sudodus can go up there and  mark that they were affected... So that it's status gets bumped to  confirmed.

I figure maybe it might get sent upstream to let  Calamares figure out if it is something they want to decide on...  Whether as a Bug or as a proposed Enchancement. Or not. Let them decide.

---

### Post by guiverc on 2023-12-14
> **MAFoElffen said:**
> I confirmed it: [https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291705/testcases/1701/results](https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291705/testcases/1701/results)

I filed it: [https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/2046500](https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/2046500)

It  was the right thing to do. Iripetti and sudodus can go up there and  mark that they were affected... So that it's status gets bumped to  confirmed.

I figure maybe it might get sent upstream to let  Calamares figure out if it is something they want to decide on...  Whether as a Bug or as a proposed Enchancement. Or not. Let them decide.

Thank you @**MAFoElffen**, I saw the bug report appear in my inbox; and for reporting on the ISO tracker (*meaning it'll appear on random tests into the future, meaning others may test for it, and I get reminded when I see it!*).

Thanks also to @Iripetti & @sudodus for their testing & reporting... I've not had much time to QA test recently; and I'm very thankful to see others ahead of me in the cycle testing stats.

---

### Post by Irihapeti on 2023-12-14
Thanks for the report. I've added myself as affected, and subscribed.

---

### Post by Irihapeti on 2023-12-14
Would anyone testing the Xubuntu installer be able to confirm [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2045535](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2045535) ?

The title probably isn't the best. It seems that anything writable connected to the USB bus becomes the default and only choice for installing to when using auto-resize. At the time I made the report, I thought it had to be bootable, but it appears now that it needn't be. I've been able to confirm it in a VM, but because it's still just me, Launchpad doesn't consider that a confirmation. I think this bug has a potential to really mess things up badly for someone.

---

### Post by TenPlus1 on 2023-12-15
The one thing that annoys me about the new 24.04 dailys vs 22.04 releases is that the memory use for each desktop has gone right up by 300mb or more, and that's using the same kernel on both just to be sure.  What's using all that extra memory ??

---

### Post by guiverc on 2023-12-15
> **TenPlus1 said:**
> The one thing that annoys me about the new 24.04 dailys vs 22.04 releases is that the memory use for each desktop has gone right up by 300mb or more, and that's using the same kernel on both just to be sure.  What's using all that extra memory ??

[A recent review of a *minimal *Lubuntu 24.04 daily install says the following]("https://debugpointnews.com/lubuntu-24-04-snap/")

> The minimal install only takes 4 GB of disk space, and its lightning fast. It only uses 419 MB of RAM at idle. 

I doubt an *equivalent* Lubuntu 23.10 install was using only 119 MB.

Personally that 419 MB means nothing to me, almost no-one uses their desktop without additional programs, and starting up some services/processes will mean the *idle* RAM is higher, but also that starting apps may also be faster. There are always *pros* and *cons* with anything, and that includes use of RAM.

If a  system I'm using allows me to freely adjust what is started/stopped, and have control over what is running (*which Ubuntu does*) I'm happy.

fyi:  A *minimal* install option is also something that I don't care about.  Myself I find it as easy to uninstall unwanted packages as it is to add those I want; but the world would be boring if we all thought/felt the same.

---

### Post by sudodus on 2023-12-15
> **Irihapeti said:**
> Thanks for the report. I've added myself as affected, and subscribed.
+1

---

### Post by sudodus on 2023-12-15
> **Irihapeti said:**
> Would anyone testing the Xubuntu installer be able to confirm [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2045535](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2045535) ?

The title probably isn't the best. It seems that anything writable connected to the USB bus becomes the default and only choice for installing to when using auto-resize. At the time I made the report, I thought it had to be bootable, but it appears now that it needn't be. I've been able to confirm it in a VM, but because it's still just me, Launchpad doesn't consider that a confirmation. I think this bug has a potential to really mess things up badly for someone.

I cloned the current Xubuntu Noble iso file to a USB connected SSD and booted into my old Toshiba Satellite Pro C850-19W.

- There is an internal SSD with Lubuntu (since yesterday).
- I connected a 32 GB Sandisk Extreme USB pendrive with an MSDOS partition table and an exfat partition.

When booted in BIOS mode, only the internal drive and the pendrive could be selected for booting.

When booted in UEFI mode, I could boot into the USB connected SSD and run Xubuntu Noble liive. At the partitioning menu I selected 'Install alongside' and only the internal drive was possible to select (the pendrive could not be selected).

In other words, I could not reproduce the behaviour that you describe. Please suggest how I should modify the setup of the test to be able to confirm your bug report.

In your test, is your SD card connected via USB or PCI? If via PCI, I must test in another computer.

[hr][/hr]
Edit: In the same Toshiba, in UEFI mode, I replaced the USB pendrive with another one that is bootable with Clonezilla in UEFI mode.

Now there was no option to install alongside, only

- 'Erase Ubuntu Noble' (actually Lubuntu)
- 'Erase disk'
- 'Something Else'

I interrupted the installer before writing anything (I am rather sure about that). Anyway, I repeated booting with the Sandisk Extreme connected and then 'Install alongside' was available again. So I can confirm that Ubiquity is flaky, but I see other symptoms than you.

---

### Post by Irihapeti on 2023-12-15
I need to re-run the tests in UEFI mode to be sure of that, and they are in a QEMU/KVM VM. From memory, it was the same thing. I used a physical USB stick in that instance, because I don't know how to emulate USB things in software.

The original set where I discovered the behaviour was on the Acer travelmate 4740, which is BIOS boot. It has a 500GB SSD in it, and the SD card was connected to the USB bus. I subsequently noted the same behaviour when I inserted a USB stick. The SD card has ext4 file system and the USB sticks have either ext4 or fat32. In all cases, only the external devices were visible for auto-resize installing. (I consider the SD card to be external, even though it sits entirely in the laptop casing when it's attached.) Maybe I should try testing with exfat, seeing as a lot of USB storage comes with that these days.

---

### Post by sudodus on 2023-12-15
@Irihapeti,

Maybe the old computers that you and I are testing have non-standard features in the UEFI-BIOS systems, that cause the different behaviour. Anyway, the Clonezilla drive has an MSDOS partition table and a FAT32 file system, which should match your test with a fat32 pendrive. Maybe the size of the pendrives makes a difference ...

---

### Post by Irihapeti on 2023-12-15
The size doesn't seem to make a difference. A 500GB external SSD connected via USB exhibits the same behaviour.

But I've discovered that if the USB stick is formatted with exfat file system, the xubuntu installer doesn't see it. Which sounds fine, but this particular VM has two internal sata drives, and only one of them is visible/selectable. It almost seems like it's only going to allow one drive to be installed to. :)

As I can replicate this in a VM, I don't think it's just old and weird hardware that's the problem.

---

### Post by Irihapeti on 2023-12-15
Further notes: according to GParted on the xubuntu installer, the install ISO doesn't include exfatprogs, which might explain why the installer isn't "seeing" an exfat USB stick. If I format the USB stick to ntfs, then the installer can "see" it and doesn't allow me to select any other drive.

---

### Post by sudodus on 2023-12-15
Next I tested the current Xubuntu Noble iso file to a USB connected SSD and booted into my old Dell Precision M4800 (with generation 4 Intel i7 and nvidia graphics.

- In BIOS mode it also tries to boot into the USB pendrive, if connected, instead of into the USB SSD with Xubuntu live.

- In UEFI mode,

. when the Clonezilla pendrive connected, it boots into Clonezilla, even if I select to boot into the Xubuntu SSD in the temporary menu. Strange!

. when a USB pendrive with Windows installer is connected, it can boot into Xubuntu. This time there is an option to install alongside, but not into the internal drive, but into the pendrive with Windows installer, seen as /dev/sdc. See the attached screenshot. I did not continue because I did not want to damage anything installed. This is more like what you see, so I can click 'me too' in the bug report.

---

### Post by MAFoElffen on 2023-12-15
@Irihapeti -- 

I tried to recreate it and couldn't on my physical laptop which has an SD card drive... I was thinking may be couldn't because it doesn't see that drive on my laptop in it's BIOS as being a bootable drive?

I took interest, because previously I had tried to do that on purpose to install to SD card on this machine and it wouldn't do it... I figured "how" the BIOS saw that drive was the reason.

You said you also recreated it in Virtual... How did you lay out the machine of that to reproduce that?

---

### Post by lammert-nijhof on 2023-12-15
After more than a month I have given up on Installing Ubuntu 24.04 dev.ed. in a Virtualbox VM. The installation keeps freezing, after I think 90 seconds. 
 I cloned Ubuntu 23.10 VM and upgraded the clone with "do-release-upgrade -d" to Ubuntu 24.04.  The advantage? is, that it runs the Linux kernel 6.5.0.14 instead of 6.5.0.9 :)

---

### Post by Irihapeti on 2023-12-15
> **MAFoElffen said:**
> @Irihapeti -- 

...

You said you also recreated it in Virtual... How did you lay out the machine of that to reproduce that?

The VM is QEMU/KVM UEFI. It currently has two .qcow2 drives attached as sda and sdb, but it exhibits the behaviour regardless of number of internal drives. (I prefer using SATA for testing, as that's what people are likely to use on real machines, unless they are using M.2/NVMe.) For the USB devices, I plug something into the PC and then attach it to the VM as a USB host device.

If you need further details (or tests) let me know.

---

### Post by MAFoElffen on 2023-12-15
@Irihapeti -- You said as USB. Is the Second KVM vdrive setup as USB? Or as SATA or virtio?

@et-all -- On the Calamares Install changing Partition table types on "Erase All". Very timely reactions to, and spurned some very good, seriously taken discussions on it. It actually got mark as "Importance=High".

Final Decision: "Won't Fix." I agree with the reasoning. It is just setup that way on purpose. For that Installer, Interpret "Erase All" literally. If you want other than, as a choice, then use "Other" to get into the Partitioner, and do it manually. That way there is no confusion on how it will turn out.

---

### Post by Irihapeti on 2023-12-15
> **MAFoElffen said:**
> @Irihapeti -- You said as USB. Is the Second KVM vdrive setup as USB? Or as SATA or virtio?



The second KVM drive is SATA. It probably doesn't need to be there at all. It was just something left over from testing another issue. :)

---

### Post by MAFoElffen on 2023-12-15
Okay -- trying it to see what happens here. Might take a while, I have to feed the animals and pick up my wife from baby-sitting the grand-kids.

---

### Post by guiverc on 2023-12-15
If i recall correctly; I mentioned Ubuntu Studio *noble* issues earlier (*with [launchpad bug report link]("https://bugs.launchpad.net/ubuntu/+source/livecd-rootfs/+bug/2046386")*), but it's also written about here - [https://ubuntustudio.org/2023/12/noble-numbat-updates-for-december/](https://ubuntustudio.org/2023/12/noble-numbat-updates-for-december/)

> Right now, **[our daily .iso images boot to a black screen with a mouse cursor.]("http://launchpad.net/bugs/2046386")**  In other words, they do not work. Additionally, you cannot login to a  virtual terminal to diagnose the issue via logs. This is because, upon  extracting the .iso image and included squashfs file, we found out that  the default live user (normally named &#8220;ubuntu-studio&#8221;) is not being  created upon image build.


    We do not expect this issue to be resolved until January.

---

### Post by MAFoElffen on 2023-12-15
I kind of remember that was fairly recent... 2 days ago, Post #92.

Oh Dang! Happy Holidays...

I guess we don't have to worry about that one for a while. LOL.

---

### Post by MAFoElffen on 2023-12-16
Well heck...

I created a KVM VM machine with 2 SATA vDisks and 1 USB vDisk... Used the Noble Xubuntu Daily 20231215 image.

Installed 4 times. 1st said erase, and installed on /dev/sda. 2d said alongside, and chose the next drive with free space, which was /dev/sdb. 3rd install, said alongside, and chose the next device with free space, /dev/sdc. 4th install said alongside, and did not find enough space to freely choose a drive, so presented the drives in the resize panel, asking to resize the partitions on one of the drives...

It worked as expected. I couldn't recreate the error.

One thing I did notice, with the first boot of each, it had me login "twice" on each before continuing to the desktop... On the first time it returned to the second login, where it then would go to the desktop. I noticed that previously, but was a hit in the face with tonights install. Has anyone else seen that with theirs? (Just with Xubuntu. I didn't notice that with Kubuntu.)

---

### Post by Irihapeti on 2023-12-16
I wonder: does it make any difference if the USB is a physical disk instead of a vdisk? At least, that's what I think I was doing, and probably what most people installing would be doing.

However, I'm starting to wonder if I should leave things alone for a while. I seem to be coming up with some rather odd edge cases.

---

### Post by MAFoElffen on 2023-12-16
> **Irihapeti said:**
> 
I seem to be coming up with some rather odd edge cases.
Isn't that what we are here for? To weed through all the weird stuff? LOL

Even if something turns out to be "normal", at least we (hopefully) won't be surprised if it comes up later, asked by a user, where we can explain it. Right?

(Though that still happens.)

---

### Post by sudodus on 2023-12-16
> **MAFoElffen said:**
> [QUOTE=Irihapeti;14169534]
I seem to be coming up with some rather odd edge cases.

Isn't that what we are here for? To weed through all the weird stuff? LOL

Even if something turns out to be "normal", at least we (hopefully) won't be surprised if it comes up later, asked by a user, where we can explain it. Right?

(Though that still happens.)[/QUOTE]

+1 :-)

---

### Post by este.el.paz on 2023-12-16
> **este.el.paz said:**
> :

Thanks for the fast reply . . . well, April isn't that far away . . . .  : - )  I'm OK with Mantic, it seems to be "steadying down" on my machine, today booting it up didn't spin up the GPU to subsonic speeds as it seemed to be doing only last week . . . it's more quiet.

But, then, I do like fresh horsies . . . better part of valor these days seems to be to wait for "alpha" level product . . . too much going on with the multi-boot machine as it is, keeping the various "plates" operational.  Might be a couple of months and then check out the "noble" offering . . . .

et al:

So, had a couple of moments to spare, so I edited my Lubuntu mantic sources which pulled in 1017 packages and on reboot everything seems to be running well.  Noble is running the machine more quietly than Mantic did . . . .

Only thing left to do is check whether my mkusb install needs to move up from "lunar" to something newer . . . ????  : - )  ):P

---

### Post by sudodus on 2023-12-16
@este.el.paz,

There is am PPA set for **[FONT=Courier New]mkusb[/FONT]** in Noble. It worked when I tested it. Please let me know if there is any problem.

I know that **[FONT=Courier New]dus-persistent[/FONT]** has problems with secure boot in some new computers (because of old versions of grub), but you should be able to make persistent live Ubuntu (and Ubuntu flavour) systems with **[FONT=Courier New]dus-iso2usb[/FONT]** and with **[FONT=Courier New]mkusb-plug[/FONT]**. Otherwise **[FONT=Courier New]mkusb[/FONT]** should work as before also with Noble.

---

### Post by este.el.paz on 2023-12-16
> **sudodus said:**
> @este.el.paz,

There is am PPA set for **[FONT=Courier New]mkusb[/FONT]** in Noble. It worked when I tested it. Please let me know if there is any problem.

I know that **[FONT=Courier New]dus-persistent[/FONT]** has problems with secure boot in some new computers (because of old versions of grub), but you should be able to make persistent live Ubuntu (and Ubuntu flavour) systems with **[FONT=Courier New]dus-iso2usb[/FONT]** and with **[FONT=Courier New]mkusb-plug[/FONT]**. Otherwise **[FONT=Courier New]mkusb[/FONT]** should work as before also with Noble.

@sudodus:

Thanks for the reply . . . I do have mkusb installed in my now Noble edition of Lubuntu, but seems like it isn't included in the /etc/apt/sources.list  data, and is kept in "other software" in the GUI "sources and xxx" . . . where there is both "unstable" and what?  "stable" editions listed . . . .

I didn't know if I could edit those in the GUI to be "noble" . . . it seems like I could, so at somepoint I'll get to it.

@guiverc:

Tried to reply to your post back on the Lubuntu forum yesterday about noble, in Debian and today in Lubuntu, forum would not load the forum page, it showed the proper link, but only see the three dots.  I then tried to reply by email and this morning that bounced back.  So my troubles with the Lubunut Discourse forum . . . continue.

---

### Post by sudodus on 2023-12-17
@este.el.paz,

After installing mkusb
```

sudo add-apt-repository ppa:mkusb/unstable
sudo apt install mkusb

```
the following grep command should show something like
```

$ grep -H mkusb /etc/apt/sources.list.d/*
/etc/apt/sources.list.d/mkusb-ubuntu-unstable-noble.sources:URIs: https://ppa.launchpadcontent.net/mkusb/unstable/ubuntu/

```

---

### Post by guiverc on 2023-12-17
> **este.el.paz said:**
> 
@guiverc:

Tried to reply to your post back on the Lubuntu forum yesterday about noble, in Debian and today in Lubuntu, forum would not load the forum page, it showed the proper link, but only see the three dots.  I then tried to reply by email and this morning that bounced back.  So my troubles with the Lubunut Discourse forum . . . continue.


I can access [Lubuntu discourse] here on this box without issue, and connected earlier tonight from my Debian box too (I did experience an issue like what you describe on initial starting of firefox; but a refresh had it connect correctly thus I didn't worry about it). I'm not aware of any [reported] issues in the last ~24 hours, but I fear if the time the site was up over the last month or two was calculated, that would not be an impressive value/% 

I'll suggest you re-try [accessing Lubuntu discourse], and if you're unable to access it please tell me (again). If you use IRC, I can be found in Lubuntu, Ubuntu News & man other rooms most of my local (AEST or aussie east cost) daylight hours, but sending to me anytime will reach me thru matrix/telegram (even if I'm not using IRC). Reporting issues about Lubuntu sites is best done on IRC/matrix/telegram

---

### Post by MAFoElffen on 2023-12-17
+1 with guiverc --

I was reading it yesterday and was having no problems bringing things up that I was looking for there.

---

### Post by este.el.paz on 2023-12-17
@sudodus:

It's installed, been so for years . . . just seems to be from "lunar" . . . . 

@et al:

Well the part about "noble being more quiet than mantic . . ." . . . no longer applies, also seems to be spinning the gpu up quite a bit for routine web browsing . . . .  Otherwise, all is fine in the Noble Numbat system.

---

### Post by MAFoElffen on 2023-12-17
Dang. Downloaded the Ubuntu current twice already. Bit fial on KVM w/QXL. On normal boot it fails at bringing up the "try/instal" panel (stays blank white). On safe graphics is stays at a black screen. On bringing it up with init mode 3, it never fully boots the kernel, so stays at a black screen...

Found that while trying to do this: [https://ubuntuforums.org/showthread.php?t=2492697&p=14169763#post14169763](https://ubuntuforums.org/showthread.php?t=2492697&p=14169763#post14169763)

Anyone else have luck with that with a different machine type?

Going to try the pending image (versus the current)...

EDIT: Get the same on the pending image.

Going to boot off my last downloaded successful image to report that.

RE: [https://bugs.launchpad.net/subiquity/+bug/2046663](https://bugs.launchpad.net/subiquity/+bug/2046663)

Dang. May be a duplicate of this earlier: [https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2043915](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2043915)

I connected the dots between those.

---

### Post by MAFoElffen on 2023-12-18
Noble Ubuntu Desktop ISO still broken for me today.

---

### Post by MAFoElffen on 2023-12-18
Success with Testing the daily Noble WSL image, and the Ubuntu Base image.

---

### Post by guiverc on 2023-12-18
Ubuntu Studio ISOs I gather are working again, Erich posted this

[https://mastodon.art/@ubuntustudio/111602837659994703](https://mastodon.art/@ubuntustudio/111602837659994703)

> Our Noble Numbat daily images are working again, but our installer is  not. As it is early days, this is expected. Rest assured, this will get  remedied in January.

The update on [URL="https://ubuntustudio.org/2023/12/noble-numbat-updates-for-december/"]Ubuntu Studio's blog is better

[/URL]> **UPDATE: **The boot issues have been fixed, however,  the installer frontend is not yet working. This is true for Ubuntu  Desktop Noble Numbat as well. If you wish to test the installation, it  must be tested with subiquity. This can be done with:
    sudo snap install subiquity --classic
sudo subiquity    However, the live .iso image is now functioning.
[URL="https://ubuntustudio.org/2023/12/noble-numbat-updates-for-december/"]
 
and do note it may look different, Erich added on IRC

> That command starts the installer in a text mode, fwiw.
[/URL]

---

### Post by Irihapeti on 2023-12-18
I have a couple of arm64 devices floating around; I can use those for testing Ubuntu Base arm64.

I might be able to do something about armhf, but it could take a day or two.

---

### Post by Irihapeti on 2023-12-19
Successful testing of Ubuntu Base arm64 and armhf

---

### Post by MAFoElffen on 2023-12-21
I'm quoting him here to bring it together:

From RE:[https://ubuntuforums.org/showthread.php?t=2492697&p=14170455#post14170455](https://ubuntuforums.org/showthread.php?t=2492697&p=14170455#post14170455)
> **corradoventu said:**
> My last successful install was with ISO dated 2023-12-10 
[https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291424/testcases/1743/results](https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291424/testcases/1743/results)
[https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291424/testcases/1761/results](https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/291424/testcases/1761/results)
After this installer starts with a blank empty window 
[https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2043915](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2043915)
When is a working ISO expected? Please post a message HERE so I can resume testing.
Thank you
That is a good question that I am wondering also. I don't understand how (for Ubuntu & Budgie) that all went backwards from a working Installer ISO (with very few errors), to bad, to much worse.

---

### Post by Irihapeti on 2023-12-21
I thought I try running a riscv64 server in a VM and test the base package in that.

Ummm... no. It takes my machine something like 12-15 mins to generate an initramfs in an emulated architecture. Maybe someone else has a risc board lying around. I gather they do exist.

---

### Post by MAFoElffen on 2023-12-22
> **Irihapeti said:**
> I thought I try running a riscv64 server in a VM and test the base package in that.

Ummm... no. It takes my machine something like 12-15 mins to generate an initramfs in an emulated architecture. Maybe someone else has a risc board lying around. I gather they do exist.
I just update one of my KVM RISCV64 test-cases to check that: 125 updates in less than 7 minutes. Hmmm.

I give it about 4GB RAM and 8vcpu's, on a 16GB vdisk...

---

### Post by MAFoElffen on 2023-12-23
Dang. Ubuntu Desktop still broken. I really don't expect any changes with that now, until probably after the holidays.

---

### Post by Irihapeti on 2023-12-23
> **MAFoElffen said:**
> Dang. Ubuntu Desktop still broken. I really don't expect any changes with that now, until probably after the holidays.

Probably right. And thanks for the heads-up — I won't waste any time trying to test Budgie or Edubuntu, either.

I did run a test on Cinnamon and...  holy smokes! ... I managed to do an install with NO BUGs or other fiddly little errors.

(Yes, Xubuntu installs OK, but there's always that odd shutdown behaviour. And my peculiar auto-resize bug was still there last time I looked.)

---

### Post by corradoventu on 2023-12-24
ubuntu-desktop-installer is the negation of the concept of snap which should contain all the necessary components so should be independent from environment.
Versions 1276 and 1278 worked with the ISO until December 10th, then the environment changed and the installer no longer works.

---

### Post by MAFoElffen on 2023-12-24
I don't expect anything to change until after the holidays. (Unless some Elves do some magic.)

Happy Holidays one and all!

---

### Post by Irihapeti on 2023-12-24
> **MAFoElffen said:**
> .....Happy Holidays one and all!

And to you, too.

---

### Post by corradoventu on 2023-12-25
Happy Holidays to everyone and best wishes for a speedy recovery to ubuntu-desktop-installer

---

### Post by Irihapeti on 2023-12-25
> **corradoventu said:**
> ... and best wishes for a speedy recovery to ubuntu-desktop-installer

:lol:

---

### Post by guiverc on 2023-12-25
> **corradoventu said:**
> Happy Holidays to everyone and best wishes for a speedy recovery to ubuntu-desktop-installer

:P  & Merry Christmas all.

---

### Post by kc1di on 2023-12-25
Merry Christmas!

---

### Post by MAFoElffen on 2023-12-25
Today's Ubuntu Daily still fails...

But I can open a terminal, kill the installer, and use the desktop in the Live Environment just fine. The system is stable, just not the installer.

---

### Post by guiverc on 2023-12-26
Just FYI:  But Lubuntu *noble* daily has an issue that (may) require you to hit ALT+TAB to have it fully operational  :(

[https://bugs.launchpad.net/ubuntu/+source/lubuntu-installer-prompt/+bug/2047379](https://bugs.launchpad.net/ubuntu/+source/lubuntu-installer-prompt/+bug/2047379)

*and (belated) Merry Christmas all.*

---

### Post by Irihapeti on 2023-12-26
> **guiverc said:**
> Just FYI:  But Lubuntu *noble* daily has an issue that (may) require you to hit ALT+TAB to have it fully operational  :(

[https://bugs.launchpad.net/ubuntu/+source/lubuntu-installer-prompt/+bug/2047379](https://bugs.launchpad.net/ubuntu/+source/lubuntu-installer-prompt/+bug/2047379)

*and (belated) Merry Christmas all.*

Sorry, I have to say that I'm not encountering it on a EFI VM.

I'll see what my dungy old Acer Travelmate has to say about it. :)

---

### Post by guiverc on 2023-12-26
> **Irihapeti said:**
> Sorry, I have to say that I'm not encountering it on a EFI VM.

I'll see what my dungy old Acer Travelmate has to say about it. :)

Thanks for testing @Irihapeti

On my first two boxes I experienced [https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/2013074;](https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/2013074;) both having two displays

Next two boots were on different boxes using only a single display; the issue was not experienced.. so I commented on bug report it appears to occur only when two screens are connected :P

Alas fifth box I booted/test on has two screens & did not experience an issue :o .. so its more involved than number of screens...

I'm doing a *QA test install* on box; so my thumb-drive is *busy* for now, but I'll try booting on a few more boxes in hopes of finding a pattern (*since it's not screen count*).

---

### Post by Irihapeti on 2023-12-26
Install was successful on the old laptop as well.

---

### Post by MAFoElffen on 2023-12-27
Ubuntu daily ISO fails still at the white-screen of the try-install panel. I found a dependable way to kill the installer at that point. <Alt><F2> > gnome-terminal
```

sudo su -
ps aux | grep -e 'snap/ubuntu' | grep -v grep | awk '{print $2}' | xargs kill -15

```
Funny thing about finding those PID's... ubuntu_desktop_installer --try-or-install is loaded twice(?)... Hmmm. So that kills both instances of the PID's for me to test the Live Env.

---

### Post by Irihapeti on 2023-12-28
I'm still seeing that strange bug with Xubuntu auto-resize wanting to install to removable storage [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2045535](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2045535)

After doing some more tests, my tentative conclusion is that it depends on the file system(s) on the removable device. They have to be something that the partitioner can resize. That seems to rule out exfat (the most common), possibly xfs, and some unusual ones that probably aren't used much. I almost entirely use the ext* or fat* systems, which might be why I see the behaviour all the time. The installer doesn't include exfatprogs, so an exfat storage device doesn't register as an install candidate.

I think that what we can definitely conclude is this: if you (one) are doing an auto-resize, make sure that you don't have any other storage devices attached. This is probably good advice anyway.

---

### Post by sudodus on 2023-12-28
> **Irihapeti said:**
> if you (one) are doing an auto-resize, make sure that you don't have any other storage devices attached. This is probably good advice anyway.

+1

---

### Post by corradoventu on 2023-12-28
> **MAFoElffen said:**
> Ubuntu daily ISO fails still at the white-screen of the try-install panel. I found a dependable way to kill the installer at that point. <Alt><F2> > gnome-terminal
```

sudo su -
ps aux | grep -e 'snap/ubuntu' | grep -v grep | awk '{print $2}' | xargs kill -15

```
Funny thing about finding those PID's... ubuntu-desktop-installer --try-or-install is loaded twice(?)... Hmmm. So that kills both instances of the PID's for me to test the Live Env.

I just use System Monitor to kill the installer.

---

### Post by sudodus on 2023-12-28
[SIZE=4]Lubuntu (Mantic and) Noble problems with 2 screens connected[/SIZE]

There are two bug reports about problems to use two screens with Lubuntu. In a 10-11 years old Toshiba also Kubuntu Noble has problems.

Live: [bugs.launchpad.net/ubuntu/+source/lubuntu-installer-prompt/+bug/2047379](https://bugs.launchpad.net/ubuntu/+source/lubuntu-installer-prompt/+bug/2047379) - already confirmed
[s]Installed: [bugs.launchpad.net/ubuntu/+source/lxqt-session/+bug/2047456](https://bugs.launchpad.net/ubuntu/+source/lxqt-session/+bug/2047456) - needs confirmation[/s]

If you have time and suitable hardware, please test for example in an old laptop with an external screen connected, and let us know if you are also affected by these bugs.

[HR][/HR]
Edit: I no longer think the problems described in the bug report  #2047456 can be blamed on any component of any Ubuntu flavour.

---

### Post by #&amp;thj^% on 2023-12-31
Well there is no link for a RPI4 yet, but it works with sed to noble approach.
```
System:
  Kernel: 6.5.0-1005-raspi arch: aarch64 bits: 64 Desktop: MATE v: 1.26.2
    Distro: Ubuntu 24.04 (Noble Numbat)
Machine:
  Type: ARM System: Raspberry Pi 4 Model B Rev 1.1 details: BCM2835 rev: c03111
    serial: <filter>
CPU:
  Info: quad core model: N/A variant: cortex-a72 bits: 64 type: MCP cache:
    L2: 1024 KiB
  Speed (MHz): avg: 600 min/max: 600/1500 cores: 1: 600 2: 600 3: 600 4: 600
Graphics:
  Device-1: bcm2711-hdmi0 driver: vc4_hdmi v: N/A
  Device-2: bcm2711-hdmi1 driver: vc4_hdmi v: N/A
  Device-3: bcm2711-vc5 driver: vc4_drm v: N/A
  Display: x11 server: X.Org v: 1.21.1.10 driver: X: loaded: modesetting
    unloaded: fbdev dri: vc4
    gpu: vc4-drm,vc4_crtc,vc4_dpi,vc4_dsi,vc4_firmware_kms,vc4_hdmi,vc4_hvs,vc4_txp,vc4_v3d,vc4_vec
    resolution: 1920x1080~60Hz
  API: EGL v: 1.4,1.5 drivers: swrast,v3d,vc4
    platforms: gbm,x11,surfaceless,device
  API: OpenGL v: 4.5 compat-v: 3.1 vendor: broadcom mesa v: 23.3.0-2ubuntu3
    renderer: V3D 4.2
Audio:
  Device-1: bcm2711-hdmi0 driver: vc4_hdmi
  Device-2: bcm2711-hdmi1 driver: vc4_hdmi
  API: ALSA v: k6.5.0-1005-raspi status: kernel-api
  Server-1: PulseAudio v: 16.1 status: active
Network:
  Device-1: bcm2835-mmc driver: mmc_bcm2835
  IF: wlan0 state: down mac: <filter>
  Device-2: bcm2711-genet-v5 driver: bcmgenet
  IF: eth0 state: up speed: 1000 Mbps duplex: full mac: <filter>
  IF-ID-1: tun0 state: unknown speed: 10000 Mbps duplex: full mac: N/A
Bluetooth:
  Device-1: pl011 driver: uart_pl011
  Report: hciconfig ID: hci0 state: up address: <filter> bt-v: 5.0
  Device-2: pl011 driver: N/A
Drives:
  Local Storage: total: 3.75 TiB used: 3.58 TiB (95.4%)
  ID-1: /dev/mmcblk0 model: SC128 size: 119.08 GiB
  ID-2: /dev/sda vendor: Western Digital model: WD40NDZW-11MR8S0
    size: 3.64 TiB type: USB
Partition:
  ID-1: / size: 116.89 GiB used: 10.27 GiB (8.8%) fs: ext4 dev: /dev/mmcblk0p2
Swap:
  ID-1: swap-1 type: file size: 1024 MiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 45.8 C mobo: N/A
  Fan Speeds (rpm): N/A
Info:
  Processes: 234 Uptime: 4m Memory: total: N/A available: 3.7 GiB
  used: 873.6 MiB (23.0%) Shell: Bash inxi: 3.3.31

```

---

### Post by ajgreeny on 2024-01-02
I've been looking at Kubuntu-24.04 after many years of Xubuntu and was trying unsuccessfully to find **muon-package-manager**.
Has this now been abandoned and replaced by discover?

I generally use terminal for everything to do with package management but occasionally find a GUI is a useful search tool.
I still occasionally use synaptic in Xubuntu but it's a gtk application so in Kubuntu pulls in a lot of libraries etc, which I'd prefer not to have to do.

---

### Post by Irihapeti on 2024-01-02
That funny bug with auto-resize on Xubuntu (and Kubuntu as well) [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2045535](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2045535) reared its head on a VM with two SATA disks. Would only allow installation to /dev/sdb but installed the EFI stuff to /dev/sda with no indication that it was going to do so.

I think we need to tell people NOT to use auto-resize on either of these flavours unless they have a very basic setup i.e. one disk with one or maybe two OS on it. Otherwise, there's too much potential for a mess.

---

### Post by Frogs Hair on 2024-01-02
> **ajgreeny said:**
> I've been looking at Kubuntu-24.04 after many years of Xubuntu and was trying unsuccessfully to find **muon-package-manager**.
Has this now been abandoned and replaced by discover?

I generally use terminal for everything to do with package management but occasionally find a GUI is a useful search tool.
I still occasionally use synaptic in Xubuntu but it's a gtk application so in Kubuntu pulls in a lot of libraries etc, which I'd prefer not to have to do.

Muon is no longer maintained or released.

---

### Post by ajgreeny on 2024-01-03
Thanks.
It's such a long time since I tried any distro with KDE that I'm totally out of touch with them.
However, it's back to Xubuntu tor me I think as I havent got the time (or the patience) to investigate how to use KDE in the detail i need to satisfy myself.

---

### Post by MAFoElffen on 2024-01-03
@ajgreeny -- LOL. I had previously just stayed with a few flavors...

I have to admit... The Doctors will not let me back to work still. To keep myself from going stir crazy, I have tried to keep myself busy trying new things and re-exploring other flavors(, that I usually would not do).

I keep coming up with crazy things to see if I can make something, usually not normally done, working. Or staying with upstream problems (Intel Advanced Graphics issues), which I would have previously, normally just let go of. 

I've worked with 2 Engineer Graphics Support Teams from Intel for 4 months (so far) trying to get one of their driver packages working. It started when Ubuntu HWE went to the 6.2 kernel series as their LTS in 22.04.3... This Intel Support Case has been an extreme (forced) practice in patience and public relations. We thought it worked (momentarily) last week, but then I found it broke 'something else' as a side-affect. I told them I want it working to test with Noble, (with 6.5 series kernels) before it gets released. I just got one of their Senior Engineers to step in to help...

I have to say, "we are spoiled" with having Launchpad.

---

### Post by ajgreeny on 2024-01-03
Yes, I agree with you about Launchpad, and I sometimes wish I had more time to look at other problems in the Development Versions.

Isn't it amazing how "comfortable" we become using an OS or perhaps just a DE with which we are very familiar and then get completely mystified when trying something new.
That's certainly how I feel trying to use KDE, and even more so the few times a year that I now have to use Windows-10 (never yet had to try Windows-11); I probably feel exactly like many users who are trying to use Linux for the first time and expect it to be another version of Windows!

That, of course is just not the way things work!

---

