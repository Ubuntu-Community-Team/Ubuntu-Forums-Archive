---
title: "Ubuntu One sync erases data in file"
date: 2009-12-02
forum: Ubuntu One (CLOSED)
---

### Post by jheaton5 on 2009-12-02
I have a text file created with gedit that I saved to the Ubuntu One directory in nautilus on my home computer.  At work on my netbook (running karmic) I opened the Ubuntu One directory in nautilus.  The file was there but when I opened it it was blank.  Thinking I did something wrong I recreated the file at work and saved to Ubuntu One.  Got home, the file was there, but it was blank.  I reaped the same steps today with the same results.

---

### Post by nessita on 2009-12-02
Hi jheaton5,

first of all, thanks for taking the time on reporting this.

Secondly, in order to do the proper follow up for this issue, I've created a bug report on launchpad: [https://bugs.launchpad.net/ubuntuone-client/+bug/491613](https://bugs.launchpad.net/ubuntuone-client/+bug/491613) .

Could you please subscribe to the bug report and upload all your ubuntuone log files?

We would also need DEBUG logs to find the issue here. You should do the following:

 1. close the applet and stop the syncdaemon client and be sure it's fully stopped ("ps -eaf | grep ubuntuone-client" should give you nothing).

 2. put (or edit if it exists) a file named syncdaemon.conf in your $HOME/.config/ubuntuone directory with the following information: 
    [__main__]
    log_level = DEBUG

3. restart the client.

4. attach the logs to the bug report, just zip you $HOME/.cache/ubuntuone/log/ folder and attach the zip there.

Thanks for your time and help!

---

