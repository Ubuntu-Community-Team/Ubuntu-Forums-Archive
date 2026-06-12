---
title: "Remove extra repos."
date: 2022-04-08
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2022-04-08
Upgraded from Ubuntu 21.10 to Ubuntu 22.04.  Now a have a lot of sources in my list, and I do not know which ones to remove.  How do I just clean them up with one command from the terminal.


Henry

[ATTACH=CONFIG]290256[/ATTACH]

---

### Post by TheFu on 2022-04-08
Use **sudoedit**.
That's 1 command, but probably not what you hoped.

You do realize that 22.04 hasn't been released yet, correct?  Thanks for testing a beta release.

---

### Post by ajgreeny on 2022-04-08
It will be much easier to see the current situation if you show us the output of command ```
cat /etc/apt/sources.list
```

In your image there are no enabled repos at the moment; how did you upgrade to 22.04?
Did you manually edit the ***/etc/apt/sources.list*** file?
Is the image you attached from your installed OS or from somewhere else; I presume it is not from the installed OS as there is nothing showing for the jammy repos.

As TheFu says above, don't forget that 22.04 is still in beta status and you can expect many bugs still to be squashed, even after its release; it can take several weeks for a really smooth running version to be guaranteed, though having now been running dual boots of Focal, 20.04, and Jammy, 22.04, on both my machines since November last year I will admit that Jammy is looking very good with no major problems for me so far.

---

### Post by grahammechanical on 2022-04-08
Source code repositories (deb scr) are in the sources list file but they are comment out with a hash ( # ). Therefore they are ignored by the software updater utility and the apt update/upgrade commands. No time is lost connecting to these internet addresses.

Ubuntu is open source software. So Canonical, the sponsor of Ubuntu, makes it easy for uses to obtain the source code as required by the commitment to open source software.

Please explain the benefit from removing the internet addresses of commented out repositories

Regards

---

### Post by DuckHook on 2022-04-08
> **ajgreeny said:**
> &#8230;I will admit that Jammy is looking very good with no major problems for me so far.
Still lots of minor to not&#8209;so&#8209;minor irritants here. See: [https://ubuntuforums.org/showthread.php?t=2473639](https://ubuntuforums.org/showthread.php?t=2473639)

Also, there's the complete absence of a .deb version of Firefox, the updates to various databases that make them incompatible with older releases (gnucash, LXD), old scripts that must be revised to work&#8230;

But, overall, I agree that it's looking like a nice upcoming release. Still lots of bugs to squash, but no different than any other LTS at this point in the development cycle.

---

### Post by ajgreeny on 2022-04-09
> **DuckHook said:**
> Still lots of minor to not&#8209;so&#8209;minor irritants here. See: [https://ubuntuforums.org/showthread.php?t=2473639](https://ubuntuforums.org/showthread.php?t=2473639)

Also, there's the complete absence of a .deb version of Firefox, the updates to various databases that make them incompatible with older releases (gnucash, LXD), old scripts that must be revised to work…

But, overall, I agree that it's looking like a nice upcoming release. Still lots of bugs to squash, but no different than any other LTS at this point in the development cycle.
I'm sure you're right, but as you may know, I use Xubuntu, not Ubuntu, so wayland sessions are something I have still to investigate fully.

The lack of .deb versions of some packages is a problem, I agree, but so far one for which I've managed to find workarounds, however I suspect I will eventually have to accept that snaps are almost inevitable and will have to move towards them.

It will not mean I like the idea of them and the restrictions they put towards my usual way of using thr filesystem.

---

### Post by TheFu on 2022-04-09
I've thought about creating a snap-stripping script. One that pulls all the files out of the snap directories so we aren't stuck using them and can apply our own constraints as we like.  In the old days, we would setup a **run** script for different versions of software to setup any environment variables to ensure our libraries were found before the system libraries were.

I'm not a fan of packages that should be 15MB being 950MB.

---

### Post by DuckHook on 2022-04-09
> **ajgreeny said:**
> …I use Xubuntu, not Ubuntu, so wayland sessions are something I have still to investigate fully.
I've found Wayland to solve some problems for me while creating others. It feels smoother—I don't get the artifacts and refresh rate limitations that I had with X11, but it lacks equivalent tools to those that I found useful: I miss the ease of info in xrandr. The extra security of Wayland is very welcome, but even this comes at a cost to some people: it breaks their old workarounds.
> The lack of .deb versions of some packages is a problem, I agree, but so far one for which I've managed to find workarounds, however I suspect I will eventually have to accept that snaps are almost inevitable and will have to move towards them.

It will not mean I like the idea of them and the restrictions they put towards my usual way of using thr filesystem.
I wonder if snaps will evolve? :-k If the devs could just revise the snap system to give power users the options of finer grained and more personal control, then they could sometimes be a good thing. As things stand, they are another mixed blessing. I was just force&#8209;installed the snap version of FF and it still doesn't work with Gnome extensions.
> **TheFu said:**
> …I'm not a fan of packages that should be 15MB being 950MB.
Yep. One of the casualties of Ubuntu's recent evolution is the erosion of its opposition to system bloat. It's not just Canonical. Fedora and Manjaro seem to be headed in the same direction. No one is offended by multi&#8209;GB apps anymore. It's a little depressing. Not quite a deal&#8209;breaker (yet) but, still, disappointing.

@OP

With respect to your issue:

The info you provided us is incomplete. No one can help you with only the info provided. Please post the output that ajgreeny asks for.

A more general observation follows:

If you stick to only the repos that were installed by default in a virgin install, you don't need to turn anything off. Ubuntu is already quite secure by default, and turning off repos will likely invite trouble rather than solve anything.

People get into trouble because they introduce *additional* repos to those that are installed by default. These include PPAs. It is these foreign repos that end up breaking both security and the system itself. If you want to get back to a solid system, you need to turn off these foreign repos; not the ones that came with Ubuntu.

We can't help you until you post what ajgreeny asks, plus the following:```
ls -laH /etc/apt/sources.list.d
```Some repos don't install themselves in the sources.list file. Instead, they install their own config file in the sources.list.d subdirectory. We need to see those too.

---

### Post by TheFu on 2022-04-09
If there is interest in hardening an Ubuntu system, a 4-part blog/podcast just finished up on that topic.  Nothing new, except it is listed in an overview version for experienced users.  [https://ubuntusecuritypodcast.org/episode-156/](https://ubuntusecuritypodcast.org/episode-156/) .... scroll down to the TL;DR section.    Or is that TL;DL?

Cleaning up extra sources would included in the 'remove software that isn't used' section, though not specifically listed.

---

### Post by #&amp;thj^% on 2022-04-09
> **TheFu said:**
> If there is interest in hardening an Ubuntu system, a 4-part blog/podcast just finished up on that topic.  Nothing new, except it is listed in an overview version for experienced users.  [https://ubuntusecuritypodcast.org/episode-156/](https://ubuntusecuritypodcast.org/episode-156/) .... scroll down to the TL;DR section.    Or is that TL;DL?

Cleaning up extra sources would included in the 'remove software that isn't used' section, though not specifically listed.

+1 That was a good read and listen for those who like to stay abreast.

---

