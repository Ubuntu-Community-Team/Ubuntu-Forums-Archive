---
title: "cdimage server not showing correct daily build"
date: 2015-07-01
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2015-07-01
Humm.  Daily build is getting pretty old: 

[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)
wily-desktop-amd64.iso       03-Jun-2015

I've gotten a ton of updates since then.....

---

### Post by kansasnoob on 2015-07-01
> **jerrylamos said:**
> Humm.  Daily build is getting pretty old: 

[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)
wily-desktop-amd64.iso       03-Jun-2015

I've gotten a ton of updates since then.....

That's odd, the images are updated on the QA Tracker:

[http://iso.qa.ubuntu.com/qatracker/milestones/340/builds](http://iso.qa.ubuntu.com/qatracker/milestones/340/builds)

---

### Post by flocculant on 2015-07-02
> **jerrylamos said:**
> Humm.  Daily build is getting pretty old: 

[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)
wily-desktop-amd64.iso       03-Jun-2015

I've gotten a ton of updates since then.....

> **kansasnoob said:**
> That's odd, the images are updated on the QA Tracker:

[http://iso.qa.ubuntu.com/qatracker/milestones/340/builds](http://iso.qa.ubuntu.com/qatracker/milestones/340/builds)

Quickest way to sort that is pop by #ubuntu-quality and ping balloons - people probably don't know the current is not refreshing, also possible that the current is held because of automatic tests failing somewhere - in those cases the daily doesn't update.

---

### Post by mc4man on 2015-07-02
I go to pending (probably same as Qa), not yet automatically tested
[http://cdimage.ubuntu.com/cdimage/daily-live/](http://cdimage.ubuntu.com/cdimage/daily-live/)

---

### Post by flocculant on 2015-07-02
You can see that the build date at Ubuntu Pending 1st July matches the last Latest Build at Jenkins 

[https://jenkins.qa.ubuntu.com/view/Ubiquity/view/All/](https://jenkins.qa.ubuntu.com/view/Ubiquity/view/All/)

This has been occurring off and on since December 2014.

---

### Post by philinux on 2015-07-02
Just been in  irc and messaged Nick Skaggs (ballons)

---

### Post by PaulW2U on 2015-07-02
offtopic posts moved to their own thread

---

### Post by ventrical on 2015-07-02
I got June 30 for lubuntu amd64.iso.

So they are working here.

---

### Post by VMC on 2015-07-02
> **ventrical said:**
> I got June 30 for lubuntu amd64.iso.

So they are working here.

Its now "02-Jul-2015" for Lubuntu, but I think Jerry was referring to Ubuntu.

---

### Post by ventrical on 2015-07-03
> **VMC said:**
> Its now "02-Jul-2015" for Lubuntu, but I think Jerry was referring to Ubuntu.

...and thats another reason why   [http://ubuntuforums.org/showthread.php?t=2281877](http://ubuntuforums.org/showthread.php?t=2281877)  because we are not all psychic :)

Regards..

---

### Post by grahammechanical on 2015-07-03
Automation is fine but it does not always notice when something falls of the conveyor belt.

iso.qa has a section for Ubuntu Desktop (Unity8) and the build version is 20150703 but the link to the download information is blank. I conclude that the build does not actually exist yet. Or these builds are being made but are not yet of a fit state to be released. Or, [answer in one sentence].

Regards.

---

### Post by ventrical on 2015-07-04
> **grahammechanical said:**
> Automation is fine but it does not always notice when something falls of the conveyor belt.

iso.qa has a section for Ubuntu Desktop (Unity8) and the build version is 20150703 but the link to the download information is blank. I conclude that the build does not actually exist yet. Or these builds are being made but are not yet of a fit state to be released. Or, [answer in one sentence].

Regards.

'
[h=2]Unity 8 session start still not working at the moment[/h]from..
[http://news.softpedia.com/news/ubuntu-15-10-wily-werewolf-gets-chromium-43-snappy-images-coming-soon-485484.shtml](http://news.softpedia.com/news/ubuntu-15-10-wily-werewolf-gets-chromium-43-snappy-images-coming-soon-485484.shtml)

---

### Post by jerrylamos on 2015-07-04
> **mc4man said:**
> I go to pending (probably same as Qa), not yet automatically tested
[http://cdimage.ubuntu.com/cdimage/daily-live/](http://cdimage.ubuntu.com/cdimage/daily-live/)

Tried "Pending" on Vivid getting a couple busted vivid's so concluded it wasn't worth my effort.  
Vivid daily build was a bit behind pending but nowhere near a month like Wily.
Couldn't see how to get rsync going on the Wily QA site so just did a download of the whole Wily amd64 ubuntu .iso.  Went pretty quick.  Bookmarked it.

Sometimes I try other flavors like Lubuntu and Next mostly just straight vanilla lately.  
Out of curiosity trying the "free Windows 10" a bit.  Ugh.  Easy to install, gparted resize Win7 down, gparted create a NTFS partition, and install alongside Win 7..........toook a while.  Just to have some vague familiarity with what the industry is talking about.  
On the same PC I've several ubuntu's running off USB SSD just fine, thanks.

---

### Post by philinux on 2015-07-08
Update on this here.

[http://news.softpedia.com/news/ubuntu-15-10-daily-images-haven-t-been-refreshed-in-a-month-486332.shtml](http://news.softpedia.com/news/ubuntu-15-10-daily-images-haven-t-been-refreshed-in-a-month-486332.shtml)

---

### Post by ventrical on 2015-07-08
ubuntu-gnome and lubuntu are showing 6 July and 7 July respectively. Looks like ubuntu-unity desktop  problem only. I speculate that the next current dump will be a major convergence wad thrown into our laps . :)

Regards..

---

### Post by grahammechanical on 2015-07-08
I have been looking at cdimage.com almost every day. I am looking for you know what. Sometimes I think that I have numbers dancing before my eyes. Today I am seeing Ubuntu wily daily image dated 08-July-2015. Same as in Pending. Whereas, Ubuntu current is still 03-june-2015.

A lot of images have to be built every day. Ubuntu core and Snappy Ubuntu core have now been added. And they must be building Ubuntu Snappy Personal ISO images otherwise how would they know that the ISO image loads to a black screen? If human resources are getting stretched it would not be right for the flavours to miss out. 

And another thing, at some point someone will have to test build Snappy versions of the flavours. Just to remove any doubts about that side of things.

Regards.

---

### Post by ventrical on 2015-07-08
I just received an email from Sebastian Bacher and he informs me that , yes, the image from some days ago is bootable to a working desktop but that they did not want to advertise it because it was unstable. So , respecting his request , I will not post his email.

 I can say this: from reading much info and after joining snappy dev mail-list - that the snappy core image is still in very infant stages and they are begging for developers to build on what they have currently stacked in the current image. My assumption is that they took an ubuntu mini .iso and hacked it to conform to the new snappy packages format. The image may have security encryption so that if you try to hack it to be able to fork to a common ubuntu repository with .deb packaging that  it will likely get bricked. The idea is that we have to convert .deb packages to snappy format to be able to run and install something familiar to us like htop, mc or a minimal graphical desktop. The current app , Docker, is a container app that  creates containers and loads images, (something like we were working on with lxc? containers?) @graham .. you might remember more on this - and you can install Docker on snappy core. 

 So I  (unofficially) encourage  you testers to try the current snappy image and use the method of install that I have suggested (to USB) boot from there and test to your hearts content :).

Regards..

---

### Post by ventrical on 2015-07-08
> **grahammechanical said:**
> I have been looking at cdimage.com almost every day. I am looking for you know what. Sometimes I think that I have numbers dancing before my eyes. Today I am seeing Ubuntu wily daily image dated 08-July-2015. Same as in Pending. Whereas, Ubuntu current is still 03-june-2015.

A lot of images have to be built every day. Ubuntu core and Snappy Ubuntu core have now been added. And they must be building Ubuntu Snappy Personal ISO images otherwise how would they know that the ISO image loads to a black screen? 
Regards.

The current *image* amd64 boots to a working desktop. 

Regards..

---

### Post by ventrical on 2015-07-08
> **grahammechanical said:**
> If human resources are getting stretched it would not be right for the flavours to miss out. 

Regards.

I think this is a 'core' issue :) no pun intended :)

Regards..

---

### Post by ventrical on 2015-07-08
From sebastian bacher to ventrical
          
      
                                                            
                          
                         [FONT=Calibri][SIZE=3]  >[SIZE=2][/SIZE] Le 08/07/2015 17:25, ventrical a écrit :
 > > I am a little surprised that no one told us we could boot it and that
 > > they wanted 'testers' to use a kvm (qemu). Some of us at U+1 team have
 > > been waiting for snappy personal, but, now that we can boot the image
 > > we can try to break it there. Thats what we do at development version
 > > qa. We try to bust things as we are asked to do:) (and fix them too) :)
 > 
 > ..snip.. In any case those images
 > started booting to a working desktop some days ago and we want them to
 > stabilize a bit before advertizing them/getting more feedback. We are
 > looking forward having other tests and snap writters though ;-)
 > 
 > Cheers,
 > Sebastien Bacher


[/SIZE][/FONT]

---

### Post by sparker256 on 2015-07-11
Looks like whatever issues [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) had are now resolved. For the last two days it has been updated.

Bill

---

