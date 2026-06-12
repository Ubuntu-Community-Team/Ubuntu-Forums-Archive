---
title: "Firefox 57"
date: 2017-11-14
forum: Ubuntu, Linux and OS Chat
---

### Post by makitso on 2017-11-14
Wow, just added FF 57 to my xubuntu 17.10 system, wow, its a rocket.  I have switched to Chrome but, may go back :-)  However, I am still ticked that Firebug is no longer available.

    ppa:ubuntu-mozilla-security

---

### Post by handydandyhim on 2017-11-15
I have to say that I'm super impressed with the new build as well. I've been using Firefox Nightly on my Win10 machine for over a month and have grown fond of the update UI and features. I was using Edge the other day (don't judge) and saw that they are still touting the highest score on Octane II. However, when I ran Octane on Edge, Chrome, and FF 57 I saw that FF and Chrome dominated Edge by about 5,000 points each. The main reason I use FF57 at work is for the add-ons. Our policies prevent us from installing Chrome apps or Microsoft Apps in Edge, so FF is the only browser I can use with LastPass and this new build is just so sexy.

---

### Post by walts48 on 2017-11-15
> **makitso said:**
> Wow, just added FF 57 to my xubuntu 17.10 system, wow, its a rocket.  I have switched to Chrome but, may go back :-)  However, I am still ticked that Firebug is no longer available.

    ppa:ubuntu-mozilla-security

Firebug has been integrated into Firefox Developer Tools.

> So it’s sad that Firebug is now reaching end-of-life in the Firefox  browser, with the release of Firefox Quantum (version 57) next month.  The good news is that all the capabilities of Firebug are now present in  current Firefox Developer Tools.

REF: [https://hacks.mozilla.org/2017/10/saying-goodbye-to-firebug/](https://hacks.mozilla.org/2017/10/saying-goodbye-to-firebug/)

---

### Post by kansasnoob on 2017-11-15
Sadly it's totally unusable on my old Intel Atom 230 CPU box with 2GB of RAM :(

It must use vastly more resources because the previous version ran fairly well with uBlock origin added. The new version just chokes altogether and displays a "webpage opening slowly" warning before freezing up.

---

### Post by kostkon on 2017-11-15
> **kansasnoob said:**
> Sadly it's totally unusable on my old Intel Atom 230 CPU box with 2GB of RAM :(

It must use vastly more resources because the previous version ran fairly well with uBlock origin added. The new version just chokes altogether and displays a "webpage opening slowly" warning before freezing up.
Atom 230 is a fairly weak Atom CPU. But, you could try creating a new profile in Firefox and starting afresh.

---

### Post by poorguy on 2017-11-15
I just installed Firefox 57 and the one extension and dictionary that I use and it seems to work well and the new clean design is cool. ;)

---

