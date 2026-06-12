---
title: "Public WiFi remote install"
date: 2017-11-16
forum: Security
---

### Post by pointy2 on 2017-11-16
As a road warrior, I'm concernied about public wifi security.

AA17.10 is up to date and runs with a paid VPN for Linux, strong firewall rules, full encryption install, good passwords, agent spoofer in FF, as well tweaks in about:config and others. 
[B]Can a hostile attack 'ride in' to the target system on the wifi signal to establish a remote connection, or to corrupt/view file system? with these security measures?

[/B]I'm concerned about keyloggers, screen captures, installing other spyware on the system. Not concerned about LE or nation states, but rather talented hackers on a mission. (Yes, I am paranoid about this (for good reason)

---

### Post by TheFu on 2017-11-18
WiFi is always a risk.  It is a broadcast protocol.  There are methods, like using a VPN for all traffic, which can mitigate many of those risks, but often the default configuration for VPNs is weak.  For example, most VPNs use PPTP, which has been hacked since 2005, but somehow is still being used.

WiFi has bugs.  Kernels have bugs.  I wouldn't assume that those bugs are all known to everyone. Having worked in highly secure settings, where we tracked every bug in our software for decades, I can say with complete confidence there are at least 500 bugs in any code with over 1M SLOCs and at least 100 critical bugs.  At least.  What those bugs are and whether they can be used for remote access is unknowable, but it is best to be paranoid.

Any computer can be hacked if there is physical access.  The level of effort required to perform that can be raised, but if the system is running and does anything automatic when a USB device is inserted, BAM, you are compromised.  Bluetooth is another attack vector.  I was at a hacker conference a few years ago and got hacked over bluetooth.  I had planned to be hacked and had a full image to restore once I returned home.  The system was a fully-patched Ubuntu-Mate installed 2 days prior.

HTTPS isn't really secure.  It is based on trusting every CA in your CA-Cert DB **and** trusting the DNS provider.  When you connect to any network, they generally own the DNS.  Have you cleaned out your CA-Cert DB to remove any CAs who are untrustworthy?  There are lots of govt and commercial CAs in there who have proven NOT to be trustworthy.  It is possible to generate an SSL cert on-the-fly with hardware available today.  If you own the DNS and can work a deal with any of the CAs in the list, you can insert whatever javascript code you like into a browser. Without HTTPS, it is trivial to get people to run whatever Javascript we like. Just send a shortened link.  Do you allow Javascript?  Do you follow shortened links?

There are hundreds of different attack vectors to any system. Hundreds.  Nothing can replace a smart, attentive, end-user to protect a system.

With your FDE, do you boot off media that never leaves your person, even in the shower?  Look up "evil maid attack" for why this is important.  Oh - and always power off your laptop when you leave the room. Hibernate and standby are the enemies of secure.

You can search for "wifi attacks" to see what people are being trained about.  A VPN using IPSec and 2FA is the best mitigation that I know, but is it 100%?  Nope.  Even if you ran the VPN yourself and configured it correctly (which is non-trivial), it is still code.  All code has bugs. All code has bugs. 

You should be paranoid.  That will keep you upping your security.

My educated guess is that by running Linux, patched weekly, using FDE, zero inbound services and an IPSec VPN, then you are better off then 95% of the world.  Disallowing javascript, flash, and other addons would bump you into the 99% group.  Not allowing anyone near your laptop while it is running would get you to the 99.9%.  

Everyone thinks they have good passwords.  If you are still using passwords, you've already lost the security fight. Use a different login for every different account. Don't reuse the same email address for banking as you use for social networks.  I have over 100 different email accounts for the different services I use.  Some of my accounts use randomized logins - I couldn't tell you the login to my bank or brokerage accounts.  I don't know them.  They are different and use different email addresses too.

If you use a password manager, and I think you should, have every login be different for every remote system.  Use 2FA to access your laptop and cell phone too.  A fingerprint is NOT 2FA.  Fingerprints have been hacked for a long time. It appears that faces have been hacked too.  
* something you know - a passphrase
* something you have - a crypto-device - your finger/face/voice are not crypto-devices!!!

Lie on all those password reset questions.  Your pet, mother's maiden name, high school mascot - lie. Make them different everywhere.  Use randomly generated answers for each.

Get a U2F token. Use it everywhere you can.  If your bank/financial institution supports it (and they should), get a 2FA solution from them.  I mentioned it to my broker and 3 days later it arrived in the snailmail. This was 15+ yrs ago, so it isn't new.  I'd like for them to support U2F, so I mention it every time I call.

Being secure isn't about 1 thing. It is about 1,000s of things, all performed correctly, every day.  Expect crackers to use side-attacks if the front-door attack is non-trivial.  Making a phone call to your bank and begging to get a transfer is easier (helpfully) than hacking their website.  Well, that is debatable about some banking sites.

If you aren't using firejail for all your web browsing, I'd encourage you to do so.  Also, I would use a different browser for the different types of online stuff you do.  Visiting facebook is **very** different from online banking or connecting to your work VPN. Compartmentalize where you can.

Use different logins where you can.  Linux is multi-user.  Take advantage of that segmentation. It is a powerful security tool.

Stay paranoid. Hopefully, it will be enough.

---

