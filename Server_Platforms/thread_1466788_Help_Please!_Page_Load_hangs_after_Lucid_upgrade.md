---
title: "Help Please! Page Load hangs after Lucid upgrade"
date: 2010-04-30
forum: Server Platforms
---

### Post by bgb1122 on 2010-04-30
Greetings!

I just upgraded my server from 9.10 to 10.04.  I have ISPconfig installed on it and worked like a charm until the upgrade.  Now when I point a browser to my site the page just hangs as if it is trying to load it but I never get an error nor does it load the page.  I have tried to restart apache using /etc/init.d/apache2 restart in which I receive an fail error:


root@ubuntu:~# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]

I can successfully kill apache2 with the command: killall apache2
Then start it with /etc/init.d/apache2 start

After this I still get the same results when trying to load the page in the browser.

I cannot load anything in the www root or virtual host files.

Any help would be appreciated!

---

### Post by penguin_patrick on 2010-04-30
I just posted a thread about the ports.conf being different than my 9.10 box, maybe that's got something to do with it?

---

### Post by bgb1122 on 2010-04-30
Thanks for the reply... Tried to modify ports.conf with no luck.

---

### Post by omarino on 2010-05-02
Same problem here after upgrade:
> bp@kubik:/etc/apache2$ /etc/init.d/apache2 start
 * Starting web server apache2                                        apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

Help aprecciated, thanks o

---

### Post by bgb1122 on 2010-05-02
Come to find out, ISPconfig3 is not supported on Lucid yet.  Had to do fresh install with ISPconfig2.

---

