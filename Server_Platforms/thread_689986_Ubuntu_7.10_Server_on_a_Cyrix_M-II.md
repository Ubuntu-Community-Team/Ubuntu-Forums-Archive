---
title: "Ubuntu 7.10 Server on a Cyrix M-II"
date: 2008-02-07
forum: Server Platforms
---

### Post by sherman on 2008-02-07
Hey hey,
I have been using a Cyrix M-II 333Mhz machine for the past 2 years running Ubuntu 5.04 server... excellent 'low power' (and low noise!) samba and apache server for my website at fourtytwo.org... but umm.. well.. I cannot install 7.10 server on it because there is no default kernel for this type of machine.

I tried to cheat last night by putting a harddrive into a PIII machine and installing 7.10 server, and then apt-get installed linux-image-2.6.xxx-386.

Putting the harddrive back into the cyrix machine, it hangs on boot saying I should try acpi=force (which I also tried as a boot option in grub).

Any chance there is a solution? I kinda dont want to use a PIII or P4 for this...

---

### Post by sherman on 2008-02-07
would installing 7.04 then dist-ugrading help?

---

