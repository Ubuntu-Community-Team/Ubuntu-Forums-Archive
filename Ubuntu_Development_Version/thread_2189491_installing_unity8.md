---
title: "installing unity8"
date: 2013-11-22
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-11-22
Currently installing unity8 on desktop. Just have to check this out :)

```

sudo apt-get install unity8

```

---

### Post by ventrical on 2013-11-22
It installed a variety of files. No show stoppers. Looks like normal unity , except faster. Actually I am not even sure if Unity 8 is running. Will look see.

---

### Post by ventrical on 2013-11-22
So far..

```

ventrical@ventrical-desktop:~$ unity --version
unity 7.1.2
ventrical@ventrical-desktop:~$ 


```

---

### Post by deadflowr on 2013-11-22
Run the two commands at the end of this article.
[http://www.omgubuntu.co.uk/2013/08/unity-8-ubuntu-13-10-arrives](http://www.omgubuntu.co.uk/2013/08/unity-8-ubuntu-13-10-arrives)

those would be the export command and the unity8 -mousetouch command.

Then when the window opens, simply click on it, it should load you as guest(me thinks).

---

### Post by ventrical on 2013-11-22
Yep ... there it is :) lol

---

### Post by ventrical on 2013-11-22
> **deadflowr said:**
> Run the two commands at the end of this article.
[http://www.omgubuntu.co.uk/2013/08/unity-8-ubuntu-13-10-arrives](http://www.omgubuntu.co.uk/2013/08/unity-8-ubuntu-13-10-arrives)

those would be the export command and the unity8 -mousetouch command.

Then when the window opens, simply click on it, it should load you as guest(me thinks).

It says to just run 'unity8' in terminal.. and I did and got the phone :) 

Thanks .. I'll look at your method also.

---

### Post by ventrical on 2013-11-22
Some of the apps are already working :) Actually it works like a little mini Unity 2D thingy. Now if they can get this effect on a tablet emulator that will be  a real accomplishment (probably already have) and seeing that they have come so far, so fast .. it's looking good ! :)

---

### Post by grahammechanical on 2013-11-22
For the record there is a Unity 8 Shell in the Trusty software centre that does it for us. Unity 8 shell sits on top of Unity 7. Anyway, Unity 7 is not replaced. This might be the sort of thing available in 14.04 for those who choose it. Remember, anything looking like a phone app will have swipe gestures from the side and top and bottom.

The Dash gives a system setting with an icon like a blank page. That loads the systems settings for the phone.
 
Regards.

---

### Post by ventrical on 2013-11-22
After experimenting a little bit with this new app I was able to expand it and make it look like an android tablet and behave like an iPad using mouse and key.

Regards..

---

### Post by ventrical on 2014-05-21
> **ventrical said:**
> After experimenting a little bit with this new app I was able to expand it and make it look like an android tablet and behave like an iPad using mouse and key.

Regards..

Running unity8 in Mir will nto give me a mouse... but it looks nice and is responsive  to mouse movement swipes .. but nothing like my last test. btw .. I can log on from lightdm.

---

