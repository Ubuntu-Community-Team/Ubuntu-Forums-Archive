---
title: "Howto create local repository using apt-mirror and create DVD/CD images using aptoncd"
date: 2008-07-18
forum: Server Platforms
---

### Post by framallo on 2008-07-18
I wanted to mirror all Ubuntu 8.04 Hardy LTS (main and universal) and burn it to DVDs. In my scenario I decided to mirror 8.04 because is a LTS version. If i have a new version every 6 months the DVDs would be obsolete very quickly.

I've found this some days ago:
[http://www.howtoforge.com/local_debian_ubuntu_mirror]("http://www.howtoforge.com/local_debian_ubuntu_mirror") 
and started to download with apt-mirror ubuntu repositories while i was trying to figure out how to split it in DVDs.

And then i bumped with [http://www.howtoforge.com/dvd_images_of_ubuntu_repositories]("http://www.howtoforge.com/dvd_images_of_ubuntu_repositories")
that says how to create dvds using debmirror. 

That's ok if you want to have one thread downloading. I was interested in apt-mirror because it allows me to download using up to 20 downloads like DownThemAll and so many multi-thread-downloaders.
Another benefit of using apt-mirror is that /etc/apt/mirror.list is very similar to /etc/apt/sources.list so you can just copy a few lines and It's working.
Also apt-mirror has a cron task to update the mirror daily. 

Let's run as root
```
sudo -s 
```

now we can install apt-mirror
```
 apt-get install apt-mirror
```

Then add to /etc/apt/mirror.list your repositories URL. I added:

```
 deb http://ar.archive.ubuntu.com/ubuntu hardy main restricted universe multiverse [CODE]

then create the local repositories

[CODE]su - apt-mirror -c apt-mirror
```

This download takes long time and spends lots of hard disk. Mine took it nearly 45GB including main,universe and multiverse.

Now we need to put all debs to one folder. 

```

cd /var/spool/apt-mirror 
find mirror/ -iname *.deb -print | xargs ln -t aptoncd/ 

```
Using ln instead of mv can keep your repositories updated and you can publish them with apache.

Now you need to run aptoncd
```
aptoncd -p /var/spool/apt-mirror/aptoncd/
```
you shouldn't use aptoncd cache folder, because i couldn't run
```
rm *.deb
```
seems to be we have too many deb files.
Instead i deleted the entire folder
```
rm -r /var/spool/apt-mirror/aptoncd 
```

enjoy!

---

