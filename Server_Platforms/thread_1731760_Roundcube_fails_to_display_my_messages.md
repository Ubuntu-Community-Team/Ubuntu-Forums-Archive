---
title: "Roundcube fails to display my messages"
date: 2011-04-17
forum: Server Platforms
---

### Post by simolokid4 on 2011-04-17
Hi peeps,

- I've installed Courier & Clamav succesfully
- I can send mails trough roundcube.
- I can send mails from my hotmail to my new made email

I just can't get roundcube to display all of this.

What I have noticed is the following:

In the /home/contact directory, there is a Maildir with the standard directorys with nothing in it.
In /var/mail/contact is 1 file, containing all testmails ive send so far.

So I think im only seeing the top of the iceberg and not the entire problem so to say.

How would I go and solve this? I'm kind of lost after 3 houres of searching on google..

Thanks for any answers,

Simolokid

---

### Post by elico on 2011-04-17
and what the logs has to say?
what about standard IMAP client such as Thunderbird?

---

### Post by simolokid4 on 2011-04-18
> and what the logs has to say?
what about standard IMAP client such as Thunderbird?     - Logs are empty, or atleast.. they have no errors or anything. The most interesting that happens is me loggin in....

- Just tested it with thunderbird. Also fails.

I think it has something to do with mails added to the /var/mail/contact file (mail adres is [EMAIL="contact@domain.tld"]contact@domain.tld[/EMAIL]) instead of adding it to the home directory which contains Maildir directory.

[Edit] Just looked in /etc/ folder to see if i saw more then 1 mail programs and i did. I'm seeing courier and postfix. Tried to find a configfile with /var/mail in it, but have been unsuccesfull so far.

---

### Post by simolokid4 on 2011-04-18
Letting you know it seems solved.

I can now succesfully read my mail with roundcube!

What I did:

Uninstalled everything even remotely connected to postfix / courier

Reinstalled postfix using the ubuntu documentation.
Reinstalled courier-imap

Changed roundcube default server to localhost... think i might try and make it my actual domain, but for now this works.

Weird-*** /var/mail dir is still there.. going to keep it for the sake of ... not busting anything up.

Thanks for your reply anyway

Cya!

---

