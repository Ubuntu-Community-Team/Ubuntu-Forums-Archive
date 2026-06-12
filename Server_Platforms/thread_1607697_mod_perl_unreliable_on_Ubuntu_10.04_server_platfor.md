---
title: "mod_perl unreliable on Ubuntu 10.04 server platform"
date: 2010-10-28
forum: Server Platforms
---

### Post by blentus on 2010-10-28
Hello.

I have been working on a mod_perl application for a while. I was using Debian 5 as a testing platform, and everything worked fine.

It has been decided that Ubuntu 10.04 server will be deployed on production machines, so I have moved my test environment to Ubuntu 10.04 server as well.

After moving to Ubuntu 10.04 environment, load tests against the application (using ApacheBench) started showing failed requests (threads being in 'W' state, which is "Sending Reply" - worker threads ended up hanging so some requests were timing out), so I started investigating, trying to find the bug in the application.

No matter what changes I made to the app, it was still failing. I pretty much ended up returning from the application immediately after invocation, but I would still end up with failed requests.

So, I decided to completely disable all mod_perl apps I had configured, removed all of mod_perl configuration (so no extra modules are loaded, etc), only defaults remained, and ended up with testing a very basic application:

```

package MyPackage::ltest;

use strict;
use warnings;

use Apache2::RequestRec;
use Apache2::RequestIO;

sub handler
{
	my $r = shift;
	$r->content_type("text/plain");
	
	$r->puts("OK\n");
	$r->rflush;

	return 0;
}

1;

```

I have configured Apache and ran the tests, but I got failed requests again. Now, it doesn't make sense that something this simple ends up hanging. Testing looks like this:

```

dev@dev:~> ab -c 20 -n 10000 "http://192.168.1.8/ltest" 
This is ApacheBench, Version 2.3 <$Revision: 655654 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking 192.168.1.8 (be patient)
Completed 1000 requests
Completed 2000 requests
Completed 3000 requests
Completed 4000 requests
Completed 5000 requests
Completed 6000 requests
Completed 7000 requests
Completed 8000 requests
Completed 9000 requests

apr_poll: The timeout specified has expired (70007)
Total of 9993 requests completed

```

This is the handler configuration:

```

<Location /ltest>
  SetHandler perl-script
  PerlResponseHandler MyPackage::ltest
</Location>

```

On some occasions, test will go through and I will get no errors. But very very often (especially when I increase number of total requests, over 1,000), I will end up getting up to 20 requests timing-out (and Apache worker threads hanging), which is not acceptable for something this simple.

So, I just wanted to point out that there might be an issue with mod_Perl on Ubuntu 10.04 server.

I have tested this on 3 different setups:

1) Ubuntu 10.04 64-bit server, running on Virtual Box
2) Ubuntu 10.04 64-bit server, running on real server hardware
3) Ubuntu 10.04 32-bit server, running on Virtual Box

I have observed same type of behavior on all 3.

As I mentioned before, I moved to Ubuntu 10.04 server from Debian 5 test environment. I had no problems on Debian before, so I have tested this on Debian as well before posting, to make sure it really is Ubuntu specific issue.

So, I just made 1 million requests to a Debian box, and had no problems and no failed requests. Did few more hundreds thousands requests in batches of 100,000, just to make sure, and again - had no issues whatsoever.

Ran 1 million requests against Ubuntu 10.04 server, and ended up with failed requests again:

dev@dev:~> ab -c 20 -n 1000000 "http://192.168.1.8/ltest"
This is ApacheBench, Version 2.3 <$Revision: 655654 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, [http://www.zeustech.net/](http://www.zeustech.net/)
Licensed to The Apache Software Foundation, [http://www.apache.org/](http://www.apache.org/)

Benchmarking 192.168.1.8 (be patient)
Completed 100000 requests
Completed 200000 requests
Completed 300000 requests
Completed 400000 requests
Completed 500000 requests
Completed 600000 requests
Completed 700000 requests
Completed 800000 requests
Completed 900000 requests
apr_poll: The timeout specified has expired (70007)
Total of 999981 requests completed

Ended up with 19 worker threads hanging forever.

Oh yes, forgot to mention, I'm using apache2-mpm-worker Apache setup.

Any comments, recommendations and/or fixes are very welcome :)

Thank you.

---

### Post by parsim on 2011-10-27
I am experiencing this problem, as documented [here](http://www.gossamer-threads.com/lists/modperl/modperl/99879). Did you ever find a solution?

---

### Post by s2young on 2011-12-09
We are having this same issue trying to upgrade from Ubuntu 9.04 to 11.10 on Rackspace. The CPU pegs during simple load tests that shouldn't cause the server to sweat in the least.

---

### Post by parsim on 2012-03-11
Latest news: the problem has [been patched](http://www.gossamer-threads.com/lists/modperl/dev/104026) in mod_perl. I'm not sure if it will make it into mod_perl 2.0.6, since they've already rolled release candidates for that.

---

