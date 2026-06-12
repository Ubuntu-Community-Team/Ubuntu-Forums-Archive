---
title: "My email server marked as spam?"
date: 2009-03-09
forum: Server Platforms
---

### Post by Dr Small on 2009-03-09
I just tried sending out an email to a friend, and got this response back from my server:
> This is the mail system at host mycroftserver.homelinux.org.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<friend@domain.com>: host smtp.secureserver.net[64.202.166.12] said:
    553 Spam Attack PREMIER INFORMATION -zb 70.41.142.209.
    <http://unblock.secureserver.net/?ip=70.41.142.*> (in reply to RCPT TO
    command)


My server requires authentication to relay mail through my SMTP server (implemented and tested) and I have never sent spam/spam related messages to this friend/domain.

I host my subdomain at DynDNS.org and have sent lots of mail to this friend at this email before. What should I do?

---

### Post by solitaire on 2009-03-09
Might be something as simple as your IP address being on a spam list (since you are using DynDNS i suspect your IP address is Dynamic not a fixed one) most ISPs get their dynamic IP range reported in bulk to anti-SPAM servers.

---

### Post by Dr Small on 2009-03-09
> **solitaire said:**
> Might be something as simple as your IP address being on a spam list (since you are using DynDNS i suspect your IP address is Dynamic not a fixed one) most ISPs get their dynamic IP range reported in bulk to anti-SPAM servers.
That's what it appears like. So, is there anything I can do to fix this? Because as you say, my IP is dynamic. It changes if I keep the modem off for 24 hours (happens on a few occasions).

---

### Post by solitaire on 2009-03-09
Only way (I think) is to get a Static IP address from your ISP. Or see if your ISP has a section of their IP range that's not black listed as spam.

---

### Post by Dr Small on 2009-03-09
> **solitaire said:**
> Only way (I think) is to get a Static IP address from your ISP. Or see if your ISP has a section of their IP range that's not black listed as spam.
That's so unlikely that I would go as far as to say that it's impossible. But, what about that link? What do you figure my odds would be of getting that IP range unblocked?
[http://unblock.secureserver.net/?ip=70.41.142.*](http://unblock.secureserver.net/?ip=70.41.142.*)

---

