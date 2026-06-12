---
title: "url_helper.py - Network is unreachable errors when using 15.10 (Wily) on EC2"
date: 2015-09-04
forum: Ubuntu Development Version
---

### Post by victorhooi on 2015-09-04
Hi,

I'm attempting to start a Ubuntu 15.10 (Wily) Beta 1 instance on EC2:

[http://cloud-images.ubuntu.com/releases/wily/beta-1/](http://cloud-images.ubuntu.com/releases/wily/beta-1/)

The AMI I am using is ami-3795d80d.

During the startup phase, I am seeing errors like this:

[  137.303122] cloud-init[1096]: 2015-09-04 08:37:16,774 - url_helper.py[WARNING]: Calling 'http://169.254.169.254/2009-04-04/meta-data/instance-id' failed [0/120s]: request error [('Connection aborted.', OSError(101, 'Network is unreachable'))]

[  138.300220] cloud-init[1096]: 2015-09-04 08:37:17,776 - url_helper.py[WARNING]: Calling 'http://169.254.169.254/2009-04-04/meta-data/instance-id' failed [1/120s]: request error [('Connection aborted.', OSError(101, 'Network is unreachable'))]

[  139.302948] cloud-init[1096]: 2015-09-04 08:37:18,779 - url_helper.py[WARNING]: Calling 'http://169.254.169.254/2009-04-04/meta-data/instance-id' failed [2/120s]: request error [('Connection aborted.', OSError(101, 'Network is unreachable'))]

[  140.305640] cloud-init[1096]: 2015-09-04 08:37:19,782 - url_helper.py[WARNING]: Calling 'http://169.254.169.254/2009-04-04/meta-data/instance-id' failed [3/120s]: request error [('Connection aborted.', OSError(101, 'Network is unreachable'))]

[  141.307716] cloud-init[1096]: 2015-09-04 08:37:20,784 - url_helper.py[WARNING]: Calling 'http://169.254.169.254/2009-04-04/meta-data/instance-id' failed [4/120s]: request error [('Connection aborted.', OSError(101, 'Network is unreachable'))]


Full console log is here - [https://gist.github.com/victorhooi/641a18bc4f27b8300087](https://gist.github.com/victorhooi/641a18bc4f27b8300087)

I tried with a daily build just now - same error messages.

Has anybody been able to successfully start a Wily instance on EC2?

Cheers,
Victor

---

### Post by howefield on 2015-09-04
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by dino99 on 2015-09-04
if the 'proposed' archive is activated, then you probably install the broken 1.0.4 network-manager packages; downgrading to 0.9.10 is the solution till we get a fix.

---

