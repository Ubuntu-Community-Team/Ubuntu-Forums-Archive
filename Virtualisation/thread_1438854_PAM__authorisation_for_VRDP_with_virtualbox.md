---
title: "PAM  authorisation for VRDP with virtualbox"
date: 2010-03-25
forum: Virtualisation
---

### Post by mcmiao on 2010-03-25
Hi, I am new to Ubuntu/Linux. On my home computer, I have Ubuntu 9.10 as my host and have set up a virtual machine using virtualbox with Windows 7 as a guest. I would like to remotely access the virtual machine from a work computer using windows remote desktop connection. I have so far been trying to remotely access my computer from another computer on my home network and have had success when the guest authentication is set to "null", but am unable to get it to work with "external" authentication. When trying to connect, I get the following message:
 
**"Your remote desktop session has ended"** proceeded by **"Your remote desktop session is about to end, virtual memory may be low"**
 
I think it may be an issue with PAM as described here- 
 
[https://help.ubuntu.com/community/VirtualBox/RDP](https://help.ubuntu.com/community/VirtualBox/RDP)
 
I have created a new configuration file as suggested and have tried to set an environment variable so that VRDPAuth.so uses the correct PAM Service by inserting the command: [COLOR=navy]export VRDP_AUTH_PAM_SERVICE="vrdpauth"[/COLOR]

[COLOR=black]I have inserted this into the following files:[/COLOR]

[COLOR=black]etc/environment[/COLOR]
[COLOR=black]~/.pam_environment[/COLOR]
[COLOR=black]~/.bashrc[/COLOR]
 
[COLOR=black]It still does not work. I am not sure if I am inserting it into the wrong file, inserting it incorrectly into the file or using the wrong command.[/COLOR]
 
I have seen that a few others on this forum have had similar problems, but there does not seem to be a suitable answer provided.

[COLOR=black]Could anyone who has gotten VRDP to work using virtualbox please help me with step by step instructions on how to do this?[/COLOR]

[COLOR=black]Thanks[/COLOR]

---

### Post by mcmiao on 2010-03-27
Finally working, it may have been an issue with the clients remote desktop connection settings in the end-
I ignored the vrdpauth commands mentioned in my original post and added the line:
 
[COLOR=navy]account required        pam_unix.so broken_shadow[/COLOR]
 
into the common-account (sudo gedit /etc/pam.d/common-account) under the line:
 
[COLOR=navy]account required        pam_permit.so
[/COLOR]
I altered the advanced connection settings in the remote desktop connection on my client machine so that I could connect from anywhere without a TS gateway server (this is likely to be dependant on any individuals network setup).

Strangely, only when I then checked the "allow me to save credentials" box in the Logon Settings did it ask me for my password when I tried to connect- otherwise it would still give me an error message as I described initially.
 
Hope this might be of some help to others.

---

### Post by mattajas on 2010-05-13
> **mcmiao said:**
> Finally working, it may have been an issue with the clients remote desktop connection settings in the end-
I ignored the vrdpauth commands mentioned in my original post and added the line:
 
[COLOR=navy]account required        pam_unix.so broken_shadow[/COLOR]
 
into the common-account (sudo gedit /etc/pam.d/common-account) under the line:
 
[COLOR=navy]account required        pam_permit.so
[/COLOR]
I altered the advanced connection settings in the remote desktop connection on my client machine so that I could connect from anywhere without a TS gateway server (this is likely to be dependant on any individuals network setup).

Strangely, only when I then checked the "allow me to save credentials" box in the Logon Settings did it ask me for my password when I tried to connect- otherwise it would still give me an error message as I described initially.
 
Hope this might be of some help to others.

Yes it really was, thanks to you it is also working for me now. I'm not sure how, but it appears to work without any of the changes in the pam-files, what made it was the "allow me to save credentials"-checkbox, I'm connecting via Windows 7 Remote Desktop.

Thanks again, and it was good that you posted the solution even with no replies in your thread!

---

### Post by riprowan on 2011-01-19
I have the same problem that you report, but following your steps I still cannot resolve the problem.  Both machines are on the same physical LAN and can see each other.  I can remote into the guest machine when I set Remote Display authentication to "NULL" (unsecured) but when I select "External" I get the same RDC error you received (**"Your remote desktop session has ended"** proceeded by [B]"Your remote desktop session is about to end, virtual memory may be low")

Any advice??
[/B]

---

