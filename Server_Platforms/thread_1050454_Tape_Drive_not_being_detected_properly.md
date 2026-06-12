---
title: "Tape Drive not being detected properly"
date: 2009-01-25
forum: Server Platforms
---

### Post by tomwerner470 on 2009-01-25
Hi,

I am having some issues getting a tape drive working properly. The drive was working perfectly when the system was running Ubuntu 6.06 (Drake?). I have done alot of trawling of various tips, most won't work. I hope someone outthere can help....

So far I have identified:

**cat /var/log/messages | grep -i "scsi"** (extract)

```
Jan 25 21:00:46 server4 kernel: [ 1232.529284] scsi 2:0:1:0: Sequential-Access Seagate  STT3401A         310C PQ: 0 ANSI: 2
Jan 25 21:00:46 server4 kernel: [ 1232.561682]  target2:0:1: FAST-40 SCSI 40.0 MB/s ST (25 ns, offset 127)

```

**sg_map**

```

/dev/sg0  /dev/sda
/dev/sg1         <--- Being blank I guess it isn't being assigned properly
/dev/sg2  /dev/sdb

```

Although the scsi driver appears to be picking it up in the probe, **it is not getting assigned an entry in /dev.**

I have read various tips talking about rmmod/modprobe ide-scsi, ide-tape and st but none of these modules were found - are they obselete or are they available in packages? I have installed the mt-st package from the repos.

I am using Hardy 8.04.2.

Any help would be appreciated,

Cheers,

Tom

---

### Post by redroad55 on 2009-01-25
Hi, Is the drive recognized in Bios ? 
    Are you using an scsi controller card or is it a chip built in the motherboard ?
    Are there any firmware updates appropriate for this Tape Drive 
Let's start there 1st

---

### Post by aaron.d on 2009-01-26
is there anything else on the controller, and if so, is it working? It is obviously recognized in the BIOS if the kernel can ID it, and that seems like a hella old tape drive, so firmware is what it is, most likely.
Wondering if you have the right modules.

show us the whole she-bang:

```
cat /proc/scsi/scsi
```

and 

```
sudo /sbin/lsmod
```

---

### Post by tomwerner470 on 2009-01-26
Hey Guys,

Here is the info requested:

```
cat /proc/scsi/scsi

Attached devices:
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: VMware,  Model: VMware Virtual S Rev: 1.0 
  Type:   Direct-Access                    ANSI  SCSI revision: 02
Host: scsi2 Channel: 00 Id: 01 Lun: 00
  Vendor: Seagate  Model: STT3401A         Rev: 310C
  Type:   Sequential-Access                ANSI  SCSI revision: 02
Host: scsi2 Channel: 00 Id: 02 Lun: 00
  Vendor: VMware,  Model: VMware Virtual S Rev: 1.0 
  Type:   Direct-Access                    ANSI  SCSI revision: 02

```

```
sudo /sbin/lsmod
Module                  Size  Used by
sg                     36752  0 
vmblock                16544  3 
vsock                  40344  0 
vmmemctl               10556  0 
vmhgfs                 44288  0 
parport_pc             28324  0 
parport                38472  1 parport_pc
ipv6                  266372  14 
evdev                  13056  0 
psmouse                19592  0 
serio_raw               7940  0 
pcspkr                  4224  0 
container               5632  0 
i2c_piix4               9612  0 
button                  9232  0 
intel_agp              25492  1 
agpgart                34760  1 intel_agp
ac                      6916  0 
i2c_core               24832  1 i2c_piix4
vmci                   32552  1 vsock
ext3                  135816  2 
jbd                    46740  1 ext3
mbcache                 9600  1 ext3
sd_mod                 30592  5 
floppy                 59460  0 
pcnet32                34820  0 
mii                     6400  1 pcnet32
mptspi                 19720  3 
mptscsih               27904  1 mptspi
mptbase                60644  2 mptspi,mptscsih
scsi_transport_spi     25472  1 mptspi
ata_piix               19588  0 
ata_generic             8324  0 
pata_acpi               8320  0 
libata                159216  3 ata_piix,ata_generic,pata_acpi
scsi_mod              150924  6 sg,sd_mod,mptspi,mptscsih,scsi_transport_spi,libata
thermal                16668  0 
processor              36488  1 thermal
fan                     5636  0 
fbcon                  42784  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
vmxnet                 19200  0 

```

Just a bit more about the setup, this is a Virtual Machine running under VMware using scsi passthrough, however, unless there is a convincing reason, I don't think this is the issue, my Ubuntu 6 VM with the same setup worked without an issue. Also this is an ide tape drive, but again, this drive worked perfectly through the ide-scsi module before...

The only thing I could think of is the drive was removed from the supported list because of it's age?

Cheers for the interest so far, hopefully someone can shed some light...

Regards

Tom

---

### Post by aaron.d on 2009-01-26
I have never worked on anything in this type of setup, but I think you are missing the tape driver module (st). Try finding and loading that.

---

### Post by tomwerner470 on 2009-01-26
Any ideas where I can get the st module from?

/lib/modules/2.6.24-23-virtual/kernel/drivers/scsi does not contain st.ko.

Google searches are finding nothing to say what package this is in or whether it has been superceeded.

---

### Post by tomwerner470 on 2009-01-26
After some investigation, it appears to be an issue with the -virtual kernel package that is installed as default by vm-builder. As part of the 'optimisation' process drivers are taken out, one of which is the tape module. 

I did try a straight copy from a -server module directory (sane kernel version) but to be honest I didnt have any luck loading it, I tried:

```
sudo depmod st  (there was a few seconds pause, no output)
sudo modprobe st   (error message)
```

Anyway for now, I have got it working by booting a -server kernel instead of the virtual, hopefully that won't have too much of an impact...

However, any ideas how I could make the copy? Or should I raise a bug as although rare, i doubt this is unheard off?

Cheers for the help,

Tom

---

### Post by aaron.d on 2009-01-27
Glad it works. As for the module, it should be available in one of the modules packages available for the kernel, or the source at the very least. The one you grabbed most likely failed for a number of reasons (they have to be compiled with the same gcc version, etc).

I don't know if I would consider it a bug, per se, to not have a specific module included, but I don't really think it is "optimized" when the module isn't loaded, it doesn't affect the kernel at all. Maybe they are trying to save space??

If the server kernel works, I would say rock that, I have never used "VM" specific kernels though, so I can't say what you might be missing.

---

### Post by tomwerner470 on 2009-01-27
Yeah, I don't know the exact details of the kernel tuning that takes place for the virtual packages, although I am sure they have played with the HZ setting to try and avoid issues of a guest ticking faster than a host...

Apart from that, they stripped alot of the unneeded drivers as mentioned above.

Anyways, thanks for the help with this...

Tom

---

### Post by redroad55 on 2009-01-29
I'm wondering on this if the driver is being removed as part of the optimization process then it perceives it as not being needed .. Am I right in thinking that?

---

