---
title: "Battling Spam"
date: 2006-12-05
forum: Server Platforms
---

### Post by NewbieUser on 2006-12-05
I am running a Ubuntu mail server using Postfix, Amavis, Clam, SA and Maia Mailguard.  I would like to optimize our ability to reject spam prior to delivery to SA. I have added a greylisting server as as a SPF policy server.  I am contemplating policyd-weight or adding additional rbls.  I presently use zen.spamhaus.org.  Does anyone have any pros or cons on policyd-weight versus rbl lists, or can recommend additional rbls?

Thanks

---

### Post by MJN on 2006-12-05
The RBLs I use are zen.spamhaus.org, bl.spamcop.net and relays.ordb.org and have a very low (zero to my knowledge) false positive rate. What greylisting server are you using? Postgrey?

Mathew

---

### Post by speedman on 2006-12-05
If you're not using it - postgrey is super effective for grey listing.  apt-get install postgrey and mod /etc/postfix/main.cf like this:

=====

# -=CAH=-
# smtp server restrictions
smtpd_recipient_restrictions =
        permit_mynetworks,
        permit_sasl_authenticated,
        reject_unauth_destination,
        check_policy_service inet:127.0.0.1:60000,
# -=CAH=- next 8 variables problematic for some environments
        reject_invalid_hostname,
        reject_non_fqdn_hostname,
        reject_non_fqdn_sender,
        reject_non_fqdn_recipient,
        reject_unknown_sender_domain,
        reject_unknown_recipient_domain,
        reject_unauth_pipelining,
# -=CAH=- following line zaps mail with no ptr record
#        reject_unknown_client,
        reject_rbl_client zombie.dnsbl.sorbs.net,
        reject_rbl_client relays.ordb.org,
        reject_rbl_client opm.blitzed.org,
        reject_rbl_client list.dsbl.org,
        reject_rbl_client zen.spamhaus.org,
        reject_rbl_client blackholes.mail-abuse.org,
        reject_rbl_client cbl.abuseat.org,
        reject_rbl_client relays.mail-abuse.org,
        reject_rbl_client bl.spamcop.net,
        reject_rbl_client or.orbl.org,
        reject_rhsbl_sender dsn.rfc-ignorant.org,

=====

Restart postfix and you'll be in good shape.  I have mail servers that reject ~100k messages per day, but only deliver ~2000 messages to user inboxes, out of which less than 50 are tagged as spam by SA and amavis.

The combination of the rules, rbls and grey listing noted above is pretty good for reducing cpu loads, but eliminating most spam.

HTH


Regards,

SM

---

### Post by NewbieUser on 2006-12-05
Thank you for your responses.  Always educational to see how others handle these problems.  I utilize postgrey for my greylisting server and also use SPF and Policyd-weight as policy servers.  To be honest I do not see that either SPF or Policyd-weight is doing a great deal of spam rejection. I will try your list of RBLS.  BTW why do you not use reject_unknown_client.  That seems to be an effective statement for us with very few false positives.

Thanks again.

---

### Post by speedman on 2006-12-05
> **NewbieUser said:**
> BTW why do you not use reject_unknown_client.  That seems to be an effective statement for us with very few false positives.

There are a ton of mail servers out there with no PTR record on their IP address.  I manage dozens of email servers across North America and every time we have enforced the requirement for a PTR record to exist on remote mail servers it has resulted in complaints.

I have tried to maintain exceptions to this rule on some boxes in the past, but it is way too much work.  If you're interested here's how it's done:

Add this to main.cf:

# -=CAH=- added following line RE exceptions for dumb admins
# with poorly configured mail servers with no PTR (reverse dns entry)
smtpd_client_restrictions = hash:/etc/postfix/client_restrictions

Then create /etc/postfix/client_restrictions in this format:

# -=CAH=- RE no PTR exceptions
# Whoops, we need to talk to these machines
# but they have no reverse DNS set up:
165.154.245.103     OK
64.72.235.210       OK
# Reject these guys, they keep sending us junk mail
# and won't take us off their lists
#spam_central.com        REJECT

The run:

postmap /etc/postfix/client_restrictions

HTH


Regards,

SM

---

