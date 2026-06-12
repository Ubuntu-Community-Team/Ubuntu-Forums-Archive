---
title: "Crash Dumps in Ubuntu with EC2"
date: 2013-11-15
forum: Ubuntu Cloud and Juju
---

### Post by mario-aleman on 2013-11-15
Hi everyone.


I'm trying to configure an Ubuntu AMI capable of record crash dumps.
ubuntu-precise-12.04-amd64-server-20131003 (ami-3f32ac3e)


I followed this recipe:
[https://wiki.ubuntu.com/Kernel/CrashdumpRecipe](https://wiki.ubuntu.com/Kernel/CrashdumpRecipe)


But after having all configured and testing it, it doesn't show any dump files in /var/crash


I also found this happened to another user [bug unrelated] [https://bugs.launchpad.net/ubuntu/+source/linux-ec2/+bug/614853](https://bugs.launchpad.net/ubuntu/+source/linux-ec2/+bug/614853)


And in the thread says that the person was trying to capture also the crash, but the files
never appeared.

In first instance I thought it was because I didn't had a swap partition, but added it and there were no changes.


Is this a bug? or is just a misconfiguration?

By the way here are the commands to check that crashdump is running:

root@ip-172-31-11-34:/var# cat /sys/kernel/kexec_crash_loaded
1
ubuntu@ip-172-31-11-34:~$ cat /proc/cmdline 
root=LABEL=cloudimg-rootfs ro console=hvc0  crashkernel=384M-2G:64M,2G-:128M

Greetings!

---

### Post by esnyder on 2014-02-05
I have no answer for you, just wanted to chime in with a "me too," as your attempts and problems mirror mine exactly.

---

