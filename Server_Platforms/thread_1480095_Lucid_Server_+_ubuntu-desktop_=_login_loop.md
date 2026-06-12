---
title: "Lucid Server + ubuntu-desktop = login loop?"
date: 2010-05-11
forum: Server Platforms
---

### Post by mailman1175 on 2010-05-11
I don't know quite how to title the thread, and I did a quick search, but I'm not even sure enough of what's going on to formulate effective search terms. So, here's the situation:

I did a fresh install of Ubuntu Server 10.04 LTS on a PIII, 933Mhz, 512GB RAM old-school Dell machine, including mail, samba, fileserving, etc. Updated, safe-upgraded, then aptitude installed ubuntu-desktop. Restarted.

It brings me to the login window, I click my username, enter my password correctly, it thinks about it for a minute, then appears to restart X, bringing me back to the login window. It'll do this as long as I care to play along.

This is my first attempt at a server install (hoping to set up a mailserver). What gives?

---

### Post by mailman1175 on 2010-05-11
Is this in the right forum to get some traction? Do I need to move it up to General Support? Bueller?

---

### Post by arrrghhh on 2010-05-11
I guess why did you install ubuntu-desktop if this is going to be a server?  If you want a desktop, you can install ubuntu-desktop plain and put the services on top of it - no problem.

If you want a server, then build a server... but don't install the ubuntu-desktop package on top of it!

---

### Post by mailman1175 on 2010-05-11
Lots of people install desktop packages on top of servers for lots of different reasons.

---

### Post by arrrghhh on 2010-05-11
> **mailman1175 said:**
> Lots of people install desktop packages on top of servers for lots of different reasons.

Still doesn't make sense when you can have all of the server applications running on a standard desktop install.

If you just wanted a GUI, there's Webmin or you could've done a core install of Gnome or a minimal Ubuntu install.  Sorry, to me it just doesn't make sense to install the entire ubuntu-desktop package on a server install.  

It... just seems like a horrible idea.  You're proving my point.

---

### Post by mailman1175 on 2010-05-11
Fine. These are not the droids you're looking for. 'preciate you bumping my thread for me. :D

---

### Post by arrrghhh on 2010-05-11
I can't help you if you refuse to even explain your reasoning.  No one can help you if you're not willing to help yourself.

---

### Post by mailman1175 on 2010-05-11
> **arrrghhh said:**
> I can't help you if you refuse to even explain your reasoning.

insert huge logical leap here 

> **arrrghhh said:**
> No one can help you if you're not willing to help yourself.

I'm trying to be nice, arrrghhh. I don't think you need to know why I want to do something to deal with why the packages aren't working correctly. If you don't want to help, that's fine. Move along and help someone else.

I'm perfectly willing to help myself, but I'm not about to waste any (more) time explaining something irrelevant to someone who doesn't want to help me solve the problem at hand. And, before you ask: It's irrelevant because ubuntu-desktop packages have worked with server installs (based on anecdotal evidence) in the past.

If there's a reason why it suddenly doesn't work in Lucid, chime in. That's relevant discussion. But just because you think it's a horrible idea doesn't make it so.

---

### Post by arrrghhh on 2010-05-11
I guess you've never heard of "best practices".

If you really do want to install ubuntu-desktop ON TOP of a -server install, by all means go ahead.  Just don't expect anyone to support/help with your setup.  There's other ways to get a GUI that I mentioned earlier, installing ubuntu-desktop is probably the worst way you could get a GUI onto a server machine.  My point still stands, if you truly do want ubuntu-desktop then install that and setup your services on top of it.  Problem solved.

---

### Post by mailman1175 on 2010-05-11
There has been a lot of debate in the bowels of the interwebs about whether servers need GUIs or not. There are plenty of people who come down on both sides of the issue, depending on what the server's being used for, etc., etc., etc. I've said it before in different terms: This is not the thread for hashing that out. If you don't want to help, move on. You're just wasting your time.

Thanks again for bumping my thread.

---

### Post by arrrghhh on 2010-05-11
Please mark the thread as solved then.  I solved your issue - install the actual ubuntu-desktop, then put your services on top.  Problem solved.  Not much of a server, but hey you wanted a GUI.

---

### Post by bibleman on 2010-05-11
I hate to say it, but if you want a GUI you should install the desktop version and then put whatever services on it from there. I do that for my windoze admin who can't live without a GUI.

As far as your problem is concerned I would try to look at error logs and do normal troubleshooting. It seems like your X server is not configured properly.

---

### Post by mailman1175 on 2010-05-11
> **bibleman said:**
> I hate to say it, but if you want a GUI you should install the desktop version and then put whatever services on it from there. I do that for my windoze admin who can't live without a GUI.

I started to do that in the first place, but the ubuntu wiki (among other sources) suggested it was easier to do it the other way around: server first, then desktop packages. This is my first go-around with a server, so I'm looking for incremental changes from what I'm accustomed to.

> **bibleman said:**
> As far as your problem is concerned I would try to look at error logs and do normal troubleshooting. It seems like your X server is not configured properly.

I'll see what I can dig up.

---

### Post by arrrghhh on 2010-05-11
> **mailman1175 said:**
> I started to do that in the first place, but the ubuntu wiki (among other sources) suggested it was easier to do it the other way around: server first, then desktop packages. This is my first go-around with a server, so I'm looking for incremental changes from what I'm accustomed to.

I don't know what wiki you read that said it would be easier to start with a server install... that doesn't make any sense really.  The server install is built to be stripped, specifically for web servers, database, etc - no GUI so your server can focus on crunching numbers for the services.

However, if you want a GUI, there's really nothing stopping you from building services on a -desktop install, it just means that there'll be a lot of overhead from running a GUI.  Just means you'll need a beefier server to get the same performance... If you're not concerned about performance, then it really won't matter.  Trust me, you'll save yourself a TON of headache by starting with the -desktop install.  Especially since you were completely willing to just throw that package on top of a server install.

---

### Post by krodrigue on 2010-05-12
A good way to add desktop to server

apt-get install --noinstall-recommends ubuntu-desktop

that should do it for you.

---

