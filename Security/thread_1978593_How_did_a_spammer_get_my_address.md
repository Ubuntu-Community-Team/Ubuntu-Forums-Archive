---
title: "How did a spammer get my address?"
date: 2012-05-12
forum: Security
---

### Post by aligator12 on 2012-05-12
Hi, I have an email address I only use for facebook, and today I got a spam message, how do you think a spammer get my address? 

I just want to know how my email address was compromised as I only use it for facebook. Only 14 people (and facebook of course) can see my email address, could one of my friends have downloaded a rouge app or something that looked at my address on my Info page or something? 

Or the only other option is, is that a compromised Windows computer on my network sniffed my address over the router and then sold it to spammers but none of my other addresses are being spammed. It is highly unlikely that I have malware myself as I use Ubuntu.

So how do you theorize my address was compromised? Any help would be appreciated as I am bed bound and my whole life is my facebook and I don't want to lose it to hackers and never see my only friends again. :(

---

### Post by carl4926 on 2012-05-12
Once other people have it, no matter who they are. That's it!
There has been some massive hacking of Hotmail recently and spam is everywhere as a result. And I'm just citing one example. It's a massive problem. I find gmail filters spam pretty well.

---

### Post by lisati on 2012-05-12
Sometimes spammers get lucky and guess a real working email address to use for targeting someone or to try to disguise the true origins of their emails.

---

### Post by codemaniac on 2012-05-12
There are many ways in which spammers can get your email address

1. From web pages.
Spammers have programs which spider(sometimes called webcrawlers) through web pages, looking for email addresses, e.g. email addresses contained in mailto: HTML tags [those you can click on and get a mail window opened]

2.Dictionary attack
Millions of users share one common domain name, so you already know that ("hotmail.com" in the case of Hotmail). Try to sign up for a new account and you will discover that guessing an existing user name is not difficult either. Most short and good names are taken.

3.Brute Searching Force

Another tactic employed by spammers to discover email addresses is to search common sources for email addresses. They have robots scanning web pages and following links.

4.From a web browser.

Some sites use various tricks to extract a surfer's email address from the web browser, sometimes without the surfer noticing it.

5.From mailing lists.

Spammers regularily attempt to get the lists of subscribers to mailing lists [some mail servers will give those upon request],knowing that the email addresses are unmunged and that only a few of the addresses are invalid.

and many more ..

---

### Post by aligator12 on 2012-05-12
Hi, I am pretty paranoid so here is my setup:

In a separate Firefox profile I ONLY log in to my Yahoo webmail and Facebook account, I never visit any other sites and I only registered at Facebook with that address.

I think the chances of a brute force attack is slim since I use no dictionary words in my address. 

So as you can see I am pretty worried now about how this happened.

---

### Post by codemaniac on 2012-05-12
You can also tighten spam handling security features of your email provider in order to get rid off unwanted ones .

---

### Post by carl4926 on 2012-05-12
> So as you can see I am pretty worried now about how this happened.
Really it's not a thing to worry about.

**** happens

Be happy you are alive and well):P

---

### Post by lisati on 2012-05-12
> **codemaniac said:**
> You can also tighten spam handling security features of your email provider in order to get rid off unwanted ones .
+1
Another option to consider is running your own mail server. I did so after getting totally fed up with the influx of spam that was being (mis)handled by the email provider I was using at the time. One advantage is that there are more options for identifying, blocking and otherwise keeping out spam than if you rely on someone else to provide your email services.

---

### Post by aligator12 on 2012-05-12
But how did they find my email address? And what other info do they have about me? Because if they got my email address they surly got something else, right?

---

### Post by codemaniac on 2012-05-12
> **aligator12 said:**
> But how did they find my email address? And what other info do they have about me? Because if they got my email address they surly got something else, right?

You can never be assured of complete anonymity over the Internet network , All your packets are streaming through the public tunnel of internet .
And you never know what intelligent programs are there to sniff your packets and retrieving your personal data .

---

