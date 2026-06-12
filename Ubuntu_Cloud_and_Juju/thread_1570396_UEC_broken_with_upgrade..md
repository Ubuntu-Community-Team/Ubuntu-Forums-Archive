---
title: "UEC broken with upgrade."
date: 2010-09-08
forum: Ubuntu Cloud and Juju
---

### Post by pnunn on 2010-09-08
Hi guys,

I've been directed here from the Meerkat forum...

I just upgraded my UEC cloud to meerkat to try and use the eucalyptus 2.0 tools that are installed within it (as I couldn't find them in a 10.04 package).

The install appears to have gone OK, but now my cloud in broken..

I can't seem to register any clusters even though the logs seem to indicate that they are working OK and are being seen by the CC.

When I try and log into the front end on the CC I get an error:

"The call failed on the server; see server logs for details"

I've looked in the logs and can't really see anything that makes sense, however, when I do a

euca-describe-clusters

I get..

Traceback (most recent call last):
File "/usr/sbin/euca-describe-clusters", line 4, in <module>
from euca_admin.clusters import Cluster
ImportError: No module named euca_admin.clusters

and other describe-* commands return similar problems. This looks like an issue to me.. but I'm not sure where to start looking to try get tis going again.

I have got around the front end error by resetting my password, but I still can't seem to register the nodes.  There are no "VM Types" on the configuration page either but, I'm assuming that this is because of the nodes not being registered correctly.

The odd thing is that when I do a

sudo euca_conf --no-rsync --discover-nodes

The two node controllers are discovered, but they are reported by IPV6 address rather that IPV4 as they were in UEC 1.6. Is that causing the issues?

Ta

Peter.

---

### Post by pnunn on 2010-09-09
Testing testing 123? Anyone home??

---

### Post by Rusty au Lait on 2010-09-09
I'd like to help. I have not tried nor downloaded Meerkat yet. I assume installs are fresh and clean. I'll try looking at it today. Is the UEC install the same as Lucid (from the CD/live or must you install UEC over an existing system)?

---

### Post by baboli on 2010-09-09
I have never tried Meerkat but I read that it is officially released in October 2010, maybe you have a RC? 
In any case, I would never upgrade and will just do a new install. Please let us know how it goes.
Vahid.

---

### Post by pnunn on 2010-09-10
OK, thanks guys.

These were done as updates to the existing systems, so I will blow them away and try again.

It seems the CC and Walrus is up OK but I simply cannot get the nodes to register.

Peter.

---

### Post by pnunn on 2010-09-14
OK, this is totally broken.

I have just re-installed the CC and NC's afresh from the 10.10 disk and I shill have no nodes registered.

The front end seems to work, although I can't download any images from the store (it comes up with "Bad request signature" on any image I try to install).

When I do  sudo euca_conf --no-rsync --discover-nodes on the CC I get the nodes appearing with IP6 addresses (most of the time, its not consistent) but the keys cannot be installed, even though I tried adding the credentials manually (doesn't seem to be setting up the eucalyptus user correctly).

I tried disabling IP6 on the CC and NC's, but now I don't even see the nodes when I don the discover-nodes.

Did anyone actually test this before pushing out the Beta?  Is there a way I can upgrade a 10.04 (which mostly works) to 2.0 without breaking it? Or.. do I give up on UEC entirely and go to a supported (by eucalyptus) distro?

I'm really starting to take some heat on this now.. any help would be GREATLY appreciated.

Peter.

---

### Post by Rusty au Lait on 2010-09-14
Peter,
What a bummer. Here are a few guesses: using euca_conf try:
   --deregister-nodes "host host ..."   remove nodes from EUCALYPTUS
   --deregister-cluster <clustername>      remove cluster from EUCALYPTUS
   --register-cluster <clustername> <host> add new cluster to EUCALYPTUS
You reinstalled the CC and NC, but you did not say anything about the CLC. It might still be holding on to something.
Keep us posted.

---

### Post by pnunn on 2010-09-14
OK, slow progress...

I've managed to get the nodes registered using 

euca_conf --register-nodes "192.168.123.82"

I have now restored my bukkits and volumes from the 1.6 version, BUT, how do  I register the images in these bukkits.  The xml file is now in some compressed? format in the bukkit so I can't use register-image etc...

Ta.

Peter.

---

### Post by pnunn on 2010-09-14
OK, I've decided to give up on the restore of the images (not that important anyway).

I've managed to install an image from the store (had to log in as Admin to do it) and now have an image running... but I can't connect to it.. sigh.

I can ping it from the CC (not from elsewere in the network) but I can't connect to it.

ssh -vvv -i id-pnunn ubuntu@192.168.124.101
OpenSSH_5.5p1 Debian-4ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.124.101 [192.168.124.101] port 22.
debug1: Connection established.
debug3: Not a RSA1 key file id-pnunn.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype


Been looking all over google for this one, but turning up a blank.

---

### Post by pnunn on 2010-09-15
OK.. this is still crazy.. got the keys working by removing the old keys from authorized_keys.. but now I can't see any volumes attached to the running instance.

It says its attached, but it doesn't appear in /dev/

Now what??

---

### Post by pnunn on 2010-09-15
Anybody??? Has anyone actually got this working??

I have found some information on the eucalyptus forum that seems to relate 

[http://open.eucalyptus.com/forum/ebs-volume-not-seen-linux-instance](http://open.eucalyptus.com/forum/ebs-volume-not-seen-linux-instance)

but no joy with my setup.

I can't see any sign of the disk hitting the instance in dmesg or anywhere else.

Who can I talk to about this?? Please??

---

### Post by pnunn on 2010-09-16
OK I give up.  Looks like no one is interested.  UEC on 10.10 is broken. STAY AWAY... I now can't log in to any instance running (ssh connection refused).  I had none of these issues with 10.04.  Looks like I roll back, or try some other distro for this.

Peter.

---

### Post by pallaire on 2011-03-14
Hello PNUNN,

I am having the same difficulties that you were having ... did you find a solution ? 

I am at the same point ... going back to 10.04 LTS or starting from scratch with the sources.

My current state is that I have a NC installed, which is registered on the CC, but from the NC machine (not an instance) I cant access the web at all!

So, on the NC, I cant do 

apt-get update
apt-get install ntp
apt-get upgrade eucalyptus


Its like the iptables is not working on the CC ... I have never had this problem on 10.04 ... but I need to upgrade to euca 2.x

thanks

---

### Post by pallaire on 2011-03-29
Hello PNUNN,

I found some problems with 10.10 ... but I was able to debug enough to have a working setup. So may be you will be interested in what I found ... 


1. Images using SCSI are not working! 
2. Qcow2 images are not working in 10.10 ... they were in 10.04 LTS
3. Splited front end setup is not working in 10.10 ... it was in 10.04 LTS

About problem #1 and #2: 

All my problems were happening with my Windows XP image, it was working fine in 10.04 LTS, but I could not connect to them in 10.10! At first glance, I thought it was an iptables problem, but in fact, the problem was that the instance was never really running. Windows was stuck in its DOS mode telling me it could not boot. This error was not written to the console output, so if I ever did a "euca-get-console-output", I would get nothing. To find that error I had to debug directly on the node. I installed a minimal xorg on the NC and debugged following this procedure: [http://cssoss.wordpress.com/2010/05/04/ueceucalyptus-debugging-instances/](http://cssoss.wordpress.com/2010/05/04/ueceucalyptus-debugging-instances/) so on the NC were my instance was trying to start I would attach vncviewer to the instance! 

Bug #1 ... they way that eucalyptus/libvirt create the SCSI device in 10.10 ... is really more complicated than any tutorial out there that show you how to create an image. In the tutorial, the scsi drive parameter is: -drive file=./disk,if=scsi,boot=on,index=1

The instance will receive :  -device lsi,id=scsi0,bus=pci.0,addr=0x4 -device scsi-disk,bus=scsi0.0,scsi-id=0,drive=drive-scsi0-0-0,id=scsi0-0-0 -drive file=./disk,if=none,id=drive-scsi0-0-0,boot=on,format=raw 

Somewhere in this huge line, Windows Scsi driver is not working, it won’t boot with that, I tried this line manually with kvm, and I can reproduce the bug.

How to go around this bug? Use the IDE interface instead. To do that you will need to modify this file : /usr/share/eucalyptus/gen_kvm_libvirt_xml

Change that : <target dev='sda'/>
To that :  <target dev='hda'/>


Bug #2 ... After fixing the bug #1, I was still not able to boot, I found the qcow2 format images are not supported in this version of libvirt/qemu/kvm !!!! How to go around that? Convert your image back to raw. 

qemu-img -f qcow2 -O raw disk disk.raw

Then re-bundle/upload/register your image and it will work!

One way to validate that your cloud is working fine is to use an image created by Ubuntu, you can find them there: [http://uec-images.ubuntu.com/](http://uec-images.ubuntu.com/)  Once you know that the cloud is working you can try to make other images work on it.


Bug #3 ... I have not found a fix for this bug on 10.10 (this bug does not exist in 10.04), if you put the CLC+Walrus on one server, the CC+SC on another server, then a NC (or many) on another machine ... the instances won’t be able to talk to the walrus to download the files (kernel,boot,image) so the instances will be pending forever! There is something wrong with the way 10.10 Clusters manage the iptables, the NC cannot talk to the walrus, and it can only talk to the CC machine. You won’t see this bug if you follow every tutorials out there, because they are all a copy of the same tutorial that was made using only one machine as the front end (CLC+Walrus+CC+SC on one computer) Since the NC is limited to talk to the CC's computer, in this setup it’s the same machine as the Walrus, so it is working. I will try to contact eucalyptus about that.

---

