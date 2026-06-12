---
title: "Gnome extension &quot;places&quot; is missing"
date: 2014-03-27
forum: Ubuntu Development Version
---

### Post by cincibluer6 on 2014-03-27
Didn't see any results in a search.

Installed Ubuntu Gnome 14.04 beta 1 and all was well. Somehow I lost my places extension that puts a simple tab up on the top bar (akin to Gnome 2.)
No other extension is missing as far as I know.
I even went so far as to download it from github and place it in the user extension folder- no dice.
Then I did sudo nautilus and placed it in the system extension folder- again nothing. (These both were checked after closing tweak tool and rebooting gnome shell.)

Not sure what else to do. I have the applications extension but I never use it. The places one is handy though.
Any help is appreciated.

---

### Post by sgage on 2014-03-27
> **cincibluer6 said:**
> Didn't see any results in a search.

Installed Ubuntu Gnome 14.04 beta 1 and all was well. Somehow I lost my places extension that puts a simple tab up on the top bar (akin to Gnome 2.)
No other extension is missing as far as I know.
I even went so far as to download it from github and place it in the user extension folder- no dice.
Then I did sudo nautilus and placed it in the system extension folder- again nothing. (These both were checked after closing tweak tool and rebooting gnome shell.)

Not sure what else to do. I have the applications extension but I never use it. The places one is handy though.
Any help is appreciated.

Have you tried going to extensions.gnome.org? It may be a simple matter of updating your version from there. Or you can fiddle with the metadata.json as described many times. 

The Places extension is working just fine here - fully updated Ubuntu Gnome as of today...

---

### Post by cincibluer6 on 2014-03-27
I did try that and I switch it to on, choose to install, and it goes right back to off with no error message or anything.

---

### Post by sgage on 2014-03-28
I think I know what the problem is. I just remembered that Places is now packaged with the distro, and it conflicts with the one you might have in ~/.local/share/gnome-shell/extensions. Just delete Places folder from there, restart GS, and you'll be good to go. You might have to go into Tweak Tool to turn it on again.

---

### Post by cincibluer6 on 2014-03-28
I figured as much and I deleted the local one and tried again to place/turn on/whatever to get it into system but no go. One thing I HAVEN'T tried though is using a guest account to do so. Maybe I'll make another sudo/admin account and see if I can't get it to work from there.

---

### Post by cincibluer6 on 2014-04-01
Never did figure it out. I went ahead and reinstalled Ubuntu (easy when you have a separate home partition) and it worked out well. I was a little leery as I had originally done Ubuntu on GPT, then installed Windows 8, and the only real way to switch which one was startup (since I didn't configure grub to boot first and then display a menu.) But the reinstall did fine and now I get a proper grub menu and everything.

Kudos to the Ubuntu devs as the installs and configuring keep getting better each release (especially the Gnome Ubuntu devs as well.)

---

