---
title: "Firefox loses focus whenever Thumbnail Zoom plus extension is used"
date: 2012-09-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jokerdino on 2012-09-07
I am on gnome-shell 3.6 (3.5.91) right now. Whenever I use Thumbnail Zoom plus addon ([https://addons.mozilla.org/en-US/firefox/addon/thumbnail-zoom-plus/](https://addons.mozilla.org/en-US/firefox/addon/thumbnail-zoom-plus/)) in Firefox, Firefox loses focus.

This does not happen in Xfce, LXDM or Unity. It only happens in gnome-shell. 

Can anyone else reproduce this and should I file a bug report against Firefox or the addon or the gnome-shell?

---

### Post by DavidAdler on 2012-09-08
Hello, I am the developer of Thumbnail Zoom Plus.  I have heard a couple reports of this kind of problem, but haven't been able to reproduce it since it doesn't happen on the flavor of Linux I'm running.  I'd be interested to hear how wide-spread the problem is.

You might try changing the setting of the Thumbnail Zoom Plus setting "Pop-up Takes Keyboard Focus" and see if that helps.

---

### Post by jokerdino on 2012-09-08
> **DavidAdler said:**
> Hello, I am the developer of Thumbnail Zoom Plus.  I have heard a couple reports of this kind of problem, but haven't been able to reproduce it since it doesn't happen on the flavor of Linux I'm running.  I'd be interested to hear how wide-spread the problem is.

You might try changing the setting of the Thumbnail Zoom Plus setting "Pop-up Takes Keyboard Focus" and see if that helps.

Wow, didn't expect the developer of the addon to show up. Thanks much for creating this extension. It has made my web experience a whole lot better.

And, I have tried disabling the "Pop-up takes keyboard focus" option and it doesn't help. Once I mouse over, say a Reddit sharing a link to imgur, I see the popup of the thumbnail. However, once I move away from the link, the popup goes off and I no longer have the keyboard focus on Firefox. (Edit: Actually, once the pop up shows up, I lose focus and it remains that way even after moving away from the link.)

I would be very much glad to help you test further if you are keen. Thanks again for the otherwise excellent addon!

---

### Post by DavidAdler on 2012-09-09
So basically Firefox loses focus, and you have to click back on Firefox before you can type into Firefox again, or hover another link again, right?

Does your gnome normally give the window under the mouse keyboard focus automatically, or do you have to click to get focus?  On my version of Gnome (2.x) the window under the mouse always has focus so it would be weird (a gnome bug I suppose) if the mouse was over the Firefox window but Firefox didn't have the focus.

Check the Gnome preferences and see if there are any settings (perhaps under Windows) related to focus, and see if they make a difference.

If any Gnome experts on the board have other ideas, that'd be helpful too!

---

### Post by jokerdino on 2012-09-09
> **DavidAdler said:**
> So basically Firefox loses focus, and you have to click back on Firefox before you can type into Firefox again, or hover another link again, right?



Yes, that's exactly it. I have to click again to give Firefox the focus. 

> 
Does your gnome normally give the window under the mouse keyboard focus automatically, or do you have to click to get focus?  On my version of Gnome (2.x) the window under the mouse always has focus so it would be weird (a gnome bug I suppose) if the mouse was over the Firefox window but Firefox didn't have the focus.



No, the default for Window focus mode is by Click. I have the same Click mode for window focus on all the different Desktop environments, eg Unity, XFCE, LXDM and they all work fine. Only GNOME-shell seems to be problematic. 


> 
Check the Gnome preferences and see if there are any settings (perhaps under Windows) related to focus, and see if they make a difference.

If any Gnome experts on the board have other ideas, that'd be helpful too!


I changed the windows focus mode to Mouse and then sloppy, but it still doesn't make any difference. When I mouseover, I see the thumbnail zoomed in but Firefox loses focus as always. Firefox doesn't get focus even when the cursor is above Firefox. A really weird gnome bug I suppose.

---

### Post by DavidAdler on 2012-09-09
When Firefox loses focus, can you tell what window (or pehaps the desktop) has gained focus?  You may be able to tell by the look of the titlebar or by pressing keys and seeing what is affected.  I'm wondering whether the hidden pop-up still has focus, or some other application has focus.

I've been googling for related issues...

It'd be interesting to see if the [Steal My Focus]("https://extensions.gnome.org/extension/234/steal-my-focus/") Gnome extension makes a difference.

Does a similar problem happen with Firefox dialogs?  EG if you do Tools > Downloads to pop up the Downloads window, and close that window via Control-W or clicking its close button, does Firefox get the focus back automatically?

Same question, but for the Thumbnail Zoom Plus preferences dialog -- when opened from the add-ons page and when opened using the 'p' hotkey while a TZP pop-up is displayed.

---

### Post by jokerdino on 2012-09-09
> **DavidAdler said:**
> When Firefox loses focus, can you tell what window (or pehaps the desktop) has gained focus?  You may be able to tell by the look of the titlebar or by pressing keys and seeing what is affected.  I'm wondering whether the hidden pop-up still has focus, or some other application has focus.

I've been googling for related issues...


None of the other windows or Desktop gets the focus back. See image -- [http://i.imgur.com/y5hLFl.jpg](http://i.imgur.com/y5hLFl.jpg)

One interesting thing to note since I switched to sloppy focus mode is that, on subsequent mouseovers on other image links, I can see the popup. But FF still doesn't have the focus. 

> 
It'd be interesting to see if the [Steal My Focus]("https://extensions.gnome.org/extension/234/steal-my-focus/") Gnome extension makes a difference.


Unfortunately, I can't install any of the extensions. I (and a group of others) have a problem with the extensions website. See -- [http://ubuntuforums.org/showthread.php?t=2050183](http://ubuntuforums.org/showthread.php?t=2050183)

> 
Does a similar problem happen with Firefox dialogs?  EG if you do Tools > Downloads to pop up the Downloads window, and close that window via Control-W or clicking its close button, does Firefox get the focus back automatically?

Same question, but for the Thumbnail Zoom Plus preferences dialog -- when opened from the add-ons page and when opened using the 'p' hotkey while a TZP pop-up is displayed.

I tried that and whenever I close it, Firefox gets back the focus. 

And, when I open the TZP preferences from addon and close it back again, Firefox gets the focus back.

However, I am unable to activate the preferences dialog using a hotkey. My guess is because Firefox or the popup doesn't have the focus to begin with.

---

### Post by DavidAdler on 2012-09-09
Does the 'p' hotkey work with the other setting of Popup Takes Keyboard Focus?  I've sometimes seen problems on Linux where it only works when (I think) off.

---

### Post by jokerdino on 2012-09-10
> **DavidAdler said:**
> Does the 'p' hotkey work with the other setting of Popup Takes Keyboard Focus?  I've sometimes seen problems on Linux where it only works when (I think) off.

Just to ensure I wasn't doing the whole thing wrong, I tried this in a different Desktop environment. The p hotkey works for both the settings in Unity but doesn't do anything in gnome-shell for both of the settings. 

When I set the popup to not take the keyboard focus, Firefox ends up losing focus with popup showing up. When I set the popup to take the keyboard focus, Firefox loses focus and the popup doesn't show up. It shows up momentarily for a fraction of a second but goes away very quickly. Subsequently, moving over other image links shows the popup though but Firefox still doesn't have the keyboard focus and p hotkey doesn't do anything.

---

### Post by jokerdino on 2012-09-11
By the way, I just tried in gnome-shell v3.4.1 in Fedora 17 and the same thing happens. It seems like some sort of a bug in gnome-shell's focus handling.

---

### Post by DavidAdler on 2012-09-30
I've tried a few variations on how I pop-up and dismiss the image, but  in all cases Gnome seems to take focus away from Firefox and not return  it when the pop-up is dismissed.  

I don't know what else I can do in the  add-on; I suspect it's a bug in gnome and/or Firefox.  It may be tricky  to solve since it involves the interaction of software from three  different organizations.  But feel free to open a bug with Gnome or  Mozilla is you want to pursue it.

---

### Post by jokerdino on 2012-10-01
> **DavidAdler said:**
> I've tried a few variations on how I pop-up and dismiss the image, but  in all cases Gnome seems to take focus away from Firefox and not return  it when the pop-up is dismissed.  

I don't know what else I can do in the  add-on; I suspect it's a bug in gnome and/or Firefox.  It may be tricky  to solve since it involves the interaction of software from three  different organizations.  But feel free to open a bug with Gnome or  Mozilla is you want to pursue it.
Thank you very much for your reply. I have filed bug reports with both GNOME and Mozilla. 

Here are the links:

[https://bugzilla.mozilla.org/show_bug.cgi?id=795817](https://bugzilla.mozilla.org/show_bug.cgi?id=795817) and [https://bugzilla.gnome.org/show_bug.cgi?id=685185](https://bugzilla.gnome.org/show_bug.cgi?id=685185)

---

### Post by DavidAdler on 2012-10-01
Thanks for submitting it to Mozilla and Gnome.  For completeness I've also added an issue to the Thumbnail Zoom Plus issue tracker: [https://github.com/dadler/thumbnail-zoom/issues/92](https://github.com/dadler/thumbnail-zoom/issues/92)

---

