---
title: "Have I been Hacked?"
date: 2009-06-09
forum: Security
---

### Post by DBQ on 2009-06-09
Hi everybody.  Before shutting down my laptop today, got a message warning me that if I shutdown "other" users can be logged off.  After examining my auth.log, I found this suspicious entry (where xxxxx is the name of my computer being masked):

Jun  7 16:12:14 xxxxxxxx su[2811]: Successful su for jetty by root
Jun  7 16:12:14 xxxxxxxx su[2811]: + console root:jetty
Jun  7 16:12:14 xxxxxxxx su[2810]: Successful su for jetty by root
Jun  7 16:12:14 xxxxxxxx su[2810]: + ??? root:jetty
Jun  7 16:12:14 xxxxxxxx su[2811]: pam_unix(su:session): session opened for user jetty by (uid=0)
Jun  7 16:12:14 xxxxxxxx su[2810]: pam_unix(su:session): session opened for user jetty by (uid=0)
Jun  7 16:12:15 xxxxxxxx su[2811]: pam_unix(su:session): session closed for user jetty
Jun  7 16:12:15 xxxxxxxx su[2810]: pam_unix(su:session): session closed for user jetty

BTW, I run VirtualBox (I heard stories that sometimes the message warning about logging out other users appears as a result of that).  Any ideas?

---

### Post by cariboo on 2009-06-09
I was playing with the guest user the other day and got the same message. To find who is logged on to your computer open a terminal and type:

```
who
```

Running the above command I get the following output.

```
who
jim     tty7         2009-06-09 10:35 (:0)
jim     pts/0        2009-06-09 11:14 (:0.0)
```

In the above output the first user is me running the desktop note the tty7, it also dispalys the time the desktop was started. The second user is also me with a terminal open pts/0.

---

### Post by DBQ on 2009-06-09
I did not play around with Guest.  

What is this "jetty" thing which supposedly gained the root access. There is no such user on my system.  Thank You!

---

### Post by Zimmer on 2009-06-09
[http://rbytes.net/linux/jetty-review/](http://rbytes.net/linux/jetty-review/)

[http://docs.codehaus.org/display/JETTY/port80](http://docs.codehaus.org/display/JETTY/port80)

Were you running some Java stuff?

[http://linux.open.ac.uk/157/lieber.html](http://linux.open.ac.uk/157/lieber.html)

---

