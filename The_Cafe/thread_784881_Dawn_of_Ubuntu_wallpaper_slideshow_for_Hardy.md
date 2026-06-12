---
title: "Dawn of Ubuntu wallpaper slideshow for Hardy"
date: 2008-05-06
forum: The Cafe
---

### Post by Mr. Picklesworth on 2008-05-06
A neat feature that was quietly added to GNOME 2.22 is time-lapsed backgrounds; essentially a nice slideshow for your background image. Works best with very long transitions and very few keyframes.

This immediately had me thinking about the Dawn of Ubuntu wallpaper, and its two variants Night of Ubuntu and Ubuntu Spring. I popped them together into a little slideshow, and am quite pleased with the results :)

[http://dylanmccall.googlepages.com/DayOfUbuntuSlideshow.tar.gz](http://dylanmccall.googlepages.com/DayOfUbuntuSlideshow.tar.gz)

This slideshow ("Day of Ubuntu") gradually changes over time with a fading transition, continually providing a unique view that perfectly reflects the time of day!

Unfortunately, the images cannot use relative paths at the moment, so you have to place them as directed. Copy day_of_ubuntu to /usr/share/backgrounds (sudo cp day_of_ubuntu /user/share/backgrounds/day_of_ubuntu), then add day_of_ubuntu.xml as a wallpaper.
Read Readme for more information.

(Also unfortunately, it seems that I must set an arbitrary day, month and year, which means that the slideshow gets messed up over time).

Again, please note that this is for Ubuntu Hardy; it will not work in a previous release, though should work with any recent GNOME based distro. Check your GNOME version in System -> About GNOME.

I like it, so I hope you do too! :)


Update:
Added midnight scene, entering after 9PM, in full force at 2AM. Sorry, the times here probably make no sense on other lines of latitude...

---

### Post by Kingsley on 2008-05-06
Hasn't there been time-lapsed backgrounds since Gnome 2.20? The Infinity wallpaper I had in Fedora 8 would slightly change it's coloring throughout the day. 

Or maybe it was some fancy script that had nothing to do with Gnome 2.20.

---

### Post by Mr. Picklesworth on 2008-05-06
The patch was originally developed in Fedora, and they sent it upstream for GNOME 2.22.

---

### Post by the yawner on 2008-05-06
Uhm... So is this how they made the Fedora 8 wallpaper? Am gonna try it out. :D

---

### Post by FuturePilot on 2008-05-06
w00t! I heard that this was in Fedora and I was wondering if we would get it too. But I couldn't find any info on this, until now. Thanks! I'm going to try this out. :guitar:

---

### Post by pastalavista on 2008-05-06
Those are some really nice pictures for wallpapers. I was wondering why you didn't include a night image?

---

### Post by Mr. Picklesworth on 2008-05-06
Eh? There is a night image! Granted, I called the file "dusk" to fit with the other one being called "dawn", but it is definitely a somewhat dark nightish scene.
The only one I don't have is a sunset one, but this seems to do fine without. (Unless you have a sunset picture)...

---

### Post by pastalavista on 2008-05-06
nope... the tar.gz I dowwnloaded had dusk (which is sunset--kinda nightish) dawn and noon. midnight is missing

---

### Post by Mr. Picklesworth on 2008-05-06
I suppose a version of Ubuntu Night (Dusk), with saturation turned down could do it.

Edit:
Done!

New download, as before, at [http://dylanmccall.googlepages.com/DayOfUbuntuSlideshow.tar.gz](http://dylanmccall.googlepages.com/DayOfUbuntuSlideshow.tar.gz)

Originally had it with Ubuntu Night, then I switched over to a darker Ubuntu Spring image; the former looked too lively for the dead of night, what with falling Ubuntu logos and all...

Thanks for the suggestion!

---

### Post by Nem1976 on 2008-05-07
very cool I really like the images and the fact that they rotate.

Thanks

---

### Post by quasimodo69 on 2008-05-07
> **pastalavista said:**
> Those are some really nice pictures for wallpapers. I was wondering why you didn't include a night image?
OK..just for giggles-take a pic with your lens cap on-develope it-or pull it out of memory and cal it  "night"...just kiddin' :-)

---

### Post by RSingh on 2008-06-02
I have taken the waves version from Fedora 9 and edited it to work on Ubuntu. The original XML file was not working so I edited it and removed all the unnecessary code for the extra resolutions. It is designed for widescreen resolution but I have left all of the other resolution images in there so you can edit the XML for your screen size.

Here is the pack anyway: [Link]("http://rapidshare.com/files/119599520/Waves.tar.html") (Rapid Share)

Another Link: [Link]("http://www.filecrunch.com/fileDownload.php?sub=3c9a0b430a363f69fc225b1a41e29a2b&fileId=153221") (File Crunch)

---

### Post by Mr. Picklesworth on 2008-06-02
Sounds interesting, RSingh. However, just so you know, your work there is almost inaccessible because RapidShare has developed the worst Captcha system ever. Really, try downloading it as a guest and you will see :O

Oh, and I have it now. Thanks!
Anyone have the Fedora 8 set?

---

### Post by FuturePilot on 2008-06-02
Good grief, that is one of the worst CAPTCHAs I've ever seen. Is there another way to get this?

---

### Post by groeswenphil on 2008-06-02
When I tried copying the folder I was told that this wasn't permitted.

Ami I missing something?

Phil

---

### Post by RSingh on 2008-06-02
Sorry for that, this should be easier.;)

