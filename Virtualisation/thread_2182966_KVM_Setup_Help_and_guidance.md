---
title: "KVM Setup Help and guidance"
date: 2013-10-23
forum: Virtualisation
---

### Post by krish2487 on 2013-10-23
Good afternoon,

Let me start off by saying that I am an electrical engineer and an ubuntu fan and no big shakes when it comes to system administration and/or networking. 
I have managed to convince my boss and convert the entire office (~25 systems) to ubuntu. The only exception is our server which runs Win 2K3. We cannot migrate that to and *nix distro because we run SAP on it. We do not have an inhouse IT department to manage the systems and I have been assigned the admin job.

Again, at my insistence, we are trying to move over to KVM to manage the present server and possibly deploy other virtual servers for additional services.

Presently we are running only a SAP server. We also wanted to implement
1. Owncloud - for our internal cloud sharing.
2. Moodle - for internal training for new recruits.
3. Untangle - as a UTM/gateway to our server from external world (we have 2 static IP addresses)

I am trying to implemnt all these VMs on a ubuntu 13.04 desktop fresh install. The machine is a I5 quad core with 16 gigs memory and 2 TB HDD and 2 NICs.

Now let me get to the problem I am facing.

I have successfully managed to get KVM up and running, download vmware virtual appliances and convert them to .img files for use by kvm and also start the kvm vms.

Here is the problem I am facing, and it is largely due to my own lack of knowledge more than anything else.

1. Networking : I need to access VMs behind the static IP from an external network. 
I understand you can use port forwarding, Can anyone indulge me and give a brief walkthrough on what each networking option in the VM creation means?
Like "macvtap :eth0","specify a shared name" etc. and also on how to setup a proper port forwaring rule on the 13.04 host.  so that I can access the internals vms from an external network. 

2. Static IP : All the VMs need to be given a static IP.
I understand that the static IPs for the vms can be configured by modifying the interfaces file in each vm . Is my understanding correct?


I apologize if my questions seems foolish and immature. As I ve said, I am electrical engineer by profession. I have learnt a little of ubuntu and that is the limit of my knowledge so far. I would really appreciate if anyone can help me out here.

---

### Post by TheFu on 2013-10-23
Everything that follows is opinion.  I don't know where to start, since you haven't provided too much on your Linux/UNIX background or the systems being replaced.

Backups should be job #1 and be certain that you can recover.  Test it on bare metal so you don't look stupid when you need to restore. Backups aren't just about programs, settings and data. There are many other problems - some from outside and some from admin error - that can be mitigated with good backups.

Using a "desktop" as a server is definitely NOT a best practice. Desktops are different from servers in software AND hardware. Desktops are inherently less stable than servers. Using 2 desktop hardware systems is a viable option to avoid many of the problems, but using desktop software will still lead to instability.

Running a firewall on shared hardware is definitely NOT a best practice regardless of whatever you've read.  Certain things are just too important to screw around - security of an entire company is one. ** Use dedicated hardware for this.** I prefer pfSense for a business solution. A $100 dual core Atom or AMD-E class box would be fine for a business with 50 or so end users. Having 2 makes more sense, unless the business can be offline for the time it takes to rebuild it and all the settings (even a restore will take 30-90 minutes) without practice.  pfSense restores can be 30 seconds, BTW.

The routing you will need to setup will be complex. You'll need to learn more about IP networking first. Not impossible, just not intuitively obvious under a VM. People struggle with this all the time. You may be smarter than me - I was a NASA rocket scientist, however.

A slow migration to those systems would be best. Start by centralizing authentication via LDAP (use kerberos), then add a transparent proxy server, file server, print server.  That should take a few weeks, min. Verify backups work for each, before moving on.  Then I'd suggest asking 1 question at a time related to 1 of the systems you are trying to setup.

Having a single HDD is asking for trouble. A failure takes down every VM, not good.

Do you run the email server currently? Not mentioning that is concerning.

No mention of using cloud computing ... while I agree, there is a place for some of those resources in most solutions.

Convenience and security are usually on opposite ends of a solution.  Php-based solutions tend to have 10x more security issues than others.  Just sayin'.  Be careful with php.

You'll have a steep learning curve if you want this to be secure AND to work.  Should be fun, however.

---

### Post by krish2487 on 2013-10-23
Thank you for the suggestions.

1.This "server" is only for beta testing. We presently have two actual servers from HP - Xeon dual core procs w/ 16 gigs ram and 1 TB HDDs. The boss wanted proof of demonstration before production servers are deployed. So yes, this entire exercise is only a run up to the main deployment to find, understand, overcome and log the issues we might face and solve them.

2. Regarding the firewall, we have another box with specs similar to what you suggested. I can take the firewall off the list of VMs and deploy independantly.

3.Backups : we have a HP microserver N36 with 4 x 1 TB HDDs in RAID 0 config backing up user directories and the main SAP server.

4.Email server : No plans/need to implement in the near future.

5. Cloud computing : Only a personal hobby interest but not useful in our company.

Thank you for your time and invaluable suggestions, TheFU. I guess my next avenue of pursuit is Pfsense and IP networking. At the risk of sounding google-impaired, do you have any suggestions as to where I might get a good start for IP networking?

---

### Post by TheFu on 2013-10-23
No idea on ipv4 networking, but he.com has ipv6 certifications and training for free.  If you don't have much understanding, grc.com/sn episode 25+ will help solidify your understanding, but he doesn't get into complex routing.

Your backup config is SCARY.  RAID0 should only be used for temporary storage - like a video editor needs for 30 minutes at a time, not for backups.  If any 1 of the drives fails in that RAID-set, all the data on the other 3 drives will be lost too. That setup has made a failure 4x more likely - not what you want, I'm certain. Much better off using LVM and merging the PEs into a single VG and then into a right-sized LV that can be extended as needed. Be very carefull with LVM - not understanding it can lead to data loss, just like using RAID can. I'm worried about the backups, as you can tell.

There is lots of stuff not mentioned like alarming, monitoring, log management and review.

---

### Post by krish2487 on 2013-10-23
As you probably know by now, I am that inexperienced in this field. 
:-)
 
It is a area of interest for me, however and I will definitely read up more on what you find scary about my present setup.
Hopefully I will be able to learn some new stuff.

Thank you again TheFU

---

### Post by TheFu on 2013-10-23
We all started out knowing less than we do now. There are organized ways to attack the steep learning curve, LPI training materials are a start, but even that will leave huge gaps of knowledge. That is a necessary evil, I suppose. There is just too much to know and getting started is important more than reading books.

I've been doing this sort of stuff for 20+ yrs and there is still so very much I should learn. Things are always changing - usually for the better, but not always.  We all run into the same issue - we don't know what we don't know.  I think I understand about 10% of linux.

Going slow with your deployment will give you time to learn from small mistakes before amplified across many systems.  File and print are the most stable parts of Linux and will integrate well with Windows ... are you replacing all the desktops too?

---

### Post by krish2487 on 2013-10-23
All the desktops have already been replaced with mint as it have a closer UI to windows - something that is easier to navigate for most used to MS Windows.

If you dont mind my asking - what is LPI??

---

### Post by krish2487 on 2013-10-23
never mind. first result on google gave the result.

:-)

---

