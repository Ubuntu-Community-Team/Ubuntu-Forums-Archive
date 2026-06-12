---
title: "upgrading from Ubuntu 12.04 alpha 2 to 12.04 Beta 1?"
date: 2012-03-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by computerboy on 2012-03-07
Hi, a little while ago I decided to upgrade to Ubuntu 12.04 alpha 2 instead of staying with Ubuntu 11.10 until the official version of 12.04 came out.  But since Beta 1 has just come out I would like to upgrade to that.  The problem is that I don't know how.  I've tried pressing Alt+F2 and typing in "upgrade-manager -d" but it doesn't show that there is a new version available.



Anyone?

---

### Post by haqking on 2012-03-07
> **computerboy said:**
> Hi, a little while ago I decided to upgrade to Ubuntu 12.04 alpha 2 instead of staying with Ubuntu 11.10 until the official version of 12.04 came out.  But since Beta 1 has just come out I would like to upgrade to that.  The problem is that I don't know how.  I've tried pressing Alt+F2 and typing in "upgrade-manager -d" but it doesn't show that there is a new version available.



Anyone?

i dont use them but i imagine 

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by howefield on 2012-03-07
> **computerboy said:**
> Hi, a little while ago I decided to upgrade to Ubuntu 12.04 alpha 2 instead of staying with Ubuntu 11.10 until the official version of 12.04 came out.  But since Beta 1 has just come out I would like to upgrade to that.  The problem is that I don't know how.  I've tried pressing Alt+F2 and typing in "upgrade-manager -d" but it doesn't show that there is a new version available.

Thread moved to "*Ubuntu +1 (Precise Pangolin)*"

If you already upgraded to Alpha2, simply keeping updated will give you the current state of play.

All you have to do is what haqking said.

---

### Post by grahammechanical on 2012-03-07
I too wanted to make sure that my alpha 2 was now beta 1. So, I downloaded the beta iso and upgraded from that. Only one small package was transferred over.

I think that it is wise to have a fairly up to date live CD available anyway. Just in case we need to re-install.

Regards.

---

### Post by computerboy on 2012-03-07
> **howefield said:**
> Thread moved to "*Ubuntu +1 (Precise Pangolin)*"

If you already upgraded to Alpha2, simply keeping updated will give you the current state of play.

All you have to do is what haqking said.

How will I know that it works?

---

### Post by wojox on 2012-03-07
> **computerboy said:**
> How will I know that it works?

It will load your Desktop. :P

---

### Post by cariboo on 2012-03-07
> **computerboy said:**
> How will I know that it works?

Beta 1 was just a snapshot of Precise last Thursday. There is nothing to indicate that you are running the Beta. I'd suggest you update at least once a day, and you'll have the current version, all the way through to the final release.

---

### Post by howefield on 2012-03-07
> **computerboy said:**
> How will I know that it works?

Don't believe there is a way to tell that you have the Beta running as opposed to an Alpha, you are either running the development or stable branch.

```
lsb_release -a
```

Keep updating and a few days before official release day, the development branch tag will drop off and you will have the full release.

You can subscribe to the mailing lists which will inform you as and when packages are available.

[https://lists.ubuntu.com/mailman/listinfo/Precise-changes](https://lists.ubuntu.com/mailman/listinfo/Precise-changes)

---

### Post by screaminj3sus on 2012-03-07
Just update and you will have the "beta"

---

### Post by jerrylamos on 2012-03-07
On "unstable development code" I prefer to have another partition to install the new level in.  I still have the running one in case of trouble.  Besides install can surface some bugs.  Well, upgrade may expose bugs too.

If you update your -only- ubuntu you stand a chance of being stranded....

For whatever reason this Betal level install went O.K.  Oh, by the way, the current Beta installs generic-pae level kernels - which happen to run on this non-pae flag IBM Thinkpad.  Never know, might run, might not, this is development so I gave it a whirl.

Jerry

---

### Post by computerboy on 2012-03-07
The main problem for me is, after pressing Alt+F2 and typing in "upgrade-manager -d", it asked me if I wanted to install a partial upgrade.  I clicked OK, thinking it would make it Beta 1, but instead I don't see a difference and these weird error messages keep popping up that are really annoying me.  I really have no clue what's happening.  Thanks for all the help by the way.

---

### Post by 3rdalbum on 2012-03-08
I believe sometimes you need to click Check after running update-manager -d.

What you describe sounds like an ordinary partial update within 11.10. When you type update-manager -d and click Check, it should show a piece of text at the top of the window saying "New release 12.04LTS available" with an "Upgrade" button next to it. When you click that it shows you what steps it will take to upgrade, and there's no confusing that with an ordinary update within the same version.

---

