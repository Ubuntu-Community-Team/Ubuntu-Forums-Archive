---
title: "Pidgin for Fiesty."
date: 2007-05-05
forum: The Cafe
---

### Post by Fylk on 2007-05-05
Its seems that very ones favourite fawn is missing one very important part, a pigeon. Yes, I know that's a really, really bad play one words, but you know what? Too bad. 

What I want to know is why you all think we haven't gotten the upgrade. I know there area a few community maintained packages, and that you can build it yourself, but what's the point of that in a distro where the main focus is out of the box function? I mean, really now, I know there aren't any really BIG security improvements, but there are huge functional improvements over 1.5 series of gaim, which we are all currently using. 

So, do you think we will every get pidgin? Or will our fawn be without a feathered friend?

---

### Post by aidanr on 2007-05-05
it'll take a while to get into the repos, in the meantime there are lots of debs out there for it, i'm using [http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0-1_i386.deb](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0-1_i386.deb) (have to remove gaim first)

---

### Post by prizrak on 2007-05-05
> **Fylk said:**
> Its seems that very ones favourite fawn is missing one very important part, a pigeon. Yes, I know that's a really, really bad play one words, but you know what? Too bad. 

What I want to know is why you all think we haven't gotten the upgrade. I know there area a few community maintained packages, and that you can build it yourself, but what's the point of that in a distro where the main focus is out of the box function? I mean, really now, I know there aren't any really BIG security improvements, but there are huge functional improvements over 1.5 series of gaim, which we are all currently using. 

So, do you think we will every get pidgin? Or will our fawn be without a feathered friend?

Because there is no point in the upgrade. Just for the record Feisty has a 2.0Beta6 of Gaim not a 1.5 and there is very little difference from Pidgin 2.0. Also because of the name change it's a very significant upgrade because every single package that "talks" to Gaim has to start "talking" to Pidgin. Basically the ROI is not significant enough to warrant the upgrade.

---

### Post by karellen on 2007-05-05
> **Fylk said:**
> Its seems that very ones favourite fawn is missing one very important part, a pigeon. Yes, I know that's a really, really bad play one words, but you know what? Too bad. 

What I want to know is why you all think we haven't gotten the upgrade. I know there area a few community maintained packages, and that you can build it yourself, but what's the point of that in a distro where the main focus is out of the box function? I mean, really now, I know there aren't any really BIG security improvements, but there are huge functional improvements over 1.5 series of gaim, which we are all currently using. 

So, do you think we will every get pidgin? Or will our fawn be without a feathered friend?

is really so hard to spell that name correct? it's Feisty, not Fiesty
:confused:

---

### Post by MarilenCorciovei on 2007-05-10
Here is how to compile it yourself:

apt-get install libglib2.0-dev
apt-get install libgtk2.0-dev (will install a lot of dependencies)
apt-get install libxml2-dev
#at this point it will compile
apt-get install libgnutls-dev (for ssl support)
apt-get install libgstreamer0.10-dev (for gstreamer support)
apt-get install libdbus-1-dev (for dbus support)
apt-get install libgtkspell-dev libdbus-glib-1-dev (for gtkspell support)

tar xvfj pidgin-2.0.0.tar.bz2
cd pidgin-2.0.0/
./configure
make
su
make install

from here: [http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/install-pidgin/view]("http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/install-pidgin/view")

---

### Post by igknighted on 2007-05-10
Simple: Pidgin was released after Feisty.  Look at other significant upgrades like Firefox2.  It didn't get into Dapper, you had to manually upgrade.  This is because Ubuntu doesn't typically upgrade apps in a release (no T-bird2 either).  In reality, Pidgin adds almost nothing as well.  The theme is nicer, but you could change that on your own, and thats about it.

---

### Post by macogw on 2007-05-10
> **MarilenCorciovei said:**
> Here is how to compile it yourself:

