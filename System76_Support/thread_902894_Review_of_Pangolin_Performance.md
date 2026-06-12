---
title: "Review of Pangolin Performance"
date: 2008-08-27
forum: System76 Support
---

### Post by Emblem Parade on 2008-08-27
So, I got my shiny new [Pangolin Performance]("http://system76.com/product_info.php?cPath=28&products_id=86") laptop from [system76]("http://system76.com/"), and I think it warrants a review, because it comes pre-installed with Ubuntu rather than, say, Windows Vista or Windows XP. Most reviews of free operating systems start with "Part 1: Installation," an utterly unfair comparison to reviews of computers which come ready-to-use with Windows or Mac OS.

(Fun fact: many free operating systems are easier to install than any version of Windows. Ubuntu is one of them. The installation CD is "live," meaning that actually boots you into the operating system itself, so you can make sure everything works before you install it.)

**HARDWARE**

The Pangolin hardware itself is beautiful and functional. It's exceptionally light and well-organized, even minimalistic. Glossy black cover, cream on the inside, with a 15" wide-screen, which is the sweet-spot between laptop portability vs. usability. 15" could be cramped, but I got the high-resolution glossy upgrade, which is easily the best screen I have seen on a laptop. The gloss adds some glare, but the display is crystal clear and very sharp. The touchpad could be better: the buttons are kinda hard to click. But, I use an external mouse: even the best touchpads make me go postal after five minutes. Above the screen is a built-in webcam.

On the left and right you'll find all the standard laptop connectors: three USB ports, audio (including digital out), Ethernet (gigabit speed), modem, VGA, ExpressCard. Some very nice extras are an eSATA port for connecting external hard drives (much, much faster than USB or FireWire), an HDMI port for high-quality external monitors, and a memory card reader, supporting all common types. My machine also came with a fingerprint reader on the touchpad, but this still has limited support in Ubuntu.

Inside, it's all the latest-and-greatest. The chipset is Intel's new "Centrino 2" platform. "Centrino" is Intel's brand-name for its laptop platform, which combines CPU, RAM, WiFi and external ports for minimal power consumption, while maintaining top performance. Centrino actually kept being upgraded over the years, and there's nothing too dramatic that warrants re-branding it "Centrino 2" this time. Still, this is the best right now. It also supports the newest range of Intel mobile CPUs. I got mine with the T9400, which has a whopping 6MB of L2 cache. That's some astounding processing power. Centrino 2 also supports fast 800MHz DDR2 memory, which is what system76 uses. Fast memory makes little difference in actual performance for home uses, but it's still a nice touch. Finally, my Pangolin came with the latest mobile video support from NVIDIA, the 9300M GS. Very good for 3D games. Note also that the Pangolin comes with the 64bit version of Ubuntu, which is better at using all this great tech. 64bit software can offer up to 30% better performance over 32bits.

The machine itself is brand-less. The box says "Made in China," but the documentation does not mention any manufacturer information. It could very well be a company that makes laptops for famous brands (Dell, HP, etc.). The bottom line is that this is a well-made computer. I should also mention that the price is very competitive, without even considering all those extra touches. Expect to pay $500 more for an equivalent Apple.

**THE UBUNTU EXPERIENCE**

Since I've been using Ubuntu for years, nothing here is new for me. For you newbies, you'll find a remarkably easy-to-use, fast, pretty and safe computing experience. The most dramatic change for those coming from Windows or Mac is how to add software to your machine. With Ubuntu, you simply click add/remove, and choose from an overwhelmingly huge repository of software. And that's it, if you can believe it. There are also additional repositories out there from some other companies, that can even further expand your repertoire. It sometimes takes a while for new versions of software to get into the repositories (there's a quality-assurance process they must pass), so there's also [GetDeb]("http://www.getdeb.net/"), where the latest-and-greatest can be found. For example, I was anxious to get the latest version of Pidgin (2.5), which was available there. A nice perk to this already-great repository system is that software updates all come together, and immediately, as soon as they are available on the repositories.

Need I mention that all of this is free? As in: it will cost you nothing. As for "free" as in "you have a license to modify the source code," the Ubuntu repositories actually do contain some software that's non-free. These are quite rare and marked quite clearly, so you have the option not to add such software if you want to maintain purity. However, note that system76 might install some non-free hardware drivers for you when you get the machine (notably, video drivers). If free-software purity really is important to you, Ubuntu might not be the best choice.

Still, even before adding software, your Ubuntu laptop comes out of the box with far more software than a Mac or an expensive Windows Vista Ultimate machine: a complete office suite (OpenOffice), a powerful PhotoShop-like graphic editor (GIMP), a Microsoft Outlook-like email/contact/calendar center (Evolution), an instant messenger that can connect you to all major networks (Pidgin), an iTunes-like media center (Rhythmbox), and lots of games and useful utilities.

One easily-fixable limitation, which might surprise you, is that out-of-the-box Ubuntu does not play MP3s and a lot of video formats, including DVDs! First, the reason: these formats, despite being ubiquitous, are actually not free. They are registered trademarks, which must be used with permission from the appropriate consortium or private company. Instead, Ubtuntu encourages you to use a series of truly-free formats wrapped as OGG files. In many cases, these formats are better than the proprietary formats, offering better compression, quality and performance. However, it's likely that a lot of the files you already have or find are not OGGs. Ubuntu will in most cases detect this and automatically install the appropriate codec. Additionally, I recommend adding the [Medibuntu]("http://www.medibuntu.org/") repository, which adds even more codecs, including full DVD support. To quote Medibuntu: "It is your legal responsibility to make sure that the software you are installing can be legally used in your country and for your intended purpose."

If you're worried about some special software you have that you think only works on Windows, then think again. First, there might be software in the repositories that is a decent substitute. Second, a lot of Windows software can install in Ubuntu, by adding a package called WINE from the repositories. The WINE site maintains a [database of applications]("http://appdb.winehq.org/") which are known to work well. WINE is not an emulator (actually, that's what the acronym stands for!), and works as fast if not faster than Windows. In fact, there is a long list of older Windows software that won't work on Windows Vista, but will work fine with WINE. Third, you can install Windows as a virtual machine running *inside* Ubuntu, by adding VirtualBox from the repositories. It works great for everything except 3D games. Note that you will need your Windows installation CD to do this. Fourth and finally, you can actually install Windows on your laptop while keeping Ubuntu on it. Whenever you turn on your laptop, it will ask you if you want to boot into Ubuntu or Windows.

That last step might be required if you want to run the latest-and-greatest computer games (though check first: some work fine with WINE). But, it's also required for Mac owners. Game makers target Windows.

For people who care about looks, I should say that Ubuntu provides a beautiful, clean, simple desktop experience. The default theme, called "Human," offers Earth-themed colors oriented around brownish-orange, and pristine controls. Ubuntu also comes with many other themes, oriented around blue, and there are thousands available online. The desktop is also fully 3D, giving you cool application-flipping like in Vista, and easy window selection like Exposé in Mac. It does even better by adding the famous "desktop cube," which makes it easy and fun to expand your desktop size. I personally like to run a Windows virtual machine on the other side of my cube. See a complete demo [here]("http://www.youtube.com/watch?v=E4Fbk52Mk1w").

