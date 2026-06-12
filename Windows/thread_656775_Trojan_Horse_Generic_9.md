---
title: "Trojan Horse Generic 9"
date: 2008-01-02
forum: Windows
---

### Post by gary1163 on 2008-01-02
Help! 
I'm trying to help a buddy whom is running a Free Home Edition AVG Anti_Virus program, It appears to be runnig well except for this one Threat Detected that cannot be healed. A Trojan Horse Generic 9-AEKBO8, it seems to be affecting c:\windows/systems32/cmd.dll. I was told to go into My Computer, click on Windows, find the Systems32 folder , delete it, then empty out of the Trash/Recyle Bin. Does this sound safe to do? Should I do this if Safe Mode if so? My thinking is that the AVG can only detect the threat. Or is there some other way I should handle this issue? Thanks for any help.

Gary:
confused:

---

### Post by Tyke91 on 2008-01-02
DO NOT DELETE YOUR WINDOWS SYSTEM 32 FOLDER.

it holds a bunch of vital stuff for your PC. (it is similar to typing rm -rf /  in linux)


other than that... i can't help you

---

### Post by twin_57103 on 2008-01-02
Most of the major anti-virus companies (Symantec, McAffee, etc.) have posted solutions & often have downloads to help recover from viruses.  Unfortunately, some of them can be very difficult to permanently eliminate - I have reformatted more than one computer to get rid of viruses.  Try Norton Virus removal page [http://www.symantec.com/norton/security_response/removaltools.jsp]("http://www.symantec.com/norton/security_response/removaltools.jsp") and see if you can find the specific virus.

---

### Post by GuitarRocker2562 on 2008-01-02
DO NOT DO THAT

try scanning in safe mode, or just leave it alone.

---

### Post by gary1163 on 2008-01-02
Ok I won't delete the WINDOWS32 FOLDER didn't think that sounded right..I'll try the link you sent, also I 'll try scannng in Safe Mode..Let you know what happens..

Thanks All

---

### Post by stinger30au on 2008-01-03
if avg wont get rid of it, try installing the one month free version of kaspersky labs kav and it will get rid of it.

---

### Post by digital_exhaust on 2008-01-03
Grab the 30 day trial of [NOD32]("http://www.eset.com/"), disable system restore,run it in safe mode and that should do the trick for you. I personally would simply leave system restore disabled, but that's up to you.

 If NOD (or Kaspersky, both are good) can't fix it, you'll likely be looking at a clean install.

---

### Post by gary1163 on 2008-01-05
Do I go into MSCONFIG (systems configurations) to disable Systems Restore? and should I do all of this in Safe Mode, then Restart in Normal  Mode once I'm done?

Thanks
Gary 

:guitar:

---

### Post by digital_exhaust on 2008-01-05
> **gary1163 said:**
> Do I go into MSCONFIG (systems configurations) to disable Systems Restore? and should I do all of this in Safe Mode, then Restart in Normal  Mode once I'm done?

To disable system restore, go to Control Panel, System, System Restore and check the box next to "Disable System Restore for all Drives" and then re-boot. 

Hope it helps...

---

### Post by KoolBeans on 2008-01-06
Trojan horse.generic could be a false positive. or a heuristic detection.
I suggest getting help from a forum that specializes in windows security. 

[http://www.castlecops.com/forums.html](http://www.castlecops.com/forums.html)
[http://www.wilderssecurity.com/](http://www.wilderssecurity.com/)

For a double check of the system, try Micro World Anti Virus. This will not clean in trial mode. but will report a true state whether you are infected. Because it doesn't clean it isn't a threat to a trojan app.
Troj writers attack the progs installed that can clean them. Trojans can determine if security apps installed then what security apps installed so workaround security apps.

Also, TrojanHunter 5.0 free 30days and A2malware 3.whatever free.
A2 A.K.A. EMSI software has a forum for fixing problems even if it's prog doesn't detect anything.

Also, most of the Trojans target windows via internet explorer while surfing, sites like, Crackz, Warez, Keyz, Porn, P2P file sharing, or sites that advertise these. Disable IE as default browser and use a browser that does not contain the Trident Layout Engine, like Netscape 7 and below or Opera. Firefox Contains the Trident Layout Engine and Gecko Layout Engine. Not sure if the linux version of FF has both.

It is basically a religious thought police battle.
You can not legislate goodness into the hearts of men.

Now, if I could just get my install of Ubuntu working I can watch some Porn](*,)

System Restore doesn't matter in shaking an infection, on the whole. System Restore Tracks Installs which can include the infector app. But, the infection is loaded buy some type of document like XML and zip. Documents are not erased by System Restore, they remain after a roll back. See.

---

