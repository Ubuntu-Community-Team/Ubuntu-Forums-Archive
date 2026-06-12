---
title: "Was I Hacked? My Home IP Bought a Ton of Stuff on Paypal!"
date: 2014-02-26
forum: Security
---

### Post by SedaliaSteve on 2014-02-26
Forgive me if this has been previously discussed but I just found I'm liable for a lot of money. Over a several day period my Paypal account purchased a lot of stuff I never heard about. I worked with my bank and credit card company and they are good. Paypal denied all my disputes and wants the money. They claimed that all these purchases came from my home IP. I have a laptop and desktop running 12.04. I believe I've only used my laptop for PP. The setup then was a DSL with a firewall turned on but I didn't have it turned on on my machines. My laptop is set to do various remote logins out to the desktop but I had turned off all methods into my laptop including SSH and telnet.

My password for the laptop is fairly strong and I had removed all other logins, including guest. My Paypal password is also different. The only other people in the house are my wife and mother-in-law who are both technophobes and use Windows but I've never used their machines for financial transactions.

I do keep a Truecrypt disk on my laptop that does have passwords in it but it doesn't automount and I only use it when needed since all my money related accounts have different strong passwords that I can't remember.

Once this happened I started playing with the local firewall and loaded several malware scanners but they found nothing.

I'm going into detail since Paypal claims that they can detect IP spoofing. If they're full of it I'd appreciate any links for this since I'm in a fight. I'm going to check  /var/log/auth.log and see if any new users has appeared. Have there been cases of keyboards loggers. I'm just trying to figure out how a password could be captured on a 12.04 machine and then be used from the laptop or from within my router if it really was my home IP.

Steve

---

### Post by SeijiSensei on 2014-02-26
Do you use a wifi router?  Is it running WPA2 or WEP? 

This would be a complicated case of identity theft, though.  Someone would have to obtain your PayPal password, then park a car outside your house, break into your router, and start using your PayPal credentials.  Not impossible, but not too likely either.

I'd start with the more critical issue.  How did this person obtain the password to your PayPal account?

---

### Post by thnewguy on 2014-02-26
Thee are lots of ways to break into a computer, even remotely. If that is what happened here the less important issue is not how it happened, but what to do about it. This is damage control time.

As for whether the purchase originated at your IP address, there are a few things to consider...
1. Is your home IP static? If it is dynamic, then how would PayPal know what your home IP address is? On the other hand, if it is static, and someone has your PayPal password, chances are the person who made the purchases is in your immediate region. Or using you as a proxy.

2. It is possible to detected a spoofed IP address, but the odds of a company as notoriously bad at technology as PayPal actually detecting a spoofed address seems unlikely. Chances are the customer support person was bluffing. Call them on it and demand evidence the purchase came from your IP and that it was not spoofed.

3. It may be that an attacker got into your machine and is using your own (local) login credentials to get your PayPal account and use your machine as a proxy. I recommend doing two things at this point. Create an image of your computer(s) for evidence later and then do a fresh installation to wipe out any backdoors. Clonezilla's live disc is a good imaging tool for this sort of thing.

4. Factory reset and patch the router, those are often a weak link in the network and a good way to attack your local machines.

5. Change your PayPal password, preferably from another computer.

6. i recommend you stop hunting for evidence for the time being. Focus on getting things locked down (fresh installations, changed passwords). Go back later and wonder about the how/why. Right now you need to lock down your systems so this stops happening and get all the evidence PayPal has against you.

---

### Post by kurt18947 on 2014-02-26
I feel for Sedalia Steve, I always worry about the same thing happening to me.  A couple thoughts I have - 

Are Steve's Ebay & PayPal passwords the same?  I think they often are, or at least anyone possessing an Ebay username & password can log onto that person's PayPal account.

Where were the goods shipped to?

---

### Post by CharlesA on 2014-02-26
Do you have VNC enabled at all?

If they can confirm what IP address the purchases were made from and it is your IP address, I think you are out of luck.

The best thing you can do is follow the advice of the above posters - check router security, and check the security of your PCs too.

---

