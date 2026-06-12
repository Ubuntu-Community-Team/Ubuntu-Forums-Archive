---
title: "Security running wine apps"
date: 2010-09-04
forum: Security
---

### Post by Garthhh on 2010-09-04
I use both picasa & Google Earth, which were installed through the software center.

I'm having a similar discussion on a different forum
[http://linux.ittoolbox.com/groups/technical-functional/linuxadmin-l/wine-security-3724440#M3738598](http://linux.ittoolbox.com/groups/technical-functional/linuxadmin-l/wine-security-3724440#M3738598)


I don't understand the instructions given for determining whether or not these apps present a security problem?

Can any one provide a step by step [noob] for how to determine whether or not picasa runs as root?

I also found this
[http://groups.google.com/group/google-labs-picasa-for-linux/search?group=google-labs-picasa-for-linux&q=security&qt_g=Search+this+group](http://groups.google.com/group/google-labs-picasa-for-linux/search?group=google-labs-picasa-for-linux&q=security&qt_g=Search+this+group)

from what I can decifer from the 1st post, I've already limited my exposure, by setting picasa to only access one folder for files.

---

### Post by an0dos on 2010-09-04
> **Garthhh said:**
> I use both picasa & Google Earth, which were installed through the software center.

I'm having a similar discussion on a different forum
[http://linux.ittoolbox.com/groups/technical-functional/linuxadmin-l/wine-security-3724440#M3738598](http://linux.ittoolbox.com/groups/technical-functional/linuxadmin-l/wine-security-3724440#M3738598)


I don't understand the instructions given for determining whether or not these apps present a security problem?

Can any one provide a step by step [noob] for how to determine whether or not picasa runs as root?

I also found this
[http://groups.google.com/group/google-labs-picasa-for-linux/search?group=google-labs-picasa-for-linux&q=security&qt_g=Search+this+group](http://groups.google.com/group/google-labs-picasa-for-linux/search?group=google-labs-picasa-for-linux&q=security&qt_g=Search+this+group)

from what I can decifer from the 1st post, I've already limited my exposure, by setting picasa to only access one folder for files.

I don't think you should worry about picasa or google earth. You can figure out whether picasa is running as root by typing the following command in the terminal while picasa is running

```
ps aux | grep picasa
```

On the left of the screen you will see who is running it. The main issue with wine is that you don't want to install programs while running as root. This means running something like
```
wine setup.exe
```
instead of running
```
sudo wine setup.exe
```

You should look at the tips under the security sticky in the security forum.
Since you installed the programs via the software center, you don't need to worry about whether you installed it as root.

---

### Post by Garthhh on 2010-09-04
> **an0dos said:**
> I don't think you should worry about picasa or google earth. You can figure out whether picasa is running as root by typing the following command in the terminal while picasa is running

```
ps aux | grep picasa
```

On the left of the screen you will see who is running it. The main issue with wine is that you don't want to install programs while running as root. This means running something like
```
wine setup.exe
```
instead of running
```
sudo wine setup.exe
```

You should look at the tips under the security sticky in the security forum.
Since you installed the programs via the software center, you don't need to worry about whether you installed it as root.

Thanks for your reply, 
I wanted some more understanding
I had trouble believing that I could install an app from the repository, that would leave a gaping security hole[-X
the toolbox forum is more oriented towards system admin guys who have a different perspective [the sky is falling, run save yourself]

---

### Post by OpSecShellshock on 2010-09-04
Almost anything that you can install could, under some circumstances, present a security risk. Well, not the application itself, but the way it's used, to be more precise. If you don't elevate privileges prior to running the command it should be fine.

Part of the problem (and possibly the reason for the panic you were seeing on the other forum) is that if something that some users expect to work instantly doesn't end up working instantly, *and* they think/discover that it has something to do with default access control settings, they may just elevate privileges rather than change configurations. If that ends up working, they may just start doing it all the time as a habit. For obvious reasons, that could be trouble.

---

### Post by Garthhh on 2010-09-04
> **OpSecShellshock said:**
> Almost anything that you can install could, under some circumstances, present a security risk. Well, not the application itself, but the way it's used, to be more precise. If you don't elevate privileges prior to running the command it should be fine.

Part of the problem (and possibly the reason for the panic you were seeing on the other forum) is that if something that some users expect to work instantly doesn't end up working instantly, *and* they think/discover that it has something to do with default access control settings, they may just elevate privileges rather than change configurations. If that ends up working, they may just start doing it all the time as a habit. For obvious reasons, that could be trouble.

The following are just some observations, opinion [your mileage may vary]

There is the resentment, that comes to the surface, against companies that don't offer linux compatible versions of their products.

As users become more experienced they can become terminalcentric & practically forget about software center

I seem to occasionally am able to remind the sys admins of the existence of some of the wonderful GUI's people in the open source community have built;)

---

### Post by OpSecShellshock on 2010-09-04
You're certainly right about the resentment, but as long as it remains pointed at those software developers and not at Linux, I can't really take issue with it. Personally, rather than give myself over to resentment (at least over that specific thing), I simply decline to use their stuff.

---

### Post by Garthhh on 2010-09-04
> **OpSecShellshock said:**
> You're certainly right about the resentment, but as long as it remains pointed at those software developers and not at Linux, I can't really take issue with it. Personally, rather than give myself over to resentment (at least over that specific thing), I simply decline to use their stuff.

I understand the resentment, it goes with the territory
the coming of more mobile devices, should make this continuing discussion very interesting over the next few years.  Cloud applications can also present unique security challenges.  The line between operating system & browser will continue to blur.

---

