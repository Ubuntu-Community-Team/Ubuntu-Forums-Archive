---
title: "Command line RSS reader for TVrss wanted"
date: 2006-11-03
forum: The Cafe
---

### Post by neilp85 on 2006-11-03
Does anyone know of a decent command line RSS reader that I could use for downloading torrents from TVrss feeds. I've been doing a decent amount of searching on the net for something but haven't been able to find anything to suit my needs. I could probably write something myself to solve this problem but would prefer not to.

---

### Post by neilp85 on 2007-01-31
I hacked out a solution to this a while back so I figured I would post it for everyone. It's pretty ugly (one of my first python scripts), but does exactly what I need. There are a couple things I planned on fixing but never got around to. You will need to install the universal feed parser package for this to work.

```
#!/usr/bin/env python
"""torrentdl.py - Downloads new torrents from tvrss.net feeds"""

import feedparser, os, time

path = os.getenv('HOME') + '/downloads/torrents'

# Load every line of the file to a list element
file = open(path + '/tvrss-feeds')
lines = [line for line in file.readlines() if line.strip()]
file.close()

# Last line of the file should be the previous time we
# checked the feeds, if not make it the current time.
if lines[-1][0] == '(':
    # Force it to the proper format
    prev_time = lines[-1].strip()[1:-1]
    prev_time = (prev_time.split(', '))
    prev_time = tuple([int(val) for val in prev_time])
    lines.pop()
else:
    prev_time = time.gmtime()

# Generate a list of rss urls by removing comments
url_list = [url.strip() for url in lines if url[0] != '#']

# Get the current time (GMT because feedparser uses it) to
# replace old time value at bottom of file
curr_time = time.gmtime()

# TODO: This could really be sped up if each feed was handled
#            in it's own thread from here on

# Grab all the rss feeds
feeds = [feedparser.parse(rss_url.strip()) for rss_url in url_list]

# Basic wget command for all torrent downloads
# --referer is a workaround for torrents from mininova
base_command = 'wget --quiet --tries=1 --read-timeout=90 --referer=%s %s'

# Make sure torrents get dowloaded to proper directory
os.chdir(path)

# Check all your feeds for new torrents
for feed in feeds:
    for entry in feed['entries']:
        # Only download new torrents
        if(prev_time < entry['updated_parsed']):
            # Check that the torrent was actually downloaded
            command = base_command % (entry['link'], entry['link'])
            print entry['summary']
            if(os.system(command) != 0):
                # TODO: Error handling
                pass

# Overwrite the old file with the new time value
file = open(path + '/tvrss-feeds', 'w')
file.writelines(lines)
curr_time = [str(val) for val in curr_time]
file.write("(" + ", ".join(curr_time) + ")" + '\n')
file.close()
```

Find the shows you want on tvrss then add the RSS links to your feeds file and off you go. I use this as a cron job in conjunction with rtorrent watching the directory torrents are downloaded to. Feel free to critique and post any improvements.

---

### Post by Mateo on 2007-01-31
does this have to be used with torrents?  could it work with podcasts or something like that too?

I've been looking for a solution similar to this to use in conjuction with youtube-dl, this might work.  i'll take a look at it later more closely.

---

### Post by neilp85 on 2007-01-31
This could probably be modified to be a more generic RSS content downloader. You would need an abstraction for obtaining the content link and action to perform on it. I'm gonna take a look at it and see what I come up with.

---

### Post by neilp85 on 2007-01-31
Alright, after some work I've come up with a more generic version. I also cleaned up the code some. Besides adding the feed to the file with all your others, the only thing you should have to do is provide an action for new types of feeds (i.e. youtube, tvrss, etc...). I added a basic one for youtube videos using youtube-dl. There's still some more modifications I want to make, but this is a pretty good start.

```
#!/usr/bin/env python
"""rssdl.py - Performs acctions on new content linked to from rss feeds"""

import feedparser, os, time

# Retrieves value from dictionary with partial match key
def getValue(key, dict):
    for k in dict.keys():
        if key.startswith(k):
            return actions[k]
    return None


# Actions are dependent on the type of feed
actions = { \
    'tvRSS': 'wget --quiet --tries=1 --read-timeout=90 %(link)s', \
    'YouTube': 'youtube-dl --output="%(title)s.flv" %(link)s', \
}

path = '%s/downloads' % os.getenv('HOME')
name = '%s/feeds' % path

# Load every line of the file to a list element
file = open(name)
lines = [line for line in file.readlines() if line.strip()]
file.close()

# Last line of the file should be the previous time we
# checked the feeds, if not make it the current time.
if lines[-1][0] == '(':
    # Force it to the proper format
    oldtime = lines[-1].strip()[1:-1]
    oldtime = (oldtime.split(', '))
    oldtime = tuple([int(val) for val in oldtime])
    lines.pop()
else:
    oldtime = time.gmtime()

# Generate a list of rss urls by removing comments
urls = [line.strip() for line in lines if line[0] != '#']

# Get the current time (GMT because feedparser uses it) to
# replace old time value at bottom of file
newtime = time.gmtime()

#TODO: This could really be sped up if each feed was handled
#      in it's own thread from here on

# Grab all the rss feeds
feeds = [feedparser.parse(url.strip()) for url in urls]

# Make sure torrents get dowloaded to proper directory
os.chdir(path)

# Check all your feeds for new torrents
for feed in feeds:

    # Ignore feeds we don't know what to do with
    action = getValue(feed['feed']['title'], actions)
    if action is None:
        continue

    for entry in feed['entries']:
    # Only download new torrents
        if oldtime < entry['updated_parsed']:
            # Check that action was taken
            if os.system(action % entry) != 0:
                # TODO: Error handling
                pass


# Overwrite the old file with the new time value
file = open(name, 'w')
file.writelines(lines)
newtime = [str(val) for val in newtime]
file.write("(%s)\n" % ", ".join(newtime))
file.close()

# End of file rssdl.py
```

---

### Post by neilp85 on 2007-01-31
Could a moderator move this thread to programming talk. It seems like a much more appropriate place for it now.

---

### Post by Mateo on 2007-01-31
ohh wow, I wasn't expecting you to do all of that. thanks a lot, i'll take a look at it and see if it needs any tweaking.

---

### Post by tbroderick on 2007-02-01
You can use raggle or snownews with a console web browser like lynx or elinks. Add the feed and open the entry with the browser, it will ask you to save the .torrent.

