---
title: "Problem with vlc"
date: 2018-03-19
forum: Ubuntu Development Version
---

### Post by cariboo on 2018-03-19
I have this problem where vlc when running is just huge, is there anything I can do to make it normal size. See screenshot

---

### Post by #&amp;thj^% on 2018-03-19
What Version? Is it the snap vlc?
You can use shortcuts to re-size to various preset values:

    ALT+1 Quarter size
    ALT+2 Half size
    ALT+3 Original size
    ALT+4 Double size

You can change the shortcuts by going to Tools>Preferences>Hotkeys

---

### Post by cariboo on 2018-03-19
I'm running vlc 3.0.1, using the hotkeys doesn't make any difference

---

### Post by mc4man on 2018-03-19
There is a long time issue where if vlc closed in a maximized state then all subsequent vids would be displayed in a maximized window no what what their actual size.
(- may of only been seen in unity where a max'ed window merges with panel..

What you show seems quite different, never seen that before. I'd try deleting ~/.config/vlc  (has 2 files, vlcrc & vlc-qt-interface.conf). If wanting to try to keep current vlc settings delete the .conf only

If using a snap then a little different,  in ~/snap/vlc/XXX   or just delete the whole ~/snap/vlc/XXX/ folder, it'll rebuild on vlc start.

---

### Post by cariboo on 2018-03-19
Removing the two files in ~/.config/vlc didn't help either. I had a similar problem with qbittorrent, running the the following command solved the problem, but doesn't work for vlc:

```
QT_AUTO_SCREEN_SCALE_FACTOR=0
```

---

### Post by monkeybrain20122 on 2018-03-19
Is that KDE? Don't have a problem here. vlc 3.0.1 from repo.

---

### Post by cariboo on 2018-03-19
> **monkeybrain20122 said:**
> Is that KDE? Don't have a problem here. vlc 3.0.1 from repo.

I'm running Ubuntu on that system.

---

### Post by monkeybrain20122 on 2018-03-20
Wayland or xorg?

---

### Post by cariboo on 2018-03-20
> **monkeybrain20122 said:**
> Wayland or xorg?

Xorg, as I'm running an Nvidia graphics card.

---

### Post by #&amp;thj^% on 2018-03-20
I'm sure you have looked through the various settings. :)
Just a passing thought.
On vlc>>Tools>>Customize Interface>>(Top Tabs)>>Fullscreen Contorller>>
Togel some of the options like "Flat Bottom" "Big Button" "Native Slider"
On my end I notice if Set "Big Button" I get a closer view as to what you are now seeing.
And might be fun to see what happens when the Advanced Control is set to hidden.
And in Select profiles: might be fun to see the differences with changes

---

### Post by SeijiSensei on 2018-03-21
I've had similar problems running certain non-native apps on KDE like Handbrake and mkvtoolnix-gui. Oftentimes important buttons at the bottom of the window are cut off.  I can resolve it in the latter by futzing with the minimize button but gave up using Handbrake.

---

### Post by mc4man on 2018-03-21
What's not mentioned is if this is on a high rez/HiDPI screen?
If so would be worth a bug report
I'd check another qt5 app first, ex. smplayer

---

### Post by SeijiSensei on 2018-03-21
I never have any problems running smplayer in KDE.  Have done so for years including now on the 18.04 daily.

---

### Post by #&amp;thj^% on 2018-03-21
> **SeijiSensei said:**
> I never have any problems running smplayer in KDE.  Have done so for years including now on the 18.04 daily.

+1 But no KDE for me>>> but thumbs up for smplayer and even started playing with gnome-mvp "2.32+18.04~pre6" not as polished as the former 2 mentioned, but it works well enough with keyboard short cuts.

---

### Post by cariboo on 2018-03-21
> **mc4man said:**
> What's not mentioned is if this is on a high rez/HiDPI screen?
If so would be worth a bug report
I'd check another qt5 app first, ex. smplayer

Nope, I'm running a 4 year old BenQ 23" and an even older Samsung 32" TV. I tried smplayer, I thought it looked a bit strange, but running it on my laptop with Xubuntu 18.04 it looks exactly the same

---

### Post by VMC on 2018-03-21
Have you tried re-installing.

---

### Post by cariboo on 2018-03-22
> **VMC said:**
> Have you tried re-installing.

No, just purged vlc, ran autoremove and autoclean, then reinstalled, there is no difference.

---

### Post by sudodus on 2018-03-22
How is vlc working in *live* sessions of the current versions of Ubuntu in the affected computer, and in another computer?

Maybe testing that can help identify what is causing this problem.

---

### Post by Dmitry_Riakhovsky on 2018-03-25
Lubuntu 18.04 proprietary driver nvidia

Very large icon size in media player vlc. Only in vlc

[IMG]http://images.vfl.ru/ii/1521978759/b485a5ed/21107764.png[/IMG]

---

### Post by adamchristensen on 2018-03-27
FWIW, I have seen the same issue with VLC 3.0.1 on Arch Linux. I have a strong feeling it's HiDPI related. When I move VLC to a low res screen, the buttons and font change to a normal size. I don't see any options to disable this "feature". If no one has filled out a bug report upstream with VLC, I think I will be doing that.

---

### Post by cariboo on 2018-05-20
Just an update, then I'll close the thread.

I solved the problem, my Samsung 32" tv was being detected as a 9" screen when using a HDMI cable. Using a VGA cable the tv/monitor is detected as a 32" so everything looks normal again.

---

