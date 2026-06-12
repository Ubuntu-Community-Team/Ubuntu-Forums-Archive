---
title: "Upgrade from 7.1 to 8.04 Mailscanner refused to work"
date: 2008-04-28
forum: Server Platforms
---

### Post by Bernd Nowak on 2008-04-28
Did an update to 8.04 and all went well with the expection of Mailscanner.

It was complaining about some lines in Message.PM and due to this I couldn't remove or do anything with it.
I found that this was an issue in the beta part but I had no luck. So I downloaded mailscanner_4.68.8-1_all.deb and extracted the file from this and replaced it and now it works.
The one which made the trouble was  mailscanner_4.58.9-2ubuntu1_all.deb

---

### Post by sulla on 2008-05-01
confirmed!

I have the same issue, so do other people. See
[https://bugs.launchpad.net/ubuntu/+source/mailscanner/+bug/195260](https://bugs.launchpad.net/ubuntu/+source/mailscanner/+bug/195260)
for more detailed explanation.

I deactivated mailscanning by commenting the HOLD-line in the postfix configuration until a new mailscanner version will come up in the repositories!

sulla

---

### Post by Bernd Nowak on 2008-05-03
Thanks Sulla and yes I have found that link you provided too. It's strange but why are there not more which report this error ?

---

### Post by Bernd Nowak on 2008-05-13
Still having problems with APT and Mailscanner. No help or updated package from Mailscanner to somehow try to correct this ?

---

### Post by sulla on 2008-05-13
Hi Bernd!

No, I haven't solved the problems either.
My workaround so far is to disable mailscanner altogether in postfix.conf.
I am waiting for new packages, then I'll try it again. I can somehow live with it, as I am using my mailserver only as a satellite system, not exposed to the "free internet".

Still, it is really strange that so few people seem to have the problem.

Regards, Sulla

---

### Post by sulla on 2008-06-12
Hi Bernd!

The last upgrade of package mailscanner by ubuntu did not resolve things but rather made them worse.

I downloaded the newest mailscanner-4.68.8-1  package from debian and installed it manually (forcefully overwriting the ubuntu one):
sudo dpkg -i --force-overwrite mailscanner-4.86.8-1-all.deb

It works now perfectly.

I have no idea, however, what will happen when a new package will come through the ubuntu upgrade function or when I will do a dist-upgrade...

Regards, Sulla

---

### Post by albinootje on 2009-06-25
I'm interested in testing mailscanner + postfix in either Debian or Ubuntu.

I came across this page : [http://www.mailscanner.info/ubuntu.html](http://www.mailscanner.info/ubuntu.html) which says : 
> 
The setup of MailScanner distributed with Ubuntu is totally broken, as you may have already discovered.


Can someone confirm this ?

This [https://bugs.launchpad.net/ubuntu/+source/mailscanner](https://bugs.launchpad.net/ubuntu/+source/mailscanner) doesn't show that many serious problems afaik.

The disadvantage for the usage of the howto on the mailscanner webpage is that there's no mention of gpg key for apt-get on the 3rd party repository (which is not a big disadvantage, but i prefer no errors or warnings after an "sudo apt-get update".

I might as well go for using Debian Lenny, and then see how the mailscanner package from Lenny backports is (there is no mailscanner package in Lenny).

---

