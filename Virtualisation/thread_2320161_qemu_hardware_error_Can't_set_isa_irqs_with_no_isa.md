---
title: "qemu: hardware error: Can't set isa irqs with no isa bus present"
date: 2016-04-11
forum: Virtualisation
---

### Post by ardabeyaz on 2016-04-11
When i am trying to run android emulators, i got this error on a fresh ubuntu-kde 14.04 (64bit). 
Looks like a problem about qemu or kvm, however i dont have much knowledge about it. Is there any possible reasons for this ?

```
Starting emulator for AVD 'Nexus_5X_API_23'
**qemu: hardware error: Can't set isa irqs with no isa bus present.**
CPU #0:
EAX=00000000 EBX=00000000 ECX=00000000 EDX=00000663
ESI=00000000 EDI=00000000 EBP=00000000 ESP=00000000
EIP=0000fff0 EFL=00000002 [-------] CPL=0 II=0 A20=1 SMM=0 HLT=0
ES =0000 00000000 0000ffff 00009300
CS =f000 ffff0000 0000ffff 00009b00
SS =0000 00000000 0000ffff 00009300
DS =0000 00000000 0000ffff 00009300
FS =0000 00000000 0000ffff 00009300
GS =0000 00000000 0000ffff 00009300
LDT=0000 00000000 0000ffff 00008200
TR =0000 00000000 0000ffff 00008b00
GDT=     00000000 0000ffff
IDT=     00000000 0000ffff
CR0=60000010 CR2=00000000 CR3=00000000 CR4=00000000
DR0=0000000000000000 DR1=0000000000000000 DR2=0000000000000000 DR3=0000000000000000 
DR6=00000000ffff0ff0 DR7=0000000000000400
EFER=0000000000000000
FCW=037f FSW=0000 [ST=0] FTW=00 MXCSR=00001f80
FPR0=0000000000000000 0000 FPR1=0000000000000000 0000
FPR2=0000000000000000 0000 FPR3=0000000000000000 0000
FPR4=0000000000000000 0000 FPR5=0000000000000000 0000
FPR6=0000000000000000 0000 FPR7=0000000000000000 0000
XMM00=00000000000000000000000000000000 XMM01=00000000000000000000000000000000
XMM02=00000000000000000000000000000000 XMM03=00000000000000000000000000000000
XMM04=00000000000000000000000000000000 XMM05=00000000000000000000000000000000
XMM06=00000000000000000000000000000000 XMM07=00000000000000000000000000000000
CPU #1:
EAX=00000000 EBX=00000000 ECX=00000000 EDX=00000663
ESI=00000000 EDI=00000000 EBP=00000000 ESP=00000000
EIP=0000fff0 EFL=00000002 [-------] CPL=0 II=0 A20=1 SMM=0 HLT=1
ES =0000 00000000 0000ffff 00009300
CS =f000 ffff0000 0000ffff 00009b00
SS =0000 00000000 0000ffff 00009300
DS =0000 00000000 0000ffff 00009300
FS =0000 00000000 0000ffff 00009300
GS =0000 00000000 0000ffff 00009300
LDT=0000 00000000 0000ffff 00008200
TR =0000 00000000 0000ffff 00008b00
GDT=     00000000 0000ffff
IDT=     00000000 0000ffff
CR0=60000010 CR2=00000000 CR3=00000000 CR4=00000000
DR0=0000000000000000 DR1=0000000000000000 DR2=0000000000000000 DR3=0000000000000000 
DR6=00000000ffff0ff0 DR7=0000000000000400
EFER=0000000000000000
FCW=037f FSW=0000 [ST=0] FTW=00 MXCSR=00001f80
FPR0=0000000000000000 0000 FPR1=0000000000000000 0000
FPR2=0000000000000000 0000 FPR3=0000000000000000 0000
FPR4=0000000000000000 0000 FPR5=0000000000000000 0000
FPR6=0000000000000000 0000 FPR7=0000000000000000 0000
XMM00=00000000000000000000000000000000 XMM01=00000000000000000000000000000000
XMM02=00000000000000000000000000000000 XMM03=00000000000000000000000000000000
XMM04=00000000000000000000000000000000 XMM05=00000000000000000000000000000000
XMM06=00000000000000000000000000000000 XMM07=00000000000000000000000000000000

```

---

### Post by MAFoElffen on 2016-04-11
You "say" you suspect a Qemu error, but...

What android emulator are you trying to run? How? (meaning, is it formally using qemu? If not, what?)

---

### Post by ardabeyaz on 2016-04-12
My emulator options are like this:

Device: Nexus 5
Architecture: SDK 6.0, Api Level 23, Google Apis (Intel x86_64)
Enable Host Gpu: yes or no (both tried)

I am not sure about qemu, it is just written in the error message. Everything worked a while ago until it stopped after some updates. Then I made a clean ubuntu install, installed only neccesary packages like java, android etc.. I also followed this [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation) to enable kvm. However, it doesnt work in any case.

---

### Post by MAFoElffen on 2016-04-13
Do you have adt installed and loaded? Meaning have you installed the Android SDK? From Linux, I use Eclipse and the Android SDK, so have that perspective of the emulator.

But to be honest, I've never seen that throw a qemu error.

---

### Post by ardabeyaz on 2016-04-14
I have everything installed and loaded. Everything workes except emulators. And that was also working in the past. I dont know which update broke this.

---

### Post by MAFoElffen on 2016-04-15
On the original Installation: Did you download the SDK zip from Google or did you install .deb package through the Ubuntu SDK Developer PPA?

Can you open the SDK Manager? 

Thinking maybe after some kernels updates, that maybe the emulator might need to be reinstalled, which would recompile it with the newer kernel... Just thinking out loud.

---

### Post by ardabeyaz on 2016-04-16
I downloaded the standalone android sdk, and sdk manager works fine. I did a fresh install of ubuntu and then installed android the last time and nothing changed...

---

### Post by ahmetmatematikci on 2016-06-30
Is this a problem solved ???
What is problem solving ?

---

### Post by ardabeyaz on 2016-06-30
No, but I started to use Genymotion android emulator. It works well and even better. [https://www.genymotion.com/](https://www.genymotion.com/)

---

### Post by ahmetmatematikci on 2016-06-30
[SIZE=1]
[/SIZE]
&#8203;I started using the genymotio . Android Studio and Genyöotio i5 CPU and 4 GB RAM computer tiring.

---

