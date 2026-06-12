---
title: "This is interesting"
date: 2005-11-02
forum: Server Platforms
---

### Post by Efwis on 2005-11-02
just so you all know,

I recently, today, did a full AV scan on my ubuntu HDD with Aegis AV. results were one virus.

W32/Magistr.a@MM here is the info on it [W32/Magistr.a@MM info](http://vil.nai.com/vil/content/v_99040.htm)


**usr/lib/win32/vp31vfw.dll** this file is the infected one.

 I got the codecs from the source listed in the WIKI. 

Make sure you don't share this file with someone on a Windows OS!!!!

---

### Post by wylfing on 2005-11-02
Did you report your findings to the package maintainer? That would be a good step to take.

---

### Post by Efwis on 2005-11-02
not yet, that was going to be my next step, finding out who maintains the package and then notifiing them.

Of course the biggest problem is that I used the secondary link in the wiki, so I'm not sure where it was downloadig from at the time I installed the codecs. Plus there are more wiki installation instructions, so I'm not even sure which one I used lol

---

### Post by fishfork on 2005-11-10
Hi, did you get anywhere with this? It would be useful if you could post the md5sum and file size of this file so that people can compare it with the versions on their system. I certainly have that file on my machine - it came with w32codecs from the Marillat repository.

---

### Post by Efwis on 2005-11-10
unfortunately I don't have the md5sum, my installation got corrupted, by my own hand, so I had to reinstall. 

I do know that the link for the w32codecs in the wiki are not the same as what I had. actually when I went and installed the codecs they didn't install from the wiki link. so now I have to find another source for them. maybe I didnt' use the wiki links afterall the first time. it's all a blur to me know since I have recently had a death in the family.

---

### Post by Efwis on 2005-11-10
update, I just went ahead and scanned the system again with the codecs from the wiki link, as it turned out they did work, and it is infected also. 

> Hi, did you get anywhere with this? It would be useful if you could post the md5sum and file size of this file so that people can compare it with the versions on their system. I certainly have that file on my machine - it came with w32codecs from the Marillat repository.

when I ran the following code
```
md5sum /usr/lib/win32/vp31vfw.dll
```

This is what I got for the md5sum
```

d1fea82b115492d4a8ba002e2db31412  /usr/lib/win32/vp31vfw.dll
```

the size of the file in my system is

 452.0 KB in size.

---

### Post by fishfork on 2005-11-10
Well, the file on my system has the exact same md5sum and size. I submitted it to virustotal.com and these are the results (the formatting's a bit messed up, sorry):

```
This is a report processed by VirusTotal on 11/10/2005 at 22:17:36 (CET) after scanning the file "vp31vfw.dll" file.

Antivirus	Version	Update	Result
AntiVir	6.32.0.6	11.10.2005	no virus found
Avast	4.6.695.0	11.09.2005	no virus found
AVG	718	11.03.2005	no virus found
Avira	6.32.0.6	11.10.2005	no virus found
BitDefender	7.2	11.10.2005	no virus found
CAT-QuickHeal	8.00	11.10.2005	no virus found
ClamAV	devel-20051108	11.10.2005	no virus found
DrWeb	4.33	11.10.2005	no virus found
eTrust-Iris	7.1.194.0	11.10.2005	no virus found
eTrust-Vet	11.9.1.0	11.10.2005	no virus found
Fortinet	2.48.0.0	11.10.2005	no virus found
F-Prot	3.16c	11.10.2005	no virus found
Ikarus	0.2.59.0	11.10.2005	no virus found
Kaspersky	4.0.2.24	11.10.2005	no virus found
McAfee	4625	11.10.2005	no virus found
NOD32v2	1.1283	11.10.2005	no virus found
Norman	5.70.10	11.10.2005	no virus found
Panda	8.02.00	11.10.2005	no virus found
Sophos	3.99.0	11.10.2005	no virus found
Symantec	8.0	11.10.2005	no virus found
TheHacker	5.9.1.032	11.10.2005	no virus found
VBA32	3.10.4	11.10.2005	no virus found

VirusTotal is a free service offered by Hispasec Sistemas. There are no guarantees about the availability and continuity of this service. Although the detection rate afforded by the use of multiple antivirus engines is far superior to that offered by just one product, these results DO NOT guarantee the harmlessness of a file. Currently, there is not any solution that offers a 100% effectiveness rate for detecting viruses and malware.
```

It looks like it's probably a false positive with Aegis. I'm not an expert on viruses, but I think it would be unusual for one to infect a .DLL (though it's no doubt possible). Anyway, looks like there's probably nothing to worry about. Might be worth reporting it to the guys at Aegis.

Cheers,

Ben

---

### Post by Efwis on 2005-11-10
well like you I did an online scan of the file itself, based on what it stated was the same results as yours. I shall notify Aegis immediately so that they can get this corrected.

sorry for the mis-info, being a malware removal expert at a number of forums I know better then trust one source.[img]http://www.iamviet.com/forum/images/smilies/smilie_yellow_icon_redface.gif[/img]

> I'm not an expert on viruses, but I think it would be unusual for one to infect a .DLL (though it's no doubt possible). 

just for informational purposes, it is possible to infect a .dll file, and no one would be the wiser unless they knew what the file size is supposed to be as well as looking for the increased file size. which 90% of those on the internet don't.

```

 AntiVir  	
Found nothing
ArcaVir 	
Found nothing
Avast 	
Found nothing
AVG Antivirus 	
Found nothing
BitDefender 	
Found nothing
ClamAV 	
Found nothing
Dr.Web 	
Found nothing
F-Prot Antivirus 	
Found nothing
Fortinet 	
Found nothing
Kaspersky Anti-Virus 	
Found nothing
NOD32 	
Found nothing
Norman Virus Control 	
Found nothing
UNA 	
Found nothing
VBA32 	
Found nothing
```

---

### Post by Hairy_Palms on 2005-11-16
aegis seems to fin the exact same virus, W32/Magistr.a@MM virus, all over my system, but no other scanner does, i pretty sure this is a false positive according to aegis i have 74 instances of it, and the windows partiton doesnt even connect to the internet. so i dont know what its talking about

---

### Post by Efwis on 2005-11-16
I emailed the author for the file::scan engine that is used on Aegis-Virus-Scan. Have yet to hear back from them regarding this.

---

### Post by mike4ubuntu on 2005-12-12
I've been finding the same thing with Aegis.  It seems to give a lot of false positives.

---

### Post by towsonu2003 on 2005-12-13
Did anyone copied this file to a windows machine and runned a couple of local scans with stuff like McAfee and Symantec Norton?

---

### Post by Efwis on 2005-12-13
[QUOTE=towsonu2003]Did anyone copied this file to a windows machine and runned a couple of local scans with stuff like McAfee and Symantec Norton?[/QUOTE]
no we haven't, the online scans like I used and fishfork used use the same scanning engines and the same heuristics as Norton and Mcafee, If everyone is really that worried about it I can copy them to my VM on Windows and test them, but I can say with fair certainty that those are false readings from the Aegis virus scanning engine.

---

### Post by Irony on 2005-12-18
I scanned my win32 file with Norton (latest updates), it checked 126 files (including vp31vfw.dll) and found no threats.

---

### Post by DoorGunner on 2005-12-26
From what i have read ....the Mistra a is primarily a file that infects various win32.exe files. All the Mistra virus detections were on .dll's accept one in my case. However, I ran a virus scan of my windows cdrive using my f-secure and found no problems. According to the developers site the problem lies in the engine itself and to contact them:not him. [http://jodrell.net/projects/aegis](http://jodrell.net/projects/aegis)

My solution was to switch over to F-Prot  (and also amavis or P3Scan). It works  much better. I dont really get a warm fuzzy when the engine doesnt work flawlessly. I think its just asking for trouble. This of course is just my opinion. 

F-Prot is avialable in synaptic packages. (fs-linux-ws, f-prot-installer, amavis-ng or p3scan)

---

### Post by xtacocorex on 2005-12-27
I'm pretty sure that a virus in a Windows .dll file that is being used on Linux won't infect Linux at all due to the filesystem difference.

I could be wrong though.

But it is better to be safe than sorry. Definately subscribing to this thread to keep up on the news.

---

### Post by davebgimp on 2006-01-18
[QUOTE=Efwis]just so you all know,

I recently, today, did a full AV scan on my ubuntu HDD with Aegis AV. results were one virus.

W32/Magistr.a@MM here is the info on it [W32/Magistr.a@MM info](http://vil.nai.com/vil/content/v_99040.htm)


**usr/lib/win32/vp31vfw.dll** this file is the infected one.

 I got the codecs from the source listed in the WIKI. 

Make sure you don't share this file with someone on a Windows OS!!!![/QUOTE]

I had the exact same experience recently. Same dll, same virus. Aegis found it.

---

