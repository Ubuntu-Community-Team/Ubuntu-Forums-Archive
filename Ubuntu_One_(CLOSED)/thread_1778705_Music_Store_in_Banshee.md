---
title: "Music Store in Banshee"
date: 2011-06-09
forum: Ubuntu One (CLOSED)
---

### Post by SallyK on 2011-06-09
I've just upgraded to the latest version of Banshee and as part of the process, it removed the Ubuntu One Music Store plugin.

I read up on the process, and it said that the plugin would be removed, because the Music Store would now be part of the base install. Unfortunately, I can't find it anywhere.

Am I just being blind, or is there something genuinely wrong with my install - where should it be?

Thank you very much to anyone who can help.

---

### Post by coffeecat on 2011-06-09
I'm not sure I can help, but let's get a few details. Which version of Banshee have you upgraded to and which version of Ubuntu are you using? And was the upgrade part of a distribution upgrade of Ubuntu?

All I can say is that with a fresh install of Natty/11.04, Ubuntu One Music store is integrated out of the box. However, there is a part of the configuration where you can enable/disable the Ubuntu One plugin. In the Banshee menu, have a look in Edit > Preferences > Extensions tab and then under "Online Sources", do you have an entry for Ubuntu One Music Store and is it ticked?

Also, in my Natty installation, there is a package installed (it must have been default - I didn't install it) called banshee-extension-ubuntuonemusicstore. The package description in Synaptic says:

> <snip>

This package contains Banshee's support for the Ubuntu One Music StoreThis seems to be essential, at least in Natty, but if you are running an earlier Ubuntu version, I don't know.

---

### Post by SallyK on 2011-06-09
Thank you very much for trying to help.

I'm actually running Bodhi Linux, which is based on 10.04, as the LTS version, and the version of Banshee that it originally came with was 1.6. I was able to install the ubuntuone-extension from Synaptic, and it worked absolutely fine.

Today I upgraded to the latest versions, which included Banshee 2.0, and it removed the ubuntuone-extension as part of the upgrade. I looked all over the new version and couldn't find any reference to Ubuntu One.

Doing some googling, I found article like this one [http://www.ghacks.net/2011/04/11/banshee-2-0-major-update-major-improvement/](http://www.ghacks.net/2011/04/11/banshee-2-0-major-update-major-improvement/) which mention that the extension will be removed but that it should still be there in the core.

As it seemed to be an Ubuntu One problem, rather than a Bodhi one, I thought it better to ask here, as I hoped someone else might have upgraded and know where it was supposed to be.

Ubuntu One used to appear in the Extensions tab, as it does in yours, but after the upgrade it's no longer there.

---

### Post by coffeecat on 2011-06-09
That link is interesting, but the version of Banshee in Natty is also 2.0 and seems to have Ubuntu One as an extension, rather than as the "core", going by the presence of the extension package in my system. Seeing as that link is neither a Banshee team nor Ubuntu one, it could be just a simple error or misunderstanding on their part.

Is banshee-extension-ubuntuonemusicstore listed in Synaptic now that you have the ppa repository enabled? It might be worth installing it and seeing if it helps.

---

### Post by SallyK on 2011-06-09
After adding the PPA, the extension did update to version 1.9, which will install, unlike 1.6. 

On the other hand, it still doesn't appear in the preferences list of extensions, so you can't actually enable it.

Is there any chance you could look in Synaptic on your system, and see what version number your extension is?

Thank you very much for trying to help. It's not the end of the world if it won't work - the extension for Rhythmbox seems to be absolutely fine, but I just thought that as Banshee was the new default, it was worth seeing how I got on with it.

---

### Post by coffeecat on 2011-06-09
No problem. :)

The package banshee-extension-ubuntuonemusicstore is version 2.0.0-2ubuntu1 in Natty, which is interesting. Fwiw the Natty version of the actual banshee package is 2.0.0-2ubuntu1.

I don't know whether this will work, but here is the download link for the 2.0.0-2ubuntu1 version of the extension:

[http://packages.ubuntu.com/natty/banshee-extension-ubuntuonemusicstore](http://packages.ubuntu.com/natty/banshee-extension-ubuntuonemusicstore)

It might be worth downloading the amd64 or i386 package, whichever is appropriate to your system, and installing it manually. It shouldn't do any damage and if it doesn't work, it is easy enough to uninstall.

It's a pity if you can't get Ubuntu One to work in Banshee. It's nicely integrated, apart from the appalling search facility, and I've used it to purchase albums from the Music Store. That is, when I can actually find them in Banshee. Unfortunately, as someone who buys mostly classical music, I find the search in Banshee worse than hopeless. See this forlornly unanswered thread:

[http://ubuntuforums.org/showthread.php?t=1760658](http://ubuntuforums.org/showthread.php?t=1760658)

As you can see from my post to the Launchpad bug, I'm reduced to searching on the 7digital website.

---

### Post by SallyK on 2011-06-11
Thank you very much for the link, that was a good idea.

Unfortunately there's another dependency, and I'm reluctant to start upgrading things randomly just to get one function to work- I can see that causing all sorts of problems.

I'll just go on using Rhythmbox for the time being, where the extension is still working fine.

Thank you again for trying to help.

---

### Post by nmyrick on 2012-10-18
I have the same issue.  Im running 10.04 with Banshee 2.0.  Here are the dependency issues I am running into when trying to install this.  Is there anyone who can help me with how to upgrade this dependancy? I currently have an older version installed.

---

