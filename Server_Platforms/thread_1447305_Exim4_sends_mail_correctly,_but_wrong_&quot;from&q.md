---
title: "Exim4 sends mail correctly, but wrong &quot;from&quot; address"
date: 2010-04-05
forum: Server Platforms
---

### Post by Gambakoker on 2010-04-05
Hello everyone!

I have a ubuntu server 9.10 installed with exim4 as MTA. I configured a mail address on it (let's say [email]me@example.com[/email]). Before i had it working i had a other email configured (let's say [email]me_2@example.com[/email]). At the time i had this one it didn't work i removed exim4.

Now i can successfully send mails with it by the configured [email]me@example.com[/email]. I also configured the password for this, but when i receive the mail the old configured mail is presented as "from" (so from: [email]me_2@example.com[/email]).

Anyone knows how this can be changed so it says the mail is from [email]me@example.com[/email]? The mail is not an alias, and in a mail client they work separately.

---

### Post by Bachstelze on 2010-04-05
How are you sending your email? The From: address is generally configured in your client, independently of the MTA.

---

### Post by Gambakoker on 2010-04-05
> **Bachstelze said:**
> How are you sending your email? The From: address is generally configured in your client, independently of the MTA.

I'm sending the mail with the CLI of ubuntu server. It's a virtual machine where i connect to from the terminal with ssh

EDIT:
Example of how i send it is:
mail [email]mail_to_send_to@examples.com[/email]
Cc: <empty>
Subject: test
message to sent
.
user@server:~$

---

### Post by Bachstelze on 2010-04-05
Then, unless you configured some kind of address rewriting in your MTA, the From: email will be user@host where host is the hostname of te machine and user is your real username on the machine (the same name that is returned by e.g. the *whoami* command).

---

### Post by Gambakoker on 2010-04-05
> **Bachstelze said:**
> Then, unless you configured some kind of address rewriting in your MTA, the From: email will be user@host where host is the hostname of te machine and user is your real username on the machine (the same name that is returned by e.g. the *whoami* command).

If i understand you correctly, i think this isn't the problem. I have a email account specially for the server it is [email]myname.ubuntu@myhost.com[/email], while the email where it's from is completely different, and my username of the server is the same as the [email]myname.ubuntu@hmyhost.com[/email].

But it's strange i can't find that old email address anywhere anymore so i dont' get where it's getting from.

---

