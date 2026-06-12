---
title: "fast way to clone running machines"
date: 2012-05-07
forum: Virtualisation
---

### Post by Lovebongo on 2012-05-07
Hello,

I'm currently playing around with kvm-qemu. I would like to copy a running machine (or a machine paused in a booted state) and start it on demand. I was able to save a machine state (with savevm) and load the state again but that seems to take a lot of time (about 20 seconds). Is there any faster way?

I saw a video on youtube where a guy did a live migration (post copy live migration) in about one second. I figured that if a live migration can be that fast then it should'nt be a problem to copy and start/resume an image of a machine saved in a certain state or even running (by using copy on read/write for example for hard disk and memory like in the post copy live migration).

Just in case this is not possible with kvm-qemu, is there any other virtualization solution where it is possible to clone and start a running machine?

I'm quite new to virtualization, therefore this question might sound a little bit stupid, I apologize for that. Thank you very much in advance for your help...

---

### Post by wilee-nilee on 2012-05-07
Personally I use virtualbox and use a vdi type file when asked. This is on installs of course, that file can be used in another vbox just a copy and paste and loading it to a new machine.

---

