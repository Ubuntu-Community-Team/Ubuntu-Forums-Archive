---
title: "How to detect weak postfix passwords ?"
date: 2011-01-02
forum: Server Platforms
---

### Post by mscag on 2011-01-02
Hi,

I am running postfix with virtual users on Ubuntu LTS. Users can change their paswords using Squirrelmail.

I have also managed to write a "self service password recovery" script using "unix_md5_crypt" function with Perl overwriting new passwords to the mailbox table of the postfix database.

I have taken all the security precautions I could for spammers and intruders, but due to some weak passwords, outsiders managed to compromise some addresses and send spam by authenticating to postfix.

Is there a way to detect weak passwords using the MD5 encrypted password values in the database ?

I was planning to encrypt the usernames, names, surnames, "1234"s, birthdates etc. using the same Perl function and compare them with the current hash values, but then realized that any password does not result with the same value after being encrypted. So this does not seem to be a solution.

Any idea ?

---

### Post by kidders on 2011-01-03
Hi there,

> **mscag said:**
> any password does not result with the same value after being encrypted.

That's probably because your password hashes are being salted. Detecting weak passwords by comparing their hashes against a dictionary basically amounts to performing a brute force attack on your own server, so it's very labour-intensive by design. You'd need to create individual hash dictionaries for every user on your system, because each of their passwords would most likely be salted differently.

I've used that approach on a few occasions as a last resort, but it's only practical if you've got a reasonably small number of users. It'd be far better to prevent weak passwords being set in the first place, eg by modifying your perl script to enforce a few basic complexity rules. If you really have no other option, I'd recommend using a proper dictionary attack word list, rather than manufacturing one of your own (ie use the same approach as the script kiddies trying to hijack your mail server).

An alternative option might be to frustrate brute force attacks by making them inordinately time-consuming ...[LIST]
[*]You could write another perl script to monitor your SMTP logs and temporarily ban accounts (or maybe even IP addresses) that repeatedly fail to authenticate.
[*]Depending on how your authentication is being handled, you may be able to insert artificial delays into the password verification process. For example, PAM-based authentication mechanisms can be configured to sit there and think for a while (eg 5 or 6 seconds) before rejecting a login.
[/LIST]

I hope that helps.

---

