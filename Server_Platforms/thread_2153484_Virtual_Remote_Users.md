---
title: "Virtual Remote Users"
date: 2013-06-11
forum: Server Platforms
---

### Post by pisio on 2013-06-11
Hello,  
I'm looking for solution for this problem.
I have small office with  5 -6 pc. Is there any way to create virtual remote desktop. I see something like that  at schools.
There is monitor, keyboard, mouse connected to  server. When you sit at this computer you actualy connect to  remote desktop at this server.
And I think it will be more inexpensive of that  I spend tones of money to get  6x PC + monitor , keyboard , mouse...
PC will use only for php and java developing. And what kind of  server I must get if is it possible ?

---

### Post by mlentink on 2013-06-11
You might want to take a look at the Linux Terminal Server project: [http://www.ltsp.org/](http://www.ltsp.org/)

---

### Post by SeijiSensei on 2013-06-11
I think you might find the costs of terminal equipment plus a hefty enough server to support them may not be much different from buying half-a-dozen PCs.  Here's the [cheapest thin client from Wyse](http://www.newegg.com/Product/Product.aspx?Item=N82E16859222087) I could find at NewEgg.   It costs $240 and still needs a keyboard, mouse and monitor.  Dell sells a [20" all-in-one computer]("http://www.dell.com/us/p/inspiron-one-20-2020-aio/pd") with 4 GB of memory and a 1 TB drive for $479.

---

### Post by Cheesemill on 2013-06-11
+1 for LTSP, it's the easiest way to set up thin clients on Ubuntu.

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

If you want to do some quick testing then the bootable Edubuntu Live DVD lets you run an LTSP server with the click of a button.
[http://edubuntu.org/documentation/ltsp-live](http://edubuntu.org/documentation/ltsp-live)


> **SeijiSensei said:**
> I think you might find the costs of terminal  equipment plus a hefty enough server to support them may not be much  different from buying half-a-dozen PCs.  Here's the [cheapest thin client from Wyse]("http://www.newegg.com/Product/Product.aspx?Item=N82E16859222087") I could find at NewEgg.   It costs $240 and still needs a keyboard, mouse and monitor.  Dell sells a [20" all-in-one computer]("http://www.dell.com/us/p/inspiron-one-20-2020-aio/pd") with 4 GB of memory and a 1 TB drive for $479.
It's true that if you are buying all new equipment then purpose built thin clients aren't cheap, but using LTSP you can often repurpose old machines that were destined for the tip or pick up dirt cheap second hand PC's to use as clients (obviously power consumption needs to be taken into account as well). As a side note one of my projects at the minute is researching using the Raspberry Pi as a client using [BerryTerminal]("http://www.berryterminal.com/doku.php"), $35 would be a great price for a client if it's suitable for the job (initial results are promising).

---

### Post by pisio on 2013-06-11
Thanks for all of you ! 
I think LTSP  is that I'm looking for. Thanks again ! 
<3

---

