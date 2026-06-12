---
title: "HOWTO: Associate filetypes with Windows(wine) applications"
date: 2007-10-02
forum: Tutorials
---

### Post by weblordpepe on 2007-10-02
[SIZE="5"]What is needed:[/SIZE]
Hello guys. I found it nessecary to have an icon on my desktop for Irfanview, which I could drag pictures onto and have them load. Or simply double-click on a picture, and have it load in IrfanView.
This is a problem with any Windows app, but today Matthew we will be using IrfanView.

[SIZE="5"]Why it cant normally be done[/SIZE]
The problem is that Irfanview is a Windows program, and you can't pass linux filepaths to Windows programs unless you convert them with winepath.

[SIZE="5"] The end result[/SIZE]
The end result after this HOWTO, is a icon on the desktop which launches Irfanview(in wine) when clicked, and I can also drag files onto it. Also, I have .gif files associated with Irfanview.

[SIZE="5"]How to do it[/SIZE]
This is done by having a quick script which accepts normal linux filepath arguments, and creates a SH script on the fly to convert it to a Windows-friendly path and launch IrfanView With it.

You then simply put a launcher to it on your desktop. And you can even register filetypes to open with the script.

So here is the script. Save it where ever. In this example it is **~/irfanview.sh**:
```
#!/bin/sh
# This is a script to allow a launcher to open Irfanview with a file dragged onto it.
# It uses winepath -w to convert the file's path to the Windows version, and then 
# creates a simple sh script to launch wine/irfanview/document with the correct syntax.

# Note: Yes I know the constructed shell script doesnt have #!/bin/sh at the beginning.
#       Im not that good, and hey it works. So shoosh
#
#
# By Weblordpepe. Oct 3, 2007. 5:10am.
# (Finished: Oct 6, 2007. 11:25pm)


# Report to console the file wanted, clear temporary files.
	rm -f ~/.wine/iprog3 ~/.wine/iprog2 ~/.wine/iprog


# Display to user whats going on
	echo ---
	echo Loading $1- into Irfanview.
	echo Make Pepe a SANDWICH!
	echo ---

# Begin command line making:
	# Output (to text file) the command to launch Irfanview under Wine.
	echo -n wine /usr/local/IrfanView/i_view32.exe\ >> ~/.wine/iprog 

	# Output Windows version of the file path to the same text file.
	echo -n "\\042" >> ~/.wine/iprog # First doublequotes
	winepath -w "$1" |tr 'h:' 'H:' | tr 'z:' 'Z:' >> ~/.wine/iprog  # Replace lowercase driveletter to uppercase and output to file.
	echo -n "\\042" >> ~/.wine/iprog # Second doublequotes

	# Create new textfile but delete all 'new lines's so its all on one line.
	less ~/.wine/iprog | tr -d '\n'   >> ~/.wine/iprog2

# End of command file making


# Run the file text file which includes instruction to run Irfanview under wine with
# the Windows filepath on the end.
	sh ~/.wine/iprog2

# clean up
	rm -f ~/.wine/iprog3 ~/.wine/iprog2 ~/.wine/iprog
```

Now what you want to do is create a launcher on the desktop. I've only done this with Gnome.  So KDE guys try it out & lemme know.

Create a launcher (type: application) on the desktop, and call it anything you like. The command should be **gksu -u dork /home/dork/irfanview.sh** where **dork** is your username. I think there's also a variable you can use.

There you have it. An icon you can drop files onto and have them loaded with Irfanview, or another Windows app.

To associate files, just right click any file, go to Properties, then 'Open With' and create a new entry. Select 'custom command' and put in **sh /home/dork/irfanview.sh** or wherever you've put the file.


And thats it. Filetypes opening with a windows application. No doubt there's a much easier way that I'm not aware of. But eh, it works so I'm happy. :guitar:

---

### Post by stinger30au on 2007-11-03
awesome!!!

