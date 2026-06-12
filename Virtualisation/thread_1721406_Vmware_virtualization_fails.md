---
title: "Vmware virtualization fails"
date: 2011-04-04
forum: Virtualisation
---

### Post by cloud25 on 2011-04-04
i am using vm player for my UEC work i had running an instance..during that time i find bug

server@Node:~$ kvm-ok
INFO: Your CPU does not support KVM extensions
KVM acceleration can NOT be used
server@Node:~$ 

i had enabled the intel-vt and AMD-V in vmplayer from the processor option but till i am getting the same..

how to solve this and make my cpu to use KVM support.

---

### Post by falko on 2011-04-05
Does
```
egrep '(vmx|svm)' --color=always /proc/cpuinfo
```
show any output?

---

