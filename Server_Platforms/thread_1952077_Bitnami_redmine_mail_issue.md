---
title: "Bitnami redmine mail issue"
date: 2012-04-03
forum: Server Platforms
---

### Post by saphil on 2012-04-03
I have 2 machines in a network.
the client is a website running  redmine, on which the email client worked great when the email account  involved was a gmail acct.
I want my network mailserver to be the smtp server for this client.
The  mailserver is running exim4 and the account can receive email from  outside the network, and it also can receive mail from a commandline  test.
Other web-servers are able to use this mailserver for outbound mail.

Redmine documentation suggests:

```
production:   delivery_method: :smtp   smtp_settings:     tls: true     address: "smtp.gmail.com"     port: 587     domain: "smtp.gmail.com"     authentication: :plain     user_name: "your_email@gmail.com"     password: "your_password"     enable_starttls_auto: true
```This config worked great for gmail

The following is how my setup is:
the mailserver is just example.net at NATted address of 192.168.20.20
The redmine server is on the same subnet  at 192.168.20.30

```
# default configuration options for all environments default:   # Outgoing emails configuration (see examples above)   email_delivery:     delivery_method: :smtp     smtp_settings:       address: example.net       port: 25       domain: example.net       authentication: :login       user_name: "webmaster@example.net"       password: "redmine"
```

This does not work. Is there anybody here running bitnami rubystack with redmine in a similar network architecture?

-Wolf

---

