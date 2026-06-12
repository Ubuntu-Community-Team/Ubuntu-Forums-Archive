---
title: "Ubuntu Enterprise Cloud - Single point of failure??"
date: 2010-02-17
forum: Server Platforms
---

### Post by fveggerby on 2010-02-17
Hi

I was wondering.......

According to [https://help.ubuntu.com/community/UEC/PackageInstallSeparate](https://help.ubuntu.com/community/UEC/PackageInstallSeparate) in the Glosary section, there should be only 1 Cloud Controller (CLC) and, as I read the page, only 1 Walrus Controller. (WS3)

What would happen is 1 of these chrash?

Can the cloud still run without them?
Or will the whole thing go down, until a new CLC or WS3 is up?

This also means that backup of these is essential.
Especially the CLC.

What about Storage?
Is data replicated around the disks?
Can Storage Controller make/control some Raid config of the different disks.
Or is it nessecary to use some kind of SAN for that?

My main concern is the CLC!
Will the Cloud still run, if CLC is shut down/chrashed?

It would be very nice to have a Backup/Mirror-CLC and Backup/Mirror-WS3. :)

Just thought of the Cluster Controller.
Is this also a SPOF?

FV

---

### Post by john-boy on 2010-02-17
From my limited experience of installing UEC on a couple of spare PCs in the last week or two, I would say:

If your cloud controller/cluster controller/walrus controller goes down then you have lost your cloud and everything that runs on it until they allcome back up...I didn't find anything about having a cluster of Controllers to provide resilience. If you follow the installation instructions from CD I think you end up with those 3 controllers on the same hardware server anyway.

Have you found any recommendations for backing up the UEC?

I'm no expert mind and this is just my two cents worth so if anyone can offer any more valuable information then please do!

---

### Post by fveggerby on 2010-02-17
thanks.
As I thought, Single point of failure. :(
This is really bad.


If you look at the link in my post, there's the how to install the different controllers on different hardware.
But then you'll have 3 SPOF's :(

A solution COULD be:
2 VMWare ESX or other, with Vcenter server.
Both ESX is running failover for the intance "UEC Controller"
Then you will have virtual running on top of virtual.
I have no idea of it is doable. :)

The Heartbeat/DRDB solution would be a NoSPOF solution.
Much better.
And GlusterFS as a SAN.

---