### Post by vasa1 on 2017-11-15
Nice video: [https://www.youtube.com/watch?v=ftYFz-DLIfE](https://www.youtube.com/watch?v=ftYFz-DLIfE) but the speed/RAM tests the poster reports don't support Mozilla's claims :???:

---

### Post by kansasnoob on 2017-11-16
> **kostkon said:**
> Atom 230 is a fairly weak Atom CPU. But, you could try creating a new profile in Firefox and starting afresh.

That was a fresh install of Artful and I didn't even sync. So for now I'm just using Chromium on that box. BTW I even tried upgrading to 3GB of RAM and it made no difference. I wonder what the minimum specs are supposed to be?

---

### Post by makitso on 2017-11-16
> [COLOR=#000000]Firebug has been integrated into Firefox Developer Tools.[/COLOR]
 
Yes I know.  I use the dev tools in both FF and Chrome.  The Developer Tools in FF are not quite as good as the old Firebug ones.

---

### Post by kansasnoob on 2017-11-16
It works great, really great, on everything I have in-house other than that old Atom box. The new layout is a big improvement.

---

### Post by canucksailor2 on 2017-11-16
It's a disaster -- certainly no faster than 56, deletes most add-ons, nos "restore closed windows", etc. But my main concern (Ubuntu 16.04.3LTS, Mate Desktop) is that it has updated without my permission. I have all "automatic upgrades" turned off (system and Firefox), always upgrade manually via CLI. But This morning, Firefox 57 out of nowhere. The only log entry I can find is: 

me@mybox:/var/log$ cat syslog.1 | grep 'firefox'
Nov 16 08:45:30 mybox apparmor[713]: Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

How the heck did Mozilla get sudo rights?

---

### Post by mc4man on 2017-11-16
> **canucksailor2 said:**
> It's a disaster -- certainly no faster than 56, deletes most add-ons, nos "restore closed windows", etc. But my main concern (Ubuntu 16.04.3LTS, Mate Desktop) is that it has updated without my permission. I have all "automatic upgrades" turned off (system and Firefox), always upgrade manually via CLI. But This morning, Firefox 57 out of nowhere. The only log entry I can find is: 

me@mybox:/var/log$ cat syslog.1 | grep 'firefox'
Nov 16 08:45:30 mybox apparmor[713]: Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

How the heck did Mozilla get sudo rights?
Maybe you have unattended upgrades still enabled or upgraded without realizing.
If you want to go back to last dl the needed packages from here & install all at once with dpkg
[https://launchpad.net/ubuntu/+source/firefox/56.0+build6-0ubuntu0.16.04.2](https://launchpad.net/ubuntu/+source/firefox/56.0+build6-0ubuntu0.16.04.2)

if using the ubuntu start page then also downgrade xul-ext-ubufox to 
[https://launchpad.net/ubuntu/xenial/amd64/xul-ext-ubufox/3.4-0ubuntu0.16.04.1](https://launchpad.net/ubuntu/xenial/amd64/xul-ext-ubufox/3.4-0ubuntu0.16.04.1)

---

### Post by vasa1 on 2017-11-17
Some UI customizations: [How to Customize Firefox Quantum&#8217;s New Interface]("https://www.howtogeek.com/333110/how-to-customize-firefox-quantum-and-remove-the-white-space-around-the-title-bar/")

---

### Post by kansasnoob on 2017-11-17
> **vasa1 said:**
> Some UI customizations: [How to Customize Firefox Quantum’s New Interface]("https://www.howtogeek.com/333110/how-to-customize-firefox-quantum-and-remove-the-white-space-around-the-title-bar/")

Awesome. I hadn't figured out how to get the downloads button to stay visible.

---

### Post by kc1di on 2017-11-17
I like the new FF but still like Opera better.

---

### Post by Buntu Bunny on 2017-11-17
I'm not very happy with it. Made my start page defunct. Seems every time they do a major Firefox overhaul it takes forever to get things back to the way I like them.

---

### Post by jg1 on 2017-11-18
It's rubbish
No control over security, cookies, scripts - everything relies on Google etc whom we all love and trust!!
Slow and bloated with unnecessary features you can no longer turn off
Looking for a new browser - any suggestions welcomed
Temporarily changed to Midori

---

### Post by vasa1 on 2017-11-18
> **Buntu Bunny said:**
> ... Made my start page defunct. ...
How's that?

---

### Post by poorguy on 2017-11-18
> **jg1 said:**
> It's rubbish
No control over security, cookies, scripts - everything relies on Google etc whom we all love and trust!!
Slow and bloated with unnecessary features you can no longer turn off
Looking for a new browser - any suggestions welcomed
Temporarily changed to Midori
What are the unnecessary features you can no longer turn off.

If you like tweaking settings here are two you should love.

[https://vivaldi.com/](https://vivaldi.com/)

[https://www.slimjet.com/](https://www.slimjet.com/)

---

### Post by kc1di on 2017-11-18
> **jg1 said:**
> It's rubbish
No control over security, cookies, scripts - everything relies on Google etc whom we all love and trust!!
Slow and bloated with unnecessary features you can no longer turn off
Looking for a new browser - any suggestions welcomed
Temporarily changed to Midori
Try Opera.

---

### Post by canucksailor2 on 2017-11-18
[QUOTE=mc4man;13712001]Maybe you have unattended upgrades still enabled or upgraded without realizing.

Tnx, but -- No and No

And it's repeatable, I run more than 20 workstations (16.04.3 LTS + Mate desktop.)  I can take any one of them (with FF 56), make sure that unattended upgrades are disabled, and reboot. I don't even get the desktop before the upgrade to 57 starts.

Now I'm going to try FF 52 ESR and see if that "auto-upgrades" -- but even if that works properly, there's still less than a year of "ESR" left on the Mozilla project.  In the meanwhile I'm deleting FF on all our boxes and installing Opera.

---

### Post by kansasnoob on 2017-11-19
The one thing I'd change if I could is moving the tab bar down to where it's just above the windows. It just always made sense to me to have the tabs located right above the windows because that's what you're actually "moving" to. Not a big deal but having the tabs at the very top just feels "off".

---

### Post by vasa1 on 2017-11-19
> **kansasnoob said:**
> The one thing I'd change if I could is moving the tab bar down to where it's just above the windows. It just always made sense to me to have the tabs located right above the windows because that's what you're actually "moving" to. Not a big deal but having the tabs at the very top just feels "off".
Please look at [https://github.com/Aris-t2/CustomCSSforFx/releases/](https://github.com/Aris-t2/CustomCSSforFx/releases/). I think it may have what you want. 

Edit: But see post #30 in this thread. It's much simpler.

---

### Post by vasa1 on 2017-11-19
I downloaded [https://github.com/Aris-t2/CustomCSSforFx/releases/download/1.3.1/custom_css_for_fx_v1.3.1.zip](https://github.com/Aris-t2/CustomCSSforFx/releases/download/1.3.1/custom_css_for_fx_v1.3.1.zip) and extracted it.```
$ ls -l
total 48
drwx------ 11 vasa1 vasa1  4096 Nov 19 15:47 css
drwx------  2 vasa1 vasa1  4096 Nov 19 15:47 image
-rw-rw-r--  1 vasa1 vasa1 25462 Nov 19 15:48 userChrome.css
-rw-rw-r--  1 vasa1 vasa1  4667 Nov 18 01:15 userContent.css
drwx------  2 vasa1 vasa1  4096 Nov 19 15:47 xml
$
```
Renamed my own userChrome.css to MyuserChrome.css.
Moved Aris' userChrome.css and css subfolder to my chrome subfolder in my profile.
Then, I uncommented just this one line (line #194 in this version) in Aris' userChrome.css:
```
@import url(./css/tabs/tabs_below_navigation_toolbar.css);
```
Saved userChrome.css.
Started Firefox.

For those who don't know, the "Aris" in the github link is the developer of Classic Theme Restorer. He's doing his best to help users cope with Firefox 57!

And details about userChrome.css are here: [http://kb.mozillazine.org/index.php?title=UserChrome.css](http://kb.mozillazine.org/index.php?title=UserChrome.css)

---

### Post by ajgreeny on 2017-11-19
Just what I would have likes vasa1, but having done what you said with the original userChrome.css and imported the version from that archive with the /* removed from the start and the /**/ from the end of the line, I still have tabs at the very top.

Any idea what I am missing.

PS: I have not messed with css files before so I could have missed something obvious which I just am not seeing, even though I am pretty sure I did what you say in post 24.

---

### Post by vasa1 on 2017-11-19
> **ajgreeny said:**
> Just what I would have likes vasa1, but having done what you said with the original userChrome.css and imported the version from that archive with the /* removed from the start and the /**/ from the end of the line, I still have tabs at the very top.

Any idea what I am missing.

PS: I have not messed with css files before so I could have missed something obvious which I just am not seeing, even though I am pretty sure I did what you say in post 24.I'll give it another look-see and will post in a while ...

---

### Post by vasa1 on 2017-11-19
@ajgreeny, let's try another way:
Rename the existing userChrome.css file to something else.

Then create a new userChrome.css file with the following contents:```
/*AGENT_SHEET*/

/* Firefox 57+ userChrome.css tweaks ****************************************************/
/* code mostly taken from 'Classic Theme Restorer' & 'Classic Toolbar Buttons' add-ons **/
/* by Aris (aris-addons@gmx.net)*********************************************************/
/* Github: https://github.com/aris-t2/customcssforfx ************************************/
/****************************************************************************************/


/* tabs toolbar adjustment */
#main-window[tabsintitlebar] #toolbar-menubar[autohide="true"][inactive="true"] ~ #TabsToolbar, 
#main-window[tabsintitlebar][sizemode="maximized"] #toolbar-menubar[autohide="true"][inactive="true"] ~ #TabsToolbar,
#main-window[uidensity=compact][tabsintitlebar] #toolbar-menubar[autohide="true"][inactive="true"] ~ #TabsToolbar,
#main-window[uidensity=compact][tabsintitlebar][sizemode="maximized"] #toolbar-menubar[autohide="true"][inactive="true"] ~ #TabsToolbar,
#TabsToolbar{
  -moz-padding-start: 2px !important;
}
#main-window[tabsintitlebar][sizemode="normal"]:not([inFullscreen]) #TabsToolbar {
  margin-top: 0px !important;
}

/* fix for application/hamburger button in titlebar */
#main-window[tabsintitlebar][inFullscreen] #toolbar-menubar[autohide="true"][inactive="true"] ~ #nav-bar  #PanelUI-button {
  visibility: collapse !important;
}

/* tab height */
#tabbrowser-tabs,
#tabbrowser-tabs > .tabbrowser-arrowscrollbox,
.tabbrowser-tabs[positionpinnedtabs] > .tabbrowser-tab[pinned] {
  min-height: 25px !important;
}

/* toolbar order (start) ************************************/
#print-preview-toolbar,
#printedit-toolbar,
#titlebar {
  -moz-box-ordinal-group: 0 !important;
}
#navigator-toolbox #toolbar-menubar {
  -moz-box-ordinal-group: 1 !important;
}
/* navigation toolbar */
#navigator-toolbox #nav-bar {
  -moz-box-ordinal-group: 2 !important;
}
/* bookmarks toolbar */
#navigator-toolbox #PersonalToolbar {
  -moz-box-ordinal-group: 3 !important;
}
/* 3rd party toolbars */
#navigator-toolbox toolbar {
  -moz-box-ordinal-group: 10 !important;
}
/* tabs toolbar */
#navigator-toolbox #TabsToolbar {
  -moz-box-ordinal-group: 100 !important;
}
/* toolbar order (end) **************************************/

