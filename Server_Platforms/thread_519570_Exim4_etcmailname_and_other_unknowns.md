---
title: "Exim4 /etc/mailname and other unknowns"
date: 2007-08-07
forum: Server Platforms
---

### Post by dannyboy79 on 2007-08-07
I am not sure what to do regarding my Exim4 configuration on my Gutsy box which is on a lan behind a router where another Feisty box already contains a FQDN for it's IP? Should the hosts file for the feisty box not contain the FQDN for the internal ip 192.168.0.3? I just use workgroup's instead of domains is this an issue?

 I was previously using my isp's smtp to relay my mail as I didn't want to bother  with setting up a imap, spamassassin, squirrelmail, etc etc so when I tried to send an email from my Gutsy box, it was rejected from the isp's smtp server because the domain name of gutsy-tribe3 wasn't recognized. This is the error:
TP error from remote mail server after MAIL FROM:<daniel@gutsy-tribe3> SIZE=1400: host smtp-server.rdc-kc.rr.com [24.94.162.101]: 553 5.1.8 <daniel@gutsy-tribe3>... Domain of sender address daniel@gutsy-tribe3 does not exist
And until I changed /etc/mailname to match the domain of my Feisty box (which is getmyip.com from dyndns) it wouldn't work BUT then it appears as though the email was sent from that box because I use the same username on all my internal machines. OR I can get it to work if I set exim4 to "internet" but then it's a full out email server so now I have to install and configure all the other stuff which leads to more questions.

ALso, how would I set this up if I just wanted to send local emails within the lan if I don't have a domain name for gutsy?

Where is the aliases database kept? I read that after I edit /etc/aliases, I  must run  "newaliases" as root which rebuilds the exim4 alias database. Where is the bi_command configuration set? What file does newaliases update?

Is there some bug that prevents Evolution from using SpamAssassin from working properly?

WHen I am within squirrelmail-configure, and I chose the Serfver Settings, and then the Domain name, what the heck is that super long line of what looks to be giberish? It looks like this
[trim(implode('', file('/etc/'.(file_exists('/etc/mailname')?'mail':'host').'name')))]:

Any help would be appreciated. THanks.

---

