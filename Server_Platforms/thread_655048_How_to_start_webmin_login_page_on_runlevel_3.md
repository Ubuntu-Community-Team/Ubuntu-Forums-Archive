---
title: "How to start webmin login page on runlevel 3"
date: 2007-12-31
forum: Server Platforms
---

### Post by satimis on 2007-12-31
Hi folks,


Ubuntu 7.04 server amd64


IIRC webmin does not require X to run.  Performed following steps on runlevel 3;

$ sudo /etc/webmin/start login```

Password:
Starting Webmin server in /usr/share/webmin

```

$ /usr/share/webmin/```

Display all 151 possibilities? (y or n)

```


Please advise how to start webmin console/login in page on runlevel 3 instead of running "https://localhost:10000" on browser.  TIA


B.R. and Happy New Year
satimis


OR I need text browser to start webmin?

---

### Post by doogy2004 on 2008-01-01
Maybe I don't fully understand your question.

Webmin is a WEB utility to adMIN your computer.  Hence, it runs as a deamon and is accessed via the WEB by using a WEB browser to access & use it.

---

### Post by satimis on 2008-01-02
> **doogy2004 said:**
> Maybe I don't fully understand your question.

Webmin is a WEB utility to adMIN your computer.  Hence, it runs as a deamon and is accessed via the WEB by using a WEB browser to access & use it.
Having performed following tests with text browser previously but met with failure;


1)
Lynx


$ lynx [https://localhost:10000](https://localhost:10000)```

....
SSL error:Can't find common name in certificate-Continue? (y)
....

```
Ignored the warning and continued.  Finally login webmin as root.

Warning:```

This page uses frames, but your browser doesn't support them.

```
Webmin started with all items displayed but w/o the boxes for changing config.



2)
$ elinks [https://localhost:10000](https://localhost:10000)```

Unable to retrieve https://localhost:10000/: SSL error

```
unabled to login and start webmin.



3)
$ w3m [https://localhost:10000](https://localhost:10000)```

self signed certificate: accept? (y/n) y

Bad cert iden * from localhost: accept? (y/n) y

Accept  unsecure SSL session : Bad cert  iden * from localhost
(it waited a while then displayed)

Option Setting Panel
(w3m version w3m/0.5.1+cvs-1.968)

```


I can't type on it.

Pressing "q"```

Do you want to exit w3m (y/n) y

```
exits webmin


Remark:
Webmin can be started on Firefox running "https://localhost:10000" w/o problem.


I'm trying to find out starting webmin w/o X running.



What I discovered wass on starting Firefox the first time after relogin/reboot following warning popup;```

"localhost" is a site that uses a security certificate to encrypt and 
during transmission, but its certificate expired on Thursdaay, 
December 27,2007 11:05 PM

You should check to make sure that your computers time 
(currently set to Wednesday, January 02, 2008 AM 10:27:34 PST) 
is correct

Would you like to continue anyway?


[Veiw Certificate] [Cancel] [Continue]

```



I'm now poking around on Internet to find a solution.


Advice would be appreciated.  TIA


satimis

---

### Post by doogy2004 on 2008-01-02
So you want to be able to use webmin on a system using only a command line environment?   If this is the case I think that you are missing the point of Webmin.  Webmin is simply a cgi script that is ran in an internet browser.  The cgi that gets run allows a local or remote user to administer the system.

Webmin's purpose is to provide a web interface (GUI) to aid someone in administering system functions and services/daemons.

The reason that you are having problems with text based browsers, such as lynks/elinks is that they do not support how the web page is displayed and how information is passed between the browser and webmin(server).  This is why firefox works fine, except that it is telling you that the certificate provided does not match the actual conditions. (e.g. certificate states that the site is *, but the site is acctually localhost or some ip).  If you do not want to see these warnings download the "Remember Mismatched Domains" extension to firefox and allways accept the certificate.

It seems that you want to use webmin on a computer, to aid you in the administration of the computer.  Correct?  But you don't want the overhead of running X on that computer. Yes?  If you answered yes to the previous two questions then simply do the following:

[LIST=1]
[*]Determine the IP of the computer that you are running Webmin on.  (run the command: ifconfig)
[*]On the remote machine(computer running X), open firefox and go to [https://myserver:10000/](https://myserver:10000/)  Replace "myserver" with the IP that you found in step 1.
[/LIST]

This will allow your server to keep a low overhead, and it will allow you to use webmin as it is intended to be used, as a web interface for remote administration.

Has this explaination helped?

---

### Post by satimis on 2008-01-02
Hi doogy2004,


Thanks for your detail explanation.

One thing I can't resolve.  Previously I was informed somewhere that webmin does not need X to run.  But w/o X it is unable to make it to work locally.

> 
.......
.... This is why firefox works fine, except that it is telling you that the certificate provided does not match the actual conditions. (e.g. certificate states that the site is *, but the site is acctually localhost or some ip).  If you do not want to see these warnings download the "Remember Mismatched Domains" extension to firefox and allways accept the certificate.

Install "Remember Mismatched Domains 1.4.3" on
[https://addons.mozilla.org/en-US/firefox/addon/2131](https://addons.mozilla.org/en-US/firefox/addon/2131)

Restart Firefox (including further test rebooting PC).  The warning disappears.  But on Firefox running;

[https://satimis.com/mail](https://satimis.com/mail)

to start SquirrelMail, the warning pop up again.


> 
It seems that you want to use webmin on a computer, to aid you in the administration of the computer.  Correct?  But you don't want the overhead of running X on that computer. Yes?  If you answered yes to the previous two questions then simply do the following:

[LIST=1]
[*]Determine the IP of the computer that you are running Webmin on.  (run the command: ifconfig)
[*]On the remote machine(computer running X), open firefox and go to [https://myserver:10000/](https://myserver:10000/)  Replace "myserver" with the IP that you found in step 1.
[/LIST]

This will allow your server to keep a low overhead, and it will allow you to use webmin as it is intended to be used, as a web interface for remote administration.

Noted with thanks.


> 
Has this explaination helped?
Yes, certainly.  Thanks


B.R.
satimis

---

### Post by rsw686 on 2008-01-02
> **satimis said:**
> Hi doogy2004,
Thanks for your detail explanation.

One thing I can't resolve.  Previously I was informed somewhere that webmin does not need X to run.  But w/o X it is unable to make it to work locally.


WebMin doesn't need X to run the service. That is all that means.

---

### Post by doogy2004 on 2008-01-02
> **rsw686 said:**
> WebMin doesn't need X to run the service. That is all that means.

Dito,  for future reference a service and a daemon are refering to the same type of program.  One that runs in the background, typically started at the startup of the computer.  From my experience, the word service is typically used in windows and daemon is used in GNU/Linux/BSD/OSX.

---

