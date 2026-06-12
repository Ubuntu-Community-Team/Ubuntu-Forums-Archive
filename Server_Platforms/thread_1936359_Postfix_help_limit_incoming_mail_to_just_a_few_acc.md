---
title: "Postfix help: limit incoming mail to just a few accounts?"
date: 2012-03-05
forum: Server Platforms
---

### Post by webservervideos on 2012-03-05
Hello.
I am new to postfix and have it working so far, even through ssl.
There is one issue I cannot resolve and not sure what to do.

IN a nutshell: I want my mail/web server to only accept incoming mail addresses to user1 and user2, and no one else. I want all local mail not blocked (such as cron to root).

The local delivery is working fine.
However I can receive mail from any user listed in the shadow file (and alias file) and they are relayed to root.....

root is getting spammed to high heaven. 

I have 2 books on postfix, have spent many hours a day in the last week, but cannot find how to prevent all but a couple users from getting incoming mail without blocking normal local mail stuff.

any ideas?

---

### Post by HermanAB on 2012-03-06
Howdy,

Your best source for postfix information is not books, but rather the postfix.org web site ([http://www.postfix.org/STANDARD_CONFIGURATION_README.html#some_local):](http://www.postfix.org/STANDARD_CONFIGURATION_README.html#some_local):)
```
Delivering some but not all accounts locally

A drawback of sending mail as "user@example.com" (instead of "user@hostname.example.com") is that mail for "root" and other system accounts is also sent to the central mailhost. In order to deliver such accounts locally, you can set up virtual aliases as follows:

    1 /etc/postfix/main.cf:
    2     virtual_alias_maps = hash:/etc/postfix/virtual
    3 
    4 /etc/postfix/virtual:
    5     root     root@localhost
    6     . . .

Translation:

    Line 5: As described in the virtual(5) manual page, the bare name "root" matches "root@site" when "site" is equal to $myorigin, when "site" is listed in $mydestination, or when it matches $inet_interfaces or $proxy_interfaces.

Execute the command "postmap /etc/postfix/virtual" after editing the file. 
```

---

### Post by webservervideos on 2012-03-06
> **HermanAB said:**
> Howdy,

Your best source for postfix information is not books, but rather the postfix.org web site ([http://www.postfix.org/STANDARD_CONFIGURATION_README.html#some_local):]("http://www.postfix.org/STANDARD_CONFIGURATION_README.html#some_local%29:")
```
Delivering some but not all accounts locally

A drawback of sending mail as "user@example.com" (instead of "user@hostname.example.com") is that mail for "root" and other system accounts is also sent to the central mailhost. In order to deliver such accounts locally, you can set up virtual aliases as follows:

    1 /etc/postfix/main.cf:
    2     virtual_alias_maps = hash:/etc/postfix/virtual
    3 
    4 /etc/postfix/virtual:
    5     root     root@localhost
    6     . . .

Translation:

    Line 5: As described in the virtual(5) manual page, the bare name "root" matches "root@site" when "site" is equal to $myorigin, when "site" is listed in $mydestination, or when it matches $inet_interfaces or $proxy_interfaces.

Execute the command "postmap /etc/postfix/virtual" after editing the file. 
```

true dat about the books.

Solution was to use local_maps and just add some users there. Stopped all incoming mail except to those users and allows all local deliveries.

some other stuff too, but I will either post a vid or add it to a small sys admin book I am going to write for this kind of stuff...book..yea, I know, internet better..lol

---

