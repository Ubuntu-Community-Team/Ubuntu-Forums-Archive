---
title: "vpn vps proxy ftp on 10.04 lts ubuntu server"
date: 2012-07-19
forum: Server Platforms
---

### Post by Craigst on 2012-07-19
im very new to sever hosting but have rented a vps server for verious reasons
1. website hosting (will work on later)
2. teamspeak server (up and working)
3. vpn (having lots of issues)
4. proxy (want all my internet to go via same as vpn)
" want static ip on all my devices"
5. ftp server (to share all my files
6. download torrent movies and stream (not a clue where to start)
7. minecraft server (java install issues)
 
as i said im new and got little exeriance , server has static ip , so pptpd settings may be the problem .
i had a test server at home i have been playing with but hard to test vpn on home network
 
server has a unlimited fast internet and up to 4gb of ram 50gb of hd space 
 
anyone that could help me set this up would be greatly appricated 
 
regards craig

---

### Post by Craigst on 2012-07-19
anyone can help me with any of the ports ?

---

### Post by sandyd on 2012-07-19
> **Craigst said:**
> im very new to sever hosting but have rented a vps server for verious reasons
1. website hosting (will work on later)
2. teamspeak server (up and working)
3. vpn (having lots of issues)
4. proxy (want all my internet to go via same as vpn)
" want static ip on all my devices"
5. ftp server (to share all my files
6. download torrent movies and stream (not a clue where to start)
7. minecraft server (java install issues)
 
as i said im new and got little exeriance , server has static ip , so pptpd settings may be the problem .
i had a test server at home i have been playing with but hard to test vpn on home network
 
server has a unlimited fast internet and up to 4gb of ram 50gb of hd space 
 
anyone that could help me set this up would be greatly appricated 
 
regards craig
Post output of
```

sudo apt-get install pastebinit
cat /etc/pptpd.conf | pastebinit
cat /etc/ppp/pptpd-options | pastebinit

```

btw, are you on an openvz vps?

---

### Post by Craigst on 2012-07-20
openvz vpn ??
[http://pastebin.com/VYZg69ir](http://pastebin.com/VYZg69ir)
[http://pastebin.com/5xuuQrG4](http://pastebin.com/5xuuQrG4)
 
ip , <snip>
vpn
user : <snip>
password : <snip>

---

### Post by sandyd on 2012-07-20
i meant an openvz **vps **not an openvz **vpn**

---

### Post by Elfy on 2012-07-20
> **Craigst said:**
> openvz vpn ??
[http://pastebin.com/VYZg69ir](http://pastebin.com/VYZg69ir)
[http://pastebin.com/5xuuQrG4](http://pastebin.com/5xuuQrG4)
 
ip , <snip>
vpn
user : <snip>
password : <snip>

If the information here was made up - put it back if you wish

Otherwise - google has indexed this thread and that IP and password are all out there for anyone to see till the thread's reindexed.

---

### Post by Craigst on 2012-07-21
i made the user name and password so u guys could check and see y it messes ups :s i duno what i have , i posted the ip and vpn password ect , google had idexed ? sorry im still very new to this

---

