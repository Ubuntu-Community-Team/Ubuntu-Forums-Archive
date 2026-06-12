---
title: "Distraction free distro - no drivers for internet"
date: 2017-04-15
forum: Ubuntu, Linux and OS Chat
---

### Post by RabbitWho on 2017-04-15
Does this exist? 

It might be a fun project for someone?

It would have the libre office suit, for everyone, and bibisco, for writers. It would have any other programs that people who frequently need to avoid distraction might need. It would, of course, allow you to run a live disk, and ideally dual boot. You could mount partitions on your hard drive and save work there, or load previously saved work, but it would not allow you to access the internet and of course it would have no browsers or chat programs etc. 

People are buying laptops and physically breaking their internet capabilities, and even spending 500 dollars + on "e-ink typewriters" just so they can avoid temptation. Is there a distro that will do this for me? 

In the meantime I will just use puppy I guess, since it won't work with my wifi. But of course I can't install any programs I need on that 'cause no internet.  Any other ideas?

---

### Post by wildmanne39 on 2017-04-15
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by Tadaen_Sylvermane on 2017-04-15
Arch, build to fit what you want. Can do same with Ubuntu if you start with the minimal or server installer.

---

### Post by Bucky Ball on 2017-04-15
As above. [Install the minimal ISO]("https://help.ubuntu.com/community/Installation/MinimalCD"), add the apps you want/need. Switch off or disable networking. :)

Don't use the server version. That just adds stuff you won't need and will never use in your situation, and that is what you are trying to avoid.

---

### Post by RabbitWho on 2017-04-16
Switching off networking doesn't work I'm afraid, I just switch it on again. it needs to be difficult or almost impossible to connect to the internet. I'm an ordinary user and member of the public, and not a programmer. I have a full time job and I study part time. I do not have time to learn how to Arch I'm afraid. 

I am so confused about where to put this, it's been moved to a chat forum, but I think it's support.  I put it in a support forum and I got the message below. So what I thought was a support forum was a chat forum? So is my message chat or support? How do I move it back into the support forum like the bold writing is telling me. I feel like I am being told off for putting it in a chat forum but I actually put it in a support forum.. 

**Hello RabbitWho, this sub-forum is for chat, not support &#8211; hence the name.[B] If you need technical help, please post in an appropriate support sub-forum. **
[/B]

---

### Post by wildmanne39 on 2017-04-16
Then blacklist the driver.
```
echo "blacklist [COLOR="#FF0000"]drivername[/COLOR]" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by RabbitWho on 2017-04-19
This is useful! Thank you! :)

I can't mark as solved for some reason.. maybe because this was moved into a chat forum?

---

### Post by wildmanne39 on 2017-04-19
> **RabbitWho said:**
> This is useful! Thank you! :)

I can't mark as solved for some reason.. maybe because this was moved into a chat forum?
That is exactly why!
Glad you got what you needed.

---