/* toolbar colors */
#TabsToolbar:not(:-moz-lwtheme){
  -moz-appearance: none !important;
  background-image: linear-gradient(#f9f9fa,#f9f9fa) !important;
}

/* remove color overlay for lw-themes */
#main-window:not([style*='--lwt-header-image:url("resource:///chrome/browser/content/browser/defaultthemes/compact.header.png");']) :-moz-any(#nav-bar,#PersonalToolbar,#TabsToolbar):-moz-lwtheme{
  background: unset !important;
}

/* adjust compact themes background color */
#main-window[style*='--lwt-header-image:url("resource:///chrome/browser/content/browser/defaultthemes/compact.header.png");']:-moz-lwtheme-brighttext #TabsToolbar:-moz-lwtheme {
  background-image: linear-gradient(#323234,#323234) !important;
}
#main-window[style*='--lwt-header-image:url("resource:///chrome/browser/content/browser/defaultthemes/compact.header.png");']:-moz-lwtheme-darktext #TabsToolbar:-moz-lwtheme {
  background-image: linear-gradient(#f5f6f7,#f5f6f7) !important;
}

/* toolbar borders */
#main-window #navigator-toolbox::after {
  opacity: 0 !important;
}
#TabsToolbar{
  margin-bottom: 0px !important;
  border-bottom: 1px solid #5f7181 !important;
}
#main-window[sizemode="normal"]  #TabsToolbar:not(:-moz-lwtheme){
  border-left: 1px solid #5f7181 !important;
  border-right: 1px solid #5f7181 !important;
}

