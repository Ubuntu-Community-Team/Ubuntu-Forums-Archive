---
title: "Hypervisor 1 with gui?"
date: 2011-06-02
forum: Virtualisation
---

### Post by blwegrzyn on 2011-06-02
Is there a stripped down version of Ubuntu server with gui that would allow me create vms and run them locally on my deskotp?
I want to simply start the os and have options to run different oses at the same time.  I would use it like a workstation but instead of 1 os i would have 2 or 3 on top of the hypervisor?

thx

---

### Post by CharlesA on 2011-06-02
Just install Ubuntu Desktop and uninstall the stuff you don't want/need.

---

### Post by blwegrzyn on 2011-06-03
would not be better to install ubuntu server and then only add the necessary stuff?  Basically all i need is sound support and simple gui. The rest will be on the vms.
So far I did server install with virtualization option and added below packages:
sudo apt-get install xserver-xorg xserver-xorg-core
sudo apt-get install openbox
sudo apt-get install obconf
sudo apt-get install virt-manager
sudo apt-get install lxterminal
sudo apt-get install xinit
sudo apt-get install virt-goodies
sudo apt-get install vlan

but , i need also audio and not sure how to install it?

thx

---

### Post by CharlesA on 2011-06-03
It would be easier to just install Ubuntu Desktop, since you wouldn't have to install all the other stuff.

Alsa is for sound, isn't it?

The way I do it is that I have my VMs running headless and use RDP or VNC to access the GUI of the VM. It's not the best, but it works for me.

---

### Post by blwegrzyn on 2011-06-03
So the way you do it you have a server with no keyboard and mouse , monitor attached? (HEADLESS)
Are you getting audio on the machines through RDP or VNC?

thx

---

### Post by CharlesA on 2011-06-03
> **blwegrzyn said:**
> So the way you do it you have a server with no keyboard and mouse , monitor attached? (HEADLESS)
Are you getting audio on the machines through RDP or VNC?

thx
That's correct.

---

### Post by blwegrzyn on 2011-06-03
sorry, buy i need some clarification, so if the vm host is installed on ubuntu and no audio drivers are installed but the vms are configured with audio, does it mean that audio is transferred over remote connection?

for example lets say i have a softphone on the vm windows 7

can  i connect to the vm from the desktop and actually use that softphone with the microphone and speakers on that desktop?

would i use regular rdp connection or special connection?

thx

---

### Post by CharlesA on 2011-06-03
It depends on the remote connection. I've used plain RDP on an XP virtual machine and it transfers audio over fine. Should be the same with Windows 7.

Are you trying to use a Windows box to access it or a linux box? I've only tried it using Windows 7 RDP.

---

### Post by blwegrzyn on 2011-06-04
So basically the audio on the vm is set to null
and the audio driver is set to something type of the audio driver.
And the audio redirection depends on the os and remote client?

I guess no virtual solution provides the audio redirection on its own?

I found this for vmware:
[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1004839](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1004839)
but it is os specific

not sure if similar stuff exist for ubuntu?

---

### Post by CharlesA on 2011-06-04
I think it's specific to Windows RDP. I have the audio set to "disabled" on virtualbox and if I connect to a windows box via RDP, I can watch youtube or whatever with sound.

See attached.

---

### Post by blwegrzyn on 2011-06-06
so i created the simple ubuntu server with gui openbox
now i need to add audio support
what are the basic packages needed to add audio support
so i can use it vms created on the local machine?

---

