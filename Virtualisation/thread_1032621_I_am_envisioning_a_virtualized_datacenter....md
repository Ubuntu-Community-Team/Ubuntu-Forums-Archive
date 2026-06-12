---
title: "I am envisioning a virtualized datacenter..."
date: 2009-01-06
forum: Virtualisation
---

### Post by Starks on 2009-01-06
What would be the best way to go about creating a virtual environment (using free and/or non-free software) that would allow clients (ie: various companies), to be served their own personalized desktop environment with logins from a single or group of remotely located server boxes?

---

### Post by Dedoimedo on 2009-01-06
Amazon Elastic Cloud Computing (Amazon EC2):
[http://aws.amazon.com/ec2/](http://aws.amazon.com/ec2/)

Dedoimedo

---

### Post by Starks on 2009-01-06
Is this similar to having a VMWare ESX on a blade system?

---

### Post by dwanders on 2009-01-06
You mean something like this:

[http://www.ulteo.com/home/en/home?autolang=en](http://www.ulteo.com/home/en/home?autolang=en)

---

### Post by Starks on 2009-01-06
Wow. This stuff is pretty interesting.

---

### Post by dwanders on 2009-01-06
Which - the Uleto or the Amazon Cloud? or just Linux in general :D Personally I love it all! I was reading an article in Linux Format when I came across that Uleto - looks pretty cool but I have not tried it - would like to though.

---

### Post by Starks on 2009-01-06
Is ESX baremetal?

---

### Post by Starks on 2009-01-07
What I am aiming for is this:

Person sits at dummy terminal. Turns on computer. PXE boots into remotely served client.

---

### Post by PilotJLR on 2009-01-08
That's not necessarily a virtualized desktop... 

If you want a linux desktop, then you need LTSP.

If you want a windows desktop, then you need Citrix Provisioning Server.


(yes, ESX is baremetal, but that has nothing to do with PXE booting endpoints).

If you want actual guest OSs served to endpoints, then you need an endpoint system (PXE or not) and a VDI infrastructure, which could be VMware View or Citrix XenDesktop.

---

### Post by PilotJLR on 2009-01-08
FYI, if you do want to serve up Windows desktops, don't forget about the Microsoft police. You'll need VECD licensing; google that for all the details. 

Most people don't know about VECD and wind up non-compliant.

---

### Post by Starks on 2009-01-10
> **PilotJLR said:**
> That's not necessarily a virtualized desktop... 

If you want a linux desktop, then you need LTSP.

If you want a windows desktop, then you need Citrix Provisioning Server.


(yes, ESX is baremetal, but that has nothing to do with PXE booting endpoints).

If you want actual guest OSs served to endpoints, then you need an endpoint system (PXE or not) and a VDI infrastructure, which could be VMware View or Citrix XenDesktop.

Which would be the cheapest way, in terms of both software (and perhaps even hardware) to achieve that?

Ideally, I'd like a FLOSS solution.

---

### Post by PilotJLR on 2009-01-10
Both for software (free and free) and hardware (modest), LTSP is the winner in cost. That's one reason why LTSP is so popular is schools with no or little budget available.

LTSP would work provided you are okay with users getting a Linux desktop instead of a Windows one. It will also PXE boot diskless endpoints.

The commercial virtual desktop solutions have a significant upfront cost.

---

### Post by Starks on 2009-01-11
With LTSP, is each client isolated?

---

### Post by PilotJLR on 2009-01-11
Depends on what you mean by isolated... LTSP is basically a terminal server, so each user would have a session and their applications executed on the same server instance. It's like user 1 has VNC session 1, user 2 has VNC session 2, etc.

Of course, you have a lot of power to control what users are able to see and read. Most people would allow a user to only read and write to their own home directory.

If you want fully separate OS instances for each user, then that would go back to a virtual desktop infrastructure setup. Have a look at the budget you can allocate for this project before you go too far down that road. You'll need bigger/more servers for a good user experience with a VDI framework.

---

### Post by Starks on 2009-01-12
Well, I'm looking for a multi-platform approach. I don't want to be limited in he OS that can be served. Additionally, when I said isolated, I meant that each company would be served an OS and each employee would have their own session.

---

### Post by PilotJLR on 2009-01-12
Ok, that eliminates any form of term server... going multiplatform will also eliminate the VMware and Citrix choices as well.

Provision networks (now Quest software) has a connection broker that supports windows and linux guests. Ulteo (from the poster on the previous page) seems to as well, though I hadn't heard of them before.

---

### Post by Starks on 2009-01-12
meh, multiplatform support isn't a deal-breaker for me.

---

