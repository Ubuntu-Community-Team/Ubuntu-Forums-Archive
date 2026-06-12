---
title: "What will happen when Adobe flash support end?"
date: 2014-05-05
forum: Ubuntu, Linux and OS Chat
---

### Post by Tar_Ni on 2014-05-05
Hi,

Apparently, Adobe will stop supporting Linux with security update in 2016, which means about 2 years from now. There doesn't seems to be a solid alternative right now. The only option seems to be using Google Chrome, which is against the free and open software philosophy (it's no more about choice but obligation to use it in this case!) that many of us hold dear.

Mozilla is working on a solution, the implementation of Shumway, an open-source HTLM5 based flash. We have no idea when it's going to be near stable to replace the Adobe flash player for good but we may be talking years in this case.

Where does that leave Linux? Obviously with an obsolete flash plug-in, it's a serious issue security wise but also websites with gradually by surely stop supporting this version.

What do you think?

---

### Post by ventrical on 2014-05-05
I just noticed this  when I tried to download Flash from adobe website. It says the current version is the last Linux supported version, at least for Ubuntu.

---

### Post by craig10x on 2014-05-05
So use Chrome..what's the big deal...does everything have to be open source to get your seal of approval?  If it is, it's a very limited philosophy...they may not be open source but they provide for free, so enjoy! :D
They support linux...in fact Chrome Os (ex: Chromebooks) is Linux! 

Eventually (maybe 5 years down the road or so) perhaps html5 will replace flash as the main standard...but until it does, that's your best solution...Chrome happens to be an excellent all-around browser anyway and it's my "go to" one everyday i web surf on my ubuntu 14.04....

Ubuntu may be open source...but don't forget Canonical is a commercial venture too...

---

### Post by deadflowr on 2014-05-05
To avoid google chrome use chromium instead.
The pepperflash-plugin is available in the repos, for 14.04(at least)


You might also look into [pipelight]("http://fds-team.de/cms/pipelight-installation.html").

---

### Post by craig10x on 2014-05-05
@deadflowr: a very good suggestion...although i kind of get the impression that he is an "open source purist" and in effect, you are adding a "closed source plug in from Chrome" (non-open source) to an open source Chromium web browser...so that probably wouldn't do it for him ;) :D

---

### Post by slickymaster on 2014-05-05
> **craig10x said:**
> So use Chrome..what's the big deal...does everything have to be open source to get your seal of approval?  If it is, it's a very limited philosophy...they may not be open source but they provide for free, so enjoy! :D
They support linux...in fact Chrome Os (ex: Chromebooks) is Linux! 

Eventually (maybe 5 years down the road or so) perhaps html5 will replace flash as the main standard...but until it does, that's your best solution...Chrome happens to be an excellent all-around browser anyway and it's my "go to" one everyday i web surf on my ubuntu 14.04....

Ubuntu may be open source...but don't forget Canonical is a commercial venture too...

+1

---

### Post by deadflowr on 2014-05-05
> **craig10x said:**
> @deadflowr: a very good suggestion...although i kind of get the impression that he is an "open source purist" and in effect, you are adding a "closed source plug in from Chrome" (non-open source) to an open source Chromium web browser...so that probably wouldn't do it for him ;) :D

As oppose to the fully non-free flash plugin wanted.;)

If purist is wanted, go gnash.

---

### Post by monkeybrain20122 on 2014-05-05
BTW I think it is 2017. By that time you may need flash only as much as you need silverlight now.

---

### Post by Tar_Ni on 2014-05-05
> **craig10x said:**
> So use Chrome..what's the big deal...does everything have to be open source to get your seal of approval?  If it is, it's a very limited philosophy...they may not be open source but they provide for free, so enjoy! :D
They support linux...in fact Chrome Os (ex: Chromebooks) is Linux! 

Eventually (maybe 5 years down the road or so) perhaps html5 will replace flash as the main standard...but until it does, that's your best solution...Chrome happens to be an excellent all-around browser anyway and it's my "go to" one everyday i web surf on my ubuntu 14.04....

Ubuntu may be open source...but don't forget Canonical is a commercial venture too...

