---
title: "Instance goes from pending to shutting down to terminated??"
date: 2010-09-16
forum: Ubuntu Cloud and Juju
---

### Post by darkksyde on 2010-09-16
Hi,
I am trying to install a private cloud but whenever i go to start an instance, it says pending then shutting down then terminated??
I have attached the logs below
Any help would be appreciated,
Thanks


nc.log
____________
[Fri Sep 17 01:32:35 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:32:39 2010][001119][EUCADEBUG ] doStartNetwork() invoked
[Fri Sep 17 01:32:39 2010][001119][EUCAINFO  ] StartNetwork(): SUCCESS return from vnetStartNetwork 0
[Fri Sep 17 01:32:39 2010][001119][EUCAINFO  ] StartNetwork(): done
[Fri Sep 17 01:32:39 2010][001119][EUCAINFO  ] doRunInstance() invoked (id=i-44F9075D cores=1 disk=2 memory=192)
[Fri Sep 17 01:32:39 2010][001119][EUCAINFO  ]                          image=emi-E0AA107D at [http://192.168.0.90:8773/services/Walrus/image-store-1284658069/image.manifest.xml](http://192.168.0.90:8773/services/Walrus/image-store-1284658069/image.manifest.xml)
[Fri Sep 17 01:32:39 2010][001119][EUCAINFO  ]                          krnel=eki-F6E010F8 at [http://192.168.0.90:8773/services/Walrus/image-store-1284658069/kernel.manifest.xml](http://192.168.0.90:8773/services/Walrus/image-store-1284658069/kernel.manifest.xml)
[Fri Sep 17 01:32:39 2010][001119][EUCAINFO  ]                          rmdsk=eri-0B4E115B at [http://192.168.0.90:8773/services/Walrus/image-store-1284658069/ramdisk.manifest.xml](http://192.168.0.90:8773/services/Walrus/image-store-1284658069/ramdisk.manifest.xml)
[Fri Sep 17 01:32:39 2010][001119][EUCAINFO  ]                          vlan=10 priMAC=d0:0d:44:F9:07:5D pubMAC=d0:0d:44:F9:07:5D
[Fri Sep 17 01:32:39 2010][001119][EUCAINFO  ] network started for instance i-44F9075D
[Fri Sep 17 01:32:39 2010][001119][EUCAINFO  ] retrieving images for instance i-44F9075D (disk limit=2048MB)...
[Fri Sep 17 01:32:39 2010][001119][EUCAINFO  ] walrus_request(): downloading /var/lib/eucalyptus/instances//admin/i-44F9075D/kernel-digest
[Fri Sep 17 01:32:39 2010][001119][EUCAINFO  ]                   from [http://192.168.0.90:8773/services/Walrus/image-store-1284658069/kernel.manifest.xml](http://192.168.0.90:8773/services/Walrus/image-store-1284658069/kernel.manifest.xml)
[Fri Sep 17 01:32:39 2010][001119][EUCADEBUG ] walrus_request(): writing GET output to /var/lib/eucalyptus/instances//admin/i-44F9075D/kernel-digest
[Fri Sep 17 01:32:40 2010][001119][EUCADEBUG ] walrus_request(): wrote 3479 bytes in 1 writes
[Fri Sep 17 01:32:40 2010][001119][EUCAINFO  ] walrus_request(): saved image in /var/lib/eucalyptus/instances//admin/i-44F9075D/kernel-digest
[Fri Sep 17 01:32:40 2010][001119][EUCAINFO  ] downloading and preparing image into /var/lib/eucalyptus/instances//admin/i-44F9075D/kernel...
[Fri Sep 17 01:32:40 2010][001119][EUCAINFO  ] walrus_request(): downloading /var/lib/eucalyptus/instances//admin/i-44F9075D/kernel
[Fri Sep 17 01:32:40 2010][001119][EUCAINFO  ]                   from [http://192.168.0.90:8773/services/Walrus/image-store-1284658069/kernel.manifest.xml](http://192.168.0.90:8773/services/Walrus/image-store-1284658069/kernel.manifest.xml)
[Fri Sep 17 01:32:40 2010][001119][EUCADEBUG ] walrus_request(): writing GET/GetDecryptedImage output to /var/lib/eucalyptus/instances//admin/i-44F9075D/kernel
[Fri Sep 17 01:32:41 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:32:41 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:32:41 2010][001119][EUCADEBUG ] walrus_request(): wrote 4159008 bytes in 351 writes
[Fri Sep 17 01:32:41 2010][001119][EUCAINFO  ] walrus_request(): saved image in /var/lib/eucalyptus/instances//admin/i-44F9075D/kernel
[Fri Sep 17 01:32:41 2010][001119][EUCAINFO  ] vrun(): [cp -a /var/lib/eucalyptus/instances//admin/i-44F9075D/kernel /var/lib/eucalyptus/instances//eucalyptus/cache/eki-F6E010F8/kernel]
[Fri Sep 17 01:32:41 2010][001119][EUCAINFO  ] vrun(): [cp -a /var/lib/eucalyptus/instances//admin/i-44F9075D/kernel-digest /var/lib/eucalyptus/instances//eucalyptus/cache/eki-F6E010F8/kernel-digest]
[Fri Sep 17 01:32:41 2010][001119][EUCAINFO  ] walrus_request(): downloading /var/lib/eucalyptus/instances//admin/i-44F9075D/ramdisk-digest
[Fri Sep 17 01:32:41 2010][001119][EUCAINFO  ]                   from [http://192.168.0.90:8773/services/Walrus/image-store-1284658069/ramdisk.manifest.xml](http://192.168.0.90:8773/services/Walrus/image-store-1284658069/ramdisk.manifest.xml)
[Fri Sep 17 01:32:41 2010][001119][EUCADEBUG ] walrus_request(): writing GET output to /var/lib/eucalyptus/instances//admin/i-44F9075D/ramdisk-digest
[Fri Sep 17 01:32:42 2010][001119][EUCADEBUG ] walrus_request(): wrote 3482 bytes in 1 writes
[Fri Sep 17 01:32:42 2010][001119][EUCAINFO  ] walrus_request(): saved image in /var/lib/eucalyptus/instances//admin/i-44F9075D/ramdisk-digest
[Fri Sep 17 01:32:42 2010][001119][EUCAINFO  ] downloading and preparing image into /var/lib/eucalyptus/instances//admin/i-44F9075D/ramdisk...
[Fri Sep 17 01:32:42 2010][001119][EUCAINFO  ] walrus_request(): downloading /var/lib/eucalyptus/instances//admin/i-44F9075D/ramdisk
[Fri Sep 17 01:32:42 2010][001119][EUCAINFO  ]                   from [http://192.168.0.90:8773/services/Walrus/image-store-1284658069/ramdisk.manifest.xml](http://192.168.0.90:8773/services/Walrus/image-store-1284658069/ramdisk.manifest.xml)
[Fri Sep 17 01:32:42 2010][001119][EUCADEBUG ] walrus_request(): writing GET/GetDecryptedImage output to /var/lib/eucalyptus/instances//admin/i-44F9075D/ramdisk
[Fri Sep 17 01:32:43 2010][001119][EUCADEBUG ] walrus_request(): wrote 3899035 bytes in 297 writes
[Fri Sep 17 01:32:43 2010][001119][EUCAINFO  ] walrus_request(): saved image in /var/lib/eucalyptus/instances//admin/i-44F9075D/ramdisk
[Fri Sep 17 01:32:43 2010][001119][EUCAINFO  ] vrun(): [cp -a /var/lib/eucalyptus/instances//admin/i-44F9075D/ramdisk /var/lib/eucalyptus/instances//eucalyptus/cache/eri-0B4E115B/ramdisk]
[Fri Sep 17 01:32:43 2010][001119][EUCAINFO  ] vrun(): [cp -a /var/lib/eucalyptus/instances//admin/i-44F9075D/ramdisk-digest /var/lib/eucalyptus/instances//eucalyptus/cache/eri-0B4E115B/ramdisk-digest]
[Fri Sep 17 01:32:43 2010][001119][EUCAINFO  ] walrus_request(): downloading /var/lib/eucalyptus/instances//admin/i-44F9075D/disk-digest
[Fri Sep 17 01:32:43 2010][001119][EUCAINFO  ]                   from [http://192.168.0.90:8773/services/Walrus/image-store-1284658069/image.manifest.xml](http://192.168.0.90:8773/services/Walrus/image-store-1284658069/image.manifest.xml)
[Fri Sep 17 01:32:43 2010][001119][EUCADEBUG ] walrus_request(): writing GET output to /var/lib/eucalyptus/instances//admin/i-44F9075D/disk-digest
[Fri Sep 17 01:32:43 2010][001119][EUCADEBUG ] walrus_request(): wrote 5887 bytes in 2 writes
[Fri Sep 17 01:32:43 2010][001119][EUCAINFO  ] walrus_request(): saved image in /var/lib/eucalyptus/instances//admin/i-44F9075D/disk-digest
[Fri Sep 17 01:32:43 2010][001119][EUCAINFO  ] downloading and preparing image into /var/lib/eucalyptus/instances//admin/i-44F9075D/disk...
[Fri Sep 17 01:32:43 2010][001119][EUCAINFO  ] walrus_request(): downloading /var/lib/eucalyptus/instances//admin/i-44F9075D/disk
[Fri Sep 17 01:32:43 2010][001119][EUCAINFO  ]                   from [http://192.168.0.90:8773/services/Walrus/image-store-1284658069/image.manifest.xml](http://192.168.0.90:8773/services/Walrus/image-store-1284658069/image.manifest.xml)
[Fri Sep 17 01:32:43 2010][001119][EUCADEBUG ] walrus_request(): writing GET/GetDecryptedImage output to /var/lib/eucalyptus/instances//admin/i-44F9075D/disk
[Fri Sep 17 01:32:47 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:32:48 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:32:54 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:32:54 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:33:00 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:33:00 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:33:06 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:33:06 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:33:12 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:33:13 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:33:19 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:33:19 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:33:25 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:33:25 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:33:31 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:33:31 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:33:37 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:33:37 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:33:43 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:33:43 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:33:49 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:33:49 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:33:55 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:33:55 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:34:01 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:34:01 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:34:07 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:34:07 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:34:08 2010][001119][EUCADEBUG ] walrus_request(): wrote 1476395008 bytes in 148831 writes
[Fri Sep 17 01:34:08 2010][001119][EUCAINFO  ] walrus_request(): saved image in /var/lib/eucalyptus/instances//admin/i-44F9075D/disk
[Fri Sep 17 01:34:08 2010][001119][EUCAINFO  ] vrun(): [//usr/lib/eucalyptus/euca_rootwrap //usr/share/eucalyptus/partition2disk /var/lib/eucalyptus/instances//admin/i-44F9075D/disk 0 0]
[Fri Sep 17 01:34:14 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:34:14 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:34:20 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:34:20 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:34:26 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:34:26 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:34:32 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:34:32 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:34:38 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:34:38 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:34:44 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:34:44 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:34:50 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:34:50 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:34:56 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:34:56 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:35:02 2010][001119][EUCAINFO  ] vrun(): [cp -a /var/lib/eucalyptus/instances//admin/i-44F9075D/disk /var/lib/eucalyptus/instances//eucalyptus/cache/emi-E0AA107D/disk]
[Fri Sep 17 01:35:02 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:35:02 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:35:09 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:35:09 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:35:15 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:35:15 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:35:21 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:35:21 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:35:27 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:35:27 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:35:33 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:35:33 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:35:39 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:35:39 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:35:45 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:35:45 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:35:49 2010][001119][EUCAINFO  ] vrun(): [cp -a /var/lib/eucalyptus/instances//admin/i-44F9075D/disk-digest /var/lib/eucalyptus/instances//eucalyptus/cache/emi-E0AA107D/disk-digest]
[Fri Sep 17 01:35:49 2010][001119][EUCAINFO  ] vrun(): [//usr/lib/eucalyptus/euca_rootwrap //usr/share/eucalyptus/partition2disk /var/lib/eucalyptus/instances//admin/i-44F9075D/disk 512 88]
[Fri Sep 17 01:35:50 2010][001119][EUCAINFO  ] preparing images for instance i-44F9075D...
[Fri Sep 17 01:35:50 2010][001119][EUCAINFO  ] adding key/tmp/sckey.5fSaBH to the root file system at /var/lib/eucalyptus/instances//admin/i-44F9075D/disk using (//usr/lib/eucalyptus/euca_rootwrap //usr/share/eucalyptus/add_key.pl //usr/lib/eucalyptus/euca_mountwrap)
[Fri Sep 17 01:35:50 2010][001119][EUCAINFO  ] vrun(): [//usr/lib/eucalyptus/euca_rootwrap //usr/share/eucalyptus/add_key.pl //usr/lib/eucalyptus/euca_mountwrap 32256 /var/lib/eucalyptus/instances//admin/i-44F9075D/disk /tmp/sckey.5fSaBH]
[Fri Sep 17 01:35:50 2010][001119][EUCADEBUG ] system_output(): [//usr/lib/eucalyptus/euca_rootwrap //usr/share/eucalyptus/gen_kvm_libvirt_xml --ramdisk --ephemeral]
[Fri Sep 17 01:35:50 2010][001119][EUCAINFO  ] currently running/booting:  i-44F9075D
[Fri Sep 17 01:35:50 2010][001119][EUCAERROR ] libvirt: internal error no supported architecture for os type 'hvm' (code=1)
[Fri Sep 17 01:35:50 2010][001119][EUCAFATAL ] hypervisor failed to start domain
[Fri Sep 17 01:35:51 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:35:51 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:35:53 2010][001119][EUCAERROR ] libvirt: Domain not found: no domain with matching name 'i-44F9075D' (code=42)
[Fri Sep 17 01:35:53 2010][001119][EUCAINFO  ] vrun(): [rm -rf /var/lib/eucalyptus/instances//admin/i-44F9075D/]
[Fri Sep 17 01:35:53 2010][001119][EUCAINFO  ] stopping the network (vlan=10)
[Fri Sep 17 01:35:57 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:35:57 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:36:03 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:36:04 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:36:05 2010][001119][EUCAINFO  ] doTerminateInstance() invoked (id=i-44F9075D)
[Fri Sep 17 01:36:05 2010][001119][EUCAERROR ] libvirt: Domain not found: no domain with matching name 'i-44F9075D' (code=42)
[Fri Sep 17 01:36:05 2010][001119][EUCAWARN  ] warning: domain i-44F9075D to be terminated not running on hypervisor
[Fri Sep 17 01:36:10 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:36:10 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:36:16 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:36:16 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:36:22 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:36:22 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:36:28 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:36:28 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:36:34 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:36:34 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:36:40 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:36:40 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:36:46 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:36:46 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:36:52 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:36:52 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:36:58 2010][001119][EUCAINFO  ] forgetting about instance i-44F9075D
[Fri Sep 17 01:36:58 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:36:59 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:37:05 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:37:05 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:37:11 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:37:11 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:37:17 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:37:17 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:37:23 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:37:23 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:37:29 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:37:29 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:37:35 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:37:35 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:37:41 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:37:41 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:37:47 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:37:47 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:37:53 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:37:53 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:38:00 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:38:00 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:38:06 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:38:06 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:38:12 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:38:12 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:38:18 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:38:18 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:38:24 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:38:24 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:38:30 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:38:30 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:38:36 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:38:36 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:38:42 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:38:42 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:38:48 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:38:48 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:38:54 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:38:54 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:39:01 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:39:01 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:39:07 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:39:07 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:39:13 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:39:13 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:39:19 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:39:19 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:39:25 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:39:25 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:39:31 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:39:31 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:39:37 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:39:37 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:39:43 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:39:43 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:39:49 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:39:49 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:39:55 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:39:55 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:40:01 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:40:01 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:40:07 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:40:07 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:40:14 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:40:14 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:40:20 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:40:20 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:40:26 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:40:26 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:40:32 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:40:32 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:40:38 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:40:38 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:40:44 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:40:44 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:40:50 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:40:50 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:40:56 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:40:56 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:41:02 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:41:02 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:41:08 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:41:09 2010][001119][EUCADEBUG ] doDescribeInstances() invoked

---

### Post by Rusty au Lait on 2010-09-16
> **darkksyde said:**
> Hi,
I am trying to install a private cloud but whenever i go to start an instance, it says pending then shutting down then terminated??
I have attached the logs below
Any help would be appreciated,
Thanks


nc.log
____________
[Fri Sep 17 01:35:50 2010][001119][EUCAERROR ] libvirt: internal error no supported architecture for os type 'hvm' (code=1)

Maybe type 'hvm' should be 'kvm'.

[Fri Sep 17 01:35:50 2010][001119][EUCAFATAL ] hypervisor failed to start domain
[Fri Sep 17 01:35:51 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:35:51 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:35:53 2010][001119][EUCAERROR ] libvirt: Domain not found: no domain with matching name 'i-44F9075D' (code=42)
[Fri Sep 17 01:35:53 2010][001119][EUCAINFO  ] vrun(): [rm -rf /var/lib/eucalyptus/instances//admin/i-44F9075D/]
[Fri Sep 17 01:35:53 2010][001119][EUCAINFO  ] stopping the network (vlan=10)
[Fri Sep 17 01:35:57 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:35:57 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:36:03 2010][001119][EUCADEBUG ] doDescribeResource() invoked
[Fri Sep 17 01:36:04 2010][001119][EUCADEBUG ] doDescribeInstances() invoked
[Fri Sep 17 01:36:05 2010][001119][EUCAINFO  ] doTerminateInstance() invoked (id=i-44F9075D)
[Fri Sep 17 01:36:05 2010][001119][EUCAERROR ] libvirt: Domain not found: no domain with matching name 'i-44F9075D' (code=42)
[Fri Sep 17 01:36:05 2010][001119][EUCAWARN  ] warning: domain i-44F9075D to be terminated not running on hypervisor


Seem to be the start of your problems. Is kvm misspelled somewhere?

---

