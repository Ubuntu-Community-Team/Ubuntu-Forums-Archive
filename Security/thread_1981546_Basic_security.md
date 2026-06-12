---
title: "Basic security"
date: 2012-05-17
forum: Security
---

### Post by praveenkumarpon on 2012-05-17
Hi, I am new to Ubuntu.

I have been using Windows7 all these days. Basically, to keep it secure, I turn on Auto updates, use Microsoft Security Essentials, Push UAC control settings to the highest, disable browser cookies and Use Sandboxie when I browse a lot.

Can you mention certain basic tweaks to Ubuntu 12.04 like the ones that we'd do on a Win7 - like firewall settings/ Antivirus and anything that is supposed to be done basically.

---

### Post by Soul-Sing on 2012-05-17
!) there are great security sticky's here on this forum.

my small contribution: disable things you don't need via start-up applications

```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```
now you have list of applications with applications that start automagically. Don't need them? Disable them.

<Disable the avahi deamon.

<Enable ufw, with strong outbound rules. See the security sticky's.

<Monitor your system with:

```
netstat -taupen
```
```
netstat -tulnp
```
```
sudo lsof -n -P -i
```

lets discuss the outcome

---

### Post by HermanAB on 2012-05-17
Howdy,

Ubuntu Linux is pretty secure out of the box.  You need not do anything.

Relax and enjoy your nice new, secure computer, the way the computer gods intended...

---

### Post by Hungry Man on 2012-05-17
```
tcp        1      0 192.168.1.116:55800     91.189.89.134:80        CLOSE_WAIT  1000       13022       4526/python     

```

Just thought I'd try one of those tips. What is this?

---

### Post by unspawn on 2012-05-17
> **Hungry Man said:**
> What is this?
//If your question doesn't address the OP's questions wouldn't it be better to start your own thread?
If it's not a transient process try:
```
sudo lsof -Pwlnp 4526; sudo cat -v /proc/4526/{cmdline,environ}
```
and see [this thread]("http://ubuntuforums.org/showthread.php?t=1961081") wrt the remote address.

---

### Post by Hungry Man on 2012-05-17
> //If your question doesn't address the OP's questions wouldn't it be better to start your own thread?

Seemed relevant considering:
> lets discuss the outcome

And I don't think that a single line warrants another topic.

I'll give that topic a read, thanks.

---

### Post by Ms. Daisy on 2012-05-17
To the OP, the [basic security wiki]("https://wiki.ubuntu.com/BasicSecurity") was written to specifically answer your question. Give it a read. A few other wikis hang off of that one and are useful in answering your question.  Then you can read Bodhi.zazen's [security sticky ]("http://ubuntuforums.org/showthread.php?t=510812")in the security forum.

---