**EXTERNAL HARDWARE**

As for working with external hardware, there's this myth that Linux-based operating systems only support a limited amount of hardware, due to the unavailability of drivers. Well, let me debunk this right now: Linux supports a much, much longer list of hardware than any version of Windows, and definitely much more than Mac. Not only that, there usually isn't any need to install drivers: with Linux, hardware usually works just by plugging it in. I've had this easy experience in the past with printers, professional audio adapters and webcams. I plugged them in, and Ubuntu immediately started using them.

The problem, of course, is that a long list doesn't help you if your particular hardware isn't on the list. Mac owners know to check that the hardware clearly says that it works on Mac. Unfortunately, because Linux-based operating systems are still fairly new to the consumer market, few hardware manufacturers note on the box whether or not they support Linux. So, you must add the question "Does it work with Linux?" to your research when you plan to buy new hardware. Also note that sometimes the answer might be "yes," but might require some special work to get it running, and that not all features are supported. The best answer, of course, is "yes, and out of the box, and fully." The only trouble I had this time around was getting my Pangolin connected to my external monitor. It did work "out of the box," but it used a very low resolution for the monitor. It took considerable fiddling to make it work. For what it's worth, Windows laptops are also notoriously bad at this task.

Of course, all the hardware inside the Pangolin worked immediately for me: the webcam, sound, video, all the ports. Actually, I couldn't get the internal microphone to work for me, but it seems that it's not even worth trying to fix it. People say that it's of miserable quality. Plugging in an external mic works just fine. In fact, today I had a nice video chat with my friend over Skype.

system76 provides a repository with all the necessary drivers, so if you ever need to reinstall Ubuntu (or add a specialized Linux kernel to it), it's just a few clicks to reinstall them. (Note that support for the fingerprint reader is still experimental.)

**system76 SUPPORT**

I'll just give you an example of it. When I got my Pangolin, the first thing I did was install a realtime Linux kernel, which I need for my audio recording work. That worked fine, except that my video did not work well with this kernel. So, I shot system76 an email, and also posted on their forums. Now, this is a rather specialized support request. Nevertheless, I got an email response within half an hour, and a forum response within a day. I got all my questions answered and everything works fine now.

Getting support from small companies is a crapshoot: sometimes it means unprofessional, slow response, but sometimes it means up-close and personal. system76 seems like the latter type.

Another nice touch is that the system76 support forum is actually part of the general Ubuntu support forum. So, if you search for an answer to a problem, you're much more likely to find answers in one place.

---

### Post by tssgery on 2008-08-27
Very cool. Mine should ship later this week and I'm really looking forward to it!

---

### Post by ms277017 on 2008-08-27
Nice review... Im dying to use mine, should ship soon.

---

### Post by elene on 2008-08-27
Are the pictures up on system76's site accurate?  It seems like it's a creamy/silvery color all around (save the sides/around the screen).

I feel like I have to wait foreverrr for my machine to come.

---

### Post by Emblem Parade on 2008-08-28
The online pictures indeed seem to be inconsistent, with each other and with the machine I got. Mine definitely has a black cover.

---

### Post by thomasaaron on 2008-08-28
Thank you for the kind words and great review. Very well written.

---

### Post by ms277017 on 2008-08-28
Probably going to cry myself to sleep for a few nights in a row when they release the serval performance... probably should have waited, although pangolin will deffinatly meet all my needs :)


SHIP SHIP SHIP SHIP... LOL

---

### Post by ninjagin on 2008-09-02
You know what,
it look just the same as my new bought fujitsu E8420,
with exacly the hardware spec!

I spend 2200+SGD on this...

---

### Post by ninjagin on 2008-09-02
as mine comes with a vista, and i am thinking og changing it to ubuntu, just wondering which version yours is runing on?
64bit version or the 32 bit version?

---

### Post by djhyland on 2008-09-02
The Pangolins from System 76 come with 64-bit Ubuntu.

---

