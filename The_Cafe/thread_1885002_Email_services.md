---
title: "Email services"
date: 2011-11-22
forum: The Cafe
---

### Post by alphaamanitin on 2011-11-22
Hello Ubuntu Community,

I have recently became sick of gmail trying to trick me into giving me a phone number to associate with my email account.  I am looking into find an email service that offers the storage space and powerful tools that gmail offers, with more privacy.  Does anyone know such a service?  I tried GMX but found it lacking.  My other thought is to rent a low-cost server and set up and email server on it.  But then I run into the same problem, a name, phone number, and with that, even an address and credit card number associated with that email.   I could encrypt the emails, but that still doesn't solve the issue.  I am not concerned with some one accessing my emails, I am sure the latest phylogenetic tree of the Boletineae is really exciting to two or three other people, but that my name, phone number, etc is associated with the email.  

I dread the day gmail tells me I have to put in a phone number to access my email.  Thoughts?

AlphaA

---

### Post by WasMeHere on 2011-11-22
Hi alphaamanitin,

One option is to access gmail via Thunderbird
```
sudo apt-get install thunderbird
```
It can handle imap access, and you don't see any ads at all. Tbird can easily manage several email accounts. And when you are travelling without your computer, you still have the emails available via the web browser.

Have fun finding out :-)
Olle

---

### Post by alphaamanitin on 2011-11-22
I would do that, and did think about it, but it doesn't solve the problem that I am worried about.  I am sure, that at some point, google will demand I give them my phone number to access my account.  This happened to my gf.  They said that there was suspicious activity and would not give her access without her phone number.  Which is stupid.  She finally had to break down and give her phone number because the account had emails from work in it.  After she accessed it I looked at the access logs and could not find an unknown IP address, so not sure what this suspicious activity google found was.

AlphaA

---

### Post by WasMeHere on 2011-11-22
That sounds bad. Are you sure it was Google that asked, not someone pretending to be Google? If it happens to me, I would also be worried, and consider using another service for important (maybe all) email conversation, even if it would cost money or be limited in size.

Anyway, Tbird can archive the mail locally, even if you use imap, so you won't have to worry about losing old mails.

I have an account at my internet service provider, I guess most ISPs include accounts will a small storage space for their customers.

---

### Post by alphaamanitin on 2011-11-22
I am sure that it was google.  About once a month when I log into my account and get a message to add my phone number.  At the very bottom of this message is a small link to continue on without entering my phone number.  My ISP offers an email service, but again my phone number, credit card, and address would be associated with that account.  

I think I might access my gmail via thunderbird just to make a back up of all my emails though.  I have about 4 gigs of emails in there.  I just want an account that doesn't ask for any identifying info like google does.  I mean, I accept that they will always ask for name, address and the like, but I always put in false information.  I just don't want an account that makes me nervous like gmail does.  

AlphaA

---

### Post by Docaltmed on 2011-11-22
I get that same message. They are ostensibly looking for a way that you can be sent your private account data in the event that you need to be sent a new password. That sort of thing.

An alternative, that I have done, is to give them a secondary email address where you can be contacted. You can just get a dummy account elsewhere, and use that.

I think it's probably stretching it to fear that your phone number will become part of the standard access requirements.

---

### Post by BrokenKingpin on 2011-11-22
> **Olle Wiklund said:**
> 
One option is to access gmail via Thunderbird

This is what I do. I haven't accessed my gmail account through a web browser in probably a year.

I have thought about moving away from gmail, but the integration with my calendar and Android phone are too good to give up. I am very conscious of the type of information I store in the "Google cloud" though, but that is the same for any online provider.

---

### Post by alphaamanitin on 2011-11-22
> **Docaltmed said:**
> I get that same message. They are ostensibly looking for a way that you can be sent your private account data in the event that you need to be sent a new password. That sort of thing.

An alternative, that I have done, is to give them a secondary email address where you can be contacted. You can just get a dummy account elsewhere, and use that.

