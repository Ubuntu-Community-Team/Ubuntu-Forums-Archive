---
title: "apt-cacher-ng -&gt; sources.list"
date: 2011-04-04
forum: Server Platforms
---

### Post by munky99999 on 2011-04-04
Apt-cacher-ng is an unusual sort of server package. Server is super easy to setup and clients are hard.

apt-get install apt-cacher-ng apache2 

and that's all it takes. It's up and running fine.

Then you have the clients to the server. You have to go manually edit each line to add like 10.11.12.13:3142/ in for each of the sources. Sure does discourage the use of apt-cachers.

Perhaps we could get a tool like:

apt-cache server 10.11.12.13:3142

Does it easy then?

---

### Post by MadCow108 on 2011-04-04
just put:
Acquire::http::Proxy "http://your-host:3142";
in your apt.conf or apt.conf.d
adding a extra command for this one line is overkill in my opinion.

also using the alternate installer you can set this up during installation.

you can also use the -o flag on the command line to change the proxy temporarily or set the *http_proxy* environment variable (the later use very useful for pbuilder)

---

### Post by cariboo on 2011-04-04
This really doesn't have anything to do with Natty Testing, moved to Server Platforms.

---

