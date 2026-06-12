---
title: "modified CSS doesn't take effect on local Apache server"
date: 2008-07-28
forum: Server Platforms
---

### Post by pytheas22 on 2008-07-28
I run an Apache server that I use, among other things, for testing web pages on localhost.  I've noticed that sometimes (but seemingly not all the time, which makes this extra frustrating), when I edit a CSS file, the changes don't take effect when I refresh my web page, even though I'm sure that the correct CSS file is specified in the html header.  It seems that I need to wait some arbitrary amount of time (maybe ten minutes) before I can refresh the page and have it use the latest CSS.  When I make changes to html, however, they're always applied immediately.

I've discovered that I can even rename or delete my CSS file without editing the html to reflect the change, but the web page is still displayed as if the CSS were there.  So I assume that what's going on is the CSS is being cached somewhere, but I'm not sure if it's Firefox or Apache that's doing the caching.  I'm inclined to believe that it's Apache, because the problem still seems to occur even with wined IE 6 and 7.  On the other hand, restarting Apache doesn't force the latest CSS to be used, so I'm not entirely sure that the caching is being done by the server.

If anyone knows what's going on and how I could disable it so that the CSS files that I get on localhost are always the latest version that I have stored on the server, not some earlier cached edition, I would be grateful.  Thanks in advance.

---

### Post by 47_MasoN_47 on 2008-07-28
I've never had a problem with CSS taking longer to reflect changes made.  I have Firefox setup to empty temp files, cookies, etc. upon closing it.  You could try emptying your temp files before testing it and see if that makes a difference.

---

### Post by pytheas22 on 2008-07-29
Thanks for your response.

I've discovered that pressing control-R in Firefox will force the latest CSS to be used, even though F5 or the refresh button don't.  So I guess it was Firefox' fault.  I don't know why it was behaving like that, but at least I've figured out how to work around it.

---