Sorry but it doesn't make a lot of sens to me to use a free and open operating system only to be handcuffed to a browser which I've some legitimate privacy concerns about and for the reason that it has the monopole of flash on Linux. I hope not to be forced to go down that road to be able to use Linux in 2 years for now. It's not about been a ''purist'' of the open-source but only about having the freedom of choice. There are some nice browser out there, such as Firefox, Midori, Opera, Pale Moon, Seamonkey which requires a flash plug-in to work. But the clock is ticking before the Linux built of flash becomes obsolete and not longer secure.

---

### Post by pqwoerituytrueiwoq on 2014-05-05
the pepperflashplugin-nonfree package works on older release

mozilla is making there own flash replacement, look up shumway
> **monkeybrain20122 said:**
> BTW I think it is 2017. By that time  you may need flash only as much as you need silverlight now.
i hope so

---

### Post by Tar_Ni on 2014-05-05
> **deadflowr said:**
> To avoid google chrome use chromium instead.
The pepperflash-plugin is available in the repos, for 14.04(at least)


You might also look into [pipelight]("http://fds-team.de/cms/pipelight-installation.html").

I will look at that, thanks. But is it updated? I like chromium-type browser, such as the barebone Chromium and Opera. Chrome I prefer to avoid.

Also, will the pepperflash-plugin work for Opera?

---

### Post by Tar_Ni on 2014-05-05
> **pqwoerituytrueiwoq said:**
> mozilla is making there own flash replacement, look up shumway

I follow that closely, there was an hype in october when it landed on Nightly but as far as I know it's still very unstable and far from even remotely able to replace Adobe Flash player. Mozilla is working on it since 2012 and it may be that it will be ready in 2016-17. I sure hope so!

I believe Shumway (and so HTML5) is the solution too. Because it will not be restricted to chromium-type of browser but available to all on Github. So other browsers will be able to make use of it.

[http://www.ghacks.net/2013/10/02/mozillas-flash-plugin-replacement-shumway-lands-firefox-nightly/](http://www.ghacks.net/2013/10/02/mozillas-flash-plugin-replacement-shumway-lands-firefox-nightly/)

---

### Post by pqwoerituytrueiwoq on 2014-05-05
i would expect ARM based systems to become more and more common and if content providers want to support that hardware they can't use flash so that should help make them move away from it
unless you have a fairly power system flash is horrible, it is a little more forgiving on windows than linux/osx

---

### Post by monkeybrain20122 on 2014-05-05
> **pqwoerituytrueiwoq said:**
> i would expect ARM based systems to become more and more common and if content providers want to support that hardware they can't use flash so that should help make them move away from it
unless you have a fairly power system flash is horrible, it is a little more forgiving on windows than linux/osx

The bad news is that performance wise html5 is just as horrible if not worse than flash on weak hardware. To really rub it in actually html5 runs a lot smoother on Chrome than on Firefox with supported graphic drivers because of hardware acceleration. I set up Ubuntu on a 5 year old hp netbook with an AMD card (open driver), gpu is decent but cpus are quite weak. vimeo hd videos are unwatchable on Firefox but they run quite smoothly on Chrome (Hwacc for html5 is not available for Firefox, at least for Linux, not sure about other platforms)

Another thing is Chrome has h264 decoding built in while firefox requires installing gstreamer0.10-ffmpeg.The package is removed from Trusty so before Firefox 30 you can't even watch html5 videos (most use h264) on Trusty with FF unless you install the missing package from ppa. Since h264 has gone open source lately I think Mozilla will catch up eventually.

I don't really think pepper flash is such a big deal as 99% of sites don't require flash 13 and pepper flash would not work on drm streams (while system flash + hal or pipelight flash would, both options not available for Chrome) I in general prefer Firefox (and FF29 is faster than Chrome. :)) But unfortunately at this point Chrome is actually a better choice for html5 videos than Firefox if cpu usage is a concern.

Edited: Youtube 1080p only plays in html5 on Chrome and IE11,--may work on Chromium as well,-- there is a ticket on Mozilla's bug list to implement this feature, someone is working on it apparently.

---

### Post by saye-187 on 2014-05-07
i'm not realy understand :(

---

