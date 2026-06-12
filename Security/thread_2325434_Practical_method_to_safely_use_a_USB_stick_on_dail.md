---
title: "Practical method to safely use a USB stick on daily basis"
date: 2016-05-22
forum: Security
---

### Post by johnmne on 2016-05-22
Which practical method exist for **safely** using a USB stick on a daily basis ?

With emphasis over the following:

[LIST]
[*]I'm well aware that nothing is 100% secure when connecting a USB stick to PC. 
[*]It is on a daily basis - means that it has to be relatively quick, easy and convenient. 
[*]The USB stick may be plugged also to other PCs - might be big networks (work/college/etc.) 
[*]The method should cover all the malware that an average person has access to.  
By average person I mean:
[LIST]
[*]Someone who doesn't have a deep understanding about security/technology, so he'll probably **download** the malware from someplace on the net, or **buy at low price**. 
[*]Someone who knows to program, but because that he lacks a deep understanding about security, he will program relatively **simple malware**. 
[/LIST]
    
[/LIST]

I have read the following: [https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
But it seems outdated (at the bottom: "last edited 2011-04-09 01:19:26 by k.dejong")

Additional specific questions:
[LIST=1]
[*]Since when Ubuntu has stopped autorun files from USB drive by default ? (also referring to "noexec mount option" of USB devices)
[*]Does Nautilus considers "Local files" as files which are stored in a USB drive? (Protection against files preview vulnerabilites)
[*]Would the method be any different if we were at one year ago (May 2015) and using Ubuntu 12 ?
[/LIST]

Edit:

As a **defense against the "rubberducky" attack** (USB which look like a storage but is actually a keyboard):  
Ubuntu could allow only a single keyboard to be used at a single time - which is the keyboard that was connected first.  
Any additional connection of a keyboard/mouse via USB should require admin privileges.

---

### Post by johnmne on 2016-05-23
Why no one answers? Aren't you interested?
Especially about my idea to protect Ubuntu/Linux from the "rubberducky" attack (especially on normal Desktop computers), because that normally only a single keyboard and mouse should be used at a single time.
It should be quite easy to implement and boosts Linux/Ubuntu regarding its security aspect!

---

### Post by ventrical on 2016-05-27
Yes .. we are interested.. well .. at least I am. I usually post in Ubuntu Development Version Testing. If you  search carefully you will see that I had made contributions in security forums also. My last security venture was with COMODO AntiVirus  for Linux (Ubuntu). Uhh.. I may have posted in LinuxOSchat or Cafe...

Conventional Malware detection with COMODO, AVG and CLAMAV is all possible with Ubuntu graphical user interface. USB sticks are , unfortunately, not mounted directly and have to be scanned by mounting the media descriptor but if you have EICAR test set in your USB /HOME then COMODO will detect it.

COMODO has real time scanning so if you are surfing and a mutex or other malware tries to enter the system over the wire then the alerter will pop-up!! The thing is .. there is virtually benign traffic because Ubuntu is , by nature, an antimalware beast! :) .. what .. 8 years for me with Ubuntu and nothing .. but if you mount a Windows XP HDD or USB that has malware .. it is guarenteed  that if there is malware on your Windows HDD (which there always is) COMODO or AVG will detect it where  it will not be detected while running a Windows OS. I think this may be perhaps why there is slow response to your post .. because is is *extremely* rare for most forms of known malware to interfect ubuntu.  it is probably the best free gift from Canonical developers.

Regards..
UDV Testing, Team Captain

---

### Post by ventrical on 2016-05-27
ie;

[http://ubuntuforums.org/showthread.php?t=2172863&highlight=COMODO](http://ubuntuforums.org/showthread.php?t=2172863&highlight=COMODO)

---

### Post by johnmne on 2016-06-05
Hi ventrical,

First - thank you for the answer! :)

Second, I think that this kind of security should be built into Linux core or perhaps its USB drivers (not sure which one).
This is a very basic security feature, don't you think?
On the connection of a device that has a physical access, the OS should permit the device to perform actions based on what the users allows it to do. 
Does the user allow a USB flash drive to act like a USB keyboard? Probably not!
Also, if from a single USB port - the OS detect a USB flash drive AND a USB keyboard - this kind of event should light a red alert (!).

Thus, the OS should ask the user: 
Do you allow the USB stick to act as:
(1) ..
(2) ..
(3) ..

While the options (1) to (3) are the devices that the USB stick presents itself to the PC.

---

### Post by ventrical on 2016-06-05
Good point , but I have never seen this instance (usb-keyboard) be misconstrued for an hdd flash drive. I'll have to review this again.

edit:

