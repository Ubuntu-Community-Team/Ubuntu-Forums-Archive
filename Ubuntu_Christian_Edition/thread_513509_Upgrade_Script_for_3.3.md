---
title: "Upgrade Script for 3.3"
date: 2007-07-30
forum: Ubuntu Christian Edition
---

### Post by kiwidipstick on 2007-07-30
Where can I access this script to update to 3.3 please.
And, how do I do it?
Blessings from a slow learner! James.

---

### Post by mhancoc7 on 2007-07-31
> **kiwidipstick said:**
> Where can I access this script to update to 3.3 please.
And, how do I do it?
Blessings from a slow learner! James.

You can use the convert_me script located here.

[www.mirror.christianubuntu.com](www.mirror.christianubuntu.com)

Once you download the archive you need to extract it and you will find instructions inside.

Please read them carefully. :)

God Bless, Jereme

---

### Post by kiwidipstick on 2007-08-01
Thanks Jereme, the script worked fine.
Blessings to thee, James.
Gal.5:16

---

### Post by stevet-l on 2007-08-02
Yes, thanks Jereme, this *nearly* worked nicely (I used the script to upgrade from 3.1 to 3.3)

I read the disclaimers, and don't expect anything to be done about this, but just for the record...

[LIST]
[*]My desktop background image was taken away (fair enough if thats part of the CE look and feel)
[*]My pre-existing firefox extensions were lost (but are now found cos I backed them up and worked out how to copy them back)
[*]My Evolution mail account details vanished, and I can't find where these used to be.  Looks like I'll have to add these again manually.
[*]I had to kill an apt-get job to get the script to run at all (there was a helpful message)
[/LIST]

all the Best

steve

---

### Post by mhancoc7 on 2007-08-02
> **stevet-l said:**
> Yes, thanks Jereme, this *nearly* worked nicely (I used the script to upgrade from 3.1 to 3.3)

I read the disclaimers, and don't expect anything to be done about this, but just for the record...
[LIST]
[*]My desktop background image was taken away (fair enough if thats part of the CE look and feel)
[*]My pre-existing firefox extensions were lost (but are now found cos I backed them up and worked out how to copy them back)
[*]My Evolution mail account details vanished, and I can't find where these used to be.  Looks like I'll have to add these again manually.
[*]I had to kill an apt-get job to get the script to run at all (there was a helpful message)[/LIST]
all the Best

steve

Thanks for letting me know how it went Steve.

Your Firefox extensions should have been backed up during the conversion. There should be a "backup" folder in your home directory.

I may be able to fix the evolution issue in the next release. Thanks for mentioning that one.

What do you mean when you say you had to kill an apt-get job?

Thanks for your input. It really helps me make this better and better.

God Bless, Jereme

---

### Post by stevet-l on 2007-08-02
> Thanks for letting me know how it went Steve.
No problem.  Glad to be able to contribute.
> 
Your Firefox extensions should have been backed up during the conversion. There should be a "backup" folder in your home directory.
Yes, they were there - that's where i got them back from - so for me it was just a matter of copying [FONT="Courier New"].mozilla/firefox/ubuntuce.default/extensions/[/FONT] back from the backup [FONT="Courier New"]mozilla[/FONT] directory to  the users home  - not sure if thats scriptable from your point of view as you might be overwriting extensions that are part of the new version.
> 
I may be able to fix the evolution issue in the next release. Thanks for mentioning that one.

I've now restored my mail account settings and everything now - from the users home you have to restore [FONT="Courier New"].gconf/apps/evolution/[/FONT] as well as [FONT="Courier New"].evolution/ [/FONT].  Interestingly, the [FONT="Courier New"]gconf/[/FONT] backup created by the upgrade script on my system has files which were empty which shouldn't be.  As it happened I'd created my own backup which had the correct data, but had a job to restore it, because its part of the gconf database.  I think you actually have to have gconf shutdown to restore these files.

> 
What do you mean when you say you had to kill an apt-get job?


When I first tried to run the script, it reported that apt-get was running as a background job (sorry can't remember the exact message now) so I 'kill' ed the corresponding job from a [FONT="Courier New"]ps -ef[/FONT] list and all was well.

Keep up the Good Work

steve

---

### Post by the switch on 2007-08-16
that link doesn't work

---

### Post by mhancoc7 on 2007-08-16
> **the switch said:**
> that link doesn't work

Thanks, it is fixed.

I can't figure out why my redirects keeping getting messed up. :(

Thanks again, Jereme

---

### Post by the switch on 2007-08-19
ok, i ran the upgrade script and rebooted,
now i can't load a web page.
the aptget stuff works, just no websites.

i'm typing to you now usiing a liive cd.  (64Studio).


i'm not too clever yet with Linux and don't know how to fix this,
but i have a feeling it's related to my botched removal of Dansguardian.
i really hate that program...

---

### Post by mhancoc7 on 2007-08-19
> **the switch said:**
> ok, i ran the upgrade script and rebooted,
now i can't load a web page.
the aptget stuff works, just no websites.

i'm typing to you now usiing a liive cd.  (64Studio).


i'm not too clever yet with Linux and don't know how to fix this,
but i have a feeling it's related to my botched removal of Dansguardian.
i really hate that program...

Is your system 64bit? If so that could be the issue as Ubuntu CE does not yet support it fully. Also, it could be the removal of dansguardian. Things can get a little sticky there. I would try to reinstall dansguardian using the script available [here]("http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html") and then simply disable it using the GUI.

Thanks, Jereme

Jereme

---

### Post by the switch on 2007-08-19
> **mhancoc7 said:**
> Is your system 64bit? If so that could be the issue as Ubuntu CE does not yet support it fully. Also, it could be the removal of dansguardian. Things can get a little sticky there. I would try to reinstall dansguardian using the script available [here]("http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html") and then simply disable it using the GUI.

Thanks, Jereme

Jereme


Yes, i have a 64bit,
but when i run the live disc (i am now), Firefox works fine.
so i think the big problem is Dans.
I tried to run the script and it didn't work,
so i used the Synaptic Package Manager and got these errors:

installing:  "...returned runtime error status 1."
complete uninstall:  "...returned runtime error status 127."

ugh.  why??

---

### Post by the switch on 2007-08-21
when will there be a version of Ubuntu CE that is compatible with a 64bit processor?

---

### Post by mhancoc7 on 2007-08-21
> **the switch said:**
> when will there be a version of Ubuntu CE that is compatible with a 64bit processor?

I am not really sure. There has been some testing done by various members of the forums. 

One of the major issues is that I do not use a 64bit processor. Since I am the main developer of the project it is a bit hard to do real testing. Also, some of the packages that are in Ubuntu CE do not seem to work properly in 64bit. 

So to answer your question, I don't really know.

Jereme

---

### Post by the switch on 2007-08-21
> **mhancoc7 said:**
> 
One of the major issues is that I do not use a 64bit processor. 


well it's time to upgrade, dude!
how do we donate to the 64bit processor fund?
do you have a paypal?

---

### Post by mhancoc7 on 2007-08-21
> **the switch said:**
> well it's time to upgrade, dude!
how do we donate to the 64bit processor fund?
do you have a paypal?

Yeah, I have seen them in action, but just have not had the finances to do it. I really like my current laptop. It might be hard to part ways. :(

If you really want to donate to the Ubuntu CE project just go [here]("http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/donations.html"). If you were able to get enough people to donate for a new 64bit laptop then I would start work on the 64bit version as soon as it arrived. :) Just add a note when donating or send me an email to let me know that you want the donation earmarked for the purpose of getting a 64bit edition.

God Bless, Jereme

---

