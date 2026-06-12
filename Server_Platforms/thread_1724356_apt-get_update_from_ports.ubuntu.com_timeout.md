---
title: "apt-get update from ports.ubuntu.com timeout"
date: 2011-04-08
forum: Server Platforms
---

### Post by NickFankhauser on 2011-04-08
I just got a SheevaPlug with ubuntu installed on it. But I have a problem I can not solve: Running "apt-get update" hangs at "[Connecting to ports.ubuntu.com (91.189.88.36)]", and then timeouts. But "ping ubuntu.com" works, so the connection to the inet is there.
It has "deb [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty main restricted universe multiverse" in /etc/apt/sources.list.
Strangely, "ping ports.ubuntu.com" does not work, but I can connect to [http://ports.ubuntu.com](http://ports.ubuntu.com) from my laptop.
What could be the problem?

---

### Post by falko on 2011-04-08
Might be a temporary problem. Can you try again?

---

### Post by 7iton on 2011-04-08
> **falko said:**
> Might be a temporary problem. Can you try again?

I've been having the same problem with the SheevaPlug for at least 48 hours

---

### Post by tomwigwam on 2011-04-12
I pinged ports.ubuntu.com from another Ubuntu machine and it redirected the ping to wahoo.canonical.com. Changing it in /etc/apt/sources.list seems to have fixed this on my Sheevaplug, allowing me to apt-get again, although I'm not sure how 'recommended' this is.

---

### Post by kinnison41 on 2011-04-22
I just noticed this same problem on my sheevaplug. I couldn't ping ports.ubuntu.com from it either.
But then I tried pinging it from a dos box on my PC and it worked fine (different IP address though, 91.189.92.175. 
Then I suddenly had an idea, looked in the hosts file on the sheevaplug, and there it was - a hardcoded IP address for ports.ubuntu.com :-
91.189.88.36 ports.ubuntu.com

I just commented this out with a # on the front, and apt-get update works fine now.
Not quite sure why it was hard-coded into the hosts file though????

Hope this helps anyone else in the same situation.

Cheers, 

Chris.

---

### Post by adrianrosian on 2012-01-19
Thank you very much, I have the same problem, hope this helps

---

### Post by adrianrosian on 2012-01-19
Except that it didn't, as it seems jaunty isn't supported anymore. Have to install debian now

---

### Post by wc3 on 2012-02-20
I found the fix [here]("http://plugcomputer.org/plugwiki/index.php/New_Plugger_How_To#Fixing_the_existing_Ubuntu_install"). 

Just update your /etc/apt/sources.list from ```
deb http://ports.ubuntu.com jaunty main restricted universe multiverse
``` to ```
deb http://old-releases.ubuntu.com/ubuntu jaunty main restricted universe multiverse
```

---

