---
title: "Postfix aliases forward rule has me confounded."
date: 2012-08-14
forum: Server Platforms
---

### Post by pl1ght on 2012-08-14
I have a fully working/configured /etc/aliases file.  I have one email address that forwards email to 5 different users.  The oddity I am having is that while it sends to these 5 users listed for this email, it then forwards to a sixth user inbox that I can not track down where this user is configured to receive forwarded emails from.

So basically  /etc/aliases for this addy looks like this

#itba
itba: [email]user1@asdf.net[/email] [email]user2@asdf.net[/email] [email]user3@asdf.net[/email] [email]user4@asdf.net[/email] [email]user5@asdf.net[/email]


When an email is sent to [email]itba@asdf.net[/email]  all of those 5 users receive it just fine, but also a 6th user, [email]user6@asdf.net[/email], gets a copy.  I have checked all of the users fowarding rules to see if one of them is forwarding it, and they arent. I can also see the forward in the logs as

to=<user6@asdf.net>, orig_to=<itba@asdf.net>   (forwarded as 2BD4E38113)


Im sure I am missing something stupid and not thinking 'outside of the box' enough but any insight on where within postfix i can try to track down where this is being forwarded from would be appreciated it.  I am somewhat of a *nix mail admin noob, and think i have run out of personal resources to troubleshoot this.


Thanks!

---

### Post by pl1ght on 2012-08-14
nevermind!  Apparently all it took was me typing out my whole problem and then re-reading to look somewhere else.  Looks like i found my answer by tracking down that forward message ID in maillog.  One of our java report systems had that address set in it to forward to the email i was looking for.  Thanks anyway!

---

