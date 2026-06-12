---
title: "Firefox snap is zippy"
date: 2022-09-06
forum: The Cafe
---

### Post by mickee384 on 2022-09-06
I am now using the snap for Firefox as a result of installing Ubuntu MATE. I was going to switch browsers immediately after the install, but left it for a few days. It is just a zippy as Chromium and Chrome. I guess I am one of the lucky few who don't experience a lag using the snap...

---

### Post by vanadium on 2022-09-06
The lag is only while loading. It is largest when loading firefox the first time in a session, and smaller (compared to loading the deb version) on subsequent loadings. While running, there never has been an issue with the performance of the snap app compared to a deb install.

---

### Post by ajgreeny on 2022-09-06
The only issue that bothers me is the snap version of firefox's inability to access the file system except for certain folders in your home.

This is far too limiting for me given the way I use my machines so I have completely removed the snap infrastructure from all of them and I run firefox from the extracted .tar.gz archive direct from Mozilla.
I realise this is not the same for all, but with my fairly old computers with spinning disks and both nearly 10 years old the snap startup first time in a session is simply too slow to use, and that inability to view or save files in the "wrong" folders is just too much bother to deal with.

---

### Post by poorguy on 2022-09-07
> **ajgreeny said:**
> 
I realise this is not the same for all, but with my fairly old computers with spinning disks and both nearly 10 years old the snap startup first time in a session is simply too slow to use,


My Linux computers are all 10 years and older all with mechanical hard drives it's what I have so what I use glad to see I'm not the only one still using old computers.

Yup Firefox Snap startup first time in a session ain't the quickest but after that Firefox Snap  startup first time in a session Firefox Snap opens in seconds.

I don't have any problems with Snap and since Snap comes as default in Ubuntu I'll use it.

---

### Post by Shibblet on 2022-09-07
> **poorguy said:**
> My Linux computers are all 10 years and older all with mechanical hard drives it's what I have so what I use glad to see I'm not the only one still using old computers.

Yup Firefox Snap startup first time in a session ain't the quickest but after that Firefox Snap  startup first time in a session Firefox Snap opens in seconds.

I don't have any problems with Snap and since Snap comes as default in Ubuntu I'll use it.

I keep waiting for Snaps to get better.  It's good to hear Firefox is a bit more "snappy."

Chromium is still only available as a Snap, and it seems to work just fine.  It does feel a bit slower than the previous "non-snap" version, but that could be due to a Chromium update... not sure.  Either way, the "bit slower" isn't enough to get frustrated over.  ;-)

---

### Post by ajgreeny on 2022-09-07
> **Shibblet said:**
> I keep waiting for Snaps to get better.  It's good to hear Firefox is a bit more "snappy."

Chromium is still only available as a Snap, and it seems to work just fine.  It does feel a bit slower than the previous "non-snap" version, but that could be due to a Chromium update... not sure.  Either way, the "bit slower" isn't enough to get frustrated over.  ;-)
If you can use the snap without problems that is fine but when I first tried chromium as the snap when it appeared in 20.04 (or was it 18.04; I do not remember?) it did not allow me to save downloaded files to anywhere other than downloads in my home and it also would not open html files from other than specific home folders the details of which I can't remember.

I found this extremely annoying as I have things set up to download different file types to different destinations, and that was simply impossible using the snap system so I got rid of snaps completely and started using the Dev. ppa from [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev) and have stayed with it ever since.

Now I remove the complete snap infrastructure from my Xubuntu machines with no problems following on from doing so.

---

### Post by grahammechanical on 2022-09-08
A while ago the developers changed the compression algorithm used for snaps.

[https://ubuntu.com/blog/snap-speed-improvements-with-new-compression-algorithm](https://ubuntu.com/blog/snap-speed-improvements-with-new-compression-algorithm)

Regards

---

### Post by lammert-nijhof on 2022-09-08
Almost nobody investigates what happened to the Firefox snap, but many spout a completely outdated opinion. There have been many improvement, resulting is a much faster load time of Firefox. A large part of the problem was the slow decompression of the XZ compressed files. One of the changes was that XZ has been replaced by LZO. Another improvement has been to parallelize the decompression over all CPU threads. On the 2nd slowest Ryzen (4C4T) available in the world Firefox now loads in ~5 seconds, the following loads are in ~3 seconds :)    I use here a nvme-SSD. 

