---
title: "Pepper Plugin possible in repository"
date: 2014-01-14
forum: The Cafe
---

### Post by grier-devon on 2014-01-14
Legally would it be possible for Canonical with Ubuntu to be able to offer google's "pepper" plugin for Chromium in the "Ubuntu Restricted Extras" in the future? It would be nice once the current Flash plugin for FF goes belly up to have something to offer new users who must have flash, especially would be nice since I am now using Chromium and it feels faster then Chrome, plus I am hearing the next release of Chromium won't support Adobe Flash 11.2 plugin anyway. I know of the PPA but it would be nice to see this in the Ubuntu Restricted Extras. Thoughts, opinions and facts you all know?

---

### Post by d-cosner on 2014-01-14
Pepper Flash will be in the repos for 14.04 if I remember right.

---

### Post by vasa1 on 2014-01-14
> **d-cosner said:**
> Pepper Flash will be in the repos for 14.04 if I remember right.
At least that's what it looks like now.

---

### Post by grier-devon on 2014-01-14
Well this is good to hear, I don't see why they couldn't since there are some stuff offered in the Ubuntu Restricted Extras which I am sure violate copy right laws just as severely.

---

### Post by craig10x on 2014-01-14
Yeah, i am running 14.04 development and i noticed in the package manager...it's a separate package from ubuntu restricted extras....i believe what it does is extract pepperflash from Chrome and then put it into Chromium...Canonical probably added it because as of April, Chromium won't support the old adobe flash plug in anymore...

---

### Post by grier-devon on 2014-01-14
Okay well my next question is I know "Pepper" updates through Google, being it is provided in 14.04 though an official repository will the Pepper version of flash update come through the Ubuntu Update Manager or how will that work when google releases a newer version of Pepper since it is not originally for Chromium?

---

### Post by vasa1 on 2014-01-15
> **grier-devon said:**
> Okay well my next question is I know "Pepper" updates through Google, being it is provided in 14.04 though an official repository will the Pepper version of flash update come through the Ubuntu Update Manager or how will that work when google releases a newer version of Pepper since it is not originally for Chromium?My guess is that that will be handled by the "maintainer" of the Pepper Flash plugin. You'll probably just see it as a regular update.

At least one other distro (OpenSUSE) has been making Google Chrome's Pepper Flash available to Chromium users for quite a few months.

---

### Post by cariboo on 2014-01-15
> **grier-devon said:**
> Okay well my next question is I know "Pepper" updates through Google, being it is provided in 14.04 though an official repository will the Pepper version of flash update come through the Ubuntu Update Manager or how will that work when google releases a newer version of Pepper since it is not originally for Chromium?

To install pepper flash, the package in the repository downloads the current version of Chrome, and extracts pepper from the Chrome package, and installs it for use by Chromium.

I haven't tried it yet, as the current version of flash still works with the current version of Chromium, but the next time I do a fresh Trusty install, I'll give it a try.

---

### Post by monkeybrain20122 on 2014-01-15
I can't see the point of this. Just use Chrome if you need pepper flash. Otherwise Chromium would be even more crippled when all its NNAPI plugins stop working in April.

---

### Post by craig10x on 2014-01-15
Chromium will work with pepperflash after April...but it won't work with the native flash 11.2 anymore...that's why Canonical added the package to 14.04...
But i agree, One should just use Chrome because not only do you already have pepper by default but also have a neat built in pdf viewer and Google adds on a ppa to your software sources so that you get the latest version as soon as it is released :D

In my Chrome, i noticed that both pepper and the native are activated...i just recently disabled the native flash in chrome so this way i am running on pepper only..i figured having both on may conflict with each other and maybe less chance of crashes that way...i will let you know if that is the case....so far, it seems to help...

As of April, the native plug in option will be gone on Chrome and of course also on Chromium which is why Chromium users are going to need that pepperflash added on...

---

