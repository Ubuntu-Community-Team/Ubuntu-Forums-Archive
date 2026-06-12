---
title: "Launch KVM Machine from Command Line"
date: 2022-02-10
forum: Virtualisation
---

### Post by Quarkrad on 2022-02-10
I have a kvm machine called win10 (win10.qcow2) - I would like to run a script that would launch this machine.  I have played with *virsh start win10* but all this does (looking at the libvirt manager gui) is start the machine (which I guess is fair enough!) - in order to launch as a Desktop machine I have to *Open* it via virt manager. So I'm half way to where I want to go.  Is there a (simple?) way of running a *command/having a script* that will actually launch win10.qcow2 as a Desktop machine?

---

### Post by TheFu on 2022-02-10
> **Quarkrad said:**
> I have a kvm machine called win10 (win10.qcow2) - I would like to run a script that would launch this machine.  I have played with *virsh start win10* but all this does (looking at the libvirt manager gui) is start the machine (which I guess is fair enough!) - in order to launch as a Desktop machine I have to *Open* it via virt manager. So I'm half way to where I want to go.  Is there a (simple?) way of running a *command/having a script* that will actually launch win10.qcow2 as a Desktop machine?

```
#!/bin/bash

if [[ $HOSTNAME == "hadar" ]] ; then
   # Is the VM running?
   ON=$( virsh list |egrep -c Win7Ult )
   echo "ON says: $ON"
   if [ $ON == "0" ] ; then
      echo "Win7Ult VM not running. Starting ..."
      virsh start Win7Ult
   else
      echo "Win7Ult VM is already running"
   fi
    # For local connection on hadar
    /usr/bin/virt-viewer -a -d  Win7Ult &
else
    # For remote connections on the LAN
    /usr/bin/virt-viewer --connect qemu+ssh://hadar/system Win7Ult &
fi

```
That's what I do to start a Win7 VM on hadar, then start the local virt-viewer to access the GUI. It isn't production ready, but probably fine for home use. I break a number of scripting rules.

hadar is the VM host.
Win7Ult is the VM name, according to libvirt. It is case-sensitive. Yes, I'm stupid for mixing case in VM-names.

---

### Post by Quarkrad on 2022-02-10
Wow - that works brilliantly.  Yet another forum user thanking you for your help.

---

### Post by TheFu on 2022-02-10
> **Quarkrad said:**
> Wow - that works brilliantly.  Yet another forum user thanking you for your help.

It is 100% dependent on the reader to understand that it was a script and how to deal with that. Lots and lots of newer Linux users wouldn't know what to do with that response.

Best of all, it works remotely too. So if you have a Linux system elsewhere in the house with virt-viewer installed, it can access the "desktop" using ssh+spice over the LAN.  It is fast enough to be used for anything except FPS gaming or video editors.

Lots of unstated dependencies ... ssh, SPICE, virt-manager all have to be setup on both sides.  If ssh uses key-based authentication, it won't prompt for a password either; assuming ssh-agent and the main ssh-key has already been unlocked since the last reboot.  Basically, it is seamless.  Copy the script to any Linux systems you want to connect to the desktop from  ... 

But if you are already on the LAN, I'd just use **ssh -X program-name** instead.  Have the desktop system started up automatically, that's what I do for my "main desktop" ... it really isn't my main desktop, but it has all the desktop programs that I use on it. Those are accessed remotely, since some of them are dangerous ... like browsers and email clients.  Not worth the risk of running on a physical machine, IMHO.

For example, here's my thunderbird launch script:
```
#!/bin/bash

# limit RAM VSS to 4.7G
FJ_OPTS="--dns=172.22.22.80 --rlimit-as=4700000000 "
TB_OPTS="-no-remote "

PID=$(ssh -X  regulus /usr/bin/firejail $FJ_OPTS /usr/bin/thunderbird $TB_OPTS $@ & )
exit;
```
I got tired of FF and Thunderbird trying to snatch all the RAM+swap in a system, so decided to limit what it could even see. Also, I wanted to force all DNS to my pi-hole, regardless of what thunderbird/firefox wanted and the -no-remote prevents the normal Mozilla ignoring of which machine we're running the process ... without it, the process will try to connect back to another instance on a different machine. If I wanted that, I'd have gone out of my way to make it happen. The Mozilla team has been screwing us on this stuff for 10 yrs on the RAM-grab and 20+ yrs on the remote-connect-back-to source stuff.

---

