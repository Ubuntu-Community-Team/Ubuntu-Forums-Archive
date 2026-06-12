---
title: "How to upgrade BIOS in ubuntu 10.10?"
date: 2011-05-22
forum: Security
---

### Post by Andreawws on 2011-05-22
Ok so I have established that there is a BIOS virus in this machine (I have basically done every test that can be done) And I found the flashing utility for upgading and everything, now the only problem left is installing it :(
Whenever I try this happens.....

(copy/paste from the terminal)

```
./BIOSUpdate/FTS_FlashBIOSUpdateLinuxBootDisk_500110_1005782.SH

Flash FirstBIOS Update Diskette
V5.00 R1.10.2164.A1

Extracting 1474560 bytes ...
Writing 1474560 bytes to /dev/fd0...
dd: opening `/dev/fd0': Read-only file system
failed.

Now I did that while logged in as root....
sudo ./BIOSUpdate/FTS_FlashBIOSUpdateLinuxBootDisk_500110_1005782.SH
I also tried above command logged in as root and the 'normal' admin account.
```

the usage instructions that I obtained from the manufacturer are:

The BIOS Update File is a .sh file (Shell Script), which enables you to create
a bootable disk to update the BIOS.
The script only works if there is a C-Compiler installed at usr/bin/cc and the
user has write access on dev/fd0 (e.g. if not filed as Root). 

so does anyone have a solution?

                  thanks in advance
                                //Andreawws

P.S. If this is in the wrong section I apologise for it:tongue:

---

### Post by CharlesA on 2011-05-22
BIOS viruses are rather rare.

What makes you think you have one?

---

### Post by mikewhatever on 2011-05-22
The scrip seems to try writing something to the floppy disk and fails because of the read only file system. Now, dd usually needs admin privileges to operate. Do you get the same output when running the scrip with sudo? This may be too obvious, but still, do you actually have a floppy drive and a floppy disk in it?

---

### Post by Andreawws on 2011-05-22
> Now I did that while logged in as root....
sudo ./BIOSUpdate/FTS_FlashBIOSUpdateLinuxBootDisk_500110_1005782.SH
I also tried above command logged in as root and the 'normal' admin account.I already included it in the text......
can it maybe be modified to write to a usb stick instead?

> **CharlesA said:**
> BIOS viruses are rather rare.

What makes you think you have one?

Because my brothers used it....
I call them:
Sir click-alot (watch robotwars to get the catch in this one...)
and The prince of porn (Should be obvious what game this refers to....)
And I call them that because well one clicks EVERYTHING and the other one well he visits alot of 'questionable' sites

and I have done every test you could ever think of.
I formatted the hard drives 7 times in a row (Including the MBR)
I have tried several hard drives
I have tried several cables
I have tried both hard drives and cables in different computers
same goes for ram
I ran memory tests for 8 hours in a row, nothing wrong
...List goes on...

if anyone have a test I haven't done...
I'll do it
But I have done all tests and consulted two computer specialists and all points to a BIOS virus :(

---

### Post by mikewhatever on 2011-05-22
> **Andreawws said:**
> I already included it in the text......
can it maybe be modified to write to a usb stick instead?


Well, the command is included, but where is the output? Was there no output at all?

---

### Post by Andreawws on 2011-05-22
./BIOSUpdate/FTS_FlashBIOSUpdateLinuxBootDisk_500110_1005782.SH

Flash FirstBIOS Update Diskette
V5.00 R1.10.2164.A1

Extracting 1474560 bytes ...
Writing 1474560 bytes to /dev/fd0...
dd: opening `/dev/fd0': Read-only file system
failed.

that is the output, and yes I do have a floppy installed with a floppy disk inside..

(I installed Eye of the beholder and doom through it using dosbox :D)

---

### Post by CharlesA on 2011-05-22
Try using this to get a root shell:

```
sudo -i
```

Then run the script without sudo.

---

### Post by FuturePilot on 2011-05-22
> **Andreawws said:**
> I already included it in the text......
can it maybe be modified to write to a usb stick instead?



Because my brothers used it....
I call them:
Sir click-alot (watch robotwars to get the catch in this one...)
and The prince of porn (Should be obvious what game this refers to....)
And I call them that because well one clicks EVERYTHING and the other one well he visits alot of 'questionable' sites

and I have done every test you could ever think of.
I formatted the hard drives 7 times in a row (Including the MBR)
I have tried several hard drives
I have tried several cables
I have tried both hard drives and cables in different computers
same goes for ram
I ran memory tests for 8 hours in a row, nothing wrong
...List goes on...

if anyone have a test I haven't done...
I'll do it
But I have done all tests and consulted two computer specialists and all points to a BIOS virus :(

So you ran a bunch of tests and nothing out of the ordinary showed up? Doesn't sound like a BIOS virus to me. Besides things like BIOS viruses are extremely, extremely rare if they even exist at all. You still haven't said what problem you are having that made you come to this conclusion.

---

### Post by Soul-Sing on 2011-05-22
please be very careful with bios flashing, you can destroy your computer! 

working via linux is thinking the other way around: no viruses. Don 't think of them, there are no active linux viruses in the wild.

relax. :)

---

### Post by CharlesA on 2011-05-22
> **FuturePilot said:**
> So you ran a bunch of tests and nothing out of the ordinary showed up? Doesn't sound like a BIOS virus to me. Besides things like BIOS viruses are extremely, extremely rare if they even exist at all. You still haven't said what problem you are having that made you come to this conclusion.

Definitely. Need more info here.

> **leoquant said:**
> please be very careful with bios flashing, you can destroy your computer! 

working via linux is thinking the other way around: no viruses. Don 't think of them, there are no active linux viruses in the wild.

relax. :)

