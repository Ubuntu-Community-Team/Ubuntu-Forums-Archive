---
title: "Posible iSCSI problem"
date: 2011-04-22
forum: Server Platforms
---

### Post by TheR on 2011-04-22
Ubuntu 10.4 on all servers.

I am using ubuntu for my KVM servers connected with 10g Ethernet to ubuntu based iSCSI server. Everything seems to work OK for almost a year now. The only problem (which seems like it is not critical) is that at the night, when I am doing my LVM snapshots and making copies of virtual machines, once or twice a week I get this error message on one of windows machine system log:

Program: Viostor
Error id: 9
Description: The device, \Device\Scsi\viostor2, did not respond within the timeout period. 

It looks like iSCSI server was to busy during snapshot and virtualized server got timeout. HW shouldn't be problems since all servers are using i7 xeons.

Can you suggest iSCSI server or maybe client tweaking to avoid this?


by
TheR

---

### Post by usatonycuba on 2011-04-22
> **TheR said:**
> ...is that at the night, when I am doing my LVM snapshots and making copies of virtual machines...
Have you change the Default Values in ietd.conf of *[COLOR="Gray"]MaxRecvDataSegmentLenth[/COLOR]* and/or *[COLOR="Gray"]MaxXmitDataSegmentLenth[/COLOR]*..?

---

### Post by TheR on 2011-04-22
All my ietd.conf settings are still commented out. So:

  #MaxRecvDataSegmentLength 8192          # Max data per PDU to receive
  #MaxXmitDataSegmentLength 8192          # Max data per PDU to transmit

by
TheR

---

### Post by usatonycuba on 2011-04-22
> **TheR said:**
> All my ietd.conf settings are still commented out. So:

  #MaxRecvDataSegmentLength 8192          # Max data per PDU to receive
  #MaxXmitDataSegmentLength 8192          # Max data per PDU to transmit

