---
title: "web server problem : can't get sessions to work"
date: 2010-11-10
forum: Server Platforms
---

### Post by dkby on 2010-11-10
Hi,

I made a server using the Ubuntu 10.04LTS, and I had a problem with the first website I installed on it. It's a phpBB3 forum, and the matter was it was impossible to make the auto login function work. I tried a lots of cookie settings using the phpbb interface, but no success. Then I tried installing another website : phpmyadmin, and same problem : sessions don't work properly.

For example : i can log to the website (x.x.x.x/forum or x.x.x.x/phpmyadmin), but if, without even closing my browser or my tab, I go to x.x.x.x/forum or /phpmyadmin again, my session is lost and I have to log again.

It's then I noticed that once logged, there's a session id in the url although php seems to be setup correctly (apache2 & php are on default settings). Each time I go to x.x.x.x/forum or /phpmyadmin again, the session id changes. My browser can use cookies, and when I checked their values, session stored in it was the same as the one in the url.

```

session.use_cookies = 1
session.use_only_cookies = 1
session.use_trans_sid = 0

```I tried to swap their value, reload, swap their value to get back to normal, reload, no effect. So I'm stuck now, I don't know what to do next.

Configuration :
Server : 10.04 LTS / apache.conf : [http://82.66.3.242/apache2.conf]("http://82.66.3.242/apache.conf") / php settings : [http://82.66.3.242]("http://82.66.3.242/")

Any help would be very appreciated :)
thanks in advance

---

### Post by dkby on 2010-11-10
None had the same problem ?:(

---

### Post by wongo888 on 2010-11-11
You might be better off posting this question to the PHPBB support forum. If the app is not trying to set cookies, then the cookies won't be set. My guess is it is your browser not accepting cookies or else the app is not setting them (maybe due to the numbered IP you are using - not a hostname). LiveHTTPHeaders for Firefox would probably help debug a cookie setting issue.

PS. Why is your upload_max_filesize set to 2OM? Rather than 20M.

---

