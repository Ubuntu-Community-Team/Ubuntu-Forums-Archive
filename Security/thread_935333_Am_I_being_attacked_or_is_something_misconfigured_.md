---
title: "Am I being attacked or is something misconfigured? (auth.log)"
date: 2008-10-01
forum: Security
---

### Post by XCan on 2008-10-01
I have noticed that my auth.log is totally spammed with the following messages:
```
Oct  1 21:14:38 med gdm[25888]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Oct  1 21:14:40 med gdm[25888]: pam_unix(gdm:auth): check pass; user unknown
Oct  1 21:14:40 med gdm[25888]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Oct  1 21:14:43 med gdm[25888]: pam_unix(gdm:auth): check pass; user unknown
Oct  1 21:14:43 med gdm[25888]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Oct  1 21:14:46 med gdm[25888]: pam_unix(gdm:auth): check pass; user unknown
Oct  1 21:14:46 med gdm[25888]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Oct  1 21:14:49 med gdm[25888]: pam_unix(gdm:auth): check pass; user unknown
Oct  1 21:14:49 med gdm[25888]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Oct  1 21:14:52 med gdm[25888]: pam_unix(gdm:auth): check pass; user unknown
Oct  1 21:14:52 med gdm[25888]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Oct  1 21:14:55 med gdm[25888]: pam_unix(gdm:auth): check pass; user unknown
Oct  1 21:14:55 med gdm[25888]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Oct  1 21:14:58 med gdm[25888]: pam_unix(gdm:auth): check pass; user unknown
Oct  1 21:14:58 med gdm[25888]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Oct  1 21:15:01 med gdm[25888]: pam_unix(gdm:auth): check pass; user unknown
Oct  1 21:15:01 med gdm[25888]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Oct  1 21:15:04 med gdm[25888]: pam_unix(gdm:auth): check pass; user unknown
Oct  1 21:15:04 med gdm[25888]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Oct  1 21:15:07 med gdm[25888]: pam_unix(gdm:auth): check pass; user unknown
Oct  1 21:15:07 med gdm[25888]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Oct  1 21:15:10 med gdm[25888]: pam_unix(gdm:auth): check pass; user unknown
Oct  1 21:15:10 med gdm[25888]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Oct  1 21:15:13 med gdm[25888]: pam_unix(gdm:auth): check pass; user unknown
Oct  1 21:15:13 med gdm[25888]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Oct  1 21:15:15 med gdm[25888]: pam_unix(gdm:auth): check pass; user unknown
Oct  1 21:15:15 med gdm[25888]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Oct  1 21:15:19 med gdm[25888]: pam_unix(gdm:auth): check pass; user unknown
Oct  1 21:15:19 med gdm[25888]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Oct  1 21:15:21 med gdm[25888]: pam_unix(gdm:auth): check pass; user unknown
Oct  1 21:15:21 med gdm[25888]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
Oct  1 21:15:24 med gdm[25888]: pam_unix(gdm:auth): check pass; user unknown
```

Am I being attacked? I have set up the vnc server included in Ubuntu, and changed its port. Other than that the only service listening that I know is sshd on a non standard port as well.

---

### Post by cariboo on 2008-10-02
Check your /etc/shadow to see if there is a user missing or disabled. In a terminal type:

```
sudo /etc/shadow
```

The only user with a uid of 0 is should be root.

Jim

---

### Post by XCan on 2008-10-02
This is what is shown, and gdm seems to be listed. But I'm not sure what all those other users are. :confused:

```
root:!:14075:0:99999:7:::
daemon:*:14062:0:99999:7:::
bin:*:14062:0:99999:7:::
sys:*:14062:0:99999:7:::
sync:*:14062:0:99999:7:::
games:*:14062:0:99999:7:::
man:*:14062:0:99999:7:::
lp:*:14062:0:99999:7:::
mail:*:14062:0:99999:7:::
news:*:14062:0:99999:7:::
uucp:*:14062:0:99999:7:::
proxy:*:14062:0:99999:7:::
www-data:*:14062:0:99999:7:::
backup:*:14062:0:99999:7:::
list:*:14062:0:99999:7:::
irc:*:14062:0:99999:7:::
gnats:*:14062:0:99999:7:::
nobody:*:14062:0:99999:7:::
libuuid:!:14062:0:99999:7:::
dhcp:*:14062:0:99999:7:::
syslog:*:14062:0:99999:7:::
klog:*:14062:0:99999:7:::
hplip:*:14062:0:99999:7:::
avahi-autoipd:*:14062:0:99999:7:::
gdm:*:14062:0:99999:7:::
pulse:*:14062:0:99999:7:::
messagebus:*:14062:0:99999:7:::
avahi:*:14062:0:99999:7:::
polkituser:*:14062:0:99999:7:::
haldaemon:*:14062:0:99999:7:::
can:$1$vasdf:14075:0:99999:7:::
niclas:$1$aasdf:14085:0:99999:7:::
sshd:*:14075:0:99999:7:::

```

---

### Post by davidryder on 2008-10-02
I get that with SSH. They won't get in as long as you don't have some extremely easy password set.

---

### Post by XCan on 2008-10-02
If it is a bruteforce attempt, how can I look up the IP that the attack originates from?

---

### Post by Titan8990 on 2008-10-02
> If it is a bruteforce attempt, how can I look up the IP that the attack originates from?


This is a hopeless thing that many would like to do. The problem is that script kiddie very rarely will hack from his own IP. Most of the time they will use a bot computer or a proxy so that you can't contact his ISP. Also, the vast majority of these script kiddies are from countries with less restrictive or no computer laws.

---

### Post by XCan on 2008-10-02
> **Titan8990 said:**
> This is a hopeless thing that many would like to do. The problem is that script kiddie very rarely will hack from his own IP. Most of the time they will use a bot computer or a proxy so that you can't contact his ISP. Also, the vast majority of these script kiddies are from countries with less restrictive or no computer laws.

Thanks for you answer. My main goal though is to block the attacking IP(s) from the ranges used by my University.

---

### Post by shqip on 2008-10-02
> **cariboo907 said:**
> Check your /etc/shadow to see if there is a user missing or disabled. In a terminal type:

```
sudo /etc/shadow
```

The only user with a uid of 0 is should be root.

Jim
what about when you get [bash: /etc/shadow: Permission denied] what does that mean?

---

### Post by cariboo on 2008-10-02
Are you having problems with sudo?

Jim

---

### Post by shqip on 2008-10-02
> **cariboo907 said:**
> Are you having problems with sudo?

Jim
i am not sere... this is what i get [sudo: /etc/shadow: command not found]

i am having the same problem trying to configure PSAD ....
bash: /var/lib/psad/psadfifo: Permission denied
[*] Could not find mail, edit /etc/psad/psad.conf at /usr/sbin/psad line 9467.
bash: /etc/psad/psad.conf: Permission denied
and i am running as root@*******:/*********/********#

---

### Post by shqip on 2008-10-02
sere=sure

---

### Post by cariboo on 2008-10-03
The command was:

```
sudo cat /etc/shadow
```

But if you are running as root you don't need sudo. I don't suggest running as root all the time as it can lead to mistakenly screwing up the system. You can do the same with sudo of course, but is is way easier when running as root.

Your problem with psad is you are trying to run files that are not executable. to edit a .conf file you need a text editor for example if you are running as a normal user:

```
sudo nano /etc/psad/psad.conf
```

Will allow you to edit the configuration file.

As for your problem with /var/lib/psad/psadfifo again
psadfifo is not an executeable file, it is a named pipe.

To find how to run pasd in a terminal type:

```
man psad
```

Jim

---

### Post by davidryder on 2008-10-04
> **XCan said:**
> If it is a bruteforce attempt, how can I look up the IP that the attack originates from?

System|Admin|System Log

It will be in the auth.log section. You can filter entries with the string 'sshd' or whatever protocol they are using to get in. The IP along with some other pertinent information will be there. 

In my log they were trying all sorts of logins. 

root
http
ftp
webserver
admin
test

along with a-whole-nother slew of users. They are just looking for common invulnerabilities.

---

