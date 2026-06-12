---
title: "Wake up server on Demand"
date: 2008-09-28
forum: Server Platforms
---

### Post by emacdonald on 2008-09-28
This is probably an obvious one.

I have set up as system where I have various PC's around the house, mostly ubuntu with some XP, I have set up one of these PC's to be a server with Server 8.04 installed. (Network is made up of a Netgear Router/modem and some hubs.) I have set up Wake on Lan, and this works perfectly.

But, I have been trying to find a way of controlling the server power consumption, and have it working successfully with Wake on Lan etc.. 

I want to be able to put the server to sleep when it has not been used for a time, and then wake up when required.

I have tried various methods, such as adding a scripts to the Linux & XP machines that starts up the server, when the PC is powered on, this works fine, but I have the server setup to go into Hibernate on Idle after 40 Minutes, so the user then has to remember to activate the WOL script when required.

What I want to try and do is to get the Server to wake up if a request has been made by any of the users. e.g. If I open a File Manager, and clicking on a link or anything else that links to the Server or requires the server.

In a nutshell, does anyone know who to set up a Wake on Demand service,

---

