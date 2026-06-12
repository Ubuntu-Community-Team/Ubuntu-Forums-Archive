---
title: "Need guidance on:  new email provider; personal domain for persistent email addresses"
date: 2018-12-18
forum: Ubuntu, Linux and OS Chat
---

### Post by cmetzler on 2018-12-18
Hi folks.  Executive summary of what I'm looking for:

1.  I want to find a reasonably trustworthy email service that allows IMAP connections so I can pull my email down using fetchmail and store it locally, deleting it from the remote server, rather than keeping it there.  I need recommendations.

2.  Once I've found that service and gotten things working, I want to obtain a personal domain and arrange for email forwarding at that domain, so that all email sent to my_username@my-personal-domain ends up at my_username@the-email-service-i-just-obtained.  And I want that to be changeable, so that if I switch email services down the road, I can simply point my_username@my-personal-domain to the new email service rather than the old one, and thus not have to tell folks to change the email address they use for me.  I want it to be transparent to the folks I interact with, the mailing lists I'm on, etc.  I need to be pointed in the right direction on this.

=====

ISSUE #1:  changing email services.

The ISP we have used since 2001 appears to be circling the drain.  They recently sent out a notice saying they'd no longer be providing all hosted services, including email, starting at the end of this month.  So, we need to find a new email service.

I really don't want to have all my emails from 1991-2018 stored and backed-up locally, and then starting with 2019 stored and backed up on some third-party service.  Right now I use fetchmail to pull down my email (via IMAP) from my ISP and pass it to the local SMTP server for delivery.  I'd love to continue to do this.

Protonmail was recommended to me, and I've liked what I've read about their dedication to security/privacy/etc.  But their support for Linux seems to be in early days.  In particular, supposedly one needs their Linux bridge (which is still in beta), which in turn can be obtained only by purchasing service.  I don't want to buy their service and then find out the bridge doesn't do what I need and I can't establish a good/compliant IMAP connection with them.

Does anyone have any ideas on good email providers?

=========

ISSUE #2:  a personal domain for persistent email addresses

Once I get the new email service established, we're going to have to tell everyone our new addresses, change mailing list subscriptions, email address for web registrations, etc. to infinity.  This is going to suck.  I don't want for us to have to do it again two or three or seven years down the road.

It struck me that one way to minimize the likelihood of having to do this again is to register a personal domain and keep it up to date, with email addresses at that personal domain forwarding to whatever email service we're using.  But I'm not entirely sure what I need to do to make this happen.  Every time I've wandered over to Network Solutions or GoDaddy's webpages to look at domain registration, there's a ton of additional stuff they seem to want to sell you, and it's not clear what's needed and what's not.  Furthermore, there's no information on what you need to do to set up mail forwarding or whatever.  I know this can't be a new idea -- other people have to have done this before -- but I've googled and haven't found a page that's straightforward enough on what I need to do.

Can anyone point me to decent quality docs/HOWTOs/whatever on how I can go about making this happen?  If such really doesn't exist, then I guess I need any guidance folks have the time for.

Thanks very, very much.

---

### Post by TheFu on 2018-12-18
If all you want is an email forwarding service, then get one of those.  Most Universities do that for their alumni for free.

If you always want to pull email local and leave nothing on the server, then you want POP3S, not IMAPS.  IMAP is designed to leave the email on a central server. POP3 forces the email to be removed.

Protonmail is a value-add email solution, but because they use added encryption, it really doesn't make sense to me to try and pull the email to a local machine, breaking their "value add" proposition.  I have a few protonmail accounts, just the free ones.  I don't think those allow normal email clients, so their webmail interface is it for the free accounts.

Please, be very careful dealing with the two companies you've mentioned.  Do your homework to see why they may not be the best options.  Google found this list: [https://www.techradar.com/news/best-email-hosting-providers](https://www.techradar.com/news/best-email-hosting-providers) and [https://www.namecheap.com/hosting/email.aspx](https://www.namecheap.com/hosting/email.aspx)

---

### Post by cmetzler on 2018-12-19
> **TheFu said:**
> If all you want is an email forwarding service, then get one of those.  Most Universities do that for their alumni for free.
That's all I want now, but I don't know that that's all I'll want in the future.

> 
If you always want to pull email local and leave nothing on the server, then you want POP3S, not IMAPS.  IMAP is designed to leave the email on a central server. POP3 forces the email to be removed.

IMAP does have commands in the protocol for deleting from the server; I know because that's what fetchmail has been doing for me for 17 years.  :)  But you're right that I don't need to restrict myself to IMAPS going forward; I was absent-mindedly repeating what I've done up to now.

> 
Protonmail is a value-add email solution, but because they use added encryption, it really doesn't make sense to me to try and pull the email to a local machine, breaking their "value add" proposition.

That's a good point.

> 
Please, be very careful dealing with the two companies you've mentioned.  Do your homework to see why they may not be the best options.  Google found this list: [https://www.techradar.com/news/best-email-hosting-providers](https://www.techradar.com/news/best-email-hosting-providers) and [https://www.namecheap.com/hosting/email.aspx](https://www.namecheap.com/hosting/email.aspx)
One of those I'd seen, but not the other.  Thanks much!

---

