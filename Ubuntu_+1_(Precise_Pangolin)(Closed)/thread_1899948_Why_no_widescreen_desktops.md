---
title: "Why no widescreen desktops?"
date: 2011-12-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by teh603 on 2011-12-24
Anyone else notice that there aren't any 1366x768 desktop wallpapers in any flavor of Ubuntu, or really anywhere else?

It'd be really wonderful if Precise were to include one or two that didn't look horribly stretched when viewed at the same proportions as a lot of 15" displays. The ones that're larger or smaller don't even look right when scaled; they either chop off the top and bottom, or have ugly black bars on the right and left sides.

---

### Post by xyzzyman on 2011-12-25
Can you post a screen shot of your desktop? All the wallpapers are widescreen ratio so they all fit on 1366x768 just fine without any aspect problems. When you click on the wallpapers it shows you their resolution.

---

### Post by teh603 on 2011-12-25
Haha nice. I can't upload it because the max size of uploaded images is 1024x768.

The problem is, most "widescreen" images are out of proportion when viewed on 1366x768. The scaling system actually distorts them. This is true even with downloaded wallpapers; I usually end up getting one or two sizes larger and then cropping and scaling them in GIMP.

The fact that I'm running Kubuntu might have a little to do with it, but I doubt it.

---

### Post by kansasnoob on 2011-12-25
What graphics chip do you have?

---

### Post by teh603 on 2011-12-25
On this computer, something by nVidia. On the laptop, something by Intel. It doesn't matter, the "widescreen" desktops always come out horribly out of proportion.

---

### Post by ronacc on 2011-12-25
unless you can post some example of what you are calling "out of proportion " we are having difficulty grasping what you mean . I can assure you that all of the ubuntu wallpapers display with no distortion on my 1920x1080 widescreen monitor , on the ones that are larger that the screen I may loose a bit off the egdes but they are not distorted either horizontally or vertically and I have no difficulty adjusting random downloaded ones with gimp as long as the aspect ratio is close to right .

---

### Post by effenberg0x0 on 2011-12-25
I'm looking to a machine that has Ubuntu (unity), Ubuntu 2d, XUbuntu, Lubuntu installed and available via Lightdm, with two monitors plugged in: One 23" (1920x1080) and one 19" (1360x768). All sessions look perfect. 

