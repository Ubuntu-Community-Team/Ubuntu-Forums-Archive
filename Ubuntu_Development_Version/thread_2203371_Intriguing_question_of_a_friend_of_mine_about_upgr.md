---
title: "Intriguing question of a friend of mine about upgrade 13.10&gt;14.04 in the midst of U+1"
date: 2014-02-03
forum: Ubuntu Development Version
---

### Post by zika on 2014-02-03
A friend of mine, currently using 13.10 asked me a following question:
*&#8222;Could I, now, today, just change saucy into trusty in */etc/apt/sources.list* and do update/upgrade with all PPA's active (and also with change saucy>trusty done) and be sure that everything is properly upgraded...?&#8220;*
Even though I've walked through transition at the beginning of U+1 not a few times, I'm not quite sure how to answer him now... Most of my transitions were in a &#8222;proper Debian way&#8220; and near or after toolchain so...
Of course, I answered him that PPAs should be turned off during transition (especially xorg-edgers, if that is even necessary in this shortcut case...) but this one is a nice thought-entertainer... Only stumbling block and reason why I write this is &#8222;the midst of U+1&#8220; ...
What does update-manager at this point in U+1 do more than just this (simple) replacement (saucy>{trusty, devel}) and PPAs-turn-off...?

---

### Post by craig10x on 2014-02-03
zika: is he just running 13.10 by itself (what i mean is no other ubuntus)...if so, he probably would get the option on the daily build iso to upgrade (as one of the automatic options)...that is what i used to move from 13.10 to 14.04 development...i just unchecked my ppas before i began (they get removed anyway during the upgrade)...all his data should transfer with the majority of his apps as well (except perhaps for license programs like Chrome and MS Core Fonts)..and all his personal settings should be remembered...

You will recall when i once tried to move into testing by changing the source lists i messed up...but using this upgrade method it does everything automatically for you and correctly! :D
The advantage of doing it from the iso (rather the upgrade manager) is it is a lot faster because the files are right on the iso...
Upgrade does work best if he hasn't made a lot of heavy modifications to he system...i don't and it's worked well for me everytime i did it...

---

### Post by grahammechanical on 2014-02-03
My opinion?

Do not try upgrading from a stable release to a development release by changing the sources lists if the development cycle is more than 6 - 8 weeks old. The download will be very large. This means that the code differences will be very large. This means an increase in risk of something breaking. The risk of breakage increases the further away from the start of the development cycle we get. Simply install a daily image. It is safer.

With PPAs active the sources for those PPAs will also be changed to the development repositories which will not actually exist. For example, has the maintainer created a trusty PPA for that application? If not then there will be errors during the upgrade. Does the saucy version of the application run on the trusty code? There have been times when I have had to remove applications and re-install them from PPAs that are purpose built for that version of Ubuntu.

Update Manager (apt-get/software centre) also has responsibility for conflict management. We see people in other sections of this forum saying they have an error message that amounts to apt-get refusing to install a package because that will require replacing a newer version of a library with an older version of the library and it is not going to be that stupid.

Think also about why we are advised to refuse the offer of a partial upgrade. That offer may make some sense in a stable release but we know it makes no sense with a development version so we ignore it. The one time I tried it I ended up with a broken system. Someone trying what your friend wants to do will surely get a Partial Upgrade offer and it will be a mixture of "this usually happens during the development cycle" and "there is genuine need to fix library mismatches." 

Regards.

---

