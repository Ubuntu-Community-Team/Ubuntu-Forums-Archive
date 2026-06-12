---
title: "Ubuntu -Gnome 17.10 with Gnome 3.26"
date: 2017-09-15
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-09-15
I saw this [http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/) and thought of giving it a go. Anyone else?
Trying live iso. Like what I see. :)
Reacts smoother than Ubuntu default. Will install on bare metal later.
98.3 MB to upgrade!

---

### Post by Chanath on 2017-09-15
Interesting, if they'd really release Ubuntu-Gnome 17.10 on October 19th.

---

### Post by Chanath on 2017-09-15
Installed it on bare metal. Once, installed it booted in to a normal Gnome environment. No system extensions, no restrictions!:)
If I am to use Gnome as default in Ubuntu, I'd quite happily keep this and upgrade it, rather than be stuck with restrictions in the default Ubuntu.
The movement of windows is not jumpy here, quite smooth. The swarm effect is also quite smooth.

EDIT: Not exactly without restrictions. Tried to uninstall gnome-shell-extensions package, but it'd also uninstall ubuntu-gnome-desktop. But, they are not enabled by default, so you can simply ignore them and install any other you want.

EDIT2: I was wrong in thinking those were not system extensions. But, they are not troubling like Ubuntu Dock and Dash to Dock at each other.

---

### Post by Chanath on 2017-09-15
Tweaks don't coordinate with installed extensions, either in default Ubuntu or in Ubuntu-Gnome. The only way to enable/disable extensions is through [https://extensions.gnome.org/local/](https://extensions.gnome.org/local/).

---

### Post by ventrical on 2017-09-16
Chanath,

