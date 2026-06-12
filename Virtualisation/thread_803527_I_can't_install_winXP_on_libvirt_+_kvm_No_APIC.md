---
title: "I can't install winXP on libvirt + kvm: No APIC"
date: 2008-05-22
forum: Virtualisation
---

### Post by Román on 2008-05-22
Hi! 

I'm trying to install a Windows XP virtual machine on libvirt + kvm + qemu on a ubuntu 8.04 system), but it fails &#65279;every time on this AMD 64 machine.  As soon as it boots (from a win XP installer CD), the installation aborts because it can't find APIC.  The virt-install command I'm using is:

```
sudo virt-install -n windows1024 -r 1024 -f ./uindows_recursiva.img -s 10 -v -c /dev/hdb --os-type=windows --os-variant=winxp
```

This same machine has a windows xp installed so I guess somehow apic is not getting "exported" to the virtual machine.

My questions are:

a) ¿Is my guess right? ¿Am I doing something else wrong?
b) If I'm right ¿How do I fix it?

Beside this particular issue:
c) Every time an install fails, I have to change the VM name because qemu says 
```
ERROR:  Domain named windows1024 already exists!
```  
¿How/where do I delete failed domains?

d) I made an ISO out of the CD (I think I used kiso or genisoimage, I don't remember now) but I can't boot a VM from that iso ¿Did I forget to tell it "make this iso bootable"?

I hope I'm giving all the information needed, if you need anything else, just ask.

---

### Post by Román on 2008-05-23
¿Warnocked?

---

### Post by Glucklich on 2008-05-23
Can I make a suggestion? I didn't know how you were trying to make your virtual machine. But I got mine by installing a program called VirtualBox OSE (check your programs list and later it will ask you to get some things on synaptic) and install Win XP normally.
That's all I had to do.
Hope this helps you.

---

### Post by Re Persina on 2008-05-27
Román: 
a) I'm not sure if it will help, but you can try using the --noapic flag.

c) Even though the install fails, the virtual domain is still created. You can try stopping/restarting the existing domain to reattempt installation, or if you want to start from scratch, stop (if necessary) and undefine the existing domain first.

```
virsh shutdown windows1024
virsh undefine windows1024
```

---

### Post by Román on 2008-06-07
Hi! Sorry I didn't answer before.

About VirtualBox OSE, it needs a kernel module witch is not always available for the last kernel i.e. the one I'm usually running.  And I can't easily switch kernels because I've got a nVidia graphics card so I get a black screen due to the wrong restricted-modules version.  That card was one of my worst mistakes, I know.

@[Re Persina]("http://ubuntuforums.org/member.php?u=462198"): --noapic doesn't work.  Actually I think I need a --yesapic flag...  The "virsh undefine" command did the trick though, thanks

---

### Post by hopelessone on 2008-06-07
Hi,

i have the same computer and followed the guide in community docs @ [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

no probs installing xp afterwards...have a look maybe it can help you with something as i stuffed up my first install..

---

### Post by besson3c on 2008-06-14
I'm having this same problem, even with APIC enabled in my domain's XML:

<features>
	  <pae/>
	  <acpi/>
	  <apic/>
	</features>

---

### Post by besson3c on 2008-06-14
> **besson3c said:**
> I'm having this same problem, even with APIC enabled in my domain's XML:

<features>
	  <pae/>
	  <acpi/>
	  <apic/>
	</features>


My capabilities says that apic should have been enabled by default anyway...

Has anybody gotten libvirt/WindowsXP 64 bit working in AMD 64?

---

### Post by besson3c on 2008-06-15
I figured it out. After modifying your domain XML to add:

<features>
<apic/>
</features>

You need to define your domain:

virsh -c qemu:///system define /etc/libvirt/qemu/yourdomain.xml


You can observe what flags are being sent to start KVM/qemu by checking out your logs in /var/log/libvirt. If you are seeing "-no-apic", your domain still hasn't been updated to reflect the above change. I suppose the default os-type/os-variant settings for Windows don't include APIC support?

Hope this helps!

---

### Post by besson3c on 2008-06-16
Sorry, the above should read "<acpi/>" not "<apic/>"

---

