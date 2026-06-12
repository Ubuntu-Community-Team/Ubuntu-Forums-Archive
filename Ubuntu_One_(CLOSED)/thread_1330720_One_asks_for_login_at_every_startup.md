---
title: "One asks for login at every startup"
date: 2009-11-18
forum: Ubuntu One (CLOSED)
---

### Post by crisnoh on 2009-11-18
How to I get Ubuntu One to remember my login info between sessions?  Additionally, I have to re-add my computer every time I reboot.

Thanks.

---

### Post by duanedesign on 2010-01-28
I'm sorry to hear Ubuntu One isn't working properly for you. Can you try the following and let us know the results?

   1. Quit the Ubuntu One client
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open Applications->Internet->Ubuntu One
   9. A web page should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer 

You should be connected after you follow these steps.

If you are not connected, please file a bug by right-clicking the applet in the panel at the top of the screen and selecting 'report problem'.Please attach the following files to this bug report.

~/.cache/ubuntuone/log/oauth-login.log
~/.cache/ubuntuone/log/syncdaemon-exceptions.log

---

### Post by bryceowen on 2010-01-29
Scratch that. I'm still having the same problem. I had just submitted my reply when Firefox opened a new tab to the U1 login screen.

---

### Post by fbkarsdorp on 2010-01-30
I'm having the same problem. U1 keeps logging me out and asks me for my computer-address. Previously everything was just fine. It started only yesterday.

---

### Post by 334455 on 2010-01-30
I have the same problem since a couple of days. I have tried to uninstall the program and reinstall but the problem remains. when I check the Applications->Accessories->Passwords there is no entry for U1 even if I have added the computer. 
I have to log-in everytime I start the computer. After a few minutes I have to log in again.

---

### Post by brujoquizz on 2010-01-30
Same problem here. I was thinking that maybe it was a browser problem, but even if I use Firefox or Chromium I have the same issue. I going to look on launchpad if there's any solution...

---

### Post by burpootus on 2010-01-30
Same problem here...Firefox keeps opening a tab directed at Ubuntu One asking me to add the computer I'm on. Very annoying.

---

### Post by andrea000 on 2010-01-31
Same problem here as well i have been working on it
since friday i have reported it and it looks like
another bug that has been reported sometime back so
i guess we will have to wait till the bug is fixed.

---

### Post by pw1 on 2010-01-31
It's getting boring, but I'm having the same problem. I've been using Ubuntu One without any problems for a several months, until a couple of days ago I started having this problem.

For those interested, here is the bug report in Launchpad:
[https://bugs.launchpad.net/ubuntuone-client/+bug/514723](https://bugs.launchpad.net/ubuntuone-client/+bug/514723)

---

### Post by duanedesign on 2010-02-02
Sorry to hear you are having problems.There was a problem recently with one of the servers causing authentication errors. The U1 team has fixed this and put in place some monitoring measures to insure this does not happen again. You should be able to use the service as expected.

Additionally if you are running Karmic make sure you are running the ubuntuone-client 1.0.3 or better. if you run in a Terminal (Applications > Accessories > Terminal)

```
dpkg -l ubuntuone-client
```

and find you are still running 1.0.2 visit the link below for instructions to update your ubuntuone-client.

[https://answers.launchpad.net/ubuntuone-client/+faq/930](https://answers.launchpad.net/ubuntuone-client/+faq/930)

thank you,
duanedesign

---

### Post by offrampextreme on 2010-02-09
Thanks for the solution. I was running the old version and not aware of it. I had to add my desktop computer like four times already. My Asus netbook running UNR was added once and never had a problem. Neither did my android phone.

---

### Post by Jim Boy on 2010-02-13
I have been having this as well for the last couple of weeks, now however it has flagged all my files with u1conflict, so now I have to clean up this mess.

I am also running Dropbox on another folder, which has not missed a beat.

---

