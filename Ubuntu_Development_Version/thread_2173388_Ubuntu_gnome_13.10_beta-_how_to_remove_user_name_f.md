---
title: "Ubuntu gnome 13.10 beta- how to remove user name from top panel"
date: 2013-09-09
forum: Ubuntu Development Version
---

### Post by williammanda on 2013-09-09
Hello
Loaded Ubuntu gnome 13.10 beta and can't find out how to remove the user name from the top panel. I looked in shell ext's but the one that I found says you don't need it since you can goto settings-privacy and change it but I don't see that anywhere.
Thanks

---

### Post by ZoiaGuyver on 2013-09-09
There should be the option in System Settings under privacy.

---

### Post by williammanda on 2013-09-09
> **ZoiaGuyver said:**
> There should be the option in System Settings under privacy.

I don't see a privacy icon.

---

### Post by williammanda on 2013-09-09
This is one way to do it:
Use dconf...change:
org-gnome-desktop-privacy
uncheck show-full-name-in-top-bar

---

### Post by philinux on 2013-09-09
> **williammanda said:**
> Hello
Loaded Ubuntu gnome 13.10 beta and can't find out how to remove the user name from the top panel. I looked in shell ext's but the one that I found says you don't need it since you can goto settings-privacy and change it but I don't see that anywhere.
Thanks

What happens if you type privacy in the dash?

---

### Post by Hewjr100 on 2013-09-09
sudo apt-get install unity-tweak-tool

Run unity tweak tool click on panel and you will see a check box to show hide name.

Henry

---

### Post by su:bhatta on 2013-09-10
> **Hewjr100 said:**
> sudo apt-get install unity-tweak-tool

Run unity tweak tool click on panel and you will see a check box to show hide name.

Henry


I did it with the simple extension from extensions.gnome.org:
heres the link: [https://extensions.gnome.org/extension/156/quit-button/](https://extensions.gnome.org/extension/156/quit-button/)

It replaces the user name with quit button.. theres another extension in those pages too, 'Remove User Name', if I am not mistaken.

Does Unity Tweak Tool work with Gnome 3.8?

---

### Post by su:bhatta on 2013-09-10
> **philinux said:**
> What happens if you type privacy in the dash?

Nothing happens, nothing is displayed, strange.

I found in extensions.gnome.org the developer of the extension 'Remove User Name' has also said that his extension is not needed in Gnome 3.8  as in  Settings/Privacy User name can be turned off. ([https://extensions.gnome.org/extension/106/remove-user-name/](https://extensions.gnome.org/extension/106/remove-user-name/))

But there is no Privacy in Settings menu or elsewhere!

---

