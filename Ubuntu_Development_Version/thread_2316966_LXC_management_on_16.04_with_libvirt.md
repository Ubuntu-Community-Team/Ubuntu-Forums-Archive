---
title: "LXC management on 16.04 with libvirt"
date: 2016-03-12
forum: Ubuntu Development Version
---

### Post by markus34 on 2016-03-12
Hi,

I created a LXC OS container on ubuntu 16.04 and started it. After stopping it and adding it to libvirt, I get an error message every time I try to start it with virt-manager or virsh. Below are the commands I used:

```

root@lxchost:~# lxc-create -n testing -t ubuntu -P /home/benutzer/lxc
Checking cache download in /var/cache/lxc/xenial/rootfs-amd64 ... 
Copy /var/cache/lxc/xenial/rootfs-amd64 to /home/benutzer/lxc/testing/rootfs ... 
Copying rootfs to /home/benutzer/lxc/testing/rootfs ...
Generating locales...
  de_DE.UTF-8... done
Generation complete.
Creating SSH2 RSA key; this may take some time ...
2048 SHA256:LHZfFeOD2YVAP9bNlMh0J+G5DMTOG2tUuJtOD9YNMKg root@lxchost (RSA)
Creating SSH2 DSA key; this may take some time ...
1024 SHA256:cRQVdARG3iwnAVLnZhL18TAMtto7b1y282Lhjsnk7cM root@lxchost (DSA)
Creating SSH2 ECDSA key; this may take some time ...
256 SHA256:ilgFALRLqG+VeiatYWiLJ4/ff4hDic2KRJXOgjrRKXU root@lxchost (ECDSA)
Creating SSH2 ED25519 key; this may take some time ...
256 SHA256:MC7Y1/BM55DI9h/BsFabN6iDBiFfFgFL0CfLB26T4GQ root@lxchost (ED25519)
invoke-rc.d: policy-rc.d denied execution of start.

Current default time zone: 'Etc/UTC'
Local time is now:      Sat Mar 12 13:46:59 UTC 2016.
Universal Time is now:  Sat Mar 12 13:46:59 UTC 2016.


##
# The default user is 'ubuntu' with password 'ubuntu'!
# Use the 'sudo' command to run tasks as root in the container.
##

root@lxchost:~# lxc-ls --fancy --name testing -P /home/benutzer/lxc
NAME    STATE   AUTOSTART GROUPS IPV4 IPV6 
testing STOPPED 0         -      -    -    

root@lxchost:~# lxc-start --name testing -P /home/benutzer/lxc/

root@lxchost:~# lxc-ls --fancy --name testing -P /home/benutzer/lxc
NAME    STATE   AUTOSTART GROUPS IPV4      IPV6 
testing RUNNING 0         -      10.0.3.30 -    

root@lxchost:~# lxc-attach --name testing -P /home/benutzer/lxc/

root@testing:~# uname -a
Linux testing 4.4.0-10-generic #25-Ubuntu SMP Wed Mar 2 14:55:50 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

root@testing:~# exit

root@lxchost:~# uname -a
Linux lxchost 4.4.0-10-generic #25-Ubuntu SMP Wed Mar 2 14:55:50 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

root@lxchost:~# lxc-stop --name testing -P /home/benutzer/lxc/

root@lxchost:~# lxc-ls --fancy --name testing -P /home/benutzer/lxc
NAME    STATE   AUTOSTART GROUPS IPV4 IPV6 
testing STOPPED 0         -      -    -    

root@lxchost:~# virsh -c lxc:/// domxml-from-native lxc-tools /home/benutzer/lxc/testing/config > /home/benutzer/lxc/testing/config.xml

root@lxchost:~# cat /home/benutzer/lxc/testing/config.xml 
<domain type='lxc'>
  <name>testing</name>
  <uuid>55ba6a56-5660-46ba-8e65-15f0d3a181e6</uuid>
  <memory unit='KiB'>65536</memory>
  <currentMemory unit='KiB'>65536</currentMemory>
  <vcpu placement='static'>1</vcpu>
  <resource>
    <partition>/machine</partition>
  </resource>
  <os>
    <type arch='x86_64'>exe</type>
    <init>/sbin/init</init>
  </os>
  <features>
    <capabilities policy='allow'>
    </capabilities>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/lib/libvirt/libvirt_lxc</emulator>
    <filesystem type='mount' accessmode='passthrough'>
      <source dir='/home/benutzer/lxc/testing/rootfs'/>
      <target dir='/'/>
    </filesystem>
    <interface type='bridge'>
      <mac address='00:16:3e:26:01:56'/>
      <source bridge='lxcbr0'/>
      <link state='up'/>
    </interface>
    <console type='pty'>
      <target type='lxc' port='0'/>
    </console>
  </devices>
</domain>

root@lxchost:~# virsh -c lxc:/// define /home/benutzer/lxc/testing/config.xml 
Domain testing von /home/benutzer/lxc/testing/config.xml definiert

root@lxchost:~# virsh -c lxc:/// start testing
Domain testing gestartet

root@lxchost:~# virsh -c lxc:/// console testing
Verbunden mit der Domain: testing
Escape-Zeichen ist ^]
Failed to mount cgroup at /sys/fs/cgroup/systemd: Permission denied
[!!!!!!] Failed to mount API filesystems, freezing.
Freezing execution.


```

