---
title: "Relay Access Question"
date: 2008-07-14
forum: Server Platforms
---

### Post by JordanCB on 2008-07-14
Hello,

Recently setup a mail server in Ubuntu 8.04 LTS. I tried testing out my setup by logging into a gmail account and sending a test message to 'user@mydomain.com' (domain, user changed).  I get a returned mail delivery from Gmail stating

'554 5.7.1 <user@mydomain.com>: Relay access denied (state 14).'

I have been scouring google and the ubuntu forums on 'relay access denied' and have come to think that this may be related to some configuration issues in my postconf/main.cf.

If I do not specify the localnetwork in the mynetworks parameter and also 'mydomain.com' in the mydestination parameter, could this be causing the problem of not relaying because it doesn't recognize the domain?  Currently my main.cf has the following for those two parameters:

'mydestination = localhost, localhost.localdomain, mail.mydomain.com'

'mynetworks = 127.0.0.0/8, 192.168.2.0/24'

FYI - I have a static IP and a MX record setup. The MX record is setup correctly and propogated.  Followed [http://www.howtoforge.org/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04](http://www.howtoforge.org/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04)

Other than the relay access denied, my mail server works good, sends and receives locally just fine.  Can send out, but can't send in from gmail account.

Thanks for any advice/input.

-- Jordan

---

### Post by Aranjedeath on 2008-07-25
I have a similar predicament, in fact, so similar it returns the exact same error. for anyone's reference, my two lines are 
mydestination = {serverhostname}, localhost.localdomain, , localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128

I was also wondering if this might contribute to rejection of incoming exterior mail.

Any help would of course be appreciated.

{{Edit}}{ Ok, as of course I fixed it 30 seconds after posting this. Working configuration, taking into account the line change made was, 
mydestination = {server web address}, {server hostname}, localhost.localdomain, , localhost
}

---

### Post by MJN on 2008-07-25
You both need to add your domains to the mydestination directive. As things currently stand your servers do not recognise that they are the final destination for mail to 'mydomain.com' and hence attempt to relay it (failing given you are an untrusted 3rd party).
 
Mathew

---

