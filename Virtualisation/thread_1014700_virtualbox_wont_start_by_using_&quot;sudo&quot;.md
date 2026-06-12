---
title: "virtualbox wont start by using &quot;sudo&quot;"
date: 2008-12-18
forum: Virtualisation
---

### Post by legendsohai on 2008-12-18
Hello all,

  I'm just a newbie and noob of linux, now because of my noob, when i type in terminal with "sudo VirtualBox" and enter it, i get this message

No protocol specified
Qt WARNING: VirtualBox: cannot connect to X server :0.0

However, i can start normally without "sudo".


Can anybody please tell me how to solve this problem? I'm very appreciate on any comments or helps. Sry for my bad english :cry:

---

### Post by chrisxtj on 2008-12-18
encountered the same problem, anyone helps?

---

### Post by damis648 on 2008-12-18
Why would you want to do that? Just run it as your normal user.

---

### Post by chrisxtj on 2008-12-18
> **damis648 said:**
> Why would you want to do that? Just run it as your normal user.

I've just upgrade from 1.6.0 and my existing guest system is created with superuser privilege.

---

### Post by andrewstaflin on 2008-12-18
Does it really worth it that much to purchase Virtual Center? Would it be worth it to purchase Virtual center
If I don't upgrade my VI3 from standard to Enterprise. The post above cheered me up a lot into buying it, but it did not
mention what it will give & not give in standard edition.

[http://www.virtualizationteam.com/virtualization-vmware/vmware-virtual-server-virtualization-vmware/virtualcenter-for-vm-ware-server-real-value.html](http://www.virtualizationteam.com/virtualization-vmware/vmware-virtual-server-virtualization-vmware/virtualcenter-for-vm-ware-server-real-value.html)

---

### Post by damis648 on 2008-12-18
Don't bother, virtualbox is just as good. Try this:
```
cp ~/.VirtualBox ~/.VBoxback
rm -R ~/.VirtualBox
sudo cp /root/.VirtualBox ~/
sudo chown -R $USER ~/.VirtualBox
```
and then run it as your normal user.

---

### Post by chrisxtj on 2008-12-18
> **andrewstaflin said:**
> Edit bodhi.zazen: <Spam deleted>

I cannot see any relation between your post and my problem...

---

### Post by chrisxtj on 2008-12-18
> **damis648 said:**
> Don't bother, virtualbox is just as good. Try this:
```
cp ~/.VirtualBox ~/.VBoxback
rm -R ~/.VirtualBox
sudo cp /root/.VirtualBox ~/
sudo chown -R $USER ~/.VirtualBox
```
and then run it as your normal user.

You mean just copy my guest system to home folder? Well, that will be my last choice as my home folder is on a different partition and has little free space.
Anyway, Thx

---

### Post by damis648 on 2008-12-18
> **chrisxtj said:**
> You mean just copy my guest system to home folder? Well, that will be my last choice as my home folder is on a different partition and has little free space.
Anyway, Thx

You could just symlink it; It won't use any extra space.
```
rm -R ~/.VirtualBox
sudo chown $USER /root/.VirtualBox
ln -s /root/.VirtualBox ~/VirtualBox
```

---

### Post by bodhi.zazen on 2008-12-18
> **chrisxtj said:**
> I cannot see any relation between your post and my problem...

It was spam and is now removed.

When you see spam, just use the report button (it is on the left, under the user name).

---

### Post by chrisxtj on 2008-12-18
> **damis648 said:**
> You could just symlink it; It won't use any extra space.
```
rm -R ~/.VirtualBox
sudo chown $USER /root/.VirtualBox
ln -s /root/.VirtualBox ~/VirtualBox
```

it works! thanks a lot!
I just input these commands
```

mkdir ~/.VirtualBoxbak
cp ~/.VirtualBox/* ~/.VirtualBoxbak -r
rm -r ~/.VirtualBox
sudo chown $USER /root/.VirtualBox -R
ln -s /root/.VirtualBox ~/.VirtualBox

```

---

### Post by legendsohai on 2008-12-18
thx for your all reply, but im still cannot make it works.

my problem is i do not have .VirtualBox folder under /root

Can please tell me what happen to me? wrong installation?

thx for your all replies

---

### Post by legendsohai on 2008-12-18
now I found that I will get the error when running virtualbox 2.1.0

while no problem for 2.0.6

---

### Post by Tobis87 on 2008-12-19
Hi!
I got it working by running xhost before starting VirtualBox.
```
xhost local:root
```

You can also add it to .bashrc to get executed after login.
```
echo "xhost local:root > /dev/null" >> ~/.bashrc
```

---

### Post by legendsohai on 2008-12-20
> **Tobis87 said:**
> Hi!
I got it working by running xhost before starting VirtualBox.
```
xhost local:root
```

You can also add it to .bashrc to get executed after login.
```
echo "xhost local:root > /dev/null" >> ~/.bashrc
```

thx very much guy, I will test it later.

I will report what happen later. 

Thx. :)

---

### Post by legendsohai on 2008-12-21
sry guys, it seems like not work and I get this message:

```

Failed to create the VirtualBox COM object.
The application will now terminate.


Could not load the settings file '/root/.VirtualBox/VirtualBox.xml'.
Element '{http://www.innotek.de/VirtualBox-settings}SystemProperties', attribute 'defaultHardDiskFolder': [facet 'pattern'] The value '' is not accepted by the pattern '.+'.
Element '{http://www.innotek.de/VirtualBox-settings}SystemProperties', attribute 'defaultHardDiskFolder': '' is not a valid value of the atomic type '{http://www.innotek.de/VirtualBox-settings}TLocalFile'.


Result Code: 
VBOX_E_XML_ERROR (0x80BB000A)
Component: 
VirtualBox
Interface: 
IVirtualBox {339abca2-f47a-4302-87f5-7bc324e6bbde}

```

---

### Post by hertelend on 2008-12-25
Hi,

I have the same behavior like legendsohai. 
VB (2.1.0) runs on account 1 (ubuntu 8.10) perfect. Trying to start VB on account 2, I get the same COM .... error like described by legendsohai.
The VB was installed on account 1.
Any ideas? :confused:

Ulrich

---

### Post by legendsohai on 2008-12-30
Or is this a bug of VBox??

---

### Post by Empty56 on 2009-01-16
> **hertelend said:**
> Hi,

I have the same behavior like legendsohai. 
VB (2.1.0) runs on account 1 (ubuntu 8.10) perfect. Trying to start VB on account 2, I get the same COM .... error like described by legendsohai.
The VB was installed on account 1.
Any ideas? :confused:

Ulrich
Hi,

same problem (ubuntu 8.10) with VBox 2.1.0 (virtualbox-2.1_2.1.0-41146_Ubuntu_intrepid_i386.deb)

2.0.6 installed without error.

---