### Post by grier-devon on 2014-01-15
I use to agree to the Chrome over Chromium thing but for the last 6-9 months Chrome has felt so slow to me and I had heard that Chromium was lighter and faster, for me and even my wife has said she has noticed on here Ubuntu Machine Chromium to be far more responsive over Chrome. If in the future this changes I may go back to Chrome. Honestly why does everyone bring up the pdf viewer, if I need to view a pdf from the web then Chromium downloads it and I just open it in document viewer as it can do more then what is built into the browser anyway.

---

### Post by craig10x on 2014-01-15
Well, the nice part about the built in pdf reader on Chrome is that you can view an online pdf file without having to actually download it to your drive to view it...and then after viewing it, if you should decide you want to keep it, then you just right click and download it as usual...

Regarding Chromium running faster, i would say this (based on my observations) i am running 14.04 development and Chrome seems to be more zippy on it then it did when i was running it on 13.10...so you if you upgrade to 14.04 when it comes out you may want to give Chrome another try...

---

### Post by vasa1 on 2014-01-15
> **grier-devon said:**
> ... it can do more then what is built into the browser anyway.
I don't rely much on PDF files and so Chrome's PDF viewer is default for me but do you know if someone has done a comparison of features offered by Chrome's PDF viewer and Evince aka Document Viewer? If you feel that would be off-topic just post a link please.

Re. Chrome slowing down over time ... I don't mean to sound disbelieving but is this with a new profile and no extensions? Again, this is off-topic but this being the Cafe I'm hoping there's a bit of wiggle room here.

---

### Post by grier-devon on 2014-01-15
> **vasa1 said:**
> I don't rely much on PDF files and so Chrome's PDF viewer is default for me but do you know if someone has done a comparison of features offered by Chrome's PDF viewer and Evince aka Document Viewer? If you feel that would be off-topic just post a link please.

Re. Chrome slowing down over time ... I don't mean to sound disbelieving but is this with a new profile and no extensions? Again, this is off-topic but this being the Cafe I'm hoping there's a bit of wiggle room here.

No I have not seen anyone do a comparison, just personal experience which is all I need.

I have checked the extension in Chrome and I have the same ones running in there as I do Chromium under the same gmail account with everything synced. I do want to make this clear, I am not a Chromium open source fan boy. As I do believe open source to be superior in many ways if I found a proprietary piece of software that was equal or better in stability, performance and features I would gladly use that instead. Though this has not been my experience with Chrome especially in the last two releases of Ubuntu. 

On a further note this was not meant to start a flame war between Chrome and Chromium opinions, more of a way for current flash to be installed on an open source browser that could ship with Ubuntu. I am hoping what I am reading about FF is true with there plans for future flash replacement, the question is how long? So it will be nice to have something partial open source while FF irons things out.

---

### Post by carl4926 on 2014-01-15
> **vasa1 said:**
> My guess is that that will be handled by the "maintainer" of the Pepper Flash plugin. You'll probably just see it as a regular update.

At least one other distro (OpenSUSE) has been making Google Chrome's Pepper Flash available to Chromium users for quite a few months.
Correct, well it's been this way for well over a year. It actually comes via Packman our Multimedia repo, which has to be added manually by the end user.

I can see this whole flash business turning ugly or uglier than it is now.

---

### Post by grier-devon on 2014-01-16
> **carl4926 said:**
> Correct, well it's been this way for well over a year. It actually comes via Packman our Multimedia repo, which has to be added manually by the end user.

I can see this whole flash business turning ugly or uglier than it is now.

What do you mean uglier? Like in terms with Browsers trying to find a way to provide the plugin or the user trying to get Flash on there favorite open source browser?

---

### Post by vasa1 on 2014-01-16
> **carl4926 said:**
> Correct, well it's been this way for well over a year. It actually comes via Packman our Multimedia repo, which has to be added manually by the end user.

I can see this whole flash business turning ugly or uglier than it is now.

