---
title: "Snapd - Connecting to search.apps.ubuntu.com"
date: 2017-07-27
forum: Server Platforms
---

### Post by terencewklau on 2017-07-27
Hi,

There's some difference on the snapd configuration between 16.04.1 and 16.04.2.

On our 16.04.2 boxes, syslog has lots of entries regarding connections to [https://search.apps.ubuntu.com](https://search.apps.ubuntu.com) like this:

Jul 27 11:42:13 Server /usr/lib/snapd/snapd[939]: retry.go:81: DEBUG: Retrying because of: net/http: request canceled while waiting for connection (Client.Timeout exceeded while awaiting headers)
Jul 27 11:42:13 Server /usr/lib/snapd/snapd[939]: retry.go:49: DEBUG: Retrying [https://search.apps.ubuntu.com/api/v1/snaps/metadata](https://search.apps.ubuntu.com/api/v1/snaps/metadata), attempt 2, elapsed time=10.000756484s
Jul 27 11:42:23 Server /usr/lib/snapd/snapd[939]: retry.go:81: DEBUG: Retrying because of: net/http: request canceled while waiting for connection (Client.Timeout exceeded while awaiting headers)
Jul 27 11:42:23 Server /usr/lib/snapd/snapd[939]: retry.go:49: DEBUG: Retrying [https://search.apps.ubuntu.com/api/v1/snaps/metadata](https://search.apps.ubuntu.com/api/v1/snaps/metadata), attempt 3, elapsed time=20.001272897s

Our server is not allowed to access the above web site.  16.04.1 doesnt have the same entries in syslog.

Is there a snapd configuration file somewhere to change this behaviour?

The other differences I can see between 16.04.1 and 16.04.2 is:

16.04.1 - package snap-confine is installed
16.04.2 - additional snapd.system-shutdown.service is installed

Short of disabling snapd.service, how can I configure snapd to stop connecting to search.apps.ubuntu.com?  I couldn't find any snap config in/etc or anywhere else for that matter.

Any advice would be much appreciated.  Thanks.

---