I think it's probably stretching it to fear that your phone number will become part of the standard access requirements.

I have many email accounts, and I do have a back up email for gmail to send my password to.  I know my fear is most likely irrational, but that is my nature.  And as you might appreciate, it is easier to change email providers than change one's nature.  I also dislike my emails being stored on companies servers, so I do like the thunderbird option.  Then I get into the comparing the likelihoods of gmail's servers crashing and me losing emails or my hard drive failing.  Currently, I am looking at my HD failure as the more likely option.  

Thanks for the suggestion guys!  I think I might move to pulling all my emails off of the gmail servers immediately and go to thunderbird.  The biggest issue I have with that though is having to use multiple computers and carrying around my laptop in the area I live is not a viable option.  I am a grad student that walks to work through the worst part of the town I live in, so....

AlphaA

---

### Post by SavageWolf on 2011-11-22
I trust Google enough that I would give them my phone number, if I had a phone.

Anyway, I see no problem in this, how would they act if they used a fingerprint scanner (assuming that technology and all that worked and everything) to validate your account instead of a password?

Also, the access logs only log logins, yes? So it's possible that someone set up a "brute force" password breaker thing on her account, causing Google to block it.

---

### Post by alphaamanitin on 2011-11-22
No google stated that there was suspicious activity from her account.  I don't trust any company that I am not actively in a business arrangement with to give them my phone number.  I do not consider using free services a business arrangement.  

Would never use any service that wanted to use any sort of biometric authentication methods.  Though I would be more open to a fingerprint (despite the fact that fingerprint scanners suck, look up the Myth Busters work on them) than DNA though.

AlphaA

---

### Post by lisati on 2011-11-22
There are pros and cons to all the email providers I've used over, including Hotmail, Yahoo, Gmail, GMX, and a couple of different ISPs. The same can be said for email clients. 

The server for my current primary email provider sits under a table at the end of my couch. The main benefit is that I have a greater control over stuff like spam filtering and the information that's needed to access it. The downside is that apart from the monetary cost for making the necessary arrangements with my ISP there have been things to learn, such as basic security, access control, and how best to keep the troublemakers out.

---

### Post by alphaamanitin on 2011-11-22
I would really love to set up my own server, but sadly my ISO prohibits servers without a business plan, which cost a little more, and as a biology graduate student I cannot afford it.  I would do it anyway, but I read up on people who did so on the same ISP and they cut off port access to your server as they notice activity, and the block the common ports for email servers and the like by default.  

AlphaA

---

### Post by ubupirate on 2011-11-22
> **alphaamanitin said:**
> I have recently became sick of gmail trying to trick me into giving me a phone number to associate with my email account.

I only get that message once every 6 months, lol.

---

### Post by alphaamanitin on 2011-11-22
I'm jealous!  I get it once a month.

AlphaA

---

### Post by Dry Lips on 2011-11-22
I'm going to quote what I wrote in another thread:

[>  ]("http://lavabit.com/")[http://lavabit.com]("http://lavabit.com/") has the best privacy policy I've seen among all providers
of free webmail. They offer traditional webmail, in addition to pop3/imap.
[...]
More propaganda for Lavabit:
- Even their admins cannot read your emails.
- All logfiles are deleted within 7 days
-Their servers use CentOS 4.8.

Finally, check this out:
"[B]Lavabit is in debt to the open source code projects we rely upon. 
We  hope to someday repay this debt by releasing our e-mail server 
back to  the community[/B]."


---

### Post by alphaamanitin on 2011-11-22
It only ebcrypts emails if you pay...

AlphaA

---

### Post by Dry Lips on 2011-11-22
> **alphaamanitin said:**
> It only ebcrypts emails if you pay...

AlphaA

If you use a free email provider and in addition use Thunderbird plus the
addon "Enigmail" (it's in the repos); then you have free, encrypted email.

It's a win-win situation! :D

---

