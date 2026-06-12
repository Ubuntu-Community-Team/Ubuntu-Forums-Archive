---
title: "VNC SSH question"
date: 2009-09-15
forum: Security
---

### Post by sheridon on 2009-09-15
Hi,

I'm trying to get vncviewer to work via SSH on a different port

I can get vncviewer to work on port 22 with

vncviewer -via name@IPADDY localhost:0

how to I get it to work on a port other than 22.

I changed the port to say 4000 and can ssh in with

ssh name@IPADDY:4000 

how do I get vncviewer to use that port instead of 22?

Thanks in advance!!

---

### Post by issih on 2009-09-15
According to the man pages here:

[http://linux.die.net/man/1/vncviewer](http://linux.die.net/man/1/vncviewer)

you need to set the "VNC_VIA_CMD" environment variable

Setting it to this should work:

```
"/usr/bin/ssh -f -p 4000 -L %L:%H:%R %G sleep 20"
```

which you can achieve with the command:

```
export VNC_VIA_CMD="/usr/bin/ssh -f -p 4000 -L %L:%H:%R %G sleep 20"
```

N.B. I think the quotes are needed, but I'm not sure.

If you run that, then try vncviewer things should work.

If that does sort it out then you would want to put the export command into your .profile.


You may find, however, that you are better served by setting up a per host configuration file for ssh:

[http://unixhelp.ed.ac.uk/CGI/man-cgi?ssh_config+5](http://unixhelp.ed.ac.uk/CGI/man-cgi?ssh_config+5)

Hope that helps

---

