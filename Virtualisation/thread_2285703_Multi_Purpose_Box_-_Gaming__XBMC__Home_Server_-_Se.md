---
title: "Multi Purpose Box - Gaming / XBMC / Home Server - Setup Questions"
date: 2015-07-08
forum: Virtualisation
---

### Post by sapo916 on 2015-07-08
So I'm building a home server (i5 with VT-d, Nvidia GTX 570) that will be sitting in the living room and hooked up to my TV. I'm interested in doing the follow with it.

[LIST=1]
[*]XBMC and misc. applications through the IGP wired via HDMI to my TV, I was thinking to use Kodibuntu for this as the Host OS. 
[*]A headless gaming windows 8 gaming VM using KVM vfio-vga passthrough which will be accessed through steam in home streaming.
[*]A various assortment of windows 2012 server VMs that I will spin down as needed. This is for home lab purposes so I can experiment with solutions for work clients.
[*]One or two linux public facing server VMs that will probably stay up 24/7 for my personal projects.
[/LIST]

I'm aware that the vga passthrough can be challenging to setup. I really liked using proxmox when I was testing it due to the great web interface. I believe to be able to use the IGP hardware acceleration for XBMC I need to install it on the host OS? If I can somehow have XBMC hardware accelerated as a guest OS alongside my gaming VM I would probably lean towards that solution.

I'm aware of tools like virt-manager to help manage the VMs, are there any simple tools I can install on the host that I can use to remotely manage the VMs as to not disturb my host OS if I'm using kodibuntu?

Appreciate any advice in regards to this, I will start playing with this on Friday.

---

### Post by KillerKelvUK on 2015-07-08
I've never run Kodibuntu but if you're wanting to build a virtual host I would suggest a vanilla server variant of Ubuntu (recommend 15.04) as this is guaranteed to enable to vm features/functions needed.  If you want to then run XMBC/Kodi on top of the host this can easily be achieved by installing a desktop like Unity or XFE and then just installing Kodi via the PPA.

If you use something like KVM as the VM core then the out-of-box management tools live in the command-line (CLI) using 'virsh', your requirements for remote administration of the host are then achieved using SSH to remotely access the hosts shell.  Note here that virt-manager can operate remotely over ssh tunnels, so if you'd prefer to minimise your CLI involvement then virt-manager is the way to go however if you're intending VGA passthrough you absolutely will need to get comfortable with CLI for virtual machine admin as well as other host OS customisations.  There are other web-admin interfaces for KVM you can explore...check out the KVM website which has a consolidated list of 3rd party admin tools, however in my experience these generally provide only basic functions or require significant installation and maintenance processes that make them less preferable to virt-manager.

I personally would recommend you separate XMBC/Kodi off the host completely, not even vm it and use a separate device to drive kodi on your TV e.g. a Raspberry Pi or an Intel Nuc...lots of options here.  Running Kodi on the host you may find issues due to your requirements for a  gaming Win8 vm...Nvidia passthrough is notorious for introducing VGA arbitration issues that affect the host IGP, there are methods to minimum/remove this risk but the requirements are quite prescriptive needing OVMF on the vm, EFI capable pass-through card and a heap of luck!  Alternatively change your gaming vm to a headed one and run Kodi in that but I suspect you want to do Kodi and gaming at the same time which might be too much for your rig to handle?

---

### Post by TheFu on 2015-07-08
Ok - I'll share my ignorance. ;)

I just swapped a completely silent Kodi+plex server machine (AMD E350) for an Intel G3258 machine with a stock cooler - about 3 days ago. Talk about noisy!!!!!  It is louder than the projector it connects with - throwing 100 inch hidef screen. Too distracting. Looks like a $50 player is in my future to get silence back for watching TV/movies.

I cannot imagine the noise from a Core i5 with THAT GPU.  Water cooling? I would keep the PC in another room just to manage the noise.

My kodi machine has just the projector and a usb dongle (remote control) connected. All other management is done through ssh.  About once a year, have to connect a keyboard to deal with a boot issue. Last time it was a USB drive that the OS wanted to boot from first - before the internal SATA drive - couldn't see the error because the HDMI output doesn't get pushed until grub is displayed, not from the BIOS screen. I still need a solution for that.

Will you be connecting the TV and the monitor or will you try to use an HDMI switch to the TV? The 2 video outputs - 1 from each card - need to be available.

Webserver - depending on the website, this could be trivial or power sucking. Plus internet traffic could impact the online gaming latency. Might not be any issue at all.  Most gamers willing to go through that much effort to get video-passthru working won't want anything unnecessary running.

In the end, there isn't any way to know if or how great this will work without trying it on your specific setup.

---

### Post by sapo916 on 2015-07-08
I am comfortable with using the CLI. Only reason I enjoy a GUI is to monitor everything at a glance. I don't expect heavy use out of the gaming VM and XBMC, so I don't anticipate a performance problem, it's for the occasional users in my home. The primary goal is to setup a lab environment for my other servers. Thanks for the heads up on the arbitration issue, looks like I have an interesting weekend ahead of me.

---

### Post by gordintoronto on 2015-07-09
Depending on what you want to run in the WS 2012 VMs, you will want lots of memory. 16 GB might be marginal!

---

### Post by Bucky Ball on 2015-07-09
> **KillerKelvUK said:**
> ... I would ... (recommend 15.04)...

What is this thinking based on? LTS releases are generally recommended for servers as you ordinarily would not want to be upgrading a server every six months. What functionality does 15.04 bring to the server environment that 14.04 LTS does not? New functionality for running VMs? Is it functionality that warrants upgrading the server OS every six or nine months?

15.04 support ends January 2016 at which point you will need to upgrade to 15.10. 14.04 LTS is supported until April 2019. Unless there was a veeeery specific reason for an interim release, I know where I'd be going. :)

---

### Post by KillerKelvUK on 2015-07-10
> **Bucky Ball said:**
> What is this thinking based on? LTS releases are generally recommended for servers as you ordinarily would not want to be upgrading a server every six months. What functionality does 15.04 bring to the server environment that 14.04 LTS does not? New functionality for running VMs? Is it functionality that warrants upgrading the server OS every six or nine months?

15.04 support ends January 2016 at which point you will need to upgrade to 15.10. 14.04 LTS is supported until April 2019. Unless there was a veeeery specific reason for an interim release, I know where I'd be going. :)

Hey Bucky, if your requirements are a true server deployment then I completely agree you want an LTS deployment for all the goodness that brings.  However if you're looking at game vm's with VGA passthrough then the stability of LTS releases go against the bleeding edge features of KVM and QEMu that are required to enable most passthrough solutions.  If you're using 14.04 then you'll need to look at building your own binary for qemu at the latest version as the stock repo for 14.04 has an older but more tried and tested version (specifically for LTS).  Yes you could map in someones PPA where they have built it for you, however my experience is these tend to run into wider dependency problems with the packages.  Ergo if you're doing gaming vm's and VGA passthrough you aren't going to be running a production mail server etc on the same box therefore the driver for LTS in my opinion is diminished in comparison to the latest release which has latest and more bug fixed versions.

Specific challenges here are that 14.04 only packages qemu 2.0 and for Nvidia vga passthrough you're going to need qemu 2.1.1 minimum which introduces a feature to hide KVM from the guest.  This is needed to get the Nvidia drivers to work inside the guest which is all about the (code43) error which is prone to nvidia passthrough.

---

### Post by Bucky Ball on 2015-07-10
Ok. Understood. ;)

---

