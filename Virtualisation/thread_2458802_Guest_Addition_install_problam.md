---
title: "Guest Addition install problam"
date: 2021-03-04
forum: Virtualisation
---

### Post by barbenezri on 2021-03-04
Hello everyone!


I watch a few tutorials on installing Guest Additions on YouTube, and on every one of them (after click Device >>Insert Guest Additions CD image) an autorun pop up on the screen while I get only option to open the file and watch the documents , even after click the execute file nothing happens.
Why is this happen and how can I solve it?
[https://ibb.co/K9v1PQ4](https://ibb.co/K9v1PQ4)

---

### Post by howefield on 2021-03-04
Thread moved to the "*Windows*" forum which seems to be a beter fit.

---

### Post by barbenezri on 2021-03-06
pop-up

---

### Post by TheFu on 2021-03-06
Please step back and start from the beginning.  You've jumped in about 5 steps and we can't guess where you think you are.
Is this something related to virtualization?
What is the hostOS?
What is the guestOS?
Which hypervisor is being used?

Or is it something else?

I'm sorry to say, but we cannot read your mind. We need facts.  Tell use the story.

---

### Post by ajgreeny on 2021-03-06
The only **guest-additions** I know of is that for VirtualBox so I have therefore now moved this thread to Virtualisation.

---

### Post by barbenezri on 2021-03-07
My computer runs on Windows 10
With VirtualBox Version 6.1 I'm runs on Ubuntu 20.10 
Everything is running OK except that i cant run disk 
the best way to show my problem is with video [https://www.youtube.com/watch?v=RxmGFsaOyks&t=137s](https://www.youtube.com/watch?v=RxmGFsaOyks&t=137s)
on sec 0:50~ after clicking "Insert...."  the message i get is the image I sent on the first comment

---

### Post by CelticWarrior on 2021-03-07
You can do it [the hard way]("https://www.tecmint.com/install-virtualbox-guest-additions-in-ubuntu/") or install from the repositories:
```
sudo apt install virtualbox-guest-dkms
```

---

### Post by barbenezri on 2021-03-07
> **CelticWarrior said:**
> You can do it [the hard way]("https://www.tecmint.com/install-virtualbox-guest-additions-in-ubuntu/") or install from the repositories:
```
sudo apt install virtualbox-guest-dkms
```

Thank you, its now work.
any idea why this is happening ?

---

### Post by CelticWarrior on 2021-03-07
Why what is happening?
Installing from the Virtualbox's own ISO needs to be done as described in the link. The ISO mounted when "insert" is issued contains software for different OSes. You shouldn't expect it run the installer automatically and you really don't want such behavior.

---

### Post by barbenezri on 2021-03-07
> **CelticWarrior said:**
> Why what is happening?
Installing from the Virtualbox's own ISO needs to be done as described in the link. The ISO mounted when "insert" is issued contains software for different OSes. You shouldn't expect it run the installer automatically and you really don't want such behavior.

Thank you! this was very helpful!

---

