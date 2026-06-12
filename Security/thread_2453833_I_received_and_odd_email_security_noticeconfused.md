---
title: "I received and odd email security notice:confused:"
date: 2020-11-17
forum: Security
---

### Post by rsteinmetz70112 on 2020-11-17
I received an odd email today purporting to be from a large national company, who we have done work for in the past. 
[LIST]
[*]The message identifies our company. 
[*]It identifies certain files related to some past projects that are claimed to be exposed on the Internet. 
[*]The domain is legit, the email addresses could be from that company. 
[*]All of the contact phone numbers are offshore.
[*]The information portion of the message looked like an email but it is an image, not text. 
[*]As far as we know this company was not involved in the projects identified but are projects we worked on.
[*]There is no information identifying the server by DNS or IP address.
[*]There is no information identifying the nature of the exposure like an open port or some protocol.
[/LIST]
I have in the past received notices from an ISP identifying open ports, but they included specific information about the issue.
:confused:

---

### Post by ActionParsnip on 2020-11-17
Check email headers and if SPF failed or passed. Check the location of the IP address. Check the WHOIS of the domain.

---

### Post by ActionParsnip on 2020-11-17
If in doubt, don't reply to the email but call the sender to see if they sent it or craft a new email to someone on the inside to see if they sent it.

---

### Post by SeijiSensei on 2020-11-18
Use the option in your mail client to show all the headers. Look at the Received entries and make sure the message came from it alleged source. First thing I do with any suspicious email is reveal all the headers. There may be SPF and DKIM headers that will provide useful clues as well.

---

### Post by rsteinmetz70112 on 2020-11-18
I did check the whois and the domain is legit, although it could be spoofed. I was thinking of sending something to the admin contact for the domain.

---

### Post by rsteinmetz70112 on 2020-11-18
> **rsteinmetz70112 said:**
> I did check the whois and the domain is legit, although it could be spoofed. I was thinking of sending something to the admin contact for the domain.

All of the phone numbers in the email are offshore, so I'm not sure who I'd get or if they were legit. The company is big enough that I don't have a clue what verifiable number I could call to get someone who would care.

---

### Post by SeijiSensei on 2020-11-18
Have you looked at the headers yet?

---

### Post by rsteinmetz70112 on 2020-11-18
> **ActionParsnip said:**
> Check email headers and if SPF failed or passed. Check the location of the IP address. Check the WHOIS of the domain.

OK the IP address 207.82.80.112 it seems to be  Mimecast Services Limited, and the mail was passed through prod.outlook.com
I don't think that tells me anything.

---

### Post by EuclideanCoffee on 2020-11-18
> **rsteinmetz70112 said:**
> OK the IP address 207.82.80.112 it seems to be  Mimecast Services Limited, and the mail was passed through prod.outlook.com
I don't think that tells me anything.

Are you certain it wasn't forwarded from Mimecast? Sometimes that header can become difficult to follow.

Without the full information, it's hard for us to provide much more advice. :(

---

### Post by DuckHook on 2020-11-18
When in doubt, treat it like it's a live hand grenade. If it turns out that you are over&#8209;reacting, the company in question will appreciate your abundance of caution. If the threat turns out to be real, you will have saved yourself a world of hurt.

You state: > **rsteinmetz70112 said:**
> …the email addresses could be from that company……so contact those email addresses. When you initiate clean virgin emails—vs clicking some "reply" button—you can be sure that it goes directly to that recipient. If you still question the veracity of the reply, then the next measure would be to simply contact your client's security department. I don't believe that any "large national company" will lightly wave off security threats these days.

---

### Post by rsteinmetz70112 on 2020-11-25
OK this has gotten weirder. Someone purporting to be from the company called and asked that we call them back.
I sent an email to the  domain administrative contact listed in the who is ICCAN database. I verified he is a real person in their Network Department.
WE'll see what hapens.

---

### Post by TheFu on 2020-11-25
> **rsteinmetz70112 said:**
> All of the phone numbers in the email are offshore, so I'm not sure who I'd get or if they were legit. The company is big enough that I don't have a clue what verifiable number I could call to get someone who would care.

TL;DR Check the full email headers.  [https://www.cmu.edu/iso/news/email-spoofing.html](https://www.cmu.edu/iso/news/email-spoofing.html) explains what to look for. Carnegie Mellon U is a reputable source.

Longer stuff ... 
You do business with a company that you don't have a telephone number and human to call? For anything that isn't specifically related to domain registration, DNS, or setting up computer servers, I wouldn't do business with a company like that.  I have a phone number for my ISP, my hosting providers, and other businesses.  No way would I call a number listed in an email. Go to the web site for the company.  Find the "Contact Us" page.  Call that number. Let them figure out where you should go.  Don't follow any link to the webpage. Type it in. For any company I do lots of business with, I have a personal contact name and number. We talk monthly or quarterly to be certain we are on the same page.

I'm a corporate officer for a company and get spearfishing emails all-the-time.  Got 6 this morning.  3 had viruses that my email server caught and dumped.  2 were claiming to be from Amazon with $100 gift cards sent to different accounts as a thank you. One claimed that someone had charged $1200 to a FedEx account (which I don't have).  The Amazon ones were pretty good, except the link for to "claim" the cards was clearly not Amazon in either email and the "TO" wasn't to any email that has been used with Amazon, ever. My amazon account is a random, long, email address, that only gets used with Amazon.

