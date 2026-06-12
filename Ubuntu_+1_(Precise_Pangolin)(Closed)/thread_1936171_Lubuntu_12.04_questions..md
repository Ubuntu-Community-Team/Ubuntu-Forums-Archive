---
title: "Lubuntu 12.04 questions."
date: 2012-03-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dagroves on 2012-03-05
If I want to upgrade to Lubuntu 12.04, how do I do that without downloading the ISO? If I do this, will it break my OS and if it does, how can I recover it?
Thanks!
David

---

### Post by ajgreeny on 2012-03-05
> **dagroves said:**
> If I want to upgrade to Lubuntu 12.04,
1.  how do I do that without downloading the ISO?
2.  If I do this, will it break my OS and if it does,
3.  how can I recover it?
Thanks!
David
1.  You can't at the moment;  you will have to wait for the final release then update-manager should tell you that a new version is avaiable.
2.  Possibly, but some users do it every time a new version arrives with no major problem.
3.  Make sure everything is backed up properly so you will not lose personal files, then probably do a clean installation of the new version.

I have never used the distro update in my 7 years of running ubuntu; always a clean installation, but I have a separate /home partition to make it all easier when IO do so.

---

### Post by Iowan on 2012-03-05
Moved to Ubuntu +1 (Precise Pangolin)

---

### Post by pinguinhood on 2012-03-06
If you already use Lubuntu and want to upgrade to 12.04 you can try
```
sudo update-manager -d
```
but **it's not stable** yet!!!
You can find the new beta ISO [here]("http://cdimage.ubuntu.com/lubuntu/releases/12.04/beta-1/") if you want to try it in live mode.

---

### Post by dagroves on 2012-03-06
Yesterday I did ```
 sudo update-manager -d
``` and I am now on Lubuntu 12.04. So far it is working great! It is fast and I am enjoying it! I have noticed that the Network Indicator shows for about 5 minutes then goes bye bye, it is still there, I can click on it, but it just goes bye bye. I shall report a bug!

---

### Post by DogMatix on 2012-03-06
I've been using Lubuntu 12.04 for a few weeks and its sweet as a nut. The only issue I have had is 'Hotot' (twitter client) won't work.

**Bug: **[https://bugs.launchpad.net/ubuntu/+source/hotot/+bug/941000](https://bugs.launchpad.net/ubuntu/+source/hotot/+bug/941000)

---

### Post by pinguinhood on 2012-03-07
That's a good news! Nice to see a so-stable beta1 release!

---

