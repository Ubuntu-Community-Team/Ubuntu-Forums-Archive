---
title: "Firefox 3.6.4 coming to Hardy, Jaunty, Karmic and Lucid"
date: 2010-06-03
forum: The Cafe
---

### Post by lovinglinux on 2010-06-03
Not so long ago, Mozilla announced a Firefox update policy change that led Ubuntu developers to [review how Firefox is updated in Ubuntu](https://blueprints.edge.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model).

Basically, Mozilla is updating Firefox more frequently and pushing some feature changes as minor updates. For example, Firefox 3.7 would bring a [new feature](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1450678) that prevents the browser from crashing when viewing Flash and Silverlight video content. This is achieved by isolating the plugin execution in a new process, instead of executing it as part of firefox-bin. It is a great feature. Anyway, this will no longer be a new feature in Firefox 3.7. Instead, Mozilla pushed this feature to Firefox 3.6.4 (currently at the release candidate stage) and Firefox 3.7 will become Firefox 4. Additionally Mozilla is now [dropping support for Firefox 3](http://www.h-online.com/news/item/Firefox-3-0-approaches-end-of-life-956587.html).

There was a lot of discussions here in the forums when the blueprint became public, but I guess most of us mortals didn't know for sure when this would happen and if this would also be applied to Hardy and Jaunty. This is particularly important, since these Ubuntu releases already reached the last version of Firefox 3.x series.

Well, the wait is over. According to [this announcement](http://ubuntuforums.org/showthread.php?t=1500594) in TheFridge, Firefox 3.6.4, which will be released next week, will be rolled out to Hardy, Jaunty, Karmic and obviously Lucid.

Any Hardy user interested in testing the new version should read the [original announcement](http://ubuntuforums.org/showthread.php?t=1500594) and [these instructions](http://ubuntuforums.org/showthread.php?t=1500593). It is strongly advised to use a Virtual Machine or a new separate Ubuntu installation. Do not use it on a production environment.

Testing versions for Jaunty and Karmic will be available soon.

I would like to thank [wojox](http://ubuntuforums.org/member.php?u=802919), who spotted the original announcement and sent me a PM. I apologize to the moderators if this is considered a double-post-like thread, but I thought it would interesting to share this info on the Community Cafe.

---

### Post by philinux on 2010-06-03
Good news indeed. ;)

---

### Post by philinux on 2010-06-03
Good news indeed. ;)

I did catch the new about firefox updates in ubuntu. Step in the right direction.

---

### Post by lovinglinux on 2010-06-03
> **philinux said:**
> Step in the right direction.

Indeed. It would be really awesome if they could release the new version simultaneously with Mozilla official release. This would certainly end the drama about Firefox updates.

---

### Post by Merk42 on 2010-06-03
> **lovinglinux said:**
> Indeed. It would be really awesome if they could release the new version simultaneously with Mozilla official release. This would certainly end the drama about Firefox updates.

Doubtful

When Firefox 4 is released, I'd imagine 3.6.X to still be supported for some time, so you'll still get threads of "How do I upgrade firefox to the latest version"

---

### Post by lovinglinux on 2010-06-03
> **Merk42 said:**
> Doubtful

When Firefox 4 is released, I'd imagine 3.6.X to still be supported for some time, so you'll still get threads of "How do I upgrade firefox to the latest version"

You are right, I forgot about major releases. :)

---

### Post by mkvnmtr on 2010-06-03
I understand the thinking behind the Ubuntu release cycle but I have been using the latest release and sometimes an alfa release for the four browsers I use for some time. They all work fine and it is easy to do.

---

### Post by lovinglinux on 2010-06-03
> **mkvnmtr said:**
> I understand the thinking behind the Ubuntu release cycle but I have been using the latest release and sometimes an alfa release for the four browsers I use for some time. They all work fine and it is easy to do.

I use the latest version downloaded from Mozilla and it works great too. Nevertheless, you need to consider the average user who doesn't want to download and install manually or doesn't have enough familiarity with PPA repositories.

---

### Post by wojox on 2010-06-04
> **mkvnmtr said:**
> I understand the thinking behind the Ubuntu release cycle but I have been using the latest release and sometimes an alfa release for the four browsers I use for some time. They all work fine and it is easy to do.

Really? You can use an alpha and still get the add-ons to work.

Nice write up and thread lovinglinux. It's good to spread the word. :P

---

### Post by lovinglinux on 2010-06-04
> **wojox said:**
> Nice write up and thread lovinglinux. It's good to spread the word. :P

Thanks wojox. Also thanks again for sending me the link to the original thread

---

### Post by wojox on 2010-06-04
> **lovinglinux said:**
> Thanks wojox. Also thanks again for sending me the link to the original thread

Your welcome my friend. I knew if anybody would be interested in that post it would be you FTW.

---

### Post by lovinglinux on 2010-06-04
> **wojox said:**
> Your welcome my friend. I knew if anybody would be interested in that post it would be you FTW.

True :)

---

### Post by kcbnac on 2010-06-24
> **mkvnmtr said:**
> I understand the thinking behind the Ubuntu release cycle but I have been using the latest release and sometimes an alfa release for the four browsers I use for some time. They all work fine and it is easy to do.

Personally, meh.  I used to be on the alpha wagon...I'm fine with waiting 3 days past actual release, it gives me time to have the gaming rig (Windows) discover the major bugs before I update the primary machine (Ubuntu, laptop) and break something.  Then any massive showstoppers are found and (generally) fixed anyways :-D

---

### Post by Jigen on 2010-07-06
At the moment it seems that the upgrade to 3.6 is not available for JJ and KK. I use JJ and there is still that ugly, unsupported 3.0 version #-o Any news about that?

---

### Post by lovinglinux on 2010-07-07
> **Jigen said:**
> At the moment it seems that the upgrade to 3.6 is not available for JJ and KK. I use JJ and there is still that ugly, unsupported 3.0 version #-o Any news about that?

No news. It seems for now it is only available for Hardy.

You could download it manually from Mozilla and install on /opt if you don't want to wait.

See the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) tutorial.

