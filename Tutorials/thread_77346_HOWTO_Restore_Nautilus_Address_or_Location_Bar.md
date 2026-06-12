---
title: "HOWTO: Restore Nautilus Address or Location Bar"
date: 2005-10-16
forum: Tutorials
---

### Post by Dr. Nick on 2005-10-16
Many people dislike the new Nautilus view where the full text path is not shown, but instead Icons of each folder. To restore Hoary like location "address" bar

Here is the Simple Fix

If you want it to only last for the current session hit CTRL+L

When you are done with it and want the "new" view back , click in the location bar and simply push "esc"

To make it permanemt: 
**Open Applications->System Tools -> Configuration Editor**
find the entry 
"**/apps/nautilus/preferences/always_use_location_entry**"
and click the checkbox on

---

### Post by william_nbg on 2005-10-17
Thanks a lot.

Little tips like these make using Ubuntu all the more fun.

---

### Post by denisesballs on 2005-10-19
It's amazing how simple ctrl+L just made me so happy.

---

### Post by tseliot on 2005-10-19
Thanks, now it's better.

---

### Post by LaSSarD on 2005-10-19
ok then you need to ctrl+L everytime you open nautilus ^^

---

### Post by `GooZ´ on 2005-10-21
Thanks ALOT! This should be implemented somewhere in the system -> preferences menu.

---

### Post by waffen on 2005-10-24
and exist another ctrl+ ??? to restore the view? :-)

Thanks!

---

### Post by Dr. Nick on 2005-10-24
[QUOTE=waffen]and exist another ctrl+ ??? to restore the view? :-)

Thanks![/QUOTE]

hmm I will make this interesting, Im going through every ctrl+?  combo and will post a nice little keyboard shortcut guide aswell :)

ctrl+w Closes nautilus
ctrl+r  Refreshes 
ctrl+s  Starts selection patern dialog
ctrl+x  Clears address bar so you can type any location
ctrl+b  Bookmark Editor
ctrl+n  Opens a new window with old view restored
ctrl+"+ or -" changes zoom
ctrl+1 or 2 changes views

I dont see anything that changes it back though, ctrl + n is the closest but it open back to your home directory

**EDIT**
Found out how to get back to button view without closing/re-openig. Pretty simple actualy, a bit to simple I thought it wouldnt work but it did :)

just push "esc" :) :) 
If you click a folder to open while in location view then you have to click in the location bar then esc, if you hit ctrl+l then click nothing then esc will take you back fine

I added this up to the top post aswell

---

### Post by dartakaum on 2006-01-01
how do i make that not using gnome? :b

---

### Post by kaamos on 2006-01-01
use this commad in terminal
```
gconf-editor
```

---

### Post by dartakaum on 2006-01-02
thanks! :)

and how to put the left tab with small icons?

and take text and use small icons from the main toolbar?

and at last where o i change de font type?

---

### Post by Dr. Nick on 2006-01-02
[quote=dartakaum]thanks! :)

and how to put the left tab with small icons?

and take text and use small icons from the main toolbar?

and at last where o i change de font type?[/quote] 
Not sure exactly what you mean, but running 
gconf-editor will give you alot of option to configure it. I saw option to change icon sizes and fonts in their one day I think, look in  /desktop/gnome/interface/toolbar_style for the text only and no icons if you would just like to get rid of toolbar icons, I belive one of them keys can change icon size aswell. Their are others around their that look like other stuff you want

---

### Post by mintcoffee on 2006-01-21
Thank you! This was one of my biggest gripes with nautilus!

---

### Post by jbaou on 2006-08-15
Ok lads, a whole year later here I come ... Nautilus 2.14.1 Edit->Preferences->Behaviour Tab-> Tick the *"Always use text-entry location bar"* ... hope this helps ...

---

### Post by fakeh on 2006-09-15
Any idea how to apply this change to the file Open/Save dialog too?

Dan.

---

### Post by Grone1985 on 2008-05-06
Thank you very much! I had been looking for a permanent fix for this!

---

### Post by NMFTM on 2010-05-02
> **Dr. Nick said:**
> To make it permanemt: 
**Open Applications->System Tools -> Configuration Editor**
find the entry 
"**/apps/nautilus/preferences/always_use_location_entry**"
and click the checkbox on
I don't know why that isn't the default setting to be honest. It's much more compact and easier to read.

---

