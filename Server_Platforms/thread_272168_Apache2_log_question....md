---
title: "Apache2 log question..."
date: 2006-10-05
forum: Server Platforms
---

### Post by chipyoung on 2006-10-05
I am running a lamp server for the first time.  I routinely check my /var/log/auth.log file and also my /var/log/apache2/access.log file.  lately in my access.log file I am finding an entry that I am not sure of the meaning.  I am worried someone is trying to break in.  The line is...

24.94.53.27 - - [05/Oct/2006:17:46:02 -0400] "GET / HTTP/1.0" 200 5109 "-" "-"
****
I found about 10 instances of this line tonight.  Do I need to worry?

Also, is there a procedure for reporting attempted break-ins from the access.log file.  I have had numerous attempts on the server mostly from the China.  I am using the networking administration program whois to identify these individuals.

One last question.  Are there other log files I should be monitoring on my server?

Thank you very much in advance.

Chip

---

### Post by MJN on 2006-10-06
Looks alright to me, assuming the combined log format:
 
**24.94.53.27** = IP of the connecting client
**-** = Identity of the client (not provided in this case; quite normal)
**-** = User ID of the connecting person (not provided in this case; quite normal)
**[05/Oct/2006:17:46:02 -0400]** = Date/time of the request
**"GET / HTTP/1.0"** = Request sent by client ie. give me the root (and using HTTP v1)
**200** = Status response code (200 = OK)
**5109** = Size of the response (i.e. file, directory listing etc)
**"-"** = Referer i.e. what page referred him to this one (none provided in this case; quite normal)
**"-"** = User agent i.e. what browser they were using (none provided in this; quite normal)
 
It's simply someone connecting to your web server, asking for the root directory (e.g. [www.ubuntuforums.org/]("http://www.ubuntuforums.org/")) - nothing to worry about!
 
Mathew

---

### Post by gg234 on 2006-10-06
i would suggest check the ipaddress origin from where it is coming so that you can realise

---

### Post by chipyoung on 2006-10-06
Thank you Mathew.  I feel much better now.

Thank you GG for your link.  It looks like it will help me.

Chip

---

