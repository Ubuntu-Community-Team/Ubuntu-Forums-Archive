---
title: "Newb server question, what do these entries in auth.log mean?"
date: 2012-10-01
forum: Security
---

### Post by ausrick on 2012-10-01
I have a lamp server that beyond my initial setup on it, other than using it for lamp stuff I don't pay it much mind.  Anyway, I decided to look at the auth.log and I'm baffled by what I saw.  I'm not that savvy with the command line, marginally more-so with the gui.  Is the information in the below image normal? or bad? automated process? or attacks?  I know I didn't log in during that time frame.

[IMG]https://dl.dropbox.com/u/54319871/authlog.png[/IMG]

---

### Post by Stonecold1995 on 2012-10-02
Looks fine to me.  If it was an automated attack, there would be a lot of failed logins.

Run this command:
```
grep fail < /var/log/auth.log
```
If there's a lot of output then it means something has been trying to log in and failed repeatedly, which could be an indication of an attack.

---

### Post by 2F4U on 2012-10-02
Usually, "nobody" is a system user, which is used to run services. Find out more about "nobody":

```
sudo grep nobody /etc/passwd
```

On my system, it reveals something like this:

```
nobody:x:99:99:nobody:/:/bin/false
```

The last entry in the line (/bin/false) means, that the user nobody is not allowed to execute a login shell such as /bin/bash and therefore it can't regularly login to your system.

---

### Post by ausrick on 2012-10-02
Thanks you two!

The only thing that comes up from grep'ing for fail is a reverse mapping checking getaddrinfo that fails with my company firewall address.  These all coincide with timeframes where I ssh'd into my home server from work so I'm assuming this is just saying it couldn't reverse traverse my NAT at work?

When I grep to find nobody's attributes I get the following:

```
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
```

Does that mean I should change some configurations on what nobody is allowed to do?

---

### Post by 2F4U on 2012-10-02
Good question, but highly depends on how concerned you are about security. In general, if nobody has a login shell, as it is in Ubuntu, the nobody account may become the target of a brute force attack. If the permissions on what nobody is allowed to do is changed, there is a certain risk, that some things are no longer working:

[https://wiki.ubuntu.com/nobody](https://wiki.ubuntu.com/nobody)

However, I think it would be save to change the login shell for the nobody account:

[http://secnut.blogspot.de/2009/11/ubuntu-nobody-user.html](http://secnut.blogspot.de/2009/11/ubuntu-nobody-user.html)
[http://linuxg.net/the-linux-and-unix-nobody-user/](http://linuxg.net/the-linux-and-unix-nobody-user/)

This is quite a little change, but would at least prevent anybody from attacking this user account.

---

### Post by Stonecold1995 on 2012-10-02
> **ausrick said:**
> Does that mean I should change some configurations on what nobody is allowed to do?

I don't think you need to.  That's what the output is on my computer and a fresh install in VirtualBox.

---

### Post by Stonecold1995 on 2012-10-02
> **2F4U said:**
> Good question, but highly depends on how concerned you are about security. In general, if nobody has a login shell, as it is in Ubuntu, the nobody account may become the target of a brute force attack.

I thought the nobody account is locked, and only root can log in?

---