by
TheR
8192 are the default values....   **Edited**: why not to move them to a little higher value...?.. (If you really are expecting higher values &#8203;&#8203;due to your  work-processes)..?

PD: My doubt is due, because this happens exactly when you're doing (LVM snapshots and making copies of virtual machines) .. may be an overload ( not due to your i7 xeons) .. but the parameters of the file ietd.conf on the ability/capacity of Data-Lenth..?

**[COLOR="Sienna"]Carefully [/COLOR]**.. remember that each value change in a node Must Be the Same at Other End

---

### Post by TheR on 2011-04-22
> **usatonycuba said:**
> 
PD: My doubt is due, because this happens exactly when you're doing (LVM snapshots and making copies of virtual machines) .. may be an overload ( not due to your i7 xeons) .. but the parameters of the file ietd.conf on the ability/capacity of Data-Lenth..?

**[COLOR="Sienna"]Carefully [/COLOR]**.. remember that each value change in a node Must Be the Same at Other End

This made me think maybe snapshoting is using block that is too large. I am doing dd with bs=64k, simply because it is faster than default. 

I will lower bs to 8k and see if there is any difference.

by
TheR

---

### Post by TheR on 2011-04-23
> **TheR said:**
> This made me think maybe snapshoting is using block that is too large. I am doing dd with bs=64k, simply because it is faster than default. 

I will lower bs to 8k and see if there is any difference.


Nope. No difference. Still got one error.

by
TheR

---

### Post by usatonycuba on 2011-04-23
When using open-iscsi you can change few parameters to improve it... between  (initiator and target).. as you said .. there is Ubuntu 10.4 on all servers...  you can get the the whole parameter list (at the indicator side) typing *[COLOR="DarkRed"]iscsiadm -m session -P 2[/COLOR]*   result will give you something like:

```
************************
Negotiated iSCSI params:
************************
HeaderDigest: None
DataDigest: None
MaxRecvDataSegmentLength: 262144
MaxXmitDataSegmentLength: 8192
FirstBurstLength: 65536
MaxBurstLength: 262144
ImmediateData: Yes
InitialR2T: No
MaxOutstandingR2T: 1
```

and here its ...outlined  how to Sets  the  maximum  data  segment  length that can be received/sent

```
       [MaxRecvDataSegmentLength <value>]
              Optional.  Sets  the  maximum  data  segment  length that can be
              received. The <value> should be set to multiples  of  PAGE_SIZE.
              Currently  the  maximum  supported value is 64 * PAGE_SIZE, e.g.
              262144 if PAGE_SIZE is 4kB. Configuring  too  large  values  may
              lead to problems allocating sufficient memory, which in turn may
              lead to SCSI commands timing out  at  the  initiator  host.  The
              default value is 8192.

       [MaxXmitDataSegmentLength <value>]
              Optional. Sets the maximum data segment length that can be sent.
              The    <value>    actually    used    is    the    minimum    of
              MaxXmitDataSegmentLength    and   the   MaxRecvDataSegmentLength
              announced by  the  initiator.  The  <value>  should  be  set  to
              multiples of PAGE_SIZE. Currently the maximum supported value is
              64 * PAGE_SIZE, e.g. 262144 if PAGE_SIZE is 4kB. Configuring too
              large  values may lead to problems allocating sufficient memory,
              which in turn may lead  to  SCSI  commands  timing  out  at  the
              initiator host. The default value is 8192.
```

It may help

---

### Post by TheR on 2011-04-24
> **usatonycuba said:**
> When using open-iscsi you can change few parameters to improve it... between  (initiator and target).. as you said .. there is Ubuntu 10.4 on all servers...  you can get the the whole parameter list (at the indicator side) typing *[COLOR="DarkRed"]iscsiadm -m session -P 2[/COLOR]*   result will give you something like:

```
************************
Negotiated iSCSI params:
************************
HeaderDigest: None
DataDigest: None
MaxRecvDataSegmentLength: 262144
MaxXmitDataSegmentLength: 8192
FirstBurstLength: 65536
MaxBurstLength: 262144
ImmediateData: Yes
InitialR2T: No
MaxOutstandingR2T: 1
```

and here its ...outlined  how to Sets  the  maximum  data  segment  length that can be received/sent

```
       [MaxRecvDataSegmentLength <value>]
              Optional.  Sets  the  maximum  data  segment  length that can be
              received. The <value> should be set to multiples  of  PAGE_SIZE.
              Currently  the  maximum  supported value is 64 * PAGE_SIZE, e.g.
              262144 if PAGE_SIZE is 4kB. Configuring  too  large  values  may
              lead to problems allocating sufficient memory, which in turn may
              lead to SCSI commands timing out  at  the  initiator  host.  The
              default value is 8192.

       [MaxXmitDataSegmentLength <value>]
              Optional. Sets the maximum data segment length that can be sent.
              The    <value>    actually    used    is    the    minimum    of
              MaxXmitDataSegmentLength    and   the   MaxRecvDataSegmentLength
              announced by  the  initiator.  The  <value>  should  be  set  to
              multiples of PAGE_SIZE. Currently the maximum supported value is
              64 * PAGE_SIZE, e.g. 262144 if PAGE_SIZE is 4kB. Configuring too
              large  values may lead to problems allocating sufficient memory,
              which in turn may lead  to  SCSI  commands  timing  out  at  the
              initiator host. The default value is 8192.
```

It may help

Thank you. So you are suggesting lowering MaxRecvDataSegmentLength parameter. 

According to usatonycuba this could be a problem since parameters should be changed both on client and initiator.

It is going to be a bit hard since this is working system with 9 active virtualized servers. I do plan to make one software update on iscsi server soon (uptime is close to 200 days now) but am waiting for new usb keys with cache so updating should be a lot faster.

by
TheR

---

### Post by usatonycuba on 2011-04-24
> **TheR said:**
> Thank you. So you are suggesting lowering MaxRecvDataSegmentLength parameter. 

According to usatonycuba this could be a problem since parameters should be changed both on client and initiator.

It is going to be a bit hard since this is working system with 9 active virtualized servers. I do plan to make one software update on iscsi server soon (uptime is close to 200 days now) but am waiting for new usb keys with cache so updating should be a lot faster.

by
TheR
run that command too, at the target side, take a look what you get ```
iscsiadm -m session -P 2
```

MaxRecvDataSegmentLength will be, the maximum size of data that the initiator can receive in just one iSCSI PDU... So, whatever the initiator is able to receive and handle, it will be also what the target is permitted to send

---

### Post by TheR on 2011-04-29
> **TheR said:**
> Nope. No difference. Still got one error.

by
TheR

Using bs=4k seems to help. I have had three backups without hickup now.

Backup window has gone from 1.5 hours to 2 hours which is acceptable.

Thank you guys for ideas.

by
TheR

---

