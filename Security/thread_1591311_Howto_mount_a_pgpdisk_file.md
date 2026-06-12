---
title: "Howto mount a pgpdisk file"
date: 2010-10-09
forum: Security
---

### Post by nab on 2010-10-09
Hi all,

at work we have to encrypt all data that goes on an USB-Stick or Notebook with pgpdisk. 

Having migrated completely to linux at home I look for a way to mount these files to work with the data. 

I did my google search ... but no luck there.

TIA!

---

### Post by P4man on 2010-10-09
doesnt look like there is any linux support for it, and without published specs (which I also cant find), its not likely it will come. Have you tried running pgpdisk under wine? Would your employer be okay if you used an alternative like [http://www.freeotfe.org/](http://www.freeotfe.org/) ?

If neither of those work, then you may need something ugly like installing XP in a VM and use that to read the sticks and feed it back over a shared folder.

---

### Post by nab on 2010-10-09
I'm working for a company with rather strict IT rules, so I can't install anything on my PC and IT-policies for switching software are ...

In the end I have to use pgpdisk 8.1.0 on my work PC.

With Google I couldn't find anything to suggest that pgpdisk will work with wine.

And going back to windows ... well, that would be a last resort, but not a happy one :-)

---

### Post by P4man on 2010-10-09
Im not suggesting you go back to windows, merely that you install it in a virtual machine that you use specifically for this purpose. You could probably make it transparent by sharing the USB stick in the (virtual) windows so it appears in ubuntu, decrypted. 

Id try wine first though.

---

### Post by nab on 2010-10-09
I'm using a Acer 1810tz with ubuntu 10.04. 

Well, a VM on a netbook? ... I don't know ... as things are ubuntu is already not really fast, but that is for my normal uses no problem.

And wine ... up to now I avoided that mainly because I don't see a point in buying Windows programs and then loosing support because I don't use Windows. And dualboot ... well, then I have to keep Windows up to date and this hassle was the main reason to leave behind windows ... But that's just me.

But back to my subject:

At the moment I'm looking into "FreeOTFE Explorer". If it works really without admin rights and I get the linux-side running, I'll give it a try as a portable app.

The Linux Examples [http://www.freeotfe.org/docs/Main/Linux_examples__LUKS.htm]("http://www.freeotfe.org/docs/Main/Linux_examples__LUKS.htm") are still with cryptoloop, so I have to "translate" them to cryptsetup.

Thanks for this suggestion.

---

### Post by P4man on 2010-10-09
You might be surprised how the VM performs. Remember,a VM is not emulation, its running the guest OS natively. It does cost memory, but it seems your netbook is a pretty well equipped one (looks like 3 GB typical?). 

You can host a  XP VM with 256Mb, no sweat. There are even minimalistic XP respins that require only 64Mb or so. CPU load is neglectable if the VM guest OS isnt running anything CPU heavy, and even boot times are almost nonexistant since you can save the guest VM state (like hibernating it).

Now, freeotfe would be better if you get it working and you're allowed to use it, no question. Just dont discount the VM option. Its quite useful for the odd windows only app as well.

---

