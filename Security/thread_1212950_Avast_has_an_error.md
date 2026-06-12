---
title: "Avast has an error"
date: 2009-07-14
forum: Security
---

### Post by rapattack on 2009-07-14
After I did a scan I got what is in the screen shot. I am unused to using an antivirus program in linux so I have no idea what this means and what to do about it when I right click. Would appreciate any advice.

---

### Post by sasho_zl on 2009-07-14
First of all avast can scan only for windows viruses and you don't need to scan your Linux partitions with it or any other antivirus program. Second the program needs to be run with root privileges to scan system files.

---

### Post by wojox on 2009-07-14
Looks like a glich or false positive,. .bash_history keeps all your bash commands so you can review, change, and reuse. You can always open it up and see what's in there.

---

### Post by rapattack on 2009-07-14
Oh really someone told me that Linux antivirus programs only scan for linux stuff....whatever that is because I don't know much about this field.
Ah but I am running it as user so I am not sure what you mean?

I don't know what it would mean even if I opened the bash command and what it would mean sorry!
I have used it but can't remember what for. I just did this new install of Ubuntu a couple of days ago after using Dreamlinix for a couple of months. Now I am back to Ubuntu because it is easier for me.

---

### Post by cybergalvez on 2009-07-14
most likely a false positive, the only reason to run AV software on Linux is if your running an email server or something like that and you have windows users.  Otherwise its just a waste of your cpu cycles

---

### Post by sasho_zl on 2009-07-14
Well you can use the antivirus program to scan files you are going to send to windows or mac users, but really scanning your linux partitions is useless. For running the program as root you can do that by starting it from the terminal with the **sudo **command and the name of the program command.  You can try with **sudo avast** and if that doesnt work I suggest checking the name of the process with the **top** command while you are running a scan. Then use that name with sudo to start it with root privileges.
Also if you are really interested in the good security of your system I would suggest to you to scan with software like **rkhunter **and** tiger**. They will check for hidden rootkits and other Linux vulnerabilities.
You can install rkhunter with the command **sudo apt-get install rkhunter**. Then you can scan with:*** sudo rkhunter -c . ***[I]The scanning is fast and if you receive any warnings you can post them here.
[/I]

---

### Post by rapattack on 2009-07-14
I am only experimenting but I did have the intention ages ago to use it for scanning windows programs I was downloading to use on my windows machine. I then put it on a usb drive and then put it on the windows machine. It is odd that I was told that the linux antivirus programs don't scan windows infections. I was told this months ago.
OK yes I can see that it scans when I do the ocmmand **sudo avast**.
OK well I will try those other programs but ultimately I am not doing anything that important that anyone would want to spy or make trouble for me. Just an average home user that will do some audio production when I get to learning properly how to do that in linux.

---

### Post by sasho_zl on 2009-07-14
Well just because you are a average home user don't assume that you are of no interest to the "bad guys" out there. Every box with a processor, memory and a internet connection is important tool for use for DDoS or just for a middle point in to cracking a gov site with your IP address all over it. Have in mind that running Linux doesn't make you bulletproof but you are much safer than others running windows. But still good security of your system is not a bad thing.

---

### Post by rapattack on 2009-07-14
What is DDos?
I understand all the rest. One of the many reason I ditched windoze 2 years ago.):P

---

### Post by sasho_zl on 2009-07-14
DDOS stands for Disturbed Denial of Service attack. It is one of the most common forms of attack against different servers. The attack consists of making as more as possible computers to attempt a connection with a desired server at the same time and making him "overload" with requests. There was a massive attack of that type 10 days ago against US and South Korea sites. Some folks think that North Korean hackers did it.
With the DDoS attack the hackers need to take control on as much computers as possible mostly with different types of automated scripts which are scanning and searching for exploits.
That is the reason that the internet would be much safer place without all those windows computers out there.
Cheers, and I hope I was useful! Good luck with securing your PC!

---

### Post by rapattack on 2009-07-14
Ah cool. Yes I was trying to explain to a friend that has only recently got on the net about security. This not my field but since he uses windows he needs to be extra careful. I was explaining about the origins of the internet and why hacking/viruses etc exist. It is a very vast field we all need to be aware. A lot of peoples first response is anger about the hacking/virus making etc but when I explain why it happens they are a little more understanding.
So with the attack your talking about was that to only windows machines or linux too? I honestly don't know what scripts are but have heard the word many times.

---

