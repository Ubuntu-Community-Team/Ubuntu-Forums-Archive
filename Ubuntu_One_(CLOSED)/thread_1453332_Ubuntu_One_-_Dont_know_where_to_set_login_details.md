---
title: "Ubuntu One - Dont know where to set login details"
date: 2010-04-13
forum: Ubuntu One (CLOSED)
---

### Post by w1z4rd on 2010-04-13
So somewhere along the line I have messed up something. I think it happened when I clicked a couple of days ago on the Ubuntu One icon... then couldnt be bothered to fill out another form on that day so cancelled the setup.

Now the problem is, when I click on the Ubuntu One icon, it starts the little system tray and everything... but um... theres no where in the preferences or anywhere else to fill in my login details. 

So.. its not working... where would I fill in those details so I can make use of this service?

---

### Post by joshuahoover on 2010-04-13
> **w1z4rd said:**
> So somewhere along the line I have messed up something. I think it happened when I clicked a couple of days ago on the Ubuntu One icon... then couldnt be bothered to fill out another form on that day so cancelled the setup.

Now the problem is, when I click on the Ubuntu One icon, it starts the little system tray and everything... but um... theres no where in the preferences or anywhere else to fill in my login details. 

So.. its not working... where would I fill in those details so I can make use of this service?

First, make sure you have all the latest updates then try this:

Run from a terminal session (Applications->Accessories->Terminal):

killall ubuntuone-login ubuntuone-syncdaemon

Then open System->Preferences->Ubuntu One. This should prompt you to login or sign-up for Ubuntu One. Follow that process and then you'll eventually get to add your computer to your Ubuntu One account which completes the process. Once that is done, click on the "Devices" tab in the Ubuntu One Preferences panel and click the "Connect" button.

Thank you,

Joshua

---

