---
title: "StackSwitch FTW! (Compiz Fusion development)"
date: 2008-06-20
forum: The Cafe
---

### Post by Kernel Sanders on 2008-06-20
[http://fusioncast.blogspot.com/2008/06/fusioncast-vi-new-plugin-stackswitch.html](http://fusioncast.blogspot.com/2008/06/fusioncast-vi-new-plugin-stackswitch.html)

:guitar:

---

### Post by vishzilla on 2008-06-20
Awesome plugin. Attractive as well as a functional plugin

---

### Post by geoken on 2008-06-20
Can someone give a brief description of what this does? YouTube is blocked here so I haven't been able to view the screencast.

---

### Post by tad1073 on 2008-06-20
I get this error when trying to make stackswitch. 

```
Makefile:58: *** [ERROR] Package pangocairo was not found in the pkg-config search path. 
Perhaps you should add the directory containing `pangocairo.pc' to the PKG_CONFIG_PATH 
environment variable Package 'pangocairo', required by 'compiz-text', not found.
```

---

### Post by tribaal on 2008-06-20
Looks like the kind of plugin I'd use :)

Thanks for the link :)

- Trib'

---

### Post by Exsecrabilus on 2008-06-20
I only use Compiz Fusion to show off the effects when other people are around.

Otherwise, I turn them off for more snappier performance and faster computing.

---

### Post by gameryoshi600 on 2008-06-20
thats awesome!

---

### Post by 71CH on 2008-06-20
Can somebody help me install this.  Do I need Compiz from git to install this?

---

### Post by tribaal on 2008-06-20
Good question - I would assume so, but the git branch for the plugin itself gives me a timeout error.
Since I'm at work I suspect some kind of corporate firewall paranoia... I'll try from home instead and report back :)

- Trib'

---

### Post by Exsecrabilus on 2008-06-20
> **71CH said:**
> Can somebody help me install this.  Do I need Compiz from git to install this?
Yeah, I know right? How do we install it?

I'm assuming you need to install [Compiz-Git](http://ubuntuforums.org/showthread.php?t=781218), then type in the address bar of Firefox:

git://anongit.compiz-fusion.org/fusion/plugins/stackswitch

And it will automatically install.....but that's just my guess. Can anyone verify?

---

### Post by tribaal on 2008-06-20
Actually download sources from git require you to install [git-core]("apt://git-core"), and then invoke 
```
git clone git://anongit.compiz-fusion.org/fusion/plugins/stackswitch
``` from the command-line.

Like I said, I couldn't test this from work, so I'll try tonight.

Cheers,

- Trib'

---

### Post by 71CH on 2008-06-20
well i tried that git thing and I can't seem to find StackSwitch in the settings

---

### Post by miggols99 on 2008-06-20
That's amazing! I like that there's lots of innovation and **no** copying ;) This is definately better than flip switch/scale.

---

### Post by Exsecrabilus on 2008-06-20
Now we just wait for Microsoft or Apple to copy it and claim they invented it.

---

### Post by zmjjmz on 2008-06-20
I can't seem to compile it.
make returns ```
Makefile:58: *** [ERROR] Package pangocairo was not found in the pkg-config search path. Perhaps you should add the directory containing `pangocairo.pc' to the PKG_CONFIG_PATH environment variable Package 'pangocairo', required by 'compiz-text', not found.  Stop.

```

---

### Post by madjr on 2008-06-20
> **Exsecrabilus said:**
> Now we just wait for Microsoft or Apple to copy it and claim they invented it.

but the video is prove we invented it first :)

anyway, this would be a great base plugin for something like real desktop 3d thing

[IMG]http://screen.uptodown.com/screen/screen.php?screen=Real%20Desktop%201.1-4.jpg[/IMG]

---

