---
title: "Deploying Images over Lan"
date: 2011-01-19
forum: Server Platforms
---

### Post by motermouth15 on 2011-01-19
I'm setting up Ubuntu Server for the first time and was wondering if there is a way to deploy iso files over lan with it. My goal would be to be able to re-image computers with iso files over the network. If someone could give me a link to a step by step process or help me out on this thead that would be great!

Thank You!
-Nate

---

### Post by arrrghhh on 2011-01-19
Certainly!  There's a couple of great pages for you to read.

[PxE Install Server](https://help.ubuntu.com/community/PXEInstallServer) and [Netboot installation](https://help.ubuntu.com/community/Installation/Netboot) - hopefully those will get you going!

---

### Post by arrrghhh on 2011-01-19
Damnit... sorry for the doublepost again.

---

### Post by koenn on 2011-01-19
> **arrrghhh said:**
> Certainly!  There's a couple of great pages for you to read.

[PxE Install Server](https://help.ubuntu.com/community/PXEInstallServer) and [Netboot installation](https://help.ubuntu.com/community/Installation/Netboot) - hopefully those will get you going!

err, not really. The pages you link to are about automatic, PXE triggered install. That works well to repeat the same install process multiple times, but what the OP is looking for is a way to redeploy an image of an already set up and configured system. Slightly different approach.

Cloezilla Server seems to be capable of handling stuff like that.
[http://clonezilla.org/clonezilla-SE.php](http://clonezilla.org/clonezilla-SE.php)

---

### Post by arrrghhh on 2011-01-19
Ah yes, re-reading the OP's post it seems CloneZilla would be a better fit... thanks!

---

### Post by arrrghhh on 2011-01-19
Wow, another dupe.  Sorry again... not sure if it's my network or the forums, but I seem to be doing this a lot lately!

---

### Post by arrrghhh on 2011-01-19
Dupe...

---

### Post by arrrghhh on 2011-01-19
Dupe...

---

### Post by arrrghhh on 2011-01-19
Dupe...

---

### Post by arrrghhh on 2011-01-19
Sorry for the dupes... I wish I could delete posts!

---

### Post by motermouth15 on 2011-01-19
> **koenn said:**
> err, not really. The pages you link to are about automatic, PXE triggered install. That works well to repeat the same install process multiple times, but what the OP is looking for is a way to redeploy an image of an already set up and configured system. Slightly different approach.

Cloezilla Server seems to be capable of handling stuff like that.
[http://clonezilla.org/clonezilla-SE.php](http://clonezilla.org/clonezilla-SE.php)

On their page it says its used to clone a computer through USB flash drive or cd/dvd rom. Does it work over LAN?

---

### Post by arrrghhh on 2011-01-19
> **motermouth15 said:**
> On their page it says its used to clone a computer through USB flash drive or cd/dvd rom. Does it work over LAN?

Yup, you can even use mutlicast and drop images to (I believe) up to 40 computers at the same time - assuming your network can keep up ;).

---

### Post by arrrghhh on 2011-01-19
Oy, it must be my work's proxy.  Sorry for all the dupes, I'm only hitting the button once... Grrrrr

---

### Post by koenn on 2011-01-19
you sure you're looking at that same page I linked to ?
I see no mention of USB there, but rather
> 
# Make sure the clients will boot from the network (PXE or etherboot) then turn on the clients to let them boot from network.
# The clients will begin to clone the system image to their harddisks. 


---

