---
title: "How many Gnome Shell extensions are you using?"
date: 2011-12-30
forum: The Cafe
---

### Post by Perfect Storm on 2011-12-30
Yes, another pointless poll :popcorn:

For those who uses Gnome Shell, how many extensions are you using? And which?




I use only 4 extensions as I quite like Gnome Shell as it is. But it may change if I find something useful in the future. So for now it looks like this for me:

- User Themes Extension
- noa11y Extension
- Alternative Status Menu Extension
- Weather indicator Extension

---

### Post by hhh on 2011-12-30
I currently just use two, User Themes and Weather Indicator. The weather indicator will occasionally show the wrong day's weather, restarting it fixes that but some days I leave it disabled. I was using noa11y but now I just comment out the a11y indicator line in /usr/share/gnome-shell/js/ui/panel.js (though that needs to be redone at every shell update). I also commented out the userMenu line there and use a script from the Run dialog to logout, or a terminal to reboot/halt.

[[img]http://ompldr.org/tYnpqOA[/img]](http://ompldr.org/vYnpqOA)

Once I customized a few keyboard shortcuts to open a terminal, file browser, internet browser and to close and hide windows, I've been thrilled with the shell. I'm running Debian testing with gnome-shell 3.2 installed from experimental, though I believe that's been moved to testing as well now. -edit- Nope, it is in unstable now.

-edit- @AI, do you have a current screenshot of your setup (I can't remember your latest post in the screenshot thread)? Thanks.

---

### Post by wolfen69 on 2011-12-30
Shutdown menu

Bottom panel (for open windows and workspaces)

Top panel app icons

Weather applet

Elegant Dark theme

---

### Post by Primefalcon on 2011-12-30
1=unity

---

### Post by qamelian on 2011-12-30
Only one: User Themes Extension. Thus far, I haven't had any reason to want or need any other extensions.

---

### Post by Frogs Hair on 2011-12-30
Use Occasionally 

Dock extension 
Workspace indicator Extension

Always Enabled

Alternative Status Indicator Extension 
Places Status Indicator Extension.
User Themes Extension 

I have more installed , but haven't decided if they are worth while yet .

---

### Post by Copper Bezel on 2011-12-31
Just the essentials. = )

[[img]http://dl.dropbox.com/u/17749392/Screenshots/2012-12-30/extensions-thumb.png[/img]](http://dl.dropbox.com/u/17749392/Screenshots/2012-12-30/extensions.png)

Nine in total. Almost all of them are either removing something or making it act more self-consistently than it does by default. Jump lists are an exception, but I like them. 

Edit: Oh, and the Activities button bit, which is purely cosmetic.

---

### Post by bookcrazy on 2012-01-18
Touchpad-indicator 
Remove Accessibility
Cover Flow Alt-Tab
User Themes
Alternative Status Menu
Remove Blue Tooth Extension

BTW, what is this weather extension you all are talking about?

---

### Post by satanselbow on 2012-01-18
Alt status menu, User Themes (still use adwaita though!) , noa11y... I can look out a window if I need to know the weather :popcorn:

---

### Post by Perfect Storm on 2012-01-18
> **bookcrazy said:**
> Touchpad-indicator 
Remove Accessibility
Cover Flow Alt-Tab
User Themes
Alternative Status Menu
Remove Blue Tooth Extension

BTW, what is this weather extension you all are talking about?

[quote=hhh]-edit- @AI, do you have a current screenshot of your setup (I can't remember your latest post in the screenshot thread)? Thanks.[/quote]

[[img]http://s6.postimage.org/qzlopn9bl/Weather.png[/img]](http://postimage.org/)

[[img]http://s6.postimage.org/wvf94qwoh/Screenshot_at_2011_11_26_09_35_57_pre.png[/img]](http://postimage.org/image/nz4h0t625/full/)

---

### Post by BigSilly on 2012-01-18
Like the OP, I love Gnome Shell pretty much as-is. I only have two extensions - the shutdown button and the media player integration. Enough for me. :)

> **Copper Bezel said:**
> Just the essentials. = )

[[img]http://dl.dropbox.com/u/17749392/Screenshots/2012-12-30/extensions-thumb.png[/img]](http://dl.dropbox.com/u/17749392/Screenshots/2012-12-30/extensions.png)


Love your Gtk theme. Which one is it?

---

### Post by Copper Bezel on 2012-01-18
[Radiamentary]("http://gnome-look.org/content/show.php?content=144806"). It's totally the new Orta, to my taste. I love it, too - simple and clear. I like the simple close button, the smooth transition between the title bar, menu bar, and toolbar, and the button contours.

I should note that I changed the selected bg color in the GTK3 and GTK2 to #75a6ff, the washed-out blue Orta used. By default, it's a more energetic, Maccy jewel blue.

On topic, thanks to bookcrazy, I've tentatively swapped out Windows Alt Tab for Coverflow. I wish it could be restrained to the present workspace, and I'll have to figure out how to make Alt+Grave cycle backward and turn off the gray "floor" if I can, but it's still very pretty and nicer than Compiz's equivalent.

Edit: Done. The shadow can be altered in the extension's handy included stylesheet, and the switcher behavior can be modified in switcher.js by moving around the events that start at line 231.

---

### Post by Perfect Storm on 2012-01-18
@Copper Bezel
Looks very elementary-ish.

@hhh
I have added a screenshot, sorry I haven't responded earlier but I missed the 'edit' you made to your post.

---

### Post by Copper Bezel on 2012-01-18
[QUOTE=Artificial Intelligence]Looks very elementary-ish.[/QUOTE]

Yes, that's why it has *mentary in the name. = ) The Metacity is Elementary, and the toolbar shading is similar, but fields, buttons, and toolbar items are more similar to Radiance.

Edit: Oh, you meant the layout. Yeah, I love-love-love the look of Wingpanel, and I tried it for a while on 10.10, but it wasn't entirely functional. Now I just make everything else look like Wingpanel. The panel theme is Elegance, modified with the shadow removed, the gradient changed, and the curlies added back on. The "standby" style "unavailable" icon is custom.

---

### Post by shuttleworthwannabe on 2012-01-18
> **wolfen69 said:**
>  Elegant Dark theme

Where did you get this from? Link?

---

### Post by wolfen69 on 2012-01-18
> **shuttleworthwannabe said:**
> Where did you get this from? Link?
I have it right here as an attachment. ;)

The way I installed it (there may be other ways) was to first unpack it and put the folder in ~/.themes and then download **gconf-editor**. Open gconf editor and navigate to desktop>gnome>shell>windows, and on the right, change *theme* to Elegant Dark. (spelling and capitalization are important) Log out and back in. Enjoy.

---

### Post by bookcrazy on 2012-01-18
Could you do me a favor and direct me to the ppa for that weather extension you are using? Looks cool! 

Thank you!

Also, do you have to log out and log back in for the extensions to take effect or can you just hit Alt+F2 and then "r"? 

Cheers

> **Artificial Intelligence said:**
> [[img]http://s6.postimage.org/qzlopn9bl/Weather.png[/img]](http://postimage.org/)

[[img]http://s6.postimage.org/wvf94qwoh/Screenshot_at_2011_11_26_09_35_57_pre.png[/img]](http://postimage.org/image/nz4h0t625/full/)

---

### Post by wolfen69 on 2012-01-19
Go [here]("https://launchpad.net/~webupd8team/+archive/gnome3") for the weather extension ppa. Among other things too. :)

---

### Post by malspa on 2012-01-19
I voted "1-2."

I actually have 8 installed and 6 enabled, but the only one I regularly use is "Alternative Status Menu," for the power off option. I've found that I don't really need anything else. I don't understand why that power off option wasn't included by default.

---

### Post by bookcrazy on 2012-01-19
Thank you! 

Downloaded, installed, and running perfectly here in Nanjing. :D

> **wolfen69 said:**
> Go [here]("https://launchpad.net/~webupd8team/+archive/gnome3") for the weather extension ppa. Among other things too. :)

---

