---
title: "Gnome shell extensions stopped installing"
date: 2017-05-27
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-05-27
Ubuntu 17.10 with Gnome shell installed. GNOME Shell 3.24.2
Installed five extensions, but after that none is getting installed.  
Is this happening with you guys too?

---

### Post by Chanath on 2017-05-28
Gnome shell extensions can be installed in stock Ubuntu-Gnome 17.04, though. GNOME Shell 3.24.1

---

### Post by joseph592 on 2017-06-01
Upgrade from 17.04  to 17.10 same issue Gnome Shell, extensions not installing.

---

### Post by amano on 2017-06-02
One problem of Gnome Shell is that it constantly breaks its extensions. Thus you will probably have to wait until those are updated.

---

### Post by dino99 on 2017-06-02
extensions are fully installed and working when they are picked up from the  artful archive; but you need first to purge the ones installed from extensions.gnome.org which indeed does not work with a dev release (as usual)
(so, delete the extensions entries from .local dir)

---

### Post by #&amp;thj^% on 2017-06-02
> **dino99 said:**
> extensions are fully installed and working when they are picked up from the  artful archive; but you need _**first to purge the ones installed from extensions.gnome.org which indeed does not work with a dev release**_ (as usual)
(so, delete the extensions entries from .local dir)

+1 After that no problems here.
FWIW>>They also install very nicely from synaptic package manager.
Regards

---

### Post by jbicha on 2017-06-02
Hi, could one of you affected by this issue file a bug with details about what's not working

```
ubuntu-bug gnome-shell
```

---

### Post by joseph592 on 2017-06-02
I went in and deleted the contents of extensions directory, but am still not able to install extensions. Can we install them using the Chrome extension? Are we not able to install from extensions.gnome.org?

Regards

---

### Post by #&amp;thj^% on 2017-06-02
> **jbicha said:**
> Hi, could one of you affected by this issue file a bug with details about what's not working

```
ubuntu-bug gnome-shell
```

+1 And maybe make sure you logout and login again to double check if install failed in the first place.

---

### Post by joseph592 on 2017-06-02
I'll file a bug report for this issue.

---

### Post by joseph592 on 2017-06-02
Bug report. Done.

---

### Post by joseph592 on 2017-06-02
Can confirm after logout and log back in no extensions installed. Was able to use Chrome extension to reinstall extensions I was using before. So +1 here.

---

### Post by jbicha on 2017-06-02
Please make sure 'chrome-gnome-shell' is installed.

It is not installed currently by default in Ubuntu 17.10 because it needs to be [approved]("https://wiki.ubuntu.com/MainInclusionProcess") for inclusion in Ubuntu's main repository first.

See also [this list]("https://wiki.ubuntu.com/DesktopTeam/GNOME/MIR_List").

---

### Post by joseph592 on 2017-06-02
I verified that chrome-gnome-shell version 9 is installed.

---

### Post by jbicha on 2017-06-02
What version of Firefox are you using?

---

