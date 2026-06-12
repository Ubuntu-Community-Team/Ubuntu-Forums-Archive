---
title: "KVM shutdown problem"
date: 2009-02-11
forum: Virtualisation
---

### Post by sevor on 2009-02-11
Ok so I have been playing with KVM.  I have a running vm and every time I enter (I should say that usTest is the name of my vm)

    virsh shutdown usTest  

It brings back
    connecting to uri: qemu:///system
    Domain usTest is being shutdown

Now if I run
    virsh list --all

It returns

id Name             State
-------------------------
1  usTest          running

it does not acutally shut down.  Am I missing something?
Please help.

---

### Post by sevor on 2009-02-11
nvm ....  After doing more research if Shutdown doesnt work (which there is no guarantee it will)  use the destroy command.. it simulates pulling the powercord!

---

### Post by jimezam on 2010-01-04
I solved this problem today.

Check that your have the ACPI feature on in the virtual machine specification XML file and installed on the guest.

For example, if your guest is Ubuntu you should install ACPId.

$ sudo aptitude install acpid

After that, the shutdown works as like a charm.

I hope it helps.

jimezam.

---

### Post by ryanrad on 2010-07-02
Thanks jimezam.  I can confirm that I had the same problem and
```
sudo aptitude install acpid
```
worked for me as well.

---

### Post by kuda on 2010-09-11
1+ thank you!!!

---

### Post by basdoorn on 2010-12-10
I have just needed to install the acpi-support package to get a 10.04 guest to finaly shutdown properly. This was needed in addition to the already present acpid package and the <acpi/> tag in the xml configuration of the guest.

---

