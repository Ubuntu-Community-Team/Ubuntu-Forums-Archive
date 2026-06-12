---
title: "Ubuntu server with old Dell PowerEdge??"
date: 2011-07-24
forum: Server Platforms
---

### Post by firstrock on 2011-07-24
Hello all!!

I currently have a new project I'm working on. I plan to set up my own home LAN using older tech for real world use & education. I am in school working towards a BS with plans on becoming a system admin. So, this is both a project (professional development) and a hobby.

Here is what I currently have for hardware:

[Dell PowerEdge]("http://support.dell.com/support/edocs/systems/pe1650/en/ug/8g540aa0.htm") 1650 1.4 x 2 CPU 4GB RAM 214GB SCSI RAID-0 Server
[HP MSA30]("http://www.onthefirm.org.uk/?page_id=1542") 2.2TB SCSI Ultra320 Storage Enclosure (Single BUS)
14-10,000RPM 74GB SCSI Drives
Sun Microsystems 220v 38u 19" Storage Cabinet

OS- Ubuntu server???? or W2K Server Data Center??

First of all let me say that this system is less than ideal as most of the tech is at least 10 years old. Secondly, this is for home use with no critical data. Third, this is to be my mini system to play with and get the basics of administration down..... a hands on approach to be used along side what I have learned in school.

Now that is out of the way, I have several questions that I hope someone can help me with. 


[LIST=1]
[*]What OS choices do I have given the hardware above?
[*]Can I dual boot OSes for testing/learning?
[*]Any specific thoughts on compatibility of the MSA30 and OS?
[/LIST]
Another question on the MSA30. The SCSI connector on the back is a 68 pin female connector and so is the connector on the back of the Dell server. What cable do I need to connect the two components together? I can't seem to figure this SCSI connector out! (I think [this]("http://www.computercablesource.com/scsi-cable-vhdci-68-male-to-vhdci-68-male-u320-lvdsehvd-006-foot-845.html") is the cable I need but I'm not sure)[URL="http://www.computercablesource.com/scsi-cable-vhdci-68-male-to-vhdci-68-male-u320-lvdsehvd-006-foot-845.html"]
[/URL] 
My ultimate goal for this system is to be connected via Gb CAT6e and cable run to every room in the house for data/Internet. The 1TB of storage will be for media streaming and eventual home user backups.

Any thoughts or information would be appreciated!

firstrock

---

### Post by 2F4U on 2011-07-24
There are quite some options with respect to OS available to you.  Firstly, I wouldn't go for W2K since it is outdated. I would suggest you  go in a *nix direction, since this is widely used in data centers. The  big vendors here are:
- Sun Solaris
- Red Hat Enterprise Linux (paid subscription) 
- based on RHEL: CentOS and Scientific Linux (often used in universities)
- Suse Linux Enterprise Server
- FreeBSD
- Ubuntu Server (don't go for a desktop variant, choose the server edition)

This list is certainly not complete and the order does not imply any priority.

---

### Post by firstrock on 2011-07-24
Thanks for the info!! What is the difference between a datacenter OS as opposed to a server OS?

---

### Post by Gyokuro on 2011-07-24
To learn Linux administration with this equipment I would suggest to go with CentOS to get a feel for RHEL systems or Debian/Ubuntu. Solaris with ZFS is no fun on a system with only 4GB RAM (it's a memory hungry beast) and I'm not sure whether the CPU can handle a current Solaris release. 
For Windows administration: try to get a copy of Windows 2003 as Windows 2000 isn't supported anymore and the difference between Windows 2003 and Windows 2008r2 is smaller as between Windows 2000 and 2003.

Datacenter edition of Windows server OS: support more CPU's and RAM and the same goes for RHEL systems but you can use CentOS instead as there is no such artifical limitation.

---

