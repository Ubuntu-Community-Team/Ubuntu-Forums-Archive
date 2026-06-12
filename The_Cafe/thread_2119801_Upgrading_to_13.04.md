---
title: "Upgrading to 13.04"
date: 2013-02-24
forum: The Cafe
---

### Post by anaconda on 2013-02-24
I was bored, and that is why I just started the upgrade from xubuntu 12.10 to 13.04 on my MAIN MACHINE !! Oops..

probably a bad idea. 

Hope my machine still boots after the upgrade is finished.

Anyone else upgraded their main machine to "Raring Ringtail" without thinking too much?

---

### Post by CharlesA on 2013-02-25
Whoops. How did you upgrade?

I accidentally upgraded a test box "partially" to precise from lucid.

I'm not even sure what happened cuz I had Unity installed, but 2.6.x kernels and I couldn't install anything. At least it was a machine was not much on it.

---

### Post by matt_symes on 2013-02-25
I ran the dev versions for a year on my main laptop and it still worked so you may be lucky.

Either way, part of the fun can be fixing issues.

---

### Post by fdrake on 2013-02-25
> **CharlesA said:**
> Whoops. How did you upgrade?

I accidentally upgraded a test box "partially" to precise from lucid.

I'm not even sure what happened cuz I had Unity installed, but 2.6.x kernels and I couldn't install anything. At least it was a machine was not much on it.

same thing happened to me a month ago from precise to Raring Ringtai with a partial upgrade. Uhmmm weird.  The system looks like it's working fine. 

I was hoping that the annoing password keyloger would get fixed with the upgrade but this is not the case.

Anyway everything is working for me,  nothing new ; note: I am not using unity, since I uninstalled it right the way when precise come out and installed back gnome classic, so i can't confirm on that issue.

---

### Post by grahammechanical on 2013-02-25
I always use a development version as my working OS. I have been using Raring since development switched from 12.10 to 13.04. But I also always have a standby OS (12.04 connected to a /home partition with my files on) just in case.

And that just in case happened during the Quantal development cycle when a combination of kernel, XServer, and Nvidia driver made the OS inaccessible for a couple of weeks.

Always test a new version of Ubuntu (let alone a development version) in a spare 10-15Gb partition before upgrading the Ubuntu that is working fine. That is my advice.

Oh, by the way, it is standard practice for those of us on Ubuntu+1 section to never accept a partial upgrade. It removes stuff from a development version that does not yet have a replacement.

[https://wiki.ubuntu.com/U%2B1/partial_upgrade]("https://wiki.ubuntu.com/U%2B1/partial_upgrade")

Regards.

---

### Post by pqwoerituytrueiwoq on 2013-02-25
as long as you are using any [lightdm scripts](https://bugs.launchpad.net/lightdm/+bug/1128474) it will probably boot just fine, maybe a bit slow to boot
i have had my mom using xubuntu 13.04 on my old laptop for a week now and it works fine
but that was a clean install

---

### Post by anaconda on 2013-02-25
> **CharlesA said:**
> Whoops. How did you upgrade?

I accidentally upgraded a test box "partially" to precise from lucid.

I'm not even sure what happened cuz I had Unity installed, but 2.6.x kernels and I couldn't install anything. At least it was a machine was not much on it.

I updated using these commands.
```
sudo sed -i 's/quantal/raring/g' /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade

```
And I do know that there are still some 12.10 -repositories in the /etc/apt/sources.list.d/  -folder (some of which don't have new versions yet.)

Strange that you have such an ancient kernel. I now have 3.8.0-7 

Yep. Wasn't too smart to upgrade. Upgrade broke grub, so the machine didn't boot after it... :C
Just got the text: 
> error: file not found.
grub rescue>
Went to sleep after that, and re-installed grub today. After that it booted with one error message.

Now almost everything seems to be working well. With some exceptions eg. totem doesn't work. Luckily I have installed parole and vlc, which both work well.

---

### Post by anaconda on 2013-02-25
> **grahammechanical said:**
> I always use a development version as my working OS. I have been using Raring since development switched from 12.10 to 13.04. But I also always have a standby OS (12.04 connected to a /home partition with my files on) just in case.
Wow. That is brave. You must encounter some problems frequently. Atleast in the beginning of each new "cycle"

> Always test a new version of Ubuntu (let alone a development version) in a spare 10-15Gb partition before upgrading the Ubuntu that is working fine. That is my advice.

Oh, by the way, it is standard practice for those of us on Ubuntu+1 section to never accept a partial upgrade.

Thanks for the advice. 
Actually I have previously tried versions of ubuntu+1 on either Virtualbox or my older laptop first. Before even thinking of installing it on my main machine.

---

### Post by mastablasta on 2013-02-26
> **anaconda said:**
> Wow. That is brave. 
 
no that is the way to test the OS propperly. to use it's test version for real.

---

### Post by coutts99 on 2013-02-26
> **anaconda said:**
> I updated using these commands.
```
sudo sed -i 's/quantal/raring/g' /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade

```


I think ```
do-release-upgrade -d
``` is safer

---

### Post by CharlesA on 2013-02-26
> **coutts99 said:**
> I think ```
do-release-upgrade -d
``` is safer

Yep. That is also the official way to move between releases, at least from from a terminal. ;)

---

