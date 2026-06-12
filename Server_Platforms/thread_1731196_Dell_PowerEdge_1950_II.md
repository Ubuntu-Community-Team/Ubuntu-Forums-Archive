---
title: "Dell PowerEdge 1950 II"
date: 2011-04-16
forum: Server Platforms
---

### Post by juzzy on 2011-04-16
I am considering purchasing a refurbished Dell PowerEdge 1950 II server. Does anyone know if there are any issues with installing ubuntu server edition onto this model. Thanks in advance for any advice.

---

### Post by MakOwner on 2011-04-16
> **juzzy said:**
> I am considering purchasing a refurbished Dell PowerEdge 1950 II server. Does anyone know if there are any issues with installing ubuntu server edition onto this model. Thanks in advance for any advice.

I have PowerEdge 350, 1650, 1750 and 2950 servers.
I have been able to load Ubuntu on all of them. 
I typically use the minimal installation CD image.

The 1650, 1750 and 2950 all have various generations of the PERC raid controllers and after configuring the array in the Dell firmware the appropriate drivers load during the install with no issue for me so far.

---

### Post by juzzy on 2011-04-16
fantastic! thank you

---

### Post by MakOwner on 2011-04-16
> **juzzy said:**
> fantastic! thank you

There are some tools from dell to manage the hardware - it's called OpenManage or some such.  I haven't had much luck with it so far.

---

### Post by juzzy on 2011-04-19
for anyone thinking of doing the same I have now installed the 10.10 server edition on this model with no problems, all working fine and dandy. Happy days!

---

### Post by collisionystm on 2011-04-19
I have used Ubuntu Server on several Power edge servers with no issues. I had more issues trying to load Server 2008 on one then I ever did with Ubuntu. I actually ended up using Zentyal 2.0 and its awesome.

---

