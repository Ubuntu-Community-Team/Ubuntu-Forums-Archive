---
title: "Six fatal mistakes you'll want to avoid"
date: 2010-02-11
forum: Security
---

### Post by Pjotr123 on 2010-02-11
I've published a web page with six fatal mistakes, which the beginner with Ubuntu should avoid. Maybe a bit controversial for some of you, but it's written from the viewpoint of a careful and cautious system administrator and aimed at the inexperienced.

Here it is:
[http://sites.google.com/site/easylinuxtipsproject/fatalmistakes](http://sites.google.com/site/easylinuxtipsproject/fatalmistakes)

Remember: it's written with caution in mind, mainly aimed at beginners with Linux, and of course it doesn't apply to the intrepid adventurers and experienced old hands among you.... :)

---

### Post by lovinglinux on 2010-02-11
I agree that users should be warned about the possible implications of using third-party repositories, scripts, backports and deb files or about removing applications installed by default, but saying they are fatal mistakes is a little bit sensationalist. 

The real problem is that people run commands and follow tutorials without even knowing what they do. I have helped several users that didn't even know they had a PPA repository enabled.

I particularly don't like the title of your article and the inclusion of Ubuntuzilla on your list. 

Unbuntuzilla is not a script anymore. It is a repository and it doesn't replace Firefox or anything installed by default, it just installs another package with the version released by Mozilla and divert the launcher command to use the new version. It can be easily added/removed without causing any problem to your system.

> Besides, Firefox (and the Mozilla engine) is such an important part of the entire operating system, that you can't simply replace it by another version.

