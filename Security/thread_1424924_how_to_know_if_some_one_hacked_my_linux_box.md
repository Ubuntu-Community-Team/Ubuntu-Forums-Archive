---
title: "how to know if some one hacked my linux box"
date: 2010-03-08
forum: Security
---

### Post by venkatad on 2010-03-08
Hi I want to know if any one hacked or getting into my computer.
I am using lucidlynx right now, My computer directly connected to modem, not using any wireless router.
How can i check if some one hacked?
How to prevent it?
thanks in advance....

---

### Post by cdenley on 2010-03-08
You can check /var/log/auth.log to see if someone has authenticated, but attacks don't always involve authentication and if an attacker knows what they are doing, they will cover their tracks and you won't know your system was compromised. To prevent your system from being compromised, simply configure it correctly if it is a server, keep security updates current, and don't do anything stupid. For most users that is sufficient. If you're paranoid, take a look at the security sticky.

---

### Post by Revolutionary101 on 2010-03-08
To find out if you got hacked go to "System>Administration>Log File Viewer". This may seem like a lot to take in but just get used to what it normally looks like and watch for any abnormalities.

To protect your computer make sure that the Ubuntu Firewall is enabled. To enable it go into terminal and type this:

```
sudo ufw enable
```

After doing that, a good program to configure your firewall is gufw. To install it type this into terminal:

```
sudo apt-get install gufw
```

If you need any more help with security related questions, check out this thread.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by rookcifer on 2010-03-08
> **Revolutionary101 said:**
> To find out if you got hacked go to "System>Administration>Log File Viewer". 

It's not that simple.  What if the attacker utilized a buffer overflow exploit?  Nothing will show up in the log files in that case.  There are so many ways to crack a box that merely telling someone to look at log files is not enough.

---

### Post by Revolutionary101 on 2010-03-08
> **rookcifer said:**
> It's not that simple.  What if the attacker utilized a buffer overflow exploit?  Nothing will show up in the log files in that case.  There are so many ways to crack a box that merely telling someone to look at log files is not enough.

I see your point. I didn't think about that.

---

### Post by CharlesA on 2010-03-08
Shouldn't you just check the list of processes that are running for any that seem out of place?

That and run a rootkit detector. Logs work, but they can only go so far.

---

### Post by OpSecShellshock on 2010-03-08
Is there something going on that makes you suspect that your computer has been accessed remotely by an unauthorized person? If so, I'd suggest looking for anything else that it might be. For the most part, gaining direct remote access to a desktop isn't particularly useful to an unauthorized person. Also, if it's a default installation that's running I doubt any unsolicited incoming traffic would be allowed with or without ufw, since iptables should be running from the very beginning.

---