### Post by wajiguqu0223 on 2008-09-04
To pillow your forces, apiece map is blemished with yellow mines and flags that human a multifaceted capableness of benefits. While the former allows[ ffxi gil ](http://www.ugamegold.com/c_Cheap-FFXI-GIL/)you to work at a specific in-game stock, the latter can do anything from disenable your hostile's ability to spawn troops to gift you new, landscaped units.

---

### Post by Emblem Parade on 2008-09-04
My original review was a bit too glowing, so I feel it best to temper it with a few criticisms.

**HARDWARE**

The Pangolin hardware is beautiful, but there are problems. The cover and screen both smudge very, very easily. If you want it to stay beautiful, you're going to have to constantly be wiping it off.

I mentioned that the internal microphone isn't worth turning on. That's an understatement. It's a total piece of junk. All I manage to record from it is the noise of tapping on it to see if it works. For the price of this laptop, you got to wonder how hard it would be to include a basic tiny mic. It would have been better had it not been included.

And on that "note," the internal speakers are almost as awful. Tinny, weak and barely audible. They'll work in a pinch if you have to listen to something, but you're not going to enjoy it.

Not a really good audio laptop, is it?

But... let me temper that criticism by mentioning that the onboard Realtek High-Definition audio performs *very* well. Connect your Pangolin to some external speakers, and you will be very pleased.

**DRIVERS**

This can be better. My webcam, which worked just fine at first, now stopped working. Works fine in Windows. I'm sure the folks at system76 will try to help me to fix it, but it's still annoying.

Also, I think the driver installer can be better. Right now it offers no feedback to the user (unless you run it from the command line). You don't even get a notification if the process succeeded or failed, or what drivers exactly were installed. It's just a bit too opaque.

Might even be better if there was a suite of tests to see if everything works after you reboot... and possibly send results to system76...

Also, there is a longstanding problem with Linux and suspending your laptop. The bottom line is that it's very broken. There are many reasons for this, part of them having to do with individual drivers. Still, it's not fun when audio stops working, when Compiz needs to be restarted, and just everything kind of becomes funky.

A laptop that can't suspend? I don't think this is a dealbreaker, but I do think it's a serious problem that potential buyers should consider.

I am confident that this problem will be solved, perhaps with the next release of Ubuntu, perhaps with system76 improving the drivers. For now, though, beware.

Also, what's this nonsense about recognizing monitors? Windows XP immediately recognized my external monitor, by name and model, and immediately supported all its resolutions. Why doesn't X.org (the project handling graphics on Ubuntu) do the same? Worse, I couldn't force a certain resolution through the user interface. To solve my problems, I had to go into a lot of depth with the xorg.conf file.

**THE UBUNTU EXPERIENCE**

Ubuntu 8.04 has a lot of little things that are annoying, though the fault is not Ubuntu specifically but the projects it assembles, which can use a bit more maturity.

* Well, one thing that is partly Ubuntu's fault is that they rushed and added the new PulseAudio to Ubuntu 8.04 without enough consideration of its impact. PulseAudio is an ingenious sound system that lets you broadcast sound anywhere to anywhere, network or not, and also control individual volume and mixing per application (like in Vista). Unfortunately, not all packages in Ubuntu are configured to use it properly at this point. Expect many frustrations with this. Getting Skype to work with PulseAudio is especially painful.

* As much as I really like the design and philosophy of the GNOME desktop, I'm quite astounded that there are bugs that haven't been fixed since 2003. I mean, seriously, I move around icons in my panels and they sometimes randomly disappear. Or the order changes every reboot. It's a desktop suite: it's supposed to handle the desktop. It still can't do that without failing.

* Another major complaint is about Adobe's Flash, and this isn't the fault of the free software community. Flash still burns and crashes Firefox far too often. There are free software initiatives to replace it, but they still don't support all web sites. Also, Flash is still only available in 32bit... the free software community had to create a huge kludge just to make it run in 64bits. That kludge can be a source of some the problems. Although, 32bit users complain, too.

I'm sure these complaints will diminish somewhat in the next Ubuntu release, which will include upgraded versions of many of these packages.

---

### Post by thomasaaron on 2008-09-04
You sound frustrated.

The Pangolins suspend very well. And the webcam works well too. 
I can help you sort it out.

Feel free to contact me via email for support (support(at)system76(dot)com).

---

### Post by hvacr on 2008-09-05
> **Emblem Parade said:**
> My original review was a bit too glowing, so I feel it best to temper it with a few criticisms.

**HARDWARE**

The Pangolin hardware is beautiful, but there are problems. The cover and screen both smudge very, very easily. If you want it to stay beautiful, you're going to have to constantly be wiping it off.

I mentioned that the internal microphone isn't worth turning on. That's an understatement. It's a total piece of junk. All I manage to record from it is the noise of tapping on it to see if it works. For the price of this laptop, you got to wonder how hard it would be to include a basic tiny mic. It would have been better had it not been included.

And on that "note," the internal speakers are almost as awful. Tinny, weak and barely audible. They'll work in a pinch if you have to listen to something, but you're not going to enjoy it.

Not a really good audio laptop, is it?

But... let me temper that criticism by mentioning that the onboard Realtek High-Definition audio performs *very* well. Connect your Pangolin to some external speakers, and you will be very pleased.

**DRIVERS**

This can be better. My webcam, which worked just fine at first, now stopped working. Works fine in Windows. I'm sure the folks at system76 will try to help me to fix it, but it's still annoying.

Also, I think the driver installer can be better. Right now it offers no feedback to the user (unless you run it from the command line). You don't even get a notification if the process succeeded or failed, or what drivers exactly were installed. It's just a bit too opaque.

Might even be better if there was a suite of tests to see if everything works after you reboot... and possibly send results to system76...

Also, there is a longstanding problem with Linux and suspending your laptop. The bottom line is that it's very broken. There are many reasons for this, part of them having to do with individual drivers. Still, it's not fun when audio stops working, when Compiz needs to be restarted, and just everything kind of becomes funky.

A laptop that can't suspend? I don't think this is a dealbreaker, but I do think it's a serious problem that potential buyers should consider.

I am confident that this problem will be solved, perhaps with the next release of Ubuntu, perhaps with system76 improving the drivers. For now, though, beware.

Also, what's this nonsense about recognizing monitors? Windows XP immediately recognized my external monitor, by name and model, and immediately supported all its resolutions. Why doesn't X.org (the project handling graphics on Ubuntu) do the same? Worse, I couldn't force a certain resolution through the user interface. To solve my problems, I had to go into a lot of depth with the xorg.conf file.

**THE UBUNTU EXPERIENCE**

Ubuntu 8.04 has a lot of little things that are annoying, though the fault is not Ubuntu specifically but the projects it assembles, which can use a bit more maturity.

* Well, one thing that is partly Ubuntu's fault is that they rushed and added the new PulseAudio to Ubuntu 8.04 without enough consideration of its impact. PulseAudio is an ingenious sound system that lets you broadcast sound anywhere to anywhere, network or not, and also control individual volume and mixing per application (like in Vista). Unfortunately, not all packages in Ubuntu are configured to use it properly at this point. Expect many frustrations with this. Getting Skype to work with PulseAudio is especially painful.

* As much as I really like the design and philosophy of the GNOME desktop, I'm quite astounded that there are bugs that haven't been fixed since 2003. I mean, seriously, I move around icons in my panels and they sometimes randomly disappear. Or the order changes every reboot. It's a desktop suite: it's supposed to handle the desktop. It still can't do that without failing.

* Another major complaint is about Adobe's Flash, and this isn't the fault of the free software community. Flash still burns and crashes Firefox far too often. There are free software initiatives to replace it, but they still don't support all web sites. Also, Flash is still only available in 32bit... the free software community had to create a huge kludge just to make it run in 64bits. That kludge can be a source of some the problems. Although, 32bit users complain, too.

I'm sure these complaints will diminish somewhat in the next Ubuntu release, which will include upgraded versions of many of these packages.

I just purchased one of these units, so hopefully all the bugs are worked out. As far as the speakers, that's ok, I use usb speakers, or run xp and stream music to my airport express. I don't think laptops make good audio players with the built in speakers anyways.

The unit is more than what I need, that's why I did not wait for the new serval to come out.

---

### Post by sandalle on 2008-09-14
I'll be purchasing a Pangolin tomorrow (doing research today). :) Hopefully it doesn't have the overheating problem this Latitude does when I play games (overheats, wireless/LAN shutoff, but the rest of the machine works, but I have to reboot to get networking).

I priced this against a comparable Dells (XPS and Studio) and this was *cheaper* with *better* hardware. I love it! Oh, and all the games I play run via WINE, so no dual-boot for me (just a 32-bit chroot). :)

I would like more screen options, especially a WLED!

---

### Post by Koraq on 2008-10-02
Tell me more about the flash problems, please. 

I'm now using FreeBSD, where Flash support is making it un-usable as a modern browser system. Is the flash problem with 64-bit severe? Flash not working is a deal breaker for a computer for me right now.

---

### Post by Emblem Parade on 2008-10-02
I've had slightly better luck installing the beta of Flash 10. I don't experience any more crashes.

I still get times where Firefox grays out while watching a video, but after 10 seconds it continues to where it was. Definitely annoying, but not quite a dealbreaker for me.
[URL="http://meandubuntu.wordpress.com/2008/08/20/flash-10-rc-on-ubuntu-amd64/"]
Here's[/URL] a nice script for installing it without any fuss.

---

### Post by Koraq on 2008-10-02
Thanks. This do sound promising. 

I had an Kubuntu install on my old 32-bit machine and it worked fairly well. I'd love to get a Pangolin if I can get that experience again.

---

### Post by sandalle on 2008-10-03
Just an FYI, but the internal mic on my Pangolin Performance I bought at the end of September 2008 works great. :) It's not perfect, and external mics might be better, but others hear me well and haven't complained.

---

### Post by matt5ash on 2008-10-18
Using Pangolin Laptops – What's Happened To Me

