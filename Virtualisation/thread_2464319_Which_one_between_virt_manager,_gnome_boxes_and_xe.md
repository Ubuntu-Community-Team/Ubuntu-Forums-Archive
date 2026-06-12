---
title: "Which one between virt manager, gnome boxes and xen is better?"
date: 2021-06-29
forum: Virtualisation
---

### Post by EngineerStrange on 2021-06-29
How is gnome boxes and xen as compared to kvm?

---

### Post by EngineerStrange on 2021-06-29
I will be using ubuntu 20.04.2 as host and q4os as guest and will use google meet. Which one will be better option for me. I am now using virtual box but having some problem in system because of python being main python version.

---

### Post by slickymaster on 2021-06-29
Post #1 moved to a thread of its own.

Please don't hijack other people's threads and don't start duplicate threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

### Post by EngineerStrange on 2021-06-29
Ok I thought it to be like social medias. Very very sorry for my mistake.

---

### Post by MAFoElffen on 2021-06-29
I agree with slickymaster's reasoning... I was going to suggest that in the last thread, that your question would get more exposure in a thread of it's own (instead of being buried at the end of another thread.)

"They are different animals than Virt-Manager. I know that statement deserves an explanation.

Virt-Manager is geared for a System Administrator. It has some advanced features that are there to be able to change and make the VM behave in different ways. Those assume that the person using the VM Guest has the ability and control over the guest. You install your own VM's...

Gnome Boxes, XenApps and XenDesktop are VM Viewers. Think of them as thin-clients. Just like VNC or RDP clients. There is a bit of shielding that just deals with viewing the VM, without having the ability to change how the VM runs on the hypervisor. It deals just with the VM itself.

Gnome Boxes will connect to a KVM host and is geared for an alternative to Virt-Manager, but just with access as a VM Viewer. It will work out-of-the box.

XenApp and XenDesktop is geared to work with Citrix/XenServer as a Hypervisor... You can make it work with KVM, though you have to install and configure Citrix ADM (Access Delivery Management) on the KVM Hypervisor, so that is has something compatible to connect to/through. To get around a licensing issue with the ADM, you have to configure your VM to use an external connection to your local network, instead of an internal switch to the local machine.

As for other VM Viewers to connect to a VM running on KVM... Many, many, many options.

---

### Post by TheFu on 2021-06-29
Very few people will have looked at all 3 of those. Of the people who have, I suspect they weren't looking to perform a comparison, rather they were seeking a solution for their specific needs.
Now add in some obscure distro, I'd never heard of it, q4os, and the list of people qualified to answer the question shrinks more.

I'm not qualified either.

I used Xen - the xm version, so nothing recent. That was from 2008 - 2011-ish.  It was used only for Linux servers on a headless system. Access was all via ssh/cli, almost always from a remote system. I have doubts that matches your needs. A few times a year, post-patching, some of the Xen VMs would refuse the boot. The more important it was that I needed to do something else, the more likely the VMs would refuse to boot. That was how it seemed. Disclosure, I owned stock in Citrix, the company behind Xen's commercial stuff.

I've been using **virt-manager** with KVM/qemu as the hypervisor since around 2010. It is mostly used for Linux servers, but there are a few desktops, Ubuntu and Windows, but all of these are still accessed remotely.  I use virt-manager to create a VM and to modify most settings as needed, but I use **virt-viewer** to access the full desktops over ssh+spice tunnels.  Since I'm still using this setup, for the last 11 yrs, you can assume it is what I prefer for a number of reasons - some are technical (extreme stability) and some are political (i.e., not running a hypervisor from a corporate overlord). My personal decisions likely don't align with very many others, so add some more salt to my opinion.

I've attempted to use Gnome boxes a few times the last few years.  I remember 2 yrs ago, it worked, but felt dumbed down so much as to be limiting for my needs. It is like asking an Indy car racer to drive a plastic big-wheel. Nothing wrong with big wheels, I have one in the attic. ;)  But it isn't an Indy car - ok, get that image out of your mind. ;|

