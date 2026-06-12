---
title: "Ubuntu One wont start first time"
date: 2010-03-13
forum: Ubuntu One (CLOSED)
---

### Post by blakep2 on 2010-03-13
Ubuntu One wont start first time , it loads in the taskbar but never comes up.

---

### Post by duanedesign on 2010-03-15
I am trying to understand what your issue is. You open Ubuntu One by going to Applications > Internet > Ubuntu One. The applet appears in the panel. If you right-click the panel and select 'Preferences' does the preferences window appear? Does the Client connect if you left-click and select 'Connect'? What version of Ubuntu One are you using? If you are not sure you can run:

```
dpkg -l ubuntuone-client
```

---

### Post by blakep2 on 2010-03-17
it is not even located under app-internet, it is under sytem-preferences-ubuntu one; it will come up in the task bar but wont launch it just closes before anything comes up.   I am running ubuntu  9.04 desktop. this is what came out with the code you gave me.


Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  ubuntuone-clie 1.1.3+r409-0ub Ubuntu One client

---

### Post by joshuahoover on 2010-03-19
> **blakep2 said:**
> it is not even located under app-internet, it is under sytem-preferences-ubuntu one; it will come up in the task bar but wont launch it just closes before anything comes up.   I am running ubuntu  9.04 desktop. this is what came out with the code you gave me.


Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  ubuntuone-clie 1.1.3+r409-0ub Ubuntu One client

I'm guessing you're being affected by [http://launchpad.net/bugs/535207](http://launchpad.net/bugs/535207) and the work around is to install python-httplib2. You can do this quickly from a terminal session (Applications->Accessories->Terminal): sudo apt-get install python-httplib2

If that doesn't solve the problem for you, can you try the following command from a terminal session and report back any errors you receive? 

ubuntuone-preferences

Thank you,

Joshua

---

### Post by blakep2 on 2010-03-19
i installed python successfully.
when i click on ubuntu one under preferences it opens a little status box with preferences it does the same with the code you gave me.  It is not under the internet option either.

---

### Post by joshuahoover on 2010-03-22
> **blakep2 said:**
> i installed python successfully.
when i click on ubuntu one under preferences it opens a little status box with preferences it does the same with the code you gave me.  It is not under the internet option either.

It sounds like that is working then. You may need to click on the "Devices" tab and then click on the "Connect" button to get the client connected.

Thank you,

Joshua

---

### Post by blakep2 on 2010-03-22
it dosent seem to be syncing at all not showing up on ubuntu one

---

### Post by joshuahoover on 2010-03-23
> **blakep2 said:**
> it dosent seem to be syncing at all not showing up on ubuntu one

OK, I think you may need to file a bug. You can do this here: [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug) Please put the steps your taking and the results your seeing in the bug report. Then run the following command in a terminal session (Applications->Accessories->Terminal):

apport-collect -p ubuntuone-client ######

Replace "######" with the bug report number. This will send log files that will help us troubleshoot the problem. You can also hop on #ubuntuone on Freenode IRC and ask for help. I'm there (joshuahoover) Monday-Friday, 13:00-21:00 UTC.

Thank you,

Joshua

---

### Post by RichardRicardo on 2010-03-23
I think that I must have the same problem as op. System > Preferences > Ununtu One the task bar shows "Starting Ubuntu One" then it, unexciting, doesn't do anything. 

Similarly ubuntuone-preferences at the terminal causes the cursor to blink. I don't have an ubuntu one account or anything. I was just going to poke around and see what it did. Do you have to have an account?

I also tried the python-httplib2. That installed ok, but didn't seem to have an effect.

---

### Post by blakep2 on 2010-03-23
i also installed python and it had no effect; I do not understand the launchpad thing

---

### Post by joshuahoover on 2010-03-24
> **blakep2 said:**
> i also installed python and it had no effect; I do not understand the launchpad thing

If you haven't setup Ubuntu One before on your computer, when you open System->Preferences->Ubuntu One, your web browser should open and prompt you to sign up/login to Ubuntu One. Once you do this, you should then be prompted to "add your computer". You do this and then when you open System->Preferences->Ubuntu One you should be able to click on the "Devices" tab and click the "Connect" button to connect to the Ubuntu One service.

Thank you,

Joshua

---

### Post by RichardRicardo on 2010-03-24
An update came through that got me squared away. Who knows what it was. Either way, I am good to go, I will commence playing around with it this evening.

blakep2 - You may want to try another update from the update manager, then see if it works for you too. It must have been some update that happened last night. My update manager said everything was up to date, but I clicked check anyway. Something good happened.

---

### Post by it.henrik on 2010-04-03
Whats the status on this problem? Im seeing it now on ubuntu 9.10 all packets updated and python-httplib2 is installed just fine.

---

### Post by joshuahoover on 2010-04-05
> **it.henrik said:**
> Whats the status on this problem? Im seeing it now on ubuntu 9.10 all packets updated and python-httplib2 is installed just fine.

We fixed the python-httplib2 dependency issue ([https://bugs.edge.launchpad.net/ubuntuone-client/+bug/535207](https://bugs.edge.launchpad.net/ubuntuone-client/+bug/535207)). Is Ubuntu One not working properly for you on 9.10? If it's not, can you either file a bug or hop on #ubuntuone on Freenode IRC and do some real time troubleshooting? I'm normally on from 13:00-21:00 UTC as joshuahoover.

Thank you,

Joshua

---