/* adjust compact themes borders color */
#main-window[sizemode="normal"][style*='--lwt-header-image:url("resource:///chrome/browser/content/browser/defaultthemes/compact.header.png");']:-moz-lwtheme-darktext #TabsToolbar:-moz-lwtheme {
  border-left: 1px solid #5f7181 !important;
  border-right: 1px solid #5f7181 !important;
}
#main-window[style*='--lwt-header-image:url("resource:///chrome/browser/content/browser/defaultthemes/compact.header.png");']:-moz-lwtheme-brighttext #TabsToolbar:-moz-lwtheme {
  border-bottom: 1px solid #323234 !important;
}

/**/

#main-window:not([inFullscreen="true"])[tabsintitlebar] #TabsToolbar{
  -moz-margin-end: 0px !important;
}

#main-window[tabsintitlebar] #TabsToolbar .titlebar-placeholder{
  visibility: collapse !important;
}

#main-window[tabsintitlebar][sizemode="normal"] #toolbar-menubar[autohide="true"][inactive="true"],
#main-window[tabsintitlebar][sizemode="maximized"] #toolbar-menubar[autohide="true"][inactive="true"] {
  margin-top: 21px !important;
}

#tabbrowser-tabs .tab-drop-indicator {
  margin-bottom: 0px !important;
}

#PersonalToolbar:-moz-lwtheme,
#nav-bar:-moz-lwtheme {
  background-image: none !important;
  box-shadow: none !important;
  border-top: none !important;
  border-bottom: none !important;
}

/* remove tab fog */
#TabsToolbar:not(:-moz-lwtheme),
#TabsToolbar:not(:-moz-lwtheme)::before,
#TabsToolbar:not(:-moz-lwtheme)::after {
  box-shadow: unset !important;
}

/* remove 'dragging tab' margin/padding nonsense */
#TabsToolbar[movingtab] {
  padding-bottom: unset !important;
}

#TabsToolbar[movingtab] > .tabbrowser-tabs {
  padding-bottom: unset !important;
  margin-bottom: unset !important;
}

#TabsToolbar[movingtab] + #nav-bar {
  margin-top: unset !important;
}

