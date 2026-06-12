---
title: "Hardy Heron 8.04: operation=”inode_permission” requested_mask=”a::”  -  permission de"
date: 2008-10-27
forum: Server Platforms
---

### Post by Sixsh00ter on 2008-10-27
I have two questions. And, I'm logged in as root as I do this stuff.

One:
I'm trying to setup logging on our DNS server. I have the following msg in syslog. Can somebody clue me in as to what I may need to do to fix it? I'm guessing it has something to do with umask.

kernel: audit : type=1503 operation=”inode_permission” requested_mask=”a::” name=”/var/log/query.log” pid=5819 profile=”/usr/sbin/named” namespace=”default”

named: logging channel ‘query’ file ‘/var/log/query.log’: permission denied


I searched the forum and found a thread about Apparmor being the culprit so I set it to complain mode, restarted named, but no joy.

Here's my logging statement straight out of Ubuntu's documentation.

logging {
channel query.log {
file "/var/log/query.log";
// Set the severity to dynamic to see all the debug messages.
severity debug 3;
};

category queries { query.log; };
};

ls -al /var/log/query.log
returns
-rw-r--r-- 1 bind bind 0 date time query.log

I've also tried this statement out of Mark Sobell's "A Practical Guide to Ubuntu Linux" book. No joy.
Should either one of these statements work once I have the "permissions denied" problem resolved?

logging {
channel "query" {
file "/var/log/query.log";
// Set the severity to dynamic to see all the debug messages.
severity debug 3;
};

category queries { "query"; };

};

Two:
Why can't I view the contents of usr.sbin.named?
When I run the cmd "more /etc/usr.sbin.named" it returns "No such file or directory."
ls -al /etc/usr.sbin.named
returns
-rw-r--r-- 1 root root 742 date time usr.sbin.named

---

