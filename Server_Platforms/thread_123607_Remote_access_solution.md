---
title: "Remote access solution"
date: 2006-01-30
forum: Server Platforms
---

### Post by embsupafly on 2006-01-30
Hi,

We are looking for a remote access solution. We have a main location that has a Ubuntu Server running a php/mysql application that runs on the intranet there at the main location. Users access the application via a web browser. This location does not have internet access.

We have a remote location needing to access the php/mysql application as well. This location does not have internet access.

We can get a dedicated phone line for each location, at the main location we could connect the intranet server with the application installed to a phone line, and the remote system could be connected with their dedicated phone line.

My question is, what type of solution will allow a remote location to dial in to the main location in order to connect to that network and access the web application.

I know this is normally done with a VPN, but we do not have an internet connection at either location and we need to have it done via dialup for security concerns that have been expressed. I think RADIUS might be a solution, but could someone confirm?

---

### Post by embsupafly on 2006-01-31
Anyone?

---

### Post by Soleil-Raid on 2006-01-31
Yep, this is all possible without a internet connection. What you'll be doing is effectivily creating your own mini-ISP that doesn't connect to the outside world.

If you just have small (say, four or less) number of external locations, you could plug modems into your Linux box, and set up PPP to provide dial-up access. Each remote computer would get it's own IP, and then you have you're own WAN. ;)

If you're going above four, you may want to look into dedicated modem banks, linked to an E1/T1 digital line (depending on country), which also gives you 56K access, instead of just 33.6k.

Depends on what you're accessing of course.

---

