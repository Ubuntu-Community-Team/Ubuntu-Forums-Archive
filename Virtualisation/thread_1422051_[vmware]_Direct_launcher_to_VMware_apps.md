---
title: "[vmware] Direct launcher to VMware apps"
date: 2010-03-04
forum: Virtualisation
---

### Post by jedimattk on 2010-03-04
I've been trying to create a desktop launcher using vmware-unity-helper for a couple hours now, but to no avail. I have Linux Mint 8 as the host and Windows XP Home as the guest; the launcher is supposed to open a program in my Windows VM with one click in the applications menu.

Here's the command I've been using up until now:

```
vmware-unity-helper --run "/home/matt/vmware/Windows XP/Windows XP.vmx" C:/Program Files/Microsoft Office/Office12/WINWORD.EXE
```

Anyone here experienced with VMware who can tell me what I'm doing wrong? If it helps, the error message I keep getting is "None of the files you opened are in shared folders, so they cannot be opened in the guest."

TIA!

---

### Post by dcstar on 2010-03-06
> **jedimattk said:**
> I've been trying to create a desktop launcher using vmware-unity-helper for a couple hours now, but to no avail. I have Linux Mint 8 as the host and Windows XP Home as the guest; the launcher is supposed to open a program in my Windows VM with one click in the applications menu.

Here's the command I've been using up until now:

```
vmware-unity-helper --run "/home/matt/vmware/Windows XP/Windows XP.vmx" C:/Program Files/Microsoft Office/Office12/WINWORD.EXE
```

Anyone here experienced with VMware who can tell me what I'm doing wrong? If it helps, the error message I keep getting is "None of the files you opened are in shared folders, so they cannot be opened in the guest."


Either you have a Windows file path in a Linux system, Linux probably knows nothing about "C:" drives, or you have not quoted the file path.

---

### Post by stonebit on 2011-04-11
I'm exploring this too.
More like this:
vmware-unity-helper -r /home/matt/vmware/Windows\ 7/Windows\ 7.vmx 'C:\\Program Files\Microsoft Office\Office12\WINWORD.exe'

Your quotes are off and you need a double slash after c:.

See here:
[http://everydaylht.com/howtos/desktop/launch-virtual-apps-directly-from-your-linux-desktop/](http://everydaylht.com/howtos/desktop/launch-virtual-apps-directly-from-your-linux-desktop/)

---