apt-get install libglib2.0-dev
apt-get install libgtk2.0-dev (will install a lot of dependencies)
apt-get install libxml2-dev
#at this point it will compile
apt-get install libgnutls-dev (for ssl support)
apt-get install libgstreamer0.10-dev (for gstreamer support)
apt-get install libdbus-1-dev (for dbus support)
apt-get install libgtkspell-dev libdbus-glib-1-dev (for gtkspell support)

tar xvfj pidgin-2.0.0.tar.bz2
cd pidgin-2.0.0/
./configure
make
su
make install

from here: [http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/install-pidgin/view]("http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/install-pidgin/view")
You could shorten that to 
sudo apt-get build-dep gaim

then the compiling bit

---

### Post by Polygon on 2007-05-11
it might be important because the name was changed due to legal reasons

not to mention that the interface in 2.0 looks a lot better then the one in whatever beta feisty shipped with.

---

### Post by Mateo on 2007-05-11
> **Fylk said:**
> Its seems that very ones favourite fawn is missing one very important part, a pigeon. Yes, I know that's a really, really bad play one words, but you know what? Too bad. 

What I want to know is why you all think we haven't gotten the upgrade. I know there area a few community maintained packages, and that you can build it yourself, but what's the point of that in a distro where the main focus is out of the box function? I mean, really now, I know there aren't any really BIG security improvements, but there are huge functional improvements over 1.5 series of gaim, which we are all currently using. 

So, do you think we will every get pidgin? Or will our fawn be without a feathered friend?

Ubuntu developers care more about whether a bug exists where the title pidgin is misspelled on the third Tuesday of each month starting with a J when the tide is up and you're using the liveCD, than they are about getting users what they want: **new software**.

---

### Post by Mateo on 2007-05-11
> **prizrak said:**
> Because there is no point in the upgrade. Just for the record Feisty has a 2.0Beta6 of Gaim not a 1.5 and there is very little difference from Pidgin 2.0. Also because of the name change it's a very significant upgrade because every single package that "talks" to Gaim has to start "talking" to Pidgin. Basically the ROI is not significant enough to warrant the upgrade.

That's an Orwellian point of view.  If a user doesn't think it's "significant enough", they don't have to upgrade it.  It should be up to the users, not Big Brother who think they have a right to control what's important or not.

---

### Post by Polygon on 2007-05-11
> **Mateo said:**
> Ubuntu developers care more about whether a bug exists where the title pidgin is misspelled on the third Tuesday of each month starting with a J when the tide is up and you're using the liveCD, than they are about getting users what they want: **new software**.

and version 2.0 is  different from version 2.0 beta 6, aka "new software". It has a lot of UI improvements and not to mention that the name was changed for legal reasons.

and since its the same version,just different minor version it should be included. (kinda like how since there is firefox 2.0.0..3 on feisty, if 2.0.0.4 comes out then the update will be released in the repos, but its ubuntus policy not to include upgrades for major version changes as they have no idea what the effects it will be on the rest of the system)

---

### Post by loell on 2007-05-11
> **Mateo said:**
> That's an Orwellian point of view.  If a user doesn't think it's "significant enough", they don't have to upgrade it.  It should be up to the users, not Big Brother who think they have a right to control what's important or not.

oh well, big brother's got to be rationale , so gaim will suffice.

---

### Post by Mateo on 2007-05-11
> **aidanr said:**
> it'll take a while to get into the repos, in the meantime there are lots of debs out there for it, i'm using [http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0-1_i386.deb](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0-1_i386.deb) (have to remove gaim first)

i've always wondered, what happens if you install an outside DEB and then that software gets put into the repos.  Does it automatically switch to the repo version?

---

### Post by loell on 2007-05-11
> **Mateo said:**
> i've always wondered, what happens if you install an outside DEB and then that software gets put into the repos.  Does it automatically switch to the repo version?

no it doesn't. don't worry it won't get into the official repo.

---

### Post by pirothezero on 2007-05-11
I might have missed something but today on my desktop that I hadn't started in about 3-5 days it had all the gaim and pidgin updates in the update manager when I booted into it. So if its not in the offical repo where did those come from?

