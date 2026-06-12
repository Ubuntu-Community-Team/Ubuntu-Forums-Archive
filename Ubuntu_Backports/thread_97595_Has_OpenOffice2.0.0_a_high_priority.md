---
title: "Has OpenOffice2.0.0 a high priority ?"
date: 2005-12-01
forum: Ubuntu Backports
---

### Post by tassou on 2005-12-01
Hi there,
first of all I apreciate the great and reliable work done on backporting.
I am a bit confused with the backports policy :
* I do understand that being a new version, firefox 1.5 can not be incorporated instead of it's previous version, because dependancies have changed and so on.
* But : OpenOffice 2 stable should not differ from the beta (and buggy) version shiped with Breezy. I mean it should be straightforward to replace current buggy version with the stable release, with no modification in the packaging management.

It seems to be a high priority for many end users and I wonder why this work has not been not yet :rolleyes: 
Thanks in advance to enlighten me

Paul

---

### Post by `GooZ´ on 2005-12-01
you can find the 2.O version by adding these lines to your /etc/apt/sources.list
#OpenOffice 2.0 final, not beta like ubuntu repos
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

---

### Post by tassou on 2005-12-01
yes I know that. There are plenty of way to install the stable version.
But, first, none of them suit the neebie. Even accumulating unofficial repositories is a threat for packages database integrity.
My question is : Why isn't it in official repositories, or at least in backports repositories ? It is the same *major version* as the one shipped by default with breezy, that means it is exactly the same with bugfixes, so we are in the case in wich  even official repositories should be updated. And at least backports.
So ... why isn't it in yet ? Is there a good reason for that ?

Cheers


paul

---

### Post by poofyhairguy on 2005-12-01
I have no say, but I think waiting for the .1 release might me a good idea.

---

### Post by abandoned_hussam on 2005-12-10
I'm currently running 1.9.129 like many people.
2.0.1 should be out soon. Can somebody from the backports team please tell us if 2.0.1 could be backported when it hits dapper? I'm sure the whole (k)(X)Ubuntu community would appreciate an answer for this.

---

### Post by jdong on 2005-12-12
When a stable 2.0x hits Dapper, sure, I'll take a look at it for backporting.

---

### Post by abandoned_hussam on 2005-12-15
[QUOTE=jdong]When a stable 2.0x hits Dapper, sure, I'll take a look at it for backporting.[/QUOTE]
Ok, thanks for the answer. :)

---

### Post by GothicX on 2005-12-20
Check it there =)

[http://mirrors.isc.org/pub/openoffice/stable/2.0.1/](http://mirrors.isc.org/pub/openoffice/stable/2.0.1/)

Backport it !!! :-)

---

### Post by jdong on 2005-12-20
OOo 2.0.1x from Dapper no longer compile cleanly under Breezy. I'm told this is due to yet another GCC Java transition in Dapper.

For now, we are going to have to rely on ~doko to make his packages....


P.S. politeness would be well appreciated. I'm a volunteer, after all :)

---

### Post by jdong on 2005-12-20
UPDATE: I've pinpointed the location of the issue in the 50MB build log :)

Now, to  contact the Ubuntu dev on fixes....

---

### Post by jdong on 2005-12-21
I spoke with doko about this, and he says that official breezy-updates for 2.0.1 are planned, if all goes well. I'll keep everyone updated on that!

---

### Post by MichaëlVD on 2005-12-21
that's great news: every small openoffice improvement makes a big difference for me; it's the program I spent most of my Ubuntu time with... Thanks!

---

### Post by abandoned_hussam on 2005-12-22
[QUOTE=jdong]I spoke with doko about this, and he says that official breezy-updates for 2.0.1 are planned, if all goes well. I'll keep everyone updated on that![/QUOTE]
Wow, if that does happen, it'll be the best christmas present ever. :)

---

