---
title: "Duplicating AutoHotKey Functionality"
date: 2010-04-17
forum: The Cafe
---

### Post by DJ Barney on 2010-04-17
Hello,

Some users coming from Windows who have been used to using utilities like [AutoHotKey]("http://autohotkey.com") may be unaware of the way the CLI can be made to interact with the GUI to make life easier. So I decided to publicise some simple scripts.

[COLOR=#000000]There are  many ways to write functions that take highlighted text and make it  into an HTML link, or IMG HTML so it can be pasted back into a X.  Shortcut Keys can fill the paste buffer with often used text like email  addresses and links and can move windows around and resize them by the pixel or  to predetermined sizes (for The Gimp for example). This is achieved  using a mixture of Tcl, Tk, Zenity and Bash scripting along with various  X utilities.[/COLOR]

[COLOR=#000000]I use  this script to quickly make links in Drupal for content that allows HTML  formatting, of course you could us it for any repetitive task.

[IMG]http://djbarney.files.wordpress.com/2010/04/make-url.gif[/IMG]

[/COLOR]```
#!/bin/bash
# Make URL - Barney Holmes, 2010, http://djbarney.wordpress.com/2010/04/17/autohotkey-for-linux/
# Usage:
# * Highlight the text using the middle mouse button.
# * Activate the script on the command line or link it to a keyboard shortcut. See System -> Preferences -> Keyboard Shortcuts -> Custom Shortcuts (Lucid).
# * Enter the URL link into the script GUI.
# * The paste buffer is now full with an HTML formatted link.
# * Paste with the middle mouse button.
link=
buffer=`xsel -o`
url=`zenity --title "Make HTML URL" --entry --text "Highlighted text = \"$buffer\" \nLink will be placed in paste buffer. Use middle mouse button click. What is the URL ( http:// ) link ?"`
rc=$?
if [ "${rc}" == "1" ]; then
 echo User cancelled operation.
 exit 1
fi
echo -n "<a href=\"$url\">$buffer</a>" | xsel -i
```[COLOR=#000000]I have this script connected to a WinKey & L key press.[/COLOR] Lucid can allow the user to define custom shortcut keys. For other releases [see this guide]("https://help.ubuntu.com/community/KeyboardShortcuts#Text%20Entry%20Shortcuts").
[SIZE=4]
[/SIZE][SIZE=4]Make Image link into HTML.[/SIZE]

```
#!/bin/bash
# Make image HTML - Barney Holmes, 2010, http://djbarney.wordpress.com/2010/04/17/autohotkey-for-linux/
# Usage:
# * Highlight the text using the middle mouse button.
# * Activate the script on the command line or link it to a keyboard shortcut. See System -> Preferences -> Keyboard Shortcuts -> Custom Shortcuts (Lucid).
# * The paste buffer is now full with an image HTML.
# * Paste with the middle mouse button.
buffer=`xsel -o`
echo -n "<img src=\"$buffer\"></img>" | xsel -i
```[COLOR=#000000]

This one uses a WinKey & I key press on my system.[/COLOR] Other functions could capitalise words, or add forum BBCode.

[SIZE=4]Paste Often Used Text Snippets[/SIZE]

```
#!/bin/bash
# Make URL - Barney Holmes, 2010, [http://djbarney.wordpress.com/2010/04/17/autohotkey-for-linux/](http://djbarney.wordpress.com/2010/04/17/autohotkey-for-linux/)
# Usage:
# * Activate the script on the command line or link it to a keyboard shortcut. See System -> Preferences -> Keyboard Shortcuts -> Custom Shortcuts (Lucid).
# * Paste with the middle mouse button.
echo -n "contact@server.co.uk" | xsel -i
```[COLOR=#000000]

[/COLOR][COLOR=#000000]Just replace the text with your own and duplicate the script as necessary. I have my snippets linked to WinKey & 1,2,3 ... number keys.[/COLOR]

[SIZE=4]What about custom GUI's ?[/SIZE] 

This can be achieved using Tcl and Tk. Here is an interface that provides a menu for me to use MPlayer for watching my DVB-T digital TV.

[IMG]http://djbarney.files.wordpress.com/2010/04/interface.gif[/IMG]

Here is the code.

```
#!/usr/bin/wish
# DVB-T GUI Barney Holmes, 2010, http://djbarney.wordpress.com/2010/04/09/digital-tv-gui-linux-vs-autohotkey/

# Tk is the GUI language. Tcl is the programming language.
# See http://www.tkdocs.com/tutorial/intro.html

package require Tk

wm title . "MPlayer DVB Channels"
frame .clipaste_frame -relief raised -bd 1
label .1 -text "Digital TV"
button .2 -text "301\(BBC\)" -command { exec xterm -e mplayer dvb://301\(BBC\) & }
button .3 -text "4Music" -command { exec xterm -e mplayer dvb://4Music & }
button .4 -text "Absolute\ Radio\(Absolute\ Radio\)" -command { exec xterm -e mplayer dvb://Absolute\ Radio\(Absolute\ Radio\) & }
button .5 -text "BBC\ 1Xtra\(BBC\)" -command { exec xterm -e mplayer dvb://BBC\ 1Xtra\(BBC\) & }
button .6 -text "BBC\ 6\ Music\(BBC\)" -command { exec xterm -e mplayer dvb://BBC\ 6\ Music\(BBC\) & }
button .7 -text "BBC\ Asian\ Net.\(BBC\)" -command { exec xterm -e mplayer dvb://BBC\ Asian\ Net.\(BBC\) & }
button .8 -text "BBC\ FOUR\(BBC\)" -command { exec xterm -e mplayer dvb://BBC\ FOUR\(BBC\) & }
button .9 -text "BBC\ NEWS\(BBC\)" -command { exec xterm -e mplayer dvb://BBC\ NEWS\(BBC\) & }
button .10 -text "BBC\ ONE\(BBC\)" -command { exec xterm -e mplayer dvb://BBC\ ONE\(BBC\) & }
button .11 -text "BBC\ Parliament\(BBC\)" -command { exec xterm -e mplayer dvb://BBC\ Parliament\(BBC\) & }
button .12 -text "BBC\ R5L\(BBC\)" -command { exec xterm -e mplayer dvb://BBC\ R5L\(BBC\) & }
button .13 -text "BBC\ R5SX\(BBC\)" -command { exec xterm -e mplayer dvb://BBC\ R5SX\(BBC\) & }
button .14 -text "BBC\ Radio\ 1\(BBC\)" -command { exec xterm -e mplayer dvb://BBC\ Radio\ 1\(BBC\) & }
button .15 -text "BBC\ Radio\ 2\(BBC\)" -command { exec xterm -e mplayer dvb://BBC\ Radio\ 2\(BBC\) & }
button .16 -text "BBC\ Radio\ 3\(BBC\)" -command { exec xterm -e mplayer dvb://BBC\ Radio\ 3\(BBC\) & }
button .17 -text "BBC\ Radio\ 4\(BBC\)" -command { exec xterm -e mplayer dvb://BBC\ Radio\ 4\(BBC\) & }
button .18 -text "BBC\ Radio\ 7\(BBC\)" -command { exec xterm -e mplayer dvb://BBC\ Radio\ 7\(BBC\) & }
button .19 -text "BBC\ THREE\(BBC\)" -command { exec xterm -e mplayer dvb://BBC\ THREE\(BBC\) & }
button .20 -text "BBC\ TWO\(BBC\)" -command { exec xterm -e mplayer dvb://BBC\ TWO\(BBC\) & }
button .21 -text "BBC\ World\ Sv.\(BBC\)" -command { exec xterm -e mplayer dvb://BBC\ World\ Sv.\(BBC\) & }
button .22 -text "bid\ tv\(Sit-Up\ Ltd\)" -command { exec xterm -e mplayer dvb://bid\ tv\(Sit-Up\ Ltd\) & }
button .23 -text "Channel\ 4+1\(Channel\ 4\ TV\)" -command { exec xterm -e mplayer dvb://Channel\ 4+1\(Channel\ 4\ TV\) & }
button .24 -text "Channel\ 4\(Channel\ 4\ TV\)" -command { exec xterm -e mplayer dvb://Channel\ 4\(Channel\ 4\ TV\) & }
button .25 -text "CNN\(CNN\)" -command { exec xterm -e mplayer dvb://CNN\(CNN\) & }
button .26 -text "Dave\ ja\ vu\(UKTV\)" -command { exec xterm -e mplayer dvb://Dave\ ja\ vu\(UKTV\) & }
button .27 -text "Dave\(UKTV\)" -command { exec xterm -e mplayer dvb://Dave\(UKTV\) & }
button .28 -text "E4+1\(Channel\ 4\ TV\)" -command { exec xterm -e mplayer dvb://E4+1\(Channel\ 4\ TV\) & }
button .29 -text "E4\(Channel\ 4\ TV\)" -command { exec xterm -e mplayer dvb://E4\(Channel\ 4\ TV\) & }
button .30 -text "ESPN\(ESPN\)" -command { exec xterm -e mplayer dvb://ESPN\(ESPN\) & }
button .31 -text "Film4\(Channel\ 4\ TV\)" -command { exec xterm -e mplayer dvb://Film4\(Channel\ 4\ TV\) & }
button .32 -text "FIVE\(five\)" -command { exec xterm -e mplayer dvb://FIVE\(five\) & }
button .33 -text "FIVER\(five\)" -command { exec xterm -e mplayer dvb://FIVER\(five\) & }
button .34 -text "FIVE\ USA\(five\)" -command { exec xterm -e mplayer dvb://FIVE\ USA\(five\) & }
button .35 -text "Gay\ Rabbit\(Teletext\ Limited\)" -command { exec xterm -e mplayer dvb://Gay\ Rabbit\(Teletext\ Limited\) & }
button .36 -text "G.O.L.D.\(five\)" -command { exec xterm -e mplayer dvb://G.O.L.D.\(five\) & }
button .37 -text "Heart\(Global\ Radio\)" -command { exec xterm -e mplayer dvb://Heart\(Global\ Radio\) & }
button .38 -text "heat" -command { exec xterm -e mplayer dvb://heat & }
button .39 -text "Ideal\ Extra\(Ideal\ Shopping\ Direct\ PLC\)" -command { exec xterm -e mplayer dvb://Ideal\ Extra\(Ideal\ Shopping\ Direct\ PLC\) & }
button .40 -text "Ideal\ World" -command { exec xterm -e mplayer dvb://Ideal\ World & }
button .41 -text "ITV1\(ITV\)" -command { exec xterm -e mplayer dvb://ITV1\(ITV\) & }
button .42 -text "ITV2\ +1\(ITV\)" -command { exec xterm -e mplayer dvb://ITV2\ +1\(ITV\) & }
button .43 -text "ITV2\(ITV\)" -command { exec xterm -e mplayer dvb://ITV2\(ITV\) & }
button .44 -text "ITV3\(ITV\)" -command { exec xterm -e mplayer dvb://ITV3\(ITV\) & }
button .45 -text "ITV4\(ITV\)" -command { exec xterm -e mplayer dvb://ITV4\(ITV\) & }
button .46 -text "Kerrang\!" -command { exec xterm -e mplayer dvb://Kerrang\! & }
button .47 -text "Kiss" -command { exec xterm -e mplayer dvb://Kiss & }
button .48 -text "Magic" -command { exec xterm -e mplayer dvb://Magic & }
button .49 -text "More\ 4\(Channel\ 4\ TV\)" -command { exec xterm -e mplayer dvb://More\ 4\(Channel\ 4\ TV\) & }
button .50 -text "Premier\ Radio\(London\ Christian\ Radio\ Ltd\)" -command { exec xterm -e mplayer dvb://Premier\ Radio\(London\ Christian\ Radio\ Ltd\) & }
button .51 -text "price-drop\ tv\(sit-up\ limited\)" -command { exec xterm -e mplayer dvb://price-drop\ tv\(sit-up\ limited\) & }
button .52 -text "Q" -command { exec xterm -e mplayer dvb://Q & }
button .53 -text "QUEST\(Discovery\)" -command { exec xterm -e mplayer dvb://QUEST\(Discovery\) & }
button .54 -text "QVC\(QVC\)" -command { exec xterm -e mplayer dvb://QVC\(QVC\) & }
button .55 -text "Rabbit\(Teletext\ Limited\)" -command { exec xterm -e mplayer dvb://Rabbit\(Teletext\ Limited\) & }
button .56 -text "Russia\ Today\(Information\ TV\)" -command { exec xterm -e mplayer dvb://Russia\ Today\(Information\ TV\) & }
button .57 -text "Sky\ News\(Sky\)" -command { exec xterm -e mplayer dvb://Sky\ News\(Sky\) & }
button .58 -text "Sky\ Spts\ News\(Sky\)" -command { exec xterm -e mplayer dvb://Sky\ Spts\ News\(Sky\) & }
button .59 -text "SKY\ THREE\(Sky\)" -command { exec xterm -e mplayer dvb://SKY\ THREE\(Sky\) & }
button .60 -text "Smash\ Hits\!\(EMAP\)" -command { exec xterm -e mplayer dvb://Smash\ Hits\!\(EMAP\) & }
button .61 -text "SMOOTH\ RADIO\(GMG\)" -command { exec xterm -e mplayer dvb://SMOOTH\ RADIO\(GMG\) & }
button .62 -text "talkSPORT\(talkSPORT\)" -command { exec xterm -e mplayer dvb://talkSPORT\(talkSPORT\) & }
button .63 -text "The\ Hits\ Radio" -command { exec xterm -e mplayer dvb://The\ Hits\ Radio & }
button .64 -text "Ttext\ Holidays\(Teletext\ Limited\)" -command { exec xterm -e mplayer dvb://Ttext\ Holidays\(Teletext\ Limited\) & }
button .65 -text "Virgin1+1\(Virgin\ Media\ Television\ Limited\)" -command { exec xterm -e mplayer dvb://Virgin1+1\(Virgin\ Media\ Television\ Limited\) & }
button .66 -text "Virgin1\(Virgin\ Media\ Television\ Limited\)" -command { exec xterm -e mplayer dvb://Virgin1\(Virgin\ Media\ Television\ Limited\) & }
button .67 -text "VIVA\(MTV\ Europe\)" -command { exec xterm -e mplayer dvb://VIVA\(MTV\ Europe\) & }
grid .1 -column 0 -row 1 -sticky w
grid .2 -column 0 -row 2 -sticky w
grid .3 -column 0 -row 3 -sticky w
grid .4 -column 0 -row 4 -sticky w
grid .5 -column 0 -row 5 -sticky w
grid .6 -column 0 -row 6 -sticky w
grid .7 -column 0 -row 7 -sticky w
grid .8 -column 0 -row 8 -sticky w
grid .9 -column 0 -row 9 -sticky w
grid .10 -column 0 -row 10 -sticky w
grid .11 -column 0 -row 11 -sticky w
grid .12 -column 0 -row 12 -sticky w
grid .13 -column 0 -row 13 -sticky w
grid .14 -column 0 -row 14 -sticky w
grid .15 -column 0 -row 15 -sticky w
grid .16 -column 0 -row 16 -sticky w
grid .17 -column 0 -row 17 -sticky w
grid .18 -column 0 -row 18 -sticky w
grid .19 -column 0 -row 19 -sticky w
grid .20 -column 0 -row 20 -sticky w
grid .21 -column 0 -row 21 -sticky w
grid .22 -column 0 -row 22 -sticky w
grid .23 -column 0 -row 23 -sticky w
grid .24 -column 0 -row 24 -sticky w
grid .25 -column 0 -row 25 -sticky w
grid .26 -column 0 -row 26 -sticky w
grid .27 -column 1 -row 1 -sticky w
grid .28 -column 1 -row 2 -sticky w
grid .29 -column 1 -row 3 -sticky w
grid .30 -column 1 -row 4 -sticky w
grid .31 -column 1 -row 5 -sticky w
grid .32 -column 1 -row 6 -sticky w
grid .33 -column 1 -row 7 -sticky w
grid .34 -column 1 -row 8 -sticky w
grid .35 -column 1 -row 9 -sticky w
grid .36 -column 1 -row 10 -sticky w
grid .37 -column 1 -row 11 -sticky w
grid .38 -column 1 -row 12 -sticky w
grid .39 -column 1 -row 13 -sticky w
grid .40 -column 1 -row 14 -sticky w
grid .41 -column 1 -row 15 -sticky w
grid .42 -column 1 -row 16 -sticky w
grid .43 -column 1 -row 17 -sticky w
grid .44 -column 1 -row 18 -sticky w
grid .45 -column 1 -row 19 -sticky w
grid .46 -column 1 -row 20 -sticky w
grid .47 -column 1 -row 21 -sticky w
grid .48 -column 1 -row 22 -sticky w
grid .49 -column 1 -row 23 -sticky w
grid .50 -column 2 -row 1 -sticky w
grid .51 -column 2 -row 2 -sticky w
grid .52 -column 2 -row 3 -sticky w
grid .53 -column 2 -row 4 -sticky w
grid .54 -column 2 -row 5 -sticky w
grid .55 -column 2 -row 6 -sticky w
grid .56 -column 2 -row 7 -sticky w
grid .57 -column 2 -row 8 -sticky w
grid .58 -column 2 -row 9 -sticky w
grid .59 -column 2 -row 10 -sticky w
grid .60 -column 2 -row 11 -sticky w
grid .61 -column 2 -row 12 -sticky w
grid .62 -column 2 -row 13 -sticky w
grid .63 -column 2 -row 14 -sticky w
grid .64 -column 2 -row 15 -sticky w
grid .65 -column 2 -row 16 -sticky w
grid .66 -column 2 -row 17 -sticky w
grid .67 -column 2 -row 18 -sticky w
```A bit more complex than the other scripts but it shows how some simple interfaces for everyday uses can be built.

With a little knowledge of some basic scripting it's possible to connect the power of the Linux CLI and scripting to the GUI and make the experience a lot more interesting and useful. The mouse is a handy tool but it can get overused at the expense of missing the power that Linux provides to the Desktop user :guitar:.
[COLOR=#000000](Next: How to manipulate windows from the keyboard)
[/COLOR]

---

### Post by cdekter on 2010-04-18
[http://autokey.googlecode.com](http://autokey.googlecode.com)

'Nuff sed :P

---

### Post by lovinglinux on 2010-04-18
I used AutoHotKey and like your idea, but for manipulating web text I think is more practical to use a Firefox extension. I have developed [QuoteMarks](https://addons.mozilla.org/en-US/firefox/addon/125271), which can do text manipulation and formatting, including custom HTML and BBCode, save text as notes, save ubuntuforums posts as quotes and paste them with proper formatting, search selected text with custom search strings or format selected text with search strings.

---

### Post by DJ Barney on 2010-04-19
Hi. Oh that's interesting. I use a lot of forums so that could be useful. Has given me an idea for using Zenity to allow me to choose a system shortcut key to add the highlighted text to.

---

### Post by lovinglinux on 2010-04-19
> **DJ Barney said:**
> Hi. Oh that's interesting. I use a lot of forums so that could be useful. Has given me an idea for using Zenity to allow me to choose a system shortcut key to add the highlighted text to.

Feel free to use any code or idea, the extension is released under GPL license.

BTW, I just realized you might like [FoxRunner](http://lovinglinux.megabyet.net/?page_id=527) ([Mozilla](https://addons.mozilla.org/en-US/firefox/addon/98430)). It allows to send a selected text from a site to a script, among other things. So it could save you some time developing the interaction code and allowing you to concentrate on the scripts that use the data.

---

### Post by DJ Barney on 2010-04-19
Thanks. I just installed those two addons. I already use Launchy to pass url's to external scripts from FF. FoxRunner is aimed at readers of tutorial and help pages ?

I find the most fiddly BBCode link to be the combined IMG and URL tags. This is one I want to add as a script. There must be hundreds of these little fiddly things we do in browser (or system) windows that could be made easier. This could be called my mission to save finger joints\\:D/

---

### Post by lovinglinux on 2010-04-19
> **DJ Barney said:**
> FoxRunner is aimed at readers of tutorial and help pages ?

Yes, but to be honest, I barely run any commands posted on tutorials and help pages these days. What I do a lot is to run my own scripts.

---

### Post by begtognen on 2010-09-28
I used AutoHotKey to accomplish this task, and I'm wondering if there's an easy way to do it in Ubuntu?

All I'm after is this:

alt + C, then 11 downarrows, then Enter

Audacity doesn't provide keyboard shortcuts for Effects, and this is the only way to use the "Fade In" menu item.

Thanks so much for any help or suggestions you might have.

---

