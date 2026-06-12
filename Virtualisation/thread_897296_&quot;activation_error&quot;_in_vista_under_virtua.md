---
title: "&quot;activation error&quot; in vista under virtualbox"
date: 2008-08-22
forum: Virtualisation
---

### Post by varonbondumb on 2008-08-22
sorry if this is posted in the wrong forum

my problem:  I installed Vista on this computer using virtualbox and everything has gone well for a week or two, until now.  on attempting to boot up the vista installation, it gave me an "activation error", and after re-entering the valid vista code, it said "a problem occurred when windows tried to activate.  error code 0xC004F063." after clicking 'more information', it said "description:  the software licensing service reported that the BIOS is missing a required license."

the best possible match for a solution came at
[http://forums.virtualbox.org/viewtopic.php?t=3224&postdays=0&postorder=asc&start=0&sid=3d7fd1fdde9cfb98ca56a303825ceb4f](http://forums.virtualbox.org/viewtopic.php?t=3224&postdays=0&postorder=asc&start=0&sid=3d7fd1fdde9cfb98ca56a303825ceb4f)

I have the vista installation disc, have installed vista to its own partition for dual booting purposes with no problem.  all i need to do is use internet explorer (yes, tried ies4linux / wine which wont properly run what I need to run) and I don't want to have to dual boot into windows to do one simple task.  

the link above might be the solution I am looking for, but past running the "sudo dmidecode -t 1", I feel like a monkey looking at a math problem.  

any ideas?

---

### Post by varonbondumb on 2008-08-29
/bump

---

### Post by frup on 2008-08-29
Did you upgrade virtualbox? My brother has vista in virtualbox and it did the same when he upgraded it, luckily he had made a snapshot on install with my advice. Snapshots are a really good idea when using virtual machines.

---

### Post by swoll1980 on 2008-08-29
If you had already installed it on the computer and registered it, it logged your hardware with MS. Now you go into vbox install it, it uses the vbox hardware configuration, but the same serial#  which is a red flag to MS. MS thinks your trying to install the same license on several computers

---

### Post by varonbondumb on 2008-09-03
I never did make any snapshots as I never thought to use them.  I understand them to be 'system restore points'

is there any (easy) way to be able to let virtualbox tell windows that its using the proper motherboard (in this case, the same motherboard it is registered to), or something similar?

---

### Post by 01d5k001 on 2008-10-19
well, i dont use virtual box, i have a drive partitioning, and had installed ubuntu after vista so... sorry, i have a similar problem as well... [http://ubuntuforums.org/showthread.php?t=952265](http://ubuntuforums.org/showthread.php?t=952265)

---

### Post by DGortze380 on 2008-10-19
> **varonbondumb said:**
> I never did make any snapshots as I never thought to use them.  I understand them to be 'system restore points'

is there any (easy) way to be able to let virtualbox tell windows that its using the proper motherboard (in this case, the same motherboard it is registered to), or something similar?

Call and beg for a new key until they give you the inevitable 'Go buy a new copy. What you're trying to do violates the license' speech.

Honestly though, it sucks, but that's the way they are with the licenses. You could try to reinstall, it should then give you two more weeks to register during which time you can attempt to take a snapshot, and just continually revert to it.

Disclaimer: I have no idea as to the legality or EULA implications of doing that.

---

### Post by Zzl1xndd on 2008-10-19
Not sure about this but I seem to remember MS saying that the Vista Homes are not allowed to be run in VM's. I'm not sure if there was an update to Vista or Virtualbox that allows them to enforce this but it might be part of the problem,

---

### Post by aman7731 on 2009-07-15
Using Virtualbox 2.1.4_OSE provides a simple resolution for this problem.
On a Dell desktop:
1. run 
```
sudo dmidecode -t0
```2. run 
```
sudo dmidecode -t1
```This provides the information you need to provide next.
3. run the following and replace "Vista" with the name of your virutal machine, and replace the values with those from your DMI:
```

VBoxManage setextradata "Vista" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSVendor" "Dell Inc"
VBoxManage setextradata "Vista" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSVersion" "1.1.4"
VBoxManage setextradata "Vista" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSReleaseDate" "12/09/2006"
VBoxManage setextradata "Vista" "VBoxInternal/Devices/pcbios/0/Config/DmiSystemVendor" "Dell Inc"
VBoxManage setextradata "Vista" "VBoxInternal/Devices/pcbios/0/Config/DmiSystemProduct" "Dimension E521"

```I'm not sure they are all necessary, but they get the job done. After you have changed these, restart your vista virtual machine and re-enter your activation code.

---

### Post by emwaiz on 2009-11-10
Hi everyone ... I've been using VirtualBox 3.0.8 OSE for my Vista guest. The same problem I'm facing now ... I couldn't activate my Vista product key.

1. Bios information
```
dmi decode -t0
```

Vendor: Acer   
	Version: v1.3401
	Release Date: 11/06/2007

2. System information
```
dmi decode -t1
```

	Manufacturer: Acer, inc.
	Product Name: TravelMate 6292 
	Version: Not Applicable

I've followed the instruction to enter them in the terminal

```
VBoxManage setextradata "Vistaem" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSVendor" "Acer"
VBoxManage setextradata "Vistaem" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSVersion" "v1.3401"
VBoxManage setextradata "Vistaem" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSReleaseDate" "11/06/2007"
VBoxManage setextradata "Vistaem" "VBoxInternal/Devices/pcbios/0/Config/DmiSystemVendor" "Acer, inc."
VBoxManage setextradata "Vistaem" "VBoxInternal/Devices/pcbios/0/Config/DmiSystemProduct" "TravelMate 6292"
```

Restarted my virtual machine, entered the original product serial key.
Then, activation error. Really in mess now. Really need my Vista to run in my Ubuntu 9.10. TQ in advance!

---