---

### Post by neilp85 on 2007-02-01
The problem with those is that they won't automatically download the torrent file when a new entry is added to the RSS feed. I would have to check them periodically and go download any files. However, my solution is fully automated so the torrents will start downloading as soon as they are available.

---

### Post by casaschi on 2007-02-01
It uses a different RSS feed, but you can automate torrent downloads from RSS using tvtorrentfetch ( [http://xyzabc.xy.ohost.de/](http://xyzabc.xy.ohost.de/) )

---

### Post by benpretend on 2007-06-20
What is the format for the config files? It's hard to decipher what exactly you want us to put in the files.

---

### Post by neilp85 on 2007-06-21
In the config file just put a link to each feed you wish to subscribe to on a seperate line. Lines starting with # are comments. Here's part of what mine looks like.

```

# Battlestar Galactica
http://tvrss.net/search/index.php?distribution_group=eztv&show_name=battlestar&filename=&date=&quality=WS&release_group=&mode=rss
# Entourage
http://tvrss.net/search/index.php?distribution_group=combined&show_name=entourage&filename=&date=&quality=&release_group=&mode=rss
# Family Guy
http://tvrss.net/search/index.php?distribution_group=vtv&show_name=family+guy&filename=&date=&quality=&release_group=&mode=rss
# Heroes (High Res)
http://tvrss.net/search/index.php?distribution_group=combined&show_name=Heroes&filename=&date=&quality=HR+HDTV&release_group=&mode=rss
# Lost (High Res)
http://tvrss.net/search/index.php?distribution_group=combined&show_name=Lost&filename=&date=&quality=HR+HDTV&release_group=&mode=rss

```

---

### Post by balance07 on 2007-09-22
i'm having a tough time getting this to work properly, even with tvrss search based feeds like you are using. the problem comes at the download part i beleive. instead of getting .torrent files, i get files like '576773' and that's all. looks like wget is not "following through" mininova's links to download the file properly.

now if i add a .torrent to the end of the file, it DOES work, but now it's not automated. any thoughts?

---

### Post by phatmonkey on 2007-11-16
[http://sourceforge.net/projects/pytvshows](http://sourceforge.net/projects/pytvshows)

---

### Post by ughknight on 2008-03-04
Here's one that I slapped together. Disclaimers and instructions are within the comments.

```
#!/bin/bash

# This is released under the GPL

# Ugly ugly tv rss script.

# Relies on tvrss.net and assumes that the newest show will be at the top of the page

# Also needs "xmlstarlet" to parse the feed

# Finally, relies on rtorrent, or any torrent client that lets you use a "watch" folder.

# How it works. Make a directory for your shows. In it, make 1 textfile per show,
# with the name of the file having no spaces - eg "DailyShow" 
#The content of the file should be the actual show's feed.

# The program will then check the feed every hour, seeing if there is a new show
# via a "datefile" - if there is a new show, it will download the torrent
# file and put it in your "watch" folder. From there, your torrent client
# should be able to pick it up. rtorrent is what I use, but I think others
# work as well.

# You can let this script run forever, theoretically. 
# It hits tvrss.net once an hour. I like to run it
# in a window using GNU Screen, that way I can do other stuff and check on 
# it periodically.
 
# Disclaimer--this program sucks and it might blow up your system and revisions are 
# welcome. I'm not a programmer AT ALL. 

while [ 1 ]; do


# Universal parms.
torrentwatchdir=~/torwatch/
tvshowdir=~/tvdl/tvshows/


# Massive loop starts here
for eachtvshow in `ls ${tvshowdir}` ; do

showname=${eachtvshow}
indexurl=`cat ${tvshowdir}/${eachtvshow}`

# This quasi-universal variable comes from the name of the show, so we put it here.
olddatefile=~/tvdl/${showname}-olddatefile


echo "Working on the show $showname, with indexurl $indexurl"

#Create an empty datefile if there isn't one there
if [ ! $olddatefile ]; then
	echo "No datefile found, gonna make one..."
	sleep 5
	touch $olddatefile
else
	echo "Datefile found, proceeding."
	sleep 5
fi


#Setting temporary file
tmpfile=~/tvdl/tvtemp	


#Read the old date into a variable
olddate=`cat $olddatefile`

echo "the old date for this show is $olddate"
sleep 2

#Get the rss feed
echo "Getting the rss feed in 5"
sleep 5
wget -O $tmpfile $indexurl

# Pull out magic url to extract new date and file. All this particular one does is
# grab the first one on the page, this works for tvrss. You know, these could
# be functions. To make this script bigger and interchangeable.
magicurl=`xmlstarlet sel -t -v "/rss/channel/item/link" $tmpfile`

echo "$magicurl is the magic url"

# Pull out date--this should make this so you dont get 5 diff versions of same date
latestdate=`xmlstarlet sel -t -v "/rss/channel/item/pubDate" $tmpfile | awk '{print $2x $3}' `

echo "the latest date for this show is $latestdate"

# Determine whether the new date = the old one, which really means, "Got newest episode?"
if [ $latestdate = $olddate ] ; then
	echo "Date $latestdate is same as the one in $olddatefile - No new episode, exiting."
	continue

else
	echo "New episode found, with date $latestdate. Fetching torrent file..."
	# okay, here's the magic. I don't think I will do any DELETION here, Will just fetch the torrent file and worry about everything later.
	# Read up on rtorrent to figure out all that magic. So, note, this will just store tons of movies.
	
	#Note, this screws up if there are any quotes WITHIN the url, which I dont think happens. Note the second one as a cutter, the double _ _ is odd
	torrenturl=$magicurl
	echo "Url torrent is $torrenturl"
	wget -O "${torrentwatchdir}${showname}-${latestdate}.torrent" "$torrenturl"
	echo "Torrent downloaded- setting new date"
	echo ${latestdate} > ${olddatefile}
fi	

# Massive Loop ends here
done

# Fake cron is the below 2 commands

echo "sleepin' for an hour..."

sleep 3600

done

exit
```

---

### Post by dcherryholmes on 2008-03-21
Hey,

I found this thread while I was looking for some advice on pytvshows.  I'm currently using it, rtorrent, and screen for a very nice and flexible system.  However, I'm not sure how to tell pytvshows to only grab HD, or 720p, or whatever.  So far all I've figured out is how to pluck the [Show+name] out, and specify seasons and episodes.  Any advice?

---

### Post by chochem on 2008-03-21
> **ughknight said:**
> Here's one that I slapped together. Disclaimers and instructions are within the comments.


Just wanted to say a big thank you for this. I tried once to do something like this based on bashpodder but never made much progress. And also a big thank you for pointing me in the direction of GNU screen (I always wondered why nobody had done something like this.... :D )

The script certainly does what it say on the tin (downloads topmost torrent) - I'll have a look at the code to see if there's room for improvement (not that I'm a pro in any way). One thing struck me though: You might want to be more explicit and consistent in terms of how you refer to the different directories. "tvshowdir" is "directory where you keep the files containing the rss feeds (or torrentfeeddir)", not as a non-bash'er might suppose the directory which will eventually contain the tv show itself. And torrentwatchdir?... well, it could be the torrents that *the script* is watching/monitoring, not rtorrent. Maybe stating clearly that $torrentwatchdir is "The directory monitored by your torrent client for torrent files" would clear things up :) Oh and maybe putting all the user defined directories/files at the top of the script (log files and stuff) would help too. Sorry for being a busybody...

---

### Post by chochem on 2008-03-30
I finally got the time to take a closer look at ughknight's script. It works really well for a 'ugly, ugly, ugly' script so there was no real need to tinker with it. Except that I'd prefer for it to be more of a subscription than a 'get the last one' kinda thing. So I pretty much reworked it completely (only thing that's the exactly same is the loop structure) - this one will check the feed against a log of already downloaded torrent files, then get all the new ones. (so if you do not want the entire backcatalogue, be sure to delete the resulting torrent files after you run it for the first time). As with ughknight's, you'll need to enter your own directory settings and make sure that you meet the requirements (see comments), and as with ughknight's I'd recommend running it in a window in [GNU screen]("http://en.wikipedia.org/wiki/Gnu_screen") or the like. Enjoy :)

```
#!/bin/bash

# This is released under the GPL
# A tvrss script by chochem, a reworking of ughknight's (http://ubuntuforums.org/showthread.php?t=292386&page=2)
# Functions much like ughknights, except that it checks the feed against a list
# of already downloaded torrent files, then gets all the new ones.
# Also added functions are error checking and removing old unused torrent files

# REQUIRES:
# Text files containing a single feed url from tvrss.net (keep these in the 'tvrssdir' folder)
# "Xmlstarlet" to parse the feed (to get it, enter: "sudo apt-get install xmlstarlet")
# A torrent client that lets you use a "watch" folder (torrent files in said folder are automatically loaded)

# Please set the two directory variables and the waiting period under 'SETTINGS' to reflect your setup.
# The script will make the directories if they do not already exist.
# Though care has been taken to protect filenames and locations containing spaces, they should
# still be avoided in the directory and feed file names if at all possible.

# SETTINGS - CUSTOMIZE ACCORDING TO YOUR SETUP
# tvrssdir is the directory in which you put the files containing feed urls (and tvrss keeps its log and temp files)
tvrssdir=~/tvrss
# watchdir is the directory your torrent client checks for new torrents to load automatically
watchdir=~/rtorrentwatch
# waitingperiod is the time in hours between checks for new torrents (accepts decimals, e.g. 0.25 for 15 minutes)
waitingperiod=1
# maxage is used in a routine that deletes old torrent files from a show subscription. Torrents more than this number of months old gets deleted.
maxage=1
# END OF SETTINGS

while [ 1 ]; do

if [ ! -d "$tvrssdir" ]; then mkdir "$tvrssdir"; fi
if [ ! -d "$watchdir" ]; then mkdir "$watchdir"; fi

# For-each-tvshow-subscription-do loop starts here
for tvshow in $(ls "${tvrssdir}"); do

#Setting temporary files and variables
newtorrentscount=0
feedurl=$(cat "${tvrssdir}/${tvshow}")
tmpxml="${tvrssdir}/.tmpxml"
oldurllist="${tvrssdir}/.${tvshow}-oldurllist"

# Get the rss feed
echo "Working on the show \"$tvshow\""
echo "Getting the rss feed..."
wget -q -O "$tmpxml" "$feedurl" 2> /dev/null && echo "Feed file downloaded. Parsing file for new torrents..." || (
	echo "The feed \"$tvshow\" at \"$feedurl\" could not be downloaded." 
	echo -e "\r\033[7mCheck the address and/or your connection.\033[0m"; echo
	rm "$tmpxml"
	)

# On condition that wget got hold of a file...
if [ -e "$tmpxml" ]; then

# Parse the feed file for torrent links
touch "$oldurllist"
oldurlstring=$(cat "$oldurllist")
currenturlstring=$(xmlstarlet sel -t -m "/rss/channel/item/link" -v "concat(.,' ')" "$tmpxml" 2> /dev/null)

# Check for no results (this covers an empty feed as well as a parsing error)
if [ -z "$currenturlstring" ]; then 
	echo  -e "\r\033[7mA file has been downloaded but parsing it resulted in no URLs.\033[0m"
	echo "Either the address in the ${tvrssdir}/${tvshow} file does not refer to a tvrss.net feed or the feed is empty."; echo
else
# Check for URLs not in the log (the show's oldurllist), get new ones, add the entry to the log and inform user
for url in $(echo "$currenturlstring"); do
	if [[ ! "$oldurlstring" =~ "$url" ]]; then
		echo "$url is new. Getting torrent file..."
		wget -q -O "${watchdir}/${tvshow}_$(date +%y%m%e)_$(date +%H%M%S%N).torrent" "$url"
		echo "$url" >> "$oldurllist"
		let "newtorrentscount++"
	fi
done

# Evaluate / user output
if [ "$newtorrentscount" -gt 0 ]; then
	echo -e "\r\033[7mFound ${newtorrentscount} new torrent(s) for \"$tvshow\"\033[0m"; echo
else
	echo -e "\r\033[7mNo new torrents for \"$tvshow\"\033[0m"; echo
fi

# No results condition ends...
fi

# Cleaning up (remove tmpxml)
rm "$tmpxml"

# wget condition ends...
fi

# Check for old torrent files for this show and remove any older than two months
now=$(date +%s)
for filename in $(ls ${watchdir}/${tvshow}_*.torrent 2> /dev/null); do 
	birthday=$(date +%s -r "${filename}")
	agesecs=$(($now-$birthday))
	agemonths=$(($agesecs/2629743))
	if [ $agemonths -gt $maxage ]; then
		echo "Cleaning up old torrent file for \"$tvshow\"..."
		rm "$filename"
	fi
done

# For-each-tvshow-subscription-do loop ends...
done

# Fake cron is the below 2 commands
echo "Sleeping for ${waitingperiod} hour(s)..."
sleep ${waitingperiod}h

# Neverending loop ends...
done
exit
```

---

### Post by chochem on 2008-03-31
I've put a very different version of this up on my web site. The new version is easier to configure (has it's own configuration file), has an option to add new subscriptions and is crontab friendly. Check it out [here]("http://bash.viharpander.dk/#tvrss").

---

### Post by ughknight on 2008-06-18
Ha, wow, I'd totally given up on this project and was using Miro--I'm glad to see that someone took this and ran with it, and so far its working really well. Good stuff, chochem!

---

### Post by chochem on 2008-06-25
thanks - glad you like it :)

---

### Post by zoomb on 2010-09-25
Hiya,

The tvrss script from this thread has been incredibly helpful to me! I've been using it for about a year, and recently decided to add some tolerance for wget errors, i.e., when links are not yet live. I had a problem where the script thought it had properly downloaded a torrent file, added it to the oldurllist, and therefore never tried to grab the torrent again. 

The script is currently setup to run as a daemon/monit script which sleeps for a period of time, but could easily be modified to run standalone, by cron or what-have-you. If anyone is interested, please let me know! Fair warning: I'm not a coder by trade, so I imagine it's a bit ugly. :p Any input would be welcome!

---

### Post by Badcam on 2011-06-02
> **zoomb said:**
> Hiya,

The tvrss script from this thread has been incredibly helpful to me! I've been using it for about a year, and recently decided to add some tolerance for wget errors, i.e., when links are not yet live. I had a problem where the script thought it had properly downloaded a torrent file, added it to the oldurllist, and therefore never tried to grab the torrent again. 

The script is currently setup to run as a daemon/monit script which sleeps for a period of time, but could easily be modified to run standalone, by cron or what-have-you. If anyone is interested, please let me know! Fair warning: I'm not a coder by trade, so I imagine it's a bit ugly. :p Any input would be welcome!


Any chance you could post it here, for us? :popcorn:

---

### Post by Badcam on 2011-06-02
> **chochem said:**
> I've put a very different version of this up on my web site. The new version is easier to configure (has it's own configuration file), has an option to add new subscriptions and is crontab friendly. Check it out [here]("http://bash.viharpander.dk/#tvrss").

Oh No. The link is broken. :( Does anyone still have a copy of the script that link points to?

---

### Post by zoomb on 2011-06-17
> **Badcam said:**
> Any chance you could post it here, for us? :popcorn:

Certainly!

You should only really need to modify the initial variable settings in the #variables# section to suit your environment. Everything else should be good to go. :D

If you need help, the traditional "-h" or "--help" command line modifier will do the trick. ;)

- zoomb


P.S. I'm 30KB over the upload limit, so here's my code.

```

#!/bin/bash
# a RSS torrent subscription script 
# based on 0.33 by chochem
# revised by zoomb
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

########################
### check for conf file
########################
ORIGINAL_IFS=$IFS
IFS=$'\n'

if [ -f ~/.tvrss ]; then
	. ~/.tvrss
else
	echo "Config file missing. Please run 'tvrss --setup' to create one."
	exit
fi

# ensure folders in config file exist
[ -d "$tvrssdir" ] || mkdir -p "$tvrssdir"
[ -d "$watchdir" ] || mkdir -p "$watchdir"
[ -d "$mediadir" ] || mkdir -p "$mediadir"

###############
### variables
###############

### This script assumes that you want to keep all logs in the same location that you are
### keeping all configuration files and, theoretically, from where you are running the 
### script, though this is not necessary.

## command directory
com_dir="$tvrssdir"

## output file
out_log="tvrss-log.txt"

## path to output file
output="$com_dir"/"$out_log"

## file storing errored urls from previous run
url_store="$com_dir"/url-store.txt

## file storing temporary urls
url_tmp="$com_dir"/url-tmp.txt

## file storing urls to be worked on
url_cache="$com_dir"/url-cache.txt

## file storing temporary show titles
name_tmp="$com_dir"/name-tmp.txt

## file storing temporary show publishing dates
date_tmp="$com_dir"/date-tmp.txt

## number of times run
cycle=0

# ensure log archive folder exists
[ -d "$com_dir"/logs ] || mkdir -p "$com_dir"/logs


##############
### functions
##############

printhelp () {
printf "tvrss is a torrent RSS subscription script. It will check your 
feeds for new torrent files (.torrent) or media files and download them 
to a designated folder. It can be run manually but it is probably preferable 
adding it as a crontab entry or combining it with daemon and monit.

It requires a .tvrss configuration file in the home folder, so run it
once as 'tvrss --setup' to create one. This will allow you to designate 
three folders: (1) a 'tvrss' folder where your subsciption files and log 
files (log of previously downloaded torrents) will be kept, (2) a 'watch' 
folder where the .torrent files will be saved, and (3) a folder where your 
AV media is stored.

Subscriptions are given to the script in the form of lines in the 'feeds' 
file, a text file containing a single 
'[name][tab][media type][tab][feed url]' 
set per line. This should be kept in the 'tvrss' folder, and can be edited 
manually or by using 
\"tvrss --add '[feed name of choice]' '[media type]' '[url]'\" 
(the quotes are important). You can also use 
\"tvrss -i\" to interactively add a feed.

There are built-in notifications to the user when run in the foreground,
mostly for the purpose of debugging. Because the script runs for 15 minutes
(though this can be easily modified), I would recommend running it in the 
background. Also, the number of downloaded torrents is added to a counting 
file in /tmp (thus it will be reset whenever /tmp is cleared, usually at reboot), 
making it available for other scripts/programs to pick up, e.g. 'watch'.

REQUIRES:
- xmlstarlet to parse the feed (apt package: xmlstarlet)
- suggested: a torrent client that lets you use a watch folder (torrent files
  in said folder are automatically loaded), e.g. vuze, rtorrent and utorrent.
"

}

setupConfFile () {
rm ~/.tvrss &> /dev/null

tvrssdir="\*"
watchdir="\*"
mediadir="\*"

printf "Entering tvrss configuration. This will produce a configuration file
(.tvrss) in your home directory in order to save your settings. Please see 
'tvrss --help' for more details."

echo

read -p "Where would you like tvrss to store your tvrss .feed and .log files 
(e.g. '/home/user/p2p/tvrss')? " tvrssdir

while [ ! -d "$tvrssdir" ]; do
	read -p "$tvrssdir is not a directory - do you wish to create it now? (yes/no/exit) " reply
	case $reply in
		yes)
		mkdir -p "$tvrssdir"
		;;
		no) 
		echo "Please try again."
		echo
		read -p "Where would you like tvrss to store your tvrss .feed and .log files? " tvrssdir
		;;
		exit)
		echo .tvrss file has not been created.
		exit
		;;
		*)
		echo "Please enter either 'yes', 'no', or 'exit'."
		;;
	esac
done

echo

read -p "Where would you like tvrss to store your downloaded .torrent files 
(suggestion: the folder you have told your torrent client to watch for new 
.torrent files, e.g. '/home/user/p2p/watch')? " watchdir

while [ ! -d "$watchdir" ]; do
	read -p "$watchdir is not a directory - do you wish to create it now? (yes/no/exit) " reply
	case $reply in
		yes)
		mkdir -p "$watchdir"
		;;
		no) 
		echo "Please try again."
		echo
		read -p "Where would you like tvrss to store your downloaded .torrent files? " watchdir
		;;
		exit)
		echo .tvrss file has not been created.
		exit
		;;
		*)
		echo "Please enter either 'yes', 'no', or 'exit'."
		;;
	esac
done

echo

read -p "Where would you like tvrss to store your media files
(suggestion: the folder where your torrent client saves media by default)? " mediadir

while [ ! -d "$mediadir" ]; do
	read -p "$mediadir is not a directory - do you wish to create it now? (yes/no/exit) " reply
	case $reply in
		yes)
		mkdir -p "$mediadir"
		;;
		no) 
		echo "Please try again."
		echo
		read -p "Where would you like tvrss to store your media files? " mediadir
		;;
		exit)
		echo .tvrss file has not been created.
		exit
		;;
		*)
		echo "Please enter either 'yes', 'no', or 'exit'."
		;;
	esac
done

echo "tvrssdir=${tvrssdir}" > ~/.tvrss
echo "watchdir=${watchdir}" >> ~/.tvrss
echo "mediadir=${mediadir}" >> ~/.tvrss

echo "Setup done"
}


interAdd()
{
touch "$tvrssdir"/feeds

local namestring="$(cat $tvrssdir/feeds)"

read -p "What would you like to call the show? Make sure to use a single 'word': " tvshowname

while [[ "$namestring" =~ "$tvshowname" ]]; do
	read -p "Name already exists. Please try a different monicker: " tvshowname
done

read -p "What filetype is in the feed? (torrent or other): " tvshowtype

while [[ "$tvshowtype" != "torrent" && "$tvshowtype" != "other" ]]; do
read -p "Please enter 'torrent' or 'other': " tvshowtype
done

read -p "What is the url of the feed? " tvshowurl

while [[ "$namestring" =~ "$tvshowurl" ]]; do
	read -p "Url already exists. Do you need to complete this entry (yes or no): " choice

	case $choice in
		yes)
		read -p "Please enter a modified url: " tvshowurl
		;;
		no)
		echo "OK then, thanks!" && exit
		;;
		*)
		echo "Please enter 'yes' or 'no': "
	esac

done

echo -e "$tvshowname\t$tvshowtype\t$tvshowurl" >> "$tvrssdir"/feeds

}



## usage: log_chk "name based on purpose of log" ##
log_chk()
{
# name of log file
local log="$(echo "$1")"

# path to original log
local old_log="$(echo "$com_dir"/"$log")"

# path to archived log
local new_log="$(echo "$com_dir"/logs/"`date +%Y%m%d`"_"$log")"


if [ -f "$old_log" ]; then

	# date original log was created
	local old_date="$(expr substr "`cat $old_log`" 1 8)"
	
	# date of current script run
	local new_date="$(date +%Y%m%d)"

	#if original log is not from today, archive it and create new log
	if [ "$old_date" != "$new_date" ]; then
		echo "`date +%Y%m%d-%H%M%S` Moving log files." >> $old_log

		temp_out="$(echo `mv -v "$old_log" "$new_log"`)"

		echo "$temp_out" >> $new_log
	
		log_init

	fi
	
else
	log_init
		
fi

}

log_init()
{
# initialize new log
	date +%Y%m%d-%H%M%S >> $output
	echo >> $output
	
	echo Watch directory is "$watchdir" >> $output
	
	echo Media directory is "$mediadir" >> $output
	
	echo Command directory is "$com_dir" >> $output
	
	echo TVRSS directory is "$tvrssdir" >> $output
	echo >> $output
	
	echo Output goes to "$out_log" >> $output
	echo with path "$output" >> $output
	echo >> $output
	
	echo Store file for errored urls is "$url_store" >> $output

	echo ------------------ >> $output
	echo >> $output

}


## usage: log_cln /path/to/folder log ##
log_cln()
{
local log_folder="$1"

local log="$2"

# check if last character of $log_folder is a "/"
local char="$(echo "$log_folder" | awk '{print substr($0,length,1)}')"

if [ "$char" != "/" ]; then
	log_folder="$(echo "$log_folder"/)"
fi

local log_output="$(find "$log_folder" -type f -iname '*"$log"' -mtime +7 -exec rm -fv {} 2>&1 \;)"


# if logfile exists, remove it
if [[ "$log_output" ]]; then
	date +%Y%m%d-%H%M%S >> $log_folder/logclean.txt
	echo $log_output >> $log_folder/logclean.txt
	echo >> $log_folder/logclean.txt
fi

}

## usage: form_chk "fileform"
form_chk()
{
#local fu=fileurl
#local ft=filetitle
#local fc=filecat
#local fd=filedate
#local fn=filename
#local fo=tmp_fname
#local ex=extension

fform="$(echo "$1")"

[[ "$fform" ]] || fform="$(echo fd-ft.ex)"

form=$(echo "$fform" | sed -e 's/fu/\$fileurl/g' -e 's/ft/\$filetitle/g' -e 's/fc/\$filecat/g' -e 's/fd/\$filedate/g' -e 's/fn/\$filename/g' -e 's/fo/\$tmp_fname/g' -e 's/ex/\$extension/g')

final=$(eval echo "$form")

}

## usage: url_chk "fileurl" "filetype" "filetitle" "filecat" "filedate" "fileform"
url_chk()
{
local fileurl="$1"

echo File URL is $fileurl
echo
sleep 1

local filetype="$2"

echo File type is $filetype
echo
sleep 1

local filetitle="$3"

echo File title is $filetitle
echo
sleep 1

local filecat="$4"

echo File category is $filecat
echo
sleep 1

local filedate="$5"


# if filedate is empty, fill it with current date
[[ "$filedate" ]] || filedate="$(echo `date +%Y%m%d`)"


echo Filedate is $filedate
echo
sleep 1

local fileform="$6"

echo Fileform is $fileform
echo
sleep 1


# grab end of url after final "/" as filename
local filename="$(echo `expr "$fileurl" : '.*//*/*\(.*\)'`)"

echo Filename is $filename
echo
sleep 1

# grab last 8 characters of the url to check later (looking for .torrent)
local end="$(echo `expr "$fileurl" : '.*\(........\)'`)"

echo Last 8 characters are $end
echo
sleep 1


# and just in case file is not a torrent, grab characters after last "."
local extension="$(echo `expr "$filename" : '.*\.\(.*\)'`)"

echo Extension seems to be $extension
echo
sleep 1

# filename without extension for naming use
local tmp_fname="$(expr "$filename" : '\(.*\)\.')"

echo Filename without extension is $tmp_fname
echo
sleep 1


# if the filetype is torrent, place file in watch directory and set extension to "torrent"
if [ "$filetype" = "torrent" ]; then
	filedir="$watchdir"
	extension="$(echo torrent)"

# else, put the file in a folder in the media directory
else
	filedir="${mediadir}"/"$filecat"
	[ -d "$filedir" ] || mkdir -p "$filedir"

fi

echo Directory for this file should be $filedir
echo
sleep 1


form_chk "$fileform"

echo Attempting to put "$final" in folder "$filedir"/...
echo
sleep 2


# capture all messages from wget
status=$(wget --tries=2 -O "${filedir}"/"$final" "${fileurl}" 2>&1)

# echo $status

# will contain information if there is a 404 error
error="$(echo $status | grep ERROR)"

# will contain information if there is another type of failure
failed="$(echo $status | grep failed)"

# will contain information if the file was empty
empty="$(find "$filedir"/ -maxdepth 1 -empty -iname '$final')"

}


#if [[ "$1" ]]; then
# check for help & setup parameters
case "$1" in 
	-h) 
		printhelp 
		exit
	;;
	
	--help) 
		printhelp 
		exit
	;;
	
	--setup) 
		setupConfFile
		exit
	;;
	
	--add) 
		echo -e "$2\t$3\t$4" >> "${tvrssdir}/feeds"
		echo "${2} feed added." 
		exit
	;;
	
	-i) 
		interAdd
		exit
	;;
	
	--log) 
		cat "$output" 
		exit
	;;
	
	--feeds) 
		cat "$tvrssdir"/feeds 
		exit
	;;
	
	--quick) 
		num_cycles=1
	;;
	
	--run)
		shopt -s extglob

		num_cycles="$2"

		while [[ "$num_cycles" != +([0-9]) ]]; do
			echo Number of cycles not recognized.
			read -p "How many times do you want tvrss to run?: " num_cycles
		done
		
		echo Will run $num_cycles times.
	;;
	
	*) printf "Available options: 
	'-h' | '--help'\t\t Help message 
	'--setup'\t\t Interactive setup 
	'--add'\t\t\t Add feed by commandline arguments
	'-i'\t\t\t Add feed interactively
	'--log'\t\t\t Display output log
	'--feeds'\t\t Current list of feeds
	'--quick'\t\t Runs script only once
	'--run'\t\t\t Runs the number of times specified"
	echo
	exit
	;;

esac

#fi


###################
### main exec loop
###################

## zero out pseudo-notifications
newtorrentscount=0

## check that no logs already exist. if they do, check that they are current 
## or put them with old logs
log_chk $out_log


#### default style ####
### run script for 1 hour in 15 minute intervals 
echo Number of cycles to run is $num_cycles
echo
if [ -z $num_cycles ]; then
	num_cycles=4
fi
echo Verifying the number of cycles - $num_cycles
echo

## for loop 1 ##
for ((i=1;i<=$num_cycles;i++)); do

	cycle=$i
	
	echo `date` >> "$output"
	
#	echo - Cycle is "$cycle" - >> "$output"
	echo Cycle is "$cycle"
#	echo >> "$output"
	echo
	
	echo Checking errored urls... >> "$output"
	echo Checking errored urls...
	echo
	
	touch "$url_store"

	if [[ "`cat $url_store`" ]]; then	
		cat "$url_store" > "$url_cache"

		if [ -f "$url_tmp" ]; then
			rm -f "$url_tmp"
		fi
		
		touch "$url_tmp"

## for loop 1-A ##	
		for url_entry in $(cat "$url_cache"); do
		
			showname="$(echo "$url_entry" | cut -f 1)"
			mediatype="$(echo "$url_entry" | cut -f 2)"
			tv_title="$(echo "$url_entry" | cut -f 3)"
			tv_date="$(echo "$url_entry" | cut -f 4)"
			tv_url="$(echo "$url_entry" | cut -f 5)"
			tv_form="$(echo "$url_entry" | cut -f 6)"
			
			oldurllist="${tvrssdir}/${showname}.log"
			touch "$oldurllist"
			
			rm -f /tmp/tmpxml &> /dev/null
		
			url_chk "$tv_url" "$mediatype" "$tv_title" "$showname" "$tv_date"
			
			if [[ "$error" || "$failed" || "$empty" ]]; then
				echo Still having trouble...
				echo
				echo -e "${showname}\t${mediatype}\t${tv_title}\t${tv_date}\t${tv_url}\t${tv_form}" >> "$url_tmp"
				echo Still having trouble with "$final" >> "$output"
				echo with url "$tv_url" >> "$output"
				echo >> "$output"
				
			else
				echo "$tv_url" >> "$oldurllist"
				echo "$tv_title" at >> "$output"
				echo "$tv_url" >> "$output"
				echo >> "$output"
			fi

## for loop 1-A done ##
		done
	
		cat "$url_tmp" > "$url_store"
		echo URL check complete. >> "$output"
		echo URL check complete.
		echo >> "$output"
		echo
		
	else
		echo No urls to check. >> "$output"
		echo No urls to check.
		echo >> "$output"
		echo
	
	fi
	
#	echo >> "$output"

## run subroutine to check show feed every 5 minutes (15 min * 1/5 runs/min = 3 runs)

## for loop 1-B ##	
	for ((x=1;x<=3;x++)); do

		subcycle=$x
		
#		echo -- Subcycle is "$cycle" - "$subcycle" -- >> "$output"
#		echo >> "$output"
		
		echo Subcycle is $cycle - $subcycle
		echo

	# for-each-tvshow-subscription-do loop

## for loop 1-B-a ##
		for tvshow in $(cat "$tvrssdir"/feeds); do
	
			# clearing temporary files and variables
			rm -f /tmp/tmpxml &> /dev/null
			
			showname="$(echo "$tvshow" | cut -f 1)"
			echo "$showname"
			
			mediatype="$(echo "$tvshow" | cut -f 2)" 
			echo "$mediatype"
			
			feedurl="$(echo "$tvshow" | cut -f 3)" 
			echo "$feedurl"
			
			fileform="$(echo "$tvshow" | cut -f 4)"
			echo "$fileform"
			
			oldurllist="${tvrssdir}/${showname}.log"
			touch "$oldurllist"
			
			oldurlstring=$(cat "$oldurllist")
			errorurlstring=$(cat "$url_store")
			
			count=0
	
			# start log feed
			echo `date` >> "$output"
			echo "$showname" >> "$output"
		
		
			# get and parse the rss feed
			currenturlstring="$(xmlstarlet sel --net -t -m "/rss/channel/item" -v "enclosure/@url" -o "" -n "$feedurl")"
		
			# check for URLs not in the log, get new ones, add the entry to the log file
			if [ -n "$currenturlstring" ]; then 

			# initiate loop counter for file title position
				loop=1
			
			# cache titles in file
				xmlstarlet sel --net -t -m "/rss/channel/item" -v "title" -n "$feedurl" | sed 's/\([(),:!?'"'"']\)//g' | sed -e 's/\&amp;/and/g' -e 's/ -//g' | sed 's/ /./g' | sed 's/\.\././g' > $name_tmp
			
			# cache publish dates
				xmlstarlet sel --net -t -m "/rss/channel/item" -v "pubDate" -n "$feedurl" > $date_tmp
			

#			cat $name_tmp

## for loop 1-B-a-i ##
				for url in $currenturlstring; do
					
					counter=$loop
					let "loop++"
					
					if [[ ! "$oldurlstring" =~ "$url" && ! "$errorurlstring" =~ "$url" ]]; then
					
						showtitle="$(sed -n "$counter"p "$name_tmp")"
					
					
						# check if last character of $showtitle is a "."
						last_char="$(echo "$showtitle" | awk '{print substr($0,length,1)}')"
						
						if [ "$last_char" = "." ]; then
							showtitle="$(expr "$showtitle" : '\(.*\).')"
						fi
					
					
						pubDate="$(expr "`sed -n "$counter"p "$date_tmp"`" : '.*,\(.*20[0-9][0-9]\).*')"
					
						showdate="$(date -d "$pubDate" +%Y%m%d)"
						
						echo Show $showtitle published on $pubDate aka $showdate
					
					# check file extension and media type, and download to correct directory
						url_chk "$url" "$mediatype" "$showtitle" "$showname" "$showdate" "$fileform"

				
					# if file does not exist or times out, save url to check later and log error to output
						if [[ "$error" || "$failed" || "$empty" ]]; then
							echo File not downloaded properly...
							
							if [[ "$error" || "$empty" ]]; then	
								echo "$final" does not seem to exist >> "$output"
								echo "at $url" >> "$output"
								
							else
								echo "$final" failed to download >> "$output"
								echo "from $url" >> "$output"
								
							fi
							
							echo Will check it later. >> "$output"
							
							echo -e "${showname}\t${mediatype}\t${showtitle}\t${showdate}\t${url}\t${fileform}" >> "$url_store"

					
					# else, copy url to old list and confirm in output
						else
							echo Success!
							echo
							
							echo "$url" >> "$oldurllist"
							echo "$showtitle" at >> "$output"
							echo "$url" >> "$output"
							echo >> "$output"
							
							let "newtorrentscount++"
							
							count=$newtorrentscount
					
							echo Count is $count with url \"$url\" in folder \"$filedir/\"
							echo
						fi
					fi
			
					
					# sleep 1

## for loop 1-B-a-i done ##
				done
				
				echo
				echo "Currenturlstring check is done."
				echo
			
				if [ "$count" -lt "1" ]; then
					echo No new files. >> "$output"
					echo No new files.
					echo >> "$output"
					echo
				fi
				
				echo Pausing for 1 second.
				sleep 1
				echo

			else
				echo "Xmlstarlet found no torrents in the feed $showname. Are you sure it is valid?" >> "$output"
				
				echo Pausing for 5 seconds.
				sleep 5
				echo
			fi
	
			echo Loop for $showname is complete.
			echo
			
## for loop 1-B-a done ##
		done
		
		
		echo Pausing for 1 second.
		sleep 1
		echo
		
#		echo >> "$output"

		# pseudonotification
		touch /tmp/newtorrents
		oldcount=$(cat /tmp/newtorrents)
		if [ -z "$oldcount" ]; then oldcount=0; fi
		newsum=$(($newtorrentscount+$oldcount))
		echo $newsum > /tmp/newtorrents
		
		echo "Done with Subcycle $cycle - $subcycle"
		echo

		if [ $num_cycles -eq 1 ]; then
			echo Quick run complete. && exit
		fi

		echo Pausing for 5 minutes.
		echo

## for loop 1-B-b ##		
		for ((a=1;a<=5;a++)); do
			if [ "$a" != "5" ]; then
				echo Minute $a

## for loop 1-B-b-i ##
				for ((b=1;b<=5;b++)); do
					sleep 10
					echo .

## for loop 1-B-b-i done ##
				done
			
			sleep 10
			echo
			
			else
				echo Minute 5
				sleep 10
				echo .
				sleep 10
				echo .
				sleep 10
				echo 30 seconds and counting...
				sleep 10
				echo 20 seconds and counting...
				sleep 10
				echo 10 seconds and counting...
				sleep 5

## for loop 1-B-b-ii ##		
				for ((c=1;c<=5;c++)); do
					echo "$((6-$c))"
					sleep 1
					
## for loop 1-B-b-ii done ##
				done
			fi

## for loop 1-B-b done ##
		done
		
		echo
		
## for loop 1-B done ##
	done

	echo "Done with Cycle $cycle"
	echo

## for loop 1 done ##	
done

IFS=$ORIGINAL_IFS
# echo IFS is $IFS

## swap logfiles if necessary
log_chk $out_log
log_cln "$com_dir"/logs/ "$out_log"

```


I couldn't find the original, so here's something very close if you're interested. I added the "cronlog" bits, as I was using cron at the time in order to run the script.

```

#!/bin/bash
# a tvrss.net torrent subscription script 
# 0.33 by chochem
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

printhelp () {
printf "tvrss is a tvrss.net subscription script. It will check your feeds for 
new torrent files (.torrent) and download them to a designated folder.
It can be run manually but it's probably preferable adding it as a 
crontab entry.

It requires a .tvrss configuration file in the home folder, so run it
once as 'tvrss --setup' to create one. This will allow you to designate 
two folders: a 'tvrss' folder where your sbusciption files and log files
(log of previously downloaded torrents) will be kept) and a 'watch' 
folder where the .torrent files will be saved.

Subscriptions are given to the script in the form of lines in the 'feeds' file,
a text file containing a single '[name][tab][feed url]' set per line. This should 
be kept in the 'tvrss' folder, and can be edited manually or created/expanded by 
using \"tvrss --add '[feed name of choice]' '[url]'\" (the quotes are important).

There is no notification of the user per se, but the number of downloaded torrents
is added to the number in a counting file in /tmp (thus it will be reset whenever /tmp 
is cleared, usually at reboot), making it available for other scripts/programs to pick 
up, e.g. 'watch'.

REQUIRES:
- xmlstarlet to parse the feed (apt package: xmlstarlet)
- suggested: a torrent client that lets you use a watch folder (torrent files
  in said folder are automatically loaded), e.g. rtorrent and utorrent.
"
exit
}

setupConfFile () {
rm ~/.tvrss &> /dev/null
printf "Entering tvrss configuration. This will produce a configuration file
(.tvrss) in your home directory in order to save your settings. Please see 
'tvrss --help' for more details."
echo
read -p "Where would you like tvrss to store your tvrss .feed and .log files 
(e.g. '/home/user/p2p/tvrss')? " tvrssdir
if [ ! -d "$tvrssdir" ]; then 
	read -p "$tvrssdir is not a directory - do you wish to create it now? (y/n) " reply
	if [ "$reply" = "y" ]; then 
		mkdir -p "$tvrssdir" && echo "tvrssdir=${tvrssdir}" >> ~/.tvrss
	else
		echo "Please try again" && exit
	fi
else 
	echo "tvrssdir=${tvrssdir}" >> ~/.tvrss
fi
echo
read -p "Where would you like tvrss to store your downloaded .torrent files 
(suggestion: the folder you have told your torrent client to watch for new 
.torrent files, e.g. '/home/user/p2p/watch')? " watchdir
if [ ! -d "$watchdir" ]; then 
	read -p "$watchdir is not a directory - do you wish to create it now? (y/n) " reply
	if [ "$reply" = "y" ]; then 
		mkdir -p "$watchdir" && echo "watchdir=${watchdir}" >> ~/.tvrss
	else
		echo "Please try again" && exit
	fi
else 
	echo "watchdir=${watchdir}" >> ~/.tvrss
fi
echo "Setup done" && exit
}

# check for conf file
ORIGINAL_IFS=$IFS
IFS=$'\n'
if [ -f ~/.tvrss ]; then
	. ~/.tvrss
else
	echo "Config file missing. Please run 'tvrss --setup' to create one."
	exit
fi

# check for help & setup parameters
case "$1" in 
	-h) printhelp;;
	--help) printhelp;;
	--setup) setupConfFile;;
	--add) echo -e "$2\t$3" >> "${tvrssdir}/feeds" && echo "${2} feed added." && exit;;
esac

# global initialisation
[ -d "$tvrssdir" ] || mkdir -p "$tvrssdir"
[ -d "$watchdir" ] || mkdir -p "$watchdir"
newtorrentscount=0

# for-each-tvshow-subscription-do loop
for tvshow in $(cat "$tvrssdir"/feeds); do

	# clearing temporary files and variables
	rm "$tvrssdir"/tmp/tmpxml &> /dev/null
	showname="$(echo "$tvshow" | cut -f 1)"
	feedurl="$(echo "$tvshow" | cut -f 2)"
	oldurllist="${tvrssdir}/${showname}.log"
	cronlog="${tvrssdir}/cron.txt"
	touch "$oldurllist"
	touch "$cronlog"
	oldurlstring=$(cat "$oldurllist")
	count=0
	
	# start log feed
	echo `date` >> "$cronlog"
	
	# get and parse the rss feed
	currenturlstring="$(xmlstarlet sel --net -t -m "/rss/channel/item" -v "link" -o "" -n "$feedurl")"
		
	# check for URLs not in the log, get new ones, add the entry to the log file
	if [ -n "$currenturlstring" ]; then 
		for url in $currenturlstring; do
			if [[ ! "$oldurlstring" =~ "$url" ]]; then
			#	torrentfilename="${watchdir}/${showname}_$(date +%y%m%e)_$(date +%H%M%S%N).torrent"
			#	wget -q -O "$torrentfilename" "$url"
				wget -q -P "${watchdir}" "$url"
				echo "$url" >> "$oldurllist"
				echo "$url" >> "$cronlog"
				let "newtorrentscount++"
			fi
			
			count=$newtorrentscount

		done
			
		if [ "$count" -lt "1" ]; then
			echo No torrents. >> "$cronlog"
		fi

	else
		echo "Xmlstarlet found no torrents in the feed $showname. Are you sure it is valid?" >> "$cronlog"
	
	fi
	
done
IFS=$ORIGINAL_IFS

# pseudonotification
touch "$tvrssdir"/tmp/newtorrents
oldcount=$(cat "$tvrssdir"/tmp/newtorrents)
if [ -z $oldcount ]; then oldcount=0; fi
newsum=$(($newtorrentscount+$oldcount))
echo $newsum > "$tvrssdir"/tmp/newtorrents

```

---

