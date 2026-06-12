---
title: "Making Ghost Image of live Server"
date: 2012-12-24
forum: Server Platforms
---

### Post by ketan985 on 2012-12-24
I need to make ghost image of my live  Ubuntu servers for disaster management . For this solution I searched lot but could not find best open source software for solution.  Pls suggest me any solutions for such purpose.

---

### Post by Cheesemill on 2012-12-24
The only way I can think of to image a drive on a running server is to install using LVM for your partitions. Then when you need to make an image you can create an LVM snapshot of the required partition and then use fsarchiver or partimage to dump this partition snapshot to a file.

---

### Post by haqking on 2012-12-24
Disaster management should be proactive not reactive, not an afterthought.

Clonezilla is about the best but you will need to reboot the servers, if you cant do that then look at the "dump" command.

Something like 

```
dump -0 -f - / <path>
```

I think Acronis and the last few versions of Ghost support hot transfers also

---

### Post by craigp84 on 2012-12-24
AMANDA & Baculus are mature, well documented and easy to use - you can make a great, cross platform disaster recovery system with these. Alternatively [http://www.mondorescue.org](http://www.mondorescue.org) can easily churn out bootable ISOs for bare metal recovery too.

A better way is to get to the stage where you just need to backup the data. If we classify all files on a system with these 3 types of file:

[LIST]
[*]Data
[*]Configuration
[*]Software
[/LIST]

Then a great way to handle this is backup only data, you can get to that stage by never applying config directly on a host - use configuration management tools such as puppet (or cfengine, or chef, or...)

There was a quote from a puppet presentation that i really liked, it went something like: servers can be pets or cattle. When pets get sick we nurse them back to health. When cattle get sick we shoot them.

By getting to the stage where you are treating your servers as cattle, you neatly solve a whole ton of potential headaches (disaster recovery, change of hardware, change of hosting provider, change rollback...).

Hope this helps

---

### Post by spynappels on 2012-12-24
> **craigp84 said:**
> 

There was a quote from a puppet presentation that i really liked, it went something like: servers can be pets or cattle. When pets get sick we nurse them back to health. When cattle get sick we shoot them.


That genuinely is the best analogy I've heard on this issue ever!

---

### Post by LHammonds on 2012-12-24
> **Cheesemill said:**
> The only way I can think of to image a drive on a running server is to install using LVM for your partitions. Then when you need to make an image you can create an LVM snapshot of the required partition and then use fsarchiver or partimage to dump this partition snapshot to a file.
This is how I have my servers setup.  Check my sig for details on LVM + Snapshots + fsarchiver (100% full online backup)

---

### Post by jamesr on 2013-01-06
Hi, 

Apologies about the slow reply but personally I use mondorescue from [http://www.mondorescue.org](http://www.mondorescue.org). The support is great although there times when the distro distributor changes locations of files there may a delay until the problem are identified and solved.

I am running mondo on both 12.04 LTS  and 10.04 LTS servers using crontab on the 10.04 although as yet I have not as yet solved the a problem with running crontab/mondo on the 12.04 version although I have fudge that works using the at command.

Best Wishes
jim

---