### Post by worldsayshi on 2010-05-05
Last Ubuntu release (Koala) there was a button to the left of the adress bar doing what ctrl-L does. Seems like Lynx took that away. 

Thats no good.

---

### Post by wild_oscar on 2010-05-17
Any idea where one should suggest bringing the option back. It's a rather annoying change and having to go to gconf to change it seems like complicating things too much for the average user. Why change something that was simple and functional?

---

### Post by psypher on 2010-07-09
There was a button with a pencil icon you can just click to activate this permanently. wasn't wasting any space or hurting anyone and now it's gone. It's just a silly as removing the button from the media menu which allowed you to stop usb drives from auto mounting. required when you wanted to format a usb drive in gparted. not so much anymore but still loads of times i want to manually mount my usb disks.

having the location bar always on should be the default, instantly type which folder you want or smb/ftp/scp:// to any network location. it's brilliant.

now for both you have to you gnome "regedit"??? how is that easier for the less experienced?

Also in lucid the option under the behaviour tab was removed. so you have to use gconf-editor.

---

### Post by SisterNotes on 2010-09-05
I'm in complete agreement. I'm trying to set up a connection to my website files and the instructions were to put the provided address into Nautilus. I still think of myself as a newbie, even if I started on Jaunty. It had taken me quite a while (the past 30+ min.) to find this particular post explaining how to get the address bar back. 

For the other newbies, you need to press ALT-F2 and then type gconf-editor in order to change the settings. Is there a GUI way to get to the ALT-F2 window for when I forget these key-strokes?

---

### Post by MestreLion on 2010-09-17
Humm, ESC to restore the button bar works ONLY if location bar is NOT the default. Looks like (unfortunately) theres no key to bring to button bar if the location is the default one (after configuring always_use_location_bar to true)

That is sad :(

Heres my scenario: i want location bar to be default, because it has many benefits (mostly copy-and-paste). So i must either set configuring always_use_location_bar=true OR i would have to hit CTRL+L like 90% of the times i enter Nautilus.

BUT, after changing the default, i cannot have the button bar back, or quickly toggle it. ESC does not work. Do i really have to let the button bar as the default to be able to toggle the bars???

---

### Post by L a r r y on 2011-05-06
> **Dr. Nick said:**
> Many people dislike the new Nautilus view where the full text path is not shown, but instead Icons of each folder. To restore Hoary like location "address" bar

Here is the Simple Fix

If you want it to only last for the current session hit CTRL+L

When you are done with it and want the "new" view back , click in the location bar and simply push "esc"

To make it permanemt: 
**Open Applications->System Tools -> Configuration Editor**
find the entry 
"**/apps/nautilus/preferences/always_use_location_entry**"
and click the checkbox on

You actually have your choice of default behavior now:

If your system shows the full-path-in-location-bar by default, and you want the folder-button view by default, and its ability to be switched  between text (CTRL+L) and buttons (ESC), then follow these steps:

Open 
**Applications->System Tools -> Configuration Editor**
find the entry 
"**/apps/nautilus/preferences/always_use_location_entry**"
and remove the check from the box.  Close the editor and you have buttons.

You may toggle the default back-and-forth by repeating these steps and placing the check back in the box for text-only or removing the check for buttons.

Now:  For those of us who *like* the button view some of the time, wouldn't it be nice if there were a set of keyboard shortcuts that work when the default is set to full-path-text mode?

Job for someone with knowledge of programming bash and some time to kill:  Create an app for that!  It might offer the default behavior option in the Nautilus Preferences menu, of all places.  (Edit) Or Right out on the user interface!  I agree textual full paths are best for copy-paste, but buttons do quickly move one through the tree.(/edit)

Thank you Dr Nick!

---

### Post by tofudrifter on 2011-10-16
Is it still possible to do this in 11.10?
I installed gconf-editor and the always_use_location_entry is missing.
Manually adding it does nothing.

edit: found it!!!
[AskUbuntu.com]("http://askubuntu.com/questions/66927/nautilus-missing-toolbar-stuck-in-text-only-location-bar-mode-after-11-10-upg")

In 11.10 you need to install dconf-tools
Then run dconf-editor
Location Bar option is stored in "org &#10140; gnome &#10140; nautilus &#10140; preferences &#10140; always-use-location-entry"

---

### Post by abdulmajid on 2011-10-28
Thanks for the tip. Until now I used Ctrl+l to display the address/location bar. :D

---

