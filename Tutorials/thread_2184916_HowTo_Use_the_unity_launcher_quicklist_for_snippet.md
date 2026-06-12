---
title: "HowTo: Use the unity launcher quicklist for snippets"
date: 2013-10-31
forum: Tutorials
---

### Post by stinkeye on 2013-10-31
_[SIZE=3]**[COLOR="#FF0000"]UPDATE[/COLOR]**[/SIZE] version 1.3 (4-Nov-2013)_
Thank you to Vaphell for doing a rewrite of my script.
Renamed quicksnips. See included ReadMe.txt for installation and info.
-------------------------------------------------------------------------------------------


I find glipper's snippet plugin handy but also quite buggy.

This will create a launcher with whatever snippets are defined in snippets.txt.
Just  move the extracted **.quicksnips** folder to your home directory. (folder will be hidden when first extracted)

Make the scripts executable...
```
chmod +x ~/.quicksnips/date.sh ~/.quicksnips/quicksnips.sh ~/.quicksnips/snip2clip.sh
```

Run the **quicksnips.sh** script to create/update  the launcher.
```
cd ~/.quicksnips && ./quicksnips.sh
```

Open the dash and search for "quicksnips" and drag and drop to the launcher
or
open the file browser and and drag and drop  ~/.local/share/applications/quicksnips.desktop.

All you need to do now is create your own snippets as shown in the attached video or
follow the included ReadMe.txt.
You can also add snippets from the clipboard content using a quicklist item.
Adds the snippet and reloads the launcher.

Snippets are currently sent to "-selection clipboard" (right mouse copy/paste and ctrl+c/ctrl+v).
See ReadMe.txt to change to  "-selection primary" (left mouse selection/middle click paste)

Requires xclip.
```
sudo apt-get install xclip
```

---

### Post by ray_field2 on 2013-10-31
thanks very much for this -- I have been using xclip in Midnight Commander to similar purpose.


unfortunately it does not work for me. all the items in snippets.txt display quite handsomely, but no matter which one I select, the clipboard buffer contents do not change. I use Diodon (something like Glipper, I guess) and sometimes things which don't make it to the buffer show up there, but this is not the case.


should mention 1) I don't know if it's pertinent, but I have the mouse buttons reversed, 2) I have noticed in the past that xclip can be very, very picky/flaky/buggy.

---

### Post by Sector11 on 2013-10-31
Nice stuff stinkeye!

You'll be famous soon, can I get your autograph now?

---

### Post by stinkeye on 2013-10-31
Hi ray_field2,
(See edit in first post)
Firstly, I made a small change to the xclip.sh file.
(This isn't related to your problem but may as well change)
To save dowloading again,make this edit..
```
gedit ~/.snippets-launcher/xclip.sh
```
and change...
```
echo $1 | tr -d '\n' | xclip
```
to
```
echo [COLOR="#FF0000"]"[/COLOR]$1[COLOR="#FF0000"]"[/COLOR] | tr -d '\n' | xclip
```
Save the file and close.

Check the scripts are executable ....
```
chmod +x ~/.snippets-launcher/date.sh ~/.snippets-launcher/snippets.sh ~/.snippets-launcher/xclip.sh
```

It works here with diodon in fact you don't even need a clipboard manager running for it to work.
The xclip.sh script is whats's run when you click on a snippet in the quicklist.

Run the command....
```
~/.snippets-launcher/xclip.sh 'test snippet works'
```
If "**test snippet works**" shows with a middle click paste then the xclip script is working.

If not, try sending to the ctrl+c/v of the clipboard.(right click copy/paste)
Use diodons menu item "clear" in between tests
```
echo "test snippet works" | tr -d '\n' | xclip **-selection clipboard**
```

Try also **-selection primary**      (should send to middle click same as with no option)

Let me no the results and we'll go from there.

---

### Post by psypher246 on 2013-11-01
Hello, looks like this doesn't work for snippets with inverted comma ( ' ) in it. So "doesn't"  doesn't work

---

### Post by stinkeye on 2013-11-01
> **psypher246 said:**
> Hello, looks like this doesn't work for snippets with inverted comma ( ' ) in it. So "doesn't"  doesn't work
Hi
Yes, you'll find some copying with quotes in it won't work because of the way it's written to work with 
quicklists. That's just how it is at the moment until I find a better way.
Thanks.

---

