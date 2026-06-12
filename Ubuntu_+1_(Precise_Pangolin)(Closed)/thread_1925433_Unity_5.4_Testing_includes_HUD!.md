---
title: "Unity 5.4 Testing includes HUD!"
date: 2012-02-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by balloons on 2012-02-14
Another opportunity for testing -- there's going to be a lot this week. :-)

Unity 5.4 has landed and has a new suite of tests surrounding the HUD. You have until Thursday at 8 am UTC as usual to test.

Please see this post for the details
[http://www.theorangenotebook.com/2012/02/unity-54-whats-new-and-call-for-testing.html](http://www.theorangenotebook.com/2012/02/unity-54-whats-new-and-call-for-testing.html)

Thanks everyone!

---

### Post by kaldor on 2012-02-14
Awesome. Will be testing this out shortly :)

Edit: Not working out nicely :(

For the most part, trying to type a command into the HUD switches the application from the current to the connection manager. For example, if you launch Firefox and start typing you'll get a bunch of Wireless-related options. Entirely unrelated to Firefox.

This is the same for all programs.

---

### Post by balloons on 2012-02-14
> **kaldor said:**
> Awesome. Will be testing this out shortly :)

Edit: Not working out nicely :(

For the most part, trying to type a command into the HUD switches the application from the current to the connection manager. For example, if you launch Firefox and start typing you'll get a bunch of Wireless-related options. Entirely unrelated to Firefox.

This is the same for all programs.

Weird -- I'm not having any issues like that on my installation.

EDIT: ok, as soon as I say that... xchat is doing what your describing.

---

### Post by go7Ul1ai on 2012-02-14
I have the Unity Staging PPA, would I be able to get the latest version of Unity by adding the PPA you mentioned in your blog post? Should I purge the Staging PPA and add it or would I be able to use both without issues?

---

### Post by kaldor on 2012-02-14
This PPA seems to be absolutely riddled with bugs :)

Animation problems, incorrect icons, HUD broken, etc. Lots of reporting to do.

---

### Post by balloons on 2012-02-14
> **lee.jarratt said:**
> I have the Unity Staging PPA, would I be able to get the latest version of Unity by adding the PPA you mentioned in your blog post? Should I purge the Staging PPA and add it or would I be able to use both without issues?

AFAIK, the unity staging ppa is auto generated builds, which are not meant to be stable release snapshots. I'm assuming you know this but like running the bleeding bleeding edge of unity as it's developed :-).

With that in mind, the staging ppa should have newer versions than the unity team ppa, so it will overwrite what's in that ppa. It would be best to purge staging and install from the team ppa while doing these tests. Your certainly welcome to switch back when your done. Thanks for helping out!!

---

### Post by balloons on 2012-02-14
> **kaldor said:**
> This PPA seems to be absolutely riddled with bugs :)

Animation problems, incorrect icons, HUD broken, etc. Lots of reporting to do.

Awesome discovery work kaldor. Happy reporting! I'm running through the checkbox tests myself atm.

---

### Post by kaldor on 2012-02-14
Bug reports...


[LIST]
[*][HUD searching wrong application.]("https://bugs.launchpad.net/unity/+bug/932297")
[*][Need to click the search field when invoking the HUD]("https://bugs.launchpad.net/unity/+bug/932301").
[*]["Show Desktop" in wrong spot.]("https://bugs.launchpad.net/unity/+bug/932304")
[*][BFB discolouration]("https://bugs.launchpad.net/unity/+bug/932310")
[/LIST]


It may be brief, nitpicky, and trivial, but I guess this release is called "Precise" for a reason :)

---

### Post by mc4man on 2012-02-14
The 'default' for the bfb & all non-favorite launcher icons would now be to color them based off of the background (intended wouldn't know
If you change the color in a some ways the bfb will get a grey background or other changes then all will be re-colored

Any which way it looks possibly ok to awful, unfortunately there is no way to use 000000 with any opacity, icons will disappear (known bug, whether any intention or possibility to fix don't know backfround, be vastly improved

THe 'current' look can, depending on background, be vastly improved by turning 
off the default "Backlight always on"

Actually the hud works here ok most of the time other than cursor focus (blinking), though it is currently slower than gui menus & not even close to current keyboard shortcuts

---

### Post by balloons on 2012-02-14
> **kaldor said:**
> Bug reports...


[LIST]
[*][HUD searching wrong application.]("https://bugs.launchpad.net/unity/+bug/932297")
[*][Need to click the search field when invoking the HUD]("https://bugs.launchpad.net/unity/+bug/932301").
[*]["Show Desktop" in wrong spot.]("https://bugs.launchpad.net/unity/+bug/932304")
[*][BFB discolouration]("https://bugs.launchpad.net/unity/+bug/932310")
[/LIST]


It may be brief, nitpicky, and trivial, but I guess this release is called "Precise" for a reason :)

This one is particularly annoying:

[Need to click the search field when invoking the HUD]("https://bugs.launchpad.net/unity/+bug/932301").

---

### Post by Xgen on 2012-02-14
Hmmm....on preliminary inspection, using back/forward buttons and any buttons modified by xbindkeys does nothing except bring up the search box and make the cursor disappear. Requires a hard boot to bring back. Will inspect more in depth...

---

### Post by grahammechanical on 2012-02-14
I have run the test and all I can say is it is getting there but still needs work. I am coming to the opinion that HUD will be of little use to anyone who does not know what it is supposed to do. I do not want to be negative but this is twice that I tried to use it. This time was better than the last but I find the thing frustrating.

Regards.

---

### Post by kaldor on 2012-02-14
> **grahammechanical said:**
> I have run the test and all I can say is it is getting there but still needs work. I am coming to the opinion that HUD will be of little use to anyone who does not know what it is supposed to do. I do not want to be negative but this is twice that I tried to use it. This time was better than the last but I find the thing frustrating.

Regards.

As someone who only uses a mouse while gaming or other mouse-centric tasks, the HUD will probably be a massive use for me. Sadly, I've not been able to get the HUD working properly at all since it was announced. Seeing this is an LTS, I've no doubt that by release the HUD will work as expected. Give it time :)

