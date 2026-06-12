---
title: "Installing Dapper PHP on Breezy?"
date: 2007-02-22
forum: Repositories &amp; Backports
---

### Post by TimP on 2007-02-22
I have a headless machine running amd64 Breezy server. I'm planning on upgrading it to Dapper once support for Breezy ends, but recently there have been issues with the 64-bit version of PHP, specifically with MediaWiki:

> Note: PHP 5.0 has bugs on 64-bit systems which cause fundamental problems with MediaWiki. If you are running on an x86_64 (AMD64, EMT64) or other affected 64-bit platform, you must run PHP 5.1 or higher.

Since Breezy is locked in with PHP 5.0.5, I can't upgrade MediaWiki past 1.7.1 (now at 1.9.3). Is there any easy way to use the Dapper version of PHP so I can get past PHP 5.0? I'd rather not start compiling my own version of PHP, so if there's no suitable solution I guess I can just hold off until I upgrade in May.

---

