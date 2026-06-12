---
title: "Should Ubuntu have its own Open Office???"
date: 2006-12-11
forum: The Cafe
---

### Post by geokok1981 on 2006-12-11
There seems to be at least one major issue that I am aware of in Open Office that is caused by the
compilation done using gcj and it is possible that there may be others. This is an problem inherited 
in the suite from Debian. Other distros work fine. 

OO is a major component of any OS. Do you think that Ubuntu should start making/compiling its own version of
OO so that it works just like in other distros? Or should it keep using the version from Debian with the risk of 
getting extra glitches?

Problem Details: OO base is useless due to the fact that the form wizard does not complete creating the form.
Issue filled in launchpad: Bugs report: 
[https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/72539](https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/72539)
[https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/72262](https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/72262)
[https://bugs.launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/62254](https://bugs.launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/62254)
[https://bugs.launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/73395](https://bugs.launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/73395)

[B]I filled a report in Launchpad about this, asking for a version of OO that works. If u like u may add your opinion here:
[https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/76450](https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/76450)
[/B]
P.S. I mean no disrespect to any of the hard working developers of any distro. Just posting some thoughts on a matter that seems important to me and seems logical to complain about. After all, it would only benefit Ubuntu to have a good OO installation, right?? 
Also, I am not a techie, so I dont even know if is possible in the first place for a debian based disrto to discard pieces from debian that easily and add others.

---

### Post by weatherman on 2006-12-11
what problems are you encountering?

---

### Post by geokok1981 on 2006-12-11
> **weatherman said:**
> what problems are you encountering?

I gave a link on the first post that has the bug report which is detailed.
In brief, the problem is that when you try to create a form in OO base 
using the wizard, the wizard will not finish.

---

### Post by hoagie on 2006-12-11
Yeah OO Base is just useless, and it runs like crap. You can't work with it. I can't even create a form. And still the bug in launchpad is not even confirmed!

Can anyone say to me a way to get this right?

---

### Post by geokok1981 on 2006-12-11
> **hoagie said:**
> Yeah OO Base is just useless, and it runs like crap. You can't work with it. I can't even create a form. And still the bug in launchpad is not even confirmed!

Can anyone say to me a way to get this right?

Actually the bug has been confirmed. It is just that my report has been marked as a duplicate. so the orginal one got confirmed.

One solution to the problem is:
1. Uninstall OO from ubuntu.
2. Find deb package for OO from somewhere 
OR
Get the RPM packages from the OO website
Unpack the file
Use alien (in a terminal: alien -i *.rpm) to convert to debs and install
Have fun with a working OO.....

Is gcj a Java thing?? If yes, then the good relationship between Ubuntu
and sun would give a better compilation of OO (I think...) by using Sun's tools..

---

### Post by Brunellus on 2006-12-11
> **geokok1981 said:**
> Actually the bug has been confirmed. It is just that my report has been marked as a duplicate. so the orginal one got confirmed.

One solution to the problem is:
1. Uninstall OO from ubuntu.
2. Find deb package for OO from somewhere 
OR
Get the RPM packages from the OO website
Unpack the file
Use alien (in a terminal: alien -i *.rpm) to convert to debs and install
Have fun with a working OO.....

Is gcj a Java thing?? If yes, then the good relationship between Ubuntu
and sun would give a better compilation of OO (I think...) by using Sun's tools..
up until now, the java bits of OOo were problematic as Java was not Free Software. 

I wonder if recent events will change policy.

---

### Post by dbbolton on 2006-12-11
the only problem i've had is that writer/presentation freeze when attempting to export as xhtml.

---

### Post by Polygon on 2006-12-11
the java source will be open sourced officially in January, so it is just a matter of time before the code gets improved a lot and bugs and performance issues like this get fixed. Cant wait :D

---

### Post by darkhatter on 2006-12-11
don't waste time, download the rpm off of Sun and install that.

---

### Post by geokok1981 on 2006-12-12
> **darkhatter said:**
> don't waste time, download the rpm off of Sun and install that.
 
The idea is that it should have the same level of functionality as the rpm 
packages do, out of the box. Show a broken "access" to a newbie and try 
to make him understand about Java :impurities" and the like...its a lost cause...and a lost user...

---

### Post by hoagie on 2006-12-12
> **geokok1981 said:**
> Actually the bug has been confirmed. It is just that my report has been marked as a duplicate. so the orginal one got confirmed.

One solution to the problem is:
1. Uninstall OO from ubuntu.
2. Find deb package for OO from somewhere 
OR
Get the RPM packages from the OO website
Unpack the file
Use alien (in a terminal: alien -i *.rpm) to convert to debs and install
Have fun with a working OO.....

Is gcj a Java thing?? If yes, then the good relationship between Ubuntu
and sun would give a better compilation of OO (I think...) by using Sun's tools..

In synaptic there are more than about 30 packages installed which ones shall I remove?

---

### Post by darkhatter on 2006-12-12
> **geokok1981 said:**
> The idea is that it should have the same level of functionality as the rpm 
packages do, out of the box. Show a broken "access" to a newbie and try 
to make him understand about Java :impurities" and the like...its a lost cause...and a lost user...

I know what you mean, but this problem will have to be fixed on the debian side cause ubuntu does repackages.

---

### Post by geokok1981 on 2006-12-12
> **darkhatter said:**
> I know what you mean, but this problem will have to be fixed on the debian side cause ubuntu does repackages.

Exactly!!!I think its time to take some things on its own hands!!

---

### Post by geokok1981 on 2006-12-12
> **hoagie said:**
> In synaptic there are more than about 30 packages installed which ones shall I remove?

Well, I had way too much trouble uninstalling OO cause Synaptic kept 
complaining for a broken package (but it turned out that there was no broken package). To solve this I took the following steps:

1. Search for open office in Synaptic. Results will be plenty...
2. Start taking out components, one by one. For example, take out OO base, OO writer and so on. Some things will get uninstalled along with them automatically. Also get rid of any dictionary, language support packages that are OO specific (not sure if it matters for them to stay but I took them all out).
3. Leave the openoffice.org and openoffice-core for the end. They would complain if i chose them first in my installation.
4. U should have a clean system now...

---

### Post by wilbur.harvey on 2006-12-12
Yes, Ubuntu should have their own OpenOffice.

I have many crashes. Instant crash when trying to create a new document from my template (template opens fine). Many crashes in Draw when editing text.

I have verified the crashes on 2.03 under Dapper on one system, and another system running Edgy with 2.04. Same basic crashes.

I posted a bug with OpenOffice and gave them the template file, they said it worked fine for them and recommended that I download and install the official release.

Sounds like a very bad Ubuntu thing. How can I use Ubuntu as a desktop with a broken Office?

Using alien to install the latest 2.1.0 on Dapper seems to work, but, of course it isn't installed nicely, no menus, no mime etc.

---

### Post by geokok1981 on 2006-12-13
Just found this...
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=354895](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=354895)

It looks like many parts of OO are broken because of the way Debian 
does the source code compilation.
Even more evidence proving the need for a version of OO taken 
straight from OO.org ......

---

### Post by geokok1981 on 2006-12-16
Although the poll results agree with me, it is suprising how few people voted
out of the total number that viewed the thread.....
I thought that the Office suite would be a more important issue for many in here.....

---

### Post by Lord Illidan on 2006-12-18
I agree that it should be compiled from scratch. Ubuntu has now moved substantially away from its Debian roots, and we want something better.

---

### Post by Stealth on 2006-12-18
I'd actually like to see a whole new office suite be created. Something that is built for speed (unlike Ooo, which has seem to get bloated) and based off of GTK (for GNOME integration). I guess like a gOffice? That'd be cool...

---

### Post by jongkind on 2006-12-18
> **Stealth said:**
> I'd actually like to see a whole new office suite be created. Something that is built for speed (unlike Ooo, which has seem to get bloated) and based off of GTK (for GNOME integration). I guess like a gOffice? That'd be cool...

I agree on this.

---

### Post by Lord Illidan on 2006-12-18
> **Stealth said:**
> I'd actually like to see a whole new office suite be created. Something that is built for speed (unlike Ooo, which has seem to get bloated) and based off of GTK (for GNOME integration). I guess like a gOffice? That'd be cool...

I'd also like to see a KDE version of this...not KOffice, it sucks.. Krita is good, but the rest is a let down.

Open Office is not bad, but it does not integrate well with KDE, and not so well with GNOME, and it is slow and bloated.

---

### Post by FyreBrand on 2006-12-18
> **geokok1981 said:**
> Although the poll results agree with me, it is suprising how few people voted
out of the total number that viewed the thread.....
I thought that the Office suite would be a more important issue for many in here.....

Because the poll is biased.  How about an option for Debian to now compile OO with Sun's compiler instead of the gnu compiler.  By Debian's policy they couldn't really use the Sun compiler before, but now there may be more options for them.  It would be good to find out what they have in mind here.  Now if Debian decides not to compile OO with Sun's compiler in the future then maybe there is a good reason to create a new package tree for Ubuntu.

---

### Post by Lord Illidan on 2006-12-18
> **FyreBrand said:**
> Because the poll is biased.  How about an option for Debian to now compile OO with Sun's compiler instead of the gnu compiler.  By Debian's policy they couldn't really use the Sun compiler before, but now there may be more options for them.  It would be good to find out what they have in mind here.  Now if Debian decides not to compile OO with Sun's compiler in the future then maybe there is a good reason to create a new package tree for Ubuntu.

But do we really need to use Debian's version of OpenOffice?

---

### Post by geokok1981 on 2006-12-18
> **FyreBrand said:**
> Because the poll is biased.  How about an option for Debian to now compile OO with Sun's compiler instead of the gnu compiler.  By Debian's policy they couldn't really use the Sun compiler before, but now there may be more options for them.  It would be good to find out what they have in mind here.  Now if Debian decides not to compile OO with Sun's compiler in the future then maybe there is a good reason to create a new package tree for Ubuntu.

I don't see how it is biased. Biased would be to demand from Debian to compile with
whatever_Java so that we could get a working ubuntu.
What I am saying is completely different and does not bias anyone. I dont see why Ubuntu 
has to put up with Debian problems due to policy or why it should hassle Debian to do things
in a more Ubuntu way. 

If Ubuntu had its own compilation everybody would be happy and still free to follow ones principles .......

As for gOffice...I believe that like the kOffice it wouldnt have much of success.
Right now OO is much more complete and although it has problems it is a strong open source card. Instead of putting effort to re-invent the wheel, I see more benefit in developers focusing on OO to make it better...

---

### Post by reiatzu on 2006-12-18
> **jongkind said:**
> I agree on this.

I do too. However, do you mean an 'Ubuntu Office' of sorts? & Would this be something re-implemented off the OpenOffice suite, or created from entire scratch?

---

### Post by Lord Illidan on 2006-12-18
> **geokok1981 said:**
> I don't see how it is biased. Biased would be to demand from Debian to compile with
whatever_Java so that we could get a working ubuntu.
What I am saying is completely different and does not bias anyone. I dont see why Ubuntu 
has to put up with Debian problems due to policy or why it should hassle Debian to do things
in a more Ubuntu way. 

If Ubuntu had its own compilation everybody would be happy and still free to follow ones principles .......

As for gOffice...I believe that like the kOffice it wouldnt have much of success.
Right now OO is much more complete and although it has problems it is a strong open source card. Instead of putting effort to re-invent the wheel, I see more benefit in developers focusing on OO to make it better...

True, but right now, I am only seeing the devs focusing on adding more features instead of removing bloat and bugs.

---

### Post by 23meg on 2006-12-18
Ubuntu already builds OOo with its own toolchain, just like every other package.

---

### Post by SunnyRabbiera on 2006-12-18
I think there should be a home brewed OO for debian systems period as converting a million different RPM's is a pain in the neck.

---

### Post by geokok1981 on 2006-12-18
> **23meg said:**
> Ubuntu already builds OOo with its own toolchain, just like every other package.

If that is the case then why did the reported bug in launchpad was assigned to Debian open office? Why did people claim that it was a gcj compilation problem from debian?
And even if it is so, why not compile using Sun Java....I mean its Ubuntu, not Debian....
and Sun is a partner for Ubuntu as stated in the website.....

---

### Post by FyreBrand on 2006-12-18
> **geokok1981 said:**
> If that is the case then why did the reported bug in launchpad was assigned to Debian open office? Why did people claim that it was a gcj compilation problem from debian?
And even if it is so, why not compile using Sun Java....I mean its Ubuntu, not Debian....
and Sun is a partner for Ubuntu as stated in the website.....GCJ was and still might be, in future releases, the default compiler.  That seems the logical reason why you compile with that.  Just as there are GCJ and Sun Java compiled versions of eclipse in the repos.  Some people only use gpl'd software.

As far as the poll, it reads:
1. Yes, I want a version that works.
2. No, I don't want a version that works, i want to keep the old version that doesn't work.

The poll didn't provide very reasonable or sensible options.  Writing polls is really difficult.  It's easy to word a poll so that the results support your opinion.  It's hard to write a poll offering realistic options.  It's even harder to do this and try and anticipate all the options that fit the given question.

You asked why so many people read the thread but didn't vote and that's just my opinion as to why.  It's also possible that many people just don't care (also not an option in your poll).

There are bugs in the compiled version of OO for Ubuntu that aren't present in the Windows compiled version.  It's hard to say whether this is due to the compiler choice or if there is some other library or dependency problem.  Just compiling OO with the Sun compiler won't necessarily guarantee that these bugs will disappear.

---

### Post by 23meg on 2006-12-18
> **geokok1981 said:**
> If that is the case then why did the reported bug in launchpad was assigned to Debian open office? Why did people claim that it was a gcj compilation problem from debian?Because apparently it's affecting Debian OOo as well. The bug was filed against the OOo *source* package from Debian, and according to the Debian bug report linked at the Launchpad page, it seems the Debian people were having problems with not just gcj but other JREs as well.
[QUOTE=geokok1981]And even if it is so, why not compile using Sun Java....I mean its Ubuntu, not Debian....
and Sun is a partner for Ubuntu as stated in the website.....[/QUOTE]One reason can be that OOo is in Main, and Sun Java wasn't GPL'd at Edgy's release time. There may be another rationale though, and gcj may still be kept.
[QUOTE=FyreBrand]The poll didn't provide very reasonable or sensible options. [/QUOTE]Agreed, I didn't vote either since there's no such thing as a "Debian compiled OOo" in Ubuntu.

---

### Post by geokok1981 on 2006-12-18
> **FyreBrand said:**
> GCJ was and still might be, in future releases, the default compiler.  That seems the logical reason why you compile with that.  Just as there are GCJ and Sun Java compiled versions of eclipse in the repos.  Some people only use gpl'd software.

As far as the poll, it reads:
1. Yes, I want a version that works.
2. No, I don't want a version that works, i want to keep the old version that doesn't work.

The poll didn't provide very reasonable or sensible options.  Writing polls is really difficult.  It's easy to word a poll so that the results support your opinion.  It's hard to write a poll offering realistic options.  It's even harder to do this and try and anticipate all the options that fit the given question.

You asked why so many people read the thread but didn't vote and that's just my opinion as to why.  It's also possible that many people just don't care (also not an option in your poll).

There are bugs in the compiled version of OO for Ubuntu that aren't present in the Windows compiled version.  It's hard to say whether this is due to the compiler choice or if there is some other library or dependency problem.  Just compiling OO with the Sun compiler won't necessarily guarantee that these bugs will disappear.

Ok the poll may not be an example of poll creation to be followed but I am sure that by seeing the poll + reading my first post u got the general idea of what i was talking about...

As for compiling with Sun Java and problems not being solved....I am not a dev, I can barely write a script and I am a linux user for 6 months so I may not be able to grasp 
completely the inner workings of the programs,.,,......

But I do know this. If I get OO from OpenOffice.org and alien those rpm's I get a working OO suite......the conclusions to this can come from you........

---

### Post by geokok1981 on 2006-12-19
I filled a report in Launchpad about this, asking for a version of OO that works. If u like u may add your opinion here:
[https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/76450](https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/76450)

---

### Post by 23meg on 2006-12-19
Here's the correct URL: 

[https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/76450](https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/76450)

> It seems that many of the bugs related to OO shipped with Ubuntu are
due to the fact that it is being compiled using gcj.This doesn't seem to be the case; other JREs fail as well, as said in the Debian bug report.

---

### Post by geokok1981 on 2006-12-19
> **23meg said:**
> Here's the correct URL: 

[https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/76450](https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/76450)

This doesn't seem to be the case; other JREs fail as well, as said in the Debian bug report.

URL corrected thanks for letting me know.

I seem to be a bit confused here with all the java things....I read in mailing lists/forums/etc 
that the source of problems is the compilation done with gcj.......I know that OO fails regardless of the JRE...what am I saying wrong?? Please add any info u are able to 
provide/correct in my report in Launchpad. 

Thanks.

---

### Post by Robvdl on 2006-12-19
The Form wizard and Table wizard in OpenOffice base in Edgy don't work, I get nothing coming up at all when I click on these wizards, so have to create forms and tables manually. This is seriously broken in Edgy unfortunately.

I don't agree with the Grey/brown, in my mind "defaced" open office splash screen either, I prefer to see the original, "unmodified" blue splash screen, which is much nicer. I don't see any reason why to modify original graphics that came with a product. The graphics give the product an identity, they should remain unchanged. The same goes for Firefox and Thunderbird, although they have since replaced the icon and picture under help->about of Firefox back to the original in Edgy now, the icon and picture under help->about in Thunderbird, are still the ugly modified versions. I would rather see the standard, "unmodified" graphics for OpenOffice, Thunderbird and Firefox.

---

### Post by danyul on 2006-12-22
I'm also affected by this bug.  I wouldn't mind getting OO from Sun's site, but is there any way of installing it in a "clean" way?  I.e., so that it doesn't mess up package management, and so that I wouldn't necessarily need to delete my package-based install?  that way, I could just delete the working Sun-downloaded version once OpenOffice in the repositories is usable.   I'm worried that installing via alien will mess up future attempts to upgrade.

Thanks!

---

### Post by Robvdl on 2006-12-23
> I'm also affected by this bug. I wouldn't mind getting OO from Sun's site, but is there any way of installing it in a "clean" way? I.e., so that it doesn't mess up package management

This is exactly what has been running through my mind. I want to build Open Office from source directly from [http://openoffice.org](http://openoffice.org), but because Ubuntu/Edgy has split Open Office into many sub packages, this sounds like a scary thing, without screwing up my existing install.

I've built various smaller things from source already, Glipper, Geany, XChat Rhythmbox plugin, Gaim Rhythmbox plugin and the 2.6.19 Kernel for K8 :) But that's about as far as I've gone. Oh.. then there's also the broken java-gnome packages I have built for Edgy, as I'm not sure if they were going to get fixed until Feisty. Those are broken to the point you cannot run any GTK based Java apps or write them, which is quite serious, as it holds back potential new developers.

Anyway, my question would be, how difficult would it be to build Open Office from source for Edgy, without doing too much damage to the existing packages?

I wouldn't even try doing it with Alien though, some smaller things can work when you convert RPM's with Alien, but larger things can go wrong, besides it's going to possibly put everything into Redhat based locations on your drive that way.

---

### Post by geokok1981 on 2006-12-23
> **Robvdl said:**
> 
I wouldn't even try doing it with Alien though, some smaller things can work when you convert RPM's with Alien, but larger things can go wrong, besides it's going to possibly put everything into Redhat based locations on your drive that way.

Alien worked for me fine but I dont know if there were any "hidden" problems....

All your thoughts verify my original question....Why would Ubuntu ship a broken office suite?
Why would it give to its users a broken component of the desktop when an office suite is an 
important part of it. I mean Ubuntu is supposed to sell commercial support as well for its 
desktop. I cant imagine how any serious company would choose an OS that offers seriously flawed apps or what would the support team have to say to the company once they discovered the problems in OO.....

The bottom line is, when Suse is trying its best to improve the Office suite by doing so much to advance the suite, its a shame that Ubuntu is going the other way and adds even more problems in the existing OO.org version.......and that is a fact!

---

### Post by rlozano on 2006-12-23
i believe its better to stay with the office suite of Openoffice.org so that ubuntu can really focus its resources in stabilizing and strengtheing the OS. ;-)

---

### Post by wdo_will on 2006-12-23
Never had a problem with the default OOo... but I don't use base (MySQL and phpMyAdmin take care of that for me).

---

### Post by shining on 2006-12-23
> **geokok1981 said:**
> Alien worked for me fine but I dont know if there were any "hidden" problems....

All your thoughts verify my original question....Why would Ubuntu ship a broken office suite?
Why would it give to its users a broken component of the desktop when an office suite is an 
important part of it. I mean Ubuntu is supposed to sell commercial support as well for its 
desktop. I cant imagine how any serious company would choose an OS that offers seriously flawed apps or what would the support team have to say to the company once they discovered the problems in OO.....

The bottom line is, when Suse is trying its best to improve the Office suite by doing so much to advance the suite, its a shame that Ubuntu is going the other way and adds even more problems in the existing OO.org version.......and that is a fact!

I agree. Ubuntu should stop presenting itself as a free operating system, like Debian does, and stop giving a damn about what is free or not, and make some contracts with Microsoft for making a better operating system, as closed and proprietary as possible.

---

### Post by Busch on 2006-12-23
I think OO is fine the way it is, if not just use the rpm of it like people have said.  no need for ubuntu to take over any programs, just like rlozano said 

> i believe its better to stay with the office suite of Openoffice.org so that ubuntu can really focus its resources in stabilizing and strengtheing the OS. 

---

### Post by Robvdl on 2006-12-23
> **geokok1981 said:**
> All your thoughts verify my original question....Why would Ubuntu ship a broken office suite?
Why would it give to its users a broken component of the desktop when an office suite is an 
important part of it. I mean Ubuntu is supposed to sell commercial support as well for its 
desktop. I cant imagine how any serious company would choose an OS that offers seriously flawed apps or what would the support team have to say to the company once they discovered the problems in OO.....

Ok, true, however I think when Ubuntu shipped Edgy though, the idea was that it was not supposed to be a long term support release like Dapper. Edgy was supposed to be a more "cutting edge" release over Dapper, so there were bound to be problems. For example, here are the problems I have found with Edgy so far:

[list]
[*]The form and table wizard in Open Office Base are broken
[*]The foot in the corner of nautilus windows is too small
[*]When browsing a SAMBA share, you randonly get "blank icons", double clicking these produces an error
[*]java-gnome is seriously broken, to the point you can't run any GTK+ java apps, or create them - I had to compile java-gnome myself
[*]I get more frequent crashing compared to Dapper, the bug reporting tool comes up a lot
[/list]

Most of these problems won't be fixed by the looks of it, the SAMBA nautilus "blank icon" bug, small foot in nautilus window, and broken java-gnome, we have to live with these 'till Feisty gets released. But on the more positive side, Edgy does give us more up-to-date software, such as Firefox 2, Evolution 2.8, Gnome 2.16, etc. I think the idea is, for those that want commercial support, stick with Dapper for now, for those that are not afraid of a few bugs, but want more cutting edge software, get Edgy.

But I totally agree, that Ubuntu should use the standard version of Open Office, that just works, instead of the Debian modified one, that is currently broken.

I think Feisty should be a better release, like Edgy, with cutting edge software, but hopefully not as many problems, as stable as Dapper was.

> **rlozano said:**
> i believe its better to stay with the office suite of Openoffice.org so that ubuntu can really focus its resources in stabilizing and strengtheing the OS. ;-)

