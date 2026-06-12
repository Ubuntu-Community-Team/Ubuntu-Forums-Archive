---
title: "Odd ports open?"
date: 2010-06-29
forum: Security
---

### Post by w0Rm210 on 2010-06-29
I decided to do a bit of computer securing yesterday and i scanned my IP for open ports i came up with a few normal ones FTP and http and some other normal ones.

But i did find two very odd ones with odd services

Port 3388 with service unknown and it was open
Port 10080 with service of amanda:confused::confused::confused:

I blocked all incoming and outgoing connections from both ports and nothing seems to be wrong but i would like to know how and why theyre there. Any help is appriciated :D ):P

---

### Post by yeleek on 2010-06-29
1) Did the you scan the machine from itself, or from another host?  You can get strange results (at least with NMAP) if you scan yourself

2) 

[http://wiki.zmanda.com/index.php/Quick_start](http://wiki.zmanda.com/index.php/Quick_start)

amanda 10080/udp

amandaidx 10082/tcp

amidxtape 10083/tcp

---

### Post by w0Rm210 on 2010-06-29
> **yeleek said:**
> 1) Did the you scan the machine from itself, or from another host?  You can get strange results (at least with NMAP) if you scan yourself

2) 

[http://wiki.zmanda.com/index.php/Quick_start](http://wiki.zmanda.com/index.php/Quick_start)

amanda 10080/udp

amandaidx 10082/tcp

amidxtape 10083/tcp

Well at first i got a little worried seeing a human name pop up but yes i was scanning myself then the second time i had a very trustworthy friend scan it. He got the exact same results. But what does that amanda port belong to? I have a list of ports and none of them came up as 10080 or 3388 -_- kinda creepy actually.

---

### Post by yeleek on 2010-06-29
Amanda - Look at the link provided (its backup software)

3388 - Depends what you used, if you used NMAP and that couldn't tell you what it was.  You could try
```
netstat -nlp | grep 3388
```

See what it comes up with.

When you say you got your friend to scan you, is that on the same LAN as you?  or over the internet?

And why isn't your firewall blocking these ports if you don't know what they are/want them?

---

### Post by w0Rm210 on 2010-06-29
> **yeleek said:**
> Amanda - Look at the link provided (its backup software)

3388 - Depends what you used, if you used NMAP and that couldn't tell you what it was.  You could try
```
netstat -nlp | grep 3388
```See what it comes up with.

When you say you got your friend to scan you, is that on the same LAN as you?  or over the internet?

And why isn't your firewall blocking these ports if you don't know what they are/want them?

My firewall does what i tell it to so i scan for open ports and search for vulnrabilities in 10.10 and 10.04 and then i secure them accordingly. Its not set to auto block anything because you never know what i may be running and if it were to block something and it become a hassle then it kinda diminishes its own cause right?:lolflag:
Ill check that link and thanks for your answers ):P
P.s: It was over the net.

---

### Post by CharlesA on 2010-06-29
Running *sudo netstat -tulnp* will show you which process is using that port (as well as UDP ports) and that should help narrow it down.

---

### Post by yeleek on 2010-06-29
> **w0Rm210 said:**
> My firewall does what i tell it to so i scan for open ports and search for vulnrabilities in 10.10 and 10.04 and then i secure them accordingly. Its not set to auto block anything because you never know what i may be running and if it were to block something and it become a hassle then it kinda diminishes its own cause right?:lolflag:
Ill check that link and thanks for your answers ):P
P.s: It was over the net.

I'm sorry but thats madness.  You've ports open to the internet, which you don't know why they are open, what services they are relevant to and they aren't being blocked by your firewall....

I can't help you any further.

---

### Post by CharlesA on 2010-06-29
> **w0Rm210 said:**
> My firewall does what i tell it to so i scan for open ports and search for vulnrabilities in 10.10 and 10.04 and then i secure them accordingly. Its not set to auto block anything because you never know what i may be running and if it were to block something and it become a hassle then it kinda diminishes its own cause right?:lolflag:
Ill check that link and thanks for your answers ):P
P.s: It was over the net.

Pardon me, but that sounds like a very, very stupid thing to be doing. The purpose of a firewall is to block unwanted services from the local network and/or internet.

If you have it set to accept everything, what's the point of having a firewall? If you add a new service, you can always use netstat -l to see what port it's listening to and add a rule to the firewall to allow that port.

---

### Post by Rubi1200 on 2010-06-29
+1 to what yeleek and CharlesA are saying.

By the way, have you read this?

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by w0Rm210 on 2010-06-29
> **Rubi1200 said:**
> +1 to what yeleek and CharlesA are saying.

By the way, have you read this?

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
 

Yes i have.

And to [CharlesA]("http://wwww.ubuntuforums.org/member.php?u=923868")

It blocks anything i tell it to block i dont have it set to allow everything i check my ports do a portscan on my own computer then have a family member on LAN do a port scan on my IP and then have a friend over the net do so also then if i find something gone weird or odd i block it auto style then i check my listening ports i scan its a daily process i was just wondering why i have an unknown process and something with a human name which turns up to be backup software that i never installed and ive been up all night working this down but i have the ports blocked and a couple hundred IPs as well.

---

### Post by bodhi.zazen on 2010-06-29
If you are not sure what is listening on those ports you can use a number of tools.

Personally I like lsof

```
sudo lsof -i -n -P
```

---

### Post by CharlesA on 2010-06-29
> **bodhi.zazen said:**
> If you are not sure what is listening on those ports you can use a number of tools.

Personally I like lsof

```
sudo lsof -i -n -
```

Nice. Thanks. :-)

Except you had an extra "-" so it should be:

```
sudo lsof -i -n
```

---

### Post by bodhi.zazen on 2010-06-29
> **CharlesA said:**
> Nice. Thanks. :-)

Except you had an extra "-" so it should be:

```
sudo lsof -i -n
```

no, I missed the P, see revised post ...

---

### Post by CharlesA on 2010-06-29
Ah ok. Thanks.

---

