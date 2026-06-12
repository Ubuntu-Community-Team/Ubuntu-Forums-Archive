---
title: "VirtualBox keeps crashing"
date: 2023-02-24
forum: Virtualisation
---

### Post by 9ck on 2023-02-24
Hi forum
I&#8217;m having issues with VMs crashing on VirtualBox vers. 6.1. Admittedly I&#8217;m a novice when it comes to VMs and VirtualBox, so I&#8217;d really appreciate some help identifying why my VMs keep crashing.

I&#8217;ve set up two VMs, one running HomeAssistant OS on a &#8220;Other Linux 64 bit&#8221; VM and the other running Plex Media Server on "Ubuntu  22.04.2 LTS 64 bit" VM. I&#8217;m running both simultaneously on a Intel Nuc 10i5 (Intel Core i5-10210U &#8211; 4 cores / 8 threads) with 16GB RAM. I have allocated 4GB RAM / 2 processors to both WMs. Still they both end up being &#8220;Aborted&#8221; each morning. The NUC is running Ubuntu 22.04.2 LTS 64 bit.

Below links to my logfiles. I've attach logs from both VMs. Is it correct that the VBox.log.1 is the latest &#8220;crashed&#8221; version (I have restarted the VMs before getting the log file)?

Log from VM running HomeAssistant OS
[https://pastebin.com/yGJyHHby](https://pastebin.com/yGJyHHby)

Log from VM running Ubuntu / Plex
[https://pastebin.com/sbs6xf9W](https://pastebin.com/sbs6xf9W)

---

### Post by ian-weisser on 2023-02-24
From the HASS VM log: 

```

06:52:05.778705 GUI: UICommon::sltHandleCommitDataRequest: Emergency shutdown initiated

```

This usually occurs when a human clicks 'X' to close the VM window. There could be other causes, like a SIGHUP. The key point is that it's being logged. It's not hardware failure nor a crash -- the hypervisor (VirtualBox application on the host) is receiving a shutdown signal and following instructions.

---

### Post by 9ck on 2023-02-24
OK I belive it has something to do with that I log out of my host NUC. But why? Do I have to be logged into the host in order to keep VirtualBox running?

---

### Post by 9ck on 2023-02-24
Deleted

---

### Post by 9ck on 2023-02-24
> **ian-weisser said:**
> From the HASS VM log: 

```

06:52:05.778705 GUI: UICommon::sltHandleCommitDataRequest: Emergency shutdown initiated

```

This usually occurs when a human clicks 'X' to close the VM window. There could be other causes, like a SIGHUP. The key point is that it's being logged. It's not hardware failure nor a crash -- the hypervisor (VirtualBox application on the host) is receiving a shutdown signal and following instructions.

Both VMs abort without my interference - but as mentioned in the post  above I do log out of the host running Ubuntu. Not sure if it happens at  the moment I log out or after a while - but will investigate.

---

### Post by ian-weisser on 2023-02-24
Yes, logout would indeed cause the Hypervisor to terminate, shutting down (aborting) the Guest VMs.

Graphical applications (like the Host VirtualBox GUI application) cannot run when the user is not logged in.

So the next question is how to get those VMs to be active when you are logged out. It's possible, it's not difficult. It's just not possible the way you did it.

To keep using those VMs, you must use VBox's Headless or Detached modes. I'm not expert in those, so will defer to another community member to expand on those.

Use of VM is an  appropriate tool for this kind of job, and there are other alternatives for tinkerers and experimenters: Both HomeAssistant and Plex can be run from LXD containers (that's how I do it), or both are also available as ordinary Snap packages.

---

### Post by TheFu on 2023-02-24
[https://www.virtualbox.org/manual/UserManual.html#vboxheadless](https://www.virtualbox.org/manual/UserManual.html#vboxheadless) explains.

---

### Post by SeijiSensei on 2023-02-24
You started the VirtualBox process from your own log in. If you log out, all the applications associated with your session will close.

---

### Post by 9ck on 2023-02-24
@ Ian, Fu and Seiji - Thank you for your help and input.

---

### Post by TheFu on 2023-02-24
> **9ck said:**
> @ Ian, Fu and Seiji - Thank you for your help and input.

Did it work?

---

