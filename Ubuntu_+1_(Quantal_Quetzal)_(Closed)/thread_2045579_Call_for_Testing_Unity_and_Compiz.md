---
title: "Call for Testing Unity and Compiz"
date: 2012-08-21
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by balloons on 2012-08-21
Unity testing! This bas been my favorite testing each cycle -- I just love seeing the new stuff come out. A new version of unity has arrived, stock full of compiz fixes. The team has removed metacity completely, and also migrated to gsettings from gconf. The result is removal of unity2d, and the enablement of llvmpipe on unity for those running without hardware acceleration.

The gsettings migration especially needs to be tested, and is the primary testcase. In addition, there are some multi-monitor unity bugs to help triage if you are able. Sadly, I just upgraded to a one monitor display from my dual monitors last cycle, so I can't speak to multi-monitor unity anymore.

Full details on my blog: [http://www.theorangenotebook.com/2012/08/call-for-testing-compiz-unity.html](http://www.theorangenotebook.com/2012/08/call-for-testing-compiz-unity.html)

---

### Post by ventrical on 2012-08-21
Nice work Nick :). I go to your webpage, do all that work and then there is no instruction for the ppa , or at least none that I can see??

:)

---

### Post by balloons on 2012-08-21
> **ventrical said:**
> Nice work Nick :). I go to your webpage, do all that work and then there is no instruction for the ppa , or at least none that I can see??

:)

Ventrical, you should check out the walkthrough link :-) 

[https://wiki.ubuntu.com/Testing/CallforTesting/Walkthrough](https://wiki.ubuntu.com/Testing/CallforTesting/Walkthrough)

Every package has installation instructions.. for this, it's found here:

[http://packages.qa.ubuntu.com/qatracker/milestones/231/builds/21598/downloads](http://packages.qa.ubuntu.com/qatracker/milestones/231/builds/21598/downloads)

I wanted to get folks used to knowing where to find stuff, but let me know if this isn't being made explicit somewhere. For instance, bug reporting info is also linked:

[http://packages.qa.ubuntu.com/qatracker/milestones/231/builds/21598/buginstructions](http://packages.qa.ubuntu.com/qatracker/milestones/231/builds/21598/buginstructions)

Do you see the links from this page?

[http://packages.qa.ubuntu.com/qatracker/milestones/231/builds/21598/testcases](http://packages.qa.ubuntu.com/qatracker/milestones/231/builds/21598/testcases)

'Link to the installation instructions'
'Link to bug reporting instructions'

---

### Post by ventrical on 2012-08-21
Ok .. got it . Thanks! However the walkthrough is a dumb terminal and pertains to 'web-apps' not compiz. It is then not imeadiatly clear at that point where the ppa instructions are.

As you stated in your preamble of "Unity Gsetting Migration' I would suggest then that the instructions would be better placed at the bottom of that page because then one would know  at that point how to followup with ppa installation. It's just that it would be more convenient.

thanks again.

---

### Post by grahammechanical on 2012-08-21
It is all too late for me. The update that brought in the 3.5.0-10 kernel also removed Ubuntu 2D from the log in screen and gave me the login bounce back in Ubuntu (3D). I thought I fixed it by running the dpkg Repair broken packages from the recovery mode. That removed Nvidia-current, which was strange because I thought I was on Nouveau. But now all I get from this install of Quantal is crazy mixed up graphics on the login screen and on the desktop if and when I can load into it.

I tried downloading the latest daily image but it also gives messed up graphics and cannot be used.

I had an install of Quantal that worked fine with Unity 3D + Nouveau. Now it is all messed up. And I cannot even reinstall.

Changes like this should not be pushed out through updates without asking if I wanted Unity 2D removed and llvmpipe thingy installed. We should be warned about the possible consequences.

Ok, so I am a tester. Ok, so I am using an install on a partition that I do not mind messing up. But it seems that these changes are being pushed out without prior testing. So, what happened to the aim of keeping the development release as stable as the distribution release?

Now, if I can get a fresh install of 12.10 I just might be able to answer this call for testing.

Regards.

---

### Post by balloons on 2012-08-21
> **ventrical said:**
> Ok .. got it . Thanks! However the walkthrough is a dumb terminal and pertains to 'web-apps' not compiz. It is then not imeadiatly clear at that point where the ppa instructions are.

As you stated in your preamble of "Unity Gsetting Migration' I would suggest then that the instructions would be better placed at the bottom of that page because then one would know  at that point how to followup with ppa installation. It's just that it would be more convenient.

thanks again.

The walkthrough is intended to be generic for any call for testing. Is it too confusing to follow generically?

I can add a hotlink to the installation instructions from inside the testcase -- would that help? (EDIT: YES, that looks much better -- I likely just forget to make this a link :-) ) I mean, I could also point them out in the post, and perhaps I'll just do that anyway from now on. I just want people to get used to how the tracker works, so it's not so laborious each time to test. Thanks for the feedback! We don't want you having to dig for this info!

---

### Post by balloons on 2012-08-21
> **grahammechanical said:**
> It is all too late for me. The update that brought in the 3.5.0-10 kernel also removed Ubuntu 2D from the log in screen and gave me the login bounce back in Ubuntu (3D). I thought I fixed it by running the dpkg Repair broken packages from the recovery mode. That removed Nvidia-current, which was strange because I thought I was on Nouveau. But now all I get from this install of Quantal is crazy mixed up graphics on the login screen and on the desktop if and when I can load into it.

I tried downloading the latest daily image but it also gives messed up graphics and cannot be used.

I had an install of Quantal that worked fine with Unity 3D + Nouveau. Now it is all messed up. And I cannot even reinstall.

Changes like this should not be pushed out through updates without asking if I wanted Unity 2D removed and llvmpipe thingy installed. We should be warned about the possible consequences.

Ok, so I am a tester. Ok, so I am using an install on a partition that I do not mind messing up. But it seems that these changes are being pushed out without prior testing. So, what happened to the aim of keeping the development release as stable as the distribution release?

Now, if I can get a fresh install of 12.10 I just might be able to answer this call for testing.

Regards.

grahammechanical, I completely agree with everyone's sentiment on how this was handled. It's a topic for discussion this week when I meet with the release team. I had no idea this was happening -- trust me I would have warned you all :-)

Now, as to what can be done for you, I would use the alpha3 iso and install 12.10. Next, add this ppa and then do a dist-upgrade. Don't update or upgrade before adding the ppa! Reboot. Bingo, everything should work. I tried this myself and had success, but caveat emptor.

---

### Post by ventrical on 2012-08-21
> **guitara said:**
> The walkthrough is intended to be generic for any call for testing. Is it too confusing to follow generically?

I can add a hotlink to the installation instructions from inside the testcase -- would that help? (EDIT: YES, that looks much better -- I likely just forget to make this a link :-) ) I mean, I could also point them out in the post, and perhaps I'll just do that anyway from now on. I just want people to get used to how the tracker works, so it's not so laborious each time to test. Thanks for the feedback! We don't want you having to dig for this info!


Thats the right stuff guitara! :) I seen that embedded hotlink :) 

 I ran the test but everything went south and now launchpad has timed out  and I can't get in .  There is this  bug that reports that  this is not an official Ubuntu package (see screenshot below) but otherwise the rest of the test went well with the 'appearance' settings not being altered after install of the ppa. I will try to report this bug again but I thing my tracker report was trashed.

