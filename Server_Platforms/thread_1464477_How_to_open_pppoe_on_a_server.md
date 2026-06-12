---
title: "How to open pppoe on a server?"
date: 2010-04-28
forum: Server Platforms
---

### Post by expatCM on 2010-04-28
The two methods in this link work to open the Internet connection
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)
but they are no good on a server.  The server stops loading processes as soon as it finds the pppoe command, it opens the connection and stops.  This stalls the server.

The command
pon dsl-provider 
works from a terminal but as soon as you close the terminal the connection closes.

I was thinking to use a script.  Something like 
```
#! /bin/sh
# command to start dsl connection when server starts
pon dsl-provider
```
and then put it in init.d But this seems to be too straight forward.

I was also thinking of using the dsl tab on the network manager from a client to open the connection but I could not figure out how to set this to talk to the server.

....  could anyone please tell me what is the proper way of dealing with this?

---

### Post by redmk2 on 2010-04-28
> **expatCM said:**
> The two methods in this link work to open the Internet connection
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)
but they are no good on a server.  The server stops loading processes as soon as it finds the pppoe command, it opens the connection and stops.  This stalls the server.

The command
pon dsl-provider 
works from a terminal but as soon as you close the terminal the connection closes.

I was thinking to use a script.  Something like 
```
#! /bin/sh
# command to start dsl connection when server starts
pon dsl-provider
```
and then put it in init.d But this seems to be too straight forward.

I was also thinking of using the dsl tab on the network manager from a client to open the connection but I could not figure out how to set this to talk to the server.

....  could anyone please tell me what is the proper way of dealing with this?

Try running the command in the background.  This allows you to close the shell.  The command would look like this```
pon dsl-provider &
```

See [**_here _**]("http://linux.about.com/od/glossary/l/bldef_bgprocess.htm")for a description.

---

### Post by expatCM on 2010-04-28
Thank you for that suggestion redmk2, I need to sleep now but I will be taking a look at this in detail in the morning ..........

---

### Post by expatCM on 2010-05-01
I have managed to solve this using a program called Monit.  Monit is in the repositories and really worth taking a look at.  There is even quality documentation ...  ok so you have to read it but it is well set out.

I added the following 
> 
# check pppd
check process pppd with pidfile /var/run/ppp0.pid
 start program = "/usr/bin/pon dsl-provider"
 stop  program = "/usr/bin/poff dsl-provider"

# internet test
check host internet with address [www.google.com](www.google.com)
    if failed icmp type echo count 5 with timeout 30 seconds
        then exec "/usr/bin/killall -9 pppoe pppd" 
to the monit configuration file and for me this has solved the problem very well.

---

