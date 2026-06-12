---
title: "A story, some hints and a question"
date: 2011-05-20
forum: Security
---

### Post by pete_l on 2011-05-20
A few weeks ago I finally got sufficiently annoyed by ssh break-in attempts (none successful) to do something about it.
Initially I wrote a perl script to check who was trying to hack in (see below: watch.pl) which turned up some interesting information about where all the hacks were coming from.

Using that information I added some rules to /etc/hosts.deny (see below: hosts.deny and hosts.deny.sh) which has lowered the number of attacks from 2 or 3 a day to practically zero. At least, a well-over 90% drop in attempts.
That is until yesterday when I noticed the hosts.deny.sh log file had grown large. It appears that even though the IP address this user is from is denied, they *still* tried to break in over 5000 times during the course of the day - once every 6 seconds, repeatedly.
Now, I'm assuming that they were using some particularly brain-dead kiddie-script that was too dumb to know when to given up, but (short of turning off logging) is there anything more I can to to "discourage" this sort of behaviour in the future? I'm not prepared to turn off sshd as I have some genuine use for some incoming connections.

Part1. **watch.pl**  Here's the script that scans syslog for break-in attempts:

```

use File::Tail;
use Time::Local;

$FN="/var/log/auth.log";
$DF="/etc/hosts.deny";

open DF, $DF or die "Can't open $DF";
$nd = 0;
%deny = {};
while (<DF>) {
  chomp;
  next unless (m/^ALL:/);
  s/ALL:(\d+\.\d+\.\d+\.\d+).*/\1/;
  $deny{$_} = 1;
  $nd++;
}
print "Found $nd denied IP addresses\n";
#foreach $d (sort keys %deny) {
#  if($deny{$d} == 1) { print "$d\n"; }
#}
close DF;

$update_deny = 0;
$file=File::Tail->new(name=>$FN, maxinterval=>300, adjustafter=>7);

while (defined($line=$file->read)) {
  my ($sc, $mi, $hr, $dy, $mo, $yr, $wday, $yday, $isdst) = localtime();
  my $mn = qw(Jan Feb Mar Apr May Jun Jul Aug Sep Oct Nov Dec)[$mo];
  $tstr = sprintf "%04d-%3s-%02s %02d:%02d:%02d", $yr+1900,$mn,$dy,$hr,$mi,$sc;


  chomp $line;

# illegal access attempts look like this:
# Dec  2 12:09:10 corv sshd[11016]: Invalid user test from xx.xx.xx.xx

  ($mon,$dat,$tim,$myhost,$type,$message) = split /\s+/,$line,6;

  if($message =~ m/invalid user/) {
# message="Failed password for invalid user devin from  xx.xx.xx.xx port 46301 ssh2
    $from = $message;
    $from =~ s/.* from (\d+\.\d+\.\d+\.\d+) port.*/\1/;
#    chomp $from;
    print "$tstr - Break in attempt from $from (line: $line)\n";
    $update_deny = 1;
  }

  if($message =~ /POSSIBLE BREAK-IN ATTEMPT/) {
# message="Address xx.xx.xx.xx maps to <some host> but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!"
    $from = $message;
    $from =~ s/Address (\d+\.\d+\.\d+\.\d+) maps.*/\1/;
#    chomp $from;
    print "$tstr - Host doesn't map from $from (line: $line)\n";
    $update_deny = 1;
  }
  if($message =~ /Did not receive identification string from/) {
#message="Did not receive identification string from xx.xx.xx.xx"
    $from = $message;
    $from =~ s/.* from //;
#    chomp $from;
    print "$tstr - Did not receive identification string from $from\n";
    $update_deny = 1;
  }

  if($update_deny) {
    if($deny{$from} != 1) {
     print "$tstr - Adding $from to hosts.deny\n";
     open HD, '>>', $DF;
     print HD "ALL:$from # written by watch.pl, $tstr\n";
     close HD;
     $deny{$from} = 1;
    } else {
      print "$tstr - Got another attempt from denied host $from\n";
    }
  $update_deny = 0;
  }
}

```

