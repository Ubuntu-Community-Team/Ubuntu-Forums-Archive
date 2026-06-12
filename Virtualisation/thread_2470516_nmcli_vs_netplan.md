---
title: "nmcli vs netplan"
date: 2022-01-02
forum: Virtualisation
---

### Post by aljames2 on 2022-01-02
Using Ubuntu MATE 20.04 desktop as KVM host machine.  The OS uses Network Manager by default.  I prefer using the netplan configuration file to set up my bridge, dns, etc.  The netplan file of course shows network manager as my renderer.  For now I have configured my setup using Network Manager on the command line.

If I understand correctly, to use netplan, like I am used to on my server, I can disable Network Manager, and enable systemd-networkd, and then use networkd as my renderer.  Of course doing this disables all of the network manager GUI stuff on the desktop.  Is there a cleaner way in order to use the netplan configuration file vs. network manager?

---

### Post by TheFu on 2022-01-02
Cleaner?  I find the netplan file to be the best option remaining, since the deprecation of ifupdown (/etc/network/interfaces).  I've been purging all network-manager* and nm-* packages almost 10 years now with few issues.

Even on laptops with both wifi and wired ethernet connections, I don't use nm- anything.  To manage wifi connections on wifi when away from home, I use wicd-curses. I don't use wifi in the house. That is for guests and other untrusted devices.

---

### Post by MAFoElffen on 2022-02-15
There is no such thing as: "nmclii vs netplan" (specifically)

NetPlan is a different, separate piece from systemd-networkd and/or NetworkManager (of which nmcli is one of the tools of network-manager)... You can still use the NetPlan utilities, no matter whether the renderer is systemd-networkd or NetworkManager.

Seems to be a lot of confusion with the two network renderers (managers) on Ubuntu (Linux)... Actually each has it's pro and cons... And not much people know that both managers can be run at the same time, as long as they are managing different devices. Let me say that in different wording so there is no confusion on that-- As long as each renderer is managing different network devices and there is no overlap with that on a specific device, they can coexist and run at the same time!!! 

On the other side of that, since a lot of people do not know that, it is hard to configure both to exist and run together at the same time, because you have to ensure that there are no conflicts between the two... It's one of those cases where "it *can* be done..." but not wise thing for some average person to do that unless you know what they are doing.

Both of these were developed by RedHat over a decade ago. Yes, neither is "new" or newer technology. Each reads files from different locations. Both manage network devices. systemd-networkd is better at virtual networking for containers and Virtual Machines. (Static, with Server kinds of events.) NetworkManager is better at sensing changes in the environment which require dynamic changes- Desktops and Laptops, plugging in a cable, especially wireless devices and Wireless Network (SSID) changes...(User kinds of events.)

I don't believe that one is better than the other over-all. They are just different.

And they are not NetPlan. They both use NetPlan and the NetPlan .yaml files. 

So you can see that the title of this thread is a bit incorrect and misleading...

---

### Post by TheFu on 2022-02-15
I use wicd-curse for systems with wifi that I want to use. It understands that ethernet should always have priority and disconnects wifi when the plug is connected. This only works for trivial network setups.

Having static IPs for systems that don't move but run network services is just so much easier than letting DHCP deal with it. IPs that change are not good for most network services.

---

### Post by kevdog on 2022-02-16
Serious question -- what the heck is the purpose of netplan anyway??  I mean this since netplan is really a frontend for systemd-networkd.  You can configure systemd-networkd directly using almost the same commands but just different syntax.  I think netplan uses yaml, systemd-networkd doesnt however the documentation is pretty straight forward.  Why even use netplan in the first place??

---

### Post by TheFu on 2022-02-16
> **kevdog said:**
> Serious question -- what the heck is the purpose of netplan anyway??  I mean this since netplan is really a frontend for systemd-networkd.  You can configure systemd-networkd directly using almost the same commands but just different syntax.  I think netplan uses yaml, systemd-networkd doesnt however the documentation is pretty straight forward.  Why even use netplan in the first place??

NIH syndrome, is my guess.  I'm not thrilled with networkd, but it is better for complex networking that anything network-manager does.

IMHO.

Sometimes I'm tempted to rip all that crap out and create some scripts to bring up and down the non-trivial network stuff manually. For all the time we waste on these "ease of use" overlays and pre-processors, a 10 line, bonehead, script would be easier.

---

### Post by rsteinmetz70112 on 2022-02-16
> **TheFu said:**
> NIH syndrome, is my guess.  I'm not thrilled with networkd, but it is better for complex networking that anything network-manager does.

IMHO.

Sometimes I'm tempted to rip all that crap out and create some scripts to bring up and down the non-trivial network stuff manually. For all the time we waste on these "ease of use" overlays and pre-processors, a 10 line, bonehead, script would be easier.

I've been convinced for a long time that the developers sometimes get enamored with a shiny new toy and can't wait to implement it, often without seriously evaluating whether it's better or not.

---

### Post by TheFu on 2022-02-16
> **rsteinmetz70112 said:**
> I've been convinced for a long time that the developers sometimes get enamored with a shiny new toy and can't wait to implement it, often without seriously evaluating whether it's better or not.

I've seen this too. When I was a developer, the question was always, does what we have work? Can we retain any files that customers know about as-is, so they aren't impacted?  Sometimes it is necessary to throw everything out, but extending the existing is almost always a better choice.

I suspect that YAML was the shiny new thing they wanted to learn. YAML is much to picky to be a good language for end-users.  The old win3 ini file format is better for those people.  I've used that in programs that we sold to clients for $Ms as part of our import/export features. There were some growing pains with that code.  I expected import files to have 1000 lines - just to setup meta-objects.  One of our clients had a manually created import file with 2M lines that took overnight to be imported ... assuming their workstation didn't crash before completion.  If it crashed, the nested DB transactions would all need to be rolled back to prevent partial results.  I suggested they split their import objects up to be per meta-tree and I created a separate import method for the type of object that had 1.5M entries ... with a single transaction around the entire import, not follow the OO methods of 1 transaction per DB record.  BTW, the DB was running on a grid AIX server with lots of RAM and fast SAN storage. It wasn't the problem. We had a 4-teir architectures system. The app and db layers were running on similarly sized boxes. It was just her workstation that was under-powered. It was Windows and they were using a double-byte character encoding. This was before UTF8/Unicode.

Ah, the good ole' days.

---

