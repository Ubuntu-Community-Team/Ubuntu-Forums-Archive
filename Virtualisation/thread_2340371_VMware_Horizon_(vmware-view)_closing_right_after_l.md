---
title: "VMware Horizon (vmware-view) closing right after log-on"
date: 2016-10-18
forum: Virtualisation
---

### Post by amin-mar-71 on 2016-10-18
I installed VMware Horizon Client 4.2.0 and ran using  ```
vmware-view
```. After logging on, the screen would blank for  about a minute then exit the virtualization without any prompt. This is what the terminal says:

```
vmware-view
Using log file /tmp/vmware-amin/vmware-horizon-client-16523.log
2016-10-17  23:52:57.699-04:00: vmware-view 16523| Spawn of vmware-view-usb failed:  Failed to execute child process "vmware-view-usb" (No such file or  directory)
2016-10-17 23:52:57.699-04:00: vmware-view 16523|  ViewUsblib: mmfw_RegisterClient: error opening connection: error 2 (No  such file or directory)
2016-10-17 23:52:57.700-04:00: vmware-view 16523| ViewUsblib: ViewUsb_InitLib: cannot connect to vmware-view-usbd: mmfw_ret=1
2016-10-17 23:52:57.700-04:00: vmware-view 16523| CdkViewUsb_Init: ViewUsb_InitLib returned ViewUsbStatus_UsbdCommsFailure
2016-10-17 23:52:57.700-04:00: vmware-view 16523| CdkViewUsb_Init: (is vmware-view-usbd running?)
2016-10-17  23:52:58.335-04:00: vmware-view 16523| rmksContainer(16550):  CreateMKSInterface: forcing mount, Remote MKS already present
2016-10-17 23:52:58.335-04:00: vmware-view 16523| rmksContainer(16550): OnMountUnmount: (0, 0) 1280 X 800.
2016-10-17  23:53:01.431-04:00: vmware-view 16523| rmksContainer(16550):  OnDisplayTopologyChanged: monitor 0: left=0, top=0, right=1280,  bottom=800
2016-10-17 23:53:01.749-04:00: vmware-view 16523| rmksContainer(16550): Unexpected signal: 4.
2016-10-17 23:53:01.907-04:00: vmware-view 16523| rmksContainer(16550): Loop on signal 4.
2016-10-17 23:53:01.908-04:00: vmware-view 16523| rmksContainer(16550): Panic loop
2016-10-17  23:53:01.916-04:00: vmware-view 16523| rmksContainer(16550): Caught  child exit with status 0x100, requesting container exit
2016-10-17 23:53:02.211-04:00: vmware-view 16523| rmksContainer(16550): ProcessPollCb: received exit request, shutting down...
2016-10-17  23:53:02.211-04:00: vmware-view 16523| rmksContainer(16550):  Vmdb_SetCurrentPath Failed: /vm/#0/type/sub/mountState/req/#9/ (Schema  path not found)
2016-10-17 23:53:12.213-04:00: vmware-view 16523| rmksContainer(16550): Killing vmware-remotemks child: 40aa
```

I tried a solution at the end of this thread: [https://ubuntuforums.org/showthread.php?t=2322324](https://ubuntuforums.org/showthread.php?t=2322324)
> by adding  /usr/lib/vmware to /etc/ld.so.conf.d/libc.conf and then running ldconfig

but this did not solve the problem. I thought I would start a new thread because that one was already off topic.

Thanks!

---

### Post by amin-mar-71 on 2016-10-19
Update:
I've found some other threads that recommended downgrading to 14.04 to get VMware client to work, so I'm going to try that route for now
[https://ubuntuforums.org/showthread.php?t=2327746](https://ubuntuforums.org/showthread.php?t=2327746)

---

