---
title: "SSH Segmentation Fault?"
date: 2015-07-12
forum: Server Platforms
---

### Post by streat on 2015-07-12
Hello, I am having difficulty with my Ubuntu 14.04 server. I had this fully functioning with SSH working just fine and it just crapped out this morning. When trying to SSH into the server I am given this:

```
Last login: Sat Jul 11 15:10:02 2015 from [my location]
Segmentation fault
Segmentation fault
/usr/bin/lesspipe: 295: [: =: unexpected operator
```

I am logged in sort of but any command I try to run returns this:
 
```

Segmentation fault
```

If I try to run a service like htop I am given this:


```
-bash: /usr/lib/command-not-found: Input/output error
```

Unfortunately I am away from my server and I will be for some time, can anyone provide any advice as to how I should proceed?
Thank you!

---

### Post by QIII on 2015-07-12
*Moved to **Server Platforms***

Please use code tags:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by streat on 2015-07-12
Thank you for the help with post formatting!

---

### Post by streat on 2015-07-12
Update: Rebooted the machine, Boot drive didn't even show up. I default to thinking hardware problems but the drive is an Intel Pro 2500 SSD which seems unlikely but I suppose is possible.

---

