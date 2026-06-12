---
title: "SSHD refuses connection after sleep?"
date: 2016-11-18
forum: Server Platforms
---

### Post by timonoj on 2016-11-18
Hi guys,

I'm installing a new Ubuntu Server 16.04 on a new miniPC I just purchased. After the minimal install (no extra options installed), I add openssh-server in order to get SSH. And I log in from there and start running my stuff from the SSH. After 10 mins or so, the server screen goes to sleep, and I immediately get a broken pipe on my SSH terminal. Attempting to reconnect result in connection refused. Hitting a key on the server wakes up the screen, and the server is responsive and connected to the network, but the ssh keeps refusing connection. After a reboot, it STILL refuses connection. If I purge remove the openssh-server and reinstall it, it works again...until the next time it sleeps. What can I do?

Thanks!

---

### Post by darkod on 2016-11-18
Why are you putting it to sleep? And did you install the ubuntu server or desktop version? Because I have never seen the server version going to sleep, it shouldn't do that by default.

Although it's strange that ssh is not working even after a reboot, I would focus first to why would you want a server going to sleep and maybe the way you set it up has something to do with ssh not continuing to work after it wakes up. Are you doing this for power saving, etc?

---

### Post by timonoj on 2016-11-18
Nah, not putting it to sleep by myself...not really full sleep either, but the screen disables itself to sleep mode. At that exact moment the connection dies. It still responds to ping. This is a brand new installation of Ubuntu Server 16.04, with no options or additional configuration added. Just set static IP, openssh and...then this.

---

### Post by darkod on 2016-11-18
Hmmm... weird... Maybe because I never have monitors connected to servers... Have you tried unplugging the monitor just to see what happens?

No ubuntu server has even gone to sleep/power down mode to me... ever... Not sure if having a monitor connected might produce some power saving settings...

I assume you've googled the situation?

---

### Post by timonoj on 2016-11-18
Yeah, but nothing came up related to SSH and "sleep" or "suspend"...So I'm not sure what it is. I reckon it's not really sleep, just one of the many middle states a CPU can reach, but heck what do I know...
Ok, I unplugged the HDMI and let's see how this goes. But it's rather weird behavior.

---

### Post by timonoj on 2016-11-18
Yeah, but nothing came up related to SSH and "sleep" or "suspend"...So I'm not sure what it is. I reckon it's not really sleep, just one of the many middle states a CPU can reach, but heck what do I know...
Ok, I unplugged the HDMI and let's see how this goes. But it's rather weird behavior.

EDIT: Yeah...After about 10 minutes I still got kicked with no return.

EDIT2: Ok. Stupid me. We can close the thread...Duplicated IP with the Pioneer Amplifier. Most of the time it's idling and doesn't use the network...but I guess it checks every 10 minutes.

---

### Post by darkod on 2016-11-18
Hahaha... Good catch... :) Watch out with the static IPs, have to make sure not duplicating them... You can mark it as Solved in Thread Tools above the first post. Cheers.

---

