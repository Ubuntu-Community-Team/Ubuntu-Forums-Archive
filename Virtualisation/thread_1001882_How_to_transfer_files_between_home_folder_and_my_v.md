---
title: "How to transfer files between home folder and my virtual machine"
date: 2008-12-04
forum: Virtualisation
---

### Post by faraz_k86 on 2008-12-04
I have virtual box installed. with win XP pro.

How do i transfer files from my home folder in ubuntu to my documents in virtual box;s win xp?

---

### Post by SIGTERMer on 2008-12-04
personally, i use samba to share my files between my computer and the virtual machine..
i'm sure there might be other ways, but that's how i do it sense i already use it to share my files across the lan.

---

### Post by faraz_k86 on 2008-12-04
thx, can u plz tell me how i an use samba to do that.. is there some tutorial or howto for it?

---

### Post by bodhi.zazen on 2008-12-04
Samba is all point and click ;)

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by SIGTERMer on 2008-12-04
this might also help

[http://ubuntuforums.org/showthread.php?p=6267802#post6267802]("http://ubuntuforums.org/showthread.php?p=6267802#post6267802")

---

### Post by faraz_k86 on 2008-12-04
thx, also i see that to use usb drives, i need some PUEL license, i tracked it here : [http://www.virtualbox.org/wiki/VirtualBox_PUEL](http://www.virtualbox.org/wiki/VirtualBox_PUEL)

now how do i get this to my virtual box?

---

### Post by faraz_k86 on 2008-12-04
just to add, i downloaded virtual box from the terminal, by the apt-get command.

so is mine the full version or the opensource version?

---

### Post by faraz_k86 on 2008-12-04
just to add, i downloaded virtual box from the terminal, by the apt-get command.

so is mine the full version or the opensource version?


edit:

im sorry about the double post. dont know how that happened..

---

### Post by bodhi.zazen on 2008-12-04
> **faraz_k86 said:**
> just to add, i downloaded virtual box from the terminal, by the apt-get command.

so is mine the full version or the opensource version?


edit:

im sorry about the double post. dont know how that happened..

No worries.

If you downloaded the VirtualBox .deb from the Virtualbox (sun) site, they you use "sudo dpkg -i VirtualBox*.deb" to install => then you have the PUEL version.

If you sudo "apt-get install virtualbox" then you have the OSE.

---

### Post by HermanAB on 2008-12-05
I simply install OpenSSH Server on the Ubuntu host and then use FileZilla with SFTP to transfer files from Windows.  This works like a charm and is almost zero effort to set up, since I always run OpenSSH Server on my Linux machines.

Cheers,

Herman

---

### Post by zero244 on 2008-12-06
Im running Vmware Player 2.5 and according to the documentation I should only be able to copy and paste text from Linux to my XP VM.
As it turns out this is not correct.
I can copy any file from XP to my Linux home folder and vise versa.
I cant drag and drop files to the Linux desktop or any files that require root access.
Why Vmware says you cant do this is perplexing.
You would think they would know there own product 9 ways to Sunday.
I do it all the time, I can download some music in my XP VM then drag and drop them into a folder in my home folder and they copy just fine.
Just my 2 cents.

---

### Post by abdusamed on 2010-05-15
i made my download folder on home machine ubuntu to share using virutal box folder share.. how am i suppose to access it on the xp virutal machine?

---

### Post by dcstar on 2010-05-15
> **zero244 said:**
> Im running Vmware Player 2.5 and according to the documentation I should only be able to copy and paste text from Linux to my XP VM.
As it turns out this is not correct.
I can copy any file from XP to my Linux home folder and vise versa.
I cant drag and drop files to the Linux desktop or any files that require root access.
Why Vmware says you cant do this is perplexing.
You would think they would know there own product 9 ways to Sunday.
I do it all the time, I can download some music in my XP VM then drag and drop them into a folder in my home folder and they copy just fine.
Just my 2 cents.

Copy and Paste from VMs to host 10.04 system also works on Player 3.1.0.

---

### Post by bodhi.zazen on 2010-05-15
> **abdusamed said:**
> i made my download folder on home machine ubuntu to share using virutal box folder share.. how am i suppose to access it on the xp virutal machine?

You may access / transfer files via several methods.

1. Use a USB / Flash drive.

2. Use the VirtualBox Shared Folders feature.

3. Configure a network protocol such a samba. Configuration is dependent on several variables including how you configure Virtualbox (Hint use a bridge not the default , NAT), and issues such as firewalls (did you activate your firewall on Windows or Ubuntu?).

4. You can also use ssh , FTP, or even http to share a directory.

---

