---
title: "Can't install Thunderbird using Ubuntuzilla"
date: 2008-11-20
forum: Ubuntuzilla
---

### Post by Chris62 on 2008-11-20
Hi,

I have just downloaded and run ubuntuzilla-4.5.7-0ubuntu-i386.deb and when I typed ubuntuzilla.py -a install -p thunderbird, I got the following message:

bash: /usr/bin/ubuntuzilla.py: permission denied

I don't understand why this has happened. I have installed Thunderbird on my laptop, my old computer and that of a friend a few weeks ago and it all went as smooth as clockwork. Today I have a new computer and I can't install Thunderbird.

The only difference between today's installation and previous ones is that the previous ones were with Ubuntu 8.04 and the new computer has Ubuntu 8.1

Being fairly new to Ubuntu I don't know how to give myself permission to install Thunderbird - I didn't need permission before. I am the 'administrator' of the new machine

---

### Post by nanotube on 2008-11-20
> **Chris62 said:**
> Hi,

I have just downloaded and run ubuntuzilla-4.5.7-0ubuntu-i386.deb and when I typed ubuntuzilla.py -a install -p thunderbird, I got the following message:

bash: /usr/bin/ubuntuzilla.py: permission denied

I don't understand why this has happened. I have installed Thunderbird on my laptop, my old computer and that of a friend a few weeks ago and it all went as smooth as clockwork. Today I have a new computer and I can't install Thunderbird.

The only difference between today's installation and previous ones is that the previous ones were with Ubuntu 8.04 and the new computer has Ubuntu 8.1

Being fairly new to Ubuntu I don't know how to give myself permission to install Thunderbird - I didn't need permission before. I am the 'administrator' of the new machine

Hi
hmm, could you see the permissions on /usr/bin/ubuntuzilla.py?
```
ls -al /usr/local/bin/ubuntuzilla.py
```

i recently recoded some auto-packaging scripts, maybe i messed up the permissions. if it's not executable, do
```
sudo chmod 755 /usr/local/bin/ubuntuzilla.py
```

and then it should work. :)

---

### Post by nanotube on 2008-11-20
Update: i just made another ubuntuzilla release (4.5.8) that fixes this .deb bug (which was just introduced in this previous release because i changed the .deb packaging script). So best thing to do is to get the latest release and install it, then you won't have any permissions problems.

---

### Post by Chris62 on 2008-11-21
Hi nanotube, thanks for your reply. I have just typed 'ubuntuzilla.sourceforge.net' into Firefox but can't get into the web site; I immediately get invited to download a file called 'auth.php' which appears to be an empty file. I have tried several times, always with that result

I'll try again later

---

### Post by Chris62 on 2008-11-21
Hello again nanotube. I'm just letting you know that I have now downloaded the new version of Ubuntuzilla and have installed Thunderbird. Many thanks for your help

---

### Post by war59312 on 2009-01-01
Yeah I too wondered why script would not run. Upgraded and fine now.

Thanks, just wanted to confirm the fix for ya... Have a great new year every body!!

---

### Post by nanotube on 2009-01-02
Thank you for your feedback. :) good luck in the new year to you as well. :)

---

