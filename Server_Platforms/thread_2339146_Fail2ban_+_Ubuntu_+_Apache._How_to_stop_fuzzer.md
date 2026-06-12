---
title: "Fail2ban + Ubuntu + Apache. How to stop fuzzer?"
date: 2016-10-05
forum: Server Platforms
---

### Post by rhandy2 on 2016-10-05
Hello

I´m beginner on linux and I have some questions.

First i´m using webmin

apache logs are in```
 /var/log/virtualmin/domains_logs

```

I install fail2ban

in jail.conf for example i have log path like this:

> 
[php-url-fopen]


port    = http,https
logpath = %(apache_access_log)s
              %(apache_error_log2)s
      enabled = true
filter = 3proxy




But anyone can explain what is meansthis path means? ```
%(apache_access_log)s
``` it catch all apache logs including inside ? ```
/var/log/virtualmin/*
``` 

After this I make some penatration tests in url fuzzer but i can´t stop attack.

I need some help to config this right.

Sorry for my english.

---

