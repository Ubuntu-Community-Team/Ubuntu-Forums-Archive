---
title: "whitelist with python-policyd-spf"
date: 2010-10-26
forum: Server Platforms
---

### Post by Homer on 2010-10-26
Hello,

I'm trying to whitelist a domain in policyd-spf.  I don't want mail from this domain to be checked for spf (the mail should pass even if spf fail).

I added this line in /etc/postfix-policyd-spf-python/policyd-spf.conf
```
Domain_Whitelist = whitelisted-domain.tld
```

But policyd-spf still blocks email from this domain...

---

### Post by the_original_billq on 2010-10-26
> **Homer said:**
> Hello,

I'm trying to whitelist a domain in policyd-spf.  I don't want mail from this domain to be checked for spf (the mail should pass even if spf fail).

I added this line in /etc/postfix-policyd-spf-python/policyd-spf.conf
```
Domain_Whitelist = whitelisted-domain.tld
```

But policyd-spf still blocks email from this domain...

Can you resolve the domain on the server?

-Bill

---

### Post by Homer on 2010-10-26
> **the_original_billq said:**
> Can you resolve the domain on the server?

-Bill

Yes.

---

### Post by the_original_billq on 2010-10-26
> **Homer said:**
> Yes.

Does the domain have an SPF record?  If not, you will need to use the IP Whitelist.

---

### Post by Homer on 2010-10-26
> **the_original_billq said:**
> Does the domain have an SPF record?  If not, you will need to use the IP Whitelist.

Yes the domain have an SPF record.

I cannot use ip whitelist because mail can come from various unknown ips.

---

### Post by the_original_billq on 2010-10-26
> **Homer said:**
> Yes the domain have an SPF record.

I cannot use ip whitelist because mail can come from various unknown ips.

Are you able to validate the SPF records here?

