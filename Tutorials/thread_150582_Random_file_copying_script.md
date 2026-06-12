---
title: "Random file copying script"
date: 2006-03-26
forum: Tutorials
---

### Post by lapsey on 2006-03-26
edit: I made a minor change to how the script searches for files, which should speed things up a bit. Also renamed the script to a more general-purpose name (randomcopy)
A more ipod shuffle specific modification is in the next post. The one here can be used with any old device.

---------------

This will show you how to copy a number of random files from selected directories into the folder of your choice. You can use this to fill cd-roms, dvd-roms, ipod shuffles, palm pilots, etc etc.
Currently it is set up to only look for files with the extensions mp3, aac or aa. With a tiny bit of modification (see the 'variables' section in this post) you can make the script randomly copy *any* type of file -pending file extension- of practically any size. Providing the target device doesn't require you to reconvert files (like in a psp) or use any pointlessly complicated transfer software like itunes, there are many uses for this script.



*Remember, it's totally random so it won't remember your favourite tracks or anything like that. I don't recommend this as a solution to software such as rhythmbox or gtkpod, but until those work properly with my ipod shuffle this seems to be the best alternative.
Personally I recommend using the [iPod shuffle Database Builder](http://shuffle-db.sourceforge.net/) python script in order to point your ipod shuffle to all the files on it. It's really really easy to run.

And now for some informative stuff stolen from that gnome nut, ardchoille:
> **Nautilus script explanation**
A nautilus script is just an executable shell script (usually bash) that is placed in a special scripts directory so that the Nautilus graphical shell can find it. This is a really neat function of Nautilus, because it allows you to extend the functionality the the file browser to do just about anything. Scripts are invoked by selecting a file or group of files, and right-clicking with the mouse, to bring up a 'Context' menu. One of the options of this menu is the 'Scripts' submenu (this option only appears once you have at least one script in the scripts directory), which allows you to select a script to invoke on the selected files.

For a script to appear on the script menu, it must:
1. be placed in your scripts directory (~/.gnome2/nautilus-scripts), and
2. be executable (with chmod a+x filename)

If you place an executable script in your scripts directory, its name will not necessarily appear on the scripts menu immediately. You first must visit the scripts directory with Nautilus - which can be done using the last option in the scripts menu. Once the directory is visited, Nautilus will know about which scripts you have, and you will be able to use them.

**installation and use**

1) copy and paste the code below into a file called "randomcopy" (or whatever you  like!) under ~/.gnome2/nautilus-scripts/ and chmod it as detailed above
2) right-click any folder (the folder icon, not when you are in the folder itself) and select "scripts > randomcopy" from the menu.
3) when prompted, select any folders with files of the extensions as listed in the script. Maybe one day I will make this more interactive.
4) the script will then search quickly to see how many megabytes of appropriate files there are. it will then ask you how much you want to copy (you are limited only by how much space there is on the device you are copying to).
5) let it run! It only tends to take as long as it does to transfer files from one place to another. Of course, as with all programs, your mileage may vary.

**Variables**

The variables in the script may interest you as well:

**minFS** is the smallest and **maxFS** is the largest you want a file to be when copying.
In this case i have them at 0.5MB and 40MB respectively. Anything larger or smaller will be ignored during deepscan.

If you want the script to handle more file types than this, you can add the appropriate extensions to the **searchPattern** variable (7th line down)

```
#!/bin/bash
# randomcopy 0.6
# a general-purpose script for copying random files

bInMB=1048576
window_title="Randomcopy"
window_icon="/usr/share/icons/gnome/16x16/devices/gnome-dev-ipod.png"
searchPattern=".*\.\(aac\|aa\|mp3\)"

minFS=$(($bInMB/2))
maxFS=$(($bInMB*40))

######################################################################

O=$IFS IFS=$'\n' tgtPaths=(`echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"`) IFS=$O