part 2 my **/etc/hosts.deny** with examples of logging
```

ALL:58. : spawn /root/hosts.deny.sh %a %A %c %d %r %R %p
ALL:59. : spawn /root/hosts.deny.sh %a %A %c %d %r %R %p
ALL:60. : spawn /root/hosts.deny.sh %a %A %c %d %r %R %p
ALL:92. : spawn /root/hosts.deny.sh %a %A %c %d %r %R %p
ALL:61. : spawn /root/hosts.deny.sh %a %A %c %d %r %R %p
ALL:112. : spawn /root/hosts.deny.sh %a %A %c %d %r %R %p
ALL:113. : spawn /root/hosts.deny.sh %a %A %c %d %r %R %p

.... more lines like the above ,,,

```
In all, I have identified 23 x.0.0.0/8 IP ranges that account for almost all ssh break-in attempts. All from China/S.E Asia

Part 3. here's the **hosts.deny.sh** script
```

/bin/echo `/bin/date "+%d-%b-%Y %H:%M:%S"` "From:" $1 "To:" $2 "IP" $3 "Daemon:" $4 ", port" $5"/"$6 ", process" $7  >> /tmp/hosts.deny.log

```

Any improvements that people can think of would be gratefully received. Likewise comments on how I can make it more painful for people to try to break in, to hopefully discourage them.

---

### Post by Lars Noodén on 2011-05-20
> **pete_l said:**
> ... is there anything more I can to to "discourage" this sort of behaviour in the future? ...

You can use iptables and --limit how many times per minute SSH connections are made before the host is blocked.

```

start_ssh()
{
   ip6tables -N SSH;    # create chain
   iptables  -N SSH;    # create chain

   # send all incoming SSH trafficc to SSH chain
   ip6tables -I INPUT -i eth0 -p tcp --destination-port 22 -j SSH;
   iptables  -I INPUT -i eth0 -p tcp --destination-port 22 -j SSH;

   # accept incoming connections, in moderation
   ip6tables -I SSH -i eth0 -p tcp --destination-port 22 \
      -m limit --limit 1/minute --limit-burst 2 -j ACCEPT 
   iptables  -I SSH -i eth0 -p tcp --destination-port 22 \
      -m limit --limit 1/minute --limit-burst 2 -j ACCEPT 
   # allow finite new connections per timelimit
   ip6tables -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --update --seconds 60 --hitcount 4 -j REJECT
   iptables  -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --update --seconds 60 --hitcount 4 -j REJECT

   ip6tables -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --set
   iptables  -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --set
}

```

Of course you'll have to adjust the actual numbers to match the conditions in your working environment.

---

### Post by Lars Noodén on 2011-05-20
> **pete_l said:**
> 
Any improvements that people can think of would be gratefully received.