### Post by ray_field2 on 2013-11-01
> **stinkeye said:**
> Hi ray_field2,
(See edit in first post)
Firstly, I made a small change to the xclip.sh file.
(This isn't related to your problem but may as well change)
To save dowloading again,make this edit..
```
gedit ~/.snippets-launcher/xclip.sh
```
and change...
```
echo $1 | tr -d '\n' | xclip
```
to
```
echo [COLOR=#FF0000]"[/COLOR]$1[COLOR=#FF0000]"[/COLOR] | tr -d '\n' | xclip
```
Save the file and close.

Check the scripts are executable ....
```
chmod +x ~/.snippets-launcher/date.sh ~/.snippets-launcher/snippets.sh ~/.snippets-launcher/xclip.sh
```

It works here with diodon in fact you don't even need a clipboard manager running for it to work.
The xclip.sh script is whats's run when you click on a snippet in the quicklist.

Run the command....
```
~/.snippets-launcher/xclip.sh 'test snippet works'
```
If "**test snippet works**" shows with a middle click paste then the xclip script is working.

If not, try sending to the ctrl+c/v of the clipboard.(right click copy/paste)
Use diodons menu item "clear" in between tests
```
echo "test snippet works" | tr -d '\n' | xclip **-selection clipboard**
```

Try also **-selection primary**      (should send to middle click same as with no option)

Let me no the results and we'll go from there.

I had chmod'd the scripts, so I'm sure that wasn't the problem; I made the change you suggested.

so now, okay -- 99% of the time I use Ctrl-V to paste, and when I don't, I use [mouse button]/menu, then select paste -- I very seldom use the middle mouse button. it may very well be that it was working before -- so for now, you might want to indicate in the documentation that that's how it's working. I've been too lazy to understand how the X clipboard works, just seem to know that "xclip -i selection clipboard" seems to put it where I want it to.

anyway for the moment I can middle click on my desktop, just not sure how this is going to work on my netbook...

thanks

---

### Post by stinkeye on 2013-11-01
I made a few changes and uploaded a new version.
Seems to copy and paste everything fine now including long commands.
Thanks.

---

### Post by ray_field2 on 2013-11-01
thanks for the quick response. not quite there yet. I cleaned out the directory, copied in the new files, and chmoded. out of the box, middle-mousebutton pressing shows the clipboard hasn't flushed/copied -- however, the xclip.sh works.

just for grins, I uncommented the Ctrl-V option and commented out the button-paste. still no joy -- however, once again, xclip.sh works, placing the text where it should be in the buffer where Ctrl-V can paste it.

tested it on my laptop with same results. 

-ray

---

### Post by stinkeye on 2013-11-01
In version 1.1 the xclip.sh script isn't used.
This was giving me problems with quotes and variables.

Open ~/.snippets-launcher/snippets.sh and go to line #56.
Change the line...
```
Exec=sh -c \"head -$n ~/.snippets-launcher/snippets.txt | tail -1 | tr -d '\n' | **xclip -i**\"
```
to
```
Exec=sh -c \"head -$n ~/.snippets-launcher/snippets.txt | tail -1 | tr -d '\n' | **xclip -i** [COLOR="#FF0000"]-selection clipboard[/COLOR]\"
```
Update the launcher after change.

xclip..............................................default left mouse selection/middle click paste
xclip -selection primary........................same as above
xclip -selection clipboard ......................right mouse copy/paste and ctrl+c/ctrl+v

You can check the commands being run by looking at the ~/.local/share/applications/snippets.desktop file.
```
gedit  ~/.local/share/applications/snippets.desktop
```
You should see similar to this with your snippets listed.
```
[Desktop Entry]
Version=1.0
Name=Snippets
Comment=Snippets to clipboard using xclip
GenericName=Snippets
Exec=gedit /home/glen/.snippets-launcher/snippets.txt
Icon=/home/glen/.snippets-launcher/Snippets.png
Terminal=false
X-MultipleArgs=false
Type=Application
Categories=GNOME;System;
X-Ayatana-Desktop-Shortcuts=Snippet1;Snippet2;Snippet3;Snippet4;Snippet5;Snippet6;Snippet96;Snippet97;Snippet98;Snippet99
[Snippet1 Shortcut Group]
	Name=**compizconfig-settings-manager**
	Exec=[COLOR="#FF0000"]sh -c "head -1 ~/.snippets-launcher/snippets.txt | tail -1 | tr -d '\n' | xclip -i -selection clipboard"[/COLOR]
	TargetEnvironment=Unity
[Snippet2 Shortcut Group]
	Name=read -n 1 -p "Press any key to exit this script..." 
	Exec=sh -c "head -2 ~/.snippets-launcher/snippets.txt | tail -1 | tr -d '\n' | xclip -i -selection clipboard"
	TargetEnvironment=Unity
[Snippet3 Shortcut Group].......
.....................................
```

This is the [COLOR="#FF0000"]command[/COLOR] that runs when clicking on a quicklist item..
eg if I run the "Exec=" command in the terminal  for my first snippet...
```
sh -c "head -1 ~/.snippets-launcher/snippets.txt | tail -1 | tr -d '\n' | xclip -i -selection clipboard"
```
....it will send **compizconfig-settings-manager** to right mouse copy/paste and ctrl+c/ctrl+v.

This is my diodon settings....

---

### Post by ray_field2 on 2013-11-02
not sure I made myself clear -- the launcher object no longer seems to be working AT ALL. whereas the original version was capturing snippets for middle-click pasting, in this version nothing is happening right now.

---

### Post by ray_field2 on 2013-11-02
couple notes:

1) the "Date" snippet works fine -- as things are configured now, to middle-mousebutton

