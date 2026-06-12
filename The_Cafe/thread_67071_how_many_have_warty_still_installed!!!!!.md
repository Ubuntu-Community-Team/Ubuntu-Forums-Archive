---
title: "how many have warty still installed!!!!!"
date: 2005-09-19
forum: The Cafe
---

### Post by seiflotfy on 2005-09-19
how many still use warty!! and y wont u upgrade to hoary or breezy

---

### Post by nimrod_abing on 2005-09-24
I still run Warty. I did not upgrade to Hoary because it contained updated NVIDIA drivers that did not support my old graphics card RivaTNT2. Last version that is stable is NVIDIA drivers version 61.11 and it's what Warty has. Later versions of the driver caused my rig to become totally unstable. Plus there were no compelling new features (for my purposes at least) in Hoary. So I stayed with Warty.

Now I have a new NVIDIA graphics card and was planning on upgrading to Breezy, but I am having second thoughts. I work as a web developer and I have a lot of projects that require PHP4 for development and testing. Breezy seems to have PHP5 by default. I am doing some very funky stuff in my PHP4 scripts and I have doubts about them working without changes in PHP5. I am thinking of pinning PHP4 but then I am worried about breakage of other packages.

Upgrading from Warty to Breezy is going to be a nightmare for me even more so because I have several custom built packages and I would have to rebuild them all over again after the upgrade.

For me Warty to Breezy upgrade is definitely out of the question for now for the following reasons:

1. Again there are no compelling new features in Breezy.
2. Performance seems to be on-par with Warty based on the previews I have seen.
3. No real enhancements worth having (I don't need for the new Gnome features).
4. Some of the upgraded packages will break my current setup (e.g. PHP4)
5. Warty will still be supported up until the 6.04 version.

Maybe when Warty gets EOL'ed then I would upgrade. Maybe... Perhaps if there would be good instructions on upgrading from Warty to Breezy, then I would reconsider upgrading. But then again, frequent upgrade cycles and upgrade problems were one of the reasons I switched from Gentoo to Conectiva to Ubuntu.

Anyone else? :)

---

### Post by UbuWu on 2005-09-24
[QUOTE=nimrod_abing]
Now I have a new NVIDIA graphics card and was planning on upgrading to Breezy, but I am having second thoughts. I work as a web developer and I have a lot of projects that require PHP4 for development and testing. Breezy seems to have PHP5 by default. I am doing some very funky stuff in my PHP4 scripts and I have doubts about them working without changes in PHP5. I am thinking of pinning PHP4 but then I am worried about breakage of other packages.
[/QUOTE]

While php5 might be the default, breezy also has php4 and even php3 in the repositories. So that shouldn't be a problem.

---

### Post by Leif on 2005-09-24
nimrod_abing, if you've got a few gbs to spare, you could try installing breezy on a separate partition so you can assess whether it's worth the hassle. make sure your /home has its own partition and it'll be painless.

---

### Post by bsussman on 2005-09-24
After about 2 hrs of trying, I finally found the info on the net that says you cannot run php4 and 5 in the same instance of apache2, soo there!

---

### Post by nimrod_abing on 2005-09-25
[QUOTE=UbuWu]While php5 might be the default, breezy also has php4 and even php3 in the repositories. So that shouldn't be a problem[/QUOTE]

Yep. But I think the default action in ```
apt-get dist-upgrade
``` is to upgrade to the latest version which makes sense because it's what most people would expect. The Synaptic found in Warty does not have easy pinning support found in the new version. Plus I have read elsewhere that Warty to Breezy straight upgrade will break a lot of stuff.

PHP4 is not my only concern, I think some parts of WineX break on the new kernel found in Breezy. I also have rolled my own Mono debs from sources. It was a PITA to get that working under Warty. That and also several custom built debs.

[QUOTE=Leif]nimrod_abing, if you've got a few gbs to spare, you could try installing breezy on a separate partition so you can assess whether it's worth the hassle. make sure your /home has its own partition and it'll be painless.[/QUOTE]

Ya know, I still have about 7Gb Win2k partition just begging to be reformatted :) All my old favorite games already work under WineX so it looks like I won't be needing WIndows anymore.

Anyway, I will still wait for 6.04 because maybe then there will be a lot of compelling new features to make the upgrade worthwhile. But then again, I will be requesting Breezy CD's from shipit so by the time they arrive things will have actually settled. I can do a lot of watching and waiting to see what others experience with Breezy.

I have never actually seen Breezy in action, but I based my decisions from the preview reports floating around the Net.

---

### Post by Goober on 2005-09-25
I must confess that the major reason that I upgraded from Warty to Hoary was because of the name.  Upon reflection, I am not sure that it was worth it.  Hoary didn't really provide anything that Warty didn't have.  I mean, performance wasn't a lot better (but, with my machine, it can't get much better), and things just seemed very similar.  And I messed up the upgrading process, so had to totally re-install, and it got messy.

---

### Post by nimrod_abing on 2005-09-25
[QUOTE=bsussman]After about 2 hrs of trying, I finally found the info on the net that says you cannot run php4 and 5 in the same instance of apache2, soo there![/QUOTE]
There's no need to run both PHP4 and PHP5 in the same Apache2 instance. Though you could always run two Apache2 instances using different ports. If you need to have some bit PHP4 compatibility then [zend.ze1_compatibility_mode](http://www.php.net/manual/en/ini.core.php#ini.zend.ze1-compatibility-mode) might work for you. But I think it only reverts to the way PHP4 handles object references and not much else. If you are using some of the old behavior found  [here](http://www.php.net/manual/en/migration5.incompatible.php) as I am, then you have no choice but to run PHP4.

---

