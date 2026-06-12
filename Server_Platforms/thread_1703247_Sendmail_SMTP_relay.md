---
title: "Sendmail SMTP relay"
date: 2011-03-09
forum: Server Platforms
---

### Post by megabuffen on 2011-03-09
[FONT=Verdana]Since I need PHP to send e-mails, i am trying to configure the sendmail program to use my ISP's SMTP server as a relay, because outgoing traffic on port 25 is blocked. I found a tutorial about this and I added the line "define(`SMART_HOST', `smtp.bredband.net')" to sendmail.mc, but when i try to run the command "[/FONT]m4 /etc/mail/sendmail.mc > /etc/mail/sendmail.cf" I get this:

```
*** ERROR: FEATURE() should be before MAILER()
*** MAILER(`local') must appear after FEATURE(`always_add_domain')*** ERROR: FEATURE() should be before MAILER()
*** MAILER(`local') must appear after FEATURE(`allmasquerade')*** ERROR: FEATURE() should be before MAILER()
```

The same thing happens when i try to run this command with an unmodified version of sendmail.mc.

What to do?

---

### Post by SeijiSensei on 2011-03-09
Uninstall, theh reinstall, sendmail. 

What you do next depends on whether you want to take a "brute-force" approach or a more elegant one.  The more elegant route would modify sendmail.mc then use m4 to create a new sendmail.cf.  The brute-force approach is to edit (as root) sendmail.cf directly.  Look for the line that reads
```
# "Smart" relay host (may be null)
DS
```

Add the name of the relay host directly after DS with no space like this:

```

DSsmtp.bredband.net

```

That will forward all outbound mail to smtp.bredband.net.

---

### Post by megabuffen on 2011-03-11
I did this, but there still seems to be problems. I tried running sendmail from the command line, and I get this:

```
root@megabuffen:/# sendmail -v -s "test" kalle.elmer@telia.com
test
kalle.elmer@telia.com,test... Connecting to [127.0.0.1] via relay...
kalle.elmer@telia.com,test... Deferred: Connection refused by [127.0.0.1]
root@megabuffen:/#
```

It doesn't make sense to me.

---

### Post by SeijiSensei on 2011-03-11
Are you sure you started/restarted sendmail using 'sudo service sendmail restart'?  What do you see if you run 'telnet localhost 25'?  If you don't see the sendmail banner, it's not running.

What do you see in /var/log/mail.log when you run tests?

---

### Post by megabuffen on 2011-03-11
I tried restarting it again. I got this result:
```
root@megabuffen:/var/log# service sendmail restart
 * Restarting Mail Transport Agent (MTA) sendmail
451 4.0.0 /etc/mail/sendmail.cf: line 106: fileclass: cannot open '/etc/mail/local-host-names': Group writable directory
[ OK ]
root@megabuffen:/var/log#
```Afterwards, "ps -A | grep send" shows nothing and when i try "telnet localhost 25" it just says "telnet: Unable to connect to remote host: Connection refused". It doesn't seem to be running.

These are the permissions for the file "/etc/mail/local-host-names":
```
-rw-r--r--   1 root  smmsp    32 2011-03-08 12:34 local-host-names
```When I try to send a mail, these 2 lines show up in mail.log:
```
Mar 11 15:36:01 megabuffen sendmail[14362]: p2BEZwjs014362: from=kalle, size=5, class=0, nrcpts=2, msgid=<201103111435.p2BEZwjs014362@megabuffen.dyndns.org>, relay=root@localhost
Mar 11 15:36:01 megabuffen sendmail[14362]: p2BEZwjs014362: to=kalle.elmer@telia.com,test, ctladdr=kalle (1000/1000), delay=00:00:03, 
xdelay=00:00:00, mailer=relay, pri=60005, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]
```

---

### Post by SeijiSensei on 2011-03-11
Sendmail is very picky about permissions.  The error you encountered is "Group writable directory".  That means that /etc/mail or, worse, /etc itself has group writable permissions.  If you don't care about these things, you can turn off these security checks with the [DontBlameSendmail]("http://www.sendmail.org/tips/dontBlameSendmail") directive.  The simplest solution, though, it to make sure /etc and /etc/mail have 0755 permissions.

---

### Post by megabuffen on 2011-03-12
Apparently, / had group writeable permissions, although the group was root. I fixed it and it now works from PHP. Thanks a lot!

---

### Post by srsubbulakshmi on 2013-04-02
Hi,

I used by the above command with my smtp server then send mail in terminal. Then I saw the mail log following error,

Apr  2 03:54:01 panzeea sm-mta[3451]: r327rwdH003451: to=<srstest@yahoo.co.in>, ctladdr=<user@net4india.com> (1000/1000), delay=00:00:03, xdelay=00:00:03, mailer=esmtp, pri=30265, relay=mx-apac.mail.gm0.yahoodns.net. [106.10.166.52], dsn=5.6.0, stat=Data format error
Apr  2 03:54:01 panzeea sm-mta[3451]: r327rwdH003451: r327rwdI003451: DSN: Data format error
Apr  2 03:54:01 panzeea sm-mta[3451]: r327rwdI003451: to=<user@net4india.com>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30000, dsn=2.0.0, stat=Sent
Apr  2 03:54:01 panzeea sendmail[3359]: r327dJ09003359: to=srstest@yahoo.co.in, ctladdr=user (1000/1000), delay=00:14:42, xdelay=00:00:03, mailer=relay, pri=60000, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (r327rwdH003451 Message accepted for delivery)
Apr  2 03:54:01 panzeea sendmail[3359]: r327dJ09003359: r327dJ0A003359: DSN: User unknown
Apr  2 03:54:01 panzeea sm-mta[3451]: r327rwdK003451: from=<>, size=1866, class=0, nrcpts=1, msgid=<201304020754.r327dJ0A003359@net4india.com>, proto=ESMTP, daemon=MTA-v4, relay=net4india.com [127.0.0.1]
Apr  2 03:54:02 panzeea sm-mta[3451]: r327rwdK003451: to=<user@net4india.com>, delay=00:00:01, xdelay=00:00:01, mailer=local, pri=31866, dsn=2.0.0, stat=Sent
Apr  2 03:54:02 panzeea sendmail[3359]: r327dJ0A003359: to=user, delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=31024, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (r327rwdK003451 Message accepted for delivery)

Pls help me

---

