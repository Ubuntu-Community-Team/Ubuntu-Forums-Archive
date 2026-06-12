---
title: "Discussion on: Improved keyboard interaction in Nautlius"
date: 2010-10-17
forum: The Cafe
---

### Post by zawlazaw on 2010-10-17
Hi there,

with this thread I want to put up an elaborated and clear formulated feature-request on Nautilus for discussion.


**The problem...**

To start with some motivation of the background: Not just programmers, but anybody who uses the PC extensively, does frequently have to rename, move, copy, transfer or edit files and directories - in fact this is the most crucial part of daily work and should be intuitive and fast. Because of this, since the 80's there are several alternatives to the pure shell, e.g., I started with XTree (DOS), later XTGold (DOS), then the famous Norton Commander (DOS), later the great Total Commander (Windows) and the Midnight Commander (Unix) and Krusader (X-Linux). These split-screen file-managers provide the user with powerful and fast capabilities for the above mentioned tasks. There are some basic interaction standards amoung all of them that turned out to be practicable to use the keyboard, instead of the much slower mouse interactivity, to get what you want. However, 'pure' split-view file-managers might confuse novices or handicapped persons, so the challenge is to find a very good compromise between those and advanced users in a file-manager.

Since Nautilus provides the F3-key to create a second 'list' in a split-view fashion it can optionally enter the world of a classic split-view file-manager, and under many other aspects it is even now already much better than others (e.g. the grandiose possibilities in transparently accessing remote directories, and its perfect system integration and extensibility).

However, there is still an important (!) disadvantage: Beside the lack of some specific advanced multi-selection capabilities, the *keybindings* do not match the standards of split-screen file-managers, or there do not even exist any for several actions! Because of this, Nautilus is often unhandy for an experienced keyboard-user, who must frequently use the much slower mouse interface or rely on the terminal or an external file manager, though Nautilus also has some strong advances over them! I think, many of you know this 'GUI versus Keyboard'-discrepancy. While the keyboard input is much faster for experienced users, it is important for a GUI not to confuse the user with too many visible functionality. So, what would be the best compromise here? This is presented in the following idea.



**The solution...**

The best solution I can think of is a combination of a *nautilus-keybindings-manager* **and** an optional *robust selection mode* **and** a few other improved interactions, see below! With these things implemented (which doesn't seem too extensive), Nautilus could definitely become the file-manager of choice for GUI-clickers *and* for terminal-junkies!

At first, there should be a clear seperation between keyboard events and the associated action itself. These should correspond to entries in gconf-editor under 'apps/nautilus/keybindings' and be editable by a small GUI that supports loading/saving these keybinding-settings along with some other settings to/from a config-file. By this, one could use the 'default profile' just as it is now, or could switch to a 'split-view profile' with different settings.

In the following I give a list of several actions (some of them do already exist as such, others not) that all should be bindable to some key. I also suggest a default key for the split-view profile (being some collection of standards in diverse split-view file-managers). For the terminology, I assume we have two 'lists' (left and right list, where always one of both is 'active' and will react to keyboard-input if it has the focus), each containing one or more 'tabs'.

1.) Actions in window navigation:

(1.1) Toggle active list between left and right list. <TAB>. This is a very basic change of a keybinding, but the most crucial and frequently used action in split-screen file browsing.
(1.2) Make the current directory of the active list also the new directory of the other list AND then make the other list the active one. <Strg>+<Insert>.
(1.3) Open current directory in a terminal. <F2>.
(1.4) Move to next/previous tab in the currently active list. <Strg>+<TAB> and <Strg>+<Shift>+<TAB>. This is just a general standard behaviour.
(1.5) Close the current tab. <Shift>+<Strg>+<T>.
(...)

2.) Actions on current *(multi-)selection* (as currently createable using the Strg-key and mouseclicks or Strg+Space and cursors) as well as actions on the currently *active item* (the focused item that was lastly clicked, or navigated-to when using Strg and Cursors up/down)

