---
title: "POSTFIX - create domain blacklist"
date: 2008-08-08
forum: Server Platforms
---

### Post by dannyboy1121 on 2008-08-08
Hi folks,

I'm interested in seeing if I can create a domain blacklist in postfix to automatically reject incoming mail from specific domains.

e.g. all mail from advertisingstuff.com to be rejected - preferably with a user defined code. 

Is there a way of doing this? Any info appreciated.

---

### Post by HermanAB on 2008-08-08
Yes, you can create your own RBL using BIND.  Here is a howto:
[http://www.ladro.com/docs/dns/rblsmtpd.html](http://www.ladro.com/docs/dns/rblsmtpd.html)

---

### Post by dannyboy1121 on 2008-08-08
now **_THAT_** .. is a bleedin brilliant idea. Excellent.

---

### Post by MJN on 2008-08-08
It's even easier than that...

1. Create a file using with your blacklisted addresses/domains with customised responses as follows:

```
# Specific users
user@example.com 550 Sorry user, I've had enough of your spam
# Whole domains
example2.com 550 Messages not accepted from the example2.com domain
# Whole domains with a non-customised response
example3.com REJECT
```(Further options for this file can be found in **man access 5**)

2. Convert this text file into a Postfix-compatible database with **postmap <file> **(output will be file.db)

3. Reference this database with a **check_sender_access hash:<path to file>** (leave off the .db extension) option in your **smtpd_recipient_restrictions** directive.

Mathew

---

### Post by HermanAB on 2008-08-08
A postfix access list is a good idea, but I like the DNS method, since it works with any MTA.

Here is another better howto:
[http://www.kloth.net/internet/dnsbl-howto.php](http://www.kloth.net/internet/dnsbl-howto.php)

---

### Post by dannyboy1121 on 2008-08-14
> **MJN said:**
> It's even easier than that...

1. Create a file using with your blacklisted addresses/domains with customised responses as follows:

```
# Specific users
user@example.com 550 Sorry user, I've had enough of your spam
# Whole domains
example2.com 550 Messages not accepted from the example2.com domain
# Whole domains with a non-customised response
example3.com REJECT
```(Further options for this file can be found in **man access 5**)

2. Convert this text file into a Postfix-compatible database with **postmap <file> **(output will be file.db)

3. Reference this database with a **check_sender_access hash:<path to file>** (leave off the .db extension) option in your **smtpd_recipient_restrictions** directive.

Mathew

Thanks for this also ..... help much appreciated.

---

### Post by lobo_cobra on 2011-07-31
I solved the same issue for my debian lenny today... I made 2 scripts. One to dectect attacks on my mail server and one to update the blacklist. The whole script is started all 10 min by cron. I decided that 30 failed login attempts qualify somebody to  be blacklisted. The script checks /var/log/mail and /var/log/mail.1, means on my server around 1.5 days back.

cat BlacklistMailAttack
#Script to automatically scan the log files:
#!/bin/sh

#set the variables
LogFile='/tmp/ResultInput';
SearchString='failed';
maxTrialAllowed=30;

#prepare start
touch $LogFile #make sure the file exists, even when we were not attacked
cat /var/log/mail.log|tr [:upper:] [:lower:]|grep $SearchString > $LogFile
cat /var/log/mail.log.1|tr [:upper:] [:lower:]|grep $SearchString >> $LogFile
cat $LogFile|tr [:upper:] [:lower:]|grep $SearchString|cut -f7- -d" "|cut -f2 -d"["|cut -f1 -d"]"|tr -d "f:"|sort|uniq -c|sort -n -r|tr -s " " >/tmp/ResultFile
z=$(cat $LogFile|wc -l);#check if we need to proceed

#stop script, if nobody tried to compromized mail
if [ $z -eq 0 ];
 then exit;
fi;

while read i
do
x=$(echo $i|cut -f1 -d" ")
 if (("$x" > "$maxTrialAllowed"));
  then echo "$i";  /home/Scripts/addPostfixBlacklistIp $(echo $i|cut -f2 -d" ");
 fi;
done < /tmp/ResultFile

rm /tmp/ResultFile
rm $LogFile


#Script to update the blacklist
gismoPROD:/home/Scripts# cat addPostfixBlacklistIp
#!/bin/sh

echo -e "$1\tREJECT" >> /etc/postfix/client_access #create line
cat /etc/postfix/client_access |sort|uniq > /etc/postfix/testrs; mv /etc/postfix/testrs /etc/postfix/client_access #avoid duplicate entries
postmap /etc/postfix/client_access #make the hash

===> start this script every 10 min and all attackers get (in this case) blocked after 30 failed log-in attempts. You can of course extend this with some firewall rulz blocking, to prevent that the attacker tries ssh.
===> of course this is only an add on to rdbl and greylists, to update manually my own blacklist, I consider as not feasable on long term. this is why I automated it

---

