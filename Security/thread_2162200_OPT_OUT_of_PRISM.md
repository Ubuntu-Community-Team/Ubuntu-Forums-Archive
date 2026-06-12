---
title: "OPT OUT of PRISM"
date: 2013-07-13
forum: Security
---

### Post by Barney on 2013-07-13
[https://prism-break.org/](https://prism-break.org/)

"Canonical’s Ubuntu is not recommended by PRISM Break because it contains Amazon ads and data leaks by default."

HELP? Who can help to get rid of the non-recommendation above?

---

### Post by Cheesemill on 2013-07-13
Just go to Settings > Privacy and turn off 'Include online results'.

---

### Post by Barney on 2013-07-13
Apparently, the problem has come up in 12.1, so maybe I'm okay with 10.04.4; see:
[https://www.eff.org/deeplinks/2012/10/privacy-ubuntu-1210-amazon-ads-and-data-leaks](https://www.eff.org/deeplinks/2012/10/privacy-ubuntu-1210-amazon-ads-and-data-leaks) .

---

### Post by Cheesemill on 2013-07-13
The problem with using 10.04 on a desktop/laptop is that it is no longer supported so any new bugs or security issues that are discovered won't ever get fixed.

---

### Post by snowpine on 2013-07-13
> **Cheesemill said:**
> The problem with using 10.04 on a desktop/laptop is that it is no longer supported so any new bugs or security issues that are discovered won't ever get fixed.

+1; I agree users are throwing out the baby with the bathwater if they think using obsolete releases will improve their security/privacy.

---

### Post by Barney on 2013-07-13
To each his own: I have several old machines that 10.04 works just fine on, so will stick with it, remembering how many Windows users long for Windows XP Pro after MS's misadventures into their newer/better distros.

I slap my own face for comparing Ubuntu to Windows!!!!!

---

### Post by snowpine on 2013-07-13
The difference (if you are going to make that comparison) is that Windows XP is still 100% fully supported by Microsoft.

---

### Post by CharlesA on 2013-07-13
> **Barney said:**
> To each his own: I have several old machines that 10.04 works just fine on, so will stick with it, remembering how many Windows users long for Windows XP Pro after MS's misadventures into their newer/better distros.

I slap my own face for comparing Ubuntu to Windows!!!!!

> **snowpine said:**
> The difference (if you are going to make that comparison) is that Windows XP is still 100% fully supported by Microsoft.

This. MS supports XP until April 2014 while 10.04 has been End of Life for a couple months now.

---

### Post by kevdog on 2013-07-13
I'm not sure if there is a way around this problem.  After learning about the latest leaks concerning Microsoft and how PRISM intercepted supposedly secure communications prior to encryption, I'm sure each major search engine has something like this in place.

---

### Post by Hexxus on 2013-07-13
Just to throw out a wrench into everyone's metaphors.

If your communications aren't encrypted, assume that they're easy to read. Your connection to the internet, who's to say that there isn't a similar program with ISP's that just hasn't been
un-covered to the general public?

Using old technology to prevent modern security flaws from 3rd party governments doesn't make sense.  Of course this is all IMO but just assume if you cannot control it yourself and watch access yourself, its going to be monitored by someone else.

---

### Post by snowpine on 2013-07-13
I got in trouble at my first job out of college for doing something I wasn't supposed to on the computer (I'll spare you the details).

Our head of IT said something that made a lot of sense and has stuck with me ever sense:

"Don't do anything on the Internet you wouldn't want to see on the front page of tomorrow's newspaper."

Sound advice; the best way to survive in our world of constant surveilance is to not have anything to hide. ;)

---

### Post by CharlesA on 2013-07-13
> **snowpine said:**
> 
"Don't do anything on the Internet you wouldn't want to see on the front page of tomorrow's newspaper."

Sound advice; the best way to survive in our world of constant surveilance is to not have anything to hide. ;)

/thread

---

### Post by Hexxus on 2013-07-14
> **CharlesA said:**
> /thread


Isn't that part of the old "sudo" login mantra?

Either way, good things to go by.

---

