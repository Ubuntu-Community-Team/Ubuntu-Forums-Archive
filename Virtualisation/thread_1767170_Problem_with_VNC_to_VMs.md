---
title: "Problem with VNC to VMs"
date: 2011-05-25
forum: Virtualisation
---

### Post by kevpatts on 2011-05-25
Hey all,

I just backed up my VM's, reinstalled ubuntu and copied the VM's back in:
/var/lib/libvirt/images/*, /etc/libvirt/qemu/*, /etc/libvirt/qemu/networks/*, /etc/libvirt/nwfilter/*. I then installed the VM's using virsh nwfilter-define, virsh net-create, virsh create.

The machines start and stop fine but I can't VNC to them. In virt-manager I get the message:```
Error: viewer connection to hypervisor host got refused or disconnected!
``` and in the ~/.virt-manager/virt-manager.log file I get:```
[Wed, 25 May 2011 14:23:47 virt-manager 3633] DEBUG (engine:461) window counter incremented to 2
[Wed, 25 May 2011 14:23:47 virt-manager 3633] DEBUG (console:921) Starting connect process for proto=vnc trans=None connhost=localhost connuser=None connport=None gaddr=127.0.0.1 gport=5900 gsocket=None
[Wed, 25 May 2011 14:23:47 virt-manager 3633] DEBUG (console:808) Viewer disconnected
```

What am I doing wrong?

---

### Post by kevpatts on 2011-05-26
I forgot to mention that I created a new VM and it had the same problem also, and that virt-viewer also throws an error.

---

### Post by kevpatts on 2011-05-26
Full logging in DEBUG mode:
```
[Thu, 26 May 2011 10:55:13 virt-manager 2366] INFO (virt-manager:175) Application startup
[Thu, 26 May 2011 10:55:13 virt-manager 2366] DEBUG (virt-manager:352) Launched as: /usr/share/virt-manager/virt-manager.py --debug
[Thu, 26 May 2011 10:55:14 virt-manager 2366] DEBUG (config:34) Error importing spice: No module named SpiceClientGtk
[Thu, 26 May 2011 10:55:15 virt-manager 2366] DEBUG (engine:335) About to connect to uris ['qemu:///system']
[Thu, 26 May 2011 10:55:15 virt-manager 2366] DEBUG (engine:461) window counter incremented to 1
[Thu, 26 May 2011 10:55:15 virt-manager 2366] DEBUG (connection:872) Scheduling background open thread for qemu:///system
[Thu, 26 May 2011 10:55:15 virt-manager 2366] DEBUG (connection:1032) Background thread is running
[Thu, 26 May 2011 10:55:15 virt-manager 2366] DEBUG (connection:1060) Background open thread complete, scheduling notify
[Thu, 26 May 2011 10:55:15 virt-manager 2366] DEBUG (connection:1065) Notifying open result
[Thu, 26 May 2011 10:55:16 virt-manager 2366] DEBUG (connection:1072) qemu:///system capabilities:
<capabilities>

  <host>
    <uuid>c0191684-8dfe-d511-b5f3-00248cc146a0</uuid>
    <cpu>
      <arch>x86_64</arch>
      <model>Opteron_G3</model>
      <vendor>AMD</vendor>
      <topology sockets='1' cores='4' threads='1'/>
      <feature name='osvw'/>
      <feature name='3dnowprefetch'/>
      <feature name='cr8legacy'/>
      <feature name='extapic'/>
      <feature name='cmp_legacy'/>
      <feature name='3dnow'/>
      <feature name='3dnowext'/>
      <feature name='pdpe1gb'/>
      <feature name='fxsr_opt'/>
      <feature name='mmxext'/>
      <feature name='ht'/>
      <feature name='vme'/>
    </cpu>
    <migration_features>
      <live/>
      <uri_transports>
        <uri_transport>tcp</uri_transport>
      </uri_transports>
    </migration_features>
    <secmodel>
      <model>apparmor</model>
      <doi>0</doi>
    </secmodel>
  </host>

  <guest>
    <os_type>hvm</os_type>
    <arch name='i686'>
      <wordsize>32</wordsize>
      <emulator>/usr/bin/qemu</emulator>
      <machine>pc-0.14</machine>
      <machine canonical='pc-0.14'>pc</machine>
      <machine>pc-0.13</machine>
      <machine>pc-0.12</machine>
      <machine>pc-0.11</machine>
      <machine>pc-0.10</machine>
      <machine>isapc</machine>
      <domain type='qemu'>
      </domain>
      <domain type='kvm'>
        <emulator>/usr/bin/kvm</emulator>
        <machine>pc-0.14</machine>
        <machine canonical='pc-0.14'>pc</machine>
        <machine>pc-0.13</machine>
        <machine>pc-0.12</machine>
        <machine>pc-0.11</machine>
        <machine>pc-0.10</machine>
        <machine>isapc</machine>
      </domain>
    </arch>
    <features>
      <cpuselection/>
      <deviceboot/>
      <pae/>
      <nonpae/>
      <acpi default='on' toggle='yes'/>
      <apic default='on' toggle='no'/>
    </features>
  </guest>

  <guest>
    <os_type>hvm</os_type>
    <arch name='x86_64'>
      <wordsize>64</wordsize>
      <emulator>/usr/bin/qemu-system-x86_64</emulator>
      <machine>pc-0.14</machine>
      <machine canonical='pc-0.14'>pc</machine>
      <machine>pc-0.13</machine>
      <machine>pc-0.12</machine>
      <machine>pc-0.11</machine>
      <machine>pc-0.10</machine>
      <machine>isapc</machine>
      <domain type='qemu'>
      </domain>
      <domain type='kvm'>
        <emulator>/usr/bin/kvm</emulator>
        <machine>pc-0.14</machine>
        <machine canonical='pc-0.14'>pc</machine>
        <machine>pc-0.13</machine>
        <machine>pc-0.12</machine>
        <machine>pc-0.11</machine>
        <machine>pc-0.10</machine>
        <machine>isapc</machine>
      </domain>
    </arch>
    <features>
      <cpuselection/>
      <deviceboot/>
      <acpi default='on' toggle='yes'/>
      <apic default='on' toggle='no'/>
    </features>
  </guest>

</capabilities>

[Thu, 26 May 2011 10:55:16 virt-manager 2366] DEBUG (connection:1245) Connection doesn't seem to support interface APIs. Skipping all interface polling.
[Thu, 26 May 2011 10:55:16 virt-manager 2366] DEBUG (connection:545) Connection managed save support: True
[Thu, 26 May 2011 10:55:17 virt-manager 2366] ERROR (halhelper:87) Unable to connect to HAL to list network devices: <class 'dbus.exceptions.DBusException'> org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Hal was not provided by any .service files
[Thu, 26 May 2011 10:55:17 virt-manager 2366] DEBUG (connection:202) Could not initialize HAL for interface listing: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Hal was not provided by any .service files
[Thu, 26 May 2011 10:55:17 virt-manager 2366] DEBUG (connection:244) Using libvirt API for mediadev enumeration
[Thu, 26 May 2011 10:55:30 virt-manager 2366] DEBUG (engine:952) Starting vm 'Win7'.
[Thu, 26 May 2011 10:55:31 virt-manager 2366] DEBUG (manager:722) VM Win7 started
[Thu, 26 May 2011 10:55:34 virt-manager 2366] DEBUG (engine:461) window counter incremented to 2
[Thu, 26 May 2011 10:55:34 virt-manager 2366] DEBUG (console:921) Starting connect process for proto=vnc trans=None connhost=localhost connuser=None connport=None gaddr=127.0.0.1 gport=5900 gsocket=None
[Thu, 26 May 2011 10:55:34 virt-manager 2366] DEBUG (console:808) Viewer disconnected
[Thu, 26 May 2011 10:57:19 virt-manager 2366] DEBUG (engine:465) window counter decremented to 1
[Thu, 26 May 2011 10:57:21 virt-manager 2366] DEBUG (engine:461) window counter incremented to 2
[Thu, 26 May 2011 10:57:21 virt-manager 2366] DEBUG (console:921) Starting connect process for proto=vnc trans=None connhost=localhost connuser=None connport=None gaddr=127.0.0.1 gport=5900 gsocket=None
[Thu, 26 May 2011 10:57:21 virt-manager 2366] DEBUG (console:808) Viewer disconnected
[Thu, 26 May 2011 10:57:28 virt-manager 2366] DEBUG (engine:465) window counter decremented to 1

```

---

### Post by kevpatts on 2011-05-26
Strangely enough, if I install xvncviewer and run "xvncviewer 127.0.0.1" I can connect to the VM! Don't know how this would work with multiple VMs running though, what ports would be used for example.

---

### Post by kevpatts on 2011-06-08
Anyone else having this problem?

---

### Post by konslik on 2011-08-12
Hi kevpatts,

I seem to have exactly the same problem. Googling was no help - somebody blames zsh for this (ridiculous), but your post was on the top of my googly answers.

But ... it seems like some relatively benign fuckup with the timing/repeats/whatever virt-manager got compiled in.

A silly workaroung (for me) is to close the "view" window after hitting "run". And then opening the "view" once more connects me with the VM without problems. It'd be consistent with your vncviewer findings.

If I do it fast enough, I have still my grub menu (set to 4 secs) and can work almost if nothing screwy was happening.
Such acrobatics shouldn't be needed, but I have no idea, how to *really get noticed* in the shiny ubuntu world.

So maybe my post helps (hopefully you and maybe someone will notice and fix it).

Cheers

---

### Post by rakesh_roshan on 2011-09-24
Thanks closing the window and reopening it worked, thanks a lot :)

---

