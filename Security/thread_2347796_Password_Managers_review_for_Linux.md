---
title: "Password Managers review for Linux"
date: 2016-12-28
forum: Security
---

### Post by llamabr on 2016-12-28
It's 2017, and it's finally time to do something about your passwords. I hope that you don't use '123456', even though the Ashley Madison hack revealed that this was the [most common password]("http://www.zdnet.com/article/these-are-the-worst-passwords-from-the-ashley-madison-hack/"). If you're old like me, you've had a yahoo account for about 20 years, and if so, your password there [was hacked recently]("http://www.nytimes.com/2016/09/23/technology/yahoo-hackers.html?_r=1") ([twice]("http://www.nytimes.com/2016/12/14/technology/yahoo-hack.html")). Even Obama wants you to [get rid of your passwords]("http://www.wsj.com/articles/protecting-u-s-innovation-from-cyberthreats-1455012003").

So I decided to start using a password manager (PM). A PM is a centralized database of your login details and password, either stored locally or in the cloud. They can also be used to store credit card information, addresses and contact info, and other private details. Thus, all of your passwords are protected by one master password, that you have to remember &#8211; the one that opens your PM. Also, usefully, most will generate and save a difficult, complex password, and then save it for you.

Q: Isn't a PM like putting all my eggs in one basket? That is, rather than opening myself to one hack, doesn't the use of a PM open me to the possibility of having all my PW's hacked?

A: Ostensibly, yes. In fact, one of the most popular PM sites, LastPass, was [hacked last year]("http://thehackernews.com/2016/07/lastpass-password-manager.html"). However, according to the site, all the hackers got was the encrypted data. So if users' passwords were complex (which they should be), hackers will not have access to the login details themselves. This lesson generalizes, so (1), you should pick a PM that encrypts your data, and that doesn't allow backdoors (by, for example, using[ open source software]("http://www.pcworld.com/article/2061918/some-password-managers-are-safer-than-others.html")), and your master password should be complex.

Q: Should I use a PM? That is, isn't it more secure to keep my complex passwords in my brain, change them often, and use unique logins and passwords for the dozens or hundreds of sites I routinely use?

A: Yes. However, most people cannot remember complex passwords (so they make them simple), don't change them often or ever (until last month, my yahoo password was unchanged since 1998!), and reuse login and passwords for multiple sites (I'll bet your login to this forum is the same as your bank information).

What I'm looking for is a PM that works across many devices and OS (including Linux, iOS, OSX, Android, and Windows), is open source, is free, or has premium versions, and is easy to use. I reviewed software that saves my credentials both locally and in the cloud. Here's what I came up with. Here's what I discovered.

[**KeePassX**]("https://www.keepassx.org/") A port to Linux of the older [KeePass]("https://www.reddit.com/r/Ubuntu/comments/25fq28/keepass2_vs_keepassx_on_ubuntu_which_one_is_better/") for Windows, is opensource (using the GNU General purpose license 2), has a simple interface, has a customizable tool to generate complex passwords, and is available for Android [here]("https://play.google.com/store/apps/details?id=com.android.keepass&hl=en") and [here]("https://play.google.com/store/apps/details?id=keepass2android.keepass2android") and [iOS]("http://appcrawlr.com/ios-apps/best-apps-keepass-database"). It's available in repos natively (apt-cache search keepassx). There's even a CLI for the database, which I've not tried. It can be set up to use a strong password, a[ PGP key]("https://forum.keepassx.org/viewtopic.php?t=81"), or both, which can be saved locally, or in the cloud, using a service such as [dropbox]("https://aegisnet.de/2015/02/10/securely-synchronize-keepassx-data-between-computers.html"). Here is a [full list of features]("https://forum.keepassx.org/viewtopic.php?t=81"), from their website. Autofill is available from additional browser addons.

Setup is simple. Install from the repos, and then run. Choose 'new database' and choose a password and/or key (or create a new key). After setting up your site, right click to copy username and password to site.

[**Encryptr**]("https://spideroak.com/solutions/encryptr") Edward Snowden recommended that we stop using Dropbox, which encrypts your data in transit, in favor of [SpiderOak]("https://spideroak.com/"), which also encrypts it while it's on your computer. SpiderOak's no-frills PM is called Encryptr. This is a cloud-based service, which does not store your keys on their server, making it impossible for anyone to obtain your data without your password. Features include the ability to create strong passwords, automatic sync between all devices (including Windows, OSX, Linux, Android and iOS), and the ability to search for passwords and notes (convenient for those who store hundred of files). Offline access to materials is currently not supported. 

