---
title: "Remapping &lt;Insert&gt; for Use as the &lt;Compose&gt; Key"
date: 2019-04-11
forum: Tutorials
---

### Post by DuckHook on 2019-04-11
**Table of Contents:**

[The <Compose> Key]("https://ubuntuforums.org/showthread.php?t=2416537&p=13851009#post13851009")
[Remapping the <Insert> Key]("https://ubuntuforums.org/showthread.php?t=2416537&p=13851010#post13851010")
[Remapping in X11]("https://ubuntuforums.org/showthread.php?t=2416537&p=13851011#post13851011")
[Remapping in Wayland]("https://ubuntuforums.org/showthread.php?t=2416537&p=13851012#post13851012")
[Adding Custom <Compose> Sequences]("https://ubuntuforums.org/showthread.php?t=2416537&p=13851013#post13851013")
[Accessing All Unicode Characters]("https://ubuntuforums.org/showthread.php?t=2416537&p=13851015#post13851015")
[Avoiding Danger and Recovering from Disaster]("https://ubuntuforums.org/showthread.php?t=2416537&p=13851017#post13851017")

The following tutorial is meant for users of plain Ubuntu versions Bionic and later. It was tested on only plain Ubuntu running both X11 and Wayland. Users of other flavours may find the following procedures applicable with only minor adjustments, but these techniques have not been tested on any other flavours.

:!: ***CAUTION*** :!:
> Starting sometime around Impish (21.10) Ubuntu has turned on the compose key feature by default and assigned it the <LeftAlt> key. Because of this, the following procedure ***will break your system*** unless the compose key feature is ***turned off first***. Otherwise, the system encounters conflicting keyboard pointers at boot and goes into unrecoverable shock. Because the keyboard subsystem dies, you will not be able to elegantly recover, or even power off with the usually reliable [sysrq method]("https://www.kernel.org/doc/html/latest/admin-guide/sysrq.html").

This makes the following tutorial workaround very brittle. A big upgrade or an inadvertent config change that sets the keyboard subsystem back to its defaults could render your system unusable. Proceed cautiously, and only if you always have means for recovery, like a LiveUSB session that you can use to revert the below process.

It may be advisable for newcomers to stick with Ubuntu's new default compose keys, though they are limited and do not permit choice of the <Insert> key. If you still wish to proceed, do so at your own risk.

---

