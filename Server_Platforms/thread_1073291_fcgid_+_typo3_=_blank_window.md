---
title: "fcgid + typo3 = blank window"
date: 2009-02-18
forum: Server Platforms
---

### Post by brack on 2009-02-18
I setting up a server by following [=single&cHash=45a565e1de"]http://typo3.org/development/articles/using-php-with-mod-fcgid/?tx_rlmpofficedocuments_pi1[view]=single&cHash=45a565e1de]("http://typo3.org/development/articles/using-php-with-mod-fcgid/?tx_rlmpofficedocuments_pi1[view) and everything is working fine except typo3 itself. BE of it is working but FE only generates head section of the page - no extension loaded and thus no content shown. there is nothing between body tags. error.log doesnt show any errors as well as there is nothing suspicious in access.log, just empty pages. The typo3 site is not fresh install, it was working fine on the same server with mod-php5. Hoster requested to change mod to fcgid and I wanted to reproduce changes before actually doing it on the server. TSFE array has everything but content related stuff. All debug variables in install tool set to 1 php set to all errors and warnings and I dont know how else to debug this thing.:(

---

### Post by brack on 2009-02-23
anyone?

---

### Post by sappy on 2009-04-30
I had same problem and reason is in path, where is script (index.php) executed.
mod_php will execute index.php in root of website and then follow symlink to typo3_src dictionary, so index.php is executed in root dictionary of website.
mod_fcgid and suphp follow symlink before executing and then execute script (index.php) in context of typo3_src dictionary, so relative files (e.g. templates (fileadmin/templates...) are not accessible.
My solution is use of normal files instead of symlinks. So index.php in root of website is a normal direct file, not a symlink.

---

### Post by brack on 2009-05-04
> **sappy said:**
> I had same problem and reason is in path, where is script (index.php) executed...

I also figured it is some symlinks complications, I tried though to set simple echo in sourche index.php and the other file that source index referring to and those echos were showing up. I believe there are some complications when pathes are pointing back to server docs from source. Well, I just gave up on this issue for now, continue to use php5-mod and it works fine. So far I have only two sites and both of them set up using sub servers in virtualmin so they use the same apache username and group and I dont have any problems with permissions. Good to know that I'm not alone though :P

---

