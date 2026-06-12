---
title: "Spammers using my email address"
date: 2008-04-14
forum: Security Discussions
---

### Post by whitefort on 2008-04-14
Hi.

I logged on this morning to find 127 non-deliverable emails bounced back to my mailbox.

Bad enough, but what's worse is that I didn't send any of them.

Obviously spammers are spoofing my address on the junk they're sending out.

My first question is, can I actually do anything about this, or do I just have to wait for it to eventually pass?

In the meantime, I've set up a filter in Thunderbird so that they all go into a little folder of their own, so that my genuine emails don't get lost among all the rubbish.

Hmmm.. in the time it's taken to type this, I've had another half-dozen of these bounced spams.

Any advice will be gratefully received!

---

### Post by hyper_ch on 2008-04-14
if you have your own domain and operate your own mailserver or have at least access to your webhost where you can setup countless email addresses, then I have a suggestion for you...

Otherwise you'll just have to wait...

---

### Post by whitefort on 2008-04-14
Hi,

yes, i can set up a lot of email addresses, though I'd prefer to keep the email address I normally use.

It's starting to tail off now (for a while anyway).  So far, I've had around 200 messages bounced at me, and a couple of angry notes from people who think they're replying to the spammer.

Makes me wonder how many of these things went out with my name on them, if so many bounced.

I always use Spamcop to report every spam that arrives in my letterbox, and recently got word that I'd had a few spammer accounts deactivated.  i'm wondering if this is some sort of revenge or something.

---

### Post by hyper_ch on 2008-04-14
as I operate my own server I have written myself a small script where I can just generate a new email address (the left side of the @) and then it will be created on the system in a manner, that everything goes into the same email box.

So, when I need to give my email for a website (e.g.  [http://www.supercoolwebsite.com](http://www.supercoolwebsite.com)) then I just generate myself a valid email address looking like this: [www.supercoolwebsite.com@MYDOMAIN.COM](www.supercoolwebsite.com@MYDOMAIN.COM)

The mailserver is then that way configured, that it accepts only valid, existing email addresse... (no wildcards). So if someone forges an email address then
(a) it will not exist and my mailserver will refuse to accept the "return" email
(b) it will exist because [www.supercoolwebsite.com](www.supercoolwebsite.com) has somehow leaked my email address --> but then I will see that and I can delete that email address again.

That's how I do it and it works well :)

---

### Post by aysiu on 2008-04-14
This happened to me, and I did a little Googling around and found the best thing to do is just ride it out. After a while, they'll get tired of spoofing you and move on to someone else.

If you're using a catch-all account... don't. That also helps.

---

