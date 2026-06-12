---
title: "ubuntu sucks"
date: 2007-05-09
forum: Testimonials &amp; Experiences
---

### Post by stevennp on 2007-05-09
Usually use Mandriva and thought i'd give Ubuntu a try
Using Ubuntu v 7.04.  Clean install
System-admin-users and groups is missing
tried system-preferences-main menu and can't check the users and groups box.
can't login as root
can't create password using su passwrd root / sudo passwrd root
can't install any deb packages (sudo won't let me)
can't do s#*t.
Ubuntu sucks!!!

---

### Post by AAM on 2007-05-09
go back to mandriva - there's nothing wrong with it.

---

### Post by hyper_ch on 2007-05-09
Good luck with Mandriva.

---

### Post by Terl on 2007-05-09
You sound fairly unwilling to learn but....

You can activate root if you need it.  It just takes a quick search here or on the documents page.

You do not need root however as you can do everything you need with sudo and the password you created at the install.

You should know that each distro is different in how it is set up and you should be ready for changes.  Bottom line is, Ubuntu does not suck - you just don't like it.  If you don't like it, move back to Mandriva.  That is the nice thing about Linux, there is a flavor for everyone. :)

---

### Post by ironfistchamp on 2007-05-09
Ubuntu doesn't suck it's just different from what you know. 

Ok a couple of these things I might be able to help with.

When you have done a clean install the sudo password should be the same as your user password. Root isn't enabled by default but you can enable it by typing 

```


sudo passwd


```

check this post: [http://www.ubuntuforums.org/showthread.php?t=31053](http://www.ubuntuforums.org/showthread.php?t=31053)

Now to login with the GUI I think you have to change a login setting (under the login menu) and check allow admin/root (can't remember the exact wording.

If I have told you what you already know maybe you can be a bit more specific with your problems. i.e. the output you get when you try to do these things.


HTH

Ironfistchamp

EDIT: gah Terl beat me to it :p

---

### Post by KIAaze on 2007-05-09
It's sudo "_passwd_", not "sudo _passwrd_".

But I suppose this was just a typo here on the forum.

You seem to really have a problem with sudo permissions. That's really weird. O.o

Is it that sudo doesn't accept your password (wouldn't make sense, since you logged in with it right?) or is it really a permission problem?

What's in your "/etc/sudoers" file?

edit: Or you didn't enter your user password, in which case the above post applies...

---

### Post by alienexplorers on 2007-05-09
If  you hate Ubuntu that much go back to Mandriva.  No big loss to our fine family.

---

### Post by LaRoza on 2007-05-09
If you want a specific problem solved, could you be more specific, i.e. what did you do, what errors you received, what you were trying to do?

What is Mandriva like? I am interested in using it.

---

### Post by kerry_s on 2007-05-09
> **stevennp said:**
> Usually use Mandriva and thought i'd give Ubuntu a try
Using Ubuntu v 7.04.  Clean install
System-admin-users and groups is missing
tried system-preferences-main menu and can't check the users and groups box.
can't login as root
can't create password using su passwrd root / sudo passwrd root
can't install any deb packages (sudo won't let me)
can't do s#*t.
Ubuntu sucks!!!

I would say mandriva has babied to way to much.
it's just users and groups under adminstration <-like that's not obvious
There is no root set up.
It's passwd, sudo passwd root <- check your commands
Packages, you just double click on<- so simple a monkey can do it
I agree you can't do **** right
On occasion i say this sucks, but it's usually something stupid i did.

---

### Post by PartisanEntity on 2007-05-09
Sounds like someone installed Ubuntu without doing research to see how it differs from other distributions he/she/it has used. Then you blame Ubuntu?? Hmm...

---

### Post by arkangel on 2007-05-09
These are minor problems, specially for someone who loves Mandriva ,  if you dont like it is fine, no need to complain here

---

### Post by starcraft.man on 2007-05-09
> **PartisanEntity said:**
> Sounds like someone installed Ubuntu without doing research to see how it differs from other distributions he/she/it has used. Then you blame Ubuntu?? Hmm...

