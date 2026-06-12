---
title: "VIRTUALBOX Failed to Open Session"
date: 2023-08-15
forum: Virtualisation
---

### Post by Rick St. George on 2023-08-15
Can't find where this was Posted, so Resubmitting ....

Running Virtualbox v6.1.38 / Windows for Trading Platform with quotes, data, charts etc. for years - Therefore any help is appreciated.



VIRTUALBOX ERROR / DETAILS

```

Failed to open a session for the virtual machine XP32-2.

Failed to open image '/media/stephen/Data/VirtualBox VMs/XP32-2/XP32-2.vdi' for writing due to wrong permissions (VERR_VD_IMAGE_READ_ONLY).

PIIX3 cannot attach drive to the Primary Master (VERR_VD_IMAGE_READ_ONLY).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: ConsoleWrap
Interface: IConsole {872da645-4a9b-1727-bee2-5585105b9eed}

```

PARTIAL LOG FILE:

```

00:00:01.679360 GUI: UIDesktopWidgetWatchdog::sltHandleHostScreenAvailableGeometryCalculated: Screen 1 work area is actually resized to: 0x28 x 1280x996
00:00:01.691094 File system of '/home/stephen/VirtualBox VMs/XP32-2/Snapshots' (snapshots) is unknown
00:00:01.691114 File system of '/media/stephen/Data/VirtualBox VMs/XP32-2/XP32-2.vdi' is ext4

```


Where did my "snapshots" folder go?

and, When i run ...

```

dpkg --list virtualbox-* in terminal, I get:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version                       Architecture Description
+++-==============================-=============================-============-============================================================
un  virtualbox-2.0                 <none>                        <none>       (no description available)
un  virtualbox-2.1                 <none>                        <none>       (no description available)
un  virtualbox-2.2                 <none>                        <none>       (no description available)
un  virtualbox-3.0                 <none>                        <none>       (no description available)
un  virtualbox-3.1                 <none>                        <none>       (no description available)
un  virtualbox-3.2                 <none>                        <none>       (no description available)
un  virtualbox-4.0                 <none>                        <none>       (no description available)
un  virtualbox-4.1                 <none>                        <none>       (no description available)
un  virtualbox-4.2                 <none>                        <none>       (no description available)
un  virtualbox-4.3                 <none>                        <none>       (no description available)
un  virtualbox-5.0                 <none>                        <none>       (no description available)
un  virtualbox-5.1                 <none>                        <none>       (no description available)
un  virtualbox-5.2                 <none>                        <none>       (no description available)
un  virtualbox-6.0                 <none>                        <none>       (no description available)
un  virtualbox-6.1                 <none>                        <none>       (no description available)
ii  virtualbox-dkms                6.1.38-dfsg-3~ubuntu1.20.04.1 amd64        x86 virtualization solution - kernel module sources for dkms
in  virtualbox-ext-pack            <none>                        all          (no description available)
un  virtualbox-guest-additions-iso <none>                        <none>       (no description available)
un  virtualbox-guest-dkms          <none>                        <none>       (no description available)
un  virtualbox-guest-modules       <none>                        <none>       (no description available)
un  virtualbox-modules             <none>                        <none>       (no description available)
ii  virtualbox-qt                  6.1.38-dfsg-3~ubuntu1.20.04.1 amd64        x86 virtualization solution - Qt based user interface
ii  virtualbox-source              6.1.38-dfsg-3~ubuntu1.20.04.1 amd64        x86 virtualization solution - kernel module source
~

```

Checking if DKMS is installed:
	
```


MS-7640:~$ dpkg -l | grep virtualbox-dkms
ii  virtualbox-dkms                               6.1.38-dfsg-3~ubuntu1.20.04.1              amd64        x86 virtualization solution - kernel module sources for dkms


```


If I uinstall it, install DKMS and Rebuild it, will I lose all data I had in the VM ??


After closing the VM, and Running again I get this Error inside the VBox Window;

"Windows could not start because the following file is mising or corrupt;
\WINDOWS\SYSTEM32\CONFIG\SYSTEM
You can attempt to repair this file by starting Windows Setup using the original Setup CD-Rom.
Select 'r' at the first screen to start repair."

---

### Post by Rick St. George on 2023-08-15
Upon opening VM windos did a Chkdsk, found some errors, did repair, and Booted Up Ok!
All my files still there and away we go.
Hope this Helps somebody else.

:guitar:

---