---

### Post by ventrical on 2012-08-21
Ok.. got it.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1039754](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1039754)

---

### Post by balloons on 2012-08-21
> **ventrical said:**
> Thats the right stuff guitara! :) I seen that embedded hotlink :) 

 I ran the test but everything went south and now launchpad has timed out  and I can't get in .  There is this  bug that reports that  this is not an official Ubuntu package (see screenshot below) but otherwise the rest of the test went well with the 'appearance' settings not being altered after install of the ppa. I will try to report this bug again but I thing my tracker report was trashed.

Thanks for following this through! Yea, ppa's without apport hooks run into this issue. Sigh, I thought there were hooks for this...

---

### Post by mc4man on 2012-08-21
>  A new version of unity has arrived, stock full of compiz fixes. 
A downside of these 'testing' ppa's is there are no changelogs avail. to directly see what was fixed, changed, ect.,  can be somewhat inferred from the lp trunk page(s).
Didn't see any issues, not even the 4 reported bugs, though ATM gsettings 'support' seems quite remedial.
Other than a few basic settings it seems to only react to changes made elsewhere instead of containing all the plugin settings ala gconf.

Sorta makes ccsm more valuble then before when gconf was an alt. means

The commands plugin is currently dead in the water as only bindings are set in gsettings, not the commands themselves
(and whether those bindings are going to correct location is unknown here, possibly not..

---

### Post by mrv on 2012-08-22
> **mc4man said:**
> A downside of these 'testing' ppa's is there are no changelogs avail. to directly see what was fixed, changed, ect.,  can be somewhat inferred from the lp trunk page(s).


Changelogs can be seen under the "View package details" link in the ppa. From there it can be seen that in this case the compiz is the bzr3308 version, on top of which there is a lot of GSettings work which is only just now landing to lp:compiz trunk.

Unity is the less than two weeks old 6.2 release patched for GSettings.

---

### Post by MacUntu on 2012-09-01
Compiz/Unity are KIA here. Any way to revive them?

Compiz (regular repo) segfaults, all I see on the console is ```
compizconfig - Error: NULL encountered while reading GConf setting
```

I tried the "unity --reset" dance, no luck.

---

### Post by jerrylamos on 2012-09-01
Current Unity/Compiz bug I have is 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1041354](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1041354)
where Libre Office Write freezes.  The bug says:

unity-panel-service uses ~100% CPU when libreoffice-gtk is installed and enabled

To use Libre Office Write I either log into LXDE desktop with quantal or boot Precise 2D.

When there's an indication of a fix in the daily iso I'll try to recreate the situation resulting in the bug.  My problem with ppa's is getting them back off cleanly short of a re-install, and I don't know enough to do patches & compiles.

---

### Post by nanog on 2012-09-02
> **jerrylamos said:**
> My problem with ppa's is getting them back off cleanly short of a re-install, and I don't know enough to do patches & compiles.

remove:
[PHP]sudo add-apt-repository --remove ppa:someppa/ppa[/PHP]purge:
[PHP]sudo apt-get install ppa-purge
sudo ppa-purge ppa:someppa/ppa[/PHP]

[http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html](http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html)

---

### Post by MacUntu on 2012-09-06
```
rm -rf ~/.compiz/
rm -rf ~/.compiz-1/
dconf reset -f /org/compiz/
```

Boom, fixed.

---

