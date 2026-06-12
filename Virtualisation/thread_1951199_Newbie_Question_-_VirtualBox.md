---
title: "Newbie Question - VirtualBox"
date: 2012-04-02
forum: Virtualisation
---

### Post by gabrielshier on 2012-04-02
Hey,
Just upgraded to 12.04 and it's a huge improovment. 
My question is regarding the VirtualBox.

Have multipile machines running under VBox and need to run a few of them at a time. Since linux treats everything as a file, is there any (relativly) easy way, to make the virtual RAM (Base Memory as called in VBox) not a refference a a real memory but to a swap file on one of my partitions? 
If this is possible please reffer me to the guide/tutorial. 

My machine is running Ubuntu 12.04 with original Unity. 
Kernel - 3.2.0-21-generic-pae .
VBox version of 4.1.10 .
Virtual Machines are: W2k3 Server, W2k8 Server R2, WXPSP1, WXPSP3, Win7, Win8, Win2k3 and one BT5R2 machine...

Thanks in advance

---

### Post by nothingspecial on 2012-04-02
*Thread moved to **Virtualization**.*

---

### Post by gabrielshier on 2012-04-03
Nothing?

---

### Post by QIII on 2012-04-03
Not that I know of.  If I get a chance, I'll dig through the documentation or go to a few forums.

I wonder, however, if you might find your vms to be dog slow.

---

### Post by Cheesemill on 2012-04-03
You are probably better off just having a large swap partition/file on your Ubuntu installation and letting the linux kernel handle all of the memory and swap access.

But I agree with QIII above, it's likely to be slow.

Do you actually need several VM's running at the same time or can you pause most of them?

The proper solution would be to get more RAM, I just picked up another 4GB for my machine for £20.

---

### Post by CharlesA on 2012-04-03
> **Cheesemill said:**
> You are probably better off just having a large swap partition/file on your Ubuntu installation and letting the linux kernel handle all of the memory and swap access.

But I agree with QIII above, it's likely to be slow.

Do you actually need several VM's running at the same time or can you pause most of them?

The proper solution would be to get more RAM, I just picked up another 4GB for my machine for £20.
What he said.

I don't believe this is possible. The only way you can set a VM to use "swap" instead of RAM is to run out of memory.

---

### Post by Rebelli0us on 2012-04-06
Swap files would slow you down. I have a Phenom II quad with 8 GB ram and can easily run Ubuntu, and 2-3 other OSes simultaneously.

---

### Post by Rebelli0us on 2012-04-06
Here it is running Win2k and Win7. And occasionally I boot up Guests XP and Win8 preview for testing apps.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212449&stc=1&d=1328903048[/IMG]

---

### Post by gabrielshier on 2012-04-07
Hey,
Well, first off, thank you all for the comments. :)

The idea of swap partition is known but i didn't want to get there. I am a penetration tester and instructor so a lot of times i need those VMs for my students and acctually get a few windows machine connecting to another VM which have AD on it - as an assault simulator. 
At normal my computer have 4GB ram and can handle 5-7 VMs depending on the machines i run. The issue is that since linux treats everything as a file, thought i can get this to work. About getting my RAM bigger is always an option that's true, but i have an IBM Thinkpad X61 so it supports up to 4GB (the motherboard) so i'll have to buy a new laptop (preferebly System76, once they get thier stock replenished :) ). 

Really don't care that the machines will be slow. They don't need to be really fast, they just need to respond normally to outside connections and i don't assume that they will be that slow...

Any ideas?

Thanks again.

---

### Post by gabrielshier on 2012-04-07
Oooh, and Rebelli0us - how about this?
[IMG]https://fbcdn-sphotos-a.akamaihd.net/hphotos-ak-ash4/424034_3217138700243_1019638145_33105634_522372645_n.jpg[/IMG]

---

### Post by Cheesemill on 2012-04-07
> **gabrielshier said:**
> Hey,
Well, first off, thank you all for the comments. :)

The idea of swap partition is known but i didn't want to get there. I am a penetration tester and instructor so a lot of times i need those VMs for my students and acctually get a few windows machine connecting to another VM which have AD on it - as an assault simulator. 
At normal my computer have 4GB ram and can handle 5-7 VMs depending on the machines i run. The issue is that since linux treats everything as a file, thought i can get this to work. About getting my RAM bigger is always an option that's true, but i have an IBM Thinkpad X61 so it supports up to 4GB (the motherboard) so i'll have to buy a new laptop (preferebly System76, once they get thier stock replenished :) ). 

Really don't care that the machines will be slow. They don't need to be really fast, they just need to respond normally to outside connections and i don't assume that they will be that slow...

Any ideas?

Thanks again.

Just go for the swap idea I mentioned above.

Even if there was another method it wouldn't be any faster or have any advantages over the swap method.

---

