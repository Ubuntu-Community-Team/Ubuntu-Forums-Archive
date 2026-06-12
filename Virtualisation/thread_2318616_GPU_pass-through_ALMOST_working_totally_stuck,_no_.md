---
title: "GPU pass-through ALMOST working totally stuck, no video output"
date: 2016-03-27
forum: Virtualisation
---

### Post by rkuykendall on 2016-03-27
I mostly used [this video]("https://www.youtube.com/watch?v=w-hOr44oBAI"), which references the [Purget Systems Guide]("https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/") heavily. I verified my hardware supports it before buying by researching online and even using the `cpu-checker` tool in apt-get. Everything actually went really well, and by the evening the script was running and booting the VM. The VM is booting correctly when I remove the `-vga none` flag, but with that flag, the machine boots but I get no output from the graphics card. The graphics card is verified working. It's also verified claimed by pci-stub. I'm very willing to work, just been dead-stuck for a day now with no progress, and would love for any direction.

**All my specs:**
EVGA GeForce GTX 980 Ti DirectX 12 06G-P4-0998-KR 6GB 384-Bit GDDR5 PCI Express 3.0 x16 SLI Support Video Card
GIGABYTE GA-Z170X-UD5 (rev. 1.0) LGA 1151 Intel Z170 HDMI SATA 6Gb/s USB 3.1 USB 3.0 ATX Intel Motherboard
Intel Core i7-6700K 8M Skylake Quad-Core 4.0 GHz LGA 1151 91W BX80662I76700K Desktop Processor Intel® HD Graphics 530

[B]All my files and outputs:
[/B][dmesg | grep pci-stub]("https://github.com/rkuykendall/gpu-passthrough-ubuntu-15-10/blob/master/dmesg_grep_pci-stub") output
[/etc/default/grub]("https://github.com/rkuykendall/gpu-passthrough-ubuntu-15-10/blob/master/etc_default_grub") file
[/etc/initramfs-tools/modules]("https://github.com/rkuykendall/gpu-passthrough-ubuntu-15-10/blob/master/etc_initramfs-tools_modules") file
[/etc/modules]("https://github.com/rkuykendall/gpu-passthrough-ubuntu-15-10/blob/master/etc_modules") file
[/etc/vfio_pci1.cfg]("https://github.com/rkuykendall/gpu-passthrough-ubuntu-15-10/blob/master/etc_vfio_pci1_cfg") file
[lspci -nn | grep NVIDIA]("https://github.com/rkuykendall/gpu-passthrough-ubuntu-15-10/blob/master/lspci_nn_grep_nvidia") output
[/usr/vm]("https://github.com/rkuykendall/gpu-passthrough-ubuntu-15-10/blob/master/usr_vm") script

Looking for any direction or help I can find.

---

### Post by KillerKelvUK on 2016-03-28
Hey, your setup reads okay to me although you're stubbing in multiple locations which isn't needed.  From your grub line it looks like you're attempting an i915 arb patch, is that the case?  Have you considered/researched OVMF as an alternative to legacy seabios and thus avoiding VGA Arbitration?

Little more reading for you... [http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-1-hardware.html](http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-1-hardware.html), the blog is by Alex Williamson who is one of the main devs working on KVM/QEMU and VGA Passthrough...the link I've sent is to a 5 part article on how to do this the proper way, your link was a little dated.

If you going to try OVMF make sure you get the latest release from here [https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download](https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download), its a simple change to your config, you effectively just change the -bios line in your qemu commandline.

---

### Post by MAFoElffen on 2016-03-28
I sort of modestly have some Linux Graphics Layer experience (see the sticky in my sigline) ...Just a few questions and a thought. (I run SLI with 2 of those cards, but do not like  doing passthrough.)

When you say no video, just what do mean? (clarification) No X or no output at all? Meaning do you not get any text output either? (BIOS messages and/or cannot boot to a text console...)

If no text output, then a deeper problem on it... Addressing that the graphics GPU is not getting addressed. Not addressed... but you said it was getting addressed right? Just how was that confirmed?

If no X, then use a "nomodeset" kernel boot tag for the VM. Being a GTX 980ti... it is too new GPU for the openSourced Neaveau to support, so you haveto use the "nomodeset" kernel boot option to turn off KMS until you get the proprietary NVidia driver for that card installed.

---

