---
title: "cron tab help ?"
date: 2008-11-20
forum: Server Platforms
---

### Post by rompstar420 on 2008-11-20
currently my command my line in crontab is like this:

01 01 * * * perl /usr/local/awstats/wwwroot/cgi-bin/awstats.pl -update -config=www.mydomain.com

this is to update 

I would like to update it to schedule every 5 minutes? how do I do that?  Just wanted to confirm I am doing this right, crontab newbie.

Thanks!

---

### Post by jrib on 2008-11-21
From 'man 5 crontab':
> Step values can be used in conjunction with ranges.  Following a  range with  &#8216;&#8216;/<number>&#8217;&#8217;  specifies  skips of the number&#8217;s value through the range.  For example, &#8216;&#8216;0-23/2&#8217;&#8217; can be used in the hours field to specify command execution every other hour (the alternative in the V7 stan&#8208; dard is &#8216;&#8216;0,2,4,6,8,10,12,14,16,18,20,22&#8217;&#8217;).  Steps are also  permitted after  an asterisk, so if you want to say &#8216;&#8216;every two hours&#8217;&#8217;, just use &#8216;&#8216;*/2&#8217;&#8217;.

So */5 in the minute field seems to be what you want.

---

### Post by rompstar420 on 2008-11-21
so this is right ?

05 * * * * perl /usr/local/awstats/wwwroot/cgi-bin/awstats.pl -update -config=www.mydomain.com

how about the rest of the command, is that ok ?

---

### Post by jrib on 2008-11-21
nope. */5, not 05

---

### Post by linux_tech on 2008-11-21
0-55/5 should work also

---

### Post by hictio on 2008-11-21
This is the whole thing:

```

*/5 * * * * perl /usr/local/awstats/wwwroot/cgi-bin/awstats.pl -update -config=www.mydomain.com

```

---