Installation is easy. [Download the file]("https://spideroak.com/solutions/encryptr") and [install]("https://spideroak.com/solutions/encryptr"). (Notice that if you run from the cli, Encryptr starts with a capital &#8220;E&#8221;). Choose a username and passphrase. Choose &#8220;add&#8221; to add your site, login, and password.

[**LastPass**]("https://www.lastpass.com/") This service is available across all of your devices, but runs in the cloud. If you're concerned about this (see my note above), then choose another service. It has an easy to use, attractive configurable interface, makes it easy if you have many accounts on a single site (such as 3 different gmail accounts), and autofills passwords as you go (since it runs in the cloud). It also sets up quickly and free (since it runs in the cloud). The premium service supports 1 gig of storage, fingerprint identification, and support for multiple users. There is a CLI to LastPass available in the repositories. It runs either locally, or as a firefox addon.

Installation is easy. [Download the file]("https://lastpass.com/misc_download2.php") and install, or install and sign up for the browser addon. 

[**Password Gorilla**]("https://github.com/zdia/gorilla/wiki") This PM is also available in the repositories, and is perhaps the simplest to use and configure. It allows you to generate new passwords according to the most obscure criteria, it can be set to time out according to any limit (default: 5 minutes).  It is available on OSX, Windows, and Linux. Files can be accessed via iOS via [pwSafe]("https://itunes.apple.com/us/app/pwsafe-password-safe-for-ios/id440783112?mt=8&ls=1") and [Dropsafe]("https://itunes.apple.com/us/app/dropsafe/id440414160?mt=8&ls=1"), and Android via [Passwordsafe]("https://play.google.com/store/apps/details?id=com.jefftharris.passwdsafe"). 

Setup is simple. Install from the repository, and then run. Choose a URL, and type your login and password. That's it. Double click and the service will log you in. Note: I had to configure Password Gorilla to find my browser, using File > Preferences > Browser. Choose copy username to clipboard and paste. Then choose copy password to clipboard and paste it, to login.

It's easy to set up a PM today. LastPass is the most popular, so start there, unless one of the others appeals to you. Start small; choose a service, and then pick that one mid-complicated password that you use everyday (work, school, bank, etc), and use a PM to access it from now on. Let it autogenerate a complex password for you, and then change your password. It will take you twenty minutes to set up, maybe, and a little while to get used to. But as your comfort grows, you'll use it for new sites, and you'll migrate more and more of those vulnerable passwords to your PM, until using it becomes second nature to you. Your data will be safer for it.

---

### Post by Habitual on 2016-12-29
Thanks. Bookmarked!

---

### Post by TheFu on 2016-12-29
Nice post.  Switching to using a password manager is like any other habit. Seems hard and limiting at first, but after a week, most people find a password manager invaluable.  I've seen this over and over.

The most important decision is to ensure that all the platforms can read the same password database.

There is no need to pay for software in this area. KeePassX has features on Linux that it doesn't have on other platforms. The auto-complete is very nice, while requiring activation by the user. It won't send credentials without positive action. That is a best practice.  Sites that automatically enter credentials can be tricked.
There are v1 and v2 KeePassX databases. Picking the version you want/need is only slightly important.

Make certain to backup the DB multiple times, multiple places. Also, using a strong passphrase to access the DB is required, plus using a "key file" or 2FA device for access. In the end, only 4 passwords should need be memorized.  
1) Computer login (home/work?)
2) KeePassX access 
3) Smartphone login/pin/passphrase
4) Encrypted storage access (pre-boot)
All others should be entered by the password manager.  The most secure password is the one you don't know.

Password managers aren't just for passwords:  [http://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager](http://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager)
Password Manager: [http://blog.jdpfu.com/2010/04/24/keepassx-password-manager](http://blog.jdpfu.com/2010/04/24/keepassx-password-manager)

Password managers aren't just for passwords.

---

### Post by untrustytahr on 2016-12-29
Password Manager?!?!??  I just write them on a piece of paper and put it on my desk... NO ONE can find things on my desk... including me:lol:.

Happy New Year to all!

---

### Post by TheFu on 2016-12-29
> **untrustytahr said:**
> Password Manager?!?!??  I just write them on a piece of paper and put it on my desk... NO ONE can find things on my desk... including me:lol:.

Happy New Year to all!

That worked for my mother. She only used a computer at her desk at home, so she wrote down the 2nd-half of each password for every online login into a small journal.  The first half was the same and only 8 characters. It was never written down anywhere.  The real issue was that she had to type in these 20+ character passwords. 

Whatever works and is secure for the needs.

---

### Post by Habitual on 2016-12-29
Certain US Military types at General Atomics, Aeronautical did this. OK, a lot of them.
Right on the Monitor.

---

### Post by TheFu on 2016-12-30
> **Habitual said:**
> Certain US Military types at General Atomics, Aeronautical did this. OK, a lot of them.
Right on the Monitor.

I cannot speak for current methods, but in the mid-90s, I worked for the govt and had many, many, many accounts to maintain across many different air-gapped systems. At the time, there was no approved method to write down or place these passwords into any electronic device. I was expected to memorize them all AND change them on schedule.  Each system had different times when the passwords needed to be changed. Some were 90 days, 60 days, 30 days and others were monthly, quarterly, yearly ... It was impossible to track, so I changed all of them every 28 days. Took me 4 hours that day to visit the locations on the campus (no driving needed) and change all the passwords.  Some systems, I had access to, but never really used much.  Getting on the logs of entry monthly wasn't a bad thing.  I was told that having any of these passwords the same as any others was a federal offense. Doubt that was true, but the idea stuck, so I made a system to migrate passwords by the required security levels of each system.

Only one of the systems was on the internet. Most weren't even connected to each other.

These systems didn't have any external ports that were usable. Devices were glued in place and empty ports were either disconnected internally or glued closed to be inaccessible.

Let's just say - I much prefer password managers AND believe password managers are much more secure.

Mom's method of writing down half the password for each login isn't bad. It is basically 2FA.  Something she knew "first-part" and something she had, the notebook with "unique-2nd-half".  The password for each system was "first-part unique-2nd-half."  If there was a theft, they'd get the "unique-2nd-half" parts for every login, but not the 1st half (not written down anywhere).  Mom (rip) was smart.  BTW, she ran Lubuntu the last 4 yrs of her life. ;)

---

