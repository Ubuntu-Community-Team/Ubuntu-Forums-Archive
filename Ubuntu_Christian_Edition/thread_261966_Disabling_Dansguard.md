---
title: "Disabling Dansguard"
date: 2006-09-21
forum: Ubuntu Christian Edition
---

### Post by pman on 2006-09-21
Hello all.  I am new to the linux scene and love it, actually.  Until I can get a few files to either migrate or put on a CD/DVD disc i am going to switch over to Ubuntu complete...
  The reason for the post is i am wondering if it is possible to disable Dansguardian (until i figure out how to configure properly).  i had tried it before amd it blocked a lot of sites that weren't questionable (since i have been in linux, it's been reading through various linux sites (mainly staying with the ines with tutorials and news and such) but it would block it out.  Since i am also a Christian i liked the theme-based idea of Ubuntu Christian Edition: the various religious or biblical aspects.  So it's not that i am going to sites (well...:---) ) that are in question, it's kind pf frustrating.  i just did a complete reinstall as i was tinkering with this and that (all kinds of software and desktops and such) kept installing removing and reinstalling :-k 
  Any help would be appreciated.  i have been searching the threads and haven't seen much but still looking.

Pman

---

### Post by honda on 2006-09-21
Hello, I disabled dansguardian by setting my browser to use the tinyproxy directly at port 3128. Normally the firewall is set up to disallow this, but after removing this line in /etc/firehol/firehol.conf it is possible: 

iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

sudo gedit /etc/firehol/firehol.conf
put a # in the beginning of that row: #iptables -t filter ...
then reboot or restart the firewall by:
sudo firehol stop
sudo firehol start

This way only those who figure out to set the browser to use http proxy at port 3128 can bypass the filter, I have it setup like this to be able to have very tight rules for the small kids while still allowing normal use for the rest of the family.

---

### Post by mhancoc7 on 2006-09-21
> **pman said:**
> Hello all.  I am new to the linux scene and love it, actually.  Until I can get a few files to either migrate or put on a CD/DVD disc i am going to switch over to Ubuntu complete...
  The reason for the post is i am wondering if it is possible to disable Dansguardian (until i figure out how to configure properly).  i had tried it before amd it blocked a lot of sites that weren't questionable (since i have been in linux, it's been reading through various linux sites (mainly staying with the ines with tutorials and news and such) but it would block it out.  Since i am also a Christian i liked the theme-based idea of Ubuntu Christian Edition: the various religious or biblical aspects.  So it's not that i am going to sites (well...:---) ) that are in question, it's kind pf frustrating.  i just did a complete reinstall as i was tinkering with this and that (all kinds of software and desktops and such) kept installing removing and reinstalling :-k 
  Any help would be appreciated.  i have been searching the threads and haven't seen much but still looking.

Pman

You can go to Synaptic and do a "Complete Removal" of dansguardian, firehol, clamav, and tinyproxy. That will completely disable the filtering. I also get some sites blocked that should not be. What I did was add a launcher to my panel for the Configure Parental Controls GUI. Now when I get a site that is blocked and should not be I simply click the launcher and add that site to the "Sites Not Filtered". Hope that helps.
Jereme

---

### Post by pman on 2006-09-21
Oops it's Dansguardian, isn't it;) .  So a firewall, an antivirus, and a proxy is bundled with Dansguardian?  Does that mean i'll have to remove all?  i am kind of reticent on disabling all, but may need to as i have only experience with windows stuff.  i know some open source software can and does run on windows (i have or had k-meleon the gimp and various other 'wares).  The only experience i have with a firewall is ZA and that was pretty much point and click "allow or deny."  It did give info on what was trying to get in (or out as the case may be) and it pretty clamped everything down.  The antivirus i recently used was Symantec corparate edition (given to me with the computer).  i have use AVG in the past with good results, both are actually.  i have not however used a proxy.  Always wanted to but looked complicatred, thus never did.  Ironically i am in Linux which is new and complicated.  It is also easier in some respects (mainly b/c of these forums).\\:D/ 
  So amid all my jabbering i think i will, indeed, install the Christian Edition.  i may start with your suggestion mhancoc7 before yours honda.  i am still mulling over which to use.
  Back to my origional querie, though, are they all bundled together, to work together?  Or are they separate entities? (In which case i need to read more on configuring)
  Again thanx for your repies

---

