---
title: "HowTo: VMware Tools on Ubuntu 8.10 Server JeOS (ESXi 3.5)"
date: 2008-11-19
forum: Virtualisation
---

### Post by marcpem on 2008-11-19
I managed to install VMware Tools on Ubuntu 8.10 Server JeOS (64-bit) on ESXi 3.5.0, build 110271. It was complicated so I thought I'd share. Now I still have a question about paravirtualization at the end of this post.

When you define your VM, set the network adapter to be E1000 at first.

**INSTALLING THE OS**

Start the virtual machine and in the console select the language and press F4 to change the mode to ***Install a minimum virtual machine***. Press Enter to start the installation.

Select the following items from the desired services (this is for what I intend to do with my server, you might need different options):

[LIST]
[*]Basic Ubuntu server
[*]DNS server
[*]OpenSSH server
[*]Samba file server
[*]Virtual Machine host
[/LIST]

Log into the machine and update it with: 
```
sudo apt-get update
sudo apt-get upgrade
```


**INSTALL THE VMWARE TOOLS**

According to [COLOR="RoyalBlue"]_[Peter Cooper]("http://peterc.org/2008/62-how-to-install-vmware-tools-on-ubuntu-hardy-804-under-vmware-fusion.html") _[/COLOR]and many other posts out there, there is a problem compiling VMware tools in Ubuntu. So we will follow the workaround using parts of the open source tools.

Install dependency for VMware Tools: 
```
sudo apt-get install build-essential linux-headers-$(uname -r) psmisc
sudo apt-get install gcc binutils make wget
```

