---
title: "update overwrote Dan's Guardian settings?"
date: 2007-02-15
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2007-02-15
Is the update supposed to overwrite the Dan's guardian settings?  I had to re-set it up again.  I tried to download a zip file and was denied, I was surprised.  It doesn't take long to go back and re-setup the way I had it, but just wondered if it was supposed to do that?  Thanks.

Shane

---

### Post by mhancoc7 on 2007-02-16
> **shane2peru said:**
> Is the update supposed to overwrite the Dan's guardian settings?  I had to re-set it up again.  I tried to download a zip file and was denied, I was surprised.  It doesn't take long to go back and re-setup the way I had it, but just wondered if it was supposed to do that?  Thanks.

Shane

Yes, that does happen during an upgrade. I am working to find a way to not have this happen. The reason for this is dansguardian is actually removed and reinstalled during the upgrade or conversion. This became necessary because some users where having dansguardian getting mis-configured during the upgrade process. The only way that I have found to avoid that is to reinstall it which does reset the settings. 

I will take a closer look at this and see if I can fix this for the next release.

God Bless, Jereme

---

### Post by shane2peru on 2007-02-16
Jereme,

  I just wanted to let you know in case you were not aware of it.  I did notice it uninstalled and installed dansguardian too.  But that makes sense what you say.  When it is removed is it purged?  If not I was under the impression that the config files would stay.  I could be wrong.  It isn't a real big deal, but a minor detail to work out.  
  I appreciate all the work you have put into this I really like Ubuntu CE, and many times it is what keeps me with Ubuntu to be honest with you.  At times I want to check out other distros, but I just love having Ubuntu Christian Edition, it is the only distro with a CE, and I think really enhances the Ubuntu community.  Thanks.

Shane

---

### Post by apjone on 2007-02-16
Another important leason about backing up my friend

Also, DG does change and add extra option to config. Im on a self rolled 2.9.8.1 with A/D support

---

### Post by mhancoc7 on 2007-02-16
Hi Shane,
Thanks for your kind words. I am glad to hear how much you are enjoying Ubuntu CE.

Yes it is set to purge. I could probably change that without causing problems. However, the next release is going to have some changes to the default conf files. So they will need to be overwritten. I will have to think on this one.

It may be one of the many trade offs that has to be made. :)

Have you taken a look at the latest beta version of the Dansguardian GUI?
[http://www.ubuntuforums.org/showthread.php?t=355935](http://www.ubuntuforums.org/showthread.php?t=355935)

God Bless, Jereme

---

### Post by shane2peru on 2007-02-16
yeah, it is a minor issue, just wanted to bring it to attention in case it had been overlooked.  Of course if you don't purge and you had mentioned that some have had problems in the past, it could still save the problems.  So purge may be your best route.  

Very nice look on the new GUI for DG.  Looks very nice.  I will hold off for the official release.  I used to run beta stuff and try lots of things, but I started only using Ubuntu, and no longer have Windows, so if things get really messed up, it is more of a pain to re-install and setup again, or restore.  I have found that restoring doesn't always prove to be fail proof.  I do back up regularly though.  Maybe some day I will have a Desktop with more space and can play around a little more with trial things, and other distros.  Until then, I'll have to stick to the stable stuff.  :)  Thanks for the info. 

Shane

---

### Post by mhancoc7 on 2007-02-16
> **shane2peru said:**
> yeah, it is a minor issue, just wanted to bring it to attention in case it had been overlooked.  Of course if you don't purge and you had mentioned that some have had problems in the past, it could still save the problems.  So purge may be your best route.  

Very nice look on the new GUI for DG.  Looks very nice.  I will hold off for the official release.  I used to run beta stuff and try lots of things, but I started only using Ubuntu, and no longer have Windows, so if things get really messed up, it is more of a pain to re-install and setup again, or restore.  I have found that restoring doesn't always prove to be fail proof.  I do back up regularly though.  Maybe some day I will have a Desktop with more space and can play around a little more with trial things, and other distros.  Until then, I'll have to stick to the stable stuff.  :)  Thanks for the info. 

Shane

I totally understand. I get myself in trouble all the time with beta stuff. :)

Thanks for letting me know about your experience with the upgrade_me script. It really helps to get good quality feedback.

God Bless, Jereme

---

