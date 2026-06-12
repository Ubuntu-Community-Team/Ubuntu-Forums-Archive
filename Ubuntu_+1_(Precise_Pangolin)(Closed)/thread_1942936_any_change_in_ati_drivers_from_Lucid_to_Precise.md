---
title: "any change in ati drivers from Lucid to Precise?"
date: 2012-03-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kurja on 2012-03-18
I've had some video/3d problems with ATI cards in Lucid, namely I have a "new" HD3450 AGP card I'd like to use but it seems there are no proper drivers for it in Lucid; do any of you know if there will be any difference in this regard when switching to Precise?

Catalyst drivers do not support this card in linux, and I didn't get 3d acceleration with default ati or fglrx drivers in Lucid.

---

### Post by alphacrucis2 on 2012-03-18
The changes since lucid are huge. HD 3450 should be supported by both Catalyst and open source driver in Precise. In any case in Lucid you ought to be able to use the latest catalyst from AMD, even if the one in the ubuntu repos doesn't support your card. Just download the latest binary installer from the AMD website and install using the --buildpkg method. For Precise you can test using the live CD. That will test the open source driver out of the box. To test catalyst you would need to use live USB with persistent storage to be able to test the catalyst driver without a full install.

---

### Post by kaldor on 2012-03-18
> **kurja said:**
> I've had some video/3d problems with ATI cards in Lucid, namely I have a "new" HD3450 AGP card I'd like to use but it seems there are no proper drivers for it in Lucid; do any of you know if there will be any difference in this regard when switching to Precise?

Catalyst drivers do not support this card in linux, and I didn't get 3d acceleration with default ati or fglrx drivers in Lucid.

*Major* changes in the graphics in general since Lucid. 

If you aren't a gamer, the default drivers should work awesomely for you. By now, the 3d acceleration has gotten quite fast compared to Lucid, too. Create a live USB or CD session for 12.04 daily build and check to see how it works out of the box. It'll give you a good idea.

I'm not sure about that series of card entirely, but I believe I'm correct. I am 100% positive that 3d and such will work with the 4000 series and greater, though. 

If you want a cheap, low-end card with the open source driver support, then take a look into a 6450 or something.

---

### Post by kurja on 2012-03-18
Ati web site says that catalyst supports only the pcie version of the card. Are you saying that it should work anyway?

---

### Post by kurja on 2012-03-18
kaldor, I'll put that video card in and try off the live cd, I guess it will be apparent how it works then. But - how to test acceleration with live cd? I guess I should install something that uses it... never done that with a live cd.

---

### Post by kaldor on 2012-03-18
> **kurja said:**
> Ati web site says that catalyst supports only the pcie version of the card. Are you saying that it should work anyway?

I'm unsure about Catalyst, as I only use it on one PC. I'd just use the default driver if you don't do any 3d-intensive stuff. It should be fine for desktop usage with Unity 3d overall.

Edit: You *should* boot straight into a Unity 3d session. Check for shadowing under the top panel or under the windows which would indicate a full 3d session.

Edit 2: Here's a copy of the latest 64-bit daily build: [http://cdimage.ubuntu.com/daily-live/current/precise-desktop-amd64.iso](http://cdimage.ubuntu.com/daily-live/current/precise-desktop-amd64.iso)