Not to mention that the machine aside from that is connected to three TVs (32", 40" and 42" LCD/LED from Samsung/AOC). Not a single one of them has it's image distorted. The VGAs are Nvidia (2x 9500GT, 1x GT220, 1x GTS450). 

All these widescreen displays were properly auto-detected and had it's resolutions/refresh rates set using nvidia-settings from NVidia-proprietary 290.10. I have never had to do anything to set them up correctly. 

I also have 2 laptops (mine, wife's) here: 13.1" and 14", running PP, no distortion at all (Intel GPUs)

---

### Post by xyzzyman on 2011-12-26
Here is my 1366x768 with an ubuntu default wallpaper. And even though this says 1024x768 for screenshots it lets you upload 1366x768 just fine so not sure what error the forum was giving you.

---

### Post by jfernyhough on 2011-12-26
Can you just change the wallpaper (desktop background) settings from Fill to Zoom?

---

### Post by Paddy Landau on 2011-12-26
Here we are.

[http://www.widescreen-wallpaper.eu/1366x768-wallpapers-r.html](http://www.widescreen-wallpaper.eu/1366x768-wallpapers-r.html)
[http://www.ubuntuwallpapers.com/1366x768_hd-wallpapers-r.html](http://www.ubuntuwallpapers.com/1366x768_hd-wallpapers-r.html)

A [little Google]("http://lmgtfy.com/?q=widescreen+wallpapers+ubuntu") helps ;)

---

### Post by teh603 on 2011-12-26
Here we go.

Note that I selected "scaled, keep proportions." That's where the black bars on the side of the screen come from. If I don't choose that option, any human figures in the picture come out looking awful and stretched.

Just a note, this display is 1360; six pixels narrower than my laptop. Both the big Dell and the one that's supposed to have been repaired claim to be 1366. Either way, I still have more or less the same problem with black bars on the edges of the screen when I'm trying to view the pics at correct proportions.

I'm not trying to start a fight here, just get some wallpapers that don't look like pants when I view them in the correct proportions.

---

### Post by Paddy Landau on 2011-12-26
> **teh603 said:**
> "scaled, keep proportions."
That means to scale the picture to the maximum size that will fit in your screen. That is the correct behaviour.

You can choose to to fill the screen, which means some of the background will disappear off the screen.

Try the [post=11565788]links that I gave you[/post] to get wallpapers exactly the right size for your screen. There are plenty on the Internet if you look around.

---

### Post by Elfy on 2011-12-26
Offtopic posts moved to a thread in the cafe.

---

### Post by teh603 on 2011-12-26
> **Paddy Landau said:**
> That means to scale the picture to the maximum size that will fit in your screen. That is the correct behaviour.

You can choose to to fill the screen, which means some of the background will disappear off the screen.Actually, the default behavior in Kubuntu seems to be scaling the bloody thing disproportionately. Scaled proportionally may be the correct behavior, but correct and default are rarely the same thing.

> Try the [post=11565788]links that I gave you[/post] to get wallpapers exactly the right size for your screen. There are plenty on the Internet if you look around.I'll check on it. I'll be honest, I ditched the thread when I saw the fight starting and haven't read every post.

---

### Post by Elfy on 2011-12-26
> **teh603 said:**
> I'll be honest, I ditched the thread when I saw the fight starting and haven't read every post.

Report it next time - I just happened upon it and moved them off elsewhere.

---

### Post by ronacc on 2011-12-26
> **teh603 said:**
> Actually, the default behavior in Kubuntu seems to be scaling the bloody thing disproportionately. Scaled proportionally may be the correct behavior, but correct and default are rarely the same thing.

I'll check on it. I'll be honest, I ditched the thread when I saw the fight starting and haven't read every post.

can you post the original file ( not a screenshot ) that you are trying to use or at least where you found it? also originally you didn't specify Kubuntu I'll do an install of that and take a look there but it will take me awhile since I haven't got one running now just Ubuntu and Lubuntu .

---

### Post by xyzzyman on 2011-12-26
From the screenshot this looks like more of a kubuntu decision to do 4:3 and just let them stretch on widescreens. I'm suprised as their website makes it look like they are shipping widescreen ones to begin with. Anyays, Ubuntu actually is including wallpapers that will fit your screen quite nicely. In 2 minutes I'll be able to load kubuntu up in virtualbox so I can see just how off they are. If so we can see about finding out who maintains their wallpaper package as that is something that would be nice to tighten up before the LTS.

UPDATE: You're partially right. Other than 2 of them, all of their wallpapers are 4:3 1280x1024's. At least in the LiveCD of kubuntu it defaults to scale instead of scale-cropped. Ubuntu's already got widescreen wallpapers and there was a competition to submit wallpapers for 11.10 so I'm thinking that 12.04 may have them also. What kubuntu probably should do is default to scale-cropped so aspect ratio's stay proper, and then maybe include some more widescreen aspect wallpapers like Ubuntu does. The 4:3's on just regular scale mode will stretch them out really wide. I'm installing it to see what if it defaults differently when permanently installed.

UPDATE 2: Defaults to scale instead of scale-cropped so alot of the wallpapers do look bad in widescreen.

---

### Post by ronacc on 2011-12-26
yes thats what it looks like to me also , if that is it we should file a bug on it .

---

### Post by teh603 on 2011-12-26
Might want to check upstream, too. Its possible these desktops were coming in bundled with KDE and nobody was checking proportions.

I'm willing and able to provide some FOSS desktops for 1366 or 1360, if there's any interest.

---

### Post by xyzzyman on 2011-12-26
The wallpapers with Ubuntu are all large but at varying widescreen ratios, so when they are scaled down there is a tad bit of cropping being done whether it's 1366 or 1360. Gnome3/Unity both are hard locked in at Scale:Cropped so aspect ratio stays perfect. There are multiple kde wallpaper packages, and as I don't want to install kde on my main install I'll have to clone it later and install kde-standard to see if it's anything that needs to be taken care of on Ubuntu's end.

EDIT: Doing a 'snapshot' in virtualbox of my precise machine and doing it from there. Let you know.

---

### Post by ronacc on 2011-12-26
I d/l'd the kde wallpapers direct from KDE , I did find the one you have in your screenshot , from kde it is available in 4 resolutions . 1280x1024 , 1600x1200 , 1920x1080 and 1920x1200 . what is the native res of the one you have on your desktop , the 1920x1080 should scale to 1360(6)x768 with no distortion .

---

### Post by seeker5528 on 2011-12-26
> **teh603 said:**
> Note that I selected "scaled, keep proportions." That's where the black bars on the side of the screen come from. If I don't choose that option, any human figures in the picture come out looking awful and stretched.

Looking at '/usr/share/backgrounds', some of the wallpapers are widescreen some are not, of course being wide screen doesn't necessarily mean they will fit your screen either depending on which aspect ration your selected screen resolution provides versus the aspect ration of the wallpaper, but the difference between 16:9 and 1.6:1 is not so great that you would usually notice *that* much if you choose the stretch option instead of the scale option, of course you could always choose to co-ordinate the solid background color with your wallpaper if you choose to scale and prefer something other than black at the left and right or top and bottom edges.

I wouldn't expect a lot of the wallpapers to be updated with wide screen versions, I would expect more of the newer ones to be wide screen or have wide and non-wide versions. 

Being that there *are* wide screen wallpapers asking 'Why no wide screen desktops?' seems a bit excessive.

Later, Seeker

---

### Post by xyzzyman on 2011-12-26
> **seeker5528 said:**
> Looking at '/usr/share/backgrounds', some of the wallpapers are widescreen some are not, of course being wide screen doesn't necessarily mean they will fit your screen either depending on which aspect ration your selected screen resolution provides versus the aspect ration of the wallpaper, but the difference between 16:9 and 1.6:1 is not so great that you would usually notice *that* much if you choose the stretch option instead of the scale option, of course you could always choose to co-ordinate the solid background color with your wallpaper if you choose to scale and prefer something other than black at the left and right or top and bottom edges.

I wouldn't expect a lot of the wallpapers to be updated with wide screen versions, I would expect more of the newer ones to be wide screen or have wide and non-wide versions. 

Being that there *are* wide screen wallpapers asking 'Why no wide screen desktops?' seems a bit excessive.

Later, Seeker

That's why I'm checking kubuntu on a fresh install. To see what a new user gets as far as wallpapers and which option is chosen as default for scaling as kde gives you a number of 'scale' options. We all just go and fix things to our liking upon install, so we don't necessarily notice.

---

### Post by teh603 on 2011-12-26
> **seeker5528 said:**
> Being that there *are* wide screen wallpapers asking 'Why no wide screen desktops?' seems a bit excessive.
Maybe the ugly wide black bands are really frustrating to get rid of? Its one thing to see three black pixels on either side, but when you have really wide bands?

---

### Post by seeker5528 on 2011-12-26
> **xyzzyman said:**
> The wallpapers with Ubuntu are all large but at varying widescreen ratios, so when they are scaled down there is a tad bit of cropping being done whether it's 1366 or 1360. Gnome3/Unity both are hard locked in at Scale:Cropped so aspect ratio stays perfect.

None of this appears to be hardcoded on my system (unity).

When I choose the 'Scale' option it works as expected (no cropping), if it didn't it wouldn't be scale it would be Zoom, and Zoom is it's own option, that works as expected. 'Stretch' is also still an option, but it's called 'Fill' now, maybe if it was called 'Mangled to fit your screen' people would have a better sense of what to expect, or just call it stretch if you prefer a shorter name. ;)

Later, Seeker

---

### Post by seeker5528 on 2011-12-26
> **teh603 said:**
> Maybe the ugly wide black bands are really frustrating to get rid of? Its one thing to see three black pixels on either side, but when you have really wide bands?

When I click on the background color icon in the wallpaper selection window it brings up a color picker with an eye dropper which I can choose, then click an area in the wallpaper with a color I want to use, then the bands are not black any more.

I'm pretty sure it's just as easy to choose a background color in KDE.

Later, Seeker

---

### Post by effenberg0x0 on 2011-12-26
Just a note: I had posted this here before, I believe it's important to be considered, so here's a quote from wiki again: [http://en.wikipedia.org/wiki/Graphic_display_resolutions#WXGA_.281280.C3.97768.29](http://en.wikipedia.org/wiki/Graphic_display_resolutions#WXGA_.281280.C3.97768.29)

> 
**WXGA (1280×768)**

 **Wide eXtended Graphics Array** (Wide XGA or WXGA) is a set of **[non standard]("http://en.wikipedia.org/wiki/Display_standard")** resolutions derived from the [XGA]("http://en.wikipedia.org/wiki/XGA") [display standard]("http://en.wikipedia.org/wiki/Display_standard") by widening it to a [wide screen]("http://en.wikipedia.org/wiki/Wide_screen") [aspect ratio]("http://en.wikipedia.org/wiki/Aspect_ratio"). WXGA is commonly used for low-end [LCD TVs]("http://en.wikipedia.org/wiki/LCD_TV") and LCD [computer monitors]("http://en.wikipedia.org/wiki/Computer_monitor") for widescreen presentation.
 **When referring to televisions and other monitors intended for  consumer entertainment use, WXGA is generally understood to refer to a  resolution of ****1366(1365.333)****×768, with an aspect ratio of 16:9.** In 2006 this was the most popular resolution for [liquid crystal display televisions]("http://en.wikipedia.org/wiki/Liquid_crystal_display_television") while XGA was for [Plasma]("http://en.wikipedia.org/wiki/Plasma_display") TVs [flat panel displays]("http://en.wikipedia.org/wiki/Flat_panel_display").[[11]]("http://en.wikipedia.org/wiki/Wide_XGA#cite_note-10")
 **When referring to laptop displays or monitors intended primarily as  computer displays, WXGA is most commonly used to refer to a resolution  of ****1280×800 pixels with an aspect ratio of [16:10]("http://en.wikipedia.org/wiki/16:10").[[12]]("http://en.wikipedia.org/wiki/Wide_XGA#cite_note-11")  **This resolution is particularly popular for most laptops with a 14" or  15" screen. The exact resolution this refers to is somewhat variable,  however, as the 1280x*nnn* resolutions were among the first  widescreen resolutions commonly used, and term entered use (especially  for laptop displays) before the broad standardization 16:10 for  widescreen computer displays.
 Overall, several resolutions have been labeled as WXGA. These are the  most common resolutions given the label (in ascending order by total  number of pixels):
 
[LIST]
[*]1280×720[[13]]("http://en.wikipedia.org/wiki/Wide_XGA#cite_note-12")
[*]1280×768[[14]]("http://en.wikipedia.org/wiki/Wide_XGA#cite_note-13")
[*]1280×800[[15]]("http://en.wikipedia.org/wiki/Wide_XGA#cite_note-14")[[16]]("http://en.wikipedia.org/wiki/Wide_XGA#cite_note-15")
[*]1360×768
[*]1366×768[[17]]("http://en.wikipedia.org/wiki/Wide_XGA#cite_note-16")
[/LIST]
 1280×720 provides perfectly square pixels at an aspect ratio of 16:9,  while the additional pixels in 1280×768 and 1280×800 must be ignored to  give the 16:9 ratio without vertical stretching of the image. **1360×768  and 1366×768 come very close to 16:9, displaying exactly square pixels  if 1360×765 pixels of the display are used.**
 Recent widespread availability of 1280×800 pixel resolution LCDs for laptop monitors can be considered an [OS]("http://en.wikipedia.org/wiki/Operating_system") driven evolution from the formerly popular [1024×768]("http://en.wikipedia.org/wiki/XGA") screen size. In [Microsoft Windows]("http://en.wikipedia.org/wiki/Microsoft_Windows") [operating system]("http://en.wikipedia.org/wiki/Operating_system") specifically, the [task bar]("http://en.wikipedia.org/wiki/Task_bar") when fit to the bottom of the screen occupies about 30 pixels, allowing a program [window]("http://en.wikipedia.org/wiki/Window_%28computing%29") sized 1024×768 pixels to fit on screen without obstruction(800-768=32). Operating the [Windows Sidebar]("http://en.wikipedia.org/wiki/Windows_Sidebar") in [Windows Vista]("http://en.wikipedia.org/wiki/Windows_Vista") can use the remaining width of 256 pixels (1280-1024).
 [720p]("http://en.wikipedia.org/wiki/720p") is a related [HDTV]("http://en.wikipedia.org/wiki/HDTV") video display resolution measuring 1280×720 pixels.
 1440×900 resolution displays have also been found labeled as WXGA; however, the correct label is actually [WSXGA or WXGA+]("http://en.wikipedia.org/wiki/Wide_XGA#WXGA.2B_.281440.C3.97900.29").
So, we must look at the proportion of the wallpapers (16:9, 16:10). Saying they are widescreen is not enough since this can mean different proportions.

---

### Post by seeker5528 on 2011-12-26
> **effenberg0x0 said:**
> So, we must look at the proportion of the wallpapers (16:9, 16:10). Saying they are widescreen is not enough since this can mean different proportions.

16:10 just seems wrong, like saying four eighths instead of half, I guess we do have a precedent set in music though, two four time, six eight time, twelve eight time... :P

Later, Seeker

---

### Post by xyzzyman on 2011-12-26
> **seeker5528 said:**
> None of this appears to be hardcoded on my system (unity).

When I choose the 'Scale' option it works as expected (no cropping), if it didn't it wouldn't be scale it would be Zoom, and Zoom is it's own option, that works as expected. 'Stretch' is also still an option, but it's called 'Fill' now, maybe if it was called 'Mangled to fit your screen' people would have a better sense of what to expect, or just call it stretch if you prefer a shorter name. ;)

Later, Seeker

I'm using Unity and I don't have any scale/crop/tile options when looking at the included wallpapers as you can see in the attached screen shot. That option only appears for user wallpapers. It just automatically scales and crops, which a little gets cropped on everything. The default wallpapers are designed for this though so they look good on everyone's computer. (EDIT: I just put a VM into 1024x768 and whatever scaling it uses looks pretty decent actually even though that's a 4:3 being converted from a wide format.)

And I think for this issue we can use widescreen to mean any 16:9 or 16:10, whether 1360/1366, 1920x1080, 1600x900 or the lot. Alot of the included wallpapers w/Ubuntu don't fit at any of those ratio's exactly so most people are going to get some croppage. 

I had to shut down for a bit and do real world stuff so a little behind on seeing what a new user sees with kde on ubuntu or a new kubuntu install.

---

### Post by ronacc on 2011-12-26
here is a screenshot of my kde desktop on my 1920x1080 monitor , exactly as it looked on first boot as kde selected it .I had to downsize the screenshot to get it to upload since the original was 1.3 mb , I sized it to 1366x768 using gwenview , try it and see if it fits your desktop  , it may fix your problem but raises the question of why kde is geeting it wrong on your desktop .

hmm it changed the png to a smaller jpg , if it dont look good I'll upload the original to pastebin .

---

### Post by xyzzyman on 2011-12-26
So on kubuntu 11.10 there is just the one 1920x1200 (That blue one) wallpaper. You have to click to download the rest of the default wallpapers, and the rest are 1280x1024 (4:3) with a sole 1024x768 (4:3). Default is to just scale all the way out. My ubuntu vm is installing KDE as we speak, but I'm thinking this is a KDE issue of just packaging one wider wall-paper and the rest are 4:3. Ubuntu takes care of this as you're going to have the wallpapers even if you go and install KDE on top of everything, so this really falls down to if kubuntu is willing to include the ubuntu default wallpapers in their install or come up with their own package for 12.04. Right? I'm double checking 12.04 but it looks like teh603 will have to find a friend over on the kubuntu team. :)

[https://code.launchpad.net/~kubuntu-packagers/kubuntu-packaging/kde-wallpapers](https://code.launchpad.net/~kubuntu-packagers/kubuntu-packaging/kde-wallpapers)

EDIT: 12.04 has the widescreen formats... [http://bazaar.launchpad.net/~kubuntu-packagers/kubuntu-packaging/kde-wallpapers/view/head:/debian/kde-wallpapers.install](http://bazaar.launchpad.net/~kubuntu-packagers/kubuntu-packaging/kde-wallpapers/view/head:/debian/kde-wallpapers.install)

teh603 when is the last time you updated your 12.04?

---

### Post by ronacc on 2011-12-26
I just checked my fresh kubuntu install , you are right the only one in the wallpaper directory is the 1920x1200 one . But I think that is kubuntu's doing not KDE's . the wallpaper directory shipped by KDE has dozens of wallpapers each in several resolutions . see here [http://download.kde.org/stable/4.7.4/src/kde-wallpapers-4.7.4.tar.bz2](http://download.kde.org/stable/4.7.4/src/kde-wallpapers-4.7.4.tar.bz2) . so I think it needs to be bugged in kubuntu if anywhere , they probably did it that way to save space , kind of a useless gesture since the .iso is already past cd size .

---

### Post by teh603 on 2011-12-26
> **xyzzyman said:**
> teh603 when is the last time you updated your 12.04?Good question. Time to hit the download page again, methinks?

---

### Post by ronacc on 2011-12-26
be careful about the update , when I tried to update the fresh install from todays daily the package manager was broken .

---

### Post by xyzzyman on 2011-12-26
This issue is already taken care of by kubuntu. I just installed a kubuntu daily and when you click 'more wallpapers' it installed kde-wallpapers and there were a number of 1920x1080p.

EDIT: It was updated on Dec 23rd with all the wide formats: [http://bazaar.launchpad.net/~kubuntu-packagers/kubuntu-packaging/kde-wallpapers/revision/19](http://bazaar.launchpad.net/~kubuntu-packagers/kubuntu-packaging/kde-wallpapers/revision/19) Take a look at the .install file.

Not a bad idea actually to only install one single wallpaper that looks good stretched at 4:3 or 16:9/10. Then have the 'Install default wallpapers' button right below it.

EDIT #2: It may have been taken care of earlier from the looks of it. But either way they took care of it. Mark as solved!

---

### Post by seeker5528 on 2011-12-28
> **xyzzyman said:**
> I'm using Unity and I don't have any scale/crop/tile options when looking at the included wallpapers as you can see in the attached screen shot. That option only appears for user wallpapers.

It didn't occur to me that some brain damage may have occurred that would result in options that you expect to have, and do have for your pictures/wallpapers stored in various locations, to be missing when you are using the view the shows you the system wallpapers. :(

Later, Seeker

---

### Post by xyzzyman on 2011-12-28
> **seeker5528 said:**
> It didn't occur to me that some brain damage may have occurred that would result in options that you expect to have, and do have for your pictures/wallpapers stored in various locations, to be missing when you are using the view the shows you the system wallpapers. :(

Later, Seeker

I had to read that 2-3x as I thought you were mocking me and not Unity... lol I would almost submit as a bug but I think it's done on purpose so the included wallpapers always look good. If you want to use your own then it gives you the options to make it look as bad as you want. :)

---

### Post by teh603 on 2011-12-28
Side note- is there any way we can submit some widescreen ones upstream for the Debian Propaganda package? It used to have some very nice ones a few years ago, but the last few months they've just been downright bleakh.

---

### Post by jerrylamos on 2011-12-28
No problem!  One of the first things I do when installing like Pangolin today (again!) is copy a jpg of my wife in a swimsuit on a beach, in this case just finishing a triathlon swim.

Fills up the wide 1440x900 screen nicely.

For my money, "commercial wallpaper" is of no use, save the space on the overcrowded CD.

Jerry

---

### Post by ronacc on 2011-12-28
As Jerry  says there is no need to worry about what backgrounds Kubuntu , Ubuntu or any other distro provides . There are literally millions of images on the net or if none of them suit you relief is only a click ( of your digital camera ) away .

---

### Post by xyzzyman on 2011-12-28
> **ronacc said:**
> As Jerry  says there is no need to worry about what backgrounds Kubuntu , Ubuntu or any other distro provides . There are literally millions of images on the net or if none of them suit you relief is only a click ( of your digital camera ) away .

With all the focus on OOBE for new users it is important. A lot of "mom & dad" users stay with the included wallpapers. I've found that the Windows 7 'theme packs' that rotate a series of themed wallpapers are quite popular. This is Ubuntu not Arch. I think at least for the mothership Ubuntu they are on top of wallpapers after the great job with the wallpaper pack for 11.10, especially with the feature (The name escaped my mind at the moment) that auto adjusts your colors of dash and top panel based on the wallpaper's predominant color.

Earlier I actually figured out how Ubuntu handles the wallpaper pack that's included differently than showing the list of your own pictures. It's in a settings file that sets the 'zoom' automatically for each image individually, and you can set up xml files for actual theme packs with auto rotation just like Windows 7. I'm working on a script right now to let someone use any of the themes on [http://windows.microsoft.com/en-US/windows/downloads/personalize/themes](http://windows.microsoft.com/en-US/windows/downloads/personalize/themes). You can't distribute them so I'm not sure if I could write a program that allows the user to select from a menu, and it downloads the theme for them of if that's considered distributing.

---

### Post by seeker5528 on 2011-12-29
> **xyzzyman said:**
> I had to read that 2-3x as I thought you were mocking me and not Unity... lol I would almost submit as a bug but I think it's done on purpose so the included wallpapers always look good. If you want to use your own then it gives you the options to make it look as bad as you want. :)

I was mocking Gnome actually, since Unity uses the same gnome-control-panel appearance applet that you would have using Gnome-Shell or the Gnome fallback environment.

If all the default wallpapers look good scaled and cropped, it's not such a big deal, but it still seems odd that you don't get a choice on how the wallpapers are displayed when using the wallpapers installed in the system wallpaper directory.

What happens if you have some tiles installed there, or doesn't anybody use tiles anymore? Or is there a possibility to use a .desktop file to clue in the wallpaper managers? 

EDIT:
> **xyzzyman said:**
> Earlier I actually figured out how Ubuntu handles the wallpaper pack that's included differently than showing the list of your own pictures. It's in a settings file that sets the 'zoom' automatically for each image individually, and you can set up xml files for actual theme packs with auto rotation just like Windows 7.

Guess that partially answers that question. ;)

Later, Seeker

---

