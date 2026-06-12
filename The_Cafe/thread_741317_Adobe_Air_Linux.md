---
title: "Adobe Air Linux"
date: 2008-03-31
forum: The Cafe
---

### Post by macewan on 2008-03-31
An alpha version of Adobe Air is available for download.

Get

[http://download.macromedia.com/pub/labs/air/linux/adobeair_linux_a1_033108.bin](http://download.macromedia.com/pub/labs/air/linux/adobeair_linux_a1_033108.bin)

Read

[http://labs.adobe.com/downloads/air_linux.html](http://labs.adobe.com/downloads/air_linux.html)

Digg

[http://digg.com/linux_unix/First_look_Adobe_AIR_alpha_unleashed_for_Linux](http://digg.com/linux_unix/First_look_Adobe_AIR_alpha_unleashed_for_Linux)

---

### Post by BDNiner on 2008-03-31
I would like them to finish flash on linux first. But this news is very positive.

---

### Post by twright on 2008-03-31
tried the alpha and absolutely love it :)

---

### Post by SunnyRabbiera on 2008-03-31
some motivation at last.
I hope more adobe products will get ported soon

---

### Post by nonly1n on 2008-03-31
Hi everyone, 

Got a problem i can't install it and am running The Hardy Heron Beta anybody got any help///its goin to be greatly appreciated...

my error msg when i try to install is

"""
Sorry an error has occurred.

An error occurred while installing Adobe AIR. Installation may not be allowed by your administrator. Please contact your administrator.

"""

even if i sude the installer and if i run it as a normal user it asks for my password and still ends up with that error

---

### Post by sefs on 2008-03-31
I installed by double clicking on the .bin file.

How do I uninstall it.


Also I see a setup.deb in the adobe air directory, what is that for?

---

### Post by SunnyRabbiera on 2008-03-31
> **nonly1n said:**
> Hi everyone, 

Got a problem i can't install it and am running The Hardy Heron Beta anybody got any help///its goin to be greatly appreciated...

my error msg when i try to install is

"""
Sorry an error has occurred.

An error occurred while installing Adobe AIR. Installation may not be allowed by your administrator. Please contact your administrator.

"""

even if i sude the installer and if i run it as a normal user it asks for my password and still ends up with that error

well hardy is still a beta...

---

### Post by Superkoop on 2008-03-31
> **nonly1n said:**
> 
Sorry an error has occurred.

An error occurred while installing Adobe AIR. Installation may not be allowed by your administrator. Please contact your administrator.
r


I get the same error message while installing. And I'm using 7.10, so this isn't a Hardy error. I have tried running from the terminal, and by double clicking. Both give me the same error. (I have tried running it using both gksudo and sudo)
There is a thread open on the Adobe Air Linux forums about this: [http://www.adobe.com/cfusion/webforums/forum/messageview.cfm?forumid=72&catid=677&threadid=1349878&enterthread=y](http://www.adobe.com/cfusion/webforums/forum/messageview.cfm?forumid=72&catid=677&threadid=1349878&enterthread=y)
Lets hope this gets figured out.

---

### Post by macewan on 2008-03-31
[http://www.macewan.org/2008/03/31/howto-install-adobe-air-on-ubuntu-linux/](http://www.macewan.org/2008/03/31/howto-install-adobe-air-on-ubuntu-linux/)

[[IMG]http://www.macewan.org/pownceAirLinuxScreenshot2.png[/IMG]]("http://www.macewan.org/pownceAirLinuxScreenshot.png")


My first Adobe Air App was Pownce's Air client.

---

### Post by Superkoop on 2008-04-01
Ah, I think I have discovered that my problem is a 64bit problem, and that the AIR installer only works on 32bit architectures. :'[

---

### Post by mrgnash on 2008-04-01
I still don't know what the point of this thing is supposed to be.

---

### Post by SomeGuyDude on 2008-04-01
> **mrgnash said:**
> I still don't know what the point of this thing is supposed to be.

Yeah, what the heck IS it? :confused:

---

### Post by twright on 2008-04-01
just an easy way to write apps for the desktop using web technologies (which many developers are familiar with)

it is also now multiplatform so that's another plus

---

### Post by blithen on 2008-04-01
> **Superkoop said:**
> Ah, I think I have discovered that my problem is a 64bit problem, and that the AIR installer only works on 32bit architectures. :'[
Me too...I hate life. T_T
If anyone wants the error here it is:
```
(setup:10441): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libaurora.so: wrong ELF class: ELFCLASS64

```

---

### Post by retrow on 2008-04-01
It worked just fine for me. I installed Hardy Heron from scratch after upgrade from gutsy started giving me some troubles. Installation of Adobe Air went fine and so did installation of apps.

Here are a few snapshots from the installation process of one example application:

[screencap 1]("http://www.nuclear-imaging.info/files/image/adobeair_ss1.png")
[screencap 2]("http://www.nuclear-imaging.info/files/image/adobeair_ss2.png")
[screencap 3]("http://www.nuclear-imaging.info/files/image/adobeair_ss3.png")
[screencap 4]("http://www.nuclear-imaging.info/files/image/adobeair_ss4.png")

---

### Post by Twitch6000 on 2008-04-01
I would lmfao if adobe ever went fully open source.
This is nice though :).

---

### Post by DoktorSeven on 2008-04-01
Is this anything like Air Jordans?

Cause I need some good shoes to wear while using Linux.

;)

---

### Post by Jaymoon on 2008-04-01
> **sefs said:**
> I installed by double clicking on the .bin file.

How do I uninstall it.


Also I see a setup.deb in the adobe air directory, what is that for?

From the command line, you can uninstall with:

**dpkg -r adobeair-enu**

Or I suppose you could also use **rpm -e AdobeAIR_enu**

---

### Post by retrow on 2008-04-01
Another way would be:

[i] chmod +x adobeair_linux_a1_033108.bin
./adobeair_linux_a1_033108.bin[/i]

---

### Post by macewan on 2008-05-26
retrow, thanks for the screenshots. took a couple myself and uploaded to flickr.

[http://www.flickr.com/photos/macewan/](http://www.flickr.com/photos/macewan/)

[[IMG]http://farm4.static.flickr.com/3108/2499649954_8bd279bbaa_m.jpg[/IMG]]("http://www.flickr.com/photos/macewan/2499649954/")

---

### Post by twoseids on 2008-05-29
I have just installed it and am loving life! Only really using it for Twhirl at this point. But it was awesome to go to Twhirl's site, see that it is only for Windows and Mac, and to be able to download and install it with no problems whatsoever. Awesome.

Also tried the Fresh feed reader, but it keeps downloading duplicate feeds, so I'll just stick with Liferea for that. They also have a Google reader clone but it was buggy so I uninstalled.

I also would like to see a way to minimize Twhirl to the panel tray thingie, instead of having an ugly icon on the button in my taskbar down below.

Still, I'm a big fan. Can't wait to see what else becomes available!

---

### Post by Shaythong on 2008-07-10
> **twoseids said:**
> I also would like to see a way to minimize Twhirl to the panel tray thingie, instead of having an ugly icon on the button in my taskbar down below.

I agree, Adobe AIR should make it available to minimize it to the tray instead of the panel bar.

---

### Post by mikemimik on 2008-09-06
does anyone know if they have released a 64bit verion of adobe air? I am still unable to install it and would really love to be running twril. I'm currently using gtwitter and I dont like it because it doesnt let you reply to people.

---

### Post by lukjad on 2008-09-06
D'Oh! Posted on the wrong thread.

---

### Post by binbash on 2008-10-02
Bump for this.I tested around 20 applications and they work perfect.The thing that sucks is you cant install applications via flash (at adobe marketplace)

---

### Post by iheartubuntu on 2008-10-17
So how do I get these apps working in linux? Every site I go to says the app is not available for my system!!

---

### Post by gnothi on 2008-12-26
Some assert that Linux's terminal CLI is required to install [_Adobe AIR_](http://www.adobe.com/products/air/). Wrong!

First, install Adobe [_Flash 10_](http://get.adobe.com/flashplayer/). ;)

For AIR: Using (GNOME's) Nautilus file manager GUI, right-click on the Adobe BIN file and check under the Properties' Permissions tab, to allow executing the file as a program. Next, right-click and Rename the file to remove its .bin extension, so the file name is just AdobeAIRInstaller. Finally, double-click the file to run the Adobe installer, which pops open a new window, requests your authorization (password), and prompts you through the install. That's it.

You'll then find AIR maintenance items in the Ubuntu "Accessories" menu (or in the "Tools" menu of Mandriva Linux 2009). The .air file extension is associated with Adobe's run-time. An AIR application can be removed via the distro RPM or DEB package manager GUI, or by double-clicking its original .air installation file.

:-)

---

### Post by nyiti on 2009-03-25
I'm having problems with Adobe AIR 1.5.1: the installer finishes all right, but when I try to install any air app, it throws segmentation fault.

No errors or anything. The file browser opens, I select the .air, the installer windows pops up for a moment but instantly segfaults.

The same results for TweetDeck and Twhirl, so the problem is not with the apps. I guess the AIR installer should be ok as well, the bug may be somewhere in the system settings, env. variables or something?

---

### Post by nyiti on 2009-03-27
> **binbash said:**
> Bump for this.I tested around 20 applications and they work perfect.The thing that sucks is you cant install applications via flash (at adobe marketplace)

Gosh, I'm going crazy over what makes everything throw segmentation fault for me then. AIR installs, that's fine. But every .air app I try to load, flashes up the install window and crashes.

Maybe I'm missing some libraries or sth? I'm using Thunar file manager instead of Nautilus, but that shouldn't be a problem. I guess you just installed AIR and it was all working right away?

---

### Post by binbash on 2009-03-27
> **nyiti said:**
> Gosh, I'm going crazy over what makes everything throw segmentation fault for me then. AIR installs, that's fine. But every .air app I try to load, flashes up the install window and crashes.

Maybe I'm missing some libraries or sth? I'm using Thunar file manager instead of Nautilus, but that shouldn't be a problem. I guess you just installed AIR and it was all working right away?

I was using beta when i wrote that post.Now i amm using latest (1.5) and that also works fine.Tried 5-6 more applications and all work great.You may be missing some deps.Please post the output of terminal when it crashes

---

### Post by yarko on 2009-06-28
...I simply get "segmentation fault"....

I thought the goofy spaces in the path / command might be messing, so I went right to the installation dir:  /opt/Adobe\ AIR/Versions/1.0  and read thru the script, and just invoked things manually.

It just all looks like this:

```
yak:/opt/Adobe AIR/Versions/1.0$ ./airappinstaller /home/yak/downloads/TourDeFlex.air 
Segmentation fault
yak:/opt/Adobe AIR/Versions/1.0$ ./airappinstaller /home/yak/downloads/ColorBrowser.air 
Segmentation fault
yak:/opt/Adobe AIR/Versions/1.0$ 
```

Cool, huh?   Argh!


AIR installer 1.5.1,  Ubuntu 9.04 x86 (32 bit).

Oh, fun...

---

