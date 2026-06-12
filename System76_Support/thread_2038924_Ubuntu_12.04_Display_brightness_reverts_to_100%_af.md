---
title: "Ubuntu 12.04: Display brightness reverts to 100% after reboot."
date: 2012-08-07
forum: System76 Support
---

### Post by akwala on 2012-08-07
I have a Serval Pro (serp7).

The brightness setting in System Settings -> Brightness and Lock isn't sticky across reboots. Is there either a config setting that I can set or a command that I can run at startup to automate brightness control?

I've tried xbacklight, which doesn't seem to have any effect.
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by isantop on 2012-08-07
> **akwala said:**
> I have a Serval Pro (serp7).

The brightness setting in System Settings -> Brightness and Lock isn't sticky across reboots. Is there either a config setting that I can set or a command that I can run at startup to automate brightness control?

I've tried xbacklight, which doesn't seem to have any effect.
[LEFT][COLOR=#000000][/COLOR][/LEFT]

Are you on battery power or on AC?

---

### Post by akwala on 2012-08-07
> **isantop said:**
> Are you on battery power or on AC?
On AC.

[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by isantop on 2012-08-08
> **akwala said:**
> On AC.

[LEFT][COLOR=#000000][/COLOR][/LEFT]

I believe the BIOS resets the Brightness on AC to full for best viewing quality.

---

### Post by akwala on 2012-08-08
> **isantop said:**
> I believe the BIOS resets the Brightness on AC to full for best viewing quality.
Ah. And I don't see a setting for it on the BIOS console, so can't be controlled there. Is there a way to control it post-boot, during session start up? I can do this manually using 'indicator-brightness', but would prefer to automate it.

---

### Post by akwala on 2012-08-08
I looked at the indicator-brightness (**ppa:indicator-brightness/ppa**) code and found the command it uses:

```
$ pkexec /usr/lib/gnome-settings-daemon/gsd-backlight-helper --help
Usage:
  gsd-backlight-helper [OPTION...]

GNOME Settings Daemon Backlight Helper

Help Options:
  -h, --help               Show help options

Application Options:
  --set-brightness         Set the current brightness
  --get-brightness         Get the current brightness
  --get-max-brightness     Get the number of brightness levels supported
```More info here: [http://superuser.com/questions/409945/how-to-set-the-laptop-screen-brightness-programatically](http://superuser.com/questions/409945/how-to-set-the-laptop-screen-brightness-programatically)

In my case...
```
$ pkexec /usr/lib/gnome-settings-daemon/gsd-backlight-helper --get-max-brightness
7
```...so I can pick brightness level 0 to 7, like so:
```
$ pkexec /usr/lib/gnome-settings-daemon/gsd-backlight-helper --set-brightness 2
```


[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by isantop on 2012-08-09
> **akwala said:**
> I looked at the indicator-brightness (**ppa:indicator-brightness/ppa**) code and found the command it uses:

```
$ pkexec /usr/lib/gnome-settings-daemon/gsd-backlight-helper --help
Usage:
  gsd-backlight-helper [OPTION...]

GNOME Settings Daemon Backlight Helper

Help Options:
  -h, --help               Show help options

Application Options:
  --set-brightness         Set the current brightness
  --get-brightness         Get the current brightness
  --get-max-brightness     Get the number of brightness levels supported
```More info here: [http://superuser.com/questions/409945/how-to-set-the-laptop-screen-brightness-programatically](http://superuser.com/questions/409945/how-to-set-the-laptop-screen-brightness-programatically)

In my case...
```
$ pkexec /usr/lib/gnome-settings-daemon/gsd-backlight-helper --get-max-brightness
7
```...so I can pick brightness level 0 to 7, like so:
```
$ pkexec /usr/lib/gnome-settings-daemon/gsd-backlight-helper --set-brightness 2
```


[LEFT][COLOR=#000000][/COLOR][/LEFT]

If it's easier, you can also adjust it using Fn+F8 and F9 for down and up respectively.

I should also point out that it will be persistent across suspend and resume, so that may be an option if you want to be able to leave it.

---

