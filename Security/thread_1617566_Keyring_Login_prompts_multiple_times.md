---
title: "Keyring Login prompts multiple times"
date: 2010-11-09
forum: Security
---

### Post by cooltd825 on 2010-11-09
It's been awhile since I've been on here.  I suppose that can be considered a good thing, since I made the completely transfer to Ubuntu three months ago and everything's been running completely smoothly.

Anyway, security is a pretty big thing to me.  I usually change the root password, take sudo off (and default gksu, not gksudo), encrypt my hard drives, etc...  One thing I also do is create a separate password for my login keyring.  I don't mind having to enter one extra password at login, but it started prompting two times, and now three.  It's the same password every time, so my question is..  why is it doing this?  Has anyone encountered a similar problem?

Thanks!

---

### Post by DaleAnderson on 2010-11-24
I have also experienced this problem of late. Does anyone know of a solution?

---

### Post by jevejo777 on 2010-12-29
Same problem here. Is there already any known solution for this?
Please reply.

UPDATE:
I found possible answers on askubuntu.com
see: [unlock keyring promts three times instead one time]("http://askubuntu.com/questions/7578/unlock-keyring-promts-three-times-instead-one-time")

---

### Post by smokydig on 2011-02-22
i to was having this highly irritating issue having to re-enter my login keyring pass 2-3 times after much research and narrowing down stuff I discovered by removing the chat accounts under the user main menu drop down on the task bar solved this problem for me yay finally!!

---

### Post by FoxEWolf on 2011-02-22
I have experienced this problem only once; however, I was able to determine the cause of the problem right away. The laptop that I was using didn't have built in Wireless and I was obtaining the signal through Linksys card. The Linksys card would somtimes disconnect from the Access point and in order for it to reconnect it would prompt me to access the keyring. It turned out that the network card was failing and kept reseting itself. I highly doubt that this is the case for you, but it would not hurt to make sure that your connections are secure. As for the internal usage of the keyring (data encryption), I would select "Always Allow" and see if this eliminates the need to prompt multiple times. I would think that if you'd change the root password, It would prompt again due to the stored password not matching the new one.

---

