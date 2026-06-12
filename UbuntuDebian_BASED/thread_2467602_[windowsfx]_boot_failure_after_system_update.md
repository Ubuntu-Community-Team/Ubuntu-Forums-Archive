---
title: "[windowsfx] boot failure after system update"
date: 2021-10-01
forum: Ubuntu/Debian BASED
---

### Post by kaolincash on 2021-10-01
Hi,

I just had standard updates and now windowsfx ([an ubuntu distro]("https://www.windowsfx.org/")) won't boot, it hangs at the loading initial ramdisk part and I'm not sure why the boot-repair-disk boot repair tool isn't working.
Here's the pastebin link it gave me, I hope this is the right place (I followed a link from [here]("https://help.ubuntu.com/community/Boot-Repair") to [here]("https://ubuntuforums.org/showthread.php?t=1769482&page=235&p=13359459#post13359459") to here):
[http://paste.ubuntu.com/p/gz8Xkd2ynY/](http://paste.ubuntu.com/p/gz8Xkd2ynY/)

My main partition is sda2, for clarity, I'm not sure how clear or relevant that is, as I'm very out of my depth here.

Thanks for any assistance,
Maia

edit: gonna put any further pertinent information from later posts here, in the interest of clarity:

p1:
Also, there's only one OS here, I'm not dual booting: I'm in the process of migrating data FROM windows TO windowsfx, as I've decided to jump ship and this seemed an accessible-ish step for me.

What appears to be a windows drive is a copy of the windows install I had on THIS SSD, which I cloned to an HDD partition while I set up my main OS back over here on my SSD, and as I said this was working perfectly fine, fresh out the box so to speak, after a clean install directly to the SSD. That is, until this round of updates did something weird to the boot files, from what i can gather.

I followed the instructions I was given when I googled around and found the boot-repair-disk utility seemed to be the best option, and I already had it on my medicat drive, so gave it a go.

Now I'm in completely over my head and I'm afraid I need complete newbie level advice here. I am a brand new linux user.

sda2 is where my main OS is, from what I can tell, which is windowsfx, and I intend to use this machine to boot directly into windowsfx, and did have the boot manager hidden entirely until all of this suddenly started happening after those updates. Now I don't know WHAT'S going on.

p2: 
I am and have always been booting in UEFI mode. My BIOS settings have remained unchanged since well before the round of updates that caused Windowsfx to begin hanging at "loading initial ramdisk".

I proceeded to plug in my ventoy-based wd passport that runs Jayro's Medicat USB recovery drive and through that booted into boot-repair-disk and ran the boot repair tool provided, on its recommended settings. You may be seeing that in there somewhere, as it's what I was running to generate the program output you see above.

After this failed, said output led me here with the pastebin link in hand, and that's all that's happened thus far.

I am still able to access the grub menu, I can select the correct operating system, and it just hangs seemingly indefinitely (I don't have the money for the electricity meter to keep my gaming rig on for 24 hours, waiting to see if it does anything, but if it takes more than a half hour--which it does--then something's deeply wrong regardless of how long I'm prepared to wait).

---

### Post by deadflowr on 2021-10-01
*Thread move to **Ubuntu/Debian BASED***

---

### Post by grahammechanical on 2021-10-01
Here is the clue:

> LegacyWindows detected. The boot of your PC is in EFI mode. You may want to retry after changing it to BIOS-compatibility/CSM/Legacy mode.

Both operating systems must be in the same boot mode. Either, EFI mode or BIOS-compatibility/CSM/Legacy mode. Also the Windows 8 boot loader will not give you an option to load an Linux OS. Whereas, the Linux boot loader (Grub) will give options to load both Microsoft Windows and Linux operating systems. Which is why if you accept Boot Repairs offer to reinstall Grub2 you should do this:

> Please do not forget to make your BIOS boot on sda (ATA Samsung SSD 850) disk!

Oh, by the way, WindowsFX is built on Ubuntu software but is not officially recognised as a Ubuntu flavour. In fact it takes a lot from Kubuntu.

Regards

---

### Post by kaolincash on 2021-10-01
I'm afraid this is completely over my head, I'm fresh out of windows, and this was all working fine a few hours ago.

Also, there's only one OS here, I'm not dual booting: I'm in the process of migrating data FROM windows TO windowsfx, as I've decided to jump ship and this seemed an accessible-ish step for me.

What appears to be a windows drive is a copy of the windows install I had on THIS SSD, which I cloned to an HDD partition while I set up my main OS back over here on my SSD, and as I said this was working perfectly fine, fresh out the box so to speak, after a clean install directly to the SSD. That is, until this round of updates did something weird to the boot files, from what i can gather.

I followed the instructions I was given when I googled around and found the boot-repair-disk utility seemed to be the best option, and I already had it on my medicat drive, so gave it a go.

Now I'm in completely over my head and I'm afraid I need complete newbie level advice here. I am a brand new linux user.

sda2 is where my main OS is, from what I can tell, which is windowsfx, and I intend to use this machine to boot directly into windowsfx, and did have the boot manager hidden entirely until all of this suddenly started happening after those updates. Now I don't know WHAT'S going on.

---

### Post by oldfred on 2021-10-01
Are you booting in UEFI mode.
You have old grub entries in MBR of both sda & sdb, but they will not work.

The UEFI entry looks like it is using ESP on sda1, grub in ESP boots to sda2.
And fstab is loading /, swap & tmpfs which looks correct.

Do you get grub menu? 
With one install, you may have to press escape (UEFI only) to get grub menu.
Then can you boot recovery mode or second line in grub menu?

---

### Post by kaolincash on 2021-10-02
I am and have always been booting in UEFI mode. My BIOS settings have remained unchanged since well before the round of updates that caused Windowsfx to begin hanging at "loading initial ramdisk".

I proceeded to plug in my ventoy-based wd passport that runs Jayro's Medicat USB recovery drive and through that booted into boot-repair-disk and ran the boot repair tool provided, on its recommended settings. You may be seeing that in there somewhere, as it's what I was running to generate the program output you see above.

After this failed, said output led me here with the pastebin link in hand, and that's all that's happened thus far.

I am still able to access the grub menu, I can select the correct operating system, and it just hangs seemingly indefinitely (I don't have the money for the electricity meter to keep my gaming rig on for 24 hours, waiting to see if it does anything, but if it takes more than a half hour--which it does--then something's deeply wrong regardless of how long I'm prepared to wait).

---

### Post by oldfred on 2021-10-02
Recovery mode uses nomodeset for video issues, and shows boot process.
That may show an issue. In old days the posting was slow enough you could easily follow it. Now it is a lot quicker.

Any issues are also in logs that are same file(s) you see when booting with recovery mode. 
I prefer to always see boot process, so change a grub setting to use noplymouth as default. 

Review log files
sudo egrep -i 'warn|error' /var/log/*g
If not mounted from inside your install, you have to modify /var/log to where you mount it with live installer.

---

### Post by kaolincash on 2021-10-03
Please be patient with me. I have essentially no foundational knowledge here, as this is my Baby's First Linux &#128517;

What does "Recovery mode uses nomodeset for video issues" mean? And I assume this "boot process" you mention is the console output of the OS as it attempts to boot? I haven't heard this referred to as a posting before, so that took me a while to figure out.

I'm also struggling to follow most of the implicit references you're making; How does one "change grub settings"? 

I'm entirely new to this, coming straight from windows, so I don't know what "noplymouth" is, and when you say "If not mounted from inside your install," do you mean if sda2 isn't mounted? From within sda2? I'm completely baffled by this part, I'm afraid!

I also don't know what files you're referring to when you say booting from recovery mode, as for where to input your egrep command, I'm assuming you mean in the recovery mode's console? 

Finally, I'm not sure what you mean by "live installer"--do you mean the iso I booted from in order to install Windowsfx in the first place?

I apologise for taking so long between updates, it's taking me this long to process each of the responses!

---

### Post by oldfred on 2021-10-03
Live installer is the ISO converted to DVD or flash drive to be bootable.
It has two modes as either installer or live system which you can use to test that it works on your system. You also should keep it (and a Windows recovery/repair flash drive) so you can boot system if issues and make repairs.

I was getting into weeds of details, that probably you do not even need to know at this point.

Recovery mode is the second line in grub menu, and may be under a sub menu. It has different settings to avoid video issue (if that is the issue) and boots to a command line and a simple menu of options to make repairs from the terminal or continue to boot. 
Ubuntu installer now has a safe boot mode to avoid some of the old video issues. In the past particularly with nvidia, we had to add nomodeset boot parameter to boot. 

If you get grub menu, then boot using recovery mode.

Your sda2 is your ESP - efi system partition. That is where UEFI has its initial boot files, both Windows & Ubuntu put boot loaders into the ESP. It must be FAT32 formatted and flagged as ESP for UEFI to find it. Windows also requires drives to be gpt partitioned for UEFI boot. The older MBR(msdos) partitioning is used for BIOS boot, even if a new UEFI hardware system. Systems have been UEFI/gpt since 2012 when Microsoft required vendors to install Windows 8 in UEFI mode. Vendors still often call it BIOS, as that is what they think users understand. Users can install in BIOS mode, but that really was available for pre-2012 systems. How you boot install media for both Windows & Ubuntu is then how it installs or repairs.

When you boot your system, you have standard paths for files.
But if you boot a live installer & mount one of those standard files, it will have a different  path.
Default mount is often /media/$USER where user is the signed on administrator. 
Or you can specify mount.

Normal boot with one system or only one system found will not show grub menu.
At that point we do not know if grub/booting is issue or if grub has booted and it is further in the boot process.
And if only one system found, you can force grub menu to appear by using escape key, just after the UEFI/BIOS screen showing vendor's icon. If old BIOS install, you use shift key, not escape key.

---

### Post by kaolincash on 2021-10-04
Okay. Thanks for explaining all that, I think I managed to follow it &#128517;

So, what exactly do I.... do?

---

### Post by oldfred on 2021-10-04
Can you boot recovery mode, second line in grub menu?

---

### Post by kaolincash on 2021-10-04
It seems to just be hanging on a blank screen, which is what the main install seems to be doing too, not sure if that's a consequence of having run the boot repair tool unsuccessfully.

Here are the [options I see]("https://cdn.discordapp.com/attachments/770612605025779742/894594808306335754/20211004_153537.jpg"), and here are the [options given to me when selecting advanced options]("https://cdn.discordapp.com/attachments/770612605025779742/894594809472356402/20211004_153604.jpg").

---

### Post by oldfred on 2021-10-04
And if you click on recovery mode what happens?
Try first, and even try other recovery mode kernels as they are your older install's versions.
Ubuntu normally keeps two kernels, one older one in case of issues with newer one.

---

### Post by kaolincash on 2021-10-04
The first recovery mode is blank, the second opens EFI Shell version 2.31 [4.655]

---

### Post by oldfred on 2021-10-04
That is a bit unusual.
Not all systems have EFI Shell and I have not used it.
Did you also try booting with older kernel?

Also use e for edit on grub menu and your entry and change linux line.
Remove quiet splash boot parameters and see what happens. It should show boot process. And when it stops it usually has an error several lilnes above that point.

---

### Post by kaolincash on 2021-10-04
Ok, so I'm not sure what I did, but I managed to get into the latest recovery, so I followed your instructions and it managed to get as far as this before hanging: [https://media.discordapp.net/attachments/770612605025779742/894693249078394920/20211004_220205.jpg](https://media.discordapp.net/attachments/770612605025779742/894693249078394920/20211004_220205.jpg)

So I ran the command on the failed task and this is the output from that: 
[https://media.discordapp.net/attachments/770612605025779742/894693650481696828/20211004_221252.jpg](https://media.discordapp.net/attachments/770612605025779742/894693650481696828/20211004_221252.jpg)

Edit: I ran a boot update and now it's downloading packages, since I asked it to fix any broken ones, hopefully it should boot after this, at which point I'll mark this solved. Gonna stick on an episode of Columbo and call it a night, for now, though.

---

### Post by oldfred on 2021-10-04
Is this a virtual install?
I do not know about that but error seems related to lxc. 
Someone else may know more about that.

---

### Post by kaolincash on 2021-10-05
Bare metal. Windowsfx installed directly to my SSD. I've attempted to boot normally and it doesn't, but I *can* now access the recovery options of the most recent install, so that's progress. I also managed to boot into the GUI after running through the recovery menu, but at that point it fully disabled all USB interfaces and I don't have a PS/2 keyboard/mouse so I'm not sure where to go from there if I can't physically interface with the device, other than getting SSH set up which--while I'm comfortable enough using SSH as an interface--I'd need to be talked through the process step by step. I don't know if it's even enabled, nor how I might achieve this, but I do have both my laptop and phone, which can interface with my desktop motherboard easily enough (I use WOL, for one thing).

I've done a once-over of my UEFI settings, in the mean time, and ensured I haven't inadvertently messed up anything in my boot order or hardware settings somehow, but nothing changes whether I have the default profile or my custom one enabled, and my custom profile's UEFI settings match the default ones.

So, the current board state appears to be:
- I cannot boot into the GUI at all via normal means and [this is the console output of the main boot sequence]("https://media.discordapp.net/attachments/770612605025779742/894693249078394920/20211004_220205.jpg")
- I can boot into the GUI via recovery mode, but apparently with USB disabled (and potentially other drivers/functionality missing, possibly including networking)
- I can access the grub console via ESC on boot
- I can access the root console via recovery mode.
- I can boot into a recovery drive with either Windows PE or Ubuntu and access the unmounted filesystem itself, with [an arsenal of useful tools]("https://gbatemp.net/threads/medicat-usb-by-jayro.572452/"), in case I need to do any surgery

---

### Post by oldfred on 2021-10-05
Do not know what changes Windows fx may have made to standard Ubuntu.
You may want to see what boot parameter(s) are used with recovery mode. Ubuntu uses nomodeset which defaults video driver to prevent video issues primarily with nVidia until nVidia driver installed. Did not think that changes USB settings. 
USB settings could also be an UEFI setting. If Secure boot is on, you may have to turn on full USB support or similar setting in UEFI.

I did find lxc is related to Windows container for Linux. But no idea how that is used?

---

### Post by kaolincash on 2021-10-05
Secure boot is disabled, as are any Fast Boot settings that may disable USB peripherals.

Here are the boot parameters of my install:
[https://media.discordapp.net/attachments/770612605025779742/895047524157644800/20211005_213805.jpg](https://media.discordapp.net/attachments/770612605025779742/895047524157644800/20211005_213805.jpg)

---

### Post by oldfred on 2021-10-05
My Asus motherboard has a totally separate setting for USB ports, I have to enable full support to have them work whether Secure Boot on or off.

---

### Post by kaolincash on 2021-10-06
At any rate, I'm at a loss; what should I do now?

---

### Post by QIII on 2021-10-06
I am downloading a copy right now.  I'll use a VM to test, so not bare metal, but perhaps I can fiddle around and see if I can find some answers for you.  I won't get done right away, since I only have time to goof off on the forums during the day when I am taking a break from making a paycheck or waiting for a test to run or such things.

---

### Post by tea for one on 2021-10-06
> **kaolincash said:**
> The first recovery mode is blank, the second opens EFI Shell version 2.31 [4.655]

Is your EFI shell similar to attached image?

Can you see entries such as FS0: or FS1: ?

---

### Post by kaolincash on 2021-10-10
If you'll all bear with me for a little while, some stuff has come up IRL and while this is still unresolved, I have not abandoned the thread--I will return and continue this by replying to the relevant responses, I just wanted to leave this message here for any mods who may think I've vanished leaving the thread unsolved.

Rest assured, I will keep this fully updated throughout the resolution procedure--whatever that ends up looking like--in case someone else needs to go through the same steps. I will make the thread solved myself, after furnishing the original post with a full rundown of the events and the steps that worked for me, once we figure out what those are.

For the time being, though, I have to put this on the backburner due to some unavoidable things occurring offline.

Thanks for your patience, and I hope to get this sorted soon. Please feel free to drop suggestions here for me to try when I have time, and yes, I will have a look at the EFI shell thing, tfo, and as for you QIII, if you find anything out then I will still get the email and read the thread, so lemme know if you find anything <3

---

