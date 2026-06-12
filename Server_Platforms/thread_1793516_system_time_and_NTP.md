---
title: "system time and NTP"
date: 2011-06-29
forum: Server Platforms
---

### Post by Cyked on 2011-06-29
Not sure when this started exactly.  I just had comcast installed last Thursday, had AT&T before that with about a week and half with no internet in between.  Other than that, I haven't changed anything.

I noticed on Monday that my system time is off, and it keeps happening.  I've never had an issue with this before.  I'd run sudo ntpdate pool.ntp.org to update, would be fine, and then it would end up being about 8 minutes fast again the next day (CRON was firing off early and I was getting system emails early).  System has been up for about a week, so its not happening when rebooting.

I just setup cron to do an ntp update every hour.  I let it run and here is the output.

in syslog

```
Jun 29 12:10:03 tux ntpdate[14790]: step time server 128.10.254.7 offset -4.521275 sec
Jun 29 12:10:03 tux ntpd[14818]: ntpd 4.2.4p8@1.1612-o Tue Apr 19 07:08:29 UTC 2011 (1)
Jun 29 12:10:03 tux ntpd[14819]: precision = 1.000 usec
Jun 29 12:10:03 tux ntpd[14819]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Jun 29 12:10:03 tux ntpd[14819]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jun 29 12:10:03 tux ntpd[14819]: Listening on interface #1 wildcard, ::#123 Disabled
Jun 29 12:10:03 tux ntpd[14819]: Listening on interface #2 lo, 127.0.0.1#123 Enabled
Jun 29 12:10:03 tux ntpd[14819]: Listening on interface #3 eth1, 192.168.2.102#123 Enabled
Jun 29 12:10:03 tux ntpd[14819]: kernel time sync status 2040
Jun 29 12:10:03 tux ntpd[14819]: frequency initialized -10.360 PPM from /var/lib/ntp/ntp.drift

```


One thing I guess, any thoughts on why my system time was getting off track in the first place.  And two, any issue with how I setup cron and the log entries from syslog?  I don't understand why this would have just started recently.

---

### Post by Bachstelze on 2011-06-29
cron is not the way to keep your time update. Just let ntpd run, it will keep your clock accurate (that's what it's for). That your clock would drift by 8minutes in a single day is not common but not rare either. Most consumer-grade computers are notoriously very bad at keeping time (hence why ntpd exists).

---

### Post by Cyked on 2011-06-29
> **Bachstelze said:**
> cron is not the way to keep your time update. Just let ntpd run, it will keep your clock accurate (that's what it's for). That your clock would drift by 8minutes in a single day is not common but not rare either. Most consumer-grade computers are notoriously very bad at keeping time (hence why ntpd exists).

Thanks.  How can I check when ntpd runs?

---

### Post by Bachstelze on 2011-06-29
ps aux | grep ntp

You should see ntpd there.

---

### Post by arrrghhh on 2011-06-29
> **Cyked said:**
> Thanks.  How can I check when ntpd runs?

While Bachstelze's answer was accurate, I have a feeling you want to know how frequently ntpd updates the system clock.

The answer isn't exactly straightforward, ntpd tracks drift using a file (on Ubuntu the default is /var/lib/ntp/ntp.drift) and automatically adjusts how frequently it updates according to how bad the time drift on your server is.

