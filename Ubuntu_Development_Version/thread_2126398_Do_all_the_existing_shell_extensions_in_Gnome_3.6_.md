---
title: "Do all the existing shell extensions in Gnome 3.6 work in 3.8?"
date: 2013-03-17
forum: Ubuntu Development Version
---

### Post by Baldrick_NZ on 2013-03-17
I'm thinking about testing Gnome 3.8, but before I do, do all the existing shell extensions in 3.6 work in 3.8 as well, or do they all pretty much require upgrading?

Cheers.

---

### Post by VinDSL on 2013-03-17
Short answer is "No".

Some work, some don't. Some are flagged as requiring upgrading. And, there are some new extensions.

It's all over the place...  ;)

---

### Post by Baldrick_NZ on 2013-03-17
Thanks VinDSL,

So is there somewhere that I can check which extensions work, which don't and what the new ones are before upgrading?

---

### Post by VinDSL on 2013-03-17
> **Baldrick_NZ said:**
> Thanks VinDSL,

So is there somewhere that I can check which extensions work, which don't and what the new ones are before upgrading?
You're welcome.

I don't know of any place(s) to check which extensions work, or not.

---

### Post by Baldrick_NZ on 2013-03-17
Is it easily removed, if it doesn't work well for me, by purging the ppa and reverting to gnome 3.6?

---

### Post by VinDSL on 2013-03-17
> **Baldrick_NZ said:**
> Is it easily removed, if it doesn't work well for me, by purging the ppa and reverting to gnome 3.6?
You should be able to purge it, using ppa-purge, but no guarantees.  Cavsfan had ppa-purge fail, if I remember correctly.

Just make sure you know how to use ppa-purge before upgrading, and you should be able to downgrade to 3.6.

If you have a problem remembering which ppa you used to install Gnome 3.8, you can try...

```
history | grep add-apt-repository
```

---

### Post by Baldrick_NZ on 2013-03-17
Thanks again.

I think the answer has already been decided for me. I went to upgrade using synaptic, and it told me it could only download some of the files and would I like to continue? The answer, naturally, was no. :-)

I might wait until the official release, which is the end of the month, if I'm not mistaken?

Cheers.

---

### Post by jbicha on 2013-03-17
> **Baldrick_NZ said:**
> 
So is there somewhere that I can check which extensions work, which don't and what the new ones are before upgrading?

Except for the extensions included in the gnome-shell-extensions package, it doesn't look good yet.

