---
title: "HowTo Disable IO APIC in Vbox after install guest Windows to improve performance"
date: 2009-11-18
forum: Virtualisation
---

### Post by Markkreuzz on 2009-11-18
**[COLOR="Red"]!!!UPDATE!!![/COLOR]**[COLOR="Red"](11-20-2009): I tried some preliminary test on 3.0.12 like playing flash in firefox 10!!! Result was disappointing... Playing flash videos lags and stutters barely watchable. Tried disabling it again and voila!!!! it struggles a bit but everyting is watchable!!!! Even much smoother when I used IE8. I even tried the **VEOH** webplayer (^^_).... [/color]

**[COLOR="Red"]!!!UPDATE!!![/COLOR]**[COLOR="Red"](11-19-2009): The new version Vbox 3.0.12 r54655 doesn't slow my system down as it used to w/ IO APIC enabled, so I suggest you try updating first before going through this guide.... -will do some test to see the difference w/ IO APIC disabled and try to post it later[/COLOR]

:KS:KS
**I.Introduction**


Do you ever feel that your windows guest install is a bit sluggish in Vbox?
Slow, lagging. Tried increasing the RAM and still feels slow?

WELL mine did! Until... I disabled IO APIC ;) (warning!!! disabling it improperly might trigger Armageddon on your pc) :shock:... 
And yes it improved my guest windows performance.

I was fiddling around the configs trying to to figure out some other problem im having and stumbled upon this nifty little **_[[COLOR="DarkOrange"]guide[/COLOR]]("http://forum.virtualbox.org/viewtopic.php?f=2&t=21480&start=0")_** 
which i didn't find any similar post here in ubuntuforums.
 So, to help my fellow users i created this thread,. also just in case that howto suddenly disappear from the net.
 All credits go to **sleewok** of virtualbox.org.


**II. Understanding IO APIC**


**What is IO APIC?**- here is what [[COLOR="DarkOrange"]**Microsoft says**[/COLOR]]("http://www.microsoft.com/whdc/archive/io-apic.mspx"). -and i didn't **get** any of that.:P All i know is it has something to do with Interrupt Controllers and multi-CPU support.

**Why Enable the IO APIC option?** - here is what [**[COLOR="DarkOrange"]Virtualbox.org says[/COLOR]**]("http://www.virtualbox.org/wiki/Migrate_Windows")
 > "A standard installation on a modern physical PC or VMware will usually result in Halaacpi.dll being chosen as most systems nowadays have an IO APIC and VMware chose to virtualize it by default"
Ok. From what ive gathered it says almost every modern native install have IO APIC enabled. And  Disabling IO APIC on an existing install will wreak havoc on the system.

**Why Disable It?** - because its slow... and says so right here.
[IMG]http://i219.photobucket.com/albums/cc28/Markkreuzz/Ubuntuforums/APIC2.png[/IMG]
 And yes the change is dramatic after disabling it but then again YMMV.

So our main objective is to increase virtualbox performance by PROPERLY disabling IO APIC. WARNING!!! Doing it wrong will trigger a nuclear reaction in your guest install!!!  
Oh and pls. read the disclaimer below;).


**III. Forcing IO APIC to disable after a Windows Install**
O.K. Here is the guide. Copied and pasted for my* convinience :D.

> 
_**How to force IO APIC to disable after a Windows Install:**_

