---
title: "Quickbooks EDS 9 on Ubuntu 8.04.2 LTS"
date: 2009-04-07
forum: Server Platforms
---

### Post by gblackburn on 2009-04-07
Hello all,
Let me begin by saying this is my first post on the Ubuntu forums so excuse me if some of this is obvious or already in a thread (couldn't find much QB info). What I have found is a guide in the community documentation- [https://help.ubuntu.com/community/Quickbooks%20Enterprise%20Data%20Server](https://help.ubuntu.com/community/Quickbooks%20Enterprise%20Data%20Server) and I wanted to know is how many people have tried this, and if so how were the results?

Most of my work experience has been Windows-based and I have never set up a Linux-based server in an actual production environment so I guess I am a little weary. I have traditionally believed that Linux is better for large companies that can afford to customize everything, but with the availability of QB data server on Linux many small businesses can save thousands on licensing fees.

So here is my situation:
A small company co-owned by my boss needs a central Quickbooks/filesharing solution on the cheap and they are about 1000 miles from where I work. I need to set up this server and two desktops and ship them out to the location where I will walk a person through setting up the basic connections. All the machines are running XP and Vista (6 and 2) and since there are no public IPs available I guess I will just ask users to fire up Crossloop on their Windows desktops when I need to remote in. Basically, I'm hoping I can set up the server and not have to mess with it for years. (watch Intuit drop Linux support now I'm doing this)

If you are going to tell me to run Linux on the desktops, please save your energy as it's not even an option for the users at this location. I'm really only interested in Linux on the server side because there are a dozen custom Windows apps they use and they work very well.

If you have any experience in this or are interested in doing this as well, your comments are welcome.

Greg

---

### Post by HermanAB on 2009-04-07
Use VMware and make Windows 2003 server VM running Quickbooks.  This way, your installation is hardware independent and users can log into Quickbooks using RDP or VNC.

---

### Post by windependence on 2009-04-08
I'll second Hermann's recommendation. Use VMware ESXi and then you will be able to control all the virtual machines from your remote location. You can even install new VMs with different operating systems right from your home PC or laptop using an image or your CDROM.

I'm not going to suggest running Linux desktops because Quickbooks has no support for that at this time, however, if they did, it would be a great combination.

To be able to access the VM control panel from the outside with a dynamic IP, you will need to sign up for a service such as no-ip.com.

-Tim

---

### Post by gblackburn on 2009-04-08
So you guys are saying I should run Quickbooks from a 2k3 virtual machine on top of Ubuntu? I would think if I was going to run Windows Server, I may as well just install it as the main OS anyways right? I could see some real security improvements with this setup not to mention less QB licensing but wouldn't I still have to get a 2k3 license? Or maybe I can just use an XP VM?
Either way, I'm starting the 8.04 install this morning and I'll see how things work in VMware.

Thanks for the comments-
Greg

---