What can I do to get this up and running?

kind regards,

Markus

---

### Post by Bucky Ball on 2016-03-12
*Thread moved to **Ubuntu Development Version**.*

---

### Post by dino99 on 2016-03-12
your two latest log entries explain the problem. Follow that wiki about cgroups:
[https://wiki.debian.org/LXC](https://wiki.debian.org/LXC)

---

### Post by markus34 on 2016-03-12
I installed libvirt-bin, which was missing and added the line to /etc/fstab. After a reboot, I tried again, but I got the same error again. I tried to mount beforehand and got this output:

[ATTACH=CONFIG]267778[/ATTACH]

---

### Post by MAFoElffen on 2016-03-12
Your problem seems to me ... not a Dev 16.04 version LXC issue ... but rather trying to use an LXC container as an unprivileged user. I use those images as a privileged user and have no troubles... So I read your problems as being permissions related.

For info related more to Ubuntu LXC (instead of just Debian) and related to how you are trying use / access the LXC Container as an unprivileged user, please go to the [Ubuntu LXC Docs]("https://help.ubuntu.com/lts/serverguide/lxc.html") (<-- Link), and read the sections "User Namespaces," "Basic Unprivileged Usage," and "Nesting."

---

### Post by markus34 on 2016-03-12
but I am running virsh in a sudo -i environment, shouldnt root be privileged enough?

---

### Post by MAFoElffen on 2016-03-12
But this is where you varied from a default priviledged LXC environment:
```

lxc-ls --fancy --name testing -P [COLOR=#ff0000]/home/benutzer/lxc[/COLOR]

```
it no longer is located in a directory that had permissions setup to run containers, right?
> 
[COLOR=#333333][FONT=Ubuntu]...so that it is seamless for unprivileged use. The rootfs for a privileged directory backed container is located (by default) under [/FONT][/COLOR][COLOR=#333333][FONT=monospace]/var/lib/lxc/C1/rootfs[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu], while the rootfs for an unprivileged container is under [/FONT][/COLOR][COLOR=#333333][FONT=monospace]~/.local/share/lxc/C1/rootfs[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]. If a custom lxcpath is specified in lxc.system.com, then the container rootfs will be under [/FONT][/COLOR][COLOR=#333333][FONT=monospace]$lxcpath/C1/rootfs[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu].[/FONT][/COLOR]

Has to do with the settings you have in your lxc.conf files, whether it is looking for settings under /etc/lxc or under ~/.config/lxc. If you are using as privileged, then it is using settings from /etc/lxc/lxc.conf...
```

ls -la /home/benutzer/lxc
ls -la $lxcpath

```
Do those match?

If not ... and if that is how you are going to use it, then make the permissions and group ownership match. Either that, or set if up further for unprivileged use for container images located there.

EDIT-- But then I see this:
> 
[COLOR=#333333][FONT=Ubuntu]By default, containers are located under /var/lib/lxc for the root user, and $HOME/.local/share/lxc otherwise. The location can be specified for all lxc commands using the "-P|--lxcpath" argument.
[/FONT][/COLOR]

Or just as a test, install the image to it's default image directory ... create a container and run it. Did it run without errors? It it ran, then it is a difference in the location of the image, the settings & permissions set for it to run in that environment.

---

### Post by markus34 on 2016-03-13
Hi,

thank you very much for the advice, I created a VM without specifying a path and tried to manage it with virsh. Sadly I got the same error again. I also tried to run the old setup with chmod 777 -R on the rootfs folder, and it didnt work either :(

---

