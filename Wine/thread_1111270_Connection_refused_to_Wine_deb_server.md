---
title: "Connection refused to Wine deb server"
date: 2009-03-30
forum: Wine
---

### Post by blaise69 on 2009-03-30
Hi there,

I'm trying to add the Wine dev releases to my package manager so that I can use the latest builds, however I'm getting refused from their sever.

Even if I use a web browser on [http://wine.budgetdedicated.com/archive/index.html]("http://wine.budgetdedicated.com/archive/index.html") I get a not authorised message (although is says it may not be available at the current time).

I followed the instructions from the website [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb") to set up my package manager, have tried both with synaptic and with apt-get.

I'm also not behind a proxy.

Any help would be really appreciated.

Cheers,

Blaise.

---

### Post by YokoZar on 2009-03-30
Should be fixed now, I had to restart something on the web server.

---

### Post by voxel on 2009-03-30
I have had the wine repository set up for quite a while now and performed numerous updates, but now I am also having the same problem: getting connection refused.

---

### Post by Flatuance on 2009-03-30
I can't connect to the server anymore either.  I also can't import the GPG key as well

---

### Post by hikaricore on 2009-03-30
Be patient I'm sure it will be all fixed in no time.

---

### Post by voxel on 2009-03-31
Oh yeah, I'm not grumbling! Hopefully it didn't sound like that :)

---

### Post by blaise69 on 2009-03-31
[UPDATE]
This now works without problem, it must have been a server issue, perhaps due to traffic, as the new version of Wine had just been released.
[/UPDATE]

> **YokoZar said:**
> Should be fixed now, I had to restart something on the web server.

Hmm, when I follow the instructions on [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) I still have permission and access trouble.

Trying to download Scott Ritchie's authentication key gives me a browser window with a Page Load Error, "The connection was refused when attempting to contact wine.budgetdedicated.com."

Running the command line method;
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
Gives me a report: "gpg: no valid OpenPGP data found."

Is anyone else still having trouble with this?

---

### Post by bilkos on 2009-08-31
Ok I see it's been a loooong time since the last post.:)

Unfortunatley I'm also having this problem with "Connection Refused".
I did manage to get it downloaded yesterday on my stationary PC, now that I want to install it on my notebook I get this error:

```
W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/hardy/Release.gpg  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/hardy/main/i18n/Translation-en_US.bz2  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
```I don't want to push anyone to work... just a notice. I'll wait for repo to be online whenever that is. I Love Ubuntu and great work Wine Team. =D>

---

### Post by edwford on 2009-08-31
I'm also getting the error. Done it before, but today, it's a no no. I assume it's more a matter of waiting for it to be accessible that something I can do to fix it.

---

