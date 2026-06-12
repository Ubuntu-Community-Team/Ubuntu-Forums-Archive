---
title: "Do you use Redshift or similar ?"
date: 2019-08-16
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2019-08-16
When I use my PC after 6 pm I always use Redshift. It very soothing for the eyes.

Do you use Redshift or similar ?

---

### Post by cruzer001 on 2019-08-16
I find turning down screen brightness just as useful.

---

### Post by guiverc on 2019-08-16
Yep, redshift is setup and auto-started  on my systems

---

### Post by linuxyogi on 2019-08-16
> **cruzer001 said:**
> I find turning down screen brightness just as useful.

My 10 year old monitor died recently so I purchased a new one.

My old monitor was LCD and my new monitor is LED.

When I brought this new monitor from the shop the brightness 

by default was really high. It was hurting my eyes. I had to manually decrease the brightness

but still I find Redshift very useful. It blocks the blue light coming from the screen.

---

### Post by linuxyogi on 2019-08-16
> **guiverc said:**
> Yep, redshift is setup and auto-started  on my systems

The reason I haven't added Redshift to startup is because I prefer not to use Redshift while 

watching videos.

---

### Post by ajgreeny on 2019-08-16
Yes I've been using it for a while now, using geoclue2 as the location provider, though its necessary to edit the **/etc/geoclue/geoclue.conf** file in order for it to work by adding
```
[redshift]
allowed=true
system=false
users=
```
to the end of the file.

I find it absolutely necessary to avoid the eye strain that comes from too much blue light in darker ambient conditions, and I've even cut down the default temp-night level to 3500 which suits my situation better.

---

### Post by linuxyogi on 2019-08-16
@[**[COLOR=#C61919][B]ajgreeny**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=27747")

Can you please tell me in details what is geoclue2 ?

---

### Post by ajgreeny on 2019-08-16
It is a utility that figures out where you are in the world and sets the changes of light level of the screen according to what it finds; using this you have no need to esetdit the computer's location manually if you move to the other side of the world or happen to take a laptop on vacation with you somewhere distant from its usual home.
If the computer always stays in the same location it will not strictly be necessary to use it and you can use manual location provider in the geoclue.conf file.

Just for info here's my geoclue.conf file
Any line starting with ; is commented out so is not read and does not have any effect.
```
[redshift]
; Set the day and night screen temperatures
temp-day=6500
temp-night=3500

; Enable/Disable a smooth transition between day and night
; 0 will cause a direct change from day to night screen temperature.
; 1 will gradually increase or decrease the screen temperature
transition=1

; Set the screen brightness. Default is 1.0
; brightness=0.9
; It is also possible to use different settings for day and night since version 1.8.
; brightness-day=0.7
; brightness-night=0.4
; Set the screen gamma (for all colors, or each color channel individually)
; gamma=0.9
; gamma=0.8:0.7:0.8
; This can also be set individually for day and night since
; version 1.10.
; gamma-day=0.8:0.7:0.8
; gamma-night=0.6

; Set the location-provider: 'geoclue', 'gnome-clock', 'manual'
; type 'redshift -l list' to see possible values
; The location provider settings are in a different section.
location-provider=geoclue2

; Set the adjustment-method: 'randr', 'vidmode'
; type 'redshift -m list' to see all possible values
; 'randr' is the preferred method, 'vidmode' is an older API
; but works in some cases when 'randr' does not.
; The adjustment method settings are in a different section.
adjustment-method=randr

; Configuration of the location-provider:
; type 'redshift -l PROVIDER:help' to see the settings
; e.g. 'redshift -l manual:help'
; [manual]
; lat=
; lon=

; Configuration of the adjustment-method
; type 'redshift -m METHOD:help' to see the settings
; ex: 'redshift -m randr:help'
; In this example, randr is configured to adjust screen 1.
; Note that the numbering starts from 0, so this is actually the second screen.
[randr]
screen=0

```

---

### Post by linuxyogi on 2019-08-16
@[**[COLOR=#C61919][B]ajgreeny**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=27747")

Thanks a lot.

---