If I load the Firefox from two HDDs (9 power-on years) in Raid-0, the first load takes ~7 seconds and the following loads take ~3 seconds. Note that all 3 seconds loads (nvme and Raid-0) are done from the L1ARC memory cache (openZFS), because Firefox is cached there. 

From my 11 year old i5-2520M laptop with a 2TB HDD; Firefox load the first time in ~9 seconds and afterwards in ~3 seconds. Also here after the 1st time Firefox is loaded from the Linux disk cache used by ext4.  With an Ubuntu boot time of more than 2 minutes, I don't complain about the 1st Firefox load time of 9 secs (laptop HDD); 7 secs (Raid-0) or 5 seconds (nvme).  If Firefox is loaded from memory cache, it takes ~3 seconds for all following loads. 

Note that only the first load of Firefox is determined by 1st the disk speed and 2nd the CPU speed, all following loads depend mainly on the CPU speed. If I want faster Firefox load times, I have to replace my Ryzen 3 2200G by a Ryzen 5 5600G (3x faster than the 2200G). Probably I can reach 1 second instead of 3 seconds.

---

### Post by Shibblet on 2022-09-12
> **ajgreeny said:**
> I found this extremely annoying as I have things set up to download different file types to different destinations, and that was simply impossible using the snap system so I got rid of snaps completely and started using the Dev. ppa from [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev) and have stayed with it ever since.

Now I remove the complete snap infrastructure from my Xubuntu machines with no problems following on from doing so.

Double check and see if you're not running a Snap of Chromium.  I have never been able to get that "~saiarcot895" PPA to work.

I'll point you to this thread:  [https://ubuntuforums.org/showthread.php?t=2464112]("https://ubuntuforums.org/showthread.php?t=2464112")

---

### Post by ajgreeny on 2022-09-12
I remember that thread very well as it totally baffled me.However looking back at it now I wonder if you were running the command ***sudo apt install chromium*** which as you say will install the snap version.

To use the PPA I use and you have linked above you need to use command ***sudo apt install chromium-browser*** which will definitely pull in the PPA version plus dependencies, not the snap version.

---

### Post by Paddy Landau on 2022-09-15
> **ajgreeny said:**
> The only issue that bothers me is the snap version of firefox's inability to access the file system except for certain folders in your home.
Since Canonical fixed the slow startup of Snap, it has been rather nice — but for this one problem, where Canonical has been overly paranoid about the security model.

The Snap security model would have been a good one, had it not been for the fact that you have no way to tweak or tailor the security model for an app. An example is Gedit, which is unusable if you wish to edit, or even view, files outside the pre-designated areas. For example, you [cannot edit your own]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1897562") [FONT=courier new]~/.bashrc[/FONT] file, or any files within [FONT=courier new]~/.config[/FONT] or [FONT=courier new]~/.ssh[/FONT]. Nor is it possible to view, much less edit even with [FONT=courier new]sudoedit[/FONT], system files such as [FONT=courier new]/etc/fstab[/FONT].

The good news is that it's easy to install the Flatpak system. Firefox and Gedit (among others) are available, along with auto-updates should you include that option. Flatpak allows you to tweak, tailor and even completely replace the security model for any app. So, if you were to install the Flatpak version of Firefox, you could tweak its security model to allow any folder that you so desire — or restrict it even further, should you feel that that is important.

I'm happy to use Snap, but I'm even happier to use Flatpak.

---

### Post by vanadium on 2022-09-15
Not everybody is sensitive to it, but in the snap or flatpak version, the loss of focus of a file dialog is a major bummer for users with a keyboard oriented workflow. Try it:

- Open Firefox snap or flatpak
- Hit Ctrl+S to save the webpage
- Type a file name, hit enter.

All good ... the first time you do this in a session. Now do that again. You will see that your filename is ended up nowhere (or with Chromium/Chrome is ending up in the URL bar): the file dialog is displayed after hitting Ctrl+S, but it is not anymore focused.

The bug is with xdg-desktop-portal, so affects many applications that are containerized, but also non-containerized installs that use this library to display native file dialogs (e.g. Google Chrome installed with the vendor supplied deb).