### Post by joseph592 on 2017-06-02
Am using Chrome [COLOR=#303942][FONT=Ubuntu]Version 58.0.3029.110 (64-bit).[/FONT][/COLOR]

---

### Post by Chanath on 2017-06-03
All these DEs are problematic in all kinds of ways. After 6 years, Unity had been stopped. It would be nice, if apps interconnected in DEs be allowed to be installed without many (or any) artificial dependencies. Gnome shell actually is not useful without the Dash to Panel extension. With this extension, even the Activities Overview could be used without much wrist problems. The Ubuntu devs should think about wrist problems, when making the "new" Ubuntu with Gnome. Actually, I don't see much difference of this Activity Overview from Skippy-XD.

Openbox with Tint2, Plank dock and Skippy-XD gives a better service than Gnome shell with Activities overview and dash--less resources and less wrist problems. (Carpal tunnel syndrome is one of the problems.)

Why do I want to install extensions? Mostly to have less mouse actions, so I can save my wrist.

---

### Post by kurt18947 on 2017-06-04
Chanath I'm sorry to hear about your wrist pain. Have you considered a track ball in place of a mouse? I thought trackballs were helpful that way. I don't have carpal tunnel and don't want it so I've been using a trackball for years. Trackballs take some getting used to but they work fine in *buntu.

---

### Post by Chanath on 2017-06-05
Thank you for your kindness, Kurt. I don't have carpal tunnel syndrome, and I don't want to have it. But, I have wrist and palm pains due to extensive mouse use. I use mouse to work, not to play. The continuous moving from any place of the screen to the top left corner is a terrible thing, Unity and Gnome developers had given us. That's why the use of Plank dock or any other dock. I like Openbox, because of the lightness, ease of use, and the right click anywhere on the screen. Gnome 3 is nice, but I can get the same look at all open apps with Skippy XD. Anyway, I am looking forward for Ubuntu to do something nice with stock Gnome3, maybe bring down the top left hotcorner to the bottom right or left.  Maybe, the Windows devs listen to the users, who after experimenting with a different desktop in Win 8 and 8.1, came back to the old bottom panel and start menu. The user created Dash to Panel brings in ease to work flow and that has to heard by the Gnome devs, and if they can't, by the Ubuntu devs, or users would run away.

---

### Post by jbicha on 2017-06-06
You can press the Super/Windows key to see the Activities Overview instead of using your mouse.

It appears like Ubuntu's Desktop Team is more interested in Dash to Dock than in Dash to Panel from what I've seen so far, but you're welcome to install whatever extensions you want on your computer.

---

### Post by amano on 2017-06-07
> **jbicha said:**
> 
It appears like Ubuntu's Desktop Team is more interested in Dash to Dock than in Dash to Panel from what I've seen so far,...

That's probably a sane decision (if already made) to have a smooth transistion for the Unity crowd. It's visually closer to what people are used to and it's also closer to the Unity user experience.

---

### Post by kurt18947 on 2017-06-07
> **jbicha said:**
> You can press the Super/Windows key to see the Activities Overview instead of using your mouse.

It appears like Ubuntu's Desktop Team is more interested in Dash to Dock than in Dash to Panel from what I've seen so far, but you're welcome to install whatever extensions you want on your computer.

Dash to Dock is the first extension I install on a new install. Without a couple extensions (and tweak tool) I would likely switch Desktops. It will be interesting to see what Canonical does. They said not to expect much but I don't think it would take much to get Gnome 3 usable on the desktop as installed.

---

### Post by ventrical on 2017-06-08
> **amano said:**
> That's probably a sane decision (if already made) to have a smooth transistion for the Unity crowd. It's visually closer to what people are used to and it's also closer to the Unity user experience.

I'm really having a problem with the "unity crowd" reference. May I just remind everyone that unity is still the current-release flagship desktop and that the option will be available in the universe come 18.04. I have encouraged the development version team to test gnome3 on wayland (as which I am using right now) and we are doing it respectfully as possible. We accept gnome3 and wayland as part of Ubuntu , not as a crowd. Can the same respect be shown to unity as it is being phased out.

Thanks..

Regards..

---

### Post by Chanath on 2017-06-09
> **jbicha said:**
> You can press the Super/Windows key to see the Activities Overview instead of using your mouse.

It appears like Ubuntu's Desktop Team is more interested in Dash to Dock than in Dash to Panel from what I've seen so far, but you're welcome to install whatever extensions you want on your computer.

The fact is, the extensions that get installed in Ubuntu Gnome 17.04 doesn't get installed in Ubuntu 17.04 + gnome shell and also in Ubuntu 17.10 that came only with Gnome yesterday. For example, try Applications Menu, Arc Menu, Gno-Menu etc.

---

### Post by jbicha on 2017-06-09
Chanath, could you file a bug please?

---

### Post by amano on 2017-06-13
> **ventrical said:**
> I'm really having a problem with the "unity crowd" reference. May I just remind everyone that unity is still the current-release flagship desktop and that the option will be available in the universe come 18.04. I have encouraged the development version team to test gnome3 on wayland (as which I am using right now) and we are doing it respectfully as possible. We accept gnome3 and wayland as part of Ubuntu , not as a crowd. Can the same respect be shown to unity as it is being phased out.

Thanks..

Regards..

Sorry, I didn't want to sound disrespectful. English isn't my first language. "The unity crowd" should just refer to the expected mass converts from Unity, myself included (and I love Unity!!) and nothing pejorative at all.

---

### Post by ventrical on 2017-06-13
> **amano said:**
> Sorry, I didn't want to sound disrespectful. English isn't my first language. "The unity crowd" should just refer to the expected mass converts from Unity, myself included (and I love Unity!!) and nothing pejorative at all.

Thanks for your explanation. I guess it's my problem :)

If I can just point out once again, unity-desktop will be in the universe repos actively being developed and I disagree with the term conversion:) At this stage of the game, especially with development version testing, it is the direction of the ubuntu development team , Canonical and most likely their partners that have decided that artful-desktop and beyond to the next LTS  will be default flagship DE .. but . .ya know ... if testers and noobs and general users want to be on the cutting edge and have the next new shiny thing in their hands .. then 'convert' is a fair term.

It's not exactly fun switching from one desktop to another.  ... so yeah .. it's sort of like eating crow :)

Regards..

---

### Post by jbicha on 2017-06-13
> **ventrical said:**
> unity-desktop will be in the universe repos actively being developed

Unity is not really being actively developed in Ubuntu.

---

### Post by ventrical on 2017-06-13
> **jbicha said:**
> Unity is not really being actively developed in Ubuntu.

"We will maintain Unity7  for LTS releases" Ok.. 'developed' , 'maintain' ..big difference. I agree. So current LTS is 16.04 with Unity as default. Until it's EOL it will be default.  Come 18.04 , after this current development cycle, the ball will be in gnome3's court and we will see then if it will cut the mustard as  a workable  LTS.
 :)

regards..

---

### Post by Chanath on 2017-06-14
Even though I started this thread, my interest in Gnome 3 in Ubuntu is getting thinner and thinner. Unity was developed by Ubuntu, and made Ubuntu different. Gnome 3 can be found everywhere. Ubuntu coming with Gnome 3 is not a big deal. Gnome 3 distros are nothing new. If I am going to use Ubuntu, most probably it'll be with Xubuntu and Openbox + Ubuntu base. If Unity is pulled out of the repos, it is not nice at all!

---

### Post by ventrical on 2017-06-14
> **Chanath said:**
> Even though I started this thread, my interest in Gnome 3 in Ubuntu is getting thinner and thinner. Unity was developed by Ubuntu, and made Ubuntu different. Gnome 3 can be found everywhere. Ubuntu coming with Gnome 3 is not a big deal. Gnome 3 distros are nothing new. If I am going to use Ubuntu, most probably it'll be with Xubuntu and Openbox + Ubuntu base. If Unity is pulled out of the repos, it not nice at all!

I was posting in another thread about this. Unless somebody comes forward to maintain the depends it will stay in the archive , or may even be pulled from the archives if it causes problems - perhaps even during this cycle as I can tell already there are problems with systemd slowing down login even after logging on to gnome-shell on a fresh install.

 I agree ., it is very sad for unity to go. 

regards..

---

