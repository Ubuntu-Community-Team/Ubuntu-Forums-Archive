---
title: "Home server hangs at boot"
date: 2009-05-10
forum: Server Platforms
---

### Post by tstack77 on 2009-05-10
My home server inexplicably stopped working earlier today (intrepid), and all samba/nfs/ssh connection attempts timed-out. I tried simply giving her a hard-reset, but when that didn't help I attached a keyboard and monitor to try and see the problem. I thought it was simply a network issue, but am now seeing that booting halts at "Configuring network interfaces...".

What can I do to diagnose this issue further?

-axel

---

### Post by ikonia on 2009-05-10
are any of your network interfaces set to GET dhcp addresses ?

that would be my first thing to check.

Second, boot into single user mode (recovery mode from grub) and look in the syslog for any warnings info that may help

---

