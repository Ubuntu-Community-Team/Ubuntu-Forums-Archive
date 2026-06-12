---
title: "Parental Controls"
date: 2008-02-12
forum: Ubuntu Christian Edition
---

### Post by dardack on 2008-02-12
So I've noticed that CE comes with parental controls.  I also noticed a thread regarding accountability.  Few things:

Is CE close enough to regular Ubuntu to run what I normally run?

Can the GUI/Dansguardian/Filter/etc. be run on a password only my wife knows, and still have access to the SU when I need it for other things?  

How integrated is the parental controls?  Is it possible to make it so it can't be uninstalled?  

Do you use a known blacklist?  If so how often is it updated?

Does it also filter based on other things?  Ie. words, pictures, etc.?
(Kind of like covenant eyes filter part)

It's kinda late, i did try searching for all of this first, so I apologize if I missed the answers somewhere.

---

### Post by Ek0nomik on 2008-02-12
> **dardack said:**
> So I've noticed that CE comes with parental controls.  I also noticed a thread regarding accountability.  Few things:

Is CE close enough to regular Ubuntu to run what I normally run?

Can the GUI/Dansguardian/Filter/etc. be run on a password only my wife knows, and still have access to the SU when I need it for other things?  

How integrated is the parental controls?  Is it possible to make it so it can't be uninstalled?  

Do you use a known blacklist?  If so how often is it updated?

Does it also filter based on other things?  Ie. words, pictures, etc.?
(Kind of like covenant eyes filter part)

It's kinda late, i did try searching for all of this first, so I apologize if I missed the answers somewhere.

As far as I know, the Christian Edition is *very* similar to regular Ubuntu.  It just includes an additional software stack.

I don't know what the parental controls are called because I have never ran the CE.  Does it have a specific name?  Either way, it won't be able to be removed unless your son or daughter have the root password because software can only be installed as root.  Ex: sudo apt-get remove package.name

Regarding the filtering and blacklist, I presume it uses some default settings.  Perhaps it contacts a third party site for the blacklist file.  I wouldn't know how often it's updated though.  I'd suggest playing around with the preferences and seeing how it is setup, and then come back with some more information.  Hopefully I was able to offer some insight.  :)

---

### Post by dardack on 2008-02-12
Well it's kind of for me.  So i want sudo for some stuff but don't want to be able to alter the parental controls or turn off dans guardian?

---

### Post by Ek0nomik on 2008-02-12
> **dardack said:**
> Well it's kind of for me.  So i want sudo for some stuff but don't want to be able to alter the parental controls or turn off dans guardian?

You can keep the sudo password a secret from whoever you are trying to restrict.

---

### Post by dardack on 2008-02-14
I think that there is some mis communication.  I want One sudo password for everything EXCEPT Dansguardian/filtering/etc.  And than one to control that that will be secret.

---

### Post by gigaferz on 2008-02-15
my 2 cents here.

well i was shocked when i found out the sites that were on the browser....

I searched here,but i  didnt find a straight answr, so  i found this:

[https://addons.mozilla.org/en-US/firefox/addon/1803](https://addons.mozilla.org/en-US/firefox/addon/1803)

I know is not all that,like many people want but so far ive been testing it with all my,,uhmm,knowledge and its been blocking all of them...

---

### Post by urukrama on 2008-02-16
> **dardack said:**
> I think that there is some mis communication.  I want One sudo password for everything EXCEPT Dansguardian/filtering/etc.  And than one to control that that will be secret.

Dardack, this question comes up regularly, and (as far as I know) it is not possible to do so. In theory it should be possible to set some complex permissions in the sudoers file, but haven't heard of anyone that managed to get that to work.

---

### Post by shane2peru on 2008-02-16
Dardack,

What you want is this:

[http://ubuntuforums.org/showthread.php?t=487520](http://ubuntuforums.org/showthread.php?t=487520)

OpenDNS will block what you want it to, and your wife can setup a password for it, it is not controlled on your computer, so the sudo is not an issue so much.  Your wife can setup the password, and setup the filter.  She can also log on online and see what sites have been blocked or not blocked.  Personally I think it is a very good solution.  Ours is setup so any computer connected to my network (even wireless) is protected and not allowed to access inappropriate sites.  Check it out at least.

Shane

---

### Post by jonathonblake on 2008-02-17
> **dardack said:**
> 
Is CE close enough to regular Ubuntu to run what I normally run?

Yes.   You don't have to switch to Ubuntu Christian Edition to install DansGurdian.  [I'm assuming that DansGurdian is the program you are asking about.]  

> Can the GUI/Dansguardian/Filter/etc. be run on a password only my wife knows, and still have access to the SU when I need it for other things?  

If you are using DansGuardian as part of a hardware firewall, that everybody's traffic has to go thru, then yes.  The way you do this is give her control of that system, and have her install it on that system.   Then you use your system, doing whatever you want with it.   

> Is it possible to make it so it can't be uninstalled?  

Since you'll need root access to uninstall it,the only person that can uninstall it is the person who knows that password.

> Do you use a known blacklist?  If so how often is it updated?

Whoever installs DansGuardian has to decide which blocklists, if any, to use.   Some of them are free. Some of them are distributed on the honour system.[If you download it more than once, you pay the second and subsequent time.]  Some of them require a payment to download.

The frequency of the updates depends partially upon the list that is selected, and how often the user wants to run the update blocklist thing.  

Some lists haven't been updated in years.  Others are updated daily.  Others are updated anywhere between those two extremes.

> Does it also filter based on other things?  Ie. words, pictures, etc.?

DansGuardian can be adjusted to look at ICRA and PICS ratings, and umpteen similar rating schemes. [Most adult orientated sites use at least one, and usually several of those schemes, for defensive reasons.]

It analyzes the words on the site, and can be configured to block the site if a specific threshold score is reached. (You may have to do some configuring here.)

It can also utilize precompiled block lists.  [This is what most of the most of the block lists are for.  They are available for a number of specific categories. New categories emerge monthly. ]

Images.  AFAIK, no content filtering system can determine what a specific graphic is of, and block the site accordingly.   
What DansGuardian does offer, is a way to filter images on Google Image search, that is stricter than those provided by Google.  

xan

jonathon

---

### Post by dailychoices on 2008-05-06
> **urukrama said:**
> Dardack, this question comes up regularly, and (as far as I know) it is not possible to do so. In theory it should be possible to set some complex permissions in the sudoers file, but haven't heard of anyone that managed to get that to work.

I'm not terribly familiar with the sudoers file, but shouldn't you be able to add a simple rule that filters out access to that application, or is it set up that you have to explicitly state what the user does have access to?

---

### Post by milesje on 2008-05-08
[http://sudo.rtin.bz/sudo/man/sudoers.html](http://sudo.rtin.bz/sudo/man/sudoers.html)
is the link to the manual for the sudoers file. You could set up a seperate user group that has a specific Runas_Spec while alows the person who set up the sudoers file to say that a certain user group can only access these files as a certian type of user. So if you set up the Runas_Spec for your new user group to only allows you to run the dans gaurdian app as an operator instead of as root than you can not change the settings of dan gaurding. I have not tested this with dan gaurdian, but I have set up something simular to this with the sudoers file. Give it a try and see what you can do. the site I list above will help a lot in setting up the sudoers file correctly.

---

