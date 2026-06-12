---
title: "pop!_os running hot after gnome boxes install"
date: 2023-08-22
forum: Ubuntu/Debian BASED
---

### Post by ross02012 on 2023-08-22
Please be patient with me, I'm not a skilled troubleshooter.

I'm not positive they're related but after I installed gnome boxes on Pop os my computer (Dell XPS 15) is always warm, fan runs constantly and it doesn't sleep correctly. It basically performs like Windows, including getting really hot with the lid closed in a bag.

I understand while running a VM it's taxing, but I have boxes closed. I didn't change anything in bios, checked but everything was configured correctly already.

---

### Post by TheFu on 2023-08-23
Which OSes are running in the VMs?  MS-Windows isn't as efficient as other OSes and is known to use 25% of a vCPU just sitting there, doing nothing, when Linux VMs use 1-3%, usually less than 1% each while running when no work is requested.

I never got Gnome-Boxes to work.  OTOH, Gnome isn't exactly known for making efficient software.

---

### Post by ross02012 on 2023-08-23
Thanks for your reply

I'm running Windows 11; but just to be clear, I'm having issues when I have Gnome Boxes closed, not just when I'm running it. Unless it stays on in the background somewhere I can't find. But I do also shut the Windows OS down.

I looked briefly and didn't see a simple CPU monitor, can you recommend one?

---

### Post by TheFu on 2023-08-24
> **ross02012 said:**
> Thanks for your reply

I'm running Windows 11; but just to be clear, I'm having issues when I have Gnome Boxes closed, not just when I'm running it. Unless it stays on in the background somewhere I can't find. But I do also shut the Windows OS down.

I looked briefly and didn't see a simple CPU monitor, can you recommend one?

**top, htop, glances**, or there are more serious monitoring tools like **munin, cacti, zabbix, opennms**, but I doubt those are useful to you. They are non-trival to setup, but provide many more details for what a system is actually doing by capturing 50+ types of performance data.  Don't be afraid to google for tools.  There are different, simple, tools to monitor most things.  **free, iostat, vmstat, sar,** are some other "simple" examples.  Top is probably the first tool used, but not all the column headings mean what you may think they mean. Beware.

If you wait for personal recommendations, you'll get only what the person making the recommendation suggests.  Since I'm a server admin, I avoid GUI tools. They are next to useless for server management, since servers don't have any GUI. Also, I'm not afraid to spend 30 minutes setting up a monitoring system post-install to provide more details. I doubt that interests you.  So, the tools you are likely to use will be simplistic with a simplistic view. Nothing wrong with that, provided it helps you.

---

### Post by ross02012 on 2023-08-24
Thanks. Overall it doesn't seem like the computer is running hard all processes are below 1% except occasionally the app store at 5-8%, but it sure is warm.

One core is running at near 100%, and it's not always the same core, the rest are around 10%. I don't know how to narrow that down to why.

My computer also stopped sleeping, both with time and with closing the lid. Would this be easier to track down?

---

### Post by TheFu on 2023-08-24
> **ross02012 said:**
> Thanks. Overall it doesn't seem like the computer is running hard all processes are below 1% except occasionally the app store at 5-8%, but it sure is warm.

One core is running at near 100%, and it's not always the same core, the rest are around 10%. I don't know how to narrow that down to why.

My computer also stopped sleeping, both with time and with closing the lid. Would this be easier to track down?

I don't know. I prevent my systems from sleeping to extend the lifetime.  I haven't booted an ubuntu laptop in a few years, but the last time I did, sleep worked. I don't hibernate and never have due to security concerns. If you do want to track that down, open a new thread and provide lots of clear OS and hardware details.  Running **inxi -Fxxz** would be a good start. Post that output to the thread, so people don't need to ask for it.

A warm computer could just mean there's dust inside or blocking the fan outlets.  Clean it. Dust sticks to both sides of the fan blades.

---

### Post by ross02012 on 2023-08-24
Thanks, I'll try a new post.

All this started right after installing boxes, so I thought that was most relevant.

---

### Post by TheFu on 2023-08-24
I didn't say this, but don't block any air inlets around and under the laptop.  Also, many laptop models use the keyboard area to release heat, so closing the lid completely isn't a good idea.  I had a 2010 Dell laptop like that. I'd leave the lid closed enough to turn off the screen, but not so closed to prevent airflow.  I setup a little fan to blow over the keyboard so it wouldn't overheat.

A newer Asus laptop that I'd put to sleep nightly was setup to sleep whenever I closed the lid.  About once a month, I'd reboot it, based on getting a new kernel in a patch set.

---

### Post by ross02012 on 2023-08-24
Thanks. I do know how to clean a computer and not block ports. I haven't opened it to clean it out, just seems suspicious to me that all these things changed at once, but you're right, they could all be separate.

---

