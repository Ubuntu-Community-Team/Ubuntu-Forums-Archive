---
title: "How to access host file system?"
date: 2008-01-17
forum: Virtualisation
---

### Post by yesint on 2008-01-17
Dear All,
I'm sorry for asking this dumb question, but I understand almost nothing in networks both in linux and windows. 
How can I access shared folder in the host from the guest in VMware? I installed samba on the linux host and opened the access to desired directory, but what next? How can I tell windows guest to use this folder? It seems that the guest doesn't see the host. How can make it visible? Step-by-step instructions would be very appreciated!

---

### Post by fjgaude on 2008-01-17
Okay, in Windows you have to go to Start/Network and there you should see your shares. You can do this also in Windows Explorer down near the bottom of the folder list under Network or something similar.

If you see your shares and you have already in Ubuntu entered your smbpasswd then all will be okay. If not:

```
sudo smbpasswd -a login-name
```

in Ubuntu terminal.

Let us know how you do.

---

### Post by yesint on 2008-01-18
The problem is that I don't see the shares from Windows at all. There is nothing in the network in Windows, just the guest machine itself. 
Probably I chosed the wrong network type for the guest? I'm using NAT, which allows me to access the internet from the guest.

---

### Post by fjgaude on 2008-01-18
NAT is correct. You have re-booted your machine since adding the password, etc, eh?

---

### Post by yesint on 2008-01-18
Yes, I rebooted the machine. Windows still does not see the host. In Windows 
under "My network places" I have "Entire network"->"Microsoft windows network"->"workgroup" and there is only windows machine itself inside, nothing else. 
I also tried to connect in a stupid way entering "\\name_of_linux_host" in windows explorer. This displays the login dialog, but my login and password set for samba doesn't work. Does this mean that it actually sees the host?
Probably it doesn't work because I'm running windows server 2003 as a guest?

---

### Post by fjgaude on 2008-01-18
If it asks for login and pw, then it means Windows is seeing Linux. I think you haven't entered your smb pw, like suggested earlier. Try it and see.

---

### Post by yesint on 2008-01-19
I did
sudo smbpasswd -a login-name
and entered the password. This password is not recognized in Windows...

---

### Post by fjgaude on 2008-01-19
You mean Windows asks for the password and when you enter it it still asks again?

If this is so, there is still something not set correctly. <grin> Duh!

---

### Post by popch on 2008-01-19
I do not use VMWare anymore. Therefore my suggestions will be somewhat vague. However, they might still point you into the right direction. 

One: There are different ways of sharing 'folders' between the host and the guest: you can use the 'shared folders' feature of VMWare or you can use SMB and share your folders over the network just as you would with real computers.

Two: When using 'shared folders' for a Windows guest within a Linux host, you will find the folder in Windows' "my Network" under 'all of the network' and/or my network places. Sorry, in addition to not using VMWare any more, I also don't use an English version of Windows. This requires VMWare tools to be installed in the guest machine.

Three: When using Samba to share between a Linux host and a Windows guest, using NAT for the network might not be the best idea. When using NAT, your virtual computer will be on a subnet different from your real computer. Windows' name resolution works only across different subnets when you are in a Windows domain and using a WINS server. I don't think that Samba provides WINS functions, but  I could be mistaken here. You might want to try bridged networking for your VM (in order to bring them to the same subnet). You also might want to try accessing Samba on your host computer by specifying its IP address instead of the name. Lastly, look up the Samba documentation on WINS services.

---

