---
title: "net use Z: \\vboxsvr\vb-share;  System error 53 network path not found"
date: 2021-01-18
forum: Virtualisation
---

### Post by luigiwriter2 on 2021-01-18
**Summary: Errors received**
```
net use Z: \\vboxsvr\vb-share
   System error 53 has occured
   The network path was not found.
```
and
Map drive: ```
\\vboxsvr\vb-share
    "Windows can't find a computer or device named 'vboxsvr'"
    Error code 0x80070035
    The network path was not found.
```

**[SIZE=4]What I have done:[/SIZE]**
virtualbox.org/virtualbox/6.1.16/Oracle_VM_VirtualBox_Extension_Pack-6.1.16.vbox-extpack
Installed
Member of both vboxsf and vboxusers
**Win10-Home Guest: **Created and Windows 10 Home installed
Used File->Close->Power off .
**Ubuntu 18.04 Host Terminal**
 \home\luigiwriter\vb-share share file created
```
VBoxManage sharedfolder add "Win10-Home" --name "vb-share" --hostpath "/home/luigiwriter"
VBoxManage: error: Shared folder named 'vb-share' already exists
```
Well, at least VBoxManage knows it exists, but not able to tell Windows 10???:(
**Win10-Home Guest:**
```
net use Z: \\vboxsvr\vb-share
   System error 53 has occured
   The network path was not found.

```
Windows file manager:
*  network lists local machine, but not \\vboxsvr
*  Map drives does not find it either.

*Hard Reboot just to be sure*
**Windows file manager:**
Map drive: ```
\\vboxsvr\vb-share
    "Windows can't find a computer or device named 'vboxsvr'"
    Error code 0x80070035
    The network path was not found.
```
Have to type everything in because the clipboard is not working either although set to bi-directional.

4 days at this. searched google, Oracle, Virturalbox.org, and too many more to discover that no one with this combination has this exact problem. 
Or if they did and did what I did above, and it worked for them but usually on older Ubuntu and older Window combinations.
At wits end, :confused:

Hope someone can see what I have missed while been staring at this for days

---

### Post by TheFu on 2021-01-19
**Guest additions installed?**
I suspect "vboxsvr" is a placeholder. Put the real hostname there and try again.

Lastly, google "virtualbox manual" to find the manual for how to do this.
[https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders) Appears you've found that.

I've never used linux as the hostOS with vbox. Sorry. I can say that KVM-qemu flies with Windows as a guest when the spice protocol is used.

---

### Post by Tadaen_Sylvermane on 2021-01-20
I don't fully understand what you are doing as I prefer KVM. Maybe just switch the network to bridged mode inside Virtualbox then create a regular samba share and map it like that? Then for all purposes it's just another machine on the lan and you can work with it as such.

---

