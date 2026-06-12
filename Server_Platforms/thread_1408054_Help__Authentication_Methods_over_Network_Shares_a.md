---
title: "Help : Authentication Methods over Network Shares and SFTP"
date: 2010-02-15
forum: Server Platforms
---

### Post by Ares545 on 2010-02-15
Hi all,

I run some IT systems for my schools Engineering student organization.

We are upgrading our systems and I just purchased a new server system which I am configuring.

I am using Ubuntu 10.04 Lucid Lynx and the new likewise-open packages.

**The points I bring up following this sentence are to fulfill this final goal **: Get SFTP, SSH, and Network Share's over our private network all using the schools Active Directory for auth and it's groups to derive privs.

So... Here's what i've done and what i've tried to do.

1 ) I set up likewise-open and got it to join the domain. When I do this I can ssh to localhost as 'schoolnetwork\ADname'. So that part works (hurray). To get a network share to use these same auth methods I have tried installing likewise-open-server. Everything launches find and the daemons run, but when I go into computer management on a windows server to set up the actual shares, I get permission denied. The account it is giving permission denied to is the same AD account that join likewise-open to the network, so... what is going on.

2 ) Samba, fail. I can't seem to get samba to run on this machine at all, which is strange because even my Samba expert was puzzled. It just won't let Samba join the domain properly, and due to this, I want to keep on the newer likewise package... unless I have to switch to this.


Any ideas on how I can get the lame likewise-open-server to work?

Thanks!
Zach

---

### Post by HermanAB on 2010-02-16
Howdy,

Here is some debug information:
[http://www.aeronetworks.ca/LinuxActiveDirectory.html](http://www.aeronetworks.ca/LinuxActiveDirectory.html)

---