### Post by pointy2 on 2017-11-18
Thanks for all of this, Fu, I't's alot to consider, and am happy to know that I'm almost there with your suggestions. Can I ask about full disc encryption...is all data encryted for a remote attacker even after it's unlocked for my viewing? The side attacks have been  attempted in several cases, and have a few HD's and phones at the University forensics lab for analysis. I've heard much about Evil Maid, but have yet to read about it thoroughly...it does seem well named. 

According to your suggestions, I'm about at 99% and more. But, I just don't feel safe right now. A strong firewall rules, pass keys, daily checks for updates, and browser lockdowns through cofig all seem pretty good as of now. My feeble attempt to install and config Lynis is hampering any reassurance about security. 

....the irony is that for years I had no idea that the www was so full of psychopaths with nothing better to do, all the while running Wintel and feeling secure with an AV. I may just be inspired and motivated for a new career......

---

### Post by TheFu on 2017-11-18
For browser security, nothing helps more than disabling javascript and running in a firejail sandbox with limited access to the file system.

FDE is unlocked for everyone just after boot.  Data is only encrypted when the system is powered off.

firewalls are overrated, IMHO.  "Strong" can mean anything.  Blocking inbound AND outbound is necessary.

I think daily checks for updates is counter-productive.  When there is an issue, it becomes harder to determine the root cause. I like weekly patching, so I know when something breaks, it is likely due to a patch.

Also, my #1 security technique is versioned backups using a non-disk-sharing method.

AV is about 50% effective on Windows.  Running 3 different AV products gets to 80% effective.

If you are traveling overseas, start and end each trip with a wiped computer and smartphone.  Nothing else is very effective.  Use a remote desktop to access whatever data you need. Don't take it with you and definitely don't have email, CSM, CRM, or any other web-app configured for auto login.  For international travel, a chromebook makes lots of sense, but only if you can prevent google from pushing updates (which I don't think is possible).

People trying to make money off others aren't psychopaths. They just want money and the less time it takes to get, the better.

Phones are a completely different issue.  I don't believe it is possible to lock down any smartphones. The network provider can load firmware, which can do almost anything.  Just because the FBI can't break into a phone, that doesn't mean nobody can.

---

### Post by litlesam on 2017-11-19
I must use public wifi on the road and this has help me out time after time.

A few dnscrypt links and addresses.

[http://www.webupd8.org/2014/08/encrypt-dns-traffic-in-ubuntu-with.html](http://www.webupd8.org/2014/08/encrypt-dns-traffic-in-ubuntu-with.html)

[https://github.com/jedisct1/dnscrypt-proxy/blob/master/dnscrypt-resolvers.csv](https://github.com/jedisct1/dnscrypt-proxy/blob/master/dnscrypt-resolvers.csv)

Do everything posted from TheFu as well. 

He's definitively extremely smart!

---

### Post by bashiergui on 2017-11-22
What is the specific threat that worries you?

---

### Post by pointy2 on 2017-11-22
My concern is this....
As for the nation state thing, I couldn't care less, as while I demand privacy as a libertarian, I'm not out to do anything wrong or illegal. I'm only a guy who uses his pc for business, writing, and graphical works. I'd be guite boring to the alphebit agencies. 
What I need to accomplish is keeping a twisted stalker who is actively harrassing and tracking me from knowing my whereabouts, who and what I'm talking to and writing about. The good feeling is that while she is looking for something to blackmail me with, after a prolonged tracing by pi's, she still can't find anything. Ha! go figure! 

This time, it's gonna be me to hire a hacker....to break in to my system and alert me of the weakness to patch and protect. It's the creep factor from an unscrupulous twisted jerk who can't control me so they control how others see me. Think malignant Narcissist!

I'm still looking for an answer to my OP.

---

### Post by bashiergui on 2017-12-01
> **pointy2 said:**
> [B]Can a hostile attack 'ride in' to the target system on the wifi signal to establish a remote connection, or to corrupt/view file system? with these security measures?

[/B]I'm concerned about keyloggers, screen captures, installing other spyware on the system. Not concerned about LE or nation states, but rather talented hackers on a mission. (Yes, I am paranoid about this (for good reason)
IMO you should file a report with law enforcement as the sort of stalking you’re describing is serious and alarming.

The short answer is yes, it is **possible. **The** liklihood **depends on how knowledgeable and determined your stalker is. A solid defense is to make sure all your https sessions are actually secure. See this for more detail: [https://scotthelme.co.uk/wifi-pineapple-karma-sslstrip/](https://scotthelme.co.uk/wifi-pineapple-karma-sslstrip/)

But that’s just one route in. Hackers use any vulnerability they can find so I recommend you focus on a broader comprehensive security posture instead of focusing on one particular possibility. Thefu provided extensive advice on what you can do to make it harder for a hacker, which in the end is really all anyone can do to defend themselves. In addition you can heed the advice in the sticky posts in the security forum.

---

### Post by pointy2 on 2017-12-02
Thanks for your empathy on this matter, bashiergui. Yes, it is alarming in the fact that it comes from someone I have trusted during my entire life. Local LE tell me to notify the feds, since it's a multi-state offense. As for the link you provided, I'm on the site now, and will study any recommendations set forth. I've learned alot about computer security, and realize just how naive I've been about the popular OS that is at the forefront of consumerism.

---