### Post by towsonu2003 on 2005-12-22
[QUOTE=jdong]I spoke with doko about this, and he says that official breezy-updates for 2.0.1 are planned, if all goes well. I'll keep everyone updated on that![/QUOTE]
so great to hear (although I have dial up)

---

### Post by at2000 on 2005-12-22
Just FYI, 2.0.1-0ubuntu1 has landed dapper.

Will we see it in breezy-updates or breezy-backports soon?

---

### Post by jdong on 2005-12-22
This will most likely be done by breezy-updates, and Backports will only be considered if something fails in the preferred path. There are numerous source changes that'd be easier to do in breezy-updates than Dapper (patch branching and build dependencies)

---

### Post by abandoned_hussam on 2005-12-28
Jdong, any update on OO.o 2.0.1 for breezy-updates?

---

### Post by MichaëlVD on 2005-12-31
I read on the oooforum.org forums that 2.0.1 solves some of the numbering problems OOo has... that would be great... Still no news about the update? I guess I'll have to wait until next year! ;-)

---

### Post by jdong on 2005-12-31
Because of the high quality standard for breezy-updates, this is going to take a while to do. Please be patient. Ask doko or mdz about review progress, since I am not the one responsible for breezy-updates (and they'll have more accurate answers than me)

---

### Post by abandoned_hussam on 2005-12-31
Jdong, thanks for keeping us updated on this one. 
How may we contact doko or mdz? Maybe we can send them an email about this next week after the new year holidays are over.

---

### Post by jdong on 2005-12-31
Asking about it on #ubuntu-devel/freenode would probably be your best bet.

---

### Post by WayneSchuller on 2006-01-02
2 comments:

1. I've just discovered backports. I kept hearing it mentioned but it felt like a secret cult. Finally I found this part of the forums and the HOWTO. 
This is one of the most important ubuntu features because everyone loves having software easily updated.

2. I would love to see the ooo 2.0.1 backport.... Just adding my moral support!!

---

### Post by jeremy on 2006-01-07
I just got doko's Oo.org 2.0.1!
Many thanks to doko, thanks.

---

### Post by jdong on 2006-01-07
2.0.1. will not build cleanly in Breezy due to Java changes... too many for me to track now. Plus, with doko's repository, there's little motivation left for him to modify Dapper sources to compile under Breezy.

As a result, I'm recommending for everyone seeking OOo 2.0.1 to use Doko's repository.

---

### Post by abandoned_hussam on 2006-01-08
Jdong, why don't they just move doko's 2.0.1 builds to breezy-updates?

Edit:. 
Ok, I installed doko's OpenOffice.org 2.0.1 and it's working so far.

---

### Post by sdavy on 2006-01-09
Hello everybody,

and happy new year!

I've installed OOo 2.0.1 from doko's repository, and everything is fine except one thing: I don't have my templates  anymore. And when I create a new template, I can not recover it also. My templates are placed under ~/.openoffice.org2/user/template/, and I don't have any error message, even if run oofromtemplate2 from the command line.

---

### Post by ecastro on 2006-01-10
Hi,
I have installed OOo 2.0.1 from doko's repository too.
I understand the work involved in repackaging it (and adding new things, like the  KDE support, not in OOo oficial release). And I am grateful to doko and others, since OOo is an essential piece of my desktop. Updates to 2.0.1 are a must, since OOo 2.0 (either .129 or 2.0 final) is severely broken, with major regression bugs.

Here I want to report (and warn other people) that there are significant issues with current 2.0.1 version available at doko's repos 
(deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./ ). 
a) The built-in bibliographic  database is unreachable
b) Gallery opens, but doesn't read in default clipart
c) Complex arrows and bezier lines are corrupted (I got a presentation with all bezier lines as simple, angled polylines)

I would like to inform doko, is there a site to let him know these issues?

Enrique

---

### Post by zoly on 2006-01-10
The same problems for me, too...

---

### Post by abandoned_hussam on 2006-01-12
I'm guessing these are Openoffice.org problems and not ubuntu problems.

---