---

### Post by kevpan815 on 2012-02-15
Be sure that you install gnome-session-fallback before testing this as it does have a lot of problems currently, as one was created today on my systeem when apt-get update and apt-get upgrade tried to revert it back to Unity 5.2 with today's updates! Just FYI. I will be filing a Bug Report on that shortly.

---

### Post by balloons on 2012-02-15
> **kaldor said:**
> As someone who only uses a mouse while gaming or other mouse-centric tasks, the HUD will probably be a massive use for me. Sadly, I've not been able to get the HUD working properly at all since it was announced. Seeing this is an LTS, I've no doubt that by release the HUD will work as expected. Give it time :)

Yes the HUD needs some testing and bug hunting love in order for it to be up to snuff for precise. Thanks for testing and reporting things you find wrong. It's neat when it works, but like you on my box it's been clumsy.

---

### Post by mc4man on 2012-02-15
> **mc4man said:**
> The 'default' for the bfb & all non-favorite launcher icons would now be to color them based off of the background (intended wouldn't know
If you change the color in a some ways the bfb will get a grey background or other changes then all will be re-colored


This is an intended change, so depending the backgound image one may like or hate
The method to attempt to modify if desired is also a bit limited, subdued coloring can be hard to get, fruitloops or grey is more likely

---

### Post by jfernyhough on 2012-02-15
Has anyone else found they can no longer resize windows using ALT+mouse3 (middle mouse button) (or in my case mouse2 (right mouse button))?

I have this with Unity 5.2 on my Mini 311c, and the Unity 5.2+git from the unity-team PPA

---

### Post by artshark on 2012-02-22
does anyone have a raw .deb I can install? the x86 repo is down.

---

### Post by cariboo on 2012-02-22
Try the main repos. I use the main Canadian repository, and it's working fine.

---

### Post by artshark on 2012-02-22
will do.
thanks!
Art> **cariboo907 said:**
> Try the main repos. I use the main Canadian repository, and it's working fine.

---

### Post by kaldor on 2012-02-23
Working much better for the last couple of days. Definitely like this, but it needs a lot of polishing work before April. 

How is it going to work with LibreOffice? This is probably where I'd like to use HUD the most.

---

### Post by balloons on 2012-02-23
> **kaldor said:**
> Working much better for the last couple of days. Definitely like this, but it needs a lot of polishing work before April. 

How is it going to work with LibreOffice? This is probably where I'd like to use HUD the most.

Kaldor, I'm not a big libreoffice user -- how is working / not working for you right now?

---

### Post by kaldor on 2012-02-24
> **guitara said:**
> Kaldor, I'm not a big libreoffice user -- how is working / not working for you right now?

It seems that it only works properly with the native GNOME applications. LibreOffice still has the bug where the HUD searches the network settings.

Edit: works decently after installing *lo-menubar *package. Will this be in the default 12.04 install?

---

### Post by VinDSL on 2012-02-25
> **guitara said:**
> Another opportunity for testing -- there's going to be a lot this week. :-)

Unity 5.4 has landed and has a new suite of tests surrounding the HUD. You have until Thursday at 8 am UTC as usual to test.

Please see this post for the details
[http://www.theorangenotebook.com/2012/02/unity-54-whats-new-and-call-for-testing.html](http://www.theorangenotebook.com/2012/02/unity-54-whats-new-and-call-for-testing.html)

Thanks everyone!
Interesting!

I installed/enabled/invoked (pick a word) HUD about a week ago, and it didn't do anything, until tonight.

So, while I missed the deadline (not for want of trying) I can tell you that it's magically working now.  LoL!

---

### Post by balloons on 2012-02-27
> **kaldor said:**
> It seems that it only works properly with the native GNOME applications. LibreOffice still has the bug where the HUD searches the network settings.

Edit: works decently after installing *lo-menubar *package. Will this be in the default 12.04 install?

Hmm, might be worth filing a bug to force a depends or at least suggest for this package then kaldor. I don't know.

---

