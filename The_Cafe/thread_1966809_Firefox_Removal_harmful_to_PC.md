---
title: "Firefox Removal harmful to PC?"
date: 2012-04-27
forum: The Cafe
---

### Post by sports fan Matt on 2012-04-27
Just had an interesting thought...If one completely removed Firefox from their system (if they chose to run Google Chrome..Opera, etc), would the system be in a state to where you couldn't boot?  

I have heard various answers on this ranging from It can't boot because FF is part of the integrated system that makes Precise able to function to it doesn't harm it at all.  Just looking for clarification.  (And no, wasn't going to remove it, just curious) Matt

---

### Post by Irihapeti on 2012-04-27
I'm running an install without Firefox on my EeePC 900 (using Seamonkey from Mozilla instead), and have been doing for a while, and no harm has occurred.

---

### Post by MisterGaribaldi on 2012-04-27
Hmm... I have no idea about this since I haven't run any of the last three releases of Ubuntu.

I can't imagine this would actually be the case. I mean, how can they in one release establish such a system-wide dependency? Secondly, wouldn't that completely fly in the face of the F/OSS community and its philosophy of liberty?

I mean, I like Firefox and was using it since about version .70 or .80, but (hypothetically) if Canonical were to "Internet Explorer" Firefox onto their distro, then that would be a pretty darned good reason to switch (not because FF is necessarily bad, but because of the sort of mentality behind such a dependency) to some other distro.

---

### Post by Copper Bezel on 2012-04-27
Firefox is not integrated into Ubuntu in the way that Internet Explorer is integrated into Windows - or in any other way, really. It just has an add-on pack (for the *browser*) to work better with the Ubuntu desktop, and it's in the default software. I think it tends to get reinstalled if you do a distribution upgrade, but it's not going to cause you any fuss. (And these things tend to be very modular in Linux - Epiphany has a lot of integration with the Gnome desktop, but it doesn't damage the latter not to have the former installed.)

---

### Post by vasa1 on 2012-04-27
Let's say one removes Firefox after installing some other browser and making that other browser the "default". Will the links in Ubuntu Software Center open with that other browser?

---

### Post by lovinglinux on 2012-04-27
You can safely remove Firefox from your system and install any browser you want.

---

### Post by keithpeter on 2012-04-27
Hello vasa1 and all

I'm posting this from chromium-browser having removed Firefox on my 'throwaway' Precise testing install (I'm going to do a clean install on Sunday when Canonical's servers have recovered). The commands I used were

```
keith@xeon:~$ sudo apt-get purge firefox
```

then

```
keith@xeon:~$ sudo apt-get install chromium-browser
```

I've just loaded Ubuntu Software Centre and searched for the pyroom full screen editor. I clicked on the More Info button, then I clicked on the Developer Website link, and Chromium loaded the pyroom developer's Web site in a new tab.

I loaded the System Settings app and clicked on Default Applications to find Chromium listed as my default Web browser.

Now, the only issue is that I purged Firefox *before* installing Chromium. If you are having problems, let us know what kinds.

@MisterGaribaldi

+1, and I say that as an NCSA 0.3 user :twisted: who actually *paid money* for Netscape back in the days. 

I suspect the 'stack integration' will be in the direction of wayland/lightdm/compiz, and I'm prepared to give that a try. An integrated video stack would be cool.

---

### Post by lovinglinux on 2012-04-27
> **keithpeter said:**
> Now, the only issue is that I purged Firefox *before* installing Chromium. If you are having problems, let us know what kinds.

The only issue about removing Firefox and installing Chromium/Chrome is phylosofical. Even considering Chromium is open source, using a Mozilla product is still much better for the future of the Internet.

---

### Post by Version Dependency on 2012-04-27
I've installed Opera in the last two releases of Ubuntu with no problems.  Links in email and other programs open up in Opera with no problems.  So no...you won't hurt your installation removing Firefox and installing another browser.

---

### Post by keithpeter on 2012-04-27
> **lovinglinux said:**
> The only issue about removing Firefox and installing Chromium/Chrome is phylosofical. Even considering Chromium is open source, using a Mozilla product is still much better for the future of the Internet.

I think I'm inclined to agree, plus Firefox has the Firebug and Zotero addins!

I'm just extracting the last bits of juice from my 'testing' install before doing a clean install on Sunday.

---

### Post by keithpeter on 2012-04-27
> **Version Dependency said:**
> I've installed Opera in the last two releases of Ubuntu with no problems.  Links in email and other programs open up in Opera with no problems.  So no...you won't hurt your installation removing Firefox and installing another browser.

Opera has an email client and note taking app built in. Do you make use of these? How heavy a footprint is it these days? 

Could be handy for a 'light' install (netinstall, gdm, icewm, opera)

---

### Post by lovinglinux on 2012-04-27
> **keithpeter said:**
> Opera has an email client and note taking app built in. Do you make use of these? How heavy a footprint is it these days? 

Could be handy for a 'light' install (netinstall, gdm, icewm, opera)

All major browsers have a big footprint these days.

I am running Firefox with 49 extensions right now and it is using 350 Mb of RAM. I am also running Opera with 6 extensions and it is using 198 Mb of RAM. However, I am not actually browsing with Opera right now. When I do that, it can go over 500 Mb. But Firefox can go over that as well.

Opera is an excellemnt option. I like it a lot, specially the built-in mail/feed reader and the irc integration. Unfortunatelly, I still have issues with compatibility with some sites. In that regard Firefox is unbeatable.

---

### Post by Version Dependency on 2012-04-27
> **keithpeter said:**
> Opera has an email client and note taking app built in. Do you make use of these? How heavy a footprint is it these days? 

Could be handy for a 'light' install (netinstall, gdm, icewm, opera)


I can't comment on the note taking app (don't take notes).  I've looked at the email client and it works fine, but I use thunderbird (been using it forever on both Windows and Ubuntu).  

Opera is fine for a lightweight install.  I've used on minimalist installs with openbox.  What really turned me on to Opera a few years ago was using Firefox in an old Windows XP machine with only 256MB of RAM (did I mention it was an old machine?).  Firefox would barely load up, and when it did it ran slooooow.  Installed Opera and it ran like champ even with just the 256MB of RAM.  Continued to use Opera in Windows ever since, and since moving to Linux I just continued using it.

---

### Post by TheMTtakeover on 2012-04-27
> **lovinglinux said:**
> the only issue about removing firefox and installing chromium/chrome is phylosofical. Even considering chromium is open source, using a mozilla product is still much better for the future of the internet.
 
+1

---

### Post by lovinglinux on 2012-04-27
> **keithpeter said:**
> I think I'm inclined to agree, plus Firefox has the Firebug and Zotero addins!

I'm just extracting the last bits of juice from my 'testing' install before doing a clean install on Sunday.

There are several examples of Firefox add-ons that are superior in quality or doesn't have Chromme/Opera conterparts due to limitations of the extension APIs. 

Unfortunately, we should see a mass migration to Chrom... eventually, because of the flash plugin.

---

### Post by Copper Bezel on 2012-04-27
It baffles me, really. I really want a simple speed dial. The top search item for "Firefox speed dial" is awesome and usable and intelligent and stable. I've tried, like, fifteen Chrome speed dial extensions, and not one of them simply worked without compromise. 

Similar results for touch scrolling. The top hit for Firefox works. The top hit for Chrome randomly makes text unselectable and occasionally breaks random page elements, including, recently, the page navigation links here at UF. Hilarity ensued.

I use Chrome, but damn, the extension base is not comparable.

---

### Post by lovinglinux on 2012-04-27
> **Copper Bezel said:**
> It baffles me, really. I really want a simple speed dial. The top search item for "Firefox speed dial" is awesome and usable and intelligent and stable. I've tried, like, fifteen Chrome speed dial extensions, and not one of them simply worked without compromise. 

Similar results for touch scrolling. The top hit for Firefox works. The top hit for Chrome randomly makes text unselectable and occasionally breaks random page elements, including, recently, the page navigation links here at UF. Hilarity ensued.

I use Chrome, but damn, the extension base is not comparable.


There is also the problem that Google doesn't review extensions in their database. So there is no quality control. Mozilla reviews all extensions, including updates and don't approve them if they don't meet a minimum requirement. Sometimes extensions break with updates, but the review process filter a lot of problems.

Anyway, Opera's speed dial is superb. A really cool feature is the automatic arreangement of dials. There are also extensions that display some information on dials. For example, you can have a dial that is a feed reader.

I am currently using [FVD Speed Dial](https://addons.mozilla.org/en-US/firefox/addon/fvd-speed-dial/?src=search), which has a really nice set of features. However there are also others less known like [Super Start](https://addons.mozilla.org/en-US/firefox/addon/super-start/), in addition to [Speed Dial](https://addons.mozilla.org/en-US/firefox/addon/speed-dial/?src=search) and [Fast Dial](https://addons.mozilla.org/en-US/firefox/addon/fast-dial-5721/?src=search)

---

### Post by Bandit on 2012-04-27
> **Copper Bezel said:**
> Firefox is not integrated into Ubuntu in the way that Internet Explorer is integrated into Windows ..........

Like Copper Bezel siad, Firefox is just program and has nothing to do with the operating system. Anyone that claims otherwise should be placed on a ignore list and reported to the devs for stupidity. 

I will explain why for you so you have a better understand of Linux. Windows has Explorer (not internet explorer) as its built in file system browser and even the command prompt is a total emulation these days. Windows services (parts of the OS; i.e, video, sound, explorer..) work in tandum with each other. Much like slices of a Pizza, placed together they make a whole pizza. By their self they are just a slice. I like Pizza. Now Linux on the other hand is not built this way, at least not completely. First off the GUI Desktop Enviroments are optional. You dont even need them, most servers dont have them unless they are a VM server. But linux is built uppon layers of layers. A simple way to look at this is you have your linux kernel and ajoining modules, then your command line. Uppon that you have the Xserver, then on that you have your desktop enviroment. So what ever you have GUI wise in that Desktop has nothing to do with Linux booting up. There is much more detail. But thats a good quick example. So I hope this helps you out.

---

### Post by lovinglinux on 2012-04-28
> **Copper Bezel said:**
> It baffles me, really. I really want a simple speed dial. The top search item for "Firefox speed dial" is awesome and usable and intelligent and stable. I've tried, like, fifteen Chrome speed dial extensions, and not one of them simply worked without compromise. 

Similar results for touch scrolling. The top hit for Firefox works. The top hit for Chrome randomly makes text unselectable and occasionally breaks random page elements, including, recently, the page navigation links here at UF. Hilarity ensued.

I use Chrome, but damn, the extension base is not comparable.

Just found that FVD is available for Chrome as well. Despite minor limitations, like using local images as background, the quality of this add-on is pretty much the same. I strongly recommend you try it, either for Firefox or Chrome.

[https://chrome.google.com/webstore/detail/llaficoajjainaijghjlofdfmbjpebpa?utm_source=chrome-ntp-icon](https://chrome.google.com/webstore/detail/llaficoajjainaijghjlofdfmbjpebpa?utm_source=chrome-ntp-icon)

[https://addons.mozilla.org/en-US/firefox/addon/fvd-speed-dial/](https://addons.mozilla.org/en-US/firefox/addon/fvd-speed-dial/)

---

### Post by zombifier25 on 2012-04-28
> **lovinglinux said:**
> The only issue about removing Firefox and installing Chromium/Chrome is phylosofical. Even considering Chromium is open source, using a Mozilla product is still much better for the future of the Internet.
+infinity. The Mozilla team makes a lot of cool stuff that is to make a better web.

---

### Post by Sableyes on 2012-04-28
The only software thats hard to remove is Brasero and Banshee (both of which want to take the Desktop with it). Maybe Rythmbox in 12.04 (havent gotten to installing it yet).

---

### Post by vasa1 on 2012-04-28
> **keithpeter said:**
> Hello vasa1 and all

I'm posting this from chromium-browser having removed Firefox on my 'throwaway' Precise testing install (I'm going to do a clean install on Sunday when Canonical's servers have recovered). The commands I used were

```
keith@xeon:~$ sudo apt-get purge firefox
```

then

```
keith@xeon:~$ sudo apt-get install chromium-browser
```

I've just loaded Ubuntu Software Centre and searched for the pyroom full screen editor. I clicked on the More Info button, then I clicked on the Developer Website link, and Chromium loaded the pyroom developer's Web site in a new tab.

I loaded the System Settings app and clicked on Default Applications to find Chromium listed as my default Web browser.

Now, the only issue is that I purged Firefox *before* installing Chromium. If you are having problems, let us know what kinds...
Thanks for a very complete and thorough reply!

I'm sure it will be helpful to those who, for whatever reason, don't wish to use Firefox. For me, Firefox is the main browser and I have Seamonkey because of its excellent editor and newsreader and Chrome for my cloud activities.

---

