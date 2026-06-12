---
title: "open-iscsi fails to list sessions"
date: 2008-10-24
forum: Server Platforms
---

### Post by dani2305 on 2008-10-24
I have a problem getting iscsi to work with a kernel later than 2.6.27-5.

I am able to discover the different targets, and after restarting the open-iscsi daemon, everything seems to be fine.

But now the problems start:
Looking up the session via "iscsiadm -m session" fails with:

iscsiadm: Could not get host for sid 1.
iscsiadm: could not get host_no for session 6.
iscsiadm: could not find session info for session1
iscsiadm: Can not get list of active sessions (6)

And looking a bit deeper, no sessions at all are created.

What did change with kernel 2.6.27-6? Did someone else experience the same problem?

Thanks for your reply
Cheers
Dani

---

### Post by dani2305 on 2008-10-26
I have the impression, it's related to a change in the sysfs structure for iscsi....

---

### Post by dani2305 on 2008-10-26
It seems as the kernel-modules and the user-space do not match?
Using the latest open-iscsi 870rc3 seems to give better results...?

---

### Post by RMSe17 on 2008-11-17
Wait.. could you explain how to fix that problem? I am having the same issue with Ubuntu 8.10 32bit server.  The iscsiadm in discovery mode sees the targets, then I use the node login to the specified target, go to restart the open-iscsi and it says Login session iface:default, target: iqn.2006-01.com.openfiler:tsn.exodus, portal: xxx.xxx.xxx.xxx,3260 ...done.

Yet, when I do sudo /etc/init.d/open-iscsi status  it gives me
Current active iSCSI sessions:
iscsiadm: Could not get host for sid 1.
iscsiadm: could not get host_no for session 6.
iscsiadm: could not find session info for session1
iscsiadm: Can not get list of active sessions (6)

---

### Post by chrplunk on 2008-11-19
Updated Intrepid release notes: Mounting multiple iscsi targets at the same time is currently not supported. Systems configured to use more than one iscsi targets should not be upgraded to Intrepid.
[https://bugs.launchpad.net/ubuntu/+source/open-iscsi/+bug/289470](https://bugs.launchpad.net/ubuntu/+source/open-iscsi/+bug/289470)

---

### Post by RMSe17 on 2008-11-19
What do you mean by multiple targets?  I just followed the guidelines:

sudo apt-get install open-iscsi
sudo /etc/init.d/open-iscsi restart
sudo iscsiadm -m discovery -t sendtargets -p 192.168.xxx.xxx

This shows me 3 iscsi things...  I only want one of them, dont quite know how to get rid of the other two..

sudo /etc/init.d/open-iscsi restart

showed 3 logins into 3 nodes..  So, then I went as root into /etc/iscsi and got rid of two of the iscsi listings that I didn't need, leaving only one..  

After that, doing
sudo /etc/init.d/open-iscsi restart

only showes one login message, into the iscsi that I want.  But, I have no idea how to access it, or mount it.   So, I did 

sudo /etc/init.d/open-iscsi status

and got those error messages.  So I am guessing that means that I can not mount that drive?  

I tried getting the latest version, the 870 rc3, which I extracted, and it is a folder with a bunch of stuff.  I then did the sudo apt-get install build-essential   and then through senaptic package manager, I added the kernel headers for my kernel...  I then ran 
sudo make install

but got a bunch of error messages...  I am stuck now.

---

