---
title: "serving using a ddns"
date: 2010-07-02
forum: Server Platforms
---

### Post by rekahsoft on 2010-07-02
Hi all, i currently run a server from home using ddns from dd-wrt linksys wrt160n v1. I am wondering what i should do with my domain name...as in /etc/hostname, /etc/hosts and other configuration file having to do with host name. Since my ip is not static i don't know how i would add it /etc/hosts..how does this affect running my computer as a server?

Lately i have been working on getting postfix working on my server. i can access port 25 (smtp), 110 (pop3) and 143 (imap) (using netcat or telnet) but i can't send email to my server or from my server. I don't get any error messages (that i'm aware of (although i haven't scoured the logs that well...)). Also i use alpine as my mail client..when i try and send an email i get the following error:```
There was a failure validating the SSL/TLS certificate for the server

                                                                 rekahsoft.homelinux.org

The reason for the failure was

                                                            self signed certificate (details)

We have not verified the identity of your server. If you ignore this certificate validation problem and continue, you could end up connecting to an
imposter server.

If the certificate validation failure was expected and permanent you may avoid seeing this warning message in the future by adding the option

                                                                    /novalidate-cert

to the name of the folder you attempted to access. In other words, wherever you see the characters

                                                                 rekahsoft.homelinux.org

in your configuration, replace those characters with

                                                         rekahsoft.homelinux.org/novalidate-cert

Answer "Yes" to ignore the warning and continue, "No" to cancel the open of this folder.
``` Another note: in alpine i have my smtp server as my external domain (rekahsoft.homelinux.org) as well as my domain...is this right?

---

