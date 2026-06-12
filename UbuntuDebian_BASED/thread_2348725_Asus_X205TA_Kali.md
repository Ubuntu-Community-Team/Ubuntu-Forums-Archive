---
title: "Asus X205TA Kali"
date: 2017-01-06
forum: Ubuntu/Debian BASED
---

### Post by xmaspaul on 2017-01-06
Hello

I installed **Kali** on my asus X205TA and I have a **problem** regarding **grub** file editing.
I go to the etc/default folder and when I hit nano grub it doesn t display any line but instead : " **Error reading lock lock file ./.grub.swp: Not enough data read** "

Can u please help me Linux gurus ? :)

Thank you

---

### Post by howefield on 2017-01-06
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by ajgreeny on 2017-01-06
Can you read the file if you go to it in the file manager of kali and open it in the default GUI text editor?
Does you kali install have any GUI or is it command line only?

---

### Post by xmaspaul on 2017-01-07
ajgreeny,

It worked with the GUI text editor :)
Thank you for your answer and your help ! 

Do you have any idea what might be the problem when I use the command prompt ?

---

### Post by ajgreeny on 2017-01-07
None, I'm afraid.
Can you open any other text files using nano?

---

### Post by xmaspaul on 2017-01-07
Yes I can open the hosts file for example

edit : ajgreeny,

When I **installed** Kali I **updated** and **upgraded** everything right **after the installation**. 
I **reinstalled** the whole system and I had** no problem** to open the **grub** file with **nano**.

So it kinda sucks because I don t want to upgrade/update it if some problems like this appear.
Do u reckon it is related to the upgrade ?

---

### Post by ajgreeny on 2017-01-08
> **xmaspaul said:**
> Yes I can open the hosts file for example

edit : ajgreeny,

When I **installed** Kali I **updated** and **upgraded** everything right **after the installation**. 
I **reinstalled** the whole system and I had** no problem** to open the **grub** file with **nano**.

So it kinda sucks because I don t want to upgrade/update it if some problems like this appear.
Do u reckon it is related to the upgrade ?
Could be, as users do sometimes have difficulties related to that.
However, I have never updated from one version to another, if that is what you mean; I always do a clean installation, which with a separate /home partition, takes about 20-30 minutes, so have no experience of update problems.

Nor, I hasten to add, do I know kali at all.

---

