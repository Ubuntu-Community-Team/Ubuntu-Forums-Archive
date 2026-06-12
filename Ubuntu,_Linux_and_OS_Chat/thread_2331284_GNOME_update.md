---
title: "GNOME update"
date: 2016-07-20
forum: Ubuntu, Linux and OS Chat
---

### Post by windowsfree on 2016-07-20
Does anyone know if UbuntuGnome will update to Gnome 3.20 soon ?

Thank you.

---

### Post by vanadium on 2016-07-20
With the release of Ubuntu Gnome 16.10 in October forthcoming.

---

### Post by windowsfree on 2016-07-20
Will I be able to upgrade my 16.04 install at that time ?

---

### Post by uNoubu8a on 2016-07-20
Firstly - If you break your install you get to keep both pieces.

Have a gander at - [http://www.webupd8.org/2016/04/how-to-install-gnome-320-in-ubuntu.html](http://www.webupd8.org/2016/04/how-to-install-gnome-320-in-ubuntu.html) which is an article from April.  It is possible that the situation with installing Gnome 3.20 has improved (and off course it might have become much worse).

The tldnr:

edit: you also need to add the main gnome3 ppa (which I had originally missed, thanks [**[COLOR=#000000]kansasnoob[/COLOR]**]("https://ubuntuforums.org/member.php?u=554595")):
```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo add-apt-repository ppa:gnome3-team/gnome3-staging
sudo apt update
sudo apt dist-upgrade
```

*Note that after running the above your warranty is now void.

Remember to upgrade responsibly :KS

---

### Post by QDR06VV9 on 2016-07-20
Just Adding this for those who do not Visit the Page in the Link:
And if you have the need to revert the changes and go back to GNOME 3.18 in Ubuntu 16.04  you can purge the PPA. To purge the PPA, use the following commands:

```
sudo apt install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3-staging
```
Reboot to your Old Gnome Environment.. If You did not Break your system too badly.

---

### Post by kansasnoob on 2016-07-21
> **work-work said:**
> Firstly - If you break your install you get to keep both pieces.

Have a gander at - [http://www.webupd8.org/2016/04/how-to-install-gnome-320-in-ubuntu.html](http://www.webupd8.org/2016/04/how-to-install-gnome-320-in-ubuntu.html) which is an article from April.  It is possible that the situation with installing Gnome 3.20 has improved (and off course it might have become much worse).

The tldnr:

```
sudo add-apt-repository ppa:gnome3-team/gnome3-staging
sudo apt update
sudo apt dist-upgrade
```

*Note that after running the above your warranty is now void.

Remember to upgrade responsibly :KS

It's imperative to also use the gnome3 ppa with the gnome3 staging ppa. Read:

[https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging](https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging)

> This PPA will be used to test uploads before they are uploaded to the main archive for the coming Release.

=== *WARNING* ===
The packages here have been deemed not ready for general use, they have known bugs and/or regressions, sometimes of a critical nature. Mostly things should run smoothly but be prepared to use ppa-purge, when you encounter issues!

If they break your system, you get to keep both halves.

=== Installing ===
**To use this PPA, you should enable the main GNOME3 PPA.**

- You need to run 'sudo apt-get dist-upgrade' to avoid problems. Please read the output before entering 'Y' to make sure important packages won't be removed.

=== Removing ===
Use ppa-purge to remove this PPA. It is *particularly* important to do this before upgrading to a new release!

ppa-purge gnome3-team/gnome3-staging
ppa-purge gnome3-team/gnome3

=== Bugs ===
Please use 'ubuntu-bug' to report bugs against packages in this PPA

So you need both of these:

[https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3](https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3)

[https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging](https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging)

That will get Xenial to GNOME 3.20.

---

### Post by kansasnoob on 2016-07-21
> **windowsfree said:**
> Will I be able to upgrade my 16.04 install at that time ?

The interim releases like 16.10 will only be supported for 9 months whereas the LTS releases are supported for 3 years. But if you always want the latest then you could always run the interim releases with both the gnome3 ppa and the gnome3 staging ppa. But I'd count on having to reinstall every 6 months because the likelihood of surviving release upgrades is low.

---

### Post by alvintimothyjr on 2016-07-27
I've been running this for two days on the 4.7rc kernel.  Not  bad.

> **work-work said:**
> Firstly - If you break your install you get to keep both pieces.

Have a gander at - [http://www.webupd8.org/2016/04/how-to-install-gnome-320-in-ubuntu.html](http://www.webupd8.org/2016/04/how-to-install-gnome-320-in-ubuntu.html) which is an article from April.  It is possible that the situation with installing Gnome 3.20 has improved (and off course it might have become much worse).

The tldnr:

```
sudo add-apt-repository ppa:gnome3-team/gnome3-staging
sudo apt update
sudo apt dist-upgrade
```

*Note that after running the above your warranty is now void.

Remember to upgrade responsibly :KS

---

### Post by uNoubu8a on 2016-07-27
> **kansasnoob said:**
> It's imperative to also use the gnome3 ppa with the gnome3 staging ppa. Read:

[https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging](https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging)



So you need both of these:

[https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3](https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3)

[https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging](https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging)

That will get Xenial to GNOME 3.20.

Good catch! I hadn't noticed that :? (will have to edit my initial post!!)

---

