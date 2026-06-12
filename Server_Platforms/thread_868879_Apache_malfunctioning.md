---
title: "Apache malfunctioning"
date: 2008-07-24
forum: Server Platforms
---

### Post by sysadmn on 2008-07-24
Hey!

I'm a member of a small system administrator team, who's running a medium sized free non-commercial service. We have a powerful dedicated server for hosting our services. We have about 500-600 users.

Last month our Apache started to malfunction. When I use htop I can see sometimes that some instances pop up as <defunct> and disappear, but this is not all. Once or twice in 24 hours Apache's cpu load skyrockets and only killing it via console helps. Apache restart would take forever when it gets to that condition.

I'm not entirely sure what's causing us these problems. I've been trying to solve the issue for a month now to no avail. It could be a misconfiguration by someone of our team. It could be the fact that we are running on VMWare Server. Or it could be an user trying to crash our Apache intentionally.

So now I turn to you, the Ubuntu community, for help. Has anyone of you ever ran into something similar to this? Any ideas what could be causing this?

If requested, I can provide you with a sample of our apache configuration along with php.ini.

---

### Post by azadpanchi on 2008-07-25
If you are looking to find out if someone maybe trying to intentionally cause too many connections to apache I would recommend using netstat and identifying unique connections being made to apache or port 80.  If there are a lot of connection from a single IP Address then you have your answer.  Use netstat and then pipe the results and grep for connection made to port 80.

---

