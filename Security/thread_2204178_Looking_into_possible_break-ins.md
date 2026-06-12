---
title: "Looking into possible break-ins"
date: 2014-02-07
forum: Security
---

### Post by s0mba on 2014-02-07
Hello,
Need help on looking into possible break in.
```
$ lastlog 
Username         Port     From             Latest
root             pts/0    ***    Sat Feb  2 02:42:37 +0400 2013
...

```
Searching the auth.log for the IP address and the timestamp did not give any results..
Any leads on how to proceed?

Thanks.

---

### Post by tomearp on 2014-02-07
Try
```
last -i | grep root
```

What services are you running? e.g. SSH

---

### Post by s0mba on 2014-02-07
Hi,
Sorry forgot to mention..
> last -i also does not show a root entry at all..
Looks like the logs on that were cleared or something..

Services in use are SSH, Apache, and MySQL (accessible only from localhost),
i.e. a very basic web server setup...

Thanks.

---

### Post by cariboo on 2014-02-07
If you are running a default Ubuntu Server installation, the root account isn't enabled, so you won't see any entries for root in the logs. It also depends on how your server is connected to the internet, if any of the services are open to the world, you may see attempted root logins in auth.log, but you haven't given us enough information to really answer your question.

---

### Post by s0mba on 2014-02-10
The machine is connected to the Internet, and is being used as simple web server..
It's not a default installation. The root login was enabled, and it was enabled for SSH as well (disabled now).
I do see a lot of login attempts for the root user in the auth.log (which is a "normal" thing I believe with
so many bots and alike running automated). But the strange thing is that I did not find anything related
to the login that I see in the lastlog (searching the auth.log for the timestamp and the IP address from
lastlog did not yield any results).
What other logs can I possibly look into? And is it possible to check if the log file was manually altered?

Thanks.

---

### Post by tomearp on 2014-02-11
If you have an entry for root in lastlog, the root account was enabled, root login was enabled for SSH at that time, and it definitely wasn't you; then I would assume someone gained unauthorized access.

---

### Post by ubudog on 2014-02-11
Do you use password authentication for ssh?

---

### Post by bashiergui on 2014-02-11
> **ubudog said:**
> Do you use password authentication for ssh?
Good question. 

Look at all your auth logs and sys logs. Make sure you can find logs for the timeframe you're concerned about. If you're missing chunks of time in logs then that's a pretty good indicator of compromise.

---

### Post by s0mba on 2014-02-13
Yes, password authentication is used for ssh. Will have to change that to use keys (good lesson)..
I'm not sure how check if the logs were tampered.. But I do not see the timestamp for the login in
question..
Could someone possibly point out a good tutorial/how-to on practices/procedures for investigation
of such cases.

Thanks.

---

### Post by Habitual on 2014-02-13
Have a look/read over at [https://www.linuxquestions.org/questions/linux-security-4/security-references-45261/](https://www.linuxquestions.org/questions/linux-security-4/security-references-45261/) for some excellent references by a very skilled Linux exploit enthusiast.
I've heard he's a "developer" or coder for one for the more popular exploits "kits" on the Linux platform, and I'll leave it at that.

---

### Post by raja.genupula on 2014-02-13
Open your terminal and type 

> ac -p

When you have done that, It will list all users and their total active time. Advantage is it wont calculate service users active times. you will get only users time report. That will help you to find out as which unfamiliar account name is in the list.


one more: you can move in a way like , how to differentiate system users & service users.

---

### Post by s0mba on 2014-02-25
> **Habitual said:**
> Have a look/read over at [https://www.linuxquestions.org/questions/linux-security-4/security-references-45261/](https://www.linuxquestions.org/questions/linux-security-4/security-references-45261/) for some excellent references by a very skilled Linux exploit enthusiast.
I've heard he's a "developer" or coder for one for the more popular exploits "kits" on the Linux platform, and I'll leave it at that.

Thanks. Will take lots of time to review, though. Some stuff on the list might be outdated, but it gives a good overview of the areas to look into..

Redeployed the server now. With root over ssh disables, and ssh keys..
As a side note: this [http://www.sshguard.net/](http://www.sshguard.net/) might be an option if you are annoyed by the ssh brute-force traces in your auth.log...

Thanks for all the suggestions.

---

### Post by Habitual on 2014-02-25
> **s0mba said:**
> Thanks. Will take lots of time to review, though. Some stuff on the list might be outdated, but it gives a good overview of the areas to look into..

Redeployed the server now. With root over ssh disables, and ssh keys..
As a side note: this [http://www.sshguard.net/](http://www.sshguard.net/) might be an option if you are annoyed by the ssh brute-force traces in your auth.log...

Thanks for all the suggestions.

Don't be misled by the "dated" Security Info. much of the techniques are **V**ery Relevant.
[fail2ban]("https://help.ubuntu.com/community/Fail2ban") also works "out of the box" for ssh intrusions as well and in a repo near you.


That, with ssh-keys only, you are on your way.

---

