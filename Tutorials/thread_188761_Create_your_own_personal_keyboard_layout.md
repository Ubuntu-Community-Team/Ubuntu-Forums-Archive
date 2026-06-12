---
title: "Create your own personal keyboard layout"
date: 2006-06-04
forum: Tutorials
---

### Post by henriquemaia on 2006-06-04
**********UPDATED May 2010**********

This HowTo is for those of you who are not satisfied with the layout of your keyboard, like myself.

You can have several reasons to do this (eg. for the sake of the experience, for achieving a more ergonomical typing experience, etc). I have done this for the sake of ergonomy. I type a lot (professionally) and I use my computer most of the time (99%). My keyboard is now non-standard, but that's not a problem, since I'm much more productive this way and I STILL know how to use a normal keyboard.



**[SIZE=3]1. The Basics[/SIZE]**

You don't have to mess with many things. Just edit one file. But to achieve your goal, you have to understand what's in it. 

The file is located at:

/usr/share/X11/xkb/symbols/

This is where the different language keyboard layout files are. I use **pt** and I'll use that as an example. First, backup the file you want to edit so you can put things back normal again if not satisfied. For that do:

```
cp /usr/share/X11/xkb/symbols/pt /usr/share/X11/xkb/symbols/pt_backup
``` 
just change **pt** for your selected keyboard.

now open the file:

```
sudo gedit /usr/share/X11/xkb/symbols/pt
``` 
You'll see something like this (it's not the complete file, but just a part of it):[INDENT]    [SIZE=1]key <AE01> { [ 1, copyright, registered, trademark ] };
    key <AE03> { [ 3, numbersign, section, paragraph ] };
    key <AE04> { [ 4, EuroSign, dollar, sterling ] };
    key <AE11> { [ masculine, ordfeminine, dead_circumflex, dead_caron ] };
    key <AE12> { [apostrophe, asterisk, plus, dead_abovering ] };

    key <AD11> { [dead_acute, dead_grave, dead_diaeresis, dead_macron ] };
    key <AD12> { [question, exclam, questiondown, slash ] };
    key <AC10> { [ ccedilla, Ccedilla, dead_acute, dead_doubleacute ] };
    key <AC11> { [dead_tilde, dead_circumflex, dead_diaeresis, dead_breve] };
    key <TLDE> { [ backslash, bar, notsign, notsign ] };

    key <BKSL> { [question, exclam, questiondown, slash ] };[/SIZE]
[/INDENT]The entries with key <xxxx> are the name of the keys (based on xkb keycodes*) and their resulting symbols*. There are four symbols you can get when pressing a given key: normal (no modifier key), with Shift key modifier, with Alt Gr key modifier and with Alt Gr + Shift key modifiers.

Let's take a look at a particular example. Where is located the [SIZE=2]key <AE12>? You can take a look at following image:

[IMG]http://www.charvolant.org/%7Edoug/xkb/html/img3.png[/IMG]

or you can understand the logic behind it. The key [/SIZE][SIZE=2]<**[COLOR=Red]A[/COLOR][COLOR=SeaGreen]E[/COLOR][COLOR=Blue]12[/COLOR]**> is located is an **[COLOR=Red]A[/COLOR]**lphanumeric character, located at the row **[COLOR=SeaGreen]E[/COLOR]** at the column **[COLOR=Blue]12[/COLOR]**. You can understand the rows and columns layout looking at the picture below:
[IMG]http://static.flickr.com/60/159120197_cbc62be32d_b.jpg[/IMG]
[/SIZE]
The other keys, like Control, Alt, and so on, have particular keycodes names. Consult the list of available keycodes to know the key you want.


[SIZE=3]**2. The Actual Configuration**[/SIZE][LIST]
[*]Look at you keyboard and have a thought on what keys you like to change.
[*]Go to your opened language file (**pt **in my case).
[*]Edit the entries accordingly to your needs.[/LIST]**Example:**

I wanted to change the dead accent and the dead tilde location** as I find them rather unergonomically on the pt keyboard. As such, I edited the file and exchanged the places of the symbols entries for those keys:

    key <AD11>    { [     [COLOR=Red]plus,   asterisk, dead_diaeresis, dead_abovering[/COLOR] ] };
    key <AD12>    { [[COLOR=Blue]dead_acute, dead_grave,   dead_tilde,  dead_macron[/COLOR] ]    };

and:

    key <AC10>    { [  [COLOR=DarkGreen]ccedilla,   Ccedilla,   dead_acute, dead_doubleacute[/COLOR] ] };
    key <AC11>    { [ [COLOR=Magenta]masculine, ordfeminine, dead_circumflex,   dead_caron[/COLOR] ] };

to become:

    key <AD11>    { [[COLOR=Blue]dead_acute, dead_grave,   dead_tilde,  dead_macron[/COLOR] ] };
    key <AD12>    { [      [COLOR=Red]plus,   asterisk, dead_diaeresis, dead_abovering[/COLOR] ]    };

and: 

    key <AC10>    { [ [COLOR=Magenta]masculine, ordfeminine, dead_circumflex,   dead_caron[/COLOR] ] };
    key <AC11>    { [  [COLOR=DarkGreen]ccedilla,   Ccedilla,   dead_acute, dead_doubleacute[/COLOR] ] };

It's easy as this. Remember that you can even put different symbols that weren't there in the first place, like making your backspace key type an ® you you want. It's all up to you. 

