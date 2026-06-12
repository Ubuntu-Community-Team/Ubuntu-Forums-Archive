---
title: "Is this behaviour of the Ubuntu India Mirror alright?"
date: 2010-06-01
forum: Security
---

### Post by gphilip on 2010-06-01
Hi,

  I am from India, and I tried to update my Ubuntu system today. 

```
$ sudo apt-get update

```

The update failed because the connection to the India mirror timed out:

```
Err http://in.archive.ubuntu.com lucid Release.gpg                                                                                                                     
  Could not connect to in.archive.ubuntu.com:80 (111.91.91.37). - connect (110: Connection timed out)

```

I tried the update a few times, with the same result every time.

I had firestarter running at this time, and noticed that I would get new security events every time I tried an update. I checked the events list, and it turned out that the machine at the ip address 111.91.91.37 (the in.archive.ubuntu.com machine, to go by the above error message) had been trying to make connections to seemingly random ports on the machine every time I tried the update: see the attached screenshot.

I then changed my repositories to the Main Server using Synaptic, and tried the update again (from the command-line). This time it worked without a hitch, and firestarter did not report any unwanted incoming connection.

So my question is: why is the India mirror trying to open connections that the Main server apparently does not need in order for me to do the update? Should I (we) be concerned?

Thanks,
Philip

---

### Post by cdenley on 2010-06-02
That mirror does seem to be online at the moment. When you establish a connection to a web server, the TCP port used on your end is a high random number such as what you see. What you're probably seeing in firestarter is the response to your connection attempt. I suggest finding an alternative to firestarter since it is no longer maintained.

---

### Post by brunolabs on 2010-06-02
I've been having that problem a lot lately.
But with the Ubuntu Main Server though. So I guess it's not just an indian server problem.

---

### Post by gphilip on 2010-06-03
> **cdenley said:**
> That mirror does seem to be online at the moment. When you establish a connection to a web server, the TCP port used on your end is a high random number such as what you see. What you're probably seeing in firestarter is the response to your connection attempt. I suggest finding an alternative to firestarter since it is no longer maintained.


Thank you, that explains it.

Regards,
Philip

---