### Post by zika on 2014-02-03
As You could witness from previous pages of these forums, I'm aware of many (if not all, I might've missed one or two while reading, to be honest...) things You do mention in Your answers... I've just asked (i.e. my friend did) if that would be possible... Surely I would not advise that method as even close to best/safe/anything_similar... I'm not even advising it for the first day of U+1 (remember I've wrote: proper Debian way)... This is/was just a kind of rhetorical question...  Yes/No... ;) Download should not exceed DL of CD, anyway... ;) Etc... My answer was given already... Even about &#8222;partial upgrade&#8220;, somewhere here in a neighborhood of this thread of mine... An answer to question of mine at the end of my post would be even more informative... I'll take a look into a code his evening or later and see... I've just asked for a shortut, just in case if anyone have already looked into the code for himself...

---

### Post by craig10x on 2014-02-03
@grahammechanical: i agree with you that changing source lists at this point in time would be taking a big chance...he would be far safer using the upgrade method like i used...i just did it very recently, and it was very smooth...but i still maintain that if one has the auto option to upgrade on the live iso installer as i did, then that IS the best way to do an upgrade...doing it with update manager would be a second choice but i rate the iso installer upgrade way above it...

---

### Post by zika on 2014-02-03
> **craig10x said:**
> @grahammechanical: i agree with you that changing source lists at this point in time would be taking a big chance...he would be far safer using the upgrade method like i used...i just did it very recently, and it was very smooth...but i still maintain that if one has the auto option to upgrade on the live iso installer as i did, then that IS the best way to do an upgrade...doing it with update manager would be a second choice but i rate the iso installer upgrade way above it...But, I do re-iterate, question was not about the best way of doing anything, just if someone have tried or have insight about what would happened if that scenario (my friend proposed) were entertained...
There are many other threads that do deal with choosing best method and similar stuff...

---

### Post by Mateusz Stachowski on 2014-02-03
I've upgraded to 14.04 by changing sources.list in first week of 2014. I also made sure that PPA's which don't have support for Trusty would remain at Saucy and in gloobus-preview case Raring.

I used Synaptic for installation of the upgrades and everything worked and is still working very well.

There is even someone that upgraded from 13.04 with only a minor problem.

[http://ubuntuforums.org/showthread.php?t=2200121](http://ubuntuforums.org/showthread.php?t=2200121)

---

### Post by zika on 2014-02-03
That's the spirit. Thank You... ;)

---

### Post by philinux on 2014-02-03
I used update-manager -d to upgrade a spare laptop to 14.04. It's currently borked with a black screen at boot. Clean install looks likely on the cards if I cant unbork it.

---

### Post by zika on 2014-02-03
> **philinux said:**
> I used update-manager -d to upgrade a spare laptop to 14.04. It's currently borked with a black screen at boot. Clean install looks likely on the cards if I cant unbork it.Black screen on boot or black screen on DM entrance? Did You try just to boot into tty and fix DM from there? Yes, moderator made even me to go off-topic... ;) As I remember there was a thread about this trouble of Yours, so we could continue there... I'm (almost) sure that that install could be saved with some TLC...

---

### Post by philinux on 2014-02-03
Not off topic as I would not recommend changing sources at this stage. :) As in your OP.

---

### Post by zika on 2014-02-03
> **philinux said:**
> Not off topic as I would not recommend changing sources at this stage. :) As in your OP.OK, that way looking, it is definitely not off-topic... But, You've used ```
update-manager -d
```and, despite that it &#8222;broke&#8220; Your install I could fix Your install, I'm (almost) sure... ;) Who knows, You might've been better with simple change like my friend've suggested... Just teasing, NHF...

---

### Post by craig10x on 2014-02-03
I used the upgrade on the iso installer, and mine didn't break (although i do get the GNU GRUB screen initially when booting up...otherwise everything totally normal)....just saying ;)
I suspect the iso installer upgrade is generally less troublesome then the software updater upgrade...

---

### Post by grahammechanical on 2014-02-03
I think that most questions about upgrading are close to being hypothetical questions. It does not matter what method is chosen, the variety of hardware and the various user modifications that can be done make each upgrade almost individual. "Try it and see" could be a valid response but what works on my system may not work on somebody else's system. Now, add in conditions set down by the user and mix in the fact that the person wants to do this on their only install of Ubuntu and thinks that they can revert back if they do not like what they get and I would say that we have a recipe for a disaster cake.

Regards.

---

### Post by PJs Ronin on 2014-02-03
My chosen upgrade path is to clone my production partition and then in the new partition: ```
sudo sed -i 's/saucy/trusty/g' /etc/apt/sources.list
sudo apt-get update && sudo apt-get dist-upgrade
sudo do-release-upgrade -d
```
which I do/did as soon as the new version becomes available in the repos.   I only have a single ppa (mc4man (sic) to provide scrollbars).   I have not had any problems doing this but later today will try re-cloning my old saucy and do an upgrade using the above method to see if the passage of time introduces problems.

Edit:   I did as described above and all went smoothly.   Large update viz: ```
Reading state information... DoneCalculating upgrade... Done
The following packages will be REMOVED:
  foomatic-filters <snip>
The following NEW packages will be installed:
  bbswitch-dkms cheese <snip>
The following packages will be upgraded:
  account-plugin-google <snip>


**1396 upgraded, 143 newly installed, 8 to remove and 0 not upgraded**.
Need to get 824 MB of archives.
After this operation, 556 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
sure, what the hell!
```

During the install I was warned something about pixbuf which I ignored, and changes to sysctrl.conf which I declined to change as this was modified by me in the past.   My system came up complete with a Win 7 Pro VM and PostgreSQL server.

No substantial issues from what I can see.

---

### Post by zika on 2014-02-04
@PJs_Ronin: Thank You. Essentially the same output was produced at my friend's machine last night... ;) (He has almost as much PPAs as I do...) I've contemplated pap-purge-ing all first but... It was late at night and Daily USB was handy so, as You wrote &#8222;what the hell!&#8220;... Only simple```
 for f in /etc/apt/sources.list.d/*.list; do sudo sed -i 's/deb http/# deb http/g' $f;done
```
Disclaimer (as on any edgers or such PPA ;)) : I of course would not recommend to anybody doing that... Done only for (sort of) testing purposes...
Off-topic: About scrollbars (if I've got it right about what You want about them): There is a switch in dconf-editor: com.canonical.desktop.interface>normal... ;)

---

### Post by PJs Ronin on 2014-02-04
Happy to help Sir.
> **zika said:**
> Off-topic: About scrollbars (if I've got it right about what You want about them): There is a switch in dconf-editor: com.canonical.desktop.interface>normal... ;)
Ty for the dconf-editor switch... you'd be correct in thinking that was the lil sucker.

---

### Post by zika on 2014-04-14
For the first time in long time I'm in U+1 at the very end of the cycle, due to more important jobs that requested stable machine...
Yes, I've done, last few hours the way I've proposed at the very beginning of this thread: keeping all 40+ repositories alive and just changing saucy into trusty in each and every .list file, including sources.list... Few bumps on the road and for the first time patient me made this possible... Now i can change my profile to 14.04... ;) Successfully rebooted and only ubuntu-desktop on hold pending some work in some ppas... ;) MPV and few other packages were removed but I can live happily without them pending resolution of generation of some support packages...

---

