---
title: "iSCSI troubles with Ubuntu Server 11.10"
date: 2011-11-07
forum: Server Platforms
---

### Post by mcarey on 2011-11-07
Hello,
  I'm posting a solution to the nasty iSCSI bug that I've encountered in Ubuntu Server 11.10.  

The story goes like this (mostly for google):

I installed the iSCSI target package (iscsitarget).  The first error was a missing module (iscsi_trgt.ko).  This was resolved by installing iscsitarget-dkms.  This soon led to the second problem; the snippet below is from my dmesg.  

---- snip ----

Nov  7 22:24:03 coredata kernel: [93398.385777] Pid: 10683, comm: istiod1 Not tainted 3.0.0-12-server #20-Ubuntu
Nov  7 22:24:03 coredata kernel: [93398.385782] Call Trace:
Nov  7 22:24:03 coredata kernel: [93398.385800]  [<ffffffffa01dcbc9>] send_data_rsp+0x1f9/0x230 [iscsi_trgt]
Nov  7 22:24:03 coredata kernel: [93398.385814]  [<ffffffff815fe82e>] ? _raw_spin_lock+0xe/0x20
Nov  7 22:24:03 coredata kernel: [93398.385826]  [<ffffffffa01e7c3d>] ? ua_pending+0x8d/0xf0 [iscsi_trgt]
Nov  7 22:24:03 coredata kernel: [93398.385833]  [<ffffffff815fe82e>] ? _raw_spin_lock+0xe/0x20
Nov  7 22:24:03 coredata kernel: [93398.385845]  [<ffffffffa01e60c7>] disk_execute_cmnd+0x257/0x290 [iscsi_trgt]
Nov  7 22:24:03 coredata kernel: [93398.385853]  [<ffffffffa01e0c9d>] worker_thread+0x15d/0x300 [iscsi_trgt]
Nov  7 22:24:03 coredata kernel: [93398.385859]  [<ffffffff815fc5c4>] ? schedule+0x3d4/0x770
Nov  7 22:24:03 coredata kernel: [93398.385865]  [<ffffffff81057340>] ? try_to_wake_up+0x200/0x200
Nov  7 22:24:03 coredata kernel: [93398.385873]  [<ffffffffa01e0b40>] ? nthread_stop+0x60/0x60 [iscsi_trgt]
Nov  7 22:24:03 coredata kernel: [93398.385879]  [<ffffffff81080c5c>] kthread+0x8c/0xa0
Nov  7 22:24:03 coredata kernel: [93398.385885]  [<ffffffff81607d24>] kernel_thread_helper+0x4/0x10
Nov  7 22:24:03 coredata kernel: [93398.385890]  [<ffffffff81080bd0>] ? flush_kthread_worker+0xa0/0xa0
Nov  7 22:24:03 coredata kernel: [93398.385896]  [<ffffffff81607d20>] ? gs_change+0x13/0x13
Nov  7 22:24:03 coredata kernel: [93398.385919] ------------[ cut here ]------------
Nov  7 22:24:03 coredata kernel: [93398.385923] kernel BUG at /var/lib/dkms/iscsitarget/1.4.20.2/build/kernel/iscsi.c:392!
Nov  7 22:24:03 coredata kernel: [93398.385927] invalid opcode: 0000 [#1] SMP 
Nov  7 22:24:03 coredata kernel: [93398.385932] CPU 2 
Nov  7 22:24:03 coredata kernel: [93398.385934] Modules linked in: iscsi_trgt bnep rfcomm bluetooth parport_pc ppdev bonding binfmt_misc e752x_edac edac_core shpchp lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov usbhid hid aic79xx 3w_9xxx e1000 tg3 raid6_pq async_tx raid1 raid0 multipath linear

---- snip ----

Notice the lines:
kernel BUG at
/var/lib/dkms/iscsitarget/1.4.20.2/build/kernel/iscsi.c:392


Hum... not so good.  So I started looking for a solution.  Buried deep in the iSCSI developer site, I found that this bug was fixed in the development version of the source code.   As such, I tried downloading the newest source from svn and compiling and installing it.  Low and behold, it worked like a champ!  


The below is how I did it:

# become root
sudo su -

# check out the source from source forge (do an "apt-get install subversion" if you don't have the svn command)
svn co [https://iscsitarget.svn.sourceforge.net/svnroot/iscsitarget](https://iscsitarget.svn.sourceforge.net/svnroot/iscsitarget) iscsitarget

# cd into the iscsitarget/trunk
cd iscsitarget/trunk

# build the package
make

# now install it
make install


And you're done.  You will want to reboot the box to bring your iSCSI module online.

  Hope this helps someone! :D
  -Mark.

---

### Post by cgjrdl on 2011-11-11
Thanks very much.  I'd been grappling with this and you really helped me out.

---

### Post by MickSx on 2012-05-02
This also worked for me on Ubuntu 12.04 with kernel 3.4.
 
I had to update the kernel due to suspend / resume issues on Asus P8H61-I.
 
Then I ran into all sorts of issues trying to get iscsitarget installed.
 
Finally downloaded the source according to your instructions and everything started to work. I didn't even have to reboot module just loaded using modprobe.
 
Thanks a bunch

---