Recent attempts to use gnome boxes has failed, so I've looked at some other options. Canonical has a snap package with a competitor to Boxes.  Let me search for the name. Multipass.  **Multipass** has a great name (Corbin Dallas!), but it has never worked for me either. Seemed it always needed to be in the shop. Snap packages don't work on many of my systems. Often for known reasons, sometimes for unknown reasons. [https://ubuntu.com/server/docs/virtualization-multipass](https://ubuntu.com/server/docs/virtualization-multipass) explains.

Found this comparison:  [https://arstechnica.com/gadgets/2020/04/virtualization-on-the-linux-desktop-gnome-boxes-vs-virt-manager/](https://arstechnica.com/gadgets/2020/04/virtualization-on-the-linux-desktop-gnome-boxes-vs-virt-manager/)

Anyway, as you can see, my history of great results and terrible failures has warped my ability to provide a response that is useful for your needs.  At least we aren't trying to compare containers to VMs. Good for that, though virt-manager is just an interface into libvirt which is just an access API for other hypervisors like virtualbox, kvm, qemu, xen, and probably some VMware stuff.  The libvirt website probably has a nice diagram to explain this. [https://libvirt.org/api.html](https://libvirt.org/api.html) has some nice diagrams - not the first one - skip that. Scroll down.

I think you'll need to try each to make an informed decision.  I think the Xen stuff makes pretty apps, but if the goal is just to run 1 VM, it is overkill.  For that need, Gnome-Boxes or Multipass are probably the GUI and KVM is probably the hypervisor.

---

### Post by MAFoElffen on 2021-06-29
Oh man!!! TheFu  I laughed so hard I hurt!

Yes, XenServer has not been the same since Citrix bought the commercial interests to it. I have to stay out of that discussion Big Time. The same when Oracle bought Sun.

I think if you are used to VirtualBox and it's VM interface, that you  are going to be very happy with Virt-Manager and Virt-Viewer. Anything else is going to feel like a thin client, Isolated.

A VM Viewer does have a purpose... That purpose is usually for a company to provide access to their services to their employees and customers, in a safe, secure manner. Meaning, they have Sys and NOC Admin's who control the VM's and access to them ...and don't want them F#@ked up, as well as someone entering their system unfettered. Something light that they can click on from home or the road, and do {only) what they need to do.. Got even bigger interest in the Pandemic and the work from home/remote workplace.

---

### Post by kevdog on 2021-06-30
@TheFu -- really nice post and detailed.  What's your host -- Ubuntu or another linux disto or something like ProxMox?  The dedicated hypervisor distros like Proxmox have a lot of nice features baked into them. 

XMAFoElffen -- xcp-ng -- it's the open-source Citrix hypervisor.  No Citrix or commercial limitations here.

---

### Post by EngineerStrange on 2021-06-30
In virt-manager and kvm how can I use microphone in order to use google meet?

---

### Post by QIII on 2021-06-30
Are you using the Virtual Machine Manager GUI?

---

### Post by TheFu on 2021-06-30
> **EngineerStrange said:**
> In virt-manager and kvm how can I use microphone in order to use google meet?

USB passthru.  I've never attempted that with a microphone.  The only thing I've passed through was USB storage.
No clue how to passthru an analog mic (the hardware), but audio does passthru for output just using the correct audio drivers presented to the VM.

_Update_: VMM and virt-manager are the same.  VMM is probably what shows up in a GUI (I don't know), but the program to be run is actually virt-manager.  virt-manager can be run on the VM host if there is a GUI or on remote workstations connected via ssh+qemu:// URLs in the GUI.  Both sides, the workstation and the VM host must have libvirtd installed, which provided the client/server connectivity.  No need for sudo or root to be a manager of VMs.  Membership in the Unix **libvirtd** group on each side of the client/server connection is sufficient. Obviously, ssh should work too. I've never used it without ssh-keys configured. I know that works.

---

### Post by EngineerStrange on 2021-06-30
Yes it's name appears as Virtual Machine Manager and I got it by installing the apt virt-manager.

---

### Post by MAFoElffen on 2021-06-30
On the Last 4 posts, if you have a USB headset with Virt-Manager, you are golden. While in Vert-Manager > Virtual Machine > Redirect USB Device > Check the boxes of the host's attached USB devices.

LOL. I can even add the receiver for my host's game controllers to a VM with just a click.

---

### Post by EngineerStrange on 2021-07-01
And is it possible to use the system microphone i.e. the one with laptop?

---

### Post by TheFu on 2021-07-01
> **EngineerStrange said:**
> And is it possible to use the system microphone i.e. the one with laptop?

Try it. Takes 10 minutes and you'd know the answer.

---

### Post by EngineerStrange on 2021-07-01
I am using Ubuntu 20.04.2 (64-bit) as host and Q4OS(32-bit) as guest.  I have added camera from USB host devices and hence it works now on  using google meet in virtual machine.


But I am still unable to use mic there and meet says that my mic is  not working. What can I do? (Please note that I haven't added mic from  usb host device as I can't find it there).

---

### Post by EngineerStrange on 2021-07-01
I tried as much as possible from my side.

---

### Post by TheFu on 2021-07-01
> **EngineerStrange said:**
> I tried as much as possible from my side.

And what did you try, 
what happened, and 
what were the errors shown?

Nobody here is Carnac the Magnificent, unfortunately.

I don't have a similar system, so I can't test it. Sorry.

I can 100% confirm that USB headset passthru from 18.04 KVM host to a 21.04 Ubuntu guest VM works.  

After the VM is running, from the menu at the top of the VM window, select **USB Redirect Device** - I see 2 options there. a PS2 --> USB converter and a Plantronics 780 headset. I check the "plantronics" - "OK" - then look inside the VM sound options.  I'm using **pavucontrol**.  As soon as the tabs are switched, the new Plantronics GameCom 780 shows up under the "Configuration" tab. I disable the "built-in audio" to be 100% certain only the headset gets used.  Ok, output and recording is working.  The output is good, similar to what I hear on the host.  Recording my voice is clearly showing hiccups as the VM context swaps in/out while running.  Initially, I'd forgot that the microphone was muted. Wasted about 3 minutes on that while watching the monitor levels in pavucontrol.  Based on this, I wouldn't use the microphone under a VM for any voice anything.

Inside the VM, I was never able to get the build-in microphone device to show up.  I did see a "line in" option, but not a microphone.  Looks like some complex PCI-passthru using IOMMU would be necessary. I could be wrong.  If it were me, I'd buy a cheap, USB mic that supports Linux for $10.

---

### Post by QIII on 2021-07-01
Threads merged.

---

### Post by EngineerStrange on 2021-07-01
Okay in my case also I am unable to use the system mic. I don't know if earphone mic will work as I haven't tested.

---

### Post by 7-vric-8 on 2021-07-02
Virt manager, known boxes are hypervisor interfaces which let you graphically change properties of virtual machines. xen and kvm are hypervisor's. I'm currently working with xcp-ng as a replacement for kvm in my personal and production environments. So far it is so much easier to work with than KVM. Yes there is a bit of learning curve but it's worth it.  Take a look at xcp-ng (hypervisor) and Xen Orchestra (tool for managing xcp-ng environment)

---

### Post by TheFu on 2021-07-02
> **7-vric-8 said:**
> Virt manager, known boxes are hypervisor interfaces which let you graphically change properties of virtual machines. xen and kvm are hypervisor's. I'm currently working with xcp-ng as a replacement for kvm in my personal and production environments. So far it is so much easier to work with than KVM. Yes there is a bit of learning curve but it's worth it.  Take a look at xcp-ng (hypervisor) and Xen Orchestra (tool for managing xcp-ng environment)

XEN-xcp is great if you have server-on-server needs.

---

### Post by EngineerStrange on 2021-07-03
Does the system microphone and camera work in xcp-ng?
P.S. I have checked a few things now mic is working. Btw do u know if I need to create a virtual phone in virt-manager in order to use AVD with KVM?

---

### Post by MAFoElffen on 2021-07-04
> **7-vric-8 said:**
> Virt manager, known boxes are hypervisor interfaces which let you graphically change properties of virtual machines. xen and kvm are hypervisor's. I'm currently working with xcp-ng as a replacement for kvm in my personal and production environments. So far it is so much easier to work with than KVM. Yes there is a bit of learning curve but it's worth it.  Take a look at xcp-ng (hypervisor) and Xen Orchestra (tool for managing xcp-ng environment)
I know this is  sort of an off-subject side-commet, but someone openned the door to it... I've been biting my tongue for a day, since you posted this... Just thought I'd talk politely about the elephant in the room..

Xen, XenServer and Xen Cloud Platform are not the same things and shouldn't be be used universally as such. It confuses people, who don't know the difference.

As such, Xcp-ng, in practice,  is a dedicated machine(s) solution. Just like vSphere is. Both are meant to be headless, and managed from other machines, remotely. Yes, it does have http management, so you don't have to have a full loaded machine to install XenCenter or XenOrchstrator, because both of them are hogs, when it comes to resources. All of those are remote access management. The VM's are meant to be access from other machines, remotely, hence "Cloud Platform".. There are many pieces to it. Hence your comment on that it does have a learning curve. Though... this is not a simple recommendation to the OP, who is looking for an easy, one machine in all, solution to replace using VirtuallBox on his laptop... So he can do video calls. Agreed?

My question to you, as an Xcp-ng user, RE: [Xcp.ng Organization Blog- "Thoughts about CentOS & XCP-ng future"]("https://xcp-ng.org/blog/2020/12/17/centos-and-xcpng-future/")

RedHat, which was swallowed up by IBM, Swallowed up full control of CentOS. They announced almost a year ago, that CentOS* * was dead = EOL in 2021.. That betrayed where they said it would be supported through 2029. Xcp-ng is CentOS kernel based. It's not like the "old" XenServer, where you could install/build to other Kernels. It is Kernel brand/version specific to just Centos. Stable is to CentOS 7. Development was CentOS 8.

A year ago, the announcements on CentOS, was that CentOS* had stopped, and direction changed to CentOS8-Stream, which doesn't have anything to do with Xcp-ng. RedHat further said that any and all support to Xcp-ng would be only by their own approval, on a package by package basis... With me so far? Since RedHat has owned KVM since 2008, and their focus on Cloud Platforms is OpenStack and OpenShift, where do you think their focus with Xcp-ng is?

In 2017, Amazon EC2 went from Xcp-ng to KVM. Amazon EC2 is now completely KVM based. So technology trend-wise, your shift from KVM to Xcp-ng seems, well... Against the flow(?)

IMOA: XenServer (DOM0), technology-wise, was an early exploit, until hardware virtualization was worked out. KVM and LXD incorporate the use of hardware virtualization now natively in the Linux Kernel, without having to do that "exploit" anymore.

You might say, then there's Cintrix... the company that sells and own's it's commercial interests... Which for over a year their stocks have fallen over 17% a share, and their earnings have been falling since also. In the past year, there are no new answers or changes to any of that. Not sure IBM cares.

So as a user of Xcp-ng, how do you see that? You really want to drag a new user into something complex, that does not have the hardware (he has a laptop), that may not have a stable future? Are you, yourself, looking at other virtualization options?

I myself have personally spent years supporting OpenSource Projects that went away, or have not been the same, when the business interests shifted behind them. Just saying. Just curious.

---

