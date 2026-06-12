---
title: "Ubuntu to Serve Profiles to XP"
date: 2009-07-24
forum: Server Platforms
---

### Post by TDrakeHI on 2009-07-24
Ok, I know, there is probably a number of posts about this, but my searches always came back with to much info.  

I am currently moving my office and have decided that this is a good time to change the way our network is setup, as the original installer has left the island, and I now use Jaunty on all of my personal machines.

The current network is as follows:
1 Win 2K Server, running as the Domain Controller, SQL server, authentication, file server, and serves DHCP
5 WinXP Pro workstations 

The server no longer has to perform as SQL server, as the software suite requiring that is no longer in use, and I was planning on letting my router handle all of the DHCP requests.
The only thing that is necessary for the server to do is to be the Domain controller, authentication, and file server.  All of those are pretty well documented so no help really needed there.  What I would like to be able to do, is to use the Jaunty server to serve windows user profiles to the workstations, so that a user can log in from different stations, and still have access to documents worked on from any workstation.  I'm not worried about visual bling, but more about file access.  This would also make changing out dead computers a fairly easy task, as everything needed would be accessible from the server.  

Any thoughts or points in the right direction would be greatly appreciated.

---

