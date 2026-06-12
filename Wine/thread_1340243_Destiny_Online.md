---
title: "Destiny Online"
date: 2009-11-28
forum: Wine
---

### Post by zaini118 on 2009-11-28
Hi.

I've been trying to play this online game: Destiny Online in Karmic by using Wine.
I've checked at the [Wine Application Database]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=9938") and notice that the game (Destiny Online) is playable by using Wine (it got the Gold Rating).

But I dunno where I went wrong 'cuz I still can't seems to play this game in my ubuntu.
I hope you guys can help me in this.

Many thanks.

---

### Post by beastrace91 on 2009-11-28
What Wine version are you using? (If you are unsure run **wine --version** in terminal to display it)

I'm betting you have the older ("stable") Wine release installed (1.0.1). If this is the case upgrade to the latest "beta" package. 

Also are you using Ubuntu 32bit or 64bit, what video card do you have, and what driver version do you have installed for your video card?

Regards,
~Jeff

---

### Post by Psumi on 2009-11-28
> **zaini118 said:**
> Hi.

I've been trying to play this online game: Destiny Online in Karmic by using Wine.
I've checked at the [Wine Application Database]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=9938") and notice that the game (Destiny Online) is playable by using Wine (it got the Gold Rating).

But I dunno where I went wrong 'cuz I still can't seems to play this game in my ubuntu.
I hope you guys can help me in this.

Many thanks.

Sadly, most tests are just copied installations from windows machines. Wine tests in the app DB no longer mean anything because people just copy over successful installs from windows.

How do I know this?

Flash CS3 gets a gold/platinum rating, when it cannot even install in Wine.

---

### Post by beastrace91 on 2009-11-28
> **Psumi said:**
> Sadly, most tests are just copied installations from windows machines. Wine tests in the app DB no longer mean anything because people just copy over successful installs from windows.

How do I know this?

Flash CS3 gets a gold/platinum rating, when it cannot even install in Wine.

Borderline spam IMO - you didn't really contribute anything useful to the topic at hand.

That being said I just took a look at the AppDB page you linked to in your first post and noticed this: > What works
Can be installed but will not run, so what i do is installed the older version and then manually download the patch to 1.0.2.0 

What does not
version 1.0.2.0 full install cannot work. when run you get "warning: Trying to create a socket of type SOCK_RAW, this will fail unless you have special permissions

Did you try installing the older version first and then manually patching it as this user said worked for them?

Regards,
~Jeff

---

### Post by zaini118 on 2009-11-28
_**@[beastrace91]("http://ubuntuforums.org/member.php?u=341545"),**_

My Wine version is (as u guested ;p), the stable 1.0.1.
I already upgraded my Wine to the latest beta version (1.1.31) but the problem still arises.
The game did load, but when I click 'Enter' (indicating entering one of the game server), the game just seems to have vanished.

> **beastrace91 said:**
> Also are you using Ubuntu 32bit or 64bit, what video card do you have, and what driver version do you have installed for your video card?

For these, I can't be so sure but I think these're the details:
- Ubuntu 32bit
- Intel GMA 4500MHD 

I'm using Acer Aspire 4736 btw.

> **beastrace91 said:**
> Did you try installing the older version first and then manually patching it as this user said worked for them?

That's the thing. I'm aware of the said method but I cannot get a hold of the older installation file. I already emailed the admin team but still no reponse. 
I just need to keep emailing them then ;p



_**@[Psumi]("http://ubuntuforums.org/member.php?u=959444"),**_
I somehow kinda have that feeling too the first time I read 'bout Wine, but the thing is, the game did load (I mean the welcoming window and all), but when I select my server option, it just vanish.
It suppose to come back again with the login window.


ps: Thanks for you guy's quick reply ^^

---

