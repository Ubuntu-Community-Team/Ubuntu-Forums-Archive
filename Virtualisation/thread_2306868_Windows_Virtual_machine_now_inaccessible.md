---
title: "Windows Virtual machine now inaccessible"
date: 2015-12-19
forum: Virtualisation
---

### Post by AbleTassie on 2015-12-19
The only Windows machine I have in Virtualbox is inaccessible, see below. I am not sure what happened, but I am wondering if there is anything I can do short of reinstalling Windowscas a virtual machine and again installing the other utilities.

I get the following when opening virtualbox:

The selected virtualmachine is inaccessible. Please inspect the error message shown below and press the refresh button if you want to repeat the accessibility check:
: 

Runtime error opening '/home/rob/VirtualBox VMs/NewWindows/NewWindows.vbox' for reading: -102(File not found.).

 /home/vbox/vbox-5.0.2/src/VBox/Main/src-server/MachineImpl.cpp[736] (nsresult Machine::i_registeredInit()).
 [TABLE]
 [TR]
 [TD] Result Code: 
[/TD]
 [TD] NS_ERROR_FAILURE (0x80004005)
[/TD]
[/TR]
 [TR]
 [TD] Component: 
[/TD]
 [TD] MachineWrap
[/TD]
[/TR]
 [TR]
 [TD] Interface: 
[/TD]
 [TD] IMachine {f30138d4-e5ea-4b3a-8858-a059de4c93fd}
[/TD]
[/TR]
[/TABLE]

---

### Post by gtozzi on 2015-12-19
do you have a file called /home/rob/VirtualBox VMs/NewWindows/NewWindows.vbox ?

---

### Post by AbleTassie on 2015-12-19
> **gtozzi said:**
> do you have a file called /home/rob/VirtualBox VMs/NewWindows/NewWindows.vbox ?

Yes gtozzi, I have such a file. When I open it (it opens with Virtualbox) I get the Oracle VM Virtualbox manager window with the error message that I posted in my first post. 

Thanks,

A.

---

### Post by gtozzi on 2015-12-19
Please open a terminal an type

> ls -l "/home/rob/VirtualBox VMs/NewWindows/"

then also type

> VBoxManage list vms

post output of both commands here.

---

### Post by AbleTassie on 2015-12-20
> **gtozzi said:**
> Please open a terminal and type

ls -l "/home/rob/VirtualBox VMs/NewWindows/"

then also type

VBoxManage list vms

post output of both commands here.

gtozzi,

Here is the output thanks,

rob@RobNotebook:~$ ls -l "/home/rob/VirtualBox VMs/NewWindows/" 
ls: cannot access /home/rob/VirtualBox VMs/NewWindows/: No such file or directory


rob@RobNotebook:~$ VBoxManage list vms 
"<inaccessible>" {5916d51e-72c7-47e8-a507-ac6366b7530b}

---

### Post by SeijiSensei on 2015-12-20
> **AbleTassie said:**
> Yes gtozzi, I have such a file. When I open it (it opens with Virtualbox) I get the Oracle VM Virtualbox manager window with the error message that I posted in my first post. 

rob@RobNotebook:~$ ls -l "/home/rob/VirtualBox VMs/NewWindows/"
ls: cannot access /home/rob/VirtualBox VMs/NewWindows/: No such file or directory

What about the "Virtual VMs" directory itself.  Try using 
```
ls -lR '/home/rob/VirtualBox VMs/
```
to list all the files and directories in the "VMs" directory.

See if you can re-add the VM to the manager app with Machine > Add and pointing to the appropriate file.  (Remove the old one if it is listed already.)

---

### Post by gtozzi on 2015-12-20
> ls: cannot access /home/rob/VirtualBox VMs/NewWindows/: No such file or directory

Apparently this means the file is not where it is supposed to be.

Let's try to locate it using these commands:
> cd ~
pwd
find -iname NewWindows.vbox

---

### Post by AbleTassie on 2015-12-20
> **SeijiSensei said:**
> What about the "Virtual VMs" directory itself.  Try using 
```
ls -lR '/home/rob/VirtualBox VMs/
```
to list all the files and directories in the "VMs" directory.

See if you can re-add the VM to the manager app with Machine > Add and pointing to the appropriate file.  (Remove the old one if it is listed already.)

The only output I get from the command "ls -lR '/home/rob/VirtualBox VMs/" is ">" see below. Not sure what this means. And I am not exactly sure what your instructions mean. Thanks

Terminal copy:

rob@RobNotebook:~$ ls -lR '/home/rob/VirtualBox VMs/
>

> **gtozzi said:**
> Apparently this means the file is not where it is supposed to be.

Let's try to locate it using these commands:

gtozzi, thanks. Here is the output I get:

rob@RobNotebook:~$ cd ~
rob@RobNotebook:~$ pwd
/home/rob
rob@RobNotebook:~$ find -iname NewWindows.vbox 
./Downloads/VirtualBox VMs/NewWindows/NewWindows.vbox
rob@RobNotebook:~$

---

### Post by deadflowr on 2015-12-20
The command is incomplete, you need to add the ' to the end like so[COLOR=#000000]
[/COLOR]```
ls -lR '/home/rob/VirtualBox VMs/'
```

---

### Post by AbleTassie on 2015-12-20
> **deadflowr said:**
> The command is incomplete, you need to add the ' to the end like so[COLOR=#000000]
[/COLOR]```
ls -lR '/home/rob/VirtualBox VMs/'
```

OK, I get this output now:

rob@RobNotebook:~$ ls -lR '/home/rob/VirtualBox VMs/'
ls: cannot access /home/rob/VirtualBox VMs/: No such file or directory
rob@RobNotebook:~$ 

I think this is because the directory is in Downloads. Maybe the attached screenshots will help.

[ATTACH=CONFIG]266285[/ATTACH][ATTACH=CONFIG]266286[/ATTACH]

OK, thanks to everybody. I solved the problem. I moved the VirtualBox VMs folder from Downloads into Rob and now it works, the New Windows Virtual Machine is accessible with VirtualBox. So somehow the folder must have been moved to Downloads by mistake. I do not know how this happened. I will mark this thread as SOLVED.

Thanks again.

A.

---

### Post by gtozzi on 2015-12-20
It looks like we've found the problem: the directory is in Downloads.

Just move it outside Downloads and thinks should start working again.

I suggest you to do a backup of your home first, just in case.

We've posted together :D
Yep, maybe you just had dragged it by mistake.

Yahoo!

---

### Post by AbleTassie on 2015-12-20
> **gtozzi said:**
> It looks like we've found the problem: the directory is in Downloads.

Just move it outside Downloads and thinks should start working again.

I suggest you to do a backup of your home first, just in case.

Thanks I just did that, but I did not do the backup. I did it before I read your post gtozzi. Thanks to you Deadflower and Sensei.

A.

---