You then[LIST]
[*]save the file
[*]restart your X session (logout and press ctrl+alt+backspace[/LIST]Before you do this, take a look at the next section, 3. Hints.


[SIZE=3]**3. Hints**[/SIZE]

1. Since to try the new keyboard layout you'll need to restart your X session, you can use this trick to test it without abandoning your current session. After saving the file, you open a terminal and type:

```
sudo xinit -- :2
``` 
This will open a new screen with a terminal on it. Type around on that terminal to see if you got the expected results. To end that session, just press ctrl+alt+backspace and you'll get back to your current session again. Do this as many times as you like it until you have achived your final keyboard layout.

2. If you really like your new keyboard layout (like I do) and want it to survice future installations, you just have to put your keyboard layout file on a archive folder on you home (supposing you have a different partition for you /home) and then link the file to the actual file on /etc.

** example:**

You create a archive folder on your /home on the location:

/home/archive/keyboard/layout

and put there your layout file my_layout.

Then you just have to backup your language layout file (probably you just did on the beginning of the HowTo) and then link your layout file to the actual language layout file, like this:

```
sudo ln -sf /home/archive/keyboard/layout/my_layout /usr/share/X11/xkb/symbols/pt
``` 
Just adjust the folders and file names to your needs. Your layout will be preserved even if newly install your system. You can repeat the link step after an installation to get you layout working again.


[SIZE=3]**4. Documentation**[/SIZE]

You can find further information about this topic on the following sites:[LIST]
[*][**An unreliable guide to xkb configuration**]("http://www.charvolant.org/%7Edoug/xkb/html/index.html") (don't let the name fool you)
[*][**How to configure xkb**]("http://pascal.tsu.ru/en/xkb/setup.html")[/LIST][SIZE=3]
**5.** **Reverting to the Original Layout**[/SIZE]

1. Ok, you are not satisfied with the experience, you grow tired of your layout and want your old keyboard back. No problem, since you made a backup at the beginning of the HowTo. To revert to your original layout, you just have to do:

```
sudo cp /usr/share/X11/xkb/symbols/pt_backup /usr/share/X11/xkb/symbols/pt
``` 
After this, you just have to restart your X session and next time you login you'll have the normal layout again. Please note that the **pt** must be changed to your own language keyboard layout.

2. You thought you were Dvorak himself and changed your complete keyboard layout. You were prepared to chalenge yourself for the hard work of learning a complete new set of keys and then you fail miserably in doing so, finding yourself stuck with a untypeable keyboard where it's a headache to find the keys. Don't stress. You have the layout backup. "But I can't type the commands!". 

No problem. Press ctrl+alt+F1 and you're on the console. Login and type:

```
sudo cp /usr/share/X11/xkb/symbols/pt_backup /usr/share/X11/xkb/symbols/pt
``` 
After this, press ctrl+alt+F7 to get back to your X session again. 

Restart your session and you'll have your normal keyboard back again.




*[SIZE=1]An extensive list of keycodes and symbols available can be found on the files I attached for your convinience.
[/SIZE]
[SIZE=1]**In actuality, I changed the location of all dead accents and the ? and the ! punctuation marks. I don't know who designated those keys on the Portuguese keyboard, but certainly it was not a professional typist versed in this language. It's not my point to discuss this here, so I just simplified the example.[/SIZE]

---

### Post by henriquemaia on 2006-06-06
I have updated the HowTo. I have added the section **Reverting to the Original Layout**.

---

### Post by ow50 on 2006-06-06
Another way to configure the keyboard for X is to use a ~/.xmodmap file. It gets loaded automatically on X login. You can get the keycodes at least with xev (run in terminal). As an example, SWE/FIN Colemak layout.
```
! Q W F P G   J L U Y Ö Å ¨
!  A R S T D   H N E I O Ä '
! < Z X C V B   K M , . -

!keycode   9 = Escape Escape
!keycode  10 = 1 exclam
!keycode  11 = 2 quotedbl at
!keycode  12 = 3 numbersign sterling
!keycode  13 = 4 currency dollar
!keycode  14 = 5 percent
!keycode  15 = 6 ampersand
!keycode  16 = 7 slash braceleft
!keycode  17 = 8 parenleft bracketleft
!keycode  18 = 9 parenright bracketright
!keycode  19 = 0 equal braceright
!keycode  20 = plus question backslash
!keycode  21 = dead_acute dead_grave
!keycode  22 = BackSpace Terminate_Server
!keycode  23 = Tab Tab
keycode  24 = q Q
keycode  25 = w W
keycode  26 = f F
keycode  27 = p P
keycode  28 = g G
keycode  29 = j J
keycode  30 = l L
keycode  31 = u U
keycode  32 = y Y
keycode  33 = odiaeresis Odiaeresis
keycode  34 = aring Aring
!keycode  35 = diaeresis asciicircum dead_tilde
!keycode  36 = Return
!keycode  37 = Control_L
keycode  38 = a A
keycode  39 = r R
keycode  40 = s S
keycode  41 = t T
keycode  42 = d D
keycode  43 = h H
keycode  44 = n N
keycode  45 = e E EuroSign
keycode  46 = i I
keycode  47 = o O
keycode  48 = adiaeresis Adiaeresis
!keycode  49 = section onehalf
!keycode  50 = Shift_L
!keycode  51 = apostrophe asterisk
keycode  52 = z Z
keycode  53 = x X
keycode  54 = c C
keycode  55 = v V
keycode  56 = b B
keycode  57 = k K
keycode  58 = m M
!keycode  59 = comma semicolon
!keycode  60 = period colon
!keycode  61 = minus underscore
!keycode  62 = Shift_R
!keycode  63 = KP_Multiply
!keycode  64 = Alt_L
!keycode  65 = space
!keycode  66 = Caps_Lock
!keycode  67 = F1 XF86_Switch_VT_1
!keycode  68 = F2 XF86_Switch_VT_2
!keycode  69 = F3 XF86_Switch_VT_3
!keycode  70 = F4 XF86_Switch_VT_4
!keycode  71 = F5 XF86_Switch_VT_5
!keycode  72 = F6 XF86_Switch_VT_6
!keycode  73 = F7 XF86_Switch_VT_7
!keycode  74 = F8 XF86_Switch_VT_8
!keycode  75 = F9 XF86_Switch_VT_9
!keycode  76 = F10 XF86_Switch_VT_10
!keycode  77 = Num_Lock
!keycode  78 = Scroll_Lock
!keycode  79 = KP_Home KP_7
!keycode  80 = KP_Up KP_8
!keycode  81 = KP_Prior KP_9
!keycode  82 = KP_Subtract
!keycode  83 = KP_Left KP_4
!keycode  84 = KP_Begin KP_5
!keycode  85 = KP_Right KP_6
!keycode  86 = KP_Add
!keycode  87 = KP_End KP_1
!keycode  88 = KP_Down KP_2
!keycode  89 = KP_Next KP_3
!keycode  90 = KP_Insert KP_0
!keycode  91 = KP_Delete KP_Decimal
!keycode  94 = less greater bar
!keycode  95 = F11 XF86_Switch_VT_11
!keycode  96 = F12 XF86_Switch_VT_12
!keycode  97 = Home
!keycode  98 = Up
!keycode  99 = Prior
!keycode 100 = Left
!keycode 102 = Right
!keycode 103 = End
!keycode 104 = Down
!keycode 105 = Next
!keycode 106 = Insert
!keycode 107 = Delete
!keycode 108 = KP_Enter
!keycode 109 = Control_R
!keycode 110 = Pause Break
!keycode 111 = Print Execute
!keycode 112 = KP_Divide
!keycode 113 = Mode_switch
!keycode 115 = Super_L
!keycode 116 = Super_R
!keycode 117 = Menu
```

For virtual consoles, a separate .kmap file is needed. See /usr/share/keymaps for examples. As an example, SWE/FIN Colemak layout in file ~/.colemak.kmap.
```
# Q W F P G   J L U Y Ö Å ¨
#  A R S T D   H N E I O Ä '
# < Z X C V B   K M , . -

charset "iso-8859-1"
keymaps 0-2,4-6,8-10,12-14
alt_is_meta
include "qwerty-layout"
include "linux-with-alt-and-altgr"
strings as usual

keycode  1 = Escape
keycode  2 = one exclam
keycode  3 = two quotedbl at
keycode  4 = three numbersign sterling
keycode  5 = four dollar dollar
keycode  6 = five percent
keycode  7 = six ampersand
keycode  8 = seven slash braceleft
keycode  9 = eight parenleft bracketleft
keycode 10 = nine parenright bracketright
keycode 11 = zero equal braceright
keycode 12 = plus question backslash
keycode 13 = dead_acute dead_grave
keycode 14 = Delete
keycode 15 = Tab
keycode 16 = q
keycode 17 = w
keycode 18 = f
keycode 19 = p
keycode 20 = g
keycode 21 = j
keycode 22 = l
keycode 23 = u
keycode 24 = y
keycode 25 = odiaeresis Odiaeresis
keycode 26 = aring Aring
keycode 27 = diaeresis asciicircum dead_tilde
keycode 28 = Return
keycode 29 = Control
keycode 30 = a
keycode 31 = r
keycode 32 = s
keycode 33 = t
keycode 34 = d
keycode 35 = h
keycode 36 = n
keycode 37 = e
keycode 38 = i
keycode 39 = o
keycode 40 = adiaeresis Adiaeresis
keycode 41 = section onehalf
keycode 42 = Shift
keycode 43 = apostrophe asterisk
keycode 44 = z
keycode 45 = x
keycode 46 = c
keycode 47 = v
keycode 48 = b
keycode 49 = k
keycode 50 = m
keycode 51 = comma semicolon
keycode 52 = period colon
keycode 53 = minus underscore
keycode 54 = Shift
keycode 56 = Alt
keycode 57 = space
keycode 58 = Caps_Lock
keycode 86 = less greater bar
keycode 97 = Control
```

Handy aliases for virtual console
```
alias asdf='sudo loadkeys ~/.colemak.kmap'
alias arst='sudo loadkeys fi-latin1'
```

---

### Post by henriquemaia on 2006-06-06
[quote=ow50]Another way to configure the keyboard for X is to use a ~/.xmodmap file. It gets loaded automatically on X login. You can get the keycodes at least with xev (run in terminal). As an example, SWE/FIN Colemak layout.
```
! Q W F P G   J L U Y Ö Å ¨
!  A R S T D   H N E I O Ä '
! < Z X C V B   K M , . -

!keycode   9 = Escape Escape
!keycode  10 = 1 exclam
!keycode  11 = 2 quotedbl at
!keycode  12 = 3 numbersign sterling
!keycode  13 = 4 currency dollar
!keycode  14 = 5 percent
!keycode  15 = 6 ampersand
!keycode  16 = 7 slash braceleft
!keycode  17 = 8 parenleft bracketleft
!keycode  18 = 9 parenright bracketright
!keycode  19 = 0 equal braceright
!keycode  20 = plus question backslash
!keycode  21 = dead_acute dead_grave
!keycode  22 = BackSpace Terminate_Server
!keycode  23 = Tab Tab
keycode  24 = q Q
keycode  25 = w W
keycode  26 = f F
keycode  27 = p P
keycode  28 = g G
keycode  29 = j J
keycode  30 = l L
keycode  31 = u U
keycode  32 = y Y
keycode  33 = odiaeresis Odiaeresis
keycode  34 = aring Aring
!keycode  35 = diaeresis asciicircum dead_tilde
!keycode  36 = Return
!keycode  37 = Control_L
keycode  38 = a A
keycode  39 = r R
keycode  40 = s S
keycode  41 = t T
keycode  42 = d D
keycode  43 = h H
keycode  44 = n N
keycode  45 = e E EuroSign
keycode  46 = i I
keycode  47 = o O
keycode  48 = adiaeresis Adiaeresis
!keycode  49 = section onehalf
!keycode  50 = Shift_L
!keycode  51 = apostrophe asterisk
keycode  52 = z Z
keycode  53 = x X
keycode  54 = c C
keycode  55 = v V
keycode  56 = b B
keycode  57 = k K
keycode  58 = m M
!keycode  59 = comma semicolon
!keycode  60 = period colon
!keycode  61 = minus underscore
!keycode  62 = Shift_R
!keycode  63 = KP_Multiply
!keycode  64 = Alt_L
!keycode  65 = space
!keycode  66 = Caps_Lock
!keycode  67 = F1 XF86_Switch_VT_1
!keycode  68 = F2 XF86_Switch_VT_2
!keycode  69 = F3 XF86_Switch_VT_3
!keycode  70 = F4 XF86_Switch_VT_4
!keycode  71 = F5 XF86_Switch_VT_5
!keycode  72 = F6 XF86_Switch_VT_6
!keycode  73 = F7 XF86_Switch_VT_7
!keycode  74 = F8 XF86_Switch_VT_8
!keycode  75 = F9 XF86_Switch_VT_9
!keycode  76 = F10 XF86_Switch_VT_10
!keycode  77 = Num_Lock
!keycode  78 = Scroll_Lock
!keycode  79 = KP_Home KP_7
!keycode  80 = KP_Up KP_8
!keycode  81 = KP_Prior KP_9
!keycode  82 = KP_Subtract
!keycode  83 = KP_Left KP_4
!keycode  84 = KP_Begin KP_5
!keycode  85 = KP_Right KP_6
!keycode  86 = KP_Add
!keycode  87 = KP_End KP_1
!keycode  88 = KP_Down KP_2
!keycode  89 = KP_Next KP_3
!keycode  90 = KP_Insert KP_0
!keycode  91 = KP_Delete KP_Decimal
!keycode  94 = less greater bar
!keycode  95 = F11 XF86_Switch_VT_11
!keycode  96 = F12 XF86_Switch_VT_12
!keycode  97 = Home
!keycode  98 = Up
!keycode  99 = Prior
!keycode 100 = Left
!keycode 102 = Right
!keycode 103 = End
!keycode 104 = Down
!keycode 105 = Next
!keycode 106 = Insert
!keycode 107 = Delete
!keycode 108 = KP_Enter
!keycode 109 = Control_R
!keycode 110 = Pause Break
!keycode 111 = Print Execute
!keycode 112 = KP_Divide
!keycode 113 = Mode_switch
!keycode 115 = Super_L
!keycode 116 = Super_R
!keycode 117 = Menu
``` 
For virtual consoles, a separate .kmap file is needed. See /usr/share/keymaps for examples. As an example, SWE/FIN Colemak layout in file ~/.colemak.kmap.
```
# Q W F P G   J L U Y Ö Å ¨
#  A R S T D   H N E I O Ä '
# < Z X C V B   K M , . -

charset "iso-8859-1"
keymaps 0-2,4-6,8-10,12-14
alt_is_meta
include "qwerty-layout"
include "linux-with-alt-and-altgr"
strings as usual

keycode  1 = Escape
keycode  2 = one exclam
keycode  3 = two quotedbl at
keycode  4 = three numbersign sterling
keycode  5 = four dollar dollar
keycode  6 = five percent
keycode  7 = six ampersand
keycode  8 = seven slash braceleft
keycode  9 = eight parenleft bracketleft
keycode 10 = nine parenright bracketright
keycode 11 = zero equal braceright
keycode 12 = plus question backslash
keycode 13 = dead_acute dead_grave
keycode 14 = Delete
keycode 15 = Tab
keycode 16 = q
keycode 17 = w
keycode 18 = f
keycode 19 = p
keycode 20 = g
keycode 21 = j
keycode 22 = l
keycode 23 = u
keycode 24 = y
keycode 25 = odiaeresis Odiaeresis
keycode 26 = aring Aring
keycode 27 = diaeresis asciicircum dead_tilde
keycode 28 = Return
keycode 29 = Control
keycode 30 = a
keycode 31 = r
keycode 32 = s
keycode 33 = t
keycode 34 = d
keycode 35 = h
keycode 36 = n
keycode 37 = e
keycode 38 = i
keycode 39 = o
keycode 40 = adiaeresis Adiaeresis
keycode 41 = section onehalf
keycode 42 = Shift
keycode 43 = apostrophe asterisk
keycode 44 = z
keycode 45 = x
keycode 46 = c
keycode 47 = v
keycode 48 = b
keycode 49 = k
keycode 50 = m
keycode 51 = comma semicolon
keycode 52 = period colon
keycode 53 = minus underscore
keycode 54 = Shift
keycode 56 = Alt
keycode 57 = space
keycode 58 = Caps_Lock
keycode 86 = less greater bar
keycode 97 = Control
``` 
Handy aliases for virtual console
```
alias asdf='sudo loadkeys ~/.colemak.kmap'
alias arst='sudo loadkeys fi-latin1'
```[/quote]

Thanks, nice to know this! I wasn't aware of this other way. I'm very familiarized with the method I presented, but yours looks much simpler.

---

### Post by soren.kyale on 2007-07-06
I have two questions:

How can I create my own dead keys, or modify existing dead keys.
     I use semicolon and comma as dead keys, and they don't quite match any of the existing dead keys.

How do I save configuration settings?
     I modified the us file under etc\x11\xkb\symbols . But I get an access denied message every time I try to save it. I also tried saving to usr\share\x11\xkb .

I'm using the Feisty version of Kubuntu. Konqueror and Kite are the programs I attempted to save the changes with.

---

### Post by henriquemaia on 2007-07-06
> **soren.kyale said:**
> I have two questions:

How can I create my own dead keys, or modify existing dead keys.
     I use semicolon and comma as dead keys, and they don't quite match any of the existing dead keys.

How do I save configuration settings?
     I modified the us file under etc\x11\xkb\symbols . But I get an access denied message every time I try to save it. I also tried saving to usr\share\x11\xkb .

I'm using the Feisty version of Kubuntu. Konqueror and Kite are the programs I attempted to save the changes with.

I’m not very familiar with dead keys, so I can’t help you much on this. But regarding on the issue of not being able to save your changes, that is most certainly due to the fact that you must edit the files using **sudo**, otherwise you do not have the permissions to write to those files.

If you use konqueror to access and edit the files, run konqueror in sudo mode, i.e. open a terminal and type: **sudo konqueror**

---

### Post by soren.kyale on 2007-07-07
Thank you. "Sudo konqueror" really helped. Though it made me realize that the admin (root) level belongs to the system not the user. There's something evil about that ("Dave, what are you doing Dave?"). But at least I have the basic keys of my layout working.

Now, I just need to add the dead keys and turn my left alt to a shift, my left winkey to alt, caps lock to winkey, backspace to caps lock and AB05 to backspace.

Thank you, Henriquemaia, you helped me a great deal (I thought Sudo was just a copy command).

---

### Post by Yellow Onion on 2007-09-25
Hello Ive Made a international dvorak with dead keys layout variant  in the us file. woks fine

but it isnt in the layout list for gnome, im not exactly sure how i got it running i have set it through xorg.conf file and i can select it through kcontrol 
just not through gnome keyboard settings
Is there a a cache that need refreshing or is it something else

add this to bottom of the us file if you want to use it
```

partial alphanumeric_keys
xkb_symbols "dv-intl" {

        name[Group1]= "Dvorak - International (with dead keys)";
        
    include "us(dvorak)"

   key <TLDE> { [dead_grave, dead_tilde,         grave,       asciitilde ] };
    key <AE01> { [         1,     exclam,    exclamdown,      onesuperior ] };
    key <AE02> { [         2,         at,   twosuperior, dead_doubleacute ] };
    key <AE03> { [         3, numbersign, threesuperior,      dead_macron ] };
    key <AE04> { [         4,     dollar,      currency,         sterling ] };
    key <AE05> { [         5,    percent,      EuroSign                   ] };
    key <AE06> { [    6, dead_circumflex,    onequarter,      asciicircum ] };
    key <AE07> { [         7,  ampersand,       onehalf,        dead_horn ] };
    key <AE08> { [         8,   asterisk, threequarters,      dead_ogonek ] };
    key <AE09> { [         9,  parenleft, leftsinglequotemark, dead_breve ] };
    key <AE10> { [         0, parenright, rightsinglequotemark, dead_abovering ] };
    key <AE11> { [ bracketleft,  braceleft,  guillemotleft, guillemotleft ] };
    key <AE12> { [bracketright, braceright, guillemotright,guillemotright ] };

    key <AD01> { [dead_acute, dead_diaeresis, apostrophe,        quotedbl ] };
    key <AD02> { [     comma,       less,      ccedilla,         Ccedilla ] };
    key <AD03> { [    period,    greater, dead_abovedot,       dead_caron ] };
    key <AD04> { [         p,          P,    odiaeresis,       Odiaeresis ] };
    key <AD05> { [         y,          Y,    udiaeresis,       Udiaeresis ] };
    key <AD08> { [         c,          C,     copyright,             cent ] };
    key <AD09> { [         r,          R,    registered,       registered ] };
    key <AD10> { [         l,          L,        oslash,         Ooblique ] };
    key <AD11> { [     slash,   question,  questiondown,        dead_hook ] };
    key <AD12> { [     equal,       plus,      multiply,         division ] };
    key <AD13> { [ backslash,        bar,       notsign,        brokenbar ] };


    key <AC01> { [         a,          A,        aacute,           Aacute ] };
    key <AC02> { [         o,          O,        oacute,           Oacute ] };
    key <AC03> { [         e,          E,        eacute,           Eacute ] };
    key <AC04> { [         u,          U,        uacute,           Uacute ] };
    key <AC05> { [         i,          I,        iacute,           Iacute ] };
    key <AC06> { [         d,          D,           eth,              ETH ] };
    key <AC08> { [         t,          T,         thorn,            THORN ] };
    key <AC09> { [         n,          N,        ntilde,           Ntilde ] };
    key <AC10> { [         s,          S,        ssharp,          section ] };
    key <AC11> { [     minus, underscore,           yen,    dead_belowdot ] };


    key <AB01> { [ semicolon,      colon,     paragraph,           degree ] };
    key <AB02> { [         q,          Q,    adiaeresis,       Adiaeresis ] };
    key <AB07> { [         m,          M,            mu,               mu ] };
    key <AB08> { [         w,          W,         aring,            Aring ] };
    key <AB10> { [         z,          Z,            ae,               AE ] };

    include "level3(ralt_switch)"
};

```

---

### Post by jtschrock on 2007-10-10
What does the syntax look like when you want to use UTF-8 encoding rather than the standard naming conventions like "ssharp" and "period" to make your layout?

I'm used to stuff looking like U+026C and U+F242 and I'm pretty sure that's not the correct syntax in XKB. (alright all you unicode linguistics freaks out there, based on the symbols I just mentioned, what part of the world/languages am I dealing with?)

thanks

---

### Post by Dries_Lee on 2007-12-06
I've got a question about this method. When I change my keymap to the following (the rest stays the same):
```
key <AE08> { [	    8,	asterisk, dead_breve ]	};

...

include "level3(ralt_switch)"
```
the breve (&#728;) only works with the 'a' (&#259;), not with other letters. While I actually only need the 'u' with a breve...

Do you have any idea on how to fix this?

Thanks,
Dries

---

### Post by henriquemaia on 2007-12-06
> **Dries_Lee said:**
> I've got a question about this method. When I change my keymap to the following (the rest stays the same):
```
key <AE08> { [        8,    asterisk, dead_breve ]    };

...

include "level3(ralt_switch)"
```the breve (&#728;) only works with the 'a' (&#259;), not with other letters. While I actually only need the 'u' with a breve...

Do you have any idea on how to fix this?

Thanks,
Dries

I have tried to use the dead_breve with u here and it don&#8217;t work either. I have no clue why is that. Looks like a limitation from xkb (?). Or is it?


EDIT: I don&#8217;t know if this helps, but you can edit your file to use **ubreve**, which will result in the u with &#728;. You can also define keys for **abreve **and **gbreve**.

---

### Post by Dries_Lee on 2007-12-06
Using ubreve works, but only half. Capital U with breve doesn't show up. But thanks for the help anyway.

---

### Post by henriquemaia on 2007-12-06
> **Dries_Lee said:**
> Using ubreve works, but only half. Capital U with breve doesn't show up. But thanks for the help anyway.

For capital U breve, you have to add **Ubreve**.

The same applies to **Abreve** and **Gbreve**.

---

### Post by boob11 on 2008-02-01
Thanks

==========

:lolflag:

---

### Post by &#956;&#964;w on 2009-09-02
Sorry for digging out this thread again, but I have a question:

I want to add ancient greek letters to my keyboard. Do I have to write the Unicode like "03BF" or "omikron"?

Example:

Is it right this way (just an example, not right unicode):
```
[SIZE=1]key <BKSL> { [omikron, omikron_capital, omikron_whatthehell, omikron_etc ] };[/SIZE]
```or this way:

[SIZE=1]```
key <BKSL> { [03BF, 031A, 03C2, 03C3 ] };
```[/SIZE]?

Thanks a lot for your answer...

µ&#964;w

---

### Post by henriquemaia on 2009-09-02
> **&#956 said:**
> Sorry for digging out this thread again, but I have a question:

I want to add ancient greek letters to my keyboard. Do I have to write the Unicode like "03BF" or "omikron"?

Example:

Is it right this way (just an example, not right unicode):
```
[SIZE=1]key <BKSL> { [omikron, omikron_capital, omikron_whatthehell, omikron_etc ] };[/SIZE]
```or this way:

[SIZE=1]```
key <BKSL> { [03BF, 031A, 03C2, 03C3 ] };
```[/SIZE]?

Thanks a lot for your answer...

µ&#964;w

As far as I know, you use the first (omikron, etc). You don't need the actual codes (that would be really confusing).

:)

---

### Post by &#956;&#964;w on 2009-09-02
Thanks for your answer.

But, what if I want to write a capital omikron, an omikron with spiritus lenis, with spiritus asper...?

Do I have to define them as accents as ^+e=ê? If so, how are the spiriti called? asper and lenis?

And: I also need a Iota Subscriptum, how should I do this???

really confused,

µ&#964;w

---

### Post by Ubumanda on 2009-09-11
[I]I have the Netbook Remix version of Jaunty, and I have no /etc/X11/xkb/symbols dir; the only thing I have in /etc/X11/xkb/ is /etc/X11/xkb/base.xml.  Is there a new way to do this?
[/I]
Edited to answer: directories have moved to /usr/share/X11/xkb.  Hope this helps others.

---

### Post by -_- Joseph -_- on 2009-09-11
Very nice tutorial helped me a lot

                           ,Joseph

---

### Post by Olympus21 on 2009-10-15
Though it made me realize that the admin (root) level belongs to the system not the user. There's something evil about that ("Dave, what are you doing Dave?"). But at least I have the basic keys of my layout working.

Regards

Olympus

_____
[dossier surendettement]("http://dossierdesurendettement.net/dossier-de-surendettement/dossier-de-surendettement")

---

### Post by LuciusMare on 2009-11-10
And what if i dont have any "pt" ?

```
root@tomas-desktop:/# cd /etc/X11/
root@tomas-desktop:/etc/X11# ls
app-defaults             xkb                                  xorg.conf_zaloha
cursors                  Xloadimage                           Xresources
default-display-manager  xorg.conf                            Xsession
fonts                    xorg.conf.backup                     Xsession.d
rgb.txt                  xorg.conf.dist-upgrade-200904232119  Xsession.options
X                        xorg.conf.dist-upgrade-200911012211  XvMCConfig
xinit                    xorg.conf.failsafe                   Xwrapper.config
root@tomas-desktop:/etc/X11# cd xkb
root@tomas-desktop:/etc/X11/xkb# ls -a
.  ..  base.xml
root@tomas-desktop:/etc/X11/xkb#

```

---

### Post by henriquemaia on 2009-11-10
> **LuciusMare said:**
> And what if i dont have any "pt" ?

```
root@tomas-desktop:/# cd /etc/X11/
root@tomas-desktop:/etc/X11# ls
app-defaults             xkb                                  xorg.conf_zaloha
cursors                  Xloadimage                           Xresources
default-display-manager  xorg.conf                            Xsession
fonts                    xorg.conf.backup                     Xsession.d
rgb.txt                  xorg.conf.dist-upgrade-200904232119  Xsession.options
X                        xorg.conf.dist-upgrade-200911012211  XvMCConfig
xinit                    xorg.conf.failsafe                   Xwrapper.config
root@tomas-desktop:/etc/X11# cd xkb
root@tomas-desktop:/etc/X11/xkb# ls -a
.  ..  base.xml
root@tomas-desktop:/etc/X11/xkb#

```

> just change **pt** for your selected keyboard.

what's your keyboard? Just use the one you have.

---

### Post by Abhinav K Sahdev on 2010-04-19
Hi 
I am using ubuntu 9.10 on a compaq presario v5205TU laptop. I need to create a personal layout as everything dosen't work with the default one. I tried your method but there is no pt file or symbols directory in the /etc/X11/xkb dir. what should i do now?
thanks

---

### Post by henriquemaia on 2010-04-19
The files are now located at /usr/share/X11/xkb/symbols

Still works once you edit the desired file (you can use your language as base for the modification).

Good luck.

---

### Post by ernsttremel on 2010-05-12
I've just installed Ubuntu 10.04 some days ago.

On my system there is nothing in 
/etc/X11/xkb

So can you pleas tell me where the in builted keyboard layouts in this Ubuntu version are located.
Am I right to suppose that one can modify one of these keyboard layouts to make a new one?

---

### Post by henriquemaia on 2010-05-12
> **ernsttremel said:**
> I've just installed Ubuntu 10.04 some days ago.

On my system there is nothing in 
/etc/X11/xkb

So can you pleas tell me where the in builted keyboard layouts in this Ubuntu version are located.
Am I right to suppose that one can modify one of these keyboard layouts to make a new one?

As stated in the previous post, the files are now located in the folder /usr/share/X11/xkb/symbols/

example:
```

henriquemaia@EeePC ~ $ ls /usr/share/X11/xkb/symbols/
ad        cn            gn       kr              nbsp      sn
af        compose       gr       kz              nec_vndr  sony_vndr
al        ctrl          group    la              ng        srvr_ctrl
altwin    cz            hp_vndr  latam           nl        sun_vndr
am        de            hr       latin           no        sy
ara       digital_vndr  hu       level3          np        terminate
az        dk            ie       level5          olpc      th
ba        ee            il       lk              pc        tj
bd        epo           in       lt              pk        tm
be        es            inet     lv              pl        tr
bg        et            iq       ma              pt        typo
br        eurosign      ir       macintosh_vndr  ro        ua
brai      fi            is       mao             rs        us
bt        fo            it       me              ru        uz
by        fr            jp       mk              se        vn
ca        fujitsu_vndr  keypad   mm              sgi_vndr  xfree68_vndr
capslock  gb            kg       mn              shift     za
cd        ge            kh       mt              si
ch        gh            kpdl     mv              sk
```


**I've updated the **howto** to reflect xkb's files new locations.

---

### Post by ernsttremel on 2010-05-12
Thank you.
Now I found the necessary files.

I inspect to make a new keyboard layout for Avestan (Unicode  ranges U+10B00 to U+10B3F and U+10B78 to U+10B7F)

This language is written from right to left, like Hebrew but without any diacritics like there and in Arabic.
In Open Office Writer using the Symbols-Input feature shows that these Unicode ranges are supported.

So I think I should modify the Hebrew keyboard layout. I tried to find it in \.\.\symbols but I could not locate it. 
Can you plese give e some informations which file in \.\.\symbols I can take as starting file?

---

### Post by henriquemaia on 2010-05-12
Unfortunately I cannot assist you in this because I haven't dug that deep when I made the research for this howto. That is a very particular instance where you need the help of someone far more knowledgeable than me. 

You've probably tried that first, but have you googled specificly for that?

---

### Post by simosx on 2010-05-25
> **ernsttremel said:**
> Thank you.
Now I found the necessary files.

I inspect to make a new keyboard layout for Avestan (Unicode  ranges U+10B00 to U+10B3F and U+10B78 to U+10B7F)

This language is written from right to left, like Hebrew but without any diacritics like there and in Arabic.
In Open Office Writer using the Symbols-Input feature shows that these Unicode ranges are supported.

So I think I should modify the Hebrew keyboard layout. I tried to find it in \.\.\symbols but I could not locate it. 
Can you plese give e some informations which file in \.\.\symbols I can take as starting file?

The Hebrew keyboard layout is located at /usr/share/X11/xkb/symbols/il
All layouts are found in /usr/share/X11/xkb/symbols/

There is an advanced tool for keyboard layout creation at [http://github.com/simos/keyboardlayouteditor](http://github.com/simos/keyboardlayouteditor)
Requires some skill to setup and use.

Having read the Wikipedia page on the Avestan language, I see that just recently the Avestan script has been added to the Unicode standard. I suggest to
1. Install a Unicode Avestan font in Linux. Apparently ALPHABETUM UNICODE supports the Avestan script. You install new fonts in ~/.fonts/
2. If the script is right to left or left to right, this is not a problem with the keyboard layout, so there is no requirement to use the Hebrew layout as starting point.
3. What I would wholeheartedly recommend is for you to design the keyboard layout first. Use a drawing program so write the Unicode codepoints (such as 'U+10B00') on a keyboard. Having that, it is possible to get even someone else to make the layout for you.

Good luck!:guitar:

---

### Post by edwardfmo on 2010-05-26
hello!

this thread really helped me out, but i have 2 question.

first, is that symbol list complete, or if not, where can i get the complete one?

second, is there a way to determine, which keyboard file is used? because a have to make an on-screen keyboard for the current lenguage settings, so i thought, these files will provide the layouts, but i still have to get the current settings.

by the way, i'm using JAVA.

thanks in advance!

---

### Post by TheFu on 2010-05-26
> **ernsttremel said:**
> I've just installed Ubuntu 10.04 some days ago.
On my system there is nothing in 
/etc/X11/xkb
[FONT=Arial][SIZE=3]Same here - My /etc/X11/xkb directory is** completely empty.** No files, no subdirectories.

[/SIZE][/FONT][FONT=Fixedsys]# /etc/X11/xkb$ **\ls -al**
total 8
drwxr-xr-x 2 root root    1 2010-04-15 08:12 ./
drwxr-xr-x 9 root root 4096 2010-05-26 09:30 ../
[/FONT][FONT=Fixedsys]# /etc/X11/xkb$ **setxkbmap -print**
xkb_keymap {
        xkb_keycodes  { include "evdev+aliases(qwerty)" };
        xkb_types     { include "complete"      };
        xkb_compat    { include "complete"      };
        xkb_symbols   { include "pc+us+inet(evdev)+level3(ralt_switch)" };
        xkb_geometry  { include "pc(pc105)"     };
};[/FONT]

I'm looking for where (which file) to change the level3(ralt_switch) setting to be useful - either for accents or to mirror the lalt_switch.  I'm running X/Windows with Lubuntu 10.04. The base install was  Ubuntu x64 Server 10.04, then I added LXDE Desktop.

Any idea where the xkb settings are now?  Ah ... seems they've been moved to [B]/usr/share/X11/xkb/symbols
[/B]

---

### Post by ernsttremel on 2010-05-26
> **simosx said:**
> The Hebrew keyboard layout is located at /usr/share/X11/xkb/symbols/il
All layouts are found in /usr/share/X11/xkb/symbols/

There is an advanced tool for keyboard layout creation at [http://github.com/simos/keyboardlayouteditor](http://github.com/simos/keyboardlayouteditor)
Requires some skill to setup and use.

Having read the Wikipedia page on the Avestan language, I see that just recently the Avestan script has been added to the Unicode standard. I suggest to
1. Install a Unicode Avestan font in Linux. Apparently ALPHABETUM UNICODE supports the Avestan script. You install new fonts in ~/.fonts/
2. If the script is right to left or left to right, this is not a problem with the keyboard layout, so there is no requirement to use the Hebrew layout as starting point.
3. What I would wholeheartedly recommend is for you to design the keyboard layout first. Use a drawing program so write the Unicode codepoints (such as 'U+10B00') on a keyboard. Having that, it is possible to get even someone else to make the layout for you.

Good luck!:guitar:
That's great. I've added the required informations about the Avestan keyboard layout as PDF files and the nesessary font in the attached file. And I hope somebody will be able the keyboard layout and forward the instructions to me how to use it in Ubuntu 10.04.
Thank you very much.

---

### Post by simosx on 2010-05-27
> **ernsttremel said:**
> That's great. I've added the required informations about the Avestan keyboard layout as PDF files and the nesessary font in the attached file. And I hope somebody will be able the keyboard layout and forward the instructions to me how to use it in Ubuntu 10.04.
Thank you very much.

Thanks for the layout description.
I managed to create a draft layout which I attach in avestan.txt.

How can you use it?

1. Add avestan.txt at the end of /usr/share/X11/xkb/symbols/ir

sudo gedit /usr/share/X11/xkb/symbols/ir

in order to open (as administrator) the 'ir' layout, and paste the contents of avestan.txt at the end of the 'ir' file. Click Save and exit.

2. Register the new 'avestan' layout in evdev.xml and base.xml.

Both files have a section that looks like the following. Do a simple search for 'ku_ara' or some other string in order to find the segment.


```
        <variant>
          <configItem>
            <name>ku_ara</name>
            <description>Kurdish, Arabic-Latin</description>
            <languageList><iso639Id>kur</iso639Id></languageList>
          </configItem>
        </variant>
-----------HERE------------
      </variantList>
    </layout>
    <layout>
      <configItem>
        <name>iq</name>
        <shortDescription>Irq</shortDescription>
        <description>Iraq</description>
        <languageList><iso639Id>ara</iso639Id>
                      <iso639Id>kur</iso639Id></languageList>
      </configItem>

```

Open base.xml with
[INDENT]sudo gedit /usr/share/X11/xkb/rules/base.xml
[/INDENT]Then open evdev.xml with
[INDENT]sudo gedit /usr/share/X11/xkb/rules/evdev.xml[/INDENT]

Replace the '-----------HERE------------' with the following lines:

        <variant>
          <configItem>
            <name>avestan</name>
            <description>Avestan</description>
            <languageList><iso639Id>ae</iso639Id></languageList>
          </configItem>
        </variant>

What we do here is we insert a variant description for the 'avestan' keyboard layout.

Click Save and exit the text edit.

3. Install the font. Follow the steps from [http://www.bomahy.nl/hylke/blog/adding-fonts-in-gnome/](http://www.bomahy.nl/hylke/blog/adding-fonts-in-gnome/)
which says to install the font in your home directory, in a '.fonts' subdirectory. Normally, Ubuntu will pick up the font as soon as you copy it in there. Any newly started application should be able to use the new font.

4. Finally, add the new Avestan keyboard layout. Go to System/Preferences/Keyboard/Layouts, click on the [Add..] button and select from the list 'Iran' and layout 'Avestan'. Click OK. Notice the new keyboard layout indicator on the panel that allows you to switch between English and Avestan.

Thats it. Goold luck! :guitar:

p.s. You might not be able to write Avestan in Firefox since Avestan is a recent addition to Unicode. It worked fine for the Ubuntu text editor (gedit) and OpenOffice.org 3.2.

---

### Post by ernsttremel on 2010-06-07
Thank you very much for your instructions to install the Avestan keyboard layout.
It is working well.
I only had to modify the "avestant.txt" file. Maybe the Unicode Code points I'd sent were incorrect.
So I'll add it "corrected" again.
Kind regards and jia chara
Ernst tremel

---

### Post by ernsttremel on 2010-06-08
As I told you in my previous mail the Avestan keyboard is working well and as aspected.
But the onscreen keyboard looks like
"AVestan_onscreen-keyboard.jpg"
i.e. is showing the Unicode Code-Hex-Numbers instead of the Avestan glyphs.

Do you know a possibility how to modify the "avestan.txt" file to get the Avestan glyphs shown?

---

### Post by simosx on 2010-06-10
> **ernsttremel said:**
> As I told you in my previous mail the Avestan keyboard is working well and as aspected.
But the onscreen keyboard looks like
"AVestan_onscreen-keyboard.jpg"
i.e. is showing the Unicode Code-Hex-Numbers instead of the Avestan glyphs.

Do you know a possibility how to modify the "avestan.txt" file to get the Avestan glyphs shown?

Normally the characters should show up. What version of Linux do you use? 1) The Avestan script was added in Unicode 5.2 on Oct 2009, so your Linux version may have an older version of the 'glib' library.
2) The Avestan script has the characters in Plane 1, while all other layouts use Plane 0 (BMP). It could be a bug and should be reported anyway at [https://bugzilla.gnome.org/browse.cgi?product=libgnomekbd](https://bugzilla.gnome.org/browse.cgi?product=libgnomekbd)

I managed to create a screenshot of the layout which I attach.

---

### Post by ernsttremel on 2010-06-11
You wrote

"Normally the characters should show up. What version of Linux do you  use? 1) The Avestan script was added in Unicode 5.2 on Oct 2009, so your  Linux version may have an older version of the 'glib' library.
2) The Avestan script has the characters in Plane 1, while all other  layouts use Plane 0 (BMP). It could be a bug and should be reported  anyway at [https://bugzilla.gnome.org/browse.cg...ct=libgnomekbd]("https://bugzilla.gnome.org/browse.cgi?product=libgnomekbd")"

I use Ubuntu 10.04

---

### Post by simosx on 2010-06-12
> **ernsttremel said:**
> You wrote

"Normally the characters should show up. What version of Linux do you  use? 1) The Avestan script was added in Unicode 5.2 on Oct 2009, so your  Linux version may have an older version of the 'glib' library.
2) The Avestan script has the characters in Plane 1, while all other  layouts use Plane 0 (BMP). It could be a bug and should be reported  anyway at [https://bugzilla.gnome.org/browse.cg...ct=libgnomekbd]("https://bugzilla.gnome.org/browse.cgi?product=libgnomekbd")"

I use Ubuntu 10.04

Thanks.

I filed a bug report for this,
Bug 621367 - In keyboard display, characters for U+1xxxx appear as 'U1xxxx' (not as characters),
[https://bugzilla.gnome.org/show_bug.cgi?id=621367](https://bugzilla.gnome.org/show_bug.cgi?id=621367)
It is probably a bug in libgnomekbd. This keyboard layout is the first keyboard layout for the Unicode Plane 1 so there might be something small to fix.

I also blogged about this,
[http://simos.info/blog/archives/1134](http://simos.info/blog/archives/1134) :-)

---

### Post by ernsttremel on 2010-06-12
Thank you.
As I told you in a previous mail 
I corrected the avestan.txt file because some Avestan glyphs were positioned wrongly.
So I'l transmit you the corrected avestan.txt file as an attachment.

---

### Post by simosx on 2010-06-12
> **ernsttremel said:**
> Thank you.
As I told you in a previous mail 
I corrected the avestan.txt file because some Avestan glyphs were positioned wrongly.
So I'l transmit you the corrected avestan.txt file as an attachment.

Thanks, I updated my blog post with the new avestan.txt.

Your subsequent step would be to get the layout added to the xkeyboard-config project so that newer Linux distributions will have it in by default.
xkeyboard-config has a requirement to add new layouts in country files; therefore it makes sense to select 'ir' for Iran, for Avestan.
You can file a feature request following the link
[https://bugs.freedesktop.org/enter_bug.cgi?product=xkeyboard-config](https://bugs.freedesktop.org/enter_bug.cgi?product=xkeyboard-config)
As an example, see
[https://bugs.freedesktop.org/show_bug.cgi?id=2693](https://bugs.freedesktop.org/show_bug.cgi?id=2693)

---

### Post by ernsttremel on 2010-06-12
> **simosx said:**
> Thanks, I updated my blog post with the new avestan.txt.

Your subsequent step would be to get the layout added to the xkeyboard-config project so that newer Linux distributions will have it in by default.
xkeyboard-config has a requirement to add new layouts in country files; therefore it makes sense to select 'ir' for Iran, for Avestan.
You can file a feature request following the link
[https://bugs.freedesktop.org/enter_bug.cgi?product=xkeyboard-config](https://bugs.freedesktop.org/enter_bug.cgi?product=xkeyboard-config)
As an example, see
[https://bugs.freedesktop.org/show_bug.cgi?id=2693](https://bugs.freedesktop.org/show_bug.cgi?id=2693)

Hello Simosx (I'd like to address you by your real - I suppose Greek name - but I do not know it)
I think its you who is the creator of this Avestan keyboard layout and it is you who is allowed to claim this keyboard layout as your creation and you have earned the copyright to "get the layout added to the xkeyboard-config project so that newer Linux  distributions will have it in by default."
I only told you the layouts picture will say how it has to look like. 

I'll put my Avestan font on my new homepage and - if you agree - the method how you "simosx" (or your real Greek name, &#963;&#964;&#942;&#957; &#949;&#955;&#955;&#953;&#957;&#953;&#954;&#942; &#947;&#955;&#974;&#963;&#963;&#945;) got the Avestan keyboard to function in Ubuntu 10.04. 
&#935;&#945;&#953;&#961;&#949;&#964;&#943;&#963;&#956;&#945;&#964;&#945;
Ernst Tremel

---

### Post by simosx on 2010-06-12
I created a report on freedesktop.org,
[https://bugs.freedesktop.org/show_bug.cgi?id=28514](https://bugs.freedesktop.org/show_bug.cgi?id=28514)
for this layout. I hope the maintainer is happy to get the layout included so that in the next Linux distributions the layout will work by default.Thereis no policy yet for archaic layouts, but I hope that all will be fine.
The distribution license for the layout is the same as the X.Org license.

Regarding your Avestan font, you may consider licensing it with the Open Font License, [http://scripts.sil.org/OFL](http://scripts.sil.org/OFL) so that it is easy to add to the Universe repository. There is a process for this; the end result would be for users to install a 'ttf-avestan' package using the Ubuntu Software Centre instead of adding the font manually in their personal ~/.fonts/ The discussion for such font stuff takes place at [http://lists.freedesktop.org/mailman/listinfo/openfontlibrary](http://lists.freedesktop.org/mailman/listinfo/openfontlibrary)
You can introduce yourself in the list and announce your font.

You can quote me as '&#931;&#943;&#956;&#959;&#962; &#926;&#949;&#957;&#953;&#964;&#941;&#955;&#955;&#951;&#962;' :-). I am glad the XKB layout works well for you. Once you get your page online, I'll link from my blog.

---

### Post by simosx on 2010-06-17
The Avestan keyboard layout has been accepted by the X.Org project (package: xkeyboard-config). New distributions such as Ubuntu 10.10 will have the Avestan layout already available, and it would be a matter of simply going to 'System/Preferences/Keyboard/Layouts' and selecting the Avestan layout!

Here is the 'commit' in xkeyboard-config,
[http://cgit.freedesktop.org/xkeyboard-config/commit/?id=9f3dff863667bc8549fc4608069c143adc410e56](http://cgit.freedesktop.org/xkeyboard-config/commit/?id=9f3dff863667bc8549fc4608069c143adc410e56)

Here is the resolved bug report at FreeDesktop.Org,
[http://bugs.freedesktop.org/show_bug.cgi?id=28514](http://bugs.freedesktop.org/show_bug.cgi?id=28514)

The work we did for Avestan is the complete work required to have a new keyboard layout added to Linux.

---

### Post by Struwelpeter on 2010-07-04
Hi there,

The guide is really wonderful, thank you for it.

As I am new to Ubuntu, though, I have one question. How do I know which keyboard file corresponds to which keyboard layout? I mean, at the "Keyboard Preferences" screen, I have selected "United Kingdom International (with dead keys)", as that is my keyboard. How do I know which of the many files at the 

/usr/share/X11/xkb/symbols/

folder corresponds to "United Kingdom International (with dead keys)"?
Also, I was wondering if I could create an entirely new keyboard layout (starting from one of the previously existing files). If I did that, how would I be able to select it from the "Keyboard Preferences" screen? (Or perhaps there's somewhere else I can select it from?)

Thanks a lot,

S.p.

---

### Post by simosx on 2010-07-05
> **Struwelpeter said:**
> Hi there,

The guide is really wonderful, thank you for it.

As I am new to Ubuntu, though, I have one question. How do I know which keyboard file corresponds to which keyboard layout? I mean, at the "Keyboard Preferences" screen, I have selected "United Kingdom International (with dead keys)", as that is my keyboard. How do I know which of the many files at the 

/usr/share/X11/xkb/symbols/

folder corresponds to "United Kingdom International (with dead keys)"?
Also, I was wondering if I could create an entirely new keyboard layout (starting from one of the previously existing files). If I did that, how would I be able to select it from the "Keyboard Preferences" screen? (Or perhaps there's somewhere else I can select it from?)

The folder /usr/share/X11/xkb/symbols/ has many files, each of which is the named after country codes. For United Kingdom, the country code is 'gb' (Great Britain). The list of country codes can be found at 
[http://www.iso.org/iso/country_codes/iso_3166_code_lists/english_country_names_and_code_elements.htm](http://www.iso.org/iso/country_codes/iso_3166_code_lists/english_country_names_and_code_elements.htm)

('gb' is a special case when we are used to *.co.uk in domain names; 'uk' as country code is for the Ukraine).

Each of these files then are layout files. The first layout is the default layout and the rest are what we call 'variants'.

If you can master the command line, you can open a terminal window, type

cd /usr/share/X11/xkb/symbols/

and then 

grep "United Kingdom International" *

which will pinpoint the correct layout file.

---

### Post by Struwelpeter on 2010-07-05
Awesome. Thank you for the hint!

And I have another question, now. I'm reading the "Unreliable Guide to Xkb Configuration" by Doug Palmer. He appears to be working with a slightly different system than mine, and he refers to two files whose equivalent I cannot locate:

/usr/X11R6/include/X11/keysymdefh (the file that contains the symbol names used by the symbol maps to trace key codes to actual characters).

/etc/X11/XF86Config-4 (the Xkb configuration file[FONT=Verdana])

Any clues?

The only reason I'm trying to learn how to configure this is because I need to write Portuguese, German, French and Spanish with my UK keyboard, using proper dead keys for speed, and without getting things such as &#7743; and &#324; when I press '+m, which makes it harder for me to write in English (e.g. to say "I'm" I need to type I+'+[space]+m). So, if anybody knows a way to do that without having to remap the entire keyboard, I'm all ears!

EDIT: I just found the /usr/share/X11/locale/ directory. Inside it there are many directories relating to different character sets (I suppose?) such as "en_US.UTF-8", inside which there are "Compose" files containing tables such as this:

<dead_acute> <C>                     : "ç"   U0106 # LATIN CAPITAL LETTER C WITH ACUTE
<Multi_key> <acute> <C>              : "ç"   U0106 # LATIN CAPITAL LETTER C WITH ACUTE
<Multi_key> <apostrophe> <C>         : "ç"   U0106 # LATIN CAPITAL LETTER C WITH ACUTE
<dead_acute> <c>                     : "ç"   U0107 # LATIN SMALL LETTER C WITH ACUTE
<Multi_key> <acute> <c>              : "ç"   U0107 # LATIN SMALL LETTER C WITH ACUTE
<Multi_key> <apostrophe> <c>         : "ç"   U0107 # LATIN SMALL LETTER C WITH ACUTE
<dead_circumflex> <C>                : "&#264;"   U0108 # LATIN CAPITAL LETTER C WITH CIRCUMFLEX
<Multi_key> <asciicircum> <C>        : "&#264;"   U0108 # LATIN CAPITAL LETTER C WITH CIRCUMFLEX
<dead_circumflex> <c>                : "&#265;"   U0109 # LATIN SMALL LETTER C WITH CIRCUMFLEX
<dead_acute> <M>                     : "&#7742;"   U1E3E # LATIN CAPITAL LETTER M WITH ACUTE
<Multi_key> <acute> <M>              : "&#7742;"   U1E3E # LATIN CAPITAL LETTER M WITH ACUTE
<Multi_key> <apostrophe> <M>         : "&#7742;"   U1E3E # LATIN CAPITAL LETTER M WITH ACUTE
<dead_acute> <m>                     : "&#7743;"   U1E3F # LATIN SMALL LETTER M WITH ACUTE
<Multi_key> <acute> <m>              : "&#7743;"   U1E3F # LATIN SMALL LETTER M WITH ACUTE
<Multi_key> <apostrophe> <m>         : "&#7743;"   U1E3F # LATIN SMALL LETTER M WITH ACUTE

These are precisely some of the character combinations I want to get rid of. Can I just remove the lines containing the unwanted character combinations? If yes, the question remains of which folder should I tamper with (probably en_US.UTF-8, since my keyboard is an English keyboard?)

[/FONT]

---

### Post by simosx on 2010-07-05
> **Struwelpeter said:**
> Awesome. Thank you for the hint!

And I have another question, now. I'm reading the "Unreliable Guide to Xkb Configuration" by Doug Palmer. He appears to be working with a slightly different system than mine, and he refers to two files whose equivalent I cannot locate:

/usr/X11R6/include/X11/keysymdefh (the file that contains the symbol names used by the symbol maps to trace key codes to actual characters).

/etc/X11/XF86Config-4 (the Xkb configuration file[FONT=Verdana])

Any clues?

These instructions are from long long time ago. Nowdays, the X server is autoconfigured so you do not need an /etc/X11 configuration file. You may add one if you really need, but it's now called 'xorg.conf' (same format). Since then, XFree86 was renamed to XOrg.

The file keysymdef.h is a header file which lists all currently support keysyms. You cannot add stuff there and expect to work; you need to recompile the X server (Xorg) in order to enable them which is a tough task. To get this keysymdef.h file, you need to install one of the xorg development packages.
I would suggest to read instead [http://cgit.freedesktop.org/xorg/proto/x11proto/tree/keysymdef.h](http://cgit.freedesktop.org/xorg/proto/x11proto/tree/keysymdef.h) which is the link to the latest version of the file from the Xorg repository.

> **Struwelpeter said:**
> The only reason I'm trying to learn how to configure this is because I need to write Portuguese, German, French and Spanish with my UK keyboard, using proper dead keys for speed, and without getting things such as &#7743; and &#324; when I press '+m, which makes it harder for me to write in English (e.g. to say "I'm" I need to type I+'+[space]+m). So, if anybody knows a way to do that without having to remap the entire keyboard, I'm all ears!


I may miss something here; all the languages you mention have precomposed Unicode characters for the Latin block, which means that, counting the 10+ dead keys that are available from the GB keyboard layout, you can type all of them. All dead keys are accessible using AltGr, so there is little chance of hitting the wrong key.

Doing the ~/.XCompose trick, you can extend compose sequences to work characters such as t, k which do not have already a Unicode precompose character.

> **Struwelpeter said:**
> 
EDIT: I just found the /usr/share/X11/locale/ directory. Inside it there are many directories relating to different character sets (I suppose?) such as "en_US.UTF-8", inside which there are "Compose" files containing tables such as this:

<dead_acute> <C>                     : "ç"   U0106 # LATIN CAPITAL LETTER C WITH ACUTE
<Multi_key> <acute> <C>              : "ç"   U0106 # LATIN CAPITAL LETTER C WITH ACUTE
<Multi_key> <apostrophe> <C>         : "ç"   U0106 # LATIN CAPITAL LETTER C WITH ACUTE
<dead_acute> <c>                     : "ç"   U0107 # LATIN SMALL LETTER C WITH ACUTE
<Multi_key> <acute> <c>              : "ç"   U0107 # LATIN SMALL LETTER C WITH ACUTE
<Multi_key> <apostrophe> <c>         : "ç"   U0107 # LATIN SMALL LETTER C WITH ACUTE
<dead_circumflex> <C>                : "&#264;"   U0108 # LATIN CAPITAL LETTER C WITH CIRCUMFLEX
<Multi_key> <asciicircum> <C>        : "&#264;"   U0108 # LATIN CAPITAL LETTER C WITH CIRCUMFLEX
<dead_circumflex> <c>                : "&#265;"   U0109 # LATIN SMALL LETTER C WITH CIRCUMFLEX
<dead_acute> <M>                     : "&#7742;"   U1E3E # LATIN CAPITAL LETTER M WITH ACUTE
<Multi_key> <acute> <M>              : "&#7742;"   U1E3E # LATIN CAPITAL LETTER M WITH ACUTE
<Multi_key> <apostrophe> <M>         : "&#7742;"   U1E3E # LATIN CAPITAL LETTER M WITH ACUTE
<dead_acute> <m>                     : "&#7743;"   U1E3F # LATIN SMALL LETTER M WITH ACUTE
<Multi_key> <acute> <m>              : "&#7743;"   U1E3F # LATIN SMALL LETTER M WITH ACUTE
<Multi_key> <apostrophe> <m>         : "&#7743;"   U1E3F # LATIN SMALL LETTER M WITH ACUTE

These are precisely some of the character combinations I want to get rid of. Can I just remove the lines containing the unwanted character combinations? If yes, the question remains of which folder should I tamper with (probably en_US.UTF-8, since my keyboard is an English keyboard?)

[/FONT]

The /usr/share/X11/locale directory contains the compose sequences which involve dead keys (a + acute = á) or Compose key (Multi_key, you need to configure in Keyboard preferences) with mnemonics (Compose+c+0 = ©).
Which file is used? Depends on your locale setting (what you chose in Language support). See /usr/share/X11/locale/locale.dir to figure out which compose file is for your locale (en_GB, en_US use the en_US.UTF-8/ compose file).

---

### Post by Struwelpeter on 2010-07-07
> **simosx said:**
> 
The /usr/share/X11/locale directory contains the compose sequences which involve dead keys (a + acute = á) or Compose key (Multi_key, you need to configure in Keyboard preferences) with mnemonics (Compose+c+0 = ©).
Which file is used? Depends on your locale setting (what you chose in Language support). See /usr/share/X11/locale/locale.dir to figure out which compose file is for your locale (en_GB, en_US use the en_US.UTF-8/ compose file).

Thanks for the replies insofar, they've all be very useful. A doubt persists, however.

I've edited the /user/share/X11/locale/en_US.UTF-8/Compose file so as to eliminate all traces of '&#263;' and '&#262;'. I therefore have:

<dead_acute> <C>                     : "ç"   U0106 # LATIN CAPITAL LETTER C WITH ACUTE

and

<dead_acute> <c>                     : "ç"   U0107 # LATIN SMALL LETTER C WITH ACUTE

However, when I press dead acute (') + c what I get is &#263;.

I'm using UK keyboard and English (GB) as default language.

What did I miss?

---

### Post by simosx on 2010-07-07
> **Struwelpeter said:**
> Thanks for the replies insofar, they've all be very useful. A doubt persists, however.

I've edited the /user/share/X11/locale/en_US.UTF-8/Compose file so as to eliminate all traces of '&#263;' and '&#262;'. I therefore have:

<dead_acute> <C>                     : "ç"   U0106 # LATIN CAPITAL LETTER C WITH ACUTE

and

<dead_acute> <c>                     : "ç"   U0107 # LATIN SMALL LETTER C WITH ACUTE

However, when I press dead acute (') + c what I get is &#263;.

I'm using UK keyboard and English (GB) as default language.

What did I miss?

You need to verify that you are bypassing the input method that GTK+/GNOME provides to you, and that you are working directly with the X Input Method. You need to set the GTK_IM_MODULE variable to xim in /etc/environment and reboot.
To verify, open a terminal and verify the value of the above variable.

---

### Post by Struwelpeter on 2010-07-07
> **simosx said:**
> You need to verify that you are bypassing the input method that GTK+/GNOME provides to you, and that you are working directly with the X Input Method. You need to set the GTK_IM_MODULE variable to xim in /etc/environment and reboot.
To verify, open a terminal and verify the value of the above variable.

Ah, wonderful! Now it works!

I have two further questions, if you'll allow me...

First... I don't understand exactly what you mean when you say I'm bypassing the GTK+/GNOME method. What is the GTK+/GNOME method? The one involving the files in usr/share/X11/xkb ...?

Second... I noticed that when I am in "sudo" mode (for instance, when I am editing a file usigng "sudo gedit"), I still get '+c=&#263;, instead of '+c=ç, which I obtain elsewhere. Why is that?

You're a tremendous help. I appreciate it very much.

---

### Post by simosx on 2010-07-08
> **Struwelpeter said:**
> Ah, wonderful! Now it works!

I have two further questions, if you'll allow me...

First... I don't understand exactly what you mean when you say I'm bypassing the GTK+/GNOME method. What is the GTK+/GNOME method? The one involving the files in usr/share/X11/xkb ...?

'input method' is a way to type different characters. Many toolkits (libraries, such as gtk+) provide some rudimentary input methods. For programs that use the gtk+ library, they get a simple input method that provides the compose sequences (Compose + ( + 1 + 0 + ) = &#9321;), the dead keys sequences (dead acute + a = á) and the 'type any unicode character' - Ctrl+Shift+1234+space: &#4660;). In addition, gtk+ supplies about half a dozen other input methods such as the facility to type Ethiopic. You can find those if you open 'gedit', then right-click in the document and look into the Input Methods menu.

Before the gtk+ library, applications could use the X Input Method (XIM) that the X server provides. In your case, where you want to use custom compose sequences, you need (currently) to do it by getting access to XIM. gtk+ cannot do it currently. When you set 'GTK_IM_MODULE' to xim, you inform gtk+ that you want to bypass the gtk+ input method(s) and use XIM instead. XIM is the one that involves the file in /usr/share/X11/locale/*
Note that the files in /usr/share/X11/xkb/* are shared between the two input methods.

> **Struwelpeter said:**
> Second... I noticed that when I am in "sudo" mode (for instance, when I am editing a file usigng "sudo gedit"), I still get '+c=&#263;, instead of '+c=ç, which I obtain elsewhere. Why is that?

You're a tremendous help. I appreciate it very much.

When you type 'sudo gedit', you launch the gedit program using the 'root/superuser' credentials and 'environment' settings. In this elevated privilege more, the 'gedit' program does not receive the 'GTK_IM_MODULE' environment variable that you configured earlier.
If you want to force 'sudo' programs to use XIM, then you can write a script such as

[INDENT]#!/bin/sh
export GTK_IM_MODULE=xim
/usr/bin/gedit
[/INDENT]

save to a file such as 'root_gtk.sh' and then

[INDENT]chmod 755 root_gtk.sh
[/INDENT]

and finally 

[INDENT]gksudo ./root_gtk.sh
[/INDENT]

(sudo and gksudo are the same, gksudo asks your password with a new window).

---

### Post by Struwelpeter on 2010-07-09
It's all working now. Thanks a lot!

---

### Post by Struwelpeter on 2010-07-10
I have a new question. I don't know whether what I want to do is possible but...

I wanted to have the ' / @ key (AC11) work as a dead key that would deliver a ^ when in combination with the suitable vowels (so that shift+AC11+e=ê) *but* still worked as a @ when followed by a space (so that shift+AC11+space=@).

What I did was to go to /usr/share/X11/xkb/symbols/gb, look for the entry corresponding to my keyboard and alter

key <AC11>    { [apostrophe,         **at**, dead_circumflex, dead_caron]    };

to

key <AC11>    { [apostrophe,         **dead_at**, dead_circumflex, dead_caron]    };

Then I went to /usr/share/X11/locale/en_US.UTF-8/Compose and included entries like:

<dead_at> <space>            : "@"    at # COMMERCIAL AT
<dead_at> <a>                : "â"    acircumflex

Well, the result is that shift+AC11 is now working as a ". Apparently I need to define the new dead key "dead_at" somewhere, right? I have used Search to try to find in /usr/ a file containing the dead key parameters (I searched for "dead_acute"), but couldn't find one.

What should I do?

---

### Post by simosx on 2010-07-10
> **Struwelpeter said:**
> I have a new question. I don't know whether what I want to do is possible but...

I wanted to have the ' / @ key (AC11) work as a dead key that would deliver a ^ when in combination with the suitable vowels (so that shift+AC11+e=ê) *but* still worked as a @ when followed by a space (so that shift+AC11+space=@).

What I did was to go to /usr/share/X11/xkb/symbols/gb, look for the entry corresponding to my keyboard and alter

key <AC11>    { [apostrophe,         **at**, dead_circumflex, dead_caron]    };

to

key <AC11>    { [apostrophe,         **dead_at**, dead_circumflex, dead_caron]    };

Then I went to /usr/share/X11/locale/en_US.UTF-8/Compose and included entries like:

<dead_at> <space>            : "@"    at # COMMERCIAL AT
<dead_at> <a>                : "â"    acircumflex

Well, the result is that shift+AC11 is now working as a ". Apparently I need to define the new dead key "dead_at" somewhere, right? I have used Search to try to find in /usr/ a file containing the dead key parameters (I searched for "dead_acute"), but couldn't find one.

What should I do?

When you want to add a new keysym, you need to add it to keysymdef.h and recompile Xorg. It's a daunting task and the common workaround is to reuse existing keysyms in inventive ways.

However your case is quite simple.
The ^ is a circumflex and there is a dead_circumflex.
So, you need to modify the existing compose sequence for

<dead_circumflex> <space>     : "^" asciicircum

to 

<dead_circumflex> <space>     : "@" at

---

### Post by Struwelpeter on 2010-07-10
> **simosx said:**
> When you want to add a new keysym, you need to add it to keysymdef.h and recompile Xorg. It's a daunting task and the common workaround is to reuse existing keysyms in inventive ways.

However your case is quite simple.
The ^ is a circumflex and there is a dead_circumflex.
So, you need to modify the existing compose sequence for

<dead_circumflex> <space>     : "^" asciicircum

to 

<dead_circumflex> <space>     : "@" at

Thanks again for the reply!

But, well, if I did that I'd be just replacing ^ with @, and I'd no longer have a way to type in the ^ character, right? - Unless I changed its place, of course, which is something I did not want to do. Apparently, I need  either to recompile the famous Xorg, or to get used to the new ergonomics...

I wonder if there there's a beginner's guide to Xorg compilation somewhere out there...?

---

### Post by Struwelpeter on 2010-07-10
Ah, nevermind compilation, silly me! The best way is obviously to change /usr/share/X11/xkb/symbols/gb so that the appropriate entries will look like this:

key <AE06> { [6, asciicircum, NoSymbol, onesixth] }
key <AC11>    { [apostrophe, dead_circumflex, dead_circumflex,  dead_caron]    };

And /usr/share/X11/locale/en_US.UTF-8/Compose to look like you suggested:

<dead_circumflex> <space>     : "@" at

Thanks a lot!

(By the way, I just came across a graphical interface for keyboard editing. I don't know if it works right (after all, now I've learnt to do it manually...), but it's called **xkeycaps **and it can be downloaded from Universal, I think.)

---

### Post by rostfrei on 2010-08-11
I'm learning in modifying or adding new keyboard variant. I'm using Slovenian keyboard so I focused on that. Steps that I made

1.) Modifyed **/usr/share/X11/xkb/symbols/si** file by adding new 4th variant at the end.

```
// $XKeyboardConfig$
//

default partial alphanumeric_keys
xkb_symbols "basic" {

    name[Group1]="Slovenia";

    include "rs(latin)"

    key <TLDE> { type[Group1]="TWO_LEVEL", [ cedilla, diaeresis ] };
};

partial alphanumeric_keys 
xkb_symbols "us" {

    name[Group1]= "Slovenia - US keyboard with Slovenian letters";

    include "rs(latinyz)"

    key <TLDE> { type[Group1]="TWO_LEVEL", [ cedilla, diaeresis ] };
};


partial alphanumeric_keys 
xkb_symbols "alternatequotes" {

    name[Group1]= "Slovenia - Use guillemets for quotes";

    include "rs(latinalternatequotes)"

    key <TLDE> { type[Group1]="TWO_LEVEL", [ cedilla, diaeresis ] };
};

partial alphanumeric_keys
xkb_symbols "ru" {

    name[Group1]="Slovenia - Slovenian keyboard with phoneticaly placed Russian letters";

    include "rs(latin)"

    key <TLDE> { type[Group1]="TWO_LEVEL", [ cedilla, diaeresis ] };
};
```

As you can see I just copied first default entry and modified xkb_symbols name and Group1 name.


2.) Modified **/usr/share/X11/xkb/symbols.dir** and added **si(ru)** line
```

-dp----- a------- si(basic)
--p----- a------- si(us)
--p----- a------- si(alternatequotes)
--p----- a------- si(ru)
```


3.) Restarted xserver



Now I go to System->Preferences->Keyboard, Layouts tab and press Add button. Search for the Country:Slovenia and can see 3 variants that came by default, but there is no added variant in the list. I even changed the Group1 names of the existing ones just to see what will happen and nothing. These changes does not reflect at all. I restarted computer, no effect.

Is there some additional step an have to make in order to reflect changes?

Thank you!

---

### Post by simosx on 2010-08-11
@rostfei: You need to edit an .xml file as well. The GUI tool reads this XML file. See an example at [http://simos.info/blog/archives/1134](http://simos.info/blog/archives/1134)

---

### Post by rostfrei on 2010-08-11
Thank you! It works now. But I really don't understand why you have to make the same change in two files, base.xml and evdev.xml? Why same configuration on two different places?

---

### Post by simosx on 2010-08-12
> **rostfrei said:**
> Thank you! It works now. But I really don't understand why you have to make the same change in two files, base.xml and evdev.xml? Why same configuration on two different places?

evdev.xml is identical to base.xml. On my system they are different files with the same content. One should probably be a symbolic link to the other like 'xorg.xml' is a link to base.xml. I do not know the intricacies for this, so I advise to fix up both files and be done with it :-).

---

### Post by rostfrei on 2010-08-12
I managed to make additional variant of Russian phonetics on Slovenian keyboard. I'm havin problem with dead key on AE11 for Slovenian keyboard it is

key <AE11> {   [ any,any,     dead_diaeresis,      diaeresis 	 ]   };

and it actually works if I try it, but character code is not correct.

So AltGr+AE11 produces character 'ë' which have a unicode 'U+00EB'. This is not correct. In Russian variant it should produce '&#1105;' with unicode 'U+0451'. This may not seem as much of a problem, but if I leave it that way, no Russian spell checker will work correctly.

Where do I explicitly define which character will be generated if I press dead_diaeresis+<some character>?

---

### Post by simosx on 2010-08-12
> **rostfrei said:**
> I managed to make additional variant of Russian phonetics on Slovenian keyboard. I'm havin problem with dead key on AE11 for Slovenian keyboard it is

key <AE11> {   [ any,any,     dead_diaeresis,      diaeresis 	 ]   };

and it actually works if I try it, but character code is not correct.

So AltGr+AE11 produces character 'ë' which have a unicode 'U+00EB'. This is not correct. In Russian variant it should produce '&#1105;' with unicode 'U+0451'. This may not seem as much of a problem, but if I leave it that way, no Russian spell checker will work correctly.

Where do I explicitly define which character will be generated if I press dead_diaeresis+<some character>?

Which ë is ë? This is a common Unicode question for characters that are effectively equivalent. Unicode-compliant software should and is able to consider both of these ë as the same, and uses the simpler for of the latin ë. 

To verify whether the russian ë is indeed equivalent to the latin ë, you need to read at [http://www.unicode.org/charts/](http://www.unicode.org/charts/) and find any info on equivalence.

You can of course force the layout to use the russian ë; however, check for equivalence first.

---

### Post by rostfrei on 2010-08-12
I already read [http://www.unicode.org/charts/](http://www.unicode.org/charts/) Latin and Cyrillic code pages and their supplements. I'm fully aware of the equivalent symbols. I don't want equivalence. I want it to be exact. What if I want that "AltGr+dead_key some_key" produces any character for example "&#1070;"? It is really easy to do that on Win with "Keyboard Layout Creator". I'm toying with 

/usr/share/X11/locale/iso8859-2/Compose

and lines

<dead_diaeresis> <E>			: "\313"	Ediaeresis
<dead_diaeresis> <e>			: "\353"	ediaeresis

and

/usr/share/X11/locale/en_US.UTF-8/Compose

<dead_diaeresis> <E>             	: "Ë"   Ediaeresis # LATIN CAPITAL LETTER E WITH DIAERESIS
<Multi_key> <quotedbl> <E>       	: "Ë"   Ediaeresis # LATIN CAPITAL LETTER E WITH DIAERESIS

with no luck so far. Do you have any suggestions how can I map any dead key to the character of my choice?

---

### Post by simosx on 2010-08-12
> **rostfrei said:**
> Do you have any suggestions how can I map any dead key to the character of my choice?

Your default keyboard layout settings use the Unicode data when trying to figure out what you get when you type those sequences. So, if Unicode says “equivalence”, you get equivalence.

What you need to do is force Ubuntu to use raw X.Org for input methods. In doing this you will lose the Ctrl+Shift+u+HEX feature.

So, 
1. sudo gedit /etc/environment
Add in there "export GTK_IM_MODULE=xim", save and restart.
2. Now you can change stuff in /usr/share/X11/locale/* and it will work.
3. You can also put your changes in ~/.XCompose so that you keep your modification at your home directory.

---

### Post by rostfrei on 2010-08-12
To be hones I never knew about Ctrl+Shift+u+HEX feature :). So those unicode equivalence mappings are fixed in code of the GTK library? I will leave it as is. If the spell checker handles it corectly, everything is ok. I don't want to hasle with xorg.conf file. As a matter of fact there is none on the Ubuntu system so I guess it is automaticaly generated in memory. 

Thank you for all your help!

---

### Post by kallekn on 2010-09-25
Thanks, great help! I succeeded in making my own variant of the Swedish Russian phonetic keyboard in no time. Making Russian keyboards of different flavors seems to be the most frequent use for this instruction, and no wonder - there are many modifications around, and once you are used to typing on a special kind of Russian phonetic keyboard, you really don't want to change. Especially if you are still using the other variant on an other computer.

---

### Post by john1982 on 2010-11-03
Hi,

there seems to be a lot of expertise here in this thread about all things typing, so I hope I'm right in placing this question here.

I'm studying Arabistics. People who have Arabic as their mother tongue seem to be using "1, 2, 3", etc. for numbers, but in Modern High Arabic, which is what is of scholarly interest, the number symbols initially imported from Hindi are used: (&#1632;, &#1633;, &#1634;, &#1635;, &#1636;, &#1637;, &#1638;, &#1639;, &#1640;, &#1641; - that is 9, 8, 7, 6, 5, 4, 3, 2, 1, 0 if read left-to-right) - now, since these are *unlikely* to be of use to the average writer, the Arabic keyboard map creates the "normal" number symbols.

How, if at all possible, could I have the normal Arabic keyboard map, but with the above mentioned symbols on the number keys instead?

Thanks a lot!

- John

---

### Post by henriquemaia on 2010-11-04
> **john1982 said:**
> Hi,

there seems to be a lot of expertise here in this thread about all things typing, so I hope I'm right in placing this question here.

I'm studying Arabistics. People who have Arabic as their mother tongue seem to be using "1, 2, 3", etc. for numbers, but in Modern High Arabic, which is what is of scholarly interest, the number symbols initially imported from Hindi are used: (&#1632;, &#1633;, &#1634;, &#1635;, &#1636;, &#1637;, &#1638;, &#1639;, &#1640;, &#1641; - that is 9, 8, 7, 6, 5, 4, 3, 2, 1, 0 if read left-to-right) - now, since these are *unlikely* to be of use to the average writer, the Arabic keyboard map creates the "normal" number symbols.

How, if at all possible, could I have the normal Arabic keyboard map, but with the above mentioned symbols on the number keys instead?

Thanks a lot!

- John

I'm not sure If I can help, but you can use any of the methods described in the thread (editing the xkb keyboard map file, create a custom xmodmap, etc) and assign each of the number keys to the corresponding character you want to display. Note that the character won't function as a number and will be just a text character. In any case, since I haven't tried this, I'm not giving you precise information here, just guessing from my experience editing keyboard maps and messing with xmodmap.

---

### Post by simosx on 2010-11-05
> **john1982 said:**
> Hi,

there seems to be a lot of expertise here in this thread about all things typing, so I hope I'm right in placing this question here.

I'm studying Arabistics. People who have Arabic as their mother tongue seem to be using "1, 2, 3", etc. for numbers, but in Modern High Arabic, which is what is of scholarly interest, the number symbols initially imported from Hindi are used: (&#1632;, &#1633;, &#1634;, &#1635;, &#1636;, &#1637;, &#1638;, &#1639;, &#1640;, &#1641; - that is 9, 8, 7, 6, 5, 4, 3, 2, 1, 0 if read left-to-right) - now, since these are *unlikely* to be of use to the average writer, the Arabic keyboard map creates the "normal" number symbols.

How, if at all possible, could I have the normal Arabic keyboard map, but with the above mentioned symbols on the number keys instead?

The Arabic layout is at /usr/share/X11/xkb/symbols/ara

The first layout (at the start) has the text

[INDENT]    key <AE01> {  [               1,          exclam      ]     };
    key <AE02> {  [               2,              at      ]     };
    key <AE03> {  [               3,      numbersign      ]     };
    key <AE04> {  [               4,          dollar      ]     };
    key <AE05> {  [               5,         percent      ]     };
    key <AE06> {  [               6,     asciicircum      ]     };
    key <AE07> {  [               7,       ampersand      ]     };
    key <AE08> {  [               8,        asterisk      ]     };
    key <AE09> {  [               9,      parenright      ]     };
    key <AE10> {  [               0,       parenleft      ]     };
[/INDENT]

What you need to do is replace '1', '2'.. with the Arabic numbers. 

Open Character Map (in Accessories) and find the Arabic Unicode block. At the end you get the Arabic numbers, so &#1785; is U06F9, etc (see the properties of the character).

Therefore, open the file with
[INDENT]
[FONT="Courier New"]gksudo gucharmap /usr/share/X11/xkb/symbols/ara[/FONT][/INDENT]

and replace the numbers mentioned above with the correct corresponding Arabic-Indian characters. Here is the example for '9':

[FONT="Courier New"]    key <AE09> {  [               9,      parenright      ]     };
[/FONT]
becomes 

[FONT="Courier New"]    key <AE09> {  [           U06F9,      parenright      ]     };[/FONT]

Save, logout, login again and you are done :-).

It's possible to add both 012345.. and arabic-indian numbers. You can read other layouts for hints on how to do that.

---

### Post by roberto.tomas on 2010-11-07
> **simosx said:**
> Here is the example for '9':

[FONT=Courier New]    key <AE09> {  [               9,      parenright      ]     };
[/FONT]
becomes 

[FONT=Courier New]    key <AE09> {  [           U06F9,      parenright      ]     };[/FONT]

Unless the arabic system uses a completely different compat configuration, each key has 4 registers in the symbols file. If you just tack on the arabic in the third register you can then access it with AltGr + # .. like so:

[FONT=Courier New]key <AE09> {  [ 9,      parenright, [/FONT][FONT=Courier New]U06F9[/FONT][FONT=Courier New]      ]     };[/FONT]

keypress results should be:

[9] - 9
[shift 9] - )
[altgr 9] - &#1785;

altgr is the right alt key by default.

edit: of course, you probably want that to map to 1, not 9 :P

---

### Post by Ari_Lari on 2010-11-18
Forum Question

Hey guys, I'm a new Ubuntu (version 10.10) user from Albania. Switched from W7 and I'm loving it so far. I only had one problem: creating a custom keyboard map for the Albanian language as the ones that usually come with the OS I don't like (they contain useless characters and everything is misplaced).

Following advice from a previous forum  this is what I did:
  sudo gedit /usr/share/X11/xkb/symbols/al (this is the default albanian language)(I backed it up just in case)

the file looked like this: (sorry if it's long)

> // $XKeyboardConfig$

// based on
// albanian keyboard layout
// done by Pablo Saratxaga <pablo@mandrakesoft.com>
//
// $XFree86: xc/programs/xkbcomp/symbols/al,v 1.2 2002/11/22 04:03:28 dawes Exp $

partial default alphanumeric_keys
xkb_symbols "basic" {
    include "latin(type3)"
    name[Group1]="Albania";

    key <AE01>	{ [         1,     exclam,   asciitilde,   dead_tilde ]	};
    key <AE02>	{ [         2,   quotedbl,   dead_caron,    oneeighth ]	};
    key <AE03>	{ [         3, numbersign, dead_circumflex,  sterling ]	};
    key <AE04>	{ [         4,     dollar,   dead_breve,       dollar ]	};
    key <AE05>	{ [         5,    percent, dead_abovering, threeeighths] };
    key <AE06>	{ [         6, asciicircum,  dead_ogonek, fiveeighths ]	};
    key <AE07>	{ [         7,  ampersand,        grave,   dead_grave ]	};
    key <AE08>	{ [         8,   asterisk, dead_abovedot,   trademark ]	};
    key <AE09>	{ [         9,  parenleft,   dead_acute,    plusminus ]	};
    key <AE10>	{ [         0, parenright, dead_doubleacute,   degree ]	};
    key <AE11>	{ [     minus, underscore, dead_diaeresis, questiondown] };

    key <AD03>	{ [         e,          E,     EuroSign,     EuroSign ]	};
    key <AD11>	{ [  ccedilla,   Ccedilla,     division, dead_abovering ] };
    key <AD12>	{ [        at, apostrophe,     multiply,  dead_macron ]	};

    key <AC02>	{ [         s,          S,      dstroke,      section ]	};
    key <AC03>	{ [         d,          D,      Dstroke,          ETH ]	};
    key <AC10>	{ [ediaeresis, Ediaeresis,   dollar, dead_doubleacute ]	};
    key <AC11>	{ [bracketleft,  braceleft,      ssharp,   dead_caron ]	};
    key <TLDE>	{ [ backslash,        bar,      notsign,      notsign ]	};

    key <BKSL>	{ [bracketright, braceright,   currency,   dead_breve ]	};
    key <AB08>	{ [     comma,  semicolon,         less,     multiply ]	};
    key <AB09>	{ [    period,      colon,      greater,     division ]	};
    key <AB10>	{ [     slash,   question, dead_belowdot, dead_abovedot ] };

    include "level3(ralt_switch)"
};

So this was based on the latin(type 3) keyboard. I wanted to change it to use the USA layout so these are the changes I did and how the file looked afterwards:

> 
//Albanian Layout
//For Ubuntu
partial default alphanumeric_keys
xkb_symbols "basic" {

    include "USA"
    name[Group1]="Albania";
 
    key <AD11> {	[ ccedilla,      Ccedilla,     braceright	]	};
    key <AD12> {	[ bracketright,  bracketleft,  braceleft	]	};
    key <AB10> {	[ ediaeresis,	 question,     Ediaeresis	]	};
    key <BKSL> {	[ slash,         backslash,    bar	        ]	};
    include "level3(ralt_switch)"
};

To work it required a restart. upon restart the following error message came up:

Error activating XKB configuration.It can happen under various circumstances: • a bug in libxklavier library • a bug in X server (xkbcomp, xmodmap utilities) • X server with incompatible libxkbfile implementationX server version data:The X.Org Foundation10900000If you report this situation as a bug, please include: • The result of xprop -root | grep XKB • The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

I have tried reverting back to the original and it worked fine, but even with smaller changes to the file the error kept popping up. Please someone tell me what I am doing wrong?!?!

Thanks a lot for your help :)

---

### Post by simosx on 2010-11-18
> **Ari_Lari said:**
> 
...
I have tried reverting back to the original and it worked fine, but even with smaller changes to the file the error kept popping up. Please someone tell me what I am doing wrong?!?!

Thanks a lot for your help :)

The problem is what you put in 'include'. You wrote  include "USA" which is wrong.

The files that you find in the /usr/share/X11/xkb/symbols/ directory are layouts, and 'al' is an example of a layout file. If you look inside the 'al' file, you notice that there is a single *variant*, 'basic'. If I were to use the 'basic' variant from the Albanian layout in my own layout file, I would have written "al(basic)". The first variant of a layout file is the default variant, therefore it would also be OK to write "al" (it's the same with "al(basic)". 

Therefore, if you want to base the Albanian layout on the US layout, you write

[FONT="Courier New"]include "us"
[/FONT]

In addition, if you want to submit this layout so it becomes part of the Albanian layout file, you need to leave the "basic" layout as it is, and create a new one. Then, the Albanian layout file would have two variants and the users will be able to choose from the list. Finally, you submit the changes at the xkeyboard-config project, at [http://www.freedesktop.org/wiki/Software/XKeyboardConfig](http://www.freedesktop.org/wiki/Software/XKeyboardConfig)

---

### Post by ernsttremel on 2010-12-05
**Re: Creating a custom keyboard layout**             
                                                                In Microsoft's keyboard layout creator there one may 
create keystrokes like
[COLOR=Red]U+014b U+02b8[/COLOR], i.e. [SIZE=4][COLOR=Red]&#331;&#696;[/COLOR][/SIZE] one keystroke delivers a composed glyph. 

Is such a proceeding possible in Ubuntu, too?
for example
key <TILDE> { [ UE107,    [COLOR=Red]U014B U02B8[/COLOR] ] }; // &#57607; [SIZE=4][COLOR=Red]&#331;&#696;[/COLOR][/SIZE]

---

### Post by ernsttremel on 2010-12-07
Hello

I tried to make myself an "AvestanTranscription" keyboard layout.
cf. "avestantranscription.txt"

I proceded like this:
cf. "wie_AvestanTranscription_keyboard_machen.odt"

But after having added the new keyboard layout I got this error message
cf. "fehlerkeyboard.txt"

Maybe you can tell me what is wrong in my method to make this keyboard layout?

Regards,

Ernst Tremel

---

### Post by ernsttremel on 2010-12-07
Meanwhile I experienced that my keyboard layout file "avestantranscription"


partial default alphanumeric_keys
xkb_symbols "avestantranscription"
{
    name[Group1] = "Germany - AvestanTranscription";

    key <AB01> { [ U007A,         U017E ] }; // z ž
    key <AB02> { [ U0078,         UE205 ] }; // x ?
    key <AB03> { [ U0063,          U010D ] }; // c c
    key <AB04> { [ U0076,         UE206 ] }; // v ?  
    key <AB05> { [ U0062,         U0077 ] }; // b w
    key <AB06> { [ U006E,         U1E47 ] }; //  n ?
    key <AB07> { [ U006D,         UE20B ] }; //  m ?
    key <AB08> { [ U2025,         U3002 ] }; // ? ?
    key <AB09> { [ U22C5,         U2024 ] }; //  · · 
    key <AB10> { [ U2219,         U002E ] }; //  · .

    key <AC01> { [ U0061,         U0101 ] }; // a a
    key <AC02> { [ U0073,         U0161 ] }; // s š
    key <AC03> { [ U0064,         U03B4 ] }; // d d
    key <AC04> { [ U0066,         U03B3 ] }; // f ?
    key <AC05> { [ U0067,         U0121 ] }; // g g
    key <AC06> { [ U0068,          UE105 ] }; // h ?
    key <AC07> { [ U006A,         UE209 ] }; // j ?
    key <AC08> { [ U006B,          U0135 ] }; // k j
    key <AC09> { [ U006C,          UE221 ] }; // l ?
    key <AC10> { [ U003B,         U003A ] }; // ; :
    key <AC11> { [ UE207,          U1E6F ] }; // ? ?

    key <AD01> { [ U014B,         UE208 ] }; // ? ?
    key <AD02> { [ UE20D,         UE20C ] }; // ? ?
    key <AD03> { [ U0065,         U0113 ] }; // e e
    key <AD04> { [ U0072,         UE20A ] }; // r ? 
    key <AD05> { [ U0074,         U03B8 ] }; // t ? 
    key <AD06> { [ U0079,         U1E8F ] }; // y ?
    key <AD07> { [ U0075,         U016B ] }; // u u
    key <AD08> { [ U0069,         U012B ] }; // i i
    key <AD09> { [ U006F,         U014D ] }; // o o
    key <AD10> { [ U0070,         U01DD ] }; // p ?
    key <AD11> { [ U0259,         UE204 ] }; // ? ?
    key <AD12> { [ U00E5,         UE20E ] }; //  å ?

    key <TILDE> { [ UE107,    UE225 ] }; // ? ??
    key <AE01> { [ U0031,     U015B ] }; // 1 s
    key <AE02> { [ U0032,     U1E63  ] }; //  2 ?
    key <AE03> { [ U0033,     UE108  ] }; // 3 ?
    key <AE04> { [ U0034,     U03D1 ] }; // 4 ?
    key <AE05> { [ UE104,     UE222 ] }; // ? ?
    key <AE06> { [ UE220,     UE223 ] }; // ? ?
    key <AE07> { [ U03B2,     UE224 ] }; // ß ?
    key <AE08> { [ UE109,     U00E3 ] }; // ? ã
    key <AE09> { [ UE10A,    UE10C ] }; // ? ?
    key <AE10> { [ U0030,      UE106 ] }; // 0 ?
    key <AE11> { [ U03C5,      UE10E ] }; // ? ?
    key <AE12> { [ UE10B,      UE10D ] }; // ? ?

    key <BKSL> { [ U0105,         UE203 ] }; // a ?
    key <LSGT> { [ U0105,         UE203 ] }; // a ?
};

caused this error message 

Fehler beim Aktivieren der XKB-Konfiguration.
Dies kann unter folgenden Umständen passieren:
 • ein Fehler in der Bibliothek libxklavier
 • ein Fehler im X-Server (xkbcomp, xmodmap-Werkzeuge)
 • X-Server mit inkompatibler Implementation von libxkbfile

Versionsdaten des X-Servers:
The X.Org Foundation
10900000

Falls Sie dies als Fehler melden, fügen Sie hinzu:
 • das Ergebnis von xprop -root | grep XKB
 • das Ergebnis von gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

The intented keyboard layout should look like:
cf. AvestTranscr-normal
and
AvestTranscr-shift

What has to be corrected in my keyboard layout file "avestantranscription" to avoid this error?

---

### Post by ernsttremel on 2010-12-25
Finally I achieved to make a Keyboard Layout functioning in Ubuntu, too.

This was possible because of Simos Xenitellis keyboardlayouteditior

[http://simos.info/blog/archives/747](http://simos.info/blog/archives/747)

[https://github.com/simos/keyboardlayouteditor](https://github.com/simos/keyboardlayouteditor)

This is quite a great ans very useful tool.
Thanks, Simos

---

### Post by _BPS_ on 2011-07-10
Hi

i want to make my own keyboard layout, and have problem with that :(

1. I'm creating file /usr/share/X11/symbols/ti
```

// $XKeyboardConfig$
partial default alphanumeric_keys
xkb_symbols "basic" {
    name[Group1] = "My Language name";
    key <AE01> {[a, 1]};
};

```2. Im editing file /usr/share/X11/rules/xorg.lst and in section ! layout im adding line:
```

ti        MyLanguageName

```3. Im editing file /usr/share/X11/rules/xorg.xml and adding:
```

<layout>
  <configItem>
    <name>ti</name>
    <shortDescription>MyLanguageName</shortDescription>
    <description>MuLanguageName</description>
  </configItem>
</layout>

```4. Im restarting my computer

And now... why i cant select or see my new keyboard layout in GNOME (System -> Preferences -> Keyboard -> Layouts). My layout is not in list of available layouts?

How can i change keyboard layouts in terminal?

:confused:

---

### Post by inashdeen on 2012-06-22
Hi I need to create an arabic based keyboard layout for my jawi writing (Traditional Malay-ms). It is similar to arabic but with extra characters and slightly different orientation. how do i actually add these character to usr/share/xkb/ara gedit since i can't seem to see any arabic character inside it.thanks in advance

---

### Post by henriquemaia on 2012-07-08
I have created a new keyboard layout (my flavour, full of useful unicode symbols I need) based on the symbols/pt file using simosx's Keyboard Layout Editor. I'm very pleased with the result. 

The program interface is a bit awkward, but it gets the job done. I still had to edit the file by hand to add the ```
include "level3(ralt_switch)"
``` line.

I saved my new layout as **pt-henrique** (any name will do) and saved it on ```
/usr/share/X11/xkb/symbols/
```. 

I then had to edit /etc/default/keyboard and change the 

```
XKBMODEL="pc105" 
XKBLAYOUT="pt" 
XKBVARIANT="" 
XKBOPTIONS=""
```

to

```
XKBMODEL="pc105" 
**XKBLAYOUT="pt-henrique"** 
XKBVARIANT="" 
XKBOPTIONS=""
```

After rebooting I had my new [artistic] layout running. 

note: **Thanks simosx**

---

### Post by henriquemaia on 2012-07-08
> **inashdeen said:**
> Hi I need to create an arabic based keyboard layout for my jawi writing (Traditional Malay-ms). It is similar to arabic but with extra characters and slightly different orientation. how do i actually add these character to usr/share/xkb/ara gedit since i can't seem to see any arabic character inside it.thanks in advance

You have to check the characters codes for the characters you want in some kind of source. I suggest checking the here:

[http://www.fileformat.info/info/unicode/char/search.htm](http://www.fileformat.info/info/unicode/char/search.htm)

Then you have to add the codes to the file you're editing. Something akin to 

```
key <AC05> { [ g, G, **U2196**, **U2660** ] };
key <AC06> { [ h, H, **U2197**, heart ] };
key <AC07> { [ j, J, **U2199**, **U2660** ] };
```.

The Uxxxx entries are the correspondent unicode codes for the characters you want.

Good luck in creating your layout.

---

### Post by v6rg on 2012-08-13
> **henriquemaia said:**
> [SIZE=3]
**5.** **Reverting to the Original Layout**[/SIZE]


I did not get anyresult from this steps and nowI loose all of my languages in ubuntu and just have English. 
:(
How I cab recovery my languages and layouts settings?

---

### Post by henriquemaia on 2012-08-13
> **v6rg said:**
> I did not get anyresult from this steps and nowI loose all of my languages in ubuntu and just have English. 
:(
How I cab recovery my languages and layouts settings?

Can you explain in detail all the steps you took?
 
Tell us what files you edited, how you edited them, what changes you did; basically, all the information you think that might help us in undoing the changes you did.

---

### Post by v6rg on 2012-08-13
> **henriquemaia said:**
> Can you explain in detail all the steps you took?
 
Tell us what files you edited, how you edited them, what changes you did; basically, all the information you think that might help us in undoing the changes you did.

I have two languages in my ubuntu: En & Fa (Persian)
And I want to make a third keyboard layout for my nation language (Gilaki) in ubuntu. 
Based on your HowTo article, I opened Pt file and edit all of its rows and made my advanced file and saved it in GLK name. 

Then, I created a archive folder on my /home on the location:

/home/archive/keyboard/layout

  but I could not put there my layout file (glk). It would not be copy!

Then I did like this:

     Code:
     sudo ln -sf /home/archive/keyboard/layout/glk /usr/share/X11/xkb/symbols/glk 
And then...   :(
I loose both of my PT and GLK files (with all of my changes that take 6 houres of my time) and have this erroe in begining of ubuntu:

```
 
Error activating XKB configuration. 
There can be various reasons for that. 
 
If you report this situation as a bug, include the results of 
 • xprop -root | grep XKB 
 • gsettings get org.gnome.libgnomekbd.keyboard model 
 • gsettings get org.gnome.libgnomekbd.keyboard layouts 
 • gsettings get org.gnome.libgnomekbd.keyboard options
```

---

### Post by henriquemaia on 2012-08-13
I won't be home till a little later so I can't look at this properly right now. But I'll try to find a solution for you. Sorry for that.

---

### Post by v6rg on 2012-08-13
> **henriquemaia said:**
> I won't be home till a little later so I can't look at this properly right now. But I'll try to find a solution for you. Sorry for that.

Not problem. I wait.  :)
And I wish you explain your HowTo for me that how I can have my new layout?

---

### Post by henriquemaia on 2012-08-13
> **v6rg said:**
> Not problem. I wait.  :)
And I wish you explain your HowTo for me that how I can have my new layout?

I recently redid my layout in order to acommodate my new needs for symbols. While I did that, I noticed that some things had changed in the process.

I send you here my new **pt** file as reference. You have to change its name to whatever you want. Like **pt-v6rg** (don't use extension) or whatever language you want to use. The name is irrelevant, it's just a mnemonic so you know what language it refers to and the aftername to know that you edited it.


What do you do with it, then?
Edit it at will. Be wise and try to follow the pattern of the file.

After that, you will copy it (not move, but copy it) to its right place. Where is that place? Here:

```
/usr/share/X11/xkb/symbols
```

How?

like this:

```
sudo cp /path/for/your_keyboard_file /usr/share/X11/xkb/symbols
```


Then you have to edit this file:

```
/etc/default/keyboard
```

How?

Like this:

```
sudo gedit /etc/default/keyboard
```


When the file is open, 

```
XKBMODEL="pc105" 
**XKBLAYOUT="pt-henrique"**
XKBVARIANT="" 
XKBOPTIONS=""
```

change the line in bold to match the name of your keyboard file.

example:

```
XKBMODEL="pc105" 
**XKBLAYOUT="pt-v6rg"**
XKBVARIANT="" 
XKBOPTIONS=""
```
Save the file. Now reboot.

You're done.
(so I hope)

---

### Post by greywalk on 2012-08-26
could you please summarize all the steps that are required to add a new keyboard layout?

from what I could understand so far the steps seem to be the following:
1) one has to create a layout file, give it a name
2) add the file with the new layout to /usr/share/X11/xkb/symbols
3) then modify the following files:
- /usr/share/X11/xkb/rules/evdev.lst
- /usr/share/X11/xkb/rules/base.lst
- /usr/share/X11/xkb/rules/evdev.xml
- /usr/share/X11/xkb/rules/base.xml
4) anything else?

Can the 3-letter language code be looked up here? [http://www.sil.org/iso639-3/codes.asp?order=639_3&letter=g](http://www.sil.org/iso639-3/codes.asp?order=639_3&letter=g)

----
I am trying to create a Gagauz layout. I have the layout file, but I fail to add it as a separate layout into the system :( The steps above result in the failure of some module that's responsible for layout switching and configuration. I use Kubuntu 12.04

---

### Post by henriquemaia on 2012-08-26
> **greywalk said:**
> could you please summarize all the steps that are required to add a new keyboard layout?

from what I could understand so far the steps seem to be the following:
1) one has to create a layout file, give it a name
2) add the file with the new layout to /usr/share/X11/xkb/symbols
3) then modify the following files:
- /usr/share/X11/xkb/rules/evdev.lst
- /usr/share/X11/xkb/rules/base.lst
- /usr/share/X11/xkb/rules/evdev.xml
- /usr/share/X11/xkb/rules/base.xml
4) anything else?

Can the 3-letter language code be looked up here? [http://www.sil.org/iso639-3/codes.asp?order=639_3&letter=g](http://www.sil.org/iso639-3/codes.asp?order=639_3&letter=g)

----
I am trying to create a Gagauz layout. I have the layout file, but I fail to add it as a separate layout into the system :( The steps above result in the failure of some module that's responsible for layout switching and configuration. I use Kubuntu 12.04

Step 1 and 2 are correct, but 3 is not.

3) Edit the file
/etc/default/keyboard

XKBMODEL="pc105" 
XKBLAYOUT="your_keyboard_file_as_it_appears_on_the_symbols_directory"
XKBVARIANT="" 
XKBOPTIONS=""

Save the file. Reboot. If the file follow the standard of a symbols files, it will work at startup. No more fuss.

Note: look até my updated howto on the post above yours.
[http://ubuntuforums.org/showpost.php?p=12170500&postcount=86](http://ubuntuforums.org/showpost.php?p=12170500&postcount=86)

---

### Post by greywalk on 2012-08-26
I do as it's said in step 3, that is edited the /etc/default/keyboard, but nothing happens. The added layout doesn't appear in the layouts list.

I believe I may have made a mistake in the layout file itself. Could someone please look into the file? I attached all the files I used to create the layout.

---

### Post by henriquemaia on 2012-08-26
> **greywalk said:**
> I do as it's said in step 3, that is edited the /etc/default/keyboard, but nothing happens. The added layout doesn't appear in the layouts list.

I believe I may have made a mistake in the layout file itself. Could someone please look into the file? I attached all the files I used to create the layout.

Ah, I see you are trying to make the file to show on the GUI keyboard selection tool. My howto is to define the keymap directly, with no other selection. I know very little about the steps to take in order to make you keymap visible on the selection tool.

---

### Post by MountainLion37 on 2012-12-22
I can't get deadacute-c to become &#263;. The file /usr/share/X11/locale/en_US.UTF-8/Compose says that it should be, but I'm always getting ç out of the key combination, and it's really annoying to type CtrlShift-u107 every time I need that character. Is there something wrong with the UK-international keyboard, or is it a feature (it's not a bug, I've checked) of the default IME?

---

### Post by roberto.tomas on 2012-12-22
> **MountainLion37 said:**
> I can't get deadacute-c to become &#263;. The file /usr/share/X11/locale/en_US.UTF-8/Compose says that it should be, but I'm always getting ç out of the key combination, and it's really annoying to type CtrlShift-u107 every time I need that character. Is there something wrong with the UK-international keyboard, or is it a feature (it's not a bug, I've checked) of the default IME?
 
Compose is a different feature than keyboard locale, and many of the settings for regular deadkeys, etc, won't work as it says in that file. You have to see the latin-4 settings (I think) .. it should be [alt-GR]+['] [c] to get the character you want.

---

### Post by MountainLion37 on 2012-12-22
> **roberto.tomas said:**
> Compose is a different feature than keyboard locale, and many of the settings for regular deadkeys, etc, won't work as it says in that file. You have to see the latin-4 settings (I think) .. it should be [alt-GR]+['] [c] to get the character you want.
I do that and get &#265;. AltGr-; gives me the dead acute, but on c it gives me a cedilla.
áçé&#501;í&#7729;&#314;&#7743;&#324;ó&#7765;&#341;&#347;úý&#378;&#509;&#511;

---

### Post by abefroman99 on 2013-01-09
How can I add quick Spanish characters to my keyboard layout, without changing the whole map?

For instance if I want
right alt+e to be e with an accent
or
right alt+shift+e to be e with an accent

and
alt+n to be the n with the ~

How can I do that?

Thanks!

---

### Post by henriquemaia on 2013-01-09
> **abefroman99 said:**
> How can I add quick Spanish characters to my keyboard layout, without changing the whole map?

For instance if I want
right alt+e to be e with an accent
or
right alt+shift+e to be e with an accent

and
alt+n to be the n with the ~

How can I do that?

Thanks!


You can achieve this by two different methods. They're simpler than creating your own layout, but they also come with their troubles. Don't be discouraged by this, try and experience for yourself, see what suits you best.

1. [Compose Key method]("https://help.ubuntu.com/community/ComposeKey").

2. [xmodmap method]("http://askubuntu.com/a/24930/65031").

Good luck.

---

### Post by abefroman99 on 2013-01-09
Thanks henriquemaia!

But I'm not having much luck with either.

I think part of the problem is my keyboard doesnt have an Alt-GR button, and also I can't seem to get the Spanish chacters to display even if is do something like Alt+164 for the (n~).

Any ideas?

When I tried the xev one, I held down alt and then pressed n and this came up:
```
KeyPress event, serial 33, synthetic NO, window 0x9a00001,
    root 0x131, subw 0x0, time 817838225, (173,373), root:(178,537),
    state 0x10, keycode 108 (keysym 0xffea, Alt_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x9a00001,
    root 0x131, subw 0x0, time 817840481, (173,373), root:(178,537),
    state 0x18, keycode 57 (keysym 0x6e, n), same_screen YES,
    XLookupString gives 1 bytes: (6e) "n"
    XmbLookupString gives 1 bytes: (6e) "n"
    XFilterEvent returns: False

```

So I would need to remap that to display n~ with the ~ over the n.

---

### Post by henriquemaia on 2013-01-10
> **abefroman99 said:**
> Thanks henriquemaia!

But I'm not having much luck with either.

I think part of the problem is my keyboard doesnt have an Alt-GR button, and also I can't seem to get the Spanish chacters to display even if is do something like Alt+164 for the (n~).

Any ideas?

When I tried the xev one, I held down alt and then pressed n and this came up:
```
KeyPress event, serial 33, synthetic NO, window 0x9a00001,
    root 0x131, subw 0x0, time 817838225, (173,373), root:(178,537),
    state 0x10, keycode 108 (keysym 0xffea, Alt_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x9a00001,
    root 0x131, subw 0x0, time 817840481, (173,373), root:(178,537),
    state 0x18, keycode 57 (keysym 0x6e, n), same_screen YES,
    XLookupString gives 1 bytes: (6e) "n"
    XmbLookupString gives 1 bytes: (6e) "n"
    XFilterEvent returns: False

```

So I would need to remap that to display n~ with the ~ over the n.


Well, the way I see it, it's better if you try the compose key method. It's pretty straightforward to configure, and a lot of fun to use. Really. It's not just about having ~ + n =ñ, but having fractions, crazy drawings, even whole sentences with simple combinations of keys. 

The principle behind it is:
Once you press the compose key, the ones you press afterwards make the combination that produce the result you want. 

You can check an example here:
[http://userbase.kde.org/Tutorials/ComposeKey#Optional_Tweaking_of_XCompose_Map](http://userbase.kde.org/Tutorials/ComposeKey#Optional_Tweaking_of_XCompose_Map)

Good luck with your combinations. I find it really fun to play with.

---

### Post by jako2 on 2013-09-23
Hi there, first of all thanks a lot for all your time guys, this only shows how cool the linux community is.
I'm in need of a bit of help if you don't mind xD

**TL;DR** I have an Issue, **xCompose** *isn't working everywhere* (like the searchbox in buntu or Steam for linux) it does work so far everywhere else, like Google Chrome, libreoffice or gedit.

Long story short I have been a Windows user for way too many years now, I want to switch to linux because I've heard is awesome at managing computing power (like for computational modelling and such), so I want to learn to use it. But when I wanted to do the complete transition I can't find the **"us-international"** keyboard I am so used in Windows, I find some close approaches but nothing exactly like it. I proceed to research and I found this guy [http://tamh.info/en/win-us-intl-4-linux/](http://tamh.info/en/win-us-intl-4-linux/) made an awesome custom .xCompose file which sort of emulates most if not all the behaviour of the **us international** Windows keyboard.

Thanks to your awesome guide and help to other users I finally managed to get said .xCompose file to work, nevertheless it doesn't work everywhere, It works in things like terminal, libre office, Google Chrome and Firefox, but it doesn't work in Steam or the main Ubuntu menu bar ([http://cdn.howtogeek.com/wp-content/uploads/2012/04/imag e403.png]("http://cdn.howtogeek.com/wp-content/uploads/2012/04/image403.png") how to geek pic in case I'm using the wrong name for this part of the GUI). 

I could get it to work in the main Ubuntu menu bar twice for a few key strokes, but after that it goes back to normal (working almost everywhere but not in steam or the main ubuntu menu bar)

My current keyboard layout is **English (US, international with dead keys)**

**Here's it is _what I have_ done so far:**
[LIST]
[*]*Extract* the **.xCompose** file I mentioned before in my [B]Home Folder
[/B]
[*]Added Ubuntu: I added the following line ```
export GTK_IM_MODULE=xim
``` at the end of the
[LIST]
[*]**/etc/environment **file in Ubuntu
[*]**/etc/bashrc **file in Scientific Linux
[/LIST]
[/LIST]
After this the keyboard works *just like the us international one in windows **almost everywhere*** 
But when I tried to use **S****team **or the **M****ain Ubuntu menu bar** it wouldn't work, just like if both apps would *ignore* the **.xCompose** file
In *Scientific Linux* when I try to use a *sudo* app like *gedit*, It ignores the .xCompose file as well (I don't have this issue in Ubuntu, in Ubuntu using sudo apps is just fine, it won't skip the .xCompose files)

Then after more research I found this page: [https://wiki.edubuntu.org/ComposeKey#Configuration_for_Gtk_Applications_.28Gnome.2C_FireFox.2C_etc..29](https://wiki.edubuntu.org/ComposeKey#Configuration_for_Gtk_Applications_.28Gnome.2C_FireFox.2C_etc..29)
And I tried to follow the instructions for a "Persistent Configuration"

When I tried to do this ```
sudo cp /etc/X11/xinit/xinput.d/default /etc/X11/xinit/xinput.d/xim
``` I realized I don't have such a file the **default **file doesn't exist in my system, because of this, out of my reasoning here's what I did:
[LIST]
[*]Create an copy of the **i****bus **file, rename it to **xim**
[*]Deleted everything inside the **xim **file and write the following 2 lines
[/LIST]
```
GTK_IM_MODULE=xim
QT_IM_MODULE=xim
```


[LIST]
[*]Create a link for the locale all_ALL (or the desired locale only):
[/LIST]
```
sudo ln -sf /etc/X11/xinit/xinput.d/xim /etc/X11/xinit/xinput.d/all_ALL


```

I **restarted** my system and it worked in the **M****ain Ubuntu menu bar **(it would recognize the *.xCompose *file) but after a few keystrokes it would go back to ignore the *.xCompose* file again.
I managed to make it work twice, (by deleting the files created in the second part of the process, restarting and doing this second part again), but when I wanted to do it a third time, it wouldn't work anymore (I haven't tried this in Scientific Linux tbh)

Any help will be highly appreciated!!! :) and thanks a lot for your support so far

*P.S.* I know it's not Scientific Linux forums but in case somebody knows how to work this issue out in said distro as well this info would be very welcome.

[B]System Details
Ubuntu *13.04*[/B] / **Scientific Linux *6.4***
[B]OS type [I]64-bit

[/I]Edit 1: 
[/B]If I access to the *Main Ubuntu menu bar* using the keyboard *"Windows key"* and type something, it ignores the .xCompose file, and the input I get is as if I were using the vanilla *English (US, international with dead keys) *layout.
If I access to the *Main Ubuntu menu bar *by clicking the button on top left of the launcher and then type something, it acknowledges the .xCompose file, and everything works just fine
No luck getting **Steam **to work; Quite puzzled with this behaviour of the main ubuntu menu bar

---

