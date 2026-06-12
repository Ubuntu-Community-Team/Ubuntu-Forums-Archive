---
title: "Does Ubuntu Update Manager Update Plug-ins?"
date: 2010-02-24
forum: Security
---

### Post by emagine on 2010-02-24
Hey Linux community,

I just had a quick question.  Does the update manager that comes with Ubuntu update the plugins in my different browsers automatically, or must you manually search for updates?  Also, along the same lines, does the update manager keep all the applications I have installed updated?  Thank you.

---

### Post by dogdo on 2010-02-24
+1 I would also like to know 

I think the update manager does update only the programs installed-not 100% sure-can someone else verify? 

Firefox as of 3.6 i believe will include native support for detecting out of date plugins...

---

### Post by mkvnmtr on 2010-02-25
It seems to me that if you installed the plug in from the repositories then update manager will upgrade them when the repository updates that version. If you installed them from the browser then the browser will update them.

---

### Post by Soul-Sing on 2010-02-25
Some plugins are in the repos. There is a mozilla-plugin team on launchpad, so these plugins are maintained and updated by them I suppose...(?)

---

### Post by Pjotr123 on 2010-02-25
Leoquant is right. Mozilla plugins which have been installed from the software repositories of Ubuntu, are being updated automatically through the centralized update function of Ubuntu.

However, extensions (.xpi) don't fall into that category. But that's being taken care of by Mozilla, as Firefox has it's own update function for those add-ons.

I must say that I find the distinctions in Firefox between add-ons, extensions and plugins vague and needlessly confusing. Mozilla really should simplify this structure and the naming conventions....

---

### Post by scottuss on 2010-02-25
Add-ons and plugins are different:

Easy answer: If you installed an Addon from within your browser (Tools > Add-ons in Firefox) then Firefox will check for updates for these, not the Ubuntu package manager.

Plugins are for playing Flash or other video media, these are usually installed automatically when needed (you will get a prompt asking if you want to install them) and these are installed via the Package Manager, meaning they will be updated by the Update Manager.

If you install anything via the Software Centre, Synaptic or command line using apt-get, then the Update Manager will update these things for you.

Summary: Installed via browser, updated via browser. Installed automatically by prompt, or by you outside of the browser = updated by Update Manager.

---

### Post by Pjotr123 on 2010-02-25
> **scottuss said:**
> Add-ons and plugins are different:

Easy answer: If you installed an Addon from within your browser (Tools > Add-ons in Firefox) then Firefox will check for updates for these, not the Ubuntu package manager.

Plugins are for playing Flash or other video media, these are usually installed automatically when needed (you will get a prompt asking if you want to install them) and these are installed via the Package Manager, meaning they will be updated by the Update Manager.

If you install anything via the Software Centre, Synaptic or command line using apt-get, then the Update Manager will update these things for you.

Summary: Installed via browser, updated via browser. Installed automatically by prompt, or by you outside of the browser = updated by Update Manager.

So it is, of course. 

But wouldn't it be much clearer for the end users, if there would be a simpler naming convention? Something like: *system-wide* plugins (from the repo's and updated through those) and *user account-only* plugins (from third parties and updated through the browser)?

Are you reading this, mozilla devs? :P

---

