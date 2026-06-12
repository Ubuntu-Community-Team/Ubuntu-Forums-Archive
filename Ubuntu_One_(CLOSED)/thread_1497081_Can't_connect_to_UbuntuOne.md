---
title: "Can't connect to UbuntuOne"
date: 2010-05-30
forum: Ubuntu One (CLOSED)
---

### Post by ChiVampir on 2010-05-30
I can't get my computer to connect to UbuntuOne. 
When I open ubuntuone-preferences and try to click on Manage Account a window that says *"Error - [Errno 113] No route to host" *shows up and then the window freezes and won't let me exit it unless I use the System Monitor.

I run Ubuntu 10.04 (fresh install and updated) as the only OS on a Acer Aspire 3614WLMi

I really hope that you can help me.

> chi@Reca:~$ ubuntuone-preferences
Exception in thread Thread-2:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.6/threading.py", line 484, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/bin/ubuntuone-preferences", line 162, in do_rest_request
    callback(result)
  File "/usr/bin/ubuntuone-preferences", line 684, in got_quota_info
    self.update_quota_display(used, total)
  File "/usr/bin/ubuntuone-preferences", line 638, in update_quota_display
    'percent' : percent })
KeyError: 'brukt'


("Brukt" means used)

---

### Post by duanedesign on 2010-06-01
Are you trying to connect Ubuntu One for the first time and having trouble?
If so maybe [this will help]("https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?") 

or

You have already signed up and added your computer and now the service is not connecting?

If this is the case, I would try reauthorizing your computer. here is the steps for that.
>    1. Quit the Ubuntu One Preferences (if open)
   2. Open Applications > Accessories > Terminal and run the command:
killall ubuntuone-login; u1sdtool -q
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open Applications->Internet->Ubuntu One
   9. a web page should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer 

thank you,
duanedesign

---

### Post by ChiVampir on 2010-06-07
None of these two methods worked for me :(

---

### Post by duanedesign on 2010-06-20
[Here is the bug report]("https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/578977") on this isue. Please click the 'this affects me' button on the bug report'. I have also come across a few people in #ubuntuone with this error.

---

### Post by Pifilatakanemu on 2010-06-21
Just in case you need a working online storage urgently and don't want to wait until U1 leaves the beta status and works as it should: try [Dropbox]("https://www.dropbox.com/referrals/NTIxNTQxNzg5").

Following the link above you'll receive 2,25GB (and my space is raised by 250mb) that can be increased until 10GB through referrals. Not to mention that it works stable, fast and cross-plattform. ;)

---

### Post by Benic on 2010-07-01
> **duanedesign said:**
> Are you trying to connect Ubuntu One for the first time and having trouble?
If so maybe [this will help]("https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?") 

or

You have already signed up and added your computer and now the service is not connecting?

If this is the case, I would try reauthorizing your computer. here is the steps for that.


thank you,
duanedesign


I've tried that method and it didn't work. So I've decided to also the Couch DB token. Then I restarted the launcher. Bingo! It worked for me.

---

### Post by duanedesign on 2010-07-01
Update on the '
ubuntuone-preferences freezes with Norwegian locale' bug

please see [bug 571616]("ubuntuone-preferences freezes with Norwegian locale") for the latest status and a possible workaround.

This bug is marked fix released so the changes should be making there way to us soon.

---

