---
title: "ltsp: SCREEN_02=telenet error &quot;telnet not found&quot;"
date: 2008-02-17
forum: Server Platforms
---

### Post by mxc on 2008-02-17
Hi all,

I need to have my thin clients telnet to another server on login. From the edubuntu documentation it appears that one just needs to add something like

[default]
SCREEN_02=telnet
TELNET_HOST=<ip addy>

But when I do this I get a message on screen02 to press enter to telnet. Then I get an error "/usr/lib/ltsp/screen.d/telnet 59 telnet not found" I have chroot /opt/ltsp/i386 and done a "apt-get install telnet" and can telnet to the machine from chroot environment.

However I still get the message "telnet not found" from the thin client. How do I fix this.

thanks

---

