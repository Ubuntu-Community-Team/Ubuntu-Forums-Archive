---
title: "Looking for a simple calendar program!"
date: 2008-06-12
forum: The Cafe
---

### Post by PrimoTurbo on 2008-06-12
Is there a simple calendar program avalible in the repos? Kind of like the one gnome and windows uses? Just shows months/days maybe time but not needed? Will be using it with openbox and fbpanel. Thanks.

---

### Post by PrimoTurbo on 2008-06-12
Well I found xcalendar it's not bad, kind of ugly. Anything else more recent?

Also is there a simple volume control program, a bit more simple then gnome-volume-control if possible. Able to change the overall main volume? Thnx

---

### Post by Mateo on 2008-06-12
orage is the xfce calendar program.  it is pretty lightweight.

---

### Post by Ripfox on 2008-06-12
Osmo is light and awesome.

---

### Post by Mateo on 2008-06-12
Osmo is another that i was thinking of, but couldn't remember the name.  it's pretty good.

---

### Post by PrimoTurbo on 2008-06-12
> **Ripfox said:**
> Osmo is light and awesome.

I heard about it before, but it's not in repos :(

---

### Post by Ripfox on 2008-06-12
[http://ubuntuforums.org/showthread.php?t=616116](http://ubuntuforums.org/showthread.php?t=616116)

---

### Post by PrimoTurbo on 2008-06-12
K just built it, it looks awesome going to use it.

So does anyone know a simple volume/sound manager?

---

### Post by Ripfox on 2008-06-12
Kool

---

### Post by chris4585 on 2008-06-12
for calender 

> cal -3

for volume mixer

> alsamixer

if you're using fbpanel check out my sig, you might find it useful.  Also add these plugins to your fbpanel profile for controlling volume easily.


```
Plugin {
    type = launchbar
    config {
        button {
            icon = audio-volume-high
            tooltip = Adjust volumes
            action = amixer -q set PCM 10+ unmute
        }
    }
}

Plugin {
    type = launchbar
    config {
        button {
            icon = audio-volume-low
            tooltip = Adjust volumes
            action = amixer -q set PCM 10- unmute
        }
    }
}
```

---

### Post by nick09 on 2008-06-12
Click your date an time on your desktop, select a date set up the setting and you are ready to go.

---

### Post by cardinals_fan on 2008-06-12
> **nick09 said:**
> Click your date an time on your desktop, select a date set up the setting and you are ready to go.
What?

---

### Post by Ripfox on 2008-06-12
> **nick09 said:**
> Click your date an time on your desktop, select a date set up the setting and you are ready to go.

Yea, what? :lolflag:

---

### Post by nick09 on 2008-06-12
> **Ripfox said:**
> Yea, what? :lolflag:

See this screenshot:
[http://i30.tinypic.com/2je1hkx.png](http://i30.tinypic.com/2je1hkx.png)

---

### Post by chris4585 on 2008-06-12
We're talking about Openbox not Gnome though

> **PrimoTurbo said:**
> Will be using it with openbox and fbpanel. Thanks.

---

### Post by KingTermite on 2008-06-12
Google Calendar?

So many simple tools like this are easily usable from Google. If you have a Google Email account, check out iGoogle (and all the gadets available).

[www.google.com/ig](www.google.com/ig)  (my home page)

Also, there is a free tool called OggSync or something like that which you can use to sync MS Outlook with Google calendar. Its great to sync Google with my calendar at work (forced to use MS of course).

---

### Post by PrimoTurbo on 2008-06-12
> **chris4585 said:**
> for calender 



for volume mixer



if you're using fbpanel check out my sig, you might find it useful.  Also add these plugins to your fbpanel profile for controlling volume easily.


```
Plugin {
    type = launchbar
    config {
        button {
            icon = audio-volume-high
            tooltip = Adjust volumes
            action = amixer -q set PCM 10+ unmute
        }
    }
}

Plugin {
    type = launchbar
    config {
        button {
            icon = audio-volume-low
            tooltip = Adjust volumes
            action = amixer -q set PCM 10- unmute
        }
    }
}
```

Thats so awesome man, i'm messing with it right now. I changed it to around 3 and from PCM to Master. Going to make some custom icons post the results here. Thanks, your ubuntu fbpanel thing is pretty sweet also.

---

### Post by PrimoTurbo on 2008-06-12
This is pretty awesome. Thanks for the idea.

[[img]http://xs128.xs.to/xs128/08245/2008-06-12-230626_1280x1024_scrot760.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs128&d=08245&f=2008-06-12-230626_1280x1024_scrot760.png)

```
Plugin {
    type = launchbar
    config {
        button {
            icon = gnome-volume-control
            image = ~/Files/System/Customize/Icons/Single/Audio.png
            tooltip = Volume Control
            action = gnome-volume-control
        }
    }
}

Plugin {
    type = launchbar
    config {
        button {
            image = ~/Files/System/Customize/Icons/Single/AudioMinus.png
            tooltip = Decrease Volume
            action = amixer -q set Master 3- unmute
        }
    }
}

Plugin {
    type = launchbar
    config {
        button {
            image = ~/Files/System/Customize/Icons/Single/AudioPlus.png
            tooltip = Increase Volume
            action = amixer -q set Master 3+ unmute
        }
    }
}

Plugin {
    type = tclock
    config {
        ClockFmt = %r
        TooltipFmt = %A %x
        Action = osmo
    }
}

```

---

### Post by chris4585 on 2008-06-12
> **PrimoTurbo said:**
> Thats so awesome man, i'm messing with it right now. I changed it to around 3 and from PCM to Master. Going to make some custom icons post the results here. Thanks, your ubuntu fbpanel thing is pretty sweet also.

Thanks, yeah with openbox sometimes you need to think outside the box, kinda ironic lol

nice icons btw

---

### Post by urukrama on 2008-06-13
If you want a light desktop calendar (without the agenda part), try xdkcal. Otherwise, I recommend osmo or orage.

> **PrimoTurbo said:**
> So does anyone know a simple volume/sound manager?

See [here]("http://urukrama.wordpress.com/2007/12/19/managing-sound-volumes-in-openbox/").

---

### Post by scouser73 on 2008-06-13
I'd suggest Sunbird, which is in the repos,and is really good, in my opinion.

---

### Post by ellis rowell on 2008-06-13
I use a program which I first used on the Amiga, I then obtained a PC version which the which the programmers had made free but retain the copyright. It is Digita Organiser, has a calender, diary, tasks and address book. As it is an .exe file it has to run under Wine. Most Windows PC programs won't run under later versions of Windows (look at the problems with Vista), but this one runs under any version.

---

### Post by trash on 2009-05-12
> **scouser73 said:**
> I'd suggest Sunbird, which is in the repos,and is really good, in my opinion.

Sweet! Glad it's still around lol

---

