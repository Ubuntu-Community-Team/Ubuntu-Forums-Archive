---
title: "Unable to enter localhost"
date: 2009-10-23
forum: Server Platforms
---

### Post by Roger Steiner on 2009-10-23
I have a working file server running 9.04. It became necessary to shut the server down for a power outage. When I powered up the server, it appeared that all was well until I tried to access it from a connected desktop. The error message advised that Samba shares were not available.

I went into the server and tried to access Webmin using Firefox and address [https://localhost:10000](https://localhost:10000)
Firefox advised that localhost:10000 uses an invalid security certificate and I am unable to access Webmin.

Is there a work-around?

Can I start the server by another means?

---

### Post by windependence on 2009-10-23
Are you sure you didn't just misinterpret the error message? Firefox will present you with this, but still allow you to continue if you tell it to do so. This is common with certificates you create yourself because they are not known to Firefox.

The SAMBA shares probably did not reconnect because you don't have it set to start at bootup. You could try starting SAMBA from the command line.

-Tim

---

### Post by OpenGuard on 2009-10-23
```
sudo /etc/webmin/start
sudo /etc/init.d/webmin start

```One of them should start Webmin ( haven't used it for a while .. can't verify ).

---

