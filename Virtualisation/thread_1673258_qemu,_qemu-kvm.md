---
title: "qemu, qemu-kvm"
date: 2011-01-22
forum: Virtualisation
---

### Post by swamybabu on 2011-01-22
Hi, 

I have ubuntu 10.10 64 bit (intel). using synaptic, I installed the following packages.

1) qemu (0.12.5)
2) qemu-kvm (0.12.5)
3) kvm (0.12.5)
3) qemu-kvm-extras

Now that I have downloaded qemu (0.13.0) & qemu-kvm (0.13.0) and installed both of them (using commands configure, make && make install)

checked the following commands

1) qemu --version  OUTPUT is : 0.13.0 

but, 

2) kvm --version still reports 0.12.5

3) qemu-kvm --- command not found

Can someone tell me why this is happening and also can someone elaborate on commands kvm, qemu-kvm, qemu along with differences? 

If I give the command

qemu -enable-kvm -net nic -net user -hda WinXP.qcow2

Is this going to use kvm ? how to cross check whether it is really using kvm or not? the reason for asking the later question is : without installing qemu-kvm/kvm, I tried the above qemu command with -enable-kvm then also it went fine without any error.

Thanks in advance,
       SWAMY

---

### Post by bodhi.zazen on 2011-01-24
kvm and qemu are merging.

kvm provides the kernel modules only (i386 and amd64). The extras are for other arch (CPU).

qemu provides the rest ("BIOS" in the guest).

As far as the specifics, it would depend on what version of Ubuntu you are running.

See the various packages for details.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=kvm&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=kvm&searchon=name&subword=1&version=all&release=all)

---

