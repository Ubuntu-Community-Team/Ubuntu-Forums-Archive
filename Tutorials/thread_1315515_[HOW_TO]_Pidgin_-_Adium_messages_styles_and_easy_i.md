---
title: "[HOW TO] Pidgin - Adium messages styles and easy install"
date: 2009-11-05
forum: Tutorials
---

### Post by h!v on 2009-11-05
**[SIZE="4"]Base info[/SIZE]**
[LIST]
[*]How to is based around modified script for Empathy. I tweaked it to make it working with notifications and other popular IM-app, Pidgin.
[*]All credits go to Antono Vasiljev and Vertlo Oraerk. You can get script for Empathy [here]("http://ubuntuforums.org/showthread.php?t=1297237").
[*]I modified it a little to not spew out errors. Notifications work. For something they are after all.
[*] If you find any issues, especially if you've found solution,  be sure to post it. I'm visiting this thread at least once a week, I'll update thread or try to give a hand.
[/LIST]

**[CENTER][SIZE="4"]Message Themes[/SIZE][/CENTER]**
*[CENTER]Keep in mind not every theme will work properly.[/CENTER]*
[CENTER][SIZE="4"][ Adium Xtras Site](http://www.adiumxtras.com/index.php?a=search&cat_id=5) | [ Live Gnome](http://live.gnome.org/Empathy/Themes)[/SIZE]

**[SIZE="4"]Sound Themes[/SIZE]**
[SIZE="4"][ Adium Xtras ]("http://www.adiumxtras.com/index.php?a=search&cat_id=3&sort=date_reviewed")[/SIZE]

**Examples**
_I hold no rights to images._
**Renkoo theme**
This theme is worth it. There's lot's off it.
[[IMG]http://www.adiumxtras.com/images/pictures/renkoo_5_3613_2160_image_3514.jpg[/IMG]](http://www.adiumxtras.com/index.php?a=xtras&xtra_id=2160)
source:[http://www.adiumxtras.com/index.php?a=xtras&xtra_id=2160](http://www.adiumxtras.com/index.php?a=xtras&xtra_id=2160)

[SIZE="4"]**Known Issues**[/SIZE][/Center]
[LIST]
[*] Pidgin 2.7
> **TorontoStorm said:**
> I followed the guide, and the adium theme works sometimes. I'm not able to fully identify when it works, but it seems to be when I initiate the conversation with a contact, and not when they message me first. It also doesn't work if I close the conversation window, then open it again. Only a restart of Pidgin gets the adium theme back once that happens.
Workaround
> **TorontoStorm said:**
> 
I identified the source of my problem, and a temporary solution it it. If "Hide new conversations" is set "Always" or "When Away", if someone messages you, and Pidgin hides the window until you go to open it, it reverts to normal conversation rendering (not webkit) for the rest of the time pidgin is open, and only a restart will put it back to using webkit. The obvious workaround for now is to set that setting as "Never".
[*] You'll need Pidgin in version at least 2.6.X to support Sound Themes.
[*] It appears there's no indicator if someone's writing. (If you find any theme with indicator feature, be sure to post it.)
[/LIST]

[CENTER]**[SIZE="5"]Get it working[/SIZE]**[/CENTER]

**[SIZE="4"][CENTER]10.4 Lucid Lynx[/SIZE]**
[SIZE="2"]( You can also check out [this post]("http://ubuntuforums.org/showpost.php?p=9213055&postcount=15") to get it working.)[/SIZE]
[/CENTER]

[LIST=1]
[*]Issue this command
```

sudo  apt-get install pidgin libnotify-bin libpurple-dev pidgin-dev libwebkit-dev bzr wget 

```
[*] Use this script
```

#!/bin/bash
PAT="~/bin/adium-pidgin"
URL="http://dl.dropbox.com/u/422036/adium-pidgin"
bin="$HOME/bin/"
if [ !-d $bin ] 
then
	notify-send "Making" \ "bin directory in home folder" --icon=pidgin
	mkdir ~/bin
fi
cd $bin
notify-send "I'm in bin" \ "and downloading script, then appling exec rights" --icon=pidgin
wget --no-verbose -O adium-pidgin $URL
chmod +x adium-pidgin
cd ~/
notify-send "Webkit with Karmic's fixes" \ "Downloading, compiling & installing" --icon=pidgin

TMPDIR=`mktemp -d`
cd $TMPDIR
bzr branch lp:~spoidar/pidgin-webkit/karmic-fixes
cd karmic-fixes
make
cp webkit.so ~/.purple/plugins/webkit.so
rm -rf $TMPDIR

notify-send "Now let me make it working" \ "Adding keys to gconf" --icon=pidgin
gconftool-2 -t string -s /desktop/gnome/url-handlers/adiumxtra/command "$PAT %s"
gconftool-2 -t bool -s /desktop/gnome/url-handlers/adiumxtra/enabled true
gconftool-2 -t bool -s /desktop/gnome/url-handlers/adiumxtra/needs_terminal false
notify-send "Check out" \ "Plugins>Webkit message styles and configure it" --icon=pidgin
exit 0

```
[/LIST]

[CENTER][SIZE="4"]**To select theme**[/SIZE]
Go to 
Pidgin > Plugins > Webkit message style > Configure Plugin 

**[size="5"]Other versions**[/size][/CENTER]

**[center][size="4"] One Script[/size]**to rule two of them [/center]

Guess what! Now, Yoda it approves!
Copypasta this text into text editor. If you don't have bin directory in your home folder, make one. Save the file as adium-pidgin there. If you're naughty lad/lass save where ever you wan't but pay attention when you add keys to gconf.
```

#!/bin/bash
# Adium theme AdiumMessageStyle installer for Empathy
# Originally © 2009 Antono Vasiljev
# Licensed under the same terms as Empathy
# http://antono.info/en/165-install-adium-themes-to-empathy
# Changed by Vertlo Oraerk (did not work with directories containing spaces in the names)
# Changed by h!v from ubuntuforums to work with Pidgin+libwebkit and Notifications
# On Ubuntu you need to install libwebkit and libnotify-bin to get it working properly
# Further info on how to get working adium themes in Pidgin at http://www.webupd8.org/2009/05/pidgin-webkit-plugin-adium-conversation.html
# 02-12-2010 - Support for Adium 1.0 sound themes added. Hooha!
# Sound themes are supported in 2.6.x versions. If there's no file set for event, Pidgin falls to default sound file.
# 	IM
#Message Sent = send_im
#Message Received (New) = first_im_recv
#Message Received = im_recv
#	Chat
#Message Sent = send_chat_msg - you send a message in a chat 
#Message Received (Group Chat) =  chat_msg_recv - someone else sends a message in a chat 
#You Are Mentioned = nick_said - someone says your username in a chat
#	Status
#Contact Signed On = login
#Contact Signed Off = logoff
#Contact Joins = join_chat - a person enters a chat 
#Contact Leaves = left_chat - a person leaves a chat 
types[0]="<key>Message Sent</key>"
types[1]="<key>Message Received (New)</key>"
types[2]="<key>Message Received</key>"
types[3]="<key>Message Sent</key>"
types[4]="<key>Message Received (Group Chat)</key>"
types[5]="<key>You Are Mentioned</key>"
types[6]="<key>Contact Signed On</key>"
types[7]="<key>Contact Signed Off</key>"
types[8]="<key>Contact Joins</key>"
types[9]="<key>Contact Leaves</key>"
events[0]="im_sent"
events[1]="first_im_recv"
events[2]="im_recv"
events[3]="send_chat_msg"
events[4]="chat_msg_rec"
events[5]="nick_said"
events[6]="login"
events[7]="logoff"
events[8]="join_chat"
events[9]="left_chat"
# Creating a file

if [ -z $1 ]
then
    echo
    echo "Usage:"
    echo "`basename $0` adiumxtra://some.url.here/extra"
    echo
    exit 1
else
    TMPDIR=`mktemp -d`
    XTRAURL=`echo $1 | sed -e "s/^adiumxtra:/http:/"`
    DEST="$HOME/.purple/message_styles/"
    
    
    if [ ! -d $DEST ]
    then
        mkdir -v -p $DEST
    fi

    cd $TMPDIR
    notify-send "File this" \ "for Adium to be seems" --icon=pidgin
    wget --no-verbose -O xtra.zip $XTRAURL
    unzip -qq xtra.zip

    ls -d ./*.AdiumMessageStyle/ > themes_to_copy.lst
    ls -d ./*.AdiumSoundset/ > sound.lst
    num_bytes=`wc -c themes_to_copy.lst | sed 's# themes_to_copy.lst##'` 
    sound=`wc -c sound.lst | sed 's# sound.lst##'` 
    NAME=`cat themes_to_copy.lst | cut -f 2 --delimiter='.' | cut -f 2 --delimiter='/'`
    NAME_S=`cat sound.lst | cut -f 2 --delimiter='.' | cut -f 2 --delimiter='/'`

    if [ $num_bytes = 0 ]
    then
    	if [ $sound = 0 ]
    	then
        	notify-send "All here I found" \ "gibberish was" --icon=pidgin
        else
        	while read line_
        	do
        		if [ ! -d $line_/Sounds.plist ]
        		then
        		notify-send "Found I theme" \ " $NAME_S " --icon=pidgin
        		DEST="$HOME/.purple/themes/$NAME_S/purple/sound/"
        		if [ ! -d $DEST ]
			    then
			        mkdir -v -p $DEST
			fi
        		# Creating a file
			touch theme.xml
			echo -e "<?xml version=\"1.0\" encoding=\"UTF-8\"?> ">> $line_/theme.xml
			echo -e "<theme type=\"sound\" name=\"$NAME_S\">" >> $line_/theme.xml
			while read line
			do
				if [ "$line" = "<key>Info</key>" ]
				then
					read line
					inf=`echo $line | sed -e "s/<string>//" | sed -e "s/<\/string>//"`
					echo -e "\t<description>$inf</description>" >> $line_/theme.xml
				fi
				for ((j=0; j<=9; j++))
				do
					if [ "$line" = "${types[j]}" ]
					then
						read line
						file=`echo $line | sed -e "s/<string>//" | sed -e "s/<\/string>//"`
						echo -e "\t<event name=\"${events[j]}\" file=\"$file\"/>" >> $line_/theme.xml
					fi		
				done
			done < $line_/Sounds.plist
			echo -e "</theme>" >> $line_/theme.xml
			echo cp -r \'$line_\'* $DEST | sh			
			else
				notify-send "Use I force could" \ "none effect, that made" --icon=pidgin
			fi
        	done < sound.lst
        fi        
    else
        while read line 
        do
            echo cp -r \'$line\' "$DEST" | sh
        done < themes_to_copy.lst
        echo
        notify-send "Installed I" \ " $NAME for you " --icon=pidgin
    fi
    rm -r xtra.zip    
    rm -r $TMPDIR
fi
exit 0

```


[CENTER]**[size="4"]Browsers Support / Handling Adiumxtra **[/size]
As you can see script is triggered when adiumxtra is used by any browser.[/CENTER]
**Add gconf keys**
```

gconftool-2 -t string -s /desktop/gnome/url-handlers/adiumxtra/command "~/bin/adium-pidgin %s"
gconftool-2 -t bool -s /desktop/gnome/url-handlers/adiumxtra/enabled true
gconftool-2 -t bool -s /desktop/gnome/url-handlers/adiumxtra/needs_terminal false

```
[LIST]
[*]**Firefox**
As reported it should work nicely with FireFox 3.5 provided by Karmic. In Jaunty with FireFox 3.0.15, adiumxtra protocol is unrecognized, and I haven't found work around since I rarely use this browser.
[*]**Chrome**
Latest Chrome gives me no problems.
[*]**Opera**
To get it working in Opera go to Tools>Preferences>Advanced>Programs and add new 
```

adiumxtra

```
with path to file with script.
[/LIST]

**Splendid, off we go!**

[CENTER][SIZE="4"]**Karmic 10.04**[/SIZE][/CENTER]
[list]
[*] I'm not sure if provided webkit packages are enough. Add repo just in case
[*] Issue command to install what needed
[*] We will need fixed and compiled version off that plugin. Install it and we're off.
[/list] 

```

sudo ppa:webkit-team/ppa
sudo apt-get update
sudo apt-get install libnotify-bin pidgin-dev libpurple-dev libwebkit-dev
bzr branch lp:~spoidar/pidgin-webkit/karmic-fixes
cd karmic-fixes
make
cp webkit.so ~/.purple/plugins/webkit.so

```



[CENTER][SIZE="4"]**Jaunty 9.04**[/SIZE][/CENTER]
To cook it out we'll need
[LIST]
[*] libnotify-bin to allow communication feedback from script
[*] Developer packages for pidgin and libpurple
[*] Plugin itself from [www.nukeador.com](www.nukeador.com)
[*] Repo from webkit-team and webkit-dev package from there
[*] Script itself
[/LIST]

We'll do this like this
```

sudo apt-get install libnotify-bin pidgin-dev libpurple-dev
cd
wget -c http://www.nukeador.com/wp-content/uploads/2009/03/pidgin-webkit.tar.bz2
mv plugins ~/.purple/
mv message_styles ~/.purple/
rm -rf LEEME 
rm -rf pidgin-webkit.tar.bz2
sudo echo -e  "#Webkit-team repo \n deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main \n deb-src http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main \n" >> /etc/apt/sources.list
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D9A3C5B 
sudo apt-get update && sudo apt-get install libwebkit-dev

```

[center]**[size="4"]9.10 and below **[/center][/size]
I believe you'll need to repeat steps as for Jaunty and compile plugin by yourself. It's not that much of a work. Just some variations of previous commands.

Cheers.

PS. There's some lousy coding in. Suggestions? Go ahead and pm or post it here.

---

### Post by xord on 2009-11-14
not working for me. pidgin doesn't recognize the webkit plug in. im using 2.6.2 in karmic.

---

### Post by Idun on 2009-11-15
I have the same problem. Think I read somewhere that the "webkit" doesn't exist anymore, perhaps that's why it doesn't work ;). But I'm no expert...

---

### Post by h!v on 2009-11-15
Plugin does not work on 64 bit systems, which might be a problem. 
Also there are fixes for webkit in Karmic on launchpad. Take a look at last part of starting post.

> **Idun said:**
> Think I read somewhere that the "webkit" doesn't exist anymore, perhaps that's why it doesn't work ;). But I'm no expert...

Plugin is not developed currently. Webkit exists and is well. Take a look at Chrome and Safari or Arora.

---

### Post by Nahuel_ on 2009-11-18
Works a dream for me. 

Just one little thing that bothers me a bit... it won't tell you if the other person is typing. Any way to fix that?

Thank you!

---

### Post by h!v on 2009-11-21
> **Nahuel_ said:**
> Works a dream for me. 

Just one little thing that bothers me a bit... it won't tell you if the other person is typing. Any way to fix that?

Thank you!

I can give you only 2 advices.

1. Try other themes. I suppose it might depend on it.
2. Try out plugin. It predicts if someone is writing to you. Cannot recall the name. Should be in libpurple pluginpack.

Cheers.

---

### Post by bigbrovar on 2009-12-11
Is there any way to get this working on karmic?
Never mind got it to work using this guide [http://www.webupd8.org/2009/11/adium-themes-in-pidgin-ubuntu-karmic.html](http://www.webupd8.org/2009/11/adium-themes-in-pidgin-ubuntu-karmic.html)

---

### Post by xord on 2009-12-15
> **bigbrovar said:**
> Is there any way to get this working on karmic?
Never mind got it to work using this guide [http://www.webupd8.org/2009/11/adium-themes-in-pidgin-ubuntu-karmic.html](http://www.webupd8.org/2009/11/adium-themes-in-pidgin-ubuntu-karmic.html)

thanks a lot

---

### Post by kyquangthai on 2009-12-17
I complile plugin webkit, now you can download and use Adium message styles for pidgin after install it.

---

### Post by conorsulli on 2009-12-18
Guys I tried this plugin a while back (with a much easier install method from what I remember) however I would be willing to try this if someone could tell me if the bug where if you sent a nudge etc the screen would no longer scroll / update is fixed?

---

### Post by nrayever on 2009-12-18
I was wondering how it looks. i don't actually know how it looks the adium messages styles. maybe a screenshot may help. thanks a lot.

:lolflag::lolflag::lolflag:

Regards, Nrayever

---

### Post by kyquangthai on 2009-12-20
> **nrayever said:**
> I was wondering how it looks. i don't actually know how it looks the adium messages styles. maybe a screenshot may help. thanks a lot.

:lolflag::lolflag::lolflag:

Regards, Nrayever

ya, this look:

---

### Post by h!v on 2010-01-13
> **conorsulli said:**
> Guys I tried this plugin a while back (with a much easier install method from what I remember) however I would be willing to try this if someone could tell me if the bug where if you sent a nudge etc the screen would no longer scroll / update is fixed?

It's less about plugin it self and more about script to install them just by clicking install. Sorry but I have, no idea.

> **nrayever said:**
> I was wondering how it looks. i don't actually know how it looks the adium messages styles. maybe a screenshot may help. thanks a lot.

:lolflag::lolflag::lolflag:

Regards, Nrayever

Just go here, themes if installed properly should be rendered the same as in Adium on OS X
[http://www.adiumxtras.com/index.php?a=search&cat_id=5](http://www.adiumxtras.com/index.php?a=search&cat_id=5)

---

### Post by h!v on 2010-02-12
*shameful bump for updates*

---

### Post by daqron on 2010-05-01
I finally got this working, with a lot of hacking at stuff. I don't recommend doing any of this stuff unless you're comfortable with using bzr for installations, compiling code, and willing to hack at your system for a bit. If you want simple, reliable adium themes with no guesswork you probably just want Empathy. 

Cheers to h!v for all the real work on this.

**Edit: How-to for Lucid 10.04**
I've been asked how I got this working. Here are what I believe to be the important steps in Lucid (10.04). No guarantees on this as there are numerous failure points, but please respond if you have success with, or improvements to, this method.

[LIST=1]
[*]First install Pidgin and all the required libraries. These should all be available using default repositories installed with Lucid (i.e., in the Software Center). Install all of these: pidgin, libnotify-bin, libpurple-dev, pidgin-dev, libwebkit-dev, bzr (Bazaar Version Control System).
[*]Install h!v's *updated* shell script. If I understand correctly, the script's function is to handle installation of Adium styles, so that when you go download a new style it will install correctly. Use shell scripts at your own risk, of course, but this worked for me. Copy the script below, paste it into a new text file, and save it to your home directory (let's call it "adium-install.sh").
> **h!v said:**
> ```

#!/bin/bash
# Adium theme AdiumMessageStyle installer for Empathy
# Originally © 2009 Antono Vasiljev
# Licensed under the same terms as Empathy
# http://antono.info/en/165-install-adium-themes-to-empathy
# Changed by Vertlo Oraerk (did not work with directories containing spaces in the names)
# Changed by h!v from ubuntuforums to work with Pidgin+libwebkit and Notifications
# On Ubuntu you need to install libwebkit and libnotify-bin to get it working properly
# Further info on how to get working adium themes in Pidgin at http://www.webupd8.org/2009/05/pidgin-webkit-plugin-adium-conversation.html
# 02-12-2010 - Support for Adium 1.0 sound themes added. Hooha!
# Sound themes are supported in 2.6.x versions. If there's no file set for event, Pidgin falls to default sound file.
# 	IM
#Message Sent = send_im
#Message Received (New) = first_im_recv
#Message Received = im_recv
#	Chat
#Message Sent = send_chat_msg - you send a message in a chat 
#Message Received (Group Chat) =  chat_msg_recv - someone else sends a message in a chat 
#You Are Mentioned = nick_said - someone says your username in a chat
#	Status
#Contact Signed On = login
#Contact Signed Off = logoff
#Contact Joins = join_chat - a person enters a chat 
#Contact Leaves = left_chat - a person leaves a chat 
types[0]="<key>Message Sent</key>"
types[1]="<key>Message Received (New)</key>"
types[2]="<key>Message Received</key>"
types[3]="<key>Message Sent</key>"
types[4]="<key>Message Received (Group Chat)</key>"
types[5]="<key>You Are Mentioned</key>"
types[6]="<key>Contact Signed On</key>"
types[7]="<key>Contact Signed Off</key>"
types[8]="<key>Contact Joins</key>"
types[9]="<key>Contact Leaves</key>"
events[0]="im_sent"
events[1]="first_im_recv"
events[2]="im_recv"
events[3]="send_chat_msg"
events[4]="chat_msg_rec"
events[5]="nick_said"
events[6]="login"
events[7]="logoff"
events[8]="join_chat"
events[9]="left_chat"
# Creating a file

if [ -z $1 ]
then
    echo
    echo "Usage:"
    echo "`basename $0` adiumxtra://some.url.here/extra"
    echo
    exit 1
else
    TMPDIR=`mktemp -d`
    XTRAURL=`echo $1 | sed -e "s/^adiumxtra:/http:/"`
    DEST="$HOME/.purple/message_styles/"
    
    
    if [ ! -d $DEST ]
    then
        mkdir -v -p $DEST
    fi

    cd $TMPDIR
    notify-send "File this" \ "for Adium to be seems" --icon=pidgin
    wget --no-verbose -O xtra.zip $XTRAURL
    unzip -qq xtra.zip

    ls -d ./*.AdiumMessageStyle/ > themes_to_copy.lst
    ls -d ./*.AdiumSoundset/ > sound.lst
    num_bytes=`wc -c themes_to_copy.lst | sed 's# themes_to_copy.lst##'` 
    sound=`wc -c sound.lst | sed 's# sound.lst##'` 
    NAME=`cat themes_to_copy.lst | cut -f 2 --delimiter='.' | cut -f 2 --delimiter='/'`
    NAME_S=`cat sound.lst | cut -f 2 --delimiter='.' | cut -f 2 --delimiter='/'`

    if [ $num_bytes = 0 ]
    then
    	if [ $sound = 0 ]
    	then
        	notify-send "All here I found" \ "gibberish was" --icon=pidgin
        else
        	while read line_
        	do
        		if [ ! -d $line_/Sounds.plist ]
        		then
        		notify-send "Found I theme" \ " $NAME_S " --icon=pidgin
        		DEST="$HOME/.purple/themes/$NAME_S/purple/sound/"
        		if [ ! -d $DEST ]
			    then
			        mkdir -v -p $DEST
			fi
        		# Creating a file
			touch theme.xml
			echo -e "<?xml version=\"1.0\" encoding=\"UTF-8\"?> ">> $line_/theme.xml
			echo -e "<theme type=\"sound\" name=\"$NAME_S\">" >> $line_/theme.xml
			while read line
			do
				if [ "$line" = "<key>Info</key>" ]
				then
					read line
					inf=`echo $line | sed -e "s/<string>//" | sed -e "s/<\/string>//"`
					echo -e "\t<description>$inf</description>" >> $line_/theme.xml
				fi
				for ((j=0; j<=9; j++))
				do
					if [ "$line" = "${types[j]}" ]
					then
						read line
						file=`echo $line | sed -e "s/<string>//" | sed -e "s/<\/string>//"`
						echo -e "\t<event name=\"${events[j]}\" file=\"$file\"/>" >> $line_/theme.xml
					fi		
				done
			done < $line_/Sounds.plist
			echo -e "</theme>" >> $line_/theme.xml
			echo cp -r \'$line_\'* $DEST | sh			
			else
				notify-send "Use I force could" \ "none effect, that made" --icon=pidgin
			fi
        	done < sound.lst
        fi        
    else
        while read line 
        do
            echo cp -r \'$line\' "$DEST" | sh
        done < themes_to_copy.lst
        echo
        notify-send "Installed I" \ " $NAME for you " --icon=pidgin
    fi
    rm -r xtra.zip    
    rm -r $TMPDIR
fi
exit 0

```
[*]We're now assuming that the following file exists: /home/<username>/adium-install.sh. In a terminal window enter these commands (same as in h!v's original post). Make sure you substitute the appropriate value for <username>:
```

cd /home/<username>
chmod 755 adium-install.sh
gconftool-2 -t string -s /desktop/gnome/url-handlers/adiumxtra/command "/home/<username>/adium-install.sh %s"
gconftool-2 -t bool -s /desktop/gnome/url-handlers/adiumxtra/enabled true
gconftool-2 -t bool -s /desktop/gnome/url-handlers/adiumxtra/needs_terminal false

```
[*]Your system should now be configured to automatically handle installation of adium themes. Time for the fun part.
[*]Install the [pidgin-webkit plugin with karmic fixes]("https://code.launchpad.net/~spoidar/pidgin-webkit/karmic-fixes"). To install this, enter the following commands in a terminal window to download and compile the plugin:
```

cd /home/<username>
bzr branch lp:~spoidar/pidgin-webkit/karmic-fixes
cd karmic-fixes
make
```
[*]There should now be a file called "webkit.so" inside /home/<username>/karmic-fixes/. Locate that file and copy it into the pidgin plugins directory, which is /home/<username>/.purple/plugins. If there is no plugins directory inside .purple, create one and then copy webkit.so into it.
[*]Download an adium theme [from here]("http://www.adiumxtras.com/index.php?a=search&cat_id=5") (Rentoo is nice and seems to work well). If the shell script above is working properly, you should just be able to click "Install" on the website and it'll magically install the theme. If it worked properly, you should have a folder called "message_styles" in your .purple directory with some stuff in it (e.g., rentoo.AdiumMessageStyle). If that didn't work, you might have to manually download and unzip the theme and place the contents into /home/<username>/.purple/message_styles.
[*]Fire up Pidgin, go to Tools > Plugins, and enable "Webkit message styles". Click "Configure Plugin" and select a theme. Test it out. If you're lucky, you'll have sexy Adium-style messaging now.
[/LIST]

Cheers,
Jeremy

[IMG]http://state.tc/imgs/adium-example.png[/IMG]

---

### Post by xord on 2010-05-02
step 5
cd karmic-fixes

step 6
place the webkit.so in /home/<username>/.purple/plugins

---

### Post by c00lwaterz on 2010-05-02
is adium a theme/style only for IM messengers? or is it a messenger?(in google it is messenger)

---

### Post by daqron on 2010-05-03
> **xord said:**
> step 5
cd karmic-fixes

step 6
place the webkit.so in /home/<username>/.purple/plugins
Fixed -- thanks. Did you get it to work?

---

### Post by xord on 2010-05-03
yeap, but only renkoo works perfect. others make my pidgin crash

---

### Post by R2D2! on 2010-05-04
> **c00lwaterz said:**
> is adium a theme/style only for IM messengers? or is it a messenger?(in google it is messenger)
Adium is an IM client, but it uses Webkit-based themes that can be installed in Empathy and, with this plugin, in Pidgin.

---

### Post by h!v on 2010-05-06
Hello

Thanks guys for that.

Just to clarify.

Themes are being downloaded to temporary directory and unpacked into 
```
.purple
``` with .message_styles at the end.

```

/home/<username>

```
is equivalent of
```

~/

```
Command 
```

cd

```
will get you to your home folder.

Renkoo theme still unbeatable.
Great themes that still work for me are 
[LIST]
[*]Pushpin
[*]Ravenant
[*]iPhone
[*]Cinematic
[*]GoneDark ( a bit lens flare era *cough*)
[/LIST]

Real pitty tho, with these Karmic fixes 1337 theme got broken. Ehh.

Cheers.

EDIT: Updated version is up.

---

### Post by daas88 on 2010-05-10
It worked like a charm, thanks! But you have to correct some parts of the post where it says ".pidgin" instead of ".purple"

---

### Post by daqron on 2010-05-14
> **daas88 said:**
> It worked like a charm, thanks! But you have to correct some parts of the post where it says ".pidgin" instead of ".purple"
Oops, thought I'd fixed them all. Should be good now.

---

### Post by TorontoStorm on 2010-05-15
I followed the guide, and the adium theme works sometimes. I'm not able to fully identify when it works, but it seems to be when I initiate the conversation with a contact, and not when they message me first. It also doesn't work if I close the conversation window, then open it again. Only a restart of Pidgin gets the adium theme back once that happens.

The cause may be an updated Pidgin (to 2.7), but I'm not too sure, since I never tried this before in 2.6. Anyone else having this issue? And, any suggestions on how to fix it?

---

### Post by h!v on 2010-05-19
It might be the 2.7. I have not yet updated to this version. 
It also might be libwebkit itself, as I saw it got upgraded lately.

I'll update guide if I find solution or at least cause of it.


EDIT:
TorontoStorm
You might want to add repo from [https://launchpad.net/~webkit-team/+archive/ppa]("https://launchpad.net/~webkit-team/+archive/ppa")webkit-team listed on first  page and upgrade.
I believe it would do too.
```
sudo add-apt-repository ppa:webkit-team/ppa
```
Theme Renkoo works for me without any problems in 2.7.  Keep in mind **not** all themes will work.

---

### Post by TorontoStorm on 2010-05-21
I already had the webkit ppa in my repository. 

I identified the source of my problem, and a temporary solution it it. If "Hide new conversations" is set "Always" or "When Away", if someone messages you, and Pidgin hides the window until you go to open it, it reverts to normal conversation rendering (not webkit) for the rest of the time pidgin is open, and only a restart will put it back to using webkit. The obvious workaround for now is to set that setting as "Never".

Also, in the Renkoo theme, I cannot tell when the other user is typing, it does not show me in any way. Is this a known bug and is there a solution?

---

### Post by h!v on 2010-05-22
> **TorontoStorm said:**
> 
I identified the source of my problem, and a temporary solution it it. If "Hide new conversations" is set "Always" or "When Away", if someone messages you, and Pidgin hides the window until you go to open it, it reverts to normal conversation rendering (not webkit) for the rest of the time pidgin is open, and only a restart will put it back to using webkit. The obvious workaround for now is to set that setting as "Never".

Also, in the Renkoo theme, I cannot tell when the other user is typing, it does not show me in any way. Is this a known bug and is there a solution?

Thanks mate!
I actually had this setting as "never".

As for typing thing. 
I have yet to find theme that supports it, which leads me to believe Pidgin and Adium handle this other ways or it's webkit plugin problem.
If we talk about Adium/Pidgin, theme it self could get modified and we're home. If it's plugin, we are out of luck as development stopped some time ago.

---

### Post by kltpzyxm on 2010-05-27
Apart from renkoo, none of the other themes are working for me. Did everything exactly as suggested by Daqron for Ubuntu Lucid Lynx 10.04.

The Renkoo theme has installed perfectly, but none of the others have. I tried Fiat and Candybars apart from Pushpin, Ravenant, iPhone, Cinematic and GoneDark - which h!v said are working for him.

Any idea what could be going wrong?

---

### Post by h!v on 2010-05-27
> **kltpzyxm said:**
> Apart from renkoo, none of the other themes are working for me. Did everything exactly as suggested by Daqron for Ubuntu Lucid Lynx 10.04.

The Renkoo theme has installed perfectly, but none of the others have. I tried Fiat and Candybars apart from Pushpin, Ravenant, iPhone, Cinematic and GoneDark - which h!v said are working for him.

Any idea what could be going wrong?

What Pidgin version?

Try restarting message window. If you switch different between variations of theme it's ok, but between themes itself it always goes wrong. This might help.
Other. Try webkit-ppa.

---

### Post by daas88 on 2010-05-27
Other themes don't work for me either, just renkoo... Could you tell me the details to add the webkit ppa?

---

### Post by kltpzyxm on 2010-05-28
@h!v Thanks for the reply. I was on 2.6.6 and it wasn't working. I just upgraded and am on the latest v2.7.0 and have updated the webkit too.

Renkoo is working fine, but every other theme either isn't displayed right or just crashes pidgin altogether.

What could be going wrong? My only complaint with pidgin is the chat themes because i'd really like something similar to the Fiat adium theme. Any help would be appreciated.

---

### Post by BuZZ-dEE on 2010-06-12
> **daqron said:**
> ```

cd /home/<username>
bzr branch lp:~spoidar/pidgin-webkit/karmic-fixes
cd karmic-fixes
make
```
[*]There should now be a file called "webkit.so" inside /home/<username>/karmic-fixes/. Locate that file and copy it into the pidgin plugins directory, which is /home/<username>/.purple/plugins. If there is no plugins directory inside .purple, create one and then copy webkit.so into it.

thx, works for me :) but why no
```

make install

```
?

---

### Post by daqron on 2010-06-18
> **BuZZ-dEE said:**
> thx, works for me :) but why no
```

make install

```
?
Awesome! I think it's just 'make' because you're only compiling a single plugin file that you'll add from its current location, as compared to installing an application that requires binary executables to be placed in other locations on your system. That's my best guess.

---

### Post by h!v on 2010-06-18
Sweet Jabeezus.

Long time, it took me.
1. Webkit details are on first page. Obviously.
2. As for Fiat theme. If you really want themes, hence first sentences in this thread. It's modified script dedicated to Empathy. If you really want it, I'd suggest trying that app out.

As for 
```

make

```
Install part is not speciefied within makefile. Considering these are just libraries we are compiling, that part is not there "by default".

Please bare in mind. Webkit plugin got dropped. Sadly. I thought about picking it up, but that's not going to happen within near future.
Best bet is to request Pidgin's team to fork it and work on it in default branch. To be honest, I don't see why it's not happening since Empathy and Adium, Pidgin's OSX cousin, did take Webkit under their hood.

Cheers.

---

### Post by BullButcher on 2010-06-23
For Ubuntu 10.04 Lucid ( should also work in Ubuntu 9.10 Karmic Koala!)
Easy way to install and run this theams.

Do not run "adium_for_pidgin" with "sudo" as the gconf settings won't work! Instead run it as a normal user (just paste the commands exactly as I wrote them) and when asked, enter your password.

```
wget http://webupd8.googlecode.com/files/pidgin_adium2 && chmod +x pidgin_adium2
./pidgin_adium2
```

*[COLOR="Red"][SIZE="1"]Remember, it's always advisable to check the script code before running it![/SIZE][/COLOR]*


1. After the script finishes setting everything up, restart Pidgin. Then go to Tools > Plugins and enable the "WebKit Message Styles" plugin.


2. Now everything is set up so all you have to do is install some new themes. Go to the Adium themes website and click the "Install" link next to an Adium theme you want to install. 
(not all will work - a list of working themes can be found[ HERE]("http://live.gnome.org/Empathy/Themes"))

Important: for me, clicking the "Install" link only works in Chrome/Chromium so that might also be the case for you. Also, some Adium themes won't work! I only tried 2 themes and they both worked so you can try them to make sure everything is ok: Renkoo and Candybars.


3. To change between the installed themes, go to Tools > Plugins, select the "WebKit Message Styles" plugin and click the "Configure plugin" button under it.


If no themes are displayed in Pidgin, manually download the themes from the Adium website and extract them into the ~/.purple/message_styles folder.

---

### Post by Kreisverkehr on 2010-07-01
Hey guys,

i really want to use some new themes with my pidgin, so i followed this guide.

but there is one main problem, wen i try to activate the plugin Pidgin crashes.
I tried everything from installing new themes to recompiling webkit.

I'm using Ubuntu 10.04 an Pidgin 2.6.6

Is there someone who had the same Problem an is able to help me?


Kreiverkehr

---

### Post by h!v on 2010-07-01
> 
Hey guys,

i really want to use some new themes with my pidgin, so i followed this guide.

but there is one main problem, wen i try to activate the plugin Pidgin crashes.
I tried everything from installing new themes to recompiling webkit.

I'm using Ubuntu 10.04 an Pidgin 2.6.6

Is there someone who had the same Problem an is able to help me?


Kreiverkehr

I remember 2.6.6 acting little funky(still usable) with webkit libaries from launchpad. Have you tried using latest Pidgin? PPA info is on main website.

Cheers.

---

### Post by cedriczg on 2010-09-08
Thanks daqron. This finally worked and did the trick. Now I have Renkoo Adium style on my Pidgin.

---

### Post by daqron on 2010-10-26
> **h!v said:**
> Plugin does not work on 64 bit systems, which might be a problem.
I can confirm that this is a problem. I just got a new 64-bit system and all that awesome hax0ring to make Adium work does me no good now. Sad times.

---

### Post by h!v on 2010-10-26
> **daqron said:**
> I can confirm that this is a problem. I just got a new 64-bit system and all that awesome hax0ring to make Adium work does me no good now. Sad times.

I'd assume you did since Karmic and up requires it, but did you try to compile it?
If it doesn't work, it is sad times then. It's hands down the best plugin for Pidgin so far in my opinion.
Sad that support for it didn't pick up again.

---

### Post by daqron on 2010-10-31
> **h!v said:**
> did you try to compile it?
Yup. There's a bit of a discussion about it over at [Launchpad]("https://answers.launchpad.net/pidgin-webkit/+question/116522"). Looks like someone got it to work by editing the source code. Right now I'm using Empathy instead, and [hacking at the contact list]("http://j.modjeska.us/?p=167&preview=true"). When I get bored with that I might waste some more time on Pidgin.

---

### Post by sezal on 2011-03-11
works on ubuntu 10.10, but it's not compatible with history plugin (shows recent messages) :(

---

### Post by aerotux on 2011-12-13
Hello, this seems to be an old thread, but it's the best place I found to customize Pidgin message window.

I followed instructions, complied the library, move it to the plugin dir. The plugin appears in the list, but when clicking to enable it, pidgin crash.

```
Pidgin 2.9.0 has segfaulted and attempted to dump a core file.
This is a bug in the software and has happened through
no fault of your own.

If you can reproduce the crash, please notify the developers
by reporting a bug at:
http://developer.pidgin.im/simpleticket/

Please make sure to specify what you were doing at the time
and post the backtrace from the core file.  If you do not know
how to get the backtrace, please read the instructions at
http://developer.pidgin.im/wiki/GetABacktrace
Aborted
```

Any ideas? Maybe a link to a newer tutorial/discussion?

Thanks,
Jose

---

