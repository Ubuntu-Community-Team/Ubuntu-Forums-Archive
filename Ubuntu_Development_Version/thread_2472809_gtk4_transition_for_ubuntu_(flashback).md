---
title: "gtk4 transition for ubuntu (flashback)"
date: 2022-03-13
forum: Ubuntu Development Version
---

### Post by Claus7 on 2022-03-13
Hello,

Recently I noticed that under gnome tweaks->appearance->themes there is the option of *Legacy* Applications. What is new is the word Legacy.

How ubuntu looks like is changed either by changing a theme and/or a gnome-shell theme.  

Using the image viewer under jammy development, very recently it acquired a dark theme, which is not affected from the aforementioned options. 
Does this mean that it is a gkt4 application and all gkt4 apps will be configured under settings->appearance?

Regards!

---

### Post by Claus7 on 2022-03-14
Hello,

I found out that this is a long issue. Some links are:
1) how to create gtk apps using glade
[https://www.gtk.org](https://www.gtk.org)
2) first look of some gtk4 apps
[https://9to5linux.com/first-look-at-some-of-the-gtk4-apps-in-gnome-42](https://9to5linux.com/first-look-at-some-of-the-gtk4-apps-in-gnome-42)
3) some relevant files [https://blogs.gnome.org/alatiera/2021/09/18/the-truth-they-are-not-telling-you-about-themes/](https://blogs.gnome.org/alatiera/2021/09/18/the-truth-they-are-not-telling-you-about-themes/)
4) a long gtk story [https://ludditus.com/2021/05/30/is-there-any-future-for-the-gtk-based-desktop-environments/](https://ludditus.com/2021/05/30/is-there-any-future-for-the-gtk-based-desktop-environments/)

from what I understood, it is based on the app whether it will choose to be based on gtk4 or something else.
The thing is that its not clear where gtk4 can be modified: going into /usr/share/themes/Yaru/gtk-4.0
the file gtk.css contains only one line: @import url("resource:///com/ubuntu/themes/Yaru/4.0/gtk.css");

edit: I came across this video: [https://www.youtube.com/watch?v=GCb54PM-x0U](https://www.youtube.com/watch?v=GCb54PM-x0U)
it sounds that these changes might be more resource hungry

as it seems time will tell...

Regards!

---

### Post by vicshrike on 2022-03-15
Thanks for the links @Claus7, have not read them yet, but will do so later. Looks like there are some interesting stuff for me there.

---

### Post by Claus7 on 2022-03-15
Hello,

> **Claus7 said:**
> 
...The thing is that its not clear where gtk4 can be modified: going into /usr/share/themes/Yaru/gtk-4.0
the file gtk.css contains only one line: @import url("resource:///com/ubuntu/themes/Yaru/4.0/gtk.css");
...

I think that the solution is similar as here: [https://askubuntu.com/questions/1261156/editing-yaru-gtk-theme-where-is-resource-com-ubuntu-themes-yaru-3-20-gtk-css](https://askubuntu.com/questions/1261156/editing-yaru-gtk-theme-where-is-resource-com-ubuntu-themes-yaru-3-20-gtk-css)

> **vicshrike said:**
> Thanks for the links @Claus7, have not read them yet, but will do so later. Looks like there are some interesting stuff for me there.

the long story is a really long one. Happy reading!

Regards!

---

### Post by jbicha on 2022-03-16
I have a Discourse post coming soon that will give some more details about Ubuntu GNOME dark theme stuff and it mentions the Legacy Application Theme setting in the Tweaks app.

It sounds like you are using -proposed packages in a development release. While that gets you newer stuff, sometimes there are known bugs. In this case, you are being hit by [LP: #1964841]("https://launchpad.net/bugs/1964841")

You can opt in to the new dark theme by running

```

gsettings set org.gnome.desktop.interface color-scheme 'prefer-dark'

```

And to turn it off

```

gsettings reset org.gnome.desktop.interface color-scheme

```

We're going to have the appearance panel in the GNOME Settings app do that for you when you pick dark or light, but we haven't finished that work yet.

---

### Post by Claus7 on 2022-03-16
Hello,

thanks for that as well. Indeed I had proposed enabled as you mention.

Just a clarification, if possible, in the upcoming Discourse post. 
Under appearance there are two options available: light and dark. Both options have two different "windows" inside: the dark one has two dark windows (one in front and one behind), while the light theme has one light in front and one dark behind it.

The clarification would be: what does this mixed light theme represent? Will it be possible to get rid of the dark part from the light theme, since it seems that it will contain some dark characteristics and won't be a "pure" light one?

Its good to know that a guide is underway. 

Regards!

---

### Post by jbicha on 2022-03-16
> **Claus7 said:**
> 
Under appearance there are two options available: light and dark. Both options have two different "windows" inside: the dark one has two dark windows (one in front and one behind), while the light theme has one light in front and one dark behind it.

The clarification would be: what does this mixed light theme represent? Will it be possible to get rid of the dark part from the light theme, since it seems that it will contain some dark characteristics and won't be a "pure" light one?


The dark window in the background is basically the upstream GNOME 42 graphic. You can file a bug against gnome-control-center about it. Technically background windows are dimmed slightly but they aren't "dark".

> **Claus7 said:**
> 
Its good to know that a guide is underway.


Less a guide. More of an announcement. The button in the Settings app will need to do the right thing for 22.04 LTS without needing to manually adjust gsettings.

---

### Post by Claus7 on 2022-03-16
Hello,

> **jbicha said:**
> The dark window in the background is basically the upstream GNOME 42 graphic. You can file a bug against gnome-control-center about it. Technically background windows are dimmed slightly but they aren't "dark".
very nice the clarification. The bug has been filed.

> **jbicha said:**
> Less a guide. More of an announcement. The button in the Settings app will need to do the right thing for 22.04 LTS without needing to manually adjust gsettings.

Still good to hear.

Regards!

---