### Post by jdong on 2006-01-12
[QUOTE=ecastro]
I would like to inform doko, is there a site to let him know these issues?

Enrique[/QUOTE]

Find him on irc.freenode.net, IRC name doko, he usually hangs out on #ubuntu-devel.

May take several tries to find him though :)

---

### Post by aussieskin on 2006-01-13
I added the repository:
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./ )

But in synaptic package manager I still only see openoffice.org 2 version 1.9.129
I've installed it, but it looks all wrong. The fonts and what not for the menu bars look like they came out of windows 3.1!

So is there a version 2 of openoffice.org2?

---

### Post by ecastro on 2006-01-13
[QUOTE=hussam]I'm guessing these are Openoffice.org problems and not ubuntu problems.[/QUOTE]
No, OOo 2.0.1 installed from official rpms via alien do not have those issues. Official 2.0.1 is build 8890, doko's is 8824.  The problem originates at OOo, I agree, their 2.0 release was very, very buggy. That's precisely the reason why an update to last 2.0.1 is absolutely needed. By installing the rpms one lost the integration of OOo with the rest of the system that works so nicely in Ubuntu

Enrique

---

### Post by Limulus on 2006-01-13
[QUOTE=aussieskin]I added the repository:
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./ )

But in synaptic package manager I still only see openoffice.org 2 version 1.9.129
I've installed it, but it looks all wrong. The fonts and what not for the menu bars look like they came out of windows 3.1!

So is there a version 2 of openoffice.org2?[/QUOTE]
First, that repo is only good for regular Ubuntu; if you use AMD64 or PPC Ubuntu, you'll need to change "OOo2" to "OOo2-amd64" or "OOo2-powerpc", respectively.

When you added the repo and then went into Synaptic, did you press reload?

As far as the looks go, the [Ubuntu version](http://members.shaw.ca/Limulus/files/OOo2.png) that uses Gnome and the [official version](http://www.openoffice.org/screenshots/ooo20/) do look rather different, but they're supposed to...

---

### Post by bryanl on 2006-01-13
looks like the doko update to 2.0.1 is missing the binfiles that import star office 5.x files.

---

### Post by qaqa on 2006-01-15
I've installed doko's OOO 2.0.1 on my breezy machine and I'm very happy with it. Doko has made some very nice changes  to  the official build - 
1) I can start formulas in Calc with "+" like in excel (A great improvement for people like me who grew up on 1-2-3!)
2) Switched the "delete cell contents" and "delete cells" keymappings.

**Is there any windows build of OOO2 that has these changes?** If there's any way I can contribute towards this, please let me know. 


Note: OOO2.0.1 is still very unstable - It generally dies when opening 1.1.4's .sxc files. Even when working on a new spreadsheet, OOO died twice in less than an hour. Methinks OOO should have retained the "beta" status and released it only once the bugs were ironed out

---

### Post by NoNo_231 on 2006-01-19
There is a problem with gallery, templates, pictures, slide transition and maybe more. Although the paths are configured right the items are not loaded. I saw that others have the same problem too. If you can find a way too fix this please publish it here.

---

### Post by zero0w on 2006-01-28
doko's OOo 2.0.1 breezy port will crash when using SCIM, so I won't recommend installing it if you use SCIM to input Chinese or Japanese....

---

### Post by chiisu on 2006-02-04
What exactly do I add to my sources.list to get this update in Kubuntu 5.10 amd64?  I put in "deb http://people.ubuntu.com/~doko/OOo2-amd64" and apt is complaining about it.......

---

### Post by Limulus on 2006-02-05
[QUOTE=chiisu]What exactly do I add to my sources.list to get this update in Kubuntu 5.10 amd64?  I put in "deb http://people.ubuntu.com/~doko/OOo2-amd64" and apt is complaining about it.......[/QUOTE]
The exact line to put into your sources.list file should be:

```
deb http://people.ubuntu.com/~doko/OOo2-amd64 ./
```
Did you use the ./ ?

If that's not it, what is the specific error?

---