See [http://tldp.org/LDP/sag/html/basic-ntp-config.html](http://tldp.org/LDP/sag/html/basic-ntp-config.html) for more info.

---

### Post by SeijiSensei on 2011-06-29
You might also want to run the command "sudo hwclock --systohc" periodically to update the onboard hardware clock with the correct time from ntpd.

Usually I run this from cron once a day.

---

### Post by Cyked on 2011-06-30
I had the ubuntu ntp entry in the config and removed it for now and just have the pool.ntp.org entries.  I'll see what the time is like tomorrow.  It's currently about 7-8 min fast from any other system I use (win 7 machine, phone, work computer).

---

### Post by tgalati4 on 2011-06-30
Sounds like your computer real-time clock has gone wacky. If you want more logging, you need to set up some parameters in your /etc/ntp.conf file.

Here's mine:


tgalati4@tubuntu2:~$ cat /etc/ntp.conf
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

My clock is + or - 1 millisecond from the average of the peers that I query.

Here are some recent statistics:


tgalati4@tubuntu2:/var/log/ntpstats$ tail peers.20110630
55742 78682.221 204.13.164.164 96b4 0.000279949 0.080152475 0.014519756 0.002363221
55742 78690.197 72.18.205.156 94b4 0.000648236 0.056539336 0.014493895 0.000313788
55742 78822.212 17.151.16.20 94b4 -0.002780500 0.067491000 0.014505148 0.002151000
55742 78843.208 72.254.0.254 93b4 -0.031663712 0.062800057 0.014516201 0.000123775
55742 78920.203 131.216.22.24 93b4 -0.009569991 0.055449662 0.030059668 0.000023530
55742 79708.250 204.13.164.164 96b4 0.000391057 0.079674047 0.014732526 0.000111109
55742 79716.226 72.18.205.156 94b4 0.001203326 0.055960845 0.014719477 0.000555090
55742 79845.237 17.151.16.20 94b4 -0.004200000 0.063132000 0.014704645 0.001419500
55742 79868.236 72.254.0.254 93b4 -0.032223325 0.061663869 0.014723202 0.000559613
55742 79944.231 131.216.22.24 93b4 -0.009177929 0.055036139 0.030267614 0.000392062

These aren't my stat graphs, but I'm too lazy to generate them, but they are representative of what NTP can do:

[http://www.sput.nl/ntpstats/sput/](http://www.sput.nl/ntpstats/sput/)

Some folks are really into accurate timekeeping:
[http://www.febo.com/time-freq/index.html](http://www.febo.com/time-freq/index.html)

---

### Post by Cyked on 2011-07-01
Thanks, I'll look into it.  Now my clock is at 15 min off, so its drifter further.

---

### Post by Bachstelze on 2011-07-01
ntpd doesn't work very well when your clock is already off by a large amount when you start it. Stop ntpd, run ntpdate to synchronize your clock, and then start ntpd again.

---

### Post by Cyked on 2011-07-01
> **Bachstelze said:**
> ntpd doesn't work very well when your clock is already off by a large amount when you start it. Stop ntpd, run ntpdate to synchronize your clock, and then start ntpd again.

I'll try it.  Maybe different from what I have done since posting.  But I have updated my time to be correct and its drifting from there.

I was specifying a server (pool.ntp.org) with ntpdate previously.  If I just do ntpdate I get "no servers can be used, exiting".

I've checked every file I can think of and everything I have found looking for info on the error via google, and they all have ntp servers listed.

---

### Post by Bachstelze on 2011-07-01
You can run [font=monospace]ntpq -p[/font] while ntpd is running to show the server it synchronizes with and some info about them (in particular the time difference between that server and you). Maybe your system is having trouble synchronising with servers.

---

### Post by SeijiSensei on 2011-07-02
> **Cyked said:**
> I was specifying a server (pool.ntp.org) with ntpdate previously.  If I just do ntpdate I get "no servers can be used, exiting".

Are you actually using "pool.ntp.org" or one of the numbered servers like "0.pool.ntp.org"?  You should be using the latter. 

Also ntpdate requires a server name (see "man ntpdate").  What happens if you run "ntpdate 0.pool.ntp.org"?

---

### Post by Cyked on 2011-07-05
Here is the ntpq -p output

```
ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 ns3.kashpureff. 72.249.38.88     3 u   23   64  377   45.994  -173734 1497.31
 tds-solutions.n 216.45.57.38     3 u   63   64  377   59.730  -173715 1501.47
 ip-173-201-38-8 204.123.2.72     2 u   23   64  315   63.935  -173735 709272.
ID@tux:~$ date
Tue Jul  5 12:33:39 PDT 2011

```

Note that when I ran this and date just after the actual time was closer to 12:03pm.


ntp.conf file
```
# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift


# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
server 1.pool.ntp.org
server 2.pool.ntp.org
server 0.pool.ntp.org

# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html for
# details.  The web page <http://support.ntp.org/bin/view/Support/AccessRestrictions>
# might also be helpful.
#
# Note that "restrict" applies to both servers and clients, so a configuration
# that might be intended to block requests from certain clients could also end
# up blocking replies from your own upstream servers.

# By default, exchange time with everybody, but don't allow configuration.
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1

# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
#restrict 192.168.123.0 mask 255.255.255.0 notrust


# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255

# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient

```

First try even though its running
```
 sudo ntpdate 0.pool.ntp.org
 5 Jul 12:36:09 ntpdate[7827]: the NTP socket is in use, exiting
```

after stopping
```
sudo ntpdate 0.pool.ntp.org
 5 Jul 12:11:25 ntpdate[8003]: step time server 204.235.61.9 offset -1740.173954 sec
```

---

### Post by Cyked on 2011-07-07
Any other suggestions?

Thanks.

---

### Post by Cyked on 2011-07-08
Well, I've made no other changes, but this morning I rebooted twice. The first time I rebooted system came back up and the time was still off by about 15 minutes.  The second time I validated that the BIOS time is correct, but I did not validate the system time.  This was around 6:30ish.  When I got in to work I logged in to mount a share and checked the time.  System time was 8:00am, and it was 8:00am at the time.  So I'll see what happens.

---

### Post by SeijiSensei on 2011-07-08
Are you running the hwclock command from cron as I suggested above?  If you're still losing fifteen minutes a day or so, maybe you should be running hwclock once per hour.

The onboard clock's battery might be on the verge of death, too.

---

### Post by Cyked on 2011-07-13
No.  And apparently the two reboots "fixed" the issue.

---

### Post by Cyked on 2011-12-02
So this is still messed up.  Any other thoughts?

```
sudo hwclock;date
Fri 02 Dec 2011 08:51:04 AM PST  -0.680977 seconds
Fri Dec  2 08:54:24 PST 2011
```

Yesterday I had removed the ntp.pool servers from my conf list and left 
server time-a.nist.gov iburst

All day yesterday, I could see the clock creep away from the HW clock by maybe 5 seconds and most, then it seemed like time was syncing and would correct the time.  This morning I check it and I get the above.  Yesterday, my linux time was very close to my windows box.  Now its ahead by ~5 minutes.

Any other thoughts?  It doesn't look like my drift file is being updated.  Yesterday I backed up the file and changed the value in it to 0.000 just to see what would happen

Other output that might be helpful.  

```
ntpdc -c loop
offset:               0.000000 s
frequency:            0.000 ppm
poll adjust:          4
watchdog timer:       70855 s

```

```
ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 time-a.nist.gov .ACTS.           1 u   47   64  377   91.208  -365927 1490.09
```

I can post the peerstats and loopstats files if needed.

---

### Post by kjohri on 2011-12-03
I think it is better to have multiple servers in ntp.conf, that is,

server 0.pool.ntp.org iburst
server 1.pool.ntp.org iburst
server 2.pool.ntp.org iburst
server 3.pool.ntp.org iburst

You can see the file modification time of the drift file using the ls command to find out whether the drift file is being updated.

It could be authentication issue.Server or client expect authentication, which is not being provided and hence the time update is not happening.

Try the link,

[http://www.softprayog.in/tutorials/synchronize-your-computers-clock-using-the-ntp]("http://www.softprayog.in/tutorials/synchronize-your-computers-clock-using-the-ntp")

---

### Post by Cyked on 2011-12-20
So right or wrong, I fixed the issue.  I "ripped" out NTP that was there, sort of, and downloaded and installed from source.  Its been running fine now for a good 4 days with no drift.  I'm sure I screwed something up, instead of starting NTP from init.d I just start NTPD with sudo ntpd.  If I reboot the daemon doesn't start, so I need to set it up so when networking comes up it starts the daemon.

Works for me I suppose.

---