Edit 3: According to this, the 3450 should have 3d acceleration: [https://help.ubuntu.com/community/RadeonDriver#Accelerated_3D_support](https://help.ubuntu.com/community/RadeonDriver#Accelerated_3D_support)

---

### Post by kurja on 2012-03-18
> **kaldor said:**
> I'm unsure about Catalyst, as I only use it on one PC. I'd just use the default driver if you don't do any 3d-intensive stuff. It should be fine for desktop usage with Unity 3d overall.

Edit: You *should* boot straight into a Unity 3d session. Check for shadowing under the top panel or under the windows which would indicate a full 3d session.

OK, booted... Im not sure what you mean by shadowing, but I *think* I might see something there... at least the side panel is transparent, if that indicates anything. Overall performance seems super lousy, anyway, just tried some youtube video and it is choppy even in the small view, full screen it is, well, you know.

> **kaldor said:**
> 
Edit 2: Here's a copy of the latest 64-bit daily build: [http://cdimage.ubuntu.com/daily-live/current/precise-desktop-amd64.iso](http://cdimage.ubuntu.com/daily-live/current/precise-desktop-amd64.iso)

Im running the 32bit version, but I do not think that should make a lot of difference? Latest beta release.
> **kaldor said:**
> 
Edit 3: According to this, the 3450 should have 3d acceleration: [https://help.ubuntu.com/community/RadeonDriver#Accelerated_3D_support](https://help.ubuntu.com/community/RadeonDriver#Accelerated_3D_support)

Should :) I recall that Lucid was supposed to have it too, but I think it is a problem with this card being of the AGP variety. Don`t know tho.

---

### Post by kaldor on 2012-03-18
> **kurja said:**
> OK, booted... Im not sure what you mean by shadowing, but I *think* I might see something there... at least the side panel is transparent, if that indicates anything. Overall performance seems super lousy, anyway, just tried some youtube video and it is choppy even in the small view, full screen it is, well, you know.

Unity 2d has a transparent launcher these days. To see if you're running Unity 3d, run the command * echo $DESKTOP_SESSION* and post the output here if you need any help. You may need to install Flash if there's lag. Maybe lag is due to the HTML5 player?


> **kurja said:**
> Im running the 32bit version, but I do not think that should make a lot of difference? Latest beta release.

Should be irrelevant. I just prefer the 64 bit version.


> **kurja said:**
> Should :) I recall that Lucid was supposed to have it too, but I think it is a problem with this card being of the AGP variety. Don`t know tho.

If you can't get anywhere with it here, maybe it'd be a good idea to start a thread over at Phoronix. They have a lot of knowledgeable Radeon people there.

Edit: Not a really helpful note, but if you're in the US or Canada and wanting an open source Radeon card, [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814150581") is a pretty cheap option. With the rebate you could get it for $20. Same card that I use, apart from the vendor.

---

### Post by kurja on 2012-03-18
> **kaldor said:**
> Unity 2d has a transparent launcher these days. To see if you're running Unity 3d, run the command * echo $DESKTOP_SESSION* and post the output here if you need any help. You may need to install Flash if there's lag. Maybe lag is due to the HTML5 player?

*echo $DESKTOP_SESSION* returns a blank line. As in, if I just press enter without having typed a command, I get root@ubuntu... on the next row in the terminal, having copy pasted the command and having pressed enter, I get one empty row and the the root@... prompt.

> **kaldor said:**
> 
If you can't get anywhere with it here, maybe it'd be a good idea to start a thread over at Phoronix. They have a lot of knowledgeable Radeon people there.
Thanks for the tip. Or, I might try and find a second hand nvidia agp card and see if that would take me to a path of least, or failing that, lesser, resistance...

---

### Post by kaldor on 2012-03-18
Another way to see if you're using 2d or 3d would be to try resizing the Launcher. Go to your desktop and right click on it to bring up the appearance properties. Try adjusting the Launcher size. Last time I checked, Unity 2d did not have this feature.

---

### Post by kurja on 2012-03-18
Well, I can not find such an option. In either case, it is not running terribly well out of the box in my case.

---

### Post by kurja on 2012-03-18
oops, double post.

---

### Post by meborc on 2012-03-19
you can always run ```
/usr/lib/nux/unity_support_test -p
``` to see if your hardware supports unity 3D

---

### Post by kurja on 2012-03-19
Thanks. I take it I need to be running a distro that actually has unity for that command to work though, I'm on lucid right now.

I got my hands on an X800 ati agp card, which according to [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) is well-supported, but ati site says

 > The Linux ATI Catalyst™ driver will only be supported in Linux  distributions prior to February 2009 for the legacy products listed  above.

Does that mean I can't use catalyst with Precise?

---

### Post by kaldor on 2012-03-19
> **kurja said:**
> Thanks. I take it I need to be running a distro that actually has unity for that command to work though, I'm on lucid right now.

I got my hands on an X800 ati agp card, which according to [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) is well-supported, but ati site says

 

Does that mean I can't use catalyst with Precise?

Those old cards are not going to work with Catalyst, as per AMD's open source plan. The old cards have quite okay open source support, but the 3d performance is pretty lacking. I have an X3000-something on and old PC and it runs Compiz fine (Not unity though: too little RAM).

I'm confused about the 3450 not working, though.

---

### Post by kurja on 2012-03-19
that hd3450 is an agp card and ati states that it's not supported at all, only pcie version is supported, so no surprise there, I don't know but I can only guess that problems with other drivers stem from that same source (agp/pcie).

That X800 has 256MB. I guess I'll just give it a try.

---

### Post by kaldor on 2012-03-19
> **kurja said:**
> that hd3450 is an agp card and ati states that it's not supported at all, only pcie version is supported, so no surprise there, I don't know but I can only guess that problems with other drivers stem from that same source (agp/pcie).

That X800 has 256MB. I guess I'll just give it a try.

Yeah, but I was pretty sure that AMD was referring solely to Catalyst. I guess I have some more research to do on the driver situation :)

The X800 is an r420 card, so I'd be surprised if that one has issues as well.

---

