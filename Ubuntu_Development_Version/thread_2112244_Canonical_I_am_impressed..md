---
title: "Canonical I am impressed."
date: 2013-02-04
forum: Ubuntu Development Version
---

### Post by nomenkultur on 2013-02-04
I don't know what you are doing but this thing feels like it's on steroids.

 This laptop has windows and ubuntu 13 feels snappier and much more responsive.

 I noticed a few awful regressions when I installed early this week but the kernel updates have sorted everything out.

 
 Keep doing what you are doing.

 
 btw:  I asked for the mesa utils thing and it got added, I asked for a switch to SNA and it was done, now I will push my luck and ask for the inclusion of this vaapi thing that I found out when I was looking for h264 codecs (it seems to improve performance):

[http://youtu.be/xfN2sMJJU1s](http://youtu.be/xfN2sMJJU1s)

thx

---

### Post by craig10x on 2013-02-04
For Sure :-D

It's still got almost 3 months to final release and already seems so much better then 12.10...

---

### Post by kurt18947 on 2013-02-04
> **craig10x said:**
> For Sure :-D

It's still got almost 3 months to final release and already seems so much better then 12.10...

I agree but then I think back to 12.04.  When it was at 13.04 stage, it was great so I installed it on SWMBOs machine.  Thank heaven I didn't replace 10.04 :P.  Just before 12.04 reached beta, it started having all kinds of glitches on our machines.  Today 12.04 is rock solid but at one point of its development cycle it certainly had 'issues'.  I wouldn't be surprised to see 13.04 go through similar 'growing pains'.  13.04 on a USB flash drive formatted to ext2 is working very well now though.

---

### Post by nomenkultur on 2013-02-04
I can only speak about my specific case and the laptop I'm using:
 
 
 13.04 is a night and day difference from 12.10
 
 mind you I couldn't even use 12.10 because it had a weird intel gfx bug that would force software rendering on this laptop.
 
 13.04 has been stable, snappy and functional... I am really impressed.
 
 There is little doubt that this release will definitely be the most successful and with software like lightworks, steam, etc being made available your user base could easily double in numbers.
 
 I still think the ambiance theme is broken tho... it should be all dark and not just the top
 
[http://gnome-look.org/content/show.php/Plane-Gtk3.6?content=156309](http://gnome-look.org/content/show.php/Plane-Gtk3.6?content=156309)

---

### Post by EgoGratis on 2013-02-04
Yes we all like when things like this happens:

[http://www.webupd8.org/2013/02/ubuntu-1304-raring-ringtail-changes.html](http://www.webupd8.org/2013/02/ubuntu-1304-raring-ringtail-changes.html)

---

### Post by nomenkultur on 2013-02-04
"some processes were changed to exit-on-idle and be restarted-on-demand rather than running all the time (signond, signon-ui);"
 
 
 this is quite important.
 
 I have no patience for that anymore but I found I could almost double my windows speed by disabling stupid services (windows has a lot of them)
 
 I wish there was a way to easily turn off stop like cups ( I don't have a printer) and Bluetooth in ubuntu

---

### Post by cariboo on 2013-02-04
> **nomenkultur said:**
> "some processes were changed to exit-on-idle and be restarted-on-demand rather than running all the time (signond, signon-ui);"
 
 
 this is quite important.
 
 I have no patience for that anymore but I found I could almost double my windows speed by disabling stupid services (windows has a lot of them)
 
 I wish there was a way to easily turn off stop like cups ( I don't have a printer) and Bluetooth in ubuntu

You can turn off quite a few service if you populate gnome-session-properties using the following commands:

```
cd /etc/xdg/autostart/
```

then:

```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

unfortunately cups isn't in the list, so you have to disable the upstart script.

---

### Post by jerrylamos on 2013-02-04
I'm mostly into applications like Firefox, Libre Writer, printing internet articles, Libre Calc, gparted, ... and do rather little with desktop eye candy, games, etc.  

I bounce back and forth between 12.04.2 (2D) and 3.8.0-4.  I can use either for what I do.  My opinion, 2D is a bit crisper.  I haven't run gtkperf or whatever other actual measurements there are out there.

I touch type mostly, and occasionally on 13.04 the automagic Dash gets in the way and won't disappear - probably a develoment unstable glitch?

Biggest pain is on wireless hidden encrypted connect.  12.04.x, no problem at all.  13.04.x, either disconnects on boot or claims the network is out of range.  It isn't.  Manual go thru connect to hidden network, it has all it needs, finally connects.  Yes there's a launchpad bug.  Not much interest from Ubuntu.

13.04 is rather larger.  I don't know what all the extra code is, since the smaller earlier Ubuntu's do everything I want to do.

I assume Unity is all about heading to tablets? with big vague finger prints instead of precise mouse pointers?  I run Android on a couple tablets, much faster with slower hardware than Ubuntu which has faster pc's for what I'm able to do on the tablets, however I'm a newbie on Android and don't know how to do a lot of things that are easy on Ubuntu...

Well, back to updating/installing 13.04 looking for bugs in what an ordinary user would do.

---

### Post by cariboo on 2013-02-05
@jerrylamos, haven't you been keeping up? Ubuntu everywhere is now the mantra, desktops, laptops, tablets, TVs and smartphones, one desktop to rule them all. :-D

---

### Post by zika on 2013-02-05
> **cariboo907 said:**
> You can turn off quite a few service if you populate gnome-session-properties using the following commands:

```
cd /etc/xdg/autostart/
```then:

```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```unfortunately cups isn't in the list, so you have to disable the upstart script.
For cups (and all in /etc/init):
```
echo manual | sudo tee -a /etc/init/cups.override
```

---

### Post by nomenkultur on 2013-02-05
EDIT:

 unfortunately the sysv-rc- thing and boot up manager no longer work as they should.

 you can shut down processes by hand by editing the files in etc/init

 I was able to disable cups and bluetooth.

  Here's what consumes more memory and you don't really 'need' it:

 unity lens video

 unity lens photo 

 unity scope video remote (no idea what it is)

 and then indicators like telepathy and printers (I don't know how to shut them down)


 hmmmm ... by shutting down useless processes like this you will easily save 100-150 mb in ram

 removed the unity lenses and telepathy indicators

 ubuntu is now only using 400mb of ram

---

