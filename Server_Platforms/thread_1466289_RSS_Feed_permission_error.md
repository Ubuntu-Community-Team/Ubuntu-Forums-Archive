---
title: "RSS Feed permission error"
date: 2010-04-30
forum: Server Platforms
---

### Post by auraithx on 2010-04-30
I'm getting the following error from my website in relation to generating a rss feed - 

> Error creating feed file, please check write permissions.

[http://end-of-term.co.uk//index.php?option=com_ninjarsssyndicator&feed_id=1](http://end-of-term.co.uk//index.php?option=com_ninjarsssyndicator&feed_id=1)

This is happening across multiple websites and it just started after I switched hosts so it's definitely a server issue.

I've been in #joomla and according to them it's all configured correctly - but for some reason my server isn't allowing the php script to write to /cache.

I've tried changing the ownership of path-to-website/public_html/cache directory from root to www-data.

Joomla is set up with a FTP login that has ownership over /var/www and I'm not experiencing any other permission errors (file uploads,etc all work fine)

any ideas?

---

