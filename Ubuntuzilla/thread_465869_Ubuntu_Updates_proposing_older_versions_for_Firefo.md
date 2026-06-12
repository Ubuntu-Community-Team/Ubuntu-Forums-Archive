---
title: "Ubuntu Updates proposing older versions for Firefox and Thunderbird"
date: 2007-06-06
forum: Ubuntuzilla
---

### Post by coolcar on 2007-06-06
Hi There !

I had installed Firefox 2.0.0.3 and Thunderbird 2.0.0.0 some time ago by using nanos scripts. Those work really well.

However I have noticed that Ubuntu is now proposing update of Thunderbird Version 1.5.0.12-0ubuntu0.6.06: Some days ago it had proposed update of firefox and it was a lower version as well.

Have I missed updating some channel in my software preferences ? Why would the updater propose older versions and not propose the latest Firefox 2.0.0.4.

( By the way I was able to update the Firefox to 2.0.0.4 by running terminal command gksudo firefox -& )

Have a great day ( or night )

Coolcar

---

### Post by NilsE on 2007-06-06
I upgraded from Firefox 2.0.0.3 to 2.0.0.4 from the repository.  I didn't notice a lower option out there.  I just checked and 2.0.0.4 is what is in the repository so maybe something funny was going on for a day or so.

I don't use Thunderbird so not sure there.

---

### Post by vanadium on 2007-06-06
The first poster is probably using Ubuntu Edgy. Apparently, with each release of Ubuntu, only minor upgrades for applications are provided. With Ubuntu Edgy, FF 1.5 shipped. Feisty ships with version 2. The policy seems to be one Ubuntu version sticks with its versions of the applications. This policy eliminates the need to do packaging and testing for more than one Ubuntu version at a time. Currently, the Dapper LTS, Edgy and Feisty are the supported versions of Ubuntu, each with their "generation"of applications.

Your option indeed is to install these versions yourself using diffferent sources, and not have update touch these applications. Alternatively, if you want to stick with official ubuntu packages and still have the latest, you would need to upgrade to Ubuntu Feisty.

---

### Post by nanotube on 2007-06-06
according to your profile, you are a dapper user, is that right?
the dapper repositories do not have ff2 and tb2, so you will not be getting those from the repository sources. that's the whole reason we have the install script - because ubuntu only pushes out the minor updates, not the major updates, through the official repositories.
so don't worry about those - let the upgrade, but just keep using the official builds that you have installed using the ubuntuzilla scripts. ;)

alternatively, as vanadium says, if you want to get ff2 from the repos, you can upgrade to feisty - but feisty still doesn't have tb2, anyway. mozilla and ubuntu releases are really not in sync...

---

### Post by aysiu on 2007-06-06
Just to expand on what nanotube said, the script installs the new versions of Firefox and Thunderbird *next to* the ones Ubuntu has installed. So you really have two versions installed (1.5 and 2.0) of each but are using only one.

---

### Post by coolcar on 2007-06-07
Thanks NilsE vanadium nanotube and asiyu

Yes I am on Dapper Drake 6.06 LTS. So looks like I should ignore the updates that Ubuntu is proposing or let it run.

---

### Post by nanotube on 2007-06-07
> **coolcar said:**
> Thanks NilsE vanadium nanotube and asiyu

Yes I am on Dapper Drake 6.06 LTS. So looks like I should ignore the updates that Ubuntu is proposing or let it run.

no harm in letting those updates run, so that they no longer bother you telling that you have updates. :) your default firefox will still remain the version 2.

---

### Post by iteachag on 2007-06-07
I ran into the same problem as the user above.  I am running Feisty Fawn.  I installed TB2.0 and had it running and everything pointed to 2.0.  I let the updates run and now 2.0 will not launch from the launcher and when i go through applications > internet > Thunderbird it launches 1.5.

---

### Post by nanotube on 2007-06-08
> **iteachag said:**
> I ran into the same problem as the user above.  I am running Feisty Fawn.  I installed TB2.0 and had it running and everything pointed to 2.0.  I let the updates run and now 2.0 will not launch from the launcher and when i go through applications > internet > Thunderbird it launches 1.5.

hmm, that's strange... could you please check what your launcher links to (system> preferences>main menu, and find the tb launcher in there)?

could you also post the output of command
```
ls -al /usr/bin/*thund*
```

thanks. :)

---

### Post by iteachag on 2007-06-12
> **nanotube said:**
> hmm, that's strange... could you please check what your launcher links to (system> preferences>main menu, and find the tb launcher in there)?

could you also post the output of command
```
ls -al /usr/bin/*thund*
```

thanks. :)

Here is the output.  

-rwxr-xr-x 1 root root 5193 2007-06-04 07:10 /usr/bin/mozilla-thunderbird

Thanks

---

### Post by nanotube on 2007-06-12
well, from that output it's clear that there are no links to tb2 that's supposed to be sitting in /opt.
i don't know what happened to them... did you use the ubuntuzilla script to do your install of tb2, or did you install it manually? ubuntuzilla creates all the links, and diverts the repositories packages so that upgrading them doesn't mess things up. so my guess is that you did not use ubuntuzilla to install tb2. is that correct?

so please tell me what procedure you followed for installing your tb2, and we'll go from there.

---

