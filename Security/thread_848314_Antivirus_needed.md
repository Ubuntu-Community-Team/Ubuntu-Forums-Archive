---
title: "Antivirus needed?"
date: 2008-07-03
forum: Security
---

### Post by Jack.Straw on 2008-07-03
Hello.  I'm creating a custom Ubuntu for use in our company's retail showroom computers.  The main program they use for sales is a very old dos-based program, but it runs fine in wine.  However, it's having wine installed that worries me.  Can windows viruses run through wine?  Do i need ClamAV or some other antivirus to be secure?

---

### Post by HalPomeranz on 2008-07-03
I won't say "impossible" here because I'm sure somebody could whip up a proof of concept just to prove me wrong, but it would at least be VERY DIFFICULT for a Windows virus to run under Wine.  I wouldn't worry about it.

---

### Post by Kevbert on 2008-07-03
Somebody here.  Wine maybe. Dosbox definitely.  May cause a problem if you have a dual boot system with a version of Windows.  In theory you could send a virus in an email attachment.  I've so far had three DOS viruses on my Ubuntu system.  All were very old and ClamAV found and removed them.  These viruses will have no effect on the Linux side of things.   How to install ClamAV is [[COLOR="Red"]here[/COLOR]]("http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.htmlhttp://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html").

---

### Post by hyper_ch on 2008-07-03
there was an experiment a little while ago.... only one virus managed to do something in wine and tht was just using cpu.... easily killed with ^c

if you google for it I'm sure you can find it.

---

### Post by jnw222 on 2008-07-03
renember ubuntu=happy with no viruses
windows-oses for viruses to explode

we are running ubuntu which even if a virus gets in it can not spread

---

### Post by Jack.Straw on 2008-07-04
Cool.. thanks guys.  Sounds like i should go ahead and put ClamAV on the CD so our employees can't pass email viruses on to our windows using customers.  

Thanks for the help!
-Jack

---

### Post by SkonesMickLoud on 2008-07-04
> **jnw222 said:**
> we are running ubuntu which even if a virus gets in it can not spread

That's not true at all.

Any infected file can easily be passed to a Windows user through e-mail.  It's wise, and it wouldn't hurt, to run ClamAV and set it to run a system scan every once n a while.

---

### Post by hyper_ch on 2008-07-04
it cannot spread itself just like that through the whole OS... I think that's what he meant...

---

### Post by kevdog on 2008-07-04
Id like a good clamav tutorial.  Ive never run an antivirus program in linux however I'm always willing to learn.  Please post either a link or tutorial if you get it working :)

---

### Post by Master Chief on 2008-07-04
ClamAV is handy for downloaded files, but other than that pretty useless on Ubuntu if you don't have e-mail services running. Eh, you aren't using the root account now do you?

Also, can't that "very old DOS" program be re-written to something more up to date?

See also: [http://www.clamav.net/](http://www.clamav.net/)

---

### Post by Kevbert on 2008-07-04
> **kevdog said:**
> Id like a good clamav tutorial.  Ive never run an antivirus program in linux however I'm always willing to learn.  Please post either a link or tutorial if you get it working :)

Have a look at [[COLOR="Lime"]this[/COLOR]]("http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html").
IMHO ClamAV is only good for finding DOS/Windows viruses and not linux viruses.  To update signatures you need to go to terminal and type ```
sudo clamtk
``` and then go to the ClamAV help/update signatures menu item.  I saw somewhere that there was supposed to be a bounty for anyone finding a linux virus in the wild (as they are very, very rare).

---

### Post by kevdog on 2008-07-04
Anything better -- that tutorial was a little bit sketchy.

---

### Post by Sef on 2008-07-05
> there was an experiment a little while ago.... only one virus managed to do something in wine and tht was just using cpu.... easily killed with ^c

if you google for it I'm sure you can find it.

[Running Window Viruses with WINE]("http://www.linux.com/articles/42031")

---

### Post by Jack.Straw on 2008-07-06
> **Master Chief said:**
> Also, can't that "very old DOS" program be re-written to something more up to date?

Actually, it's a huge commercial program.  Current versions would cost us around $300,000 and wouldn't be as customizable.  Back in the day when our company first got the program the software company actually supplied the source code so we could edit things to our needs, which of course is unheard of today.  I have a feeling we'll be using this software for quite a while still...

---

