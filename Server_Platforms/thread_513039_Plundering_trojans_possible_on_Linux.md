---
title: "Plundering trojans possible on Linux?"
date: 2007-07-30
forum: Server Platforms
---

### Post by resander on 2007-07-30
The win32.grams trojan plunders e-gold accounts on Windows systems. It sits and waits for a user to enter the website address of egold and the password. Then it takes over (don't know how - maybe it spawns another browser process or hijacks the user's browser process) and opens an invisible 0 x 0 window and transfers the balance to another account (opened under false name with ATM card probably). When control returns to the user there is no money left in the account. As far as egold is concerned this is a normal user-initiated transaction. Similar techniques can be used for attacking PayPal accounts and Internet banking accounts.

There is no defense against this type of trojan other than not having it on the computer when you access your money or bullion account.


I am a Linux newbie so I cannot figure this out myself, so

1.  assuming a trojan of this kind has found its way into a Linux system,
     e.g. downloaded as a trojan masquerading as hex calculator, jpg image,
     etc, is there any way it can do the plundering on a Linux system?

2.  are there ways to stop the trojan doing mischief if it is already on
     the system?
    

Here is more info about the e-gold trojan:

[www.secureworks.com/research/threats/grams/](www.secureworks.com/research/threats/grams/)

---

### Post by eentonig on 2007-07-30
Possible? Yes. As long as users are insecure, an OShas always the risk to become infected.

Likely? No. 
- For one, Windows spyware/virusses/malware/etc are useless in a linux environment. Just as you can't run pragram X in linux, it is impossible for them to execute.
- Second, Every file in linux can be executable. But, if you download a file, default values are NOT to be executable. So you as a user will need to assign execute privileges to it. So at that time, you know something odd is going on, when a .jpg wants execute permissions.
- Chances of infection are higher by installing 'untrusted' applications. But as long as you stick with the repo's, they are close to none. And even third party repo's should be safe.

Possible damage and spreaad? Close to none.
- Most off the software is open source. Meaning, everybody can review the code that builds up the program. If someone manages to introduce a virus and it gets detected, thousands of programmers can look at the program and write a patch. Usually, within hours of it being released, a safe version will exist.

---

### Post by resander on 2007-07-30
Thanks Eentonig, 

Windows executables are in Portable Executable (PE) file format that would not be understood by a Linux loader. A Windows pest would at least have to be recompiled and rebuilt before it can run on a Linux system.

Trojans need to be restarted on bootup. In Windows this is achieved by putting the program .exe name into a special place in the Registry. A Trojan sets this registry entry on initial infestation. Is there an equivalent auto restart mechanism in Linux?

The e-gold plundering trojan in some way 'attaches' itself to the user browser process and then reads the content of the browser fields (I think) in order to synchronize itself for attack. This could be achieved by a keystroke logger too. In Windows there is an API function that allows a process to spy on the key strokes sent to another process (although this may not have been the intention by the designers). Is this possible in Linux?

On Windows I am configuring the ZoneAlarm firewall to allow the browser and email clients to freely access Internet. ZoneAlarm will popup a confirm dialog if other processes try to acess Internet, for example trojans trying to 'phone home'. Is this feature available in Ubuntu?

BTW Entonig på svenska betyder också eentonig.

---

