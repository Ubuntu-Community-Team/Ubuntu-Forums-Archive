---
title: "Why is Chromium Always out-of-date?"
date: 2011-12-02
forum: The Cafe
---

### Post by teejay17 on 2011-12-02
Why is Chromium in the repos always so out-of-date? For Oneiric, it is still at 14, and the stable is at 15—available since November 16th. Another couple of weeks and 16 will be out!

---

### Post by OrangeCrate on 2011-12-02
> **teejay17 said:**
> Why is Chromium in the repos always so out-of-date? For Oneiric, it is still at 14, and the stable is at 15—available since November 16th. Another couple of weeks and 16 will be out!

Though I not sure, I would suppose that this still has something to do with the frequency of updates:

> Recently, the person who was "maintaining" Chromium in Ubuntu also left the project. I plan on uploading Chromium 14 as soon as possible.

[http://askubuntu.com/questions/62472/why-doesnt-chromium-get-quicker-updates](http://askubuntu.com/questions/62472/why-doesnt-chromium-get-quicker-updates)

---

### Post by 3Miro on 2011-12-02
> **teejay17 said:**
> Why is Chromium in the repos always so out-of-date? For Oneiric, it is still at 14, and the stable is at 15—available since November 16th. Another couple of weeks and 16 will be out!

Because 11.10 came out before Nov 16. Once a version of Ubuntu is released, they don't add newer versions of any of the packages in the Software Center. The only change is if they have a bug-fix or security update.

Look for an unofficial ppa, they will have a newer version.

---

### Post by ninjaaron on 2011-12-02
> **3Miro said:**
> Because 11.10 came out before Nov 16. Once a version of Ubuntu is released, they don't add newer versions of any of the packages in the Software Center. The only change is if they have a bug-fix or security update.

Look for an unofficial ppa, they will have a newer version.

You can also get some newer packages if you enable backports, proposed updates, etc. in the 'software sources.'  It depends on how active the package maintainer is.  Mozilla controls their Ubunut packages in Univers directly, and there updates come very quickly.

---

### Post by teejay17 on 2011-12-02
> **3Miro said:**
> Because 11.10 came out before Nov 16. Once a version of Ubuntu is released, they don't add newer versions of any of the packages in the Software Center. The only change is if they have a bug-fix or security update.

Look for an unofficial ppa, they will have a newer version.
I see. Well I'm glad that Firefox is updated continually.

---

### Post by craig10x on 2011-12-02
If you grab the google chrome from their website, it will automatically add a ppa updater that will get you the latest stable version as soon as it is released...And Chrome is often ahead of Chromium on new stable releases :)

---

### Post by teejay17 on 2011-12-03
> **craig10x said:**
> If you grab the google chrome from their website, it will automatically add a ppa updater that will get you the latest stable version as soon as it is released...And Chrome is often ahead of Chromium on new stable releases :)

There's a bug in the software centre that's preventing me from opening/installing Chrome.

---

### Post by 3Miro on 2011-12-03
> **teejay17 said:**
> There's a bug in the software centre that's preventing me from opening/installing Chrome.

Try it from the terminal. Open a Terminal and cd into the folder with the Chrome .deb file (i.e. cd Downloads). Then the command is:

```
sudo dpkg -i <filename.deb>
```

Replace the <filename.deb> with the actual name of the package.

---

### Post by 3Miro on 2011-12-03
> **teejay17 said:**
> I see. Well I'm glad that Firefox is updated continually.

Not exactly, 10.04 still comes with Firefox 3.x by default. Only the latest version of Ubuntu is updated continuously, if you don't upgrade to 12.04 then FF will fall behind too.

---

### Post by teejay17 on 2011-12-03
Thanks everyone for all the answers. 
I'm not that interested in installing Chrome. 
If I have it correctly, to sum up the answer to my question: whatever version of Chromium is currently "new" when a particular version of Ubuntu is released, that's the one that remains for the duration of the distro's life-cycle.

---

### Post by craig10x on 2011-12-03
> **teejay17 said:**
> There's a bug in the software centre that's preventing me from opening/installing Chrome.

My software center works fine for installing deb files....but another way you can do it, is first install the: gdebi installer (you can get that in the software center)

Once that is installed, you should be able to right click on that deb package and select: "install with gdebi installer"...that would be an easy alternative to do it...

---

### Post by teejay17 on 2011-12-03
> **craig10x said:**
> My software center works fine for installing deb files....but another way you can do it, is first install the: gdebi installer (you can get that in the software center)

Once that is installed, you should be able to right click on that deb package and select: "install with gdebi installer"...that would be an easy alternative to do it...

Yes, that worked easiest. Gdebi is nice and simple.

---

### Post by teejay17 on 2011-12-06
> **3Miro said:**
> Try it from the terminal. Open a Terminal and cd into the folder with the Chrome .deb file (i.e. cd Downloads). Then the command is:

```
sudo dpkg -i <filename.deb>
```Replace the <filename.deb> with the actual name of the package.
This is actually the only thing that worked for one of my more obdurate machines. Thanks for the tip.

---