(2.1) Show/display the active item, if it refers to a file. <F3>. Same as Rightclick->Open with standard association. The current F3-binding for switching the split-view could be moved to Alt+V for example.
(2.2) Same as 2.1, but just show up the Open with... window and let it get the keyboard focus. <Shift>+<F3>.
(2.3) Edit the active item, if it refers to a file. <F4>. Calls an editor for this file. I don't know if ubuntu is distinguishing between 'opening' and 'editing' a file? If so, this should just open the standard edit program for this filetype or with <Shift>+<F4> present an Edit with... list. This is helpful for many filetypes (e.g. html: 'open' with Firefox, but 'edit' with gedit). If not, then <F4> and <Shift>+<F4> could just call a fixed user-defineable editor program on the file (then unfortunately regardless of its file extension). I think there is no need for nautilus to provide some build-in editor or viewer, like other file mangers do.
(2.4) Copy all items of the current selection to the other list. <F5>. Same action as clicking 'Edit->Copy to...->Other list'. Note, that these navigation titles might not match the original English ubuntu menu titles, since I just translate them from German 'Bearbeiten -> Kopieren nach -> andere Leiste'.
(2.5) Move all items of the current selection to the other list. <F6>. Same action as clicking 'Edit->Move to...->Other list'.
(2.6) Create new directory. <F7>. Same functionality as current keybinding <Shift>+<Strg>+<N>.
(2.7) Delete all selected files and directories. <F8>. However, since any modern computer has a Delete-Key, this is redundant, so one could think of making a difference here between Delete-Key and F8, namely: Delete-Key (as usually used) moves to trash, while F8 deletes without trash (after some warning).
(2.8 ) Make the main menu-bar get the keyboard focus at the same entry where it was left the last time. <F9>. Thus, pressing F9 for the first time in a session pops up the main file-menu, where we can browse with the cursor-keys e.g. until we select something or press Esc.
(2.9) Edit currently chosen active item's file/directory name in place. <Shift>+<F6>. Or, if 2.8 is not possible or wanted, then F9. It is horrible to be forced to use "right mouse-click -> Rename" for this action.
(...)

3.) Defining the items of a Multi-Selection (recall the above definition of '(multi-)selection' and the 'active item')

(3.1) Enable/disable *robust selection mode*. (No need for a keybinding, but there should be some flag for it). What is it? This is nearly exactly the behaviour we get when we hold down the Strg-key (in the standard volatile selection mode) while we use the cursor-keys, the mouse-clicks and the Space-key to select/deselect individual items. This is the standard selection-mode in all split-view file browsers, thus, left-clicking or pressing Space on some item does *not* unselect all other items. More details: If we click on an item that is not the active item, we just make it the active item now *without affecting its selection state*. If we click (again) on the active item we toggle its selection state (without affecting others).
(3.2) Toggle this directory's last file selection. <Strg>+<Space>. Only in 'robust selection' mode, see 3.1. By this, any directory saves its last defined multi-selection during the session and is able to unselect all items, or recall the last multi-selection, using this keybinding. Usually, whenever we (re-)enter a directory, no file should be selected, but the last selection can be restored by this key.
(3.2) Add items to the current multi-selection by a wildcard-expression. <Number-block's +>. Opens a new mini-prompt asking for a wildcard expression, e.g., type in *.xcf and press enter. Then all matching files and directories are merged/added to the current multi-selection. Optionally, the prompt might also provide the checkmarks 'deselect all currently selected items before adding', 'match files' and 'match directories'.
(3.3) Remove items from the current multi-selection by a wildcard-expression. <Number-Blocks's ->. Same as above, but all matching items in the current directory are removed from the current multi-selection (not the files themselfes!).
(3.4) Invert current selection. Does already exist with <Shift>+<Strg>+<I>.
(...)

4.) Some general things that would further improve the interaction, but that are not related to some individual actions:

(4.1) Provide a flag to optionally recall the last session on startup. If the new session was called with a target to open on start, then replace the active tab in the left list (in split view, otherwise of the visible list) with the new target, but keep the previous target already in history, so one could use Alt+Left to navigate back to it.
(4.2) Improved text-location-input (as currently accessible by Strg+L, which should be possible to make it the default). When typing in a part of the next directory, there should popup a scrollable list below the input field showing all potential directory names that match the current input. While this list is open we can use the cursor-keys to access it, while still we can use <TAB> for an auto-completion to the longest common subsequence of all entries, just as in the terminal. Pressing <Enter> selects an entry, while <Esc> leaves it.

All these tricks would *not* affect or confuse novices, since they are simply invisible to them. But these would *drastically* improve the keyboard-interface and make Nautilus the very best file-manager even for keyboard-users!

If you have any comments to some specific point of the above list, then please refer to the corresponding number. Finally, I plan to bring this feature request to the ubuntu brainstorm system.

Cheers,
Sven

---

### Post by roggenschrotbrot on 2010-10-17
using nautilus in a tiling window manager myself (as none of the alternatives truly satisfies me), i have to agree - keyboard navigation/interaction could really need some more attention.

---

### Post by cariboo on 2010-10-18
This isn't a support question, moved to the Cafe.

---

### Post by berndth on 2010-10-22
You can assign keybindings to Nautilus' menu items already. With that, you can already accomplish a bunch of what you proposed (e.g. F5 to copy).

Note that you cannot always switch to Norton-Commander-like shortcuts. Some keys have a very specific meaning in GNOME, and changing them in dual-pane Nautilus was rejected (e.g. Tab, F6). It's more important for Nautilus to be consistent to GNOME Applications than to Norton Commander.

For some of the more advanced stuff, you can create Nautilus Actions (which can operate on the inactive pane as well), and assign shortcuts to those.

---

