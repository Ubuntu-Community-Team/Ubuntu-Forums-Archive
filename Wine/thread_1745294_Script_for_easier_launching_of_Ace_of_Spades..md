---
title: "Script for easier launching of Ace of Spades."
date: 2011-04-30
forum: Wine
---

### Post by RoyalShrubber on 2011-04-30
The official method of launching [Ace of Spades]("http://ace-spades.com/") is through browser, but on linux you either have to use windows browser with wine for this to work or copy/paste little id string into terminal. Here is a little bash script that automatically downloads servers list and enables you to launch selected server directly from terminal greatly streamlining the process.

You have to have wine installed and fix audio drivers if you want to have sound. To launch the script simply copy/paste the following text into a file and then enter into terminal 'bash filename'. The script is very simple because I'm new to bash, if you have any improvements to the script then I can include them. 

```


#!/bin/bash
filename="/tmp/aos_list.txt"
function print_list {
	entryno='0'
	cat $filename | grep aos | while read no png tmp1 tmp2; do
		aos=$( echo $tmp2 | cut -d'/' -f3- | cut -d '"' -f-1 )
		srvname=$( echo $tmp2 | cut -d'>' -f2- | cut -d '<' -f-1 ) 
		(( entryno++ ))
		echo $entryno: $no $png $aos $srvname
	done
}
function download_list {	
	touch $filename
	wget http://ace-spades.com/?page_id=5 -O $filename
	print_list
}
function print_help {	
	echo "Enter command: "
	echo "<number>: open <number>th server"
	echo "a: attempt opening the previously selected server again"
	echo "r: redownload server list"
	echo "l: show servers again"
	echo "h: print this info"
	echo "e: exit this script" 
}
function load_game {
	echo launching $srvname
	wine "$HOME/.wine/drive_c/Program Files/Ace of Spades/client.exe" -aos://$srvname &> /dev/null
}
if [[ $1 == '-f' ]];  then print_list; else download_list; fi
print_help
while read cmd; do
	if [[ ${cmd} =~ ^[0-9]+ ]] ; then 
		srvname=$( cat $filename | grep aos | head -$cmd | tail -1 | cut -d'/' -f4- | cut -d '"' -f-1 )
		load_game  		
	elif [[ ${cmd} = a ]] ; then
		load_game
	elif [[ ${cmd} = r ]] ; then
		download_list
	elif [[ ${cmd} = l ]] ; then
		print_list
	elif [[ ${cmd} = h ]] ; then
		print_help
	elif [[ ${cmd} = e ]] ; then 
		exit
	else
		echo unrecognized command	
	fi
done


```

---

### Post by Anticontrame on 2011-07-25
Very useful! You should share this on the AoS wiki or wineHQ page.

---

### Post by eldoro100 on 2012-03-18
I'm a complete newbie to ubuntu and it's requirements for manual controlling so how do I launch the game after I've entered the command?

---