---

### Post by loell on 2007-05-11
dunno, i have pidgin too. but no updates on gaim or pidgin for that matter.

maybe you're using using third party scripts, though i know automatix will never include pidgin.

---

### Post by prizrak on 2007-05-11
> **Mateo said:**
> That's an Orwellian point of view.  If a user doesn't think it's "significant enough", they don't have to upgrade it.  It should be up to the users, not Big Brother who think they have a right to control what's important or not.

Last I checked there was no code in Ubuntu that stopped you from installing what you want. If you happen to want Pidgin 2.0 the steps to take to get it have been outlined in this thread. Since Pidgin 2.0 does not have any security fixes or major bug fixes (a nicer UI is not a major bug fix) and has changed the name to boot (which would require changing more than just the gaim package), Ubuntu package maintainers didn't see providing Pidgin as something that was worth the time/effort. 

I don't understand why you are using an OS that clearly has different beliefs. Why don't you go to a rolling distro or something else? The policy on new software has been outlined quite clearly by the maintainers and was never a secret. They seem to believe that it's the best way to balance stability with having up to date software. Ubuntu was never supposed to be an up to date distro. I mean would you go to Debian forums and tell them something like that? Yet Debian releases every 2 years if not 3.

---

### Post by Mateo on 2007-05-11
> **prizrak said:**
> I don't understand why you are using an OS that clearly has different beliefs. Why don't you go to a rolling distro or something else? 

I don't have any beliefs.  Software isn't a religion to me the way it is to the ubuntu fundamentalists.  I will not use another distro so stop asking; I will continue to use Ubuntu and criticize it's Orwellian anti-user policies.

---

### Post by prizrak on 2007-05-11
> and version 2.0 is different from version 2.0 beta 6, aka "new software". It has a lot of UI improvements and not to mention that the name was changed for legal reasons.

and since its the same version,just different minor version it should be included. (kinda like how since there is firefox 2.0.0..3 on feisty, if 2.0.0.4 comes out then the update will be released in the repos, but its ubuntus policy not to include upgrades for major version changes as they have no idea what the effects it will be on the rest of the system)
Just realised I forgot to respond to you. 2.0.0.3 to 2.0.0.4 was basically a security fix (perhaps some other fixes too) which is why it was included. Ubuntu policies state that they will not be providing anything but security updates and possibly major bug fixes during the lifecycle of each version. Pidgin 2.0 will require changes in the gaim package, all packages that depend on it (all the themes and plugins for it), and ubuntu/kubuntu/xubuntu/edubuntu-desktop package. This is just way too much work for something that doesn't introduce anything but minor UI improvements. There are .debs that work on Feisty for those who want it so really what's the point?
> **Mateo said:**
> I don't have any beliefs.  Software isn't a religion to me the way it is to the ubuntu fundamentalists.  I will not use another distro so stop asking; I will continue to use Ubuntu and criticize it's Orwellian anti-user policies.

I fail to see where I mentioned any religion like beliefs. You might be surprised but it doesn't have to be religious to be a belief. For instance you BELIEVE that a rolling release schedule (essentially what your argument seems to boil down to) is superior to a fixed release schedule. Ubuntu developers BELIEVE that a fixed (and frozen) release schedule is better. Nothing is religious about it, simply a different approach to the same issue. 

How is Ubuntu Orwellian and anti-user? There is nothing at all in the entire OS that stops you from doing what you want. You can install what software you like and uninstall what software you don't like. You are upset because the developers don't see the need to include the software you want in the repositories? They don't have unlimited time, there are other things to do that are more important than providing a nicer looking GUI for Gaim (that's really the only difference). They are working on Gutsy, they are fixing w/e serious bugs might be in Feisty, Edgy and Dapper. Hell one of the things they are working on is making sure Pidgin and Gutsy work together. 

