---
title: "Server load on clean install and &quot;free -m&quot; results."
date: 2011-03-31
forum: Server Platforms
---

### Post by simolokid4 on 2011-03-31
Dear Ubuntuforums,

Recently I've gotten myself a VPS and tried to begin small - 512 MB Memory, 10gb HD.

Ubuntu 10.04 got installed on it and decided to make a user for myself besides root, installed a lamp enviroment and let that extra user own /var/www, since im the only one developing on the vps.

Then I ran the free -m command... shockingly it had 450 mb in use, and around 40-60 mb free (varieing around a bit).

Is this normal? If so - why are company's selling vps'es with 256 mb ram... thats just ... not logical ;x

Ran the free -m command again after letting it idle for about 5 mins. Same results.

the 'top' command tells me that the cpu is boring itself with around 1% use.. not a suprise with only lamp on it and 0 visitors yet =P

So ... why does ubuntu take up nearly all my precious memory? should I upgrade to 1 GB of memory to be completely safe I dont run out of resources or is something else going on here?

Thanks in advance for any answer :)

Simolokid.

[Edit]
Discovered I was miss-reading the free -m command. To avoid confusion in the future I install htop, which is configurable to show a... nicer view of what's being used by what. Turns out I was using 50 mb.. >.>

---

### Post by Vegan on 2011-03-31
My old machine has 512 MB and its not a problem. I am using the latest version.

Now obviously more RAM would help but only if the server load is that heavy.

---

