---
title: "sshd crashes with SELinux enabled"
date: 2009-12-20
forum: Security
---

### Post by sotocan on 2009-12-20
Server 9.10 64-bit with latest updates.
After successfully installing selinux, enabling the 'ubuntu' policy in permissive mode, the system informed me that it will relabel itself on reboot. So I did reboot it. After waiting for a few minutes, I used again putty to reconnect to the server. To my surprise putty lost connection right after I entered my credentials. After that I tried connecting from my desktop's terminal through ssh. After writing my username and password and pressed enter, a memory map appeared. In the very beginning the error message was like: glibc detected an invalid pointer...
I searched it on google and the best thing I found, was something about incorrect context labeling for sshd, that is causing it to crash...
With remote-console I was able to login and verify that selinux was enabled, with the ubuntu profile, in permissive mode. The boot messages indicated  that a relabel had taken place...

Any ideas-recommendations???  

Here is the output from relabel:
root@Ubuntu-910-karmic-64-minimal ~ # fixfiles -f -F relabel
Cleaning out /tmp
/bin/rm: cannot remove `/tmp/.X11-unix': Is a directory
/bin/rm: cannot remove `/tmp/.ICE-unix': Is a directory
Relabeling / /boot
*************************************************************
find: unknown predicate `-context'
find: unknown predicate `-context'
 
Note, if I disable selinux and restart server, sshd works just fine!
Kind Regards.

---

