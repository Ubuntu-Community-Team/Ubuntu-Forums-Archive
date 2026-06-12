---
title: "Installing Firefox 3.5 - NOT shiretoko"
date: 2009-07-05
forum: The Cafe
---

### Post by scouser73 on 2009-07-05
I have installed Firefox 3.5 on Ubuntu 9.04 using the instructions set out on this website; [http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/]("http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/")

It work's perfectly, so feel free to give it a go. as Firefox 3.5 is faster than previous with new enhancements.

---

### Post by philinux on 2009-07-05
Interesting link.

---

### Post by cmost on 2009-07-05
I don't understand what the big brouhaha over the Shiretoko branding of Firefox 3.5 as available from some repos.  A rose by any other name is still a rose!  I've been using Firefox-3.5 in the guise of Shiretoko for a few days now and it's working flawlessly.  Great work Mozilla!  :p

---

### Post by sirjoebob on 2009-07-05
3.5 is old news to me. I tired of waiting for Ubuntu repos to adopt it so i added the firefox nightly build repo and I am on 3.6a lol.
:guitar:

---

### Post by lovinglinux on 2009-07-05
I personally prefer the one below, because is simpler, it installs in the /opt directory and automatically update the path for the Firefox launcher:

> **lovinglinux said:**
> 

[size="2"][color=#CC0000]**1 - Manual installation of fresh final releases from Mozilla**[/color][/size]

For manual installation of **fresh released final versions** of Firefox, you can download the current Mozilla release version from [Get Firefox site](http://www.mozilla.com/en-US/firefox/upgrade.html?from=getfirefox), saving it on your home directory, then run the commands below:

```
cp -R ~/.mozilla ~/.mozilla.backup
sudo tar -jxvf firefox-*.tar.bz2 -C /opt
rm firefox-*.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox 
```

> **[color=#CC0000]Note:[/color]** I recommend reading the original article at [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox), specially if you have installed previous versions of Firefox in the /opt directory.


---

### Post by malel on 2009-07-05
Thanks folks. It worked for me. What gives with the fonts though? It does look horrible on my screen and the fonts appear very 'thin'. Can we do anything about that. My screen resolution is set at 1280 x 960.

---

### Post by lovinglinux on 2009-07-05
> **malel said:**
> Thanks folks. It worked for me. What gives with the fonts though? It does look horrible on my screen and the fonts appear very 'thin'. Can we do anything about that. My screen resolution is set at 1280 x 960.

Solution at [http://ubuntuforums.org/showthread.php?t=1200992](http://ubuntuforums.org/showthread.php?t=1200992)

I didn't tried tho.

---

### Post by reyfer on 2009-07-06
I'm sorry for my ignorance here, but....what is wrong with just downloading the .tar.bz2 file from Mozilla and extracting the firefox folder? That's what I did on my Kubuntu 9.04 system

---

### Post by X-BANE on 2009-07-06
I'll wait for Canonical to officially update it. I've tried the vanilla 3.5, and was impressed.

---

### Post by aysiu on 2009-07-06
> **reyfer said:**
> I'm sorry for my ignorance here, but....what is wrong with just downloading the .tar.bz2 file from Mozilla and extracting the firefox folder? That's what I did on my Kubuntu 9.04 system
That's actually what the link in the original post does.

As for what's "wrong" with it, it doesn't link Firefox up to plugins (for multimedia and Flash), and it doesn't link the launcher to the *firefox* command.

Some people don't have a problem with that, but I do.

That's why I created a "single command" install that actually sets up both those things (a link to plugins and a link to the *firefox* command):
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by X-BANE on 2009-07-06
> **aysiu said:**
> That's actually what the link in the original post does.

As for what's "wrong" with it, it doesn't link Firefox up to plugins (for multimedia and Flash), and it doesn't link the launcher to the *firefox* command.

Some people don't have a problem with that, but I do.

That's why I created a "single command" install that actually sets up both those things (a link to plugins and a link to the *firefox* command):
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

How do you mean "it doesn't link Firefox up to plugins (for multimedia and Flash)"?

The 3.5 I downloaded from Mozilla worked perfectly with flash.

---

### Post by lovinglinux on 2009-07-06
> **aysiu said:**
> That's why I created a "single command" install that actually sets up both those things (a link to plugins and a link to the *firefox* command):
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

BTW, I hope you don't mind I'm putting your instructions on my thread. I have changed it a little bit a few moments ago, putting the link to your site at the top instead of the bottom of the instructions. My intention is not to take credit of your awesome work, but to provide the most common methods on a single place. I'm actually compiling Firefox myself and due to the performance boost I will always do it from now on, but I'm recommending your method because it is simple and efficient. It just works!

Thank you!

---

### Post by tjeremiah on 2009-07-06
> **aysiu said:**
> That's actually what the link in the original post does.

As for what's "wrong" with it, it doesn't link Firefox up to plugins (for multimedia and Flash), and it doesn't link the launcher to the *firefox* command.

Some people don't have a problem with that, but I do.

That's why I created a "single command" install that actually sets up both those things (a link to plugins and a link to the *firefox* command):
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Thanks!!! ):P

EDIT : I did what you said and the official FF doesnt open..

---

### Post by aysiu on 2009-07-06
> **X-BANE said:**
> How do you mean "it doesn't link Firefox up to plugins (for multimedia and Flash)"?

The 3.5 I downloaded from Mozilla worked perfectly with flash. It's not linked up to the plugins folder that the system manages. If you've installed Flash locally for only your user, then Flash will work, but other plugins won't (Totem, Java, VLC, whatever).

When you extract the .tar.bz2 the plugins folder is completely empty.

Can you post the output of these two commands? ```
ls ~/.mozilla/plugins/
ls /usr/lib/xulrunner-addons/plugins/
```

> **lovinglinux said:**
> BTW, I hope you don't mind I'm putting your instructions on my thread. Not a problem. I didn't even make up those instructions! They used to be on the Wiki in a wholly unpresentable and complicated form. I just simplified them and added in proper explanation.

---

### Post by lovinglinux on 2009-07-06
> **aysiu said:**
> Not a problem. I didn't even make up those instructions! They used to be on the Wiki in a wholly unpresentable and complicated form. I just simplified them and added in proper explanation.

Thank you. Is definitely easy to understand and use.

---

### Post by tjeremiah on 2009-07-06
I did it and FF wont launch..

---

### Post by X-BANE on 2009-07-06
> **aysiu said:**
> It's not linked up to the plugins folder that the system manages. If you've installed Flash locally for only your user, then Flash will work, but other plugins won't (Totem, Java, VLC, whatever).

When you extract the .tar.bz2 the plugins folder is completely empty.

I've just tried again with a fresh 3.5 vanilla download, and Totem worked.

---

### Post by aysiu on 2009-07-06
> **X-BANE said:**
> I've just tried again with a fresh 3.5 vanilla download, and Totem worked.
Well, let me make sure I understand what you're doing exactly.

So you download the .tar.bz2 to your desktop, right-click it, select Extract here, and then go into /home/*username*/Desktop/firefox and launch the firefox icon in there?

You don't do anything else?

Can you, as I asked before, post the output of those two commands?

---

### Post by X-BANE on 2009-07-06
> **aysiu said:**
> Well, let me make sure I understand what you're doing exactly.

So you download the .tar.bz2 to your desktop, right-click it, select Extract here, and then go into /home/*username*/Desktop/firefox and launch the firefox icon in there?

You don't do anything else?

Can you, as I asked before, post the output of those two commands?

I launch it by extracting it to the desktop and launching /home/acro/Desktop/firefox from within the extracted desktop Firefox folder.

---

### Post by aysiu on 2009-07-06
> **X-BANE said:**
> I launch it by extracting it to the desktop and launching /home/acro/Desktop/firefox from within the extracted desktop Firefox folder.
Okay. Can you post the output of those two commands?

---

### Post by X-BANE on 2009-07-06
> **aysiu said:**
> Okay. Can you post the output of those two commands?

Patience, patience, I'm just doing it :P

---

### Post by lovinglinux on 2009-07-06
> **tjeremiah said:**
> I did it and FF wont launch..

Have you tried other Firefox 3.5 methods before this one?

1 - Run the command below to launch the Profile Manager with Firefox 3.0.11

```
firefox-3.0 -P
```

2 - Create a new profile with the Profile Manager. Then close Firefox 3.0.11.

3 - Start Firefox 3.5 with this command:

```
firefox -P
```

Select the new profile and check if it works. If yes, then you might have a corrupted file in your old profile.

Also check the first item of the Troubleshooting section of the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by X-BANE on 2009-07-06
Terminal readout for commands;

acro@acro-desktop:~$ ls ~/.mozilla/plugins/
ls: cannot access /home/acro/.mozilla/plugins/: No such file or directory

acro@acro-desktop:~$ ls /usr/lib/xulrunner-addons/plugins/
flashplugin-alternative.so             libtotem-gmp-plugin.so
libjavaplugin.so                       libtotem-mully-plugin.so
libnullplugin.so                       libtotem-narrowspace-plugin.so
librhythmbox-itms-detection-plugin.so  libunixprintplugin.so
libtotem-cone-plugin.so         libmai-lrd.so
acro@acro-desktop:~$

---

### Post by aysiu on 2009-07-06
Hm. That's weird.

What about this one? ```
ls -l /home/acro/Desktop/firefox/plugins
```

---

### Post by X-BANE on 2009-07-06
acro@acro-desktop:~$ ls -l /home/acro/Desktop/firefox/plugins
total 16
-rwxr-xr-x 1 acro acro 15824 2009-06-24 10:17 libnullplugin.so

---

### Post by aysiu on 2009-07-06
I'm baffled. This is an anamoly I can't explain. Somehow your Firefox knows where to look for plugins without the plugins actually being linked. This isn't the normal behavior.

---

### Post by X-BANE on 2009-07-06
> **aysiu said:**
> I'm baffled. This is an anamoly I can't explain. Somehow your Firefox knows where to look for plugins without the plugins actually being linked. This isn't the normal behavior.

Maybe Mozilla have updated it to do this?

---

### Post by stwschool on 2009-07-06
Could be that the version actually running isn't the one downloaded? Might be worth a check of help -> About to see what version number is running.

---

### Post by X-BANE on 2009-07-06
No it was definitely 3.5 running, I checked Help>About Mozilla Firefox.

---

### Post by aysiu on 2009-07-06
I guess it must be something new, as I just tried it out myself.

Firefox must come already looking for plugins in the /usr/lib/mozilla/plugins folder, as those are the only plugins it appears to see without an explicit symlink (in my case, VLC and Flash, and that's it).

If I do an explicit symlink to the /usr/lib/xulrunner-addons/plugins directory, then it gets VLC, Flash, Rhythmbox, and printer plugins as well.

I'm still going to recommend people do an explicit symlink instead of relying on Firefox to magically discover existing plugins. Ubuntu doesn't always dump plugins into the /usr/lib/mozilla directory, and Mozilla may not always have Firefox magically detect existing plugins in that directory.

---

### Post by X-BANE on 2009-07-06
> **aysiu said:**
> I guess it must be something new, as I just tried it out myself.

Firefox must come already looking for plugins in the /usr/lib/mozilla/plugins folder, as those are the only plugins it appears to see without an explicit symlink (in my case, VLC and Flash, and that's it).

If I do an explicit symlink to the /usr/lib/xulrunner-addons/plugins directory, then it gets VLC, Flash, Rhythmbox, and printer plugins as well.

I'm still going to recommend people do an explicit symlink instead of relying on Firefox to magically discover existing plugins. Ubuntu doesn't always dump plugins into the /usr/lib/mozilla directory, and Mozilla may not always have Firefox magically detect existing plugins in that directory.

You have to love Firefox! ;)

---

### Post by drumsticks on 2009-07-06
I've followed the instructions but can't get the plugins to work either. Here's what I get at the command line:

```
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/libnullplugin.so [/usr/lib/xulrunner-addons/plugins/libnullplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/libunixprintplugin.so [/usr/lib/xulrunner-addons/plugins/libunixprintplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-cone-plugin.so [/usr/lib/totem/gstreamer/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so [/usr/lib/totem/gstreamer/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-mully-plugin.so [/usr/lib/totem/gstreamer/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so [/usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-installer/npwrapper.libflashplayer.so [/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-cone-plugin.so [/usr/lib/totem/gstreamer/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so [/usr/lib/totem/gstreamer/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-mully-plugin.so [/usr/lib/totem/gstreamer/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so [/usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-installer/npwrapper.libflashplayer.so [/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]

```

I'm running 64-bit Jaunty.

EDIT: Firefox-3.5 does run, but fails to load plugins.

---

### Post by monsterstack on 2009-07-06
aysiu, your howto gives a single command for people to run, but it assumes they've already downloaded it and there's a separate command to run if you've never installed Firefox at all! That's far too much for lazy people to accomplish.

```
if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi; wget -c 'http://download.mozilla.org/?product=firefox-3.5&os=linux&lang=en-US' && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

All in one!

---

### Post by HavocXphere on 2009-07-06
Shouldn't these scenarios be covered by backports? Or am I misunderstanding the function of backports?

---

### Post by Johnsie on 2009-07-06
> 
cp -R ~/.mozilla ~/.mozilla.backup
sudo tar -jxvf firefox-*.tar.bz2 -C /opt
rm firefox-*.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox



Yeah, because granny is going to understand that! I much prefer the Windows method for updating firefox and I'm sure the average joe would too. If Linux is to become mainstream then people need to realise that not everyone understands this kind of stuff. Software designers need to stop thinking like experts and put themselves in the shoes of a beginner.

---

### Post by mister_k81 on 2009-07-06
Personally, I just downloaded, installed and ran this script to install Firefox 3.5, and it worked like a charm for me under Jaunty: 

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

The only two minor issues I have with Firefox 3.5 so far are: 

1. The Ubuntu "drumbeat" warning sound plays when I close a window with more than one tab open in it, or if I just close Firefox all together. It gets a little bit grating to me, does anyone know how to disable it?

2: The  Dust theme colours look a bit odd in FF3.5 over the Ubuntu version of FF 3.0.11. For example; some of the text in the address bar drop down menu is blue instead of light grey, Which makes it hard to read since the blue text is on a dark background.  It's not really a big deal or anything, though.

---

### Post by aysiu on 2009-07-06
> **Johnsie said:**
> Yeah, because granny is going to understand that! I much prefer the Windows method for updating firefox and I'm sure the average joe would too. If Linux is to become mainstream then people need to realise that not everyone understands this kind of stuff. Software designers need to stop thinking like experts and put themselves in the shoes of a beginner. Why does "granny" need to understand that? I don't know any "grannies" (I'm assuming you're using the stereotype of old people being computer illiterate to stand in for all computer illiterates) who need to have Firefox 3.5 installed before October.

Ubuntu is great for "grannies," because "grannies" do not need the newest software versions immediately. They can wait six months to have everything updated automatically.

It's only Windows power users or ex-Windows power users who need the latest Firefox *right now*.

> **monsterstack said:**
> aysiu, your howto gives a single command for people to run, but it assumes they've already downloaded it and there's a separate command to run if you've never installed Firefox at all! That's far too much for lazy people to accomplish.

```
if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi; wget -c 'http://download.mozilla.org/?product=firefox-3.5&os=linux&lang=en-US' && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

All in one! Thanks for the tip. I like that little if/then in there. I'm going to leave out the *wget*, though, as I want people to be able to choose whatever locale they want (not necessarily English/US).

---

### Post by koleoptero on 2009-07-06
> **cmost said:**
> i don't understand what the big brouhaha over the shiretoko branding of firefox 3.5 as available from some repos.  A rose by any other name is still a rose!  I've been using firefox-3.5 in the guise of shiretoko for a few days now and it's working flawlessly.  Great work mozilla!  :p

+10.001

---

### Post by mamamia88 on 2009-07-06
ok i did it but is it safe to remove the old firefox or will i lose my profile?

---

### Post by andrewabc on 2009-07-06
> **cmost said:**
> I don't understand what the big brouhaha over the Shiretoko branding of Firefox 3.5 as available from some repos.  A rose by any other name is still a rose!  I've been using Firefox-3.5 in the guise of Shiretoko for a few days now and it's working flawlessly.  Great work Mozilla!  :p

I'm pretty sure the problem is that the 9.04 repository is still using beta 4. Why hasn't it been updated to final version? It's using a 3 month old version!

[http://packages.ubuntu.com/jaunty/firefox-3.5](http://packages.ubuntu.com/jaunty/firefox-3.5)
[http://packages.ubuntu.com/karmic/firefox-3.5](http://packages.ubuntu.com/karmic/firefox-3.5)

So people using jaunty, have no official way to use 3.5. They have to add a new repository or download from mozilla. Ubuntu official repository has not been updated in 3 months. And I see no reason why it has not been updated to final version when they released final version for karmic.

I'm not saying 3.0.x should be upgraded to 3.5, I'm talking about the 3.5 that was always in jaunty repos. It has been updated for karmic, why not update the beta4 to final release in jaunty?

---

### Post by lovinglinux on 2009-07-06
> **mamamia88 said:**
> ok i did it but is it safe to remove the old firefox or will i lose my profile?

You shouldn't remove Firefox 3.0 because its part of the ubuntu-desktop. 

The profiles location depend on how you installed Firefox 3.5. If you are using the one from the repositories, then it copies your profiles automatically from ~/.mozilla/firefox to ~/.mozilla/firefox-3.5. If you installed manually, then it shares the same profile with the 3.0 version.

---

### Post by oobuntoo on 2009-07-06
> **cmost said:**
> I don't understand what the big brouhaha over the Shiretoko branding of Firefox 3.5 as available from some repos.  A rose by any other name is still a rose!  I've been using Firefox-3.5 in the guise of Shiretoko for a few days now and it's working flawlessly.  Great work Mozilla!  :p

It's like calling Michael Jackson, Jimmy Jackson. He may sounds the same, but it's weird.:lol:

It's the reason I've not upgraded yet.

---

### Post by lovinglinux on 2009-07-06
> **oobuntoo said:**
> It's like calling Michael Jackson, Jimmy Jackson. He may sounds the same, but it's weird.:lol:

It's the reason I've not upgraded yet.

:lolflag:

You can manually install the official version, with Firefox brand. Check the method 1 from the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by slogum on 2009-07-17
> **monsterstack said:**
> aysiu, your howto gives a single command for people to run, but it assumes they've already downloaded it and there's a separate command to run if you've never installed Firefox at all! That's far too much for lazy people to accomplish.

```
if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi; wget -c 'http://download.mozilla.org/?product=firefox-3.5&os=linux&lang=en-US' && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

All in one!

I installed it with your script.

How can I uninstall?

---

### Post by aysiu on 2009-07-17
> **slogum said:**
> I installed it with your script.

How can I uninstall?
This should help:
[http://psychocats.net/ubuntu/firefox#remove](http://psychocats.net/ubuntu/firefox#remove)

---

### Post by windows-killer on 2009-07-17
its too difficult to install firefox... can someone create a deb package? How about upload it in the repos?

---

### Post by aysiu on 2009-07-17
> **windows-killer said:**
> its too difficult to install firefox Actually, it's not at all.

Just follow these instructions (i.e., copy and paste *with your mouse* **one** command):
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by slogum on 2009-07-18
**What fixed the sound-issues for me**

After installing firefox 3.5 my flash player had no sound. I had sound in ff 3.0 but not in 3.5. I'm using ALSA.

From package manager I have the following installed:

flashplugin-nonfree-extrasound
adobe-flashplugin
flashplugin-installer
flashplugin-nonfree

After a reboot, problem solved. Don't know exactly wich packet that did the trick, but as long as I have sound I really don't care :)

---

### Post by Eisenwinter on 2009-07-18
Ubuntu never ceases to amaze.

All these commands just to upgrade Firefox... in Arch I just run my daily pacman -Syu and it updates it.

And to think people label Ubuntu as an easy distro, what a paradox.

---

### Post by aysiu on 2009-07-18
> **Eisenwinter said:**
> Ubuntu never ceases to amaze.

All these commands just to upgrade Firefox... in Arch I just run my daily pacman -Syu and it updates it.

And to think people label Ubuntu as an easy distro, what a paradox.
It's not a paradox at all. It's a totally different release model for a different target audience.

Arch is a rolling release distro, so all software gets upgraded immediately. That's great for power users.

Ubuntu is more for the average users, the ones who have no idea Firefox 3.5 just came out (i.e., most computer users). Most people have no problems updating their software only once every six months.

---

### Post by Grant A. on 2009-07-18
> **aysiu said:**
> It's not a paradox at all. It's a totally different release model for a different target audience.

Arch is a rolling release distro, so all software gets upgraded immediately. That's great for power users.

Ubuntu is more for the average users, the ones who have no idea Firefox 3.5 just came out (i.e., most computer users). Most people have no problems updating their software only once every six months.

A rolling release also tends to have stability problems. Of course, Ubuntu has had its fair share of problems, which I'm sure would've been fixed on-the-spot if it was a rolling release.

Instead of Shiretoko, I just use the unbranded version of Firefox 3.5.

```

sudo apt-get install abrowser-3.5

```

---

### Post by Pendaws on 2009-07-19
I have tried unsuccessfully 3 times to download and install this update and it WON'T work. I am new to Ubuntu and the whole Linux thing but surely this should work?

Did the download to the home directory and ran the single command line but NOTHING happened. All I did the first time was to make the quick start icon not work. I used the single command line install and at least it has given me the links back but ONLY to version 3.011. So, PLEASE tell me WHAT I did wrong?

---

### Post by Pendaws on 2009-07-19
Why does this stuff NEED to be so hard to do. I now have Firefox 3.5 installed but I can't open it. I have a listing in applications/internet/ abrowser and that is what I am using now. I rebooted and this is what now is happening.

When I open the icon for FF it immediately says it can't connect.

---