Well, I have two Pangolin laptops, an older (fall 2007) one that came with 32 bit Ubuntu and a newer (spring 2008 ) one that came with 64 bit Ubuntu.  I've enjoyed good luck with both.  :)

I call the older 32 bit laptop “lap32” and the newer 64 bit laptop “lap64”.  Here's an outline of the features I've used and how they work for me ...

1.Wireless / bluetooth operation works easily.  I've used both computers in several locations for Internet work, and both computers use bluetooth Logitech mice.

2.Internal mic works just fine on lap32 but is not really usably on the lap64 system.  External mic works just fine in both cases.

3.Web cam on the lap64 system works just fine.  The little “Camera Monitor” app works nicely and lights up when the web cam is running (and when I remember to turn the service 'on' !!).

4.USB printer / flash drives ... no trouble.

5.SD card reader works without problem.

6.On the keyboard deck at the top are buttons (Wow Video – Wow Audio – mute speaker).  These features seem to be some what unstable on both computers, but the other two buttons (Browser and email) work just fine.

7.Ethernet hardwired network works.

8.Telephone Modems work.

9.Both systems are stable (on the order or weeks between reboots without worry).

10.No trouble with over heating taking minimal precautions.

11.Wacom tablet works OK.  Interestingly, my office desktop (Dell) seems to “drop” the tablet every so often, and one has to restart X to get things working again, so I sorta expected this kind of result with the Pangolins, but things just work for both lap32 and lap64 systems.

All in all, the Pangolins and the software work very well relative to winXP for my uses.  

Of course, there are a couple of things that would be nice.  

1.On the lap64 system there's a little finger print reader. The finger printer (fprint) software isn't quite ready for prime time.  The software clearly does stuff, but I've not been able to have the system operate in a “just works” way so far.  The folks at System76 showed my how to turn the reader off easily.

2.The audio software is 'usable' but not yet 'nice'.  For example, I Skype frequently, and general have to fiddle with the mixer settings each time I connect.  On the other hand, using Audacity I was able to convert a cassette tape to a CD for a friend with good results.

3.I have to reboot the lap32 system to use the external monitor, while on the lap64 system the blue Fn-F3 button toggles the display.  (Bet this could be fixed if I know enough!)

4.Some control over the touchpad sensitivity and etc. would be nice, especially those with low skin conductance.

Support

System76 support has been very good.  For example the lap32 system came mostly DOA.  Mostly ?? Yup, mostly as in not completely !!  In the end, the folks at System76 decided to replace it and – happy for me – upgraded the wireless system in the trade.  The lap64 system just worked “out of the box”.  In switching to Ubuntu from winXP there's a little learning curve, and the folks at System76 happily answered my questions.  When I need help, I've tried the system76 form, email, and phone.  All approaches have resulted in questions answered and computer success.

In The End – Good Things Have Happened

My wife uses the lap32 system for on-line shopping, email and so on.  There's essentially no trouble keeping the system working.  No worries about Flash / Java, etc. for her uses.  My use with the lap64 system is more about word processing, math/stat program use, and etc. Things are working just fine here too.  We've traveled a little, and used hotel / coffee house / etc. wireless internet connections with complete success.  

For us, the Pagolins are doing a better job of computing than the winXP computers they replace.

--matt5ash

---

### Post by freeqaz on 2009-02-02
So the pangolians, what have they integrated since they have been introduced? I'm rather confused as to how they operate, as seeing that the review above me stated the 2007 and 2008 models were different in hardware, software, etc.

I'm gonna be buying one soon. It has a GeForce 9300, 2.16ghz Core 2 Duo, 320gb HDD, WSXGA+ 15.4" 1680x1050 display, and 2GBs of RAM.

Laptop is 850$. Freakin' good deal, can't find anything better on the internets.

All in all, I'm just wondering if any of the early problems people have posted here still go. Crappy mic, webcam dropping, anything like that? The exact model is:

Pangolian Performance
Display: 15.4" WXGA (1280 x 800) or
15.4" WSXGA+ (1680 x 1050)
Graphics: nVidia GeForce 9300M GS 256MB DDR2
Audio Output: Intel High Definition Audio
Networking: Gigabit LAN (10/100/1000), WiFi
Wireless: 802.11 agn, Bluetooth
Expansion: Express Card 34/54 slot
Ports: VGA, HDMI, 3 x USB 2.0, eSata Port, Headphone Jack, Microphone Jack, S/PDIF Output Jack, SD Reader
Camera: Built-In 2.0 MP Webcam
Security: Fingerprint Reader (beta),
Kensington® Lock
Power Management: Suspend & Hibernate
Battery: includes one 6 Cell Lithium Ion
AC Adapter: includes one AC adapter
Dimensions: 14.13" x 10.55" x 1.46" (WxDxH)
Weight: 5.8 lbs.

---

### Post by thomasaaron on 2009-02-02
I know Matt5Ash, and neither of his computers are the current model.

Wireless, Webcam, etc... all work pretty flawlessly on the PanP4n (the current pangolin).

---

### Post by betrunkenaffe on 2009-02-04
I just picked up a Pangolin recently and I've noticed a few minor issues when using the webcam. When trying to use for amsn, it didn't display anything for the other user and on my screen it only seemed to refresh once per minute. Also I have to drop the resolution on Cheese otherwise it doesn't record at all and crashes cheese when I stop recording. Has anyone else had problems like these? How did you fix it?

audio and mic didn't work in amsn either but I was goign to look into that later, gave me a "cannot write" error message so I'm sure it's either a permissions problem or settings.

---

### Post by Jaivaz on 2009-02-04
Out of curiosity, how long did it take them to ship your laptop?

---

### Post by betrunkenaffe on 2009-02-05
That's something that was a little annoying when I got it, ordered on 6th, was received on 26th. There were delays (quite a few), they boosted the shipping to 3 day due to them.

---

### Post by thomasaaron on 2009-02-05
> When trying to use for amsn, it didn't display anything for the other user and on my screen it only seemed to refresh once per minute. Also I have to drop the resolution on Cheese otherwise it doesn't record at all and crashes cheese when I stop recording. Has anyone else had problems like these? How did you fix it?

