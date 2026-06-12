---
title: "Gnome sends double-click when I only single-click after installing gok"
date: 2009-12-02
forum: System76 Support
---

### Post by samalex on 2009-12-02
Hi,

On my PanP5 last week I installed the gok package to add an onscreen keyboard... yeah being lazy while in bed thinking I could do everything from the mouse.  Needless to say it didn't work as I expected, and instead Gnome added all this accessibility stuff plus some blue circle icon to the task bar with a guy in it --like you'd see on the outside of the men's restroom.

Anyway, I uninstalled the gok package but the icon remained.  I don't mind that so much, but somehow it's enabled something where when I single click it interprates it as a double click.  So like clicking on the menu on the task bar it thinks I'm double clicking so it opens then closes really quick.  Single-clicking on emails in Thunderbird opens the email in a new window as if I double-clicked.

Does anyone have suggestions on how to disable this?  This happens everyplace, including in Windows which is loaded through virtual box, so I take it it's a global setting in Gnome.  

Thanks for any advise or suggestions...  Also this is on my PanP5 running Ubuntu 9.04 with all updates.

Sam

---

### Post by thomasaaron on 2009-12-02
Nice! Let me know how that works out! :popcorn:

Just joking. From a tech support perspective, every once in a while something like this is good comic relief. :D

Then the feeling of dread comes when you think: "Man, if I can't figure this one out quick, I'll have to duplicate it on my *own* machine!"

So, the icon still showing up would *seem* to indicate that *something* related to gok is still running.

Did you try looking in Start Up Applications to see if there is some daemon being turned on?

---

### Post by thomasaaron on 2009-12-02
...you also might try reinstalling it and then --purge removing it....

sudo apt-get install gok
sudo apt-get --purge remove gok

That *should* get rid of the configurations.
[B]
*Should.*[/B]

---

### Post by samalex on 2009-12-03
Hi Thomas,

I tried all that but the little dude icon is still there.  I did find a workaround of sorts by going into the mouse settings and changing the double-click timeout to the shortest setting because I think what was happening is I'd click, and if I clicked anyplace else within a second or two it picked it up as the second click of a double-click causing some funky stuff.

So changing the mouse settings has seemed to work, but it's still weird...

Thanks for all the info..

Sam

---

### Post by samalex on 2009-12-03
Well that wasn't it...  I've ran more tests, and it doesn't happen all the time.  If I open Thunderbird and go into the Preferences where you can Preview the new mail notification sound, clicking on it at first plays the sound once, but if I single-click on it once more a few seconds later it plays twice or double-click plays it three times. If I click in another window and back the first click once more plays it once but then another single click up to 4-5 seconds later plays the preview sound twice.

This is happening throughout Gnome where clicking on menus in any app the menu opens then closes.  Single clicking on an email in Thunderbird opens it in another windows and so forth.  I'm at a loss on what to do, so if I can't find some fix I'm at the point of resetting my Gnome settings back to default which would suck.  I'm about to test with another user to see if it happens there, and if not is there a config file I can compare between the accounts to see what's different in the mouse configuration?  

Thanks for any feedback...

Sam

---

### Post by thomasaaron on 2009-12-03
Maybe .gconf
Maybe .gnome2

Is there a .gok directory in your home dir?

---

### Post by thomasaaron on 2009-12-03
Possible leads...
[https://wiki.ubuntu.com/Accessibility/Reviews/GOK](https://wiki.ubuntu.com/Accessibility/Reviews/GOK)

A couple of things here...

1. Have you checked your xorg.conf to see if there are any mouse-specific settings in it?

2. Looks like gok configs might be saved in /usr/share/gok

---

### Post by samalex on 2009-12-03
> **thomasaaron said:**
> Possible leads...
[https://wiki.ubuntu.com/Accessibility/Reviews/GOK](https://wiki.ubuntu.com/Accessibility/Reviews/GOK)

A couple of things here...

1. Have you checked your xorg.conf to see if there are any mouse-specific settings in it?

2. Looks like gok configs might be saved in /usr/share/gok

Thanks, I'll check these out.  I did login as another user and the problem continues there, so it's definitely not user specific.

I'll post back if I find anything.  Thanks,

Sam

---

### Post by samalex on 2009-12-03
Hi Thomas,

Though I've already completely removed the gok package once I'm trying to remember if I rebooted afterwards since possibly Gnome needs to restart for the settings to take affect.  I had reinstalled it but just now complete removed it once more and rebooted the computer.  When I went back in and tried to click a few times a message about sticky keys came up asking if I wanted to deactivate it, which I did.  Now the problem seems to be gone, though I'll keep testing it to see for sure.

So I'm wondering if sticky keys plus whatever gok added hosed something... not sure.  I still have that little Men's Restroom icon on my toolbar (Accessibility Properties), but I'll try to remove that another day since he's just hanging out and not bothering anyone for now :)  

Thanks again for your help...

Sam

---