[http://www.kitterman.com/spf/validate.html]("http://www.kitterman.com/spf/validate.html")

---

### Post by Homer on 2010-10-26
> **the_original_billq said:**
> Are you able to validate the SPF records here?

[http://www.kitterman.com/spf/validate.html]("http://www.kitterman.com/spf/validate.html")

Yes.

> evaluating...
SPF record passed validation test with pySPF (Python SPF library)!

---

### Post by the_original_billq on 2010-10-26
Can you post your policyd-spf.conf?  (sanitized...)

thanks...

---

### Post by Homer on 2010-10-26
This is my file:

```
#  For a fully commented sample config file see policyd-spf.conf.commented

debugLevel = 1
defaultSeedOnly = 1

HELO_reject = SPF_Not_Pass
Mail_From_reject = Fail

PermError_reject = False
TempError_Defer = False

skip_addresses = 127.0.0.0/8,::ffff:127.0.0.0//104,::1//128

Domain_Whitelist = whitelisted-domain.tld

```

---

### Post by the_original_billq on 2010-10-26
> **Homer said:**
> This is my file:

```
#  For a fully commented sample config file see policyd-spf.conf.commented

debugLevel = 1
defaultSeedOnly = 1

HELO_reject = SPF_Not_Pass
Mail_From_reject = Fail

PermError_reject = False
TempError_Defer = False

skip_addresses = 127.0.0.0/8,::ffff:127.0.0.0//104,::1//128

Domain_Whitelist = whitelisted-domain.tld

```

Try adding:
```

Reject_Not_Pass_Domains = whitelisted-domain.tld

```

Though I don't see why it wouldn't be working as-is...

---

### Post by Homer on 2010-10-27
Still not working... I also tried to install lucid packages (on jaunty) to get a more updated version... with no more success.

---

### Post by the_original_billq on 2010-10-27
OK, I'm sure this is the case, but I'll ask...

Are you restarting postfix after modifying the config?

---

### Post by Homer on 2010-10-27
> **the_original_billq said:**
> OK, I'm sure this is the case, but I'll ask...

Are you restarting postfix after modifying the config?

Yes I restart postfix every time.  The change apply because I see the difference when I enable/disable debugging value.

---

### Post by the_original_billq on 2010-10-27
Yeah, I knew you were, but I had to ask...

So, does anything show up in the logs if you bump up the debug level?

Also, have you tried commenting everything but the whitelist to take defaults?

---

### Post by Homer on 2010-10-27
> **the_original_billq said:**
> Yeah, I knew you were, but I had to ask...

So, does anything show up in the logs if you bump up the debug level?

Also, have you tried commenting everything but the whitelist to take defaults?

I tried to leave all defaults, but this do the same thing.

My current config file:
> #  Amount of debugging information logged.  0 logs no debugging messages
#  4 includes all debug messages.
debugLevel = 4 

#  If set to 0, no messages are rejected by SPF.  This allows you to see the 
#  potential impact of SPF checking in your mail logs without rejecting mail.
defaultSeedOnly = 1

#  HELO check rejection policy. Options are:
#  HELO_reject = SPF_Not_Pass (default) - Reject if result not Pass/None/Tempfail.
#  HELO_reject = Softfail - Reject if result Softfail and Fail
#  HELO_reject = Fail - Reject on HELO Fail
#  HELO_reject = Null - Only reject HELO Fail for Null sender (SPF Classic)
#  HELO_reject = False - Never reject/defer on HELO, append header only. 
#  HELO_reject = No_Check - Never check HELO.
HELO_reject = Null

#  HELO pass restriction policy.
#  HELO_pass_restriction = helo_passed_spf - Apply the given restriction when
#    the HELO checking result is Pass.  The given restriction must be an
#    action as defined for a Postfix SMTP server access table access(5).
#HELO_pass_restriction

#  Mail From rejection policy.  Options are:
#  Mail_From_reject = SPF_Not_Pass - Reject if result not Pass/None/Tempfail.
#  Mail_From_reject = Softfail - Reject if result Softfail and Fail
#  Mail_From_reject = Fail - Reject on Mail From Fail (default)
#  Mail_From_reject = False - Never reject/defer on Mail From, append header only
#  Mail_From_reject = No_Check - Never check Mail From/Return Path.
Mail_From_reject = Fail

#  Reject only from domains that send no mail. Options are:
#  No_Mail = False - Normal SPF record processing (default)
#  No_Mail = True - Only reject for "v=spf1 -all" records

#  Mail From pass restriction policy.
#  Mail_From_pass_restriction = mfrom_passed_spf - Apply the given
#    restriction when the Mail From checking result is Pass.  The given 
#    restriction must be an action as defined for a Postfix SMTP server
#    access table access(5).
#Mail_From_pass_restriction

#  Reject mail for Netural/Softfail results for these domains.
#  Recevier policy option to reject mail from certain domains when SPF is not
#  Pass/None even if their SPF record does not produce a Fail result.  This
#  Option does not change the effect of PermError_reject or TempError_Defer
#  Reject_Not_Pass_Domains = aol.com,hotmail.com

#  Policy for rejecting due to SPF PermError.  Options are:
#  PermError_reject = True
#  PermError_reject = False
PermError_reject = False

#  Policy for deferring messages due to SPF TempError.  Options are:
#  TempError_Defer = True
#  TempError_Defer = False
TempError_Defer = False

#  Prospective SPF checking - Check to see if mail sent from the defined IP
#  address would pass.
#  Prospective = 192.168.0.4

#  Do not check SPF for localhost addresses - add to skip addresses to 
#  skip SPF for internal networks if desired. Defaults are standard IPv4 and
#  IPv6 localhost addresses.
skip_addresses = 127.0.0.0/8,::ffff:127.0.0.0//104,::1//128

#  Whitelist: CIDR Notation list of IP addresses not to check SPF for.
#  Example (default is no whitelist):
#  Whitelist = 192.168.0.0/31,192.168.1.12

#  Domain_Whitelist: List of domains whose sending IPs (defined by passing
#  their SPF check should be whitelisted from SPF.
#  Example (default is no domain whitelist):
#  Domain_Whitelist = pobox.com,trustedforwarder.org
Domain_Whitelist = whitelisted-domain.tld

# Domain_Whitelist_PTR: List of domains to whitelist against SPF checks base
# on PTR match.
# Example (default is no PTR whitelist)
# Domain_Whitelist_PTR = yahoo.com


Debug log :
> Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "request=smtpd_access_policy"
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "protocol_state=RCPT"
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "protocol_name=ESMTP"
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "client_address=remote-smtp-ip"
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "client_name=remote-smtp"
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "reverse_client_name=remote-smtp"
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "helo_name=remote-smtp"
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "sender=sender@domain.tld"
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "recipient=sender@domain.tld"
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "recipient_count=0"
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "queue_id="
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "instance=e9a.4cc86229.230a8.0"
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "size=0"
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "etrn_domain="
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "stress="
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "sasl_method="
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "sasl_username="
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "sasl_sender="
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "ccert_subject="
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "ccert_issuer="
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "ccert_fingerprint="
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "encryption_protocol="
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "encryption_cipher="
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: "encryption_keysize=0"
Oct 27 13:32:32 mail policyd-spf[3746]: Read line: ""
Oct 27 13:32:32 mail policyd-spf[3746]: Found the end of entry
Oct 27 13:32:32 mail policyd-spf[3746]: Config: {'Mail_From_reject': 'Fail', 'Domain_Whitelist': 'whitelisted-domain.tld', 'HELO_reject': 'Null', 'defaultSeedOnly': 1, 'PermError_reject': 'False', 'debugLevel': 4, 'skip_addresses': '127.0.0.0/8,::ffff:127.0.0.0//104,::1//128', 'TempError_Defer': 'False'}
Oct 27 13:32:32 mail policyd-spf[3746]: Cached data for this instance: []
Oct 27 13:32:32 mail policyd-spf[3746]: spfcheck: pyspf result: "['None', '', 'helo']"
Oct 27 13:32:32 mail policyd-spf[3746]: None; identity=helo; client-ip=remote-smtp-ip; helo=remote-smtp; envelope-from=sender@domain.tld; receiver=sender@domain.tld 
Oct 27 13:32:32 mail policyd-spf[3746]: spfcheck: pyspf result: "['Fail', 'SPF fail - not authorized', 'mailfrom']"
Oct 27 13:32:32 mail policyd-spf[3746]: Fail; identity=mailfrom; client-ip=remote-smtp-ip; helo=remote-smtp; envelope-from=sender@domain.tld; receiver=sender@domain.tld 
Oct 27 13:32:32 mail postfix/smtpd[3738]: NOQUEUE: reject: RCPT from remote-smtp[remote-smtp-ip]: 550 5.7.1 <sender@domain.tld>: Recipient address rejected: Message rejected due to: SPF fail - not authorized. Please see [http://www.openspf.org/Why?s=mfrom;id=sender@domain.tld;ip=remote-smtp-ip;r=sender@domain.tld;](http://www.openspf.org/Why?s=mfrom;id=sender@domain.tld;ip=remote-smtp-ip;r=sender@domain.tld;) from=<sender@domain.tld> to=<sender@domain.tld> proto=ESMTP helo=<remote-smtp>
Oct 27 13:32:33 mail postfix/smtpd[3738]: disconnect from remote-smtp[remote-smtp-ip]


SPF record of the whitelisted domain:
> ;; ANSWER SECTION:
domain.tld.			1450	IN	TXT	"v=spf1 mx a:a.domain.tld a:b.domain.tld a:c.domain.tld a:d.domain.tld ip4:1.2.3.4 -all"
domain.tld.			1450	IN	TXT	"v=spf2.0/mfrom mx a:a.domain.tld a:b.domain.tld a:c.domain.tld a:d.domain.tld ip4:1.2.3.4 -all"

---

### Post by the_original_billq on 2010-10-27
AH!

Change:

Domain_Whitelist = whitelisted-domain.tld

To:

Domain_Whitelist = domain.tld

---

### Post by Homer on 2010-10-28
Mmm so the whitelist is on the rdns ip?

I added the domain where I do my test into the whitelist. If the request come from an ip with a rdns that match Domain_Whitelist, the mail pass.  If the request come from an ip w/o rdns, the mail is blocked.  

This is not what I tried to do.  I wanted to ignore SPF validating for a specific domain.

whitelisted-domain.tld is our and I want to allow internals mails (remote teleworkers) to send mail inside the domain (they use their isp smtp), but I still want to block spammers to use our domains to send spam with our identity.

I think I will just setup authenticated smtp on non-standard port (to avoid port 25 blocking by isp) to bypass spf checking for our internal mail.

---

