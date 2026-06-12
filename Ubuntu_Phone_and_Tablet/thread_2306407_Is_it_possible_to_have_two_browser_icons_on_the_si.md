---
title: "Is it possible to have two browser icons on the sidebar?"
date: 2015-12-15
forum: Ubuntu Phone and Tablet
---

### Post by naomibrown on 2015-12-15
Is it possible to have two browser icons on the sidebar? I'd like to have one for todoist and one for everything else, to make it easier to just straight to my to do list :)

---

### Post by howefield on 2015-12-15
Short answer is yes..

Creating a second .desktop file in /usr/share/applications/ would work.

---

### Post by naomibrown on 2015-12-15
I've never done that before, so I just want to check, is [this post]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles") the kind of thing that is required?  It seems quite complicated, but I think I'll have a go!

---

### Post by howefield on 2015-12-15
Well, probably better ways of doing it, but all I would do is create a copy of the firefox.desktop file (assuming it is firefox that you are using)

```
cd /usr/share/applications/
```
```
sudo cp firefox.desktop todosist.desktop
```

Using nano to edit the new todoist.desktop file.. 

```
sudo nano todoist.desktop
```

Scroll down to where it says Exec=firefox %u and append 

```
-new-window https://en.todoist.com to the end
``` (or whatever the URL is that you use)

If you download an icon to use instead of the standard firefox icon, scroll down a further few lines to where it says Icon=firefox and replace firefox with the path to the icon, eg

```
Icon=/home/hugh/Pictures/download.png
```

You should then be able to search for it in the Dash and drag on to the launcher bar like the example I have in the attached image.

---

### Post by naomibrown on 2015-12-16
Can you install Firefox on Ubuntu Phone?

---

### Post by howefield on 2015-12-16
Apologies, I am an idiot for not noticing the forum that you had posted in.

No, you can't install Firefox onto an Ubuntu Phone, but you can still get 2 icons on the launcher for what you want, I'll come back with the method in a bit, got a couple of things to do.

---

### Post by naomibrown on 2015-12-17
No probs, thanks a lot!

---

### Post by howefield on 2015-12-17
So, probably the easiest (and most fun) way to do this would be to create a click package and install it to your phone. It sounds complicated and there are a few steps but I promise it is very easy to do :)

The steps are basically as follows :
1. Download an icon that you are allowed to use (preferably 256x256 pixels and .png format).
2. Fill in the details at [https://developer.ubuntu.com/webapp-generator/](https://developer.ubuntu.com/webapp-generator/) and press the submit button.

If you are successful, you should have a click package in your Downloads folder. Now use the terminal with the adb command to push and install the click package on to the phone (you will need to connect the phone to a computer running Ubuntu and have adb installed). 

```
adb push /path/to/your.click /tmp
```
```
adb shell pkcon install-local --allow-untrusted /tmp/your.click
```

My terminal output looked like this..
```
hugh@xenial:~$ adb devices
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
List of devices attached 
JU003513	device

hugh@xenial:~$ adb push Downloads/todoist.howefield_0.1_all.click /tmp
79 KB/s (3364 bytes in 0.041s)
hugh@xenial:~$ adb shell pkcon install-local --allow-untrusted /tmp/todoist.howefield_0.1_all.click
Installing files              [=========================]         
Finished                      [=========================]         
Installing files              [=========================]         
Waiting for authentication    [=========================]         
Starting                      [=========================]         
Finished                      [=========================]         
Installed   	todoist.howefield-0.1.all (installed:click,removable=1,app_name=todoist)	summary goes here
hugh@xenial:~$ 
```

Refreshing your list of applications on your phone should show the new app which you can open and pin to the launcher. (as per the screenshot - the todoist icon sitting below the standard browser icon)

---

