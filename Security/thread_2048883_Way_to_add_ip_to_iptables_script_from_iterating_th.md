---
title: "Way to add ip to iptables script from iterating through log file"
date: 2012-08-27
forum: Security
---

### Post by jwright8 on 2012-08-27
I have a problem where in my auth.log file, I sometimes see this:

```

Aug 26 09:41:52 Aequitas saslauthd[2208]: pam_mysql - SELECT returned no result.
Aug 26 09:41:52 Aequitas saslauthd[2208]: pam_mysql - SELECT returned no result.
Aug 26 09:41:52 Aequitas saslauthd[2208]: DEBUG: auth_pam: pam_authenticate failed: User not known to the underlying authentication module
Aug 26 09:41:52 Aequitas saslauthd[2208]: do_auth         : auth failure: [user=liam] [service=smtp] [realm=] [mech=pam] [reason=PAM auth error]

```It's always a random username that has no correlation to anything (it isn't ever an actual username on my box), leading me to believe it's some kind of script that trolls around hoping to get lucky.

When I check mail.log, I find this:

```

Aug 26 09:41:52 Aequitas postfix/smtpd[3227]: warning: SASL authentication failure: Password verification failed
Aug 26 09:41:52 Aequitas postfix/smtpd[3227]: warning: unknown[69.6.152.7]: SASL PLAIN authentication failed: authentication failure
Aug 26 09:41:54 Aequitas postfix/smtpd[3227]: lost connection after AUTH from unknown[69.6.152.7]
Aug 26 09:41:54 Aequitas postfix/smtpd[3227]: disconnect from unknown[69.6.152.7]

```From what I understand, this indicates an attempt at an SQL attack on my e-mail server.  I typically cross-reference the two, trace the IP (lo and behold it's foreign, usually asian countries or Russia), and add it to iptables with the following:

```

iptables -A INPUT -s 69.6.152.7 -j DROP # SQL, Added 8/27/12

```I typically leave this IP in my script forevermore.  I go and check syslog, mysql.log, mail.err, and mysql.err for weird entries.  I do not have fail2ban installed, however I do have denyhosts installed (which only protects SSH I think).

The question I have here  is twofold:

1) Are the assumptions above correct?  Should I be doing anything more?

2) Is it possible to have a script that looks in mail.log every 30 minutes or so for the line of:

```

Aug 26 09:41:52 Aequitas postfix/smtpd[3227]: warning:  unknown[69.6.152.7]: SASL PLAIN authentication failed: authentication  failure

```and automatically adds it as an input drop to my iptables script?  The majority of these problems tend to happen from 1 am - 6 am, when I'm asleep.

Thanks in advance!

---

### Post by Lars Noodén on 2012-08-27
Preliminarily, I'm thinking that some combination of tail and awk should do it.

Can you add some further examples from mail.log?  It would help to know if 'warning:  unknown[69.6.152.7]:' comes in any other variants.

---

### Post by jwright8 on 2012-08-27
This is the block in full from mail.log
```

Aug 26 09:41:51 Aequitas postfix/smtpd[3227]: connect from unknown[69.6.152.7]
Aug 26 09:41:52 Aequitas postfix/smtpd[3227]: warning: SASL authentication failure: Password verification failed
Aug 26 09:41:52 Aequitas postfix/smtpd[3227]: warning: unknown[69.6.152.7]: SASL PLAIN authentication failed: authentication failure
Aug 26 09:41:54 Aequitas postfix/smtpd[3227]: lost connection after AUTH from unknown[69.6.152.7]
Aug 26 09:41:54 Aequitas postfix/smtpd[3227]: disconnect from unknown[69.6.152.7]
Aug 26 09:45:14 Aequitas postfix/anvil[3230]: statistics: max connection rate 1/60s for (smtp:69.6.152.7) at Aug 26 09:41:51
Aug 26 09:45:14 Aequitas postfix/anvil[3230]: statistics: max connection count 1 for (smtp:69.6.152.7) at Aug 26 09:41:51
Aug 26 09:45:14 Aequitas postfix/anvil[3230]: statistics: max cache size 1 at Aug 26 09:41:51

```This is another full block:

```

Aug 27 10:08:53 Aequitas postfix/smtpd[24032]: connect from unknown[175.143.53.113]
Aug 27 10:08:54 Aequitas postfix/smtpd[24032]: warning: SASL authentication failure: Password verification failed
Aug 27 10:08:54 Aequitas postfix/smtpd[24032]: warning: unknown[175.143.53.113]: SASL PLAIN authentication failed: authentication failure
Aug 27 10:08:54 Aequitas postfix/smtpd[24032]: lost connection after AUTH from unknown[175.143.53.113]
Aug 27 10:08:54 Aequitas postfix/smtpd[24032]: disconnect from unknown[175.143.53.113]
Aug 27 10:12:14 Aequitas postfix/anvil[24035]: statistics: max connection rate 1/60s for (smtp:175.143.53.113) at Aug 27 10:08:53
Aug 27 10:12:14 Aequitas postfix/anvil[24035]: statistics: max connection count 1 for (smtp:175.143.53.113) at Aug 27 10:08:53
Aug 27 10:12:14 Aequitas postfix/anvil[24035]: statistics: max cache size 1 at Aug 27 10:08:53

```It always looks like this, so it seems it doesn't vary.


It does seem that warning could be something else, like this:

```

Aug 26 16:38:32 Aequitas postfix/smtpd[5738]: warning: 190.0.243.91: hostname 190024391.ip3.static.mediacommerce.com.co verification failed: Name or service not known
Aug 26 16:38:32 Aequitas postfix/smtpd[5738]: connect from unknown[190.0.243.91]
Aug 26 16:38:33 Aequitas postfix/smtpd[5738]: NOQUEUE: reject: RCPT from unknown[190.0.243.91]: 554 5.7.1 <invalidemail@validdomain.com>: Relay access denied; from=<bidepiw@apmedia.ru> to=<invalidemail@validdomain.com> proto=SMTP helo=<apmedia.ru>
Aug 26 16:38:34 Aequitas postfix/smtpd[5738]: disconnect from unknown[190.0.243.91]
Aug 26 16:41:54 Aequitas postfix/anvil[5740]: statistics: max connection rate 1/60s for (smtp:190.0.243.91) at Aug 26 16:38:32
Aug 26 16:41:54 Aequitas postfix/anvil[5740]: statistics: max connection count 1 for (smtp:190.0.243.91) at Aug 26 16:38:32
Aug 26 16:41:54 Aequitas postfix/anvil[5740]: statistics: max cache size 1 at Aug 26 16:38:32

```It wouldn't be a problem, however, for this to be added to the script as well if it were that much more difficult.  So it seems as if the only two occurances are a) SQL attacks (presumably) and b) invalid e-mail addresses that don't exist on a certain domain.


EDIT:

I just searched through around two weeks of logs, and it seems like the two scenarios above are the only two types of occurrences for warning in mail.log.

---

### Post by Lars Noodén on 2012-08-27
Here's an attempt.  Double check to be sure.  I think I've set it so that it can't pass any empty or bad values to iptables.

```

for ip in $( egrep "authentication failure$" mail.log | \
 perl -e 'while ( <> ) { ( $ipadd ) = /unknown\[(\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})/;print "$ipadd\n" if ( $ipadd ) }'); 
 do iptables -A INPUT -s $ip -j REJECT;
done

```

This kind of thing is actually rather easy on BSD's [PF](http://home.nuug.no/~peter/pf/en/tables.html) using tables.  The question that remains with the iptables solution above is how to cull or expire entries.  

Really the grep could have been merged into the perl part, but I wanted to keep that as simple and small as possible.

---

### Post by jwright8 on 2012-08-27
Well, for my purposes, expiring entries won't be necessary.  For one, I typically don't remove them.  I don't have a high-traffic website or anything, so it isn't a problem for me (at least so far).  In the event I do, however, I still monitor my logs and check my stuff daily.  The script is more for when I'm sleeping, or if I get busy one day and don't have a chance to check my logs for a full 24+ hours or so.  

