---
title: "Is there a COMPLETE package manager (front-end)?"
date: 2006-06-06
forum: The Cafe
---

### Post by Jucato on 2006-06-06
Browsing through the different front-end package managers available, I was wondering if there is or will be sort of complete package manager that would at least come close to combining the advantages of existing package managers. 

Here's a review of some of the ones I've come across: 

1. Aptitude
PROS: 
- can install and remove metapackages, together with their dependencies 
- DE agnostic 
CONS 
- CLI only (It has a GUI, but one using ASCII, a sort of text-style GUI).
- basically the same as apt-get, except for metapackage handling 

2. Synaptic 
PROS: 
- History logs: you can see what you have installed through synaptic, without having to plow through the /var/logs 
- Markings: marked changes can be saved, and later on edited to do the reverse: Mark packages for installation, save marked changes, and install. Later on, you can edit the file, change all "install" to "deinstall" or vice-versa, Read Markings into Synaptic and Apply. It will remove what it installed, and install what it removed. 
- Categories: packages grouped according to type/use 
CONS: - filter only filters package names, unlike Adept. 

3. KPackage 
PROS: 
- Allows you to launch without asking for a password, if you only want to browse through. It will ask for the Admin password once you try to do something other than browse. 
- Tree view at the side (not really sure how useful that is, though) 
- Works with both RPM and DEB
CONS: -
 It's a bit slow, especially in scanning and rebuilding the dependency tree.

4. Adept (version 2.0) 
PROS: 
- Fast filter search that allows you to filter through package names, descriptions, or both. 
- Configureable toolbar 
CONS: 
- the UI is, IMHO, a mess. Only developers seem to love it. I think it scares the @#$* out of newbies. 
- No confirmation dialog boxes, allowing room for accidentally removing half of your system. 
- Their concept/use of tags is not very easy to understand.
- No utility to handle /var/cache/apt (similar to sudo apt-get clean).

So I guess, basically what I'm looking for is a pakacage manager that has these features: 
1. Efficiently manage metapackages and dependencies (like Aptitude) 
2. History/log of changes (like Synaptic) 
3. can work with DEBs and RPMs (like KPackage) 
4. Categories and/or Tags (like Synaptic/Adept) 
5. Good filter searches: names and/or descriptions (like Adept) 
6. Intrusive confirmation dialogs that can probably be enabled/disabled, depending on the user level (like everything except Adept) 

Does anyone know if such an app exists or if there are plans to make one? The reason I'm interested in this is that package management and installing software is both a boon and a bane in Linux. While many claim that installing software has never been easier in Linux thanks to these package managers, it hasn't been that easy, especially for newcomers, especially when dependencies are involved. DPKG and RPM, by themselves, are faultless. But the front-ends to these need a bit more work I think.

---

### Post by aysiu on 2006-06-06
I don't know if there's a solution, but I'm bookmarking your post for the next time someone asks about the differences between the package managers!

---

### Post by Jucato on 2006-06-06
[QUOTE=aysiu]I don't know if there's a solution, but I'm bookmarking your post for the next time someone asks about the differences between the package managers![/QUOTE]

