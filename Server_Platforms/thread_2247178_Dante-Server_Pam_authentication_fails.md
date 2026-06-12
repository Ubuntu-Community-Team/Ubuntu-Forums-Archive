---
title: "Dante-Server Pam authentication fails"
date: 2014-10-06
forum: Server Platforms
---

### Post by patrick57 on 2014-10-06
Hi folks,
I have a little bit of a trouble with the dante socks server and authentication.

I've manged to install dante-server via apt-get install dante-server and it is also working without authentication but as soon as i try to enable authentication through PAM Proxifier always gives me the follwing error msg.
> Error : Authentication on the proxy server failed.
    Please check your username and password.

I think i might generate the password file in a wrong way but im not sure about it since Im relatively new to ubuntu :-P
Another thing which is really annoying me is that the log-file doesn't give me any information about the fail of a log in.
Maybe someone can help me out with this Problem :)

Just in case I miss configured something here are the config files.

[B]/etc/danted.conf
[/B]```
## general configuration


internal: venet0:0 port = 443
external: venet0:0
method: pam
user.privileged: root
user.notprivileged: nobody
user.libwrap: nobody
logoutput: stderr /var/log/dante.log


## client access rules


client pass { from: 0.0.0.0/0 to: 0.0.0.0/0 }


## server operation access rules


# allow the rest
pass {
   from: 0.0.0.0/0 to: 0.0.0.0/0
   method: pam
}




```

[B]/etc/pam.d/socksd
[/B]```
auth required pam_pwdfile.so pwdfile=/etc/danted/socks.passwd

```

[B]I created the Login I want to use with
[/B][I]/etc/danted$ sudo htpasswd -cm socks.passwd danteprox
[/I][B]which ends in this result..
/etc/danted/socks.passwd
[/B]```
danteprox:$apr1$IobzuQgk$YdQF.2HaRPzNGIWn80ixG0

```

I appreciate every help!
Thanks in advance!

---

### Post by patrick57 on 2014-10-07
I managed to get this to work maybe there is something wrong with the version of dante-server in the repositories.

this is what i did to fix the issue
> apt-get install build-essential gcc libc6-dev libwrap0 libwrap0-dev


$ cd /usr/src/
$ wget [http://www.inet.no/dante/files/dante-1.4.1.tar.gz]("http://www.inet.no/dante/files/dante-1.3.2.tar.gz")
$ gunzip dante-1.3.2.tar.gz
$ tar -xf dante-1.3.2.tar
$ cd dante-1.3.2/
$ ./configure
$ make
$ make install


$ /usr/local/sbin/sockd -D -N 5 -f /etc/danted.conf
$ tail /var/log/syslog


maybe its going to help some people who have the same issue ;-)

---

