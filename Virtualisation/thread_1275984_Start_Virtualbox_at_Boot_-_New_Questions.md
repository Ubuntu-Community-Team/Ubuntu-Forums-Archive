---
title: "Start Virtualbox at Boot - New Questions"
date: 2009-09-26
forum: Virtualisation
---

### Post by smpoole7 on 2009-09-26
This has been asked here before, and there are some excellent suggestions in this thread:  [http://ubuntuforums.org/showthread.php?t=701735](http://ubuntuforums.org/showthread.php?t=701735) . However, the end result there is not exactly what I want.

The vital stats: the host system is an Ubuntu 8.04 LTS server. The guest in the "box" will be CentOS running (among other things) our corporate mail server.

My concerns:

1. I do NOT want Virtualbox to run as root. Unless I missed something after I pored through the script provided at the above link, it will indeed do just that.

2. Second, I don't need to save a snapshot at shutdown, the server on the guest will run non-stop. (It's on a UPS, backed up by a natural-gas-powered 40KW generator.) On those rare occasions that I take it down for maintenance, I have to go through a specific series of shutdown steps, because the server in the guest communicates with other servers in real-time.

3. However ... IF the hardware on the host machine says, "we need to shut down," VirtualBox will send an ACPI shutdown message to the guest. He will then go through those steps normally -- PROVIDED that Ubuntu will wait for the guest to finish terminating. :)

(I guess the only way to determine #3 is by experimentation, huh?)

Finally, here's the wildcard: the Ubuntu host will be running headless and text-only. I'm getting ready to remove KDE as we speak; I don't need it. Gnome was never installed.

Any tips or suggestions would be wonderful. I'm having fun learning Ubuntu (I'm a long-time OpenSuse and CentOS guy). On a completely unrelated side-note, the only issue I've had thus far with the otherwise-excellent help available online is that so much of the Ubuntu "how-to" material *assumes* that you're running Gnome. Ex., "click on System -> Do This -> Do That." If I'm running a text-only box, that's not an option. It would be helpful if some of the more advanced "how-tos" said, "do it this way if you have a GUI; if not, here are the text mode commands."

Just a suggestion.

---

