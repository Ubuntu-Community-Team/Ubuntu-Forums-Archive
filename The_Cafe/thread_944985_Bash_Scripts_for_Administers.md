---
title: "Bash Scripts for Administers"
date: 2008-10-11
forum: The Cafe
---

### Post by mmilitia9 on 2008-10-11
Hey everyone!

I'm taking a Unix course which assigned a report the other day on Administrative bash scripts. I was curious about what automated admin scripts would you run on a daily basis that you find important to know as an Administrator?

I'm not looking for scripts, but just ideas to get started on one. So what are some good important tasks that an administrator should be doing that's tedious enough to need an automated script for?

Thanks,

Dominick

---

### Post by prshah on 2008-10-12
> **mmilitia9 said:**
> 
just ideas to get started on one. So what are some good important tasks that an administrator should be doing that's tedious enough to need an automated script for?


Clearing out downloaded deb files; all updates / upgrades / installs dump deb files into /var/cache/apt/archives/ which are not used once the update / upgrade / install is completed; cleaning out these files periodically (if they are over a certain size) is good.

---

### Post by bodhi.zazen on 2008-10-12
bash script are helpful to automate and ease the burden of repetitive tasks.

It will vary on the server but examples may be backups, clearing temp files, security monitoring, rotating logs, adding users (imagine adding 100 users), etc.

---

### Post by sinclair86 on 2008-10-12
> It will vary on the server but examples may be backups, clearing temp files, security monitoring, rotating logs, adding users (imagine adding 100 users), etc.

LOL.... had this post sitting open for a while and then the time that I finally hit sumbit i looked at ur post and was like awwww damn it...

---

