---
title: "How to add my machine to Ubuntu One"
date: 2010-03-11
forum: Ubuntu One (CLOSED)
---

### Post by framat on 2010-03-11
I have installed Ubuntu one and found it under system, but when I start it I can't see any option to add my computer. I would like to activate synkronization.
I have Ubuntu 9.10 and updated everything

---

### Post by joshuahoover on 2010-03-11
> **framat said:**
> I have installed Ubuntu one and found it under system, but when I start it I can't see any option to add my computer. I would like to activate synkronization.
I have Ubuntu 9.10 and updated everything

NOTE: Right now we're having issues with users authorizing their computers with the Ubuntu One service. We're working on fixing this right now, but it is a known issue that will prevent the steps I list below from working properly.

It sounds like you have installed Ubuntu One via our web site, is this correct? If so, you'll need to do the following:

1. From a terminal session, run: sudo apt-get install python-httplib2
2. Start Ubuntu One at System->Preferences->Ubuntu One
3. You should see a web browser window open asking you to add your computer to Ubuntu One
 3a. You may get prompted to allow access to your keyring, if so, click "Allow Always"
4. If it's not open, go to System->Preferences->Ubuntu One 
5. Click on the "Devices" tab
6. Click the "Connect" button

We're fixing this process to be more streamlined in Lucid and our PPA, but these are the steps you'll likely need right now.

Thank you,

Joshua

---

