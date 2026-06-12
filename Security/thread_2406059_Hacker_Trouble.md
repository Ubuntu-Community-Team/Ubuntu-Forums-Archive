---
title: "Hacker Trouble"
date: 2018-11-15
forum: Security
---

### Post by skyesharica on 2018-11-15
Hi, I've had a very sophisticated hacking scammer access my bank user names and passwords. The banks told me, that because he used remote access software, I should get an I.T. expert in to be sure that I haven't got any new viruses or malware etc from him. I can't get an answer from I.T. people because they charge for a call out, and then give you answers ... you pay, even if it was an unnecessary trip. I don't think it's needed because these hackers wouldn't be able to get into the Linux software. As far as I know there are no known viruses or bad programs for Linux. Can anyone advise me. I am a struggling author with extreme health issues, and so the cost is killing me.  ;)

---

### Post by slickymaster on 2018-11-15
*Thread moved to **Security**.*

---

### Post by TheFu on 2018-11-15
Linux does have viruses and remote access malware. There are also remote access bugs for systems which haven't been maintained/patched. A smart user is the first line of defense on any computing system connected to the internet.

For online financial needs, follow Brian Krebs advice: [https://krebsonsecurity.com/online-banking-best-practices-for-businesses/](https://krebsonsecurity.com/online-banking-best-practices-for-businesses/)

It is too hard to tell someone all the things they should do to secure their online accounts in this medium.  But the big ones are:
* Always run a supported, patched, and backed up OS.
* Never use the same credentials to access any financial account anywhere else.
* Use a password manager to keep your long, random, credentials safe. Today, I like KeePassXC.  I would avoid any password manager that uses a cloud storage option. Why would anyone post their passwords to the cloud?
* Use a different email address for financial accounts than you use any where else. 
* If you know the password to your bank/brokerage accounts, then it isn't long, complex, random enough.
* I use the longest random password possible for all banking accounts. For some that is 10 characters (their limitation), for others it is 40+ characters.  I'm never going to type these in anyway, so why not make them long and random?
* If your financial institution supports 2FA, use it.
* Do not tie a cellular phone number to your bank account and only use SMS for 2FA if there isn't any other choice. Cloning of cellular SIM chips is real.  People can use them to gain access to any of your accounts.
* Do not use the same browser for banking that you use for everything else.  I use chromium for banking with a firejail sandbox set to --private mode.  For nominal daily use, I use firefox on a different system.
* For all password reset questions, lie.  Never tell the truth.  Store these lies in the password manager.
** Your favorite pet?  wrwaf6234asf2342qesafdad909823^
** Your high school mascot?  edfsa32324213$%124qe8f8djngegler

One of my banks doesn't allow very long passwords, so I made the login name long and random.  I have no idea what my login name+password are for that account. The password is very random. The email address is unique to that account only. My other financial accounts use a security FOB device with a code that changes every minute for the 2FA.

For more specific Linux security things, review the sticky posts at the top of the Security sub-forum here and review the Basic Ubuntu Security page: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

If you think your system has been hacked, then safe any data you can't live without and wipe the computer.  While I cannot speak for the bank who claimed your system was hijacked and that provided access to your bank account, if that happened, it was probably accomplished either through running WINE or by using some javascript + a browser addon/plugin.  The methods spelled out by Krebs will mitigate those issues.

If your system has been compromised, wipe it. It cannot be trusted.

---

### Post by bashiergui on 2018-11-15
How did the hacker get your username and password? Also ask the banks what remote access software the hacker used. Knowing the answers can help you determine if you are at risk.

---

### Post by skyesharica on 2018-11-15
> **bashiergui said:**
> How did the hacker get your username and password? Also ask the banks what remote access software the hacker used. Knowing the answers can help you determine if you are at risk.
Thanks. The hacker used TeamViewer and AnyDesk software to gain remote access to my PC, and he made me log into my bank accounts. He was incredibly professional will all sorts of evidential screens saying I was under attack and he was going to catch the hacker - representing Telstra. The banks aren't I.T. experts. I've just uninstalled those two remote software packages. Do you think I'm at risk? :KS

---

### Post by again? on 2018-11-15
You didn't allow someone to remotely connect to your computer did you?
One of the most well known scams going around.
Indian accent by chance?
The evidence and instructions they provide is usually related to windows though.
[https://www.youtube.com/watch?v=XoIU0KKg0qA](https://www.youtube.com/watch?v=XoIU0KKg0qA)

---

### Post by skyesharica on 2018-11-15
> **guber2 said:**
> You didn't allow someone to remotely connect to your computer did you?
One of the most well known scams going around.
Indian accent by chance?
The evidence and instructions they provide is usually related to windows though.
[https://www.youtube.com/watch?v=XoIU0KKg0qA](https://www.youtube.com/watch?v=XoIU0KKg0qA)
  
Yes I did and yes he was Indian. Luckily I worked it out quickly and made my three bank accounts inaccessible, and am changing passwords etc. Thankyou.

---

### Post by skyesharica on 2018-11-15
> **TheFu said:**
> Linux does have viruses and remote access malware. There are also remote access bugs for systems which haven't been maintained/patched. A smart user is the first line of defense on any computing system connected to the internet.

For online financial needs, follow Brian Krebs advice: [https://krebsonsecurity.com/online-banking-best-practices-for-businesses/](https://krebsonsecurity.com/online-banking-best-practices-for-businesses/)

It is too hard to tell someone all the things they should do to secure their online accounts in this medium.  But the big ones are:
* Always run a supported, patched, and backed up OS.
* Never use the same credentials to access any financial account anywhere else.
* Use a password manager to keep your long, random, credentials safe. Today, I like KeePassXC.  I would avoid any password manager that uses a cloud storage option. Why would anyone post their passwords to the cloud?
* Use a different email address for financial accounts than you use any where else. 
* If you know the password to your bank/brokerage accounts, then it isn't long, complex, random enough.
* I use the longest random password possible for all banking accounts. For some that is 10 characters (their limitation), for others it is 40+ characters.  I'm never going to type these in anyway, so why not make them long and random?
* If your financial institution supports 2FA, use it.
* Do not tie a cellular phone number to your bank account and only use SMS for 2FA if there isn't any other choice. Cloning of cellular SIM chips is real.  People can use them to gain access to any of your accounts.
* Do not use the same browser for banking that you use for everything else.  I use chromium for banking with a firejail sandbox set to --private mode.  For nominal daily use, I use firefox on a different system.
* For all password reset questions, lie.  Never tell the truth.  Store these lies in the password manager.
** Your favorite pet?  wrwaf6234asf2342qesafdad909823^
** Your high school mascot?  edfsa32324213$%124qe8f8djngegler

One of my banks doesn't allow very long passwords, so I made the login name long and random.  I have no idea what my login name+password are for that account. The password is very random. The email address is unique to that account only. My other financial accounts use a security FOB device with a code that changes every minute for the 2FA.

For more specific Linux security things, review the sticky posts at the top of the Security sub-forum here and review the Basic Ubuntu Security page: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

If you think your system has been hacked, then safe any data you can't live without and wipe the computer.  While I cannot speak for the bank who claimed your system was hijacked and that provided access to your bank account, if that happened, it was probably accomplished either through running WINE or by using some javascript + a browser addon/plugin.  The methods spelled out by Krebs will mitigate those issues.

If your system has been compromised, wipe it. It cannot be trusted.

Thankyou. I've read your links and am reassured that Linux malware is very rare. But it does exist, and easily could after a professional hacker on remote software. So I found a link to Sophos ([https://www.sophos.com/en-us/products/free-tools/sophos-antivirus-for-linux.aspx](https://www.sophos.com/en-us/products/free-tools/sophos-antivirus-for-linux.aspx)) anti malware software for Ubuntu 18. Quite a download. I don't mean to be rude or unappreciative of your extremely kind and lengthy response, but I would go nuts if I followed all those rules, and had passwords and questions etc that were that long, and full of numbers, and separate email addresses for finance. What if there was a cut and paste problem? Or you lost the file. You'd never be able to slowly work it out from memory. I don't know how to back up my O.S. Do you - in simple words please? I agree with you, about Cloud. Ubuntu doesn't have it and I don't miss it. I never crash, and I have good old reliable backup CDs.  :confused:

---

### Post by again? on 2018-11-15
A fresh install of Ubuntu would be the basic minimum.
For security I use a separate browser for banking and don't let the browser save the password.
I store passwords in keepassx as it's database can be used in Android with keepassdroid.
I don't do automatic backups.
Some important files that change I use [Megasync]("https://mega.nz/sync") to do cloud backups otherwise I do a couple of manual backups(copy/paste)
to another drive and usb stick.
...and I hang up when someone with an Indian accent called "Trevor" wants to inform me that my computer is under attack. :p

---

### Post by skyesharica on 2018-11-15
> **guber2 said:**
> A fresh install of Ubuntu would be the basic minimum.
...and I hang up when someone with an Indian accent called "Trevor" wants to inform me that my computer is under attack. :p
Yes, that's funny, I should have hung up on 'Rex'. He was incredibly professional with all sorts of prepared screens that looked very legit. Can you tell me the easiest way to do a fresh install of Ubuntu? :P

---

### Post by CharlesA on 2018-11-15
> **skyesharica said:**
> Thanks. The hacker used TeamViewer and AnyDesk software to gain remote access to my PC, and he made me log into my bank accounts. He was incredibly professional will all sorts of evidential screens saying I was under attack and he was going to catch the hacker - representing Telstra. The banks aren't I.T. experts. I've just uninstalled those two remote software packages. Do you think I'm at risk? :KS

I would wipe the machine and reinstall.

Then restore from backups.

As far as making those backups, this might help, might not: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Personally, I use [borgbackup]("https://borgbackup.readthedocs.io/en/stable/installation.html") and do daily backups to an external drive.

If I want to back up my entire OS installation, I'll use Clonezilla or tar. Clonezilla might work better for you.

> **skyesharica said:**
> Yes, that's funny, I should have hung up on 'Rex'. He was incredibly professional with all sorts of prepared screens that looked very legit. Can you tell me the easiest way to do a fresh install of Ubuntu? :P

Get a fresh ISO from [here]("http://releases.ubuntu.com/bionic/") and either burn it to a DVD or create a live USB drive. See here: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0)

---

### Post by QIII on 2018-11-15
At this point I'd say not to bother with a full OS backup.  You'd just have a compromised backup.  Back up only the files you can't afford to lose and just re-install the OS fresh.

---

### Post by skyesharica on 2018-11-15
> **CharlesA said:**
> I would wipe the machine and reinstall.

Then restore from backups.

As far as making those backups, this might help, might not: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Personally, I use [borgbackup]("https://borgbackup.readthedocs.io/en/stable/installation.html") and do daily backups to an external drive.

If I want to back up my entire OS installation, I'll use Clonezilla or tar. Clonezilla might work better for you.



Get a fresh ISO from [here]("http://releases.ubuntu.com/bionic/") and either burn it to a DVD or create a live USB drive. See here: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0)

Thanks a lot. I'll do that. The Sophos Anti Malware software was totally confusing and I couldn't install it.

> **QIII said:**
> At this point I'd say not to bother with a full OS backup.  You'd just have a compromised backup.  Back up only the files you can't afford to lose and just re-install the OS fresh.

Thanks. But isn't there a Malware software that works. The Sophos system was a nightmare - there were all sorts of instructions about 'tarball' etc etc, and you couldn't find it anywhere, and the download took ages and just opens with archive manager. I have no idea what's going on with it. Is it really necessary to do this clean system reinstall? Is there any easier way I can find out if that man put bad software on my computer?  :o

---

### Post by QIII on 2018-11-15
Reinstall.  A compromised system can never again be trusted, even with all the scanning under the Sun.

Just call it a Rule learned by many, many of us over many years.

---

### Post by again? on 2018-11-15
Out of curiosity was the hacker able to login to your bank account or did the bank pick up on it
before any damage done.

---

### Post by TheFu on 2018-11-15
Nothing teaches security better than being hacked.

I wouldn't trust any malware seeking software on Linux. The system is extremely flexible and placing/hiding a reverse shell is extremely easy.  Once someone had a remote desktop/remote shell into your system, they only need 3 seconds to take over and setup a minimal method to regain remote access. Making that reoccur every 6 hours or daily or 475 minutes would be trivial.

I was hacked in 2002-ish.  The way I found what they did was to compare the current system to a backup make 7 days earlier.  Without a backup that is known good, unmolested, I don't know of any other method.  They had buried some tools under multiple hidden directories spread all over the file system. Unfortunately for them, they decided to try and escalate privileged to get root and every attempt sent an email to me.  I woke up with 14,000+ emails.  Without those emails, I may have never noticed.

I don't copy/paste login credentials.  A good password manager uses something called "autotype" to enter them after I specifically ask for that to happen.  Clearly, having multiple backup copies of that file is mandatory.  I push it to multiple systems, 2 are at different addresses, using rsync every night.  AES-256 encryption is good.

Ubuntu has as much cloud support as you like or none. Pretty much every cloud provider on the internet is running on Linux. We can run as many cloud services as we want on our own.  But not everyone has that desire, which is fine.

You cannot trust that machine.  Is reinstalling really a big deal?  Should be 15 minutes for the install, then restoring the extra files should be 15-30 minutes more.

---

### Post by skyesharica on 2018-11-16
> **guber2 said:**
> Out of curiosity was the hacker able to login to your bank account or did the bank pick up on it
before any damage done.

He had screens that we could both access. He asked me to put in my login details, so he could put money in my account, in a complex plan to 'catch the hackers' that he was protecting me from. He was extremely professional. The error/hacking screens, and all the screens looked very legit. It was very high end. But when I got wise, he lost it, and phoned me 10 times, as I rejected calls. I seriously don't know what slowed him down. He transferred money from one account to another, within the same bank, but something stopped him doing anything else. I finished my online grocery shopping etc, and budget, before I cancelled my accounts. LOL. ):P

> **QIII said:**
> Reinstall.  A compromised system can never again be trusted, even with all the scanning under the Sun.

Just call it a Rule learned by many, many of us over many years.

Yes, thankyou, I'm doing that right now. It's such a hassle but it's the simplest solution. Cheers :P

> **TheFu said:**
> Nothing teaches security better than being hacked.

I wouldn't trust any malware seeking software on Linux. The system is extremely flexible and placing/hiding a reverse shell is extremely easy.  Once someone had a remote desktop/remote shell into your system, they only need 3 seconds to take over and setup a minimal method to regain remote access. Making that reoccur every 6 hours or daily or 475 minutes would be trivial.

I was hacked in 2002-ish.  The way I found what they did was to compare the current system to a backup make 7 days earlier.  Without a backup that is known good, unmolested, I don't know of any other method.  They had buried some tools under multiple hidden directories spread all over the file system. Unfortunately for them, they decided to try and escalate privileged to get root and every attempt sent an email to me.  I woke up with 14,000+ emails.  Without those emails, I may have never noticed.

I don't copy/paste login credentials.  A good password manager uses something called "autotype" to enter them after I specifically ask for that to happen.  Clearly, having multiple backup copies of that file is mandatory.  I push it to multiple systems, 2 are at different addresses, using rsync every night.  AES-256 encryption is good.

Ubuntu has as much cloud support as you like or none. Pretty much every cloud provider on the internet is running on Linux. We can run as many cloud services as we want on our own.  But not everyone has that desire, which is fine.

You cannot trust that machine.  Is reinstalling really a big deal?  Should be 15 minutes for the install, then restoring the extra files should be 15-30 minutes more.

Thanks, my friends here have been good to me. I am in the process of a clean install now. It usually takes me half the day! That's extremely frightening and useful information. With passwords etc I think I'll keep them fairly uncomplex because I've never experienced this before, and I hate complexity, and there's some basic security online at places like banks and PayPal.

---

### Post by bashiergui on 2018-11-16
The biggest threat remaining is the hacker has several sets of credentials you used at the banks. If you use those username and password combinations anywhere else, you need to change them all. It&#8217;s best if passwords are complex, but at the very least make sure each site has a unique password. 

You mentioned Paypal: turn on two-factor authentication there. That&#8217;s when they text you a code when you log in. Here&#8217;s how to do that [https://www.paypal.com/us/smarthelp/article/how-do-i-enable-2fa-(two-factor-authentication)-for-my-paypal-powered-by-braintree-user-faq3500](https://www.paypal.com/us/smarthelp/article/how-do-i-enable-2fa-(two-factor-authentication)-for-my-paypal-powered-by-braintree-user-faq3500)

If you want to avoid complex and unique passwords, then please turn on two-factor authentication on every site you can.

---

### Post by skyesharica on 2018-11-16
> **bashiergui said:**
> The biggest threat remaining is the hacker has several sets of credentials you used at the banks. If you use those username and password combinations anywhere else, you need to change them all. It&#8217;s best if passwords are complex, but at the very least make sure each site has a unique password. 

You mentioned Paypal: turn on two-factor authentication there. That&#8217;s when they text you a code when you log in. Here&#8217;s how to do that [https://www.paypal.com/us/smarthelp/article/how-do-i-enable-2fa-(two-factor-authentication)-for-my-paypal-powered-by-braintree-user-faq3500](https://www.paypal.com/us/smarthelp/article/how-do-i-enable-2fa-(two-factor-authentication)-for-my-paypal-powered-by-braintree-user-faq3500)

If you want to avoid complex and unique passwords, then please turn on two-factor authentication on every site you can.

Hi. I'm still restoring my system. The software went crazy. Then I had to fix up all my files and update the software, and get two software packages. It takes half a day.

Thanks, yes, the credentials are in the process of being changed at all three banks. The worst was the CBA which locks your account for a month! Just checking that my credentials are all fairly different.

Thanks, I've just got an extra code or whatever with my mobile at Paypal.

---

### Post by mohicann on 2018-11-16
> **skyesharica said:**
> As far as I know there are no known viruses or bad programs for Linux.

Once you know it isn't true, you're already more secure. Because you won't keep thinking you have nothing to do to be safe on Internet behind a Linux box. From my personal experience, I've seen two rootkits in my life (no matter under which circumstances), both running root privileges, the first one being the most sophisticated, and probably among the most sophisticated we can find on a Linux release : a full rootkited kernel (a kernel rebuilt to allow a full attacker access without being detected by almost anyone and anything), and the second one, something running from userland with root privileges. 

Have a look at this, and those are only the disclosed ones : [https://github.com/milabs/awesome-linux-rootkits](https://github.com/milabs/awesome-linux-rootkits)

---

### Post by TheFu on 2018-11-16
Nothing can replace a smart end-user.  Nobody will ever call you to help with computer security.  If you don't call them, they are trying to steal something.  Nobody you haven't met and trust in real life will ever ask for remote access into your computers.

I'd be worried if anyone watched me enter credentials into any financial account.  Just because ***** shows up on the screen, it doesn't mean they didn't have a keylogger running.  I would have changed all my financial login within the next 15 minutes and hoped that they weren't already cleaned out.   If you haven't already, put a credit freeze on your accounts ASAP.  In the USA, here's how: [https://krebsonsecurity.com/2018/09/credit-freezes-are-free-let-the-ice-age-begin/](https://krebsonsecurity.com/2018/09/credit-freezes-are-free-let-the-ice-age-begin/)   Don't let any other term offered by the agencies confuse you.  "CREDIT FREEZE" is the only thing you want. They will other stuff that sounds good or similar.  But the laws work in your favor with a credit freeze.

---

### Post by skyesharica on 2018-11-16
> **mohicann said:**
> Once you know it isn't true, you're already more secure. Because you won't keep thinking you have nothing to do to be safe on Internet behind a Linux box. From my personal experience, I've seen two rootkits in my life (no matter under which circumstances), both running root privileges, the first one being the most sophisticated, and probably among the most sophisticated we can find on a Linux release : a full rootkited kernel (a kernel rebuilt to allow a full attacker access without being detected by almost anyone and anything), and the second one, something running from userland with root privileges. 

Have a look at this, and those are only the disclosed ones : [https://github.com/milabs/awesome-linux-rootkits](https://github.com/milabs/awesome-linux-rootkits)

Thanks, that's awful to know. I'll probably never know what a root is so I didn't enjoy the link. :P

---

### Post by TheFu on 2018-11-16
> **skyesharica said:**
> Thanks, that's awful to know. I'll probably never know what a root is so I didn't enjoy the link. :P

To **root a computer**, it to gain access to the root userid.  That userid is all-powerful and ubuntu people generally only access it via sudo.  

With local or remote root access, the computer is completely pwn'd - that's the term hackers use to say they can do anything on a system.   "I totally pwn'd that Gibson."  While a good thing from the hacker's viewpoint, it is a terrible thing for the owner of the computer.

---

### Post by skyesharica on 2018-11-16
> **TheFu said:**
> Nothing can replace a smart end-user.  Nobody will ever call you to help with computer security.  If you don't call them, they are trying to steal something.  Nobody you haven't met and trust in real life will ever ask for remote access into your computers.

I'd be worried if anyone watched me enter credentials into any financial account.  Just because ***** shows up on the screen, it doesn't mean they didn't have a keylogger running.  I would have changed all my financial login within the next 15 minutes and hoped that they weren't already cleaned out.   If you haven't already, put a credit freeze on your accounts ASAP.  In the USA, here's how: [https://krebsonsecurity.com/2018/09/credit-freezes-are-free-let-the-ice-age-begin/](https://krebsonsecurity.com/2018/09/credit-freezes-are-free-let-the-ice-age-begin/)   Don't let any other term offered by the agencies confuse you.  "CREDIT FREEZE" is the only thing you want. They will other stuff that sounds good or similar.  But the laws work in your favor with a credit freeze.

Yes, I should have been faster. I don't know what slowed him down.

---

