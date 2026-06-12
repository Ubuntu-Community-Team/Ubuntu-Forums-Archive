---
title: "Selective backports?"
date: 2005-05-21
forum: Ubuntu Backports
---

### Post by theantix on 2005-05-21
I'm interested in using certain parts of the Ubuntu Hoary Backports, but I don't want to upgrade everything.  Is there any way to selectively pick and choose which backported projects I could install but leave everything else alone?  Ideally I'd like to give priority to the entire official hoary tree but then pick a single project and choose that to upgrade to the backported version, along with the dependencies.  Is this possible, or just a pipe dream on my part?

---

### Post by Bob D. on 2005-05-21
Sure, very easy to do.

Using Synaptic, just search for the item you want and install it. All the dependencies will be resolved.

For example, I activated the Backports repos and wanted to upgrade just Gaim. No problem, with the Backport repos active I just searched for Gaim in Synaptic and it showed me there was a newer version. I selected it for installation and installed it. After that was done, I deactivated the Backports repos again (this is easy to do in Synaptic by just checking and unchecking repos).

Using the Ubuntu Update Manager, Launch the app, it will find all the upgradeable items, just uncheck the ones you do not want to install.

I think using Synaptic is easier, but either way works. All of this assumes you have first added the Backports repos to your repo list (sources.list).

Bob

---

### Post by JDay on 2005-05-21
Using synaptic, you can set a preference to hoary and then use package>force verson to install the ones you want. You'll have to keep an eye out for new backports and updates, though, since synaptic won't tell you about them. Or you could just deactivate the repos when you're not using them.

---

### Post by techn9ne on 2005-05-22
Or ...

| deb [http://www.backports.org/debian](http://www.backports.org/debian) stable package
from..
[http://www.backports.org/installation.html](http://www.backports.org/installation.html)

Obviously have to change the information to use ubuntu not debian backports.

---

### Post by techn9ne on 2005-05-22
Just using synaptic and enabling / disabling backports will work but if it won't help you w/ security and other important updates.

---

### Post by tread on 2005-05-22
[apt-pinning](http://jaqque.sbih.org/kplug/apt-pinning.html)

---

