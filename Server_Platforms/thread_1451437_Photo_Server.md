---
title: "Photo Server"
date: 2010-04-10
forum: Server Platforms
---

### Post by gcndavidmn on 2010-04-10
My dad is a photographer and pretty soon he will be approaching the 8TB mark and I think it's time he had a server for it. I've searched around and I thought I could build him one and put Ubuntu Server Edition on it.

I know this is going to be expensive as he is probably going to need to mirror the hard drives, so here is my plan:
A beast of a case
A mobo with many sata ports
Probably going to need some SATA controllers due to the number of drives
10 2TB drives (thats where its painfully expensive)
The rest of the parts.

I was thinking of sticking them in RAID 1 and running a server so that he can access it over the network.

Here is the question, is this a good idea? (BTW he would be paying for the parts) If so what parts should I be looking out for?

---

### Post by Sporkman on 2010-04-11
You could always think about a dedicated NAS machine, but the most HD bays available I can see on newegg.com is 6...

Re photo serving software, might I suggest gallery2 - it's a commercial-grade package that's very powerful & feature rich, and is in the Ubuntu repos.

---

### Post by gcndavidmn on 2010-04-12
Is there a way of converting DVD bays into 3.5" hard drive bays? If so then it would make this a hell of a lot easier.

---

### Post by pommie on 2010-04-12
A drive bay adapter to enable 3.5"drives to use 5.25" bays, they come in all sorts of shapes, quality and price, do a 'Google' for "drive bay adapter" in your area.

Cheers David

---

### Post by gcndavidmn on 2010-04-12
Brilliant. Thank you. It looks like I could do this.

---

### Post by 1serveyou on 2010-04-12
> **gcndavidmn said:**
> Brilliant. Thank you. It looks like I could do this.


Couldn't you just put an Sata controller in the current PC? Or Isn't there anyway to have an internal connection but have the wires go outside of the case?

---

### Post by jfmanamtr on 2010-04-12
Well, if you have a few external bays, you could always do something like this:
 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817332011&cm_re=drive_bay-_-17-332-011-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16817332011&cm_re=drive_bay-_-17-332-011-_-Product)
 
Or if you didn't mind having 2 parts to the photo server:
 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817707156&cm_re=esata-_-17-707-156-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16817707156&cm_re=esata-_-17-707-156-_-Product)
 
I have the AMS backplane in my server & have had no complaints. Hope that give you some other ideas.
 
~John

---

### Post by 98cwitr on 2010-04-12
1. You need to build a NAS
There are rack mount chassis that will hold up to 32 drives and already have the controllers built in

[http://www.aberdeeninc.com/abcatg/Chassis5U.htm](http://www.aberdeeninc.com/abcatg/Chassis5U.htm)

2. Buy 20 1TB drives...much cheaper

3. Go RAID 5 or 10...RAID 1 is going to be a waste of drives, money, and space

jm2c

4. The other option would be to build a SAN with multiple, less expensive machines...but in the end it would probably cost more. What kind of budget are we playing with?

---

