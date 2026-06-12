---
title: "Firefox 1.0.6 Removed from backports"
date: 2005-07-23
forum: Ubuntu Backports
---

### Post by Mez on 2005-07-23
Firefox 1.0.6 has been removed from backports due to problems with this release, see

[http://lists.ubuntu.com/archives/ubuntu-users/2005-July/043452.html](http://lists.ubuntu.com/archives/ubuntu-users/2005-July/043452.html)

for more details

---

### Post by rpgcyco on 2005-07-23
Errrr.... doesn't that only apply to the people who used the [official security update](http://ubuntuforums.org/showthread.php?t=50685) and not the people who used\are using 1.0.6 from Backports...?

- Rpg Cyco

---

### Post by marcopse on 2005-07-24
I had problems with ubuntu package, but at present i've no problem with official 1.0.6 version and all my extensions.

From release notes:
> Here's what's new in Firefox 1.0.6:

    * Restore API compatibility for extensions and web applications that did not work in Firefox 1.0.5.
[http://www.mozilla.org/products/firefox/releases/1.0.6.html](http://www.mozilla.org/products/firefox/releases/1.0.6.html)

Does anyone else can confirm?

---

### Post by ScottEllis24 on 2005-07-24
I upgraded yesterday, and haven't had any problems Scott

---

### Post by jdong on 2005-07-24
I've restored 1.0.6 to staging for further testing... So far, it looks good. Many people have tested and reported that this version works with extensions. RedHat has also backported 1.0.6 for its Enterprise Linux customers, so that's another good vote of confidence.



I think the mailing list entry was a typo of some sort...

---

### Post by Velvet Elvis on 2005-07-24
Works fine here with the dozen or so extentions I use.

Wasn't the main problem mostly with the version of the TBE extention packaged in hoary?  I don't really understand why they feel the need to package extentions anyway.

---

### Post by TheSavage on 2005-07-24
Same here, works very good.

---

### Post by bored2k on 2005-07-24
The official .6 is working great here.

---

### Post by matthew on 2005-07-24
1.0.6 is working great for me

---

### Post by craigevil on 2005-07-25
I installed it from staging no problems.

---

### Post by AndyAWS on 2005-07-25
I've been using 1.06 since it hit staging last week. I've had no problems with it.
AFAIK all of the problems were with 1.05.
See this: [http://www.informationweek.com/story/showArticle.jhtml?articleID=166401151](http://www.informationweek.com/story/showArticle.jhtml?articleID=166401151)

---

### Post by ShaneAu on 2005-07-25
[QUOTE=AndyAWS]I've been using 1.06 since it hit staging last week. I've had no problems with it.
AFAIK all of the problems were with 1.05.
See this: [http://www.informationweek.com/story/showArticle.jhtml?articleID=166401151](http://www.informationweek.com/story/showArticle.jhtml?articleID=166401151)[/QUOTE]
 Yep no problems here either. So all is good so it seems. :).

---

### Post by jdong on 2005-07-25
excellent, it'll go into stable during the next mass-promotion.

---

### Post by jdong on 2005-07-25
Martin Pitt (who is in charge of security at Ubuntu) and I had a quick e-mail conversation, and here's what he said:

> 

John Dong [2005-07-24 15:32 -0400]:
> [http://lists.ubuntu.com/archives/ubuntu-users/2005-July/043452.html](http://lists.ubuntu.com/archives/ubuntu-users/2005-July/043452.html)
>
> >From this mailing list entry, it seems like you're saying that 1.0.6 has the
> same problems as 1.0.5 and the recent Ubuntu Security update. However, here
> at Backports, we've packaged Breezy's 1.0.6 for testing in the staging tree.
> >From the reports (8 or so, more coming) we've gathered, it seems like
> 1.0.6doesn't exhibit the instability that the USN update has.

One of the first things I tried was the packaged
mozilla-tabextensions, which does not work with 1.0.6 as well.
However, I tried some more extensions, and these worked with 1.0.6.

I'll try to backport the 1.0.6 changes today.

Martin


---

### Post by rwabel on 2005-07-25
[QUOTE=jdong]Martin Pitt (who is in charge of security at Ubuntu) and I had a quick e-mail conversation, and here's what he said:[/QUOTE]
 now I'm curious which version I should use, the one from hoary-security or the back-port one? backport is newer, but is it the more stable one?

---

### Post by jdong on 2005-07-25
Use the Backports one. I've gotten a report or two from others that the official hoary-security one crashes more than the Backports package.

I don't know the validity, and I won't go on a revenge-rant about these non-Backports bug reports finding their way to me...... (shuts up)

---

### Post by rwabel on 2005-07-25
[QUOTE=jdong]Use the Backports one. I've gotten a report or two from others that the official hoary-security one crashes more than the Backports package.

I don't know the validity, and I won't go on a revenge-rant about these non-Backports bug reports finding their way to me...... (shuts up)[/QUOTE]
 thanks for the info. I had so far no problems with 1.0.6 from backport. All my extensions are working fine and I've quit a lot! thanks for the bp

---

### Post by newbie2 on 2005-07-26
loaded ff 1.0.6 today via backports...ff froze then...then i restarted my comp(like in Window$ :-P )...and it seems ok now  :)

---

### Post by glandula on 2005-07-26
[QUOTE=][/QUOTE]
 middle click to open in new window doesent seem to work anymore after installing this :(

---

### Post by strikeforce on 2005-07-26
Erm I install the backports one and it installed I couldn't open up firefox.  I then uninstall all the firefox ones got rid of backports re-installed 1.06 off the 'official' mirrors and its all fine?

I'm not sure but the symbolic links got stuffed up.  When I tried to uninstall the official version and install the backports version it removed ubuntu-desktop and yelp as well as all the other firfox files?

I'm not sure how to get around that since I'm originally from an rpm based distro.

Does dpkg have an equivalent to rpm -e --no-deps firefox?

*edit 

Don't worry after a complete uninstall and re-install its all good.  Ignore me.

---

### Post by AgenT on 2005-07-26
[QUOTE=strikeforce]Erm I install the backports one and it installed I couldn't open up firefox. I then uninstall all the firefox ones got rid of backports re-installed 1.06 off the 'official' mirrors and its all fine?

I'm not sure but the symbolic links got stuffed up. When I tried to uninstall the official version and install the backports version it removed ubuntu-desktop and yelp as well as all the other firfox files?

I'm not sure how to get around that since I'm originally from an rpm based distro.

Does dpkg have an equivalent to rpm -e --no-deps firefox?

*edit 

Don't worry after a complete uninstall and re-install its all good.  Ignore me.[/QUOTE]

You also want to reinstall ubuntu-desktop. It's not a package, but a meta-package (it gives no files, rather it dictates what other packages should be installed/upgraded) and will be very useful when you upgrade from Hoary to Breezy.

---

### Post by AndyAWS on 2005-07-26
The metapackages (Ubuntu and Kubuntu Desktop) are nice but they do install things that I don't use, need or want...like the PIM utilities for example. Therefor as soon as I remove any of the unwanted extras, the desktop metapackages are also marked for removal.
Will they really be required to do the upgrade to Breezy?

I thought that when I do the dist-upgrade it would just upgrade all of the packages that I have installed (except for some local installs from unofficial sources).

The only issue that I can see is that I might miss some new package that has been added to the Meta-package

---

### Post by jdong on 2005-07-26
[QUOTE=AndyAWS]The metapackages (Ubuntu and Kubuntu Desktop) are nice but they do install things that I don't use, need or want...like the PIM utilities for example. Therefor as soon as I remove any of the unwanted extras, the desktop metapackages are also marked for removal.
Will they really be required to do the upgrade to Breezy?
[/quote]
Sort of. As you mentioned, you can miss a BUNCH of new packages and miss out on functionality, or not get a full upgrade to base system components if they've been swapped out (i.e. esd vs polypaudio)

---

### Post by AndyAWS on 2005-07-26
Thanks for the info.

No problem then, I'll just reinstall them before the Breezy upgrade, the re-remove any fluff that I don't use.

---

