---
title: "How to upgrade my SFTP protocol version?"
date: 2012-01-18
forum: Server Platforms
---

### Post by SethD on 2012-01-18
I am using a library that needs to access my server with a higher SFTP protocol than version 3, which is apparently what is default with Ubuntu installs.

I have spent quite a bit of time trying to find documentation on how to do this but everything seems to come up empty for me. Is it even possible to get anything better than v3 on an Ubuntu install?

Please note that I am referring to SFTP, and not FTPS.

Thanks,
Seth

---

### Post by craigp84 on 2012-01-18
Hi, upstream is still configured (see SSH2_FILEXFER_VERSION in sftp.h on cvsweb on openbsd.org) to report v3 although skimming the changelog it looks like they've backported at least some of the later versions features.

For next steps you can supply an alternate sftp-server program (do the vendors of your sftp client suggest any to use?) and via sshd_config you can instruct your sshd to service sftp requests with the alternative / newer sftp-server tool.

Hope this helps

---

### Post by SethD on 2012-01-18
Craig, thanks for your help.

No, there is not a suggested alternate SFTP server. Would you be able to recommend any? I'm not even sure what my options are.

---

