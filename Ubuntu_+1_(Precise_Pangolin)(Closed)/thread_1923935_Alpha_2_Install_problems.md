---
title: "Alpha 2 Install problems"
date: 2012-02-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ernestj on 2012-02-11
I am have installed Alpha 2 and am running into an issue. I believe it is compiz crashing, after this happens I am left with a wallpaper only. I tried to do a partial upgrade and it said that it could not because it could not identify what desktop I am running, ie. Ubuntu, Kubuntu, etc. 

The install that I did was only 750+- mb. I have read that the file is actually 1.6 gigs. Did I install the wrong Alpha 2?

I can access the desktop only after I boot in safemode.
Thanks,
Ernie

---

### Post by grahammechanical on 2012-02-11
How do you know that it is Compiz that has crashed. Did you not get some message informing you that something or other has closed unexpectedly? That is what usually happens when something breaks while testing an alpha release.

You also get an opportunity to report the problem. If you accept that opportunity a utility will generate a report that can be attached to your bug report in Launchpad.

In some cases it will tell you that the problem cannot be reported because it is caused by obsolete libraries. Then we can do two things. We can open the Synaptic Package Manager and search for those libraries. They usually have a grey icon next to them. We can then mark them for upgrade with a right click and when we click "Apply" the libraries are upgraded and the problem should be fixed.

The second thing that we can do is wait until our routine of doing daily updates actually updates the obsolete libraries. This is exactly what I am waiting to happen so that I can re-install the Ubuntu Software Centre.

In other cases the utility will tell you that it has already been reported and you can read about it to see if you have the same problem. If you accept this action a web browser will open at the Launchpad page where the bug was reported.

Otherwise, you get the opportunity to be the first to report that particular bug.

You need to give a lot more information if you want advice on what is going wrong. You do not even say if this happens before or after you log in. It does make a difference, you know. Have you tried going into Ubuntu 2D at the log in screen?

Regards.

---

### Post by ernestj on 2012-02-11
I think it is obsolete libraries.

It said that I needed to install a list of things, but I did not write them down.

One of them is Unity.

Then it said that is can not find the desktop that I am running. It said that I need to get the Ubuntu-Desktop. I do not know how to do that. 

It said that I can use synaptic or sudo. 

Any ideas?

I am running Unity 2D right now and is working fine.

Thanks,
ernie

---

### Post by Gregory Lee on 2012-02-11
> **ernestj said:**
> 
Any ideas?

If the messages you mention come from the update manager, my suspicion is that you shouldn't using it.  There is a sticky thread above this thread about "partial updates".

I'm running Alpha 2, and on my computer it seems to run nicely.

---

### Post by cariboo on 2012-02-11
Synaptic isn't installed by default, so you'll have to install it manually using the following command:

```
sudo apt-get install synaptic
```

The problem at the moment is that synaptic is fairly broken, at the moment, so you may not be able to use it, for me it crashes while updating the repositories.

The method I use when things get to this point, is to use aptitude, which also isn't installed by default. To install it use the following command:

```
sudo apt-get install aptitude
```

Once you have aptitude installed run the following two commands:

```
sudo aptitude update
```

then

```
sudo aptitude safe-upgrade
```

you can combine the two commands into one, this way:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

Of course these commands have to be run in a terminal.

The wonderful thing about running a development release, is that you learn a lot more than you would just running a regular release from day to day. If you stick with it, it will make you a much more knowledgeable user in the long run.

---

