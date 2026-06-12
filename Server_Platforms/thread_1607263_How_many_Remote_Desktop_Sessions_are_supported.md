---
title: "How many Remote Desktop Sessions are supported?"
date: 2010-10-27
forum: Server Platforms
---

### Post by roger_doger on 2010-10-27
I have a need to support multiple remote desktop sessions. Each one seperate from the other and run concurrently.

Windows XP supports one. Widows server support two. How many will Ubuntu server suuport? How about Ubuntu desktop?

---

### Post by CharlesA on 2010-10-27
Like controlling one desktop or using it as a terminal server?

---

### Post by roger_doger on 2010-10-27
Different desktops, so as a terminal server.

---

### Post by roger_doger on 2010-10-27
Right now, there are a few laptops connected in a secure area. The users use the remote desktop to access them. They primarily use an internet explorer, commmand prompt, etc.

I want to remote the pile of laptops and put this access into a server. My hope is that the server can do what I want. Another option is to virtualize the laptops.

I'm looking for ideas.

---

### Post by CharlesA on 2010-10-27
It would probably be better/easier to just use a Windows server to set up Terminal Server like that.

You can do a Terminal server with Linux, but I don't have any idea real experience with that.

[http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project](http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project)

---

### Post by koenn on 2010-10-27
AFAIK there is, technically, no limit other than the resources of your server or the network. Depending on the implementation of the technology you use (vnc, rddp, X forxarding, ...) there might be specific limitations built)in in the software, but those would probably arbitrarily large, eg max 255 sessions (just guessing)

On Windows, the limitations are bolted on for licensing reasons - technically its a multi-user system capable of multiple concurrent sessions.  XP is licensed for 1 (concurrent) user so you can only have 1 session, remote or not, although there are hacks to work around that. The 2 session limit on Windows Terminal Server are intended for system administration - as you buy additional Terminal Services licenses, you can have more simultaneous sessions

---

### Post by the_original_billq on 2010-10-27
Go [here]("https://help.ubuntu.com/community/UbuntuLTSP") and read.  LTSP is a great solution for low maintenance and kiosk-like deployment.

-Bill

---

### Post by roger_doger on 2010-10-27
OK, it's licensing issue in Windows server. Can I support multiple sessions with Ubuntu? Am I better off running multiple virtual sessions?

---

### Post by roger_doger on 2010-10-27
LTSP is a thin client application. I install the applications on the server, and the clients access it remotely. Each client has their own session. Correct? Can they save their settings, docs, etc? This is essentially a virtual desktop environment, right?

---

### Post by the_original_billq on 2010-10-27
Linux/UNIX is a "multitasking, multiuser" operating system.  Ubuntu is free. There is no cost for running 1 or 1000 users on a server, provided the hardware will support it.

There are currently some challenges with running multiple X sessions from Ubuntu 10.04/.10 - this is due to an issue with gdm in those releases.  If you want to support multiple X sessions from the server, I would suggest either 10.04 Kubuntu (which used kdm) or 9.04 Ubuntu.

---

### Post by koenn on 2010-10-27
> **roger_doger said:**
> OK, it's licensing issue in Windows server. Can I support multiple sessions with Ubuntu?
yes, didn't I say so already ?

> Am I better off running multiple virtual sessions? 
hard to tell. 
desktop visualization has lost of facets, and is often implemented with some form of Terminal service technology - the division between the two is blurring (and becoming clouded)
Your choice will not only depend on what you're trying to accomplish, but also on the IT environment you're in now, and how you envisage that environment 5 years from now, and your strategy for getting there. It's a hard question, and there are people earning a more than decent living by offering consult on  these matters 

Or you could just make a decision on personal preference, skills, and available budget. :)

---

### Post by the_original_billq on 2010-10-27
> **roger_doger said:**
> LTSP is a thin client application. I install the applications on the server, and the clients access it remotely. Each client has their own session. Correct? Can they save their settings, docs, etc? This is essentially a virtual desktop environment, right?

Yes.  In LTSP, the workspace is on the server, but the application execution uses local (PC) resources.  It's what I would call a "fat" thin client (if that makes any sense).

A "real" thin client (to me) is more like an X Terminal, which only takes care of maintaining an interface to the user, with everything running on the server.  (But that's also not LTSP)

There are a number of vendors that sell "real" thin clients, which are specialized display devices (like Oracle Sun Ray, etc...).  In general, these provide better security, as there is no data on the client end, and you can encrypt the connection to the server.

In Linux/UNIX, each user login has their own "workspace" or HOME directory.  When the user logs in, they are working out of their home directory, where all their data is stored.  This is true regardless of the solution you provide.  The real difference is noticed when you look at how you maintain and deploy applications to your user base.  Using the thin client solution, you update the server, and all your clients are updated, because they all share the same OS space.  Using a fat client solution, you need to update and maintain each workstation (or image).

HTH,
Bill

---

