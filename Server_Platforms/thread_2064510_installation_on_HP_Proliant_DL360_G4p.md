---
title: "installation on HP Proliant DL360 G4p"
date: 2012-09-29
forum: Server Platforms
---

### Post by cfisupply on 2012-09-29
Hi There, I don't know if this is the right place to post, but I'll take a shot.

I'm relatively new to servers, though I have a few "re-purposed" desktop pcs that I have been mostly successfully in installing and running ubuntu (& xubuntu) on, but now I am trying to "upgrade" to improve my network capabilities.

I found in a local college surplus sale two HP Proliant DL360 G4p servers and was told they were working when pulled, they just wanted to upgrade. From my testing, there is no OS installed (they told me they though it'd been wiped).

Is there any "special" requirements on installing ubuntu (or xubuntu) on this type of server? Has anyone out there successfully installed and deployed such a server? I know there old, but couldn't really complain for the price.

To explain what I'm hoping to do with them. One I would like to use as a LAMP server for web development & maybe keep some space for a file sharing server. The second one... well, I kinda would like it to be a media server to store movies & music (don't know if I'm asking too much). For now though, I'm mainly concerned with getting the LAMP running.

Please share your expertise, experiences or any other helpful tidbits/suggestions that would help me get these going.

---

### Post by darkod on 2012-09-29
The server would usually have a raid card. As long as ubuntu can recognize it and install on it, there should be no problems. And it should recognize it just fine in most cases.

So just give the server installation a go and see. I suggest you use only LTS versions for servers, like the latest 12.04.1 LTS.

For LAMP select the LAMP role/task when it asks you during installation. You also probably want to select the OpenSSH so you can control it by SSH.

Even when old, the servers should work fine with ubuntu server especially if you don't start adding GUI desktops etc.

I haven't had a chance to install on DL360 G4 but few months back I installed on quite old Dell Poweredge 850 which only had Pentium D cpu and it runs just fine.

---

### Post by cfisupply on 2012-09-29
Thanks! I thought it should be alright, but being my first "real" server it was making me nervous.

One thing I am excited about though is these servers are huge compared to my re-purposed pcs. Each of them have two 146gb hard drives... my pcs only had 40gb!

---

### Post by darkod on 2012-09-29
On a server you would usually run the disks in a RAID1 mirror array, which means only 146GB usable space.

But that way if one disk dies the server goes on and gives you the chance to replace the failed disk.

---

### Post by cfisupply on 2012-09-29
Ok, Thanks again!

---

