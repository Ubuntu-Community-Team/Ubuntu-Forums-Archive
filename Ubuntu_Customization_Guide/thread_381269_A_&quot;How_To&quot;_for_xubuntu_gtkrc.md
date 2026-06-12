---
title: "A &quot;How To&quot; for xubuntu gtkrc"
date: 2007-03-10
forum: Ubuntu Customization Guide
---

### Post by crimesaucer on 2007-03-10
Hello, I wrote a little "How To" modify your gtkrc for the xfce-engine used with xubuntu or the gtk2-engines-xfce.

I am a beginner so it's not a real professional guide, but more of a "How To" for beginners like me that want to change there colors and button style.

My guide is basically this:

Take a xfce-engines theme you already have installed in you /usr/share/themes

for an example, we'll use Xfce-winter, one of my favorites of the default ones.

Change directories to your /usr/share/themes

```
cd /usr/share/themes
``` 

then list

```
ls
```

pick you theme you want to work from, we'll use Xfce-winter.

Now while you're still in the /usr/share/themes directory, copy it to your home folder

```
cp -r Xfce-winter ~/
```

Now you should have it in your ~/ directory (home directory). Now just modify it using the cheat sheet from my other page, and then change the modified gtkrc's name to something like Xfce-winter_mod, and then move it back into your  /usr/share/themes directory.

So in terminal make sure you are in the home directory.

```
cd ~/
```

```
pwd
```

```
ls
```

and now to move your newly modified theme with your new name

```
sudo mv Xfce-winter_mod /usr/share/themes
```

now change directories back to /usr/share/themes

```
cd  /usr/share/themes
``` 

and list

```
ls
```

and you now see your new modified theme under your original Xfce-winter theme.

Another way to do it, is to be in the /usr/share/themes directory, and to cp it with a new name to the same directory.

```
sudo cp -r Xfce-winter /usr/share/themes/Xfce-winter_mod
```

this is if you feel comfortable editing your hex color codes and gtkrc settings when in root from pressing Alt F2-->--gksudo thunar

That's how I do it if I want to make a new original theme based from one of my own.

Now that I covered that, I'll link you to my explanation of the xfce-engine gtkrc which is like a cheat sheet of how to change the colors and sizes of basically your whole OS and Firefox/Thunderbird.

link: [http://ubuntuforums.org/showthread.php?t=377397](http://ubuntuforums.org/showthread.php?t=377397)

Now for it to look good in Firefox/Thunderbird, you can't use any other themes. Just use the plain default Firefox/Thunderbird and also if you make a dark theme, then be sure to goto the Firefox-->--Edit-->--Preferences-->--Content-->--Color-->-- and then "un-check" the box that says, "Use System Color". That way you will be able to read pages in Firefox while having a dark theme installed.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-54.png[/IMG]

This is my latest gtkrc customization.

---