for tgtPath in "${tgtPaths[@]}" ; do
	
	if [ -d "$tgtPath" ] ; then # startof if target directory
		
		# Select....
		O=$IFS IFS=$'\n' srcPaths=(`zenity --file-selection --directory --multiple --separator=$'\n' --title="Select source directories" --window-icon="$window_icon"`) IFS=$O

		# Searching.. quickscan
		(
		echo "10"
		for srcPath in "${srcPaths[@]}" ; do
		#	=$(($srcB+$(echo `dosomething` | bc)))
			srcB=$(($srcB+$(echo `find "$srcPath" -type f -size +$(($minFS-1))c -size -+$(($maxFS+1))c -iregex $searchPattern -print0 | xargs -0 stat -c %s+ ; echo 0` | bc)))		
		done
		echo "100"

		# How many?....
		tgtBFree=$((`stat -f -c %f "$tgtPath"`*`stat -f -c %s "$tgtPath"`)) 
	 	if [ $srcB -lt $tgtBFree ]; 
			then dialog_entry_text=$(($srcB/$bInMB))
			else dialog_entry_text=$(($tgtBFree/$bInMB))
		fi
		remSrcB=$(($bInMB*`zenity --entry --text="$(($srcB/$bInMB))MB of files $(($minFS/$bInMB))-$(($maxFS/$bInMB))MB found. $(($tgtBFree/$bInMB))MB free on device of /$(echo "$tgtPath" | sed 's/^.*\///'). How much to copy?" --entry-text="$dialog_entry_text" --title="$window_title" --window-icon="$window_icon"`))
		initSrcB=$remSrcB

		if [ $srcB -gt 0 ]; then # startof if not 0 Bytes
		
			# Searching.... deepscan
			(
			echo "10"
			for srcPath in "${srcPaths[@]}" ; do
				O=$IFS IFS=$'\n' tempSrcF=( `find "$srcPath" -type f -size +$(($minFS-1))c -size -+$(($maxFS+1))c -iregex $searchPattern` ) IFS=$O
				remSrcF=( "${remSrcF[@]}" "${tempSrcF[@]}" )
			done
			initSrcF="${#remSrcF[@]}"
			echo "100"

			# Copying....
			(
			while [ ${#remSrcF[@]} -gt 0 ] && [ $remSrcB -ge $minFS ] ; do 
				random=$(($RANDOM % $initSrcF)) 
				if [ -n "${remSrcF[$random]}" ] ; then # if element is not empty
					srcFS=$((`stat -c %s "${remSrcF[$random]}"`))
					if [ $srcFS -le $remSrcB ] && ! [ -e "$tgtPath/$(echo "${remSrcF[$random]}" | sed 's/^.*\///')" ] ; then # last condition prevents overwrite
						cp -i --reply=no "${remSrcF[$random]}" "$tgtPath"
						remSrcB=$(($remSrcB-$srcFS)) # post-copy!
						srcCpB=$(($srcCpB+$srcFS))
					fi
					unset remSrcF[$random] # make element empty
				fi
				echo $((100*($initSrcB-$remSrcB)/$initSrcB))
			done
			echo "100"

			zenity --info --text="$(($srcCpB/$bInMB))MB successfully copied to $tgtPath" --title="$window_title" --window-icon="$window_icon"

			) | zenity --progress --auto-close --percentage="$((100*($initSrcB-$remSrcB)/$initSrcB))" --text="copying $(($initSrcB/$bInMB))MB to $(echo "$tgtPath" | sed 's/^.*\///').." --title="$window_title" --window-icon="$window_icon"
			# endof copying pipe

			) | zenity --progress --pulsate --auto-close --percentage=0 --text="deepscanning selected folders.." --title="$window_title" --window-icon="$window_icon"
			# endof deepscan find pipe
		
		fi # endof if not 0 B
	
		) | zenity --progress --pulsate --auto-close --percentage=0 --text="quickscanning selected folders.." --title="$window_title" --window-icon="$window_icon"
		# endof quickscan find pipe
	
	fi # endof if target directory

done
# endof for tgtPath
exit

```

if you encounter any problems please let me know.

---

### Post by dudus on 2006-04-25
This was very usefull for me. I've been looking for something like this for some weeks. Every ipod supporting app seems to completely forget about ipod shuffle

---

### Post by lapsey on 2006-05-10
I mentioned earlier how the script could be used with the ipod shuffle. It has since occurred to me that 99.9% of people that use the shuffle on linux would use the [iPod shuffle Database Builder](http://shuffle-db.sourceforge.net/) script.
I also dislike waiting for prompts, so i have included a variable (useall) that allows the script to automatically use all free space, rather than prompt you to enter a number.

Most significant is that this script removes any leading non-alphabetic characters from the filenames. This is so that the ipod shuffle db builder can group files together better. For example:
```

01.mp3
02 - 2802.3478.mp3
02. elvis - jailhouse rock.mp3
03 - gnr - don't cry.mp3
07_-_talking heads_-_girlfriend is better.mp3
09.aphex twin - digeridoo.mp3
12.vbr.mp3
15, elvis, in the ghetto.mp3
aphex twin - come to daddy - 05 - bucephalus.mp3
```
becomes
```

01.mp3
02 - 2802.3478.mp3
aphex twin - come to daddy - 05 - bucephalus.mp3
aphex twin - digeridoo.mp3
elvis - jailhouse rock.mp3
elvis, in the ghetto.mp3
gnr - don't cry.mp3
talking heads_-_girlfriend is better.mp3
vbr.mp3

```

obviously it will benefit you more if you have a consistent mp3 naming scheme :cool:


installation and usage:

1) Save the [iPod shuffle Database Builder](http://shuffle-db.sourceforge.net/) script to the root of the shuffle.

2) Save this script also to the root of the shuffle and make executable (as mentioned in the first post)

3) Edit the script so the variables such as rebuild_db to point to different locations if you wish. I make use of gnome's habit of hiding files with a period at the start, so I have ".rebuild_db.py" and ".randomcopy" at the pod root. In order to run the script, I keep a launcher in the ipod root with the command **bash /media/ipod/.randomcopy**

[[IMG]http://img220.imageshack.us/img220/848/randomcopy013df.jpg[/IMG]](http://imageshack.us)

4) Make whatever changes you wish to the other variables so the script operates the way *you* want it, for example commenting out **useall** if you like

5) run it, select the folders you want to search
[[IMG]http://img208.imageshack.us/img208/3395/randomcopy025bp.jpg[/IMG]](http://imageshack.us)

and wait for the script to find and copy your files. 
[[IMG]http://img154.imageshack.us/img154/5488/randomcopy037dt.jpg[/IMG]](http://imageshack.us)

Once done, the script will pass you the results of the ipod shuffle database builder.
[[IMG]http://img217.imageshack.us/img217/1371/randomcopy049fk.jpg[/IMG]](http://imageshack.us)


6) Unmount and Enjoy!

```
#!/bin/bash
# randomcopy 0.6b
# a general-purpose script for copying random files 
# modified specifically for the ipod shuffle and the ipod shuffle database builder script

bInMB=1048576

window_title="Randomcopy 0.6b"
window_icon="/usr/share/icons/gnome/16x16/devices/gnome-dev-ipod.png"
tgtPath="/media/ipod/music" # where you wish to copy your music files to. if it doesn't exist the script will create it
dbPath="/media/ipod/iPod_Control" # where the itunes db is kept
rebuild_db="/media/ipod/.rebuild_db.py" # where the ipod shuffle database builder script is kept: this should always be on the root of the ipod

redundancy=$(($bInMB/2)) # 1/2 MB is about enough space for the ipod shuffle database, overall
searchPattern=".*\.\(aac\|aa\|mp3\)" # file extensions to copy
minFS=$(($bInMB/2)) # smallest filesize to copy, in bytes
maxFS=$(($bInMB*40)) # largest filesize to copy, in bytes

useall=yes # comment-out this variable if you wish to be prompted for how many MB of files to copy, otherwise it will automatically use whatever space is left

######################################################################

if ! [ -e "$tgtPath" ] ; then mkdir "$tgtPath" ; fi

dbFS=`du "$dbPath" -b -s | grep -o '^[0-9]*'`
if [ $redundancy -gt $dbFS ] 
	then redundancy=$(($redundancy-$dbFS))
	else redundancy=$dbFS
fi 

tgtBFree=$(((`stat -f -c %f "$tgtPath"`*`stat -f -c %s "$tgtPath"`)-$redundancy))

O=$IFS IFS=$'\n' srcPaths=(`zenity --file-selection --directory --multiple --separator=$'\n' --title="Select source directories" --window-icon="$window_icon"`) IFS=$O

(

echo 10
for srcPath in "${srcPaths[@]}" ; do
	srcB=$(($srcB+$(echo `find "$srcPath" -type f -size +$(($minFS-1))c -size -+$(($maxFS+1))c -iregex $searchPattern -print0 | xargs -0 stat -c %s+ ; echo 0` | bc)))		
done
echo 100

if [ $useall ]
	then 
		if [ $srcB -lt $tgtBFree ]
			then remSrcB=$srcB
			else remSrcB=$tgtBFree
		fi
	else 
		if [ $srcB -lt $tgtBFree ]
			then dialog_entry_text=$(($srcB/$bInMB))
			else dialog_entry_text=$(($tgtBFree/$bInMB))
		fi
		remSrcB=$(($bInMB*`zenity --entry --text="$(($srcB/$bInMB))MB of files $(($minFS/$bInMB))-$(($maxFS/$bInMB))MB found. $(($tgtBFree/$bInMB))MB free on device of /$(echo "$tgtPath" | sed 's/^.*\///'). How much to copy?" --entry-text="$dialog_entry_text" --title="$window_title" --window-icon="$window_icon"`))
fi
			
initSrcB=$remSrcB

if [ $srcB -gt 0 ] ; then # startof if not 0 Bytes found on quick scan

	(

	echo 10
	for srcPath in "${srcPaths[@]}" ; do
		O=$IFS IFS=$'\n' tempSrcF=( `find "$srcPath" -type f -size +$(($minFS-1))c -size -+$(($maxFS+1))c -iregex $searchPattern` ) IFS=$O
		remSrcF=( "${remSrcF[@]}" "${tempSrcF[@]}" )
	done
	initSrcF="${#remSrcF[@]}"
	echo 100

	(

	while [ ${#remSrcF[@]} -gt 0 ] && [ $remSrcB -ge $minFS ] ; do 
		random=$(($RANDOM % $initSrcF)) 
		if [ -n "${remSrcF[$random]}" ] ; then # if element is not empty
			tgtFN_np=$(echo "${remSrcF[$random]}" | sed 's/^.*\///') # strips leading path
			if [[ $tgtFN_np =~ '[a-zA-Z].*\.[^.]*$' ]] ; then tgtFN_np=$(echo "$tgtFN_np" | sed 's/^[^a-zA-Z]*//') ; fi # strip all nonalpha char before last extn
			srcFS=$((`stat -c %s "${remSrcF[$random]}"`))
			if [ $srcFS -le $remSrcB ] && [ $((`expr length "$(echo "$tgtPath" | sed 's/^.*\///')/$tgtFN_np"`)) -le 255 ] && ! [ -e "$tgtPath/$tgtFN_np" ] ; then # first condtn checks for space to copy, second condtn checks path not too long for ipod db rebuilder (255), third condition prevents overwrite
				cp -i --reply=no "${remSrcF[$random]}" "$tgtPath/$tgtFN_np"
				remSrcB=$(($remSrcB-$srcFS)) # post-copy!
				srcCpB=$(($srcCpB+$srcFS))
			fi
			unset remSrcF[$random] # make element empty
			echo $((100*($initSrcB-$remSrcB)/$initSrcB))
		fi
	done
	echo 100

	python "$rebuild_db" -l | zenity --text-info --title="iPod shuffle Database Builder" --window-icon="$window_icon"	

	) | zenity --progress --auto-close --percentage=0 --text="copying $(($initSrcB/$bInMB))MB to $(echo "$tgtPath" | sed 's/^.*\///').." --title="$window_title" --window-icon="$window_icon"

	) | zenity --progress --pulsate --auto-close --percentage=0 --text="deepscanning selected folders.." --title="$window_title" --window-icon="$window_icon"

fi

) | zenity --progress --pulsate --auto-close --percentage=0 --text="quickscanning selected folders.." --title="$window_title" --window-icon="$window_icon"

exit

```

again if there are any problems or changes I should look into please post about them

---

### Post by jackkerouac on 2006-08-19
Dude, you rock!

---

### Post by aysiu on 2006-11-19
This sounds like a very cool script. If I get too lazy to manually drag songs to my Sandisk player, I may give this a go.

Thanks for creating this!

---

### Post by Ago12 on 2006-11-19
> **aysiu said:**
> This sounds like a very cool script. If I get too lazy to manually drag songs to my Sandisk player, I may give this a go.

Thanks for creating this!

Will it work on an Iaudio (mounted in UMTS) please? :)

Obviously, I won't need the db builder :d

---

### Post by lapsey on 2006-11-20
> **Ago12 said:**
> Will it work on an Iaudio (mounted in UMTS) please? :)

Obviously, I won't need the db builder :d

if the device's storage can be mounted to a location on the file system, (like /media/ipod/), then the ipodified script (0.6b) should work fine

to stop the db_builder from being run, **remove** the line 

```
python "$rebuild_db" -l | zenity --text-info --title="iPod shuffle Database Builder" --window-icon="$window_icon"	
```

from randomcopy **0.6b**

the variables you may need to change (tgtPath, redundancy) are explained in the script itself.

---

### Post by MorphWVUtuba on 2006-12-10
:mrgreen: Dude.  Awesome.  Wanted something like this for a long time.  Thanks a bunch.

---

### Post by ggulik on 2007-01-18
This script is exactly what I wanted!
Before I tried it I wanted to make sure it works on the new V2 "clip" Shuffles.  Has anyone tried it yet?

---

### Post by justinmiller87 on 2009-10-15
I'm obviously way late to the party here. Is there a way to make this copy over a specific number of random files? As dumb as it sounds, I am 113 songs away from hitting 8000 over on last.fm and I wanted to be able to drag over 113 songs into my iPod and toss it on shuffle to be able to hit the milestone.

---

### Post by momist on 2009-11-07
Hi there,
If anyone is still reading this thread, do you have any idea why it now doesn't work in Karmic (9.10)?   The result I'm getting is that the script runs through and completes, but there's _nothing_ copied at all.  I've not changed anything since I used it in Jaunty where it worked fine.

Mine is a "clean install" of Karmic in Ext4, but with the old "home" still on an Ext3 partition, and the music on a separate Ext2 partition.  The breakage seems to effect only the "deep scanning folders" process, which should take several seconds (10 days worth of music!) but now happens in about 2 seconds.

I've tried to read the script, but can't see what may be wrong.

---

### Post by momist on 2009-11-16
> **momist said:**
> I've tried to read the script, but can't see what may be wrong.

Well . . .  here's what I found out:
The line that does the copying consists of ```
cp -i --noreply "${remSrcF[$random]}" "$tgtPath"
```
In this, the "--noreply" was not coloured in my gedit box, as if it was not recognised.  Reading the man entry for "cp" showed that -L will follow symlinks in the source directory - which might be part of the problem.  So I changed the script to read: ```
cp -i -L "${remSrcF[$random]}" "$tgtPath"
```
and now it works OK.

HTH someone!

---

### Post by Mandler on 2011-05-01
@lapsey: Wanted you to know that your gift keeps on giving. Years later, I just stumbled upon it. It's great and does exactly what I need. Thank you.

@momist: Thank you for taking the time to track down and post the cp solution.

---

### Post by bennyto on 2011-12-22
Hello ... sorry for the big up, but I'm wondering why the script doesn't work for me ???

I'm using Thunar so I just added the script in Edition > "Personalized Actions" (I don't know if it written like this, I have it in French ^^) and I can see the script when I right-click a folder. But nothing goes on when I select the script....

Any idea ?

---

### Post by momist on 2011-12-22
Hello bennyto,
I'm not at all familiar with Thunar, as I have so far stayed on Ubuntu 10.04 Lucid Lynx, and the script still works OK for me there.  I'm waiting for 12.04 LTS version before I upgrade, and suspect that the script will be broken again then.  
It may help others to find your problem if you say what version of Ubuntu you are currently running?

Edit: Sorry, I see it's 9.10 in your profile.  I hope you find a solution.

---

### Post by bennyto on 2011-12-27
> Sorry, I see it's 9.10 in your profile.  I hope you find a solution. 	

Hum actually due to account limitation I can't change this. I'm running CrunchBang Linux Stalter wich is also debian-based (Squeeze) (it used to be Ubuntu based but since its last version it is not the case anymore)

I hope someone has an idea about it, if no I'll ask on Crunbang's forum :)

cheers

---

### Post by momist on 2011-12-27
OK bennyto,

It's some time ago now, but I think the penny dropped for me when I tried running each line of the script (it's not very long) in a terminal.  Or maybe that was some other one I was wrestling with.

Anyway, reading my original posts, I saw that one line in the code-aware text editor stood out in a different colour, because it was not recognised, maybe.

---

### Post by LaptopU on 2012-04-29
Sadly it doesn't work on 12.04 pangolin, I have no idea how to work well with scripts so cannot see why it stopped working - is this being worked on please?

---

### Post by momist on 2012-04-29
> **LaptopU said:**
> Sadly it doesn't work on 12.04 pangolin, [snip] - is this being worked on please?

Hmm.  I only installed precise pangolin yesterday, and I haven't tried that script yet.  To be honest, I rarely use it now, as I don't have the need since I retired and get my music staight from the PC mostly.  My Android phone can get my favourite music channel off t'internet when I'm out and about, so I use the Sansa even less.

I'll have a go in the next week, and report how I get on with it.  I doubt the original author is likely to work on it.

---

### Post by momist on 2012-04-29
Well that was too easy.  It simply still works OK for me - YMMV.  :guitar:

Just a note about usage.  I'm very new to unity (I stayed with 10.04LTS until yesterday) and I'm still finding my way around.  I can't say that I like it yet, but I'll not rush to judgement.

RandomFill works for me if I do this:-
Insert a USB stick, or music player that looks like one.  This should open nautilus showing the contents.
If you want music in a folder (directory) on there, create the folder.  
If not, to fill the whole memory or write to the root, **go up one level** so that you can see the memory device as a folder.
Point at the folder and right click, this should offer the script.  
Select the script, and it asks for the **source** directory.  
Navigate to the source, your store of music, and select that.
It should now ask you "how much" in MB.  

I hope that is clear, and not too patronising.  I know the interface lacks any polish, and if one step is wrong there's no feedback, just that nothing happens.

Since it works for me, I don't think I can help any further, but please let me know how you get on.

---

### Post by LaptopU on 2012-04-30
Ahahaha, it's working!  I missed out a vital part - I was trying to sync to a local directory testing it out.  As soon as I mounted a USB device the script ran, said it copied but it didn't.  I went back to your post in 2009 and tweaked the cp -i line, it now works superbly.
```
#!/bin/bash
# randomcopy 0.6
# a general-purpose script for copying random files

bInMB=1048576
window_title="Randomcopy"
window_icon="/usr/share/icons/gnome/16x16/devices/gnome-dev-ipod.png"
searchPattern=".*\.\(aac\|aa\|mp3\)"

minFS=$(($bInMB/2))
maxFS=$(($bInMB*40))

######################################################################

O=$IFS IFS=$'\n' tgtPaths=(`echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"`) IFS=$O

for tgtPath in "${tgtPaths[@]}" ; do
	
	if [ -d "$tgtPath" ] ; then # startof if target directory
		
		# Select....
		O=$IFS IFS=$'\n' srcPaths=(`zenity --file-selection --directory --multiple --separator=$'\n' --title="Select source directories" --window-icon="$window_icon"`) IFS=$O

		# Searching.. quickscan
		(
		echo "10"
		for srcPath in "${srcPaths[@]}" ; do
		#	=$(($srcB+$(echo `dosomething` | bc)))
			srcB=$(($srcB+$(echo `find "$srcPath" -type f -size +$(($minFS-1))c -size -+$(($maxFS+1))c -iregex $searchPattern -print0 | xargs -0 stat -c %s+ ; echo 0` | bc)))		
		done
		echo "100"

		# How many?....
		tgtBFree=$((`stat -f -c %f "$tgtPath"`*`stat -f -c %s "$tgtPath"`)) 
	 	if [ $srcB -lt $tgtBFree ]; 
			then dialog_entry_text=$(($srcB/$bInMB))
			else dialog_entry_text=$(($tgtBFree/$bInMB))
		fi
		remSrcB=$(($bInMB*`zenity --entry --text="$(($srcB/$bInMB))MB of files $(($minFS/$bInMB))-$(($maxFS/$bInMB))MB found. $(($tgtBFree/$bInMB))MB free on device of /$(echo "$tgtPath" | sed 's/^.*\///'). How much to copy?" --entry-text="$dialog_entry_text" --title="$window_title" --window-icon="$window_icon"`))
		initSrcB=$remSrcB

		if [ $srcB -gt 0 ]; then # startof if not 0 Bytes
		
			# Searching.... deepscan
			(
			echo "10"
			for srcPath in "${srcPaths[@]}" ; do
				O=$IFS IFS=$'\n' tempSrcF=( `find "$srcPath" -type f -size +$(($minFS-1))c -size -+$(($maxFS+1))c -iregex $searchPattern` ) IFS=$O
				remSrcF=( "${remSrcF[@]}" "${tempSrcF[@]}" )
			done
			initSrcF="${#remSrcF[@]}"
			echo "100"

			# Copying....
			(
			while [ ${#remSrcF[@]} -gt 0 ] && [ $remSrcB -ge $minFS ] ; do 
				random=$(($RANDOM % $initSrcF)) 
				if [ -n "${remSrcF[$random]}" ] ; then # if element is not empty
					srcFS=$((`stat -c %s "${remSrcF[$random]}"`))
					if [ $srcFS -le $remSrcB ] && ! [ -e "$tgtPath/$(echo "${remSrcF[$random]}" | sed 's/^.*\///')" ] ; then # last condition prevents overwrite
						cp -i -L "${remSrcF[$random]}" "$tgtPath"
						remSrcB=$(($remSrcB-$srcFS)) # post-copy!
						srcCpB=$(($srcCpB+$srcFS))
					fi
					unset remSrcF[$random] # make element empty
				fi
				echo $((100*($initSrcB-$remSrcB)/$initSrcB))
			done
			echo "100"

			zenity --info --text="$(($srcCpB/$bInMB))MB successfully copied to $tgtPath" --title="$window_title" --window-icon="$window_icon"

			) | zenity --progress --auto-close --percentage="$((100*($initSrcB-$remSrcB)/$initSrcB))" --text="copying $(($initSrcB/$bInMB))MB to $(echo "$tgtPath" | sed 's/^.*\///').." --title="$window_title" --window-icon="$window_icon"
			# endof copying pipe

			) | zenity --progress --pulsate --auto-close --percentage=0 --text="deepscanning selected folders.." --title="$window_title" --window-icon="$window_icon"
			# endof deepscan find pipe
		
		fi # endof if not 0 B
	
		) | zenity --progress --pulsate --auto-close --percentage=0 --text="quickscanning selected folders.." --title="$window_title" --window-icon="$window_icon"
		# endof quickscan find pipe
	
	fi # endof if target directory

done
# endof for tgtPath
exit
```

Thanks for that!

---

### Post by momist on 2012-04-30
Wonderful.  Glad you got it going!

---