+1!

---

### Post by Andreawws on 2011-05-22
ah yes, to clarify, there is windows installed in a dual boot on the same machine (I don't use windows, My brothers do on the other hand)

> So you ran a bunch of tests and nothing out of the ordinary showed up?  Doesn't sound like a BIOS virus to me. Besides things like BIOS viruses  are extremely, extremely rare if they even exist at all. You still  haven't said what problem you are having that made you come to this  conclusion.

Something (According to the people I have talked to it points to being a BIOS virus) is eating, or more exactly corrupting some important windows system files....
I know that it is not on the hard drive since I wiped it 7 times in a row (Including the master boot record)
and I have exchanged all parts of the computer (all cables, the hdd's and everything) I am pretty sure that the parts aren't the problem (Not to mention that I have tried them all on another computer (With another motherboard) and nothing corrupts there....

> please be very careful with bios flashing, you can destroy your computer! 
I know exactly what can happen, the worst thing I would have to do would be to get a new bios chip and solder it to the motherboard instead of the old one.....
or that might not apply to newer stuff (I know it worked on older stuff :D)

---

### Post by tubezninja on 2011-05-22
> **Andreawws said:**
> 
Something (According to the people I have talked to it points to being a BIOS virus) is eating, or more exactly corrupting some important windows system files....

Let's step back a bit here.  What behaviors, specifically, is the system exhibiting that brought you to this conclusion?  You say you "established" that you have a BIOS virus, but there's no description as to how this conclusion was made.

---

### Post by Andreawws on 2011-05-23
by scratching my head and reinstalling everything (several times) and something kept eating the vital system files (for the dual boot windows)
so I reformatted the hard drive 7 times, problem still there, I thought it might be the ram, so I ran a memory test for a few hours, nothing wrong there, so I thought it might be the hard drive or the cables, so I took them out and put them in another computer and tried, nothing wrong at all, but I still tried with some other hard drives and cables, same problems, so I assumed that was not the problem and ended up taking everything into pieces and carefully cleaning all connectors and everything...
I reassemble everything, problem persists, I try installing with another cd, I thought the cd might be corrupted, didn't help so I assumed that my ubuntu cd was broken, so I burned a new one (64 bit this time, I thought it might be a compatibility issue) still the same problem, windows breaks after rebooting the computer (I can run it after installing it, when rebooting the system file(s) get corrupted) so I was out of options, I reinstalled ubuntu (32 bit this time, because It was the first of my ubuntu cd's I found) and left windows to sit there and rot with it's corrupted system files...
then I contacted people that I know (and that are educated computer tech supports) and we had a long run through what was wrong and we came up with that it most likely was a bios virus (Yes I know that the are extremely rare... But we did take into consideration that my brothers have BAD surfing habits... one clicks EVERYTHING and one well, surfs on somewhat questionable websites) and I was advised to flash my bios. Now I contacted the other one I know that is an educated tech support, and after a similar discussion we came to the same result.

so now with that block of text, what do you think I should do?

---

### Post by ukberry on 2011-05-23
> **Andreawws said:**
> ...something kept eating the vital system files (for the dual boot windows)
Could you describe what you mean when you say "eating the vital system" files please? Is it replacing them with something else, modifying their contents, etc...?

Aside: BIOS viruses are OS independent (so running a linux OS doesn't necessarily mean you'll be protected from its effects, so be careful!). It's unlikely that someone would write a BIOS virus to target specific files on a certain OS, but not impossible.

Meanwhile, have you scanned your Windows partitions with Clam Anti-virus while logged into Ubuntu? (just in case that finds something awry)

---

### Post by FuturePilot on 2011-05-24
> **Andreawws said:**
> by scratching my head and reinstalling everything (several times) and something kept eating the vital system files (for the dual boot windows)

Can you describe this more? I don't know what you mean by eating vital system files.

> then I contacted people that I know (and that are educated computer tech supports) and we had a long run through what was wrong and we came up with that it most likely was a bios virus (Yes I know that the are extremely rare... But we did take into consideration that my brothers have BAD surfing habits... one clicks EVERYTHING and one well, surfs on somewhat questionable websites) and I was advised to flash my bios. Now I contacted the other one I know that is an educated tech support, and after a similar discussion we came to the same result.

I have a degree in Computer Science and what is this? There is no way something could get to you BIOS in one click. You would need root access if it's even possible. And the modified BIOS would need to be created specifically for your particular chipset and motherboard. And if it wasn't, your computer would be a nice expensive brick. Besides most of the drive by malware floating around out there is for Windows. Someone let me know when you see an antivirus.sh out there.

Before jumping to BIOS viruses I would look at a bad hard drive. Do you have another one you could test with? Look at the SMART data for you current. Look for bad sectors. Use Ubuntu's Disk Utility. Tip for Memtest, you should let it run for about 24 hours for it to be accurate.

---

### Post by Andreawws on 2011-05-24
doesn't anyone READ?
I have tried with different cables AND hard drives!

> Meanwhile, have you scanned your Windows partitions with Clam Anti-virus  while logged into Ubuntu? (just in case that finds something awry)I HAVE FORMATTED THE HARD DRIVE 7 TIMES IN A ROW, IT IS WIPED TO FACTORY CONDITION.

> Could you describe what you mean when you say "eating the vital system"  files please? Is it replacing them with something else, modifying their  contents, etc...?I mean corrupting their contents. Referr to my first or second post and you will see the same info there.
> 
Aside: BIOS viruses are OS independent (so running a linux OS doesn't  necessarily mean you'll be protected from its effects, so be careful!).  It's unlikely that someone would write a BIOS virus to target specific  files on a certain OS, but not impossible.Windows is the most usual and probably what it targets I haven't NOTICED any file corruption on the linux partition (yet)

> You would need root access if it's even possible.It got installed while running windows -_-

> Before jumping to BIOS viruses I would look at a bad hard drive. Do you  have another one you could test with? Look at the SMART data for you  current. Look for bad sectors. Use Ubuntu's Disk Utility. Tip for  Memtest, you should let it run for about 24 hours for it to be accurate.I have ran a memtest for 20 hours.
The hard drive I am currently using has 2 bad sectors, none of the other one's I have tested with have any bad sectors.
and if you look at my other posts you will see that I have mentioned using other hard drives AND cables.

---

### Post by spynappels on 2011-05-24
> **Andreawws said:**
> doesn't anyone READ?
I have tried with different cables AND hard drives!

I HAVE FORMATTED THE HARD DRIVE 7 TIMES IN A ROW, IT IS WIPED TO FACTORY CONDITION.

I mean corrupting their contents. Referr to my first or second post and you will see the same info there.
Windows is the most usual and probably what it targets I haven't NOTICED any file corruption on the linux partition (yet)

It got installed while running windows -_-

I have ran a memtest for 20 hours.
The hard drive I am currently using has 2 bad sectors, none of the other one's I have tested with have any bad sectors.
and if you look at my other posts you will see that I have mentioned using other hard drives AND cables.

Chill out a second, you are being asked these questions because very often someone who comes on here convinced that they have a specific problem has a different problem altogether, and it is only by asking the questions can we find out what is actually happening. Reacting like you did will only make people less likely to help.

How did you wipe the HDD?

I wouldn't always take every word from a support tech as gospel, I used to be one.

I can't help with flashing the BIOS, but if you are right, seems to me getting a new MoBo and not letting your brothers near the computer when it is working again would look to be a better option.....

---

### Post by Starfleet on 2011-05-24
Andreawws, from your information posted, I do not think you have a BIOS virus. In 22 years I've not come across this type of infection. It's extremely difficult to contract this type of infection too. I know they exist, I have examined some in the lab, but there are very few in circulation. Most MOBO's protect themselves to some extent too from this sort of attack. Most BIOS viruses disable your machine completely or target your operating system, attacking your data, but these are few. Although I need more information to be certain, it sounds to me as though you have a problem with your Windows installation disc that is copying itself to you HD every time you install. Or, another problem on your motherboard that is causing a corruption, dry joint somewhere the most likely cause. These are much much more likely than a BIOS virus. In any case, if you want to update your BIOS, do you not have a BIOS utility disc to use within Windows? Or, is there a utility to enable an update from within your BIOS itself. Many board come with an update facility that just allows you to use a memory stick. You should be able to flash the bios in that way no problem. 

Come back to us with more information regarding your board make and model number so we can all give it some more thought, please!

---

### Post by Andreawws on 2011-05-24
ok then board make an model:
```
 *-core
       description: Motherboard
       product: D2164-A1
       vendor: FUJITSU SIEMENS
       physical id: 0
       version: S26361-D2164-A1
       serial: B02A9EC2
     *-firmware
          description: BIOS
          vendor: FUJITSU SIEMENS // Phoenix Technologies Ltd.
          physical id: 0
          version: 5.00 R1.07.2164.A1 (11/17/2005)
          size: 98KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
```

I tried with another windows disc and I find it very unlikely that both discs are broken. (Same goes for ubuntu)
so is that all?

> Chill out a second, you are being asked these questions because very  often someone who comes on here convinced that they have a specific  problem has a different problem altogether, and it is only by asking the  questions can we find out what is actually happening. Reacting like you  did will only make people less likely to help.


Sorry, I just find it annoying to answer a question several times when I have already provided the info.

> How did you wipe the HDD?

3 times standard formatting and 4 using Gparted.

---

### Post by MSPdwalt on 2011-05-24
What windows files are getting corrupt and how are you determining this?  Blue Screen of Death? Black screen pre-boot that says file xxx.sys is corrupt/missing?


When you install windows what programs are you putting on there and how throughly have you validated them?  Maybe one of your apps is shoddy or a virus?

Antivirus programs, VPN clients, system tweaking utilities can all jack with the windows system files and if they're poorly designed or you're using versions too old for your OS that can mess things up as well.

I second the threads collective option that this is likely not a BIOS virus, I for one would like to see one. I don't believe they exist nor do they need to. I don't see the point when it's so easy to get a bunch of morons to install AV2011 and give you their credit card numbers.  The goal of viruses these days is to get information of use to the person disseminating the virus, the days of lets just make a virus to wreak havoc are over.

The manufacturer of your hard drive should have some disk tools you can use. (example Seagate uses seatools) You can do integrity/Constancy checks I've found *nix to be much more tolerant of a failing drive than windows.  There may also be a low level format utility for your drive.  If you want to make sure it's blank you low level it.  There may also be firmware upates for the drive as well.

Also your mobo manufacture should have some diagnostic tools to check say the SATA or IDE controller, chipset, and anything else that may be corrupting your data.

---

### Post by Andreawws on 2011-05-24
> What windows files are getting corrupt and how are you determining this?   Blue Screen of Death? Black screen pre-boot that says file xxx.sys is  corrupt/missing?
xxx.xxx corrupt/missing (Usually HAL.dll)

> 
When you install windows what programs are you putting on there and how  throughly have you validated them?  Maybe one of your apps is shoddy or a  virus?

> Antivirus programs, VPN clients, system tweaking utilities can all jack  with the windows system files and if they're poorly designed or you're  using versions too old for your OS that can mess things up as well.

I did not put anything on it, nor was I connected to the internet.

> I second the threads collective option that this is likely not a BIOS  virus, I for one would like to see one. I don't believe they exist nor  do they need to. I don't see the point when it's so easy to get a bunch  of morons to install AV2011 and give you their credit card numbers.  The  goal of viruses these days is to get information of use to the person  disseminating the virus, the days of lets just make a virus to wreak  havoc are over.


ok, what do you think it is then? (There are people who make viruses just to wreck havoc nowadays too)


> The manufacturer of your hard drive should have some disk tools you can  use. (example Seagate uses seatools) You can do integrity/Constancy  checks I've found *nix to be much more tolerant of a failing drive than  windows.  There may also be a low level format utility for your drive.   If you want to make sure it's blank you low level it.  There may also be  firmware upates for the drive as well.

I have tried with several different drives from different manufacturers.... I KNOW that they work

> 
Also your mobo manufacture should have some diagnostic tools to check  say the SATA or IDE controller, chipset, and anything else that may be  corrupting your data.

hmm I didn't find one... I'll look again....

---

### Post by Starfleet on 2011-05-24
> **Andreawws said:**
> ok then board make an model:
```
 *-core
       description: Motherboard
       product: D2164-A1
       vendor: FUJITSU SIEMENS
       physical id: 0
       version: S26361-D2164-A1
       serial: B02A9EC2
     *-firmware
          description: BIOS
          vendor: FUJITSU SIEMENS // Phoenix Technologies Ltd.
          physical id: 0
          version: 5.00 R1.07.2164.A1 (11/17/2005)
          size: 98KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
```

I tried with another windows disc and I find it very unlikely that both discs are broken. (Same goes for ubuntu)
so is that all?


Sorry, I just find it annoying to answer a question several times when I have already provided the info.
3 times standard formatting and 4 using Gparted.


YOU MAY WANT TO TAKE A LOOK HERE: [http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)    If you are dual booted this can be the problem in Windows. Take a look at your boot.ini file too.

Apologies if I asked a question that you had already provided the answer to but actually some of your posts are not too clear. We don't even know what version of Windows you are running and this could be very important. So often it is a process of teasing out answers. But that's ok you just need to bear with us. We know you are frustrated, many of us have been there so we're all on your side.

From experience you will probably find your BIOS's will read ok if you use a FAT32 boot disc to update your BIOS. A new 'Windows friendly' BIOS file should be available from your motherboard manufacturer. Don't use the one on any factory disc that was supplied originally with the machine. Get the latest. As has been said though, most Linux installations are more tolerant of hard ware irregularities and this could be why your machine is still happy on nix and not Windows if you have a glitchy dry joint or a controller problem or the like. 

However, I am more convinced than ever it is Windows that is the key to your problem. Not a virus in the BIOS. Nearly all BIOS infections of which there are few, are very very old and 95% of them just destroy your computer. Your computer most likely just wouldn't run. 

The fact you have used two different discs to re-install doesn't mean Windows isn't the problem. As MSPdwalt mentions, there's loads that can go wrong even if you haven't loaded much. Are you sure your brothers are not deleting stuff incorrectly after visiting dubious sites using some badly made tool? In my work I come across this often - I build and maintain and I'm a network manager. That doesn't make me any sort of expert but I know a thing or two learned from experience.

ACTION I WOULD TAKE: try reflashing the bios by all means with the latest file in Miscrosoft format usually on a FAT32 disc if the board is an older one. Use a memory stick if possible but your board may not support that.

Reload windows onto another hard disc and after a clean install I would keep the machine disconnected from the internet during this early stage until it screams for updates. Then before connecting to the internet and after rebooting checkout the machine to see if the files are ok that have been causing trouble. If they are, you have a MOBO fault for sure.

NOTE: have just posted and seen your other post...if what you say is accurate, without doubt you have a hardware fault if your BIOS updates ok. I've seen this sort of thing many times and it's 99% always a hardware problem if it keep happening.

---

### Post by Andreawws on 2011-05-24
> Apologies if I asked a question that you had already provided the answer  to but actually some of your posts are not too clear. We don't even  know what version of Windows you are running and this could be very  important. So often it is a process of teasing out answers. But that's  ok you just need to bear with us. We know you are frustrated, many of us  have been there so we're all on your side.no problem ^^
> 
From experience you will probably find your BIOS's will read ok if you  use a FAT32 boot disc to update your BIOS. A new 'Windows friendly' BIOS  file should be available from your motherboard manufacturer. Don't use  the one on any factory disc that was supplied originally with the  machine. Get the latest. As has been said though, most Linux  installations are more tolerant of hard ware irregularities and this  could be why your machine is still happy on nix and not Windows if you  have a glitchy dry joint or a controller problem or the like. There wasn't one supplied originally

> However, I am more convinced than ever it is Windows that is the key to  your problem. Not a virus in the BIOS. Nearly all BIOS infections of  which there are few, are very very old and 95% of them just destroy your  computer. Your computer most likely just wouldn't run. It used to work :/

> The fact you have used two different discs to re-install doesn't mean  Windows isn't the problem. As MSPdwalt mentions, there's loads that can  go wrong even if you haven't loaded much. Are you sure your brothers are  not deleting stuff incorrectly after visiting dubious sites using some  badly made tool? In my work I come across this often - I build and  maintain and I'm a network manager. That doesn't make me any sort of  expert but I know a thing or two learned from experience.Yes I am sure they aren't deleting anything....
they are not allowed to use it (currently anyway)

> ACTION I WOULD TAKE: try reflashing the bios by all means with the  latest file in Miscrosoft format usually on a FAT32 disc if the board is  an older one. Use a memory stick if possible but your board may not  support that.

I came here for help with flashing the bios....
the script that I got from Fujitsu gives an error:

```

./BIOSUpdate/FTS_FlashBIOSUpdateLinuxBootDisk_500110_1005782.SH

Flash FirstBIOS Update Diskette
V5.00 R1.10.2164.A1

Extracting 1474560 bytes ...
Writing 1474560 bytes to /dev/fd0...
dd: opening `/dev/fd0': Read-only file system
failed.
```> 
Now I did that while logged in as root....
sudo ./BIOSUpdate/FTS_FlashBIOSUpdateLinuxBootDisk_500110_1005782.SH
I also tried above command logged in as root and the 'normal' admin account.

it tries writing to floppy but fails, (Even when running as root, or using the sudo command)

> Reload windows onto another hard disc after a clean install and I would  keep the machine disconnected from the internet during this early stage  until it screams for updates. Then before connecting to the internet and  after rebooting checkout the machine to see if the files are ok that  have been causing trouble. If they are, you have a MOBO fault for sure.


hmm that is what I did :(

> NOTE: have just posted and seen your other post...if what you say is  accurate, without doubt you have a hardware fault if your BIOS updates  ok. I've seen this sort of thing many times and it's 99% always a  hardware problem if it keep happening. 	

ok
so I just need to find out how to make the BIOS flashing script write to my usb instead of the floppy and I could try

---

### Post by Starfleet on 2011-05-24
If windows is still running I recommend using the Fujitsu Siemens 'Flash Desk' method from within windows rather than flashing from within Linux. Instruction should be on their site along with the Windows file you need.  If Windows is not running take a look at the information at the link I posted in my last post. It may be helpful as you may have a boot.ini fault causing your HAL.dll error message.

---

### Post by mikewhatever on 2011-05-24
> **Andreawws said:**
> 
xxx.xxx corrupt/missing (Usually HAL.dll)

Not sure who you've talked to, but the 'hal.dll is missing or corrupt' error message is not an infrequent one, and I've never seen anyone claiming it to be related to BIOS malware. Here is one possible explanation:
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt](http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt)

> **Andreawws said:**
> 
so I just need to find out how to make the BIOS flashing script write to my usb instead of the floppy and I could try
You'll have to modify the script for that.

---

### Post by Andreawws on 2011-05-25
I checked your solution mikewhatever and windows is located on /dev/sda2 and boot.ini says ult=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
so that is not the cause, boot.ini is correct.
> 
If windows is  still running I recommend using the Fujitsu Siemens 'Flash Desk' method  from within windows rather than flashing from within Linux. Instruction  should be on their site along with the Windows file you need.  If  Windows is not running take a look at the information at the link I  posted in my last post. It may be helpful as you may have a boot.ini  fault causing your HAL.dll error message.


The only thing there I haven't already tried is:
[COLOR=Black]Perform a repair installation of windows XP.
[/COLOR]
but doesn't that slay grub in the process of repairing windows?


> You'll have to modify the script for that.


ah yes, I know that much, but I do not know what to modify nor do I know what it should be modified to look like....

---

### Post by Starfleet on 2011-05-25
I'd just replace the corrupt HAL.dll from your XP disc and see what happens. Follow the instruction in the link in my earlier post. Or here... [http://pcsupport.about.com/od/findby...singhaldll.htm](http://pcsupport.about.com/od/findby...singhaldll.htm)   This shouldn't affect your Grub installation. If by some chance it did you'd need to re-install Grub from a live cd.

---

### Post by psusi on 2011-05-25
Close the write protect tab on the floppy.

And yes, this certainly is not a bios virus.  First, there are no known bios viruses in the wild, and second, this is not the behavior of a virus.  It wouldn't do any good if it just zapped your OS; it needs to infect it and try to spread.

How old is this motherboard?  It used to be that you could run into that error after a defrag on large hard disks that older bioses could not access all of.  You might try installing windows to just the first 8 gb of the disk ( and only Windows, no Ubuntu ).

---

### Post by Andreawws on 2011-05-25
The board isn't that old......


> Close the write protect tab on the floppy.shouldn't be a problem when running as root, right?
> 
And yes, this certainly is not a bios virus.  First, there are no known  bios viruses in the wild, and second, this is not the behavior of a  virus.  It wouldn't do any good if it just zapped your OS; it needs to  infect it and try to spread.then what could it be?


> 
I'd just replace  the corrupt HAL.dll from your XP disc and see what happens. Follow the  instruction in the link in my earlier post. Or here... [http://pcsupport.about.com/od/findby...singhaldll.htm](http://pcsupport.about.com/od/findby...singhaldll.htm)   This shouldn't affect your Grub installation. If by some chance it did you'd need to re-install Grub from a live cd.
I will look into that...


EDIT:
404 Document Not Found - See our related content below

was what I got when clicking the link -_-

---

### Post by FuturePilot on 2011-05-25
> **Andreawws said:**
> 
shouldn't be a problem when running as root, right?
No. The write protect tab is a hardware controlled write protection device. It can't be overridden through software or elevated privileges.
> then what could it be?
I would say it's either a hardware problem or perhaps the Windows install medium is bad.

---

### Post by cariboo on 2011-05-25
The XP boot loader need to be on the first partition of the first hard drive in your system, is grub over-writing them. I don't have a system with XP and Ubuntu installed, but could it possibly be that you  boot files aren't on /dev/sda1? 

Win 7 creates a 100MiB partition at the start of the first hard drive so a corrupted hal.dll isn't a problem any more.

---

### Post by psusi on 2011-05-25
> **cariboo907 said:**
> The XP boot loader need to be on the first partition of the first hard drive in your system, is grub over-writing them. I don't have a system with XP and Ubuntu installed, but could it possibly be that you  boot files aren't on /dev/sda1? 


No it doesn't, and grub isn't going to touch hal.dll.

---

### Post by Andreawws on 2011-05-25
hmmm it should work...
I'll be back
gotta try something

---

### Post by DodgeV83 on 2011-05-25
> **Andreawws said:**
> xxx.xxx corrupt/missing (Usually HAL.dll)

**How long after the installation do you see this error?**

A day?  A week?  35 seconds?

**At which point does the error come up, and what are you doing at the time?**

There is certainly **not** enough information here to conclude your problem is a BIOS virus.  On the contrary, the information here strongly indicates it is **not** a BIOS virus.  There are many many other causes which should be investigated before beginning a process which could irrevocably damage your machine.

I recommend ceasing all attempts to update your BIOS until other, more likely, scenarios are investigated.

---

### Post by Andreawws on 2011-05-26
ok.
the error displays as soon as I reboot the machine.
even with windows being the only thing installed.

the error comes up when loading windows XP

---

### Post by DodgeV83 on 2011-05-27
> **Andreawws said:**
> ok.
the error displays as soon as I reboot the machine.
even with windows being the only thing installed.

the error comes up when loading windows XP

Two things:

1.  Once Windows XP is installed, are you running Windows Update?  If you aren't running them, then do a full update before rebooting (it will reboot during this process anyway).

If you **are** running Windows Update, then don't.  It is possible one of the updates are messing up your installation.  Immediately reboot and see if the error comes up.


2.  If this fails, get a new Windows installation disc.  I don't see that you've tried this yet, but if you have I apologize for missing it.  If you don't have access to another disc, there are a few official places online where you can download one (Don't pirate it!).  Note, none of these sources will provide you with a product key, so use the one on the bottom of your computer.

Unfortunately, I can't find any official downloads out there for Windows XP (it's too old).  Here is a link with official downloads for Windows 7.  These links are from DigitalRiver.com, which is an official retailer for Microsoft.  These are not pirated links.  Again, these .iso files do not come with product keys and will start asking for one after 30 days.

[http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/](http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/)

Mods: If posting these is a no-no, I apologize, please remove the links.

Good luck!

---

### Post by Andreawws on 2011-05-27
> 1.  Once Windows XP is installed, are you running Windows Update?  If  you aren't running them, then do a full update before rebooting (it will  reboot during this process anyway).

If you **are** running Windows Update, then don't.  It is possible  one of the updates are messing up your installation.  Immediately reboot  and see if the error comes up.

Have tried both ways already.


> 2.  If this fails, get a new Windows installation disc.  I don't see  that you've tried this yet, but if you have I apologize for missing it.   If you don't have access to another disc, there are a few official  places online where you can download one (Don't pirate it!).  Note, none  of these sources will provide you with a product key, so use the one on  the bottom of your computer.

I have already tried two cd's (BOTH are verified to work (mainly by me trying them on two of my older computers))

also now my sound system is 'eaten' 
and my graphics have gone sluggish and started to corrupt a little here and there. (No problems with the graphics card, it worked like running water 2 days ago, and I bet that it will work like running water if I reinstall :D tho it would be a pity to reinstall.... again...)

---

### Post by DodgeV83 on 2011-05-27
> **Andreawws said:**
> also now my sound system is 'eaten' 
and my graphics have gone sluggish and started to corrupt a little here and there. (No problems with the graphics card, it worked like running water 2 days ago, and I bet that it will work like running water if I reinstall :D tho it would be a pity to reinstall.... again...)

Two questions:

1.  You have a Windows installation that is running right now, meaning the HAL errors are gone?

2.  Do you experience any graphical or sound issues in Ubuntu on the same machine?

---

### Post by Andreawws on 2011-05-28
the windows is still not running, it is the ubuntu installation that has started to suffer :( 

btw the sound system somehow returned.... 
but the graphics still fail (aka it still corrupts randomly, tho it runs smooth as water again...)

somethings fishy here......

---

### Post by Starfleet on 2011-05-29
Andrew, it is sounding more and more like a hardware issue. This could include a faulty cable to the HD. Can you swap that? If you haven't already done so check all connections to the motherboard. I take it the processor heat sink is clean and the fan working ok along with all your other fans?

---

### Post by Andreawws on 2011-05-29
yes everything is cleaned... I have changed cables.... there hasn't been any resent hardware change, this problem started appearing after my brother(s) got a virus destroying windows.  all connections are checked and working....

---