2) though clicking on the Unity Launcher doesn't work, running this DOES copy the snippet to where Ctrl-V can get at it

```
sh -c "head -1 ~/.snippets-launcher/snippets.txt | tail -1 | tr -d '\n' | xclip -i -selection clipboard"
```

3) here is my snippets.txt

```
718-421-8779
http://www.youtube.com/watch?v=malB-TLIpio&feature=share
Weight: 154 Hair: brown/gray; Eyes: brown Suit: 38 Pants: 34/32 Shoes: 9 Hat: 7 3/8
```

---

### Post by stinkeye on 2013-11-02
> **ray_field2 said:**
> couple notes:

1) the "Date" snippet works fine -- as things are configured now, to middle-mousebutton

2) though clicking on the Unity Launcher doesn't work, running this DOES copy the snippet to where Ctrl-V can get at it

```
sh -c "head -1 ~/.snippets-launcher/snippets.txt | tail -1 | tr -d '\n' | xclip -i -selection clipboard"
```

3) here is my snippets.txt

```
718-421-8779
http://www.youtube.com/watch?v=malB-TLIpio&feature=share
Weight: 154 Hair: brown/gray; Eyes: brown Suit: 38 Pants: 34/32 Shoes: 9 Hat: 7 3/8
```
It works here.
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **head -1 ~/.snippets-launcher/snippets.txt | tail -1** 
718-421-8779
[COLOR="#008000"]glen@Raring:~$[/COLOR] **head -2 ~/.snippets-launcher/snippets.txt | tail -1** 
http://www.youtube.com/watch?v=malB-TLIpio&feature=share
[COLOR="#008000"]glen@Raring:~$[/COLOR] **head -3 ~/.snippets-launcher/snippets.txt | tail -1**
Weight: 154 Hair: brown/gray; Eyes: brown Suit: 38 Pants: 34/32 Shoes: 9 Hat: 7 3/8
```
Try replacing your current **~/.snippets-launcher/snippets.sh**  file with this one. Then updatethe launcher
```
#!/bin/bash
#set -x
# Use snippets from a unity quicklist.
# Creates a ~/.local/share/applications/snippets.desktop file to drag and drop on the unity launcher
# or any dock that supports quicklists.
# The right click quicklist items are created from ~/.snippets-launcher/snippets.txt....one snippet per line...
# ....and will be sorted alphbetically.
# Can add cipboard content via quicklist menu.



mkdir -p ~/.local/share/applications
sed -i '/^\s*$/d' ~/.snippets-launcher/snippets.txt                            # remove blank lines
sort ~/.snippets-launcher/snippets.txt -o ~/.snippets-launcher/snippets.txt    # alphbetical
rm -rf /tmp/.actions*                                                         #clean before start


## count snippets
snipcount=$(cat ~/.snippets-launcher/snippets.txt | wc -l)

## create single line to use with desktop "Actions"
n=1
while [ $n -le "$snipcount" ];
do
echo Snippet$n\; | tee -a /tmp/.actions
n=$(( n+1 )) 
done

awk '{ printf "%s", $0 }' /tmp/.actions > /tmp/.actions2
rm -rf "/tmp/.actions"
cp /tmp/.actions2 /tmp/.actions

shortcuts=$(cat /tmp/.actions)

echo "[Desktop Entry]
Version=1.0
Name=Snippets
Comment=Snippets to clipboard using xclip
GenericName=Snippets
Exec=gedit $HOME/.snippets-launcher/snippets.txt
Icon=$HOME/.snippets-launcher/Snippets.png
Terminal=false
X-MultipleArgs=false
Type=Application
Categories=GNOME;System;
X-Ayatana-Desktop-Shortcuts=${shortcuts}Snippet96;Snippet97;Snippet98;Snippet99" | tee ~/.local/share/applications/snippets.desktop


