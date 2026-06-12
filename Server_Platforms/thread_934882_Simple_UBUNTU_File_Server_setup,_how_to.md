---
title: "Simple UBUNTU File Server setup, how to?"
date: 2008-10-01
forum: Server Platforms
---

### Post by DSP8000 on 2008-10-01
Hi guys,

Can someone point me to right direction on this one.
The plan is to move all data from Windows 2000 Server to Ubuntu Server as pain free and secure as possible. We are talking about 3500 clients, mostly tax returns docs.

I need some help in setting up simple file server for my friend that has accounting business. The current server is OK (sort of) but for security reasons I'd like to setup Ubuntu Server, mainly for data storage, file serving purposes. I do have some info, but I'd like to have everything properly planned before I jump the gun.

Step by step instructions would be great and judging by the posts on the forum, looks like I'm better of to wait for the 8.10 server because of bugs in 8.04.1. Also, I hope that the new 8.10 will have reliable samba gui for easy sharing and security. I had a quick look on how to forge and ubuntu+ebox is the closest to my easy setup requirements.

The scenario is:
1 reception PC and 3 PC's for accountants. Data would be stored on server and everyone of them would have read/write access to 4 folders only named 1RECEPTION, 2PC1, 3PC2, 4PC3.

I hope that my explanation understandable.
Any help would be greatly appreciated. 

Cheers,
DSP8000

---

### Post by volkswagner on 2008-10-01
Why not just get an NAS device. Low power consumption and can be secured.

These are raid capable and have decent reviews.  

[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16822155003]("http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16822155003")

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822165075]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822165075")
 

Bigger budget?

[http://www.cdw.com/shop/products/default.aspx?EDC=1178837&cm_sp=Product-_-Overview-_-Main+Tab]("http://www.cdw.com/shop/products/default.aspx?EDC=1178837&cm_sp=Product-_-Overview-_-Main+Tab")

If you really want to build something check out FreeNAS.

[http://www.freenas.org/index.php?option=com_openwiki&Itemid=30]("http://www.freenas.org/index.php?option=com_openwiki&Itemid=30")

---

### Post by lykwydchykyn on 2008-10-01
Some questions:
 - Does everyone need read/write to every share, or do each of the computers need read/write to its respective share only?
 - Do you need user authentication for the shares, or are they wide open on the network?

---

### Post by DSP8000 on 2008-10-01
4 workers need to have access only to the 4 shared folders. The shared folders can be accessed by any of the 4 workers and yes, the shares need to be secured on the network.I would prefer user authentication for the shares.

NAS device is my second option, however I'd prefer full file server with expanding capabilities down the track.

Tnx. for all suggestions so far.

DSP8000

---

### Post by lykwydchykyn on 2008-10-01
Samba should be able to handle this quite easily.  Have you checked out the "Samba by example" document on the Samba website?  It's very well written, and goes through scenarios similar to yours and how to set up samba for them.  The only caveat I have for it is that it's very redhat/suse oriented, so you have to ignore some of the install or OS configuration stuff, though the actual samba configuration part is pretty much the same.

I like the webmin gui for Samba, you could make short work of this using webmin.  

A few points of advice:
 - Use "user mode" security, and if you can set up your samba/linux users with the same usernames and passwords as on the windows boxes.  This saves them from being prompted for a login when mapping to the drive.
 - Install acl support, and each user to the acl for each shared directory.  This helps avoid permissions conflicts.  Remember, local and share permissions both apply.
 - Use the "hosts allow" directive to limit samba access to the local network.

You can find pretty good howtos around here or at howtoforge for most of this stuff, or just ask if you have questions.

---

### Post by windependence on 2008-10-02
If they're running QuickBooks, you can set up a backend Linux server for them also:

[http://enterprisesuite.intuit.com/resources/linux.jsp](http://enterprisesuite.intuit.com/resources/linux.jsp)

-Tim

---

### Post by DSP8000 on 2008-10-02
Tnx. a lot guys. Samba by example is very outlined source and definitely worth a look. I'm looking for some gui to simplify the task. There's some floating around so I'll check them out.
The plan is to do this test setup on a different pc and if everything goes well, we'll stick with it.

Tnx. again for the pointers.

Cheers,
DSP8000

---