### Post by vmalep on 2013-07-14
Talking about [https://prism-break.org/](https://prism-break.org/) and ubuntu, I would love to see an ubuntu flavor or a special software that allow the user to activate the recommendations listed in this webpage.

The issue of Amazon is a detail in my opinion, as said, you just turn off online search and that sit.

But aside, I would like to get rid of Google and I would love to have a distrib that automatically include encrypted email (with a wizard to create the encryption key, etc.), a safe could files store, Tor activated in firefox, etc.

It should not be so complicated to setup... Actually, a soft in the ubuntu repo that can be run by any ubuntu flavor and by mint would be nice!

What do you think?
Pierre

---

### Post by Barney on 2013-07-14
From a nephew this morning (a little above my pay grade, but I wondered about Linus and the Intel patch):

[http://lists.randombit.net/pipermail/cryptography/2013-July/004728.html]("http://lists.randombit.net/pipermail/cryptography/2013-July/004728.html")

---

### Post by tubbygweilo on 2013-07-14
> **vmalep said:**
> Talking about [https://prism-break.org/](https://prism-break.org/) and ubuntu, I would love to see an ubuntu flavor or a special software that allow the user to activate the recommendations listed in this webpage.

The issue of Amazon is a detail in my opinion, as said, you just turn off online search and that sit.

But aside, I would like to get rid of Google and I would love to have a distrib that automatically include encrypted email (with a wizard to create the encryption key, etc.), a safe could files store, Tor activated in firefox, etc.

It should not be so complicated to setup... Actually, a soft in the ubuntu repo that can be run by any ubuntu flavor and by mint would be nice!

What do you think?
Pierre

Pierre, 
out of the box encryption is indeed a seductive idea but IIRC in some jurisdictions the act of encrypting data may well be against the law. I do believe that Ubuntu-Restricted-Extras contains some code that is against the law in some countries and so has to be activated by a direct action by the user.
As always tools do exist and with a little exploration and forethought a user can select which tools to deploy.

PS after glancing at your user information I see that you are using 9.10, had you thought of upgrading to something like 12.04lts with all the updated security patches? Every little helps.

---

### Post by Hungry Man on 2013-07-14
Turn off the Amazon 'leaks'... voila. As for using an unsupported OS, yeah... you've got a lot more to worry about. When an attacker wants into a system they basically have to use a chain of vulnerabilities - one to get some kind of control over the process, which will include an overflow and likely a data leak, if not more. Then something to escalate privileges. If you don't patch, they don't have to worry about chaining vulnerabilities, there will already be a hundred known ones for your system.

In terms of, specifically, PRISM just use HTTPS-Everywhere, use services you trust, use open source software that you can verify has been vetted by someone or some organization, etc. It's not too hard.

---

### Post by dontquoteme on 2013-07-18
There are multiple services you can use to avoid or negate data mining and data collection.

Clearly if the data is stored - the government will raise a court order to obtain that information, so the first rule is to avoid services that resell your data.

1. Search engine.
Use [www.startpage.com]("http://www.startpage.com") 
Use [www.duckduckgo.com]("http://www.duckduckgo.com")
Never use Google, Bing, Yahoo or AOL for search - or any of the 60 services operated by Google, due to their "Perfect Recall" policy and the single logon.

2. Email
Use [www.hushmail.com]("http://www.hushmail.com")
Use [www.startmail.com]("http://www.startmail.com") - due to released in the next month or so, and they are looking for beta testers.
[http://uwnthesis.wordpress.com/2013/06/04/startpage-email-become-a-beta-tester-for-startpage/](http://uwnthesis.wordpress.com/2013/06/04/startpage-email-become-a-beta-tester-for-startpage/)


3. Chat
cryptocat.


4. VPN
Use OpenVPN software.
Use a VPN that does not keep server logs, and deletes those server logs every day or faster.
[www.ivpn.net]("http://www.ivpn.net") - deletes logs every 10 minutes.  But look for a VPN that does not co-operate with authorities, Local Councils, Benefit agencies, Tax man etc. Some will hand your data over to anyone who asks... and that includes divorce lawyers.  Always choose a VPN that is based outside of your own country, so that court orders do not apply.
[http://uwnthesis.wordpress.com/2013/05/17/which-is-the-safest-vpn-on-the-market-which-vpn-cares-most-for-your-privacy/](http://uwnthesis.wordpress.com/2013/05/17/which-is-the-safest-vpn-on-the-market-which-vpn-cares-most-for-your-privacy/)

5. Install Ghostery, privacyfix and disconnect.me on all web browsers.
[http://uwnthesis.wordpress.com/2013/07/06/how-to-install-and-configure-ghostery-to-block-all-trackers/](http://uwnthesis.wordpress.com/2013/07/06/how-to-install-and-configure-ghostery-to-block-all-trackers/)

6. Use HTTPS Everywhere.
Be aware that SSL can be compromised, espeically by the Government.



Further tool lists here
[http://uwnthesis.wordpress.com/2013/07/14/prism-%E2%9A%A1-break/](http://uwnthesis.wordpress.com/2013/07/14/prism-%E2%9A%A1-break/)
Operate your own private cloud, do not use Amazon, Google or any US based company, who must comply with both FISA and The Patriot Act.

Use EU servers such as [www.startpage.com]("http://www.startpage.com") - who do not track you and are AUDITED by the EU to ensure no data leakage, and no server logs are kept.

---

### Post by tubbygweilo on 2013-07-18
Arstechnica offers some thoughts upon encrypted mail tools for people to use [http://arstechnica.com/security/2013/06/encrypted-e-mail-how-much-annoyance-will-you-tolerate-to-keep-the-nsa-away/](http://arstechnica.com/security/2013/06/encrypted-e-mail-how-much-annoyance-will-you-tolerate-to-keep-the-nsa-away/), but as with all email encrypted of not it is the passage through the net that allows unencrypted who, when, where meta data to be collected. The other problem with any encrypted email communication is that you firstly need to have people install something so that you may interact in an encrypted way and secondly do you trust them with your security? I'm more worried about businesses collecting data and passing it about in ways that are often rather obscure even after viewing their privacy policies.

---

### Post by Hungry Man on 2013-07-18
I would not trust Cryptocat with anything particularly sensitive.

---

### Post by nll on 2013-07-31
There used to be this, but it looks abandoned now: [https://www.privacy-cd.org/en](https://www.privacy-cd.org/en)
Now would be a good time for a new Ubuntu privacy spin.

By the way: https for Ubuntu Forums, anyone?

---

### Post by Soul-Sing on 2013-08-01
> **dontquoteme said:**
> There are multiple services you can use to avoid or negate data mining and data collection.

Clearly if the data is stored - the government will raise a court order to obtain that information, so the first rule is to avoid services that resell your data.

1. Search engine.
Use [www.startpage.com]("http://www.startpage.com") 
Use [www.duckduckgo.com]("http://www.duckduckgo.com")
Never use Google, Bing, Yahoo or AOL for search - or any of the 60 services operated by Google, due to their "Perfect Recall" policy and the single logon.

Better ixquick imo.

2. Email
Use [www.hushmail.com]("http://www.hushmail.com")
Use [www.startmail.com]("http://www.startmail.com") - due to released in the next month or so, and they are looking for beta testers.
[http://uwnthesis.wordpress.com/2013/06/04/startpage-email-become-a-beta-tester-for-startpage/](http://uwnthesis.wordpress.com/2013/06/04/startpage-email-become-a-beta-tester-for-startpage/)

Hushmail has its issue's.


3. Chat
cryptocat.

Do not rely on this.


4. VPN
Use OpenVPN software.
Use a VPN that does not keep server logs, and deletes those server logs every day or faster.
[www.ivpn.net]("http://www.ivpn.net") - deletes logs every 10 minutes.  But look for a VPN that does not co-operate with authorities, Local Councils, Benefit agencies, Tax man etc. Some will hand your data over to anyone who asks... and that includes divorce lawyers.  Always choose a VPN that is based outside of your own country, so that court orders do not apply.
[http://uwnthesis.wordpress.com/2013/05/17/which-is-the-safest-vpn-on-the-market-which-vpn-cares-most-for-your-privacy/](http://uwnthesis.wordpress.com/2013/05/17/which-is-the-safest-vpn-on-the-market-which-vpn-cares-most-for-your-privacy/)

What is a good VPN? How do you know that? A VPN without dealing with DNS and ipv6 issue's is no good.

5. Install Ghostery, privacyfix and disconnect.me on all web browsers.
[http://uwnthesis.wordpress.com/2013/07/06/how-to-install-and-configure-ghostery-to-block-all-trackers/](http://uwnthesis.wordpress.com/2013/07/06/how-to-install-and-configure-ghostery-to-block-all-trackers/)

6. Use HTTPS Everywhere.
Be aware that SSL can be compromised, espeically by the Government.

Indeed. But one of the better add-ons imho.



Further tool lists here
[http://uwnthesis.wordpress.com/2013/07/14/prism-%E2%9A%A1-break/](http://uwnthesis.wordpress.com/2013/07/14/prism-%E2%9A%A1-break/)
Operate your own private cloud, do not use Amazon, Google or any US based company, who must comply with both FISA and The Patriot Act.

Use EU servers such as [www.startpage.com]("http://www.startpage.com") - who do not track you and are AUDITED by the EU to ensure no data leakage, and no server logs are kept.

regards.

---

### Post by Buntu Bunny on 2013-08-01
> **Barney said:**
> [https://prism-break.org/](https://prism-break.org/)

Well, I wasn't familiar with this site and so went to take a look. Seems like there are a lot of good alternatives to the major players, for those who are interested.

---