I'll try this momentarily... though I don't know if I'll be able to see it unless I get someone trying it.  

The question I have is that I currently have my iptables.sh script in my /root/ directory.  Will this be a problem?  I had the idea to sort of append the iptables rules to the end of that file, but it seems like if I were to run my iptables script after implementing this it would clear all the IPs that your script blocked, since my script's first few lines say:

```

## Flush the filter table
#
iptables -F

## Flush the NAT table, just in case
#
iptables -t nat -F


```

Thank you very much for your help so far :).

---

### Post by Lars Noodén on 2012-08-27
Yes, iptables -F would clear everything not just the items added by the script.  

One place to consider keeping the script, instead of /root, would be in [/usr/local/sbin](http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html).  It would be available to others there, too, if needed.

---

### Post by jwright8 on 2012-08-27
Okay, that makes sense.  Would there be a way to append those IPs that your script finds to my existing iptables.sh file, then execute it?  I would go back and add comments for the IPs myself after the fact, but my main concern is disallowing them before they can do any damage.

---

### Post by Lars Noodén on 2012-08-27
I think you should be able to add those lines to your iptables.sh script directly as they are.  But then the mail log would only get checked when the iptables.sh script is run.  Hopefully one of the shell experts will see this thread since there is certainly an easy solution somewhere.

---

### Post by jwright8 on 2012-08-27
Thanks for all your help so far, if nothing else I can temporarily use the script (and just not restart my box or execute my iptables.sh script again), check the iptables rules and add them to the iptables.sh script, etc. until I can poke around and figure out how to approach it as a more permanent solution.  Thanks again!

---

### Post by jwright8 on 2012-08-27
Sorry for the double post, but a thought had just occurred to me.  Would it be possible to use that script to append to a text file, say mail_log_bans.txt? Just the IPs. I could probably take it from there using my iptables.sh script and crontab.

So for instance, the mail_log_bans.txt file would look like:

> 
69.6.152.7
175.143.53.113


---

### Post by Lars Noodén on 2012-08-27
mail_log_bans.txt could be built with a simple [redirect](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html)  Then your script could read it.  That's kind of an extra step but it works.

---

### Post by jwright8 on 2012-08-27
So it would change
```

for ip in $( egrep "authentication failure$" mail.log | \  
perl -e 'while ( <> ) { ( $ipadd ) = /unknown\[(\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})/;print "$ipadd\n" if ( $ipadd ) }');   
do iptables -A INPUT -s $ip -j REJECT; 
done

```To something like:
```

for ip in $( egrep "authentication failure$" mail.log | \ 
 perl -e 'while ( <> ) { ( $ipadd ) = /unknown\[(\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})/;print "$ipadd\n" if ( $ipadd ) }');   
do ls -l > /usr/local/sbin/mail_log_bans.txt 
done

```Correct?

---

### Post by Lars Noodén on 2012-08-27
You can put the redirect at the end:

```

for ip in $( egrep "authentication failure$" mail.log | \
  perl -e 'while ( <> ) { ( $ipadd ) = /unknown\[(\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,
3})/;print "$ipadd\n" if ( $ipadd ) }');
  do echo $ip;
done > /root/mail_log_bans.txt

```

Or in the middle

```

echo > /root/mail_log_bans.txt
for ip in $( egrep "authentication failure$" mail.log | \
  perl -e 'while ( <> ) { ( $ipadd ) = /unknown\[(\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,
3})/;print "$ipadd\n" if ( $ipadd ) }');
  do echo $ip >> /root/mail_log_bans.txt;
done 

```

---

### Post by jwright8 on 2012-08-27
Wonderful then.  That looks like exactly what I need; I'll use cron and my iptables.sh script to handle the rest of it.  Thank you very much!

---

### Post by jwright8 on 2012-08-27
EDIT: Nevermind, I was doing something wrong.  Thank you! :D

---

### Post by Lars Noodén on 2012-08-28
You're welcome.  I'm glad it worked.

I should add that the perl script uses the [special variable $_](http://perldoc.perl.org/perlvar.html#%24_)  
Perl assumes $_ for input and pattern matching if you don't specify another variable.

---

