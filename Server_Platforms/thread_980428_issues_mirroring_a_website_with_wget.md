---
title: "issues mirroring a website with wget"
date: 2008-11-12
forum: Server Platforms
---

### Post by Vadi on 2008-11-12
Hi,

I'm trying to mirror a website with wget but it is failing to work for me - only download the first page and that's it. I've already went through all Internet tutorials I could find regarding this, but nothing works - wget only retrieves the first page and stops.

For example:

> vadi@ubuntu:~/Desktop/test$ **wget --force-html --convert-links --mirror [http://ubuntu.com](http://ubuntu.com)**
--2008-11-12 21:04:12--  [http://ubuntu.com/](http://ubuntu.com/)
Resolving ubuntu.com... 91.189.94.156
Connecting to ubuntu.com|91.189.94.156|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.ubuntu.com/](http://www.ubuntu.com/) [following]
--2008-11-12 21:04:12--  [http://www.ubuntu.com/](http://www.ubuntu.com/)
Resolving [www.ubuntu.com](www.ubuntu.com)... 91.189.94.199
Connecting to [www.ubuntu.com|91.189.94.199|:80](www.ubuntu.com|91.189.94.199|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 0 [text/html]
Last-modified header missing -- time-stamps turned off.
--2008-11-12 21:04:13--  [http://www.ubuntu.com/](http://www.ubuntu.com/)
Reusing existing connection to [www.ubuntu.com:80](www.ubuntu.com:80).
HTTP request sent, awaiting response... 200 OK
Length: 18067 (18K) [text/html]
Saving to: `[www.ubuntu.com/index.html](www.ubuntu.com/index.html)'

100%[===============================================>] 18,067      53.7K/s   in 0.3s    

2008-11-12 21:04:13 (53.7 KB/s) - `[www.ubuntu.com/index.html](www.ubuntu.com/index.html)' saved [18067/18067]

FINISHED --2008-11-12 21:04:13--
Downloaded: 1 files, 18K in 0.3s (53.7 KB/s)
Converting [www.ubuntu.com/index.html](www.ubuntu.com/index.html)... 1-78
Converted 1 files in 0.002 seconds.
vadi@ubuntu:~/Desktop/test$ 


Can anyone help?

---

### Post by oneloveamaru on 2008-11-12
put a www before ubuntu

---

### Post by Vadi on 2008-11-12
Wow, thank you very much, that did work on the example. However when trying it on my site that I need to mirror, adding www does not help :(

> vadi@ubuntu:~/Desktop/test$ **wget --force-html --convert-links --mirror [http://www.vadisystems.com/uppercanada/](http://www.vadisystems.com/uppercanada/)**
--2008-11-12 21:34:37--  [http://www.vadisystems.com/uppercanada/](http://www.vadisystems.com/uppercanada/)
Resolving [www.vadisystems.com](www.vadisystems.com)... 207.162.215.8
Connecting to [www.vadisystems.com|207.162.215.8|:80](www.vadisystems.com|207.162.215.8|:80)... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://vadisystems.com/uppercanada/](http://vadisystems.com/uppercanada/) [following]
--2008-11-12 21:34:37--  [http://vadisystems.com/uppercanada/](http://vadisystems.com/uppercanada/)
Resolving vadisystems.com... 207.162.215.8
Connecting to vadisystems.com|207.162.215.8|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Last-modified header missing -- time-stamps turned off.
--2008-11-12 21:34:38--  [http://vadisystems.com/uppercanada/](http://vadisystems.com/uppercanada/)
Connecting to vadisystems.com|207.162.215.8|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `vadisystems.com/uppercanada/index.html'

    [  <=>                                           ] 12,350      46.8K/s   in 0.3s    

2008-11-12 21:34:38 (46.8 KB/s) - `vadisystems.com/uppercanada/index.html' saved [12350]

FINISHED --2008-11-12 21:34:38--
Downloaded: 1 files, 12K in 0.3s (46.8 KB/s)
Converting vadisystems.com/uppercanada/index.html... 0-1
Converted 1 files in 0.001 seconds.
vadi@ubuntu:~/Desktop/test$ **wget --force-html --convert-links --mirror [www.vadisystems.com/uppercanada/](www.vadisystems.com/uppercanada/)**
--2008-11-12 21:34:52--  [http://www.vadisystems.com/uppercanada/](http://www.vadisystems.com/uppercanada/)
Resolving [www.vadisystems.com](www.vadisystems.com)... 207.162.215.8
Connecting to [www.vadisystems.com|207.162.215.8|:80](www.vadisystems.com|207.162.215.8|:80)... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://vadisystems.com/uppercanada/](http://vadisystems.com/uppercanada/) [following]
--2008-11-12 21:34:53--  [http://vadisystems.com/uppercanada/](http://vadisystems.com/uppercanada/)
Resolving vadisystems.com... 207.162.215.8
Connecting to vadisystems.com|207.162.215.8|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Last-modified header missing -- time-stamps turned off.
--2008-11-12 21:34:53--  [http://vadisystems.com/uppercanada/](http://vadisystems.com/uppercanada/)
Connecting to vadisystems.com|207.162.215.8|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `vadisystems.com/uppercanada/index.html'

    [  <=>                                           ] 12,350      47.6K/s   in 0.3s    

2008-11-12 21:34:54 (47.6 KB/s) - `vadisystems.com/uppercanada/index.html' saved [12350]

FINISHED --2008-11-12 21:34:54--
Downloaded: 1 files, 12K in 0.3s (47.6 KB/s)
Converting vadisystems.com/uppercanada/index.html... 0-1
Converted 1 files in 0 seconds.
vadi@ubuntu:~/Desktop/test$ **wget --force-html --convert-links --mirror vadisystems.com/uppercanada/**
--2008-11-12 21:35:00--  [http://vadisystems.com/uppercanada/](http://vadisystems.com/uppercanada/)
Resolving vadisystems.com... 207.162.215.8
Connecting to vadisystems.com|207.162.215.8|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Last-modified header missing -- time-stamps turned off.
--2008-11-12 21:35:00--  [http://vadisystems.com/uppercanada/](http://vadisystems.com/uppercanada/)
Connecting to vadisystems.com|207.162.215.8|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `vadisystems.com/uppercanada/index.html'

    [  <=>                                           ] 12,350      43.7K/s   in 0.3s    

2008-11-12 21:35:01 (43.7 KB/s) - `vadisystems.com/uppercanada/index.html' saved [12350]

FINISHED --2008-11-12 21:35:01--
Downloaded: 1 files, 12K in 0.3s (43.7 KB/s)
Converting vadisystems.com/uppercanada/index.html... 0-1
Converted 1 files in 0 seconds.
vadi@ubuntu:~/Desktop/test$ 


---

### Post by oneloveamaru on 2008-11-12
wget obviously doesn't like redirects. When you tell it to mirror a site and then give it a /something/ at the end of the URL, it doesn't have anywhere else to go under that.

also, whatever you are running is rewriting [www.vadisystems.com](www.vadisystems.com) to just vadisystems.com, so wget isn't liking that.

wget --force-html --convert-links --mirror [http://vadisystems.com](http://vadisystems.com)   will do it for you

---

### Post by oneloveamaru on 2008-11-12
and the opposite is true for [http://ubuntu.com](http://ubuntu.com), that's being rewritten (301 redirect to make those search engines happy), going to [http://www.ubuntu.com](http://www.ubuntu.com)

---

### Post by Vadi on 2008-11-13
The problem with "wget --force-html --convert-links --mirror http://vadisystems.com" though is that the /uppercanada/ directory isn't linked from the start page anywhere, and I got 3 other sites on there... any way to only mirror the /uppercanada/ part?

(or maybe I should setup a subdomain like uppercanada.vadisystems.com?)

---

### Post by oneloveamaru on 2008-11-13
I'm not sure exactly what wget is doing behind the sceens. Honestly, i wouldn't use wget to mirror my websites anyways, I would rsync with a cron job.

A subdomain sounds like it would work. Or maybe a link to /uppercanada/ on the front page that is not visible? Or that is visible, unless there is a problem with that?

---

### Post by Vadi on 2008-11-13
Well the issue here is that the website needs to be moved to a very, very crappy host that doesn't even offer a single MySQL database. The website was built with the basic assumption that one would exist, since $5/mo plans include it (but this is a $2/mo plan!).

So, I need to completely download the website as static html, and have the links converted to relative too. wget supposedly can do that. If I can get it to work.

---

### Post by oneloveamaru on 2008-11-13
Do they give you SSH access? You can rsync from your old host to your new host. I am available for consulting if need be. :) Who or what is hosting your site now? If you substitute static pages for mysql, you are gonna have a hell of a time editing your web pages when need be. How much traffic do your pages get? I would consider hosting it for you if it won't eat up my bandwidth.

---

### Post by Vadi on 2008-11-13
> **oneloveamaru said:**
> Do they give you SSH access? You can rsync from your old host to your new host. I am available for consulting if need be. :) Who or what is hosting your site now? If you substitute static pages for mysql, you are gonna have a hell of a time editing your web pages when need be. How much traffic do your pages get? I would consider hosting it for you if it won't eat up my bandwidth.

Yes, I have ssh access to both. This is a website for a skating club that I did for them - vadisystems.com is my personal site, it needs to be moved to uppercanadaskating.com where it'll be main. I'll be making the changes on my copy of the site, then reuploading onto theirs.

Don't worry about the hosting, this is a for-profit organization, even though I'm doing this for them as volunteer work. Apparently they're having some 'payment issues' to upgrade to a $5/mo plan (when a single skater for a season is a good $500 fee to the club itself, nevermind more for the coach and equipment. So I have zero pity really).

I'll give the subdomain thing a try.

---

### Post by Vadi on 2008-11-16
I've created *test.vadisystems.com*, however, wget is still being lazy with or without www.

Any ideas?

---

