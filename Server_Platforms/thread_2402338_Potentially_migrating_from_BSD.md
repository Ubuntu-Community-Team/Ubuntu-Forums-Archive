---
title: "Potentially migrating from BSD"
date: 2018-09-28
forum: Server Platforms
---

### Post by jayz99 on 2018-09-28
Hi All,

I'm running FreeBSD on my server and getting ready for a major upgrade. New hardware and FreeBSD 12.0 when it comes out in November.
Recently I've started considering trying a Linux server distro, primarily because of:

[LIST]
[*]Development velocity. 
[*]Broader code quality reviews. 
[*]Better hardware support. 
[*]Potentially easier day to day management. 
[/LIST]
 I'm trying to determine whether Ubuntu server might be the right product to try. The only real alternative I see is CentOS/RHEL. Ubuntu's widespread use and cloud availability is a testament to the value of the system, however I would appreciate some guidance from yourselves in order to make an informed decision:

[LIST=1]
[*]One of my requirements is to have a set of internal and external services. The external services are relatively minor and the internal data held on the server needs to be tightly controlled and segregated from the external services. The FreeBSD jails mechanism is a great way of achieving this. I've read a bit about LXC but unsure whether it can achieve the same level of secure segregation. Opinions are polarised so if anyone is able to provide me with a definitive answer that would be most appreciated. 
[*]BSD systems are well known to be relatively secure by default, especially OpenBSD. The design logic differs from Linux as well - Linux is just a kernel while individual distributions control application and service mix. BSD is an integrated set of applications plus the kernel. This contributes to system security. What are Ubuntu's security credentials? How does it stack against other distributions? Is Ubuntu security 100% a hardening exercise or are there sensible defaults? What about the fact that Ubuntu derives code from Debian - doesn't that create a natural lag in responding to vulnerabilities? 
[*]ZFS. Apparently it's supported by Ubuntu. How robust is the implementation? Can anyone compare ZFS usage on FreeBSD versus Ubuntu? 
[*]Stability. BSD is rock solid and very well tested under heavy workloads. What are your experiences with Ubuntu server? Especially versus other platforms? 
[*]What is the main driver of Ubuntu's popularity? Let's exclude cloud and pace of deployment from this question. Are there compelling technical reasons vs Debian, SUSE, RHEL, etc.? 
[*]Does Ubuntu server offer any services built for integration with Ubuntu desktop? (Much like Windows server offers a set of Windows-only, native services for Windows clients) 
[/LIST]
 Thanks in advance!
Janusz

---

### Post by TheFu on 2018-09-29
Excellent questions.  I haven't used BSD for anything other than routing in a few decades.  The main reasons for my choice was hardware compatibility and a 1000x wider range of software.  But the same could be said for why people still run Windows.

Opinions:

1.  BSD Jails are a little more than Linux chroots.  Linux containers, like LXD and docker add kernel segmentation for different critical resources like RAM, networking, and device access.  If you want more proven segmentation with a longer period of proof, stick with HVMs, like KVM+QEMU.  It is possible to create non-secure VMs and non-secure containers.  Dealing with containers is very different from dealing with chroot or VMs.  You can find how-to videos from many conferences on youtube.

2. Ubuntu server doesn't enable any services by default, unless you specifically request them. The kernel firewall doesn't have any rules in or out unless you add them.  If you install openssh-server, then you should secure unwanted connection attempts in some manner.  That applies to Apache, Bind, MariaDB, any service.  Assume you need to add any firewall rules that you want.  Some services will NOT bind to public IPs. This is often confusing for people new to Unix-like systems.

3. I don't use ZFS on Linux, but that is mainly because I'm ingrained in the LVM+file system method.  I think everything works well on  64-bit Linux, except the CIFS implementation. Fixing that seems to be a low priority.

4. Linux servers have been rock solid since the mid-1990s.  I've had servers with over a year of uptime.  They don't fail unless there is a hardware issue or bad driver.  If you have crap hardware with terrible drivers, you might only get 3 months of uptime.
```
$ uptime
 12:07:28 up 32 days,  4:34,  3 users,  load average: 1.25, 0.35, 0.12
```
I need to reboot that system. Got a new kernel earlier in the week.

