---
title: "Seeking wake on lan suggestions."
date: 2011-06-11
forum: Server Platforms
---

### Post by steve_UP on 2011-06-11
I'm looking for suggestions and input on using wake on lan to help administer multiple pc's for my work. I'd like to be able to use wake on lan to wake up multiple pc's so I can apply updates to windows pc's. Currently we have a ubuntu server set up at these sites so that we can remote into the ubuntu server using VNC, then using the Remote Desktop equivalent to remote in to the pc's so we can provide tech support without having to drive for hours each time. What I'm seeking is to use wake on lan from this on site server to turn on, what is almost exclusively, dell computers on remotely. 

I'm trying different things to make it work. Today at one site I was able to remote in to the ubuntu server while on site through a laptop on wifi, and then wake the target computer so that I can remote into the target computer and do my work. It's hit or miss, unfortunately.

After an afternoon of trial and error the two remote servers I was working through stopped accepting VNC login attempts, but I can ping them. I can only assume that they basically crashed.... To remedy this I was wondering if I should set them up with client, virtual ubuntu OS's, so that if while I'm trying to "poke" these on site pc's into waking up, and the program crashes the OS, I can still have access to the the on site Ubuntu server. 

Does this seem viable, or am I going about this the wrong way?

I did set the wake on lan setting to enabled on all of the dell pc's bios's that I was working on. The wakeonlan terminal command was very "hit or miss" even though the ubuntu server was on the same subnet. :(

Ideally I'd like to be able to use wake on lan across the internet, but i think giving redundancy to the on site servers may be more pliable across routers and firewalls.

---

### Post by volkswagner on 2011-06-11
I think you are on the right path to get it reliable locally before trying from outside the LAN.

I have noticed some proprietary MOBO's such as those from Dell, HP, etc. have WOL only reliable from a sleep state, not powered off state.  Perhaps you can confirm if this is true on some/all PC's in question.

Also within the NIC properties there is a MS Windows setting under "power management", one for allowing only local devices to wake, and a second that allows device to turn off to save power.

Also some router firmware allows WOL, such as DD-WRT.

---

