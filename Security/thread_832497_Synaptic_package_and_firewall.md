---
title: "Synaptic package and firewall"
date: 2008-06-17
forum: Security
---

### Post by isellapples on 2008-06-17
Hi, im running a dedicated webserver and have just got round to installing Guarddog to replace ufw as my firewall. VNC, SSH, http etc all work perfecto but its blocking the synaptic package installer/update manager. Any ideas as to what other ports i should try opening to let it work?

cheers

(oh, and if guarddog is a bad choice then let me know as eventually my website will be saving personal info nd i wouldnt be too popular if i got hacked now would i!)

---

### Post by brian_p on 2008-06-17
> **isellapples said:**
> Hi, im running a dedicated webserver and have just got round to installing Guarddog to replace ufw as my firewall. VNC, SSH, http etc all work perfecto but its blocking the synaptic package installer/update manager. Any ideas as to what other ports i should try opening to let it work?

Synaptic is a client  not a server so it would appear you are blocking outgoing requests to port 22 or port 80 on the remote machine. A proxy problem? An IP address problem?

> (oh, and if guarddog is a bad choice then let me know as eventually my website will be saving personal info nd i wouldnt be too popular if i got hacked now would i!)

I'd expect the way the webserver is set up to have more bearing on the safety of personal data than what could be provided by a firewall.

---

### Post by isellapples on 2008-06-17
ah that did it :) i forgot to enable port 22 for internet connections - only had it on local, which would explain why SSH appeared to be working fine for me. taa for pointing out what i should have realised

---

