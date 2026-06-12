---
title: "RetroMessenger - serverless &amp; secure IM"
date: 2008-11-18
forum: The Cafe
---

### Post by kagashe on 2008-11-18
I found this on Linux Today:
[http://retromessenger.sourceforge.net/]("http://retromessenger.sourceforge.net/")
clicked on Download link and downloaded. After extracting I found an executable file (nothing to be installed on the system).
Initially it did not work and after running in the terminal I found one dependency which I installed:
> $ sudo aptitude install libwxgtk2.8-0
Then I could run the IM.
Now I require some buddy to test it, therefore, please install and let us have server-less secure chat.

kagashe

---

### Post by Polygon on 2008-11-18
how does it work without some central source? how does the other person get your certificate so you can start chatting?

---

### Post by kagashe on 2008-11-18
> **Polygon said:**
> how does it work without some central source? how does the other person get your certificate so you can start chatting?That is what we can try if you download, extract and click on the executable (there is no installation on your system). Please remember to install the dependency before trying.

What I have done so far:
Installed dependency.
Double clicked on the executable.
Ignored the errors regarding some icons not present (clicked ok button).
Entered username, password and clicked on something like "generate certificate".

One window opened with users Bob & Eve.
Clicked on File/Login
Entered username and password.

If you do the same we will have to exchange the certificates before we can start chatting and that is what I would like to test.

kagashe

---

### Post by kagashe on 2008-11-19
I tried with some one. It does not work.

---

### Post by Polygon on 2008-11-19
ouch.

it seems more a pain then a convenience, since you first have to somehow give them your key before you can even start chatting with them.....and since there is no central source, you could run into problems with firewalls and incorrectly forwarded ports.

---

### Post by mrgnash on 2008-11-19
Jabber is already decentralized... I don't see any real advantage here.

---

### Post by loell on 2008-11-19
isn't this also the purpose of pidgin bonjour?

---

### Post by Polygon on 2008-11-19
i was under the impression that bonjour was like....local networks...

---

### Post by panpaliamahen on 2008-11-20
Hello Kagashe/All,

Please tell how did you test it?

I have tested it and working fine.I was able to generate certificate, login , add friend and was able to chat with friend.
That is what expected in this release to work.

In next release, there is other exciting feature "Link-Cloud" will be added along with fixing some user interface issues i.e. scroll bar is not proper on chat window etc

It is on beta release and i guess it should fix few user interface problems....like scroll bar is not working.

Please feel free to report any issue on hrrp://retromessenger.sf.net

Thanks and kind Regards,
Mahendra

---

### Post by FuturePilot on 2008-11-20
> **loell said:**
> isn't this also the purpose of pidgin bonjour?

> **Polygon said:**
> i was under the impression that bonjour was like....local networks...

Yes, Bonjour is meant for local networks.


> **mrgnash said:**
> Jabber is already decentralized... I don't see any real advantage here.

Also Jabber has support for encrypted messages via GPG keys.

---

### Post by kagashe on 2008-11-20
> **panpaliamahen said:**
> Hello Kagashe/All,

Please tell how did you test it?

I have tested it and working fine.I was able to generate certificate, login , add friend and was able to chat with friend.
That is what expected in this release to work.

In next release, there is other exciting feature "Link-Cloud" will be added along with fixing some user interface issues i.e. scroll bar is not proper on chat window etc

It is on beta release and i guess it should fix few user interface problems....like scroll bar is not working.

Please feel free to report any issue on hrrp://retromessenger.sf.net

Thanks and kind Regards,
Mahendra
Glad to see you on Ubuntuforums. I am trying to chat with other friends on internet. After double clicking the executable I entered username, password and clicked on "Generate Certificate" Then I clicked on File/Login and logged in with the username and password.

Then I clicked on File/Display_Certificate, copied the certificate and sent it to my friend. My friend also sent me his certificate.

I clicked on Add Friend with certificate, pasted the certificate and clicked ok. My friends username appeared on left pane. I selected the username and typed some text in the bottom window and clicked on Send button. The text appears on right pane but my friend does not receive anything.

My friend also tried but I did not receive anything.

In addition there is a bug. If I click on File/exit closing the session and start other one by double clicking there is segmentation fault. The fault gets removed only when I delete my friend's certificate from friends directory.

kagashe

---