This bug is [known](https://github.com/flatpak/xdg-desktop-portal-gtk/issues/137#issuecomment-1090119458) and recently celebrated its fourth anniversary.

Mouse users obviously will not care, but I use the [Firefox .deb version](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04) directly from Mozilla.

---

### Post by Paddy Landau on 2022-09-15
> **vanadium said:**
> … in the snap or flatpak version, the loss of focus of a file dialog…
This is interesting because, for me, it doesn't happen only in flatpak or snap. It happens to me, for example, in Chrome, which is installed from the official Chrome PPA. It started in Ubuntu 20.04, and is still here with 22.04. It also doesn't affect only the browser; I find it happening with other windows and dialogues as well.

To summarise, I've tested this and found it to be a problem with all of PPA, Snap, Flatpak and Appimage.

I see that this already has a [bug report in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1949340"). Please upvote it (the green writing near the top left after you log in).

There's a corresponding [bug report in Gnome]("https://gitlab.gnome.org/GNOME/gtk/-/issues/5087") Gitlab. Please upvote it as well.

(A Gnome extension, [Just Perfection]("https://extensions.gnome.org/extension/3843/just-perfection/"), *partially* mitigates focusing problems (turn on option Custom > Behaviour > Window Demands Attention Focus); but, as I say, it's only a partial mitigation that unfortunately doesn't fix the browser problem.)

---

### Post by vanadium on 2022-09-15
> **Paddy Landau said:**
> This is interesting because, for me, it doesn't happen only in flatpak or snap. It happens to me, for example, in Chrome, which is installed from the official Chrome PPA.

For me too, I actually indicated that as well. Thanks for localizing some more reports on the issue. I will go upvoting...

It reproduces also on Mate, but not on xfce (according to a quick test I did some time ago).

> 
(A Gnome extension, [Just Perfection]("https://extensions.gnome.org/extension/3843/just-perfection/"), *partially* mitigates focusing problems (turn on option Custom > Behaviour > Window Demands Attention Focus); but, as I say, it's only a partial mitigation that unfortunately doesn't fix the browser problem.)

This is a different issue, a result of a Gnome design decision. Applications that are launched are designed not to steal the focus once they are launched, so stay in the background and instead an annoying "...window is ready" notification appears. A dedicated extension, appropriately called "No Annoyance" exists for quite some time solely to revert this behavior, but some other extensions, including Just Perfection but also Unite, also include the setting.

---

### Post by Paddy Landau on 2022-09-15
> **vanadium said:**
> This is a different issue…
Ah, thank you.
> **vanadium said:**
> A dedicated extension, appropriately called "No Annoyance"…
I see that this has been replaced with [NoAnnoyance v2]("https://extensions.gnome.org/extension/2182/noannoyance/"). Thanks for pointing it out.

---

### Post by Paddy Landau on 2022-09-16
> **vanadium said:**
> … the loss of focus of a file dialog
I've found a workaround for this! I'm using it, and it works well.

My workaround requires [Devilspie 2]("https://www.nongnu.org/devilspie2/"). Unfortunately and unsurprisingly, it doesn't work in Wayland, but it works in X.Org.

[LIST=1]
[*]Install Devilspie 2 from the standard repositories or, if you want the latest version, which has several improvements, compile from source direct from the [Devilspie 2 Github]("https://github.com/dsalt/devilspie2").
[*]Add [FONT=courier new]devilspie2[/FONT] to your autostart programs.
[*]Create the file [FONT=courier new]~/.config/devilspie2/devilspie2.lua[/FONT] (you can use a different file name; read the instructions for details).
[*]In this file, add the following lines:
```
if ( get_application_name() == 'xdg-desktop-portal-gnome' and get_window_type() == 'WINDOW_TYPE_DIALOG' )
then
    focus_window();
end
```
[*]Log out and in again to start Devilspie 2.
[/LIST]

---

### Post by vanadium on 2022-09-16
What a great idea to try devilspie here! I added this to my config file! Indeed, nothing of this control is possible in Wayland, unfortunately.

---

### Post by Paddy Landau on 2022-09-16
> **vanadium said:**
> Indeed, nothing of this control is possible in Wayland, unfortunately.
Wayland was created for all the right reasons. Alas, as is so typical of large-scale software development, the designers designed the functionality from their personal biases, and neglected to ask what would be the real-world consequences of their decisions.

I hope that they fix this problem, because I have several scripts that depend on X.Org functionality that simply isn't possible on Wayland.

---

