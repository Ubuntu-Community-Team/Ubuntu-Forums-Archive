---
title: "Security Error in google chrome on google sites"
date: 2010-01-30
forum: Security
---

### Post by Crazy K on 2010-01-30
I recently just got my computer back up and running, and when I went to check my gmail and google wave account I was graced with this annoying prompt: [http://img.photobucket.com/albums/v434/CrazyK12/Screenshot.png](http://img.photobucket.com/albums/v434/CrazyK12/Screenshot.png)

And when I click on the "Help Me Understand" area it says this: 

> When you connect to a secure website, the server hosting that site presents your browser with something called a "certificate" to verify its identity. This certificate contains identity information, such as the address of the website, which is verified by a third party that your computer trusts. By checking that the address in the certificate matches the address of the website, it is possible to verify that you are securely communicating with the website you intended, and not a third party (such as an attacker on your network).

In this case, the certificate presented to your browser has been revoked by its issuer. This usually means that the integrity of this certificate has been compromised, and that the certificate should not be trusted. You absolutely should not proceed past this point.

Is it possible that there is a security risk? I've always used https before my gmail and google waves, as it's usually quicker.

But yeah, it works fine in firefox, but I favor google chrome over firefox at the moment.

Oh, and one more thing. I can view google.com just fine.

---

### Post by Jive Turkey on 2010-01-30
yup there could be a risk.  Namely a man in the middle attack, where someone is sitting between you and mail.google.com and is collecting the info being sent from either side before forwarding it along.

Another type of attack might be that someone is straight up spoofing google's mailserver.

It could also just be a mistake.  I'm not really sure what you should or shouldn't do about it though.

---

### Post by Crazy K on 2010-01-30
I'm able to access gmail and google wave in firefox by using https. Should I worry about that? Or am I safe using Firefox? 

I'm not sure if this has anything to do with this problem. But I had to put my main HDD into another computer. (motherboard for my main comp died or something, so I used an old computer and just put my main HDD into it. It worked)

Could that be a reason? I really don't see how it would, but I want to throw everything out there just in case.

Btw, I just checked out gmail on chrome, and it loaded up. I didn't sign into my account though. 

Also one other thing. When I put my HDD into one of my other computers, I installed some updates, one was for google chrome. A while after the security risk mess I was told by the package manager that there was outdated info or something and that I should check for updates, I did and a mess of stuff was there. I'm guessing that's due to my hiatus on using Ubuntu (I had to use a neighbors comp for like a month until I got myself a working comp). Anyways, I downloaded the updates. Just now google chrome lets me view gmail. And Google Wave works fine too. 

Sorry for the lengthy response. I just like to explain myself.

---

