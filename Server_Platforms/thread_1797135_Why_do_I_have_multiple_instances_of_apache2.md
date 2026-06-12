---
title: "Why do I have multiple instances of apache2?"
date: 2011-07-04
forum: Server Platforms
---

### Post by duncanjbrown on 2011-07-04
Hi,

When I invoke ```
ps a x
``` I can count no fewer than 11 instances of apache2! All of them look like this:

```
 PID TTY      STAT   TIME COMMAND
 1669 ?        S      0:02 /usr/sbin/apache2 -k start

```

Is this normal?

---

### Post by rudelgurke on 2011-07-04
Yes - this is normal. If you check with "ps aux" you'll see "apache2" running as "root" - required to open port 80 & port 443 and then several processes running as www-data or whatever user your configured in the apache configuration.
This "root" process open the port, is used for logging and spawns or ends processes (the www-data ones) depending on the load.

---

### Post by duncanjbrown on 2011-07-04
Thanks- that's a relief. Why would it need to spawn more processes depending on load - isn't one enough? What sort of load would be required to force the creation of a new one?

EDIT - i meant more processes beyond the first www-data one

---

### Post by Dangertux on 2011-07-04
> **duncanjbrown said:**
> Thanks- that's a relief. Why would it need to spawn more processes depending on load - isn't one enough? What sort of load would be required to force the creation of a new one?

EDIT - i meant more processes beyond the first www-data one

Each "child process" that you are seeing only handles a certain number of requests in it's life. Once it's lifetime expires it is killed off by the Apache2 parent process (depressing I know), and when the need arises another Child Process is spawned. This is done to prevent memory leaks and promote efficiency in the server. You can set the number of requests per child, and the default amount of child processes started in your apache.conf file.

This does not mean it uses any more resources then it would if it were a single process.

---

### Post by SeijiSensei on 2011-07-04
> **Dangertux said:**
> This does not mean it uses any more resources then it would if it were a single process.

Well the child processes do consume memory, though not a lot.  Most of the code they use is shared among all of them.  On the machine I'm using here, the children share 119M of memory with another 4M uniquely allocated to each child.

> I can count no fewer than 11 instances of apache2! All of them look like this:

If you run "ps aux" you'll get more details including the shared and unique memory allocations.

Remember that when someone visits a web page, they'll often generate many separate HTTP requests for the objects referenced on that page.  Having multiple children to serve those requests improves overall performance.

I have a default Apache on Ubuntu installation; it allocates five children to begin with.   There's a [StartServers]("http://httpd.apache.org/docs/2.2/mod/mpm_common.html#startservers") directive in /etc/apache2/apache2.conf that controls how many servers are allocated at startup and how that number is managed dynamically as the server is running.  This document provides the details: [http://httpd.apache.org/docs/2.2/mod/prefork.html](http://httpd.apache.org/docs/2.2/mod/prefork.html)

The Apache documentation includes these encouraging words:

> This [Multi-Processing Module] is very self-regulating, so it is rarely necessary to adjust its configuration directives. Most important is that MaxClients be big enough to handle as many simultaneous requests as you expect to receive, but small enough to assure that there is enough physical RAM for all processes.

I've rarely if ever changed these settings, and I've been using Apache for over a dozen years.

As it turns out, the default Ubuntu configuration doesn't guillotine its children at all.  MaxRequestsPerChild is set to zero in all three MPM configurations defined in apache.conf.  Processes with a zero value never die; the Apache docs mention that this is nevertheless a common setting in many default configurations.  (Maybe it demonstrates that some Apache packagers can't bring themselves to kill children!)  If you don't specify any value for MaxRequestsPerChild, they expire after 10,000 connections.

I have a public server running CentOS that hosts a few sites.  Right now it has 20 children running, compared to the ten on Ubuntu.  CentOS 5.5 also respawns listeners after 4000 connections.  Ubuntu, as I noted, never respawns.

---

### Post by duncanjbrown on 2011-07-06
Thanks for this detail. I had no idea it worked in this way.

> Remember that when someone visits a web page, they'll often generate many separate HTTP requests for the objects referenced on that page. Having multiple children to serve those requests improves overall performance.

Out of curiosity, if I try to GET a few things - some html, a few <imgs> and a couple of css files, for example - how are these multiple requests carved up and divided amongst the child processes? Do they queue up for them, go and fulfil them, then come back for more when they're done?

---

