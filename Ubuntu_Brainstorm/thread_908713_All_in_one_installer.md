---
title: "All in one installer"
date: 2008-09-02
forum: Ubuntu Brainstorm
---

### Post by rossjman1 on 2008-09-02
Why not create an all in one install cd that can install Ubuntu (Gnome), Kubuntu (KDE), Xubuntu (XFCE), Fluxbuntu, etc. This should be easy. Just include the base system on the cd along with X and a custom install application that would allow users to pick which desktop environment or edition of Ubuntu to install (screenshots could be used to show the difference to users).

---

### Post by Bios Element on 2008-09-02
Probably because it'd be overly confusing and there is no way it'd fit on a CD. So either a DVD Or Several CD's.

---

### Post by rossjman1 on 2008-09-02
The base system will be the only thing on the cd, everything else will be apt-getted or removed depending on what the user chooses.

---

### Post by smartboyathome on 2008-09-02
rossjman1: That wouldn't work. There are still many wireless cards which don't work with Ubuntu (Broadcom anyone?), and this would basically render the install useless. Also, the LiveCD is supposed to be able to test the distro, this would take that away by having something else be installed. Not to mention it would make it take a lot longer to be installed, since it has to be gotten from the internet.

---

### Post by rossjman1 on 2008-09-02
The iso has to be downloaded from the internet so I don't see your point. Also, I never said anything about getting rid of the disks we have now.

---

### Post by olskar on 2008-09-03
You mean like opensuse is doing it kind of?

[http://blog.markojung.net/wp-content/uploads/2008/06/opensuse-install8.png](http://blog.markojung.net/wp-content/uploads/2008/06/opensuse-install8.png)

---

### Post by snowpine on 2008-09-03
> **rossjman1 said:**
> Why not create an all in one install cd that can install Ubuntu (Gnome), Kubuntu (KDE), Xubuntu (XFCE), Fluxbuntu, etc. This should be easy. Just include the base system on the cd along with X and a custom install application that would allow users to pick which desktop environment or edition of Ubuntu to install (screenshots could be used to show the difference to users).

This already exists--it is called the Minimal Install CD (mini.iso) and it is a 10mb cd that installs the command line, then you can 'sudo apt-get install ubuntu-desktop' (for example) to install your desktop environment.

---

### Post by rossjman1 on 2008-09-03
> **olskar said:**
> You mean like opensuse is doing it kind of?

[http://blog.markojung.net/wp-content/uploads/2008/06/opensuse-install8.png](http://blog.markojung.net/wp-content/uploads/2008/06/opensuse-install8.png)

Exactly.

---

### Post by smartboyathome on 2008-09-03
> **rossjman1 said:**
> The iso has to be downloaded from the internet so I don't see your point. Also, I never said anything about getting rid of the disks we have now.

> **rossjman1 said:**
> Exactly.

That would require Ubuntu to move to DVD, as you can't compress all 6 GBs of data into the size of a CD (each CD holds 2-3GBs each). Since DVD burners are still not common, I don't see this happening any time soon. Could be a good community project though. ;)

---

### Post by irrdev on 2008-09-04
> **smartboyathome said:**
> That would require Ubuntu to move to DVD, as you can't compress all 6 GBs of data into the size of a CD (each CD holds 2-3GBs each). Since DVD burners are still not common, I don't see this happening any time soon. Could be a good community project though. ;)

In reference to DVD burners not being common, I have to entirely disagree. I went to Best Buy last week, and *every single laptop and desktop in the store had a CD/DVD-RW burner installed*. Sure, computers predating 2007 probably won't have DVD support, but all new computers have this. Nowadays, the question isn't whether a computer has a DVD burner, but rather whether it has a BlueRay reader! :)

Anyway, my point here is that DVDs have a strong future as a replacement to CD-ROMs, and I think that offering both LiveCDs and full-blown DVDs like opensSUSE does is a very smart option. Isn't a major philosophy behind linux to give users a choice? Imagine the possibilities a full-blown DVD could give: businesses and schools could install Ubuntu/Kubuntu/Xubuntu throughout the workplace without having to burn multiple LiveCDs; home computer users would love the chance to experiment with different desktop environments. 

I think this is a very good idea. I should point out that [this idea has already been placed in Ubuntu Brainstorm]("http://brainstorm.ubuntu.com/idea/188/"), as well as [on Launchpad]("https://blueprints.launchpad.net/ubuntu/+spec/multi-desktop-install-dvd?"). I truly hope that something will result out of this! :wink:

---

### Post by smartboyathome on 2008-09-05
> **irrdev said:**
> In reference to DVD burners not being common, I have to entirely disagree. I went to Best Buy last week, and *every single laptop and desktop in the store had a CD/DVD-RW burner installed*. Sure, computers predating 2007 probably won't have DVD support, but all new computers have this. Nowadays, the question isn't whether a computer has a DVD burner, but rather whether it has a BlueRay reader! :)