[https://extensions.gnome.org/#shell_version=3.7.91](https://extensions.gnome.org/#shell_version=3.7.91) (Next week we'll see 3.7.92 too). It'll begin to look quite a bit better once 3.8 is released.

If you change that URL to 3.7.90, there's several more choices but it's a bit more complicated to install since the version won't match what you'll have installed.

---

### Post by cariboo on 2013-03-17
> **VinDSL said:**
> You should be able to purge it, using ppa-purge, but no guarantees.  Cavsfan had ppa-purge fail, if I remember correctly.

Just make sure you know how to use ppa-purge before upgrading, and you should be able to downgrade to 3.6.

If you have a problem remembering which ppa you used to install Gnome 3.8, you can try...

```
history | grep add-apt-repository
```

Thanks, seeing as my Ubuntu Gnome install is totally broken with the ppas added, that's a great way to check the exact names of them before running ppa-purge.

---

### Post by serdotlinecho on 2013-03-17
> **Baldrick_NZ said:**
> Is it easily removed, if it doesn't work well for me, by purging the ppa and reverting to gnome 3.6?

```
~&#10095; history | grep add-apt-repository
~&#10095; sudo add-apt-repository -r ppa:gnome3-team/gnome3
~&#10095; sudo apt-get update
```

Also you can check 3rd party ppa that you've added:

```
~&#10095; cat /etc/apt/sources.list.d/*
```

---

### Post by Baldrick_NZ on 2013-03-17
Thanks Jeremy,
So with regard to extensions, I'm prolly best to wait until 3.8 officially? I see there are only two extensions listed on the link you gave me.

---

### Post by VinDSL on 2013-03-20
> **Baldrick_NZ said:**
> I see there are only two extensions listed on the link you gave me.
This stuff changes all the time.  That's the nature of testing!  ;)

Here's the list, as of today (take with a grain of salt)...

```
vindsl@Zuul:~$ apt-cache policy gnome-shellgnome-shell:
  **[COLOR="#0000CD"]Installed: 3.7.92+git20130319.307004a4-0ubuntu1~13.04~ricotz0[/COLOR]**
  Candidate: 3.7.92+git20130319.307004a4-0ubuntu1~13.04~ricotz0
  Version table:
 *** 3.7.92+git20130319.307004a4-0ubuntu1~13.04~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
     3.7.92-0ubuntu1~raring1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main i386 Packages
     3.6.3.1-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ raring/universe i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/universe i386 Packages
     3.6.2-0ubuntu0.2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe i386 Packages
vindsl@Zuul:~$
```


Linkage:  [https://extensions.gnome.org/#shell_version=3.7.92](https://extensions.gnome.org/#shell_version=3.7.92) (20 extensions listed)

I'll check "TopIcons" after I submit this post -- that's always a good...um...  test.

**EDIT**

Nope!  Flagged as needing updating.

Tomorrow is a new day... :)

---

### Post by fyfe54 on 2013-03-21
I have used Y-PPA Manager to purge PPAs.  The process was painless (for me) but you should check into it for yourself.
It's  available here - ppa:webupd8team/y-ppa-manager

---

### Post by sgage on 2013-03-21
If you go to extensions.gnome.org, it presents you with the extensions that are explicitly labeled as being compatible with whatever version of Gnome Shell you are running. There are very few for 3.8. But...

If you have already installed them in 3.6, many of them can be made to work by editing the metada.json file that each extension has in its directory. It should be obvious what you need to do in that file. Restart the shell, and you should see your newly enabled extensions in gnome tweak tool.

I was able to get most of my favorite extensions to work in 3.8 this way (I actually entered "3.7.92" in the metadata.json file). A couple wouldn't work even with this hack, but most of them did...

If you installed extensions from the website, they will be in ~/.local/share/gnome-shell/extensions. If you installed from the extensions package, I don't know where they go - maybe something like /usr/share/gnome-shell/extensions? 

I've got Remove Accessibility, Disable Window Animations, Media Player Indicator, Places, Show Desktop, Recent Items, and Windowoverlay icons working.

But I'm sure they'll all be updated pretty soon.

---

### Post by converted on 2013-03-22
> **sgage said:**
> 

I was able to get most of my favorite extensions to work in 3.8 this way (I actually entered "3.7.92" in the metadata.json file). A couple wouldn't work even with this hack, but most of them did...


I just added the gnome-team ppa last night and did the upgrade -- I'm familiar with this workaround so I'll see if it resurrects a lot of my extensions.

A more general question though if you don't mind (I'm recently returning to Gnome, after a tour of Unity, Elementary OS, and others...) -- 

How are "normal" extension upgrades handled when they are installed from extensions.gnome.org?  Say in the future I'm using the release version of GNOME, with extensions that are intended to be compatible with it, no hacks or workarounds in place, and everything is great.  Then an extension author updates the published version of the extension on the website.  Do I need to uninstall and reinstall it via extensions.gnome.org to get the upgrade, or is there some other method available?

Same question I suppose for extensions that I'm unable to resurrect with the metadata.json workaround -- will they automagically start working when updated by the authors, or do I need to uninstall/reinstall?

I guess what I'm asking is whether there's a background process that checks whether my installed extensions have published upgrades and/or if such a check is triggered when I visit extensions.gnome.org...

Thanks!

---

### Post by sgage on 2013-03-22
> **converted said:**
> I just added the gnome-team ppa last night and did the upgrade -- I'm familiar with this workaround so I'll see if it resurrects a lot of my extensions.

A more general question though if you don't mind (I'm recently returning to Gnome, after a tour of Unity, Elementary OS, and others...) -- 

How are "normal" extension upgrades handled when they are installed from extensions.gnome.org?  Say in the future I'm using the release version of GNOME, with extensions that are intended to be compatible with it, no hacks or workarounds in place, and everything is great.  Then an extension author updates the published version of the extension on the website.  Do I need to uninstall and reinstall it via extensions.gnome.org to get the upgrade, or is there some other method available?

Same question I suppose for extensions that I'm unable to resurrect with the metadata.json workaround -- will they automagically start working when updated by the authors, or do I need to uninstall/reinstall?

I guess what I'm asking is whether there's a background process that checks whether my installed extensions have published upgrades and/or if such a check is triggered when I visit extensions.gnome.org...

Thanks!

I'm not really sure about the extensions that are installed via the official package - I would assume that package is versions that work with the official version of GS is for that release.

I think a better way to deal with extensions is to use the website. Click on the 'Installed extensions' link and you will see all the extensions you have installed, and which of those have updates available.

