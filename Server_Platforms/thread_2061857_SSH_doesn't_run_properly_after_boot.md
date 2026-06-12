---
title: "SSH doesn't run properly after boot"
date: 2012-09-23
forum: Server Platforms
---

### Post by tofagerl on 2012-09-23
Openssh-server gives an error after boot forcing me to manually restart the service from a tty. This is a headless box, so that's not what you might call "practical"
Error:  ```
ssh_exchange_identification: Connection closed by remote host
```

---

### Post by cariboo on 2012-09-23
Try running:

```
ssh -v user@server
```

that should show you the error, if not add another ***v***

---

### Post by markbl on 2012-09-24
Look in /var/log on the server for any sshd error messages.

---

### Post by tofagerl on 2012-09-24
This is all I found: fatal: Missing privilege separation directory: /var/run/sshd

That directory exists now, though, and the message was three days old. I've rebooted several times since then, with SSHD not accepting anything.

ssh -vv gave nothing, but then that was run clientside, so I'm not sure what you were looking for...

---

### Post by markbl on 2012-09-24
> **tofagerl said:**
> This is all I found: fatal: Missing privilege separation directory: /var/run/sshd

That directory exists now, ..

You gotta be concerned how such an odd issue arose though? I suspect you have other problems in your installation. Perhaps flush and reinstall on your server?
```

sudo aptitude purge openssh-server
sudo aptitude install openssh-server

```

---

### Post by tofagerl on 2012-09-25
Well, this happened about a week after I formatted and installed 12.4. I had used arch just for fun, but it was driving me up the wall, so I went back to ubuntu for stability. 

I might do a complete reinstall, it wouldn't be a huge problem for me, but as far as possible I'd like to know what went wrong first.

---

### Post by Lars Noodén on 2012-09-25
Does /var/log/syslog say anything about sshd's startup?  What about stopping sshd and then starting it manually in debug mode?

```

sudo service ssh stop
sudo /usr/sbin/sshd -Dd

```

---

### Post by tofagerl on 2012-10-12
This is still happening. There's nothing in syslog when I grep for ssh.

---

### Post by Lars Noodén on 2012-10-12
Was there anything telling from "/usr/sbin/sshd -Dd" ?

---

### Post by tofagerl on 2012-10-12
Yes and no...

stop: Unknown instance:

It's a headless server, so I can't manually stop and restart the server, it has to be in one line.

---

### Post by Lars Noodén on 2012-10-12
What do you get when you manually check the server's configuration?

```

/usr/sbin/sshd -T

```

It should produce a list rather than an error message.  If there is an error message, what is it?

---

### Post by tofagerl on 2012-10-12
> **Lars Noodén said:**
> What do you get when you manually check the server's configuration?

```

/usr/sbin/sshd -T

```

It should produce a list rather than an error message.  If there is an error message, what is it?

root@hamster:~# /usr/sbin/sshd -T
port 22
protocol 2
addressfamily any
listenaddress 0.0.0.0:22
listenaddress [::]:22
usepam 1
serverkeybits 768
logingracetime 120
keyregenerationinterval 3600
x11displayoffset 10
maxauthtries 6
maxsessions 10
clientaliveinterval 0
clientalivecountmax 3
permitrootlogin yes
ignorerhosts yes
ignoreuserknownhosts no
rhostsrsaauthentication no
hostbasedauthentication no
hostbasedusesnamefrompacketonly no
rsaauthentication yes
pubkeyauthentication yes
kerberosauthentication no
kerberosorlocalpasswd yes
kerberosticketcleanup yes
gssapiauthentication no
gssapikeyexchange no
gssapicleanupcredentials yes
gssapistrictacceptorcheck yes
gssapistorecredentialsonrekey no
passwordauthentication yes
kbdinteractiveauthentication no
challengeresponseauthentication no
printmotd no
printlastlog yes
x11forwarding yes
x11uselocalhost yes
strictmodes yes
tcpkeepalive yes
permitblacklistedkeys no
permitemptypasswords no
permituserenvironment no
uselogin no
compression delayed
gatewayports no
usedns yes
allowtcpforwarding yes
useprivilegeseparation yes
pidfile /var/run/sshd.pid
xauthlocation /usr/bin/xauth
loglevel INFO
syslogfacility AUTH
authorizedkeysfile .ssh/authorized_keys .ssh/authorized_keys2
hostkey /etc/ssh/ssh_host_rsa_key
hostkey /etc/ssh/ssh_host_dsa_key
hostkey /etc/ssh/ssh_host_ecdsa_key
acceptenv LANG
acceptenv LC_*
subsystem sftp /usr/lib/openssh/sftp-server
maxstartups 10:100:10
permittunnel no
ipqos lowdelay throughput
permitopen any
root@hamster:~#

---

### Post by Lars Noodén on 2012-10-12
That looks normal.  But in post #10 above, you mentioned something that looks like an error.  Is that the full error from "/usr/sbin/sshd -Dd"  ?

---

### Post by tofagerl on 2012-10-12
> **Lars Noodén said:**
> That looks normal.  But in post #10 above, you mentioned something that looks like an error.  Is that the full error from "/usr/sbin/sshd -Dd"  ?

No, that's from "service stop ssh".

---

### Post by tofagerl on 2012-10-12
> **tofagerl said:**
> No, that's from "service stop ssh".


I'd like to repeast that upon restarting SSHD, everything's fine. It's just after a reboot that it doesn't work.

---

### Post by Lars Noodén on 2012-10-13
Upstart does not seem to log much in the way of errors, though it should.  That's the information that is missing.  What does your upstart configuration file look like?  It should be /etc/init/ssh.conf

---

### Post by tofagerl on 2012-10-13
> **Lars Noodén said:**
> Upstart does not seem to log much in the way of errors, though it should.  That's the information that is missing.  What does your upstart configuration file look like?  It should be /etc/init/ssh.conf

# ssh - OpenBSD Secure Shell server
#
# The OpenSSH server provides secure shell access to the system.

description     "OpenSSH server"

start on filesystem or runlevel [2345]
stop on runlevel [!2345]

respawn
respawn limit 10 5
umask 022

# 'sshd -D' leaks stderr and confuses things in conjunction with 'console log'
console none

pre-start script
    test -x /usr/sbin/sshd || { stop; exit 0; }
    test -e /etc/ssh/sshd_not_to_be_run && { stop; exit 0; }
    test -c /dev/null || { stop; exit 0; }

    mkdir -p -m0755 /var/run/sshd
end script

# if you used to set SSHD_OPTS in /etc/default/ssh, you can change the
# 'exec' line here instead
exec /usr/sbin/sshd -D

---

### Post by Hoox on 2012-10-27
Running Ubuntu Server 12.04.1 I also got this problem. Very frustrating.
I tried manually creating /var/run/sshd and giving it 0755 permissions. Makes sshd start, but the folder is gone at next reboot and same error is showing.

---

### Post by tofagerl on 2012-10-27
Interestingly, that does not work for me. The sshd-folder is not created in /var/run, but after creating it, chmoding, and rebooting, it still doesn't run.

**BUT **it's still deleted!

To me, this points to the init-script as the possible culprit, but surely this is the same for all users, so if that's the problem it has to be combined with another variable..

---