---

### Post by mobilediesel on 2010-07-07
I received the update to Firefox 3.6.6 in Ubuntu Hardy a few days ago. How do I go back to the 3.0.whatever? If I wanted a browser that crashed this often I would be running Windows.

---

### Post by lovinglinux on 2010-07-07
> **mobilediesel said:**
> I received the update to Firefox 3.6.6 in Ubuntu Hardy a few days ago. How do I go back to the 3.0.whatever? If I wanted a browser that crashed this often I would be running Windows.

I don't think you can and you shouldn't, since Firefox 3 is no longer supported. Anyway, you could try Synaptic. See if there is a firefox-3.0 package and if the version is not 3.6.6. If yes, then you could remove firefox and install that.

When does it crashes?

First update to make sure you have the latest patches. Then try to delete the file **secmod.db** from your Firefox profile (i.e. ~/.mozilla/firefox/<profilename>/secmod.db).

If that doesn't help, try to create a new profile.

See these:

[http://firefox-tutorials.blogspot.com/2010/05/profiles.html](http://firefox-tutorials.blogspot.com/2010/05/profiles.html)
[http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

---

### Post by mobilediesel on 2010-07-07
> **lovinglinux said:**
> I don't think you can and you shouldn't, since Firefox 3 is no longer supported. Anyway, you could try Synaptic. See if there is a firefox-3.0 package and if the version is not 3.6.6. If yes, then you could remove firefox and install that.

When does it crashes?
Synaptic only shows 3.6.6 and 3.0b5.
Firefox is slow and unstable since the update to 3.6.6. It takes longer to start up and after some seemingly random interval, it locks up so that I have to go to the terminal and kill it.
> **lovinglinux said:**
> First update to make sure you have the latest patches. Then try to delete the file **secmod.db** from your Firefox profile (i.e. ~/.mozilla/firefox/<profilename>/secmod.db).

If that doesn't help, try to create a new profile.

See these:

[http://firefox-tutorials.blogspot.com/2010/05/profiles.html](http://firefox-tutorials.blogspot.com/2010/05/profiles.html)
[http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

I did previously try 3.5 via the Ubuntuzilla script. I uninstalled 3.5 for the same reason I want to uninstall 3.6.6. Could that have left behind some settings that are interfering with 3.6.6?

---

### Post by Jigen on 2010-07-07
> **lovinglinux said:**
> No news. It seems for now it is only available for Hardy.

You could download it manually from Mozilla and install on /opt if you don't want to wait.

See the [[COLOR=Sienna]**Installing Other Versions**[/COLOR]]("http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html") tutorial.

Thanks. Of all the proposed methods, I have chosen the ubuntuzilla's one, which seemed to be the easiest way. However, fonts appearance is bad, how can I fix it?:confused:

---

### Post by lovinglinux on 2010-07-07
> **mobilediesel said:**
> Synaptic only shows 3.6.6 and 3.0b5.
Firefox is slow and unstable since the update to 3.6.6. It takes longer to start up and after some seemingly random interval, it locks up so that I have to go to the terminal and kill it.

I did previously try 3.5 via the Ubuntuzilla script. I uninstalled 3.5 for the same reason I want to uninstall 3.6.6. Could that have left behind some settings that are interfering with 3.6.6?

Yes. Although Firefox handles updates pretty well in regard to profiles, there is always the possibility of leaving behind some settings that are sub-optimal for the new version or a corrupted file that no longer works as expected.

Start a new profile and see how it goes. I'm using Firefox 3.6.4 and 3.6.6 on Lucid and it works flawlessly. Anything above Firefox 3.0.x has much better performance.

Also check my optimization tutorials.

---

### Post by lovinglinux on 2010-07-07
> **Jigen said:**
> Thanks. Of all the proposed methods, I have chosen the ubuntuzilla's one, which seemed to be the easiest way. However, fonts appearance is bad, how can I fix it?:confused:

[http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html)

---

### Post by mobilediesel on 2010-07-07
> **lovinglinux said:**
> Anything above Firefox 3.0.x has much better performance.

So far I have found the opposite to be true. I really, really miss 3.0.19 now. I have to kill 3.6.6 several times a day.

Anyone have the .deb file for 3.0.19? 3.6.6 is just awful.

---

### Post by Danny Dubya on 2010-07-07
Right-clicking on some Flash applets causes my Firefox to freeze up entirely. Anyone else on FF 3.6.6 experiencing this? I haven't noticed any random lockups or a slower start time, but that particular issue started occurring to me after upgrading from 3.6.3.

---

### Post by lovinglinux on 2010-07-07
> **Danny Dubya said:**
> Right-clicking on some Flash applets causes my Firefox to freeze up entirely. Anyone else on FF 3.6.6 experiencing this? I haven't noticed any random lockups or a slower start time, but that particular issue started occurring to me after upgrading from 3.6.3.

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by lovinglinux on 2010-07-07
Nevermind

---

### Post by lovinglinux on 2010-07-07
> **mobilediesel said:**
> So far I have found the opposite to be true. I really, really miss 3.0.19 now. I have to kill 3.6.6 several times a day.

Anyone have the .deb file for 3.0.19? 3.6.6 is just awful.

Firefox 3.6.6 is not awful. In fact it is an excellent version. The problem is the combination of Firefox 3.6.6 and Ubuntu 8.04.

---

### Post by mobilediesel on 2010-07-07
> **lovinglinux said:**
> Firefox 3.6.6 is not awful. In fact it is an excellent version. The problem is the combination of Firefox 3.6.6 and Ubuntu 8.04.

If that is a known problem, the decision to update Ubuntu 8.04 to use Firefox 3.6.6 was stupid. 8.04 is a Long Term Support version. Pushing an update that is known to cause problems is not the right thing to do for LTS.

---

### Post by Danny Dubya on 2010-07-07
> **lovinglinux said:**
> Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

    File: /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r53

I'm on 64-bit Lucid.

---

### Post by lovinglinux on 2010-07-07
> **mobilediesel said:**
> If that is a known problem, the decision to update Ubuntu 8.04 to use Firefox 3.6.6 was stupid. 8.04 is a Long Term Support version. Pushing an update that is known to cause problems is not the right thing to do for LTS.

It wasn't a stupid decision. Firefox 3.0 is no longer supported by Mozilla, so would you prefer to be stuck with a version without security patches or get a new supported version?

The updates were not known to cause problems. The Ubuntu developers made this version available through a PPA before releasing it (see first post) and asked for bug reports. If nobody tested it, than what can they do. The problems are surfacing now. I'm not sure if it is widespread tho. I have seen several complains from Hardy users, so I'm assuming there is something affecting Ubuntu 8.04.

---

### Post by lovinglinux on 2010-07-07
> **Danny Dubya said:**
> File: /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r53

I'm on 64-bit Lucid.

Open npviewer file with the command below:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Then add the following line before the last line of that file:

```
export GDK_NATIVE_WINDOWS=1
```

The file content should look like this:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```

Save the file and restart the browser.

---

### Post by mobilediesel on 2010-07-08
> **lovinglinux said:**
> It wasn't a stupid decision. Firefox 3.0 is no longer supported by Mozilla, so would you prefer to be stuck with a version without security patches or get a new supported version?
If it's primarily about security patches it's like installing a car alarm that that interferes with the throttle preventing you from accelerating normally.
> **lovinglinux said:**
> The updates were not known to cause problems. The Ubuntu developers made this version available through a PPA before releasing it (see first post) and asked for bug reports. If nobody tested it, than what can they do. The problems are surfacing now. I'm not sure if it is widespread tho. I have seen several complains from Hardy users, so I'm assuming there is something affecting Ubuntu 8.04.
Before they do things like that there needs to be a place to post about it where more people can see it to do the testing.

---

### Post by lovinglinux on 2010-07-08
> **mobilediesel said:**
> If it's primarily about security patches it's like installing a car alarm that that interferes with the throttle preventing you from accelerating normally.

Before they do things like that there needs to be a place to post about it where more people can see it to do the testing.

It was posted on The Fridge and I "double posted" here in the Cafe.

---

### Post by lovinglinux on 2010-07-23
Firefox 3.6.7 has been made available for Hardy, Jaunty, Karmic and Lucid. 

[http://packages.ubuntu.com/search?searchon=names&keywords=firefox](http://packages.ubuntu.com/search?searchon=names&keywords=firefox)

---

### Post by linas on 2010-07-23
Yes, 'apt-get upgrade' last night on jaunty resulted in firefox 3.6.7 being installed on my system. After restarting firefox, youtube stopped working :-(  Posted details here: [http://ubuntuforums.org/showthread.php?t=1537301](http://ubuntuforums.org/showthread.php?t=1537301)

---

### Post by NormanFLinux on 2010-07-24
Mozilla released a patch to solve a stability issue affecting certain plugins with Firefox by releasing 3.6.8 Friday!

---

### Post by lovinglinux on 2010-07-24
> **NormanFLinux said:**
> Mozilla released a patch to solve a stability issue affecting certain plugins with Firefox by releasing 3.6.8 Friday!

I just hope there isn't a deluge of threads complaining about flash issues until Canonical updates the repos to 3.6.8.

---

### Post by NormanFLinux on 2010-07-24
Keeping Firefox/Thunderbird updated between Ubuntu spring and fall releases is possible with Ubuntuzilla. With a simple command line script, one can update to the latest Mozilla version on all Ubuntu based operating systems.

---

### Post by lovinglinux on 2010-07-24
> **NormanFLinux said:**
> Keeping Firefox/Thunderbird updated between Ubuntu spring and fall releases is possible with Ubuntuzilla. With a simple command line script, one can update to the latest Mozilla version on all Ubuntu based operating systems.

Only if you have a 32bit system. See the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) tutorial.

---

### Post by Rubi1200 on 2010-07-24
> **lovinglinux said:**
> Firefox 3.6.7 has been made available for Hardy, Jaunty, Karmic and Lucid. 

[http://packages.ubuntu.com/search?searchon=names&keywords=firefox](http://packages.ubuntu.com/search?searchon=names&keywords=firefox)

Flawless upgrade for me on Karmic.

Thanks for the info and for your very helpful site.

I hope you don't mind, but when I read posts from people with Firefox issues I often link to your site; I hope that is okay?

Regards,
Rubi1200

---

### Post by lovinglinux on 2010-07-24
> **Rubi1200 said:**
> Flawless upgrade for me on Karmic.

Thanks for the info and for your very helpful site.

You are welcome.

> **Rubi1200 said:**
> I hope you don't mind, but when I read posts from people with Firefox issues I often link to your site; I hope that is okay?

No problem at all. The site was created to help Ubuntu Firefox users, so I appreciate when other users link to it.

---

### Post by mobilediesel on 2010-07-25
> **lovinglinux said:**
> The site was created to help Ubuntu Firefox users, so I appreciate when other users link to it.

I just tried [Swiftfox 3.6.7]("http://getswiftfox.com/deb.htm") linked from [your site]("http://firefox-tutorials.blogspot.com/") and it does seem to be in improvement over Firefox. I might have to try [compiling]("http://firefox-tutorials.blogspot.com/2010/07/compiling-firefox.html") it myself to see what I can do with it.

---

### Post by lovinglinux on 2010-07-25
> **mobilediesel said:**
> I just tried [Swiftfox 3.6.7]("http://getswiftfox.com/deb.htm") linked from [your site]("http://firefox-tutorials.blogspot.com/") and it does seem to be in improvement over Firefox. I might have to try [compiling]("http://firefox-tutorials.blogspot.com/2010/07/compiling-firefox.html") it myself to see what I can do with it.

You should see Firefox 4.0. It beats that Swiftfox with the eyes closed, even the vanilla version. Unfortunately, is too soon to use it, specially if you use too many extensions.

---

### Post by mobilediesel on 2010-07-25
> **lovinglinux said:**
> You should see Firefox 4.0. It beats that Swiftfox with the eyes closed, even the vanilla version. Unfortunately, is too soon to use it, specially if you use too many extensions.

I would try 4.0 if my job didn't require an extension that they wrote. Luckily it actually seems to work better with Swiftfox than it did with Firefox.

---

### Post by lovinglinux on 2010-07-25
> **mobilediesel said:**
> I would try 4.0 if my job didn't require an extension that they wrote. Luckily it actually seems to work better with Swiftfox than it did with Firefox.

It usually does. I don't like to use it tho, because is closed source and because you have to wait for them to update. I prefer to get my fresh new versions from Mozilla.

---

### Post by Mulenmar on 2010-07-25
> **lovinglinux said:**
> . . .is closed source and because you have to wait for them to update.

Not anymore, see [http://www.getswiftfox.com/source.htm](http://www.getswiftfox.com/source.htm)

Note that it's open source, not free. 
> 
SWIFTFOX LICENSE AND RESTRICTIONS 
       -------------------------------------

1. Swiftfox binaries are not distributed under the MPL 
   license and are not freely distributable.  [B]Swiftfox 
   is licensed only to the user that downloads the 
   binary from getswiftfox.com and no distribution 
   to other parties is allowable under this license.[/B]  
   Download of any binary from getswiftfox.com 
   constitutes acceptance of these terms.

2. Swiftfox source code is available for download from 
   getswiftfox.com which is in keeping with the 
   requirements set forth by mozilla.org.  This source 
   code includes all patches that have been applied to 
   create Swiftfox other than those that involve 
   branding.  Swiftfox source code compiles correctly 
   on my build machine.  No warranty or support is 
   provided for builders.

3. Source code only is licensed MPL as required by 
   mozilla.org [http://www.mozilla.org/MPL/MPL-1.1.txt](http://www.mozilla.org/MPL/MPL-1.1.txt)
   Binaries are not MPL and no redistribution of 
   binaries is allowable under any circumstances.

4. Swiftfox as a brand is trademark Jason Halme 
   <jason@getswiftfox.com> and as such builders must 
   either use the default unofficial build name as 
   supplied by mozilla.org or create a name of your 
   choosing other than Swiftfox.  No Swiftfox branding 
   is allowable in unofficial builds.

5. These license restrictions are in place to protect 
   the integrity of Swiftfox and to ensure that when 
   users of the community download and install Swiftfox 
   they can be assured they are getting an official 
   build that has not been altered in anyway that might 
   include malicious content.




All rights reserved.  
Swiftfox (tm) is trademark Jason Halme 
<jason@getswiftfox.com>


---

### Post by lovinglinux on 2010-07-25
> **Mulenmar said:**
> Not anymore, see [http://www.getswiftfox.com/source.htm](http://www.getswiftfox.com/source.htm)

Note that it's open source, not free.

Cool. Thanks for the heads up.

---

### Post by andrewabc on 2010-07-25
> **mobilediesel said:**
> I just tried [Swiftfox 3.6.7]("http://getswiftfox.com/deb.htm") linked from [your site]("http://firefox-tutorials.blogspot.com/") and it does seem to be in improvement over Firefox. I might have to try [compiling]("http://firefox-tutorials.blogspot.com/2010/07/compiling-firefox.html") it myself to see what I can do with it.

I presume you used your old profile with it?
Otherwise if using new profile that is why it would seem faster and not a fair comparison.

---

### Post by Old Marcus on 2010-07-26
Swiftfox source code is is open source by requirement of the MPL/GPL, but the compiled binaries aren't, and as far as I know, never have been.

---

### Post by mobilediesel on 2010-07-26
> **andrewabc said:**
> I presume you used your old profile with it?
Otherwise if using new profile that is why it would seem faster and not a fair comparison.

Yeah it used the old profile. Maybe I should try a new profile to see if it's any faster.

---

### Post by lovinglinux on 2010-07-26
Firefox 3.6.8 is now available through the official repositories.

---

