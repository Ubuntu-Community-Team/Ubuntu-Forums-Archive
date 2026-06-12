---
title: "seeking advice on local ubuntu update server"
date: 2008-07-12
forum: Server Platforms
---

### Post by wilbbe01 on 2008-07-12
Hello all,

Introduction:
    I am seeking advice on how people would recommend updating labs of machines from a local server.  I've found a few links and not sure which route to go, or if either of them would accomplish what I want.

What I want to accomplish:
    Create a local update server so as to prevent multiple ubuntu labs from using external bandwidth causing way too many downloads of the same file to our local network.  It is also desirable to have no user intervention.  I want to be able to set it up, and other than crashes and such never have to touch the lab to update, or the server to retrieve new updates for the labs.

Ideas I have:
    I have found a few resources which appear to be of some interest.  I saw one how-to article on setting up a local repository using apt-mirror.  The article said he was not going to show how to do security updates because he felt they should be downloaded from the internet to get the latest updates.  I also found a post on this forum [https://wiki.ubuntu.com/UpdateServer](https://wiki.ubuntu.com/UpdateServer) which appears like it is similar to what WSUS is for windows.  My experience with the WSUS on windows was not very good, do to reliability issues.

What I feel:
    To me I feel a local mirror of all security updates makes sense, but I still feel a little unsure on how up to date the local update mirror would be.  Also, the storage size to mirror everything in a repository seems a little large.

Does anyone have experience in setting up a local update server which automatically retrieves new updates, with labs automatically updating daily without needing to touch any of the machines?

Thanks in advance.

--
Ben

---

### Post by doogy2004 on 2008-07-12
that is exactly what I have done.  I used apt-mirror on a LAMP server.  be sure to have a large enough disk to download the updates.  see this thread for my trials and tribulations [http://ubuntuforums.org/showthread.php?t=826503](http://ubuntuforums.org/showthread.php?t=826503)

I then created a symlink from the www folder to the apt-mirror folder and changed the clients sources to something like: ```
deb http://192.168.1.10/apt-mirror/mirror/archive.ubuntu.com/ubuntu/ hardy main restricted
```

I then created a cron job to update and upgrade the clients daily: ```
apt-get update && apt-get upgrade
```

---

### Post by wilbbe01 on 2008-07-12
Thanks doogy,

Through the link you gave me I came to one of the walk throughs of setting such a thing up.  After reading the first paragraph I saw the words apt-proxy.  After reading about it (on it's not very professional website) it looks like a lot better solution than apt-mirror, as we don't have every package installed, so why cache all of them?

After chatting with the server admin a few minutes ago he also was curious about rsync.  It sounds easy enough.  His idea is that you have one machine in the lab which is set to update.  Once you are sure everything still functions on that machine you would then use rsync to push out to all other machinses.  Does that make sense as a solution?  Is that possible?  Is that too much work for the solution I want to come to?

---

### Post by doogy2004 on 2008-07-13
As always their is more than one way to accomplish any task, I just prefered apt-mirror so that I didn't have to change the clients very much.  I'm not sure how it would work with rsync as I'm not familiar with it.

On a side note, my mirror size is 52G.  That will only download the first time, each time after that it simply downloads the packages that it needs to keep up to date.

---

### Post by wilbbe01 on 2008-07-13
Thanks, for all your help I'll be looking in to everything a bit more before I decide for sure, maybe I will end up going with apt-mirror after all.

---

### Post by Wharf Rat on 2008-07-13
There is also Apt-catcher.  

[http://ubuntuforums.org/showthread.php?t=564301](http://ubuntuforums.org/showthread.php?t=564301)

---

### Post by wilbbe01 on 2008-07-13
Thank you as well WR, I looked at apt-catcher some as well, and to me it looked like the worst of them all.  Have you used it yourself?  Do you like it?

---