### Post by aligator12 on 2012-05-12
> **codemaniac said:**
> You can never be assured of complete anonymity over the Internet network , All your packets are streaming through the public tunnel of internet .
And you never know what intelligent programs are there to sniff your packets and retrieving your personal data .
Like where? At the ISP?

---

### Post by aligator12 on 2012-05-12
I think that we can deduce that either one of the 2 things has happened:

**Security flaw on my end**: As we all know, Ubuntu -although tens of thousands of times more secure then Windows, has it's own share of security flaws: 
[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

==My thoughts on this==
I hardly even browse the web very much. I mainly just do youtube and facebook and occasionally other random sites. And my other address I use daily has not received any spam emails, but it does receive fairly regular SPAM friend requests which is pretty weird.

**Security flaw on one of my friends end **: Do you know of any rouge apps/malware that sniff friends's profiles for contact info? Because my email address is clearly listed.

---

### Post by lisati on 2012-05-12
Sometimes malware (viruses etc) on a compromised machine running Windows will take a look at the address book and other contact info on that machine and start spewing out its rubbish without the owner of the machine's knowledge. 

If you have an example of the email, complete with headers, you might be able to track down the source using [http://whatismyipaddress.com/trace-email](http://whatismyipaddress.com/trace-email) or the [spamcop]("http://spamcop.net") reporting service.

---

### Post by aligator12 on 2012-05-12
> **lisati said:**
> Sometimes malware (viruses etc) on a compromised machine running Windows will take a look at the address book and other contact info on that machine and start spewing out its rubbish without the owner of the machine's knowledge. 

If you have an example of the email, complete with headers, you might be able to track down the source using [http://whatismyipaddress.com/trace-email](http://whatismyipaddress.com/trace-email) or the [spamcop]("http://spamcop.net") reporting service.
I have not opened or deleted the email yet. I don't want to open it.

> Sometimes malware (viruses etc) on a compromised machine running Windows will take a look at the address book and other contact info on that machine and start spewing out its rubbish without the owner of the machine's knowledge. 

Do you think this is what happened to me?

If yes, how come my other yahoo email addresses (which are not connected to Facebook) receive unsolicited spam "friend" requests on a monthly basis? This kinda makes me think the problem might lay on my end?

---

### Post by lisati on 2012-05-12
Most of the Facebook "friend" requests I get are from people I know, even to email addresses that I haven't registered with Facebook. Occasionally I get one that's unsolicited.

One of the things I did (after a colleague expressed concern about age-appropriateness of a link I posted on my timeline that found its way to her daughter's page) was to tighten up who could see my details via Facebook. One way is through the drop-down menu to the right of Facebook's "Home" button on the top menu and the clicking on "Privacy settings".

---

### Post by aligator12 on 2012-05-12
Alright guys, I just checked one of my other address I only use for Yahoo answers and Ubuntu forums, and I HAD A SPAM MESSAGE FROM THE SAME ADDRESS THAT SPAMMED MY OTHER ACCOUNT (rr.com it claims). This eliminates the possibility of it being Facebook entirely. In fact I created this yahoo account in April 22 of this year (I created another ubuntu account in April because I thought I lost this account, but then I remember I wrote down the password for this account). I only used it for yahoo answers and this site. And I GET A MESSAGE FROM THE same address!

OMG am I infected?!?!?!?

---

### Post by aligator12 on 2012-05-12
Also, it is pretty annoying come to think of it, because whenever I create a yahoo email account, I ALWAYS get unsolicited "friend" requests, after I only register for like 1 account somewhere (completely reputable). 

Do you think the fault could lay on my end? If so, what can I do?

---

### Post by lisati on 2012-05-12
> **aligator12 said:**
> Alright guys, I just checked one of my other address I only use for Yahoo answers and Ubuntu forums, and I HAD A SPAM MESSAGE FROM THE SAME ADDRESS THAT SPAMMED MY OTHER ACCOUNT ([COLOR="Red"]rr.com [/COLOR]it claims). This eliminates the possibility of it being Facebook entirely. In fact I created this yahoo account in April 22 of this year (I created another ubuntu account in April because I thought I lost this account, but then I remember I wrote down the password for this account). I only used it for yahoo answers and this site. And I GET A MESSAGE FROM THE same address!

OMG am I infected?!?!?!?

Could be some phisher who got lucky by guessing your email address correctly.

---

### Post by aligator12 on 2012-05-12
> **lisati said:**
> Could be some phisher who got lucky by guessing your email address correctly.
Both of them? One of them is johnsmith(3 numbers)@ymail.com and the other is my real name (which believe me is a very long weird name that is not in the dictionary and not guessable).

And how come nearly every yahoo account I create ends up getting spammed? Isn't that a bit weird?

So tell me, is my personal data at risk? I put my SSN on this computer you know. I am really freaking out now.

---

### Post by lisati on 2012-05-12
I think some of the points have already been touched on in this thread, but you might find this article interesting: [http://netforbeginners.about.com/od/scamsandidentitytheft/f/spamemailaddresses.htm](http://netforbeginners.about.com/od/scamsandidentitytheft/f/spamemailaddresses.htm)

In short: it's probably not your fault.

edit: You might also want to take a look at your Yahoo profile's privacy options.

---

### Post by aligator12 on 2012-05-12
> **lisati said:**
> I think some of the points have already been touched on in this thread, but you might find this article interesting: [http://netforbeginners.about.com/od/scamsandidentitytheft/f/spamemailaddresses.htm](http://netforbeginners.about.com/od/scamsandidentitytheft/f/spamemailaddresses.htm)

In short: it's probably not your fault.

edit: You might also want to take a look at your Yahoo profile's privacy options.
So do you think I have had a security venerability exploited or even have been infected with Linux malware?

> edit: You might also want to take a look at your Yahoo profile's privacy options.
Where could I find this?

Also, I logged into another one of my accounts I created in February of this year, and it is apparently clean of any spam. So that makes 4 out of my 5 yahoo email accounts compromised. Not good.

What do you think could be causing this? It is really a headache and is starting to scare me.

---

### Post by Irihapeti on 2012-05-12
Just wondering... do any of your friends have the habit of forwarding emails to other people? Or sending out emails to a number of addresses at once (and not using bcc)?

---

### Post by lisati on 2012-05-12
> **aligator12 said:**
> So do you think I have had a security venerability exploited or even have been infected with Linux malware?

It's unlikely that it's due to Linux malware. You might want to take a read of bodhi.zazen's "sticky" at [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

> **aligator12 said:**
> 
Where could I find this?

The next time you log in to Yahoo mail, look for a link to "My account" near the top of the page.

Yahoo is pretty useless at dealing with spam, which is why I signed up at [Spamcop]("http://www.spamcop.net/") to report spam rather than have to contend with Yahoo. I also set up my own email server so I could have greater control over what arrives in my inbox.

---

### Post by aligator12 on 2012-05-12
> Just wondering... do any of your friends have the habit of forwarding emails to other people? Or sending out emails to a number of addresses at once (and not using bcc)?
I have now determined that my Facebook friends are not the source of my problem (4 out of 5 of my yahoo accounts are being spammed). Or if you mean my email contacts... I have none. In fact I never even send emails to other people with my accounts.

> The next time you log in to Yahoo mail, look for a link to "My account" near the top of the page.
I don't see a "My account" but I do see "Account info" but I didn't see any privacy related options in there.

> Yahoo is pretty useless at dealing with spam, which is why I signed up at Spamcop to report spam rather than have to contend with Yahoo. I also set up my own email server so I could have greater control over what arrives in my inbox.
I don't really care at all if I receive SPAM or not because I can delete it. But what concerns me, is that:

1) Nearly every time I create a yahoo account I always receive SPAM (and from the same address at that).

2) How does this same attacker keep finding all of my different addresses?

Is my system (or netowrk) compromised somehow? Allowing him or her to see my data?

---

### Post by OpSecShellshock on 2012-05-12
If your system or email accounts were compromised then you'd be sending spam, not (just) receiving it. Have you checked the privacy policy at Yahoo itself? Does it allow them to provide your email address to unspecified "partners"? When you set up other accounts with these addresses, are they visible to others in your user profile on those sites?

There is no reason given what you have presented here to conclude that your accounts are being specifically targeted yet. At the moment I do find it a bit strange that the sender is always the same, but it's not much to go on.

Have you tried setting up an account and just not using it for anything at all? I mean not signing up for anything with it and also not sending or receiving anything? I would suggest trying that, then regularly check in on it and see if you receive messages.

---

### Post by jerome1232 on 2012-05-12
> **aligator12 said:**
> yahoo accounts

I think we found the problem.

All snarkiness aside, in my personal experience, yahoo is a terrible email provider. Have you read Yahoo's privacy agreement? Do they explicitly say they will not sell your email/details to third parties. It's entirely possible they do sell your details.

---

### Post by uRock on 2012-05-12
> **aligator12 said:**
> But how did they find my email address? And what other info do they have about me? Because if they got my email address they surly got something else, right?

Yahoo gives out/sells that info. They have to make money.

---

### Post by aligator12 on 2012-05-12
> If your system or email accounts were compromised then you'd be sending spam, not (just) receiving it. Have you checked the privacy policy at Yahoo itself? Does it allow them to provide your email address to unspecified "partners"? When you set up other accounts with these addresses, are they visible to others in your user profile on those sites?
Where do I find the policy? I doubt they do, Yahoo is pretty reputable you know.

> There is no reason given what you have presented here to conclude that your accounts are being specifically targeted yet. At the moment I do find it a bit strange that the sender is always the same, but it's not much to go on.
I find that very strange as well, I mean even when I create a new account I can basically always count on getting spam...

> Have you tried setting up an account and just not using it for anything at all? I mean not signing up for anything with it and also not sending or receiving anything? I would suggest trying that, then regularly check in on it and see if you receive messages.
No, but there was one I created and I only used it for Ubuntu forums. And I still get spam. 

> I think we found the problem.

All snarkiness aside, in my personal experience, yahoo is a terrible email provider. Have you read Yahoo's privacy agreement? Do they explicitly say they will not sell your email/details to third parties. It's entirely possible they do sell your details.
Yahoo appears to fight spam:
[http://help.yahoo.com/tutorials/mmail/mmail/mm_otherspam1.html](http://help.yahoo.com/tutorials/mmail/mmail/mm_otherspam1.html)

> 

---

### Post by jerome1232 on 2012-05-12
I disagree

> INFORMATION SHARING AND DISCLOSURE

Yahoo! does not rent, sell, or share personal information about you with other people or non-affiliated companies except to provide products or services you've requested, when we have your permission, or under the following circumstances:

    We provide the information to trusted partners who work on behalf of or with Yahoo! under confidentiality agreements. These companies may use your personal information to help Yahoo! communicate with you about offers from Yahoo! and our marketing partners. However, these companies do not have any independent right to share this information.
    We have a parent's permission to share the information if the user is a child under age 13. Parents have the option of allowing Yahoo! to collect and use their child's information without consenting to Yahoo! sharing of this information with people and companies who may use this information for their own purposes.
    We respond to subpoenas, court orders, or legal process, or to establish or exercise our legal rights or defend against legal claims.
    We believe it is necessary to share information in order to investigate, prevent, or take action regarding illegal activities, suspected fraud, situations involving potential threats to the physical safety of any person, violations of Yahoo!'s terms of use, or as otherwise required by law.
    We transfer information about you if Yahoo! is acquired by or merged with another company. In this event, Yahoo! will notify you before information about you is transferred and becomes subject to a different privacy policy.

Yahoo! displays targeted advertisements based on personal information. Advertisers (including ad serving companies) may assume that people who interact with, view, or click targeted ads meet the targeting criteria&#8212;for example, women ages 18-24 from a particular geographic area.

    Yahoo! does not provide any personal information to the advertiser when you interact with or view a targeted ad. However, by interacting with or viewing an ad you are consenting to the possibility that the advertiser will make the assumption that you meet the targeting criteria used to display the ad.
    Yahoo! advertisers include financial service providers (such as banks, insurance agents, stock brokers and mortgage lenders) and non-financial companies (such as stores, airlines, and software companies).

Yahoo! works with vendors, partners, advertisers, and other service providers in different industries and categories of business. For more information regarding providers of products or services that you've requested please read our detailed reference links. 

In summary they don't sell it, but they do it share it with business partners.

---

### Post by aligator12 on 2012-05-12
> **jerome1232 said:**
> I disagree



In summary they don't sell it, but they do it share it with business partners.
So are you telling me it is not my fault (but yahoo's)? It would be a relief if it was.

Can anyone else concur with this? 

I do have my doubts tho, because this is a fairly recent phenomena (it has only started in the past 11 months).

---

### Post by uRock on 2012-05-12
> **jerome1232 said:**
> In summary they don't sell it, but they do it share it with business partners.

Business partners who pay them is the same as selling, IMHO.

---

### Post by aligator12 on 2012-05-13
Alright you guys today **address number 3** received spam from "rr.com". That is the third address. What do you think is going on here?

---

### Post by uRock on 2012-05-13
> **aligator12 said:**
> Alright you guys today **address number 3** received spam from "rr.com". That is the third address. What do you think is going on here?

The internet. Every email I have ever had has received spam on some level.

---

### Post by aligator12 on 2012-05-13
> **uRock said:**
> The internet. Every email I have ever had has received spam on some level.
Yes, but why within the last 7 days have I been receiving spam form just this same spammer?

---

### Post by OpSecShellshock on 2012-05-13
The same account at rr.com or different accounts all using it? Seems like the name of a legacy Time Warner email account from back when it was called Roadrunner and from when ISPs also provided email to their subscribers. It's possible that some of those are dormant/forgotten but still valid and have been compromised in some way. Doesn't explain how the same one would be getting your details over and over.

Had another thought. When you sign up for a new email address, often the provider will ask for a second address for confirmation or in case you need to reset the new one. If you are using the same address as the backup for every new account you create, and that account has been compromised in some way (usually due to bad/re-used passwords) then it's possible that they're being acquired that way. It's still really unlikely though.

But everyone is pretty much right--spam is just part of internet life.

---

### Post by aligator12 on 2012-05-13
> The same account at rr.com or different accounts all using it? 
It is different accounts.

> Doesn't explain how the same one would be getting your details over and over.
I know, I have no idea why.

> Had another thought. When you sign up for a new email address, often the provider will ask for a second address for confirmation or in case you need to reset the new one. If you are using the same address as the backup for every new account you create, and that account has been compromised in some way (usually due to bad/re-used passwords) then it's possible that they're being acquired that way. It's still really unlikely though.
I did not supply a second address.

I am going to open one of the emails to see the header. Can you please tell me how to disable everything I should? Like html, photos, etc. Thanks.

---

### Post by aligator12 on 2012-05-14
Anyone?

---

### Post by carl4926 on 2012-05-14
> **aligator12 said:**
> Anyone?

Didn't someone say.....

> spam is just part of internet life. 	

You're totally paranoid dude.
You might want to consider not using the internet at all.

---

### Post by uRock on 2012-05-14
> **carl4926 said:**
> You're totally paranoid dude.
You might want to consider not using the internet at all.

How does excepting spam as being part of the internet make one paranoid, when spam is a part of the internet life?

---

### Post by Guilden_NL on 2012-05-14
Yahoo is the worst of the webmail providers for SPAM.  Not even close to anyone else.

Sad because Rocketmail from 411.com was great webmail before Yahoo bought them and run it into the ground.

The never ending Canadian pharmacy SPAM campaign continues on this month at Yahoo with a fake email from Amazon.com canceling an order from you. Click on it and you end up at the Canadian pharmacy site.  I saw a report a few days ago that over 100Million SPAMs were sent via Yahoo in one week. No idea if it is true, but all six Yahoo accounts I have purely for web logins have received at least one every day for the past week.  Yahoo's SPAM filter doesn't catch them.  GMail is spotlessly clean of SPAM.

Sorry to say that I am laughing about the level of stress when the user is on Facebook, one of the Internet's biggest information who*es.  If you're worried about your data being compromised, why would you be on Facebook?

---

### Post by carl4926 on 2012-05-14
> **uRock said:**
> How does excepting spam as being part of the internet make one paranoid, when spam is a part of the internet life?
The OP is obsessing over how he could possibly get spam, as if it's an impossibility given his cautious approach. That he _didn't expec_t it or considered it an impossibility and then trying to establish it's source is just plain paranoid.

---

### Post by aligator12 on 2012-05-14
If you think I am being paranoid fine. I probably am. 

But explain to me how an address which I only used FOR THIS SITE gets spammed by the same spammer who spammed my other 2 accounts? I am confused.

---

### Post by carl4926 on 2012-05-14
> **aligator12 said:**
> If you think I am being paranoid fine. I probably am. 

But explain to me how an address which I only used FOR THIS SITE gets spammed by the same spammer who spammed my other 2 accounts? I am confused.
I can't explain it, well it might be possible given all the facts, but even then I'm sure I wouldn't be bothered.
Who else knows the address (friends/family?)

---

### Post by aligator12 on 2012-05-14
> **carl4926 said:**
> I can't explain it, well it might be possible given all the facts, but even then I'm sure I wouldn't be bothered.
Who else knows the address (friends/family?)
Just me and ubuntu forums. I did not tell anyone else.

---

### Post by lisati on 2012-05-14
> **aligator12 said:**
> Just me and ubuntu forums. I did not tell anyone else.

Like I said earlier, it *could* be that the spammer got lucky and guessed your email address. One of the things they can do is use a program to generate lists of *possible* email addresses, many of which will be plain invalid, but some of which might be real. Most of the time they won't care that they're annoying people (spammers are like that), all they'll be interested in is spewing out their garbage to as many people as possible.

---

### Post by carl4926 on 2012-05-14
All the forum staff have access to your email address.
But I'm 100% sure they'd never abuse their privilege

---

### Post by kurt18947 on 2012-05-14
Perhaps aligator12 could open an email account with another email provider beside Yahoo?  If a non-Yahoo account gets spam from the same sources, that would indicate some sort of non-Yahoo specific crapware.  If only Yahoo accounts have this problem,  that is indicative as well.  A search for free email providers should turn up a few alternatives.

---

### Post by aligator12 on 2012-05-14
Alright, tommorow I am going to open 2 different accounts at AOL mail and hotmail. Can you people think of anymore free services for me to use as a control group?

Thanks.

---

### Post by jerome1232 on 2012-05-14
gmail

---

### Post by carl4926 on 2012-05-14
> **aligator12 said:**
> Alright, tommorow I am going to open 2 different accounts at AOL mail and hotmail. Can you people think of anymore free services for me to use as a control group?

Thanks.
Oh dear, nevermind

+1 gmail

---

### Post by OpSecShellshock on 2012-05-14
No reason to give anyone a hard time. The whole structure of provider relationships is confusing (by design, even). Yahoo is one of the largest providers of email addresses still, and they have partners that they share account information with. That process is most likely automated, due to high volumes of accounts. Some of those partners have partners of their own, and sometimes they just have leaks or dishonest employees that distribute that info on the side. Sometimes spammers just try every possible combination.

---

### Post by aligator12 on 2012-05-15
Well, I created some addresses, if I don't get any spam in them does that basically mean I am fine?

---

### Post by carl4926 on 2012-05-15
> **aligator12 said:**
>  if I don't get any spam in them does that basically mean I am fine?

Fine....?

If you don't use those account's maybe you'll get no spam, but that defeats the object.

---

### Post by uRock on 2012-05-15
> **carl4926 said:**
> Fine....?

If you don't use those account's maybe you'll get no spam, but that defeats the object.

+1 My Hotmail, Yahoo and Gmail accounts always get spam, but with adjustment of settings and using Thunderbird for my gmail I do not see most of the spam.

---

### Post by cortman on 2012-05-15
Really, like was said multiple times- spam is a part of life.
My personal gmail address that I use only for friends gets zero spam.
My other that I use for all my forum stuff, etc., gets about 5-6 a day. Spam is just part of being online.
And as far as the same address, it could be the spammer is spoofing his address. Frankly, it'd be the last thing I would get worried about.
Spam can be quite humorous at times actually. :)

---

### Post by computeratin on 2012-05-15
If I understand the OP correctly his concern is not that he is receiving spam per se.
 
It is that he is opening new e mail accounts and recieving spam on them shortly afterwards.
 
This is, as many others have said, simply a part of the net. 
 
There are automated programs that both crawl the net to find e mail address and ones that generate every possible combination of addresses. Some of the generation programs are very sophisticated and have been programmed to create possible combos in a way similar to what a human would do.
 
You are human, ergo: They have your number; so to speak. Plus, as many have said: A lot of information gets shared on the net and in many ways; not all of them scrupulous or ethical.
 
I would not worry unless
 
A) The *very first* of the new spam that you get at the new e mail address occurs in well under a minute (like 10-15 seconds) or 
 
B) You *immediately* (once again in well less than 60 seconds) start receiving spam "from yourself". 
 
Either one could be an indication that your browser has been hijacked by platform independent spyware / browser exploit that is collecting information from your system and broadcasting it. 
 
But, that process is automated and happens very quickly. 
 
If your situation does not fufill either the criteria of either A or B then you're OK and don't have anything to worry about.
 
I would suggest that if the situation concerns you that greatly that you should start participating in the Moziila forums and learn to use add ons and tweaks to make your browser even more secure than it's default installation configuration.
 
Then you won't have to worry so much because you'll KNOW it's secure!

---

### Post by aligator12 on 2012-05-15
> **computeratin said:**
> If I understand the OP correctly his concern is not that he is receiving spam per se.
 
It is that he is opening new e mail accounts and recieving spam on them shortly afterwards.
 
This is, as many others have said, simply a part of the net. 
 
There are automated programs that both crawl the net to find e mail address and ones that generate every possible combination of addresses. Some of the generation programs are very sophisticated and have been programmed to create possible combos in a way similar to what a human would do.
 
You are human, ergo: They have your number; so to speak. Plus, as many have said: A lot of information gets shared on the net and in many ways; not all of them scrupulous or ethical.
 
I would not worry unless
 
A) The *very first* of the new spam that you get at the new e mail address occurs in well under a minute (like 10-15 seconds) or 
 
B) You *immediately* (once again in well less than 60 seconds) start receiving spam "from yourself". 
 
Either one could be an indication that your browser has been hijacked by platform independent spyware / browser exploit that is collecting information from your system and broadcasting it. 
 
But, that process is automated and happens very quickly. 
 
If your situation does not fufill either the criteria of either A or B then you're OK and don't have anything to worry about.
 
I would suggest that if the situation concerns you that greatly that you should start participating in the Moziila forums and learn to use add ons and tweaks to make your browser even more secure than it's default installation configuration.
 
Then you won't have to worry so much because you'll KNOW it's secure!
Well in one of my accounts, I created it on April 22 2012 and received spam on May 5th. But not within 60 seconds.

---

### Post by computeratin on 2012-05-15
> **aligator12 said:**
> Well in one of my accounts, I created it on April 22 2012 and received spam on May 5th. But not within 60 seconds.
 
In comparing computer time to human time that time span (about two weeks) is the equivalent of you living until the universe ends.
 
I'm sure if you had that much time and nothing else to do you could probably figure out your neighbors' e mail address.
 
You're fine, don't sweat it.

---

