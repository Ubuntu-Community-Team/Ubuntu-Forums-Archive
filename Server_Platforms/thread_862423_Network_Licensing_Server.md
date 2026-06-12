---
title: "Network Licensing Server"
date: 2008-07-17
forum: Server Platforms
---

### Post by diablothe2nd on 2008-07-17
Hi Folks,

Long time lurker and first time poster so hope you guys can help.

My boss is looking to upgrade our server, and after putting ubuntu server under his nose he seems interested at the thought of more stability, not to mention that it's cheaper than windoze server, but there's just one thing that seems to be holding it back, and that's network licensing.

We have Autodesk Viz, and NBS both obtaining their licenses from the current windoze server.

Are you folks aware of any way I can get the potential ubuntu box to pick up this job?

Is there a network licensing application freely available (for commercial use) for ubuntu?

many thanks

---

### Post by TreeFinger on 2008-07-17
ignore this, i mis-read

---

### Post by silverglade00 on 2008-07-17
This is something that will have to run on a Windows server. Microsoft would never allow a Linux based Windows License server. There is still hope, though. Since a license server should not need too much in the way of resources, you could run it as a virtual machine on the Linux server and still use the server for other things.

---

### Post by diablothe2nd on 2008-07-17
I was afraid that may be the answer.

It kind of negates the point of choosing Linux though as the boss would have to pay for windows server to legally be able to run it in the virtual machine :(

---

### Post by windependence on 2008-07-17
This is not true. I know of at least one company that uses a Unix machine for serving licenses but not these particular products. Check with Autocad and see if they have a licensing server available for Unix or Linux.

-Tim

---

### Post by windependence on 2008-07-17
Looks like they support a number of platforms. Google is your friend.

[http://usa.autodesk.com/adsk/servlet/ps/dl/item?siteID=123112&id=9775899&linkID=9242259](http://usa.autodesk.com/adsk/servlet/ps/dl/item?siteID=123112&id=9775899&linkID=9242259)

-Tim

---

### Post by diablothe2nd on 2008-07-18
that would be great if we used maya :(

i'll have another round of googling later, i'm all googled out hehe :D

---

### Post by diablothe2nd on 2008-07-18
after a phonecall today to both Autodesk and NBS, neither of them support linux as a licensing server for Viz or NBS :(

thanks anyways folks

---

### Post by promodus on 2008-07-20
Have you considered running the windows licensing server on a virtual machine?

This way you can handle your legacy stuff without too much headache and as the non-windows versions become available transfer them to the Linux host.

Just a thought

---

