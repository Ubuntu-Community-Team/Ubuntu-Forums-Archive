---
title: "Oracle virtual box in ubuntu host"
date: 2024-01-17
forum: Virtualisation
---

### Post by AnupamMitra on 2024-01-17
In my Ubuntu Desktop I use Linux Mint in Oracle Virtual Box.  Last month also it was fine. But today when I tried to open the Virtual Box I got the following message.
```

Failed to open a session for the virtual machine LINUX MINT.

The virtual machine 'LINUX MINT' has terminated unexpectedly during startup with exit code 1 (0x1).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: MachineWrap
Interface: IMachine {85632c68-b5bb-4316-a900-5eb28d3413df}

```
Like to know the way out.

---

### Post by howefield on 2024-01-17
Thread moved to the "*Virtualisation*" forum.

---

### Post by AnupamMitra on 2024-01-17
After raising the issue in this Forum, I was searching several sites for settling the problem. At last I got the answer at "askubuntu" which was posted in August 2021. I simply updated and upgraded my host machine by using 
sudo apt update
sudo apt upgrade

And ultimately it could be settled. The link is given hereunder for further reference if needed by anybody.  

[https://askubuntu.com/questions/1287467/virtualbox-error-kernel-driver-not-installed-rc-1908-running-ubuntu-20-04-o/1358772#1358772](https://askubuntu.com/questions/1287467/virtualbox-error-kernel-driver-not-installed-rc-1908-running-ubuntu-20-04-o/1358772#1358772)

---

### Post by #&amp;thj^% on 2024-01-17
> **AnupamMitra said:**
> In my Ubuntu Desktop I use Linux Mint in Oracle Virtual Box.  Last month also it was fine. But today when I tried to open the Virtual Box I got the following message.
```

Failed to open a session for the virtual machine LINUX MINT.

The virtual machine 'LINUX MINT' has terminated unexpectedly during startup with exit code 1 (0x1).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: MachineWrap
Interface: IMachine {85632c68-b5bb-4316-a900-5eb28d3413df}

```
Like to know the way out.

**[B]EDIT I now see you have this resolved.**[/B]

This sounds very much like hardware, and we don't quite have enough info provided to really help you.
Check this and show us first please:
```
dkms status
```

---

