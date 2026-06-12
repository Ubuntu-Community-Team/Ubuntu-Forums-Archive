---
title: "Inability to login - user error or suspicious?"
date: 2009-10-03
forum: Security
---

### Post by risingsun on 2009-10-03
Hi,

I did a change of my password this morning and I successfully managed to log in once using it. However upon rebooting this afternoon I was unable to login.

Now my fear is that somebody else managed to remotely change it, but there's also the likely possibility that I managed to convince myself it was something it was not in the space of a few hours, or that I just managed to misspell it three times in a row (two for the change and once for a login, though this seems unlikely.)

I've since reset it to something else using the recovery boot option, but of course my fear is that if it was changed by someone else I would have take a good deal more action that just that. Of course, if I was just being a forgetful idiot in some manner I'd be creating a great deal of unneccesary work for myself.

As such, I just wanted to seek some kind of advice based on the evidence I had. Before resetting the password I checked the modified time of the /etc/password file using a live CD and it did appear to coincide with my password change - would this indicate that no-one had changed it since? 

I also checked the last logged in people using 'last' and saw nothing out of the ordinary other than my logins from tty7. I don't believe I have anything like an SSH server installed since I have not done so myself (and I presume Ubuntu only has the client by default, correct?)

Additionally I tend to keep a track of the services running using ps ax to check for anything new/suspicious, and there is nothing new compared to previous days. I also used sha1sum on a live CD to check the checksums of ps and ls and /bin/ps and /bin/ls match their live CD equivalents.

This would lead me to conclude that it is more likely my own fault (never ascribe to malice what can be explained by stupidity I guess) but I was just wondering if someone could help reassure me somewhat if they could concur or point out if I had missed something in my checks. The only thing I'm not sure of is if I should check cron jobs, and how I would do so.

Many thanks.

Edit: In further checks of my logs I can see that at the time of me changing the password there were two terminals opened, one after the other. Going by modified times at least one of these is me doing ps ax, and since no dhclient process is present in that log I believe I must have been off the network when I did this, meaning the second terminal is me changing the password. I can only conclude that I changed the password only once, but there appears to be nothing suspicious in the ps ax I did immediatedly before it. Currently everything is pointing to me just remembering the password wrong somehow after my first succesful login, but it just bothers me that I could forget in a matter of 4 hours or so and spelling it incorrectly three times in a row seems unlikely.

---

### Post by XCan on 2009-10-03
If you don't have anything listening, then it can't be someone changing your password remotely. You can check is using, for example, ```
 netstat -l 
``` Of course it could also be someone with physical access changing your password. But as you said, everything seems to be in order, so I would say that the chances are slim. On the other hand, if someone has physical access to your computer and it's not encrypted and you don't trust them, you're screwed either way. :p

---

### Post by wilee-nilee on 2009-10-03
It sounds like your familiar with how to reset the password with recovery though.

---

