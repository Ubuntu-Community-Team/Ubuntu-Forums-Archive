---
title: "Landscape question"
date: 2023-03-14
forum: Server Platforms
---

### Post by eric-houtjes on 2023-03-14
Hi,

Hope this is the right place to drop my question.
We have this hybrid serverplatform consisting on rhel servers and Ubuntu servers. For every server that does not NEED to be RHEL we would like to move it to Ubuntu. However we are a bit lost on what to do with provisioning, managing, etc.
For RHEL and it's derivates Satellite is there. Expensive as hell and not really capable of managing non-rhel distros as well.

So we were thinking, why not try the other way around? But I cannot, anywhere, find much info on if this possible? Is Landscape capable of manging and )provisioning) non-rhel servers? Anyone knows?
I don't really want to pay for 2 lcm systems.

Cheers,

---

### Post by LHammonds on 2023-03-14
How many servers are you managing and what vm plantform?

I had a mix of Windows/Linux hosted via vmware/nutanix and with all Linux servers, I configured a generic Ubuntu Server with all my standard settings / scripts and converted it into a VM Template.  From there, I just right-click the template and say "Deploy"   Once deployed, I would terminal into it, change the static IP and the name in /etc/host and /etc/hostname and reboot.  It was then ready for whatever services I wanted to configure.

The worked well for my environment / size.  But if I were an ISP or enterprise with multiple hundreds of servers, I would look to Ansible and Puppet.

The template deploy was extremely handy...and the ability to VM snapshot a server during an experimental or complicated install with multiple steps, it was extremely easy to rollback to a prior step if I needed to undo an install / step.  Once everything is working as intended, then I'd remove all snapshots and put the VM into the backup rotation.

**EDIT**: Oh, and once a month or so, I'd convert the template back into a VM, boot it up and perform the OS updates / patches, then shutdown and convert back into a template.  This would ensure newly deployed servers would have very-little to update.

LHammonds

---

### Post by TheFu on 2023-03-14
I've shied away from Landscape, so don't really have a valid opinion there.  Same for Cockpit.  I don't like webapps handling system admin tasks.
 
