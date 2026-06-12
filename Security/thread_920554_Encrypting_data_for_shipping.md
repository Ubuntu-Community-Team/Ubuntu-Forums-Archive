---
title: "Encrypting data for shipping"
date: 2008-09-15
forum: Security
---

### Post by StooJ on 2008-09-15
I am moving from the UK to Australia in a few months and I will need to ship some data out there with me. Some of the data is sensitive and I don't really want anyone looking through it if I can possibly help it.

I've bought a couple of external HDDs that I am hoping to back up my data onto, then pack them up and send them down under.

I would love some recommendations for encrypting the HDDs. I have looked at Truecrypt but have come across enigmatic comments about poor security in the past: I must have missed that.

I've also had a brief look at LUKS, but will do some more research on that today.

Any advice or pointers you could give me would be vastly appreciated.

---

### Post by pietjanjaap on 2008-09-15
True crypt, and a very long password.

---

### Post by pqrs541 on 2008-09-16
The Weather:[buy wow gold](http://www.mmoinn.com)  It's so dry, the trees are bribing the dogs. It's been hitter?s a goat's butt in a pepper patch.  Wintry roads are said to be "slicker than otter snot. [wow gold](http://wowus.mmoinn.com/index.do?PageModule=OrderForm_new)[wow gold](http://woweu.mmoinn.com/index.do?PageModule=OrderForm_new) [World of warcraft Gold](http://www.mmoinn.com)[wow gold](http://www.mmoinn.com)

---

### Post by StooJ on 2008-09-17
As simple as that? Is truecrypt more secure than LUKS? It seems to be designed around a well-documented standard which is always a good thing.

---

### Post by kosmiciatakuja on 2008-09-17
As far as I could check LUKS is also a well documented standard, and open source (I'm not saying truecrypt is not open source, I just don't know about them). I'm using dm-crypt, which is a partition encryption system built into the mainline kernel, which I believe is a good sign of stability and general trust in the system.  And it is compliant with LUKS (meaning you can use the LUKS commands). 

So, I chose dm-crypt because it is in the kernel, which I trust. To work with that you just have to install the userland interface named cryptsetup so you can instruct kernel to create and encrypt the partition. 

I second the advice about good password. You can pick the strongest encryption algorithm and the best software, if you have a short weak password then it can be broken by a few minute dictionary attack. Better yet, if you can, pick a pass-phrase instead of a pass-word. 

You can easily google up a dozen tutorials on dm-crypt and cryptsetup, although many of them tell you how to encrypt the root partition, which is a task somewhat more complicated than what you're trying to do. If you have trouble with the tutorials you find, and the task is confusing, please respond here in this thread and I'll tell you what to do, it should be 2-3 commands to create and mount the encrypted partition. I have done it before but a long time ago so I don't remember now, I'd have to dig a bit :)
Just let me know!

cheers

---

### Post by Penetration Testing on 2008-09-17
Luks can be accessed from Window via FreeOTFE but Truecrypt is generally easier to use for most people.

For most of your data either should be fine. It might be an idea to use something like Amazon S3 and duplicity or a similar net-based backup solution for anything you wouldn't want to be forced to hand over at immigration.

---

### Post by hyper_ch on 2008-09-18
both are open source and provide very strong encryption and have, this far, no known weakness.

---

### Post by StooJ on 2008-09-19
Great, thank you to all of you.

I gave away my original disk to a client, so I'm waiting for another to arrive next week sometime. I'll get started on it then & will post my progress.

---