[LIST]
[*]Boot the Guest OS
[*]Go to Device Manager, and click on "Computers"~>
[*]Select the Properties of ACPI Uniprocessor PC ~>
[*]Click on the Driver tab, select Update Driver, ~>
[*]Click on the "Install from list or specific location"~>
[*]Click "don't search I will choose what driver to install" ~>
[*]In the window find and click on "Advanced Power and Configuration Interface (ACPI) PC" then click next ~>
[*]Click "finish" after Windows loads the new drivers. You may need your CD.(I didn't)~>
[/LIST]
Now click Close to exit those property pages, Windows will tell you to Reboot. DO NOT REBOOT! SHUTDOWN THE GUEST

**Once the guest is shutdown you need to change the settings of the VM. **

[LIST]
[*]Changing the IO APIC Setting within VirtualBox will not work. It keeps re-enabling the setting. 
[*]Close VirtualBox and open your guest machine's XML configuration file in a text editor. 
[*]Find the setting <IOAPIC enabled="true"/>
[*]Change value from "true" to "false"
[*]Save the file and exit the text editor
[*]Right-click on the XML file and open the properties. 
[*]SET THE XML FILE TO READ ONLY (this will not allow Virtualbox to re-enable IO APIC)
[*]Start VirtualBox and Boot the guest OS
[*]After windows boots it should install some additional drivers and ask you to reboot again.
[/LIST]

IO APIC should now be disabled

If you want to change any settings within VirtualBox you'll need to remove the read-only attribute from the Machine XML file.


**[COLOR="Blue"](To-Do)[/COLOR]**: 
[LIST]
[*]A howto to re-enable IO-ACPI in windows.
[*]Include some test/benchmark  w/ the new version(v3.0.12) vs. the previous one (v3.0.10)- [COLOR="Red"]any suggestions for benchmark apps?[/COLOR].
[/LIST]
*My system that I used this on is Ubuntu 8.04 Hardy, Virtualbox 3.0.10 r54097, Windows XP SP3 all 32-bit, AMD Opteron 165.

**The Original Poster tested this on his Windows 7 Install and I used this on my Windows XP install. So far everything works fine, couple of updates and reboots still fine.

***Disclaimer: I cannot guarantee your safety. Should you follow this guide you should agree first that I shall not be responsible if anything goes wrong e.g. loss of data, hair loss, STD, Diarrhea, etc.

---

### Post by dcstar on 2009-11-18
> **Markkreuzz said:**
> 
Do you ever feel that your windows guest install is a bit sluggish in Vbox?
Slow, lagging. Tried increasing the RAM and still feels slow?

WELL mine did! Until... I disabled IO APIC ;) (warning!!! disabling it improperly might trigger Armageddon on your pc) :shock:... 
And yes it improved my guest windows performance.
.......

Chances are all you did was disable the multiprocessor use in the client by disabling IO APCI.

VM environments do not seem to handle giving clients more than one host processor to use too well, so by turning off IO APIC you effectively prevent the client VM from using more than a single processor.

In VMWare Server you can just specify how many processors to allow a client to use in each client configuration (and one processor still works better than allowing multi-processors) - no need to muck around with anything else.

---

### Post by Markkreuzz on 2009-11-19
> **dcstar said:**
> Chances are all you did was disable the multiprocessor use in the client by disabling IO APCI.

VM environments do not seem to handle giving clients more than one host processor to use too well, so by turning off IO APIC you effectively prevent the client VM from using more than a single processor.

OOh. thanks for your insight. 


Well my CPU is an Opteron 165 and afaik it doesn't support hardware VT which is why Vbox only allows 1 CPU. And i don't know if enabling it on multi-cpu VT capable system will improve their performance.. 
And as you have said its consistent with the information I gathered regarding multi-cpu and virtual machines. They see much better stability and performance using 1 CPU.

> In VMWare Server you can just specify how many processors to allow a client to use in each client configuration (and one processor still works better than allowing multi-processors) - no need to muck around with anything else.
-Well its not like virtualbox doesn't have a setting to allow use of more than 1 CPU. and in VMware IO-APIC is enabled by default.


[B]
!!!UPDATE!!![/B]: There was an update just now(*grumbles*) regarding the IO-APIC overhead [**[COLOR="DarkOrange"]HERE[/COLOR]**]("http://www.virtualbox.org/wiki/Changelog"). And i have tried it (enabling IO ACPI again) and so far its pretty stable and the system responsiveness is much better than the old one.... Will try now to do some benchmark to see if it still worth it to disable IO APIC, but may take time(pretty busy ATM).

---

