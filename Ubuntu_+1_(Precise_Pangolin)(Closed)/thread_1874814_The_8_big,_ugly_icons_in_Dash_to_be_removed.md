---
title: "The 8 big, ugly icons in Dash to be removed"
date: 2011-11-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mc4man on 2011-11-03
The top 4 are certainly worthless, I guess a few users may be using the bottom 4 as launchers, no big loss there either

tracker
[https://bugs.launchpad.net/unity/+bug/885738](https://bugs.launchpad.net/unity/+bug/885738)

---

### Post by effenberg0x0 on 2011-11-03
That I think it's a very valid customization request... I'd like to replace all of them for things I actually use. I haven't looked into it yet though. I guess they are hardcoded?

**EDIT:** Yes, it is, I just found it.
**EDIT2:** God, it actually 100x more time to compile Unity than to change it.

---

### Post by effenberg0x0 on 2011-11-03
Customizing the Dash Home is totally doable. See screenshot: I removed all icons. How useful lol :)

[ATTACH]206262[/ATTACH]

But seriously, it's just cause I'm really overloaded here. IMHO, it should load a ".file" from $HOME of the logged in $USER, with his prefs for the Dash Home, which is easy to do in that piece of code: [Name]Icon/File.  I'll try to see if I find the time to do it by monday, when I was reserving some time to play with the greeter anyway. Then someone that is into Python can put that into the settings window, like "Dash Home Setup", to avoid people from having to manually edit the text file for changing these settings. 

If I find the time to make it, I'll propose a merge, but keep in mind I'm not a developer for Ubuntu, so no idea about their coding style, and stuff to get your merge accepted, etc. 

As Icehouse lead-singer used to say quite frequently: No promises.

---

### Post by effenberg0x0 on 2011-11-04
I'm not sure what to do with icon sizes vs. number of icons. 

Normally you may have up to 20 icons (see in "Installed Apps") for example. WHen the filter is opened in the right you have 12 icons. But Home uses 8 larger icons. Either I keep up-to-8 large icons or up-to-20 smaller icons, but things may look out of alignment if the user adds fewer icons, in both cases. (there's no way I can see to align center, middle or right. It's left-to-right with fixed spacing by default).

Suggestions? 

Also, to reproduce the structure that was hardcoded, I'm going with $HOME/.dash_home in the following format:
BOF
[Name of Icon]
"path to Icon"
"path to Program 'args'"
<space>
[Name of Icon]
"path to Icon"
"path to Program 'args'"
...
EOF

---

### Post by ikt on 2011-11-04
> **mc4man said:**
> The top 4 are certainly worthless, I guess a few users may be using the bottom 4 as launchers, no big loss there either

