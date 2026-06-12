---
title: "save session for future logins"
date: 2014-09-17
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-09-17
I checked it off in the logout dialog box but I don't how how it works , how to log in to the saved session after restart.

---

### Post by Toz on 2014-09-17
By default, if you check the box on logout, it will reload the same open applications on the next login. The information is stored in ~/.cache/sessions.

If you want to manage multiple sessions, you need to enable the session chooser (Settings Manager >> Session and Startup >> General tab >> Display Chooser on Logn"). The next time you login, you will be prompted which session to load. Initially, there will only be one, the Default Session. If you click on the New Session button and name it, you will create a new session and the current session information will be saved there. 

Then on next login, when prompted with the session chooser, you will see two entries.

You can create multiple sessions, each with different open applications, workspace layouts, etc, and select on login which session to use.

---

### Post by ventrical on 2014-09-17
Awesome concept. It does create new sessions but will not open the apps_ ie; I created a new session called 'test1' and loaded ff and abiword, then logged off. When I logged in, the menu came up and had a mini-pic of the desktop but when I double clicked all I got was the original startup desktop of xubuntu, however, the default desktop has gnome-terminal on it and when i double click to log in to that session it comes up ok.

Regards...

btw .. is this feature exclusive to xubuntu only?

I am experimenting with this on fully updated utopic.

edit:
Seems like gnome-terminal is the only app that will come up in the saved sessions. Utopic bug perhaps?

---

### Post by Toz on 2014-09-17
> btw .. is this feature exclusive to xubuntu only?This feature is an Xfce feature and is available on all distros that ship Xfce.

> Utopic bug perhaps? I don't personally use this feature, but if its not working as it should, then by all means, create a bug report. I'll see if I can find some time to look into this as well.

---

### Post by Elfy on 2014-09-17
I've set mine to save and give me choice at login - I'll see what occurs in the morning and post here.

Though if there is a bug it might be a bit late to get a fix through in 14.10.

---

### Post by ventrical on 2014-09-17
Thanks.

 I just think it a very convenient tool, not available in other flavors.

---

### Post by Elfy on 2014-09-18
didn't appear to work here - can't find an existing bug on bugzilla

---

### Post by ventrical on 2014-09-18
> **Elfy said:**
> didn't appear to work here - can't find an existing bug on bugzilla


I think I have a 14.04 existing xubuntu install somewhere around here. That little feature is so unique - so I'll try to find x14.04 and see if it works there then get back.

Thanks

---

### Post by ventrical on 2014-09-18
That utility works with 14.04 on xfce desktop , however,  it does the same as 14.10- the default desktop will not display top-bar menu panel.

 Otherwise I can create multiple sessions and log on  with different apps, themes .. etc..

  Since I do not use xubuntu as my default DE I would not know exactly what program module/app to file a bug against. Then perhaps one of you more intimate with xubuntu that has duplicated the bug can report it?

 Why should another diamond in the rough get left at the wayside?

Regards..

---

### Post by Toz on 2014-09-18
Just finished some testing.

Three scenarios:

1. Xfce built from GIT on Arch.
2. Xubuntu 14.04
3. Xubuntu 14.10

In all scenarios:
- any sort of settings (appearance themes, wallpapers, etc) were not restored. The last setting was used in each session.
- any applications open on workspaces other than the first, were not restored.

Scenario #1 (Xfce git):
- Works well. Applications opened on first workspace were restored. Applications tested included firefox, thunar, terminal, cmus (in terminal), sound settings.

Scenario #2 (Xubuntu 14.04):
- Also works well. Applications opened on first workspace were restored. Applications tested included firefox, thunar, terminal, gmusicbrowser, sound settings.

Scenario #3 (Xubuntu 14.10):
- This one was messy. Initially, the default session was not restoring properly. I had to manually "rm -rf ~/.cache/sessions" to get it to start restoring apps.
- Only the terminal app was being restored - the others were not. Apps tested included firefox, thunar, terminal, gmusicbrowser and sound settings.

Bug reports pending....

EDIT:
- Xfce bug report: [https://bugzilla.xfce.org/show_bug.cgi?id=11173]("https://bugzilla.xfce.org/show_bug.cgi?id=11173")
- Xubuntu 14.04 bug report: [https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1371144]("https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1371144")
- xubuntu 14.10 bug report: [https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1371149](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1371149)

---

### Post by ventrical on 2014-09-18
I 'me tooed' them

+1 

Thanks :)

---

### Post by ventrical on 2014-11-13
Bump.

So nothing yet eh?

[https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1371144](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1371144)

---

