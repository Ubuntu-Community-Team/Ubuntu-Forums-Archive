---
title: "Can't update LMMS"
date: 2009-05-12
forum: Ubuntu Studio
---

### Post by Sig Nuka on 2009-05-12
I'm trying to update lmms-common to 0.4.4~ppa~intrepid-5 but I keep getting this error:

"Error: Breaks exisiting package 'lmms' dependency lmms-common (= 0.4.3~ppa~intrepid-1)"

I don't want to lose my projects by uninstalling LMMS just so I can update it. So what do I do? :(

---

### Post by Stochastic on 2009-05-13
you should be executing these commands:```
sudo apt-get update
sudo apt-get upgrade
```

If you have the PPA in your source tree that will get you the latest version.  The error you're getting looks like you (or the little cows in your computer) are attempting to upgrade just lmms-common but not lmms.  The old lmms package is claiming foul, shouting that it needs exact version matches.

On a related note, if you save your projects can't you uninstall lmms without loosing them?

---

### Post by Sig Nuka on 2009-05-13
> **Stochastic said:**
> The error you're getting looks like you (or the little cows in your computer) are attempting to upgrade just lmms-common but not lmms.

I downloaded the .deb files like I always do when upgrading, and I always update lmms-common before lmms (otherwise it won't update). For some odd reason it's not letting me this time (it's worked before). :(

I never use the terminal for upgrades, so maybe that's why? I've never had to, but if it's the only way...

I always assumed you lose all your songs and custom things and stuff if you uninstall. I don't really know though.

---

### Post by Stochastic on 2009-05-13
apt has super cow powers.

it can do things you and I can't do.  It can also do things you would have taken much longer to do (like find and download and install new packages).

Essentially the problem you're running into is that lmms depends on an exact version of lmms-common.

If you never use the terminal for upgrades, then an apt-get upgrade may install a lot more than lmms updates on you so you may just want to get those exact packages.  Add the repository to your /etc/apt/sources.list (or go through the GUI for Software Sources).  Then do ```
sudo apt-get update
sudo apt-get install lmms lmms-common
```
This should just install the newer versions of those programs and leave off any other updates.  Also this method doesn't involve uninstalling lmms

You may also want to include the lmms-vst package in that list.

As for the "songs and custom things and stuff" I'm pretty sure your songs will stay put.  Custom settings in the software may disappear or you may find them still there upon reinstall, depending on your/the package's uninstall method or depending on the software's setting storage method.  Should you ever screw up some setting and find it's sticking around after reinstall, you should use sudo apt-get purge lmms lmms-common to clear any and all settings files - this still won't delete your songs.

---

### Post by Sig Nuka on 2009-05-13
I tried to add the repository but I got this:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 02FE5F12ADDE29B2

What do I do now? :(

Edit: [Apparently]("https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html") I need to add the key.

> Most software repositories use a GPG key to digitally sign the files they provide, which makes it easy to check that the files have not been tampered with since their creation. In order for apt to be able to check this, you need the public key that corresponds to the signatures. The key should be available for download on the repository's website.

I'm not seeing anything to download though (unless I'm not understanding *what* to download):

[https://launchpad.net/~tobydox/+archive/ppa](https://launchpad.net/~tobydox/+archive/ppa)

Ugh, this is giving me a headache. It was so much easier to update it last time. :cry:

Edit2: Never mind, [found out what to do]("https://help.launchpad.net/Packaging/PPA#Adding%20the%20keys%20using%20Gnome"). I'll update in a bit. :)

Edit3: Uh-oh. Now what?

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lmms is already the newest version.
lmms-common is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  lmms-vst: Depends: lmms-common (= 0.4.2-0ubuntu8) but 0.4.3~ppa~intrepid-1 is to be installed
E: Broken packages
```

---

### Post by Stochastic on 2009-05-15
Um, it looks like you've added the Jaunty section of the tobydox repository but there are no LMMS packages for Jaunty as they've been accepted into the universe repository.

Which version of Ubuntu are you running?
if it's intrepid, you shouldn't add a Jaunty repository.
if it's jaunty, you shouldn't install intrepid packages as this will surely break your system - eventually.

---

### Post by Sig Nuka on 2009-05-15
I'm running Jaunty, but I'm upgrading from an Intrepid package I installed back when I was running Intrepid.

I don't think there *is* a Jaunty version of LMMS, so does this mean I have to wait who knows how long for one to come out before I'm able to update it? :cry:

---

### Post by tobydox on 2009-05-15
Please install the Intrepid packages. I didn't package for Jaunty separately as there's no benefit over Intrepid-packages and Intrepid-packages should be fully forward-compatible thanks to Qt4. So what you basically should do is re-installing LMMS (assuming, you added Intrepid source to /etc/apt/sources.list):

dpkg --purge lmms lmms-common lmms-vst
apt-get update 
apt-get install lmms lmms-common lmms-vst

---

### Post by Sig Nuka on 2009-05-15
> **tobydox said:**
> So what you basically should do is re-installing LMMS (assuming, you added Intrepid source to /etc/apt/sources.list)

I added the Jaunty repositories, so should I remove those and add the Intrepid ones instead?

Also, I was hoping to avoid uninstalling LMMS. :(

---

### Post by tobydox on 2009-05-15
> **Sig Nuka said:**
> I added the Jaunty repositories, so should I remove those and add the Intrepid ones instead? Exactly.  > **Sig Nuka said:**
>  Also, I was hoping to avoid uninstalling LMMS. :(  What's the problem with complete re-installation? It doesn't touch anything in your home directory (i.e. project files or similiar). It's simply the easiest way, although an upgrade from Jaunty's official LMMS packages should have worked as well.

---

### Post by Sig Nuka on 2009-05-15
Ahaha, it's done! I've upgraded! :mrgreen:

So I replaced the Jaunty repositories with the Intrepid ones (as told). Afterwards I did what Stochastic *originally* told me to do (adding the vst package as well):

```
sudo apt-get update
sudo apt-get install lmms lmms-common lmms-vst
```

Upgrade went **smoothly**. No reinstall was even needed. :mrgreen:

So in the end, the big problems were that I downloaded the .debs like I usually do instead of upgrading from the repository, and that I added the *wrong* repository (Jaunty) instead of the correct one (Intrepid), even though I'm on Jaunty. Whew, it doesn't feel like only 2 days have passed. :D

Many thanks to you two (especially to tobydox who ended up registering *just* for this thread). =D>

One final off-topic question: why isn't there an LMMS forum anywhere? Is there not enough people available to maintain one? Just curious.

---

