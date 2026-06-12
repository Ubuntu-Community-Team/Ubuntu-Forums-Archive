---
title: "&quot;open as administrator&quot; in Nautilus"
date: 2012-03-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by neu5eeCh on 2012-03-18
I notice that this extension doesn't seem to be available in the 12.04 repositories? 

sudo apt-get install nautilus-gksu

Comes up empty handed. Anyone know anything about this or am I off on the wrong track?

---

### Post by dino99 on 2012-03-18
when you open a session you'll get your rights, so dont really understand your needs.

---

### Post by neu5eeCh on 2012-03-18
> **dino99 said:**
> when you open a session you'll get your rights, so dont really understand your needs.

The extension adds a menu option (when you right click on a file) to open it "as administrator".

---

### Post by lucazade on 2012-03-18
[https://launchpad.net/~nae-team/+archive/daily](https://launchpad.net/~nae-team/+archive/daily)

add this ppa and install nautilus-open-as-root

ps. Be careful with root app, it is not recommended. Better to manage things from terminal via sudo.

---

### Post by VinDSL on 2012-03-18
> **VTPoet said:**
> Anyone know anything about this or am I off on the wrong track?
I *think* I enabled it by simply using Ubuntu Tweak 0.7.0

There's a box you can check, in Nautilus Settings, that shows advanced permissions in Nautilus.

Now, when I right-click a file, in the File System folder, during a normal session, Nautilus gives me the option of opening it as root.

This is what you're talking about, right?!?!?

Anyway, if I remember correctly, this is how I did it...  ;)

---

### Post by neu5eeCh on 2012-03-18
I tried the Ubuntu Tweak setting. That didn't work for me.

The PPA, on the other hand, was exactly what I was looking for. In fact, I went on an extensions binge. I'm happy now; and know just enough to be dangerous.

---

### Post by VinDSL on 2012-03-18
> **VTPoet said:**
> I tried the Ubuntu Tweak setting. That didn't work for me.

The PPA, on the other hand, was exactly what I was looking for. In fact, I went on an extensions binge. I'm happy now; and know just enough to be dangerous.
Glad it worked out for you.

For the sake of discussion...

There are 2 versions of Ubuntu Tweak, running around.  One is specific to Ubu Precise.

Here's the one I'm running:  [https://launchpad.net/~tualatrix/+archive/next](https://launchpad.net/~tualatrix/+archive/next)

Which version did you use?  Just curious...

**Edit**

To add a visual to it...


[INDENT][[IMG]http://vindsl.com/images/vindsl-nautilus-tweak-18-mar-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-nautilus-tweak-18-mar-2012-1.png")[/INDENT]


Screenshot colors look a little janky, with these apps open.

Don't pay any attention to the Launcher opacity (and #FFF border)...  LoL!  :D

Doesn't look that way, in realtime.

---

### Post by x-shaney-x on 2012-03-18
The nautilus extensions in the repos seem a bit hit and miss.
The open terminal one works but open as admin, set as wallpaper and image editing ones not working at all.

---

### Post by neu5eeCh on 2012-03-18
> **VinDSL said:**
> Glad it worked out for you.

For the sake of discussion...

There are 2 versions of Ubuntu Tweak, running around.  One is specific to Ubu Precise. Here's the one I'm running:  [https://launchpad.net/~tualatrix/+archive/next]("https://launchpad.net/%7Etualatrix/+archive/next")

Which version did you use?  Just curious...

Screenshot colors look a little janky, with these apps open.

Don't pay any attention to the Launcher opacity...  LoL!  :D

Doesn't look that way, in realtime.

I wasn't using the tualatrix version. Just added the PPA and updated Ubuntu Tweak. Thanks. After adding the prior PPA, I now have the "open as admin" option in Nautilus. Yup. I'm happy. That's a pretty cool Icon theme you've got going there. What is it?

---

### Post by VinDSL on 2012-03-18
> **VTPoet said:**
> That's a pretty cool Icon theme you've got going there. What is it?
Thanks!

I made it using ACYL 0.9.4  ;)

LINKAGE:  [http://pobtott.deviantart.com/art/Any-Color-You-Like-175624910](http://pobtott.deviantart.com/art/Any-Color-You-Like-175624910)

---

### Post by VMC on 2012-04-20
This stopped working as of today's iso install:
```
sudo cp libnautilus-gksu.so /usr/lib/nautilus/extensions-3.0
```

The *libnautilus-gksu.so* file is in there alright, I just can't open as administrator anymore. Even after re-boot.

---

### Post by mc4man on 2012-04-20
> **VMC said:**
> This stopped working as of today's iso install:
```
sudo cp libnautilus-gksu.so /usr/lib/nautilus/extensions-3.0
```

The *libnautilus-gksu.so* file is in there alright, I just can't open as administrator anymore. Even after re-boot.

I wouldn't even bother using the extension from 11.10's nautilus-gksu package anymore (that package is not in 12.04 anymore

Dr. Osman's nautilus action extra ppa's have the same as python-nautilus extensions, work well, the ppa's are activily supported & there is some other useful extensions there

release ppa
[https://launchpad.net/~nae-team/+archive/ppa](https://launchpad.net/~nae-team/+archive/ppa)

daily
[https://launchpad.net/~nae-team/+archive/daily](https://launchpad.net/~nae-team/+archive/daily)

---

### Post by VMC on 2012-04-20
> **mc4man said:**
> I wouldn't even bother using the extension from 11.10's nautilus-gksu package anymore (that package is not in 12.04 anymore

Dr. Osman's nautilus action extra ppa's have the same as python-nautilus extensions, work well, the ppa's are activily supported & there is some other useful extensions there

release ppa
[https://launchpad.net/~nae-team/+archive/ppa](https://launchpad.net/~nae-team/+archive/ppa)

daily
[https://launchpad.net/~nae-team/+archive/daily](https://launchpad.net/~nae-team/+archive/daily)
Thanks mc4man. I figured it anyone knew, it would be you. I will give it a go.

---

### Post by fragos on 2012-04-20
You can provide the same function with a nautilus script stored in ~/.gnome2/nautilus-scripts. I called my script "Open as Administrator" and in it put the following three lines:

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gksudo "gnome-open $uri" &
done

With that script you'll see an option for Scripts when you right click a file. Move the cursor to"Scripts" and your available scripts pop up. You'll need to log out and back in the first time for the Scripts to be noticeable by Nautilus.

---

### Post by dcstar on 2012-04-21
Another option is to directly launch Nautilus with root privileges via a Launcher with the following:

```
gksudo "dbus-launch nautilus --no-desktop --browser"
```

---

