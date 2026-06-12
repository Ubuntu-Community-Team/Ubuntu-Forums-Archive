---
title: "Taking Charge of Security at a Web Development Agency"
date: 2017-03-24
forum: Security
---

### Post by branau on 2017-03-24
Hi everyone, looking for a bit of advice here. I work at a small web development agency that specializes WordPress and Magento site development. We're growing pretty rapidly though, and I've brought up on multiple occasions that we need to place more emphasis on security at the firm, as we currently are a bit too lenient with it in my opinion. We don't actually have anyone dedicated to security policies and procedures at the moment, as it's pretty much just developers and a couple sysadmins. That changed today, however, when I had a meeting with my boss where he told me that I would be placed in charge of running security from now on. I've been doing development and sysadmin work for about 2 years now, and I was just about to start getting into DevOps stuff. I've got the Security+ certification from CompTIA, the Linux Sysadmin Certification from The Linux Foundation, and the Android Associate Developer certification from Google. I'm certainly not anywhere near an expert in security but I'm not expected to be one at this point. I need to grow into this role though, so where do I even begin? Google searches all say the same thing: begin with Linux/networking/maybe some coding, and then go for certifications and whatnot. I've got a pretty good understanding of Linux, networking, and code, so I'm pretty confident that I'm good on those areas. I've got the Security+ cert so I have a basic understanding of security policies and business continuity plans and all that jargon, but how do I take a tech firm with little-to-no security practices and build up from here? More importantly, how do I grow as a security specialist so that I don't screw this up? 

Also, I would love to find some kind of mentor in security. I've found something similar for development: [https://www.codementor.io/](https://www.codementor.io/) I would just love to be able to meet with someone once or twice a month to make sure that I'm not completely lost and that I'm moving in the right direction. If anyone knows of such a thing, I would love to hear about it!

---

### Post by TheFu on 2017-03-24
* don't let developers have sudo.
* only allow access from the outside via VPN - IPSec, never PPTP.
* use 2FA for everything.
* don't allow php on the internet - as this is your core product, I suspect you don't be able to do this.
* follow the policy of least permissions. Nobody gets more privileges than needed on a system to do their job. NEVER sudo nor root.  They can do their jobs without it.

Get to some SANS training.  Not trying to be rude, but Security+ is beginning, beginning, level stuff.

Your boss knows that you are in over your head and expects you to give in easily to demands when you shouldn't.  He is side-stepping an issue, so when something bad happens (and it will), that it isn't his fault.

Get to work on security policies. Get them approved by upper management BEFORE unleashing them on the dev teams.  SANS has example corporate security policies. Violation of the terms needs clear, aggressive penalties.  1st time, a warning. 2nd time, termination. Get everything in writing. Put it in writing. Get each individual to sign the policy so ignorance isn't possible later. If management doesn't provide teeth, you can't do your job.

Security rules will make some things slower. This is a feature. 

Honestly, it takes at least 5 yrs to grow into a security management position while being mentored by someone senior.  It is important to be flexible, but know when to refuse and say no.  That can only be learned by experience, over time, from someone else who has been there inside an organization like yours.

