---
title: "Centralized control of multiple servers"
date: 2011-04-07
forum: Server Platforms
---

### Post by MakOwner on 2011-04-07
I am currently using webmin on servers inside the firewall, and I like that sort of functionality -- is there some sort of centralized version of webmin that doesn't require that I log in to each server in order to accomplish some task?

I have looked at puppet and I don't think that really fits.
Or at least of what I have seen so far.

Any suggestions?

---

### Post by falko on 2011-04-07
For what tasks exactly do you use Webmin? For certain tasks there might be a control panel (like ISPConfig) that can do what you need.

---

### Post by MakOwner on 2011-04-07
> **falko said:**
> For what tasks exactly do you use Webmin? For certain tasks there might be a control panel (like ISPConfig) that can do what you need.

Mostly configuration changes like handling exports, NFS mounts, webserver changes and system updates and system updates.  

Webmin is still new to me, so I may just be missing some part of it.

The major thing I have with it is that I have to log in to each server to do anything - not that I do that much across all the servers, but 
When I log into one server, make a change, then go back to the webmin server index, login into another server... 

I'm no even sure I'm making sense here :confused:

I'm just looking for more of a central control panel than a control panel per server I suppose.  I think that means a single login, with a menu bar on the left to indicate which server I'm logged into with the ability to change between serves within the same module.

Maybe. :confused:

I'm trying to think of an application that presents a logical interface for the configuration and actions over multiple entities...


And for your further edification - I just started using webmin.  I typically find myself a bit more comfortable at the command line, so I'm trying to learn something new.

---

### Post by MakOwner on 2011-04-07
Would puppet be a suitable application to look at?

my only requirements be that it's installable from an apt repository (preferably the default Ubuntu supported ones) and a minimal client footprint and hopefully not require a fulltime dedicated master server. 

Or maybe it could.

I have 3 Ubuntu servers and a gateway/firewall that run 24x7 and probably 15 other machines that I bring up and down as needed for various tasks.
2 of the "other" machines are ESXi hosts that while I'd love to let them run and handle everything as virtual hosts, the power costs are too high.
I'm moving some things around to reduce the number of 24x7 hosts I have, and that's what prompted the hunt for a tool of this nature -- all the recovery testing I have been doing as I shuffle hardware around has had me doing installations and really taking a look at how I deploy.

At any rate, I'm just looking for suggestions for things to look at.

---

### Post by HermanAB on 2011-04-08
howdy,

If all your machines are exactly the same, then Parallel SSH would be the way to go, instead of Webmin.

---