TA: Cheese is broken. That's the best it will do at the moment. As for aMSN, that sounds like the person you're IMing doesn't have something configured correctly (and he -- or you -- could be dealing with slow Internet, bandwidth issues, a slow server somewhere...). I've never used aMSN (Skype is better IMHO, and I don't know anybody else who uses aMSN!), but it supports V4L2, so it should work for you.

> audio and mic didn't work in amsn either but I was goign to look into that later, gave me a "cannot write" error message so I'm sure it's either a permissions problem or settings.

You may be right on that one. Do you have your mics set up so that they will work with Sound Recorder? That's always a good first step before trying to get them to work with other programs.

---

### Post by betrunkenaffe on 2009-02-05
Well, I've heard Cheese was broken for some and that other programs were broken for others, is it a 8.10 issue or is there a program that anyone knows works fine? It's not that I use the camera but there are some people I'm showing it and when you say "everything works fine", they always say "prove it" :P

On the amsn thing, sound is fine in sound recorder. When I get a chance, I'm going to play with it a bit more.

---

### Post by thomasaaron on 2009-02-05
Both Skype and Ekiga Softphone (which is at Apps > Internet > Ekiga) work great.

---

### Post by former_warper on 2009-02-06
Freeqaz, this generation of Pangolin appears to be based on another Clevo model, the M760SU, just as the Servals are based on the M860TU.
Clevo has a reputation of building some kick-*ss gaming systems, used by high-end custom boutiques. They have a very good reputation for quality.  My Serval is gorgeous.  I have not had a problem witCheck out reviews online of Clevo - you will see that you are getting tremendous value in Pangolin.
Definitely go for the higher resolution screen.  It is well worth it.

---

### Post by Peebles on 2009-02-06
> **former_warper said:**
> Freeqaz, this generation of Pangolin appears to be based on another Clevo model, the M760SU, just as the Servals are based on the M860TU.
Clevo has a reputation of building some kick-*ss gaming systems, used by high-end custom boutiques. They have a very good reputation for quality.  My Serval is gorgeous.  I have not had a problem witCheck out reviews online of Clevo - you will see that you are getting tremendous value in Pangolin.
Definitely go for the higher resolution screen.  It is well worth it.
Just how closely based are these computers? I've been wanting to buy a Pangolin recently, but I've been turned off by the low battery life. I see that Clevo offers a nine-cell battery for their m760su, and if I can just buy one of those then I might be sold.

---

### Post by betrunkenaffe on 2009-02-06
> **Peebles said:**
> Just how closely based are these computers? I've been wanting to buy a Pangolin recently, but I've been turned off by the low battery life. I see that Clevo offers a nine-cell battery for their m760su, and if I can just buy one of those then I might be sold.

I can't see a closer image on their website but it appears to be exactly the same laptop and specs match up.

---

### Post by thomasaaron on 2009-02-06
I have no idea of the battery is compatible, but the clevo m760su is NOT the Pangolin Performance. 

We know of no other batteries for the Pangolin.

---

### Post by betrunkenaffe on 2009-02-07
He's right, I looked on the back of the notebook, it says the model number clearly under the sticker that s76 put on top of it (no I didn't remove the sticker, I can see through it :P)

---

### Post by betrunkenaffe on 2009-02-11
I decided the only way to really give a decent review would be to write it up after I was done setting everything up and all the problems are fresh in my mind. I won't be posting it for a few weeks after I've had this Pengolin Performance so I can put in updates or correct misconceptions I might have.

To start I had some issues with the building of the hardware, it took a little while. I think it worked out to being 10-11 business days before the laptop actually shipped from their warehouse (with weekends worked out to 16-17). My initial question regarding the amount of time it was taking was answered the same day however turned out to be inaccurate (I was told it would be shipping before end of the next business day). After 3 days I asked again and the agent contacted the warehouse, they said it would be going out for sure before end of next business day, it went out that night (they upgraded shipping to 3 days for free, thank you!).

By the time I had received my laptop, their website showed new specs for the laptops which was faster than the one I had ordered. Understandably I was a little frustrated by that HOWEVER it seems all is better than I thought it would be, they had upgraded the 2.26GHz to 2.40GHz silently. (yes, I did notice!)

As for performance wise, I like it, it worked straight out of box as everyone said, I had to tinker with it to get it to do what I wanted it to (mostly because I wanted flashy effects to show off Linux a little at work). I was impressed that they had flash 10 on it (since it's apparently beta according to adobe site), required little updates and there has been no driver issues. The wifi works better than my friends computer (which is running Vista).

Update: I updated to nVidia 180 driver, I personally found it more responsive with Compiz but I ran into blue screens in videos, had to manually reset to defaults in the nVidia X Server settings. I have tested with a large number of the games I own and pretty much all of them worked, although took a little tweaking with some, winehq was great source for the solutions. I even have Ventrilo working, although was harder on Pangolin than on my desktop (my guess is Pulseaudio is issue)

Update: One downside that I have found is that the battery life isn't what I expected it to be, it's not bad but it isn't great. I now run the laptop without the battery when plugged in and keep it off to side with 40% charge on it. I'd rather that the life didn't drop too much otherwise would be pointless even having it. If you guys can look into getting a longer lasting battery (9 cell, etc), that would be fantastic.. Or provide an option for a lower spec 15" machine with a much better battery life.

Overall, I am impressed by the laptop, it would be excellent for anyone wanting to just buy one and use it for all “basic” desktop usage (word processing, browsing, etc). I've been fiddling with Linux on my desktop for close to a week and a half after work and the laptop runs so much smoother than it, I may have to give the wife the desktop.

Update: I still use the laptop more than my desktop, last time I booted my desktop was to simply load Windows and play some Guild Wars with fiancee (I get bigger screen and better speeds, GW has a slow down bug that wine guys are looking into).

---

### Post by viridari on 2009-02-24
Thanks for the review. I ordered my Pangolin Performance yesterday.

---

### Post by justinjstark on 2009-02-25
> **Emblem Parade said:**
> Expect many frustrations with this. Getting Skype to work with PulseAudio is especially painful.

```
pasuspender skype
```

You can use this with any application that doesn't work with pulse audio.

---

### Post by 3Miro on 2009-03-02
I figured I could share my experience, I got my pangolin couple of weeks ago.

DELIVERY AND INITIAL SETUP
Delivery took some time, however, the e-mails from system76 were very accurate on the shipping and delivery dates (for some reason hotmail send those to the spam and I did not see them for a few days). I ordered it on Sunday and it arrived on Thursday 11 days later.

Flash worked right out of the box, I was able to load youtube seconds after I got the laptop. It connected to my home network flawlessly. I was able to connect at school without any trouble at all (I have friends with Vista and XP and they always have trouble connecting to my router at home).

THE ONLY CON
Negative note: I had to update the laptop with over 100 updates, not a big deal, however, one of those was a kernel update. The Grub menu file for system76 is custom made and the update program did know how to handle it. Gnome lacks a good grub editor anyway so I had to manually update the grub menu file from the terminal. I not a big deal for me, but a lot of users would be upset.

OVERALL
I wish I had seen the skype pasuspender post before, it would have saved me some time and effort, but the build in camera works great with skype out of the box). Touchpad is better than all the Dell ones I have seen (still touchpads always suck to I am using a small portable mouse, no problem getting it work).

Everything works great and to think I was almost ready to buy a Mac ... shivers are running down my spine. This is so much more than any Mac.

QUESTION:
I only have one question: on system76 web page it says that the GeForce 9300M mobo shares 256MB of system ram for graphics. The system monitor shows 3.9GiB of system RAM (out of 4GB), so i figured this is due to the 256MB shared, however, NVIDIA X Server Settings claims that the GPU has 512MB of RAM. Who's wrong, how much memory does the GPU take and from where?

---

### Post by thomasaaron on 2009-03-02
> I only have one question: on system76 web page it says that the GeForce 9300M mobo shares 256MB of system ram for graphics. The system monitor shows 3.9GiB of system RAM (out of 4GB), so i figured this is due to the 256MB shared, however, NVIDIA X Server Settings claims that the GPU has 512MB of RAM. Who's wrong, how much memory does the GPU take and from where?