Anyway, my point here is that DVDs have a strong future as a replacement to CD-ROMs, and I think that offering both LiveCDs and full-blown DVDs like opensSUSE does is a very smart option. Isn't a major philosophy behind linux to give users a choice? Imagine the possibilities a full-blown DVD could give: businesses and schools could install Ubuntu/Kubuntu/Xubuntu throughout the workplace without having to burn multiple LiveCDs; home computer users would love the chance to experiment with different desktop environments. 

I think this is a very good idea. I should point out that [this idea has already been placed in Ubuntu Brainstorm]("http://brainstorm.ubuntu.com/idea/188/"), as well as [on Launchpad]("https://blueprints.launchpad.net/ubuntu/+spec/multi-desktop-install-dvd?"). I truly hope that something will result out of this! :wink:

DVD Burners are widely available in the U.S., yes, but what about other countries? There are still many countries where CD burners are included in the computers. Unless you have a computer which is a year old or less, you most likely don't have a DVD burner in my experience (some do, but the ones I saw were more expensive).

---

### Post by rossjman1 on 2008-09-05
Well, the idea that I had was basically a base net install cd. The cd should come with the base system along with X and a custom install program. The graphical program would be able to connect to the internet and apt-get the DE behind the scenes as not to confuse the user. Of course, the internet may not work on all computers, but make it clear on the download page that the installer will require an Internet connection to work.
Of course this solution wont be adequate for all users. Since this cd would not be a live cd, users will not be able to test the hardware that way. Maybe include a quick hardware scanner that would cross-reference some database and output which devices will work and how well before the install starts? This type of installer would be usefull to those of us who would like to install Ubuntu on several computers (but use different DEs).

---

### Post by irrdev on 2008-09-06
> **smartboyathome said:**
> DVD Burners are widely available in the U.S., yes, but what about other countries? There are still many countries where CD burners are included in the computers. Unless you have a computer which is a year old or less, you most likely don't have a DVD burner in my experience (some do, but the ones I saw were more expensive).
That's true. Canada and most European countries offer the same new computer/hardware setups with CD/DVD-RW burners, however. I'd say that *at least* 50% of Ubuntu's userbase falls into these countries. I am not suggesting that a DVD replace the LiveCD, but I do think there is enough demand for a full installation DVD to be fully supported. I don't imagine a lot of effort would be required to do this - a new and flexible DVD installer and more included packages by default. I understand that a complete and flexible DVD installation would be unable to automatically upgrade Ubuntu versions, but I prefer to do fresh installs every 6 months anyway.

---

### Post by smartboyathome on 2008-09-06
> **rossjman1 said:**
> Well, the idea that I had was basically a base net install cd. The cd should come with the base system along with X and a custom install program. The graphical program would be able to connect to the internet and apt-get the DE behind the scenes as not to confuse the user. Of course, the internet may not work on all computers, but make it clear on the download page that the installer will require an Internet connection to work.

The other flaw is that, especially in the U.S., internet isn't especially fast, so getting the packages needed to install from the internet will take _much_ longer than getting a LiveCD to download (since the LiveCD is more compacted). You already have the net CD (mini CD) to install from the net, though, so you could always to that. ;)

> **rossjman1 said:**
> Of course this solution wont be adequate for all users. Since this cd would not be a live cd, users will not be able to test the hardware that way. Maybe include a quick hardware scanner that would cross-reference some database and output which devices will work and how well before the install starts? This type of installer would be usefull to those of us who would like to install Ubuntu on several computers (but use different DEs).

This can be pretty inaccurate, especially with new releases. There could be hardware which wasn't tested during development, and which is thought to work but it didn't. Also, as stated above, you CAN use the mini/net CD to install different DEs on different comps from one CD.

> **irrdev said:**
> That's true. Canada and most European countries offer the same new computer/hardware setups with CD/DVD-RW burners, however. I'd say that *at least* 50% of Ubuntu's userbase falls into these countries. I am not suggesting that a DVD replace the LiveCD, but I do think there is enough demand for a full installation DVD to be fully supported. I don't imagine a lot of effort would be required to do this - a new and flexible DVD installer and more included packages by default. I understand that a complete and flexible DVD installation would be unable to automatically upgrade Ubuntu versions, but I prefer to do fresh installs every 6 months anyway.

You'd be surprised then to find out how many people use Ubuntu and are in the East Asian companies like India. You could always try this yourself, but I guarentee it is anything but easy (I tried, I couldn't get the 3 CDs to combine unless I used them all on the same install).

---

