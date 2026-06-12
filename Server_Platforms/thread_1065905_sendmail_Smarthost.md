---
title: "sendmail: Smarthost?"
date: 2009-02-10
forum: Server Platforms
---

### Post by berankin99 on 2009-02-10
Hello,

I am trying to test some CGI scripts locally on my laptop. (Running 8.10 desktop)

It seems that I already have "sendmail" installed on my machine. 

I tried calling it like:```
cat email.txt | /usr/sbin/sendmail -t -i
```
...and received no output or error.

However the message is not delivered. This is not surprising as even if Sendmail (Exim4?) was configured to work, my ISP blocks outgoing connections on port 25.

I do have access to smarthost running on port 2525, but it also needs SSL(TLS?) + SMTP AUTH

So, I presume I must configure sendmail to do this, but how?  Also, where has all the mail I already submitted to "/usr/sbin/sendmail" gone?

(Naturally I also want to ensure the sendmail/exim will not suddenly start acting as an open relay on my laptop's port 25...)

Thank you,
:)

P.S.
Calling just "/usr/sbin/sendmail"

Yields:

```
Exim is a Mail Transfer Agent. It is normally called by Mail User Agents,
not directly from a shell command line. Options and/or arguments control
what it does when called. For a list of options, see the Exim documentation.
```

---

### Post by berankin99 on 2009-02-10
anybody?

---

### Post by mansonthomas on 2009-02-10
the sendmail exec is here for compatibility reasons... 

it's Exim you have to configure.



If your 25 port is blocked, you should use the SMTP of your ISP.

If not possible try this solution : 

[http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/](http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/)

That make exim4 uses gmail stmp over ssl,
It works great for me, but I needed to do something more.

I paste here the whole article + my comments : 




Configuration de Exim4 (installed as a dependancy of bacula)
from : [http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/](http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/)
Step 1

Run dpkg-reconfigure exim4-config

    * Choose mail sent by **smarthost**; received via SMTP or fetchmail
    * Type System Mail Name: e.g. **home.paquerette.com**
    * Type IP Adresses to listen on for incoming SMTP connections: **127.0.0.1**
    * Leave Other destinations for which mail is accepted blank (leave **home.paquerette.com**)
    * Leave Machines to relay mail for: **blank**
    * Type Machine handling outgoing mail for this host (smarthost): **smtp.gmail.com::587**
    * Choose **NO**, don&#8217;t hide local mail name in outgoing mail.
    * Chose **NO**, don&#8217;t keep number of DNS-queries minimal (Dial-on-Demand).
    * Choose **mbox**
    * Choose **NO**, split configuration into small files
    * Mail for postmaster. Leaving blank will not cause any problems though it is not recommended (**not seen on my version**)

Step 2

    * Open the file /etc/exim4/exim4.conf.template
    * Find the line .ifdef DCconfig_smarthost DCconfig_satellite and add the following in that section

       send_via_gmail:
       driver = manualroute
       domains = ! +local_domains
       transport = gmail_smtp
       route_list = * smtp.gmail.com

      If you have any other smarthost defined with &#8220;domains = ! +local_domains&#8221; remove that smarthost. 




   [PHP] .ifdef DCconfig_smarthost DCconfig_satellite
    # configtype=smarthost or configtype=satellite
    #
    # Send all non-local mail to a single other machine (smarthost).
    #
    # This means _ALL_ non-local mail goes to the smarthost. This will most
    # probably not do what you want for domains that are listed in
    # relay_domains. The most typical use for relay_domains is to control
    # relaying for incoming e-mail on secondary MX hosts. In that case,
    # it doesn't make sense to send the mail to the smarthost since the
    # smarthost will probably send the message right back here, causing a
    # loop.
    #
    # If you want to use a smarthost while being secondary MX for some
    # domains, you'll need to copy the dnslookup_relay_to_domains router
    # here so that mail to relay_domains is handled separately.

    send_via_gmail:
           driver = manualroute
           domains = ! +local_domains
           transport = gmail_smtp
           route_list = * smtp.gmail.com

    #smarthost:
    #  debug_print = "R: smarthost for $local_part@$domain"
    #  driver = manualroute
    #  domains = ! +local_domains
    #  transport = remote_smtp_smarthost
    #  route_list = * DCsmarthost byname
    #  host_find_failed = defer
    #  same_domain_copy_routing = yes
    #  no_more

    .endif[/PHP]







    * Find the &#8220;begin authenticators&#8221;. In that section add the following

       gmail_login:
       driver = plaintext
       public_name = LOGIN
       client_send = : [email]**yourname@gmail.com**[/email] : **YourGmailPassword**

      Make sure you have no other authenticators with the same public_name (LOGIN). Comment them out if needed (Thanks Jakub for reminding me) 

    * Find the comment  &#8220;transport/30_exim4-config_remote_smtp_smarthost&#8221;. In that section add

       gmail_smtp:
       driver = smtp
       port = 587
       hosts_require_auth = $host_address
       hosts_require_tls = $host_address

