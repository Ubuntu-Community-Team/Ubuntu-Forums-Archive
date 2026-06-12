---
title: "what is a good virus scanner?"
date: 2011-04-03
forum: Security
---

### Post by 007casper on 2011-04-03
I have looked at synaptic.  Most of the virus related programs are for email.

What is a good virus scanner?

please advise

Thank you

---

### Post by Dutch70 on 2011-04-03
Have you tried clamav?

What exactly are you wanting to use the anti-virus for?

I believe bitdefender and avg have anti-virus' that run on Linux.

---

### Post by uRock on 2011-04-03
Moved to security discussions.

[https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

---

### Post by 007casper on 2011-04-03
I just dont want my computer be invaded with viruses.  

I have moved all my data from windows environment.  Also, usually I need to exchange files with other people.  I am not using the computer as an email server, however, I also do need to download attachments from clients.

I know viruses are dormant in linux environment, however, I just want to make sure I am safe without keyloggers, and any buggers.

---

### Post by Dutch70 on 2011-04-03
Sounds like you want a firewall (unless you're behind a router) and a good strong password.

I don't believe you have to worry about keyloggers either, unless you decide to install one.

Although I do recommend using the live cd/usb for banking and making online purchases.

---

### Post by Zundap on 2011-04-03
Could you tell me,Witch  Fire wall works with ubuntu?   Thanks

---

### Post by Rasa1111 on 2011-04-03
ClamTK is about the best there is in the repos in my experience. 
Works great for scanning files in windows from Ubuntu to.
Good also if you "trade" files with windows users.

---

### Post by Rasa1111 on 2011-04-03
> **Zundap said:**
> Could you tell me,Witch  Fire wall works with ubuntu?   Thanks

Ubuntu comes with its own firewall.
All you have to do is turn it on. 

You can use terminal to enable it.
```
sudo ufw enable
```

 Or get the GUI for it, 
To get the GUI, install "GUFW"
find it in software center or synaptic.

Once it's installed, find it in System> Admin> Firewall config

This might be good to look at.
[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

---

### Post by Dutch70 on 2011-04-03
> **Zundap said:**
> Could you tell me,Witch  Fire wall works with ubuntu?   Thanks

Gufw is a good one.

---

### Post by Rasa1111 on 2011-04-03
GUFW is only the graphical user interface.
It's not actually a firewall.
The firewall already exists when you install ubuntu.
GUFW just makes it "easier" for people who don't like to use the terminal.

UFW is the firewall that comes with Ubuntu
GUFW is just the 'pretty window' that pops up to turn it on and off, and to add/block ports easily.

---

### Post by Dutch70 on 2011-04-03
lol, Rasa I didn't even see your post above mine until just now.

---

### Post by Rasa1111 on 2011-04-03
lol Dutch,
that happens to me a lot! :P

---

### Post by 007casper on 2011-04-03
@Dutch70> 
Although I do recommend using the live cd/usb for banking and making online purchases.

how come?  

What is the reason/benefit of using usb or live cd for banking or online purchases?

---

### Post by Dutch70 on 2011-04-03
> **007casper said:**
> @Dutch70

how come?  

What is the reason/benefit of using usb or live cd for banking or online purchases?

It leaves no traces of your critical information on your computer.

---

### Post by norseman-has-a-laptop on 2011-04-03
What are you using it for

---

### Post by HermanAB on 2011-04-04
Howdy,

Here is a very good virus scanner for Linux.  It is very friendly, light weight and it is fully multitasking.  Save it to "/usr/local/bin/scanner" and make it executable with "sudo chmod 755 /usr/local/bin/scanner", then simply type "scanner" at a prompt:

#! /bin/bash
echo Advanced, Light Weight, Super Friendly, Multitasking Linux Virus Scanner, GPL 2011.
sleep 5
echo Preparing...
sleep 5
echo Deep thinking...
sleep 10
echo Scanning...
sleep 20
echo Almost done...
sleep 5
echo Drum roll...
sleep 2
echo No viruses found!!!
sleep 2
echo Thank you, I'll be here all night...

---

### Post by Dutch70 on 2011-04-04
> **HermanAB said:**
> Howdy,

Here is a very good virus scanner for Linux.  It is very friendly, light weight and it is fully multitasking.  Save it to "/usr/local/bin/scanner" and make it executable with "sudo chmod 755 /usr/local/bin/scanner", then simply type "scanner" at a prompt:

#! /bin/bash
echo Advanced, Light Weight, Super Friendly, Multitasking Linux Virus Scanner, GPL 2011.
sleep 5
echo Preparing...
sleep 5
echo Deep thinking...
sleep 10
echo Scanning...
sleep 20
echo Almost done...
sleep 5
echo Drum roll...
sleep 2
echo No viruses found!!!
sleep 2
echo Thank you, I'll be here all night...

:lolflag:

---

### Post by 007casper on 2011-04-04
installed clamAV, and wanted to update... 

yum@yumyum:/etc/clamav$ sudo freshclam
ClamAV update process started at Sun Apr  3 23:40:22 2011
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.96.5 Recommended version: 0.97
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cvd is up to date (version: 53, sigs: 846214, f-level: 53, builder: sven)
daily.cld is up to date (version: 12943, sigs: 93208, f-level: 60, builder: guitar)
bytecode.cvd is up to date (version: 142, sigs: 40, f-level: 60, builder: acab)

maybe it is facing me on this link... [http://www.clamav.net/lang/en/support/faq/faq-cvd/](http://www.clamav.net/lang/en/support/faq/faq-cvd/)

I have been looking around... and I dont understand why it doesnt update the antivirus engine

?

---

### Post by Rasa1111 on 2011-04-04
You should use ClamTK instead.

---

