---
title: "KVM issues"
date: 2014-07-25
forum: Virtualisation
---

### Post by Lappert on 2014-07-25
So I just installed KVM on Ubuntu 14.04 server with KDE desktop. I then installed Win7. Now just poking around, but I see a few issues right away.

I created a 32GB drive which should be OK for local purposes, but I will need to access the larger drives on the Ubuntu host. Much of our larger data is kept on additional data drives. 

The Win7 install only shows drive c :and d:. (d is the cd drive, but seems to have a bunch of windows files ... maybe the install .iso)

So how would I access the drives on the host box? I tried ftp (192.168.1.x) and that didn't seem to work. The net connection (Workgroup) shows up but fails to connect.

Also, it seems the Win7 can't access the speakers on the host box. Any thoughts there?

Thank you.

---

### Post by TheFu on 2014-07-25
Treat the machines as separate and use whatever file sharing client/server method you like.  The client and server should be on the same subnet for the least issues with that.  Most people would use samba and CIFS connections for a Linux server and Windows client, but there are other ways.

Can't help with the audio - my KVM servers are headless - audio is sent through the remote desktop client connection used.

---

### Post by Lappert on 2014-07-25
Thanks... here's another issue

When I try to play solitaire on Win7, I get a pop-up that says, "Hardware acceleration is either disabled or not supported by your video card driver, which could slow game performance...."

OK, I have a fairly hefty video card: Asus Geforce GTX-670. So I don't think that's the problem. I enabled hardware virtualization in my bios in order to get KVM working.

I also went into Win7 Control Panel > Display > Change Display Settings > Advanced Settings > Troubleshoot > Change Settings and then set hardware acceleration to full.

But it doesn't fix the problem.

Any thought on this?

---

### Post by Lappert on 2014-07-25
On the connection issues, I can connect to the net on the Win7 VM.

I have tried SFTP (which usually works), FTP (just in case) and Samba in attempts to connect from and to the host to the guest VM. The user/PW is the same on both. The ubuntu host is 192.168.1.x (checking ifconfig) and the Win7 IP is 192.168.122.x.

Nothing seems to work.

I've seen some posts (on other forums) suggest that I need a bridge. I don't know if I have that or not. Is this necessary; if not how would I go about getting access?

Thank you.

---

### Post by TheFu on 2014-07-25
If the original question is answered, please mark the thread as solved.

The real video card doesn't matter to VMs at all. It sees virtual hardware for everything you do not specifically pass thru. Review all the other people trying to passthru a dedicated video card before you attempt it. It is non-trivial, requiring specific BIOS, specific CPU support and specific kernel support.  I don't do it.

---

### Post by Lappert on 2014-07-25
Thanks for your help and insight. Unfortunately, neither issue is resolved.

---

### Post by KillerKelvUK on 2014-07-26
To access files in your Win VM that are stored in a mount on your linux host I'd recommend you use samba as the server on the linux host.  There are lots of guides to installing a samba server in ubuntu, make sure you install 'libpam-smbpass' as this will synchronise the linux host user accounts and passwords with the samba server so you know what the credentials to be use are within the Win VM.

As TheFu said, make sure your linux host and VM's are in the same subnet to minimise issues connecting the samba server to client...one way I'd recommend is to us virt-manager (gui tool) to configure your KVM host.  In Ubuntu 14.04 they have worked out the networking kinks and so this tool can easily create a virtual bridge to put your host and VMs into.  Again a little googling here e.g. [http://www.techotopia.com/index.php/Creating_a_CentOS_6_KVM_Networked_Bridge_Interface](http://www.techotopia.com/index.php/Creating_a_CentOS_6_KVM_Networked_Bridge_Interface), whilst this is a CentOS guide the GUI steps are consistent and you should be able to map the process into ubuntu.

For audio within a Win7 VM this all depends on how you are accessing the desktop...if you are using VNC then forget it as this can't do audio.  Your options are RDP, SPICE, a.n.other variant...ubuntu 14.04 comes with the Remmina client which supports RDP...you need to configure the connection as SOUND=REMOTE and install the correct sound drivers within the Win VM.  However the best audio/video performance I've found for a Win_**7**_ VM (not tried any other Win vers) is SPICE although other options exist which forum members do recommend.

---

### Post by Lappert on 2014-08-03
Sorry to take so long to reply (out of town).

I am able to connect from the VM to the host using Total Commander (a windows file manager) and its SFTP plugin. This works, but it's tentative. Going the other way, from Krusader, I can connect using smb: but again, it's tentative and sometimes does not work.

The connections are buggy, slow and really a kludge, not a solution.

I don't know if this is the same as having a samba server in Ubuntu as you recommend. But checking Software Center, I already have SMB/CIFS installed, but I can't find an app to get it up and working. But how would I check to see if VM/host are on the same subnet (I really am new at this). KVM came with virt-manager and I use that to start/.stop the Win7 VM.

---

### Post by Tadaen_Sylvermane on 2014-08-04
You have a few issues here.

First if you want the Windows VM and Host on the same network then you need to create a bridge and change the network card to the bridge instead of the virtual network created by default. As it sits now the VM is on it's own private network with KVM kind of acting as it's router. Virt-manager is easy mode for creating a bridge.

Second, as mentioned whatever hardware beyond your cpu and ram is on the host really is irrelevant as far as the VM is concerned. You can have quad sli gtx 780's and it won't matter. It virtualizes the hardware for the VM. Generally speaking gaming of any kind on a VM without a vga pass through setup is pointless and a waste of your time. 

There isn't a app to make smb work that I am aware of. You need to edit configuration files.

All that being said. I can't help but think that maybe you should install a desktop ubuntu and use virtualbox until you understand the basics of virtualizing. KVM is not near as user friendly.

---

