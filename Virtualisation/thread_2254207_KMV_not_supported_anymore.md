---
title: "KMV not supported anymore?"
date: 2014-11-25
forum: Virtualisation
---

### Post by joo_marques2 on 2014-11-25
Hello community! I've been developing some code to android using adt bundle (eclipse + sdk manager) and everything was fine and the emulator was running with no trouble. until a few days ago, when I was messing around with facebook sdk, my eclipse and my android emulator started acting weird and so I decided to reinstall them.

Now, when I start a new android device it gives me the error below:

Starting emulator for AVD 'android'
emulator: ERROR: x86 emulation currently requires hardware acceleration!
Please ensure KVM is properly installed and usable.
CPU acceleration status: KVM is not installed on this machine (/dev/kvm is missing).


I've been searching and some tuturials order me to run -  egrep -c '(vmx|svm)' /proc/cpuinfo          - and if the output is 0, it's because kmv is not supported im my system. The command gives me 0, but I don't understand how it's not supported if a few days ago it was running smootlhy.

Best wishes,
João

---

### Post by sotiris2 on 2014-11-25
Well if you really had KVM support the only logical reason for a disappearance would be a change in BIOS options. Since I believe you would remember changing that it is unlikely except if you had boot issues recently and reseted your bios (and it defaults to no kvm support).

 Secondly and I am just making a somewhat wild guess, I think KVM has to do with x86 virtualization on x86 hardware which is not actually emulation. Since most android devices are ARM based is it possible that before you emulated an ARM device which did not require KVM support but you are now emulating an x86 device which needs KVM support?

---

### Post by joo_marques2 on 2014-11-25
I've tought about that too, and I decided to change the CPU/ABI option to ARM (armeabi-v7a). Unfortunately the same error appears, wich is very strange

---

