---
title: "How to find out which process is using a port"
date: 2014-01-07
forum: Security
---

### Post by Luft on 2014-01-07
Sometimes I see messages in pglgui (A firewall frontend / utility) telling me that it has blocked out going packets on a particular port to a particular IP address.  Is there anyway for me to find out which process is trying to send data to this IP / port?

Thanks.

---

### Post by steeldriver on 2014-01-07
You could try

```
sudo lsof -i :*portnum*
```
or
```
sudo netstat -np | grep :*portnum*
```

---

### Post by CharlesA on 2014-01-07
You can try capturing the packets with Wireshark or the like, but since you didn't mention which port or IP was being blocked, that will be of little use to us.

---

### Post by s0mba on 2014-01-08
Just to add a little to what steeldriver already mentioned.
Take a look at this: [http://www.cyberciti.biz/faq/what-process-has-open-linux-port/](http://www.cyberciti.biz/faq/what-process-has-open-linux-port/)
It covers netstat, lsof, and fuser usage.

---

### Post by Habitual on 2014-01-08
```
alias oports='echo '\''User:      Command:   Port:'\''; echo '\''----------------------------'\'' ; sudo lsof -i 4 -P -n | grep -i '\''listen'\'' | awk '\''{print $3, $1, $9}'\'' | sed '\''s/ [a-z0-9\.\*]*:/ /'\'' | sort -k 3 -n |xargs printf '\''%-10s %-10s %-10s\n'\'' | uniq'
```

output:
```

root       sshd       22        
root       inetd      37        
root       inetd      113       
root       cupsd      631       
jj         skype      63606
```

for a quick and dirty check.

---

### Post by clearski on 2014-01-11
Habitual,

great script. I added it to my alias file, after I shortened the alias from 6 to 2 letters: *op. *It's faster. :smile:

Thanks for sharing it!

---

