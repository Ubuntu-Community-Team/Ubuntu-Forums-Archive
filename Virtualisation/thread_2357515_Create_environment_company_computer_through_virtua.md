---
title: "Create environment company computer through virtualisation on ubuntu server"
date: 2017-04-03
forum: Virtualisation
---

### Post by sed_faster on 2017-04-03
Hello folks,

I only know install virtual box and create a virtual machine on Ubuntu desktop, with environment graphic desktop. I want learn how create virtual machine in ubuntu server (headless) through common desktop with environment Ubuntu. The goal is use the ubuntu server to management all my virtual machines and access them through my desktop or laptop. Another goal is create a networking, simulate environment company, with my ubuntu servert to create communication between machines with windows 7 and Linux.

How and what can I read to learn more about this matter? I remember which my knowledge about this topic it is very little and I am a newbie in Linux and even more on ubuntu server's.

Thanks

---

### Post by TheFu on 2017-04-03
I wouldn't use virtualbox for this.  You'll need more advanced capabilities than vbox provides.

Your question is huge.  You'll need to eat it like we eat an elephant.  1 bite at a time.

I'd start by listing all the capabilities you want to create. Perhaps this would include a list of clients and servers with the exact services/listeners desired.  The way that most enterprises do things often requires spending $100,000s in software. At home, we can use enterprise-grade, but F/LOSS versions of similar software to achieve the same results.  Enterprises assume they need to pay for the software, which is really just $100K+ of ignorance, IMHO.

Usually, starting with network management is first, so DNS and DHCP services.  Then branch out to centralized authentication and authorization with LDAP/FreeIPA servers.  By that point, you'll need daily, automatic, backups to recover from mistakes.  Then file (nfs/cifs) and print (ipp) servers are usually next, followed by email servers (SMTPS) and services for email clients to have access (IMAPS).  Then you'll probably need some key management for ssh and VPN management with a VPN server (openvpn using IPsec).  Then document management, CRM, ERP, project management, and perhaps VoIP system(s).  

About this point, you'll realize that the deployed security architecture is flawed and you'll need to restart everything with that at the front - needing 4+ different network zones for the different services.  You'll probably think that vlans are a solution, until you learn that vlans are suggestions, not the same as physical separation.  Separate networking for internet-facing, back-ends for those services, desktops, backups and storage networking - perhaps split those by different security zones too.  Storage for internet facing systems shouldn't be mixed with storage for internal-only servers, right?  Don't want to allow your high-risk systems to become a bridge to all the storage for the company.

And you'll need to patch and maintain these systems, so devops will seem like the best answer - you'll need to learn that (puppet/chef/ansible/salt/rexify) with a solid scripting language to automate more.  All of this will mean you'll be able to rebuild your infra in a few hours, when you have it all done.  "Done" will never really happen, since everyone else inside the company will be trying to push new things.

So ... really, before you start, just learning to be a power-user on Linux is the first step, [http://blog.jdpfu.com/2017/03/31/learning-linux-condensed](http://blog.jdpfu.com/2017/03/31/learning-linux-condensed) , followed by the 6 admin classes.  That should keep you busy for the next 2 yrs, if you are committed. ;)  Most people will spend 5 yrs learning that much stuff, however.

---

