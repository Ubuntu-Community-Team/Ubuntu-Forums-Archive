---
title: "Android-Ubuntu compatibility -- Tablet v. Notebook v. Netbook"
date: 2013-04-17
forum: The Cafe
---

### Post by ron177 on 2013-04-17
I am an avid Ubuntu user. I have a laptop and a desktop that are powered  by this particular distro. But now I am looking for a light-weight  device to help me with my work. Carrying a full-fledged laptop with me  all the time is no longer an option and I want to avoid it at all costs.  So I have been thinking of getting either an ultra light notebook, a  netbook, or a tablet. 
 
It seems that the rise of tablet computers has put the production of  netbooks to an end. So I am wondering from a Linux perspective which of  these devices are more powerful and more capable of doing the type of  work I would need them to do. And which of these devices is more Linux  friendly? My work involves dealing constantly with the open source word  processor, open source power point presentation and spread sheet,  various photo images, pdf files, and internet browsing.
 
So I guess I would like to know (1) whether a tablet, a netbook, or  alternatively an ultra light notebook would be a good choice for me and  (2) whether I would be able to create in these devices the type of  documents (such as .odt) that could be easily modified in my other Linux  devices. I know I can download Linux on both a netbook and an ultra  light notebook. But how does Android communicate with say Ubuntu? That's  something I don't know.
 
Appreciatively,
 
R

---

### Post by u-noob-tu on 2013-04-18
I don't really have any recommendations for a device, except that my personal preference would be a netbook, but I can say that android devices that are running Ice Cream Sandwich (4.0) or higher are a bit of a pain to use with Linux. The reason being that newer android devices no longer work as a mass storage device and instead use the windows MTP (media transfer protocol) to mount the device's file system. Linux does have a way to mount such devices, I believe it's libmtp or something similar. There is also a tool I tried called go-mtpfs and it worked for mounting my tablet but threw a fit when I tried to unmount it. Supposedly Ubuntu 13.04 will have better MTP support, but as it stands its a little flaky. Hope this helps.

---