Carl, can you clarify whether it's just the plug-in that the OpenSUSE users get or whether it's a full download of Chrome after which something is done to make the plug-in available to Chromium? cariboo907's post seems to indicate that, in the Ubuntu way in 14.04, each "update" to the plug-in entails a full download of Chrome.

---

### Post by vasa1 on 2014-01-16
> **grier-devon said:**
> No I have not seen anyone do a comparison, just personal experience which is all I need.. ...
No problem, but I was hoping for specifics on "I just open it in document viewer as **it can do more** then what is built into the browser anyway".

---

### Post by carl4926 on 2014-01-16
> **grier-devon said:**
> What do you mean uglier? Like in terms with Browsers trying to find a way to provide the plugin or the user trying to get Flash on there favorite open source browser?

Ugly as in flash support dropped by adobe and the ramifications

---

### Post by carl4926 on 2014-01-16
> **vasa1 said:**
> Carl, can you clarify whether it's just the plug-in that the OpenSUSE users get or whether it's a full download of Chrome after which something is done to make the plug-in available to Chromium? cariboo907's post seems to indicate that, in the Ubuntu way in 14.04, each "update" to the plug-in entails a full download of Chrome.
Chromium is supplied in openSUSE default repos
The pepper flash plugin is added from the Packman repository. If you don't add it, Chromium defaults to the adobe plugin ATM anyway.

Some opensuse build service users also have repositories built with the pepper flash plugin

Chrome is nothing to do with the supply of Chromium and or pepper flash.

---

### Post by craig10x on 2014-01-16
Ubuntu extracts the plug in from Chrome to put it into Chromium...it mentions that right in the description in 14.04's synaptic package manager...that's the only way they can do it...

---

### Post by carl4926 on 2014-01-16
> **carl4926 said:**
> 
Chrome is nothing to do with the supply of Chromium and or pepper flash.
Yes
Maybe that comment was poorly contrived
Of course pepper flash originates from Chrome. But the installation of Chrome itself is not required and no special symlinking is required either

---

### Post by grier-devon on 2014-01-16
> **vasa1 said:**
> No problem, but I was hoping for specifics on "I just open it in document viewer as **it can do more** then what is built into the browser anyway".

Well here is an example of something I experience today, since this discussion came about I needed to edit a PDF which I opened the PDF in Chrome and it would not let me type in it, maybe a setting issue but mine are set to default. I opened the same pdf in "Document Viewer" and just clicked where I needed to file in some blocks on the pdf and I was just able to start typing.

---

### Post by grier-devon on 2014-01-16
> **carl4926 said:**
> Ugly as in flash support dropped by adobe and the ramifications

agreed. I am a supporter of FF for default browser but for those reasons of Flash going away for new users I think it would be best to put Chromium as default and offer pepper as an officially supported in the repositories.

Before anyone decided to start a flame war here please understand my logic, I have numerous end users i have set up on Ubuntu from friends to family and they no a certain way to do things through the GUI. If tomorrow I told them they will no longer have Flash support and in order to get it they will have to install a PPA through the command line this would probably make them to start looking else where.

---

### Post by Lyfang on 2014-01-20
[Pepper Flash Player Installer For Chromium Available In The Ubuntu 14.04 Repositories]("http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html")

---

### Post by monkeybrain20122 on 2014-01-21
> **grier-devon said:**
> agreed. I am a supporter of FF for default browser but for those reasons of Flash going away for new users I think it would be best to put Chromium as default and offer pepper as an officially supported in the repositories.

Before anyone decided to start a flame war here please understand my logic, I have numerous end users i have set up on Ubuntu from friends to family and they no a certain way to do things through the GUI. If tomorrow I told them they will no longer have Flash support and in order to get it they will have to install a PPA through the command line this would probably make them to start looking else where.

Sorry, I disagree with your reasoning. 

First** flash 11.2 will be supported** **til 2017** and there are very very few sites for which you would need pepper flash. So the assertion that there will be no flash support except through pepper flash is just false. 

