---
title: "KVM - Official way of doing one guest snapshot"
date: 2011-07-21
forum: Virtualisation
---

### Post by erlguta on 2011-07-21
Hi.
I am looking further information about the 'official' way of doing one
guest snapshot.
After taking time reading this forum, the kvm doc and personal blogs
I'm still not sure which is the official way or the bests practise to
make a guest snapshot and if there is a way to do a consistent
snapshot while the guest is running (for example for critical services
that can not be sttoped).

1- Now, I make my guest snapshost's in a very basic way, but it works
for me. I have made a simple script that stops the guests I want with
the 'virsh suspend' command, then clone this guests with the
'virt-clone' command and finally resume them with the 'virsh resume'
command.
I'm reinventing the wheel with my script and is there some official
utility to do this?

2- Assuming that you can clone a running guest, which sincerely make
my day happy, what is the way to do it or where I can find information
about this?.

Thank you very much for your answers and time.

Gonzalo Marcote.

---