The Amazon gift cards sender email servers were running on Amazon's EC2 cloud, which isn't what corporate AMZ would use.  The source of the messages was a country in South America for one and Hungary for the other.

To make things a little more complicated, I was doing some domain and DNS work today, so transferring domains and DNS around. This required a few confirmation emails from multiple companies. But those use different email addresses for each and those addresses aren't used for anything else.

If you have just 1 email address, I feel sorry.  Having lots of addresses/aliases means I can tell whenever the source for an email is likely to be spam.  Mostly I use aliases that get filtered into specific folders in the imap server.  I have hundreds of aliases, but just a few actual email accounts.

What's really sad is that the email address my extended family has which has never been used with anyone else is getting about 50 spam emails each week. Someone or some-three people in the extended family has been hacked, but the list is too long to nail down who could be compromised.Anyone sending attachments with virus gets their subnet blocked from all all future web or email connections.



You probably need at least 3 different email addresses for personal stuff.
* Social
* Purchases
* Banking/Investing
Never mix those and don't use the purchase and banking accounts for anything social.  Ideally, you'd have a few social aliases, and a different email for each store and each bank and each investment account, never to be mixed.

If someone uses your social email claiming to be from a bank, you know immediately they are "bad guys."

Anyone sending attachments with a virus gets their subnet blocked from all all future web or email connections.

---

### Post by EuclideanCoffee on 2020-11-25
You likely have everything covered, but here's a short YouTube video that describes spear phishing. [https://www.youtube.com/watch?v=fZc2oXfz9Qs](https://www.youtube.com/watch?v=fZc2oXfz9Qs)

It is possible to be scammed or hacked outside of a computer.

---

### Post by DuckHook on 2020-11-25
@rsteinmetz70112

You are getting awesome advice from TheFu and EuclideanCoffee. Corporate officers whom I know have been willing to pay big money for such training.

Though TheFu has already covered it, I would only highlight/emphasize one thing: it seems to me that you are continuing to try contacting this big national company by responding to info sent to you. This is a fundamentally flawed approach. Your whole concern is that&#8212;or *ought* to be that&#8212;the info you are receiving is suspect. Therefore, you must *initiate* the detective work. **This means calling the office of this big national company and asking who their chief IT or chief security officer is.** If you don't take the initiative but instead just continue responding to stimuli, then you can never be sure that you aren't just caught up in some elaborate net.

There is no substitute for the above strategy. The only way to know that you are dealing with the real McCoys is to be the one initiating contact.

---

### Post by rsteinmetz70112 on 2020-11-27
I think some people here don't understand exactly what happened.

[LIST=1]
[*]We received an email purported to be from a large company we have done work for.
[*]That email seemed to be somewhat off for a number of reasons.
[*]We received a voice mail from a person who identified himselves as one of the people listed in the email. The call was from Hungary.
[*]I then contacted by email the Administrative and Technical Contact for the Company's Domain, after verifying that person was a senior executive in the companies IT group and his email address.
[*]I have not contacted any of the email addresses listed in the original email.
[/LIST]

I really don't know what else I can do.

---

### Post by DuckHook on 2020-11-27
Step&#8209;by&#8209;step then:

[list=1]
[*]Forget looking up domains or anything that you have received from them.
[*]Through a simple websearch, look up the company's main head office. ****Phone them****.
[*]Start with the receptionist. Explain your quandary and ask for a summary of their corporate officers/security personnel.
[*]Work your way up that structure until you get someone who has enough authority to deal with your concern.
[*]Talk to that person *by voice*, not via e-mail or some other easily spoofable medium.
[*]Even if they can't help you directly, at least you can verify that the e-mail address you've been sent is valid because it belongs to someone who is really part of their establishment.
[*]This simple series of steps should get you to the point where you can have reasonable confidence. The goal is not absolute certainty, but reasonable confidence.
[/list]
Sometimes, the best solutions are the old fashioned ones and do not involve technology.

---

### Post by TheFu on 2020-11-27
> **rsteinmetz70112 said:**
> I think some people here don't understand exactly what happened.
 ...
I really don't know what else I can do.

Only deal with the account MANAGER for your company who you have a pre-existing relationship. Have that person be the bridge to any other department - via 3-way call.

The type of information in the supposed leak should be know. Is it illegal to leak? Is it just embarrassing to the company?  Is it something that only an insider would have access?

If you are the CIO or CISO, then it is your problem to handle. If not, hand it over to those people.

If the other company knows about any leak(s), then they should provide the data and other knowledge gratis, otherwise is it a shake down and your national police should get involved.

---

### Post by DuckHook on 2020-11-27
> **TheFu said:**
> Only deal with the account MANAGER for your company who you have a pre-existing relationship. Have that person be the bridge to any other department - via 3-way call.

The type of information in the supposed leak should be know. Is it illegal to leak? Is it just embarrassing to the company?  Is it something that only an insider would have access?

If you are the CIO or CISO, then it is your problem to handle. If not, hand it over to those people.

If the other company knows about any leak(s), then they should provide the data and other knowledge gratis, otherwise is it a shake down and your national police should get involved.

&#8593; \\:D/ &#8593;
Between TheFu's thoughts and mine, you have multiple paths to a clean solution. I don't know why you are finding this so hard.

---