I fully agree ;-)

---

### Post by geokok1981 on 2006-12-24
> **shining said:**
> I agree. Ubuntu should stop presenting itself as a free operating system, like Debian does, and stop giving a damn about what is free or not, and make some contracts with Microsoft for making a better operating system, as closed and proprietary as possible.

You missed my point by far.......sorry to hear that u believe that this reflects my standards 
and beliefs........

---

### Post by Timokl on 2007-03-31
> **Robvdl said:**
> For example, here are the problems I have found with Edgy so far:

[list]
[*]The form and table wizard in Open Office Base are broken
[*]The foot in the corner of nautilus windows is too small
[*]When browsing a SAMBA share, you randonly get "blank icons", double clicking these produces an error
[*]java-gnome is seriously broken, to the point you can't run any GTK+ java apps, or create them - I had to compile java-gnome myself
[*]I get more frequent crashing compared to Dapper, the bug reporting tool comes up a lot
[/list]

One problem that you could add is that you cannot use CTL scripts (like Thai) with the Ubuntu version of OpenOffice. It works very well in the Windows version of OpenOffice. I did not manage to get the original OpenOffice installed on my ubuntu box. :-(

Timo

---

### Post by dougfractal on 2007-05-22
I've gota say i've  just replaced ubuntu's openoffice with sun's openoffice + jre6 and it rocks

starts in 1 second.
And the wizards in openoffice base actually work ;-)

download openoffice from sun.
tar -xzf OO*.tar.gz
cd OO*/RPMS
sudo apt-get remove openoffice.org-common
sudo alien -i *.rpm
sudo dpkg -i ./desktop-integration/*debian*.deb

Happy 00o-ing

---

