---
title: "boot time cut in half by removing snap"
date: 2018-05-08
forum: Ubuntu, Linux and OS Chat
---

### Post by monkeybrain20122 on 2018-05-08
I noticed that my machine with a clean 18.04 install did not boot up as snappily as 16.04 (was slightly <10s now about 20s) Running systemd-analyze blame shows that much time was spent on mounting a bunch of snap packages.

In 18.10 some snap packages such as gnome-calculator,  gnome-system-monitor are installed by default and there is also  something called gnome-3.26 -2018 something something (which I have no  idea what it is, except a search on the intetnet  says this lets you  install e.g gnome-recipe, for cooking??? )Moreover, calculator and system monitor are also installed as .debs by default, so why the duplicate?

After removing all the snap packages and uninstalling snapd now boot time is almost down by half to what it was before.

Here there are only a few packages, some snap dev was trying to push for snap as "first class citizen" for all the apps. It will probably take an hr to boot if the whole system is snap.

Other than slow to start it has other issues, so I think it is a bad idea to push these in the software center. Mostly new users use the software center (more experienced users either use command line or synaptic) and it is not good if the first impression is that Ubuntu provides broken software. I think snap should only be offered in the software center if there is no .deb alternative.

Thoughts?

---

### Post by thenailedone on 2018-05-08
By not rebooting at all I have been able to remove boot time completely (YMMV).

---

### Post by kerry_s on 2018-05-08
> **thenailedone said:**
> By not rebooting at all I have been able to remove boot time completely (YMMV).

lol +1 what he said. i use suspend.

---

### Post by poorguy on 2018-05-10
> **monkeybrain20122 said:**
> 
 so I think it is a bad idea to push these in the software center. Mostly new users use the software center (more experienced users either use command line or synaptic) and it is not good if the first impression is that Ubuntu provides broken software. I think snap should only be offered in the software center if there is no .deb alternative.

Thoughts?

Is everything in the software center a snap.

If not then how does a user determine the difference between a snap and regular software apps / programs.

I look through the ***Software Center ***and see what is available and then use ***Synaptic Package Manager*** to install them.

---

### Post by kerry_s on 2018-05-10
i think they should just separate all the snaps in to it's own section, like with addons, utility, etc.... just have a snap packages section.

---

### Post by monkeybrain20122 on 2018-05-11
> **poorguy said:**
> Is everything in the software center a snap.

No, but if there is a snap version it will be the one in USC (e.g apt install and synaptic gets you the .deb version of vlc, USC has the snap)

---

### Post by poorguy on 2018-05-11
I was just looking through the ***Software Center ***and I saw nothing marked showing which are ***Snaps*** and which are actual ***deb files***.

At least they should identify which is which and allow the user to make the decision which to use.

---

### Post by howefield on 2018-05-11
> **poorguy said:**
> I was just looking through the ***Software Center ***and I saw nothing marked showing which are ***Snaps*** and which are actual ***deb files***.

At least they should identify which is which and allow the user to make the decision which to use.

Scroll down to the details of the package and check out the source. Snap packages will be in the Snap Store. Regular deb packages will have the repository identified.

---

### Post by poorguy on 2018-05-11
> **howefield said:**
> Scroll down to the details of the package and check out the source. Snap packages will be in the Snap Store. Regular deb packages will have the repository identified.
Hey howefield,

Thanks. :)

That's some good to know information.

I'm always learning something new about Ubuntu on the Ubuntu Forums. :)


Thanks.

---

### Post by SeijiSensei on 2018-05-11
How about an option during installation to say, "I don't want any snap packages."  I'm perfectly happy with the apt/deb method and have no interest in switching.

I notice that my Kubuntu 18.04 installation runs snapd, but I don't think there are any actual snap packages running.  I'm going to disable snapd and see if it matters.

---

### Post by Qassis on 2018-05-17
> **monkeybrain20122 said:**
> ......After removing all the snap packages and uninstalling snapd now boot time is almost down by half to what it was before.......
Thoughts?
Is very tempting but I use canonical-livepatch (source snap store).  I don't see it on Synaptic Package Manager (Ubuntu 18.04 LTS).
I think I'm stuck w/ snap....

---

