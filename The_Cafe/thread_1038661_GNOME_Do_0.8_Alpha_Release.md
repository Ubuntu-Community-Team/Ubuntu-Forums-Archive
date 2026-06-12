---
title: "GNOME Do 0.8 Alpha Release"
date: 2009-01-13
forum: The Cafe
---

### Post by davidsiegel on 2009-01-13
Hello, Ubuntu fans. The GNOME Do team is busy readying the next release of GNOME Do, version 0.8. I'm excited to invite you to try out our alpha and beta releases. We are currently offering alpha packages for Intrepid only:

Intrepid i386 PPA: [http://launchpad.net/~do-testers/+archive]("http://launchpad.net/%7Edo-testers/+archive")
Tarball and Intrepid 64-bit deb: [https://edge.launchpad.net/do/trunk/0.7.95](https://edge.launchpad.net/do/trunk/0.7.95)

Install the gnome-do and gnome-do-plugins packages.

**Edit: **64-bit users will still need to add the PPA to get the gnome-do-plugins package.

Bugs can be reported here: [http://bugs.launchpad.net/do](http://bugs.launchpad.net/do) Please search
for your problem before posting a bug to be sure that you don't create
a duplicate bug report.

When you get the alpha up and running, please reply to this thread
with a nice screenshot :)

Thank you,
David

---

### Post by skintythe1andonly on 2009-01-13
I actually just compiled a 64bit version last night. Its pretty nice. I would like the feature of autohiding only when the a window is maximized... i.e it goes away when im actually trying to do something. Other than that, I actually like it. Ive had one or two problems with it crashing so I'll try this .deb to see if its more stable.

---

### Post by Kosimo on 2009-01-13
I have it installed but I can't get the dock open. How do you do it guys?

---

### Post by NewJack on 2009-01-13
Is Docky included in the PPA at all?  Thanks.

---

### Post by cookieofdoom on 2009-01-13
Docky is a skin for gnome-do, basically. It's found under the appearances tab in the gnome-do preferences thing.

---

### Post by NewJack on 2009-01-13
Thanks for the quick reply

---

### Post by pelle.k on 2009-01-13
> When you get the alpha up and running, please reply to this thread
with a nice screenshot 
Here you go!

btw, before i get flooded with requests to share my theme details etc.

[LIST]
[*]gnome-do 0.7.95
[*]icons - gnome-brave (slightly modified)
[*]GTK - clearlooks, of course!
[*]Metacity - Human Glossy
[*]Wallpaper - color, by nyx (deviantart)
[*]Font - Corbel (windows font)
[/LIST]

EDIT: **I forgot to say great work you guys.** I'm not often impressed like this. And also, RAOF, thanks for the packaging magic :)

---

### Post by no1wantdthisname on 2009-01-14
Anyone getting it working on 64bit?  I can't select docky because the theme option is greyed out.

---

### Post by onero on 2009-01-14
Compositing needs to be enabled for Docky to work, from what I know.

---

### Post by black3ug on 2009-01-14
been waiting for an update ever since i found out that "home" won't open my home folder anymore. thanks guys!

a few comments:

1. it'd be great to see a preview of the gnome-do window when choosing themes

2. for some reason, i can't take a screenshot by pressing "prtscrn" if do is open. solved the problem by using the "take screenshot" app and giving it a countdown.

again, thanks! gnome-do has become a core app for me. :guitar:

---

### Post by black3ug on 2009-01-14
I spoke too soon. Typing "home" in gnome-do won't open my home folder anymore. 

The left pane does automatically display "home folder" (complete with icon) even before I've completed the word "home". The right side pane says "Run". However, when I press enter, all that happens is that the "program running" mouse icon shows for a few seconds. The home folder never opens.

Any fix for this?

---

### Post by Mazza558 on 2009-01-14
> **black3ug said:**
> I spoke too soon. Typing "home" in gnome-do won't open my home folder anymore. 

The left pane does automatically display "home folder" (complete with icon) even before I've completed the word "home". The right side pane says "Run". However, when I press enter, all that happens is that the "program running" mouse icon shows for a few seconds. The home folder never opens.

Any fix for this?

I had this problem in the old 0.6 release too, and it's still here in 0.8 - I wonder what the problem is?

---

### Post by Marat89 on 2009-01-14
I like the new Gnome Do very much :D
NOW beat that Windows 7 , no way:popcorn:
only problem: gnome-do crahes randomly and the nautilus plugin can not be activated

---

### Post by twisted_steel on 2009-01-14
> **Mazza558 said:**
> I had this problem in the old 0.6 release too, and it's still here in 0.8 - I wonder what the problem is?

I'm not sure, but it seems to work intermittently. I haven't been able to track down when it consistently fails.

---

### Post by Niksko on 2009-01-14
Had problems compiling. Configure seemed to go ok, but it wouldn't make. Needed to install mono-gmcs and mono-mcs packages and then it went smoothly. Might want to fix that.

Docky is very nice. I'd use it over AWN, but at the moment it is REALLY slow for me in the sense that when I move my mouse along the bar, everything slows down. It's basically unusable for me at the moment, but it looks nice and slick and I will use it if it's faster in the next stable release.

-Nik

---

### Post by cookieofdoom on 2009-01-14
Forgot to do this yesterday... Running on 64 bit using the instructions in the OP. It works great... locks up whenever I enable or disable a plugin, but I don't do that much so it doesn't bug me.

It would be great if frequently opened URL's could make there way down into the menu, too. Just a thought. I love how pidgin buddies do.

[[IMG]http://img216.imageshack.us/img216/4083/screenshoteu9.th.png[/IMG]](http://img216.imageshack.us/my.php?image=screenshoteu9.png)

---

### Post by davidsiegel on 2009-01-14
> **black3ug said:**
> I spoke too soon. Typing "home" in gnome-do won't open my home folder anymore. 

The left pane does automatically display "home folder" (complete with icon) even before I've completed the word "home". The right side pane says "Run". However, when I press enter, all that happens is that the "program running" mouse icon shows for a few seconds. The home folder never opens.

Any fix for this?

This is not a GNOME Do bug. When you start Do with your session, it has trouble reading certain environment variables that allow it to run the Home Folder launcher (it's a launcher as far as Do is concerned, not a proper folder). Try quitting and starting Do again -- the Home Folder should open just fine.

---

### Post by Arlanthir on 2009-01-14
Brilliant. 
Awn stopped working with my nvidia drivers on intrepid so I was back to good ol' gnome-panel. Not anymore!

I just miss some customization options like not having the separator for launchers/open windows, a **CLOCK**, a Show Desktop button, level of zoom height (or some other effects) etc...

Minor inconveniences:
The color property seems to do absolutely nothing for Docky.

If you have a small bar (some custom launchers, nothing opened and no auto-launchers) the gnome-do part of Docky is pretty useless as you can barely read more than 2 letters. Docky should automatically resize itself or its text ;)

Before adding a "Home" launcher, Docky seemed to think nautilus was just "Network"

The same with emesene being named a python file (I know)

Apart from that.... wow. Amazing work!

---

### Post by NewJack on 2009-01-14
Great work!  I had used AWN and found it a bit too buggy and I had been using Cairo Dock with Hardy.  I just did a clean install of Intrepid and wanted to try something different.  Well as long as it only gets better, looks like I found the keeper in Docky.

---

### Post by Infected24 on 2009-01-14
I want to try the Docky plugin, is it only present on 0.8? I have 0.6.1 installed but i cant see the theme on the appearance tab.

---

### Post by twisted_steel on 2009-01-14
> **Infected24 said:**
> I want to try the Docky plugin, is it only present on 0.8? I have 0.6.1 installed but i cant see the theme on the appearance tab.

That is correct. It is only in the 0.8 alpha and is going to be in the 0.8 release.

---

### Post by cookieofdoom on 2009-01-14
> **Infected24 said:**
> I want to try the Docky plugin, is it only present on 0.8? I have 0.6.1 installed but i cant see the theme on the appearance tab.

It is only present in the alpha 0.8 version. You can get it by following the instructions at the beginning of this thread.

---

### Post by black3ug on 2009-01-15
> **davidsiegel said:**
> This is not a GNOME Do bug. When you start Do with your session, it has trouble reading certain environment variables that allow it to run the Home Folder launcher (it's a launcher as far as Do is concerned, not a proper folder). Try quitting and starting Do again -- the Home Folder should open just fine.

Great tip, it works for me! Thanks! :guitar:

---

### Post by brunovecchi on 2009-01-15
Will there be packages for Hardy once 0.8 comes out of beta?
If not, that's going to be THE reason to finally upgrade to intrepid. Docky looks too good not to use it.

---

### Post by graabein on 2009-01-17
A little off topic perhaps, but on the other hand I'm keeping this thread alive ;) ... I'm using Gnome Do 0.6.1.0 and I'm wondering how I launch Spotify (installed through Wine)? Typing "spotify" don't work and I've tried upper case S and browse through options in the dropdown list... 

Lovely piece of software though! It's genious.

---

### Post by Arlanthir on 2009-01-17
Not really sure I should ask here, but anyway:

When I launch emesene (python) with Docky, it neatly turns the launcher into an open application. But with an application I designed myself in python, it doesn't (it opens a new application next to the trash). Any idea of the steps I should follow to ensure my dialog is well seen as the result of the launcher?

Thanks

---

### Post by tr4nce on 2009-01-17
I am having some problems with the alpha package for amd64:
Docky skins makes gnome-do hangs randomly, and also it's impossible to save the preferences with docky enabled, when you shutdown the app and reload it, you got back to the default skin.

Anyone else with this problem? Yes, I know that this is an alpha version but no one seems to have the same issue, so... :(

---

### Post by graabein on 2009-01-18
Maybe we should all check [http://bugs.launchpad.net/do]("http://bugs.launchpad.net/do") to see if our problems are mentioned there. :)

---

### Post by tr4nce on 2009-01-18
Thanks, I will give it a look.

---

### Post by northwestuntu on 2009-01-20
64bit 0.7.95 release is so slow using docky.

it just drags through the apps on the dock. hopefully this will improve.

---

### Post by twisted_steel on 2009-01-20
> **northwestuntu said:**
> 64bit 0.7.95 release is so slow using docky.

it just drags through the apps on the dock. hopefully this will improve.

Are you using a NVIDIA card? If so, check out this FAQ: [https://answers.launchpad.net/do/+faq/324](https://answers.launchpad.net/do/+faq/324).

---

### Post by northwestuntu on 2009-01-21
i do have nvidia. thanks for that :p  i'll give it a shot.

---

### Post by Mazza558 on 2009-01-21
You know what would be awesome - merging some of Mozilla Ubiquity's functionality with gnome-do.

---

### Post by zachtib on 2009-01-23
out of curiosity, what went wrong with the amd64 deb in the PPA?

---

### Post by pt123 on 2009-01-30
0.8 is officially released
[http://do.davebsd.com/release.shtml](http://do.davebsd.com/release.shtml)

Please digg the article
[http://digg.com/linux_unix/Announcing_GNOME_Do_0_8_Rock_out_with_your_dock_out](http://digg.com/linux_unix/Announcing_GNOME_Do_0_8_Rock_out_with_your_dock_out)

---

### Post by e.m.fields on 2010-02-19
> **Mazza558 said:**
> I had this problem in the old 0.6 release too, and it's still here in 0.8 - I wonder what the problem is?

**SOLVED - Problem opening "Home folder" in gnome-do**

See solution here:

[https://bugs.launchpad.net/do/+bug/290136/comments/55](https://bugs.launchpad.net/do/+bug/290136/comments/55)


Busby  wrote on 2009-11-05:  	  #55
> 
For a single command fix that persists forever and doesn't require super user privileges, use this command:

cat /usr/share/applications/nautilus-home.desktop | perl -pe 's/Exec=nautilus --no-desktop/Exec=nautilus --no-desktop ./g;' > $HOME/.local/share/applications/nautilus-home.desktop

This will basically create a corrected version of the faulty launcher in your home directory which will override the system's launcher.


---

### Post by SubOne on 2011-07-31
The directory did not exist for me. After creating the directory the fix did work. Thanks for your help!

*Edited command:*

```
mkdir -p $HOME/.local/share/applications/ && cat /usr/share/applications/nautilus-home.desktop | perl -pe 's/Exec=nautilus --no-desktop/Exec=nautilus --no-desktop ./g;' > $HOME/.local/share/applications/nautilus-home.desktop
```

---