You know, a lot of people seem to be doing this... it's like they think Ubuntu will be exactly like X, where x is their old OS... even windows folk. They don't even bother looking at a wiki or anything...Why does everyone believe this inexplicable myth?

As for stevenn bye bye, have fun with mandriva and in future post where it belongs... in testimonials. If you come back, have more patience or don't bother... Ubuntu doesn't just clone your old os, contrary it seems to popular belief.

---

### Post by silent1643 on 2007-05-09
ubuntu has come a long way since its start as outlined in[ full circle magazine]("http://fullcirclemagazine.org/index.php?PHPSESSID=ctetj1j4m9s2eftah0um74vis1&action=tpmod;dl").. each release has gotten better and better... sorry you dont like FF, but you need to at least be pleasant about it and give ubuntu props for what they have achieved even if its not your cup of tea.

---

### Post by Lord Illidan on 2007-05-09
> Usually use Mandriva and thought i'd give Ubuntu a try
Using Ubuntu v 7.04.  Clean install
System-admin-users and groups is missing
tried system-preferences-main menu and can't check the users and groups box.
can't login as root
can't create password using su passwrd root / sudo passwrd root
can't install any deb packages (sudo won't let me)
can't do s#*t.
Ubuntu sucks!!!

You either installed Ubuntu wrongly, or have the wrong media or something.

You can install deb packages with sudo very well, and synaptic.

sudo dpkg -i <packagename>.deb will install a .deb package. Type in your password, and press enter.

There is synaptic and Add/Remove packages.

To make a root password, sudo passwd root

To login as root, search the forums, etc, but it's not recommended, you can do everything with sudo.

---

### Post by Sef on 2007-05-09
> sudo dpkg -i <packagename>.deb will install a .deb package. Type in your password, and press enter.

Even simpler is clicking on the deb package, and it will open automatically.

Read [Root/Sudo]("https://help.ubuntu.com/community/RootSudo") for as to why root is disabled in Ubuntu and why it is safer.

---

### Post by nowatkins on 2007-05-09
UBU is excellent. In my opinion. How can you complain about something that is free? Same as if you don't vote, you can't complain. Instead of putting it down generically. Be more specific. There are more people willing to help you here than there are people willing to agree with you. So help us help you.

---

### Post by aysiu on 2007-05-09
Well, this is more of a bad experience than a support request, so I've moved it to a more appropriate forum.

---

### Post by compmodder26 on 2007-05-09
Seems like a troll to me.  Let's all just obey the golden rule: "Don't Feed The Trolls".

---

### Post by hyper_ch on 2007-05-09
That's why I said "Good luck with Mandriva" :)

---

### Post by stevennp on 2007-05-10
After browsing the forums for a while I suddenly realised that half my menus were missing.  Turns out that somthing must have gone wrong with the installation!!!  Everything works now that i've reinstalled it and I think it's far more easy to use than Mandriva (almost as easy than windows!)

UBUNTU ROCKS!!!

---

### Post by arkangel on 2007-05-11
Cool  that  worked this time 

maybe you are considering  asking one forum staff member to change the title ...

---

### Post by stevennp on 2007-05-11
Could do but I quite like the title.  Gets peoples attention!:)

---

### Post by slimdog360 on 2007-05-11
yep I agree, Ubuntu sucks.

---

### Post by articpenguin on 2008-08-11
bump

---

### Post by karellen on 2008-08-11
if you're satisfied with Mandriva, stick to it. as long there's a Linux distro, it doesn't really matter what distro you're using

---

### Post by Methuselah on 2008-08-11
> **articpenguin said:**
> bump

May I ask why.
This was from over a year ago.

---

### Post by Canis familiaris on 2008-08-11
> **methuselah said:**
> may i ask why.
This was from over a year ago.

+1

---

### Post by vikramaditya on 2008-08-11
ubuntu doesn't suck.  it just has to operate in a vacuum.

---

