---
title: "Lubuntu with VmWare View Client"
date: 2014-12-05
forum: Virtualisation
---

### Post by ABPAlex on 2014-12-05
So I am in the middle of a project of converting hp thin clients all to a lightweight OS that doesnt have a million updates (I chose lubuntu). These machines are primarily going to be just used to access a virtual enviornment where employees do all of their work. I have previously tried to do this process but had no real luck, seeing this is my first experience out of school with a linux based OS i thought id get help with a few questions i have. For reference i am on lubuntu 14.10
1. Trying to join my company's network, I went the route of powerbroker (PBIS) and within the walkthrough of doing it I was not able to get the GUI part of the program. Anyone have a solution for this?
2. Is anyone else using VMWare view client like i purposed to use in this write up, any suggestions or help is greatly appreciated.

---

### Post by slickymaster on 2014-12-05
*Moved to the ***Virtualisation*** sub-forum*

---

### Post by TheFu on 2014-12-06
14.10 is NOT a smart idea in a corporate environment. Go with LTS releases only since a company isn't likely to load a supported OS every 6 months. Trust me on this.  14.04 or 12.04 would be better choices.  Lubuntu gets 3 yrs of support, not 5, BTW and only for LTS.

Don't know anything about VMware View or powerbroker or .... 
If you just want a tiny client machine that will be used to remote desktop somewhere else, any Ubuntu is overkill, IMHO.  Look at TinyCore or something that can be PXE loaded easily.

I use x2go as a thin client to access remote desktops running in a private cloud.  Much cheaper than anything from VMware. Of course, x2go requires a Linux server, but any of the main 3 desktops can be used as clients. Sadly, I don't see any tablet-OS clients for x2go as possible.

---

### Post by ABPAlex on 2014-12-08
> **TheFu said:**
> 14.10 is NOT a smart idea in a corporate environment. Go with LTS releases only since a company isn't likely to load a supported OS every 6 months. Trust me on this.  14.04 or 12.04 would be better choices.  Lubuntu gets 3 yrs of support, not 5, BTW and only for LTS.

Don't know anything about VMware View or powerbroker or .... 
If you just want a tiny client machine that will be used to remote desktop somewhere else, any Ubuntu is overkill, IMHO.  Look at TinyCore or something that can be PXE loaded easily.

I use x2go as a thin client to access remote desktops running in a private cloud.  Much cheaper than anything from VMware. Of course, x2go requires a Linux server, but any of the main 3 desktops can be used as clients. Sadly, I don't see any tablet-OS clients for x2go as possible.

Took your advice, went the 14.04 LTS route, ran PBIS (didnt get the gui screen to pop up again :confused:) connected my current user name to the domain.... sucessfully via command line. Ran vmware view client, installed it and connected with no issue. Heres the next thing if you could help me, I want this to run like how i have my other windows thin clients in where i have the windows boot straight up into a kiosk mode and prompt the user right away to connect into vmware. On tiop of that i cannot log into the domian with any other user besides the one i used to originally connect to the domain. Isnt there a way to connect a computer to the windows domain and any registered domain user can log onto that UNIX pc?

---

