---
title: "run script on login fail"
date: 2010-05-19
forum: Security
---

### Post by beng2cool4u on 2010-05-19
hey guys, what im trying to do, if possible is run a script when the user incorrectly types their password at the login/lock screen.

to further detail this, what i am trying to do is when the user fails to incorrectly type their password, i want to run [motion]("http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome"). i was hoping to find how ubuntu outputs the "Checking..." and "Incorrect password." dialogs and somehow embed the script to run from there... 

i'm not too used to working around the back-end of linux, but i determined that this would not work by simply calling the script in the rc.local file...

also i'm trying to accomplish this on ubuntu 10.04.

---

### Post by bodhi.zazen on 2010-05-19
I would point you to pam

[http://www.cyberciti.biz/tips/rhel-centos-fedora-linux-log-failed-login.html](http://www.cyberciti.biz/tips/rhel-centos-fedora-linux-log-failed-login.html)

From the logs you can probably script something.

Or I simply lock them out, via pam. It is not as straight forward as it may seem ...

[http://blog.bodhizazen.net/linux/ubuntu-how-to-faillog/](http://blog.bodhizazen.net/linux/ubuntu-how-to-faillog/)

---

### Post by beng2cool4u on 2010-05-19
unfortunately... i did not stress how dumb i am... i did get that to work, but i fail to see how it helps me! sorry for my own stupidity!

Has anyone Heard of anything someone has already made that does this? or is there a way to access the code that outputs "Login Fail" and simply put a call to a script right before it?

i would be creating a script that takes a picture via webcam, possibly using motion or webcamd....

---