### Post by mhancoc7 on 2006-09-21
> **pman said:**
> Oops it's Dansguardian, isn't it;) .  So a firewall, an antivirus, and a proxy is bundled with Dansguardian?  Does that mean i'll have to remove all?  i am kind of reticent on disabling all, but may need to as i have only experience with windows stuff.  i know some open source software can and does run on windows (i have or had k-meleon the gimp and various other 'wares).  The only experience i have with a firewall is ZA and that was pretty much point and click "allow or deny."  It did give info on what was trying to get in (or out as the case may be) and it pretty clamped everything down.  The antivirus i recently used was Symantec corparate edition (given to me with the computer).  i have use AVG in the past with good results, both are actually.  i have not however used a proxy.  Always wanted to but looked complicatred, thus never did.  Ironically i am in Linux which is new and complicated.  It is also easier in some respects (mainly b/c of these forums).\\:D/ 
  So amid all my jabbering i think i will, indeed, install the Christian Edition.  i may start with your suggestion mhancoc7 before yours honda.  i am still mulling over which to use.
  Back to my origional querie, though, are they all bundled together, to work together?  Or are they separate entities? (In which case i need to read more on configuring)
  Again thanx for your repies

They are seperate programs. You may be able to only "Completely Remove" dansguardian and tinyproxy, however since Linux is really not vulnerable to the same types of virus issues I would simply remove them all.

Jereme

---

### Post by pman on 2006-09-21
Cool Beans!!  One more question.  I could, if need be, install Dansguardian the firewall and/or AV, that is separately, if i went ahead and did a complete removal?  i feel i could be able to get the hang of it better that way.  Sorry for the bother, and thanx again.
 i swear i'll leave you alone.

pman

---

### Post by mhancoc7 on 2006-09-22
> **pman said:**
> Cool Beans!!  One more question.  I could, if need be, install Dansguardian the firewall and/or AV, that is separately, if i went ahead and did a complete removal?  i feel i could be able to get the hang of it better that way.  Sorry for the bother, and thanx again.
 i swear i'll leave you alone.

pman

You are not bothering me at all. I enjoy helping out.

Yes, you can install them later, seperately. The configuration of dansguardian/tinyproxy/firehol is the most challenging part. You can do a search of the forum some suggestions. There are also some (mine included) threads that include an "auto" configure. 

Jereme

---

### Post by chuckn on 2006-09-25
Hi,

Great job on Ubuntu Christian Edition. What a blessing! I've jsut installed in on my laptop, and am planning to install it on the family desktop.

I have a question about dansguardian. Will it work the same it I have multiple users? Each one of my children would like to have their own desktop.

Thanks
Pastor Chuck

---

### Post by mhancoc7 on 2006-09-25
> **chuckn said:**
> Hi,

Great job on Ubuntu Christian Edition. What a blessing! I've jsut installed in on my laptop, and am planning to install it on the family desktop.

I have a question about dansguardian. Will it work the same it I have multiple users? Each one of my children would like to have their own desktop.

Thanks
Pastor Chuck

Thanks, I am glad that you find it useful. 

Yes each user account that you setup will have the same filtering. In fact you should create user accounts for your children so they will not be able to change the filter settings using "sudo". If you have any question just let me know.
God Bless, Jereme

---

### Post by pman on 2006-09-25
Sorry for the long delay mhancoc7 in thanking you for your generosity!  Many thanks for your help.  i have been tweaking and contorting ](*,) my system again, thus, another reinstall.  installed CE again and now enjoying it.  Methinks i will keep everything and go ahead and do as you and honda suggested (though the firewall and AV i will tweak later).
Hopefully i can contribute in the near future.  i have migrated completely to linux :cool: .  Ne'ertheless i still have to dual-boot as my wife says she had enough problems with Windows (she runs an OS at work and is also the computer she cut her teeth with so she will be hard to convince)  i love this system and hoping to learn a lot while on this journey.  Again thanks for the wonderful work you (as well as others in each and all forums) have done to make this experience an enjoyable one.  =D> .  Will chat again in the near future:biggrin:  (i couldn't help the emoticons couldn't find a bowing one)
Peace,
pman

---

### Post by mhancoc7 on 2006-09-26
> **pman said:**
> Sorry for the long delay mhancoc7 in thanking you for your generosity!  Many thanks for your help.  i have been tweaking and contorting ](*,) my system again, thus, another reinstall.  installed CE again and now enjoying it.  Methinks i will keep everything and go ahead and do as you and honda suggested (though the firewall and AV i will tweak later).
Hopefully i can contribute in the near future.  i have migrated completely to linux :cool: .  Ne'ertheless i still have to dual-boot as my wife says she had enough problems with Windows (she runs an OS at work and is also the computer she cut her teeth with so she will be hard to convince)  i love this system and hoping to learn a lot while on this journey.  Again thanks for the wonderful work you (as well as others in each and all forums) have done to make this experience an enjoyable one.  =D> .  Will chat again in the near future:biggrin:  (i couldn't help the emoticons couldn't find a bowing one)
Peace,
pman

Thanks and no problem. I am still trying to convince my wife as well. :)
Jereme

---