/* scroll buttons */
#TabsToolbar:not(:-moz-lwtheme) #alltabs-button,
#TabsToolbar:not(:-moz-lwtheme) .tabbrowser-arrowscrollbox > .scrollbutton-up,
#TabsToolbar:not(:-moz-lwtheme) .tabbrowser-arrowscrollbox > .scrollbutton-down {
  fill: black !important;
}

/* tweaks for Windows Classic theme *//*
#nav-bar:not(:-moz-lwtheme),
#PersonalToolbar:not(:-moz-lwtheme),
#main-window:not([tabsintitlebar])  #TabsToolbar:not(:-moz-lwtheme) {
  border-left:  unset !important;
  border-right:  unset !important;
  background: unset !important;
}

#main-window:not([tabsintitlebar]) #toolbar-menubar:not(:-moz-lwtheme) {
  background: unset !important;
  box-shadow: unset !important;
  border-bottom: unset !important;
}

#main-window:not([tabsintitlebar]):not(:-moz-lwtheme) #navigator-toolbox,
#main-window:not([tabsintitlebar]):not(:-moz-lwtheme) #nav-bar,
#main-window:not([tabsintitlebar]):not(:-moz-lwtheme) #navigator-toolbox::before,
#main-window:not([tabsintitlebar]):not(:-moz-lwtheme) #nav-bar::before,
#main-window:not([tabsintitlebar]):not(:-moz-lwtheme) #navigator-toolbox::after,
#main-window:not([tabsintitlebar]):not(:-moz-lwtheme) #nav-bar::after {
  background: unset !important;
  box-shadow: unset !important;
  border: unset !important;
  border-image: unset !important;
}

#main-window:not([tabsintitlebar]) toolbar:not(#TabsToolbar):not(#toolbar-menubar):not(#nav-bar):not(:-moz-lwtheme) {
  background: unset !important;
}
/**/