I don't see why you are complaining at all, if you believe that Ubuntu does not provide the quality of service you expect out of them find a different distro that does. If you don't want to find a different distro, do something about it. Here is a thought, get a bunch of people who think like you and start your own Ubuntu repository that will hold all of the software you want and update it as soon as new software comes out. You could join the Backports project as well, their aim is to provide new software outside of what Ubuntu normally does. 

If you just want to sit there at your keyboard and complain, that's fine too. Just don't expect  any changes to come about as a result of that. 

Also I would advise you steer clear of saying things like "Orwellian anti-user policies". As all it does is make you seem childish and detracts from your argument. There is nothing Orwellian about an open source project it's pretty much impossible. There is also nothing "anti-user" about Ubuntu otherwise it would not be the most popular distro.

---

### Post by graabein on 2007-05-11
I don't think anyone's complaining, they just want Pidgin in the official repos. If the devs put it there that's great, if not the people who really want it have to get an unofficial deb and that's fine too, it has been done before. I have for instance installed Freeciv 2.1 beta. I don't think switching to a different distro is a reasonable suggestion. 

On another note, how come Opera is not in the repos? Is it closed or non-free?

---

### Post by maynoth on 2007-05-11
I agree it is silly to deny users new versions of software (if they want it) and no I don't want to use arch or gentoo, I like the support community ubuntu has.... but this 6 month old software crud is annoying.


There should be an experimental repo where all the latest and greatest apps (non-beta) are kept current... 6 months for a refresh is too long..   this way the ppl who don't want the latest don't have to have it.  everyone is happy...

K3B, Open Office, Pidgin, Firefox, Thunderbird, VLC and everything else people actually use on a regular basis should be kept up to date.

---

### Post by Mateo on 2007-05-11
> **prizrak said:**
> I don't see why you are complaining at all, if you believe that Ubuntu does not provide the quality of service you expect out of them find a different distro that does. If you don't want to find a different distro, do something about it. Here is a thought, get a bunch of people who think like you and start your own Ubuntu repository that will hold all of the software you want and update it as soon as new software comes out. You could join the Backports project as well, their aim is to provide new software outside of what Ubuntu normally does. 

It's extremely rude to give commands to strangers.

I think Ubuntu has an obligation to provide the software in easily installable forms.  After all they are the ones who want people to use their product.  I couldn't possibly care less if ubuntu became more popular or not.  I'm just saying that their anti-user fundamentalism is hurting them.  If they insist on being fundamentalist - because we all know how important it is to fix that bug where the word "Pidgin" is misspelled on the third Tuesday of each month starting with a J when the tide is up and you're using the liveCD - then they need to be working on finding a way to get new software to the users because that's what users want - **they want software**, not fixes to extremely rare bugs.

---

### Post by maynoth on 2007-05-11
Mateo, 

While I agree with you you should be careful, your just asking for some 12 year old moderator with a god complex to come ban your account. 

I was perm banned in the IRC with my old IP address because I made a statement that I had used automatix2 on over 25 different installations for friends family etc... and never had an issue with it..   they sent me a note telling me I was encouraging people to blow up their computers and banned me LOL... 


I used the %$#@ symbols for effect in a post in which I said it was silly to focus on things like 3d desktops when the basics haven't been taken care of first..  basics like an actual device manager(not viewer), basics like a gui to force your refresh rates and resolutions when xorg doesn't do it right, etc...    anyway because I used the #$#% symbols to give my post more "flavor" and emotion I was given a strike for cursing... how is @#$%$ a curse?



Just today I bumped one of my threads +1 and received another strike...     the mod's here act like 12 year olds with god complexes...  so be careful you might wake up banned if you strike a nerve with the wrong mod..

---

### Post by Mateo on 2007-05-11
I read you the first time.  If some moderator is going to ban me (no reason to think that) for being critical of the way ubuntu has handled pidgin, then so be it but i'm not going to stop stating my opinion out of fear.  And again, I have no reason to think I'm doing anything wrong.

---

