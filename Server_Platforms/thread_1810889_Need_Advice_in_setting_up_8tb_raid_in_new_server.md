---
title: "Need Advice in setting up 8tb raid in new server"
date: 2011-07-23
forum: Server Platforms
---

### Post by Ed_Ziffel on 2011-07-23
Have set up a 5 raid, 5 2tb drives in a new server. 8tb free after creating raid.    

Requirements for the server are that it will handle multiple Mysql databses with million plus record tables that will be accessed via a web based front end. Have 2 nic cards installed. It will also be used to store source data which is expected to be about 2 plus tb per year with needing 2 years on drives to be available as needed.  

Using LVM to set up partitions but not sure where the files should be placed and how big to make partitions. boot, swap are no brainers but what of the other partitions?  Am used to working with lamp on desktop where var partition has all the web stuff but doesn't that wind up in srv on the server?  Want to set up Samba server to let others on the lan upload and access source files.  Where should I plan to put them?  

Would hate to get all this going and wind up with less than decent formating scheme.  Might wind up being the nothing short of total mess.

Anyone been there and done that, or have a clear idea on this?

---

