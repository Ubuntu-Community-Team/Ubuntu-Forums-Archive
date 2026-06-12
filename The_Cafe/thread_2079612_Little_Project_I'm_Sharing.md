---
title: "Little Project I'm Sharing"
date: 2012-11-02
forum: The Cafe
---

### Post by gerowen on 2012-11-02
I'm not a professional programmer.  I have some basic knowledge of Python and Bash, and use them to occasionally write little tools that make my life easier, but aren't quite of a complexity to warrant a project page on Launchpad.

Hence I just created a Wiki page for myself where I'm going to try and collect a lot of the information I've thrown around the internet over the years that can be of use such walkthroughs, these scripts, etc..  I'm getting ready to go to bed, but I just used one of my tools and updated it to fix a mistake in some of the general information and thought I'd share it with you.

I call it CheckMD5, and I wrote it because at the time I couldn't find something that did just what I wanted it to do.  There were tools that would calculate an MD5 and give it to you, but there was nothing (that I could find) that made it easy to just click through and do the comparison against an original for you instead of you going character by character to find out that the last two characters were the only ones different.

This is just a Bash script that uses Zenity to draw a GUI, so just copy and paste the code below into a text document and save it with a .sh extension and you're ready to roll.  Hope somebody finds this useful.

```

#!/bin/bash
#CheckMD5 - This is a tool to compare the MD5 checksum of a given file against another file, or against a given original checksum.
############################################
#     CheckMD5 - MD5 Verification Tool     #
#            Marcus Dean Adams             #
#        marcusdean.adams@gmail.com        #
#         Updated 2 November 2012          #
############################################

#Retrieves location of file to be checked and generates an MD5 checksum.

zenity --info --text="CheckMD5 will compare the MD5 checksum of a file against an original.\n\nDepending on the size of the file(s) selected, it may take a long time to calculate the MD5 Checksum, and your computer may appear to freeze.  Please be patient.\n\nPlease select the file you wish to check." --title="CheckMD5 by Marcus Adams"

infile=$(zenity --file-selection --filename=~/Desktop --title="CheckMD5 - Select a file to check")

md5=$(md5sum "$infile" | cut -b -32)

#Determines what the file should be compared to.

options=("Compare to Original File" "Compare to Entered Checksum")

opt=$(zenity --list --title="CheckMD5 - Select an Option" --text="Pick an option:" --column="Options" "${options[@]}");

#Prompts the user for an original file to compare the one in question against, and generates its checksum.

if [ "$opt" == "${options[0]}" ]
then
newfile=$(zenity --file-selection --filename=~/Desktop --title="CheckMD5 - Select a file to compare to")
md5correct=$(md5sum "$newfile" | cut -b -32)
original=$"of $newfile"
fi

if [ "$opt" == "${options[1]}" ]
then
md5correct=$(zenity --entry --title="CheckMD5 - Enter MD5 Checksum" --text="Enter the checksum to compare the file to:")
original=$"manually entered."
fi

#Conditional statements that determine which message to display based on whether the checksums match.

if [ "$md5" == "$md5correct" ]
then
	zenity --info --title="CheckMD5 - SUCCESS!" --text="SUCCESS!\n\nThe MD5 checksum of the file you selected matches the MD5 checksum you entered.\n\nChecksum of $infile:\n\n$md5"
fi

if [ "$md5" != "$md5correct" ]
then
	zenity --info --title="CheckMD5 - Checksum Mismatch!" --text="FAILED!\n\nThe MD5 checksum of the file you selected does not match the MD5 checksum you entered.\n\nChecksum of $infile:\n\n$md5\n\nChecksum $original:\n\n$md5correct\n\nThis indicates that at some point the file in question was corrupted, and is not identical to the source file you compared it to."
fi

exit

```

---

