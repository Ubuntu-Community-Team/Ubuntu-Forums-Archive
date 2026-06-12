---
title: "Maintain iptables script or start using shorewall"
date: 2007-09-26
forum: Server Platforms
---

### Post by fatbastard spice on 2007-09-26
I've been running an Ubuntu server for about five years now, providing a few basic services (ssh, http, etc) as well as basic LAN functionality. When i looked at setting up a firewall originally i just ended up coding my own bash script.

I recently upgraded to feisty and was wondering how important it is to actively maintain that bash script. I'm not  worried about maintaining the port forwarding/opening part, it was just that i wasn't putting in any time to finding out if new rules should be added to go along with the current base level stuff i have in my script (e.g. dos protection, fraggle/martian attacks, dictionary cracking etc.).

So if these base level iptables rules do need updating i thought i might be better off using shorewall, or is there a mailing list somewhere that covers this sort of thing?

---

### Post by koenn on 2007-09-26
If you're running a server, you usually know what services it provides, so it's trivial to allow those services (or their ports) in a bash script and be done with it.

---

