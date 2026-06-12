---
title: "New Nvidia drivers released."
date: 2006-11-07
forum: The Cafe
---

### Post by plb on 2006-11-07
[http://www.nvidia.com/object/linux_display_ia32_1.0-9629.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9629.html)

---

### Post by Ramses de Norre on 2006-11-07
So this means you can use beryl/compiz on aiglx with nvidia cards now??

Man, I should get rid of my ati if they don't make this possible too.. (probably not in the near future)

---

### Post by John.Michael.Kane on 2006-11-07
Now you will have to wait to see if get's added to the edgy repos.

---

### Post by roderikk on 2006-11-07
Did anyone try them yet? I hope they solve the 'black window bug' I have been experiencing sometimes... In the beta drivers this happened because apparently when the memory of my card overflowed it just didn't draw the window instead of taking memory from the ram. At least, that is what I read/understood...

---

### Post by bastiegast on 2006-11-07
Great news \\:D/ , I'm using beta currently and I just love having aiglx instead of xgl.

Will there be a howto on removing beta drivers installed with the nvidia installer and installing the new ones from the repo's?

---

### Post by prizrak on 2006-11-07
> **bastiegast said:**
> Great news \\:D/ , I'm using beta currently and I just love having aiglx instead of xgl.

Will there be a howto on removing beta drivers installed with the nvidia installer and installing the new ones from the repo's?

You are not using either AIGLX or XGL you are using the driver's ability to do compositing. You can download and install the drivers in the same way you did the beta.

---

### Post by bastiegast on 2006-11-07
> **prizrak said:**
> You are not using either AIGLX or XGL you are using the driver's ability to do compositing. You can download and install the drivers in the same way you did the beta.

Yeah that's what I meant, i love *being able* to use AIGLX because of GLX_EXT. About the installing, yes, of course, your right, I should try things first before asking. but i thought the transition to drivers from the nvidia installer to drivers installed through synaptic might give some probs.

---

### Post by prizrak on 2006-11-07
> **bastiegast said:**
> Yeah that's what I meant, i love *being able* to use AIGLX because of GLX_EXT. About the installing, yes, of course, your right, I should try things first before asking. but i thought the transition to drivers from the nvidia installer to drivers installed through synaptic might give some probs.
I think Synaptic does the same thing that the installer does only behind the scenes. Not sure, I suggest scouting the nVidia site to see if they got any info on removing it.

---

### Post by PriceChild on 2006-11-07
I'm running the latest drivers and have updated my guides.

Nothing new really... they just work :)

Amaranth is currently updating his repos.

---

### Post by tseliot on 2006-11-07
I'll add them to my repositories ASAP.

---

### Post by prizrak on 2006-11-07
Damnit, testing is a pain in the butt I need to get my desktop up :(

---

### Post by OffHand on 2006-11-07
I installed the new driver and it works fine on my machine.

---

### Post by professor_chaos on 2006-11-07
New driver work fine here.

---

### Post by darkhatter on 2006-11-07
I still get the black screen issue with beryl, I like the new splash screen :)

---

### Post by Dual Cortex on 2006-11-07
Drivers works great!

---

### Post by 23meg on 2006-11-07
> **darkhatter said:**
> I still get the black screen issue with beryl
Same here.

---

### Post by robtotheb on 2006-11-08
Update manager just installed the new Nvidia driver.  It works fine except in Cedega / wine - my games are now very low frame rate. ](*,) 
I'm going to stop using the update manager because this is the second time it has screwed up my graphics settings.

---

### Post by Spano on 2006-11-08
> I like the new splash screen:) 
Pretty Cool.

---

### Post by fbwr75215 on 2006-11-08
I am glad to see these drivers out now.  I am just starting again in Linux.  I have been trying to get twinview to work.  I was able to get it to work but I hate the my CRT is primary when I want my LCD to be primary.

Does anyone know how to use the new function to switch which screen is the primary yet?

---

### Post by prizrak on 2006-11-08
> **darkhatter said:**
> I still get the black screen issue with beryl, I like the new splash screen :)

It's probably something that's gonna have to be fixed by Beryl people.
Also anyone know if the drivers finally support GPU throtling and screen rotation (flipping the screen to the side or upside down for tablets)?

---

### Post by geokok1981 on 2006-11-08
Drivers work perfect here + beryl.
Huge impromvent in the gui drivers config tool.
Starts to look like a windows driver....

---

### Post by red_Marvin on 2006-11-08
Do anyone of you use it on a laptop with a geforce Go 7300 card?
(If it works then it might seal a deal for me :))

---

### Post by 23meg on 2006-11-08
> **prizrak said:**
> It's probably something that's gonna have to be fixed by Beryl people.
Also anyone know if the drivers finally support GPU throtling and screen rotation (flipping the screen to the side or upside down for tablets)?
Screen rotation with xrandr has already been working for quite a long time.

---

### Post by User_Program on 2006-11-08
All is working good here too. (Beryl also works great) This is by far one of the best nvidia driver releases for linux.  I wish all there releases could be like this.

"From nivida 9629 changlog
Added new NVIDIA logo artwork to nvidia-settings and X driver splashscreen; the X driver splashscreen can now be configured with the new "LogoPath" X configuration option. "

Does this mean we can now change the splash screen logo to anything we like? (even though I love the new splash)  if so how and what file type do we use?

---

### Post by Perfect Storm on 2006-11-08
Works great here also with beryl. No problem on my machine.

---

