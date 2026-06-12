---
title: "Crontab to open specific ports"
date: 2009-11-27
forum: Security
---

### Post by BrentC on 2009-11-27
I know this sounds absurd just by reading the title, but hear me out. I am trying to find an elegant way to add a crontab to open a specific inbound port(s) every once and awhile on my server. 

Why? Port knocking. In essence, I am actually opening a port to ensure that another port is closed *almost* all the time. Make sense now? Good. :)

I am trying to get some ideas on how to accomplish this without a lot of overhead and/or more security risks. So far all I have come up with is running a crontab to SSH to the server using the port. I don't like this idea though and it wasn't working when I tried it earlier.

Google almost has no relevant returns to this subject. Most of them are about closing open ports, oh the irony. Not really asking for code, just wondering if anyone has any other ideas on how to implement this since my last method wasn't working.

---

### Post by Aearenda on 2009-11-27
You should be able to do that with 'ufw', which is installed by default in Ubuntu.

However, to avoid re-inventing the wheel, take a look at [this discussion]("http://ubuntuforums.org/showthread.php?t=1221987"), [this thread]("http://ubuntuforums.org/showthread.php?t=812573"), and [this page]("http://www.cipherdyne.org/fwknop/").

Personally, I find that the use of a mandatory RSA key along with a high port for SSH is secure enough.

---

### Post by kevdog on 2009-11-27
Take a look at the fwknop port knocking application.  It sounds like what you want.  The implementation would be a lot more secure than just randomly opening up a port at a set interval for a period of time.

---

### Post by Lars Noodén on 2009-11-29
> **kevdog said:**
> Take a look at the fwknop port knocking application.  

These two documents help with that:

[https://help.ubuntu.com/community/PortKnocking](https://help.ubuntu.com/community/PortKnocking)

[https://help.ubuntu.com/community/SinglePacketAuthorization](https://help.ubuntu.com/community/SinglePacketAuthorization)

If it is a mater of restricting access to certain minutes or hours, then 
xinetd can be used by not running sshd standalone:

```

update-rc.d ssh remove

```

The configure the file xinetd.d/ssh:

```

service **ssh**
{
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/sbin/sshd
        server_args     = **-i**
        per_source      = UNLIMITED
        log_on_success  = USERID HOST DURATION
        access_times    = **9:00-9:30** **12:00-16:00**
}

```

---

