---
title: "Time synchronisation the better way.."
date: 2010-03-06
forum: The Cafe
---

### Post by xdarkness2 on 2010-03-06
Since i don't know who to contact i will post a suggestion on the forum here.
I would really like to see ntpdate removed and be replaced by ntpd (the daemon version) which is (and the man pages confirm this too) far more accurate in measuring time. Not only that, you can enable the broadcast daemon too. Accuracy to all machines!
 
Thanks, greetings Jan

---

### Post by toupeiro on 2010-03-06
Then do it. What's stopping you?

---

### Post by ratcheer on 2010-03-06
> **toupeiro said:**
> Then do it. What's stopping you?

Yep. That's what I did.

Tim

---

### Post by blueshiftoverwatch on 2010-03-06
Real men use sundials.

---

### Post by ratcheer on 2010-03-07
> **blueshiftoverwatch said:**
> Real men use sundials.

But, sundials only tell local time. Most people want to use standard time. ;)

Tim

---

### Post by katie-xx on 2010-03-07
Are you wanting to do this for a domain ?
Or is it just a single machine?
Its a very interesting problem especially if you are running distributed systems.

Kate

---

### Post by tgalati4 on 2010-03-07
I have a Dapper Drake machine setup as a broadcast time server on my local network with 1 ms accuracy to the average of several reference clocks.  It's easy to do:

sudo apt-get install ntpd

Edit your configuration file (/etc/ntp.conf)

tgalati4@tubuntu2:/etc$ cat ntp.conf
# Updated 20 Oct 08 to add new servers
logfile /home/tgalati4/ntp_stuff/ntp_trace.log
driftfile /var/lib/ntp/ntp.drift
# The next 4 lines adds statistics to /var/log/ntpstats--hopefully
statistics loopstats peerstats #  clockstats
statsdir /var/log/ntpstats/
filegen peerstats file peers type day link enable
filegen loopstats file loops type day link enable
# filegen clockstats file clockstats type day link enable
server tick.cs.unlv.edu
server tick.mtnlion.com
#server tick.jpunix.net
server ntp1.stsn.net
server north-america.pool.ntp.org
server time.apple.com
# Beef up security policy--see hpubuntu's /etc/ntp.conf
restrict default kod notrap nomodify nopeer noquery
restrict 127.0.0.1 nomodify
broadcast 192.168.1.255


--------

Restart the server:

sudo /etc/init.d/ntpd restart

This broadcasts time to your local subnet and all linux machines will automatically pick up the correct network time.  The drift file will correct for temperature and other periodic effects.

---

### Post by toupeiro on 2010-03-08
> **katie-xx said:**
> Are you wanting to do this for a domain ?
Or is it just a single machine?
Its a very interesting problem especially if you are running distributed systems.

Kate

It's not really that difficult in distributed systems.  Most linux admins responsible for many systems have some sort of rsh/ssh key and trusted host setup which from there you can centrally configure and manipulate the NTP daemon or even the ntpdate command.  The key is setting up your domain to do so.  It can be easily done without compromising security.

---

### Post by katie-xx on 2010-03-11
> **toupeiro said:**
> It's not really that difficult in distributed systems.  Most linux admins responsible for many systems have some sort of rsh/ssh key and trusted host setup which from there you can centrally configure and manipulate the NTP daemon or even the ntpdate command.  The key is setting up your domain to do so.  It can be easily done without compromising security.

It can be fascinating actually and quite a challenge.
Remember in critical control systems the time cannot ever be put backwards. Otherwise we might end up with events reported as completed before they have been reported as started. 
Ive actually seen this with a bearing failure on heavy machinery where the fault was reported as a machine trip before the actual event had taken place (or apparently so)
There are ways an means of getting it right.

Kate

---

