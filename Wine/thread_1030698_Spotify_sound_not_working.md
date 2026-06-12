---
title: "Spotify sound not working"
date: 2009-01-04
forum: Wine
---

### Post by tehforum on 2009-01-04
Hello,

I followed these instructions 

[https://www.spotify.com/en/help/faq/wine/](https://www.spotify.com/en/help/faq/wine/)

And when I test the audio on WINE, it says

Error
Audio test failed!

So that means Spotify will not work, and I am stuck for ideas on how to fix this.

I re-installed WINE to see if that was a problem, but to no avail.

Any help is appreciated. And my version of Ubuntu is 7.10 Gutsy Gibbon.

Thank you!

---

### Post by tehforum on 2009-01-07
bump.

---

### Post by SKLP on 2009-01-12
You can try to go to winecfg and change wine to use OSS.
And then start wine with aoss wine <program>
(requires the alsa-oss package)
in newer versions of ubuntu, you can use padsp wine instead.
YMMV

---

### Post by cogadh on 2009-01-12
If PulseAudio is the problem, you can just temporarily remove it from the equation. Try running the app like this:
```
pasuspender wine "C:\Program Files\Spotify\spotify.exe"
```

---

### Post by tehforum on 2009-01-12
> **SKLP said:**
> You can try to go to winecfg and change wine to use OSS.
And then start wine with aoss wine <program>
(requires the alsa-oss package)
in newer versions of ubuntu, you can use padsp wine instead.
YMMV

```
wine: could not load L"c:\\windows\\system32\\spotify.exe": Module not found
```

> **cogadh said:**
> If PulseAudio is the problem, you can just temporarily remove it from the equation. Try running the app like this:
```
pasuspender wine "C:\Program Files\Spotify\spotify.exe"
```

```
~$ pasuspender wine "C:\Program Files\Spotify\spotify.exe"
bash: pasuspender: command not found
```

Thank for all your help so far, but in the code tags I encountered these errors.

How would I go about fixing these?

Thanks again.

---

### Post by cogadh on 2009-01-12
That's because I'm an idiot. Its not "pasuspender" its just "pasuspend".

---

### Post by tehforum on 2009-01-12
You're no idiot. :)

> pasuspend wine "C:\Program Files\Spotify\spotify.exe"
bash: pasuspend: command not found



But it didn't work.

Thanks again for your replies.

---

### Post by cogadh on 2009-01-13
Hmmm... I wonder if the pasuspend command is part of an extra PulseAudio package I installed? Unfortunately, I don't have access to Ubuntu machine right now, so I can't check.

---

### Post by tehforum on 2009-01-14
Also doesn't work with Windoze XP on a separate partition. But Windows for me doesn't have sound working for anything for some reason.

---

### Post by cogadh on 2009-01-14
Is it possible you have a hardware issue with your sound card? That would seem likely since sound isn't working in Windows either.

---

### Post by tehforum on 2009-01-15
But sound works on Ubuntu other than WINE. 

Or is it Windows app I cannot have sound on :S

---

### Post by tehforum on 2009-01-22
Bump.

[COLOR="White"]Sorry if you don't like bumps.[/COLOR]

---

### Post by olecr on 2009-02-16
I can confirm that pasuspender works.

i.e.
```

$ pasuspender wine "C:\Program Files\Spotify\spotify.exe"

```

Pasuspender is provided by pulseaudio-utils:
```
oc@oc-laptop:~$ dpkg-query -S `which pasuspender`
pulseaudio-utils: /usr/bin/pasuspender

```

(Ubuntu Jaunty 9.04)

---

### Post by SKLP on 2009-04-12
7.10 does not use pulseaudio so no point to use pasuspend

---

### Post by thewOndErEr57 on 2009-06-07
For those of you who are still having problems with Spotify on either Jaunty, Intrepid, or Hardy (i.e. using pulseaudio), then it is likely to be an issue with the pulseaudio plugin for wine.

I have posted a solution to the problem, which simply involves in disabling pulseaudio in wine (therefore keeping pulseaudio running for your native apps).

It's for Fedora, but the same exact same rules apply.

Enjoy! 
[B][I]
[Sound Fix for Spotify + pulseaudio]("http://linuxsoftwareblog.com/?p=189")[/I][/B]

---

### Post by captsisko on 2010-08-24
> **cogadh said:**
> Is it possible you have a hardware issue with your sound card? That would seem likely since sound isn't working in Windows either.

I have the same issue. I just successfully installed spotify on ubuntu 10 and logged in to my spotify account.

However, no music will play because apparently "there is a problem with" my sound card. But, as I was reading the error message, I was watching and listening to some video content.
Also, on the same computer I have a windows partition. Using the same soundcard spotify plays just fine on the windows side.

So, I'm confused why it's working on one operating system and not another.
**Can someone please help ?** ;)

---

### Post by captsisko on 2010-08-25
> **captsisko said:**
> I have the same issue. I just successfully installed spotify on ubuntu 10 and logged in to my spotify account.

However, no music will play because apparently "there is a problem with" my sound card. But, as I was reading the error message, I was watching and listening to some video content.
Also, on the same computer I have a windows partition. Using the same soundcard spotify plays just fine on the windows side.

So, I'm confused why it's working on one operating system and not another.
**Can someone please help ?** ;)


Ok, I got it working.

Some more research suggested I need to execute ```
sudo apt-get install pulseaudio
```

Upon doing that, my wine audio test was successful and I restarted my computer ........ Spotify never sounded more beautiful

---

