---
title: "Xubuntu install offers meaningless suggestion"
date: 2013-08-18
forum: Ubuntu, Linux and OS Chat
---

### Post by bkline on 2013-08-18
When you pop in a DVD burned from an Xubuntu installation ISO you get two buttons, which allow you to choose to try Xubuntu or to install it.  If you click the second button, to install Xubuntu, the installation starts off after asking a couple of questions.  One of the first panels which displays while you're waiting for the installation to run its course suggests that you try using the system you're running to get a feel for the interface, which it says will look very much like the installed system.  Why would it say that if you didn't choose the first button (to run the system from the DVD)?  I think it would give new users a more confident feeling about the system they're installing if their first impression didn't make it look like the folks who created the installation program were asleep. :-)

---

### Post by CharlesA on 2013-08-18
You can still play around in the live environment even after the installation is finished..

---

### Post by Yellow Pasque on 2013-08-18
You should file a bug against ubiquity-slideshow-ubuntu (xubuntu slideshow is included in that package).
@Charles: is that true even if you do a direct install (and don't start the live environment)? I can't remember.

---

### Post by tgalati4 on 2013-08-18
I'm may be mistaken, but the "install" button loads a minimal live environment which reduces the RAM footprint so that the installation has a better chance of success and will install faster.

If you load the full live environment, it has a larger RAM footprint.  You can still install from this environment, but because more RAM is used, any post installation configuration may take longer because it is swapping RAM or competing with the live environment for CPU cycles.  

In an ideal world, you would only have one button--load the Live environment, then if you like it, install from that full, live desktop.  If you don't have a swap partition (created beforehand by a user who knows what he is doing) and are running from a low-RAM (512 MB) system, then the installation could take a while.

So yes, the button description can be confusing, but then for a new user, the entire installation experience is a trip into the unknown.  There are several ways to mess up an installation.  I think the button description is appropriate, but then I've done a few installations and even developers need to take a nap now and then.

---

### Post by bkline on 2013-08-19
> **Temüjin said:**
> You should file a bug against ubiquity-slideshow-ubuntu (xubuntu slideshow is included in that package).

Done (thanks for the suggestion): [https://bugs.launchpad.net/ubuntu/+source/xboard/+bug/1213933](https://bugs.launchpad.net/ubuntu/+source/xboard/+bug/1213933)

---

### Post by bkline on 2013-08-19
> **tgalati4 said:**
> So yes, the button description can be confusing, ....

Sorry if I wasn't clear: it's not the button whose description is confusing, it's the panel which suggests doing something which isn't available (expermimenting with an environment which isn't present - or at least not accessible by any methods I tried).

---

### Post by bkline on 2013-08-19
Just out of curiosity: I noticed that this thread got moved.  Why wouldn't "Installation and Upgrades" be the appropriate location, if we're talking about the installation process?  Thanks!

---

### Post by Yellow Pasque on 2013-08-19
> **bkline said:**
> Done (thanks for the suggestion): [https://bugs.launchpad.net/ubuntu/+source/xboard/+bug/1213933](https://bugs.launchpad.net/ubuntu/+source/xboard/+bug/1213933)

You filed it against xboard (the chess application). :lolflag:

---

### Post by Elfy on 2013-08-19
> **bkline said:**
> Just out of curiosity: I noticed that this thread got moved.  Why wouldn't "Installation and Upgrades" be the appropriate location, if we're talking about the installation process?  Thanks!

That forum is about actual installation and upgrade issues.

You're not talking about the installation process - this bug isn't going to cause issues during installation :)

---

### Post by grahammechanical on 2013-08-19
You can always join a development team and then you too can be someone who is asleep. It is a slideshow advertising the product. The slideshow does not run when we select the TRY option. Which would you prefer? A slideshow? Or just a progress bar that seems like it will never reach the end?

---

### Post by bkline on 2013-08-19
> **Temüjin said:**
> You filed it against xboard (the chess application). :lolflag:

I'm not sure how that happened.  I was viewing a previous bug I had filed (always amusing to see a 5-year-old bug labeled as "New") filed against xboard when I clicked the button to create the new bug report, so the package defaulted to xboard.  I edited the package field, picked the package you suggested, and saved, but the edit of the package field appears to have fallen on the floor.  If I were really motivated, I might file a new report against the Launchpad interface, but I can see attempts to reproduce that behavior creating more of a mess than anyone would want to deal with. :-)

Anyway, thanks for noticing and fixing the package.

---

### Post by Elfy on 2013-08-19
> **grahammechanical said:**
> ... It is a slideshow advertising the product. The slideshow does not run when we select the TRY option....

It does run , just not until you start to install.

---

### Post by bkline on 2013-08-19
> **grahammechanical said:**
> You can always join a development team and then you too can be someone who is asleep.
Thanks, I'm already a member of several development teams, and I try not to sleep on the job too often. :-)
> It is a slideshow advertising the product. The slideshow does not run when we select the TRY option.
The slideshow does run if you choose to install from the environment which is loaded in response to the TRY option.  In that case it actually makes sense to invite the user to play around with the environment, since the environment is in fact available from that path.  
> Which would you prefer? A slideshow? Or just a progress bar that seems like it will never reach the end?
Are those really our only options?  Why not a slideshow which is aware of whether the live environment is actually available?

---

### Post by tgalati4 on 2013-08-19
So, now we need two slideshows, one which runs during a Live Session install and one which runs only during an install.  The one during the install would simply be a progress bar that reminds you not to fall asleep.

---

### Post by zealibib slaughter on 2013-08-19
I suggest a slideshow of penguins wearing funny hats

---

