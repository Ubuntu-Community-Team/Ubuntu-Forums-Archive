---
title: "Is it possible to have a swap file on another hard drive other than the OS disk"
date: 2020-10-25
forum: Server Platforms
---

### Post by sharkey97 on 2020-10-25
Hi!


I am more or less a beginner in Ubuntu.
I am in the process of setting up an Ubuntu 18.04 server where I want a swap file on another hard drive one where Ubuntu is installed on.
The Ubuntu server will be installed on a Kingston A400 240GB disk and swap file on a Seagate FireCuda 520 SSD 2TB M.2 NVMe and intends to use the entire nvme disk as a swap file if possible.
I wonder if it is possible to do as I have thought or not.
Have googled but can not find what I am looking for. Probably me who does not search for the right word.
If there is anyone who can tell me how to do it or refer to the link to the website, I would be super happy.


Please


Sharkey97

---

### Post by CelticWarrior on 2020-10-25
Yes, the swap partition can be anywhere, a swapfile can't.
You can use a partition instead but why do you think you need so much swap anyway?

---

### Post by Impavidus on 2020-10-25
A swap partition can be on any device you want. I think a swapfile can be anywhere you want in your filesystem, but giving a device a filesystem for the sole purpose of making a swapfile there seems needlessly complicated.

Why do you think you need 500 times more swap space than everybody else?

---

### Post by grahammechanical on 2020-10-25
Swap size is connected to the amount of memory in the machine. It is when the system begins to run out of available memory that the OS has to start paging data out of memory and on to a disc.

Tradition says swap space should be twice the size of memory. That came from the days when memory costs were very high and amounts of memory were very low. With large amounts of memory available at almost reasonable prices if we followed tradition we have have an excessively large swap space that might never be used.

Which is why Ubuntu has moved from a swap partition to a swap file which expands and shrinks as necessary. It seems that it is possible to have a swap file on a separate disc to the operating system

[https://askubuntu.com/questions/1072336/can-i-change-location-of-swapfile](https://askubuntu.com/questions/1072336/can-i-change-location-of-swapfile)

[https://serverfault.com/questions/279248/linux-where-to-put-the-swap-file](https://serverfault.com/questions/279248/linux-where-to-put-the-swap-file)

Regards

---

### Post by scorp123 on 2020-10-26
> **sharkey97 said:**
>  and swap file on a Seagate FireCuda 520 SSD 2TB M.2 NVMe and intends to use the entire nvme disk as a swap file if possible.

Why so much swap?? :confused:

One of the bigger single Linux servers I was in charge of during my career was a machine with 64 x CPU cores and 512 GB of RAM and even there the swap was only 128 GB. If at 512 GB of RAM you have to swap more than 128 GB then something is *very seriously wrong* anyway and no amount of swap space could fix that.

It's your server, sure, but you're wasting 2 TB of space if you use all that just for swap. Chances are it will never even be used once.

---

### Post by rsteinmetz70112 on 2020-10-26
To do what you want use gparted to partition the drive you want to use for swap and set the partition to swap then edit fstab to mount the swap partition on boot.
As everyone else asked why to you want so much swap?

---

### Post by TheFu on 2020-10-26
Well, as others have said, you can setup lots of swap if you like, but that makes me curious why?
Within the last 6 months, there was a long thread about swap sizing in these forums with lots of opinions.

If you are running VMs for clients and want to encourage them to pay for higher-priced plans, then what you intend seems like a reasonable plan. I suspect a hugely popular, well-advertised, domain registrar company does this for all their advertised plans.

Typically, the point of swap is to provide users with a "slow" feeling for the interface, so they get some indication that the machine is beyond current capabilities. So, with that in mind, using slow swap would provide that feedback better. You could put it on a USB2 HDD to help slow it down. ;)

For all my desktops, I provide 4.1G of swap.
For all my servers, I strive to have 0 swap, since RAM is pretty cheap and managing workloads isn't hard.  

Of course, only you know the real reason.  It would be interesting to discover if over 2TB of swap causes issues or not. I bet wikipedia has the answer for any size limitations. [https://askubuntu.com/questions/1041024/is-there-a-maximum-size-at-which-a-swap-file-can-function](https://askubuntu.com/questions/1041024/is-there-a-maximum-size-at-which-a-swap-file-can-function)  Looks like 16TB for 1 swap area and up to 32 areas are allowed.  Go for it!

---

### Post by sharkey97 on 2020-11-18
Oopppsss ...
Totally forgot my message.
Many thanks for the reply.
Question!
Purely performance wise.
What is best to have the swap file on?
A custom hard drive that is a 2TB M.2 NVMe or to put the swap file on the same disk as the OS "Ubuntu Server" and in that case on a 2TB M.2 NVMe.
Or does it not matter performance in terms of having Ubuntu Server on an SSD disk and the swap file on 2TB M.2 NVMe?
It should be added that the server should be for a filcoin mining machine that requires a lot of RAM.

---

### Post by slickymaster on 2020-11-18
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2020-11-18
> **TheFu said:**
>  
Typically, the point of swap is to provide users with a "slow" feeling for the interface, so they get some indication that the machine is beyond current capabilities. So, with that in mind, using slow swap would provide that feedback better. You could put it on a USB2 HDD to help slow it down. ;)
 

Perhaps you missed this above?  Swap is there to provide feedback.  You don't want to put it onto fast storage or the users won't "feel" the system getting slower before all the virtual memory is used up and the system crashes.  If you want fast performance, never let real RAM get used it.  RAM is relatively cheap. Buy more.  I know ZERO, nothing, nada, about mining on computers.  We have to pay for electricity here.

I'm not a fan of using swap files.  I prefer using a swap LV managed by LVM. This is much more flexible than a swap partition, but keeps the swap out of a file system and that overhead.

---