Could you request mod to merge your thread with  [https://ubuntuforums.org/showthread.php?t=2368129](https://ubuntuforums.org/showthread.php?t=2368129) because it us basically the same topic.

Thanks

regards..

---

### Post by Chanath on 2017-09-16
> **ventrical said:**
> Chanath,

Could you request mod to merge your thread with  [https://ubuntuforums.org/showthread.php?t=2368129](https://ubuntuforums.org/showthread.php?t=2368129) because it us basically the same topic.

Thanks

regards..
 
Greetings!

Not exactly, as I've installed Ubuntu-Gnome daily iso, *not the default Ubuntu daily iso. *
The thing is, if there won't be a release of Ubuntu-Gnome 17.10, there shouldn't be a daily of that "derivative." 

After reading this blog post, [https://didrocks.fr/2017/09/11/ubuntu-gnome-shell-in-artful-day-11/](https://didrocks.fr/2017/09/11/ubuntu-gnome-shell-in-artful-day-11/), I thought of downloading the daily Ubuntu-Gnome.

---

### Post by ventrical on 2017-09-16
> **Chanath said:**
> Greetings!

Not exactly, as I've installed Ubuntu-Gnome daily iso, *not the default Ubuntu daily iso. *
The thing is, if there won't be a release of Ubuntu-Gnome 17.10, there shouldn't be a daily of that "derivative." 

After reading this blog post, [https://didrocks.fr/2017/09/11/ubuntu-gnome-shell-in-artful-day-11/](https://didrocks.fr/2017/09/11/ubuntu-gnome-shell-in-artful-day-11/), I thought of downloading the daily Ubuntu-Gnome.

As I did also .

Point well taken. I didn't see the bifurcation.

Regards..

---

### Post by Chanath on 2017-09-16
I wrote this in the other thread, but I its better placed here.

[COLOR=#000000]Ubuntu-Gnome 17.10 can be just made into an installable live iso. It would be a pure Gnome-shell based on Ubuntu 17.10. The ubuntu-gnome-desktop can be uninstalled without any harm/loss to already installed Ubuntu with Gnome.

Considering that Ubuntu-Gnome 17.10 final will not be released on October 19th with other derivatives, this live iso could be uploaded.[/COLOR][COLOR=#000000] The creator/uploader of that iso doesn't even have to maintain it, for all packages would be maintained by Ubuntu itself, as Ubuntu default is now Gnome.

The idea of "alternative" Ubuntu, the one with gnome-session was discussed here, [/COLOR][https://didrocks.fr/2017/09/11/ubunt...artful-day-11/]("https://didrocks.fr/2017/09/11/ubuntu-gnome-shell-in-artful-day-11/")[COLOR=#000000]*,*[/COLOR][COLOR=#000000] most probably not thinking much about it.


[/COLOR]

---

### Post by ventrical on 2017-09-16
Not a problem. I already downloaded it and am going to test it.

---

### Post by ventrical on 2017-09-16
yep .. there it is. Our cake and eat it too :)

---

### Post by Chanath on 2017-09-17
> [COLOR=#373737][FONT=&amp]Next year, if you are using either Ubuntu 16.04 LTS or Ubuntu GNOME 16.04 LTS, you will be prompted to upgrade to Ubuntu 18.04 LTS. For normal release users, this upgrade should happen with the release of 17.10.

[/FONT][/COLOR]&#8203;[COLOR=#373737][FONT=&amp]The development teams from both Ubuntu GNOME and Ubuntu Desktop will be merging resources and focusing on a single combined release, that provides the best of both GNOME and Ubuntu. [/FONT][/COLOR] [https://ubuntugnome.org/blog/](https://ubuntugnome.org/blog/) This was posted in April, 2017 and after that no more blog posts.

[COLOR=#373737]But there is a separate daily iso for Ubuntu-Gnome, and it happens every day at a given time. Most probably, when a user [/COLOR][COLOR=#373737]of the Ubuntu-Gnome 17.10 development issue (if there are any), clicks blindly to upgrade to a new version, the upgrader might uninstall meta package ubuntu-gnome-desktop and install ubuntu-desktop. That is, if there is such a meta package for Ubuntu-Gnome user to move to 17.10 without changing his setup. This would happen to any "normal user" of 17.04 or 16.04, when 18.04 LTS is released. The thinking "at the top" could be that there won't be any Ubuntu-Gnome users by that time and all would have moved to the default 17.10.

Now with the talk about "alternative" Ubuntus (by the guy, who is creating the Ubuntu Dock), the Ubuntu-Gnome 17.10 development install should not be blindly upgraded to the next release (or to the final 17.10 release), if you want to keep the *pure one *going on. You can keep this Ubuntu-Gnome going on for next 18.04 and further. Even though, the Ubuntu-Gnome meta package might not be around, the "pure" one would live on as the gnome-session package cannot be taken off the repos.  

This also opens other possibilities. 
1) Getting rid of the ubuntu-gnome-desktop (as something not needed later) turning the installed system to pure Gnome. But, you can keep most or all what is there in Ubuntu-Gnome.
2) Creating new (old) Ubuntu-Gnome live iso (an exact copy),
3) Creating a pure Ubuntu based Gnome live iso,
4) Creating a Ubuntu based Gnome-flashback live iso,
5) and so on...

You don't need to be a coder to do this, just a bit of imagination. You don't have to change the wallpaper or the plymouth theme, if you don't want to.[/COLOR]:)

---

### Post by ventrical on 2017-09-17
> **Chanath said:**
> [https://ubuntugnome.org/blog/](https://ubuntugnome.org/blog/) This was posted in April, 2017 and after that no more blog posts.

[COLOR=#373737]But there is a separate daily iso for Ubuntu-Gnome, [/COLOR][COLOR=#373737]
You don't need to be a coder to do this, just a bit of imagination. You don't have to change the wallpaper or the plymouth theme, if you don't want to.[/COLOR]:)

Yes. I realize this.
I am a coder.
I am not on the development team. I know enough to expect breakage down the pipe and will deal with it accordingly. For me  and unity7 maintenance, it is wait and see atm. I do not want to be a kabitzer to the project.

regards..

---

### Post by Chanath on 2017-09-17
> **ventrical said:**
> I do not want to be a kabitzer to the project.

regards..

Interesting word, kabitzer, but that's not the idea. 

Doesn't this look nicer? Its Ubuntu-Gnome 17.10 with default Ubuntu wallpaper. This is GnoMenu extension. Its from the original idea sometime in 2010 or so, the eye-candy menu for Gnome 2. This is what made Zorin this popular. Xubuntu has Whisker Menu.

The overview is there too in the screeny, on the bottom left corner and on the default top corner.

---

### Post by ventrical on 2017-09-17
> **Chanath said:**
> Interesting word, kabitzer, but that's not the idea. 

Doesn't this look nicer? Its Ubuntu-Gnome 17.10 with default Ubuntu wallpaper. This is GnoMenu extension. Its from the original idea sometime in 2010 or so, the eye-candy menu for Gnome 2. This is what made Zorin this popular. Xubuntu has Whisker Menu.

The overview is there too in the screeny, on the bottom left corner and on the default top corner.

I don't think you understand what I said. Uh.. basically it's out of my control as far as the merge. I agree with you , perhaps there should be 2 distros of gnome but it is a resource dilema. ie; So who will pay my wages when I pull back on malware removal for Windows and devote that time to Ubuntu? Nobody. However, I have a deep gratitude for what Ubuntu has done and what it stands for and is why I am still admin of U+1  and will remain so as long as the community council supports me.

Regards..

---

### Post by ventrical on 2017-09-17
> **Chanath said:**
> Interesting word, kabitzer, but that's not the idea. 

The Canonical desktop development team sets the design flowchart. I can offer arguments against it (which of course I have) but there is a limit. I have signed CoC so my arguments have to be tempered, somewhat, as to not present too much of a disruption to the default already chosen last April. It is what it is. So, kabitzer, would sort of be like a counter-community thread. And we have to see that they are doing this for security reasons , mostly.

Regards..

---

### Post by Chanath on 2017-09-17
> **ventrical said:**
> I don't think you understand what I said. Uh.. basically it's out of my control as far as the merge. I agree with you , perhaps there should be 2 distros of gnome but it is a resource dilema. ie; So who will pay my wages when I pull back on malware removal for Windows and devote that time to Ubuntu? Nobody. However, I have a deep gratitude for what Ubuntu has done and what it stands for and is why I am still admin of U+1  and will remain so as long as the community council supports me.

Regards..

You also didn't understand me on this. I only said that Ubuntu-Gnome 17.10 can be forked, and the chances to do that are just hanging about. I am not asking you or anyone to do that, but its there. Its so obvious. It can be done right away, without waiting for 17.10's official release. I only mentioned something I saw.

---

### Post by ventrical on 2017-09-17
> **Chanath said:**
> You also didn't understand me on this. I only said that Ubuntu-Gnome 17.10 can be forked, and the chances to do that are just hanging about. I am not asking you or anyone to do that, but its there. Its so obvious. It can be done right away, without waiting for 17.10's official release. I only mentioned something I saw.

Perhaps someone will. uhh... expect big changes comming.

---

### Post by Chanath on 2017-09-17
The screenies below are with Dash to Dock, not Ubuntu Dock. 
Ubuntu Dock is not installed at all.

The new Dash to Dock enables background tiles on app launchers, when an app is running. The colour of the icon is based on the dominant colour of the app icon. The Dash 2 Dock developer thinks this will please the 'nostalgic' Unity users.

The developer would not stop developing, so what would Ubuntu dock do? I think, Ubuntu should make its own launcher, if Gnome is to become the default. Unity launcher was not someone else's, but Ubuntu's own.

---

### Post by Chanath on 2017-09-17
First came Dash to Dock and brought the Dash out of hiding--can be accessed without going to top left corner. Then another thoughtful person, placed the dash in the top panel, which cancelled the dash on the left, and made one panel for everything--the most successful model for panels at the moment in *any *OS. That panel can be placed in any side of the screen, which gave more choice to the users. The thoughtful developer brought the panel to a higher level, giving what a normal desktop user wants. There are previews, minimize, maximize from the panel, clock moves aside to give more space and so on.

Then, there are easy menus such as Gnomenu, Arc Menu that can happily co-work with the panel. What the Gnome developers are trying to take away from the users, this developer gives back.

Screeny with the Arc Menu on the Panel in Ubuntu-Gnome 17.10.

---

### Post by Chanath on 2017-09-18
I wonder, if ubuntu-gnome-desktop will be available after 16th October, the 17.10 final release day.

---

### Post by Chanath on 2017-09-19
Uninstalled ubuntu-gnome-desktop, together with gnome-shell-extensions. Now, there is no Ubuntu specific meta package, which will break the install, if a dist-upgrade is done. Have Gnome and Gnome on Xorg, but Gnome-Classic is gone, which is quite all right.

---

### Post by Chanath on 2017-09-20
Even cleaned it up with Bleachbit, which uninstalled 543MB, but nothing terrible happened. Its still Ubuntu Gnome, but without the ubuntu-gnome-desktop. I am awaiting the few weeks after the official 17.10 release to move it to 18.04 dev.

---

### Post by Chanath on 2017-09-27
Ubuntu-Gnome daily is frozen on 19th September, while other dailies are dated 26th. Finally, Ubuntu-Gnome had come to the end. I just downloaded *the last of the kind. *

The Ubuntu-Gnome 17.10 dev install, which gets normal upgrades as its the same packages that goes into Ubuntu default. The artful wall papers also came in sometime ago. This install doesn't have any Ubuntu-...-desktops, so, it'd upgrade and most probably move to 18.04 dev without a problem. 

Doesn't it look nice with just one panel on the bottom and the Arc Menu?

---

### Post by ventrical on 2017-09-27
Is here:

> 
The **Ubuntu GNOME** flavor has been discontinued. If you are using Ubuntu GNOME, you will be upgraded to Ubuntu. 


[https://wiki.ubuntu.com/ArtfulAardvark/ReleaseNotes#Ubuntu_Desktop](https://wiki.ubuntu.com/ArtfulAardvark/ReleaseNotes#Ubuntu_Desktop)

regards..

---

### Post by Chanath on 2017-09-27
> **ventrical said:**
> Is here:

> [COLOR=#000000]*The *[/COLOR]**Ubuntu GNOME flavor has been discontinued. If you are using Ubuntu GNOME, you will be upgraded to Ubuntu.**

[https://wiki.ubuntu.com/ArtfulAardvark/ReleaseNotes#Ubuntu_Desktop](https://wiki.ubuntu.com/ArtfulAardvark/ReleaseNotes#Ubuntu_Desktop)

regards..

Mine won't. It doesn't have an ubuntu-......-desktop. Its still Ubuntu Gnome, or Ubuntu with Gnome.
I'd only keep this for experimenting. Gnome is terribly slow. When I go back to Xubuntu (or Openbox), everything is so snappy, work (life) becomes easier.
Even Unity is faster than Gnome.

---

### Post by rrnbtter on 2017-09-27
Greetings,

> **Chanath said:**
>  Gnome is terribly slow. 

If you are running Gnome Shell on X then you are right. Gnome Shell on Wayland is very fast. I noticed this back in June when we were in early development. 

I find it ironic though that x11 apps load faster in Gnome with a work-around like xwayland then they do with Gnome on x. Either way the above quoted statement needs some qualification. There are just too many variables at play right now. If you don't have the heart of your system in the complete Gnome/GDM3/Wayland experience then you won't get the full results.

---

### Post by ventrical on 2017-09-27
> **rrnbtter said:**
> Greetings,



If you are running Gnome Shell on X then you are right. Gnome Shell on Wayland is very fast. I noticed this back in June when we were in early development. 

I find it ironic though that x11 apps load faster in Gnome with a work-around like xwayland then they do with Gnome on x. Either way the above quoted statement needs some qualification. There are just too many variables at play right now. If you don't have the heart of your system in the complete Gnome/GDM3/Wayland experience then you won't get the full results.

I agree .. it is very smooth n' sleek. If you leave it as it is it won't trouble much but if you try adding apps that were used in the 16.04 cycle (ie;vokoscreen) they will fail unless you have  software from ppa load ups and then there is increased risk of breakage.so to run a lot of apps you have to use gnome-shell on Xorg. So it becomes a cornered and sheltered DE. I am not complaining .. just pointing to the obvious. I am confident that this could be fixed by 18.04 release.

Regards..

---

### Post by Chanath on 2017-09-27
> **rrnbtter said:**
> Greetings,
If you don't have the heart of your system in the complete Gnome/GDM3/Wayland experience then you won't get the full results.

Greetings!

Well, I am using both Gnome on Wayland and Gnome on Xorg. There is nothing more on the GDM login screen. In different partitions, I have fully upgraded Unity only and Gnome only 17.10 installs, for experimenting. The new Unity only comes from the Unity7N.iso and Gnome only comes from former Ubuntu-Gnome, but without the ubuntu-gnome-desktop and the extensions package. The extensions installed in it are done manually. The screeny in my last post was from Gnome on Wayland or "default." The only difference from the Ubuntu (default) is that it doesn't have the Ubuntu Dock and the default system extensions. So, I have *the last of the kind*. 

It gets the same upgrades the default Ubuntu gets, for its Gnome. Its just like, you can have Xubuntu or XFCE. Both sessions work. Only Xubuntu and XFCE are friendly to each other.

I also don't have to dist-upgrade, just to get a name. All, I have to do is delete the "Suite: devel" and "(development branch)," which I can do manually.

---

