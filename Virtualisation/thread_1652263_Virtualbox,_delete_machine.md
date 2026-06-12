---
title: "Virtualbox, delete machine"
date: 2010-12-24
forum: Virtualisation
---

### Post by Senplanet on 2010-12-24
I installed Windows XP on Oracle VM VirtualBox 3.2  and gave it 20GB from my /home partition. 
I didnt use it much so I want to remove it and get the 20GB back to my home space, so I deleted the machine in VB , however the 20GB is not back. What should I do? :?

---

### Post by Senplanet on 2010-12-24
Hello, 
I installed Windows XP on Oracle VM VirtualBox 3.2  and gave it 20GB from my /home partition. 
I didnt use it much so I want to remove it and get the 20GB back to my  home space, so I deleted the machine in VB , however the 20GB is not  back. What should I do?

---

### Post by Verbeck on 2010-12-24
open you home folder>press ctrl+H>open .VirtualBox / HardDisks 
and delete it from there

---

### Post by matt_symes on 2010-12-24
Hi

> **Senplanet said:**
> I installed Windows XP on Oracle VM VirtualBox 3.2  and gave it 20GB from my /home partition. 
I didnt use it much so I want to remove it and get the 20GB back to my home space, so I deleted the machine in VB , however the 20GB is not back. What should I do? :?

goto Places->Home Folder and press ctrl and h together to show hidden files.

Look for the .VirtualBox directory and double click to enter it. You will find them in hard disc and machines folders.

They are *.vdi files

Kind regards

---

### Post by Senplanet on 2010-12-24
Thank you very much (to both of you)

---

### Post by VonFilmjölk on 2010-12-24
in my experience viritualbox only uses  a few bytes  when u set up a  new hard drive (if u dont use the space) but if u wish to erase the drives follow the guidelines  given in previes responses

---

### Post by karthick87 on 2010-12-24
Goto your Home folder.Press** CTRL+H **and goto **.VirtualBox** folder and then **HardDisks**. Delete your VirtualBox harddisk there.

---

### Post by Senplanet on 2010-12-24
> **karthick87 said:**
> Goto your Home folder.Press** CTRL+H **and goto **.VirtualBox** folder and then **HardDisks**. Delete your VirtualBox harddisk there.
Thanks

---

### Post by karthick87 on 2010-12-24
You are welcome :)

---

### Post by aytech on 2010-12-24
> **VonFilmjölk said:**
> in my experience viritualbox only uses  a few bytes  when u set up a  new hard drive (if u dont use the space)

Thats if you choose dynamically expanding storage

---

### Post by linden940 on 2010-12-24
to help keep things clean if you have it solved then list it as so :D

---

### Post by howefield on 2010-12-24
Threads merged.

---

