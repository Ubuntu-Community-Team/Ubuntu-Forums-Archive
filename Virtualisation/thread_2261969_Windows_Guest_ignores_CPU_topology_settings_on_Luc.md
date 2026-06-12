---
title: "Windows Guest ignores CPU topology settings on Lucid host"
date: 2015-01-22
forum: Virtualisation
---

### Post by karaluh on 2015-01-22
I try to assign 8 host cores to Windows 2003 Server Standard guest. Because this OS version has a limit of 4 sockets, I have to change the CPU topology. My guest definition:
```
  <vcpu>8</vcpu>
  <cpu match='minimum'>
    <model>core2duo</model>
    <topology sockets='4' cores='1' threads='2'/>
  </cpu>
```
doesn't work as expected. I should have 4 CPUs in the Device Manager and 8 CPU charts in Task Manager, but I have the opposite. And no matter what numbers I set in the topology, the guest always detects 8 sockets. What am I doing wrong?

---

### Post by Doug S on 2015-01-23
If I do the same as you did, I get the same result as you. Note that my host is an Ubuntu 14.04 server.
However, if I do this (and "virsh edit" forces some of this upon exit, so it cann't look exactly like what you did):```
  [COLOR=#ff0000]<vcpu placement='static'>8</vcpu>[/COLOR]
  <os>
    <type arch='x86_64' machine='pc-i440fx-1.7'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
[COLOR=#ff0000]  <cpu mode='custom' match='minimum'>
    <model fallback='allow'>core2duo</model>
    <topology sockets='4' cores='[/COLOR]2[COLOR=#ff0000]' threads='2'/>
  </cpu>[/COLOR]
```Then I get what I think you wanted:```
doug@desk-dev:~$ [COLOR=#ff0000]cat /proc/cpuinfo | grep "core id"[/COLOR]
core id         : 0
core id         : 1
core id         : 0
core id         : 1
core id         : 0
core id         : 1
core id         : 0
core id         : 1
doug@desk-dev:~$ [COLOR=#ff0000]cat /proc/cpuinfo | grep "cpu cores"[/COLOR]
cpu cores       : 2
cpu cores       : 2
cpu cores       : 2
cpu cores       : 2
cpu cores       : 2
cpu cores       : 2
cpu cores       : 2
cpu cores       : 2
doug@desk-dev:~$ [COLOR=#ff0000]cat /proc/cpuinfo | grep "physical id"[/COLOR]
physical id     : 0
physical id     : 0
physical id     : 1
physical id     : 1
physical id     : 2
physical id     : 2
physical id     : 3
physical id     : 3
```My guest VM is an Ubuntu 15.04 desktop

---

### Post by karaluh on 2015-01-29
> **Doug S said:**
> If I do the same as you did, I get the same result as you. Note that my host is an Ubuntu 14.04 server.

None of the settings were supported, so I upgraded to Precise, and now everything works as expected. Thank you.

---

