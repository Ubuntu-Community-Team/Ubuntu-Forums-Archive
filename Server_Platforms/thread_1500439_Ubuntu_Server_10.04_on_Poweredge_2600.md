---
title: "Ubuntu Server 10.04 on Poweredge 2600"
date: 2010-06-03
forum: Server Platforms
---

### Post by lucim100 on 2010-06-03
Hello , I am Struggling now for 2 days to install my Ubuntu server 10.04 on a Dell Poweredge 2600, 

I am booting from the cd and the install the keyboard and language settings, then it is scanning the CD drive, the the troubles come,  It say Please wait, detecting hardware under detecting network hardware... the cd stop spinning then the progress bar jumps to 94% and  the keyboard gives me 2 flashing lights . from there it does not go anywhere..

please do anyone know what i can do ? i have tried pressing F6 and under boot options in the prompt window i tried "linux napic nolapic" but it only gives me a block with a OK buttont that say loader and linux, still dont work...

i realy want to load ubuntu server on my dell poweredge

[SIZE=2]




[/SIZE]

---

### Post by lucim100 on 2010-06-03
> **lucim100 said:**
> Hello , I am Struggling now for 2 days to install my Ubuntu server 10.04 on a Dell Poweredge 2600, 

I am booting from the cd and the install the keyboard and language settings, then it is scanning the CD drive, the the troubles come,  It say Please wait, detecting hardware under detecting network hardware... the cd stop spinning then the progress bar jumps to 94% and  the keyboard gives me 2 flashing lights . from there it does not go anywhere..

please do anyone know what i can do ? i have tried pressing F6 and under boot options in the prompt window i tried "linux napic nolapic" but it only gives me a block with a OK buttont that say loader and linux, still dont work...

i realy want to load ubuntu server on my dell poweredge

[SIZE=2]




[/SIZE]
I went into expert mode and skipped the network detection mode, told it ti scan disk... does the same thing, load till 94% the freezes

---

### Post by disabledaccount on 2010-06-03
It can be hw-relalated : try memtest, "check disk for defects", and if there is some system already installed you can also check hdd S.M.A.R.T. report. Have You tried "Rising Elephants" <be patient with this> when system freezes? - this may allow to access shell prompt - then you will be able to check logs (propably).
When nothing helps, remove all add-on cards - there can be some serious IRQ routing problem.

---

### Post by lucim100 on 2010-06-03
> **tomazzi said:**
> It can be hw-relalated : try memtest, "check disk for defects", and if there is some system already installed you can also check hdd S.M.A.R.T. report. Have You tried "Rising Elephants" <be patient with this> when system freezes? - this may allow to access shell prompt - then you will be able to check logs (propably).
When nothing helps, remove all add-on cards - there can be some serious IRQ routing problem.

Hello Tomazzi, i have found out that it have to be something with my raid controller...
i have 6 scsi hdd installed on my server and in bios it is set to scsi controller, my knowledge is not that good on the server side of computing , if i swich to raid controller it does not pick up any of my hdd, but the setup go on after network detection...
could you please explain what setting i need to set please if you know,

Regards

---

### Post by disabledaccount on 2010-06-03
> **lucim100 said:**
> 
...it have to be something with my raid controller...
...in bios it is set to scsi controller, 
...if i swich to raid controller **it does not pick up any of my hdd**, but the setup go on after network detection...What I understand is You have BIOS set to boot from SCSI controller - thats obvious and ok. But the rest is non-readable for me... :-s
Could you please explain what does it mean "it does not pick" yor hdd's?
Did you enter controller bios and created any array? (raid_xx, jbod?)

Besides, most propably you will need driver for that controller - what is exact type/model of it?

---

### Post by bloodhacker2 on 2010-10-31
Hey guys i am running into the same problem with the dell poweredge 2600 and ubuntu 10.04. Have you guys figured out a solution yet?

---

### Post by Lloyd_mcse on 2010-11-01
I was having issues installing on my Poweredge 2600 - I burned the ISO as a DVD image and it worked fine.

---

