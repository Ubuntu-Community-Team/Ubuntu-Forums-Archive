---
title: "List the software you install manually not using APT! Why? How do you handle these?"
date: 2008-12-03
forum: The Cafe
---

### Post by tnek on 2008-12-03
Hi,

I thought this could be a thread in the same sense as "list the most useful applications" where people could bounce ideas off each other.

Of course I think we all agree that automatic installation where dependencies and upgrades will be handled for us is one of the truly great things with a lot (almost everyone has some kind of system like this) of Linux distributions.

As I'm still (and probably will be for a few years) too inexperienced when it comes to APT, dpkg and all that I won't be able to answer "How do you handle these?". I'm hoping that more experienced users will express their opinions on that question. I do have answers for the first two questions and my motivations: (I'm running _Hardy_.)


[LIST]
[*][Drupal]("http://drupal.org/") as I wanted version 6.x and not 5.x which is in the repositories. Drupal has its own automatic upgrade system which I think will work fine. I want version 6.x as I might create some modules of my own and I want the latest stable version so that its API won't be too old when I get around to programming.
[*][Eclipse]("http://www.eclipse.org/") as I want the latest version which is compatible with the latest plug-ins. It also has its own upgrade system. It's important to me to be running the same version as a couple of other developers as we're checking in the project files into SVN, and not just the source code. I don't want any incompatibilities due to us having different versions.
[*][OpenOffice]("http://www.openoffice.org/"), again I want the latest version. This time as 3.x has better MS Office compatibility and when I send documents to people the sad fact is they're most often expecting a Word file, and I can't start the revolution. I can't test it in the real MS Word so upgrading to 3.x will increase my chances that my documents will look as intended.
[*][Awesome]("http://awesome.naquadah.org/") window manager. Yet again I want the latest version. Version 3.x has been stable for a while now and I don't want to invest too much time in learning an obsolete configuration file format for 2.x, which I'll have to throw out and learn a different format for 3.x. I've tried 2.x. and it seemed really nice and I want to get on to the Awesome train, but I want 3.x.
[/LIST]
I want to use APT for everything else, at least at the moment.

I've already handled the Drupal installation by following the insallation instructions. I had to configure Apache a  little bit to allow .htaccess files to override a setting Drupal needed. But that wasn't a big problem.

Do you have any tips on how I should handle the other manual installations? What software do you install manually? And why?

---

### Post by geirha on 2008-12-03
OpenOffice.org provides .deb packages on their site. If you install those, you can remove them later through synaptic or apt-get or similar. Don't know about the other applications.

---

### Post by anaconda on 2008-12-03
> **tnek said:**
> Hi,
Do you have any tips on how I should handle the other manual installations? What software do you install manually? And why?

older version of samba, (3.0.32) because ubuntu:s new version doesn't support things I need most.

I compiled it myself and just copied the needed files over the ones installed using apt, and then I locked the existing versions in synaptic, so that update manager wont "update" it accidentally..

And some games that aren't in the repositories, or newer versions than in repositories..

---

### Post by gTinker on 2008-12-03
[QUOTE=tnek]
Do you have any tips on how I should handle the other manual installations? What software do you install manually? And why?[/QUOTE]

This might be a good place to mention security. When installing from the official repositories you can trust that the binaries are safe. When you choose to install from somewhere else, there is always a chance of a security risk. That being said, I would likely trust something from, for example, the Open Office site. The further you get from mainstream the risker things can become. Just because there is a .deb available doesn't mean you should trust it. If one isn't able to unpack it and check the binaries oneself, it is better to stick to official repositories, or at least have a good recent backup. This is a general answer, not directed at any software that you have mentioned.

---

### Post by tnek on 2008-12-03
gTinker: Good food for thought. As you said it's having a little less security as there is no middle man between the developer and me, the user. I would really think twice about manual installation in a corporate environment if I were the system administrator.

In my case it's just my own workstation and I'll try to stay on top of the update notifications from the software's web pages for the ones I choose to install manually. I'm willing to take the additional risk to have a little bit better (in terms of functionality, not security) environment now.

Do most of you choose to install and manage some software manually? And how much do you manage yourself? And what do you do if an application requires a few libraries and the ones you have (from APT) are too old? Do you have two versions installed? I bet it can get messy if there are lots of software to manage our self's. Any experience on that?

---

### Post by Cammy on 2008-12-03
I installed the latest conky manually, and I install my nvidia video card drivers manually.  Pretty much everything else is from the repositories.

---

### Post by aysiu on 2008-12-03
Everything I want is in the repositories. It's one of the main reasons I stick with Linux. Otherwise, I'd be using Windows or Mac. I'd hate it if I had to compile stuff from source.

---

### Post by oldos2er on 2008-12-03
Programs I've compiled and installed from source: Exaile 0.2.14, slrn (forget the version no., but it's newer than the one in the repos), BOINC 6.2.15, and some others I can't think of right now. All these programs are in the repos, but I prefer having newer versions of them.

 Some apps I compile just for fun, and for the learning experience.

---

### Post by giacomo on 2008-12-03
- I've recently compiled **wine** from source because the repository version was too old.

- I've recently installed (from .deb) **VirtualBox** because the Ubuntu version was unable to work with USB (even with workarounds found in the web).

- I'm wondering to re-install **mono** by compiling it (with debug symbols) for be able to debug CLR applications with GDB.

Bye!

---

