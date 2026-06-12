---
title: "SanDisk Cruzer and WinXP"
date: 2007-08-14
forum: Windows
---

### Post by slumcat05 on 2007-08-14
My SanDisk Cruzer Micro 2GB flash drive works great in Ubuntu. It used to work great on my WinXP laptop (unfortunately, Boeing is still stuck in Windows). But something weird happened at work today.

A co-worker tried to give me a file on his Lexar flash drive. I plugged it in, and the little bubble that shows drivers being installed and such popped up, but the drive never came up in My Computer. It showed up in the "Safely Remove Hardware" wizard as a "USB Mass Storage Device", it showed up in the device manager, but never in My Computer. So after much frustration for myself and several other computer gurus, he just put the file on a 1 gig SanDisk U3 micro (similar to my own, but different) and it popped up and worked just fine.

Fast forward to this evening, I want to watch a movie with my PortableApps version of VLC on my Cruzer Micro. Plug it in, little driver dialog pops up in task pane, but nothing in "My Computer". It shows up in "Safely Remove Hardware" and Device Manager, and is even listed as a "SanDisk u3 Cruzer Micro" (under the "USB Mass Storage device"), but still nothing in My Computer. I uninstalled it in the Device Manager and plugged it in again; this time it went through a more intense driver installation thingy as if it was the first time ever being used, still nothing. I even tried un-installing some CD/DVD burning software that others had suggested were casuing problems with the SanDisk drives... of course, nothing. I HAVE used this drive with this computer many many times in the past (and fairly recently, as I recall), both directly in the USB ports, and in the ports on the docking station, with no problems up until now. As a dummy check, I plugged it into my Ubuntu box and it mounted just fine, as always.

If anybody can offer any advice on how to get Windows to allow me to access this drive, I would really appreciate. While this is one more thing that can make me smile about my decision to make the switch, it is frustrating as I don't have the choice with my lappy. Thanks in advance for any help.

---

### Post by smoker on 2007-08-14
hi, a while back i had a similar problem, though not with a cruzer micro. i used the HP usb disk format tool to reformat the drive and it worked ok after that. it is a windows app though, but if you want you can download from here: [http://files.extremeoverclocking.com/file.php?f=197](http://files.extremeoverclocking.com/file.php?f=197)

please note reformatting will delete all your info, so remove or back up first,

best of luck.

---

### Post by LaRoza on 2007-08-15
> **slumcat05 said:**
> 
If anybody can offer any advice on how to get Windows to allow me to access this drive, I would really appreciate. While this is one more thing that can make me smile about my decision to make the switch, it is frustrating as I don't have the choice with my lappy. Thanks in advance for any help.

If you removed the drive without safely ejecting, you can easily damage the drive and wipe the formatting. You have described this scenerio. You will have to reformat and hope the circuitry still works.

If you can view the drive in Linux, this wouldn't be the problem.

---

### Post by shad0w_walker on 2007-08-15
When you started using this drive with Ubuntu did you reformat it to a Linux filesystem? If you did thats your problem right there, Windows includes no support for anything other than its own filesystems (You can get 3rd party drivers but they aren't great from what iv seen)

P.S. I wouldn't be worried about damaging the circuitry in your drive, the main reason for the safe remove feature is to prevent you removing the drive whilst it is being read from or written to (So you don't crash programs or end up with half a file) the chances of there being physical damage are incredibly low. Still recommend using safe remove as its the proper way to do things but in most cases its not strictly essential, just advisable.

---

### Post by LaRoza on 2007-08-15
> **shad0w_walker said:**
> 
P.S. I wouldn't be worried about damaging the circuitry in your drive, the main reason for the safe remove feature is to prevent you removing the drive whilst it is being read from or written to (So you don't crash programs or end up with half a file) the chances of there being physical damage are incredibly low. Still recommend using safe remove as its the proper way to do things but in most cases its not strictly essential, just advisable.

I would, I have seen many drives wiped because of this.

---

### Post by notwen on 2007-08-15
Regardless of whether you're read/writing to said flash drive, there' s always the chance of corrupting the data on it and rendering the drive unusable until you re-format it, unless your properly 'eject' in Windows or 'unmount' in *nix.

---

### Post by shad0w_walker on 2007-08-15
I have never personally seen a single drive die because of this. I have a good 5 drives, all of which i never bother to safely remove unless i have written something to them and i know it hasn't synced yet. I haven't had any of them die and haven't met anyone else who has had one die. I also don't personally see how now syncing your drives before unplugging can cause physical damage to the drive. Would be interested to hear an explanation of how it can though.

P.S. Drives being wiped is not what i was talking about. Drives being wiped is by my definition files being lost, I'm talking about damage to the actual hardware

---

### Post by smoker on 2007-08-15
personally i have lost one flash drive due to improper removal, and i know of others who have either lost data, or 'fubar'd' a usb drive beyond repair. 

the fact is the safe removal feature is put there for a reason, not to inconvenience the user. if you must insist in not using the safe removal procedure, at least ensure 'write caching is turned off' to minimise data corruption. there is more info here for anyone interested:
[http://www.microsoft.com/whdc/system/pnppwr/hotadd/XPrem-devs.mspx](http://www.microsoft.com/whdc/system/pnppwr/hotadd/XPrem-devs.mspx)

---

### Post by shad0w_walker on 2007-08-15
I know it is there for a reason, I have said that it is highly recommended to use it, all i am saying is that in my personal experience i haven't encountered a drive that has actually been physically damaged by unsafe removal.

---

### Post by LaRoza on 2007-08-15
> **shad0w_walker said:**
> I know it is there for a reason, I have said that it is highly recommended to use it, all i am saying is that in my personal experience i haven't encountered a drive that has actually been physically damaged by unsafe removal.

Basically it shocks the circuits, like ESD.

---

### Post by slumcat05 on 2007-08-15
Nope, I always safely remove, and, like I said the drive mounts fine in Ubuntu and all the data is there and usable. It's also not a formattting issue as someone suggested, it's formatted FAT16 and has been used many times in Windows (on this very laptop in fact). It pretty much seems like either there was a software change on the Windows box that doesn't play well with the drives (there have been no hardware changes), or it's just Windows being Windows, some sort of bug.

Also, if you'll remember, this isn't isolated to one drive, the problem first occured with someone else's drive (which worked fine on their computer). A second drive from the same person then worked just fine. A third drive, mine, totally different brand and had worked just fine a week or two before, performed the same as the first. Point is, it's probably not the drive itself, but the computer (either the USB ports or something in the OS).

Thanks to all for the suggestions though.

---

