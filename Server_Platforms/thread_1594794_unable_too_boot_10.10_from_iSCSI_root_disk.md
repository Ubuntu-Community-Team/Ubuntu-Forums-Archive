---
title: "unable too boot 10.10 from iSCSI root disk"
date: 2010-10-12
forum: Server Platforms
---

### Post by runelind on 2010-10-12
I'm wanting to run 10.10 server from a root disk located on an iSCSI server.  My server is FreeBSD 8 running isc-dhcpd and is sharing out a 20GB iSCSI disk.  I've run the server install CD (currently testing in VMWare), and it finds the iSCSI share without a problem.  I'm able to install the OS just fine, but the problems start when I try to boot the installation.  I'm booting off a gPXE iso until I can get PXE chain-loading figured out.  My DHCP config looks as such:

```

             host mm-iscsi
        {
                hardware ethernet 00:50:56:3f:3f:bf;
                fixed-address 10.50.3.245;
option root-path "iscsi:10.50.3.5::::iqn.2007-09.jp.ne.peach.istgt:disk3";

```

When I boot the OS from the gPXE iso, it grabs a DHCP address and then boots from the iSCSI target.  It drops me to the grub loader and I pick the first option.  It then tries to continue booting from the iSCSI disk, but it tells me:

```

iscsistart: transport class version 2.0-870
iscsistart: version 2.0-071
iscsistart: Logging into iqn.2007-09.jp.ne.peach.istgt:disk3 10.50.3.5:3260,2
:iscsistart: Login authentication failed with target iqn.2007-09.jp.ne.peach.istgt:disk3
iscsistart: Login error (Login status 0) on conn 5
iscsistart: initiator reported error (19 - encountered no-retryable iSCSI login failure)

```
then it drops me to an initramfs shell.

I've also tried this against a Nexenta iSCSI share, but it appears to be giving me the exact same problems.  I'm unsure if the problem lies with the ubuntu config or with the iSCSI server.  The istgt config for the disk is below:

```

[LogicalUnit3]
  Comment "XBMC"
  # full specified iqn (same as below)
  #TargetName iqn.2007-09.jp.ne.peach.istgt:disk1
  # short specified non iqn (will add NodeBase)
  TargetName disk3
  TargetAlias "Data Disk3"
  # use initiators in tag1 via portals in tag1
  Mapping PortalGroup2 InitiatorGroup2
  # accept both CHAP and None
#  AuthMethod Auto
  AuthMethod None
  AuthGroup AuthGroup1
  #UseDigest Header Data
 UseDigest Auto
  UnitType Disk
  # SCSI INQUIRY - Vendor(8) Product(16) Revision(4) Serial(16)
  #UnitInquiry "FreeBSD" "iSCSI Disk" "0123" "10000001"
  # Queuing 0=disabled, 1-255=enabled with specified depth.
  #QueueDepth 32
  # for file extent
  LUN0 Storage /dev/zvol/zfsraid/xbmc Auto
  # for raw device extent
  #LUN0 Storage /dev/ad4 Auto

```

In the iSCSI logs I see:

```

Oct 12 14:47:28 beastie istgt[32729]: Login from iqn.2000-09.org.etherboot:unknown (10.50.3.245) on iqn.2007-09.jp.ne.peach.istgt:disk3 LU3 (10.50.3.5:3260,2), ISID=400027230000, TSIH=3, CID=0, HeaderDigest=off, DataDigest=off

```

---

### Post by UMDGaara on 2010-10-29
Looking at the scripts/local-top/iscsi in the Ubuntu server 10.10 initrd reveals the iscsistart command used:

```
iscsistart -i $ISCSI_INITIATOR -t $ISCSI_TARGET_NAME    \
     -g $ISCSI_TARGET_GROUP -a $ISCSI_TARGET_IP   \
     -p $ISCSI_TARGET_PORT                        \
     ${ISCSI_USERNAME:+-u "$ISCSI_USERNAME"}      \
     ${ISCSI_PASSWORD:+-w "$ISCSI_PASSWORD"}      \
     ${ISCSI_IN_USERNAME:+-U "$ISCSI_IN_USERNAME"}\
     ${ISCSI_IN_PASSWORD:+-W "$ISCSI_IN_PASSWORD"}
```

These parameters come from the kernel command line arguments passed by the boot loader:


```
	for x in $(cat /proc/cmdline); do
		case ${x} in
        	iscsi_initiator=*)
                	ISCSI_INITIATOR="${x#iscsi_initiator=}"
                	;;
        	iscsi_target_name=*)
                	ISCSI_TARGET_NAME="${x#iscsi_target_name=}"
                	;;
        	iscsi_target_ip=*)
                	ISCSI_TARGET_IP="${x#iscsi_target_ip=}"
                	;;
        	iscsi_target_port=*)
                	ISCSI_TARGET_PORT="${x#iscsi_target_port=}"
                	;;
		iscsi_target_group=*)
			ISCSI_TARGET_GROUP="${x#iscsi_target_group=}"
			;;
		iscsi_username=*)
			ISCSI_USERNAME="${x#iscsi_username=}"
			;;
		iscsi_password=*)
			ISCSI_PASSWORD="${x#iscsi_password=}"
			;;
		iscsi_in_username=*)
			ISCSI_IN_USERNAME="${x#iscsi_in_username=}"
			;;
		iscsi_in_password=*)
			ISCSI_IN_PASSWORD="${x#iscsi_in_password=}"
			;;
		esac
	done
```


Therefore, at a minimum, you need to specify as kernel arguments:

iscsi_initiator (local initiator name to use, such as iqn.1993-08.org.debian:01:595de23b608a)
iscsi_target_name
iscsi_target_ip
iscsi_target_port (default is 3260)
iscsi_target_group (set this to 1 unless you created a target group tag on the server, in which case use that)

Hope that helps

---

### Post by UMDGaara on 2010-11-01
Additional notes:

You'll also need to remove the unused paramters from /etc/iscsi/iscsi.initramfs and update the initrd to use with your boot loader. To do this, I used another system as an iscsi initiator, mounted the root filesystem, then chroot'ed to it. You can then edit the file and update-initramfs -u, then exit the chroot environment and copy the updated initrd to your boot server.

While you're editing the root filesystem you might also want to comment your network interface out of /etc/network/interfaces so it doesn't go down/up on boot, dropping your iscsi session and access to your root filesystem as a result.

If you want to specify the IP to use as a kernel parameter, it must be in the format:

ip=<client-ip>:<server-ip>:<gw-ip>:<netmask>:<hostname>:<device>:<autoconf>

See [http://www.kernel.org/doc/Documentation/filesystems/nfs/nfsroot.txt](http://www.kernel.org/doc/Documentation/filesystems/nfs/nfsroot.txt) for details

You'll also need to specify on the kernel command line which device should act as the root filesystem, like root=/dev/sda1 or root=UUID=[some UUID]

Finally, there is an issue when the primary interface MAC is different than it was at install time (such as the case when you install the OS from one diskless client and boot it on another). I am still working out a solution to this and afterward I will write a more complete how-to and link it here.

---

