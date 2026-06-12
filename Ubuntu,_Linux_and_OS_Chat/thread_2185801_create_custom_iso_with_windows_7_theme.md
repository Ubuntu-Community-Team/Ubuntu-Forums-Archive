---
title: "create custom iso with windows 7 theme"
date: 2013-11-04
forum: Ubuntu, Linux and OS Chat
---

### Post by lanchopat on 2013-11-04
To convince my friend of using GNU/Linux, especially Ubuntu, I started to discuss with him. Finally, he tried Kubuntu :( Now he is strict against Linux, because "it is not user-friendly" and so on... KDE was simply too complicated. So I continued discussing, showed him Mint Cinnamon - no, that looks not like Windows, Windows looks so much better :rolleyes:
So I decided to make him a Live CD with Ubuntu Gnome and a Win 7 theme preinstalled. I hope he'll try the "normal" Ubuntu then, when he sees how cool it is to have stuff like a package manager etc.
The bad thing is that I tried everything but I am not able to do so #-oI found [this shell script]("http://www.addictivetips.com/ubuntu-linux-tips/how-to-make-ubuntu-look-like-windows-7-theme/") and wanted to use UCK to customize the Ubuntu 13.10 32-bit Gnome image from my Ubuntu 13.10 64-bit computer. However, I always run in several issues, UCK doesn't let me run the script (please use the gnome desktop for the theme installation), Customizer cannot display the new iso's display nor run the script, either, remastersys has similiar issues, ...

So what I want to know now is: How do I append the shell script at the end of the main installation to auto-install and configure the windows theme (perhaps with UCK)? My goal is to have a windows-looking Ubuntu after the installation. Other ideas are also welcome.

If there are mistakes in my text, I'm sorry because English is not my native language.

---

### Post by Mark Phelps on 2013-11-04
Don't mean to be discouraging ... but I'm afraid that you're fighting a "losing battle" here.  It appears from what you say,  Linux must be a "clone" of MS Windows for your fried to like it -- and, despite your changing the theme, it is NOT a clone -- it is an alternative.

Next thing you know, your friend will want to run all their same Windows apps on Ubuntu -- and that's not going to happen!

If you want a Linux distro that has more of the menu-oriented approach of Win7, you should try Mint 15 with the Cinnamon desktop.  If you friend says that is "not user-friendly", you might as well give up -- as you are heading down a path that will not work out for you.

---

### Post by bluedxca93 on 2013-11-18
Hi,
search for blueseven os in sourceforge net or gnome-look.org. I've done that with cinnamon for 13.04. I have already created an 13.10 version, but there are  still some litlle bugs/ so  just see the screns here: [http://askubuntu.com/a/293832](http://askubuntu.com/a/293832) . 
Much more is not possible (apart from transparency and perhaps blur and or bumpmap effects).
if your interested i could perhaps upload it for ubuntu 13.10 . The 13.04 version is already in the internet.
I could also tell you how to create your own uhbuntu live cd.
Hope you could test the system. I know my answer is a bit late, but perhaps you will read it.
regards bluedxca93

---

### Post by douglas.e.ryan on 2013-11-18
I don't guess he gave any specifics about why it isn't "user friendly" enough? Or maybe you showed him too much when you presented KDE, since there are a lot of potentially intimidating options but basic use isn't hard at all.

---

### Post by bluedxca93 on 2013-11-18
Yeah Cinnamon is easy to use, but its difficult to configure it. 
Cinnamon can have  at least all the basic options from win7 basic, ex see here( 13.04) : [http://www.pro-linux.de/kurztipps/2/1629/](http://www.pro-linux.de/kurztipps/2/1629/) . 
And you can add a lot of other options.
What is not really working ( at the moment)  are the blur effects. But i don't know if they are necessary for working.

If i start gimp on my windows 7 installation it takes about 10 Minutes. Under Ubuntu/Cinnamon it takes about 5 seconds. Photoshop CS2 and ms office 2010 runs under wine as fast as under windows. Some directx programs don`t work. But most older  NET-Framework Programs are running. If you want to run games that are designed for MS Windows you will find  ubuntu "not user " friendly of course.

sry for my bad english,  i'm german and even my french is better than english.

---

### Post by Bucky Ball on 2013-11-18
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Can't for the life of me think why you'd go to all this trouble to convince someone who seems quite happy using Windows to use Ubuntu. Why? Is it for their benefit or yours? Seems like your friend's not interested and you're wasting time. :-k

Sorry if that's a bit discouraging, but ...

Xubuntu's really simple, easy to configure, but it's not Windows. No Ubuntu/Linux flavour is. Have you tried Windows 7???

---

### Post by craig10x on 2013-11-18
How does your friend feel about macs?  If he has seen them and likes them you can tell him the main version of ubuntu is very "mac-like" in it's interface (except the dock is on the left instead of the bottom) :D

Still, he has to understand that it still won't work exactly like windows does nor will he be able to use windows programs (unless he runs wine and even then not everything well)...in fact, he will be better off just using the linux alternatives...
He would have to be willing to adopt to doing a certain amount of things different then he is use to with windows...

But no question, main Ubuntu is much more simply laid out then say Kubuntu...my friend puts windows users on main ubuntu all the time and they love it...

---

### Post by 3rdalbum on 2013-11-19
I agree with the other posters. No matter what you do, you won't make Ubuntu look or feel much like Windows 7. If the guy's not willing to tolerate a different-looking theme, he's certainly not going to tolerate something that works very differently to Windows.

Not to mention the confusion of "Well, this looks like Windows, so why can't I run Windows programs?".

And it sounds like he's not receptive, so pushing him like this will probably be counterproductive.

However, I'll point out: Anything inside the directory /etc/skel/ will appear in any new user's home directory. If you modify the Gnome settings to point to the different theme on your installed copy of Ubuntu, then take that settings file and put it into the correct location inside /etc/skel on your new live CD and put the theme into /usr/share/themes or wherever it needs to go, your new theme will be the default on the new live CD image.

---

### Post by stalkingwolf on 2013-11-19
zorin did have a win 7 look for the desk top .  I like mate I just add a panel and then the things i want to make it how i want.

I agree you are probably wasting time.

---

### Post by Bucky Ball on 2013-11-19
> **3rdalbum said:**
> 
... it sounds like _he's not receptive_, so pushing him like this _will probably be counterproductive_.



+1. [underlines mine ;)]

You could give this person an exact replica of Win7 (on the surface), but sounds like they have no interest whatsoever in using Linux (under the bonnet) and will find fault. They have poo-pooed everything you've shown them so far and refused to even try and understand where you're coming from.

---