### Post by maynoth on 2007-05-11
also getdeb.net has a pre-made pidgin deb for feisty 32bit

---

### Post by Mateo on 2007-05-11
> **maynoth said:**
> also getdeb.net has a pre-made pidgin deb for feisty 32bit

I know, and i have it.  The point is that this is not ideal.  The biggest strength of Ubuntu is the repos.  Now if pidgin releases a new version I'll have to download another deb and install that.  I like automatic updates because I don't even have to think about it.  But now I have to check the pidgin page every few weeks to see if there is a new version?  I'm not an IM enthusiast, I don't want to check the pidgin pages.  I just want the newest version at a reasonable time  (a few days after release at most).  But because of the developers fundamentalist devotion to fixing every minute unimportant bug, which again is anti-user because that's not what the users' priorities are, I now have to check for new versions all the time.  It's completely ridiculous.

---

### Post by prizrak on 2007-05-11
> I don't think anyone's complaining, they just want Pidgin in the official repos. If the devs put it there that's great, if not the people who really want it have to get an unofficial deb and that's fine too, it has been done before. I have for instance installed Freeciv 2.1 beta. I don't think switching to a different distro is a reasonable suggestion.

Actually he has complained quite a bit about the Ubuntu release style before. In his previous posts he made it pretty clear that he thinks Ubuntu has Orwellian anti-user policies when it comes to including new software. 
> On another note, how come Opera is not in the repos? Is it closed or non-free?
It's 100% closed source, although I thought it was in the commercial repository. 
> I agree it is silly to deny users new versions of software (if they want it) and no I don't want to use arch or gentoo, I like the support community ubuntu has.... but this 6 month old software crud is annoying.
Who's denying it? There is a built-in mechanism to install 3rd party software, it even comes with a GUI now (didn't before Dapper I think). If you like Ubuntu you have to take the "6 month old software crud" with it, that was a conscious decision by the developers and the reasoning is well explained on the site. 
> K3B, Open Office, Pidgin, Firefox, Thunderbird, VLC and everything else people actually use on a regular basis should be kept up to date.
How often do they release? Do they really release so often that there is a huge wait? I've been with Ubuntu since Warty and I can tell you the Pidgin situation is pretty rare and is only due to legal reasons because otherwise Gaim 2.0 Final would have been out months ago. For the most part the software doesn't get released so often that you end up waiting for 6 months, it usually comes out to about a month if that. Sometimes what is deemed to be a major improvement gets incorporated anyway. 

> There should be an experimental repo where all the latest and greatest apps (non-beta) are kept current... 6 months for a refresh is too long.. this way the ppl who don't want the latest don't have to have it. everyone is happy...
That is a great idea, I suggest that you create a spec for it on launchpad.net. Get some like minded people to chime in, I'm sure you can find enough people with necessary skills that think it's a good idea. 
> **Mateo said:**
> It's extremely rude to give commands to strangers.

I think Ubuntu has an obligation to provide the software in easily installable forms.  After all they are the ones who want people to use their product.  I couldn't possibly care less if ubuntu became more popular or not.  I'm just saying that their anti-user fundamentalism is hurting them.  If they insist on being fundamentalist - because we all know how important it is to fix that bug where the word "Pidgin" is misspelled on the third Tuesday of each month starting with a J when the tide is up and you're using the liveCD - then they need to be working on finding a way to get new software to the users because that's what users want - **they want software**, not fixes to extremely rare bugs.

How do you know what users want? Seriously you have claimed that I am being rude by giving you commands (no such thing, in fact I tried my best to be respectful in my post). Yet you seem to claim to know what users want. You are saying that "anti-user fundamentalism" is hurting Ubuntu yet Ubuntu is getting more popular not less. This would suggest that users in fact like Ubuntu and don't have a problem with the 6 month update cycle. Where do you get the idea that users care more about new software than bug fixes*? I honestly don't think that you are qualified to speak for the "users". 

