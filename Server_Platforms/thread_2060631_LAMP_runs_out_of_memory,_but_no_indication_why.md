---
title: "LAMP runs out of memory, but no indication why?"
date: 2012-09-20
forum: Server Platforms
---

### Post by Javik on 2012-09-20
Is there some way to have Ubuntu report what memory all programs are using, when the "out of memory killer" is run in an emergency?
 
 
I have a really simple LAMP server running "CMS Made Simple" for a school district website. It was originally configured with 512 megs of memory in a VM. It ran fine all summer long with almost no one using it.
 
Then when school starts with many people using it, it runs for a while, then runs out of memory in the morning for unknown reasons, and the "out of memory killer" kills the SQL database. Down goes the website.
 
I increased the VM memory to 1 gig and again it runs fine for a few weeks and bam, out of memory killer kills the SQL database. I've now got it cranked up to 2 gig for the VM, though it's only been this way a day now.
 
All I see in the Ubuntu system logger window is that the MySQL process was killed, but no indication of what else was allocating memory at the time of the error.
 
 
Memory usage seems to stay around 300 meg all the time so 512 meg seems reasonable. I have no idea what is causing the allocation to suddenly surge up, burn up all the swap too, and die.
 
The only reasonable way I can see to monitor what is going on, is to run the GUI System Monitor with a max update time of 100 seconds, so it graphs memory usage for 6000 seconds in hopes of me catching whatever is causing this.
 
 
 
If this keeps up without explanation, I am likely going to have to migrate CMS Made Simple to a Windows server host, since at least that OS can keep on incrementally increasing its swap for gigs and gigs of free disk space if necessary. I'd prefer to have slow but still working, rather than nothing at all.

---

