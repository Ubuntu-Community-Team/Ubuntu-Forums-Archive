---
title: "Postfix Server Spam Problems"
date: 2017-04-16
forum: Server Platforms
---

### Post by secoonder on 2017-04-16
Hello
i am using postfix Server(Spamasassin+Dovecot+Roundcube) on ubuntu 14.04 LTS.
My server take almost 100 Spam mails in one day.
When i checked logs ;
```
r-----:~# more /var/log/mail.log| grep UGFzc3dvcmQ6
Apr 15 20:13:38 mail postfix/smtpd[24658]: warning: unknown[91.149.157.60]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 15 20:54:38 mail postfix/smtpd[26328]: warning: unknown[112.122.101.35]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 15 20:54:44 mail postfix/smtpd[26330]: warning: unknown[112.122.101.35]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 15 21:57:41 mail postfix/smtpd[28617]: warning: unknown[49.70.165.33]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 15 21:57:49 mail postfix/smtpd[28617]: warning: unknown[49.70.165.33]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 15 21:58:02 mail postfix/smtpd[28617]: warning: unknown[49.70.165.33]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 15 22:07:47 mail postfix/smtpd[29330]: warning: unknown[58.64.190.37]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 15 22:26:01 mail postfix/smtpd[3193]: warning: unknown[36.33.92.11]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 15 22:26:06 mail postfix/smtpd[3038]: warning: unknown[36.33.92.11]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 00:31:25 mail postfix/smtpd[9770]: warning: unknown[211.103.155.236]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 00:31:47 mail postfix/smtpd[9770]: warning: unknown[211.103.155.236]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 00:31:57 mail postfix/smtpd[9794]: warning: unknown[211.103.155.236]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 00:32:15 mail postfix/smtpd[9758]: warning: unknown[211.103.155.236]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 00:33:09 mail postfix/smtpd[9770]: warning: unknown[211.103.155.236]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 00:33:32 mail postfix/smtpd[9770]: warning: unknown[211.103.155.236]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 00:33:40 mail postfix/smtpd[9794]: warning: unknown[211.103.155.236]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 00:33:48 mail postfix/smtpd[9758]: warning: unknown[211.103.155.236]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 01:18:55 mail postfix/smtpd[11588]: warning: unknown[222.191.169.26]: SASL login authentication failed: UGFzc3dvcmQ6
Apr 16 01:19:04 mail postfix/smtpd[11588]: warning: unknown[222.191.169.26]: SASL login authentication failed: UGFzc3dvcmQ6
Apr 16 01:19:17 mail postfix/smtpd[11588]: warning: unknown[222.191.169.26]: SASL login authentication failed: UGFzc3dvcmQ6
Apr 16 01:21:23 mail postfix/smtpd[11689]: warning: unknown[222.191.168.41]: SASL login authentication failed: UGFzc3dvcmQ6
Apr 16 01:21:32 mail postfix/smtpd[11689]: warning: unknown[222.191.168.41]: SASL login authentication failed: UGFzc3dvcmQ6
Apr 16 01:21:45 mail postfix/smtpd[11689]: warning: unknown[222.191.168.41]: SASL login authentication failed: UGFzc3dvcmQ6
Apr 16 02:59:09 mail postfix/smtpd[14809]: warning: unknown[117.68.66.172]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 02:59:17 mail postfix/smtpd[14809]: warning: unknown[117.68.66.172]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 02:59:31 mail postfix/smtpd[14809]: warning: unknown[117.68.66.172]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 02:59:47 mail postfix/smtpd[14809]: warning: unknown[117.68.66.172]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 05:03:17 mail postfix/smtpd[18856]: warning: unknown[108.190.37.112]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 05:03:24 mail postfix/smtpd[18856]: warning: unknown[108.190.37.112]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 05:03:35 mail postfix/smtpd[18856]: warning: unknown[108.190.37.112]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 05:03:52 mail postfix/smtpd[18940]: warning: unknown[108.190.37.112]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 05:24:11 mail postfix/smtpd[19725]: warning: unknown[31.130.94.125]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 05:24:18 mail postfix/smtpd[19725]: warning: unknown[31.130.94.125]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 05:24:28 mail postfix/smtpd[19363]: warning: unknown[31.130.94.125]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 05:24:38 mail postfix/smtpd[19559]: warning: unknown[31.130.94.125]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 05:24:40 mail postfix/smtpd[19726]: warning: unknown[31.130.94.125]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 05:24:42 mail postfix/smtpd[19726]: warning: unknown[31.130.94.125]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 06:02:25 mail postfix/smtpd[20861]: warning: unknown[41.85.161.182]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 06:02:33 mail postfix/smtpd[20861]: warning: unknown[41.85.161.182]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 06:02:45 mail postfix/smtpd[20861]: warning: unknown[41.85.161.182]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 06:12:53 mail postfix/smtpd[21215]: warning: 23-30-84-170-static.hfc.comcastbusiness.net[23.30.84.170]: SASL LOGIN authentication failed: UGFzc3dvcmQ
Apr 16 06:13:02 mail postfix/smtpd[21215]: warning: 23-30-84-170-static.hfc.comcastbusiness.net[23.30.84.170]: SASL LOGIN authentication failed: UGFzc3dvcmQ
Apr 16 06:13:14 mail postfix/smtpd[21215]: warning: 23-30-84-170-static.hfc.comcastbusiness.net[23.30.84.170]: SASL LOGIN authentication failed: UGFzc3dvcmQ
Apr 16 06:13:30 mail postfix/smtpd[21231]: warning: 23-30-84-170-static.hfc.comcastbusiness.net[23.30.84.170]: SASL LOGIN authentication failed: UGFzc3dvcmQ
Apr 16 06:33:20 mail postfix/smtpd[21918]: warning: unknown[114.99.12.181]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 06:33:25 mail postfix/smtpd[21916]: warning: unknown[114.99.12.181]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 06:33:40 mail postfix/smtpd[21919]: warning: unknown[114.99.12.181]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 07:08:01 mail postfix/smtpd[24281]: warning: 50-205-16-198-static.hfc.comcastbusiness.net[50.205.16.198]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 07:08:08 mail postfix/smtpd[24281]: warning: 50-205-16-198-static.hfc.comcastbusiness.net[50.205.16.198]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 07:08:19 mail postfix/smtpd[24391]: warning: 50-205-16-198-static.hfc.comcastbusiness.net[50.205.16.198]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 07:18:32 mail postfix/smtpd[24686]: warning: unknown[119.39.238.225]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 08:00:27 mail postfix/smtpd[26576]: warning: netpop-187-087-083-030.alfenas.mg.gov.br[187.87.83.30]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 08:00:27 mail postfix/smtpd[26571]: warning: unknown[41.79.49.57]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 08:00:27 mail postfix/smtpd[26574]: warning: unknown[41.87.161.138]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 08:00:27 mail postfix/smtpd[26579]: warning: unknown[197.220.16.104]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 08:00:32 mail postfix/smtpd[26578]: warning: unknown[187.94.112.47]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 08:00:33 mail postfix/smtpd[26584]: warning: unknown[177.23.164.115]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 08:00:33 mail postfix/smtpd[26567]: warning: unknown[197.220.16.113]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 08:00:43 mail postfix/smtpd[26590]: warning: unknown[177.91.104.253]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 08:00:43 mail postfix/smtpd[26591]: warning: unknown[186.10.21.67]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Apr 16 08:00:43 mail postfix/smtpd[26594]: warning: 223-77-118-138.interneti58.com.br[138.118.77.223]: SASL LOGIN authentication failed: UGFzc3dvcmQ6




``` 
i think This is a spambot/attacker/hacker.is it true ?
i can not see the  mail server name in most of them.So , i can not block domain name on spamassasin filter.

The ip addresss constantly changing. i am blocking ip form the iptables firewall,but it does not end :)

Can i see the domain name above ip address ?

i think, block domain name spamassasin more useful block ip?
Do you agree with me ?
What do you recommend me ?

---

### Post by wildmanne39 on 2017-04-16
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by lisati on 2017-04-16
You might want to add some DNSBL checks as part of your spam filtering. Something similar to this in your main.cf file is a good start:
```
smtpd_recipient_restrictions =

    reject_invalid_hostname, 
    reject_non_fqdn_sender, 
    reject_non_fqdn_recipient, 
    reject_unknown_sender_domain, 
    reject_unknown_recipient_domain, 
    reject_unauth_pipelining, 
    permit_mynetworks, 
    reject_unauth_destination, 
    reject_rbl_client bl.spamcop.net 
    reject_rbl_client zen.spamhaus.org
    permit

```

---