### Post by fugu2 on 2014-02-26
Where the charges sent to your card/bank or was it someone elses stolen card? 
There are so many possibilities without any evidence it will be hard to trackdown. 2 other ideas I can think of off the top of my head are DNS poisoning and XSS/CSRF.
I would think CSRF probably has a slightly higher probability to make it seem like it came from your IPADDR.

EDIT:
firefox has an addon 'RequestPolicy' that can help minimize CSRF but may be a pain to learn for some ppl.

---

### Post by bashiergui on 2014-02-26
Are you sure this isn't a scam? Did Paypal contact you? How? Did you contact them by responding to an email or did you use the contact information on their website? 

Use their website and contact them through that to verify this is actually for real.

Seems fishy to me.

Regardless, what happens if you don't pay? They cancel your account? Big deal, make a new one.

---

### Post by bashiergui on 2014-02-26
Upon further thought...

Your Paypal account is attached to a credit card or bank account. You said they're good, so I presume they reversed the charges? I don't get why your credit card/bank isn't handling the dispute with Paypal.

---

### Post by CharlesA on 2014-02-26
+1 to bashiergui. Paypal phishing emails are just plain insane.

---

### Post by SedaliaSteve on 2014-02-27
Thanks for all your suggestions. Some of the more obvious are out. I live out in the country and have only one neighbor within range and he doesn't own a computer. This went on over 2 to 3 days so I would have noticed somebody hanging out to leach off my wifi. This is not some phishing somebody actually got into my paypal account. I keep a bank account, credit card and have a Bill Me Later set up. I need the bank account since I sometimes sell stuff. I had the default order set to credit card, bank, bill me later. I'm set up with my credit cards that they notify me immediately when large purchases are made. They also look for strange patterns and deny/call me if anything strange is going on. The order was reversed to Bill Me Later, bank, credit card. The first purchases cleaned out the Bill Me Later and a balance I had sitting there from Xmas sales. Then to the bank and then to the credit card people who called me. By then I was screwed. I straightened it out with the bank and credit card company and didn't think it was my paypal account since it showed no activity.

I went in to work to use my work computer since I know it is secure. (We're an encryption security company and have high paid IT since pirates do not like us.) I logged into all the accounts and changed the passwords to tougher ones. I missed the changing of payment order but saw no profile changes. The next day the 8 transactions showed up in paypal and I opened disputes. A few days later they were denied and they gave me an address to request data they used to decide. After two weeks and no replay I called. A thoroughly unpleasant person was the one who told me it was my home IP also refused to provide any data showing that so they might be full of it. They also said they want it all. One thing that is strange is that I never received emails of purchases shipping info or anything. I experimented with paypal. I can do a lot of info changes without notification. Password change does it so mine wasn't changed. It makes me wonder if my gmail was hackd. My PP, ebay & gmail all have very different passwords. Gmail password couldn't be changed since I have multistep using my phone. I just wonder where all the emails were. I found one from superbit.hk in my spam label but no other signs.

When I made the call I was at work. Now I'm home and checking my systems. My desktop has never been used for financial stuff. It has loads of tech bookmarks like here but exists as a music server and samba shares for backup. Every so often I compress the backups and stick them into Truecrypt disks that are unmounted. Because of its music serving it is open to every kind of remote desktop including VNC. My laptop is different. I only have remote clients not servers and nothing is shared. I could not get any kind of connection to it. The users have no new or strange ones and the Auth logs look good. I'll probably clone it onto the desktop and do a clean install. Before I do anything drastic any traces I should look for?

I think Paypal is blowing smoke about their omniscient detection of IP spoofing and whether they even validated that far. As I go into copying my demands to Better Business Bureau, Attorneys General, police reports and all, I am not hopeful. I spend time reading logs and give me time I can fake one and so can PP. They really are a Tony Soprano company. "I got hacked.", "Screw you, pay us."

Steve

---

### Post by CharlesA on 2014-02-27
How is VNC set up? Does it allow remote access from outside your local network?

FWIW, Any time I have used Paypal, they send me a confirmation email, but I rarely use ebay so I dunno if the accounts are linked or anything. Do you have any records of puchases in ebay or elsewhere?

---

### Post by sandyd on 2014-02-27
This is an issue with paypal and you - not much we can do here to help.

Thread Closed.

---