5. No way to know why Ubuntu Server is popular for everyone.  I like it because LTS means LTS.  I get enough useful life from a server where they only patch security issues, not feature additions.  I prefer APT over RPM, but that's probably because I got into RPM-hell in the late 1990s.  In the Linux world, you generally pick the distro family by the package management system.  
Many people using Ubuntu Servers are developers who started out on the Ubuntu Desktops. Compared to Fedora, all the different Ubuntu desktop flavors are very nice and approachable.

6. Ubuntu supports standards. NFS is NFS.  LDAP is LDAP.   If you are looking for some Ubuntu-only communications that only works within the Canonical family, there aren't any.   There are Canonical-only server products like Juju and MAAS for people with larger scale needs.

I suspect you will be pleased with lxd (lxc is older), but if you want more industry standard, then you'd want to deploy using docker and Kubernetes solutions, probably.

For cloud deployments, I usually see Ubuntu Server at developer-centric companies.
At corporate sites in the USA or any financial company around the world, it is RHEL. The farther you are from the USA or finance industries, the more likely you will see non-RPM-based Linux, like SuSE or Debian or Ubuntu.  I remember walking into a site with Gentoo. The CEO was the founder and he had decided that anything less than perfectly compiled for the hardware wasn't right. I didn't end up working there.  Having a custom build for 1,000 different hardware platforms seemed crazy to me.

In these forums, you'll see mostly desktop-only users, so beware.

Hopefully, some other opinions will get posted. We are all limited by our experiences.

---

### Post by mastablasta on 2018-10-01
> **jayz99 said:**
> 
[LIST=1]
[*]What is the main driver of Ubuntu's popularity? 
[/LIST]

popularity of Ubuntu is because it made desktop linux easy to install for those that never had linux before on their PC. it was also backed up by a company that at first aimed mostly at home / desktop users.

the easy to install is then followed by a set of applications that make life easier for the user. in the past years this slowly also moved into the server area as well. it started with stuff aimed at smaller servers and gradually they developed easy to use apps for larger scale deployments.

as Ubuntu moved from home PC users to smartphones and then to large servers and business users, many desktop users and newbies moved to Linux Mint, which is aimed specifically to satisfy the needs of desktop users. Mint is basically Ubuntu with another desktop and some settings changed along with a couple good tools for easy desktop use. there are a couple of similar distros, but Mint is the most popular. Mint is not aimed at servers as far as i know.

i do not think there is any lag in security patches. many times issues are found on Ubuntu and then patches are made for Debian as well. Ubuntu is not Debian it is just based on it. it can sometimes use same resources or uses same methods. this is because it follows standards.

---

### Post by jayz99 on 2018-10-01
Thanks Both. I agree - RHEL is most often seen in finance. I happen to work in finance myself and 9/10 distros used happen to be RHEL. Interesting point re being developer centric. I've not considered that, but my focus in terms of distros would always be on the sysadmin side. Understandably... since I'm trying to manage a server and all... :-)

I've given thought to all of the above, and various other materials (e.g. this doc from Def Con: [https://www.defcon.org/images/defcon-13/dc13-presentations/DC_13-Potter.pdf](https://www.defcon.org/images/defcon-13/dc13-presentations/DC_13-Potter.pdf)) and concluded that I don't see sufficient evidence that migrating to Linux would be a material improvement in my case. 

I feel I'd benefit from more software but miss out on security features. While better hardware support would be good, I don't really need it that bad because I'm deploying BSD on server grade equipment which is very well supported. What I'd like to change is the fact that FreeBSD now forces the migration between minor releases (e.g. 10.3 to 10.4), but Ubuntu is not a rolling release either and LTS is supported as long as the FreeBSD main release code branch - 5 years.

The community aspect plays an important part in my decision as well. I do agree that it's mostly desktop users on here and in fact on most other sites. The FreeBSD community is focused on the server application of the OS and very, very experienced.

Thanks again. :-)

---