And for the hack with the open tools I also installed the following (although some of these were found on sites describing what's needed for Ubuntu with a GUI, some might be unnecessary):
```
sudo apt-get install libgtk2.0-dev
sudo apt-get install libproc-dev libdumbnet-dev xorg-dev
cd /tmp
sudo mkdir liburiparser
cd liburiparser
sudo wget http://ftp.ie.debian.org/debian/pool/main/u/uriparser/liburiparser1_0.7.2-0exp1_amd64.deb
sudo wget http://ftp.ie.debian.org/debian/pool/main/u/uriparser/liburiparser-dev_0.7.2-0exp1_amd64.deb
sudo dpkg -i liburiparser1_0.7.2-0exp1_amd64.deb
sudo dpkg &#8211;i liburiparser-dev_0.7.2-0exp1_amd64.deb
sudo apt-get install libicu-dev
```

Go to /tmp and download the open source version of the tools from [COLOR="RoyalBlue"]_[here]("http://downloads.sourceforge.net/open-vm-tools/open-vm-tools-2008.11.18-130226.tar.gz?modtime=1227030450&big_mirror=0")_[/COLOR].
```
sudo wget http://downloads.sourceforge.net/open-vm-tools/open-vm-tools-2008.11.18-130226.tar.gz?modtime=1227030450&big_mirror=0
```

Unpack and build the open-vm-tools:
```
sudo tar xzvf open-vm-tools*.gz
cd open-vm-tools-2008.11.18-130226
sudo ./configure --includedir=/usr/include/uriparser
sudo make
```

In the VMware management console, right click on the VM and tell VMware to install the VM tools then copy the tools:
```
sudo mount /media/cdrom0
sudo cp -a /media/cdrom0/VMwareTools*.gz /tmp/
cd /tmp/
sudo tar -xzvf VMwareTools*.gz
```

From the open source modules/linux folder we have the vmblock, vmhgfs, vmmemctl, vmsync and vmxnet modules that we need to tar up and place into the official VMware tools tarball:
```
cd /tmp/open-vm-tools-2008.11.18-130226/modules/linux/
for i in *; do sudo mv ${i} ${i}-only; sudo tar -cf ${i}.tar ${i}-only; done
cd ../../..
sudo mv -f open-vm-tools-2008.11.18-130226/modules/linux/*.tar vmware-tools-distrib/lib/modules/source/
```

Now we can run the regular VMware tools installer accepting all the defaults:
```
cd /tmp/vmware-tools-distrib/
sudo ./vmware-install.pl
```

Activate the vmxnet drivers:
```
sudo /etc/init.d/networking stop
sudo depmod &#8211;a
sudo modprobe vmxnet 
sudo /etc/init.d/networking start
```

Shutdown with sudo ```
init 0
``` and in the management console edit the VM settings, delete the Network Adapter that was previously created and create new ones with vmxnet settings.

Start the VM and this step should be complete.

[B]
So the last thing that I haven't figured out is that I thought that after installing VMware Tools, I could turn on Paravirtualization in ESXi for this VM. I did turn on the VT option in the bios of my host machine, but I still get the message "This kernel requires an x86-64 CPU, but only detected an i686 CPU." Can anybody help ?[/B]

---

### Post by bodhi.zazen on 2008-11-19
I think the problem is JeOS is a 32 bit ...

what is the output of ```
uname -m
```

In that event, try the minimal install CD (for 64 bit).

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by corranchetano on 2008-11-21
Hi,

thanks for this really great guideline. Works great!

Regards,
CC

---

### Post by marcpem on 2008-11-21
When I turn paravirtualization off and boot the VM, the output of command is:
```
$uname -m
x86_64

```
So it seems that when I turn paravirtualization on, the ESXi 3.5 generates a virtual CPU as i686 instead of using the real 64-bit CPU?

---

### Post by RobinReborn on 2008-12-01
I have a problem here

In the VMware management console, right click on the VM and tell VMware to install the VM tools then copy the tools:
Code:

sudo mount /media/cdrom0

the sudo mount /media/cdrom0 doesn't work whether I have no CD or a blank CD.  I don't know where I can go to see the VMware management console.  I am using Ubunto 8.10 but there are some slight differences (like I have a i386 not amd64).  Any help would be greatly appreciated.

---

### Post by Mark_Malewski on 2008-12-20
Ok, I have a problem with the following line:

sudo for i in *; do sudo mv ${i} ${i}-only; sudo tar -cf ${i}.tar ${i}-only; done


Is this line correct, and does it work?  I've entered it exactly like that, and it comes back with an error "bash: syntax error near expected token 'do'

I've tried it over and over and over again.  It doesn't seem to work.  Any ideas?

This falls under the section entitled:
"**From the open source modules/linux folder we have the vmblock, vmhgfs, vmmemctl, vmsync and vmxnet modules that we need to tar up and place into the official VMware tools tarball:**"

The second line down says:


**sudo for i in *; do sudo mv ${i} ${i}-only; sudo tar -cf ${i}.tar ${i}-only; done**

I've been unable to get that line to work.  Any suggestions as to what could be wrong?  Is there an error with that line, or are there any other commands I could use?

---

### Post by fourseven on 2008-12-26
Malewski:

I had the same error with the for loop line; I know nothing about shell scripting, but it seems like removing the first 'sudo' fixed it.

---

### Post by fourseven on 2008-12-26
marcpem: fantastic guide, everything seems to have worked!

Well, except for one thing :)

When it asks 'Please choose one of the following display sizes that X will start with', I chose not the default, but a higher resolution.
It spat out an error: 'error setting MTTR (base = 0xf8000000, size = 0x00400000, type = 1) Invalid argument (22)

So it looks like everything worked just peachy, except I can't change the resolution -- even in System->Screen Resolution, I only get the default vmware resolutions.

I don't really know anything about X or setting the screen resolutions (except some vague traumatic memories from a few years ago) ... any hints on how to coerce this to comply?

thx!

---

### Post by fourseven on 2008-12-27
Aha! I found the culprit: the default memory video size is 4MB, which only allows screen sizes up to 1180x885

