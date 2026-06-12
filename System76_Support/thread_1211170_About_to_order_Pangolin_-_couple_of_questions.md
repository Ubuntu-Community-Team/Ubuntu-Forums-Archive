---
title: "About to order Pangolin - couple of questions"
date: 2009-07-12
forum: System76 Support
---

### Post by SiberianBear on 2009-07-12
After a lot of shopping around, it's pretty clear that the Pangolin Performance is the best linux laptop out there.

Before I order, couple of questions:

- What is the default partition layout like? Everything in / or is there a separate /var /home etc?

- Is it possible to request a custom partition layout at order-time, if everything is in / ?


I'm looking forward to being the (possibly) only one with this laptop in Siberia :D

---

### Post by Eldera on 2009-07-12
The Pangolin comes set up with four partitions: root, boot, swap, and home. This is pretty easy for the customer to modify, if you want something different. You can shrink the home partition and add other partitions in the free space created.

If you check the S76 website, I think you will find that they ship only to the US and Canada. (Perhaps you are coming here for a vacation?:p) They are unable to give full hardware support outside the US. If something goes wrong the customer has to pay shipping back to the US. See the details in their warranty.

[http://system76.com/](http://system76.com/)

---

### Post by Derath on 2009-07-12
I believe it's root/boot combined, so it's be partition 1 = /, partition 2 = /home, and partition 3 = /swap.

iirc, depending on drive, / gets ~ 15G, /swap = ~ 3-4G, and /home gets the rest.

Really enjoyed the setup myself (panp4n)

---

### Post by betrunkenaffe on 2009-07-12
Mine is

/
/home
and swap

---

### Post by SiberianBear on 2009-07-12
> **Eldera said:**
> The Pangolin comes set up with four partitions: root, boot, swap, and home. This is pretty easy for the customer to modify, if you want something different. You can shrink the home partition and add other partitions in the free space created.

Oh?

Is everything setup using LVM, then? That'd be great.

> **Eldera said:**
> 
If you check the S76 website, I think you will find that they ship only to the US and Canada. (Perhaps you are coming here for a vacation?:p)


Not a problem, I'm in NYC for a little bit. Plus, there's always this: [http://www.myusabox.com/Default.aspx](http://www.myusabox.com/Default.aspx)  :)


> **Eldera said:**
> 
They are unable to give full hardware support outside the US. If something goes wrong the customer has to pay shipping back to the US. See the details in their warranty.
[http://system76.com/](http://system76.com/)

Well then I hope the QA process is good enough to assure me I won't need hardware support. :D

---

### Post by thomasaaron on 2009-07-13
We don't use LVM. We tried it once in the past, and it was a world-class hassle.

Partitions are set up as...

/(root)... ext3... 15GB
/swap... equal to installed RAM
/home... ext3... remainder of disk

---

### Post by SiberianBear on 2009-07-13
> **thomasaaron said:**
> We don't use LVM. We tried it once in the past, and it was a world-class hassle.

Partitions are set up as...

/(root)... ext3... 15GB
/swap... equal to installed RAM
/home... ext3... remainder of disk

Ok, thanks

---