If you've tried the metadata trick and an extension still doesn't work, check the website and see if there's an update. I've had extensions labeled "obsolete" on the Installed Extensions page, but they'll show the update icon if one is available - just click on it, and sometimes all is well.

Sometimes there is more than one extension that does pretty much the same thing - if you can't make one of your extensions work that has a feature important to you, you can search all the extensions for one that might. That's what I did to get a working 'overlay icons' and 'music indicator' for 3.8.

As far as I know, there is no way to automagically keep all extensions updated. I think I read somewhere that this is something the Gnome Team is working on - perhaps someone else knows more...

---

### Post by converted on 2013-03-22
Great, thanks for the info!  I've been intending to install via the site, not by package anyway, so this is perfect.  I didn't know about the "Obsolete" label on the Installed page at the site, and that pretty much gets me what I need (or close enough to it).

I appreciate the info!

---

### Post by VinDSL on 2013-04-03
Some interesting shell extensions are becoming available for GS 3.8

Check this out: [Dash to Dock]("https://extensions.gnome.org/extension/307/dash-to-dock/") (Unity Dash Wannabe)  :D


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-3-apr-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-apr-2013-1.png")[/INDENT]


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-3-apr-2013-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-apr-2013-2.png")[/INDENT]

---

### Post by zika on 2013-04-04
Any idea when HideTopBar will be available for 3.8?

---

### Post by VinDSL on 2013-04-04
> **zika said:**
> Any idea when HideTopBar will be available for 3.8?
I have no idea.  :(

I keep waiting for TopIcons to get updated.

Just a matter of time, I suppose, now that 3.8 has been released.

---

### Post by buzzingrobot on 2013-04-04
Tweak Tool will indicate which extensions are not working. A mouseover should generate a tiny explanation. "Outdated" is used to indicate versioning problems.  

An identical capability is available at extensions.gnome.org.

Correcting the Gnome Shell version in metadata.json has been hit or miss for me.  It seems to be important to be precise.  I.e., if you are running 3.8.0.1, use that, not simply "3.8".

Unless an extension is available in, and installed from, a repo, I'm pretty sure that updates need to be installed manually. I usually disable the extension, then go to extensions.gnome.org, and reinstall it.  If that doesn't work, I delete the extension manually and try again.   This is an area that definitely needs improvement.  Gnome seems to like having the extensions around but also seems reluctant to fully embrace and take responsibility for them.

---

### Post by buzzingrobot on 2013-04-04
> **VinDSL said:**
> Dash to Dock[/URL] (Unity Dash Wannabe)  :D


Dash To Dock is superb and really ought to be tried by anyone who's put off by Gnome's inclusion of the Launcher in the Overview. I should say it does not default to the vertical expansion shown in your image, but can be run as a traditional dock. Combined with an extension to turn off the hot corner, it's a very good alternative. It's been around for some time and its developer deserves kudos for staying with it and delivering an extension that, I think, fundamentally improves Gnome Shell.

---

### Post by sgage on 2013-04-04
> **buzzingrobot said:**
> Tweak Tool will indicate which extensions are not working. A mouseover should generate a tiny explanation. "Outdated" is used to indicate versioning problems.  

An identical capability is available at extensions.gnome.org.

Correcting the Gnome Shell version in metadata.json has been hit or miss for me.  It seems to be important to be precise.  I.e., if you are running 3.8.0.1, use that, not simply "3.8".

Unless an extension is available in, and installed from, a repo, I'm pretty sure that updates need to be installed manually. I usually disable the extension, then go to extensions.gnome.org, and reinstall it.  If that doesn't work, I delete the extension manually and try again.   This is an area that definitely needs improvement.  Gnome seems to like having the extensions around but also seems reluctant to fully embrace and take responsibility for them.

I'm using GS 3.8.0.1, and in my metadata tweaking, simply use 3.8, and it works. But during the 3.7.x dev cycle, I found I had to be exact, e.g., 3.7.92 or whatever.

I agree that the extension handling mechanism is chaotic. I think if you just stick with the extensions website, you're better off. You can see your installed extensions, and it will tell you if they have updates, which you can apply with a click.

---

### Post by ronacc on 2013-04-04
if you install gnome-tweak-tool you can actvate the installed extensions , it gives you a list . If you go to the bottom and click on "get more extension" it will take you to  [https://extensions.gnome.org/](https://extensions.gnome.org/)  and show you what other extensions will work with the gnome-shell version you have installed ( I saw 4 pages of them ) I installed some from there and they work .

---

