---
title: "KVM - Moving Guest To New Host - Cannot fix IP in Host"
date: 2024-04-14
forum: Virtualisation
---

### Post by Alan5127 on 2024-04-14
Hi All,

i am trying to move a VM from one host to another - this is just a test for now, to make sure I know how to do it later when required.

I have successfully moved the guest VHD (qcow2) over, and exported and imported the XML, so the VM appears on the new host, and boots up fine.

It gets an IP address (using DHCP).

However, when I try to fix its IP using the hosts 'default' network, I get the error:

```
error: XML error: Cannot use host name 'VM_Name' in network 'default'
```

where VM_Name is the hostname of the VM.

I am trying to do this, by running:

```
virsh net-edit default
```

The following is what appears in the editor (prior to me editing):

```
<network>
  <name>default</name>
  <uuid>92dfe069-1308-4029-8177-1259cd80c444</uuid>
  <forward mode='nat'/>
  <bridge name='virbr0' stp='on' delay='0'/>
  <mac address='52:54:00:e3:4a:cf'/>
  <ip address='192.168.122.1' netmask='255.255.255.0'>
    <dhcp>
      <range start='192.168.122.200' end='192.168.122.249'/>
      <host mac='52:54:00:2a:b6:67' name='ZZ-Test-Debian-12-5-0-20240414' ip='192.168.122.179'/>
    </dhcp>
  </ip>
</network>

```

The 'ZZ-Test-Debian' VM is one I created in the new host after setting it up, and it works fine, along with getting its fixed IP as shown.

When I try to add this line (immediately below the one for the ZZ-Test-Debian guest):

```
<host mac='52:54:00:a3:ce:8c' name='VM_Name' ip='192.168.122.24'/>
```

when I write the change, and exit the editor, I then get the error as above:

```
error: XML error: Cannot use host name 'VM_Name' in network 'default'
```

Maybe I am missing something obvious, but the fixed IP (192.168.122.24) is outside the DHCP allocation range (192.168.122.200 to 192.168.122.249), the MAC address is correct, and changing the hostname does not seem to make any difference.

My guess is that something that came over from the source host / XML definition file, is causing the problem, but I am not sure what.

Any suggestions are welcome :-)

Thanks,

Alan.

---

### Post by Alan5127 on 2024-04-14
Apologies - I was being stupid.

I had not de-activated the network link in the guest.  Just in case anyone else runs into this issue, I solved it by opening the Virtual Machine Manager, selecting the VM, and viewing 'Details', clicking on the NIC, and un-ticking 'Link State - Active'.

Once I did that, the 'virsh net-edit' as above worked fine, and the guest booted up with the correct fixed IP.

Thanks,

Alan.

---

### Post by TheFu on 2024-04-15
If this thread is solved, please use the Thread Tools button to mark it that way, so people looking to help don't waste time.
It is also easy for people looking for answers to search for SOLVED threads, so they will find the answer they seek quicker.

BTW, I've never attempted to specify a static IP in the XML.  I always specify the bridge or passthru NIC device, then inside the VM OS, set the static IP like it was a physical system.  I don't use NAT very often. Not much use for my needs.

---

### Post by MAFoElffen on 2024-04-16
+1 -- Static IP in the network settings of the VM's OS itself.

---

