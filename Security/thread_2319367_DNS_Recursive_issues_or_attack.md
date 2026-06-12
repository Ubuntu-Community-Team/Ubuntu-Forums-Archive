---
title: "DNS Recursive issues or attack"
date: 2016-04-03
forum: Security
---

### Post by mike403 on 2016-04-03
Hi all,

Looking for help on BIND9 running on Ubuntu Server 15.10.

This one of two things here, it's a DNS Recursive issues or DNS Amp attack. I am sure I have recursion part locked down, so it pointing to a DNS Amp attack. I have read over loads of security DNS docs/websites and I can get the issue to settle. I have installed fail2ban and some addition regx expression to catch logging and ask the iptable to close the connections. On top of this i have even installed dnstop to help try local and close down the issues.

I have set my name.conf.option files to use acls and only use trusted ip's, please see below

```

       allow-query { trusted; };
        allow-recursion { trusted; };
        allow-query-cache { trusted; };
        blackhole { blacklist; };
        dnssec-validation auto;
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };

```

Sample of the rapid logging I am seeing

```

3-Apr-2016 18:37:37.478 client 217.106.107.50#59613 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.478 client 217.106.107.50#59613 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.478 client 217.106.107.50#59613 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.479 client 217.106.107.50#59613 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.479 client 217.106.107.50#59613 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.482 client 222.171.249.203#80 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.488 client 69.147.242.90#58811 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.488 client 69.147.242.90#58811 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.488 client 69.147.242.90#58811 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.488 client 69.147.242.90#58811 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.488 client 69.147.242.90#58811 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.488 client 217.106.107.50#59613 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.488 client 217.106.107.50#59613 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.488 client 217.106.107.50#59613 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.489 client 217.106.107.50#59613 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.489 client 217.106.107.50#59613 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.503 client 69.147.242.90#39985 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.504 client 69.147.242.90#39985 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.504 client 69.147.242.90#39985 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.504 client 69.147.242.90#39985 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.504 client 69.147.242.90#39985 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.504 client 69.147.242.90#39985 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.504 client 69.147.242.90#39985 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.505 client 69.147.242.90#39985 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied
03-Apr-2016 18:37:37.505 client 69.147.242.90#39985 (access-board.gov): query (cache) 'access-board.gov/ANY/IN' denied

```

From dnsstop

```

Source          Query Name           Count      %   cum%
--------------- ---------------- --------- ------ ------
104.28.11.187   access-board.gov       905   13.8   13.8
79.180.160.134  access-board.gov       900   13.7   27.5
69.147.242.90   access-board.gov       540    8.2   35.7
204.101.161.159 access-board.gov       445    6.8   42.5
164.132.77.173  access-board.gov       445    6.8   49.2
94.19.137.176   access-board.gov       440    6.7   55.9
80.218.84.114   access-board.gov       440    6.7   62.6
64.129.3.173    access-board.gov       435    6.6   69.2
125.64.16.157   access-board.gov       435    6.6   75.9
89.183.39.55    access-board.gov       430    6.5   82.4
213.136.250.48  access-board.gov       425    6.5   88.9
150.254.122.114 .                      251    3.8   92.7
185.81.59.9     .                      251    3.8   96.5

```

And this is from fail2ban, but its not doing much ( or so it seems)


```

016-04-03 18:47:28,140 fail2ban.filter         [779]: INFO    [named-refused-tcp] Found 79.180.160.134
2016-04-03 18:47:28,141 fail2ban.filter         [779]: INFO    [named-refused-tcp] Found 79.180.160.134
2016-04-03 18:47:28,141 fail2ban.filter         [779]: INFO    [named-refused-tcp] Found 79.180.160.134
2016-04-03 18:47:28,142 fail2ban.filter         [779]: INFO    [named-refused-tcp] Found 79.180.160.134
2016-04-03 18:47:28,142 fail2ban.filter         [779]: INFO    [named-refused-tcp] Found 79.180.160.134
2016-04-03 18:47:28,143 fail2ban.filter         [779]: INFO    [named-refused-tcp] Found 79.180.160.134
2016-04-03 18:47:28,143 fail2ban.filter         [779]: INFO    [named-refused-tcp] Found 79.180.160.134
2016-04-03 18:47:28,144 fail2ban.filter         [779]: INFO    [named-refused-tcp] Found 79.180.160.134
2016-04-03 18:47:28,144 fail2ban.filter         [779]: INFO    [named-refused-tcp] Found 79.180.160.134
2016-04-03 18:47:28,154 fail2ban.actions        [779]: NOTICE  [named-refused-udp] 222.171.249.203 already banned

```

Any help would be great

Thanks
Mike

---

### Post by SeijiSensei on 2016-04-03
Talk to your ISP and see if they can filter these attacks upstream from you.

---

