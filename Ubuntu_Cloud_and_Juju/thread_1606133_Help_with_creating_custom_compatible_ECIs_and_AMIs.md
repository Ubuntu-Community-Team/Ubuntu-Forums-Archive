---
title: "Help with creating custom compatible ECIs and AMIs"
date: 2010-10-26
forum: Ubuntu Cloud and Juju
---

### Post by philipprince on 2010-10-26
Dear All,

I wish to create my own custom Ubuntu 10.10 (or 10.04 LTS) images with just the 'right' mix of packages installed generally for my private UEC cloud and in dire circumstances for the Amazon Cloud.

I have installed UEC from a 10.10 (AMD64) disk: one CLC/Walrus server, one CC/SC server, three NC servers. The CC and NCs all have VT support (and it is enabled). The CLC does not. The networking is very simple - all are connected only on eth0 to my LAN.

If I use one of the 10.04 images from the Store, I can create and launch instances, attach EBSs, and connect to the instances via Hybridfox. All good stuff but not quite want I want.

I have the beginners guide, [http://cssoss.files.wordpress.com/2010/06/book_eucalyptus_beginners_guide_uec_edition1.pdf](http://cssoss.files.wordpress.com/2010/06/book_eucalyptus_beginners_guide_uec_edition1.pdf), (I believe it is the same as recommended by kim0 in [http://ubuntuforums.org/showthread.php?t=1599664](http://ubuntuforums.org/showthread.php?t=1599664)).

Firstly, I have carefully followed the instructions therein using kvm-img on a 10.10 server with both a 10.10 installation disk and a 10.04.1 installation disk. I can create, bundle, and upload an image and I can even launch an instance from that image but, unlike the Store image/instances, I cannot connect to it. 

-> ssh: connect to host 192.168.123.151 port 22: Network is unreachable <-

I have "rm -rf /etc/udev/rules.d/70-persistent-net.rules" as instructed (this file did have some rules in in for 10.04.1 but only comments on 10.10) without the burden of actually understanding why.

Clearly I am thick and easily stumped. Help would be greatly appreciated!

Secondly, once I have the above EMI, I would like to have the same as an AMI so that I can quickly re-provision my services in the Amazon Cloud should my racks catch fire. I do not know if such a thing is actually possible. 

Best wishes,
Philip

---

### Post by kim0 on 2010-10-27
It may not be booting, or networking may not be working. Can you try to get the console output "euca-get-console-output" and paste it somewhere so that the problem is clearer

---

### Post by philipprince on 2010-10-28
Dear kim0,

It is very nice to hear from you. I will try what you suggest shortly.

In 9.4.2, there is a possible hack to get a VNC view into the running instance. I added my variant for <graphics type='vnc' listen='A.B.C.D' port='5904'/> into /usr/share/eucalyptus/gen_kvm_libvirt_xml on all of the NCs.

When I launched and then connected (I am using JollyFastVNC) only one line appeared "SeaBIOS ...". As you say above, it may not be booting.

I am afraid that the networking is a mystery to me. Con you point me to an explanation of how networking is accomplished in the UEC?

Thank you,
Philip

---

### Post by philipprince on 2010-10-28
I have broken something. Now, instances launched from the store image are refusing connection. I am going to re-install and get back to you.

---

### Post by wcorey on 2010-10-30
I know Canonical has spent a lot of effort in getting an easy and consistently reproducable way to make custom images. Look up VMBuilder or was it VM_Builder. I recall reading something that they have a new version in 10.10 to make it very simple. 

I know this sounds like just another 'try this', which it is but the point of vmbuilder is to ease the pain of what you are trying to do. I did it the long way, as you are, once or twice with 9.10 and with 10.4 could not, for the life of me get a valid image created. This is a very weak point with both EMI's and AMI's.....it is way easier to configure a VM running under KVM...WAY easier.

The problem you are running into, I believe, is stuffing the user key into the user area of the image and having the image startup verify the key. If that does not take place you won't be able to connect.

[http://www.thevarguy.com/2010/06/22/ubuntus-vmbuilder-script/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%253A+WorksWithU+%2528Works+With+U%2529](http://www.thevarguy.com/2010/06/22/ubuntus-vmbuilder-script/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%253A+WorksWithU+%2528Works+With+U%2529)

---

