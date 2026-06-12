---
title: "Jailkit...a couple questions"
date: 2008-03-03
forum: Security Discussions
---

### Post by moonpup on 2008-03-03
Hi all,

I've compiled and successfully installed jailkit on gutsy. After setting up the jail and a user account that is jailed, I have noticed these two things that I don't know how to fix and hope someone else has encountered them.

First, when my jailed user logs in I see the following message before the shell prompt:

**bash: groups: command not found**
**test@ubuntu:~$**

I'm sure this has something to do with the restricted bash profile, but not sure what. Maybe it's nothing to worry about, but still curious.

Second, i did the following to add telnet to the jail.

**sudo jk_cp -o -j /home/jail /usr/bin/telnet**

It copied the binaries and libraries as it should, but when the jailed user runs telnet I get this error...

**telnet: could not resolve localhost/telnet: Servname not supported for ai_socktype**

Any ideas or solutions appreciated.

Thanks!

---

### Post by NicklauZ on 2008-03-06
For the first question. I had the same problem, and solved it by copying the file /usr/bin/groups to /jail/usr/bin/. Hope that helped.

---

### Post by moonpup on 2008-03-06
Thanks, that's good to know. You should send that info to the developer Olivier as I emailed him about that but he didn't know how to fix it. He will return an email so let him know.

I found one bug which he is going to fix and it concerned ssh not working because he forgot to include /dev/null for the devices line in the ssh section.

---

