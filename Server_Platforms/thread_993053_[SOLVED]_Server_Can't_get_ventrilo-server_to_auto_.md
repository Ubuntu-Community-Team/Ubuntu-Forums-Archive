---
title: "[SOLVED] Server: Can't get ventrilo-server to auto launch on boot!"
date: 2008-11-25
forum: Server Platforms
---

### Post by maledikt on 2008-11-25
Hi

I'm currently setting up my own ubuntu-server. I've successfully set up apache and php to start when the computer boots, but I can't get the ventrilo server to start unless I start in manually.

I've googled and googled and googled some more but I just can't find it anywhere, so I come here and plead for your help, great masters of linux. :(

---

### Post by prshah on 2008-11-25
> **maledikt said:**
> but I can't get the ventrilo server to start unless I start in manually.

See [[SOLVED] starting up a ventrilo server]("http://ubuntuforums.org/showthread.php?t=831035&highlight=ventrilo") Be warned, you will have to go through the entire thread right up to the end for it to make sense.

Post back here if you have troubles, with details of the problem you're facing.

---

### Post by maledikt on 2008-11-26
> **prshah said:**
> See [[SOLVED] starting up a ventrilo server]("http://ubuntuforums.org/showthread.php?t=831035&highlight=ventrilo") Be warned, you will have to go through the entire thread right up to the end for it to make sense.

Post back here if you have troubles, with details of the problem you're facing.

Thanks a bunch for the reply, after some tinkering I finally got it to work by modifying rc.local and making a script inside /init.d/

I will mark the thread as solved and I'll be sure to search even more next time, before asking a question.

---

