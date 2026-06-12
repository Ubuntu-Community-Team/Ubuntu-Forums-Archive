---
title: "Bash Script to Set GNOME 3 Wallpaper to Bing Pic of the Day"
date: 2012-10-20
forum: The Cafe
---

### Post by SeanKD on 2012-10-20
I don't know about anyone else, but I think it's a shame that Microsoft has made it so that only Windows 7 & 8 users can have their wallpaper automatically set to a high resolution version of the daily Bing wallpaper.  So, I spent the better part of 24 hours putting together a bash script that determines the URL for the daily Bing wallpaper, downloads it to a folder of the user's choice, and then sets the GNOME 3 wallpaper to the daily Bing wallpaper.

Just open your favorite text editor, copy and paste the code, and save it as 'some-file.sh' somewhere in your home directory.  Then be sure to run a ```
chmod +x some-file.sh
``` to make it executable and ```
crontab -e
``` to create a crontab to run the script once a day.

*This script requires that curl be installed:
```
sudo apt-get install curl
```I have only had the opportunity to test this script on Ubuntu 12.10 32-bit.

I hope you enjoy using this script as much as I enjoyed making it.

** I am very new to bash scripting and I'm sure my code is less than elegant - to put it politely.  If anyone has any suggestions on how to improve and tighten the code I would appreciate hearing from you.

**NOTE** If the script code has changed since you were last here, it is because I have been working on improving and tightening the code.  Just open your version of the file in your favorite text editor and replace everything with the code listed here.

**Code last updated 11-Jul-2013 Minor improvements based upon suggestions from other forum members, including falling back to the default resolution if the desired resolution is not available for download.

```
#!/bin/bash

# $bing is needed to form the fully qualified URL for
# the Bing pic of the day
bing="www.bing.com"

# $xmlURL is needed to get the xml data from which
# the relative URL for the Bing pic of the day is extracted
#
# The mkt parameter determines which Bing market you would like to
# obtain your images from.
# Valid values are: en-US, zh-CN, ja-JP, en-AU, en-UK, de-DE, en-NZ, en-CA.
#
# The idx parameter determines where to start from. 0 is the current day,
# 1 the previous day, etc.
xmlURL="http://www.bing.com/HPImageArchive.aspx?format=xml&idx=0&n=1&mkt=en-US"

# $saveDir is used to set the location where Bing pics of the day
# are stored.  $HOME holds the path of the current user's home directory
saveDir=$HOME'/Pictures/BingDesktopImages/'

# Create saveDir if it does not already exist
mkdir -p $saveDir

# Set picture options
# Valid options are: none,wallpaper,centered,scaled,stretched,zoom,spanned
picOpts="zoom"

# The desired Bing picture resolution to download
# Valid options: "_1024x768" "_1280x720" "_1366x768" "_1920x1200"
desiredPicRes="_1920x1200"

# The file extension for the Bing pic
picExt=".jpg"

# Extract the relative URL of the Bing pic of the day from
# the XML data retrieved from xmlURL, form the fully qualified
# URL for the pic of the day, and store it in $picURL

# Form the URL for the desired pic resolution
desiredPicURL=$bing$(echo $(curl -s $xmlURL) | grep -oP "<urlBase>(.*)</urlBase>" | cut -d ">" -f 2 | cut -d "<" -f 1)$desiredPicRes$picExt

# Form the URL for the default pic resolution
defaultPicURL=$bing$(echo $(curl -s $xmlURL) | grep -oP "<url>(.*)</url>" | cut -d ">" -f 2 | cut -d "<" -f 1)

# $picName contains the filename of the Bing pic of the day

# Attempt to download the desired image resolution. If it doesn't
# exist then download the default image resolution
if wget --quiet --spider "$desiredPicURL"
then

    # Set picName to the desired picName
    picName=${desiredPicURL##*/}
    # Download the Bing pic of the day at desired resolution
    curl -s -o $saveDir$picName $desiredPicURL
else
    # Set picName to the default picName
    picName=${defaultPicURL##*/}
    # Download the Bing pic of the day at default resolution
    curl -s -o $saveDir$picName $defaultPicURL
fi

# Set the GNOME3 wallpaper
DISPLAY=:0 GSETTINGS_BACKEND=dconf gsettings set org.gnome.desktop.background picture-uri '"file://'$saveDir$picName'"'

# Set the GNOME 3 wallpaper picture options
DISPLAY=:0 GSETTINGS_BACKEND=dconf gsettings set org.gnome.desktop.background picture-options $picOpts

# Exit the script
exit
```[/SIZE]

---

### Post by yaronf on 2013-01-10
Thanks, this is nice. I had to add --create-dirs to the second curl command (Ubuntu 12.04) because it tries to create a directory hierarchy - and fails silently if it cannot do so.

I also added toward the end, so that we don't accumulate pictures indefinitely:

