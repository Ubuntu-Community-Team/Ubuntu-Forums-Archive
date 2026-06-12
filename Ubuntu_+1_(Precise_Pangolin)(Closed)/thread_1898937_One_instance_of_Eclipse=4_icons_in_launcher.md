---
title: "One instance of Eclipse=4 icons in launcher"
date: 2011-12-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-12-22
All I did was apply yesterday updates. It was working fine before it. Clicking any of the 4 Eclipse icons makes the only instance active. See in the screenshot that 3 of the 4 icons have the "white arrow" aside. 

Things are starting to get really dangerous lol.

[ATTACH]209564[/ATTACH]

---

### Post by ventrical on 2011-12-22
> **effenberg0x0 said:**
> All I did was apply yesterday updates. It was working fine before it. Clicking any of the 4 Eclipse icons makes the only instance active. See in the screenshot that 3 of the 4 icons have the "white arrow" aside. 

Things are starting to get really dangerous lol.

[ATTACH]209564[/ATTACH]

That eclipse app works ok here.

```

ventrical@ventrical-P4M266A-8237:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary)
ventrical@ventrical-P4M266A-8237:~$ 
```

---

### Post by effenberg0x0 on 2011-12-22
Hey Ventrical, 

2 quick questions:

- Did you install it from precise repos (Eclipse Indigo) or from Eclipse website (Indigo, Juno, etc)
- Your java -version is OpenJDK, sun-java6, oracle-java6, oracle-java7, etc?

Thanks

---

### Post by ventrical on 2011-12-22
> **effenberg0x0 said:**
> Hey Ventrical, 

2 quick questions:

- Did you install it from precise repos (Eclipse Indigo) or from Eclipse website (Indigo, Juno, etc)
- Your java -version is OpenJDK, sun-java6, oracle-java6, oracle-java7, etc?

Thanks

Precise repos-  (Eclipse Indigo)
openjdk-6

---

### Post by effenberg0x0 on 2011-12-23
In fact, Indigo with OpenJDK woks fine, so most users will have no problem with it. I had my alternatives set to oracle-java-7u2 and am running Eclipse Juno 4.2.0. So it's not something usual. Any misbehaviour will probably be addresses properly now that sun-java-6u* legacy and oracle-java-7u* are to be replaced by OpenJDK as the true default implementation people are supposed to develop to.

---

