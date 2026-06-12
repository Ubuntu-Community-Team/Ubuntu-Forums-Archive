---
title: "Accessing shared folders using Samba from Win XP under Virtualbox"
date: 2009-02-05
forum: Virtualisation
---

### Post by ssagi on 2009-02-05
I am using Vbox 2.1.2 under Ubuntu Intrepid to run XP. The conventional method of using Vbox and XP shared folders is extremely slow, making this feature useless. I read people use Samba for this task but could not set the Ubuntu-XP connection (threads on this use old versions of Ubuntu so no updated info is available)

Can someone guide me in establishing the connection?

thanks,
Sagi

---

### Post by HermanAB on 2009-02-06
The absolutely easiest way to share files with a VM is using good old fashioned FTP.  Simply install FileZilla in Windows and vsftp or proftp on Linux.

Getting Samba on Linux to work can be a PITA so I avoid it like the plague, but here is a debug guide:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by ssagi on 2009-02-07
> **HermanAB said:**
> The absolutely easiest way to share files with a VM is using good old fashioned FTP.  Simply install FileZilla in Windows and vsftp or proftp on Linux.

Getting Samba on Linux to work can be a PITA so I avoid it like the plague, but here is a debug guide:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

thanks for this Herman. Can you point at some guidelines (howto) for this feature (using FTP). Why then I found Samba quite popular among users? 

And more generally, are shared files practically been copied (to client) and returned to their original location (host) or there is a single copy and all accesses are mapped to it?

Sagi

---

### Post by HavocXphere on 2009-02-07
Should work without the need for long tutorials.

Check whether you can ping the router address from both OS's. Then, in XP, open an explorer select tools-option-folderoptions-view->scroll down the list and disable simple file sharing.

Next, go to ubuntu box and type in your file browser (not sure what ubuntu uses):
smb://OtherPCName/c$
then type in:
Username -> administrator
pwd-> _YouradminPasswordHere

and then you should be able to see the whole C drive on XP.

Make sure you enable networking in Virtualbox. No need to share anything manually if using admin credentials. C$, D$ etc. CD drive and USB devices are however not shared.

----
Other way round:
You'll need to install the samba server and you'll access it by typing in
\\UbuntuServerName\
into explorer addr bar.
This time you will however need to share stuff specifically on the ubuntu box.

---

### Post by ssagi on 2009-02-08
> **HavocXphere said:**
> Should work without the need for long tutorials.

Check whether you can ping the router address from both OS's. Then, in XP, open an explorer select tools-option-folderoptions-view->scroll down the list and disable simple file sharing.

Next, go to ubuntu box and type in your file browser (not sure what ubuntu uses):
smb://OtherPCName/c$
then type in:
Username -> administrator
pwd-> _YouradminPasswordHere

and then you should be able to see the whole C drive on XP.

Make sure you enable networking in Virtualbox. No need to share anything manually if using admin credentials. C$, D$ etc. CD drive and USB devices are however not shared.

----
Other way round:
You'll need to install the samba server and you'll access it by typing in
\\UbuntuServerName\
into explorer addr bar.
This time you will however need to share stuff specifically on the ubuntu box.

thanks for this but still not much of a success (in both options).
So let's try to be more specific:

The Ubuntu file browser is Nautilus. However, what should I put in place of "OtherPCName" that you wrote? I tries OtherPCName as is and got an error message. I also tried the IP I pinged for but got the same error message. So I could not pursue this option.

I tried the other option you suggest: 
I installed Samba (i am not sure I did it correctly but I have samba appearing in administration menu and it maps directory paths to share names. Again from XP windows explorer, using the IP address I pinged for, I could not access the folders I have in the samba share.

Can you give some more specific help (i.e. what names to use, etc.)?
Is this task so uncommon (i.e. sharing files between Linux (Ubuntu) and XP running in a Vbox)?

Sagi

---

