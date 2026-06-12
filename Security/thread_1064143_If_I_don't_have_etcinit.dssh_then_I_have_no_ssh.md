---
title: "If I don't have /etc/init.d/ssh then I have no ssh ???"
date: 2009-02-08
forum: Security
---

### Post by Browser_ice on 2009-02-08
I am currently following the AdvancedOpenSSH and when I wanted to restart sshd, I got this :

> sudo /etc/init.d/ssh restart
sudo: /etc/init.d/ssh: command not found

I thought I had done a mistake and went to LS that ssh file but did not find any ***ss**** files at ***/etc/init.d***

So does this mean I have no ssh service running ?  I am confused.

---

### Post by HermanAB on 2009-02-08
Probably sshd

as in:
sudo /etc/init.d/sshd restart

Cheers,

Herman

---

### Post by Browser_ice on 2009-02-08
> **HermanAB said:**
> Probably sshd

as in:
sudo /etc/init.d/sshd restart

Cheers,

Herman

I did point out that I have no /etc/init.d/ss* files at all

so doing  **sudo /etc/init.d/sshd restart**  just prints out 
**sudo: /etc/init.d/sshd: command not found**

---

### Post by wirelessmonkey on 2009-02-08
The implication is that you don't have an ssh Server installed, or at least not a startup script for one. If you installed openssh-server, then it *should* be there.

---

### Post by cariboo on 2009-02-08
By default only the ssh client is installed and it doesn't need a deamon in /etc/init.d. If you have installed openssh-server then you should have /etc/init.d/ssh

Jim

---

### Post by spearsem on 2011-08-29
I am having this same trouble on Ubuntu 11.04. I *do* have openssh installed, but I do not have any file named /etc/init.d/sshd. How can I generate a new version of that file? Rebooting did not succeed in doing this.

---

### Post by bodhi.zazen on 2011-08-29
> **spearsem said:**
> I am having this same trouble on Ubuntu 11.04. I *do* have openssh installed, but I do not have any file named /etc/init.d/sshd. How can I generate a new version of that file? Rebooting did not succeed in doing this.

You do realize that :

1. You are posting on a thread that is close to 3 years old ?

2. Ubuntu uses [Upstart](http://upstart.ubuntu.com/) ?

3. Look in /etc/init

If you still require assistance start a new thread and please explain your problem and what you are wanting to do in more detail.

---

