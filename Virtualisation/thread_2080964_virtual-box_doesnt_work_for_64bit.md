---
title: "virtual-box doesnt work for 64bit"
date: 2012-11-05
forum: Virtualisation
---

### Post by jonathandawdy on 2012-11-05
I need to use virtual-box to run other os's but i want to run 64 bit-versions but if i do it doesn't work i attached pictures. of the processes of me doing it.

---

### Post by 2F4U on 2012-11-05
Can't see any pictures. Did you really attach them?

---

### Post by pkadeel on 2012-11-05
In order to run a 64bit client in virtualbox, your hardware must be 64bit. Incase you are using a 32bit operating system on a 64bit hardware then hardware virtualization must also be in BIOS settings.

---

### Post by jonathandawdy on 2012-11-06
> **2F4U said:**
> Can't see any pictures. Did you really attach them?

> **pkadeel said:**
> In order to run a 64bit client in virtualbox, your hardware must be 64bit. Incase you are using a 32bit operating system on a 64bit hardware then hardware virtualization must also be in BIOS settings.

Dont worrie i have 64bit ubuntu.
and here is a resend of the picture.

they were bigger then the max size so there are two parts  so ya i numbered the pics for ya

---

### Post by proggy on 2012-11-06
> **pkadeel said:**
> In order to run a 64bit client in virtualbox, your hardware must be 64bit. Incase you are using a 32bit operating system on a 64bit hardware then hardware virtualization must also be in BIOS settings.
This

---

### Post by pkadeel on 2012-11-06
It is the problem of hardware virtualization according to image 16 & 17. You have it enabled in your client machine setup but in host's BIOS it is turned off.
Either turn it of in client or turn it on in host's BIOS.

As a side note, 10GB is not sufficient for windows 7. As per microsoft minimum space requirement for win 7 is;
16 GB available hard disk space (32-bit) or 20 GB (64-bit)

---

### Post by jonathandawdy on 2012-11-07
> **pkadeel said:**
> It is the problem of hardware virtualization according to image 16 & 17. You have it enabled in your client machine setup but in host's BIOS it is turned off.
Either turn it of in client or turn it on in host's BIOS.

As a side note, 10GB is not sufficient for windows 7. As per microsoft minimum space requirement for win 7 is;
16 GB available hard disk space (32-bit) or 20 GB (64-bit)

------------------------------------------------------------------
thank you i shal try that and plz if virual box 64 bit exsistes or there are repositorys that synaptic package manager doesnt speak of tellme. 

I WILL REPOST THE LAST PICTURES AFTER I CHANGE MY MISSTAKE.

STILL DAES THE SAME THING WHEN I GIVE IT 25 GIGS. AND I WENT T THE PACAGE MANAGER AND INSTALED EVER PACAGE THAT HAD VIRTUALBOX IN THERE NAME

---

### Post by cwsnyder on 2012-11-07
In the repositories, you have only the VirtualBox OSE (Open Source Edition), but there are different 32-bit and 64-bit free-of-charge versions at virtualbox.org which are different and non-open source.

To use these versions you _must_ have some understanding of adding repositories to your /etc/sources.list, the problems and pitfalls.

---

### Post by pkadeel on 2012-11-07
> **jonathandawdy said:**
> ------------------------------------------------------------------
thank you i shal try that and plz if virual box 64 bit exsistes or there are repositorys that synaptic package manager doesnt speak of tellme. 

I WILL REPOST THE LAST PICTURES AFTER I CHANGE MY MISSTAKE.

STILL DAES THE SAME THING WHEN I GIVE IT 25 GIGS. AND I WENT T THE PACAGE MANAGER AND INSTALED EVER PACAGE THAT HAD VIRTUALBOX IN THERE NAME
Yes there are both 32bit and 64bit versions available at virtualbox.org site. Instead of downloading the .deb file, I personally prefer installing it through their repository. Detailed procedure is clearly mentioned in the linux downloads section.

One thing which I forgot to mention in my last post is that if by any chance you opt to disable hardware virtualization for client then you shall also allocate only one cpu for the client otherwise you will again get the VT-x disabled error message.

---

### Post by oldos2er on 2012-11-07
Moved to Virtualisation.

---

### Post by jonathandawdy on 2012-11-07
> **pkadeel said:**
> Yes there are both 32bit and 64bit versions available at virtualbox.org site. Instead of downloading the .deb file, I personally prefer installing it through their repository. Detailed procedure is clearly mentioned in the linux downloads section.

One thing which I forgot to mention in my last post is that if by any chance you opt to disable hardware virtualization for client then you shall also allocate only one cpu for the client otherwise you will again get the VT-x disabled error message.

-----------------------------------------------------------------
Here is my ubuntu information if relivent. but can you give me a link to install it so i do this right the first time.

[SIZE="3"]UBUNTU[/SIZE]

Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-32-generic
GNOME 3.4.2

---

### Post by pkadeel on 2012-11-08
> **jonathandawdy said:**
> -----------------------------------------------------------------
Here is my ubuntu information if relivent. but can you give me a link to install it so i do this right the first time.

[SIZE=3]UBUNTU[/SIZE]

Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-32-generic
GNOME 3.4.2
Just sent you a PM containing detailed installation and client setup procedure. If that solves your issue then please mark this thread as solved.

---

### Post by jonathandawdy on 2012-11-08
Please will a staff member mark this as solved for i have found the problem.

THE ANSWER YOU HAVE BEEN WAITING FOR IS.....
My processor isn't compatible with virtual technology thus 64bit VT'S wont work.

THIS IS SOLVED PLEASE MARK IT AS SUCH

---

### Post by howefield on 2012-11-08
> **jonathandawdy said:**
> Please will a staff member mark this as solved for i have found the problem.

Done, however it is very easy to do that yourself. 

Thread tools > "Mark this thread as solved"

---

### Post by jonathandawdy on 2012-11-13
> **howefield said:**
> Done, however it is very easy to do that yourself. 

Thread tools > "Mark this thread as solved"
---------------------------------------------------------------
Oh thanks i always saw that on moderators it said "notify me if a thread is solved" so i just assumed. But thanks

---