### Post by PriceChild on 2006-11-08
> **Artificial Intelligence said:**
> Works great here also with beryl. No problem on my machine.Same...

Btw there is a problem with Some Geforce 4 Ti cards... specifically those with an Nv2 chipset or something.

---

### Post by fbwr75215 on 2006-11-08
I got home and tried to update the new drivers but it says I am fully updated.  I was not running Ubuntu until I got home.

Does anyone have any ideas as to why I am not seeing the new drivers yet?  I have tried the update tool and synaptic.  I am running 6.10.

---

### Post by Wafflesomd on 2006-11-08
Uh, can someone tell me how to install these.

I know this isnt the help portion of the forums, but I could use it.

It keeps telling me to shutdown x.

I've been using Ubuntu for 4 months and I still havnt gotten this down lol

---

### Post by Spatulas on 2006-11-08
I installed the drivers, and they are working, but I get "ripping" of sorts... when something changes, a lot of the time the bottom of that will freeze until something makes that update (scrolling etc).  A good example is highlighting: most of the time when I highlight now, either parts of the highlighted text won't update (so the top of the text will look highlighted, and the bottom won't), or when I deselect it, part of the text will appear to still be highlighted, until I click again, or scroll, or something of the sort.

Can anyone help me out with this?  The beta drivers were working fine before...

Oh, and Wafflesomd, you need to switch to tty2 (Ctrl+Alt+F2), and run sudo /etc/init.d/gdm stop, then run the driver install.  After, to start x again, type sudo /etc/init.d/gdm start, and you should be set.

---

### Post by Wafflesomd on 2006-11-08
Lets say I have the nvidia drivers on my desktop, what comman would I use.

---

### Post by hscottyh on 2006-11-08
> **Wafflesomd said:**
> Lets say I have the nvidia drivers on my desktop, what comman would I use.

I wouldn't use the one directly from Nvidia. I would use Amaranth's repository and install it with aptitude ,if I were you.

Read this thread for a howto:
[http://ubuntuforums.org/showthread.php?p=1536245](http://ubuntuforums.org/showthread.php?p=1536245)

---

### Post by Spatulas on 2006-11-09
Does anyone have any ideas for my tearing problem?

---

### Post by maagimies on 2006-11-09
Damn, it has problem with my Geforce's chipset. (The whole glxinfo/glxgears/beryl/mushroom -> Segmentation fault thing)
```
01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3] (rev a3)
```
I'll keep using 1.0-9626.

---

### Post by spockrock on 2006-11-09
well if anyone has an 8800gtx or gts nvidia has a beta driver up that includes support for those cards.

[http://www.nzone.com/object/nzone_downloads_rel70betadriver.html](http://www.nzone.com/object/nzone_downloads_rel70betadriver.html)

also the black windows should be fixed in beryl 0.1.2 I have using the svn and has been fixed for me.

---

### Post by jstew on 2006-11-09
> **Spatulas said:**
> Does anyone have any ideas for my tearing problem?

Yes,

The problem is in the composite extension. Even if you do not use it, it's enabled by default and you have to disable it explicitly.

sudo nvidia-xconfig --no-composite

Needless to say, if you use composite then don't do that, but it solved my Xv tearing problem with mythtv and also reduced the system load while watching videos in myth from 3.5 to .9.

---

### Post by el_itur on 2006-11-09
I've upgraded from the .run of nvidia's page. I don't know if it is some kind of placebo effect but I think it is much stable than beta driver, My windows qith compiz and my opengl games runs faster and without the framedrops the beta driver used to caused me. Really really happy with it. I belive the implementation of TFP will get better with subsecuent releases, this driver just has initial support for this extension. 

PS: I didn't use nvidia-xconfig it always messes my xorg.conf

---

### Post by Spatulas on 2006-11-09
> **jstew said:**
> Yes,

The problem is in the composite extension. Even if you do not use it, it's enabled by default and you have to disable it explicitly.

sudo nvidia-xconfig --no-composite

Needless to say, if you use composite then don't do that, but it solved my Xv tearing problem with mythtv and also reduced the system load while watching videos in myth from 3.5 to .9.

IIRC, my xorg.conf has composite turned off, but I will verify that when I have a chance later today.  I'm pretty sure that it is though, so I don't think that is the issue.

---

### Post by PriceChild on 2006-11-09
> **PriceChild said:**
> I'm running the latest drivers and have updated my guides.

Nothing new really... they just work :)

Amaranth is currently updating his repos.God i'm ahead of myself...

I'm now running > 1.0-9742And I'm sure Beryl is so much smoother... no more tearing rotating the cube.

---

### Post by Perfect Storm on 2006-11-09
smartass :mrgreen:

---

### Post by Spatulas on 2006-11-09
> **Spatulas said:**
> IIRC, my xorg.conf has composite turned off, but I will verify that when I have a chance later today.  I'm pretty sure that it is though, so I don't think that is the issue.

Doh.  It's enabled... I am using Beryl though, so I believe it is needed?

---

### Post by IYY on 2006-11-09
I love these drivers! My Edgy desktop is now fast and smooth even without Compiz.

---

### Post by PriceChild on 2006-11-10
> **PriceChild said:**
> God i'm ahead of myself... running 9742

I'm now running And I'm sure Beryl is so much smoother... no more tearing rotating the cube.

> **Artificial Intelligence said:**
> smartass :mrgreen:Guide here: [http://ubuntuforums.org/showthread.php?t=296933](http://ubuntuforums.org/showthread.php?t=296933)

be careful :)

---