### Post by rkuykendall on 2016-03-28
> **KillerKelvUK said:**
> Hey, your setup reads okay to me although you're stubbing in multiple locations which isn't needed.
Desperation set in.
> **KillerKelvUK said:**
> From your grub line it looks like you're attempting an i915 arb patch, is that the case?  Have you considered/researched OVMF as an alternative to legacy seabios and thus avoiding VGA Arbitration?
**First question:** I don't know. I will have to look into my setup to see if I can answer that.
**Second question:** I've seen OVMF around and it does seem to work for people, but it seems like a VERY different way of doing things, so I'd have to remove all these changes and find a new guide to follow from scratch. Something I can try if I can't get this working or if you highly recommend it. Or maybe I'm mistaken? It seems I'll know more when I read the links below.
> **KillerKelvUK said:**
> Little more reading for you... [http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-1-hardware.html](http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-1-hardware.html), the blog is by Alex Williamson who is one of the main devs working on KVM/QEMU and VGA Passthrough...the link I've sent is to a 5 part article on how to do this the proper way, your link was a little dated.
If you going to try OVMF make sure you get the latest release from here [https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download](https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download), its a simple change to your config, you effectively just change the -bios line in your qemu commandline.
These are fantastic, thank you! I will read them both throughly as soon as I can.

---

### Post by rkuykendall on 2016-03-28
> **MAFoElffen said:**
> I sort of modestly have some Linux Graphics Layer experience (see the sticky in my sigline) ...Just a few questions and a thought. (I run SLI with 2 of those cards, but do not like doing passthrough.)
When you say no video, just what do mean? (clarification) No X or no output at all? Meaning do you not get any text output either? (BIOS messages and/or cannot boot to a text console...)
I mean that the HDMI plugged into the graphics card never sends a signal of any kind.
> **MAFoElffen said:**
> If no text output, then a deeper problem on it... Addressing that the graphics GPU is not getting addressed. Not addressed... but you said it was getting addressed right? Just how was that confirmed?
I confirmed that it was getting 'stub''d, and that my `vm` script did not throw any erros during the parts that involve the GPU. That is all I know, and I do think this issue has to directly with the GPU somehow.
> **MAFoElffen said:**
> If no X, then use a "nomodeset" kernel boot tag for the VM. Being a GTX 980ti... it is too new GPU for the openSourced Neaveau to support, so you have to use the "nomodeset" kernel boot option to turn off KMS until you get the proprietary NVidia driver for that card installed.
Hm, this could explain things, could it be the Windows 7 installer just doesn't support outputting from this card whatsoever? Maybe I could install in windowed mode, then add the card, after the install is finished? If I'm understanding this correctly.

---

