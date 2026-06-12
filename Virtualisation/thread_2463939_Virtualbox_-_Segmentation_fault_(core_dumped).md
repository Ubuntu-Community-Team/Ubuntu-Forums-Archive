---
title: "Virtualbox - Segmentation fault (core dumped)"
date: 2021-06-21
forum: Virtualisation
---

### Post by eminisci on 2021-06-21
I've been running Virtualbox without problems for many years on Ubuntu 16.04 before and now on 18.04.
Since a few days I've been unable to start it. When I try, I see some black screens and then nothing more. When I try to run from command line I have a segmentation fault message.
Here below I post the log file, where I can see some errors, but I'm unable to understand what really happens and how to possibly solve the problem:

```
VirtualBox XPCOM Server 5.2.42_Ubuntu r137960 linux.amd64 (Jun  5 2020 08:26:08) release log00:00:00.000749 main     Log opened 2021-06-21T17:46:18.195973000Z
00:00:00.000752 main     Build Type: release
00:00:00.000757 main     OS Product: Linux
00:00:00.000759 main     OS Release: 4.15.0-144-generic
00:00:00.000761 main     OS Version: #148-Ubuntu SMP Sat May 8 02:33:43 UTC 2021
00:00:00.000793 main     DMI Product Name: XPS 13 9370
00:00:00.000805 main     DMI Product Version: 
00:00:00.000883 main     Host RAM: 15756MB (15.3GB) total, 9608MB (9.3GB) available
00:00:00.000889 main     Executable: /usr/lib/virtualbox/VBoxSVC
00:00:00.000890 main     Process ID: 9130
00:00:00.000891 main     Package type: LINUX_64BITS_GENERIC (OSE)
00:00:00.003465 main     IPC socket path: /tmp/.vbox-kqb12101-ipc/ipcd
00:00:00.108915 nspr-2   VirtualBox: object creation starts
00:00:00.109060 nspr-2   Home directory: '/home/kqb12101/.config/VirtualBox'
00:00:00.109292 nspr-2   Loading settings file "/home/kqb12101/.config/VirtualBox/VirtualBox.xml" with version "1.12-linux"
00:00:00.121948 nspr-2   NetIfAdpCtlOut: VBoxNetAdpCtl: Error while retrieving link speed for wlp2s0: VBoxNetAdpCtl: ioctl failed: Operation not supported
00:00:00.122622 nspr-2   NAT: resolv.conf: nameserver 127.0.0.53
00:00:00.122662 nspr-2   HostDnsMonitor::updateInfo
00:00:00.122686 nspr-2   HostDnsMonitor: old information
00:00:00.122698 nspr-2     no server entries
00:00:00.122710 nspr-2     no domain set
00:00:00.122720 nspr-2     no search string entries
00:00:00.122733 nspr-2   HostDnsMonitor: new information
00:00:00.122744 nspr-2     server 1: 127.0.0.53
00:00:00.122755 nspr-2     domain: fritz.box
00:00:00.122766 nspr-2     search string 1: fritz.box
00:00:00.125698 nspr-2   VD: VDInit finished with VINF_SUCCESS
00:00:00.125829 nspr-2   ERROR [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={0eb668d2-495e-5a36-8890-29999b5f030c} aComponent={SystemPropertiesWrap} aText={Cannot determine default Guest Additions ISO location. Most likely they are not available}, preserve=false aResultDetail=0
00:00:00.134320 nspr-2   Loading settings file "/home/kqb12101/VirtualBox VMs/WIN7/WIN7.vbox" with version "1.15-linux"
00:00:00.140793 nspr-2   VirtualBox: object created
00:01:03.048798 main     VirtualBox: object deletion starts
00:01:03.048909 main     ERROR [COM]: aRC=VBOX_E_OBJECT_IN_USE (0x80bb000c) aIID={4afe423b-43e0-e9d0-82e8-ceb307940dda} aComponent={MediumWrap} aText={Medium '/home/kqb12101/VirtualBox VMs/WIN7/WIN7.vdi' cannot be closed because it is still attached to 1 virtual machines}, preserve=false aResultDetail=0
00:01:03.151496 Watcher  ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={9570b9d5-f1a1-448a-10c5-e12f5285adad} aComponent={VirtualBoxWrap} aText={The object is not ready}, preserve=false aResultDetail=0
00:01:08.058678 main     {00007f6090017d30} HostPowerServiceLinux::~HostPowerServiceLinux: RTThreadWait() for 5000 ms failed with VERR_TIMEOUT
00:01:08.059223 main     VirtualBox: object deleted

```

Any idea on how to proceed?
Many thanks

---

### Post by monkeybrain20122 on 2021-06-21
>  ERROR [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={0eb668d2-495e-5a36-8890-29999b5f030c} aComponent={SystemPropertiesWrap} aText={Cannot determine default Guest Additions ISO location. Most likely they are not available}, preserve=false aResultDetail=

Maybe try to reinstall guest additions?

---

### Post by MAFoElffen on 2021-06-21
What version of VBox and VBox additions are you on? Did you do a recent update of packages that involve VBox? (Hint- Check your apt logs) Did the Host OS shutdown while the Guest VM was running?

---

