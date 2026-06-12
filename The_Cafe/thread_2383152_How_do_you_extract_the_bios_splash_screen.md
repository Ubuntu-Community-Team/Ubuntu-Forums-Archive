---
title: "How do you extract the bios splash screen?"
date: 2018-01-21
forum: The Cafe
---

### Post by michael337 on 2018-01-21
Just to see what the definite resolution is of the bios splash screen, I thought that I would like to see it, saved in a modern format, so that you can use it for animation. is there a way of doing this?

---

### Post by DuckHook on 2018-01-22
On bare metal the only way to do this is taking a picture of it with a camera. Obviously, you have no software tools available until the OS boots up, by which time, the BIOS screen is long gone.

If running a VM, you can use whatever keystroke gets into the guest VM's BIOS, then take a screen shot from your host. However, VM BIOSes are pretty primitive and I'm not sure that's what you are looking for. In fact, the only one I'm aware that has anything at all is VirtualBox, and it is just a screen allowing you to choose boot media.

---

### Post by galacticstone on 2018-01-22
Low-tech answer - set up your digital camera on a mini-tripod in front of the screen. Shoot a movie of the BIOS boot sequence. Like Duckhook said, no other options are really available for this.

---

### Post by michael337 on 2018-01-22
Well, that's the obvious answer, but there are many more interesting solutions, like going through the data from the update utility, and finding it. I mean, basically isolating the data from one another. I'm sorry that I'm going for the complex solution, it's just how I am when it comes to retrieving data like this.

---

### Post by DuckHook on 2018-01-22
We appear to be posting at cross purposes. You asked about the ***BIOS*** splash screen. You are quite mistaken if you think the OS has *any* record of this stage of the boot process. It is simply impossible for it to do so.

I suspect you may be thinking of the ***login*** splash screen. This is a very different animal from the BIOS splash screen and can be recorded using the VM method I previously mentioned.

I have no idea what you are referring to with "update utility". If you are referring to apt or dpkg, then it doesn't have any data about the boot or login process either.

---

### Post by michael337 on 2018-01-23
> **DuckHook said:**
> We appear to be posting at cross purposes. You asked about the ***BIOS*** splash screen. You are quite mistaken if you think the OS has *any* record of this stage of the boot process. It is simply impossible for it to do so.

I suspect you may be thinking of the ***login*** splash screen. This is a very different animal from the BIOS splash screen and can be recorded using the VM method I previously mentioned.

I have no idea what you are referring to with "update utility". If you are referring to apt or dpkg, then it doesn't have any data about the boot or login process either.

I do, because I have my bios in a 8.4 MB file in bin format, and the utility I'm referring to is here: [https://pcsupport.lenovo.com/mo/en/downloads/migr-74268](https://pcsupport.lenovo.com/mo/en/downloads/migr-74268)
Here is the Bios: [https://www.dropbox.com/s/blp1usyyr3dlgdu/T410.BIN?dl=0](https://www.dropbox.com/s/blp1usyyr3dlgdu/T410.BIN?dl=0)

---

### Post by deadflowr on 2018-01-23
I would think it be easier to ask Lenovo for the image rather than try to extract it from the bios image/binary/rom.

---

### Post by michael337 on 2018-01-23
> **deadflowr said:**
> I would think it be easier to ask Lenovo for the image rather than try to extract it from the bios image/binary/rom.
That seems reasonable, but how can I appropriately ask them? There isn’t a page to ask, only technical support. But that still doesn’t fit the case...
That’s the problem with that solution.

---

### Post by michael337 on 2018-01-29
bump

---

### Post by speedwell68 on 2018-01-30
If you have HDMI out you could try an HDMI capture box.

---

### Post by QIII on 2018-01-30
I think that what is implied by what you are asking is whether a proprietary binary, if you can identify it, could be teased apart by some means in such a manner as to yield a useful file?

---

### Post by michael337 on 2018-01-30
> **speedwell68 said:**
> If you have HDMI out you could try an HDMI capture box.

I don't, but I have the next best thing: displayport!
and I have RGB

---

### Post by michael337 on 2018-01-30
> **QIII said:**
> I think that what is implied by what you are asking is whether a proprietary binary, if you can identify it, could be teased apart by some means in such a manner as to yield a useful file?
Yes, because I've seen similar processes that extract assets from a proprietary file being done before, extracting assets from exe's, extracting gamecube instruments, nes sprites etc. I mean, if all of these tools exist, I expect that it's not really that difficult to extract the image from the bios, the only thing is that I don't know what that tool/editor is.

---

### Post by QIII on 2018-01-30
If that's a proprietary binary, attempting to decompile or reverse engineer it would be a violation of the owner's intellectual property rights.

The best we can suggest is that you contact the vendor.

Closed.

---

