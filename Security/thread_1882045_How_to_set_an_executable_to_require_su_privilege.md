---
title: "How to set an executable to require su privilege?"
date: 2011-11-16
forum: Security
---

### Post by PeterTaps on 2011-11-16
Folks,

This may be a simple question. 

I would like to set up an executable such that the user is required to run it as su:

$ sudo myapp

It is a matter of just changing ownership to root:root?

Thank you in advance for your help.

Regards,
Peter

---

### Post by matt_symes on 2011-11-16
Hi

> **PeterTaps said:**
> Folks,

This may be a simple question. 

I would like to set up an executable such that the user is required to run it as su:

$ sudo myapp

It is a matter of just changing ownership to root:root?

Thank you in advance for your help.

Regards,
Peter

Change ownership to root as you say.

```
sudo chown root:root /path/to/file
```Then change the permissions so that only root can run it.

```
sudo chmod 744 /path/to/file
```744 is read/write and execute for root user; read only for root group and everybody else.

Kind regards

---

### Post by CharlesA on 2011-11-16
That would work, but if it's a shell script you can just add this:

```
if [[ $(id -u) != "0" ]]; then
echo "Must be root!"; exit 1
fi
```

[http://www.cyberciti.biz/tips/shell-root-user-check-script.html](http://www.cyberciti.biz/tips/shell-root-user-check-script.html)

---

### Post by PeterTaps on 2011-11-17
Thank you all for your help.

Regards,
Peter

---

### Post by Jonathan L on 2011-11-18
Hi Peter

Just as Matt says, but should really chmod 700, or the enterprising user can copy the file and make their copy executable and run that.

If it's your own script and you're just checking so that you don't get cryptic error messages, then of course they do run it, but it quits, just as Charles describes.

Kind regards,
Jonathan

---

### Post by matt_symes on 2011-11-18
Hi

> **Jonathan L said:**
> Hi Peter

Just as Matt says, but should really chmod 700, or the enterprising user can copy the file and make their copy executable and run that.

If it's your own script and you're just checking so that you don't get cryptic error messages, then of course they do run it, but it quits, just as Charles describes.

Kind regards,
Jonathan

Good call Jonathan. That slipped my mind. Must be getting old....... 

Kind regards

---

