---
title: "Serverupgrade"
date: 2012-03-15
forum: Server Platforms
---

### Post by hallo200 on 2012-03-15
Hallo Forum,


I have done a ubunut 8.04 server 32bit upgrade like discribed here
[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

Now i have a pae-kernel in my grub list. 

Why isnt there a server kernel?


with kind regards
hallo200

---

### Post by 2F4U on 2012-03-15
This thread may answer your question

[http://ubuntuforums.org/showthread.php?t=1645099](http://ubuntuforums.org/showthread.php?t=1645099)

---

### Post by jerome1232 on 2012-03-15
edit: See the post above mine, linux-image-server does just install the pae kernel on a 32bit machine.

---

### Post by hallo200 on 2012-03-15
Thanks for answering.

So 10.04 32 server kernel are named pae? Is this right?

So, there is no  "server" kernel for 10.04 32bit? 

with kind regards
hallo200

---

### Post by 2F4U on 2012-03-15
As far as I understand it, it is just a naming issue.

---

### Post by trundlenut on 2012-03-15
the pae bit is all about memory access - a pae kernel can work with more than 4gb of memory.

---

### Post by hallo200 on 2012-03-16
I have just 2GB Ram in the server. Could this be a problem?

thanks, with kind regards
hallo200

---

### Post by trundlenut on 2012-03-16
> **hallo200 said:**
> I have just 2GB Ram in the server. Could this be a problem?

thanks, with kind regards
hallo200

It shouldn't be, a pae kernel can handle anything below 4gb of ram quite happily.

---