tracker
[https://bugs.launchpad.net/unity/+bug/885738](https://bugs.launchpad.net/unity/+bug/885738)

Old news;

[http://www.omgubuntu.co.uk/2011/11/user-testing-of-unity-reveals-some-surprising-results/](http://www.omgubuntu.co.uk/2011/11/user-testing-of-unity-reveals-some-surprising-results/)

> The good news is that the main “Dash” display (the one with 8 icons on) is to be retired for Precise, although the search bar will remain.

---

### Post by mc4man on 2011-11-04
> **ikt said:**
> Old news;

[http://www.omgubuntu.co.uk/2011/11/user-testing-of-unity-reveals-some-surprising-results/](http://www.omgubuntu.co.uk/2011/11/user-testing-of-unity-reveals-some-surprising-results/)

Old or new  news doesn't concern me , was only interested in the proposed user options

---

### Post by effenberg0x0 on 2011-11-04
> **mc4man said:**
> Old or new  news doesn't concern me , was only interested in the proposed user options

I agree. In my opinion, the only point in keeping the dash home there is if it's 8,12 or 20 icons are configurable via a editable dot file in each user $HOME (which can later be easily edited by users using a Python interface in settings). 

I can see use to that as companies might want to add their most used applications, like ERP/CRM software, link to intranet portal, etc in there for employees easier/faster access with no need to search, scroll, etc. 

I can easily think of the main 8,12, or 20 apps I use the most during the day and it would be nice to have them there. It would be an extension of what the launcher currently does. A second tier of preferred apps. That's the only value I see in keeping it.

But those hardcoded options (media, photos, etc) serve me no purpose. 

In other words, some degree of configuration that would allow to:
IF $HOME/.dash_config exists { 
  LOAD $HOME/.dash_config
} ELSE {
  IF set to load defaults { load defaults } (better defaults I hope)
  ELSE { Don't load home at all. }
}

---

### Post by effenberg0x0 on 2011-11-05
Hey, I have changed Unity to look at each users $HOME for .dash_home. It could be any file of course. If .dash_home is not there, it loads the defaults. See screenshot. Look at Gedit to see the syntax. Also, you can change ~/.dash_home in real time, no need to login/out.

 [ATTACH]206384[/ATTACH]

I really don't know launchpad procedures to upload to my account, pack to deb only relevant (changed) stuff, etc. And it's 3am, can't read anymore. But I'll do it soon if you guys wanna give it a try.

Regards,
Effenberg

---

### Post by mc4man on 2011-11-05
Or if you've the chance attach a .diff of your edit(s), 

May have to be revisted when the change(s) in dash take place, whether in unity-4.X or 5.X

---

### Post by philinux on 2011-11-05
> **mc4man said:**
> The top 4 are certainly worthless, I guess a few users may be using the bottom 4 as launchers, no big loss there either

tracker
[https://bugs.launchpad.net/unity/+bug/885738](https://bugs.launchpad.net/unity/+bug/885738)

Agreed.
I've not really played with these big 8 before but view photos just opens shotwell. Not an app I like at all. Seems like it's the new user focus to the OS. I dislike any photo app that wants to import anything lol.

---

### Post by effenberg0x0 on 2011-11-05
> **philinux said:**
> Agreed.
I've not really played with these big 8 before but view photos just opens shotwell. Not an app I like at all. Seems like it's the new user focus to the OS. I dislike any photo app that wants to import anything lol.

Hi Phil, the problem is here:

```
  //In case the GConf key is invalid (e.g. when an app was uninstalled), we
  //rely on a fallback "whitelist" mechanism instead of showing nothing at all
  _browser_alternatives.push_back("firefox");
  _browser_alternatives.push_back("chromium-browser");
  _browser_alternatives.push_back("epiphany-browser");
  _browser_alternatives.push_back("midori");

  _photo_alternatives.push_back("shotwell");
  _photo_alternatives.push_back("f-spot");
  _photo_alternatives.push_back("gthumb");
  _photo_alternatives.push_back("gwenview");
  _photo_alternatives.push_back("eog");

  _email_alternatives.push_back("evolution");
  _email_alternatives.push_back("thunderbird");
  _email_alternatives.push_back("claws-mail");
  _email_alternatives.push_back("kmail");

  _music_alternatives.push_back("banshee-1");
  _music_alternatives.push_back("rhythmbox");
  _music_alternatives.push_back("totem");
  _music_alternatives.push_back("vlc");
```These options for default Dash Home creation are harcoded. And, of course, not only this decision is questionable but so is why some apps get preference over others, in case user has a bunch of them available. Who gets to say one is preferable over other for all users? That can't work and should be avoided.

Regards,
Effenberg

---

### Post by jbicha on 2011-11-05
Shotwell was hardcoded; the other apps (browser, email, and music) were not. It's actually a bit difficult to specify a default photo management app (like Shotwell) and not just a default image viewer (which still is eog).

---

### Post by effenberg0x0 on 2011-11-05
> **jbicha said:**
> Shotwell was hardcoded; the other apps (browser, email, and music) were not. It's actually a bit difficult to specify a default photo management app (like Shotwell) and not just a default image viewer (which still is eog).


```

  CreateShortcutFromMime("x-scheme-handler/http", _("Browse the Web"), **_browser_alternatives**); 

  CreateShortcutFromExec("shotwell", _("View Photos"), **_photo_alternatives**);

  CreateShortcutFromMime("x-scheme-handler/mailto", _("Check Email"), **_email_alternatives**);

  CreateShortcutFromMime("audio/x-vorbis+ogg", _("Listen to Music"), **_music_alternatives**);
``````

  _browser_alternatives.push_back("firefox");
  _browser_alternatives.push_back("chromium-browser");
  _browser_alternatives.push_back("epiphany-browser");
  _browser_alternatives.push_back("midori");

  _photo_alternatives.push_back("shotwell");
  _photo_alternatives.push_back("f-spot");
  _photo_alternatives.push_back("gthumb");
  _photo_alternatives.push_back("gwenview");
  _photo_alternatives.push_back("eog");

  _email_alternatives.push_back("evolution");
  _email_alternatives.push_back("thunderbird");
  _email_alternatives.push_back("claws-mail");
  _email_alternatives.push_back("kmail");

  _music_alternatives.push_back("banshee-1");
  _music_alternatives.push_back("rhythmbox");
  _music_alternatives.push_back("totem");
  _music_alternatives.push_back("vlc");
```Hi jbicha, these are the options considered by the CreateShortCutFrom* functions when dash home shortcuts are created. I have just started studying the code a couple days ago, so I'm still learning from it. They seem pretty harcoded for me, since the end-user can't choose which app to use, add/remove/change from this list or manually set the dash home shortcuts (using the default - not mine - code). So I couldn't understand your point of view. Can you help? 

Thanks,
E ffenberg

---

### Post by jbicha on 2011-11-05
The first code snippet uses the mimetype to set the default browser, mail, and music player. The user can change these easily by using the System Info panel in System Settings. Compare with the System Settings [code]("http://git.gnome.org/browse/gnome-control-center/tree/panels/info/cc-info-panel.c#n956").

The second snippet is a fallback in case the first doesn't work. By the way you can make f-spot default by uninstalling shotwell.

---

### Post by effenberg0x0 on 2011-11-05
> **jbicha said:**
> The first code snippet uses the mimetype to set the default browser, mail, and music player. The user can change these easily by using the System Info panel in System Settings. Compare with the System Settings [code]("http://git.gnome.org/browse/gnome-control-center/tree/panels/info/cc-info-panel.c#n956").

The second snippet is a fallback in case the first doesn't work. By the way you can make f-spot default by uninstalling shotwell.

Got it, the options are there mostly as a fallback. Thanks!

Effenberg

---

### Post by effenberg0x0 on 2011-11-06
New tests: Now supporting up to 15 dynamically set icons, instead of 8, still sized and spaced differently from what they are at the applications lenses, to maintain the idea that shortcuts should be visually differentiated. But it looks better and works better for many purposes. 

[ATTACH]206483[/ATTACH]

---