Firefox is not "such an important part of the entire operating system". You can even remove it (although I don't recommend), if you do only clean installs of Ubuntu or make sure you re-install *ubuntu-desktop* metapackage before an upgrade. Some applications might depend on xulrunner, but the package manager will warn you if that is the case.

---

### Post by chemamar on 2010-02-11
> **Pjotr123 said:**
> I've published a web page with six fatal mistakes, which the beginner with Ubuntu should avoid. Maybe a bit controversial for some of you, but it's written from the viewpoint of a careful and cautious system administrator and aimed at the inexperienced.

Here it is:
[http://sites.google.com/site/easylinuxtipsproject/fatalmistakes](http://sites.google.com/site/easylinuxtipsproject/fatalmistakes)

Remember: it's written with caution in mind, mainly aimed at beginners with Linux, and of course it doesn't apply to the intrepid adventurers and experienced old hands among you.... :)

I am using ubuntu tweak and so far I thought it was safe to do it. Please I would like to know more views.

---

### Post by nanotube on 2010-02-11
Hi Pjotr123,

Just want to second what lovinglinux has said. 

I can agree that someone who doesn't know what he's doing should stick to the official repositories, but a lot of the items you have included don't really qualify as "fatal mistakes". It would be better to save that label for the really bad stuff, otherwise it will lose its 'scare power' if we apply it to everything that "may cause some trouble". 

And a note about ubuntuzilla: it is now a repository, so can really be classed together with any other ppa on the issues of risk and trust. Though it really is even safer, because (1) it doesn't overwrite any official packages, and (2), the packages are directly verifiable, since they contain official mozilla builds, and the checksums can be compared directly against the contents of the tarballs downloaded off mozilla.com. both of these items are more than can be said about most other ppas.

And another note: backports are about as safe as you get. stuff gets into backports after it's been tested in proposed. the packages in backports contain newer versions of software that will /never/ make it into the official repositories for a given ubuntu release (due to the ubuntu 'security updates only' policy for the main repos of a frozen release). it's not the case, as you imply, that after some more testing, they'll be making it into the official repos.  so you really shouldn't group proposed and backports together.

---

### Post by Silvertones on 2010-02-11
I needed to use some fillable pdf documents so I really needed Adobe. I did it like this, was this risky or OK.
Thanks
Try installing from the partner repository.

Go to System > Administration > Software Sources

You will need to enter your password to open this application.

Click on the Other Software tab, and place a check against the line  ending with "partner"

Press the close button and then press Reload.

You should then be able to find the package acroread in Synaptic Package  Manager and install.

---

### Post by lovinglinux on 2010-02-11
> **Silvertones said:**
> I needed to use some fillable pdf documents so I really needed Adobe. I did it like this, was this risky or OK.
Thanks
Try installing from the partner repository.

Go to System > Administration > Software Sources

You will need to enter your password to open this application.

Click on the Other Software tab, and place a check against the line  ending with "partner"

Press the close button and then press Reload.

You should then be able to find the package acroread in Synaptic Package  Manager and install.

That's perfectly safe. Basically stuff that is not open source or not free and are distributed by Canonical partners.

BTW, I would recommend [gPDF](https://addons.mozilla.org/en-US/firefox/addon/14814) extension for Firefox. It scan webpages for pdf links and set them to open with Google PDF viewer.

---

### Post by Silvertones on 2010-02-11
That's good thanks.

---

### Post by Pjotr123 on 2010-02-11
Using Ubuntuzilla is not a security risk, I agree. But the Firefox version it installs, hasn't been adapted to, nor been tested for Ubuntu. Virgin upstream material, not tuned to Ubuntu... This may cause weird behaviour at times.

So Ubuntuzilla's not fit for beginners with Linux, I think. They'd better stick to the default Firefox version in Ubuntu.

You'll notice that I've described the Ubuntuzilla risk as a "yellow alert", so not very risky for the system. Maybe I should tone down the remark about the Mozilla engine, though. I'll look into it. :)

@Silvertones: the Adobe Reader for Linux that you've installed, won't harm your system. No worries there. The partner source is secure. 

However, Adobe does a very bad job in issuing security updates for it's Linux Reader. The current version of Adobe Reader for Linux is insecure and has been so for a long time. There are exploits "in the wild". Only use it for specific purposes and not as the default pdf reader.

--edit: I removed the remark about the Mozilla engine entirely, and I added that using Ubuntuzilla is no security risk, but "merely" diminishes the stability and reliability of Firefox.

---

### Post by lovinglinux on 2010-02-11
> **chemamar said:**
> I am using ubuntu tweak and so far I thought it was safe to do it. Please I would like to know more views.

I never had a problem with it when I used it. Nevertheless, ubuntu-tweak is not in the official repositories. I would advise to Google for [ubuntu tweak problem](http://www.google.com/search?q=ubuntu+tweak+problem+site%3Aubuntuforums.org) and check if anyone complained about serious issues caused by it.

---

### Post by lykwydchykyn on 2010-02-11
You really have them handling the thing with kid-gloves here.  I can see the point, but I would say telling people not to uninstall ANY of the default applications is going a bit far.  

Besides, none of these are "fatal mistakes".  They're "learning opportunities" :-)

---

### Post by Pjotr123 on 2010-02-11
> **lykwydchykyn said:**
> You really have them handling the thing with kid-gloves here.  I can see the point, but I would say telling people not to uninstall ANY of the default applications is going a bit far.  


I strive to teach Linux beginners to build a system that's as sturdy and reliable as a Leopard tank (see attachment). :)

A safe platform to learn Linux. Rock solid. Later on, they'll start experimenting anyway. But then they'll know what they are doing...

---

### Post by merlin38 on 2010-02-12
First i'm french speaking and i just start reading english doc and forums, so it could help to understand my point of view.

I think it's a very good idea to claim the risks of such programm instalation.
It is clearly a good practice only to trust official release.

But many beginners come from Windows. They discover open source world with firefox, thunderbird, etc... On windows, the linux users explain they will have a better security and performance by using open-source software. Windows users became proud of using these software and they discover a new world. They can use always the latest version without wasting money.
They they decide to switch to Ubuntu. And then every body tells them they have to loose freedom to install software. You are told that software are dangerous. You are told that third party have to test software before allowing you to use them. It's very suprising ! It become hard to see the real différence beetween Windows and Linux phylosophy. With both you are considered as a stupid user. In windows you are so stupid that you have to pay a lot directly to developpers and use without understanding and everything is closed, in Linux you are so stupid that you have to help making the popularity of free software rise, so that ads could make developper indirectly earn much money, and the docs are so rare or technic  that you can't learn by yourself. Note : i emphasize to much, volontarly to be clear. Further more, users have to wait 6 month to use safely the latest vesion. (a fist i had to use my double boot to use windows to test official release of Firefox!!! Dissapointing.)

It is very rare that someone explain how to verify automated installer, how to check yourself security. Pédagogic material that combine easy access for beginners and advanced tips to understand linux are rare !!
Often you find only warnings, or too simple doc. On the other hand you find very complicated doc that are related to other, themself related to other.....
I'm very dissapointed to have difficulties to find tutorials that make me UNDERSTAND WHY, and not only LEARN HOW.

But i'm very happy to use Ubuntu. Just a little bit dissapointed;) And trust on the fact that I think Linux is clearly different, and that i do prefer the philosophy far much more.

---

### Post by Jive Turkey on 2010-02-12
I learned a couple of things from your articles, thanks.  I disagree on the removal of default apps as I remove the games that come with gnome pretty quickly after installing.  In the hands of someone that tends to over-tinker, I wouldn't say that ubuntu tweak is any more dangerous than synaptic.

---

### Post by Pjotr123 on 2010-02-12
> **Jive Turkey said:**
> I learned a couple of things from your articles, thanks.  I disagree on the removal of default apps as I remove the games that come with gnome pretty quickly after installing.


The games are probably safe to remove, I agree. But when you remove Evolution, for instance, you're in trouble. I think it's too complicated for a Linux beginner (target audience) to differentiate in this aspect, so I kept it simple.

> **Jive Turkey said:**
> 
In the hands of someone that tends to over-tinker, I wouldn't say that ubuntu tweak is any more dangerous than synaptic.

But it is.... Ubuntu Tweak offers too easy access to all kinds of PPA's and third party software, whereas Synaptic by default only uses the normal repositories.

@merlin38: Pour moi, ce n'est pas une problème d'attendre quelques mois pour le dernier Firefox.... Ce n'est pas important pour moi, d'avoir toujours les derniers cris; pourvu que je peux faire tout ce que je veux avec mon logiciel. :)

---

### Post by Soul-Sing on 2010-02-12
Pjotr123 points on the weak spot, or more precisely the vulnerability of Linux in general and Ubuntu in particular (Ubuntu is the most popular linux distro), namely the software sources. Where does software come from, and which sources are safe and secure, and which are questionable.(Or maybe unsafe)
Good point to discuss this.

---

### Post by lykwydchykyn on 2010-02-12
> **Pjotr123 said:**
> I strive to teach Linux beginners to build a system that's as sturdy and reliable as a Leopard tank (see attachment). :)

A safe platform to learn Linux. Rock solid. Later on, they'll start experimenting anyway. But then they'll know what they are doing...

Well, that sounds like a good idea.  I think the only caveat is that you don't want to make people scared to touch the thing.  I work with a lot of non-computer-savvy people, and for the most part their problem is that they fear the computer.  They fear that if they click on the wrong thing the system will break beyond repair.

What's more, they tend to acquire superstitions about computers -- you must do this, you must never do this, etc.  I don't think any of your suggestions are wrong, but you have to be careful how you phrase things so that people don't end up thinking, for example, "you should never install a .deb file" when sometimes that's the best solution.

Just my 2 cents, take it or leave it.

---

### Post by Silvertones on 2010-02-12
The version of Adobe Reader that got installed was 9.3 which is the same as  windows

---

### Post by wilee-nilee on 2010-02-12
Fud.

---

### Post by Pjotr123 on 2010-02-12
> **Silvertones said:**
> The version of Adobe Reader that got installed was 9.3 which is the same as  windows

Hmmm... In my language version (Dutch) I can only download Adobe Reader 8.1.7. I just discovered that the English language version is at 9.3. So "only" the Dutch version is currently insecure (and maybe other language versions as well).

Anyhow, the default Evince pdf reader in Ubuntu is always being kept secure. Apart from that, it's much leaner than Adobe Reader. Therefore it's my favourite.

---

### Post by xpod on 2010-02-12
> **lykwydchykyn said:**
> Well, that sounds like a good idea.  I think the only caveat is that you don't want to make people scared to touch the thing.  I work with a lot of non-computer-savvy people, and for the most part their problem is that they fear the computer.  They fear that if they click on the wrong thing the system will break beyond repair.

What's more, they tend to acquire superstitions about computers -- you must do this, you must never do this, etc.  I don't think any of your suggestions are wrong, but you have to be careful how you phrase things so that people don't end up thinking, for example, "you should never install a .deb file" when sometimes that's the best solution.

Just my 2 cents, take it or leave it.

The majority of computer users i now know are absolutely terrified to touch anything on their computers. Just investigating stuff in their menus is enough to bring many out in a cold sweat. Indeed, i myself was like that to begin with although only for my first week or two on a computer. It wasn`t long before i had the thing in bits on the floor.:p

I think i even mentioned in an earlier thread about that trialware crap i often find on peoples computers 6, 8 12+ months after they buy the things, purely because they`re terrified of removing anything....the ones that at least know of Add/Remove(99.999% Windows users) anyway.

As far as that article is concerned though it is just a wee bit dramatic sounding, to say the least.

---

### Post by Silvertones on 2010-02-12
Yes the only time I use Adobe is for the rare times I need to fill out a form.

---

### Post by OpSecShellshock on 2010-02-13
There are some additional things you can do with Adobe Reader to stop certain kinds of exploits (though most of these exploits, at the end of their convoluted processes, will try to load Windows-specific components--which lowers the risk for Linux users):

In the preferences, disable JavaScript. If you come upon a specific situation where it's necessary, enable it just for that thing and disable again when you're finished. It's also a good idea to go into Preferences-->Internet and uncheck the boxes that allow Reader to open PDFs within the browser when they come from the web. That will ensure that such documents are only ever opened in the stand-alone client application and will conform to the settings you've determined, rather than in the browser plugin with whatever those settings are. This is good because sometimes hitting the wrong link will quietly retrieve and open a PDF without you knowing that you're doing it (which, again, is a somewhat bigger risk for Windows users).

I think there's also a setting where you can make it so your Reader application can't access the internet by itself, but I don't have it on this computer so I can't say where it is.

---

### Post by Easy Limits on 2010-02-13
I have done five out of six.  So far, so good.

---

### Post by nanotube on 2010-02-14
> **Easy Limits said:**
> I have done five out of six.  So far, so good.

haha, i'm curious - which one haven't you done (yet?) :)

---

### Post by Easy Limits on 2010-02-14
#1

---

### Post by Pjotr123 on 2010-02-15
@Easy Limits: in that case, you might want to consider making a clean new start:
[http://sites.google.com/site/easylinuxtipsproject/reinstallation](http://sites.google.com/site/easylinuxtipsproject/reinstallation)

---

### Post by sh4d0w808 on 2010-02-15
"Never remove any application that's part of the default installation of Ubuntu"

Nope - it is not Windows. Ubuntu is very similar to windows from this point of view: it comes a lot of softwares, but you won't need most of them. You can delete those programs carefully.

(If you want, you can start from the other side: build up a brand new system from CLI interface with minimal necessary graphical parts of gnome - the system will work correctly without errors. In Tips and Tricks section, you can find a topic, how to achieve ubuntu-minimal desktop.)

---

### Post by Pjotr123 on 2010-02-15
> **sh4d0w808 said:**
> "Never remove any application that's part of the default installation of Ubuntu"

Nope - it is not Windows. Ubuntu is very similar to windows from this point of view: it comes a lot of softwares, but you won't need most of them. You can delete those programs carefully.

(If you want, you can start from the other side: build up a brand new system from CLI interface with minimal necessary graphical parts of gnome - the system will work correctly without errors. In Tips and Tricks section, you can find a topic, how to achieve ubuntu-minimal desktop.)

Try removing Evolution, for instance... Big chance that you'll remove too much, if you're not very careful. My instruction is aimed at beginners with Linux, who most likely won't know exactly what impact their hacking will have.

What you say about starting with a minimal no GUI Ubuntu and then adding stuff, is correct. But that's a wholly different thing...

---

### Post by sh4d0w808 on 2010-02-15
> **Pjotr123 said:**
> Try removing Evolution, for instance... Big chance that you'll remove too much, if you're not very careful. My instruction is aimed at beginners with Linux, who most likely won't know exactly what impact their hacking will have.

Evolution:

```
sh4d0w@XXXYYYZZZ:~$ sudo apt-get remove evolution
[sudo] password for sh4d0w: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  evolution evolution-exchange evolution-indicator evolution-plugins
0 upgraded, 0 newly installed, 4 to remove and 2 not upgraded.
After this operation, 10.8MB disk space will be freed.
Do you want to continue [Y/n]?
```

Here is nothing, which cannot be removed.

> **Pjotr123 said:**
> What you say about starting with a minimal no GUI Ubuntu and then adding stuff, is correct. But that's a wholly different thing...

I know, this is the reason, why I used ().

---

### Post by Pjotr123 on 2010-02-15
> **sh4d0w808 said:**
> Evolution:

```
sh4d0w@XXXYYYZZZ:~$ sudo apt-get remove evolution
[sudo] password for sh4d0w: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  evolution evolution-exchange evolution-indicator evolution-plugins
0 upgraded, 0 newly installed, 4 to remove and 2 not upgraded.
After this operation, 10.8MB disk space will be freed.
Do you want to continue [Y/n]?
```

Here is nothing, which cannot be removed.


Try getting rid of evolution-data-server-common as well... Or rather, don't.  :)

---

