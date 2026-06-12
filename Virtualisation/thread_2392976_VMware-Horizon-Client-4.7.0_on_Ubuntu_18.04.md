---
title: "VMware-Horizon-Client-4.7.0 on Ubuntu 18.04"
date: 2018-05-28
forum: Virtualisation
---

### Post by ronlin2 on 2018-05-28
Has anyone gotten this to work. I seem to succeed the .bundle installation but when connecting to a remote desktop the application just shows a black screen then loses connection back to the choise of remote machine(s)


From syslog
```
May 28 11:25:52 myworkstationLap vmware-view.desktop[19393]: 2018-05-28 11:25:52.889+02:00: vmware-view 19420| rmksContainer(9535): Unexpected signal: 11.May 28 11:25:52 myworkstationLap vmware-view.desktop[19393]: 2018-05-28 11:25:52.928+02:00: vmware-view 19420| rmksContainer(9535): VmdbCnxControlCb: pendingSubscribeReq was released with ret -32.
May 28 11:25:53 myworkstationLap vmware-view.desktop[19393]: 2018-05-28 11:25:53.067+02:00: vmware-view 19420| rmksContainer(9535): CreateMKSInterface: Remote MKS not yet present, queueing CheckForMount
May 28 11:25:53 myworkstationLap vmware-view.desktop[19393]: 2018-05-28 11:25:53.069+02:00: vmware-view 19420| rmksContainer(9535): Caught child exit with status 0xff00, requesting container exit
May 28 11:25:53 myworkstationLap vmware-view.desktop[19393]: 2018-05-28 11:25:53.069+02:00: vmware-view 19420| rmksContainer(9535): ProcessPollCb: received exit request, shutting down...
May 28 11:25:53 myworkstationLap vmware-view.desktop[19393]: 2018-05-28 11:25:53.070+02:00: vmware-view 19420| rmksContainer(9535): Vmdb_SetCurrentPath Failed: /vm/#0/type/sub/mountState/req/#6/ (Schema path not found)
May 28 11:26:03 myworkstationLap vmware-view.desktop[19393]: 2018-05-28 11:26:03.072+02:00: vmware-view 19420| rmksContainer(9535): Killing vmware-remotemks child: 2540
~           

```

found a solution in [https://communities.vmware.com/thread/587792](https://communities.vmware.com/thread/587792)

---

