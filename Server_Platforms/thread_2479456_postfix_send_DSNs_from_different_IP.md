---
title: "postfix send DSNs from different IP"
date: 2022-09-25
forum: Server Platforms
---

### Post by Anquietas on 2022-09-25
I have a Postfix email server and multiple domains, each with its own IP & Reverse DNS, etc.

The problem is that when someone sends email to one of these domains and requests a "Develivery Status Notification" (DSN), the server will automatically reply from the first IP address set on the interface (the main IP provided by the ISP).

For normal email sending, I use transport_maps with "smtp_bind_address=" so there everything is OK.

The problem is with the DSN replies only. How can I set postfix to send DSN from specific IP address ?

Thank you.

---

### Post by #&amp;thj^% on 2022-09-25
Not sure this will help but, It's been my expericnce a lot of mail servers don't accept incoming connections from systems with dynamic IP addresses because most of them are systems infected with malware that tries to send spam or spread itself.

Use your ISPs mailserver as relay (sometimes called "smarthost"). Here is a short guide for that. The server name, user and password are the same as you'd use for a mail client [http://www.postfix.org/SOHO_README.html#client_sasl_enable](http://www.postfix.org/SOHO_README.html#client_sasl_enable)

This reference is a good start: [https://www.golinuxcloud.com/postfix-smtpd-relay-restrictions/](https://www.golinuxcloud.com/postfix-smtpd-relay-restrictions/)

Hint possible:```

Logs on mail.example.com

Aug 02 11:10:56 mail.example.com postfix/smtp[21464]: A3EAD5FB32: to=<root@client-2.example.com>, relay=client-2.example.com[192.168.43.148]:25, delay=0.21, delays=0.03/0.04/0.1/0.05, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 85A1C5FBDC)
```

---

### Post by Anquietas on 2022-09-26
I think you misunderstood me...

My server does not have dynamic IPs. Only static IPs.

The problem is with the DSN replies sent by my server. Those DSN replies should be sent from a specific IP address...

---

### Post by #&amp;thj^% on 2022-09-26
> **Anquietas said:**
> I think you misunderstood me...

My server does not have dynamic IPs. Only static IPs.

The problem is with the DSN replies sent by my server. Those DSN replies should be sent from a specific IP address...

Thanks for clarifying, and no where but here in this reply do you mention  "Static IPs.
So I'm/was digging for info here and not misunderstanding, 


A tunnel or VPN between the two can be useful but is not necessary &#8211; you can just use standard SMTP relay mechanisms.
[list]
    [*]On the remote server, set up a TLS certificate and enable STARTTLS.
    [*]Configure it to permit relaying for authenticated clients &#8211; you could use either regular username/password authentication, or TLS "client certificate" auth, depending on what the SMTP software supports. (In Postfix it'd be permit_sasl_authenticated or permit_tls_clientcerts.)
    [*]Configure the local server to use your remote server as a "smarthost" or "relay host". There are plenty of Gmail-oriented tutorials, but they work just the same with any server.[/list]
I can just keep guessing, **but I'll bet you did not read the second link I provided.**: [https://www.golinuxcloud.com/postfix-smtpd-relay-restrictions/#Allow_specific_network_address_to_use_relay_server](https://www.golinuxcloud.com/postfix-smtpd-relay-restrictions/#Allow_specific_network_address_to_use_relay_server)
**_For fun_**:
Allow specific network address to use relay server

Similarly we can modify mynetworks value to allow all the network subnets to use our relay server for sending mails.
```

mynetworks = 192.168.43.0/24, 127.0.0.0/8
```

Now we allow all the IP Address in 192.168.43.0/24 subnet to be able to use our relay server for sending mails.

Reload the postfix service to activate our changes
```

# systemctl reload postfix
```
I am trying to help you FWIW

---

### Post by Anquietas on 2022-09-27
Thank you for your reply, however, I don't think SMTP Relay Server can help me with this.

My original post is this:
[https://www.linuxquestions.org/questions/linux-server-73/postfix-send-dsn-replies-from-specific-ip-address-depending-on-domain-4175694736/](https://www.linuxquestions.org/questions/linux-server-73/postfix-send-dsn-replies-from-specific-ip-address-depending-on-domain-4175694736/)

Sorry I didn't post this earlier.

Basically, I need all my domains to go out with their own IP address. Which is done.
Now, I need Postfix's DSN to be sent from a specific IP.
That's the whole problem :-)

---

### Post by #&amp;thj^% on 2022-09-27
> **Anquietas said:**
> Thank you for your reply, however, I don't think SMTP Relay Server can help me with this.

Sorry I didn't post this earlier.


I'll take your word for it then, but it works for me.
On with the thread.
Yes I understand what your asking, but I'm only familiar with "SMTP Relay Server " however I do think your wants are doable, It will just take some tinkering.



If your **"postconf -n"** looks like this example:
```

smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
        -o smtp_fallback_relay=
```

Try this change to this:
```

smtp      unix  -       -       -       -       -       smtp
        -o smtp_bind_address=192.168.0.1
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
        -o smtp_bind_address=192.168.0.1
        -o smtp_fallback_relay=
```

Of course, instead of 192.168.0.1 you must use one of your IP addresses, the one you want to send your mail from.
Keep us posted I'm curious now.

---

### Post by SeijiSensei on 2022-09-27
> **Anquietas said:**
> Basically, I need all my domains to go out with their own IP address. Which is done.
Now, I need Postfix's DSN to be sent from a specific IP.
This really sounds like something that would be solved with a outbound server running as an SMTP relay. Have all the individual domains configured to use the relay, and all the mail will go out from that machine. The outbound mail will have a Return-Path header that points to the relay server. That means you need to configure what to do with incoming bounce messages, etc., that will be sent to the relay host. They may get routed automatically depending on your DNS setup, or you may need to specify rules to forward inbound mail to the appropriate domain.

---

### Post by #&amp;thj^% on 2022-09-27
> **SeijiSensei said:**
> This really sounds like something that would be solved with a outbound server running as an SMTP relay. Have all the individual domains configured to use the relay, and all the mail will go out from that machine. The outbound mail will have a Return-Path header that points to the relay server. That means you need to configure what to do with incoming bounce messages, etc., that will be sent to the relay host. They may get routed automatically depending on your DNS setup, or you may need to specify rules to forward inbound mail to the appropriate domain.

+One Million:popcorn:
Thanks SeijiSensei for the agreement.

---

