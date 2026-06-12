---
title: "Print Screenshot Not Working, New Gazelle"
date: 2020-02-27
forum: System76 Support
---

### Post by sdsurfer on 2020-02-27
System76 Gazelle, 12 cores, 16GB RAM, 18.04 Ubuntu, fresh out of the box.

My personal System 76 Gazelle I bought a couple years ago and when hardware upgrades came around in my company they bought another one for my workstation. The new Gazelle been running three days. A lot of software installs, no system changes.

The*** Fn+PrtSc*** does not work. I have removed the shortcut assignments in keyboard settings, tried custom ones, been to 20 or so S.O. posts, none of the proposed solutions work, its as if the PrtScr key is just disabled. The default screenshot action in settings is just "Print" (sans Fn key.)

My personal Gazelle came with 17-something and I upgraded to 18.04, screen shot works fine (and don't recall having challenges with it.)

I can search the computer for and run gnome-screenshot, so the screenshot software is fine. 

When I press the  **Fn** key syslog gives me *"unknown key pressed"* then* "use 'setkeycodes 6f <keycode>' to make it known"* (sorry had to type it out on another computer.) Interestingly enough, pressing PrtSc doesn't register at all in the syslog, which tells me (at least) it's a recognized key.

Any ideas? Should I attempt to chase down the suggested command and run it? Seems like if it's assigned Print in the keyboard settings, Fn key is irrelevant.

---

### Post by sdsurfer on 2020-03-03
This is now solved, though not sure why, posting the journey here in the event anyone else is experiencing the same. 

Many S.O. posts recommend changing hotkeys, deleting existing ones, creating custom ones, none of this worked for whatever reason. I did look into the issue with the Fn key and this key is a modifier that in itself doesn't send anything to the system, it only modifies the signal sent to the system in combination with other keys.

We confirmed (in another way) the hardware is fine. In a terminal run

```
xev
```

and press the **PrtSc** key. If you see output, the key is talking to the system.

As mentioned, gnome-screenshot works fine on it's own. So we have a signal sent to the system, the software runs, they are just not connecting. When you create custom screenshots, it asks you to press the keys on the keyboard to enter the key mapping. When you enter gnome-screenshot in the command to execute, it appears to save, it just doesn't work.

The problem is complicated by the fact that there are **three** places you can modify key mappings. The first is dconf and dconf-editor, which I **think** just sets up a back end configuration for settings, it may or may not be used as Gnome/Unity has it's own place for such settings, as follows. What is unclear to me is the precedence that the settings in dconf take in the GUI. At any rate the key mappings can be found in org/gnome/settings-daemon/plugins/media-keys.

The second place key mappings can be found is "Search your  computer->Settings." In the keyboard section you will find multiple mappings for screenshots. A black arrow-box means the setting has been modified; "clicking" it resets it to default.

The third place you can find key mappings is in "Search your computer->System Settings" in the keyboard section, then the shortcuts tab. I think you will find changing a setting in any one of these changes it in the others. Why they are in three places, I don't know.

So what fixed it? I don't know that either. The final action was to reset all to default and reboot and voila, it works.

 My best guess is by changing the settings, it may have changed, added, or written something that wasn't there before, but what it added was incorrect. When I reset all to default it may have caused it to work. Surely all the hopping on one foot under the light of a full moon had nothing to do with it.

---