### Post by grahammechanical on 2014-05-21
> [COLOR=#000000]btw .. I can log on from lightdm[/COLOR]

I cannot. I am referring to the unity8-mir login session that is supposed to be available for 14.04 users. The only improvement I have noticed over the last few weeks is that I can now get to a tty to reboot and do not need to use the power switch.

I do have another install with Unity 8+Mir+the SDK+core apps and that works OK.

---

### Post by ventrical on 2014-05-21
> **grahammechanical said:**
> I cannot. I am referring to the unity8-mir login session that is supposed to be available for 14.04 users. The only improvement I have noticed over the last few weeks is that I can now get to a tty to reboot and do not need to use the power switch.

I do have another install with Unity 8+Mir+the SDK+core apps and that works OK.


In contradistinction I cannot logon to the unity8-xorg session. It is there in lightdm but when I log on I just get background screen. (no terminal ,ctrl+alt+F1 does not work) locked up solid , (ctrl+alt+del no go either). So I have to hard shutdown. Admittedly I must have borked it along the way somewhere because I first installed the Unity8 package from USC. I then removed it and installed it from synaptic then. Of course switching back and forth from Mir to Xorg requires some extra work with editing .conf files but I will research into that.

Thanks for your reply.

Regards..

---

### Post by ventrical on 2014-06-07
Recent unity8 updates do absolutely nothing to get it to work in xorg.

---

### Post by ventrical on 2014-06-07
Unity8 will not quit, even after log off. I will take up all the resources of one core (100%).

Edit:

Reboot will fix.

---

### Post by ventrical on 2014-10-19
> **deadflowr said:**
> Run the two commands at the end of this article.
[http://www.omgubuntu.co.uk/2013/08/unity-8-ubuntu-13-10-arrives](http://www.omgubuntu.co.uk/2013/08/unity-8-ubuntu-13-10-arrives)

those would be the export command and the unity8 -mousetouch command.

Then when the window opens, simply click on it, it should load you as guest(me thinks).

I just wanted to bump this because it was what I was looking for with unity8 from terminal.

Regards.

---

### Post by craig10x on 2014-10-19
Interesting article on softpedia about the current development going on for the desktop version of unity 8....what you are seeing now on the desktop version is a very raw, rough version of what it will become over the next year and a half or so...we won't likely see unity 8 desktop as the default until the next LTS (16.04) and that is also when ubuntu 6 month version should  be eliminated and essentially replaced by a rolling style release...as Mark Shuttleworth was recently talking about (at convergence which will be when unity 8 desktop becomes the default).
[http://news.softpedia.com/news/Canonical-Details-Plans-for-Unity-8-Integration-in-Ubuntu-Desktop-462117.shtml](http://news.softpedia.com/news/Canonical-Details-Plans-for-Unity-8-Integration-in-Ubuntu-Desktop-462117.shtml)

---

### Post by ventrical on 2014-10-19
> **craig10x said:**
> Interesting article on softpedia about the current development going on for the desktop version of unity 8....what you are seeing now on the desktop version is a very raw, rough version of what it will become over the next year and a half or so...we won't likely see unity 8 desktop as the default until the next LTS (16.04) and that is also when ubuntu 6 month version should  be eliminated and essentially replaced by a rolling style release...as Mark Shuttleworth was recently talking about (at convergence which will be when unity 8 desktop becomes the default).
[http://news.softpedia.com/news/Canonical-Details-Plans-for-Unity-8-Integration-in-Ubuntu-Desktop-462117.shtml](http://news.softpedia.com/news/Canonical-Details-Plans-for-Unity-8-Integration-in-Ubuntu-Desktop-462117.shtml)


Thanks . 

 I guess I sort of overshot the runway in thinking that we may be able to look under the hood during the next cycle coming up.

Regards..

---

### Post by craig10x on 2014-10-19
@ventrical: very true...but still, nice to know that they will be really concentrating on getting it perfected for the desktop now and that by next LTS we should see it as default and hopefully also finally get the rolling style ubuntu many of us here have always hoped for...including myself :mrgreen:

---

### Post by grahammechanical on 2014-10-19
> [COLOR=#000000]thinking that we may be able to look under the hood during the next cycle coming up.[/COLOR]

As with everything software related it all depends on how well the development work proceeds. The Canonical Desktop team manager in his blog has outlines the intentions.

> [COLOR=#333333][FONT=Georgia]What we&#8217;ve decided to do this time is to keep the same, stable Unity 7 desktop as the default while we offer users who want to opt-in to Unity8 an option to use that desktop. As development continues the Unity 8 desktop will get better and better.  It will benefit from a lot of the advances which have come about through the development of the phone OS and will benefit from continual improvements as the releases happen.[/FONT][/COLOR]

[LIST]
[*]**14.04 LTS**: Unity 7 default / Unity 8 option for the first time
[*]**14.10**: Unity 7 default / Unity 8 new rev as an option
[*]**15.04**: Unity 7 default / Unity 8 new rev as an option
[*]**15.10**: Potentially Unity 8 default / Unity 7 as an option
[*]**16.04 LTS**: Unity 8 default / Unity 7 as an option
[/LIST]
[COLOR=#333333][FONT=Georgia]As you can see, this gives us a full 2 cycles (in addition to the one we&#8217;ve already done) to really nail Unity 8 with the level of quality that people expect.[/FONT][/COLOR]


I think that they are going the right way about this. They are not putting the stability of the 14.04 LTS at risk. But do not forget, they do not want to put the stability of the 16.04 LTS at risk. It won't do anybody any good rushing everything during the 16.04 development cycle. Look at the actual blog and look at the section Things that are coming in the new Ubuntu desktop. All this change cannot be left just to one development cycle, the 16.04 cycle.

[http://mhall119.com/2014/10/unity-8-desktop/](http://mhall119.com/2014/10/unity-8-desktop/)

All the present default desktop applications will have to work on Mir and under Unity 8. That will have to be tested.

Regards.

---

### Post by ventrical on 2014-10-19
> **grahammechanical said:**
> 

All the present default desktop applications will have to work on Mir and under Unity 8. That will have to be tested.

Regards.

In that light our work is cut out for us then.

Regards..

---

### Post by ventrical on 2014-10-19
> **ventrical said:**
> I just wanted to bump this because it was what I was looking for with unity8 from terminal.

[http://www.omgubuntu.co.uk/2013/08/unity-8-ubuntu-13-10-arrives](http://www.omgubuntu.co.uk/2013/08/unity-8-ubuntu-13-10-arrives)
Regards.

  That code does not work with the Ubuntu-Desktop-Next from gnome-terminal.

---

