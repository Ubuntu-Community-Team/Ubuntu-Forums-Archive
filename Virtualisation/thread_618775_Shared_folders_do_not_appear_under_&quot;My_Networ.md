---
title: "Shared folders do not appear under &quot;My Network Places&quot; in Windows guest"
date: 2007-11-20
forum: Virtualisation
---

### Post by erdley on 2007-11-20
I selected the /home folder as a shared folder from the "Devices" menu.  When I go to the Windows XP guest "My Network Places" I don't find any listing for this to mount.  I am obviously doing something wrong, but I don't know what.  I am an absolute beginner, so I probably don't know what I am doing here.  Any help would be appreciaed.  Gutsy is the host and Windows XP Pro is the guest.

---

### Post by dpj23 on 2007-11-21
Try creating a mapped drive in the windows machine...  This should browse to your home folder...

---

### Post by jonandrews on 2007-11-22
I've put my simple guide to integrating Ubuntu PC's into a wired Windows home network onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


Let me know if it is helpful.

---

### Post by niceguy123 on 2007-11-22
> **jonandrews said:**
> I've put my simple guide to integrating Ubuntu PC's into a wired Windows home network onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


Let me know if it is helpful.

Thanks, Looks good and helpful. I'm having an opposite type of problem, I don't see all of my windows computers on my Ubuntu box windows network file browser. 

I now have 5 computers on a rotter. 2 Ubuntu and 3 Windows XP (had one and just added two more). sometimes I see the "older" one but not the newer ones and sometimes the older one disappears too. 

Asides for that I see my Ubuntu boxes twice, once under Network - File browser and again Under that in Network - File browser>Windows Network - File browser>mshome

Help : )

---

### Post by jonandrews on 2007-11-22
Sorry - I hadn't appreciated that. 
I have 2 Ubuntu PCs sitting on a network with 4 XP machines, and I occasionally experience random times when an otherwise well-behaved Ubuntu PC stops seeing beyond the 'Windows Network' icon. I've never been able to explain it, and get round it by rebooting everything (including the Router).  It's a very infrequent occurence, though.

---

### Post by erdley on 2007-11-22
> **dpj23 said:**
> Try creating a mapped drive in the windows machine...  This should browse to your home folder...

I probably don't know enough about drive mapping in Windows, but I cannot find a way to browse to my home folder in Ubuntu.  I have tried using the "compmgmt.msc" command in Win XP, followed by the "Disk Mangement" link, but I could find no way to browse to the Ubuntu home folder.

---