### Post by adityakavoor on 2008-06-20
Install compiz fusion from git : [http://blog.kavoor.info/?p=27#](http://blog.kavoor.info/?p=27#)

---

### Post by smartboyathome on 2008-06-20
Or, you can use the Compiz Packagers PPA. :D
[https://launchpad.net/~compiz/+archive](https://launchpad.net/~compiz/+archive)

EDIT: Attached is a screenshot of stackswitch on Ubuntu. :)

---

### Post by fatality_uk on 2008-06-20
Freaking awesome!!!!
Atlantis and WII headtracker on that site are just unreal :D
Yummy warm gloaty feeling using Linux & Ubuntu :D

---

### Post by f1uxam on 2008-06-20
> **71CH said:**
> well i tried that git thing and I can't seem to find StackSwitch in the settings
Same here -- I look in the CCSM part of Fusion Icon and there's no setting to invoke it.
But, Synaptics Package Manger shows it has been installed, as per smartboyathome PPA instructions.

**Please[B]**[/B]
somebody tell me how to start it!

---

### Post by Exsecrabilus on 2008-06-20
> **smartboyathome said:**
> Or, you can use the Compiz Packagers PPA. :D
[https://launchpad.net/~compiz/+archive](https://launchpad.net/~compiz/+archive)

EDIT: Attached is a screenshot of stackswitch on Ubuntu. :)
I installed it. Now how do I enable it?
(I thinkk I see it in *CompizConfig Settings Manager*, but I just want to be sure.)

---

### Post by kevin11951 on 2008-06-20
> **f1uxam said:**
> Same here -- I look in the CCSM part of Fusion Icon and there's no setting to invoke it.
But, Synaptics Package Manger shows it has been installed, as per smartboyathome PPA instructions.

**Please[B]**[/B]
somebody tell me how to start it!

if you have the ppa,

```
sudo apt-get install stackswitch
```

---

### Post by mvavrik on 2008-06-20
> **tribaal said:**
> Actually download sources from git require you to install [git-core]("apt://git-core"), and then invoke 
```
git clone git://anongit.compiz-fusion.org/fusion/plugins/stackswitch
``` from the command-line.

Like I said, I couldn't test this from work, so I'll try tonight.

Cheers,

- Trib'

I've installed git-core using Synaptic and ran the line above in the command line.  Stackswitch installs itself into the current directory and when I attempt to 'make', I receive an error that "Compiz not installed".  

I assure you that it is; I have desktop rain, cube, fire all enabled and working correctly. Could someone post a quick step-by-step for installing stackswitch?

---

### Post by kevin11951 on 2008-06-20
> **mvavrik said:**
> I've installed git-core using Synaptic and ran the line above in the command line.  Stackswitch installs itself into the current directory and when I attempt to 'make', I receive an error that "Compiz not installed".  

I assure you that it is; I have desktop rain, cube, fire all enabled and working correctly. Could someone post a quick step-by-step for installing stackswitch?

1. Open "System > Administration > Software Sources"

2. Click On The "Third Part Software" Tab

3. Click On "Add..."

4. Copy And Paste: "deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main"

5. Open A Terminal:

6. sudo apt-get update

7. sudo apt-get upgrade

8. sudo apt-get install stackswitch

9. enjoy

---

### Post by Exsecrabilus on 2008-06-20
Everyone's telling everyone how to add the repo and install it, but no one's saying a word on how to enable it. :?

---

### Post by mvavrik on 2008-06-20
> **kevin11951 said:**
> 1. Open "System > Administration > Software Sources"

2. Click On The "Third Part Software" Tab

3. Click On "Add..."

4. Copy And Paste: "deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main"

5. Open A Terminal:

6. sudo apt-get update

7. sudo apt-get upgrade

8. sudo apt-get install stackswitch

9. enjoy


Ah, thank you very much.



> Everyone's telling everyone how to add the repo and install it, but no one's saying a word on how to enable it. 

Is there an enable step?  I figured you enable it through "Advanced Desktop Settings"; the same place where you enable the desktop cube, etc.   ?

---

### Post by Exsecrabilus on 2008-06-20
I want to make sure what I'm assuming how to install it is correct.

So I need someone to verify and tell how to enable it via *CCSM*.

---

### Post by smartboyathome on 2008-06-20
Install "Compizconfig-settings-manager" using synaptic. That will get it for you.

---

### Post by Exsecrabilus on 2008-06-20
I have that installed.....but what I'm asking is what's the section name in CCSM?

---

### Post by smartboyathome on 2008-06-20
Window Management. You can just use the search bar on the side to look for Stack, and that will get it for you.

---

### Post by o'rly on 2008-06-20
pretty cool, thnaks

---

### Post by smartboyathome on 2008-06-20
Another thing - This repo also contains the cube deformation plugin (to make the cube a sphere/cylinder). Try it out, I know I wasn't dissapointed with it. :D

---

### Post by maniacmusician on 2008-06-20
The cube deformation is nice, but it doesn't handle cube caps very well at the moment. Hopefully, that'll change.

---

### Post by wootah on 2008-06-20
I think this plugin is a little over rated ...

---

### Post by Exsecrabilus on 2008-06-20
Please, how do I enable this effect?
I open up CCSM then what? ..... :?

---

### Post by klange on 2008-06-20
> **maniacmusician said:**
> The cube deformation is nice, but it doesn't handle cube caps very well at the moment. Hopefully, that'll change.

My caps look flawless. It has just as many options as the original Cube Caps plugin, even with deformations...

---

### Post by isaacj87 on 2008-06-20
> **WindowsSucks said:**
> My caps look flawless. It has just as many options as the original Cube Caps plugin, even with deformations...

Hey WindowsSucks,

I know your a core-dev for Compiz Fusion so I thought I'd mention this to you (ya know, while we're on the topic of cube caps). After cube caps got merged into the deformation/reflection plugin there's a huge slow down (fps) with the cylinder or sphere deformation enabled. This didn't use to be the case. I used to use the "cylinder" all the time. Now it's basically unusable for me. I think it has to do with some transparency (my not being able to turn it off via CCSM) and my Intel (i915, GMA900, AIGLX) not liking it. Should I go ahead and file a bug report?

