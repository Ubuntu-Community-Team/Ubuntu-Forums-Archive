---
title: "snort out or memory after oinkmaster update"
date: 2008-06-16
forum: Security
---

### Post by whoop on 2008-06-16
I got snort up and running on my ubuntu server. I use BASE to view the data which is running on apache2 php5 and mysql. I thought I would update the rules so I installed oinkmaster and got myself an id. I updated the rules (which seemed to go allright). I restarted snort, and then it happened. My cpu goes running full speed and after I short while I get allot of disk i/o's. Then I get an out of memory error for snort (I thought I got it for mysql as well a few times but I can't reproduce that anymore). When viewing BASE I see no entries between boot and crash.

this is my database entry in my snort.conf:
```

output database: log, mysql, user=snort password=XXXXXXXX dbname=snort host=localhost

```
I did not make many modifications to snort.conf, and it was running fine before the oinkmaster update.

I have no idea on what to do, how to diagnose the problem, find the cause and how to fix it.

Help would be very much apreciated.

---

### Post by whoop on 2008-06-16
owk, I got a little further. when I disable backdoor.rules in snort.conf my cpu is fine. So there seems to be a problem in there.

---

### Post by veiho on 2009-01-20
Put following into your snort.conf
```
config detection: search-method ac-bnfa
```
[http://www.snort.org/docs/snort_htmanuals/htmanual_2832/node48.html](http://www.snort.org/docs/snort_htmanuals/htmanual_2832/node48.html)
Check directives.

---

### Post by The Tronyx on 2009-01-20
You can reduce memory usage by removing various rules that are initialized when Snort is run.  For example, do you need to monitor POP2?  If not, then turn it off :) .  You will also want to disable the shellcode preprocessor if you have that running as it will consume quite a bit of overhead.

These are the rules that I use for monitoring approximately 700 linux servers on a per server basis.  It uses the emerging threats rules as well as having a lot of the rulesets trimmed down.  Additionally this uses just a few of the ET rules as they can bring about A LOT of false positives and thus excessive overhead.  To clarify, if you know everything that is on the server, Snort's performance will be much better if it is only listening for what matters.  For example, if you aren't running WordPress, disable the WordPress alerts in web-misc.rules or web-php.rules or anywhere else they exist.  Some people may argue that they want to see any and all hostile traffic but if you are worried about performance as well, it might be wise to understand that someone cannot hack a component of your desktop or server if that component doesn't exist thus monitoring the essentials is paramount.

#include $RULE_PATH/local.rules
# include $RULE_PATH/bad-traffic.rules
include $RULE_PATH/exploit.rules
# include $RULE_PATH/scan.rules
# include $RULE_PATH/finger.rules
include $RULE_PATH/ftp.rules
include $RULE_PATH/telnet.rules
include $RULE_PATH/rpc.rules
include $RULE_PATH/rservices.rules
include $RULE_PATH/dos.rules
include $RULE_PATH/ddos.rules
include $RULE_PATH/dns.rules
# include $RULE_PATH/tftp.rules

include $RULE_PATH/web-cgi.rules
#include $RULE_PATH/web-coldfusion.rules
#include $RULE_PATH/web-iis.rules
#include $RULE_PATH/web-frontpage.rules
include $RULE_PATH/web-misc.rules
#include $RULE_PATH/web-client.rules
include $RULE_PATH/web-php.rules

include $RULE_PATH/sql.rules
#include $RULE_PATH/x11.rules
#include $RULE_PATH/icmp.rules
#include $RULE_PATH/netbios.rules
include $RULE_PATH/misc.rules
include $RULE_PATH/attack-responses.rules
#include $RULE_PATH/oracle.rules
include $RULE_PATH/mysql.rules
# include $RULE_PATH/snmp.rules

include $RULE_PATH/smtp.rules
include $RULE_PATH/imap.rules
#include $RULE_PATH/pop2.rules
include $RULE_PATH/pop3.rules

#include $RULE_PATH/nntp.rules
# include $RULE_PATH/other-ids.rules
# include $RULE_PATH/web-attacks.rules
include $RULE_PATH/backdoor.rules
#include $RULE_PATH/shellcode.rules
# include $RULE_PATH/policy.rules
# include $RULE_PATH/porn.rules
# include $RULE_PATH/info.rules
# include $RULE_PATH/icmp-info.rules
# include $RULE_PATH/virus.rules
# include $RULE_PATH/chat.rules
# include $RULE_PATH/multimedia.rules
# include $RULE_PATH/p2p.rules
include $RULE_PATH/spyware-put.rules
#include $RULE_PATH/specific-threats.rules
# include $RULE_PATH/experimental.rules
# include $RULE_PATH/content-replace.rules
#include $RULE_PATH/voip.rules
#include $RULE_PATH/emerging-exploit.rules
include $RULE_PATH/emerging-malware.rules
include $RULE_PATH/emerging.rules

Lastly if you want to try for better performance, you should think about Barnyard.

> 
We will set Snort to output its alerts and logs to the unified (binary) format, which isn't as processor-intensive as other kinds of output, and then make use of Barnyard to process the resulting output into our required format(s). This tip presumes you already have Snort installed and configured. 

Barnyard basically takes the Snort unified output and processes it into alerts or database output. It is developed and supported by Sourcefire. Before Barnyard is installed and running, we need to make a change to our Snort configuration, usually contained in the /etc/snort/snort.conf configuration file, to output in unified format.


Good luck man.

---

