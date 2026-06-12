---
title: "Need VirtualBox tutoring ..."
date: 2013-03-29
forum: Virtualisation
---

### Post by flows69 on 2013-03-29
Hello, 

I have just switched from Windows to Ubuntu 12.10. The thing is that I need to run Windows programs too (SAS mostly) but cannot get VirtualBox to function. 

Basically I get this error: Kernel Driver not installed (rc=-1908). I found on this forum a series of code to run including:

[COLOR=#000000]*OK, problem solved. With 12.10 I had to:*[/COLOR]

[COLOR=#000000]*sudo apt-get install linux-headers-3.5.0-17-generic*[/COLOR]
[COLOR=#000000]*sudo apt-get remove virtualbox-dkms*[/COLOR]
[COLOR=#000000]*sudo apt-get install virtualbox-dkms*[/COLOR]

Nothing made a difference and I am running behind on my work, if anyone has an idea please respond. 

Thanks in advance, 

flows69

PS. I am really a beginner so if you want me to try something explain it step by step.

---

### Post by wildmanne39 on 2013-03-29
*Thread moved to **Virtualisation**.*

---

### Post by matt_symes on 2013-03-29
Hi

Did you install Vbox from the repositories or from the virtual box web site ?

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

If you the repos then purge it and try the one from the website for your kernel.

Kind regards

---

### Post by flows69 on 2013-03-29
Hello Matt, 

I removed the VirtualBox that was on my machine and installed the deb file I downloaded from the website. 
Factually I had to purge using the command [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get purge virtualbox*[/FONT][/COLOR] as some part remained after my first attempt. 

When I start VirtualBox after that I get the same error message as I had in my first post. 

Thanks again for your time, 

flows69

---

### Post by matt_symes on 2013-03-29
Hi

To be honest, i gave up using virtual box ages ago as i though it was *cough* not that good so i may not be the best person to help you here.

Currently i use qemu but in the past i have also used vmware.

Anyway, that is no help to your current situation so can you post the output of

```
[COLOR=#000000]dkms status[/COLOR]
```

Maybe someone who uses VBox can also chip in. We do not bite here :D

Kind regards

---

### Post by SeijiSensei on 2013-03-29
I recommend that you start over and follow the instructions for adding the appropriate repository under the "Debian-based distributions" section of the Linux downloads page on the VirtualBox web site.  This works flawlessly for me, and so far it has worked for everyone I have recommended this approach to here.

---

### Post by matt_symes on 2013-03-29
Hi

Thankyou SeijiSensei.[COLOR=#000000] 

Your input is very welcome.

Kind regards[/COLOR]

---

### Post by flows69 on 2013-03-30
Hello SeijiSensei, 

I tried to follow the instructions on this website as instructed: [http://www.virtualbox.org/wiki/Linux_Downloads]("https://www.virtualbox.org/wiki/Linux_Downloads")

I have changed the repositori settings in the source.list file but cannot run the command [COLOR=#000000]sudo apt-key add oracle_vbox.asc[/COLOR]
When I enter this command I get the following error message: gpg: can't open `oracle_vbox.asc': No such file or directory

When I open the source.list file I do see the added lines: 

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) oneiric contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) wheezy contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) squeeze contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lenny contrib non-free

Would you have an idea of what I did wrong ?

flows69

---

### Post by matt_symes on 2013-03-30
Hi

They give two techniques for getting the key.

Did you down load the secure key from here ?

[http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc)

Anyway ignore that method and just use the second. 

As they say run this command

```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

You'll expect output like...
```

matthew-S206:/home/matthew % wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
[sudo] password for matthew: 
OK
matthew-S206:/home/matthew %
```

If it say's OK it has imported the key correctly.

Kind regards

---

### Post by SeijiSensei on 2013-03-30
> **flows69 said:**
> When I open the source.list file I do see the added lines: 
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) oneiric contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) wheezy contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) squeeze contrib non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lenny contrib non-free


You only should include one of those lines, the one that applies to your Ubuntu distribution.  There isn't an entry for 12.10, so use the one for 12.04, "Precise".  Delete the others.

Also as Matt writes, use the wget method to download and install the key in one step.

---