*If we ONLY had the kinds of bugs you mentioned Ubuntu would be the best written piece of software on the platet. There are quite a few bugs that are being worked out, that affect alot of people and are quite serious.

Ubuntu devs don't really have any responsibility to the users if you look at it fairly. However they provide a working and reasonably up-to-date OS. The current IM client works quite well and is really not missing any killer features. 

> I was perm banned in the IRC with my old IP address because I made a statement that I had used automatix2 on over 25 different installations for friends family etc... and never had an issue with it.. they sent me a note telling me I was encouraging people to blow up their computers and banned me LOL...
Yeah they don't like Automatix much for some reason, I think Arnieboy stepped on some toes with his software.

---

### Post by carlosqueso on 2007-05-11
Just a thought...if you used any comercial software, you probably wouldn't update for a name change and some minor UI improvements because it would be too expensive.

---

### Post by Mateo on 2007-05-11
> **prizrak said:**
> How often do they release? Do they really release so often that there is a huge wait? I've been with Ubuntu since Warty and I can tell you the Pidgin situation is pretty rare and is only due to legal reasons because otherwise Gaim 2.0 Final would have been out months ago. For the most part the software doesn't get released so often that you end up waiting for 6 months, it usually comes out to about a month if that. Sometimes what is deemed to be a major improvement gets incorporated anyway. 

Maybe for the extremely popular software, but for others the releases are extremely delayed.  Rtorrent is 4 or 5 releases behind and hasn't been updated in like 6 months.  The same for Hellanzb, which actually has a major bug in the repo version that has since been fixed.  It's 2 or 3 releases behind, the repo version was released in October.

---

### Post by prizrak on 2007-05-11
> **Mateo said:**
> Maybe for the extremely popular software, but for others the releases are extremely delayed.  Rtorrent is 4 or 5 releases behind and hasn't been updated in like 6 months.  The same for Hellanzb, which actually has a major bug in the repo version that has since been fixed.  It's 2 or 3 releases behind, the repo version was released in October.

Have you considered filing a bug report? If Hellanzb does have a serious bug then there could be a good chance that it will get updated if mentioned. Does Rtorrent have any major improvements? Also you need to consider where the software is housed, remember Universe is community maintained. In fact I'm sure they would appreciate your help if you offered it.

---

### Post by Mateo on 2007-05-11
> **prizrak said:**
> How do you know what users want? Seriously you have claimed that I am being rude by giving you commands (no such thing, in fact I tried my best to be respectful in my post). 

You are being rude.  using command words to strangers is rude.  If you say "do this, do that", that's rude.  Saying something like  "this problem could be fixed if people did this and that" is not rude, since it's 3rd person.  Furthermore, the topic is not **me** , the topic is Ubuntu's handling of the pidgin release, so we shouldn't be talking about individual users at all.

---

### Post by Mateo on 2007-05-11
> **prizrak said:**
> Have you considered filing a bug report? If Hellanzb does have a serious bug then there could be a good chance that it will get updated if mentioned. Does Rtorrent have any major improvements? Also you need to consider where the software is housed, remember Universe is community maintained. In fact I'm sure they would appreciate your help if you offered it.

I have filed tons of bugs and in my experience nothing is done.  In fact, I think only 1 bug I have ever reported has ever been fixed, and in that case I wasn't the only person who filed the bug.  In fact, getting anyone to even reply to a bug report is extremely difficult

Furthermore, I do not think any software should ever go even **2 releases** without having a new version in the repositories.  You shouldn't only put a new version in the repositories to fix major bugs.  People like the new features, and yes both pieces of software in question have major new features.  I'm not going to spend all of my personal time trying to get through to these people unless they put me on their payroll.

And again, let's stay on topic, the topic isn't Mateo or any other user, it's Ubuntu's handling of the pidgin release.

---

### Post by TravisNewman on 2007-05-11
I would advise any members who  have issues with the staff here to please take the situation to the Resolution Center if you feel something has been handled incorrectly.

Otherwise, this has just turned into a flame war. The question the OP asked has been answered.

---

