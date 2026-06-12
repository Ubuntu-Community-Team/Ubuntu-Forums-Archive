---
title: "How do I completely avoid Google ?"
date: 2019-09-27
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2019-09-27
I have 92 accounts of various forums and I used Gmail as the registration email address.

I have removed all traces of Google from my browser and using [https://www.startpage.com/](https://www.startpage.com/)

instead.  All is fine but now.


Q1) Which email service should I use instead of Gmail ?

Q2) Any tips about how to change registration email of 92 accounts ?

---

### Post by Rubi1200 on 2019-09-27
Hi,

can't answer Q2 but for Q1 take a look here:
[https://www.privacytools.io/providers/email/](https://www.privacytools.io/providers/email/)

---

### Post by linuxyogi on 2019-09-27
> **Rubi1200 said:**
> Hi,

can't answer Q2 but for Q1 take a look here:
[https://www.privacytools.io/providers/email/](https://www.privacytools.io/providers/email/)

Thanks for that link but I have to find a way to change those accounts.

---

### Post by poorguy on 2019-09-27
I use ***Startpage*** and it's OK although doesn't have the resources that ***Google*** does, I guess that's the price you pay to have the privacy ***Startpage*** claim's to give.

---

### Post by linuxyogi on 2019-09-27
> **poorguy said:**
> I use ***Startpage*** and it's OK although doesn't have the resources that ***Google*** does, I guess that's the price you pay to have the privacy ***Startpage*** claim's to give.

One thing that I have noticed is the auto complete / suggestions are a bit lacking.

I am satisfied with the results though.

---

### Post by TheFu on 2019-09-27
I have hundreds of different email aliases and accounts.
What is the purpose of each email address?  That depends.  Different, unique, accounts are used for any account that is connected in any way to money.  I couldn't tell you the email account used for my brokerage accounts. It is long, random.  My login userid for each broker is long and random too. 
I have 6 different bank accounts specifically not tied together and not at the same banks. Most are for different businesses, which is why they aren't at the same banks. Each has a different, long, random, email address.
I have some general purpose accounts for places like here which are used at about 10 unimportant sites.  They are xxxx222, xxxx333, xxxx4444, ... you get the idea.
For dealings with my Govt, I use gmail. Don't want to seem too odd.  I have a few different gmail accounts, but these are never used from the same Linux login.  They are separate.  One and only 1 is tied to my real name. It is not tied to Android in anyway.
I have a few other accounts which I strive to keep anonymous. I've never, ever, accessed them without either TOR or a VPN exit node in another country.  I use these to pay for services using gift cards - like a VPN provider.

If you want to stop using google, get a list of google IP networks and setup firewall rules which block them.  ALL OF THEM.  Also, setup DNS based blocks - there are probably over 1,000 necessary.
Stop emailing anyone with a gmail address and you'll probably want to check every domain for an MX record that points to gmail/google as well.  Something like pi-hole will help at home with this, but whenever your devices are outside the home network, these blocks wouldn't be active.

Be certain to block google's DNS servers too.  DNS is an easy way they can track devices even for non-google and non-google Analytics and non-Google advertising locations.

Never forget that lots of webmasters will be providing google with data, without asking you.  Google-analytics is really easy to deploy and provides the webmaster lots of information, while also providing google all that same information (and more). Selling out their visitors is easy.  Setting up your own analytics isn't nearly as easy.

I don't do everything above. Even for me, it is too hard.  Some family and some friends have decided to use gmail and google stuff for all sorts of things.  They are unhappy that I refuse to tweet or use facebook and insta-whatver and whatsapp already. Cutting them off at gmail was just too much for them.  They see me like that auto mechanic who thinks anyone running Mobile1 oil is stupid, since Amsoil and Castroil are clearly so much better.

It just isn't important to them, when they have 20 other non-computer details daily in their lives to handle.

How do you move a bunch of email settings in other websites off gmail?  1 account at a time.  Get a password manager, KeepassXC perhaps, and start using it.  Do 10-20 accounts a day and in a few months, you'll have them all switched over.  In the time I spent writing this, I bet 20 accounts could have been changed.

Since I run email servers, having lots and lots of accounts/aliases is really easy.  That isn't so easy for most people.  Let's think about the minimal number of different email accounts needed.
[LIST]
[*]Family
[*]Work
[*]Social media
[*]online shopping - primary retailer (AMZ?)
[*]online shopping - general (everyone except the primary)
[*]Banking
[*]Brokerage
[*]Spamming/forums
[/LIST]
Then be certain to use the [email]name+site@example.com[/email] capabilities that most email providers support.
Never mix the money-connected things. Each is a risk.  If the same email address is used for a bank that is used for some random other retailer, when that retailer gets hacked, they now have half of your banking credentials.

Oh ... and any sites which force password reset questions or extra login questions - be certain to answer with gibberish, never the truth.  Keep the lies for those answers inside your password manager.  
Mother's Maiden Name: eb6f46f1ef03db46f20e4bfa530796aebc5b5 
High School Mascot: 9eadbcd7ec16f4e5961ad2035c0228de7c2 
Password managers should be able to create better random answers.

Guess those attackers.

And definitely use 2FA whenever it is supported with a hardware key solution. Avoid the smartphone 2FA methods.

---

### Post by poorguy on 2019-09-27
> **linuxyogi said:**
> One thing that I have noticed is the auto complete / suggestions are a bit lacking.

I am satisfied with the results though.

I've no complaints.

---

### Post by TheFu on 2019-09-27
And be certain to login to each email address at least once every 3 months.

---

### Post by rbmorse on 2019-09-27
> **TheFu said:**
> 
 ... and any sites which force password reset questions or extra login questions - be certain to answer with gibberish, never the truth.  Keep the lies for those answers inside your password manager.  
Mother's Maiden Name: eb6f46f1ef03db46f20e4bfa530796aebc5b5 
High School Mascot: 9eadbcd7ec16f4e5961ad2035c0228de7c2 
Password managers should be able to create better random answers.


This is brilliant and not something I had realized before.  Thank you, sir.  You've made a whole day's worth of browsing worthwhile.

---

### Post by TheFu on 2019-09-27
> **rbmorse said:**
> This is brilliant and not something I had realized before.  Thank you, sir.  You've made a whole day's worth of browsing worthwhile.

Password managers are useful for all sorts of things.  [https://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager](https://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager)  I have a scan of my current passport stored inside my password manager, for example.  It isn't just for passwords.

---

### Post by cruzer001 on 2019-09-28
@TheFu
Thanks for this too.
I do not keep my most sensitive passwords on my computer, but in my desk drawer.  Time to rethink this.

---

### Post by TheFu on 2019-09-28
> **cruzer001 said:**
> @TheFu
Thanks for this too.
I do not keep my most sensitive passwords on my computer, but in my desk drawer.  Time to rethink this.

Glad it is helping someone.
 
 **NEVER write down the entire password**. Treat the parts written down better than you treat credit cards. Don't leave them on a sticky note.

laptop:   {something you know}+d2035T T%0228de7c2 
desktop:  {something you know}+d7ec16  f4e5KP@#961

Just make certain that the "something you know" doesn't have a clear pattern, if 2 passwords get cracked, it isn't the same and it is also sufficiently long.  At least 20 characters, total length.

Logins that aren't for devices you sit behind or hold in your hands, should be in the password manager, as long a allowed, as complex as allowed and using some sort of U2F or other 2FA that isn't tied to a cell phone.

---

### Post by Skaperen on 2019-09-30
the "something you know" part can be a long wordy phrase you can remember, such as words from a song, quotes from the bible, etc.  then take the 2nd letter of each word.  then add the gibberish to it.

people wonder how i can remember the 35 characters for my disk encryption password.

take the host names of various google services and plug in an address of 127.0.0.1 or 10.20.30.40 or 44.44.44.44 for them, or some such non-broadcast address that won't go anywhere.  be sure to include their DNS servers ... ns1.google.com, ns2.google.com, ns3.google.com, and ns4.google.com.

---