```Save the new userChrome.css file and restart Firefox. Let's see if that works.

---

### Post by vasa1 on 2017-11-19
After downloading [https://github.com/Aris-t2/CustomCSSforFx/releases/download/1.3.1/custom_css_for_fx_v1.3.1.zip](https://github.com/Aris-t2/CustomCSSforFx/releases/download/1.3.1/custom_css_for_fx_v1.3.1.zip), unpack it in a new folder called **Aris**.

It's contents should look like this:
```
drwx------ 11 vasa1 vasa1  4096 Nov 19 15:47 css/
drwx------  2 vasa1 vasa1  4096 Nov 19 15:47 image/
-rw-rw-r--  1 vasa1 vasa1 25462 Nov 19 15:48 userChrome.css
-rw-rw-r--  1 vasa1 vasa1  4667 Nov 18 01:15 userContent.css
drwx------  2 vasa1 vasa1  4096 Nov 19 15:47 xml/
```

For now, we're concerned with two items in the **Aris** folder: 
[LIST]
[*]the subfolder called **css** and 
[*]the file called **userChrome.css**.
[/LIST]

Now, in your **~/.mozilla/firefox/profile_name** you need to create a folder called **chrome** (all lower case).
If you already have such a folder, see if you have a file called **userChrome.css**. If you do, rename it to something else. You'll lose the functionality of the renamed userChrome.css for now.

Now, copy over, from the folder **Aris**, the **css** folder and the **userChrome.css** file to the **chrome** folder in your profile.

Open the **userChrome.css** file using a text editor that allows for syntax highlighting (for convenience).

Find line #194. It should look like this:```
/* @import url(./css/tabs/tabs_below_navigation_toolbar.css); /**/
```

Change it to this:```
@import url(./css/tabs/tabs_below_navigation_toolbar.css);
```

Don't make any other changes. Save the file (as a text file) keeping the name **userChrome.css**.

Now, restart Firefox. Tabs should be below the nav bar.

---

### Post by ajgreeny on 2017-11-19
Ah.  Mea culpa!

I missed moving the **css** folder from the extracted archive to the **chrome** folder along with the edited **userChrome.css** file.

I am on a different machine at the moment so will get back on the one where it did not work and copy across that css folder as well as the edited file and will report back.

EDIT:
Yep! That was the problem.

I've now copied the css folder across as well as the userChrome.css file and it works, which looks so much better in my opinion, though I realise it's a case of "horses for courses" and may not be what everyone wants or likes.

Many thanks; I am glad you understand more about using .css files than I do!

---

### Post by vasa1 on 2017-11-19
Looks like there's also something much more "to the point". I haven't tried it: [https://forums.linuxmint.com/viewtopic.php?f=47&t=257605](https://forums.linuxmint.com/viewtopic.php?f=47&t=257605)

Tried it. If I liked tabs on the bottom, I'd go with this because that's all it does. Aris' code seems to do a lot more which may not be what one wants.

---

### Post by ajgreeny on 2017-11-20
I quite like the other things that Aris' code does such as the icon being coloured, but I will try this other version out of interest and report back. 

The major remaining tab aspect that I miss is the many things that could be set in tabmixplus such as always open certain link types in a new tab; that all seems to have disappeared for now at least.

EDIT:
Yes, I tried that Mint version as well and it works to move the tabbar down, but as I say above, I like the coloured toolbar icons so will stick with Aris' version, and now having figured out how these css files work I may also see if I can enable some of the other possible changes from Aris in that userChrome.css file of his.

---

### Post by Dennis N on 2017-11-20
> Looks like there's also something much more "to the point". I haven't tried it: [https://forums.linuxmint.com/viewtopic.php?f=47&t=257605](https://forums.linuxmint.com/viewtopic.php?f=47&t=257605)

This may have originally come from here:
[https://support.mozilla.org/en-US/questions/1185426](https://support.mozilla.org/en-US/questions/1185426)

I used this 'tabs on bottom' code for a while, then decided the tabs look better to me on top. I think choosing a good theme helps as well. My chosen theme reduced the tab height (which I thought was too much) before any customizing with userChrome.css. 

Since I don't need much customizing beyond the theme, I just copied the .css code I wanted from files in Aris' css folder and pasted directly into an empty userChrome.css, then made a few changes to the color codes. That part is trial and error (plus a color picker to get the codes).

See screen shot:

---

### Post by ajgreeny on 2017-11-20
One other useful option that may have been available but was unknown to me previously is to move the Bookmarks-Toolbar items into the Menubar, thus saving space.

When you're in the Customise page all the Bookmarks-Toolbar items are shown as a single star shaped icon so they can all be moved together and the Bookmarks-Toolbar can then be disabled giving a bit more vertical screen space to the main part of the window.

---

### Post by echotech2 on 2017-11-21
Ubuntu 16.04.03 - Updated v56 to Firefox v57 - Restarted - At first glance didn't notice anything different - Checked addons, all working except one "Legacy" (Saved Password Editor) which I expected - Closer look revealed other things I expected, square tabs, dropdown for addons etc. - Wait, where is my "Home" button?  Found it way over on the left.  I can live with that. -  2x faster?  I take that with a grain of salt, like when an ISP advertises "up to  xxMb". I didn't notice any really obvious gain (or loss) in page draws.

  The following is not to be taken seriously!

  I did notice one bug that should have blocked release.  While the bottom corners of the Firefox window are square, the top corners are ROUNDED!!!.  This is a serious failure of the UI team and should not be taken lightly.  I suggest they take a look at their box of Cap'n Crunch and notice that all the corners are square.

  --Dave

---

### Post by litlesam on 2017-11-21
> **echotech2 said:**
> Ubuntu 16.04.03 - Updated v56 to Firefox v57 - Restarted - At first glance didn't notice anything different - Checked addons, all working except one "Legacy" (Saved Password Editor) which I expected - Closer look revealed other things I expected, square tabs, dropdown for addons etc. - Wait, where is my "Home" button?  Found it way over on the left.  I can live with that. -  2x faster?  I take that with a grain of salt, like when an ISP advertises "up to  xxMb". I didn't notice any really obvious gain (or loss) in page draws.

  The following is not to be taken seriously!

  I did notice one bug that should have blocked release.  While the bottom corners of the Firefox window are square, the top corners are ROUNDED!!!.  This is a serious failure of the UI team and should not be taken lightly.  I suggest they take a look at their box of Cap'n Crunch and notice that all the corners are square.

  --Dave

On mine, all four corners are square.

---

### Post by kansasnoob on 2017-11-21
I'm actually getting used to this and rather like the out-of-box experience more and more the longer I use it. But I'm still bummed out that it doesn't run as well as older versions on weak hardware like the Atom 230 :(

On that box I started playing with Vivaldi again and it's notably faster and more usable. But then comes the big question - why would I want to run a different browser on just one set (or class) of hardware? It's kind of nice to have the same experience on ALL of the hardware you run, with the exception of touchscreen devices which are obviously just a different cat.

Getting way off topic here, but I recently installed Gutsy (yes - 7.10) on that old box just to remind myself how fast it was back then. It was FAST! But now it's slow with any "new" OS. Bodhi's "legacy" edition runs fairly well but still not as fast as Gutsy did. Maybe it is just time to retire that thing :cry:

---

### Post by ajgreeny on 2017-11-23
I have just found a bit of a bug with the userChrome.css file from Aris which seems to remove the ability to go to an address I type in the locationbar.

I have overcome this by renaming the locationbar folder to locationbar~ in the css folder which I moved to my profile as Aris instructs.  No doubt I could disable the various locationbar lines one by one in the userChrome.css file he provides to try and overcome the problem but I don't have time at present, so renaming the locationbar folder does the trick.

I will try to let Aris know this by contacting him on his site and see if he is already aware of this.

EDIT:
I have now passed on this info at the github site [https://github.com/Aris-t2/CustomCSSforFx/issues/41](https://github.com/Aris-t2/CustomCSSforFx/issues/41) and await his response.
Note I have now updated to version 1.3.5 of that zip archive but the problem is still there.

---

### Post by Geekboy on 2017-11-24
I'm missing the option to turn off title bars in the Custom Firefox screen.  Any ideas why?

I should have this option:


[IMG]https://i.imgur.com/acE5GE9.png[/IMG]

Instead I have this.  There is no check boxes for Title Bar or Drag Space.

[IMG]https://i.imgur.com/Dh3Ql56.png[/IMG]

---

### Post by ajgreeny on 2017-11-24
Where did your first screenshot come from? My customise screen is exactly the same as yours; was the first image from Windows?

Perhaps it is a setting in whatever window manager you are using, though I can not find anything on my system to do what you want.

---

### Post by Geekboy on 2017-11-24
Yes, it's Windows.  I'd love to do the same with Ubuntu.  I'm running on a small Lenovo laptop and would love to reclaim the vertical space if possible.

---

### Post by night_sky2 on 2017-11-24
> **kansasnoob said:**
> I'm actually getting used to this and rather like the out-of-box experience more and more the longer I use it. But I'm still bummed out that it doesn't run as well as older versions on weak hardware like the Atom 230 :(

I dropped FF some time ago on my aging PC. IMO, Firefox started to go downhill with the Australis UI. The browser became very sluggish and ressource-hungry. I'm not too convinced by this newer version. Anyway, Pale Moon is much better for weak hardware. It's what Firefox once was and still should be before it sold out to the likes of Google Chrome. There is a Linux build kept up-to-date which is actually pretty easy to install on Ubuntu.

---

### Post by walts48 on 2017-11-25
> **Geekboy said:**
> Yes, it's Windows.  I'd love to do the same with Ubuntu.  I'm running on a small Lenovo laptop and would love to reclaim the vertical space if possible.

As far as I know Ubuntu doesn't have a title bar. If you are referring to the bar across the top with the Date, Time, and icon to select Log Out, Suspend, Shutdown and other items as a title bar.

The about:config preference "browser.tabs.drawInTitlebar" is already set to "false" as the default setting in the Ubuntu version of Firefox.

---

### Post by vasa1 on 2017-11-25
This may help when Fx 59 comes around: [http://www.omgubuntu.co.uk/2017/11/firefox-nightly-adds-csd-option](http://www.omgubuntu.co.uk/2017/11/firefox-nightly-adds-csd-option)

---

### Post by ajgreeny on 2017-11-25
I have just tried the FF59 nightly release and it does exactly what you want, ie, it gets rid of the titlebar at the top which is from your window manager, therefore releasing more screen to the window itself.

On my Lubuntu 16.04 old netbook it is worth using, though at this stage I have no idea how well it can be trusted, but it's certainly working OK at the moment.

Note that as mentioned in vasa1's link, it has to be restarted after deselecting titlebar in the Customise window for the titlebar to disappear.

---

### Post by vasa1 on 2017-11-25
I took a look at the CSD option in Fx 59 with Kubuntu 18.04. It worked as advertised but the middle icon (resize/maximize) seemed somewhat "nibbled away" but hovering over it showed some sort of elaborate design. The minimize and close icons were fine.

Edit: I think I remember reading that "tabs in title bar" has been available for Windows for quite some time. Maybe that's where the poster got the images from.

IIRC, 16.04 uses gtk 3.18. And according to [https://bugzilla.mozilla.org/show_bug.cgi?id=1283299](https://bugzilla.mozilla.org/show_bug.cgi?id=1283299), gtk 3.20 is required. I didn't read the bug to the end so things may be different!

---

### Post by kansasnoob on 2017-12-02
The number of crashes has me ready to throw in the towel :mad:

I've never experienced this many browser crashes, ever :(

---

### Post by litlesam on 2017-12-02
> **kansasnoob said:**
> The number of crashes has me ready to throw in the towel :mad:

I've never experienced this many browser crashes, ever :(

I must be one of the lucky ones, my unit must be on line 20hrs a day running FF57 as well many other programs.

Not one crash yet.

---

### Post by Wadim_Korneev on 2017-12-03
The Developer Tools in FF are not quite as good as the old Firebug ones.

---

### Post by vasa1 on 2017-12-07
More appearance tweaks described in [http://www.omgubuntu.co.uk/2017/12/firefox-userchrome-css-linux-themes](http://www.omgubuntu.co.uk/2017/12/firefox-userchrome-css-linux-themes)

---

### Post by vasa1 on 2017-12-07
And just came across [VivaldiFox]("https://addons.mozilla.org/en-US/firefox/addon/vivaldifox/")!
> An add-on that allows colouring Firefox in a Vivaldi style fashion.

---

### Post by kansasnoob on 2017-12-16
Has anyone actually noticed a performance improvement over the older Firefox? 

Or could anyone actually say that Firefox is now faster than any other browser?

The only improvement I've noticed is that the new default layout is pretty good. I can use it out-of-box with only a few very minor tweaks (adding a separate search box and adding a bookmarks toolbar being the biggies), but otherwise it's just nothing to write home about. I certainly don't see any speed improvement, in fact it's more resource hungry on lower end hardware.

Since I've had to switch my lower end hardware to either Chrome, Chromium, or Vivaldi why bother with Firefox at all now? I wish I could add a true search box to the toolbar in Chromium. If that were possible Chromium would become my new default browser. I'm really leaning towards Vivaldi because it's so easily customized but there are rare websites (like The CW) that refuse to stream on it.

---

### Post by litlesam on 2017-12-16
Much faster than the older FF and like you, adding a separate search box and adding a bookmarks toolbar was a must.

---

### Post by Frogs Hair on 2017-12-17
I see almost no reduction in memory usage though page loading seems faster. There appears to be little advantage over chromium based browsers in my experience so far.

---

### Post by faraco2 on 2017-12-19
> **kansasnoob said:**
> Has anyone actually noticed a performance improvement over the older Firefox? 

Or could anyone actually say that Firefox is now faster than any other browser?

The only improvement I've noticed is that the new default layout is pretty good. I can use it out-of-box with only a few very minor tweaks (adding a separate search box and adding a bookmarks toolbar being the biggies), but otherwise it's just nothing to write home about. I certainly don't see any speed improvement, in fact it's more resource hungry on lower end hardware.

Since I've had to switch my lower end hardware to either Chrome, Chromium, or Vivaldi why bother with Firefox at all now? I wish I could add a true search box to the toolbar in Chromium. If that were possible Chromium would become my new default browser. I'm really leaning towards Vivaldi because it's so easily customized but there are rare websites (like The CW) that refuse to stream on it.

The responsiveness in my case is a great improvement. No lags and switching between the browser tabs was a breeze.

My only complaint for this version is, the occasional yet enormous CPU spikes that came with these upgrades.

---

### Post by vasa1 on 2017-12-19
> **faraco2 said:**
> ...
My only complaint for this version is, the occasional yet enormous CPU spikes that came with these upgrades.
[https://www.reddit.com/r/firefox/comments/7g6k9n/firefox_quantum_is_eating_your_cpu_help_us_debug/](https://www.reddit.com/r/firefox/comments/7g6k9n/firefox_quantum_is_eating_your_cpu_help_us_debug/)
[https://www.reddit.com/r/firefox/comments/7knnn4/firefox_quantum_is_eating_your_cpu_help_us_debug/](https://www.reddit.com/r/firefox/comments/7knnn4/firefox_quantum_is_eating_your_cpu_help_us_debug/)

Firefox developers are responding there.

---

### Post by faraco2 on 2017-12-21
> **vasa1 said:**
> [https://www.reddit.com/r/firefox/comments/7g6k9n/firefox_quantum_is_eating_your_cpu_help_us_debug/](https://www.reddit.com/r/firefox/comments/7g6k9n/firefox_quantum_is_eating_your_cpu_help_us_debug/)
[https://www.reddit.com/r/firefox/comments/7knnn4/firefox_quantum_is_eating_your_cpu_help_us_debug/](https://www.reddit.com/r/firefox/comments/7knnn4/firefox_quantum_is_eating_your_cpu_help_us_debug/)

Firefox developers are responding there.

Hey, thanks for that. It seems that I'm not totally alone with this issue.

---

