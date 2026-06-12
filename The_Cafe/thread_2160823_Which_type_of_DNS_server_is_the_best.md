---
title: "Which type of DNS server is the best?"
date: 2013-07-08
forum: The Cafe
---

### Post by chong601 on 2013-07-08
Public DNS, caching DNS running on localhost or recursive DNS on localhost? Which is the best?

---

### Post by CharlesA on 2013-07-08
Depends on your situation/environment.

You could try running this: [http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

To see which public server is the fastest for you.

---

### Post by sanderj on 2013-07-08
> **CharlesA said:**
> Depends on your situation/environment.

You could try running this: [http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

To see which public server is the fastest for you.

namebench ... what a great tool. Thank you for mentioning it.

---

### Post by chong601 on 2013-07-09
> **CharlesA said:**
> Depends on your situation/environment.

You could try running this: [http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

To see which public server is the fastest for you.

Well, I currently running a local recursive DNS on my Windows Vista... just upgraded from a local caching DNS... :)
Trying to run it on my Ubuntu 10.04 soon (work in progress)
Used namebench before but it nags at my local DNS and say other is faster...
Now, I use DNS Benchmark ( [https://www.grc.com/dns/benchmark.htm](https://www.grc.com/dns/benchmark.htm) ) because it gives more detail about DNSSEC and DNS rebinding protection on a particular DNS resolver...
This is what I get after working for a few weeks experimenting with a DNS server....

---

### Post by CharlesA on 2013-07-09
Are you running the desktop version of 10.04? If so, it has been [End of Life]("https://wiki.ubuntu.com/Releases") for a while now, and it would be a good idea to upgrade to a supported release.

---

### Post by Quarkrad on 2013-07-09
Out of interest - I installed namebench on my 13.04 machine via the software centre.  It seemed to run OK but at the end it showed this in Terminal:

[B]> Sending 250 queries to 11 servers... [2715/2750]
> Sending 250 queries to 11 servers... [2724/2750]
> Sending 250 queries to 11 servers... [2736/2750]
> Sending 250 queries to 11 servers... [2749/2750]
> Sending 250 queries to 11 servers... [2750/2750]
> Error querying alharbitelecom GB [62.3.32.17]: [www.tomtomfree.com.:](www.tomtomfree.com.:) Timeout
> Error querying UltraDNS [156.154.70.1]: talkingclipboard.com.: Timeout
> Saving report to /tmp/namebench_2013-07-09_2001.html
> Saving detailed results to /tmp/namebench_2013-07-09_2001.csv
> Opening /tmp/namebench_2013-07-09_2001.html
> Complete! BT-8 GB [194.72.9.38] is the best.

(process:8699): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed[/B]


Any help on the last line would be appreciated.

---

### Post by chong601 on 2013-07-10
> **CharlesA said:**
> Are you running the desktop version of 10.04? If so, it has been [End of Life]("https://wiki.ubuntu.com/Releases") for a while now, and it would be a good idea to upgrade to a supported release.

Just noticed it lately but no plans on upgrading it soon...

---

### Post by ubuntu27 on 2013-07-17
Best DSN server? [OpenNIC]("http://www.opennicproject.org/")

---