[https://www.sans.org/](https://www.sans.org/) - there is a conference in Orlando in 2 weeks. Get there.  Ask real security professionals your questions.  In August, there's DefCon in Las Vegas - go.  Get your tickets and time off now.  The company should be paying for these things.

You've just been given lots of responsibility, probably with very little control over anything.  Start with the standard things - access controls, physical security, backup policies, and secure coding standards. For the coding standards, be certain the OWASP Top 10 for your language/stack is included.  Php has a terrible reputation with security professionals for multiple reasons.

DevSecOps is a thing too.  That's where a security guy is added to the DevOps team to ensure those methods include security considerations.

If the best developer in the company was fired today, can you completely shut off all access to corporate and client systems within 30 minutes?  That should be a requirement.

I've seen security teams inside companies do great things, but only when upper management was behind them.  I've also seen where development-centric companies needed a figurehead for security, but really didn't plan to change anything.  If that is the case at your company, be certain the severance package covers your needs for a few years.

---

### Post by bashiergui on 2017-03-27
Excellent advice from TheFu. I would add risk acceptances. When you escalate a security recommendation, include a risk acctance for management to sign if they choose not to implement your recommendation. That will cover your butt and it will make them think twice before ignoring you. 

Don't forget the simplest defense for Magento and WordPress is to patch. If they choose to delay patching then get a risk acceptance.

---

### Post by SeijiSensei on 2017-03-28
First rule is to install WordPress updates whenever they are released.  

You can improve the security of WP by limiting write access to its directories.  That will make it impossible for WP to upgrade automatically, but you should receive a notice by email when an update is released, and logging into a site's dashboard will notify you as well.

My WP installations are all owned by an ordinary user and the Apache user's group, called www-data on Ubuntu.  Before I run a manual update of WP, I run this little script at the top of the WordPress tree:
```
#!/bin/sh
chmod g+w wp-admin wp-includes wp-content -R
chmod g+w *
echo "Run update now"

```
Then I run the update from the WP dashboard.  When it's done, I run this script:
```

#!/bin/sh
chmod g-w wp-admin wp-includes wp-content -R
chmod g-w *

```
That grants write privileges to the Apache server so it can update the WP files, then removes those privileges when done.  The only directories that need to have write privileges granted to the server are wp-content/uploads/YEAR/MONTH.  On my sites these directories are owned by Apache; everything else is owned by an ordinary, unprivileged user.  All the other content is stored in the site's MySQL database.

Now that I have three or four WP sites running, I'm going to look into have a single consolidated installation with separate content directories for each site.  I don't know how hard that will be to manage, or even if it's possible.  WordPress seems to like having a complete unique copy of itself in each site.  That makes updating a pain since you have to do it multiple times.  There might be a way to automate the process with a script that traverses the sites then downloads and installs the update in each one.  Haven't tried that approach yet either.

---

### Post by TheFu on 2017-03-28
Forgot to mention this - there are "defcon groups" in many major metro areas. [https://defcongroups.org/dcpages.html#international](https://defcongroups.org/dcpages.html#international) Hopefully, you can find one near your location. Go. Meet those people. Wear a black t-shirt and jeans/shorts so you fit in. Casual.  Security people everywhere are pretty much the same. They want to help, but also have a little devil inside. ;)

There are other security organizations - [2600 groups]("https://www.2600.com/meetings/mtg.html"), [ISSA]("http://www.issa.org/"), and you'll hear about more.  

[OWASP Top 10 project]("https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project").

At the Defcon group I attend, we have a monthly competition called [KoTH]("https://www.irongeek.com/i.php?page=security/network-king-of-the-hill-write-ups"). It is a CTF game about hacking into 5+ different servers and pwoning them while others are also attacking.  Anything is far game, except physical access to the servers.  Hacking the other guys is popular. ;)  Teaches offensive AND defensive methods - especially when your system gets cracked by another team!

If you go to these meetings (or any security meeting) a few tips:
* if you bring any device to the meetings, make a 100% backup prior. This applies to phones, tablets, portable routers, APs and computers.
* disable all bluetooth
* disable all networking - ethernet, wifi, GSM, LTE, ... anything.
* probably want to turn your phone off - I've seen people with GSM simulators doing MITM for cellular data.
Just attending, even if you aren't participating in the events, makes your stuff a target.

---

### Post by branau on 2017-04-02
First, thank you all for your responses! I really appreciate the advice.

> **TheFu said:**
> * don't let developers have sudo.
* only allow access from the outside via VPN - IPSec, never PPTP.
* use 2FA for everything.
* don't allow php on the internet - as this is your core product, I suspect you don't be able to do this.
* follow the policy of least permissions. Nobody gets more privileges than needed on a system to do their job. NEVER sudo nor root.  They can do their jobs without it.

Get to some SANS training.  Not trying to be rude, but Security+ is beginning, beginning, level stuff.

Your boss knows that you are in over your head and expects you to give in easily to demands when you shouldn't.  He is side-stepping an issue, so when something bad happens (and it will), that it isn't his fault.

Get to work on security policies. Get them approved by upper management BEFORE unleashing them on the dev teams.  SANS has example corporate security policies. Violation of the terms needs clear, aggressive penalties.  1st time, a warning. 2nd time, termination. Get everything in writing. Put it in writing. Get each individual to sign the policy so ignorance isn't possible later. If management doesn't provide teeth, you can't do your job.

Security rules will make some things slower. This is a feature. 

Honestly, it takes at least 5 yrs to grow into a security management position while being mentored by someone senior.  It is important to be flexible, but know when to refuse and say no.  That can only be learned by experience, over time, from someone else who has been there inside an organization like yours.

[https://www.sans.org/](https://www.sans.org/) - there is a conference in Orlando in 2 weeks. Get there.  Ask real security professionals your questions.  In August, there's DefCon in Las Vegas - go.  Get your tickets and time off now.  The company should be paying for these things.

You've just been given lots of responsibility, probably with very little control over anything.  Start with the standard things - access controls, physical security, backup policies, and secure coding standards. For the coding standards, be certain the OWASP Top 10 for your language/stack is included.  Php has a terrible reputation with security professionals for multiple reasons.

DevSecOps is a thing too.  That's where a security guy is added to the DevOps team to ensure those methods include security considerations.

If the best developer in the company was fired today, can you completely shut off all access to corporate and client systems within 30 minutes?  That should be a requirement.

I've seen security teams inside companies do great things, but only when upper management was behind them.  I've also seen where development-centric companies needed a figurehead for security, but really didn't plan to change anything.  If that is the case at your company, be certain the severance package covers your needs for a few years.

This is all a lot to take in, so I'm working on things one at a time. Thanks a lot for the advice! I really appreciate it. SANS training in Orlando isn't going to happen, at least not sponsored by the company and I don't have the money to get myself there. I've requested for them to send me to Las Vegas for DefCon though, since that's a little further out in the year. Honestly I'm not sure what this "promotion" is all about, considering I'm really just a freelancer. Granted, I have been working full time with them for about a year now, but at the end of the day, I'm not even truly an employee of theirs. Maybe that's why actually, they don't have to provide me with any sort of a severance package.

Unfortunately I'm afraid I'm going to end up just being the guy they point fingers at when something goes wrong, and I'm afraid very little will actually change because of my recommendations. Might be time to cut this job back to part time and fill up the other half of my time with other freelance jobs to prevent a huge loss in income if and when I get blamed for an incident and terminated.

> **bashiergui said:**
> Excellent advice from TheFu. I would add risk acceptances. When you escalate a security recommendation, include a risk acctance for management to sign if they choose not to implement your recommendation. That will cover your butt and it will make them think twice before ignoring you. 

Don't forget the simplest defense for Magento and WordPress is to patch. If they choose to delay patching then get a risk acceptance.

I will definitely have to add this. As it is right now, I have to draw attention to updates and most of the time they don't get released immediately because of stability concerns. So usually what happens is when someone finally realizes there's an update, they mention it and it gets added to the development queue but it's unfortunately never the highest priority. So I'll be making sure this gets into the policies.

> **SeijiSensei said:**
> First rule is to install WordPress updates whenever they are released.  

You can improve the security of WP by limiting write access to its directories.  That will make it impossible for WP to upgrade automatically, but you should receive a notice by email when an update is released, and logging into a site's dashboard will notify you as well.

My WP installations are all owned by an ordinary user and the Apache user's group, called www-data on Ubuntu.  Before I run a manual update of WP, I run this little script at the top of the WordPress tree:
```
#!/bin/sh
chmod g+w wp-admin wp-includes wp-content -R
chmod g+w *
echo "Run update now"

```
Then I run the update from the WP dashboard.  When it's done, I run this script:
```

#!/bin/sh
chmod g-w wp-admin wp-includes wp-content -R
chmod g-w *

```
That grants write privileges to the Apache server so it can update the WP files, then removes those privileges when done.  The only directories that need to have write privileges granted to the server are wp-content/uploads/YEAR/MONTH.  On my sites these directories are owned by Apache; everything else is owned by an ordinary, unprivileged user.  All the other content is stored in the site's MySQL database.

Now that I have three or four WP sites running, I'm going to look into have a single consolidated installation with separate content directories for each site.  I don't know how hard that will be to manage, or even if it's possible.  WordPress seems to like having a complete unique copy of itself in each site.  That makes updating a pain since you have to do it multiple times.  There might be a way to automate the process with a script that traverses the sites then downloads and installs the update in each one.  Haven't tried that approach yet either.

That's not a bad idea. As it is right now, permissions are pretty closed to the web user itself because the devs need the ability to pull down the code from git but I think we could certainly tighten that down a bit. We're moving towards automated deployments so this should be even easier to implement. All updates have to go through git first for us anyways so the web server wouldn't need write access anyways.

As for the multiple instances of WordPress sharing the same code, we actually use the built-in multisite feature for that. It's a bit of a learning curve at first but once you have it up and running, you can manage all of your sites from a single dashboard and therefore update them all at the same time. This works for plugins as well. There's sort of an undocumented hack that you can do if they're on different domains too. The initial setup restricts you to just subdomain or subdirectory installations. If you go with subdomain installation though, you can later change the entire domain name and WordPress will still recognize it and forward the request accordingly.

> **TheFu said:**
> Forgot to mention this - there are "defcon groups" in many major metro areas. [https://defcongroups.org/dcpages.html#international](https://defcongroups.org/dcpages.html#international) Hopefully, you can find one near your location. Go. Meet those people. Wear a black t-shirt and jeans/shorts so you fit in. Casual.  Security people everywhere are pretty much the same. They want to help, but also have a little devil inside. ;)

There are other security organizations - [2600 groups]("https://www.2600.com/meetings/mtg.html"), [ISSA]("http://www.issa.org/"), and you'll hear about more.  

[OWASP Top 10 project]("https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project").

At the Defcon group I attend, we have a monthly competition called [KoTH]("https://www.irongeek.com/i.php?page=security/network-king-of-the-hill-write-ups"). It is a CTF game about hacking into 5+ different servers and pwoning them while others are also attacking.  Anything is far game, except physical access to the servers.  Hacking the other guys is popular. ;)  Teaches offensive AND defensive methods - especially when your system gets cracked by another team!
    
If you go to these meetings (or any security meeting) a few tips:
* if you bring any device to the meetings, make a 100% backup prior. This applies to phones, tablets, portable routers, APs and computers.
* disable all bluetooth
* disable all networking - ethernet, wifi, GSM, LTE, ... anything.
* probably want to turn your phone off - I've seen people with GSM simulators doing MITM for cellular data.
Just attending, even if you aren't participating in the events, makes your stuff a target.

Haha yeah I sort of figured that I would have to go without any electronics on me. I planned on taking a burner phone to let my wife know when I get there and when I leave and a notebook with a pen to make note of anything helpful/interesting. Unfortunately there are no groups in my area, as I'm in Mexico. Generally, even when there are groups/events here, they're in Mexico City, which is about 2-3 hours away from where I am.

---