It will be easier to sort the log files by date if you output the date in [ISO 8601](http://www.iso.org/iso/support/faqs/faqs_widely_used_standards/widely_used_standards_other/date_and_time_format.htm) format:
```

date +"%Y-%m-%dT%H:%M:%S"

```

Also, make sure that your system clocks are synced with an external time server using [NTPd](http://packages.ubuntu.com/natty/ntp) or OpenNTPd.  That will make it possible to compare logs with other sites or to report accurately your own logs to authorities should the need arise.  And, be sure to use UTC for your system clocks instead of local time.  Again, it makes working with others much easier.

---

### Post by JKyleOKC on 2011-05-20
> Now, I'm assuming that they were using some particularly brain-dead kiddie-script that was too dumb to know when to given up, but (short of turning off logging) is there anything more I can to to "discourage" this sort of behaviour in the future?Take a look at "fail2ban" in the Software Center or in Synaptic. It's designed for this specific situation and can take the place of your entire set of scripts.

I run a private FTP server so that customers of my data recovery service can upload potentially huge (sometimes greater than 4 GiB) data sets to me, and am perpetually being probed with breakin attempts. Since I installed fail2ban, the logs are orders of magnitude smaller. When it detects a breakin attempt, it modifies the iptables rules to deny all access from the offending IP, and then 10 minutes later, removes the rule so that the rule list doesn't grow infinitely large. So far most all would-be reakers-in have given up during the 10-minute period. It can be made larger if you prefer, simply by editing a configuration file. 

Here's my log for it as of today: ```
2011-05-16 11:13:55,794 fail2ban.actions: WARNING [proftpd] Ban 201.216.227.113
2011-05-16 11:23:56,504 fail2ban.actions: WARNING [proftpd] Unban 201.216.227.113
2011-05-18 06:00:19,479 fail2ban.actions: WARNING [proftpd] Ban 112.220.98.98
2011-05-18 06:10:20,118 fail2ban.actions: WARNING [proftpd] Unban 112.220.98.98
2011-05-18 11:28:58,748 fail2ban.actions: WARNING [proftpd] Ban 58.251.136.170
2011-05-18 11:38:59,400 fail2ban.actions: WARNING [proftpd] Unban 58.251.136.170
2011-05-20 18:44:53,181 fail2ban.actions: WARNING [proftpd] Ban 193.227.197.12
2011-05-20 18:54:53,825 fail2ban.actions: WARNING [proftpd] Unban 193.227.197.12

```and here's the complete log from the FTP server for today:```
May 20 18:44:50 mehitabel proftpd[23070] mehitabel (napocska.tolna.net[::ffff:193.227.197.12]): FTP session opened.
May 20 18:44:50 mehitabel proftpd[23070] mehitabel (napocska.tolna.net[::ffff:193.227.197.12]): USER Administrator: no such user found from napocska.tolna.net [::ffff:193.227.197.12] to ::ffff:xxx.143.22.33:21
May 20 18:44:50 mehitabel proftpd[23070] mehitabel (napocska.tolna.net[::ffff:193.227.197.12]): USER Administrator: no such user found from napocska.tolna.net [::ffff:193.227.197.12] to ::ffff:xxx.143.22.33:21
May 20 18:44:51 mehitabel proftpd[23070] mehitabel (napocska.tolna.net[::ffff:193.227.197.12]): USER Administrator: no such user found from napocska.tolna.net [::ffff:193.227.197.12] to ::ffff:xxx.143.22.33:21
May 20 18:44:51 mehitabel proftpd[23070] mehitabel (napocska.tolna.net[::ffff:193.227.197.12]): USER Administrator: no such user found from napocska.tolna.net [::ffff:193.227.197.12] to ::ffff:xxx.143.22.33:21
May 20 18:44:51 mehitabel proftpd[23070] mehitabel (napocska.tolna.net[::ffff:193.227.197.12]): USER Administrator: no such user found from napocska.tolna.net [::ffff:193.227.197.12] to ::ffff:xxx.143.22.33:21
May 20 18:44:51 mehitabel proftpd[23070] mehitabel (napocska.tolna.net[::ffff:193.227.197.12]): Maximum login attempts (5) exceeded, connection refused
May 20 18:44:51 mehitabel proftpd[23070] mehitabel (napocska.tolna.net[::ffff:193.227.197.12]): FTP session closed.
May 20 18:44:52 mehitabel proftpd[23071] mehitabel (napocska.tolna.net[::ffff:193.227.197.12]): FTP session opened.
May 20 18:44:52 mehitabel proftpd[23071] mehitabel (napocska.tolna.net[::ffff:193.227.197.12]): USER Administrator: no such user found from napocska.tolna.net [::ffff:193.227.197.12] to ::ffff:xxx.143.22.33:21
May 20 18:44:52 mehitabel proftpd[23071] mehitabel (napocska.tolna.net[::ffff:193.227.197.12]): USER Administrator: no such user found from napocska.tolna.net [::ffff:193.227.197.12] to ::ffff:xxx.143.22.33:21
May 20 18:44:53 mehitabel proftpd[23071] mehitabel (napocska.tolna.net[::ffff:193.227.197.12]): USER Administrator: no such user found from napocska.tolna.net [::ffff:193.227.197.12] to ::ffff:xxx.143.22.33:21
May 20 18:49:52 mehitabel proftpd[23071] mehitabel (napocska.tolna.net[::ffff:193.227.197.12]): Session timed out, disconnected
May 20 18:49:52 mehitabel proftpd[23071] mehitabel (napocska.tolna.net[::ffff:193.227.197.12]): FTP session closed.

```You can see that once fail2ban had made its change to iptables, the server timed out 5 minutes later, and by the time the ban came off, the intruder had gone elsewhere to look for easier prey.

---

### Post by pete_l on 2011-05-24
Thanks guys, some useful looking information there. I'll check out the fail2ban package and give it a try.

---

