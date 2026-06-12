---
title: "Starting Services after booting"
date: 2009-10-31
forum: Server Platforms
---

### Post by asemrany on 2009-10-31
i have installed two new servers (application) recently.
but I have a problem while booting up the server,
the two services do not start,
so  i can start the two services manually by running these commands:-

/opt/honeywell/bin/lucid-server.py start
/etc/init.d/vsftpd.dpkg-new start

so i made a .sh file contains these two commands
but i need to make this file executable  while booting the server ?? How?


Thanks,

---

### Post by PixelDJ on 2009-11-01
Maybe this will help?

[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by Lars Noodén on 2009-11-02
For this one. you have a control script already:
/etc/init.d/vsftpd.dpkg-new 

The old way is to use update-rc.d to set it running:

```

# look before you leap
man update-rc.d

# clear the slate
sudo update-rc.d vsftpd.dpkg-new remove

# set it running for most situations except shutdown
sudo update-rc.d vsftpd.dpkg-new start 60 2 3 4 5 . stop 20 1 6 S .

```

The new way is to use 'upstart'

For the other tool, you can copy the vsftpd script and modify it to control your other program.

---