### Post by DuckHook on 2019-04-11
[Ubuntu's <Compose> key]("https://help.ubuntu.com/stable/ubuntu-help/tips-specialchars.html") is a nice feature for those who use the US keyboard layout but also:

[list=1]
[*]Use other languages and must avail themselves of non-English letters,
[*]Wish to have easy access to non-keyboard characters (like £ or €),
[/list]
Ubuntu permits us to easily assign any of a number of keys to be the <Compose> key. To do so, you must first install gnome-tweak-tool:```
sudo install gnome-tweak-tool
```
It will show up in the app list as "Tweaks".

If it isn't showing, you can alternately launch it with:

[INDENT]<Alt> + <F2> &#8594; gnome-tweaks[/INDENT]

or type into terminal```
gnome-tweaks
```

Then:

[INDENT]Tweaks &#8594; Keyboard & Mouse &#8594; Compose Key &#8594; Turn on the slider button.[/INDENT]

This yields a number of options: Scroll Lock, PrtSc, Menu, Right Alt, Right Ctrl, Right Super, Caps Lock, Left Ctrl.

If you are happy sacrificing one of these keys, say, <Caps Lock> for use as <Compose>, then select it and it will henceforth stop locking your letters into capitals and instead be used as <Compose>.

Easy peasy (as far as it goes).

But the problem is that all of these keys have other legitimate uses. Though infrequent, there are times that I want to use <Caps Lock> for a long string of capitalized letters. One might imagine that <ScrLk> or <PrtScn> are otherwise useless keys that would make good candidates, but:

[list]
[*]Not all keyboards have them,
[*]They can be tiny, hard to find and awkwardly placed,
[*]<ScrLk> still has legacy use (eg MS Excel), and
[*]<PrtScn> has a rare but critical system-level use that we do not wish to break (see [REISUB]("https://en.wikipedia.org/wiki/Reisub")).
[/list]

---

### Post by DuckHook on 2019-04-11
However, there is one key that exists on every keyboard that I personally detest and consider worse than useless, and that is the <Insert> key. The default behaviour for the <Insert> key is to toggle text entries between overwrite mode and insert mode. Personally, I *never* use overwrite mode. In fact, when I accidentally activate it&#8212;by mixing up <Insert> with <Delete>&#8212;I find myself cursing over work lost to overwriting a bunch of characters before I notice my error.
 
Therefore, I find <Insert> is the ideal key to remap as the <Compose> key. It gives me needed utility, is easy to reach, and eliminates a constant source of error and frustration. It also has the unintended benefit of describing what the <Compose> key actually does: "inserting" a non-standard character. What's not to like?

> :!: NOTE :!:
If you decide to remap the <Insert> key, it is **NOT** necessary to turn on the compose key with gnome-tweak (as per instructions in the previous section). In the sections to follow, the process of remapping <Insert> **turns** it into the <Compose> key and no further action is needed.

---

### Post by DuckHook on 2019-04-11
In X11, you can remap keys quite easily with *xmodmap*. The following simple script does the job:```
#!/bin/bash

# Remaps the useless "Insert" key to act as the "Compose" key for generation of alternate characters.
# On standard US keyboards, keycode 118 corresponds to the "Insert" key.
# "Multi_key" is the actual key name for the "Compose" key.

sleep 5
xmodmap -e "keycode 118 = Multi_key"

```
[list=1]
[*]Place the above script into a directory on your path (mine is the default *~/bin* Note this is my personal *bin*, not the system *bin* —the difference is very important—do not confuse the two):
[*]```
nano ~/bin/compose
```
[*]Carefully type in (or copy and paste) the above script.
[*]Write the changes and exit Nano.
[*]Make it executable:```
chmod ugo+x ~/bin/compose
```
[*]I run this script as a Startup Application at login. The sleep 5 command gives the X environment time to load first so that *xmodmap* has something to work on. Depending on your login delay, vary sleep length to suit your needs.
[/list]
In my opinion, this is still the preferred way to remap the <Insert> key. It isolates the modification to your own session and doesn't impose your customization on others sharing your computer. However, it's biggest drawback is that *xmodmap* only works with X11.

Wayland has nerfed *xmodmap* so remapping must be handled differently.

---

### Post by DuckHook on 2019-04-11
I have found no way to remap keys in Wayland except globally&#8212;making changes to a system file. This has three big drawbacks and one small advantage:

Drawbacks:

[list=1]
[*]Everyone sharing the computer has to live with the changes.
[*]An update to the keyboard subsystem will wipe out the changes, thus necessitating a re-edit. Thankfully, updates to the keyboard subsystem are rare, but they do happen. If your <Compose> key loses functionality after an apt update, this is the likely cause.
[*]Editing system files is dangerous. A mistake could mean that you won't even be able to type in corrections. Extreme caution is needed.
[/list]
Advantage:

[LIST=1]
[*]Modifying system files activates the change immediately at login, whereas the scripted method sometimes will not "take", likely because X11 has not fully loaded before xmodmap is executed.
[/LIST]
To affect the remapping in Wayland, you must change the keymapping in: */usr/share/X11/xkb/symbols/pc*

[list=1]
[*]First (and I cannot stress enough the importance of this), make a backup of this file so that you have a fighting chance to recover from an error. It is owned by root, so you must use sudo:```
sudo cp /usr/share/X11/xkb/symbols/pc /usr/share/X11/xkb/symbols/pc.old
```
[*]Open the file for editing:```
sudo nano /usr/share/X11/xkb/symbols/pc
```
[*]You will see something like the following:
[ATTACH]283001[/ATTACH]
[*]Towards the end of this file, find the line (#76 in mine):```
    key  <INS> {	[  Insert		]	};
```
[*]Change "Insert" to "Multi_key" so that it looks like this. You must be exact. Case and underscore are very important:```
    key  <INS> {	[  Multi_key	]	};
```
[*]Write the changes and exit Nano.
[*]Reboot.
[*]<Insert> should now be remapped as <Compose>. To test, try <Insert>    <(>    <c>    <)>   which should give you the &#9426; copyright character.
[/list]
An alternate strategy for managing this file is to store it someplace where a system update will not clobber it, say, */opt/config* and symlink it back to its expected location. If you do this, be careful to preserve its proper ownership and permission structure.

> **Please don't abuse your newfound power.**

Like the Comic Sans font and crazy colours, it's tempting to sprinkle eye-sores all over the internet&#8212;adding little bon mots that you think are "fun" or "clever", but are really&#8230; well&#8230; just eye-sores. Use Unicode sparingly, for clarity, nuance or for proper etymological spelling (Niçoise salad anyone?), but please lay off the &#8482; and &#9441; because, though you may think you come off as encyclopædic (see what I did there?), ligatures and the like do **NOT** belong on an English-language forum.

---

### Post by DuckHook on 2019-04-11
The <Compose> key and its associated subsystem actually just addresses a small subset of the thousands of characters in a complete Unicode set, but it should be enough for most Latin-based language needs. As of Bionic (18.04) the default Compose sequences and their keyboard combinations can be seen with:```
less /usr/share/X11/locale/en_US.UTF-8/Compose
```

Though lengthy, this is just a simple text file. Therefore, it is possible to add your own additional character sequences if you follow the syntax and use valid key references. Note that changing system files in this way carries risks not only of system breakage, but of lost effort when these files are unceremoniously trashed in an update. Therefore, it is wise to keep a copy of your changed file on your /home directory where it will not be replaced by a system update.

Remember, however, that the file must be owned by root when you copy it back into place.

You can also use the aforementioned strategy of storing it someplace safe and symlinking back to its expected location.

**A Better Method:**

While the above procedure works, it is primarily meant to show the logic that the OS uses to define Compose sequences. In my opinion, a better method is to create a .XCompose file in your ~ directory containing your custom Compose sequences.

This leaves the system file untouched (always a good practice), isolates changes to your own account, preserves your customizations through system updates and is just good general practice.

[list=1]
[*]If a .XCompose file exists, Ubuntu will read this file *in lieu of* the system file. Therefore, .XCompose must follow a specific form by first calling the system file. Its first lines need to be:```
# This file contains custom Compose sequences for Unicode characters 

# Import default sequences from the system Compose file:
include "/usr/share/X11/locale/en_US.UTF-8/Compose"
```The last line is the important one which ensures that your subsequent contents are *added* to the system file and do not *replace* it.
-
[*]Next, following the syntax in the system Compose file, add the sequences and characters that you wish to customize. For example:```
# Add all custom compose sequences after this line:
<Multi_key> <asciicircum> <bar>   : "&#8593;"  U2191 # UP ARROW
<Multi_key> <bar> <asciicircum>   : "&#8593;"  U2191 # UP ARROW
<Multi_key> <v> <bar>             : "&#8595;"  U2193 # DOWN ARROW
<Multi_key> <bar> <v>             : "&#8595;"  U2193 # DOWN ARROW
```

[*]Save the file, reboot.
[/list]

Alternatively, you could simply copy the whole system Compose file into your ~ directory, change its ownership to you, and dispense with step 1 above. But the system Compose file is long and nasty to edit. It's so much cleaner and easier to maintain if you just leave it in situ and append your custom sequences to it. 

> :!: **CAUTION** :!:
Make sure that you don't define a key sequence that already exists in **/usr/share/X11/locale/en_US.UTF-8/Compose** or else you will clobber an existing key sequence (with unpredictable results).

Therefore, it is advisable to do a thorough search in the system Compose file for the key sequence you wish to use before defining it. The **find** command is very useful for such work.

---

### Post by DuckHook on 2019-04-11
This tutorial is not intended as a general Unicode tutorial. That would be a massive undertaking far beyond the scope of this tutorial. However, it would be incomplete if we failed to address the Unicode foundation on which the Compose function is based.

Because it can access every Unicode character and not just the subset available to the <Compose> key, a more powerful method to insert Unicode is to do:

[INDENT]<Ctrl> + <Shift> + <u> &#8594; <Unicode number> &#8594; <Enter>[/INDENT]

However, it is impossible to remember the thousands of Unicode numbers, so the <Compose> key method was developed for its much easier mnemonics.

A good [Unicode table is available here.]("https://unicode-table.com/en/#") Be forewarned: it is massive and looking for the exact symbol one wants is like finding a needle in a haystack.

The Unicode Consortium's official web page also includes [a search engine]("https://www.unicode.org/charts/") and printable charts, but this is often a chicken or egg situation when one doesn't have the symbol ready to hand. After all, looking for a symbol is why we're visiting the site in the first place.

It may be easier to parse through Unicode on Ubuntu's character map:

[INDENT]<Alt> + <F2> &#8594; gucharmap[/INDENT]

Each character's Unicode is displayed when selected, but I find it confusing to navigate through the app. Characters are split into classes haphazardly and I find it difficult to navigate.

You can spend hours exploring the nooks and crannies of the Unicode that is installed in your system. Happy hunting!

**Further Unicode References:**

[Wikipedia's Unicode Page]("https://en.wikipedia.org/wiki/Unicode")
The Unicode Consortium's [Home Page]("https://unicode.org/")
[Unicode Emojis]("https://www.unicode.org/emoji/charts/emoji-list.html")

---

### Post by DuckHook on 2019-04-11
Some of the techniques offered in this tutorial deal with system keymaps. While none of the procedures are technically difficult, there is an inherent danger in dealing with such files. A number of forum threads are unfortunately pleas for help from users who have nuked their keymaps.

The biggest danger in working with keymaps is that they are the foundational and sole input vector into your OS. If you can't type characters into your computer, you can't fix anything.

[LIST]
[*]Backup your data. Religiously. If you don't, you are the author of your own misery. Nothing more need be said about this.
[*]Do not tinker with your base system when setting out to explore. Instead, do your experimenting inside a VM with a known good snapshot.
[*]There are so many good reasons to multi-boot. Disk space is ludicrously cheap these days. I have three separate versions/flavours on my main desktop machine. If one gets borked, even from a bad upgrade, I can almost always boot into another partition, mount the broken one, and try to repair it.
[*]When working on system files, always, always, always make a backup copy first. You then have the option of swapping out the bad file with the known good one and starting over.
[*]If you can only single boot and are ready to manipulate actual system files, at least have a LiveUSB stick handy that you've tested, is current, reliable, and that you can boot with. Use this to repair a broken system.
[*]Use the expertise in the forums. Ask for advice before you attempt something wild. It's easy for us to warn you away from doing something stupid. It's a hundred times harder trying to repair it afterwards.
[/LIST]
Please feel free to comment, question or make suggestions. I'm always willing to learn and will edit this thread with good suggestions. But if asking for help, as per forum policy, please do so in the appropriate technical subforum so that everyone can benefit from the fix.

---