i have been wondering if it could be done!!

thanks so much

---

### Post by weblordpepe on 2007-11-03
:guitar: \m/

---

### Post by TeaSwigger on 2007-11-05
Hello weblordpepe, I'm posting to thank you for the script and to tell you that I've adapted it to open KeyNote (the note manager) documents and it's working perfectly well in Kubuntu. :)

---

### Post by weblordpepe on 2007-11-05
Awesome! Thats what I like to hear! This script could easily be modified to launch any program. Just by parsing another argument on the command line.

eg:

runprogram.sh /usr/local/irfanview/i_view32.exe /home/dork/picture.jpg 

What do you think?

---

### Post by parmenpj on 2009-06-04
This line (note that I changed drive letter "H" to "C" to match my system):
    winepath -w "$1" | tr 'c:' 'C:' |  tr 'z:' 'Z:' >> ~/.wine/iprog  # Replace lowercase driveletter to uppercase and output to file.

Should be:
    winepath -w "$1" | sed s/c:/C:/g |  sed s/z:/Z:/g >> ~/.wine/iprog  # Replace lowercase driveletter to uppercase and output to file

This is because **sed** is successful in replacing the phrase "c:" with "C:", but **tr** instead replaces all instances of "c" with "C", "z" with "Z", etc.,  and does not recognize the phrase "c:", "z:", etc.

This is not causing problems most of the time, because Wine/Windows pathnames are case-insensitive - but you never know when a problem may arise.

Another thing I found:
On my Kubuntu system, Wine is in a different location so this line:
echo -n wine /usr/local/IrfanView/i_view32.exe\ >> ~/.wine/iprog

Becomes:
echo -n wine "/home/parmenpj/.wine/drive_c/Program\ Files/IrfanView/i_view32.exe"\ >> ~/.wine/iprog

Note here that "\" is needed to precede the space in "Program Files", and because there is a space the entire pathname must also be in quotes.

Hope this helps more people use this _GREAT_ _IDEA_!  Thank you!

---

### Post by parmenpj on 2009-06-04
Your efforts ROCK.  Thanks again.  FYI - I found a very small script on [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine).  Way cool and fast:[INDENT]#!/bin/sh

QUICKPARLOCATION="c:\\Program Files\\IrfanView\\i_view32.exe"
PARAM=`winepath -w "$*"`
wine "$QUICKPARLOCATION" "$PARAM"
exit 0
[/INDENT]

---

### Post by kimharding on 2009-11-25
Have anyone got this working with Karmic? I had it working beautifully under Jaunty but since I upgraded to Karmic it hasn't been working. :-(

---

### Post by skidmarks on 2010-02-02
@parmenpj - Great find!

That little script is just what I was looking for. I thought there'd be a nice simple way to do this.

@kimharding - works fine for me under karmic.

---

### Post by avada on 2010-05-11
This simple script worked for me:

```
#!/bin/bash

torrent_path=`winepath -w $1`

wine "/media/***Path to utorrent***/utorrent.exe" $torrent_path
```

What I don't know how to do is to get the icon of utorrent.exe for the quick launch icon...
Kind of annoying to have a bunch of blank icons for the windows programs.

---

### Post by MestreLion on 2011-08-07
> **avada said:**
> This simple script worked for me:

```
#!/bin/bash

torrent_path=`winepath -w $1`

wine "/media/***Path to utorrent***/utorrent.exe" $torrent_path
```What I don't know how to do is to get the icon of utorrent.exe for the quick launch icon...
Kind of annoying to have a bunch of blank icons for the windows programs.

When you install an app via wine it automatically extracts icons from the .EXE, converts them to .PNG, and places them in ~/.local/share/icons/hicolor/SIZE/apps (where SIZE=16x16, 32x32, etc)

If youre running uTorrent without installing, you can extract the icon yourself using gExtractWinIcons (its a nice app avaliable in repositores)

---

