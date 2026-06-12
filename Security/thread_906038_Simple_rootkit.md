---
title: "Simple rootkit?"
date: 2008-08-31
forum: Security
---

### Post by Camilia on 2008-08-31
I would like a simple rootkit to scan my computer with. For after I do a lot of surfing for research I like to scan my computer.  In windows I use superantispyware.  Been reading that rootkits are used to scan in ubuntu. Has anyone got any suggestions?

---

### Post by chewearn on 2008-08-31
rkhunter

```
sudo apt-get install rkhunter
```

---

### Post by Camilia on 2008-08-31
> **AstalaVista said:**
> rkhunter

```
sudo apt-get install rkhunter
```

I pasted and got directions to remove items. Did so.

Pasted sudo rkhunter -c -sk and got 
/usr/bin/mail                                            [ Warning ]
 Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]
One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)
What does this mean? What do I do?

---

### Post by lovinglinux on 2008-08-31
> **Camilia said:**
> I pasted and got directions to remove items. Did so.

Pasted sudo rkhunter -c -sk and got 
/usr/bin/mail                                            [ Warning ]
 Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]
One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)
What does this mean? What do I do?

It means you need to open /var/log/rkhunter.log file to seen further information regarding the warnings.

Could someone explain what "-c" and "-sk" parts of the above command does?

Is there any other usefull command that I should know about other than "sudo rkhunter -c -sk" to search for rootkits?

---

### Post by Promille on 2008-08-31
> **lovinglinux said:**
> It means you need to open /var/log/rkhunter.log file to seen further information regarding the warnings.

Could someone explain what "-c" and "-sk" parts of the above command does?

Is there any other usefull command that I should know about other than "sudo rkhunter -c -sk" to search for rootkits?

-c  Check the local system
-sk Show the summary of system check results

---

### Post by lovinglinux on 2008-08-31
> **Promille said:**
> -c  Check the local system
-sk Show the summary of system check results

Thank you!

---

### Post by insane_alien on 2008-08-31
just a note to anybody not sure on what a rootkit is:

The OP doesn't want to scan his computer WITH a rootkit, he wants to scan his computer FOR rookits using a rootkit detector.

rootkits are a bad thing and you don't want to install one.

---

### Post by Perfect Storm on 2008-08-31
I think it's a typo/grammar error, as it seems the following application was the thing he/she looked for.


But we'll keep an eye it in any case.

---

### Post by insane_alien on 2008-08-31
> **Artificial Intelligence said:**
> I think it's a typo/grammar error, as it seems the following application was the thing he/she looked for.


But we'll keep an eye it in any case.

those are my thoughts too just thought i'd mention it incase someone accidentally installed a rootkit on their computer.

---

### Post by MJWitter on 2008-08-31
I think the confusion came in from another thread: [Get your logs/rootkit reports and send it to email daily]("http://ubuntuforums.org/showthread.php?t=900686").  Think it might just be a misunderstanding of terms..

---

### Post by Camilia on 2008-08-31
> **insane_alien said:**
> just a note to anybody not sure on what a rootkit is:

The OP doesn't want to scan his computer WITH a rootkit, he wants to scan his computer FOR rookits using a rootkit detector.

rootkits are a bad thing and you don't want to install one.

Does doing this sudo apt-get install rkhunter install a rootkit or rootkit detector?

---

### Post by Camilia on 2008-08-31
> **lovinglinux said:**
> It means you need to open /var/log/rkhunter.log file to seen further information regarding the warnings.

Could someone explain what "-c" and "-sk" parts of the above command does?

Is there any other usefull command that I should know about other than "sudo rkhunter -c -sk" to search for rootkits?

How do I open /var/log/rkhunter.log 

I have been reading about rkhunter and checking rootkit at other post and only got more confused. Please keep the answers simple for I don't know much computer language. I leaned on wordperfect. Wasn't until I kept getting adware in windows xp, recently, I decided I had to educate myself.

---

### Post by insane_alien on 2008-08-31
> **Camilia said:**
> Does doing this sudo apt-get install rkhunter install a rootkit or rootkit detector?

a rootkit detector.

i know this would probably seems obvious that a newbie would install this but i have seen a newbie actually track down a virus via google to install for virus protection instead of anti virus software.

it comes down to that old adage about idiot proofing and nature inventing better idiots.

---

### Post by NullHead on 2008-08-31
You could always read the manual for rkhunter;```
man rkhunter
```

Reading all that could be a bit confusing, but once you get familiar with rkhunter some more, I'm sure the man page will make more sense.

---