I found a workaround here: [http://communities.vmware.com/thread/90634](http://communities.vmware.com/thread/90634)

Edit the corresponding .vmx file, adding this line to it:

svga.vramSize = 23040000

(This will enable resolutions up to 2360x1770)

cheers!

---

### Post by marcpem on 2008-12-27
Thanks fourseven, I updated the post and removed the first "sudo" from this line.

---

### Post by marcpem on 2008-12-27
> **RobinReborn said:**
> I have a problem here

In the VMware management console, right click on the VM and tell VMware to install the VM tools then copy the tools:
Code:

sudo mount /media/cdrom0

the sudo mount /media/cdrom0 doesn't work whether I have no CD or a blank CD.  I don't know where I can go to see the VMware management console.  I am using Ubunto 8.10 but there are some slight differences (like I have a i386 not amd64).  Any help would be greatly appreciated.
That might have been a little too short. In the VMware Infrastructure client  you have to right click on the virtual machine in the inventory panel on the left and select "Install/Upgrade VMware tools", then the mount should work.

---

### Post by marcpem on 2008-12-27
Since I still have no solution on my paravirtualization problem, I decided to try with an officially supported solution. So I installed the 64-bit version of Ubuntu 8.04.1 server edition on VMware ESXi Udate 3. Everything works perfectly, the vmware tools install in no time, there is no need to tweak it like in this guide. 

But again, as soon as I turn Paravirtualization on I get the same error:

“This kernel requires an x86-64 CPU, but only detected an i686 CPU.”

I did turn on VT on the bios of the host machine.

Can anybody help ?

---

### Post by caveman-jim on 2008-12-29
> **marcpem said:**
> Since I still have no solution on my paravirtualization problem, I decided to try with an officially supported solution. So I installed the 64-bit version of Ubuntu 8.04.1 server edition on VMware ESXi Udate 3. Everything works perfectly, the vmware tools install in no time, there is no need to tweak it like in this guide. 

But again, as soon as I turn Paravirtualization on I get the same error:

“This kernel requires an x86-64 CPU, but only detected an i686 CPU.”

I did turn on VT on the bios of the host machine.

Can anybody help ?

VMware paravirtualization support only extends to 32bit guests.

---

### Post by inktvis75 on 2009-01-18
I use another way to install vmware support:

[http://www.l4l.be/docs/virt/openvmtools_ubuntu810.php](http://www.l4l.be/docs/virt/openvmtools_ubuntu810.php)

sudo apt-get install linux-headers-`uname -r` build-essential g++ dkms xorg-dev libgtk2.0-dev libdumbnet-dev libicu-dev

tar xzvf open-vm-tools-2008.12.23-137496.tar.gz

cp -r open-vm-tools-2008.12.23-137496/modules/linux /usr/src/open-vm-tools-2008.12.23 

sudo dkms add -m open-vm-tools -v 2008.12.23
sudo dkms build -m open-vm-tools -v 2008.12.23 -k `uname -r`
sudo dkms install -m open-vm-tools -v 2008.12.23 -k `uname -r`

cd open-vm-tools-2008.12.23-137496
./configure --disable-unity --without-kernel-modules
make
sudo make install

---

### Post by t35t0r on 2009-02-04
> **marcpem said:**
> 
But again, as soon as I turn Paravirtualization on I get the same error:

&#8220;This kernel requires an x86-64 CPU, but only detected an i686 CPU.&#8221;

I did turn on VT on the bios of the host machine.

Can anybody help ?

```

"Your CPU does not support long mode. Use a 32bit distribution"

```

For VirtualBox you can't run a 64bit guest inside a 32bit host unless the physical CPU supports VT extensions and you have them enabled (i.e. you still need a 64bit capable cpu with VT extensions). One example of this would be running a 64 bit linux guest inside a 32 bit winxp pro host on a core 2 duo cpu.

This is also true for vmware esxi which only comes as an i386 host OS (some variant of RHEL). You must enable the CPU VT extensions in the bios and you must turn software (para-virtualization) VMI extensions off in the properties dialog of the guest OS in order to install a 64 bit guest OS. Otherwise you'll get the same error as above even though you're running on 64bit CPUs.

The reason for this is that these hypervisors can't emulate 64bit words on a 32bit architecture exclusively in software (VMI/paravirt). You need hardware VT support.

---

### Post by Mindzai on 2009-02-20
Thanks for this post, I finally have scalable desktop and copy/paste between guest and host back!

---

### Post by prickly on 2009-06-27
> **t35t0r said:**
> This is also true for vmware esxi which only comes as an i386 host OS (some variant of RHEL).

You are referring to the ESX Service Console (RHEL 3 Update 6) which is distinct from the ESX hypervisor. ESX is not RHEL. ESXi has no Service Console. 

However since your post ESX 4.0 (VSphere) has been released and this is a 64 bit hypervisor :)

---

### Post by juancarlospaco on 2009-06-28
*whats the point...*

i use on node Ubuntu JeOS+SSH+KVM and 
Convirt 1.1 on Centralized Administration Console.

---

