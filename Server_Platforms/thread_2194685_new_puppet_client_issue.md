---
title: "new puppet client issue"
date: 2013-12-20
forum: Server Platforms
---

### Post by John_Madrid on 2013-12-20
Hi All,

I have a bunch of servers currently in a puppet client - master relationship. My existing puppetmaster is working with existing Ubuntu 12.04 servers, each with different functionality.  I am now installing a new box, with precise as well, but this guy is a little stubborn.  when it is time to run puppetd -t here is what I am getting.

[FONT=arial]--[/FONT][FONT=tahoma][/FONT]
[FONT=tahoma, sans-serif]err: Could not retrieve catalog from remote server: Error 400 on SERVER: Unknown function validate_bool at /etc/puppet/modules/apt/manifests/init.pp:36 on node new_puppet_client[/FONT][FONT=arial][FONT=tahoma, sans-serif]warning: Not using cache on failed catalog[/FONT][/FONT]
[FONT=tahoma, sans-serif]
[/FONT][FONT=arial][FONT=tahoma, sans-serif]err: Could not retrieve catalog; skipping run

why is it even looking at [/FONT][FONT=tahoma]/etc/puppet/modules/apt/[/FONT][FONT=tahoma]manifests/init.pp where i don't even use that directory to run noeds.pp or init.pp[/FONT][FONT=tahoma, sans-serif]
[/FONT][FONT=tahoma, sans-serif]

[/FONT][/FONT]

---