The System Monitor Reading may be a little off, as 256MB is more than 01.GB.
As I understand it, the GPU has 256MB and borrows 256MB from the installed RAM for a total of 512MB.

---

### Post by 3Miro on 2009-03-02
> **thomasaaron said:**
> The System Monitor Reading may be a little off, as 256MB is more than 01.GB.
As I understand it, the GPU has 256MB and borrows 256MB from the installed RAM for a total of 512MB.

Thanks for the comment. This is actually good news, I did not realize that the GPU had 256MB of its own RAM. The system monitor may actually read all the ram shared or not, which is not a problem.

NVIDIA had almost no info and specs for 9300M on their web-page. Again thanks for clearing this out.

Overall I love my pangolin even more.

---

### Post by betrunkenaffe on 2009-03-03
I solved the Pulseaudio issue by uninstalling it. Installed esound and everything works fine.

---

### Post by Guille Damke on 2009-03-04
It is good to know that another Pangolin user is happy.
I also have a Pangolin but I have no issues with Skype. How do you get the conflict between Skype and Pulseaudio? What is the problem you experience? Is it caused if you suspend the laptop and SKype is up and running? I think I always close Skype before suspending, and I have no problems. Can you describe it?
Thanks,

---

### Post by 3Miro on 2009-03-04
If pulseaudio is running, skype has no sound. I can start it, log in, char, but no sound comes out of it and thus I cannot make phone calls.

killall -9 pulseaudio and then start skype did the trick for me. I should try pasuspend, might be better.

---

### Post by Guille Damke on 2009-03-04
I think you just have to set up Skype audio options correctly (the "pulse" option for sound out and ringing). It works for my on the Pangolin.
If you kill pulse audio and run skype, do you have sound in other programs or the audio device is busy?

---

### Post by viridari on 2009-03-06
> **viridari said:**
> Thanks for the review. I ordered my Pangolin Performance yesterday.

It arrived on March 4 so it showed up earlier than expected (pleasant surprise).

I've been having problems with the optical drive, but Tom in support has been helping me to get it sorted and has a replacement drive on the way. There is a bit of a delay in getting it here, but the support has a personal touch to it that is very much valued.

Otherwise I'm mostly pleased with the laptop. I did get the upgraded display WSXGA+ (1680 x 1050) and it is **gorgeous**. The webcam worked with Skype on the first try, and I'm getting good audio reports from skype buddies as well.

---

### Post by Futurian on 2009-04-30
Viridian (or anyone),

Can you tell me anything about the viewing angles on the wsxga+ display? Thanks.

---

### Post by thomasaaron on 2009-04-30
It will slant back about 40-45 degrees from vertical.

---

