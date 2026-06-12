---
title: "Any way to get WINE to install?"
date: 2011-10-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jfernyhough on 2011-10-25
When trying to install WINE (either 1.2, 1.3 from repo or WINE PPA) it fails due to wanting ia32-libs-multiarch which in turn tries to remove a load of 64-bit packages.

Does anyone have a workaround?

---

### Post by kc1di on 2011-10-25
hi jfernyhough,

which version of ubuntu are you using?

I've had no trouble here installing wine on 64 bit machine.

---

### Post by jfernyhough on 2011-10-25
Ack, I haven't updated my sig since coming back to Ubuntu. It's 64-bit precise.

Just about to try in a VM.

--edit
Yup, same thing. Looks like a multiarch issue.

--edit 2
Tried with the sid packages from here: [http://dev.carbon-project.org/debian/wine-unstable/](http://dev.carbon-project.org/debian/wine-unstable/)
Definitely a multiarch thing.

---

### Post by Sworddragon on 2011-10-25
This behaviour in ia32-libs is wanted: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/879091](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/879091)

Just install ia32-libs from Oneiric and Wine will work again.

---

### Post by jfernyhough on 2011-10-25
Ah ha, thanks for that. :)

--edit
After a little bit of a dance installing various lib32* packages the oneiric ia32-libs installed, and that allowed me to apt-get install wine1.3. Nice.

---

### Post by jdholman on 2012-02-15
So how do I install ia32-libs from Oneiric anyway?  I have Precise Alpha 2.

Thanks,

Jim

---

### Post by dino99 on 2012-02-15
> **jdholman said:**
> So how do I install ia32-libs from Oneiric anyway?  I have Precise Alpha 2.

Thanks,

Jim

sudo apt-get install wine1.4

  - wine1.4-i386/wine1.4-amd64 will provide support for 32/64 bit windows apps

---

### Post by jdholman on 2012-02-15
Thanks dino99, but I can't install Wine1.4.

Here is my error:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4~rc2-0ubuntu1)
E: Unable to correct problems, you have held broken packages.

I wish it was that easy, but I have issues with ia32-libs and multiarch which prevent Wine from loading.

Jim

---

### Post by IPEX-731BA5DD06 on 2012-02-15
you have to change the ppa in software sources to Oneiric and not Precise.

Change both of these.

Access is Via 

1)Ubuntu software centre
2)Edit-Software Sources
3)Other software tab

Now you edit the wine line, remove Precise and replace with Oneiric (Careful of the spelling)

Run software update and wine will be updated.

P.S. I've just updated to 1.4 rc3 but still say's 1.4 rc2 in the about tab, though its removed the 'wine icon' from my desktop, leaving a generic sheet of paper.

*Edit* It must just have updated some other parts of wine, rc3 isn't available as yet, so correctly displaying rc2. I assumed it was updating all of wine, must have been a specific part. Just saw the wine 1.4 part.

---

