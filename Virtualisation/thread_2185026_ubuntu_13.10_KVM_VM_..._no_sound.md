---
title: "ubuntu 13.10 KVM VM ... no sound"
date: 2013-10-31
forum: Virtualisation
---

### Post by bmullan2 on 2013-10-31
I had installed Ubuntu 13.10 on one system in a KVM VM and found there was no audio from the VM when it was running.

I created a fresh Ubuntu 13.10 KVM VM and again... no audio?

Anyone got any ideas or is this a bug with audio in Ubuntu 13.10?

---

### Post by TheFu on 2013-11-01
Use the spice client and audio should work. I've never seen audio work any other way on KVM.

I assume you are doing a desktop-on-desktop virtualization?

---

### Post by bmullan2 on 2013-12-14
I believe this is a bug in 13.10..   I was having the same problem with both KVM VM's and Amazon EC2 VMs.

My host PC is an ubuntu 13.10 x64 desktop.
I tried to troubleshoot this for several days with both the KVM VM's and the AWS VMs and got stumped.   I then started thinking maybe using a different version of ubuntu might help and doing some searching I came across this BUG report:
**[SIZE=4]/run/user/$ID/pulse owned by root and not by the user[/SIZE]**

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1197395](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1197395)

If you read through the BUG notes you will see that this is listed as a severe bug and that the Developers have a fix committed but not yet available (should be soon).

They list a simple test to show if you are affected:
TEST CASE:
- Ensure that as a normal user "echo $XDG_RUNTIME_DIR" is something like "/run/user/1000"
- do "sudo su -" to get a root shell
- In that root shell, do "echo $XDG_RUNTIME_DIR". In the saucy final  package this still gives /run/user/1000, which is incorrect for root and  leads to destroying the real user's runtime dir. With the fixed package it should be empty.

On my 13.10 system BOTH of these come back with the same response ... which showed me that this BUG was affecting me.  

If you find it is your problem be sure to click the link at the top to include yourself as someone affected by it.


Brian

---

