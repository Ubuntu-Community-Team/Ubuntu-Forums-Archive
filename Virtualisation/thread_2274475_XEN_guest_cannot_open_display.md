---
title: "XEN guest cannot open display"
date: 2015-04-20
forum: Virtualisation
---

### Post by sklpr on 2015-04-20
Hello all, 

My setup is : [B][I]

[XEN - dom0][/I][/B] installed directly on hardware [ubuntu 12.04.5 server x64bit] , using it on CLI Mode - no GUI installed

***[domU - guest] ***HVM guest created via configuration file, I Determine the started DomU port attached with : 

*# xm list --long <domU_Name> | grep location *

but when i try to connect to guest with vinagre after exporting $DISPLAY to 127.0.0.1:5900 (since I am using Ubuntu ) I get the error-warning :

```
:~$ sudo vinagre 127.0.0.1:5900
:~$ (vinagre:*process_number*) : **Gtk-WARNING **: cannont open display** 
```

If i type (found it on google): ```
 :~$ sudo vinagre 127.0.0.1:5900 >/dev/null 2>&1 &1 
I get this >>> : [1]<*process_number*>
``` and then nothing happens..

If I try to *connect to domU via console* (sudo xm console <domainU name>) System stucks and I can't type or do something just reset via desktop button

Please ask me if you need further information about the problem .. Thanks in advance

---

### Post by sklpr on 2015-04-20
***//UPDATE***
I know that I don't have a GUI package installed already.. but how am I supposed then to connect to HVM guest and install guest OS etc.. since xm console crashes? any ideas would be helpful

---

### Post by TheFu on 2015-04-20
We stopped using Xen around 2011 ... over issues like this. Switched to KVM and never looked back. You cannot run a GUI desktop inside a VM sitting on the same machine with the hostOS dom0/domU. Well, that isn't strictly true, but doing it is beyond my skill and current hardware (it requires extremely specific MB, BIOS, kernel patches, and dedicated GPUs to work at all).

However, you may be able to install libvirt, and from a remote machine use virt-manager to create, configure, install, and shutdown VMs using Xen, KVM, VirtualBox, etc ... (supported hypervisors are listed at the libvirt page).  I haven't tried this with Xen myself, we used xm scripts back then.

After you get a DomU installed, you can install GUI packages (hopefully something lite - LXDE, XFCE) and install an x2go-server. Then from any client machine, running x2go-client, connect to the server and have a remote desktop. Does that make sense?

Basically, the Dom0 server doesn't need a GPU or any other connections except power cord and ethernet cable for this to work.

---

### Post by sklpr on 2015-04-20
Thanks a lot for helping me again and giving me resources to study and think about!! ( I hope you remember me :P from other posts about XEN) 

Hmm Correct me if I am wrong but you can't have *fully virtualized* memory(RAM) on KVM because it's paravirtualized ? My guests need to be *Hardware Virtual Machines* because I need to research some things on  *volatile memory* of guest VM(Needing direct access+*fully virtualized memory*) and I can't do that using paravirtualization.

They do make sense, since I am always searching for information in order to troubleshoot my problems and ubuntuforums has many specialists !!

This ***libvirt*** thing sounds a good idea..  since I don't have any other solution plus I have to use to use XEN :D

---

### Post by TheFu on 2015-04-20
KVM is NOT paravirtual.  Xen has a paravirtual mode that many people use, but it also has an HVM mode which uses more resources.
Virtualbox and ESXi are NOT paravirtual either.

I don't know the answer to the specific RAM question inside any VM.

---

### Post by sklpr on 2015-04-23
I FINALLY managed to connect from another PC with GUI installed in the network to my XEN [ with ssh -Y uname@XEN_IP thank you so much for pointing this out :-) ]

then I try to connect to domU with ```
 sudo vinagre 127.0.0.1:5900
``` 

And I get the following errors - warnings : 
```
Gtk-Message: Failed to load module "canberra-gtk-module"

** (vinagre:4985): WARNING **: Error spawning command line `dbus-launch --autolaunch=05b4c192e763776c5249cc6700000628 --binary-syntax --close-stderr': Failed to execute child process "dbus-launch" (No such file or directory)

** (vinagre:4985): WARNING **: Failed to initialize mDNS browser: Failed to create avahi client: Daemon not running

**
```
tp-glib:ERROR:base-client.c:1153:tp_base_client_constructed: assertion failed: (self->priv->dbus != NULL)

The solution on the first one *_[Failed to load module "canberra-gtk-module"]_* is easy :

sudo apt-get install libcanberra-gtk3-module

---> Any ideas about how to fix the second error - warning _***[Failed to initialize mDNS browser: Failed to create avahi client: Daemon not running]***_?

---> In addition after domU installation the ***guest_VM asked me to reboot *** and after the reboot it crashed and now when i try to connect to it.. it shows black & grey boxes everywhere and GUI is not showed up..

---

### Post by TheFu on 2015-04-23
**ssh -Y** is not secure. Be certain you understand the caveats in using that option.
Why are you using sudo for a remote desktop command?
I don't know anything about vinagre - not even what it does.

---

### Post by sklpr on 2015-04-23
I am going to try out this x2-go server , I am just trying things out ...

***// UPDATE ***

 The problem with the grey-black boxes and not being able to log into the guest-VM (domU) was on the*** .config file***....... so It's solved ! :-)

---

