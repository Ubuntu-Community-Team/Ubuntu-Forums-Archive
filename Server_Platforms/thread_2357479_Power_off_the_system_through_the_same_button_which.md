---
title: "Power off the system through the same button which I used to power on the system"
date: 2017-04-02
forum: Server Platforms
---

### Post by sed_faster on 2017-04-02
Hello folks,

I pretend shutdown (power off, I don't understand if this words it is different in English) my ubuntu server through button power. I need know if I press button it is correct to process shutdown the system. Normally I access this server through ssh and execute this command:
```

sudo shutdown

```
But if I press the same button which I used to power on the server the system will shutdown. I haven't tottaly secure if this method is good. I should and I can use this method?

My version is: Ubuntu Server 16.04 LTS

Thanks
Note: please tell me if my explanation, in English, was good for you!

---

### Post by wildmanne39 on 2017-04-02
*Thread moved to **Server Platforms**.*

---

### Post by wildmanne39 on 2017-04-02
You should use the command:
```
sudo shutdown -h now
```
if you push the power button it will cause a hard drive crash eventually.

---

### Post by sed_faster on 2017-04-02
Hooo, sorry! I should say "sudo poweroff! Is it the same?
Okay, but if I want to arrange a way faster?

---

### Post by wildmanne39 on 2017-04-02
Do you have a desktop installed?

Edit:

Have a look at this link:

[http://quehow.com/how-to-shutdown-and-restart-your-system-using-terminal-in-ubuntu-14-04/6891.html](http://quehow.com/how-to-shutdown-and-restart-your-system-using-terminal-in-ubuntu-14-04/6891.html)

---

### Post by sed_faster on 2017-04-12
No, This environment it is an ubuntu server!
I turn on the pc through button on front PC but when I need shutdown I always have open terminal, access through ssh this server and run "sudo shutdown -h now". This it is too much steps to do a simple task.

---

