---
title: "Ratel Wired Network Inop at Boot"
date: 2007-04-18
forum: System76 Support
---

### Post by iba10753 on 2007-04-18
I have a new Ratel Value and have been getting to know it over the last few days.  Each time I boot or restart the machine, I have to left-click on the "Wired network connection" icon in the deskbar and click to enable "Wired Network" before it will go out for a DHCP address and give me network connectivity.

So far, I've looked around for information on how to get that operation to be automatic upon startup of the machine and haven't found any configuration routines that I can work with.  I have a feeling that an answer to this question will actually help me with other issues that I might encounter in the next few days.

How can I get the wired network connection to automatically be enabled at startup?

Thanks,
Ben Askew

---

### Post by thomasaaron on 2007-04-18
If you right-click on the icon, there should be a check-marks beside 'Enable Networking'.  There should also be a check beside 'Enable Wirless'.

Can you check to see if that is the case?

Best,
Tom

---

### Post by iba10753 on 2007-04-18
Yes Sir, there's always been a checkmark by the Enable Networking option.  Each time the machine boots, I have to go through the motions of the left-click to enable Wired Network.  I did not purchase the wireless option on this Ratel so options for that don't show up.

Thanks,
Ben Askew

---

### Post by thomasaaron on 2007-04-18
First thing:
Have you EVER used System > Administration > Networking to connect to the internet?
If not, don't.

If you have, let me know. We will have to modify your /etc/network/interfaces file to get network manager working right again.

Otherwise, I think it may be a bug in the system that will be by upgrading to Feisty after the 20th.

If upgrading doesn't fix it, let me know and I'll file a bug report on it.

Best,
Tom

---

### Post by iba10753 on 2007-04-18
I've never used the Networking app to configure my networking.  I've been in there looking around but haven't every effected any changes.

Let's see what the upgrade to Feisty does and we'll take it from there.  It sure isn't a major problem, just a minor annoyance when the machine starts up.

By the way, can you give me your personal opinion of whether I should just run with the Feisty upgrade on this new system or should I do a complete new install of Feisty (along with the System76 driver).  I have really nothing saved on the machine yet and have just been playing around with it so I really don't have anything to lose with a new install if that's the "best" way to get to Feisty.

Thanks,
Ben Askew

---

### Post by thomasaaron on 2007-04-19
There's no need to do a fresh install for Feisty.
Just go to a terminal and type:
update-manager -d -c

Best,
Tom

---

### Post by iba10753 on 2007-04-19
Thanks, Tom.  I did that this morning and I believe I'm just an hour or so from finishing the download portion of the upgrade.  So much for trying to do this on the first day of the release! <g>

Thanks again,
Ben

---

### Post by iba10753 on 2007-04-20
Just as a follow-up, the upgrade to Feisty did indeed fix the problem of the Wired Network not automatically being "checked" at system startup.

Thanks,
Ben Askew

---

