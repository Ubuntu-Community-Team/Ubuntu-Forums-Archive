---
title: "Integrate Pidgin with keyring"
date: 2008-05-02
forum: Ubuntu Brainstorm
---

### Post by chromex on 2008-05-02
It would be very nice to store Pidgin account passwords in the system keyring rather than in a plain text file (cat ~/.purple/accounts.xml | grep password). This can be avoided by not saving passwords but when you have four accounts on four different protocols that you log into a few times a day, it becomes annoying. Plus, many laptop users I believe already use the key ring for things like wireless passwords and such. This was achieved in Adium (also uses lib purple) on OSX and while I'm unfamiliar with how Ubuntu's keyring backend works I think this would be a fantastic addition to the system.

I intend on looking into the issue myself here in the coming weeks but I'm curious if anyone has any input on this and/or knows about the backend and has ideas or suggestions.

---

### Post by luisromangz on 2008-05-02
The problem is that Pidgin is not a Gnome app, so integrating it with the Gnome keyring will make it depend on that.

---

### Post by smartboyathome on 2008-05-02
> **luisromangz said:**
> The problem is that Pidgin is not a Gnome app, so integrating it with the Gnome keyring will make it depend on that.

And this is the reason it cannot happen. It is available for Windows also, and that doesn't have a gnome-keyring available.

---

### Post by benanzo on 2008-05-02
> **smartboyathome said:**
> And this is the reason it cannot happen. It is available for Windows also, and that doesn't have a gnome-keyring available.

That has no bearing on why it couldn't happen.  Last I checked Windows didn't have libnotify but we still manage to use it to display messages in gnome.  This could be done as a gnome-specific plugin, therefore not forcing a dependency.  Ubuntu could then ship Pidgin with this plugin enabled by default same as it ships Firefox with Ubufox enabled by default.

---

### Post by Sukarn on 2008-05-02
> **benanzo said:**
> That has no bearing on why it couldn't happen.  Last I checked Windows didn't have libnotify but we still manage to use it to display messages in gnome.  This could be done as a gnome-specific plugin, therefore not forcing a dependency.  Ubuntu could then ship Pidgin with this plugin enabled by default same as it ships Firefox with Ubufox enabled by default.

I can imagine some people coming from other distros complaining "why don't my stored accounts work?"

Other than that, I think its a GREAT idea.

---

### Post by aaaantoine on 2008-05-02
> **chromex said:**
> It would be very nice to store Pidgin account passwords in the system keyring rather than in a plain text file (cat ~/.purple/accounts.xml | grep password). This can be avoided by not saving passwords but when you have four accounts on four different protocols that you log into a few times a day, it becomes annoying. Plus, many laptop users I believe already use the key ring for things like wireless passwords and such. This was achieved in Adium (also uses lib purple) on OSX and while I'm unfamiliar with how Ubuntu's keyring backend works I think this would be a fantastic addition to the system.

I intend on looking into the issue myself here in the coming weeks but I'm curious if anyone has any input on this and/or knows about the backend and has ideas or suggestions.

*Runs **cat ~/.purple/accounts.xml | grep password** in his terminal*

Aw, crap.  +1.

[Ubuntu brainstorm - Pidgin master password](http://brainstorm.ubuntu.com/idea/4728/)

---

### Post by damoxc on 2008-05-04
it could quite easily be in libpurple core really. just have an abstraction layer for storing the passwords, and use the appropriate backend according to which platform pidgin is being run from, ie. windows uses the plain text xml format, whereas with the presence of gnome-keyring it uses gnome-keyring.

---