Ok .. I see your point now. With Microsoft Windows we will will always see a USB device in the tray and then the device will try to be installed with the graphical wiget spin.. etc. With Ubuntu there is no widget spin in the tray, however, Kubuntu may offer this which is a graphical bent such as windows.  The ubuntu-core itself is protected by the PolicyKit as are other critical files and can only be affected if root permissions are given. Also the suggested Canonical repositories are walled and the applications can be safeguarded by Apport. So there are many layers of security.

 Of course this does not answer your question and I am only assuming atm that the kernel is impervious to such attack (rubberducky).

  Speaking from my own experience I have never seen such an instance (8 years of everyday use of ubuntu). Could you point me to a case in point?

Also .. if you have a recommend of what could be updated in the wiki-link your referred then please let me know.  

  I plan to attempt an experiment time permitting to emulate this problem or at least investigate it more thouroughly.




Regards..

---

### Post by johnmne on 2016-06-08
Actually there is available (to the general public) a relatively cheap product which does exactly the rubberducky attack!
See the link (found it by searching "rubberducky" in google):
<url snipped>
That is cross-platform due to  USB's nature.

Therefore I suspect that Ubuntu/Linux **fail to protect against that**,
 because that the "rubberducky" attack can "type" the following commands: 

[LIST=1]
[*]Copy-paste a bash script 
[*]chmod it so that it will execute (under normal user - NOT root) 
[*]malware is active... 
[/LIST]

Note that **by default** - Ubuntu's **firewall is disabled**, therefore allowing an **easy access to the attacker** via internet.

What do you mean by "point me to a case in point" ?
(Unless the link above answers your request)

The general strategy for Linux - regarding **any direct physical access devices** - should be that the device is allowed to be used only upon the permission of the root user.
Then, the normal user would be allowed to choose which devices (and how much) are allowed in specific physical ports.
By default, only a single keyboard & mouse should be used! Unless the users choose otherwise - then it will configure the system to allow a device which has a specific ID (which is an ID that is similar to MAC address or something...).

I appreciate your concern regarding this matter. 
This is an utmost concern for linux developers, for it is an easy breach using social engineering - which can be relatively easily prevented with proper permissions system.

Best regards,

---

### Post by ventrical on 2016-06-08
> **johnmne said:**
> Actually there is available (to the general public) a relatively cheap product which does exactly the rubberducky attack!
See the link (found it by searching "rubberducky" in google):
<url snipped>
That is cross-platform due to  USB's nature. 

The link you have pasted also points to information that will help crack passwords .. etc..and since I have signed the Ubuntu Code of Conduct I cannot help disseminate this information.


> 
Therefore I suspect that Ubuntu/Linux **fail to protect against that**,
 because that the "rubberducky" attack can "type" the following commands: 

[LIST=1]
[*]Copy-paste a bash script 
[*]chmod it so that it will execute (under normal user - NOT root) 
[*]malware is active... 
[/LIST]

Note that **by default** - Ubuntu's **firewall is disabled**, therefore allowing an **easy access to the attacker** via internet.



If you present this as a proof of concept then perhaps I could test on a dumb terminal.

> 
What do you mean by "point me to a case in point" ?
(Unless the link above answers your request)

Question answered :)
 

> 
The general strategy for Linux - regarding **any direct physical access devices** - should be that the device is allowed to be used only upon the permission of the root user.
It is read only until the policykit authenticates a write either to the USB drive is self or the host OS.


> 
Then, the normal user would be allowed to choose which devices (and how much) are allowed in specific physical ports.
By default, only a single keyboard & mouse should be used! Unless the users choose otherwise - then it will configure the system to allow a device which has a specific ID (which is an ID that is similar to MAC address or something...).

I appreciate your concern regarding this matter. 
This is an utmost concern for linux developers, for it is an easy breach using social engineering - which can be relatively easily prevented with proper permissions system.

Best regards,

 I appreciate your research and obvious expertise in this area. I have to agree that USBs are perhaps the new way of transmitting malware. With ubuntu we have had bugs but not malware. That would be with SDC (Startup Disk Creator) and gnome-disk-utility 'disks'. These bugs have been solved and it is now the standard method to restore images using 'disks'. We have a member who has a lot of expertise in this area and I will put up his link. Although it does not delve into  USB security as you do I think you might find it interesting reading on how USBs are detected and managed. 

[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)
[http://ubuntuforums.org/showthread.php?t=2213631](http://ubuntuforums.org/showthread.php?t=2213631)


 Please see screenshot. It is why I cannot partake  in this in this  forum publicly or privately.  You did nothing wrong here as I did ask you for a case in point and you obliged.

Best Regards..

---

### Post by ventrical on 2016-06-08
@mods

Is it against the Code of Conduct to test files for security purposes provided by the link of the OP?

Regards..

---

### Post by QIII on 2016-06-08
This thread is closed.  Whether or not any nefarious activity was intended, the discussion included some details about a product that most certainly can be used with ill-intent.  Even a discussion about how to provide protection against attacks can be used by unscrupulous readers if the nature of the attack itself is described.  We do not want the UF to become a resource for ne'er-do-wells.

Please refer to The [Ubuntu Forums Rules]("http://ubuntuforums.org/misc.php?do=showrules").

This discussion falls generally into this proscription:

> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

---

