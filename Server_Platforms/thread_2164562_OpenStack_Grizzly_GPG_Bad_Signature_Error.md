---
title: "OpenStack Grizzly GPG Bad Signature Error"
date: 2013-07-31
forum: Server Platforms
---

### Post by vmtrooper on 2013-07-31
Hello Everyone,

As of July 31, 2013, I get a Bad Signature error when I try to deploy Grizzly components.  If I don't use the --forced-yes switch with my apt-get statements, the OpenStack components fail to install.

I did try executing the following commands suggested by others, but this didn't solve my problems:
[COLOR=#444444][FONT=monospace]#apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5EDB1B62EC4926EA[/FONT][/COLOR]
[COLOR=#444444][FONT=monospace]#apt-get update
[/FONT][/COLOR]
I have tried each of the suggested sources for Grizzly components, but neither works.
"deb  [http://ubuntu-cloud.archive.canonical.com/ubuntu](http://ubuntu-cloud.archive.canonical.com/ubuntu) precise-proposed/grizzly main"
"deb  [http://ubuntu-cloud.archive.canonical.com/ubuntu](http://ubuntu-cloud.archive.canonical.com/ubuntu) precise-update/grizzly main"

Yes, I do make sure to install ubuntu-cloud-keyring first.

Has anyone been able to resolve this?  It's a bit annoying since my installation scripts were working fine just yesterday.

Thanks,
Trevor

---

