---
title: "postfix and virtual accounts for $mydomain"
date: 2006-09-12
forum: Server Platforms
---

### Post by Frank-Hamersley on 2006-09-12
G'day,

FWICT postfix does not allow the creation of $virtual_mailbox_maps entries for the main system domain shown in $mydomain!

Is there another way to skin this cat?  Basically I want to have the system accept (via SMTP) and deliver (via POP3) emails for an account like "admin@mydomain.net" without having to create a physical login account.

BTW I want to achieve this with Breezy standard - ie only patches issued under the LTS programme - no bleeding edge packages.

Any ideas? Cheers Frank.

---

### Post by sclough on 2006-09-12
I'll have to check my postfix setup, but I'm pretty sure you can.  I use virtual accounts rather than real accounts and it works fine with postfix.  I have several domains hosted on the machine, but the machine's domain is also hosted there.  I'll check my postfix config file and see if it helps.

---

### Post by Frank-Hamersley on 2006-09-13
Thanks for the prompt response...

I got to thinkin'...could this be achieved by establishing a bogus virtual domain like "virtual.mydomain.net" with virtual account "admin@virtual.mydomain.net" and then use aliases on the "real" domain to map "admin@mydomain.net" to the virtual account. Might suck it and see later tonight!

Seems FSB (fully sick bro) ... but if it works hey!

Cheers Frank.

---

### Post by sclough on 2006-09-15
I assume you've figured out you just set mydomain to something like localhost.localdomain and set your real domain as a virtual domain.

---

### Post by Frank-Hamersley on 2006-09-18
That is the opposite of my expectation - which is that the "real" domain would be $mydomain and the virtual domain would be (perhaps a sub)domain of that. Would both configs perform regardless?

I was wanting to make sure that all email emanating from either domain were attributed to the real domain as a source ie. the virtual domain remains totally invisible.  Is that a feasible goal?

---

### Post by sclough on 2006-09-19
Well, I guess I need to clearly understand what you are trying to do.  I assume you want virtual accounts for email.  I.e. there is no actual Linux account for each user on the box that get's email.  Is that correct?

Also, are you hosting email for multiple domains, or just one?  Do you want to host email for subdomains or are you going down that road trying to get it to work?

---

### Post by akutz on 2006-09-19
There is a great how to for this here [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

### Post by Child of Wonder on 2006-09-19
I posted a guide on how to do this a little while back.

[http://www.linuxquestions.org/questions/showthread.php?t=474576](http://www.linuxquestions.org/questions/showthread.php?t=474576)

---

### Post by sclough on 2006-09-20
Let us know if you need more information.  Once change I made on my recent server upgrade was to switch from hashed flat files (the normal way) to using mysql to store postfix accounts.  I think it's much easier to manage and, for what I do, it's not any slower, especially since right out the box MySQL is typically configured for extremely fast select queries and considing your email tables are going to be pretty small.

---

### Post by Frank-Hamersley on 2006-09-20
Thanks for the offer ... as this is a very small site (will be less than 20 email addresses - real and virtual) I had wanted to keep it all very low tech.  My main interest was in understanding the postfix/courier-pop packages.  Haven't had time to hack for the last few days so nothing to report yet.

Cheers, Frank.

---

