---
title: "Football Manager 2009"
date: 2009-02-16
forum: Wine
---

### Post by cjslim on 2009-02-16
HI guys;

You have so far aided me in solving all of my problems but here's the big one..
I want to install Football Manager 2009 on Ubuntu..
I installed Wine, Installed winetricks, Installed recommended packages for wintricks, Installed java in wine and tried installing..

No luck installing from CD so i install steam (From CD) and download from my a/c.

Sweet all downloads, I get prompted (as I am sure you are all aware) with an activation box that has no <BACK><CANCEL><NEXT> buttons..

No i'm stumped...I been searchin the Internet for a way to do this for days but most blogs/articles offer advice on installing and end with "I havent got it working like this yet but i know someone who has" ... or all of the methods / posts are outdated..

I am starting this post with the aim of bringing together an updated method, working method preferably, of installing AND running Football Manager 2009 on Ubuntu 8.10..

All and any help and advice appreciated..

Start scratchin' those heads...

Cheers..

---

### Post by bmitov on 2009-02-16
I think you have to install ie6 using winetricks. Though I didn't install using steam cause I dled it off the internet.

As for myself, I can't get past the message telling me "Cannot run game: Failed to set up graphics system."

---

### Post by cjslim on 2009-02-17
All installed, Now I join the unhappy army of "Cannot Run Game Failed To Load Graphics"...Man am i gettin pissed with this :S

OK!! Got it installed and running, LArge database, running ok, only minor groan is the fonts are slightly distorted..

Any ideas?

Oh, I followed this guide, to the work and then patched to 9.1, bypassed activation (seems i own the bl00dy game and have activated already) and it fired straight up..

[http://www.fmtux.net/index.php?PHPSESSID=feec1dbjjkhg8ev2b666svjn35&topic=67.msg834#msg834](http://www.fmtux.net/index.php?PHPSESSID=feec1dbjjkhg8ev2b666svjn35&topic=67.msg834#msg834)

It DOES work, you need to uninstall WINE and delete the /.wine & /.winetricks (or winetrickscache cant remember the name, basically all wine folders, if you can't see them make sure you view hidden files) clean up your system (sudo apt-get autoclean) get yourself an orphan package remover, GTK i went for.

Clean system, and follow the guide on the above link... Patch to 9.1 when the install completes and bypass activation..Oh and I could see all of the install screens and I didnt need to install java...

---

### Post by andy07070 on 2009-04-13
> **bmitov said:**
> I think you have to install ie6 using winetricks. Though I didn't install using steam cause I dled it off the internet.

As for myself, I can't get past the message telling me "Cannot run game: Failed to set up graphics system."

Try installing microsoft sdk, worked for me

[http://www.microsoft.com/downloads/thankyou.aspx?familyId=5493f76a-6d37-478d-ba17-28b1cca4865a&displayLang=en](http://www.microsoft.com/downloads/thankyou.aspx?familyId=5493f76a-6d37-478d-ba17-28b1cca4865a&displayLang=en)

---

### Post by cistun on 2009-05-11
> **cjslim said:**
> HI guys;

You have so far aided me in solving all of my problems but here's the big one..
I want to install Football Manager 2009 on Ubuntu..
I installed Wine, Installed winetricks, Installed recommended packages for wintricks, Installed java in wine and tried installing..

No luck installing from CD so i install steam (From CD) and download from my a/c.

Sweet all downloads, I get prompted (as I am sure you are all aware) with an activation box that has no <BACK><CANCEL><NEXT> buttons..

No i'm stumped...I been searchin the Internet for a way to do this for days but most blogs/articles offer advice on installing and end with "I havent got it working like this yet but i know someone who has" ... or all of the methods / posts are outdated..

I am starting this post with the aim of bringing together an updated method, working method preferably, of installing AND running Football Manager 2009 on Ubuntu 8.10..

All and any help and advice appreciated..

Start scratchin' those heads...

Cheers..

try that buddy it worked for me also no steam needed

install wine and wine tricks then install directx9.0,msmxl3 and java6.11.run setup advanced install dont install java and directx then make the 9.0.1 patch.may be there will be a font problem if it happens go to wine->conf. wine->graphics->screen resolution and increase the dpi.

---

