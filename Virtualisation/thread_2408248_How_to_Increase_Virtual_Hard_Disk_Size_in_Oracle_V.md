---
title: "How to Increase Virtual Hard Disk Size in Oracle VM Virtualbox"
date: 2018-12-16
forum: Virtualisation
---

### Post by AnupamMitra on 2018-12-16
I'm using Ubuntu 18.10 as Host and Guest is Windows 7 in Oracle VM Virtual Box. Earlier I had allocated 50 GB of storage space. 

Now to increase the Virtual Hard Disk Size, I entered the following: 
```

VBoxManage modifyhd windows7.vdi [COLOR=#660033]--resize[/COLOR] [COLOR=#000000]75000
[/COLOR]
```
[COLOR=#000000]The result is as under:
[/COLOR]```
anupam@anupam-ubuntu:~$ VBoxManage modifyhd windows7.vdi --resize 75000
VBoxManage: error: Could not find file for the medium '/home/anupam/windows7.vdi' (VERR_FILE_NOT_FOUND)
VBoxManage: error: Details: code VBOX_E_FILE_ERROR (0x80bb0004), component MediumWrap, interface IMedium, callee nsISupports
VBoxManage: error: Context: "OpenMedium(Bstr(pszFilenameOrUuid).raw(), enmDevType, enmAccessMode, fForceNewUuidOnOpen, pMedium.asOutParam())" at line 179 of file VBoxManageDisk.cpp

```

As I'm not so enough to find out the mistake, I need experts' help to solve the issue. Looking forward.


[COLOR=#000000]
[/COLOR]

---

### Post by QIII on 2018-12-16
Moved to Virtualisation

---

### Post by ubname on 2018-12-16
Hi,

you need to give the full path to your ".vdi" file, let's say windows7.vdi is in /home/anupam/VirtualBox VMs:

```
VBoxManage modifyhd /home/anupam/VirtualBox\ VMs/windows7/windows7.vdi --resize 75000


```

HTH.

---

### Post by AnupamMitra on 2018-12-16
> **ubname said:**
> Hi,

you need to give the full path to your ".vdi" file, let's say windows7.vdi is in /home/anupam/VirtualBox VMs:

```
VBoxManage modifyhd /home/anupam/VirtualBox\ VMs/windows7/windows7.vdi --resize 75000


```

HTH.

Thanks for your prompt reply. However, I followed your suggestion, but again it gives error report.

```

anupam@anupam-ubuntu:~$ VBoxManage modifyhd /home/anupam/VirtualBox\ VMs/windows7/windows7.vdi --resize 75000
VBoxManage: error: Could not find file for the medium '/home/anupam/VirtualBox VMs/windows7/windows7.vdi' (VERR_FILE_NOT_FOUND)
VBoxManage: error: Details: code VBOX_E_FILE_ERROR (0x80bb0004), component MediumWrap, interface IMedium, callee nsISupports
VBoxManage: error: Context: "OpenMedium(Bstr(pszFilenameOrUuid).raw(), enmDevType, enmAccessMode, fForceNewUuidOnOpen, pMedium.asOutParam())" at line 179 of file VBoxManageDisk.cpp
anupam@anupam-ubuntu:~$ 

```

> **QIII said:**
> Moved to Virtualisation

Sorry, noted for future.

---

### Post by ubname on 2018-12-16
I gave an example, I cannot guess where 
windows7.vdi is in your system

[U]Yo need to specify full path to windows7.vdi


[/U]

---

### Post by AnupamMitra on 2018-12-16
> **ubname said:**
> I gave an example, I cannot guess where 
windows7.vdi is in your system

[U]Yo need to specify full path to windows7.vdi


[/U]

The full path is /home/anupam/VirtualBox VMs/Windows 7 (64 Bit).vdi

However, when I write the same in Terminal, it says -

```

anupam@anupam-ubuntu:~$ VBoxManage modifyhd /home/anupam/VirtualBox VMs/Windows 7 (64 Bit).vdi
bash: syntax error near unexpected token `('
anupam@anupam-ubuntu:~$ 

```

Thereafter, I written the following, but in vain.

```

anupam@anupam-ubuntu:~$ VBoxManage modifyhd /home/anupam/VirtualBox\ VMs/Windows 7.vdi --resize 75000
Oracle VM VirtualBox Command Line Management Interface Version 5.2.20
(C) 2005-2018 Oracle Corporation
All rights reserved.

Usage:

VBoxManage modifymedium     [disk|dvd|floppy] <uuid|filename>
                            [--type normal|writethrough|immutable|shareable|
                                    readonly|multiattach]
                            [--autoreset on|off]
                            [--property <name=[value]>]
                            [--compact]
                            [--resize <megabytes>|--resizebyte <bytes>]
                            [--move <path]
                            [--description <description string>]

Syntax error: Invalid parameter '7.vdi'
anupam@anupam-ubuntu:~$

```

Sorry for the trouble.

---

### Post by TheFu on 2018-12-16
Put the path in single quotes.

In the future, it is best to use "tab completion" to ensure the filename is correct.
Also, avoiding the use of spaces and () in any part of a directory or filename will make your life easier.

---

### Post by ubname on 2018-12-16
Yes, you used a bunch of unfortunate spaces and chars for you VM name. 

 I'm not sure you got the full path to the .vdi file indeed,

try to run this :

```
ls VirtualBox\ VMs/
```

and this:


```
ls VirtualBox\ VMs/Windows\ 7\ \(64\ Bit\)/
```

post output

---

### Post by TheFu on 2018-12-16
**tab  completion** solves these sorts of trivial issues.  It is so hard to explain, but intuitively obvious once you start using it.  I use it thousands of times a day.  There must be a youtube tutorial about it.

---

### Post by AnupamMitra on 2018-12-16
> **ubname said:**
> Yes, you used a bunch of unfortunate spaces and chars for you VM name. 

 I'm not sure you got the full path to the .vdi file indeed,

try to run this :

```
ls VirtualBox\ VMs/
```

and this:


```
ls VirtualBox\ VMs/Windows\ 7\ \(64\ Bit\)/
```

post output

I'm grateful for your support. However, the output is as under.

```

anupam@anupam-ubuntu:~$ ls VirtualBox\ VMs/
'Windows 7 (64 Bit)'
anupam@anupam-ubuntu:~$ ls VirtualBox\ VMs/Windows\ 7\ \(64\ Bit\)/
 Logs       'Windows 7 (64 Bit).vbox'       'Windows 7 (64 Bit).vdi'
 Snapshots  'Windows 7 (64 Bit).vbox-prev'
anupam@anupam-ubuntu:~$ 

```

> **TheFu said:**
> **tab  completion** solves these sorts of trivial issues.  It is so hard to explain, but intuitively obvious once you start using it.  I use it thousands of times a day.  There must be a youtube tutorial about it.

Yes, I was unaware about **tab completion**. Okay, I will learn and use it in next course of time. Thanks for your help.

---

### Post by AnupamMitra on 2018-12-16
> **ubname said:**
> Yes, you used a bunch of unfortunate spaces and chars for you VM name. 

 I'm not sure you got the full path to the .vdi file indeed,

try to run this :

```
ls VirtualBox\ VMs/
```

and this:


```
ls VirtualBox\ VMs/Windows\ 7\ \(64\ Bit\)/
```

post output

At last with using Tab Completion and using trial & error method, I could find the right path and got success.

```

anupam@anupam-ubuntu:~$ VBoxManage modifyhd /home/anupam/VirtualBox\ VMs/Windows\ 7\ \(64\ Bit\)/Windows\ 7\ \(64\ Bit\).vdi --resize 75000
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
anupam@anupam-ubuntu:~$

```

Thanks a lot to you and TheFu.

---

### Post by ubname on 2018-12-17
good job :D

---

