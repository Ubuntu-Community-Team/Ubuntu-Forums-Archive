---
title: "Creating a &quot;virtual&quot; firewall to filter by MAC address"
date: 2006-03-13
forum: Server Platforms
---

### Post by StueyB on 2006-03-13
Hi Everyone

Im hoping someone can help here. Basically I have a system (Win2k server) this web server is used for a special web front end that is only really designed for internal use, but at the moment it is wide open to the net ( I know its bad but you all know what bosses can be like) 

We already have a Checkpoint R54 firewall server and thats all well and good, except for the fact that I cant restrict on MAC address, ie the external net clients that are valid are allowed through and the rest are dropped. 

This machine will sit behind the firewall so all the traffic is pre filtered so all this machine would have to do is read in the incoming http request and based on source mac address forward on the valid requests to the server.

Is this possible to do, and if so how hard?

---

### Post by Glut on 2006-03-13
MAC address is not the suggested method for firewalling. It's trivial to fake a MAC address. A better method would be to have your real firewall preventing connections from external sources with ipaddresses that should be internal (this should be the default method of operation), then serve only to internal ip addresses.

---

