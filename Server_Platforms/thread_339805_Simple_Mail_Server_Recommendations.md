---
title: "Simple Mail Server Recommendations"
date: 2007-01-16
forum: Server Platforms
---

### Post by dgrincletus on 2007-01-16
Hello all,

Sorry to make my first post a question that is going to seem silly to most...

I'm setting up a server for use with a small network. The network is completely isolated from the internet. There will be the server I'm setting up (running Ubuntu Server 6.10), an existing server (running Suse 9.1), 3 or 4 other Linux boxes, and 5 or 6 Win boxes. 

I would like to setup an email server for user to user email and for utilities like Bacula to send notifications. As I've been reading about Exim4, Postfix, Dovecot, Courier, etc... I keep coming up with new questions. There are two questions in particular that keep giving me the most trouble:
[LIST=1]
[*]Do I really need a mail transfer agent (like Exim4) and a mail delivery agent (like Dovecot) if I just want to be able to send and receive mail on an isolated network?
[*]Assuming that I do want to go with Exim4 as my MTA and I use the dpkg-reconfigure exim4-config method to configure it, what configuration type should I use?[LIST][*]internet site[*]mail sent by smarthost; received via SMTP or fetchmail[*]mail sent by smarthost; no local mail[*]local delivery only; not on a network[/LIST]
The way these choices are worded, none seem to fit my application.
[/LIST]

---

### Post by Brazen on 2007-01-16
1. YES

2. "Internet Site"

I know, Internet Site is a bad way of putting it, but your email server will send and recieve just like an internet server, just without access outside your local network.

---

### Post by dgrincletus on 2007-01-16
Thanks,

I just got everything up and running!

---

### Post by Brazen on 2007-01-16
You're welcome.  Glad if helped!

---

