---
title: "Ubuntu 12.04 Server requires reboot after update"
date: 2013-05-19
forum: Server Platforms
---

### Post by fernandoch on 2013-05-19
Hello,

I have a production ubuntu 12.04 server, and in like 3 months I had to reboot it two times because of updates. 

How are you guys managing to avoid these reboots after updates?

Thank you.

---

### Post by darkod on 2013-05-19
Whether it will say a restart is needed or not depends on the updates themself. Even if you don't restart the server will work for months even years. Whether you want to do the restart so it can use the latest updated packages or not depends on you.

Try to schedule it for the time period when you least need the server.

---

### Post by fernandoch on 2013-05-19
Has anyone tried ksplice?

---

### Post by sandyd on 2013-05-19
KSplice works with Ubuntu quite well, though you still have to update (but not restart).

---

### Post by fernandoch on 2013-05-19
Yes I know I have to update... But is it free for an ubuntu server? Or does it only work with desktop? Have you tried it?

---

### Post by CharlesA on 2013-05-19
> **fernandoch said:**
> Yes I know I have to update... But is it free for an ubuntu server? Or does it only work with desktop? Have you tried it?

Only free for Ubuntu Desktop (and Fedora), which is why I don't use it.

---

### Post by fernandoch on 2013-05-20
and the desktop version does not work for a server?

---

### Post by LHammonds on 2013-05-20
You don't "have to" reboot after an update...but you should in order for the update to take affect.  Most updates do not require a reboot and take affect immediately.  The ones that require a reboot are the ones such as kernel updates that only load up during a reboot.

I have my servers scripted to get security-only updates on a daily basis.  All the servers are monitored by a Nagios server and Nagios lets me know when a server is wanting a reboot to apply a kernel update and I schedule the reboot for an appropriate time for the server.  This is the only time my servers reboot and I am usually there to watch the reboot and to clean up any old kernel images afterwards.  I have this all documented on my Ubuntu Server thread in my sig below.

**EDIT:** I don't use ksplice and I'm not interested in it either since I like to maintain the minimum number of packages necessary.  I would assume any package designed only for desktops would require a GUI interface.

LHammonds

---

### Post by CharlesA on 2013-05-20
I do the same as LHammonds when it comes to updates that require reboots. Some don't make sense to me like an update to openssl, but I just roll with it.

When I looked at the ksplice site, they had a command line tool, but I dunno how they detect which OS you are actually running.

LHammonds : Thanks for the Nagios info that was linked in your sig - it'll help me finish getting it set up at work. :)

---

### Post by fernandoch on 2013-05-20
I know that not all updates require a reboot but when I login I see this

```
System information as of Fri May 10 10:58:19 CEST 2013

  System load:  0.1                Processes:           129
  Usage of /:   1.1% of 463.53GB   Users logged in:     1
  Memory usage: 40%                IP address for eth0: 5.135.181.224
  Swap usage:   0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

0 packages can be updated.
0 updates are security updates.

*** System restart required ***
```

It means my server needs a reboot :)

---

### Post by LHammonds on 2013-05-20
I have a script that tells me what packages are requiring the reboot.  The custom script is called "check_apt_motd.sh" (which requires Nagios Plugins to be installed)

Example output:
```
Reboot required to apply linux-image-3.5.0-30-generic linux-base
```

The script and how to install the Nagios Plugins for a remote server can be found in the Nagios link in my sig below.

The above is what I see on my Nagios Monitoring web page as well as when I run it manually (rarely ever do).  If you install it, you could modify your login profile to run it so you see the output everytime you login to that server instead of just the basic message.

LHammonds

---

### Post by fernandoch on 2013-05-20
Thank you I saw that this cat gives the details

```
root@ks83747920:~# cat /var/run/reboot-required.pkgs
libssl1.0.0
```

---

### Post by LHammonds on 2013-05-20
Yes, that is the core of what the script makes use of.  Here is a partial snippet of the code that looks at it:

```

PKGS=$(echo $APTRES | cut -f1 -d';')
SEC=$(echo $APTRES | cut -f2 -d';')

if [ -f /var/run/reboot-required ]; then
        REBOOT=1
        TOAPPLY=`cat /var/run/reboot-required.pkgs`
else
        REBOOT=0
fi

if [ "${PKGS}" -eq 0 ]; then
        if [ "${REBOOT}" -eq 1 ]; then
                RET=$STATE_WARNING
                RESULT="Reboot required to apply ${TOAPPLY}"
        else
                RET=$STATE_OK
                RESULT="No packages to be updated"
        fi
elif [ "${SEC}" -eq 0 ]; then
        RET=$STATE_WARNING
        RESULT="${PKGS} packages to update (no security updates)"
else
        RET=$STATE_CRITICAL
        RESULT="${PKGS} packages (including ${SEC} security) packages to update"
fi

echo $RESULT

```

**EDIT:**

libssl1.0.0 is one of those patches that would not have been automatically applied in my apt upgrade script since it is not listed as a security patch.  You only get that one if you type something like **aptitude safe-upgrade**

---

### Post by fernandoch on 2013-05-20
Well what I did was only apt-get upgrade and that package got upgraded... I did not use aptitude safe-upgrade

---

### Post by LHammonds on 2013-05-20
I think "upgrade" and "safe-upgrade" may be the same.  I do know that "full-upgrade" and "dist-upgrade" are the same.  The core of my script calls the command with specific parameters so that it only applies security patches.

Example:
```
aptitude safe-upgrade --assume-yes --target-release `lsb_release -cs`-security
```

---

### Post by sandyd on 2013-05-21
> **CharlesA said:**
> Only free for Ubuntu Desktop (and Fedora), which is why I don't use it.

Not really.
See [http://www.ksplice.com/uptrack/manual-installation#](http://www.ksplice.com/uptrack/manual-installation#)

---

### Post by fernandoch on 2013-05-21
Yes, but you might have to get a license for a server...

---

### Post by CharlesA on 2013-05-21
> **sandyd said:**
> Not really.
See [http://www.ksplice.com/uptrack/manual-installation#](http://www.ksplice.com/uptrack/manual-installation#)

Hmmm... It says say this:

```
echo 'uptrack uptrack/accesskey string INSERT_ACCESS_KEY' | debconf-set-selections
```

I wonder how they tell the difference between server and desktop.

---

### Post by fernandoch on 2013-05-21
This is what I was wondering too...

---

### Post by sandyd on 2013-05-21
They dont
Just [get the access key]("http://www.ksplice.com/uptrack/key"), put it in, and it works for both desktop and server.

---

### Post by fernandoch on 2013-05-21
Thank you sandyd :)

---