Here is the link: [http://www.filecrunch.com/fileDownload.php?sub=3c9a0b430a363f69fc225b1a41e29a2b&fileId=153221]("http://www.filecrunch.com/fileDownload.php?sub=3c9a0b430a363f69fc225b1a41e29a2b&fileId=153221")

I have update my last post with this link also.

Cheers! :guitar:

---

### Post by elmer_42 on 2008-06-02
I'm using the waves. Look!
[[img]http://arch.kimag.es/thumbs/67914276.png[/img]](http://arch.kimag.es/share/67914276.png)

---

### Post by RSingh on 2008-06-02
> **Mr. Picklesworth said:**
> Sounds interesting, RSingh. However, just so you know, your work there is almost inaccessible because RapidShare has developed the worst Captcha system ever. Really, try downloading it as a guest and you will see :O

Oh, and I have it now. Thanks!
Anyone have the Fedora 8 set?

Its your lucky day,

**I found the set of _INFINITY_ images online and have rewritten Waves XML for it.**

Here is the pack: [http://www.filecrunch.com/fileDownload.php?sub=44f11fbacd2e5c2128e4f699331ac029&fileId=153230]("http://www.filecrunch.com/fileDownload.php?sub=44f11fbacd2e5c2128e4f699331ac029&fileId=153230")

:popcorn:

---

### Post by elmer_42 on 2008-06-02
One thing you might want to note, I'm not sure if you did it on accident or not. In waves.xml, waves-wide-1-noon transition to waves-wide-2-evening has a shorter transition time than all the rest, and waves-wide-2-evening has a shorter static time than the rest.
```
<transition type="overlay">
<duration>10800.0</duration>
<from>/usr/share/backgrounds/waves/waves-wide-1-noon.png</from>
<to>/usr/share/backgrounds/waves/waves-wide-2-evening.png</to>
</transition>

<static>
<duration>3600.0</duration>
<file>/usr/share/backgrounds/waves/waves-wide-2-evening.png</file>
</static>
```

---

### Post by RSingh on 2008-06-03
> **elmer_42 said:**
> One thing you might want to note, I'm not sure if you did it on accident or not. In waves.xml, waves-wide-1-noon transition to waves-wide-2-evening has a shorter transition time than all the rest, and waves-wide-2-evening has a shorter static time than the rest.
```
<transition type="overlay">
<duration>10800.0</duration>
<from>/usr/share/backgrounds/waves/waves-wide-1-noon.png</from>
<to>/usr/share/backgrounds/waves/waves-wide-2-evening.png</to>
</transition>

<static>
<duration>3600.0</duration>
<file>/usr/share/backgrounds/waves/waves-wide-2-evening.png</file>
</static>
```

Nicely pointed out, but i would like to say is that I did not edit any of those values. All of the values are default values from the fedora 9 waves theme. I just edited the image paths because the original one had more than one path to take multiple resolutions into consideration.


Anyway here is the original XML file from the Fedora 9 theme:

```
<background>
  <starttime>
    <year>2007</year>
    <month>04</month>
    <day>01</day>
    <hour>07</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
<!-- This animation will start at 7 AM. -->

<!-- We start with sunrise at 7 AM. It will remain up for 1 hour. -->
<static>
<duration>3600.0</duration>
<file>
	<!-- Eeepc size --> <!-- 5:3 -->
	<size width="800" height="480">/usr/share/backgrounds/waves/waves-eeepc-0-morn.png</size>
	<!-- Odd resolution but apparently popular --> <!-- 5:4 -->
	<size width="1280" height="1024">/usr/share/backgrounds/waves/waves-normalish-0-morn.png</size>
	<!-- Standard 4:3 -->
	<size width="1600" height="1200">/usr/share/backgrounds/waves/waves-normal-0-morn.png</size>
	<!-- Widescreen 16:10 -->
	<size width="1920" height="1200">/usr/share/backgrounds/waves/waves-wide-0-morn.png</size>
</file>
</static>

<!-- Sunrise starts to transition to day at 8 AM. The transition lasts for 5 hours, ending at 1 PM. -->
<transition type="overlay">
<duration>18000.0</duration>
<from>
	<size width="800" height="480">/usr/share/backgrounds/waves/waves-eeepc-0-morn.png</size>
	<size width="1280" height="1024">/usr/share/backgrounds/waves/waves-normalish-0-morn.png</size>
	<size width="1600" height="1200">/usr/share/backgrounds/waves/waves-normal-0-morn.png</size>
	<size width="1920" height="1200">/usr/share/backgrounds/waves/waves-wide-0-morn.png</size>
</from>
<to>
	<size width="800" height="480">/usr/share/backgrounds/waves/waves-eeepc-1-noon.png</size>
	<size width="1280" height="1024">/usr/share/backgrounds/waves/waves-normalish-1-noon.png</size>
	<size width="1600" height="1200">/usr/share/backgrounds/waves/waves-normal-1-noon.png</size>
	<size width="1920" height="1200">/usr/share/backgrounds/waves/waves-wide-1-noon.png</size>
</to>
</transition>

<!-- It's 1 PM, we're showing the day image in full force now, for 2 hours ending at 3 PM. -->
<static>
<duration>7200.0</duration>
<file>
	<size width="800" height="480">/usr/share/backgrounds/waves/waves-eeepc-1-noon.png</size>
	<size width="1280" height="1024">/usr/share/backgrounds/waves/waves-normalish-1-noon.png</size>
	<size width="1600" height="1200">/usr/share/backgrounds/waves/waves-normal-1-noon.png</size>
	<size width="1920" height="1200">/usr/share/backgrounds/waves/waves-wide-1-noon.png</size>
</file>
</static>

<!-- It's 3 PM, and we're starting to transition to sunset. Transition completes at 6 PM. -->
<transition type="overlay">
<duration>10800.0</duration>
<from>
	<size width="800" height="480">/usr/share/backgrounds/waves/waves-eeepc-1-noon.png</size>
	<size width="1280" height="1024">/usr/share/backgrounds/waves/waves-normalish-1-noon.png</size>
	<size width="1600" height="1200">/usr/share/backgrounds/waves/waves-normal-1-noon.png</size>
	<size width="1920" height="1200">/usr/share/backgrounds/waves/waves-wide-1-noon.png</size>
</from>
<to>
	<size width="800" height="480">/usr/share/backgrounds/waves/waves-eeepc-2-evening.png</size>
	<size width="1280" height="1024">/usr/share/backgrounds/waves/waves-normalish-2-evening.png</size>
	<size width="1600" height="1200">/usr/share/backgrounds/waves/waves-normal-2-evening.png</size>
	<size width="1920" height="1200">/usr/share/backgrounds/waves/waves-wide-2-evening.png</size>
</to>
</transition>

<!-- It's 6 PM, and it's sunset, for an hour. Ends at 7. -->
<static>
<duration>3600.0</duration>
<file>
	<size width="800" height="480">/usr/share/backgrounds/waves/waves-eeepc-2-evening.png</size>
	<size width="1280" height="1024">/usr/share/backgrounds/waves/waves-normalish-2-evening.png</size>
	<size width="1600" height="1200">/usr/share/backgrounds/waves/waves-normal-2-evening.png</size>
	<size width="1920" height="1200">/usr/share/backgrounds/waves/waves-wide-2-evening.png</size>
</file>
</static>

<!-- It's 7 PM and it's going to start to get darker. This will transition for 5 hours up until midnight. -->
<transition type="overlay">
<duration>18000.0</duration>
<from>
	<size width="800" height="480">/usr/share/backgrounds/waves/waves-eeepc-2-evening.png</size>
	<size width="1280" height="1024">/usr/share/backgrounds/waves/waves-normalish-2-evening.png</size>
	<size width="1600" height="1200">/usr/share/backgrounds/waves/waves-normal-2-evening.png</size>
	<size width="1920" height="1200">/usr/share/backgrounds/waves/waves-wide-2-evening.png</size>
</from>
<to>
	<size width="800" height="480">/usr/share/backgrounds/waves/waves-eeepc-3-night.png</size>
	<size width="1280" height="1024">/usr/share/backgrounds/waves/waves-normalish-3-night.png</size>
	<size width="1600" height="1200">/usr/share/backgrounds/waves/waves-normal-3-night.png</size>
	<size width="1920" height="1200">/usr/share/backgrounds/waves/waves-wide-3-night.png</size>
</to>
</transition>

<!-- It's midnight. It'll stay dark for 5 hours up until 5 AM. -->
<static>
<duration>18000.0</duration>
<file>
	<size width="800" height="480">/usr/share/backgrounds/waves/waves-eeepc-3-night.png</size>
	<size width="1280" height="1024">/usr/share/backgrounds/waves/waves-normalish-3-night.png</size>
	<size width="1600" height="1200">/usr/share/backgrounds/waves/waves-normal-3-night.png</size>
	<size width="1920" height="1200">/usr/share/backgrounds/waves/waves-wide-3-night.png</size>
</file>
</static>

<!-- It's 5 AM. We'll start transitioning to sunrise for 2 hours up until 7 AM. -->
<transition type="overlay">
<duration>7200.0</duration>
<from>
	<size width="800" height="480">/usr/share/backgrounds/waves/waves-eeepc-3-night.png</size>
	<size width="1280" height="1024">/usr/share/backgrounds/waves/waves-normalish-3-night.png</size>
	<size width="1600" height="1200">/usr/share/backgrounds/waves/waves-normal-3-night.png</size>
	<size width="1920" height="1200">/usr/share/backgrounds/waves/waves-wide-3-night.png</size>
</from>
<to>
	<size width="800" height="480">/usr/share/backgrounds/waves/waves-eeepc-0-morn.png</size>
	<size width="1280" height="1024">/usr/share/backgrounds/waves/waves-normalish-0-morn.png</size>
	<size width="1600" height="1200">/usr/share/backgrounds/waves/waves-normal-0-morn.png</size>
	<size width="1920" height="1200">/usr/share/backgrounds/waves/waves-wide-0-morn.png</size>
</to>
</transition>
</background>

```

---

### Post by Bou on 2008-06-03
So, given that gnome can use several images as wallpapers, how hard would it be to make the wallpaper manager let you choose SEVERAL images and how often you want to change them?

---

### Post by FuturePilot on 2008-06-03
> **Bou said:**
> So, given that gnome can use several images as wallpapers, how hard would it be to make the wallpaper manager let you choose SEVERAL images and how often you want to change them?

Found this, looks interesting.
> Support desktop wallpaper rotation. (The code to do this is largely there since there is already support for animated backgrounds which rotate over a given period of time)

[http://gsocblog.jsharpe.net/archives/8]("http://gsocblog.jsharpe.net/archives/8")

---

### Post by Bou on 2008-06-03
Wow, that's terrific.

I've come up with a simple modification to the wallpaper manager, to allow rotations:

[IMG]http://img401.imageshack.us/img401/4461/pantallazo1td9.png[/IMG]

How hard do you think this would be to implement right now?

---

### Post by Mr. Picklesworth on 2008-06-03
Bou:
Nice example! A quick issue with that modification, though, is that the behaviour of selecting / deselecting images -- particularly for an unmoving wallpaper -- is then different. For people that don't want slideshows, that would be a regression. Could be solved by a checkbox to toggle multiple wallpapers, which should be at the top to go with the flow of top-bottom reading (eek!). Two more issues: there will be a lot of images there if someone wants a big slideshow, and "rotate every" does not accommodate for the coolest part: gradual transitions. Perhaps an "add slideshow" button that pops up a quick creation tool and produces an XML file for the current system with only a single image in the wallpaper previews would be smoothest in the end...

---

### Post by groeswenphil on 2008-06-11
> **groeswenphil said:**
> When I tried copying the folder I was told that this wasn't permitted.

Ami I missing something?

Phil

I guess I've got to give some sort of command to permit the file to copy into usr/shared/backgrounds.

Anybody help me with the magic words?

Phil

---

### Post by FuturePilot on 2008-06-11
You could launch Nautilus as root and do it that way.
```
gksudo nautilus
```will launch a root instance of Nautilus which will give you the necessary permissions to move the folder to /usr/share/backgrounds. Just be careful as that is a root instance of Nautilus.

---

### Post by groeswenphil on 2008-06-11
That worked..........but I'm worried now about being careful.
How would I know if I haven't been careful?

Phil

---

### Post by FuturePilot on 2008-06-11
> **groeswenphil said:**
> That worked..........but I'm worried now about being careful.
How would I know if I haven't been careful?

Phil

As long as you didn't move or delete any other files and you closed the root instance of Nautilus after you were done, you should be fine.

---

### Post by groeswenphil on 2008-06-12
> **FuturePilot said:**
> As long as you didn't move or delete any other files and you closed the root instance of Nautilus after you were done, you should be fine.
Phhheeeww

Phil

---

### Post by bigbrovar on 2008-06-12
its freaking awesome

---

### Post by cor2y on 2008-06-20
Thanks for the examples folks.
Now that i understand how to construct my own custom xml file.
Now i have a transition slideshow using 130 wallpapers.

---

### Post by groeswenphil on 2008-08-09
I really love this wallpaper....BUT....just had a new computer and now, I can't get it to work.

Main problem is I can't copy the folder into the right directory.
I've never figured out how to make sure that TERMINAL is in the right folder. It's something involving CD isn't it?

---

### Post by jay019 on 2008-08-19
Nice work, havent had it on long enough to see a transition yet, but love the concept!

Is there any documentation regarding what can go into the XML file? Interested in seeing what options are available.

Jay

---

### Post by Mr. Picklesworth on 2008-08-19
> **groeswenphil said:**
> I really love this wallpaper....BUT....just had a new computer and now, I can't get it to work.

Main problem is I can't copy the folder into the right directory.
I've never figured out how to make sure that TERMINAL is in the right folder. It's something involving CD isn't it?

Yep, use cd to change your terminal's working directory. I usually type cd then drag a file to the terminal from my file browser because I'm a wimp ;)
pwd will tell you the  present working directory. ls lists the contents of the directory.
That should get you started!

Remember, sudo gives root privileges; you'll need to use it.
No need to actually be in the directory to copy the files. For example:
sudo cp -R /path/to/source /usr/share/backgrounds
Copies into backgrounds (since that folder already exists). Just drag & drop the file or copy & paste to avoid wiggling through the file hierarchy!


Thanks Jay!
Alas, I know of no documentation. Pretty sure it's just straight transitions right now.

---

### Post by groeswenphil on 2008-08-20
O.K. I've managed to copy the folder into the wallpaper folder. AND I've copied the .xml file into the same folder.

BUT
When I look in System>Preferences>Appearance>background. I don't see the xml file.
Where am I going wrong?
I had it working perfectly on my old computer, but this is defeating me.
I'm really sad now  :O(

Phil:(

---

### Post by Mr. Picklesworth on 2008-08-20
If for whatever reason you don't see the XML file in the Background preferences, go to add a new wallpaper there and add it again. Add the XML file in /usr/share/backgrounds, since otherwise Nautilus will get confused when the background image moves.

Oh, how badly we need relative paths for this...

---

### Post by groeswenphil on 2008-08-21
Hi,
When I try a simple copy and paste from a file window, I get an error message to say that I don't have permission to do this.
SO.....I try a copy in Terminal and it comes out like this.

sudo cp command_exp'/home/philip/Odds/day_of_ubuntu.xml' /usr/share/backgrounds/ 

and I get

cp: cannot stat `command_exp/home/philip/Odds/day_of_ubuntu.xml': No such file or directory


Plan C is ?

Phil

---

### Post by go7Ul1ai on 2008-10-30
Hey,

I'm loving it! It's awesome, would anyone be able to explain to me simply how the timings work and the dates etc, because I would like one that keeps in sync with English time day and night.

Thanks :)

Lee

---

### Post by go7Ul1ai on 2008-10-30
Mistake double-post. Please delete.

---

### Post by mnemonik on 2009-03-09
> **groeswenphil said:**
> Hi,
When I try a simple copy and paste from a file window, I get an error message to say that I don't have permission to do this.
SO.....I try a copy in Terminal and it comes out like this.

sudo cp command_exp'/home/philip/Odds/day_of_ubuntu.xml' /usr/share/backgrounds/ 

and I get

cp: cannot stat `command_exp/home/philip/Odds/day_of_ubuntu.xml': No such file or directory


Plan C is ?

Phil

try this:```
philip@philip-laptop$ sudo cp Odds/day_of_ubuntu.xml ../../usr/share/backgrounds/
```

make sure you're in the default directory when your terminal opens up. really though, you only need the images in usr/share/backgrounds/ the xml file can be anywhere, just drag it in to the _background_ tab in the window that pops up when you go to System > Preferences > Appearance

---

### Post by guywithcable on 2009-04-27
Great backgrounds. Works in Jaunty. :)

---

### Post by inckie on 2009-05-05
> **Mr. Picklesworth said:**
> The only one I don't have is a sunset one, but this seems to do fine without. (Unless you have a sunset picture)...

How about this attachment for a sunset?

This is the least I can do to thank you for such an awesome work! =D>

Cheers!

---

### Post by Mr. Picklesworth on 2009-05-05
Oh, beauty! Thanks, Inckie.

Gee, someone really needs to patch this system upstream so we can have smarter timing and whatnot. It's getting out of sync now, and if I could use real sunrise / sunset times that wouldn't happen.

And then I should make someone put this in Ubuntu's repository since it's tricky to install it by hand :)

---

### Post by sertse on 2009-05-05
How does the ever popular "All Day Long" animated wallpaper do it?

[http://www.gnome-look.org/content/show.php/All+Day+Long+(Animated+Wallpaper)?content=83443](http://www.gnome-look.org/content/show.php/All+Day+Long+(Animated+Wallpaper)?content=83443)

Or is it using the same system as here?

---

### Post by inckie on 2009-05-05
> **Mr. Picklesworth said:**
> Oh, beauty! Thanks, Inckie.

I’m really glad you like it. :grin:

> **Mr. Picklesworth said:**
> Gee, someone really needs to patch this system upstream so we can have smarter timing and whatnot. It's getting out of sync now, and if I could use real sunrise / sunset times that wouldn't happen.

What if we put the images in **[FONT="Courier New"]$HOME/.backgrounds/day_of_ubuntu/[/FONT]** and **[FONT="Courier New"]day_of_ubuntu.xml[/FONT]** in **[FONT="Courier New"]$HOME/.backgrounds/[/FONT]**? Then we could have **[FONT="Courier New"].profile[/FONT]** update the xml with the current date upon user login.

Just an idea. :)

> **Mr. Picklesworth said:**
> And then I should make someone put this in Ubuntu's repository since it's tricky to install it by hand :)

If I had the time…

Cheers!

---

### Post by cidolfas on 2009-06-06
I added the sunset wallpaper and tweaked the times a bit (actually, a lot) to match the sunset/sunrise and dusk/dawn times from [http://www.gaisma.com/en/location/richardson-texas.html](http://www.gaisma.com/en/location/richardson-texas.html) as best as I could figure, and then tested them and tweaked a bit more to make it more like a real day.  It doesn't account too much for summer/winter, but I tried to split the difference a bit.  Here's my modified xml file:

```
<background>
  <starttime>
    <year>2009</year>
    <month>06</month>
    <day>06</day>
    <hour>06</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
<!-- 6AM  !-->

<static>
<duration>3600.0</duration>
<file>/usr/share/backgrounds/day_of_ubuntu/dawn.jpg</file>
</static>
<!-- 7AM  !-->

<transition type="overlay">
<duration>18000.0</duration>
<from>/usr/share/backgrounds/day_of_ubuntu/dawn.jpg</from>
<to>/usr/share/backgrounds/day_of_ubuntu/noon.jpg</to>
</transition>
<!-- 12PM  !-->

<static>
<duration>18000.0</duration>
<file>/usr/share/backgrounds/day_of_ubuntu/noon.jpg</file>
</static>
<!-- 5PM  !-->

<transition type="overlay">
<duration>7200.0</duration>
<from>/usr/share/backgrounds/day_of_ubuntu/noon.jpg</from>
<to>/usr/share/backgrounds/day_of_ubuntu/sunset.jpg</to>
</transition>
<!-- 7PM  !-->

<static>
<duration>3600.0</duration>
<file>/usr/share/backgrounds/day_of_ubuntu/sunset.jpg</file>
</static>
<!-- 8PM  !-->

<transition type="overlay">
<duration>3600.0</duration>
<from>/usr/share/backgrounds/day_of_ubuntu/sunset.jpg</from>
<to>/usr/share/backgrounds/day_of_ubuntu/dusk.jpg</to>
</transition>
<!-- 9PM  !-->

<transition type="overlay">
<duration>14400.0</duration>
<from>/usr/share/backgrounds/day_of_ubuntu/dusk.jpg</from>
<to>/usr/share/backgrounds/day_of_ubuntu/midnight.jpg</to>
</transition>
<!-- 1AM  !-->

<static>
<duration>10800.0</duration>
<file>/usr/share/backgrounds/day_of_ubuntu/midnight.jpg</file>
</static>
<!-- 4AM  !-->

<transition type="overlay">
<duration>7200.0</duration>
<from>/usr/share/backgrounds/day_of_ubuntu/midnight.jpg</from>
<to>/usr/share/backgrounds/day_of_ubuntu/dawn.jpg</to>
</transition>
<!-- 6AM  !-->

</background>
```

---

### Post by c. elegans on 2009-06-10
This isn't working for me in Jaunty.  When I use the xml file as my background the right image shows up, but it doesn't change unless I manually cycle the background.  Am I missing something here?

I've got Compiz Fusion running, could that cause it?  My background changes fine with gbgchange, but I want this to update with time of day, not randomly.

---

### Post by pataphysician on 2009-07-05
i know this thread is a little old, but it helped me create a transitional background for the seasons pack from stuidiotwentyeight, so i thought i'd post it.

[http://www.studiotwentyeight.com/wallpapers.htm](http://www.studiotwentyeight.com/wallpapers.htm)

links are about 3/4 down the page.


```
<background>
<starttime>
<year>2009</year>
<month>05</month>
<day>13</day>
<hour>0</hour>
<minute>00</minute>
<second>00</second>
</starttime>

<!-- 12am -->
<transition type="overlay">
<duration>21600.0</duration>
<from>/usr/share/backgrounds/Winter_1600.jpg</from>
<to>/usr/share/backgrounds/Spring_1600.jpg</to>
</transition>

<!-- 6am -->
<transition type="overlay">
<duration>21600.0</duration>
<from>/usr/share/backgrounds/Spring_1600.jpg</from>
<to>/usr/share/backgrounds/Summer_1600.jpg</to>
</transition>

<!-- 12pm -->
<transition type="overlay">
<duration>21600.0</duration>
<from>/usr/share/backgrounds/Summer_1600.jpg</from>
<to>/usr/share/backgrounds/Autumn_1600.jpg</to>
</transition>

<!-- 6pm -->
<transition type="overlay">
<duration>21600.0</duration>
<from>/usr/share/backgrounds/Autumn_1600.jpg</from>
<to>/usr/share/backgrounds/Winter_1600.jpg</to>
</transition>

</background>
```

---

### Post by Mr. Picklesworth on 2009-10-01
[SIZE="4"]I finally made a Debian package :)[/SIZE]

[http://dylanmccall.googlepages.com/day-of-ubuntu-wallpaper_1_all.deb](http://dylanmccall.googlepages.com/day-of-ubuntu-wallpaper_1_all.deb)

Just double click and follow the steps to install. It will immediately appear in your choice of backgrounds via the Appearance Preferences. Super easy!

Will stick it on Launchpad one of these years, too.

---

### Post by Mobil1 on 2009-10-01
Hi guys!  I have gnome-desktop installed as well as Xfce for Xubuntu. I switched the session to Gnome and used Mr Picklesworth's deb file (thanks for that one!!) and it runs perfectly!   

Any ideas how to make it run in Xfce though? 

I've tried waves and ubuntu_day but the problem I think is more with recognition of the xml file?  Any input would be appreciated - thanks :)

---

### Post by Mobil1 on 2009-10-01
> **Mobil1 said:**
> Hi guys!  I have gnome-desktop installed as well as Xfce for Xubuntu. I switched the session to Gnome and used Mr Picklesworth's deb file (thanks for that one!!) and it runs perfectly!   

Any ideas how to make it run in Xfce though? 

I've tried waves and ubuntu_day but the problem I think is more with recognition of the xml file?  Any input would be appreciated - thanks :)

Cool! Found a partial solution thanks to: [http://forum.xfce.org/index.php?topic=4843.0](http://forum.xfce.org/index.php?topic=4843.0)

It only changes the background randomly but I got it to work via:

Create a new image list under Applications>Settings>Desktop
Choose create new list and (I created this in my home dir)
Add your images to this and close the GUI

Then using the script from the above website [http://forum.xfce.org/index.php?topic=4843.0](http://forum.xfce.org/index.php?topic=4843.0)

#!/bin/sh
MONITOR=${1:-0}
PROPERTY="/backdrop/screen0/monitor${MONITOR}/image-path"
IMAGE_PATH=`xfconf-query -c xfce4-desktop -p ${PROPERTY}`
xfconf-query -c xfce4-desktop -p ${PROPERTY} -s ""
xfconf-query -c xfce4-desktop -p ${PROPERTY} -s "${IMAGE_PATH}"

I saved this as bgchanger.sh in my home dir, made executable
then in terminal i run the command: "sh /home/mobil1/bgchanger.sh"

All that would be left is to set up a cron job to execute the script when you wish.

Not ideal but closer heheh!:P

[URL="http://forum.xfce.org/index.php?topic=4843.0"]
[/URL]

---

### Post by ahtmly2k on 2009-10-16
why can't i copy the "day_of_ubuntu" folder to "/usr/share/backgrounds".. why is this? could someone please explain this to me in detail? isn't there a "DayOfUbuntuSlideshow.deb"? it would be easier to install.. eheh.. sorry for being such an annoyance.. i'm new to this Ubuntu stuf.. enjoying it so far though..

- Cheers!
ahtmly2k :P

---

### Post by cariboo on 2009-10-16
Press ALt-F2 and type:

```
gksu nautilus
```

This will start the file manager in root mode, you can then copy the files anywhere you want. You will be asked to enter the password you created when you installed Ubuntu.

---

### Post by Mr. Picklesworth on 2009-10-16
> **ahtmly2k said:**
> isn't there a "DayOfUbuntuSlideshow.deb"? it would be easier to install.. eheh.. sorry for being such an annoyance.. i'm new to this Ubuntu stuf.. enjoying it so far though..

Look three posts above you.

---

### Post by ttilberg on 2009-10-23
A few people have asked about the xml specs for using an .xml as a background-- I would love to learn as well. Any tips? And is there an easier way to generate the required .xml file based on a folder of pics?

Or is it just easier to just install one of the other popular background changers, such as webilder, wallpaper-tray, or a script with cron, etc?

I would rather use the tools inherent to gnome/ubuntu, etc, but if the .xml file needs to be edited manually, booooo.

This would be such a sweet feature to make "better" in future releases of Ubuntu... Something along the lines of "Install Background Folder" or whatnot.

---

### Post by Isthan on 2009-10-26
I really appreciate the information thus far, very helpful!  It has given me the inspiration to try out some xml.

I'm having a bit of trouble getting the .xml to be a workable background.  I'm using Karmic 9.10 AMD build.  I've followed the examples of this thread and also the default "cosmos" slideshow that comes with Karmic.  I've made 7195 second + 5 second transition = 2hr periods.

Here is what i've come up with:

```
<background>
  <starttime>
    <year>2009</year>
    <month>05</month>
    <day>05</day>
    <hour>06</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
<!-- 
Day Scheme:
Day will start at 6 AM
HR:MM:SS
06:00:00
!-->

<!--WP1 !-->
<static>
	<duration>7195.0</duration>
	<file>/usr/share/backgrounds/my_custom_cycle/endlessblue.jpg</file>
</static>
<transition>
	<duration>5.0</duration>
	<from>/usr/share/backgrounds/my_custom_cycle/endlessblue.jpg</from>
	<to>/usr/share/backgrounds/cosmos/atoll.jpg</to>
</transition>
<!-- RNG: 6AM-8AM Ending at 8 AM !-->

<!--WP2 !-->
<static>
	<duration>7195.0</duration>
	<file>/usr/share/backgrounds/my_custom_cycle/atoll.jpg</file>
</static>
<transition>
	<duration>5.0</duration>
	<from>/usr/share/backgrounds/my_custom_cycle/atoll.jpg</from>
	<to>/usr/share/backgrounds/cosmos/borealis2k6.jpg</to>
</transition>
<!-- RNG: 8AM-12AM Ending at 12AM !-->

<!--WP3 !-->
<static>
	<duration>7195.0</duration>
	<file>/usr/share/backgrounds/my_custom_cycle/borealis2k6.jpg</file>
</static>
<transition>
	<duration>5.0</duration>
	<from>/usr/share/backgrounds/my_custom_cycle/borealis2k6.jpg</from>
	<to>/usr/share/backgrounds/cosmos/autumnwood.jpg</to>
</transition>
<!-- RNG: 12AM-2PM Ending at 2PM !-->

<!--WP4 !-->
<static>
	<duration>7195.0</duration>
	<file>/usr/share/backgrounds/my_custom_cycle/autumnwood.jpg</file>
</static>
<transition>
	<duration>5.0</duration>
	<from>/usr/share/backgrounds/my_custom_cycle/autumnwood.jpg</from>
	<to>/usr/share/backgrounds/cosmos/arctica.jpg</to>
</transition>
<!-- RNG: 2PM-4PM Ending at 4PM !-->

<!--WP5 !-->
<static>
	<duration>7195.0</duration>
	<file>/usr/share/backgrounds/my_custom_cycle/arctica.jpg</file>
</static>
<transition>
	<duration>5.0</duration>
	<from>/usr/share/backgrounds/my_custom_cycle/arctica.jpg</from>
	<to>/usr/share/backgrounds/cosmos/cancer.jpg</to>
</transition>
<!-- RNG: 4PM-6PM Ending at 6PM !-->

<!--WP6 !-->
<static>
	<duration>7195.0</duration>
	<file>/usr/share/backgrounds/my_custom_cycle/cancer.jpg</file>
</static>
<transition>
	<duration>5.0</duration>
	<from>/usr/share/backgrounds/my_custom_cycle/cancer.jpg</from>
	<to>/usr/share/backgrounds/cosmos/circularlogic.jpg</to>
</transition>
<!-- RNG: 6PM-8PM Ending at 8PM !-->

<!--WP7 !-->
<static>
	<duration>7195.0</duration>
	<file>/usr/share/backgrounds/my_custom_cycle/circularlogic.jpg</file>
</static>
<transition>
	<duration>5.0</duration>
	<from>/usr/share/backgrounds/my_custom_cycle/circularlogic.jpg</from>
	<to>/usr/share/backgrounds/cosmos/cilia.jpg</to>
</transition>
<!-- RNG: 8PM-10PM Ending at 10PM !-->

<!--WP8 !-->
<static>
	<duration>7195.0</duration>
	<file>/usr/share/backgrounds/my_custom_cycle/cilia.jpg</file>
</static>
<transition>
	<duration>5.0</duration>
	<from>/usr/share/backgrounds/my_custom_cycle/cilia.jpg</from>
	<to>/usr/share/backgrounds/cosmos/colony.jpg</to>
</transition>
<!-- RNG: 10PM-12PM Ending at 12PM !-->

<!--WP9 !-->
<static>
	<duration>7195.0</duration>
	<file>/usr/share/backgrounds/my_custom_cycle/colony.jpg</file>
</static>
<transition>
	<duration>5.0</duration>
	<from>/usr/share/backgrounds/my_custom_cycle/colony.jpg</from>
	<to>/usr/share/backgrounds/cosmos/cradle2k3.jpg</to>
</transition>
<!-- RNG: 12PM-2AM Ending at 2AM !-->

<!--WP10 !-->
<static>
	<duration>7195.0</duration>
	<file>/usr/share/backgrounds/my_custom_cycle/cradle2k3.jpg</file>
</static>
<transition>
	<duration>5.0</duration>
	<from>/usr/share/backgrounds/my_custom_cycle/cradle2k3.jpg</from>
	<to>/usr/share/backgrounds/cosmos/firmament.jpg</to>
</transition>
<!-- RNG: 2AM-4AM Ending at 4AM !-->

<!--WP11 !-->
<static>
	<duration>7195.0</duration>
	<file>/usr/share/backgrounds/my_custom_cycle/firmament.jpg</file>
</static>
<transition>
	<duration>5.0</duration>
	<from>/usr/share/backgrounds/my_custom_cycle/firmament.jpg</from>
	<to>/usr/share/backgrounds/cosmos/endlessblue.jpg</to>
</transition>
<!-- RNG: 4AM-6AM Ending at 6AM !-->

```

I've placed this .xml along with each .jpg file that I've referenced in my .xml file inside a folder my_custom_cycle.  I moved that folder into the /user/share/background directory.  When I try to change the desktop background, I click the add button and point at the .xml file.  After it is added, it just wants to make it a default "solid color" and certainly doesnt have the "stack" appearance that cosmos does.  Basically, its not working =(

Any advice would be greatly appreciated!

---

### Post by Isthan on 2009-10-26
Oh dumbness...My only problem was a closing </background> tag!

All is well =)

---

### Post by MasterNetra on 2009-10-27
I would rather see something like Dreamscene instead of just slideshows personally.

---

### Post by motang on 2009-11-05
Very cool, thanks!

---

### Post by lyncis on 2009-11-12
Maybe you find this interesting: [http://ubuntuforums.org/showthread.php?p=8303985#post8303985](http://ubuntuforums.org/showthread.php?p=8303985#post8303985)

The same, but synchronized with the your location real daylight time.

---

### Post by ttilberg on 2009-11-12
Very very cool. Wonderful photography throughout the rest of the blog as well.
Thanks for writing this script, except it doesn't seem to work on my box. I reported a bug in the google code page, as requested.

I really wish there were more involvement with the .xml wallpapers. They are soooooo cool.

[http://brainstorm.ubuntu.com/idea/22363/](http://brainstorm.ubuntu.com/idea/22363/)

---

### Post by pastalavista on 2010-03-16
What a nice surprise! I just found your wallpapers in the Ubuntu repositories. I'm feeling pride in the fact one of them was my idea ;) 

I still use these all the time! (I change my wallpapers and themes really often though)

---

### Post by misayre on 2010-12-06
Thanks for this piece of work. I like it a lot but I hate the inconsistency with the real sunrise and -set times. So I have thrown together a quick and dirty python script to calculate sunrise and -set times via pyephem, a package for astronomical calculations. 

So let's get it up and running. Download the archive [http://biophysics.hoppeban.de/day_of_ubuntu.tar.gz](http://biophysics.hoppeban.de/day_of_ubuntu.tar.gz) and extract it, preferably to 
```
/usr/share/background
```since it requires no further adjustments later on.

Now you need to get the pictures
Now you need to edit **day_of_ubuntu.cfg** and set longitude and latitude of your location. There are a bunch of sites out there to get values for you. 
The other values in **day_of_ubuntu.cfg** need no changing if you followed the earlier advise and extracted to /usr/share/background

Now that you have the files in place, we need to get your python prepped. I'm assuming you have a python2.x installation. We need mercurial to get the current repository of **ephem**.
So change to a directory of your choice for compiling stuff, e.g. /tmp and invoke
```
hg clone [http://bitbucket.org/brandon/pyephem](http://bitbucket.org/brandon/pyephem)
cd pyephem
python setup.py build
python setup.py install

```This will build and install **ephem** and we should be ready to go.

Change back to **/usr/share/backgrounds** and if you had day_of_ubuntu before do a backup of you day_of_ubuntu.xml and afterwards try
```
sudo ./day_of_ubuntu.py
```Unfortunately it's important to have root privileges to write the new XML file in this directory, but you can read the whole code to see, that there's no b*llsh*t in it.

Hopefully you got no messages which says all is fine. If you got something like 'lxml' not found, you will need to install it.

When everything is running as it should it might be sensible to add a cronjob for this script. My suggestion is to schedule it for 2 A.M. since this is my reference point for the calculations in the script.

Side note: It was mentioned earlier that it is not possible to use relative pathes for the pictures. I cannot remedy this directly but you can put this script in every directory you wish and it will search the pictures by default in the subdirecty day_of_ubuntu (changeable in the config file) This way you can put all the file in your home directory without to much trouble.

---

