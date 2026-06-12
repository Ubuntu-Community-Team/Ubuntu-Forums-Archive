---
title: "Can't seem to get 10.04 to connect"
date: 2010-05-22
forum: Ubuntu One (CLOSED)
---

### Post by jaysscholar on 2010-05-22
I have two machines connected to my UO account. One running xubuntu 9.10 another running ubuntu 10.04. My UO account has about a gig of comics in a folder titled 'x'. When I click the UO folder in 10.04 nautilus, I see a folder titled 'x', but it's empty. Not a thing in it.

So, in 10.04, I go System->Preferences->UO to bring up the preferences window. For a moment it shows nothing, then it'll update with my account info and the bar shows I have a gig of space. Underneath this bar is says 'Disconnected'. Under the Devices tab, I see my two machines, but the only options for each are to remove them. There is no 'Connect' button like the setup instructions say ([https://one.ubuntu.com/support/installation/](https://one.ubuntu.com/support/installation/)). I can't figure out how to connect. Apparently, there is some sort of connection made because the gig shows and the 'x' folder shows. But nothing tangible. How do I get access to that 'x' folder from the UO folder in nautilus?

Now, I've never used UO before so I'm not too familiar with it and feel like I'm missing something very very basic. So basic I can't seem to find it in all my Google searches.

In these searches, I come across some command line stuff, but each has very little explanation on what they do. Being a Linux beginner, it's greek to me and not really helping. I just need a little context. I've been trying to access u1sdtool, but typing that in the terminal seems to freeze it. I get a blinking cursor and nothing happens. What exactly is u1sdtool supposed to do? And why ain't it doing it?

(Sidenote: Y'all should make it clear that it's u1sdtool, not ulsdtool. In these fonts, they look the same and that was throwing me off for a long *** time :))

Any help would be appreciated.

---

### Post by joshuahoover on 2010-05-24
> **jaysscholar said:**
> I have two machines connected to my UO account. One running xubuntu 9.10 another running ubuntu 10.04. My UO account has about a gig of comics in a folder titled 'x'. When I click the UO folder in 10.04 nautilus, I see a folder titled 'x', but it's empty. Not a thing in it.

So, in 10.04, I go System->Preferences->UO to bring up the preferences window. For a moment it shows nothing, then it'll update with my account info and the bar shows I have a gig of space. Underneath this bar is says 'Disconnected'. Under the Devices tab, I see my two machines, but the only options for each are to remove them. There is no 'Connect' button like the setup instructions say ([https://one.ubuntu.com/support/installation/](https://one.ubuntu.com/support/installation/)). I can't figure out how to connect. Apparently, there is some sort of connection made because the gig shows and the 'x' folder shows. But nothing tangible. How do I get access to that 'x' folder from the UO folder in nautilus?

Now, I've never used UO before so I'm not too familiar with it and feel like I'm missing something very very basic. So basic I can't seem to find it in all my Google searches.

In these searches, I come across some command line stuff, but each has very little explanation on what they do. Being a Linux beginner, it's greek to me and not really helping. I just need a little context. I've been trying to access u1sdtool, but typing that in the terminal seems to freeze it. I get a blinking cursor and nothing happens. What exactly is u1sdtool supposed to do? And why ain't it doing it?

(Sidenote: Y'all should make it clear that it's u1sdtool, not ulsdtool. In these fonts, they look the same and that was throwing me off for a long *** time :))

Any help would be appreciated.

It's strange that you can't see the "Connect" button in the Devices tab. I haven't come across any issues where the "Connect" button wasn't visible. It would be helpful to get some debug logs attached to a bug report at this point. You can do this by following these steps:

1. Run the following from a terminal session: echo -e "[logging]\nlevel = DEBUG" > ~/.config/ubuntuone/logging.conf; sudo sed -i 's/LOG_LEVEL = logging.INFO/LOG_LEVEL = logging.DEBUG/' /usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/logger.py; u1sdtool -q; u1sdtool -c 

2. File a bug at: [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)

3. Run this command, replacing ###### with the bug number from the step above: apport-collect -p ubuntuone-client ######

4. Run this command from a terminal session: tar cjf ~/u1logs.tar.bz2 ~/.cache/ubuntuone/log

5. Attach ~/u1logs.tar.bz2 to the bug report

Once you do this, please post your bug number here and I'll be sure to have someone look into ASAP.

Thank you,

Joshua

---

### Post by jaysscholar on 2010-05-28
> **joshuahoover said:**
> Once you do this, please post your bug number here and I'll be sure to have someone look into ASAP.]

Bug #587036

---