comment out the end of the file :


   [PHP] #.ifndef AUTH_CLIENT_ALLOW_NOTLS_PASSWORDS
    #  client_send = "<; ${if !eq{$tls_cipher}{}\
    #                    {^${extract{1}{:}{PASSWDLINE}}\
    #        ^${sg{PASSWDLINE}{\\N([^:]+:)(.*)\\N}{\\$2}}\
    #      }fail}"
    #.else
    #  client_send = "<; ^${extract{1}{:}{PASSWDLINE}}\
    #       ^${sg{PASSWDLINE}{\\N([^:]+:)(.*)\\N}{\\$2}}"
    #.endif

    #login:
    #  driver = plaintext
    #  public_name = LOGIN

    #.ifndef AUTH_CLIENT_ALLOW_NOTLS_PASSWORDS
      # Return empty string if not non-TLS AND looking up $host in passwd-file
      # yields a non-empty string; fail otherwise.
    #  client_send = "<; ${if and{\
    #                          {!eq{$tls_cipher}{}}\
    #                          {!eq{PASSWDLINE}{}}\
    #                         }\
    #                      {}fail}\
    #                 ; ${extract{1}{::}{PASSWDLINE}}\
    #    ; ${sg{PASSWDLINE}{\\N([^:]+:)(.*)\\N}{\\$2}}"
    #.else
      # Return empty string if looking up $host in passwd-file yields a
      # non-empty string; fail otherwise.
    #  client_send = "<; ${if !eq{PASSWDLINE}{}\
    #                      {}fail}\
    #                 ; ${extract{1}{::}{PASSWDLINE}}\
    #    ; ${sg{PASSWDLINE}{\\N([^:]+:)(.*)\\N}{\\$2}}"
    #.endif
    #####################################################
    ### end auth/30_exim4-config_examples
    #####################################################[/PHP]



Step 3

    * Run update-exim4.conf
    * Do /etc/init.d/exim4 restart (or service exim4 restart)




Note : if you did some config mistake before getting a correct file, on exim4 restart, you&#8217;ll get this warning :

* ALERT: exim paniclog /var/log/exim4/paniclog has non-zero size, mail system possibly broken

Which tells that the log file has something in it and you should look into.

Mine got these kind of message :

2009-02-08 00:35:50 Exim configuration error in line 834 of /var/lib/exim4/config.autogenerated.tmp:
&#8220;client_send&#8221; option set for the second time

Has it&#8217;s my previous mistake, you can safely delete the file to get rid off the warning and restart exim4.




That should be it. You can test by using the command line mail client.

    * Run mail [email]user@example.com[/email]
    * Give a subject and press enter
    * Type something and press enter
    * Type a single . (dot) and press enter
    * Press enter for a blank CC:

This was on an Ubuntu server. I believe that this instructions will also work on Debain without any need for modifications.

---

### Post by hictio on 2009-02-10
berankin99, perhaps you should take a look at ssmtp. Free, easy to install, easy to setup, easy to use.

[sSMTP: A simple alternative to Sendmail](http://www.linux.com/feature/132006)
[Sending Email From Your System with sSMTP](http://tombuntu.com/index.php/2008/10/21/sending-email-from-your-system-with-ssmtp/)

---

### Post by mansonthomas on 2009-02-10
well ssmtp is surely great but if port 25 is block by the ISP, he will have the same issue...

---

### Post by hictio on 2009-02-10
> **mansonthomas said:**
> well ssmtp is surely great but if port 25 is block by the ISP, he will have the same issue...

Maybe I don't understand, but if you use Gmail's Submission port, like on the second link example, it will bypass the block on the ISP SMTP's port.

---

### Post by berankin99 on 2009-02-10
Hello all,

Thank you for the replies.  :)

Just to clarify:  Even though outgoing port 25 is blocked, **I do have access to an SMTP relay from my webhost that runs on a different port and uses TLS + AUTH**

So, i have three questions:

[LIST=1]
[*]How do I configure Exim (via the sendmail "alias") to use the above relay for all outgoing mail.
[*]How do I ensure that I don't inadvertently have Exim running as an Open Relay.
[*]What happened to all the mail I submitted already via Sendmail? It must be sitting somewhere, no?
[/LIST]

Thank you,
:)

---

### Post by mansonthomas on 2009-02-10
> **hictio said:**
> Maybe I don't understand, but if you use Gmail's Submission port, like on the second link example, it will bypass the block on the ISP SMTP's port.

Lol... I didn't see the two last line of your post were http links as css style is the same as regular text ;)

So yes, the second link provide the same solution ;)

Thomas.

---

### Post by hictio on 2009-02-10
> 
3 What happened to all the mail I submitted already via Sendmail? It must be sitting somewhere, no?


Try this:

```

sudo mailq ENTER

```

It has to print the queued email run.
Once you have the connection to your SMART_HOST setup, issue a:

```

sudo sendmail -q ENTER

```

to force a flush of the queued email(s).

---

### Post by berankin99 on 2009-02-11
> **hictio said:**
> Try this:

```

sudo mailq ENTER

```

It has to print the queued email run.
Once you have the connection to your SMART_HOST setup, issue a:

```

sudo sendmail -q ENTER

```

to force a flush of the queued email(s).


Hmm... running "sudo mailq" did not return anything.  What does that mean?

Also, I am still unsure how to configure a Smarthost that requires TLS+AUTH.

Any ideas?

---

