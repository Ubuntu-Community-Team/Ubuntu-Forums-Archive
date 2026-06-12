---
title: "Remote controlling"
date: 2017-03-31
forum: Security
---

### Post by onelightyear on 2017-03-31
Hello,
We're a small team and each one of us has an ubuntu desktop. 
I'm suspecting one of the colleagues is remotely controlling my computer or accessing it for spying purposes. He has an admin account (because he was the one who installed/configured my system). Me too have an admin account as well ("su"). 
My question is as follows: Is it enough to erase his admin account to ensure he cannot remotely access my computer? Is there anything else I can do to make sure privacy is respected?
Thank you,

---

### Post by QIII on 2017-03-31
Hello!  

See this for [how to add/delete users]("https://help.ubuntu.com/lts/serverguide/user-management.html").

See this for how to [change your password]("https://help.ubuntu.com/stable/ubuntu-help/user-changepassword.html").

And, finally, this for [some basic security tips]("https://wiki.ubuntu.com/BasicSecurity").

Does this person have physical access to your machine?  What leads you to believe this person is intruding or spying?

---

### Post by onelightyear on 2017-03-31
Thanks for the links. He is very knowledgeable of unix. He does not have access to my machine (physically) What makes me believe he does, is that, yesterday, he heard the fan of my computer spinning loudly, so he told me "Let me have a look and did a "htop" remotely and told me that my chromium browser needs to be turned off.Nothing showed up at my computer asking me if I allow him to do that...

---

### Post by howefield on 2017-03-31
Perhaps it is in his remit to have remote access for administration purposes ?

There are dozens of ways to remote in to your machine, but likely it's an ssh session running ?

Is there a problem in asking your colleague what he is doing ? You haven't said anything that indicates malice on the part of your colleague.

---

### Post by QIII on 2017-03-31
And if this person is charged with administering the network, your employer's policies or local laws may not provide for your privacy.

---

### Post by onelightyear on 2017-03-31
> **howefield said:**
> 

Is there a problem in asking your colleague what he is doing ? 

Believe me it is not in his remit to access for administration purposes :) That's why we are all admins of our own machines... 
With respect to you second question, he once confessed that he is spying on the boss :) yes ... :)

---

### Post by QIII on 2017-03-31
I suggest that this would be a subject best addressed by your employer.  The sorts of tbings we might suggest may very well be in violation of company policy.

---

### Post by HermanAB on 2017-04-05
"To measure, is to know."

Learn how to use tcpdump and ettercap:
[http://www.aeronetworks.ca/2013/10/packet-sniffing.html](http://www.aeronetworks.ca/2013/10/packet-sniffing.html)

---

### Post by TheFu on 2017-04-08
"Spying" is unlikely.  Most of us just aren't that interesting that a busy admin would care.  I doubt he used that term too. 

Unix and Linux is a multi-user OS from the ground up.  It is designed to allow thousands of users access concurrently.  Most of these would be over remote connections, like ssh.  If ssh is running, then anyone with appropriate credentials can remotely access the system. There are lots of good reasons for this. Running htop/top/atop/ntop would be expected under the situation. Not much nefarious happening from your description.

I've been an admin for 20+ yrs and only take a look around when something seems wrong. I usually have remote logging and system performance stats captured to log server.  Remote ssh is a staple of Unix systems. It is how I work and administrate systems.  As routine, remote ssh is setup on every system I install.  ALL OF THEM.  I don't keep it a secret.  Inside a corporate environment, this is my job.  If I installed Linux for someone else, not at work, leaving ssh (secured) as a courtesy for when the other user gets in over their head - which happens all the time.  For example, I remotely admin some family member's computers from 3-8 states away.  For work, I admin systems around the world ... or 3 ft away.

If you delete the other account, that should be sufficient to prevent access, but don't ask for him for help anymore. I think this is a mistake, at least until you gain a much better understanding of Linux administration or at least become a power-user.

If he really is "spying", then you need to wipe the machine and start fresh.  He could have left all sorts of remote access methods behind almost anywhere on the machine.  These wouldn't need to be running at any specific point, but could start for 5 min a day so he could get back in.  He could have the normal sudo tool setup to open a reverse ssh connect to a system he controls every time you run it, then do the normal sudo stuff that you expect. That way you'd never notice anything.  This isn't likely, but it is possible. 

If you don't trust the installer, then you need to wipe the machine and start over from a trusted source.

This is part of the reason that at my LUG, we don't do installs for anyone.  We help the owner do the install himself, but they do all the typing and make all choices. OTOH, if I provide the ISO used for the install, then I can pre-load anything I want.  If I can convince you to copy/paste something from my blog or an html-email for someone with sudoer permissions, then I can get ownership of your system - forever.

But I truly doubt anyone is "spying."

---

