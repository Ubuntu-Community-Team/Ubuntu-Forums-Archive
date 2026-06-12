---
title: "UEC instances pending - never change"
date: 2011-03-16
forum: Ubuntu Cloud and Juju
---

### Post by rabinnh on 2011-03-16
UEC 10.10

I've Googled and read everything I can about this issue for 3 days now.  I've completely uninstalled the CC and the Node a number of times, but I keep running into the same issue; whenever I start an instance, it always stays in the pending state, even though it gets a valid public IP from the Cloud's pool.

I have 2 machines, a Cloud Controller with all services (cloud, walrus, etc) and a Node Controller.  The Node Controller is a brand new i5 with 4GB of memory bought explicitly for testing UEC.  The node controller is a laptop with 2GB of memory.

I am testing with the pre-packaged 10.04 AMD64 Lucid image in the store, to keep things as simple as possible.

Here is the output of euca-describe-availability-zones verbose

root@hollis-cloud:~# euca-describe-availability-zones verbose
AVAILABILITYZONE	cluster1	192.168.0.170
AVAILABILITYZONE	|- vm types	free / max   cpu   ram  disk
AVAILABILITYZONE	|- m1.small	0003 / 0004   1    192     2
AVAILABILITYZONE	|- c1.medium	0003 / 0004   1    256     5
AVAILABILITYZONE	|- m1.large	0001 / 0002   2    512    10
AVAILABILITYZONE	|- m1.xlarge	0001 / 0002   2   1024    20
AVAILABILITYZONE	|- c1.xlarge	0000 / 0001   4   2048    20


None of the logs on either machines show that there are any errors, which is frustrating.  In viewing everything that I can find, I have tried the following:

1) Spawning instances from Hybridfox 
2) Spawning instances using a user account using euca2ools from a third machine
3) Spawning instances from the CC.
4) Spawning instances as small and as medium

All with the same result; the instance gets assigned a public IP almost immediately and then hangs on pending.

There is question that I think may be affecting this, and that I don't quite understand.  We already have a DHCP server on the network, so the CC's dhcp controller doesn't start.  However, since it is assigning the public IP successfully, that doesn't appear to matter.  However, I am not sure if that is just telling me that is the IP that WILL be assigned when the machine comes up, or if it is already assigned.

Could that be the issue?

Thanks to anyone that can help.

---

### Post by rabinnh on 2011-03-16
I changed the network type to SYSTEM, but there is no change in behavior.  This is the output of my nc.log.  Looks great . . .

 doStartNetwork() invoked
