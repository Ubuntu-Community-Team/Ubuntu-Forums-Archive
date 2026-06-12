---
title: "IT Management and Automation"
date: 2009-06-11
forum: Server Platforms
---

### Post by danrche on 2009-06-11
Hello everyone,

I'm currently working in IT and looking for an alternative to my current IT management tool (kaseya). I manage many clients using windows and MAC but had to pass on Linux customers as Kaseya doesn't support it. 

I know Nagios will monitor the systems, but will it allow for scripted pushes, and remote control from one console? 

Much of the ability for me to successfully manage 2000 nodes own my own is b/c I automate much of the process via monitoring with triggered scripts that preform a self heal and it all reports back to me. I can remote the PC anywhere as long as it's on the internet. I can push scripts to the PC that preform what I need done as well and can schedule them to run reoccurring. 

I'd like an opensource solution that provides the same type of support for Linux/Windows. 

Anyone have any recommendations? Payfor solutions are acceptable.

---

### Post by koenn on 2009-06-11
> **danrche said:**
> 
I know Nagios will monitor the systems, but will it allow for scripted pushes, and remote control from one console? 

Yes, Nagios can do that. You'll have to configure what params of the system you want monitored (through a variaty of means, including snmp), set thresholds for them, and define what action to take when that threshold is reached; the action could be any script + a mail back to you with feedback about the situation and the result of the script/command/....

It's quite a task to set all this  up (never done it myself but saw a presentation about it) so you might want to look for a Linux integrator to assist you or do it for you. 

I'm not sure what you mean by "scripted pushes, and remote control from one console", but with ssh it's trivial to execute commands on a remote Linux PC.

---

### Post by danrche on 2009-06-11
thanks for the recommendation, I like Nagios so far, 


but I'm trying to do this for both windows and Linux, and all from a remomte location and some users will need assistance from their house to get their laptops up and running, so Can I remote in (vnc or rdp) to the windows PC's to remote control from within Nagios? (Vnc is prefered so I can see what they're looking at). This portion is more for the admins to do training on and such, and when they're pc is broke for me to remote in and fix, when I have to.

---

### Post by koenn on 2009-06-11
Hm, I'm beginning to see where you're getting at.

I had a quick look at the kaseya web site, and I gather that most, if not all of its features have a counterpart in Linux (remote command execution, remote scheduling, remote desktops, the whole monitoring and triggers thing, vnc servers and clients, ...) but
a/ kaseya offers all of this i 1 application (or suite), which probably offers some additional benefits, in terms of integration and easy of use
b/ you want something that can target Windows PC's, Macs, and (any and all) Linux systems 

That's going to be a bit of a problem. 
Kaseya solves this by using agents that run on the target systems so it can execute native, local commands as instructed by the server, but as they offer no agents for Linux, ....

Nagios depends mostly on its ability to execute linux commands on the target systems, so scripted interventions on eg a Windows system would require remote access to a scriptable command interpreter, such as a telnet server on the target systems (which you don't want to begin with).

You might want to have a look at ICSInventory ( [http://www.ocsinventory-ng.org/](http://www.ocsinventory-ng.org/) ) and GLPI ( [http://www.glpi-project.org/spip.php?lang=en](http://www.glpi-project.org/spip.php?lang=en) ). ICS also uses agents to manage the target systems, eg for software deployment and such, so It can likely be tweaked towards executing whatever you tell it to execute. Those combined with Nagios can probably meet your requirements, but I'm not aware of the existence of all of it in 1 integrated suite.

---

### Post by danrche on 2009-06-11
koenn,

Ok, so let me get this straight, to effectively match kaseya's tool set in Opensource I'd need to use several different aspects at once to provide that same level of Automation, right? 

Humm, sounds like more work than I'm willing to do, this Kaseya stuff was a bit of a pain to set up on 2000 nodes, but for the most part now it's a breeze to manage. I don't think I'm willing to go with multiple tool sets. I'll try to continue to pressure Kaseya into dev on a linux agent. 

Please don't confuse this thread, very happy with Kaseya but want Linux integration as we're moving into more opensource solutions. I may just look into a way to port Nagios into my Kaseya toolset just for my *nix boxes. Most of my remote users use MAC or Windows, and all my *nix are in-house or on a LAN Segment. So I think I can do ssh for remote on the *nix, and just modify the webpage within Kaseya to add a tab for Nagios's web portal. This should do for now.... I hope.... if it works......

---

### Post by koenn on 2009-06-11
> **danrche said:**
> koenn,

Ok, so let me get this straight, to effectively match kaseya's tool set in Opensource I'd need to use several different aspects at once to provide that same level of Automation, right? .
As far as I know, yes. There may be open source or even proprietary but Linux-compatible software like this, but I don't know of it. You might want to check Novell's website, they're kinda big on enterprise solutions with Microsoft-Linux integration, maybe they have something ...

> **danrche said:**
> I'll try to continue to pressure Kaseya into dev on a linux agent. 
 That would be good ...
It seems to me that in a linux-only environment, kaseya wouldn't make much sense - linux has free, built-in, native tools for remote management etc. where Windows originaly needed 3th party solutions such as vnc and agents to accomplish the same, untill MS started incorporating such functionality in its OS. 
I'm supprised they support Mac. Porting that to Linux shouldn't be too hard ...

> **danrche said:**
> 
Please don't confuse this thread, very happy with Kaseya but want Linux integration as we're moving into more opensource solutions. I may just look into a way to port Nagios into my Kaseya toolset just for my *nix boxes. Most of my remote users use MAC or Windows, and all my *nix are in-house or on a LAN Segment. So I think I can do ssh for remote on the *nix, and just modify the webpage within Kaseya to add a tab for Nagios's web portal. This should do for now.... I hope.... if it works......
That's probably what I'd do as well : keep kaseya for the Windows and Mac clients, and add Nagios and ssh to manage the linux systems - possibly include openvpn and a remote desktop solution if you'd ever have to manage linux desktops across the internet / behind firewalls. 
That's still 2 sets, but since neither can manage all 3 of the types of systems you target, I think it's the best solution in the given situation.

---

### Post by danrche on 2009-06-11
Koenn, 

I've just finished setting up a Nagios install on my testing box, and pointed it to my K server (kaseya). I see the tab, now I have to config Nagios, I think this may work!!! So far, I'm the only user who uses Linux exclusivly and works remotly (office, and home and coffeshops on weekends for updates and such). I may have a solution for the remote linux box as well, using vpn on boot at runlevel 3 and 5, the problem is wifi, but we'll cross that bridge when needed.


:D thanks for the replies.

---

### Post by koenn on 2009-06-11
> **danrche said:**
>  now I have to config Nagios, I think this may work!!! 
Like I said, this can be quite daunting. 
Since you were willing to pay for a solution, don't hesitate to hire an expert if you can't get it all exactly right yourself. It's probably worth it. 

> **danrche said:**
> 
:D thanks for the replies.
It was an interesting problem.

---

### Post by danrche on 2009-06-11
Thinking of hiring zenoss, it's based off Nagios, I'll give them a call, I've still got a few bucks left in the budget for projects :)

---

