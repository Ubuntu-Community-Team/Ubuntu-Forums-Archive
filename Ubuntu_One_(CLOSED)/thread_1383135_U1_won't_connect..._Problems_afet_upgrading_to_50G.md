---
title: "U1 won't connect... Problems afet upgrading to 50GB"
date: 2010-01-16
forum: Ubuntu One (CLOSED)
---

### Post by jondecker76 on 2010-01-16
I updated my wife's U1 to the $10/month 50GB plan.
The local files on the computer all show green checkmarks, so I thought they were sync'd. When I logged in to her account, it showed 0% being used (she already had 11GB of files in her Ubuntu One folder while on the 2GB plan).
I removed the computer from her account, as there was obviously a problem. Now, clicking on the "connect" button (in nautilus) does nothing, it just sits there forever, trying to connect.  It never brings up an UbuntuOne page to sign in so I can re-link the computer to her account.  Now that I'm a paying customer, I want this to work correctly.

Also, I think it is also fair to mention that U1 has been riddled with bugs since day 1 (i have submitted bug reports and they never seem to get fixed). I'm very surprised at just how long it is taking the team to fix these bugs (especially since there are paying customers!)  The only reason I agreed with my wife to pay for a subscription is because I believe in OSS and want to see U1 succeed. (I'm still waiting for a Tomboy Notes syncing bug I submitted **months** ago to be fixed - then I will upgrade my account as well).  I'm afraid that if more resources aren't thrown at U1 to get it STABLE and bugs fixed, this service could be doomed to failure. I really hope Canonical starts looking at this area more seriously!

---

### Post by emurphy on 2010-01-17
Hey Jon, sorry to hear you've had troubles and thanks for your support with the paid subscription. I'm hiring someone fulltime to help us keep up with responding to questions from the influx of users - with so many people joining the service right now we're missing or taking too long to respond to some legitimate bug reports because there's plenty of duplicate reports flooding in. Despite doing our best to test things carefully, when you get a lot of people using something then even an edge case bug that only affects 0.1% of people is still going to affect a lot of people :D

If you want to email me with the list of bugs that are important to you, I can take a look and make sure we have those on the short list to fix, or figure out what additional info we need in order to debug. elliot at canonical dot com. It's possible that we fixed yours bugs but never went back and marked your particular bugs as fix released, and also it sounds like there is still a problem that we need to resolve. Hopefully we'll be able to take care of it quickly.

-elliot

---

### Post by jondecker76 on 2010-01-18
Thankyou for confirming that U1 will be getting some more resources.

I still need to get U1 working again for my wife. Right now I can't link it to an account. It never asks to log in. I have an UbuntuOne folder with all green checkmarks, but its not connected to my wife's account.  In her account, it shows 0% used with no files, and no connected computers.  On our desktop, i have uninstalled, then reinstalled Ubuntu One from the Ubuntu Software Center.
In nautilus, there is a connect button, but pressing it only yeilds a grayed-out button that says "Connecting", and nothing else happens.

---

### Post by andrea000 on 2010-01-19
This is not a fix but more of a work around for
the time being and if you don't mind expermenting
you can try to re add your pc first open a terminal
applications->accessories->terminal then copy and
past this
> sudo apt-get install ubuntuone-client-tools
or go to synaptic and install it then copy this and
past in the terminal

> u1sync --authorize
The u1 website should come up asking you to add your
pc.You may still have to right click the icon and tell
it to connect but it may work for you while they fix
the problem it fixed mine.Good luck

---

### Post by jondecker76 on 2010-01-22
We have it now to where the computer is associated with Ubuntu One. However, things are still now working correctly. I have 2 sub-folders. One is my Moneydance folder and the other is My Pictures folder. Both folders have green check marks in my Ubuntu One directory. Then, when I check the Ubuntu One website, only the Moneydance folder is present and the My Pictures folder is nowhere to be found. Again, both folders have the green check marks in my Ubuntu One directory. 

I would be willing to grant ssh access to an Ubuntu One developer if they want to look at my system configuration.

---

### Post by andrea000 on 2010-01-22
click the icon and see if it says connect or disconnect if it
says connect then click that it just isn't autoconnecting and
if it says disconnect then there is something else wrong.I
have problems uploading .deb files made with check install and
i have not solved that yet.

---

### Post by jondecker76 on 2010-01-23
It does say disconnect. So...there is something else wrong. Thank you for your help.

---

### Post by joshuahoover on 2010-01-25
> **jondecker76 said:**
> It does say disconnect. So...there is something else wrong. Thank you for your help.

Hi Jon! Did you file a bug for this? If so, can you point me to the number? If not, can you try the following so we can help get this resolved for you?

[LIST=1]
[*]Open (or create if it doesn't exist): ~/.config/ubuntuone/syncdaemon.conf 
[*]Add the following 2 lines to this file and save: 
[main] 
 log_level = DEBUG 
 
[*]Restart the Ubuntu One client 
[*]Copy some files into your ~/Ubuntu One folder and give it some time to sync
[*]Right-click on the Ubuntu One client and select "Report a Problem" to file a new bug
[*]Attach ~/.cache/ubuntuone/log/syncdaemon.log to the new bug report
[/LIST]
Thank you,

Joshua

---

