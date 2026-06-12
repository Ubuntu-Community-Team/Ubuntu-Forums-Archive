---
title: "Best updated antivirus for Ubuntu?"
date: 2009-11-05
forum: Server Platforms
---

### Post by Foeburner on 2009-11-05
Hi, 

I have read through many outdated threads about installing antivirus for ubuntu. I know what most of you are gonna say that ubuntu doesnt need an AV because its safe. 

Well, I'm not worried about the server. Im worried about the windows clients. I'm running my ubuntu server as a file server for my office's windows computers and somehow a virus (dl.exe) was embedded in the shared folder and whenever a windows user accesses the shared folder, the dl.exe would run and spread through the folders and corrupting other exe's. Everyone's windows' antivirus would catch it before it corrupted their system. 

Its not messing with my server, only windows and exes. I tried deleting the file (dl.exe) but it would just worm itself to another folder and reappear again. I searched all over google about this virus which symantec reports as w32.lycum and so far, everyone with this virus on their system ends up formatting. 

Im pretty sure I can remove it using a AV in ubuntu and the shared folder would be clean of it. 

Any suggestions?

---

### Post by orasis on 2009-11-05
I can only think of ClamAV

---

### Post by jtwhite on 2009-11-05
AVG?

[http://free.avg.com/us-en/download?prd=afl](http://free.avg.com/us-en/download?prd=afl)

---

### Post by ivanvajar on 2009-11-05
There is also Avast for Ubuntu.

---

### Post by Foeburner on 2009-11-05
I have tried clam but i'd have to use wine to install i believe. Haven't gotten around to it. 

I installed AVG but I'm not getting an icon on applications > accessories and I cant find anything on google about the commandline for it. 

I also installed avast but everytime I open it, it asks for the key code each time, I enter it as usual and it never opens unless I run it with gksu avastgui. After I get the gui up, i click on update, it looks like it downloads but then disappears and when I try to open and hope its updated, it loops back and asks for the keycode. 

weird... =|

---

### Post by Supersquirrel on 2009-11-05
The best antiviral stuff is the humans immune system.

---

### Post by nexoncore on 2009-11-05
I am not so much in need of an Antivirus, since I have never come across a virus on linux. But I am in need of a Firewall, one native to linux, powerful but also light weight on the resources. Know of any?

---

### Post by usafwings on 2009-11-05
> **nexoncore said:**
> ...I am in need of a Firewall, one native to linux, powerful but also light weight on the resources. Know of any?

Download Firestarter from the Synaptic Package Manager.

System > Administration > Synaptic Package Manager. 
Do a search for Firestarter and voilà.

---

### Post by sliketymo on 2009-11-05
> **usafwings said:**
> Download Firestarter from the Synaptic Package Manager.

System > Administration > Synaptic Package Manager. 
Do a search for Firestarter and voilà.

Firestarter is no longer supported.A better option would be to use the built in UFW. add the gufw through synaptic for a GUI interface.

---

### Post by jrusso2 on 2009-11-05
> **Foeburner said:**
> I have tried clam but i'd have to use wine to install i believe. Haven't gotten around to it. 

I installed AVG but I'm not getting an icon on applications > accessories and I cant find anything on google about the commandline for it. 

I also installed avast but everytime I open it, it asks for the key code each time, I enter it as usual and it never opens unless I run it with gksu avastgui. After I get the gui up, i click on update, it looks like it downloads but then disappears and when I try to open and hope its updated, it loops back and asks for the keycode. 

weird... =|

You have to register it.

---

### Post by usafwings on 2009-11-06
> **sliketymo said:**
> Firestarter is no longer supported.A better option would be to use the built in UFW. add the gufw through synaptic for a GUI interface.

Ah. Thanks for the correction! ;)

---

### Post by Sef on 2009-11-06
> I have tried clam but i'd have to use wine to install i believe. Haven't gotten around to it. 


I believe it is available in the repositories.  If not then go to [clamav]("http://www.clamav.net/").  There are linux versions there.

---

### Post by ZALinuxDude on 2009-11-06
I'm pretty sure i'm gonna say something stupid here but if it is Clam AV you are looking for their are versions available for Windows as well if you looking for something with a little more grunt for windows take a look at spyware terminator (google it) i recommend this as its completely free and works in the same way a fire wall would (asking if you want to allow or block things) and is pretty damn good as far as protecting not only against viruses but spyware as well it comes with the CLAMAV embedded in it and is also free (but needs to be activated seperately during the installation of spyware terminator), and because windows doesn't pick it up as either a firewall or an antivirus you can run it and any of your favourite virus scanners simultaneously without conflicts... I use it on my machine along with AVG free 8,5 and have never had any virus problems since... check it out here :
[http://www.spywareterminator.com/]("http://www.spywareterminator.com/")

---

