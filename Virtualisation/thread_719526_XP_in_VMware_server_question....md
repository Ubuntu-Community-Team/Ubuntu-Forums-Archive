---
title: "XP in VMware server question..."
date: 2008-03-09
forum: Virtualisation
---

### Post by niko123 on 2008-03-09
I have installed VMware server...and i wanted to install XP on the VM....so i put in the CD and it is detected...and it goes to the Windows XP setup screen.....but i have no idea if im doing it right or not...it is asking me to use the unpartitioned space that will use 8189 MB but since i only have a 120 gig hard drive in this laptop...i dont want it to take all my space....

my questions are...
1) should i create a new partition...if so how much?

and 

2) if i use the unpartitioned space which is 8189 will it take all my space on my hard drive?

Please help...thanks

---

### Post by fjgaude on 2008-03-09
When you go through the vmware setup for winxp did you not have the option to select how much disk space that was to be used for the guest?

If you can't remember, just start over and use less disk space. For WinXP you likely can get by with 4GB, I'm not sure.

---

### Post by niko123 on 2008-03-09
thenks for the reply... 

and no i didt have the option to set how much space....i poped the cd in it went to the aggrement...i F8 to accept...after i did...it went directly to the do i want to use the unpartitioned space that will use 8189 MB

---

### Post by fjgaude on 2008-03-09
Did you install VMware Server or Player?

It sounds like you are installing WinXP in an unallocated partition. This is not what you wish to do, I don't think. You wish to install in vmware as a guest. Is this not so?

---

### Post by niko123 on 2008-03-09
i have installed VMware server and i wanted to install XP as a guest.

---

### Post by fjgaude on 2008-03-09
Do you have a console? It should have been installed in Applications/System Tools as VMware Server Console. Do you use that to get going?

---

### Post by niko123 on 2008-03-09
yup...i use the VMware server console

---

### Post by niko123 on 2008-03-09
i find it really weird...because...when i installed windows server 2003 for my servers at work...it asked me how much space i wanted to give it...and i was able to enter it like you said....but for some reason when im trying to install winXP ....it goes stright to unpartitioned space....

---

### Post by fjgaude on 2008-03-09
In the console, go to File/New/Virtual Machine/Next...

What do you see?

---

### Post by niko123 on 2008-03-09
welcome to the new virtual machine wizard...this wizard will guid to through the steps of creating a new virtual machine

---

### Post by fjgaude on 2008-03-09
You got it working... horrah! Well, let us know for sure that you do have it all working correctly, to your liking.

We learn something new everyday, eh? Sometimes many things new. <smile>

---

### Post by niko123 on 2008-03-09
:) Thank You!!!

---

