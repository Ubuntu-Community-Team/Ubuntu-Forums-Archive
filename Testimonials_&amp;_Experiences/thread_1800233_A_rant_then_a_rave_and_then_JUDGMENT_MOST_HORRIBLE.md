---
title: "A rant then a rave and then JUDGMENT MOST HORRIBLE"
date: 2011-07-08
forum: Testimonials &amp; Experiences
---

### Post by dataSpheric on 2011-07-08
Holy cow what a time I've had. Well it started OK, I picked up a quad core, I felt like there might be something better than Mandriva out there, heard about 'buntu for years now, great community and all. So I throw 10.4 on there and things seem pretty happy. I like Gnome but being able to run some KDE stuff like the Quanta web development suite sure is nice. I like Kontact but Evolution seems fine too and the import wasn't exactly like getting teeth pulled. 

We threw our LAMP platforms on it and started tapping away but one day one of these seemingly innocuous software updates brought me into the tortured universe of the NASTY NARWHAL and then life was sheer hell. First thing I noticed when it told me to reboot is THAT IT DIDN'T, I couldn't even get a signal that my monitor recognized and that was sheer hell from Friday afternoon to Monday night before I'd gone in with boot disks, recovered my data, reconstructed my drives, wiped everything, reinstalled to 10.4, reimported all my junk, retuned all my apps and let the damn thing update itself AGAIN. Then I had back what I went to bed with Thursday night.

Now as I assemble the clouds of thunder and lightning to make my official judgment, allow me a word from our sponsors, dataSpheric.com. They do stuff for small business. OK the JUDGMENT is I kinda like 'buntu and 10.4 is a honey for the user. For the admin, well, I just don't trust upgrades anymore. I think I'll put the new Mageia on as a dual boot and see how they compare.

Either way, I'm gonna go ahead and get the t-shirts from both distros for the whole company for our summer party. I guess it will be Penguins vs. Meerkats for volleyball.

So once again the data has the integrity we demand although I'm no longer secure in this implementation of the file system. I really should be able to pull the plug and have my entire desktop session restored upon boot. A buddy is gonna drop by with the new 'driva, the Mageia or something and we'll have a whirl with that.

10.4 is now asking me to do a kernal update. I'm gonna switch off update alerts and just stick with what I'm working on now, it works. This really is a nice user environment, 10.4 is now proving to be the best, the VERY BEST thing I've seen so far for migrating Window$ users to 'nix. And as far as community goes, while you guys aren't as expert as other distribution's followers, one really couldn't ask for more friendly people.

---

### Post by tgalati4 on 2011-07-08
So you performed a distribution upgrade instead of a simple software upgrade?

There's a big difference between:

sudo apt-get update
sudo apt-get upgrade

and 

sudo apt-get update
sudo apt-get dist-upgrade

The latter causes issues.

As you have discovered.

Kernel updates, xorg updates, and cups updates can cause breakage, more so then just application updates.  Kernel updates are helpful to patch security bugs--and they are recommended for production machines.  You just have to have your catcher's mitt on when you install them, because you may get a few curveballs thrown your way.

---

### Post by CharlesA on 2011-07-08
> **tgalati4 said:**
> So you performed a distribution upgrade instead of a simple software upgrade?

There's a big difference between:

sudo apt-get update
sudo apt-get upgrade

and 

sudo apt-get update
sudo apt-get dist-upgrade

The latter causes issues.

As you have discovered.

Kernel updates, xorg updates, and cups updates can cause breakage, more so then just application updates.  Kernel updates are helpful to patch security bugs--and they are recommended for production machines.  You just have to have your catcher's mitt on when you install them, because you may get a few curveballs thrown your way.

Pretty much this whole thing.

I've done apt-get dist-upgrade a few times on my server and had it break stuff, but thankfully the fix is easy in my case.

---

### Post by MartyBuntu on 2011-07-09
> **dataSpheric said:**
> For the admin, well, I just don't trust upgrades anymore.


Do you trust backups? 

...because I don't see any mention of frequent and reliable backups being made and utilised, which is what I would expect in a production environment.

---

### Post by 3rdalbum on 2011-07-11
Ubuntu will never just spontaneously upgrade to a later version of the distribution. It always requires either a sources.list modification involving newer repositories, or the running of the CLI Update Manager with the switch that updates the distribution, or clicking the "Upgrade" button in the GUI Update Manager that upgrades the distribution.

Additionally, Ubuntu 10.04 ships with the setting "Show Long Term Support distribution releases only" active, which would only ask you to upgrade to Ubuntu 12.04, not to 11.04.

So you've either made a mistake somewhere, or purposely updated a production computer to a non-LTS release. Not even the command "sudo apt-get dist-upgrade" will cause a new distribution version to be installed on Ubuntu, unless you've got newer Ubuntu repositories in your sources.list.

---

