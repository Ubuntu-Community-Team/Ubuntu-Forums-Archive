---
title: "Relay access denied"
date: 2013-05-31
forum: Server Platforms
---

### Post by TheChef1993 on 2013-05-31
Hi guys,

I know there are a lot of threads about this issue but I still can't find a solution.
I'm using Postfix 2.9.6 and everything workes fine except the sending of mails with outlook. I always get the message that the relay access is denied.
I generally do not allow relay to prevent spam through my server.
How do I have to set up postfix to allow relay for outlook users?

I tried ```
smtpd_relay_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
``` but just got an error message that this is an unused parameter.

Can please somebody assist? Please let me know if you need more information about my configuration.

Thanks in advanced

---

### Post by Doug S on 2013-05-31
Are your clients that are using outlook on your local area network? And did you add that network to the "mynetworks" directive in main.cf? Example:```
doug@doug-64:~/config/etc/postfix$ [COLOR=#ff0000]grep -n mynet *[/COLOR]
main.cf:3:# smythies.com 2012.07.05 add LAN to mynetworks
main.cf:42:mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 [COLOR=#ff0000]192.168.111.0/24[/COLOR]
main.cf.original:36:mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
```

---

### Post by TheChef1993 on 2013-05-31
The clients are not in the lan. I want to make it possible that where ever you are you can send mail. So i can't just add some ISPs to the relay list. I'm wondering how google or other online mail provider solve this issue.

---

### Post by volkswagner on 2013-06-01
> **TheChef1993 said:**
> The clients are not in the lan. I want to make it possible that where ever you are you can send mail. So i can't just add some ISPs to the relay list. I'm wondering how google or other online mail provider solve this issue.

```
permit_sasl_authenticated
```

To eliminate the need to add outside network ranges, if your sasl auth is working properly these clients will be allowed
to connect from outside the LAN.

---

### Post by lisati on 2013-06-01
<aside>
Most of the examples I've seen have the permit_sasl_authenticated and permit_mynetworks on Postfix's smtpd_sender_restrictions option.
Are you using Postfix 2.10 or later by any chance?
</aside>

---

### Post by TheChef1993 on 2013-06-01
Thanks for the help so far. I'm using permit_sasl_authenicated already on Postfix 2.9.6.

What recipient permissions would you recommend in general?

---

### Post by lisati on 2013-06-01
As near as I can make out from the Postfix web site, [smtpd_relay_restrictions]("http://www.postfix.org/postconf.5.html#smtpd_relay_restrictions") was introduced for postfix version 2.10, so it might need a bit of re-working to get an equivalent for 2.9.6.

Here's an example of an alternative from the [Spamcop]("http://www.spamcop.net/fom-serve/cache/349.html") website, which should help get you started:
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
    permit

```

---

### Post by TheChef1993 on 2013-06-01
Thank you very much for your help. It is working know.
```
[COLOR=#000000]permit_sasl_authenticated
```
[/COLOR]
that was the missing piece in the puzzle

---

### Post by TheChef1993 on 2013-06-01
I mean in the sender restrictions it was missing and after I added it it works.

---

