---
title: "Need help with Fibre Channel"
date: 2016-02-04
forum: Server Platforms
---

### Post by Zeik_Tuvai on 2016-02-04
Hello everyone! i'm new to Ubuntu server but I have used linux in the past for lots of stuff so I think i'm ok.  But this project has been giving me some weired issues that I can't seem to figure out.  

I have been using Windows server to host VM workloads over iSCSI and I came into some Fibre Channel hardware and wanted to use the faster medium.  So I set out to figure out how to do that on linux, I have my raid cards installed with targetcli and lio-utils set up correctly, all of my initiators and iblock devices are working great.  The problem comes in when I try to use a fibre channel switch, I have a Brocade 200E that works fine, all the hosts can see and use the storage over the switch just fine.  But the moment one of those servers reboots or disconnects the entire ubuntu box stops working.  I get console messages saying rcpu detected stall on cpu tasks and nothing will fix it save for a reboot.  This of course is not idea, but oddly enough if I do point to point without the switch i can unplug and plug in all day long with no issue.

So, if anyone out there can please help me I would greatly appreciate it!
Thank you!
Greg

---

### Post by TheFu on 2016-02-05
Fibre channel compatibility is tough. Short of verifying that every device and every driver for those devices are 100% compatible in the spec sheets, I don't have any answer.  Even if other FC equipment from the same maker is 100% compatible, that doesn't mean all their stuff is. We saw some strange incompatibilities in our lab during the early days of FC.

Plus, don't forget that some equipment just has bad ports, so try different ports.

---

