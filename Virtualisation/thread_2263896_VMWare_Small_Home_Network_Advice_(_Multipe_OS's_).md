---
title: "VMWare Small Home Network Advice ( Multipe OS's )"
date: 2015-02-04
forum: Virtualisation
---

### Post by bellasnaru on 2015-02-04
Hey guys

First up, i wasn't sure if this is the right section to post this, so admins move my post if you feel its necessary

Recently ive been studying at TAFE Australia ( similar to college in america ) doing a certificate IV in networking administration and we barely work with linux much unfortunately they base all their teaching around Windows Server 2008 R2 so I've become extremely used to using that, simplistic tools and Active Directory

By the way, all this work we do is done within a VMWare workstation 10 on a host computer, they are teaching us heavily about Virtualization, so my questions are to do with servers and Virtualization

So basically what im saying is i've become fairly used to a Graphical Interface and ive looked into Ubuntu server and it seem's all CLI Based

But here's what i want to do

I want to use my Laptop, an i7-3610QM Processor and 8GB of Memory as my server box, and in the server box ( my small laptop running VMWare workstation )
 i want to run multiple Virtual Machines, the main one will be running Linux, the other 2-3 will run Windows 7 similar to a tiny business

I want to setup the Linux VM to host it all. to run DHCP, users, groups, and be able to control the windows VM's remotely, such as booting up and telling all 3 VM's at the same time to run a software installation like word or office

So my question comes down to, what software on Linux is suitable for this, and what distro would be best for me to use that can do all this with a Graphical interface/Desktop ( im not into the Command Line part of the course yet )

---

### Post by TheFu on 2015-02-04
I wouldn't touch a desktop virtualization tool to run servers inside a business.
I run IT for a  few small businesses - we use Linux for everything ... except the accountant uses Windows for Quickbooks.

KVM + libvirt + virt-manager - that's how I run virtual machines. They can be managed securely from anywhere in the world through virt-manager ... but I avoid using the built-in desktop console. RDP performance sucks compared to NX.  The servers are headless, so either shell or DevOps tools like Ansible are used for almost everything.  I do provide remote desktop facilities using x2go for selected users who travel all the time. They use it as their daily work desktop, performance is pretty good, as long as no video is needed.

Best practices have a different server for different services. I wouldn't put my LDAP/Kerberos stuff on the same box as DHCP.

I'd also only have 1 Windows install for MS-stuff and encourage the use of LibreOffice as much as possible.

I'm glad you are stepping away from MSFT. Many companies don't use any of their software these days. It just isn't necessary. The same goes for VMware/Oracle/Adobe/Apple. Not necessary to use any of their software either.

The hardest part about your setup is using a laptop.  Virtual machine servers really, really, need to have wired ethernet connections that are on all the time. Don't use wifi.  Switching between that will be a hassle for you.

Now, you just need to unlearn all the microsoft ways of doing DHCP, networking, server management, .... point-n-click.

And don't forget that the most important thing for any administrator is having daily, automatic, versioned, backups, that can be restored. If the restore isn't tested, it isn't a backup.

---