### Post by MAFoElffen on 2016-03-28
Windows 7 installer? LOL ... I forgot you were running a Windows guest. Windows works fine with that card. (it does natively on mine.) I have mine, with the SLI paired 980it's running on a dual-boot (Ubuntu/Windows). On my Windows-side, I since a gamer, I just use NVidia's "Geforce Experience" and keep their game-ready latest's up on it. I tweak the graphics, from it's recommended game accelerations... Or, at least I used to. (Now I use (Razer's because it also ties into my keyboards and macro-keypads.) On the Linux-side, I use the Edgers PPA. 


What is the hypervisor KVM, right? Running on what version of Ubuntu?


What is the OS and version of the machine you are trying to run the guest OS on? With what as the guest connection? (VNC, Spice, RDP?)


Yes, not getting any input noticed by the HDMI flat screen is a sign that it is not getting addressed at all. (not powering up at all.)

---

### Post by rkuykendall on 2016-03-29
> **MAFoElffen said:**
> Windows 7 installer? LOL ... I forgot you were running a Windows guest. Windows works fine with that card. (it does natively on mine.) I have mine, with the SLI paired 980it's running on a dual-boot (Ubuntu/Windows). On my Windows-side, I since a gamer, I just use NVidia's "Geforce Experience" and keep their game-ready latest's up on it. I tweak the graphics, from it's recommended game accelerations... Or, at least I used to. (Now I use (Razer's because it also ties into my keyboards and macro-keypads.) On the Linux-side, I use the Edgers PPA.

What is the hypervisor KVM, right? Running on what version of Ubuntu?
Latest 15.10 Ubuntu. I'm calling `[COLOR=#333333][FONT=Consolas]qemu-system-x86_64 -enable-kvm[/FONT][/COLOR]` in my vm script so I guess my hypervisor is KVM but I'm not sure.
> **MAFoElffen said:**
> What is the OS and version of the machine you are trying to run the guest OS on? With what as the guest connection? (VNC, Spice, RDP?)
I have a Win7 installer ISO I made that boots successfully when not trying to use the graphics card ( when I remove the -vga none flag from my script ) None of those guest technologies have come up during my install, so I'm not sure if I'm using any of them. I know what VNC is though, so I'm guessing you mean how I'm trying to see output. I'm trying to get the guest to output over HDMI from the graphics card to a second monitor.
> **MAFoElffen said:**
> Yes, not getting any input noticed by the HDMI flat screen is a sign that it is not getting addressed at all. (not powering up at all.)
Interestingly the card is always receiving power (leds on), even before booting the VM. Just never outputting anything. It also shows up in "Restricted Drivers" despite blacklisting and uninstalling all drivers and pci-stubing the card. Is that a sign something is configured wrong? I did get it to output when I was making sure it worked, before I stubbed it.

---

### Post by MAFoElffen on 2016-03-30
Lights are not an indication of being accessed or not. That just means that it is physically getting power to the card through the PCIe bus and the external Molex connections.

Just analyzing any differences in the start scripts...

Snippet from PSS'es script that they say works on theirs:
```

# Snippet Start
sudo qemu-system-x86_64 -enable-kvm -M q35 -m 4096 -cpu host \
-smp 4,sockets=1,cores=4,threads=1 \
-bios /usr/share/qemu/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=02:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=02:00.1,bus=root.1,addr=00.1 \
-drive file=/home/puget/windows#.img,id=disk,format=raw -device ide-hd,bus=ide.0,drive=disk \
-drive file=/home/puget/Downloads/Windows.iso,id=isocd -device ide-cd,bus=ide.1,drive=isocd \
-boot menu=on
# Snippet End

```
In your script:
```

# Snippet Start
sudo qemu-system-x86_64 -enable-kvm -M q35 -m 8192 -cpu host,[COLOR=#ff0000]kvm=off[/COLOR] \
-smp [COLOR=#ff0000]2[/COLOR],sockets=1,cores=[COLOR=#ff0000]2[/COLOR],threads=1 \
-bios /usr/share/seabios/bios.bin [COLOR=#ff0000]\[/COLOR]
-vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=01:00.1,bus=root.1,addr=00.1 [COLOR=#ff0000]\[/COLOR]-device virtio-scsi-pci,id=scsi \
-drive file=/home/rkuykendall/Virtual/windows.img,id=disk,format=raw,if=none -device scsi-hd,drive=disk \
-drive file=/home/rkuykendall/Downloads/win7install.iso,id=isocd,if=none,format=raw -device scsi-cd,drive=isocd \
-boot menu=on
# Snippet End

```
Highlighted above are differences. Below are suggested edits...
```

# Snippet Start
sudo qemu-system-x86_64 -enable-kvm -M q35 -m 8192 -cpu host \
-smp 2,sockets=1,cores=2,threads=1 \
-bios /usr/share/seabios/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=01:00.1,bus=root.1,addr=00.1 \
-device virtio-scsi-pci,id=scsi \
-drive file=/home/rkuykendall/Virtual/windows.img,id=disk,format=raw,if=none -device scsi-hd,drive=disk \
-drive file=/home/rkuykendall/Downloads/win7install.iso,id=isocd,if=none,format=raw -device scsi-cd,drive=isocd \
-boot menu=on
# Snippet End

```
kvm=off is used for NVIDIA cards to stop it detecting a hypervisor and therefore exiting with an error... but PSS script does not have that, try it without that first. If it gets an error, then throw it back in. Others are just minor formatting differences.

---

### Post by rkuykendall on 2016-03-30
> **MAFoElffen said:**
> Lights are not an indication of being accessed or not. That just means that it is physically getting power to the card through the PCIe bus and the external Molex connections.

This is what I suspected, but it's great to have it confirmed. What about showing up in the restricted drivers window? Even with successful stubbing confirmed and all my blacklists, restricted drivers still shows this: [http://i.stack.imgur.com/zD3GU.png](http://i.stack.imgur.com/zD3GU.png) ( sorry window not focused )

Thank you so much for the config recommendations. Sadly, I tried them both with and without `,kvm=off` and still got no output from the HDMI.

This is a rough problem since there's no error message I can work with or anything. Just a single blank symptom of SOME problem. Everything on the Ubuntu side looks like the whole thing is working.

What do you think about switching to OVMF, using the guide linked from [this question]("http://ubuntuforums.org/showthread.php?t=2297514")? It's a very different setup, which would require me to ditch this approach, but KillerKelvUK's comment about it somehow avoiding VGA arbitration is very tempting.

---

### Post by MAFoElffen on 2016-03-31
You *could*. You could also pull your config's to confirm that the card does work(on ubuntu). Be a shame to find out that the card does not work and that you were chasing ghosts right? Just for a confirmation and a ease of mind.

---

### Post by rkuykendall on 2016-03-31
> **MAFoElffen said:**
> You *could*. You could also pull your config's to confirm that the card does work(on ubuntu). Be a shame to find out that the card does not work and that you were chasing ghosts right? Just for a confirmation and a ease of mind.

100% agree. I actually had some other DOA-scares building this machine, and the first thing I did was make sure Ubuntu could boot from the card.

I'm currently making very slow progress on the OVMF method, so I'm hopeful that things will go better there.

---

