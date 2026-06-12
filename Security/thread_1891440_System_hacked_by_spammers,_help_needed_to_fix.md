---
title: "System hacked by spammers, help needed to fix"
date: 2011-12-05
forum: Security
---

### Post by ehime on 2011-12-05
It appears that I have had my system hacked by spammers over the last few days,
I received a shutdown notice from our provider until I can get this figured out. I'm
displaying the information that I believe is pertinent, please feel free to ask questions
that will help clarify or give advice.

Auth.log [http://pastebin.com/nfM4vMLD](http://pastebin.com/nfM4vMLD)

lastlog [http://pastebin.com/LtS6BVx5](http://pastebin.com/LtS6BVx5)

Mail.log [http://www.themonastery.org/mail.log](http://www.themonastery.org/mail.log) (804k)

I have removed the queue from /var/spool/mqueue, but how did there get to be a queue?
They were owned by root:smmsp :( This did NOT stop our servers from spamming people.

---

### Post by CharlesA on 2011-12-05
Take the machine off the network and either wipe it and reinstall or make an image so you can find out how someone got in, then wipe it and reinstall.

Just looking at your auth.log shows that you were owned by a bruteforce SSH attack. Secure SSH properly and do not allow root logins as you can always su to root if you have it enabled.

---

### Post by Dangertux on 2011-12-08
> **CharlesA said:**
> Take the machine off the network and either wipe it and reinstall or make an image so you can find out how someone got in, then wipe it and reinstall.

Just looking at your auth.log shows that you were owned by a bruteforce SSH attack. Secure SSH properly and do not allow root logins as you can always su to root if you have it enabled.


Rate limiting on the SSH service via iptables or denyhosts (or both) with keys should do you just fine in the future.

Good luck :-)

---

### Post by CharlesA on 2011-12-08
> **dangertux said:**
> rate limiting on the ssh service via iptables or denyhosts (or both) with keys should do you just fine in the future.

Good luck :-)
+1. :)

---