### Post by Futurian on 2009-04-30
I'm sorry that I wasn't clear in my question.  I was asking about the viewing angle relative to the display screen (degrees off axis or off normal, horizontally and vertically.

Thanks.

---

### Post by thomasaaron on 2009-04-30
I'm sorry. I'm still not really sure how to answer that one. I don't have any metrics on it.

It seems I can make out the display from about any angle I view it from, within reason.

Let's see if anybody else has a better answer.

---

### Post by andddlay on 2009-04-30
Nice review!  However, is there any chance you could show it on video camera?  I prefer viewing products instead of just reading about them.  There are some pictures, but it doesn't seem to be enough for me. 

Thanks! :D

---

### Post by Futurian on 2009-06-11
> **Futurian said:**
> I'm sorry that I wasn't clear in my question.  I was asking about the viewing angle relative to the display screen (degrees off axis or off normal, horizontally and vertically.

Thanks.

My Pangolin Performance with the 1680 by 1050 display arrived, and I can now answer my own question.

Short answer: The viewing angles are very good.

Psuedo-Calibration: As this is a subjective judgment, note that I am hard to please, and tend to rate displays to be worse than many others' ratings. I love my Dell 24" 2408WFP monitor, which shows almost no change at almost any angle. I look at displays from outlandish angles, trying to find problems.

In anything use resembling normal use, the Panp5 1680 x 1050 display is crystal clear in fact, and a pleasure to work with. I'm very glad I got it.

---

### Post by bgreenaway on 2009-06-11
A wonderful review and I would echo every statement made about the Pangolin, System 76 and Ubuntu experience.

One addendum is that I would go for Amarok as the preferred audio option, although if you are going to use Jaunty 9.04 it comes with the dreadful 2.0 version; make an effort and retro to the 1.4.10 version.

---

### Post by Aadidasu on 2009-08-29
everything is great about system76 Pangolin. I got it in June 2009. 
What is don't like is
1. Mouse pad is very painful to use, especially if you use the left and the right mouse pad buttons.
2. Battery life is not great. Dies in approx. 2 hrs. It would be nice if there was an option to get 8 cell or better battery for some extra cost.
3. Just with normal use, the laptop heats up very fast if kept on desk and then the fan noise. Have seen cheaper laptops not getting heated up so fast. Can't use it as a "lap" top after 30 min.

Would I buy it next time? Will see if System76 has improved the heat management/placement, mouse pad and Battery life and then decide.

---

### Post by thomasaaron on 2009-08-31
There is a key above your keyboard on the left side that has a kind of "M" above it. That is for silent mode. See if that reduces heat and fan noise.

---

### Post by Aadidasu on 2009-09-04
Thanks for that info. It did reduce the fan noise, I suppose it stopped the fan. Does that "M" kinda button reduce any functionality? Is there more detail about what that button does?

One more thing about heat managment is that the laptop gets hot under the right ahdn wrist area when you are typing. It is so painful to use the keyboard after 30 min. 

If I had know that it would be painful to type on this laptops keyboard due to the heat, I would have not bought this. Never had this issue with DELL or ThinkPads or even Thoshiba's

I hope I did not get a defective product.

Any new buyer please consider these points before make a purchace.

---

### Post by thomasaaron on 2009-09-04
The button sets the computer to "Silent Mode." It throttles back the cpu a bit so there is less head production, and thus less fan usage.

All Pangolins get a little warm on the right. It's not a defect. Heat problems are always difficult, as "hot" tends to be somewhat subjective. What is unbearable to some folks isn't even noticed by others.

---

### Post by bill516 on 2009-09-04
My PanP4 has been with me since last April (as I recall).  Delivery came quickly to my home in Kentucky.  Summary evaluation:

1.  Tech Support through Tom Aaron is terrific. Far better than I have experienced from larger vendors.  You can trust it.

2.  Screen option is well worth the money.

3.  Silent mode works.  With my T6400 CPU there is no discernible impact on performance and the machine is very quiet.

4.  Speakers are adequate for something like Skype or Ekiga (both of which work well, by the way).  They are inadequate for any serious music.  I advise purchasing outboard speakers or quality headphones if you wish to do that.

5.  Battery life is around 2 hours and no larger battery is available despite a Clevo manual that implies otherwise.  I have searched extensively.

6.  Suspend/Hibernate is important because of limited battery life.  Both work flawlessly.

7.  My optical drive failed not very long after I received my machine.  Tom made a special effort to get it to me while I traveled.  Zero problems since then.

8.  I currently dual boot wth Ubuntu 8.10 and sidux 2009-2.  sidux is snappier but it requires considerably more maintenance.  8.10 is absolutely bullet-proof.

9.   I very carefully compared against comparable Dell and HP machines before purchasing.  System 76 offered the best value for my dollar.  Still does.

---

### Post by gamerchick02 on 2009-09-04
I have not noticed a heat issue.  Granted, my last laptop was a Gateway MX3225 that had only an hour and 20 minutes worth of battery and also heated up enough to fry an egg on your thighs while you used it!

Anyway, I think it runs quiet (again, comparing to two Gateways; one was a desktop and one the laptop. Both ran with loud fans.).

System76 is an awesome value.  I was looking at computers at my local retail places and the internet, but this really is the best "bang for the buck", I think.

Just my two cents.

Amy

---

### Post by samalex on 2009-09-04
Hey Guys,

I figured I'd throw in a few words plus a question about the whole heat thing as well.

When the 'M' button on the top left is pressed to throttle the CPU and disable the fan, does the 'W' button re-enable it?  I've noticed some heat from the laptop when it's in my lap, but it's nothing unbearable even after a few hours of work.

As for a general review, the laptop is awesome!  I had to tweak Firefox some for my online classes but that's more of a gripe with Ubuntu then System76.  Though I haven't tried every feature yet (audio/video calls with skype, finger print scanner, etc), everything I've tried thus far has worked which is nice.  

Here are some Pro's and Con's about the laptop itself.  I won't base any on Ubuntu itself since those really don't pertain to System76 itself.  Any gripes I have with Ubuntu would be so on any system I ran it on :)

Pros:
- Awesome screen, though I just read the higher-res screen has been phased out. Bummer.
- Good general layout of ports
- Linux (what else is there to say [grin])
- Laptop looks great and brings lots of compliments when working from Panera, Starbucks, B&N, etc.
- Performance and multitasking is excellent, including Windows XP under VirtualBox.
- Thus far the Wifi works great and seems to have great range.
- Support is unbeatable!  These guys are great.
- I haven't really used the webcam outside of testing in Skype (no video call yet) and Cheese, but the resolution is good.
- The few native 3D games I've tried work great.

Cons: (more nitpicky things that spoiled me with my iBook)
- No battery indicator on laptop itself - have to power up laptop to see what battery is currently at.
- Screen is heaver then keyboard/computer part of laptop making the laptop tilt backwards if sitting on laptop, couch, bed, or any other soft surface that may not be completely level.
- Battery life isn't the best, 1.5-2 hours tops (again iBook spoil since it was 3.5-4 hours).
- Touchpad isn't the best, but then again I haven't met a touchpad I liked.
- No Firewire port, which is the only way to connect our DV Camera and external drives.  I'll need to add one through Express Card Slot eventually.
- Though the resolution and picture on the screen is unbeatable, it is VERY glossy and can cause a reflection. When screen is off or dark it could literally be used as a mirror.

All and all I think I made an awesome choice going with the PanP laptop, and after using it for well over a month I can say I'd definitely recommend it to other Linux users.

Take care --

Sam

---

### Post by thomasaaron on 2009-09-07
> does the 'W' button re-enable it? 
No. That should open a web browser.

---

### Post by Julian Lewis on 2010-02-10
I am extreeeeemly envious of all you Americans getting such a very cool computer. I have the misfortune of living near Geneva Switzerland and system76 don't ship outside the US !! Well I will try to get one shipped to a friends New York address and he can ship it on to me, but that is a hassel.
My request to system76 is please please start shipping outside the US as soon as possible, I know you are looking into this but a date for when you intend to provide European shipments would be nice.

---

### Post by AmadeusOK on 2010-02-10
> **Julian Lewis said:**
> I am extreeeeemly envious of all you Americans getting such a very cool computer. I have the misfortune of living near Geneva Switzerland and system76 don't ship outside the US !! Well I will try to get one shipped to a friends New York address and he can ship it on to me, but that is a hassel.
My request to system76 is please please start shipping outside the US as soon as possible, I know you are looking into this but a date for when you intend to provide European shipments would be nice.

You can try ZaReason. It's a small and relatively new company that sells computer with preloaded Ubuntu. They ship internationally. I'm not sure if they have such an amazing technical support as System76 but I've heard good things about them. 

[http://www.zareason.com/shop/home.php]("http://www.zareason.com/shop/home.php")

---

### Post by linusr on 2010-02-10
> **samalex said:**
> Screen is heaver then keyboard/computer part of laptop making the laptop tilt backwards if sitting on laptop, couch, bed, or any other soft surface that may not be completely level

thought LED screens weigh less!!

---

### Post by eddietours on 2010-02-10
can't wait to buy a Pangolin Performance

---

### Post by iwc5893 on 2010-02-10
Well, my company ordered two of the Pangolins for us techs the other day so I'm hoping they'll be here in a couple of weeks.

We work for an ISP and are constantly using our computers in a less than hospitable environment, and I'm hoping that they will stand up to the stress of the job.  The reviews I've read have been overwhelming positive on the construction and the support so I have high hopes.

I will post a review once I've had a chance to play with it some.

---

### Post by eddietours on 2010-02-11
l be waiting for your review iwc5893 :D

---

### Post by iwc5893 on 2010-02-15
> **eddietours said:**
> l be waiting for your review iwc5893 :D

You'll be waiting a while.  We were informed the other day that our order is delayed about 3 weeks due to the Chinese New Year.  I'm not complaining though, especially if they are as good as I've heard and it's worth the wait.

Once we get them, it will take a few days to get them set up so that we can use them at work (specialty ISP software and such) so it will be some time after that that I post a review.

I will say that we use our computers in every weather condition imaginable (sun, sand, rain, sleet, snow, dust) and spend a lot of time using them outdoors.  Unfortunately, I couldn't talk my boss into spending $6K on toughbooks, which is what we really should have.

---

### Post by thlaine on 2010-02-15
This is not meant to be a comprehensive review but merely some thoughts on the process of acquiring and using a Pangolin Performance during the past few months. 

About five months ago I was looking for a new laptop. As a Linux user I tried to find a good machine for my needs (fairly portable, large enough screen res., at least 4GB ram, decent graphic card, pretty design, and affordable price) that would not include Windows. While searching online, I discovered the System 76 website and their line of products of which I considered Pangolin to be something that I was looking for with a decent price. I also read great feedback on the company's quick and knowledgeable support. Then, I was ready to order. 

As many other users on this forum who do not live in the US, ordering wasn't a simple thing. Luckily I had an American friend who agreed to fill in an order and ship it to his brother's address as he currently wasn't staying in the country. I was to pick up the machine when I would travel to US later the same month. Both the ordering and delivery were hassle-free and the machine was delivered quicker than anticipated, and this was around the time when System 86 had some growth pains that were reflected in deliveries in some other cases. Maybe I was lucky but I was certainly happy. 

Then came the first meeting. Package contained all items that I expected. Later on I had to change the power cord to match the power outlets in Finland. I booted up the computer and played a bit to ensure that everything worked. Screen was very clear, mouse pad sensitive enough and overall design was positive. Keyboard, after I got used to it, proved to be excellent (except for the fact that one key is missing as per US English vs Finnish keyboard layout differences). I didn't notice any problems so I packed the device for the rest of the trip and took the beast home. 

After using the panp5 for a few months, I still like it very much and I am glad not to have paid the MS tax. There are only two minor issues that I have noticed: 


[LIST=1]
[*]After a while, a stuck pixel (red) appeared on my screen. I have read tutorials on how to remove one but have not found yet courage to start massaging as software-based approach didn't work. The red pixel is only visible when the screen is dark, which is not very often in my case. Hence, I am able to live with it.
[*]Battery life has not been as good as I had wished for. I had read from the forums that the battery life could be from 1.5h to 2.5h. I seem to be getting less than 2h although I never tried the trick to run the battery all empty and then recharging it. I use the laptop mostly at home so the battery life is not a big of a deal. However, I will be traveling more later this year and I am already looking for a battery pack with higher capacity but so far it doesn't look good. Does someone know where to get one?
[/LIST]

Despite these minor challenges, I would buy from System76 again. Let's see how long my panp5 lasts - I expect at least 3-4 years of a lifetime. Thank you, System76, for providing the good stuff. I look forward to seeing you in Europe!

---

### Post by samalex on 2010-02-17
> **thlaine said:**
> This is not meant to be a comprehensive review but merely some thoughts on the process of acquiring and using a Pangolin Performance during the past few months.
-- SNIP --


Just to throw another quick review out there, I've had my PanP5 for about 7 months now, and I have nothing but good things to say about the laptop.  It gets used daily, and I lug it between work and home every day.

Other then what comes stock below is what my system has:
- Processor Core 2 Duo P8700 2.53 GHz 1066 MHz FSB 3 MB L2 
- Memory 4 GB - DDR2 800 MHz - 2 DIMMs
- Display Resolution 15.4" WSXGA+ Super Clear Glossy LCD 
- Hard Drive 500 GB 7200 RPM SATA II

I'm still running the stock version of Ubuntu 9.04 that came pre-loaded, and it's worked out great.  Below are a hand full of the things I do on my PanP5 most on a daily bases --
- Watch Hulu and other streaming videos on HDTV using VGA output (HDMI doesn't quite work in 9.04 but I hear it's fixed in 9.10)
- Using VirtualBox I have Windows XP loaded where I work with MS SQL 2008 and MS Visual Studio 2008 for work stuff. I also get much of my music through iTunes via VirtualBox (never could get it installed via Wine).
- I code in Linux using Qt Developer, MonoDevelop, and NetBeans (PHP Development)
- Though I'm not a gamer, I've tested FreeCiv, Nexuiz, Planeshift, Vendetta Online, and Warsow, all of which run great!
- I use Skype from time to time for calls, though the on board microphone isn't the best.  I suggest using an external mic.
- Streaming video through UStream also works with the latest 64-bit Flash plugin
- Last semester I took online classes for the first time, and Pronto, the chat client used at my school, worked great in Wine though it's only available for Windows.  Also the online biology labs worked, though it took some work to get Shockwave working in Linux.
- I use the VPN client in the Gnome Network Connections app to connect into work then the Terminal Services client to RDP into work desktop.
- OpenOffice is great!  I use it for all personal and work documents, even when sharing with folks who use MS Office.
- I do web development and use the Gimp for all my graphics editing.  No need for photoshop :)
- I've installed Apache, PHP, and MySQL to test websites locally, and it works great!
- Webmin is also installed which I like using for some of the server admin stuff.
- Rhythmbox is what I use for MP3, Podcasts, and listening to Magnatune and SomaFM, which I listen to most days at work.
- I use Thunderbird with the calendar extensions for email, and Firefox for web.  I have Google Chrome installed, but I prefer Firefox.
- Bluetooth works as expected.. I've shared files with both my wife's MacBook and also my Motorola phone (not a Smartphone -- just regular ol' flip phone).
- Some of the many other apps I use daily are XChat for IRC, Pidgin for chat, SyncTerm for BBSing, KMyMoney for my budget (still learning this), Calibre for eBooks, and lots more.

So all and all I LIVE on this thing, and it has always treated me well.  As Linux goes I've had some quarks, like I had to remove the IcedTea Java and replace it with Sun Java for some sites to work properly, namely my stuff for school, and I installed the Adobe PDF Reader instead of using what came from Ubuntu.  I also haven't been able to get Real Audio to work, which is all our local NPR station streams in (blah).  And as I said before it was kindofa PITA to get Shockwave working since Adobe has no Linux client for Shockwave.  Also Battery life is less then perfect, but that's the 'give' in Give and Take... but IMO there's enough Take to make-up for it :)

The one MAIN thing I recommend people do is get a good laptop bag.  When I bought my iBook 5 or 6 years ago I also picked-up a Timbuk2 messenger bag.  These things have TONS of padding, and it's the least you can do to keep your stuff save.  The website is [http://www.timbuk2.com](http://www.timbuk2.com) for anyone interested, but there are other bags just as good I'm sure.  Mine has gone through hell and back, and like I said it gets toted from work to home and back daily.  Do yourselves a favor and don't go cheap on this...  I think that's one reason so many laptops get hosed, even small things like pixels going tard, is because the laptops are jolted around while being moved.  Here's my trusty bag:

[IMG]http://farm3.static.flickr.com/2440/3928256001_13885ee769.jpg[/IMG]

Anyway, just some thoughts and suggestions.  Take care --

Sam

---

### Post by mcm307 on 2010-02-20
I love my laptop. I put a bad karmic update on it so I had to re-install once. But it works well only freezes once a week or so. Only nagative is sometime the screen will not shut down when the computer is off.

---

### Post by samalex on 2010-02-20
> **mcm307 said:**
> I love my laptop. I put a bad karmic update on it so I had to re-install once. But it works well only freezes once a week or so. Only nagative is sometime the screen will not shut down when the computer is off.

Only freezes once a week and screen will not shut down when computer is off???  I had one freeze last week which was the first and only time it's happened, but if yours is freezing once a week then something's not right.

Maybe my system runs so well because I'm still using the stock version of 64-bit Ubuntu 9.04 that came from System76, though I have loaded all updates from Ubuntu as soon as they come out.  Also I've loaded TONS of crap on it and even tinkered with the back-end config files a great deal ... but still this thing just keeps on going strong ;)  If only I could persuade my Windows purist friends to give Ubuntu or System76 a shake.

Sam

---

### Post by brusegadi on 2010-02-21
I just want to say that I actually love the mouse pad.  It is highly responsive and sensitive.  With most laptops, to get from one end of the screen to another you have to drag your finger many times across the pad... with the Pangolin (PanP6) my mouse-padding finger is happy since one drag on the pad suffices.  Thanks!

---

