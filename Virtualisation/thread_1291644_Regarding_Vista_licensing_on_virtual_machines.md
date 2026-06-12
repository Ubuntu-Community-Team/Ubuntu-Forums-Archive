---
title: "Regarding Vista licensing on virtual machines"
date: 2009-10-14
forum: Virtualisation
---

### Post by cnbiz850 on 2009-10-14
I understand from the web that OEM Vista Home can only be activated on one "device" (including virtual devices).  I don't really want to use Windows.  I plan to install Ubuntu on the new laptop that has the OEM Vista license (I haven't activated the pre-installed copy).  Then just for occasional needs, I install and activate Vista as a guest in a virtual machine (VirtualBox for instance) on Ubuntu.  I guess this would legalize my use of the Vista on the virtual machine.  Am I right?

Further question is:  If I later on choose to create a new virtual machine (on the same system replacing the old VM) and install Vista on it.  Vista would think that it is on a new "device" and so wouldn't get activated.  Right?  How can I create a VM that Vista sees as a same one (just as I reinstall it on the same hardware)?  In other words, what makes Vista decide whether it is the same device?

Any help please?  Many thanks.

==============

Found this solution: [http://ubuntuforums.org/showpost.php?p=7621560&postcount=8]("http://ubuntuforums.org/showpost.php?p=7621560&postcount=8")  It works for me.

---

### Post by cnbiz850 on 2009-10-15
Any comments please?

---

### Post by cnbiz850 on 2009-10-19
Anyone please help?

---

### Post by SoftPops on 2009-10-19
Not an ideal reply I'm afraid.
 
The licensing for Vista Home Basic and Home Premium states that installing in a Virtual Machine is not allowed.
 
Extract from Microsoft's license terms for Vista. See [http://download.microsoft.com/documents/useterms/Windows%20Vista_Ultimate_English_36d0fe99-75e4-4875-8153-889cf5105718.pdf](http://download.microsoft.com/documents/useterms/Windows%20Vista_Ultimate_English_36d0fe99-75e4-4875-8153-889cf5105718.pdf)
[FONT=TTE1762DC8t00][SIZE=2][FONT=TTE1762DC8t00][SIZE=2]> [FONT=TTE1762DC8t00][SIZE=2][SIZE=2][FONT=TTE1762DC8t00]USE WITH VIRTUALIZATION TECHNOLOGIES. [/FONT][/SIZE]
 

[/SIZE][/FONT][FONT=TTE173C830t00][SIZE=2][FONT=TTE173C830t00][SIZE=2]You may not use the software installed on the licensed device within a virtual (or otherwise emulated) hardware system.[/SIZE][/FONT][/SIZE][/FONT]


[/SIZE][/FONT][/SIZE][/FONT][LEFT][LEFT]For Vista Ultimate, there shouldn't be a problem. The license allows _one_ instance of Vista to be installed on the hardware it was supplied. The license allows Vista to be re-installed as often as required and the license reactivated without issue. I believe the only thing not allowed by the OEM license is a change in motherboard.[/LEFT]

 

[LEFT]Hope this clarifies.[/LEFT]

 
[/LEFT]

---

### Post by cnbiz850 on 2009-10-20
Thanks very much for the clarification.  Mine is Home Premium.

Guess I am not too much concerned about that controversial clauses in there.  I believe it will be challenged in court sooner or later because it is not reasonable and MS is using its monopoly power to bully the endusers.  What I want to make sure is to run it with only one copy on my machine and that copy runs on a VM on Ubuntu.  So what I am interested in is how to get it activated on the VM -- in other words, how to fool it into believing that it actually runs on a real hardware so it activates itself.

Any insights please.

---

