---
title: "Remote IMAP server"
date: 2011-06-09
forum: Server Platforms
---

### Post by Jay89 on 2011-06-09
Does anyone know how to go about setting up a secure IMAP email server that is able to be accessed from outside the network? Similar to how you can access your google email account from your computer using Thunderbird.

Thanks!

---

### Post by egpetrich on 2011-06-15
I've gone part way down this route. First thing (obviously) is to have the IMAP server program (e.g. Dovecot) running on your machine. I think the Server Guide ([link to 10.04 version]("https://help.ubuntu.com/10.04/serverguide/C/index.html")) is good for this.

Next comes external access. If you don't have a guaranteed static IP address, you may need to use a Dynamic DNS service. (Sorry if this is rehashing stuff you know.) Then you have to decide if you're willing to open a port in your firewall for IMAP. Is the login security on the IMAP server strong enough? I don't know.

My thought was to use an SSH tunnel. Connect via SSH from outside and forward some acceptable local port to port 143 on the IMAP server machine. Then the only port you have to open in your firewall is 22.

Possible issues:
[LIST]
[*]You need to set up the SSH tunnel even if you're running inside your network, since you'll be connecting to "localhost" from your e-mail client.
[*]Your address book is still local to the machine where you're running Thunderbird, so it isn't very portable. Thunderbird has some add-ons to support syncing, but I haven't tried them.
[/LIST]

As I said, I went partway. I have Dovecot running on the server, but I'm also running Roundcube webmail. I set up my SSH tunnel to the Web server behind the firewall, then connect with a browser. It's slower, and I'm not entirely satisfied, but it works.

---

### Post by Jay89 on 2011-06-15
Thank you for your reply,
    I'll look into that but would you happen to have any tips about configuring ssl for outgoing mail? I am able to connect using thunderbird via port 993 for secure imap to the inbox. But when I try to send I have to disable ssl and use "no security" in order for it to send the mail. So it uses port 25 instead of port 465. Also, I noticed that it *can* work if I set the authentication to Kerberos / GSSAPI.

Any suggestions?

---

### Post by SeijiSensei on 2011-06-15
Sending mail is handled by a different server than IMAP.  By default, Ubuntu uses Postfix for this purpose.  If you're also using Postfix, [read this]("https://help.ubuntu.com/community/Postfix").

---

