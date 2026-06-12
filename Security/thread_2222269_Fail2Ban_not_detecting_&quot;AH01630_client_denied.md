---
title: "Fail2Ban not detecting &quot;AH01630 client denied by server configuration&quot;"
date: 2014-05-05
forum: Security
---

### Post by sahendrickson on 2014-05-05
It appears that /etc/fail2ban/filter.d/apache-auth.conf looks for the following regex pattern for failed access:

^%(_apache_error_client)s (AH01797: )?client denied by server configuration: (uri )?\S*\s*$

In my log files a new "client denied by server configuration" entry is appearing:

[Mon May 05 15:46:07.213547 2014] [authz_core:error] [pid 8119:tid 139902360438528] [client X.X.X.X:54677] AH01630: client denied by server configuration: some_uri

This appears to have changed in 12.04 so that the new error code AH01630 is being used rather than AH01797, as before.

I think the fail2ban regex should be updated to:

^%(_apache_error_client)s (AH01(630|797): )?client denied by server configuration: (uri )?\S*\s*$

How would I get that submitted to the package maintainer?

Thank you,
-- Scott

---

