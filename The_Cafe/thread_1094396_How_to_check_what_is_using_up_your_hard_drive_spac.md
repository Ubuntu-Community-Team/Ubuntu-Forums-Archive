---
title: "How to check what is using up your hard drive space on Windows?"
date: 2009-03-12
forum: The Cafe
---

### Post by NintendoTogepi on 2009-03-12
I was checking my hard drive space the other day and I noticed I only had 1GB left! Last time I checked I had 13GBs left....

What could have suddenly taken up all of that space? How can you check what is using up your space?

I've searched every inch of the hard drive and I'm baffled what's taking up all of this space.

And please no 'Windblows lol' comments, it's not ideal but I need to play my games :o

---

### Post by kestrel1 on 2009-03-12
It could be the swap file has got oversized or it could be restore points. Is this XP or Vista?

---

### Post by NintendoTogepi on 2009-03-12
> **kestrel1 said:**
> It could be the swap file has got oversized or it could be restore points. Is this XP or Vista?

Windows XP Media Edition - computer will be four years old next month, and Windows has never been reinstalled.

The thing that confuses me is how suddenly the space was taken up...I just checked it last sometime in early February...

---

### Post by bsharp on 2009-03-12
If you dualboot, you can boot up Ubuntu, mount the Windows drive and use the Disk Usage Analyzer Tool (Applications->Accessories). Just click the "Scan Folder" and find wherever the windows drive is mounted (/dev/sda1 for me).

---

### Post by kestrel1 on 2009-03-12
> **NintendoTogepi said:**
> Windows XP Media Edition - computer will be four years old next month, and Windows has never been reinstalled.

The thing that confuses me is how suddenly the space was taken up...I just checked it last sometime in early February...
That's the joys of Windows :D
If it hasn't been reinstalled in four years you are very lucky. I normally recommend a re-install of XP after a maximum of three years.

---

### Post by nitehawk777 on 2009-03-12
When I added the SP3 service pack,....it ate up a LOT of space on my partition!

---

### Post by NintendoTogepi on 2009-03-12
> **bsharp said:**
> If you dualboot, you can boot up Ubuntu, mount the Windows drive and use the Disk Usage Analyzer Tool (Applications->Accessories). Just click the "Scan Folder" and find wherever the windows drive is mounted (/dev/sda1 for me).

Nah, I don't dualboot on this one because I didn't feel it was necessary.

> **kestrel1 said:**
> That's the joys of Windows :D
If it hasn't been reinstalled in four years you are very lucky. I normally recommend a re-install of XP after a maximum of three years.

My Mom's computer is on a seven year installation of Windows...of course, it takes 10 minutes to start up and is extremely slow (it's not a bad computer, it has 1GB of RAM)...she still won't let me put Ubuntu on it. :(

---

### Post by kestrel1 on 2009-03-12
Seven years?? That is crying out for a re-install.
You could boot with the Ubuntu Live CD to check out the disk usage. I can't remember, off the top of my head what to do in XP. Use Linux more than ever now. I will boot my virtual XP & poke about a bit, once I finish the Mandriva virtual machine that is running at present.

---

### Post by kestrel1 on 2009-03-12
If you want to check out your current paging file (swap). Right click on My Computer & go to Properties. Select the Advanced tab & then select the Settings button under Performance. Once you are in the Performance Options windows select Advanced tab.
At the bottom of that tab you will see Virtual Memory. I would assume that this is set to allow Windows to manage it. I would select Change & set the Custom size to be 1.5 times your amount of RAM. So if you have 1gb RAM set the initial size to 1.5gb & the same for the max.
You will need to reboot for the changes to take effect.
You could also turn of restore points by going back to the System Properties window & select System Restore tab. In there tick the box that says to turn off system restore. Once you reboot, you can turn it back on if you wish, but all current restore points will have been deleted after the reboot.

---

### Post by dannyboy79 on 2009-03-12
you can simply use the search feature by right clicking on the My Computer icon from the Desktop, then drop down the 'what size is it' option and you could look for large files. It goes by KB so you could enter something like anything over 5,000 KB 

OR

since you know you had more space in feb, you could do a search by date modified. Chose for it to find anything modified after Feb 1, 2009.

good luck

---