---

### Post by Exsecrabilus on 2008-06-20
/Wrist

Wow, everyone keeps on talking about how great the Stackswitch plugin is, but no one cares to explain how to enable it?

---

### Post by madjr on 2008-06-20
> **WindowsSucks said:**
> My caps look flawless. It has just as many options as the original Cube Caps plugin, even with deformations...

you mean caps like this

[IMG]http://news.opensuse.org/wp-content/uploads/2008/06/cube-deform-sphere-thumb.jpeg[/IMG]

---

### Post by klange on 2008-06-20
> **isaacj87 said:**
> Hey WindowsSucks,

I know your a core-dev for Compiz Fusion so I thought I'd mention this to you (ya know, while we're on the topic of cube caps). After cube caps got merged into the deformation/reflection plugin there's a huge slow down (fps) with the cylinder or sphere deformation enabled. This didn't use to be the case. I used to use the "cylinder" all the time. Now it's basically unusable for me. I think it has to do with some transparency (my not being able to turn it off via CCSM) and my Intel (i915, GMA900, AIGLX) not liking it. Should I go ahead and file a bug report?

With an Intel, it's probably not transparency. Anything involving slow downs is probably because of large textures. I believe some optimization things were missing in the merged cube caps.

[img]http://random.ogunderground.com/compiz/itt_caps.png[/img]

---

### Post by Exsecrabilus on 2008-06-20
> **madjr said:**
> you mean caps like this

[IMG]http://news.opensuse.org/wp-content/uploads/2008/06/cube-deform-sphere-thumb.jpeg[/IMG]
Wow, that looks really nice.

---

### Post by smartboyathome on 2008-06-20
> **Exsecrabilus said:**
> Please, how do I enable this effect?
I open up CCSM then what? ..... :?

See the search box on the side? Type in stackswitch, and it will come up with the appropriate option for you. Just enable that and you are on your way.

---

### Post by Exsecrabilus on 2008-06-20
> **smartboyathome said:**
> See the search box on the side? Type in stackswitch, and it will come up with the appropriate option for you. Just enable that and you are on your way.
No wonder I couldn't find it, when I type in just "stack" in the filter, nothing comes up.
Can anyone help me?

BTW, I added the Compiz PPA and installed from there.

---

### Post by f1uxam on 2008-06-20
Stackswitch has been installed as instructed.
There is no setting to invoke it in ccsm under "Window Management."
**Please**
tell me how to start this plugin.

---

### Post by barbedsaber on 2008-06-20
I tried both guides to install stackswitch, (the repo one, and the guide on this forum) and I broke somthing. how can I just uninstall everything relating to compiz, and reinstall compiz, compleatly?

---

### Post by adityakavoor on 2008-06-20
> **smartboyathome said:**
> See the search box on the side? Type in stackswitch, and it will come up with the appropriate option for you. Just enable that and you are on your way.

What is your version of ccsm ?

---