### Post by kurja on 2012-03-19
```
ubuntu@ubuntu:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI R420
OpenGL version string:  2.1 Mesa 8.0.1

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

With the X800. Video playback is choppy though...

---

### Post by kaldor on 2012-03-19
> **kurja said:**
> ```
ubuntu@ubuntu:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI R420
OpenGL version string:  2.1 Mesa 8.0.1

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```With the X800. Video playback is choppy though...

Awesome. At least now you've got something to work with.

Which video playback is choppy? Some of your own media, YouTube (Flash or h.264/WebM?), 3d games, etc? I'll sync the latest daily build and give it a go on my PC to see how it works out as well, just to rule out any Precise issues.

How smooth is the desktop?

Edit: Giving it a go myself.

My GPU:
```
ubuntu@ubuntu:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD CAICOS
OpenGL version string:  2.1 Mesa 8.0.1

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```Youtube's default HTML5 player runs like butter. I tried a few random videos and they played just fine. As a vague benchmark, I checked a modern 720p movie trailer ([here]("http://www.youtube.com/watch?v=q-Sktgm0aD8")) and it ran acceptably, though a bit laggy when fullscreened. Still, it's definitely watchable and some lag is expected with my low end GPU.

How much RAM do you have, and what's your CPU? Maybe your bottleneck is elsewhere.

---

### Post by kurja on 2012-03-19
I checked that same movie trailer, and it was watchable in the small size but really (really!) bad in full screen.

This computer has one and a half GB of ram, cpu is - as I recall - a 1600MHz single core AMD, maybe sempron? Socket 754 anyway. I`m pretty sure I had better video playback with an even older gpu (radeon 9600) in windows, but I don`t have windows at hand (unless that one old hdd still has xp on it... not sure).

I`m still on the live cd, so haven`t had the opportunity to really try 3d.

edit - booted lucid to try UFO:ai, and 3d performance is very obviously ahead of anything I had with either previous cards. My own files, be it divx or the 25mb/s stuff from a video camera, seem to play ok even in fullscreen which is kinda weird.

edit 2 - I tried that movie trailer on youtube again, and it's playing smoother in lucid than precise. I still wouldn't watch a movie in full screen, but it's better.

---

### Post by Gregory Lee on 2012-03-19
> **kurja said:**
> *echo $DESKTOP_SESSION* returns a blank line. As in, if I just press enter without having typed a command, I get root@ubuntu... 
The value of $DESKTOP_SESSION is given in the environment, and the environment is different for each user.  If you're using your desktop as, e.g., user kurja, and as kurja you do "echo *$DESKTOP_SESSION" *that will tell you which shell is controlling your (kurja's) desktop.  But if you become user root, since root does not have a desktop, the value of $DESKTOP_SESSION in root's environment will be null.

---

### Post by kaldor on 2012-03-19
> **kurja said:**
> I checked that same movie trailer, and it was watchable in the small size but really (really!) bad in full screen.

This computer has one and a half GB of ram, cpu is - as I recall - a 1600MHz single core AMD, maybe sempron? Socket 754 anyway. I`m pretty sure I had better video playback with an even older gpu (radeon 9600) in windows, but I don`t have windows at hand (unless that one old hdd still has xp on it... not sure).

I`m still on the live cd, so haven`t had the opportunity to really try 3d.

edit - booted lucid to try UFO:ai, and 3d performance is very obviously ahead of anything I had with either previous cards. My own files, be it divx or the 25mb/s stuff from a video camera, seem to play ok even in fullscreen which is kinda weird.

edit 2 - I tried that movie trailer on youtube again, and it's playing smoother in lucid than precise. I still wouldn't watch a movie in full screen, but it's better.

If your playback quality regressed then I'd file a bug report. The open source graphics have come a very long way since Lucid, so there's no reason to have such issues. Maybe it would be better on a real install or something, but you might sadly be out of luck.

---

### Post by bcarlowise on 2012-03-19
I use the AMD/ATI proprietary drivers for my HD4250 video card in my laptop. The latest ATI driver works wonderfully well in both 11.10 and 12.04 using both Unity and Gnome3. The key is to be sure you completely uninstall any currently installed driver and install the latest driver. I use the instructions here which work well:

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

Download the latest ATI driver from here:

[http://support.amd.com/us/Pages/AMDSupportHub.aspx](http://support.amd.com/us/Pages/AMDSupportHub.aspx)

---

### Post by imbjr on 2012-03-19
> **kaldor said:**
> *Major* changes in the graphics in general since Lucid. 

If you aren't a gamer, the default drivers should work awesomely for you. By now, the 3d acceleration has gotten quite fast compared to Lucid, too. Create a live USB or CD session for 12.04 daily build and check to see how it works out of the box. It'll give you a good idea.

I'm not sure about that series of card entirely, but I believe I'm correct. I am 100% positive that 3d and such will work with the 4000 series and greater, though. 

If you want a cheap, low-end card with the open source driver support, then take a look into a 6450 or something.

Oneiric gave me odd results in this regard. I created a live USB install and booted up from it: all OK. Then I installed the OS and then had to wrestle with the system to get my display working - a combo of propriety driver, chroot and the open-source driver.

Think I will give Precise a USB boot test.

---

### Post by kurja on 2012-03-19
> **Gregory Lee said:**
> The value of $DESKTOP_SESSION is given in the environment, and the environment is different for each user.  If you're using your desktop as, e.g., user kurja, and as kurja you do "echo *$DESKTOP_SESSION" *that will tell you which shell is controlling your (kurja's) desktop.  But if you become user root, since root does not have a desktop, the value of $DESKTOP_SESSION in root's environment will be null.

Good info. However, I was running a session from a live cd, so I'd expect "root" to have been the user?

---

### Post by kaldor on 2012-03-19
> **kurja said:**
> Good info. However, I was running a session from a live cd, so I'd expect "root" to have been the user?

Nope. Just "ubuntu" on live sessions. Run *whoami* to see who you are.

---

### Post by kurja on 2012-03-19
> **bcarlowise said:**
> I use the AMD/ATI proprietary drivers for my HD4250 video card in my laptop. The latest ATI driver works wonderfully well in both 11.10 and 12.04 using both Unity and Gnome3. The key is to be sure you completely uninstall any currently installed driver and install the latest driver. I use the instructions here which work well:

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

Download the latest ATI driver from here:

[http://support.amd.com/us/Pages/AMDSupportHub.aspx](http://support.amd.com/us/Pages/AMDSupportHub.aspx)

Would that be the agp or pcie variant of that ati hd card? I would presume it's pcie, which is supported, agp is not. I'm running a computer with an agp gpu.

---

### Post by kurja on 2012-03-19
> **kaldor said:**
> Nope. Just "ubuntu" on live sessions. Run *whoami* to see who you are.

Right. Sigh. Live and learn.

---

### Post by kurja on 2012-03-19
> **kaldor said:**
> If your playback quality regressed then I'd file a bug report. The open source graphics have come a very long way since Lucid, so there's no reason to have such issues. Maybe it would be better on a real install or something, but you might sadly be out of luck.

I thought something along those lines... I'm about to install Precise beta to find out.

---

### Post by kurja on 2012-03-19
> **kaldor said:**
> Nope. Just "ubuntu" on live sessions. Run *whoami* to see who you are.
More on this - when I booted with the 3450 installed, and the whole thing was running, er, sub-optimally, I got that root@ prompt. With the X800 in there I got ubuntu@ubuntu. Super weird.

---

### Post by kurja on 2012-03-19
> **kurja said:**
> I thought something along those lines... I'm about to install Precise beta to find out.

Done now, and it's **much** better. Every bit as good as one could expect from second hand parts in a 15 year old box, and then some! yay! =D

---

### Post by kaldor on 2012-03-19
Good to hear that the open source graphics are working out well for you. I'm hoping that within a few years I won't have any need to use any third-party proprietary blobs. Always best to stick with the open driver, but sadly it's not possible for quite some people :(

---

### Post by kurja on 2012-03-19
I totally agree, these last 15 minutes are my first 15 with linux when I've not been bummed about gpu support :^/

And of course now I have more pressing things to cuss about, having freshly installed an os with a new ui.... arggggggggggg

---

### Post by kaldor on 2012-03-19
> **kurja said:**
> I totally agree, these last 15 minutes are my first 15 with linux when I've not been bummed about gpu support :^/

And of course now I have more pressing things to cuss about, having freshly installed an os with a new ui.... arggggggggggg

I highly recommend getting used to these new UI's. Hard at first, but for me they've increased my productivity a lot. If the new Unity UI isn't your thing then give some of the other awesome options in 12.04 a go...

```
sudo apt-get install gnome-shell gnome-fallback
```Log out, and select them from the little Ubuntu button by your name. Have fun :)

GNOME Shell with the Adwaita theme is my current favourite environment. Fallback is recreating the old two-panel setup.

---

### Post by kurja on 2012-03-19
> **kaldor said:**
> I highly recommend getting used to these new UI's. Hard at first, but for me they've increased my productivity a lot. If the new Unity UI isn't your thing then give some of the other awesome options in 12.04 a go...

```
sudo apt-get install gnome-shell gnome-fallback
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnome-fallback
```

Unsurprisingly, my productivity for the recent hours has been about zero.

---

### Post by kaldor on 2012-03-19
> **kurja said:**
> ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnome-fallback
```

Unsurprisingly, my productivity for the recent hours has been about zero.

oops.

gnome-session-fallback, not gnome-fallback :)

Wasn't at my 12.04 machine when I wrote that.

---