You could go with a Linux distro agnostic tool for all provisioning.  Check out Cobbler [https://help.ubuntu.com/community/Cobbler](https://help.ubuntu.com/community/Cobbler) and pair it with Ansible for post install configuration.  Obviously, if you want paid support from Canonical, then Cobbler isn't the choice.  [https://github.com/cobbler/cobbler/pull/3250](https://github.com/cobbler/cobbler/pull/3250) Seems Cobbler support was added for 22.04 last fall.  I'm not deployed Cobbler here. tftp just seems "wrong" to me.

If it were me and I were in a RHEL shop, I'd stick with that family of distros to leverage existing institutional knowledge, since Ubuntu has made many different choices with their Linux versions, many of those choices conflict with RHEL. 

Depends on what you intend to run with these servers and how long their lives will be.  If you are replacing systems every few weeks and mainly use Linux Containers and have 1000 physical machines, my answer is different than if you have 3 physical systems, each a snowflake, that changes every 8-9 yrs.  Do you run well-supported-on-Ubuntu software or is it all custom code?   What sort of SLA are you trying a achieve.  For people coming from RHEL, they are often surprised as to which software they though was universal that isn't.  When it comes to enterprise in-house server and desktop support, RHEL and SuSE probably have more complete offerings than Canonical.  Canonical is more about desktops and cloudy deployments to VMs and containers than the others.

Don't assume that Canonical has a 1-for-1 replacement for everything that RHEL sells.  They don't.  Another example, if you use FreeIPA or the paid RHEL version of it, the IPA server doesn't run on Ubuntu.  It did for a few years, but that got broken.  Canonical decided that integrating with MS-AD was a wiser choice.  Definitely a valid choice for many of their paying clients.

For managing Ubuntu, **ansible** is what I use ... along with scripts from the last 30+ yrs from before "DevOPS" was a buzzword.  I've been to formal training by the other 3 major tools and just kept seeing workarounds for dumb, self-inflicted, problems.  Perhaps those have been removed - it has been over a decade now.  OTOH, Ansible (straight CLI, free version) does everything I've needed, even with some of their DSL changes that seemed pretty foolish (sudo vs becomes, really?)  

In the last month, I've spun up more new systems on Ubuntu than in the prior 4 yrs.  Much is automated, but not all of it.  It takes about 20 minutes of my time to get a new system base up, holding deployment, backup accounts with ssh credentials and ready for customization. Then I take a snapshot. None of these were bare metal, BTW.  Bare metal installs take longer because we have different physical hardware with different NICs and vastly different storage. We don't have 1/3rd of our servers replaced every 4 yrs here.  I've worked placed where that was done.  For some paid software licensed on a per-CPU basis, the new servers were paid for by the less costly Oracle licenses while performance increased and power massively decreased, making it possible for even more servers to fit into the data centers without huge power infrastructure upgrades.

---

### Post by eric-houtjes on 2023-03-15
Thnx for the replies so far.
I cannot explain everything, but my team is managing a closed network of about 150 to 200 servers. Some of them Bare metal, some of them VM. Those servers are under very restricted security regime and are not allowed internet access. I can however use a platform proxy and have a server to be used for provisioning and patching connect to the internet via that (secure) proxy. So I want the server to be the place where repositories are mirrored, and provisioning is initiated.

I worked with satellite (& katello) in the past, and 1 of the key things that are very valuable is the fact that it is easy to freeze patchlevels. So it is simple to supply T or A env. with new patches while P is still on the previous level. By doing this one can use the same patchround over all servers since only the env. which has new patches will actually see an install. So this keeps the entire patching process very simple and straightforward and easy to manage. 

We would prefer to move to Ubuntu because RHEL chooses to rely on quite old softwareversions for many things. We can however not leave RHEL entirely because our main supplier only supports it's software on RHEL and derivates. Ans though there are some nice derivates, they usually have the same issue. Actually, I am still investigiating (quite new in this team, so just started this search) so I cannot tell how Ubuntu handles this software version policy.

As for our servers, I have to use Bare metal for some as poer requirement of the supplier. So as you an see is a bit a divers platform in which I want to bring as much ease of maintenance as possible. Hence the search for this LCM tool.

Were it RHEL (derivates) alone, satellite (or Foreman) would be perfectly viable. But I am a bit reluctant to have to LCM tools running, just because we have 2 differenct flavours of Linux. So I hope to find one which can handle them both, at least the basic tasks.

The patching itselves would be done with ansible. 
Hope this explains a bit.

Regards

---

### Post by MAFoElffen on 2023-03-15
In what you described, what you said your requirements are, and your constraints, I think you were probably looking at Self-Hosted Landscape, where you have a local-repo mirror: [https://docs.ubuntu.com/landscape/en/onprem](https://docs.ubuntu.com/landscape/en/onprem)

Note there, on this part (for Self-Hosted):
> 
Note:              Work  is being done to allow self-hosted Landscape to run on Ubuntu 20.04 and  22.04. This version of Landscape is undergoing development and testing,  and will be available in Q1 2023. Once Ubuntu 20.04 and 22.04 are  supported, self-hosted Landscape will still continue to be supported on  Ubuntu 18.04 until there has been sufficient time for customers to  migrate their environment.

That has yet to be updated... and Q1 2023 is almost over... Heck. 18.04 is almost EOS. The new version of Landscape beta was released in Oct 2022. [https://ubuntu.com/blog/landscape-beta-test-the-landscape-server-migration-to-ubuntu-22-04-lts](https://ubuntu.com/blog/landscape-beta-test-the-landscape-server-migration-to-ubuntu-22-04-lts)

I don't know how the beta went. And even though I could test it, or try it for free, I haven't. (sorry) So I have no experience with Landscape, and cannot say how it really is. (My past experience was with Ansible & Terraform.)

On rolling back updates, I do LVM2 and ZFS snapshots. I used to use a local repo mirror, then do updates to some test VM's for testing on, previous to release of the upgrades to the populous. If there were problems, then I would rollback via snapshots. That was a lot easier and faster than figuring out exactly what was installed to uninstall updates. Though I did that for some things.

I think if Landscape Self-Hosted was around 'then', I might have looked at it. But you are in a mixed shop. I don't think that Landscape will work for anything other than Ubuntu. Yes, I ran into Vendors that would only support their software if it was on RHEL... I feel that.

Using LVM LV's and ZFS datasets, I configure my servers to mostly isolate the system itself, so pieces can be flexible, and adapt (updates, rollbacks, etc) without affecting the other pieces... It didn't always work that way, but that was the intention.

---

### Post by TheFu on 2023-03-15
I've worked in an air-gapped setup.  Part of my job there was bringing in new software for just 1 project, not the OSes allowed on the different segments. 

There wasn't any Linux, so my knowledge doesn't apply. 

Heck, I don't recall any package management on the UNIX flavors at the time. Installation was a script + a tgz file.

For OS upgrades, there was an OS group that would build custom kernels and deploy them.  My development machine in my lab was on their list to get all kernel updates.  About once a year, They'd come for an hour and use dd to install the new stuff to the HDD. I was always short of storage on that system - it had a 2GB HDD and it had to hold all the software development tools for the platform locally. It was the only machine of that type and OS in our lab. We had at least 1 of everything there and supported 12 platforms with our custom software.

In the air-gapped buildings, there wasn't much commercial software that hadn't been customized.  Over 2K programmers were creating all the code used.  My team was 6 people. Oddly, we didn't allow bugs to exist more than 1-2 days. IF one was reported, it would be immediately fixed and released as soon as the paperwork allowed.  Usually, that would be the next day, but if there was a mission ongoing, or about the begin, we'd have to wait until it completed which could be a month later.  That only happened once and the issue was with some OS tools, not our code. The issue turned out to be self-inflicted by our admin due to backup software for the wrong version of the OS on the core server replacing the OSes libc for an older version of libc.  The OS vendor sent 2 of their kernel engineers in and it took them 2 days to figure out the issue (wrong libc).  I'd have never thought that backup software would be replacing a core OS library like that.

---

### Post by LHammonds on 2023-03-15
As I already mentioned, I do not utilize a patch management system.  Here are some results from a web search.  I have no experience with any of these nor do I endorse any of them...just a rando search for you to investigate:

[The Ultimate Guide to Linux Patch Management](https://tuxcare.com/the-ultimate-guide-to-linux-patch-management/)
[SysWard](https://sysward.com/)
[HCL Software BigFix](https://www.hcltechsw.com/bigfix)
[Kace Systems Management Appliance](https://www.quest.com/products/kace-systems-management-appliance/)
[GFI LanGuard](https://www.gfi.com/products-and-solutions/network-security-solutions/languard)
[Ivanti Neurons for Patch Intelligence](https://www.ivanti.com/products/ivanti-neurons-patch-intelligence)
[ManageEngine Patch Manager Plus](https://www.manageengine.com/patch-management/linux-patch-management.html)

LHammonds

---

