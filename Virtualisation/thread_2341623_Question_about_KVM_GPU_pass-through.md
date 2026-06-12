---
title: "Question about KVM GPU pass-through"
date: 2016-10-29
forum: Virtualisation
---

### Post by spydrex on 2016-10-29
I have a question that I couldn't find the answer to with Google. I am following the tutorial in this link for reference  [https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/]("https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/")
The problem that I am having is that in step 5 it is asking me for the virtual machine identifier which I have never heard of before. I am supposed to replace the "#" in 
```
sudo gedit /usr/vm#
``` 
but I don't have a clue what I would type in its place. This is going to be for a Windows 10 home machine that I am trying to create and am trying to pass through my GTX 970 to the guest. I am going to use my GT 240 as my host GPU if that makes any difference. Forgive me for my ignorance and have patience with me as I am new to Ubuntu or Linux in general.

---

### Post by deadflowr on 2016-10-29
*Thread moved to **Virtualisation**.*

---

### Post by KillerKelvUK on 2016-10-31
Hey spydrex, step 5 is about creating a custom script which is essentially a file which contents the text as shown in the guide, you can name this file whatever you like, it doesn't have to match anything on your system.  For example you could use "/usr/my-vm-script-file", however the guide is basically saying use something that will be unique to the virtual machine you're going to create.

---

### Post by spydrex on 2016-11-01
Thank you, I now understand. I was able to set everything up but now I have ran into a problem and if you don't mind was wondering if you could help me solve it. When starting the VM the hosts screen goes black connected to the GT 240 and when plugging the second monitor into my guest gpu the GTX 970 it is also black. I know Ubuntu hasn't crashed or anything but the display for some reason turns off. I checked and made sure I was using 02:00:0 and 02:00:1 which is my 970 so idk why my hosts monitor would suddenly go black and why my guests monitor would also not display an output.

EDIT: Nevermind I fixed it by reinstalling drivers. Thanks for the help, I will mark this as solved:3

---