# Remove pictures older than 7 days
find $saveDir -atime 7 -delete

---

### Post by rahst12 on 2013-01-17
I added the aforementioned --create-dirs and removal of pictures to the script for ease of copy/paste.

> #!/bin/bash

# $bing is needed to form the fully qualified URL for
# the Bing pic of the day
bing="www.bing.com"

# $xmlURL is needed to get the xml data from which
# the relative URL for the Bing pic of the day is extracted
#
# The mkt parameter determines which Bing market you would like to
# obtain your images from.
# Valid values are: en-US, zh-CN, ja-JP, en-AU, en-UK, de-DE, en-NZ, en-CA.
#
# The idx parameter determines where to start from. 0 is the current day,
# 1 the previous day, etc.
xmlURL="http://www.bing.com/HPImageArchive.aspx?format=xml&idx=0&n=1&mkt=en-US"

# $saveDir is used to set the location where Bing pics of the day
# are stored.  $HOME holds the path of the current user's home directory
saveDir=$HOME'/Pictures/BingPics/'

# Create saveDir if it does not already exist
mkdir -p $saveDir

# Set picture options
# Valid options are: none,wallpaper,centered,scaled,stretched,zoom,spanned
picOpts="zoom"

# The desired Bing picture resolution to download
# Valid options: "_1024x768" "_1280x720" "_1366x768" "_1920x1200"
picRes="_1920x1200"

# The file extension for the Bing pic
picExt=".jpg"

# Extract the relative URL of the Bing pic of the day from
# the XML data retrieved from xmlURL, form the fully qualified
# URL for the pic of the day, and store it in $picURL
picURL=$bing$(echo $(curl -s $xmlURL) | grep -oP "<urlBase>(.*)</urlBase>" | cut -d ">" -f 2 | cut -d "<" -f 1)$picRes$picExt

# $picName contains the filename of the Bing pic of the day
picName=${picURL#*2f}

# Download the Bing pic of the day
curl --create-dirs -s -o $saveDir$picName $picURL

# Set the GNOME3 wallpaper
DISPLAY=:0 GSETTINGS_BACKEND=dconf gsettings set org.gnome.desktop.background picture-uri '"file://'$saveDir$picName'"'

# Set the GNOME 3 wallpaper picture options
DISPLAY=:0 GSETTINGS_BACKEND=dconf gsettings set org.gnome.desktop.background picture-options $picOpts

# Remove pictures older than 7 days
find $saveDir -atime 7 -delete

# Exit the script
exit

---

### Post by SeanKD on 2013-01-21
Thanks for the help! :)

---

### Post by Seena85 on 2013-03-30
Good job with the script! 

I think the problem with the "dirs" is because of a small bug.

```

# Instead of picName=${picURL#*2f}
picName=${picURL##*/}

```

I also went a little further and extracted the description of the image which is actually in the EXIF data and write it in the right bottom corner of the wallpaper. You need "exiftool" and "imagemagick" for that. My script can be found here: [http://pastebin.com/iSDF10DK](http://pastebin.com/iSDF10DK)

---

### Post by F.G. on 2013-03-30
Hi SeanKD, nice job with the script, i particularly like the fact that you've put decent comments in, with details about other options.
for anyone using openbox, this script can be adapted to use feh.first install it:
```
apt-get install feh
```
comment out the GNOME stuff:
```
# Set the GNOME3 wallpaper 
# DISPLAY=:0 GSETTINGS_BACKEND=dconf gsettings set org.gnome.desktop.background picture-uri '"file://'$saveDir$picName'"'

# Set the GNOME 3 wallpaper picture options
# DISPLAY=:0 GSETTINGS_BACKEND=dconf gsettings set org.gnome.desktop.background picture-options $picOpts
```
add this option instead:
```
# Option for openbox
feh --bg-scale $saveDir$picName
```
and voila, openbox portability!

---

### Post by F.G. on 2013-03-30
ok, i removed this post, as it was no longer relevant.

---

### Post by kevdog on 2013-03-30
Anyway to modify this script for cinammon?

---

### Post by F.G. on 2013-04-01
> **kevdog said:**
> Anyway to modify this script for cinammon?
Hi Kevdog, 
a quick google turns up this: 
[http://unix.stackexchange.com/questions/59653/change-desktop-wallpaper-from-terminal](http://unix.stackexchange.com/questions/59653/change-desktop-wallpaper-from-terminal) 
looks like you can use a few different tools, including feh if you like. 
though you will need to change your desktop settings.

---

### Post by SeanKD on 2013-06-28
Thanks for the help, guys!  I have updated the script so that it checks to see if the image exists at the desired resolution.  If it does, the image is downloaded and set as the wallpaper.  If not, the image is downloaded at the default resolution and set as the wallpaper.

---

### Post by SeanKD on 2013-11-26
I'm running Linux Mint 15 64-bit with cinnamon 2.0 and the script works fine for me.

---

