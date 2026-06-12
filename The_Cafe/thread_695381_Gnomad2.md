---
title: "Gnomad2"
date: 2008-02-13
forum: The Cafe
---

### Post by rabid9797 on 2008-02-13
i'm sure its been posted about before, but for anyone who isn't satisfied with the repository version(only 2.8.12), i have built the latest version from source(2.9.1) and created a deb.

Included in the .rar is the Gnomad deb, and the dependencies needed to use it. 

__________________________

Why would you need this you ask?

You probably don't actually, but the newer version provides better(And faster) support for MTP devices.

Please don't ask me about how to fix things if they don't work, im just a simple user offering back what i think would be a helpful package to the community..

Hope everything works for you guys though!

---

### Post by imopen on 2008-06-19
> **rabid9797 said:**
> i'm sure its been posted about before, but for anyone who isn't satisfied with the repository version(only 2.8.12), i have built the latest version from source(2.9.1) and created a deb.

Included in the .rar is the Gnomad deb, and the dependencies needed to use it. 

__________________________

Why would you need this you ask?

You probably don't actually, but the newer version provides better(And faster) support for MTP devices.

Please don't ask me about how to fix things if they don't work, im just a simple user offering back what i think would be a helpful package to the community..

Hope everything works for you guys though!

thanks, I'll give a try ;)

---

### Post by geoken on 2008-06-19
Can Gnomad take an m3u file and transfer the associated music/create playlist on the player? If not I think I'll stick with Amorok which seems to support my creative Zen better than Gnomad.

---

### Post by sryk on 2008-06-19
must try it

---

### Post by TusharG on 2008-07-08
Hey thanks a lot! With little twicking it worked! Ubuntu 8.04 is shipped with most of the libraries you have packed. But libmtp version 7 is installed on Ubuntu 8.04 while the GNomad2 requires libmtp version 6. So I created a link like this libmtp.so.6 -> libmtp.so.7  and it just works!

---

### Post by MangasColoradas on 2008-07-12
How do you create that link please?

Also I can use the Gnomad in synaptic but not the new one....I didn't read the 'readme' and installed the deb before the dependencies...does that matter?

---

### Post by Martje_001 on 2008-08-09
Create the link by doing:
```
sudo ln -s /usr/lib/libmtp.so.7.1.0 /usr/lib/libmtp.so.6
```

Sorry for the topickick

---

