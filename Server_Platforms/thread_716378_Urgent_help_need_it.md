---
title: "Urgent help need it"
date: 2008-03-05
forum: Server Platforms
---

### Post by jas168 on 2008-03-05
Just got new server trying to install ubuntu 7.10 server.

my setup is raid 0 mirror.

when i install ubuntu it shows both the hard drives, is that normal?

I choose the first one to install the ubuntu on, the setup runs fine but 
after reboot the server don't boot.
any ideas?

thank you advance

---

### Post by rapiscan on 2008-03-05
To the best of my knowledge, this means you are using software raid instead of hardware raid.   With software raid your operating system is the doing the job of writing to both harddrives at the same time. Consequently you need software raid drivers for this to work.  

I did a quick google search and found this link:
[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

I'm sure there are others.

---

### Post by jas168 on 2008-03-05
hi thanks for the quick reply, can you guide me to use hardware raid 0 mirror as my mother board supports hardware raid 0, 

this is my first time using raid with ubuntu.

thank you

---

### Post by cdenley on 2008-03-06
That depends entirely on your RAID controller, and is not Linux-specific. Usually, you can press a key like F8 or F10 while your computer is booting to get to the RAID configuration menu. I think you will lose all the data on the drives when you configure the RAID array, though.

---

### Post by rapiscan on 2008-03-06
Can you post the make/model of your motherboard?  Although I could be wrong, I don't think your motherboard has a hardware raid controller.  Motherboard manufacturers are sort of misleading with this, when they say they support raid.

---

### Post by koenn on 2008-03-06
> **jas168 said:**
> 
my setup is raid 0 mirror.


there's no such thing as a raid 0 mirror
raid 0 is a striped set, i.e. data is spread over multiple disks : no mirroring, just more disk space and faster access

raid 1 is a mirror

there are also combinations of raid0 and raid1 (raid 0+1, or raid 1+0, aka raid10) but they require more than 2 disks so that's robably not your case. 

You risk getting well-intended but wrong advice if you're inaccurate or confusing in your description.

---

### Post by soulreaper76 on 2008-03-06
I had a the same issue

it seems that hardware mirror using an onbord RAID controller does not act the same for Ubuntu as it does windows. must be a drivers issue.

i have 2 servers, 1 has a motherboard with integrated RAID 0,1 controller set to mirror. The other has a add-in RAID card 0,1 set to mirror. 

the one with the Add-in works like i would expect it. the onboard one shows Ubuntu both drives as if they where not a mirror. 

wish I had a fix for you, i just ended up using single drive and running backup software as this was not a mission critical server.

---

### Post by koenn on 2008-03-06
sounds like a "fake Raid".
A true hardware raid would always present a mirrored set as 1 disk to the OS - no way the OS, any OS,  could see beyound the raid controller to know that there are actually 2 or more physical disks.
A fake raid, however, is more like a controller with multiple channels; and the actual raid is created by software (running of a chip, i suppose, rather than as a program - the latter would be called a software raid.)

This may shed some light :
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
a search for fakeraid in the forums will also bring up quite a few threads of other people dealing with fake raid

---

