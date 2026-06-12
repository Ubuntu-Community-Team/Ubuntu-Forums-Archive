---
title: "i'm in need of help..."
date: 2006-09-10
forum: Server Platforms
---

### Post by lamarchk on 2006-09-10
Hi! 

im jun and i've been using ubuntu since hoary hedgehog. i've setup this 36 cpu "internet facility" in the foundation where students are free to surf the web for their specific researches. Now the setup was not too bad... but the updating and the upgrading seem a bit tedious now that the additional help is  not available no more. now i'm searching the web for an "update server" type of setting for my ubuntu box which also runs my vnc client (for me to be able to. 

thanks a many for the future help.

---

### Post by rastilin on 2006-09-11
I'm not following at all.

What is it that you're trying to do? Do you want to upgrade between distributions on the server?

---

### Post by lamarchk on 2006-09-11
i'm sorry if you can't follow me... 

let me explain my problem further...

to keep it simple...

i would like to setup an "update server" so that i will save time rather than executing "apt-get update", "apt-get upgrade" and "apt-get dist-upgrade" on every single pc the facility has got. i though if i could setup an "update server" in the facility i would only download the fixes and update once and all the other cpus will connect to it and be able to update themselves also. 

is there any possible way to do this...

i do hope it simplifies everything... sorry for the first post.

thanks

---

### Post by Frogger on 2006-09-11
The only thing that comes to mind is to write a bash script to log onto each individually using ssh and run apt-get update, but it seems like you are suggesting another method which I know little about.
What do you want this server to do?

---

### Post by Frogger on 2006-09-11
I need an idea of specific services etc.

---

### Post by rastilin on 2006-09-11
I suspect what you need is to get a proxy to cache the deb packages as they are downloaded, so you're only downloading them once. I believe squid and polipo support this. Otherwise you would need to rsync off a target computer, so here's how I do it here.

sudo rsync -rv 192.168.2.4:/var/cache/apt/archives /var/cache/apt/

Write a script to download the archives of a main computer with rsync, then update and upgrade themselves in the normal way. As long as the main computer upgrades itself more frequently, this will insure that downloads are kept to a minimum. The updating and upgrading can be handled with a cron command.

---

### Post by lamarchk on 2006-09-11
hey many thanks... i will try it as soon as possible... i will keep you posted on the developments as i try it... thank you very much

---

### Post by Tomosaur on 2006-09-13
I think the thin-client method would be much better for this, but your server would need to be pretty beefy to handle it.

Alternatively, you could write a script which did all of this and set up a cron job to execute it every week or something. That way you'd never have to touch the machines again.

---

