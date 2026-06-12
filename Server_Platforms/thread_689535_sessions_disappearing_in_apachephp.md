---
title: "sessions disappearing in apache/php"
date: 2008-02-06
forum: Server Platforms
---

### Post by tocleora on 2008-02-06
I don't know if I should put this under programming or server related so I'll start here.

I'm having a serious problem with a new server.  I use session variables as a reference to store cart entries in a database.  so I take phpsessid that becomes the unique customer number and I store all the cart items in the database using that number.  So I've been having problems for about a week that I can't figure out what's wrong, so I build it to where I write the post values, request values and session values on every page the customer hits to a log file.  What I'm finding is the session variables just disappear.  So at 9:45:28 he was on cart.html and had session variables set (including phpsessid) then at 9:45:38 he went to checkout.html and no longer had session variables, not even phpsessid.  I've looked through the code and can't find anywhere where I've reset the session, plus this was moved from another server as-is from which it worked on the other server.  I compared the php.ini files from both servers thinking maybe the session timeout was just too short but they are exactly the same.  Any ideas?

---

### Post by DrMega on 2008-02-06
I've seen this happen. If I remember right you have to issue ob_start() at the top of each page that uses sessions otherwise it spontaneously flakes.

Sorry I can't be more certian, it is a while since I last worked with PHP.

---

### Post by tocleora on 2008-02-06
Well that's pretty dang good saying I didn't even tell you I wan't using that command. :)  I'll try it out, thanks!

---

### Post by DrMega on 2008-02-07
> **tocleora said:**
> Well that's pretty dang good saying I didn't even tell you I wan't using that command. :)  I'll try it out, thanks!

Sorry I told you a pork pie. ob_start has nothing to do with sessions, that's output buffering. The function you want is session_start(), which initialises or resumes a session.

---

### Post by tocleora on 2008-02-10
yeah I have session_start() in all the pages.  I really don't think it's with the code because it's sporadic (it only happens about 5% of the time) and it happens on different pages.  Here are the settings from php.ini:

```

session.save_handler = files
session.save_path = /var/lib/php/session
session.use_cookies = 1
session.name = PHPSESSID
session.auto_start = 0
session.cookie_lifetime = 0
session.cookie_path = /
session.cookie_domain =
session.serialize_handler = php
session.gc_probability = 1
session.gc_divisor     = 1000
session.gc_maxlifetime = 1440
session.bug_compat_42 = 0
session.bug_compat_warn = 1
session.referer_check =
session.entropy_length = 0
session.entropy_file =
session.cache_limiter = nocache
session.cache_expire = 180
session.use_trans_sid = 0

```

I should mention that these are set exactly the same way as the other server we had this site on that didn't have this problem.  But is there anything I can change in that to cause the session to work differently as an alternative solution? I really don't want to have to pass that variable through every page of the site if I don't have to...

---