Secondly flash is not the only media format on the web, there are other video audio streaming formats (quicktime, windows media e.g). Chrome/Chromium has always been inferior to Firefox on Linux for supporting these other streaming formats now it simply won't support anything other than flash(since google decides to ban all NNAPI plugins for Chromium/Chromium on Linux sooner rather than later)  So with Chromium you have flash support for may be a few extra sites that FF flash doesn't work but it has no support at all for anything else. I would say that is a much more crippled browsing experience.

Thirdly pepper flash itself is crippled. It cannot access any drmed content (google videos, amazon videos etc and for example some gaming sites), so while pepper flash is 'up to date' it is still broken if your new user needs to access drmed contents. 

There are two work arounds in Linux but both only work in FF/or other browsers that use Mozilla plugins. 1) use Hal, there is a ppa already for Trusty. 2) pipelight (a wine based solution) which lets you install Windows' flash on native Linux browsers. This won't work in Chrome/Chromium after April (since pipelight is NNAPI) You can actually use pipe-light flash as default on Firefox and it is even newer than pepper and can access contents that pepper cannot (pipelight flash updated to ver12rc yesterday) At the moment I don't recommend it as default because it is not as smooth as 11.2 if both work in my experience, but it is easy to set up the switching mechanism with a gui. 

So, if I  am setting up Ubuntu for a Windows user now I won't even bother with Chrome/Chromium at all,--I used to install Chrome as a fallback just in case the user needs up to date flash,--I would simply set up pipelight-flash for him/her on Firefox and problem solved (Note: someone proposed to include pipelight in Trusty's repo in the mailing list but it probably won't happen because of wine upstream, but it makes more sense than pepper flash for Chromium for end user experience)

---

### Post by craig10x on 2014-01-21
Are you sure about Chrome no longer supporting the quicktime plug in and windows media plug ins that we have from ubuntu restricted extras and that i see on my plugs ins list in Chrome (and they work well, by the way)...i know about it no longer supporting the old adobe flash plug in, but nothing was mentioned about those other plugs in on Chrome or Chromium...

Also, what is Chromium doing? because since it doesn't have pepperflash by DEFAULT i can't imagine them putting it out with no flash access at all!

---

### Post by monkeybrain20122 on 2014-01-21
> **craig10x said:**
> Are you sure about Chrome no longer supporting the quicktime plug in and windows media plug ins that we have from ubuntu restricted extras and that i see on my plugs ins list in Chrome (and they work well, by the way)...i know about it no longer supporting the old adobe flash plug in, but nothing was mentioned about those other plugs in on Chrome or Chromium...

Also, what is Chromium doing? because since it doesn't have pepperflash by DEFAULT i can't imagine them putting it out with no flash access at all!

Yes, I am 100% sure. The announcement is that Google will drop NNAPI support on Linux after April. It is as clear as anything can be. But for some reasons it is being reported in many places as google will drop support for Mozilla flash as if flash is the only NNAPI plugin that people use. If that is the case it is a non problem. How many people actually use Chromium? It is a perpetual beta browser pushed by a small group of Ubuntu developers who can't even keep it up to date.

The support for all media formats on Linux browsers right now is through either gstreamer (Totem plugins) or mplayer (gecko-mediaplayer) Totem doesn't work so great and mplayer pretty much plays everything but not always reliable in Chrome (does not load since Ubu11.10 or something but suddenly works perfectly in Chrome again in 13.10, but only in Ubuntu, not in Lubuntu or Fedora..) .All these are Mozilla plugins hence NNAPI. So unless something new appears I am pretty sure nothing other than flash will work on Chrome/Chromium after April. 

(There is a new (?) vlc addon for Youtube apparently, I heard it works  great in both FF and Chrome,--I never use it, I use Viewtube,-- and it  was confirmed on Videolan forum that it will not work in Chromium/Chrome after  April.)

I have never understood what Chromium is doing. It is neither here nor there, none of the arguments for making it the default in the Ubuntu summit makes any sense (basically boils down to popularity by false association)

---