Wow thanks! But those were generally just my experiences with the package managers (all except aptitude, which I'm just trying out now). So I might be off on a few things. 

There's a feature that I forgot about KPackage. Maybe I'll remember it when I reinstall it later.

I also didn't mention Kynaptic, Synaptic's KDE brother, because I have nothing good to say about it. :D

---

### Post by aysiu on 2006-06-06
By the way, there's a graphical frontend to *aptitude*. It's a text-based graphical mode, though.

Just type ```
aptitude
```

---

### Post by Jucato on 2006-06-11
Edited the first post to add two things:

Aptitude CON: CLI only, has a GUI, but is ASCII/text-based GUI

Adept CON: No tools to manage the apt cache (sudo apt-get clean)

---

### Post by bonzodog on 2006-06-11
Be prepared for another change in package management, because the Smart Package manager is being folded into Ubuntu, as the default manager. I know very little about it, but it is supposed to be good.

---

### Post by Jucato on 2006-06-11
Ah yes! The Smart Package Manager. I've been hearing about it for quite a while, since SUSE 10.1 came around. Seems like some used Smart to solve some problems regarding SUSE 10.1's package managers. I'm not really sure about the details, though. 

I really hope this will be *THE* package manager to rule them all. Although it seems like it's more RPM oriented, but nevertheless, it can work with DEB as well. I'm keeping my fingers crossed.

Btw, I never knew that it was being introduced into Ubuntu.

---

### Post by ComplexNumber on 2006-06-11
[quote=bonzodog]Be prepared for another change in package management, because the Smart Package manager is being folded into Ubuntu, as the default manager. I know very little about it, but it is supposed to be good.[/quote] i use smart on FC5. it is very good. its probably the most reliable of the lot. it seems quite resource hungry, though.


> 
Although it seems like it's more RPM oriented it works with debs too, but was targetted for rpms (i think).

---

### Post by Jucato on 2006-06-11
[QUOTE=ComplexNumber]i use smart on FC5. it is very good. its probably the most reliable of the lot. it seems quite resource hungry, though.

it works with debs too, but was targetted for rpms (i think).[/QUOTE]

WOw finally someone with experience using it. Just 2 things I wanted to know before I try it out myself:
1. Does it have it's own logging/history, like Synaptic?
2. Does it handle metapackages well, like Aptitude?

I don't really mind if it was originally targetted for RPMs as long as it will work flawlessly with DEBs, which is one of it's objectives (package manager agnostic). The FAQ says that Debian is also testing it.

But the major consideration here I guess would be the resource usage. They do admit (again in the FAQ), that it consumes quite a bit. But if it's faster than KPackage, I won't mind. Other users with lower end specs might, though.

---

### Post by ComplexNumber on 2006-06-11
>  1. Does it have it's own logging/history, like Synaptic? logging of what, exactly? it keeps a log of errors and problems (eg when it timed out when trying to access a particular package in a particular repo).


> 
2. Does it handle metapackages well, like Aptitude? no idea. i guess you're speaking about such things as when you use apt-get kubuntu-desktop(or whatever it is) to load all the kde libs. as far as i know, it only deals with individual packagaes like all other packaage manager gui's do.

> 

But the major consideration here I guess would be the resource usage. They do admit (again in the FAQ), that it consumes quite a bit. But if it's faster than KPackage, I won't mind. Other users with lower end specs might, though. i wouldn't bother using kpackage if i were you. its rubbish. very buggy, and doesn't seem to function correctly (it will appear as if its installed a package when it hasn't, etc).  its always been like that ever since i can first remember using it  sometime in the early days.

---

### Post by mcduck on 2006-06-11
[QUOTE=Fenyx]
2. Synaptic 

CONS: - filter only filters package names, unlike Adept. 
[/QUOTE]
In Synaptic's search dialog window you have option to search by name, description and name, maintainer, version, dependencies or provided packages.

Also, in Filter settings you can create your own filters for quite complex searches.

---

### Post by ComplexNumber on 2006-06-11
[quote=mcduck]In Synaptic's search dialog window you have option to search by name, description and name, maintainer, version, dependencies or provided packages.

Also, in Filter settings you can create your own filters for quite complex searches.[/quote]
smart isn't very good in that respect. it only searches on name or description.

---

### Post by Jucato on 2006-06-11
[QUOTE=ComplexNumber]logging of what, exactly? it keeps a log of errors and problems (eg when it timed out when trying to access a particular package in a particular repo).[/QUOTE]

Synaptic keeps a history of what were installed/removed/upgraded, arranged by date and time. I don't have synaptic installed right now, but it's under the first menu, "History", I think.

>  no idea. i guess you're speaking about such things as when you use apt-get kubuntu-desktop(or whatever it is) to load all the kde libs. as far as i know, it only deals with individual packagaes like all other packaage manager gui's do.

When you use aptitude to install a metapackage, like kubuntu-desktop or build-essential, it remembers the dependencies were installed with it. So when you use aptitude to remove the metapackage, it removes the dependencies also, IF they are not being used/depended upon by anything else.

> i wouldn't bother using kpackage if i were you. its rubbish. very buggy, and doesn't seem to function correctly (it will appear as if its installed a package when it hasn't, etc).  its always been like that ever since i can first remember using it  sometime in the early days.
I don't use it either. But for a KDE package manager, it far better than Adept. But I prefer to use Synaptic and apt-get.

@mcduck: yes, I know about the different categories for searching in Synaptic, but filters are faster than that. The search categories are also limited, but Adept's filters can be mixed and matched in any combination possible (name, description, maintainer, installed, not installed, upgradable, no changes, for installation, for removal, for upgrade).

I haven't checked out Synaptic's filter settings, though. Thanks for the pointer. I'll try it out.

---

### Post by ComplexNumber on 2006-06-11
> Synaptic keeps a history of what were installed/removed/upgraded, arranged by date and time. I don't have synaptic installed right now, but it's under the first menu, "History", I think.
its got summary and log in the menu, but there is nothing in mine at the moment.



> When you use aptitude to install a metapackage, like kubuntu-desktop or build-essential, it remembers the dependencies were installed with it. So when you use aptitude to remove the metapackage, it removes the dependencies also, IF they are not being used/depended upon by anything else.
smart doesn't deal with orphan packages AFAIK.

---

### Post by Gustav on 2006-06-14
Here's a list of features in smart (it seems very good and high-tech :)) [http://labix.org/smart/features](http://labix.org/smart/features)

---

### Post by Christmas on 2006-06-14
When I used Ubuntu I just loved Synaptic. It was the easiest way to install software I have ever tried in Ubuntu. Now on Kubuntu I didn't even bother to open Adept. I don't like its interface, its slowness and the way it works, I only use command line with apt-get which never fails and seems faster. I guess it's a matter of taste.

---