[Wed Mar 16 14:18:08 2011][001952][EUCAINFO  ] StartNetwork(): SUCCESS return from vnetStartNetwork 0
[Wed Mar 16 14:18:08 2011][001952][EUCAINFO  ] StartNetwork(): done
[Wed Mar 16 14:18:08 2011][001952][EUCAINFO  ] doRunInstance() invoked (id=i-388C0683 cores=1 disk=5 memory=256)
[Wed Mar 16 14:18:08 2011][001952][EUCAINFO  ]                          image=emi-DC971058 at [http://192.168.0.170:8773/services/Walrus/image-store-1300221854/image.manifest.xml](http://192.168.0.170:8773/services/Walrus/image-store-1300221854/image.manifest.xml)
[Wed Mar 16 14:18:08 2011][001952][EUCAINFO  ]                          krnel=eki-F2A810D1 at [http://192.168.0.170:8773/services/Walrus/image-store-1300221854/kernel.manifest.xml](http://192.168.0.170:8773/services/Walrus/image-store-1300221854/kernel.manifest.xml)
[Wed Mar 16 14:18:08 2011][001952][EUCAINFO  ]                          rmdsk=eri-071D113E at [http://192.168.0.170:8773/services/Walrus/image-store-1300221854/ramdisk.manifest.xml](http://192.168.0.170:8773/services/Walrus/image-store-1300221854/ramdisk.manifest.xml)
[Wed Mar 16 14:18:08 2011][001952][EUCAINFO  ]                          vlan=-1 priMAC=d0:0d:38:8C:06:83 privIp=0.0.0.0
[Wed Mar 16 14:18:08 2011][001952][EUCADEBUG ] state change for instance i-388C0683: Unknown -> Staging (Pending)
[Wed Mar 16 14:18:08 2011][001952][EUCAINFO  ] network started for instance i-388C0683
[Wed Mar 16 14:18:08 2011][001952][EUCAINFO  ] retrieving images for instance i-388C0683 (disk limit=5120MB)...
[Wed Mar 16 14:18:08 2011][001952][EUCAINFO  ] verifying cached file in /var/lib/eucalyptus/instances//eucalyptus/cache/eki-F2A810D1/kernel...
[Wed Mar 16 14:18:08 2011][001952][EUCAINFO  ] walrus_request(): downloading /tmp/walrus-digest-5kwGu5
[Wed Mar 16 14:18:08 2011][001952][EUCAINFO  ]                   from [http://192.168.0.170:8773/services/Walrus/image-store-1300221854/kernel.manifest.xml](http://192.168.0.170:8773/services/Walrus/image-store-1300221854/kernel.manifest.xml)
[Wed Mar 16 14:18:08 2011][001952][EUCADEBUG ] walrus_request(): writing GET output to /tmp/walrus-digest-5kwGu5 on 'Wed Mar 16 14:18:08 2011'
[Wed Mar 16 14:18:09 2011][001952][EUCADEBUG ] walrus_request(): wrote 3506 bytes in 1 writes
[Wed Mar 16 14:18:09 2011][001952][EUCAINFO  ] walrus_request(): saved image in /tmp/walrus-digest-5kwGu5
[Wed Mar 16 14:18:09 2011][001952][EUCAINFO  ] vrun(): [cp -a /var/lib/eucalyptus/instances//eucalyptus/cache/eki-F2A810D1/kernel /var/lib/eucalyptus/instances//admin/i-388C0683/kernel]
[Wed Mar 16 14:18:09 2011][001952][EUCAINFO  ] walrus_request(): downloading /var/lib/eucalyptus/instances//admin/i-388C0683/ramdisk-digest
[Wed Mar 16 14:18:09 2011][001952][EUCAINFO  ]                   from [http://192.168.0.170:8773/services/Walrus/image-store-1300221854/ramdisk.manifest.xml](http://192.168.0.170:8773/services/Walrus/image-store-1300221854/ramdisk.manifest.xml)
[Wed Mar 16 14:18:09 2011][001952][EUCADEBUG ] walrus_request(): writing GET output to /var/lib/eucalyptus/instances//admin/i-388C0683/ramdisk-digest on 'Wed Mar 16 14:18:09 2011'
[Wed Mar 16 14:18:09 2011][001952][EUCADEBUG ] walrus_request(): wrote 3509 bytes in 1 writes
[Wed Mar 16 14:18:09 2011][001952][EUCAINFO  ] walrus_request(): saved image in /var/lib/eucalyptus/instances//admin/i-388C0683/ramdisk-digest
[Wed Mar 16 14:18:09 2011][001952][EUCAINFO  ] downloading and preparing image into /var/lib/eucalyptus/instances//admin/i-388C0683/ramdisk...
[Wed Mar 16 14:18:09 2011][001952][EUCAINFO  ] walrus_request(): downloading /var/lib/eucalyptus/instances//admin/i-388C0683/ramdisk
[Wed Mar 16 14:18:09 2011][001952][EUCAINFO  ]                   from [http://192.168.0.170:8773/services/Walrus/image-store-1300221854/ramdisk.manifest.xml](http://192.168.0.170:8773/services/Walrus/image-store-1300221854/ramdisk.manifest.xml)
[Wed Mar 16 14:18:09 2011][001952][EUCADEBUG ] walrus_request(): writing GET/GetDecryptedImage output to /var/lib/eucalyptus/instances//admin/i-388C0683/ramdisk on 'Wed Mar 16 14:18:09 2011'
[Wed Mar 16 14:18:12 2011][001952][EUCADEBUG ] doDescribeResource() invoked
[Wed Mar 16 14:18:12 2011][001952][EUCADEBUG ] doDescribeInstances() invoked
[Wed Mar 16 14:18:12 2011][001952][EUCADEBUG ] doDescribeInstances(): instanceId=i-388C0683 publicIp=0.0.0.0 privateIp=0.0.0.0 mac=d0:0d:38:8C:06:83 vlan=-1 networkIndex=-1 
[Wed Mar 16 14:18:18 2011][001952][EUCADEBUG ] doDescribeResource() invoked
[Wed Mar 16 14:18:19 2011][001952][EUCADEBUG ] doDescribeInstances() invoked
[Wed Mar 16 14:18:19 2011][001952][EUCADEBUG ] doDescribeInstances(): instanceId=i-388C0683 publicIp=0.0.0.0 privateIp=0.0.0.0 mac=d0:0d:38:8C:06:83 vlan=-1 networkIndex=-1 
[Wed Mar 16 14:18:25 2011][001952][EUCADEBUG ] doDescribeResource() invoked
[Wed Mar 16 14:18:25 2011][001952][EUCADEBUG ] doDescribeInstances() invoked
[Wed Mar 16 14:18:25 2011][001952][EUCADEBUG ] doDescribeInstances(): instanceId=i-388C0683 publicIp=0.0.0.0 privateIp=0.0.0.0 mac=d0:0d:38:8C:06:83 vlan=-1 networkIndex=-1 

The cc.log shows no errors either.  Maybe I am assuming that the "canned" images will work, when in fact there is an issue with them?

---

### Post by rabinnh on 2011-03-16
Ok, configured as SYSTEM, *some* of the canned UEC images run.  However, their IP address doesn't show up in "euca-describe-instances" even though a look at the DHCP server shows that they have requested and received an IP address.

Furthermore, I can ping the IP address, but no other network services are running.

I thought that I was correctly checking the console output by using "euca-get-console-output", which only gave me the instance ID and a timestamp, but if I actually SSH into the node controller and "cat console.log", I can see that the instance booted fine but is hung on 

"* Waiting for EC2 meta-data service".

More research indicates that the script that is being run might pause for a 30-60 minutes if it is not being running on an EC2 compatible cloud - but it IS being run on Maverick UEC.

So here is a short summary of what I have found:

* You can only download images from the store when logged in as Admin.
* BUG: You cannot download images logged in as any other administrator - you get "Bad request signature" in response.
* POTENTIAL BUG: You cannot launch UEC images as Admin, you can only get them to run as a different user (I have experienced this, and in my research so have many others).
* Using MANAGED-VLAN mode, my instances stay in "PENDING" mode forever, although they seem to get assigned IP addresses - again Google this and you will get an amazing number of hits of people experiencing this issue.
* Using SYSTEM mode, my instances get assigned an IP address from the DHCP server, but it is not reported by euca-describe-instances for a long, long time.
* Instance hangs at "Waiting for EC2 meta-data service"

UEC looks like it would be great, and I have to believe that it works for a lot of people, but the testing matrix must be really small, because a lot of people are having issues.  Eucalyptus itself is poorly documented and appears to be riddled with bugs and gotchas.  Their forums have hundreds of people reporting the same issues.  Layering UEC on top adds another small layer of complexity, whereas Canonical usually makes things easier.

Bottom line, I don't see the advantage of using UEC over just installing Eucalyptus on its own if it doesn't make things easier.  OTOH, I would love to help make it better because I love Ubuntu, but I am really wonder if Eucalyptus is ready for prime-time, and there is nothing Canonical can do about that.

If anyone has more insight on how to make things go smoother, I would love to hear it.

---

### Post by rabinnh on 2011-03-17
I ditched the Maverick UEC and went back to Lucid UEC.  I did NOT update Eucalyptus after the install, so I am using Eucalyptus 1.6.2.

I had everything up and working in an hour on the same boxes from scratch.

I think a good part of the problem is that the bundled images in the Store don't seem to work well on Eucalyptus 2.

---