### Post by Ioky on 2008-06-20
feels a bit weird, but looks cool

---

### Post by Exsecrabilus on 2008-06-20
> **adityakavoor said:**
> what Is Your Version Of Ccsm ?
0.7.7.

---

### Post by adityakavoor on 2008-06-20
I enabled it. Yippie. [http://is.gd/CD8](http://is.gd/CD8)

---

### Post by maniacmusician on 2008-06-20
> **madjr said:**
> you mean caps like this

[IMG]http://news.opensuse.org/wp-content/uploads/2008/06/cube-deform-sphere-thumb.jpeg[/IMG]
Ah, I forgot, my caps get scaled down to size, and need to be warped a little bit to fit. If I deform the cube, the white background on the caps shows along some of the edges. So the problem is really with scaled images, I guess.

But since this thread is really about Stackswitch; are there any plans to create an "Initiate" binding for it, so that I could, perhaps, assign a screen edge to it, and be able to browse the windows using my mouse instead of my keyboard? My favorite thing about scale was that it didn't matter whether I was using a mouse or a keyboard, I could use either to easily engage and navigate the plugin.

---

### Post by Exsecrabilus on 2008-06-20
> **adityakavoor said:**
> I enabled it. Yippie. [http://is.gd/CD8](http://is.gd/CD8)
Me too, I just compiled from source. XD

---

### Post by barbedsaber on 2008-06-20
Ok, I think I removed and reinstalled compiz, but now I can't open ccsm.
when I try and do it from a terminal I get
```
harry@ubuntu:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: libcompizconfig.so.0: cannot open shared object file: No such file or directory

```
what have I missed?

---

### Post by maniacmusician on 2008-06-21
did you remember to remove and reinstall ccsm? it's called compizconfig-settings-manager in the repos.

---

### Post by barbedsaber on 2008-06-21
> **maniacmusician said:**
> did you remember to remove and reinstall ccsm? it's called compizconfig-settings-manager in the repos.

yup

---

### Post by maniacmusician on 2008-06-21
> **barbedsaber said:**
> yup
well, the file it's complaining about is in the package libcompizconfig0, which is a dependency of ccsm, so it should be installed as well. you should double check that it is.

Where did you install these packages from? the PPA, regular repositories, etc.

---

### Post by barbedsaber on 2008-06-21
its ok, I figured it out, gave up on stackswitch, and will try that again later.

---

### Post by seenxu on 2008-06-21
> **barbedsaber said:**
> its ok, I figured it out, gave up on stackswitch, and will try that again later.

don't forget after upgrade to [color=red]reload the whole compiz stuff[/color], and then search in ccsm for "stack window switcher" make sure to click the checkbox, and super+tab, whoo...

cool effect indeed! thx to the dev team.

---

### Post by Sherina on 2008-06-23
I tryed kevin11951's method changing "hardy main" to "gusty main" and I get an error saying its not found. Will this plugin work for gusty?

---

### Post by zmjjmz on 2008-06-23
Does this need .7.6?

---

### Post by smartboyathome on 2008-06-23
> **Sherina said:**
> I tryed kevin11951's method changing "hardy main" to "gusty main" and I get an error saying its not found. Will this plugin work for gusty?

I'm afraid not. It hasn't been backported to gutsy, only hardy. :(

And yes, it does need 0.7.6.

---

### Post by sharks on 2008-06-24
A new compiz effect --- Stackswitch.

For Video:[http://www.youtube.com/watch?v=dJbgjBX8DaI](http://www.youtube.com/watch?v=dJbgjBX8DaI)

Its great.

---

### Post by 71CH on 2008-06-24
[http://ubuntuforums.org/showthread.php?t=835186](http://ubuntuforums.org/showthread.php?t=835186)

---

### Post by sharks on 2008-06-24
sorry . please report the thread to be moved or removed.

---

### Post by K.Mandla on 2008-06-24
Similar threads merged.

---

### Post by decrow06 on 2009-12-20
does anybody know about the status of this plugin in karmic?

---

### Post by illpig on 2010-09-24
opening the thread again with having some troubles in lucid, with ccsm 0.8.2 (compiz 1:0.8.6) and installed stackswitch from ppa. enabling it in ccsm its off after short time again. any command for terminal needed or to try out for me?

thanks and greetings from berlin.

---