## get quicklist titles from snippets.txt and create the quicklists
	n=1
	while [ $n -le "$snipcount" ];
	do
	MENUENTRY=$(sed -n "$n{p;q;}" $HOME/.snippets-launcher/snippets.txt)   #/tmp/.ur_bootlist2
	echo "[Snippet$n Shortcut Group]
	Name=$(echo "$MENUENTRY")
	Exec=sh -c \"head -$n ~/.snippets-launcher/snippets.txt | tail -1 | tr -d '\n' | xclip -i -selection clipboard\"
	TargetEnvironment=Unity" | tee -a ~/.local/share/applications/snippets.desktop
	n=$(( n+1 ))
	done
	rm -rf /tmp/.actions* > /dev/null 2>&1

### permanent quicklists
## date
echo "[Snippet96 Shortcut Group]
	Name=Date
	Exec=$HOME/.snippets-launcher/date.sh
	TargetEnvironment=Unity" | tee -a ~/.local/share/applications/snippets.desktop

## quicklist item used as a separator
echo "[Snippet97 Shortcut Group]
	Name=__________________________________________________
	Exec=notify-send -i $HOME/.snippets-launcher/mp2.jpeg 'Go Away...or I shall taunt you a second time !'
	TargetEnvironment=Unity" | tee -a ~/.local/share/applications/snippets.desktop

## Add clipboard to snippets and update 
echo "[Snippet98 Shortcut Group]
	Name=Add Clipboard Content
	Exec=sh -c \"xclip -selection clipboard -o >> $HOME/.snippets-launcher/snippets.txt; $HOME/.snippets-launcher/snippets.sh\"
	TargetEnvironment=Unity" | tee -a ~/.local/share/applications/snippets.desktop

## update launcher after changing snippets
echo "[Snippet99 Shortcut Group]
	Name=Update Launcher
	Exec=gnome-terminal -e $HOME/.snippets-launcher/snippets.sh
	TargetEnvironment=Unity" | tee -a ~/.local/share/applications/snippets.desktop



#chmod +x ~/.local/share/applications/snippets.desktop
```

If that doesn't work I'm currently testing a cleaner version written for me by [**_[COLOR="#B22222"]Vaphell[/COLOR]_**]("http://ubuntuforums.org/member.php?u=347382")
that I will post soon.

---

### Post by ray_field2 on 2013-11-02
> **stinkeye said:**
> 
Try replacing your current **~/.snippets-launcher/snippets.sh**  file with this one.

no joy. 

again, what puzzles me is that 

```
sh -c "head -1 ~/.snippets-launcher/snippets.txt | tail -1 | tr -d '\n' | xclip -i -selection clipboard"
```

works perfectly.

---

### Post by stinkeye on 2013-11-02
Post the contents of the created snippets.desktop file.
```
gedit ~/.local/share/applications/snippets.desktop
```

---

### Post by stinkeye on 2013-11-02
I'm off to bed. The error is probably with my script.
Try Vaphell's version.
This one's packaged up as **quicksnips**.
Same install method. Check the **ReadMe**.

You can leave the other one as they don't interfere.
Can remove if like with....
```
rm -rf ~/.snippets-launcher ~/.local/share/applications/snippets.desktop
```

---

### Post by ray_field2 on 2013-11-02
pleasant dreams. Vaphell's version works perfectly. thanks once again Stinkeye, and Vaphell.

---

### Post by stinkeye on 2013-11-03
Updated to version 1.3 with thanks to Vaphell. (Bug fix for parsing of certain strings)
See first post.

---

### Post by francesc2 on 2013-11-08
Hi community... My first post of many I hope...
For me  is working perfect under 12.04.3

1- Is there a way to add 1 snipp with multiple lines in the list? If paragraph is added it chops the lines in diferent snippets.

2- colors ?  #FFFFFF ??


Thank you all for everything you ve done and will ...

---

### Post by stinkeye on 2013-11-08
> **francesc2 said:**
> Hi community... My first post of many I hope...
For me  is working perfect under 12.04.3

1- Is there a way to add 1 snipp with multiple lines in the list? If paragraph is added it chops the lines in diferent snippets.

2- colors ?  #FFFFFF ??


Thank you all for everything you ve done and will ...
It's not really meant for copying paragraphs of text but as a snippets companion
to your normal clipboard be that glipper, clipit, diodon etc.

Any line in the **~/.quicksnips/snippets.txt** file starting with "**#**" is ignored so you can add comments.
If you add  "**#FFFFFF**" via the "Add Clipboard Content" quicklist item it is added to snippets.txt
but no quicklist item is created.

---

### Post by francesc2 on 2013-11-09
Ok... It s very helpful anyway! Thanks again!

---

