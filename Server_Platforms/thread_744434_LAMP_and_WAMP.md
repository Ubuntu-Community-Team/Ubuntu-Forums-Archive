---
title: "LAMP and WAMP"
date: 2008-04-03
forum: Server Platforms
---

### Post by c-ron on 2008-04-03
Which LAMP and WAMP software package do you like?

[http://en.wikipedia.org/wiki/List_of_AMP_Packages](http://en.wikipedia.org/wiki/List_of_AMP_Packages)
and
[http://en.wikipedia.org/wiki/Comparison_of_WAMPs](http://en.wikipedia.org/wiki/Comparison_of_WAMPs)

My company has a lower-end machine (P4 1.2 GHz, 512 MB) running Windows XP that we'd like to setup a web accessible customer db for in-house purposes (6 employees). Anyone have a suggestion on which package would be easiest to setup? There's nothing really important on the box now, so a reformat with *nix is not a problem.

Thanks!

---

### Post by tribaal on 2008-04-03
Well if you need LAMP I suggest you grab a copy of Ubuntu server and select the "LAMP" install option :)

Everything is ready out of the box :)

- Trib'

---

### Post by schneider707 on 2008-04-03
I definitely agree. Grab 7.10 or whatever version you prefer. During installing choose the LAMP package. When the installation is finished you have like 90% of your server set up. The rest are minor details of setting up connections to the other computers. I'm pretty sure any ftp program could take care of that for you.

WAMP could work. I have no experience with it but i would assume it would be a good choice as well. Linux from how I see it, is mostly ran because of the security, power, and speed it provides.

---

### Post by dmizer on 2008-04-03
7.10 will not have long term support.  with 7.10 you will have to upgrade in about 6 months in order to continue getting security updates.  dapper still has another year's worth of support, and if you install dapper, you will be able to upgrade directly to hardy without going through all the intermediate releases.  alternatively, you could wait for the final release of hardy which will have 5 years of security support on the server release.

this is something to think about seriously if you want your server to be as headache free as possible.  a distribution upgrade can cause endless headaches on a production server, so you'll want to start with something that will last a while without having to worry about that kind of mess.

i really like lighttpd.  it seems to be much more responsive, and it has a better security history than apache.  i've been using it for about 2 months now, and i love it.  very easy to set up, and very low profile.  with lighttpd, my page pops, with apache, it drew.  it is available in the repositories.

---

