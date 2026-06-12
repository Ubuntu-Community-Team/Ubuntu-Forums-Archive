---
title: "PDF concatenator"
date: 2011-12-26
forum: Tutorials
---

### Post by test666 on 2011-12-26
***********************************
edited after posting:
line
# caveat 3 : only for .pdf (underscore), not .PDF nor .Pdf or other oddities;
was substituted 
# caveat 3 : only for .pdf (lower cased), not .PDF nor .Pdf or other oddities;

Substituted end of line and added a second line:
If you don't have the Scripts folder in your home folder, just create it:
mkdir "~/.gnome2/nautilus-scripts"

Big MISTAKE, sorry. I substituted this line
2 - save it as "~/Scripts/pdf_concatenator.sh"
with this line
2 - save it as "~/.gnome2/nautilus-scripts/pdf_concatenator.sh"

and also substituted this line
chmod +x ~/Scripts/pdf_concatenator.sh
with this line
chmod +x "~/.gnome2/nautilus-scripts/pdf_concatenator.sh"

or the script will not run from Nautilus

This not NOT have happened. My humblest apologies.
***********************************


Warning : this was tested in Ubuntu 11.04.

I needed to join several sets of PDF files, each set in a folder.

So I made this script. It can work from the command line or you can launch it from Nautilus by 
righ-clicking the mouse > Scripts > pdf_concatenator.sh

If you don't have the Scripts folder in your home folder, just create it:
mkdir "~/.gnome2/nautilus-scripts"

1 - Copy/paste onto gedit
2 - save it as "~/.gnome2/nautilus-scripts/pdf_concatenator.sh"
3 - make it executable through nautilus (right mouse click on the filename > properties > permissions > allow executing file as program (tick it) and close properties)
or in a terminal window
chmod +x "~/.gnome2/nautilus-scripts/pdf_concatenator.sh"

Please read the comments (lines starting with #).

Copy/paste beyond this line onto gedit

[B]#!/bin/bash
# pdf concatenator
# 2011-December-26, by test666

#BSD license, modified

#Copyright (c) 2011, test666
# All rights reserved.

#Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:
#Redistributions of source code must retain the above copyright notice, this list of conditions, the "General Notes", "The Disclaimer and personal notes", the "Political note" and the following disclaimer.
#Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
#Neither the name of the <ORGANIZATION> nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

#THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

##################################################

# Disclaimer and personal notes
# 1 - there are rough edges, I'm forever a learning newbie...
# 2 - use at your own risk, because it may kill your machine
# 3 - Limited assistance, I just don't have the time
# 4 - don't contact me except in the Ubuntu Forum thread and even so I may never answer (see #3)
# 5 - #3 & #4 : sorry, not playing role as a snob, I am honestly deprived of time
# 6 - good luck

# Political note
# 1 - unity sucks, OMG Ubuntu/Canonical, where are you heading and will I follow you?
# 2 - #1 NOT flame bait, just venting, cool it, keep it to yourself, no issue here, move along

##################################################

# What does this script brings to the user?

# concatenates pdfs stored in the nautilus opened folder

# needed : ps2pdf (+ghostscript) & pdftk & zenity (not really needed)

# caveat 1 : do NOT use with password protected pdfs;
# caveat 2 : nautilus must have write permissions for the folder
# caveat 3 : only for .pdf (lower cased), not .PDF nor .Pdf or other oddities;

# shortcoming : no visible error messages !

# prior to pdf concatenator running, arrange the files the way you want
# them sorted along the final pdf file, by giving the file names a coherent 
# alphabethical order;

##################################################

# get the current folder name in nautilus and store it in the nautilus_path variable;
if [ "$NAUTILUS_SCRIPT_CURRENT_URI" == "x_nautilus_desktop:///" ]; then
	nautilus_path=$HOME"/Desktop"
else
	nautilus_path="`echo "$NAUTILUS_SCRIPT_CURRENT_URI" | sed -e 's/^file:\/\///; s/%20/\ /g'`"
fi

# create a temporary folder with a random number name for storing temporary files;
# this step is not really necessary, but it avoids going to /tmp or dirtying too much 
# the current folder with lots of temporary files intermingled with the "proper" files;
# using urandom allows the creation of a folder name that, with a very reasonable probability,
# is not available (too lazy to test the colision of folder names...);
# (sed used for trimming whitespaces);
# temp_folder: random numberized folder name (paranoid avoidance name colision version)
for a in {1..5}
   do
      temp_folder+=$(od -vAn -N4 -tu4 < /dev/urandom | sed 's/^[ \t]*//;s/[ \t]*$//')
   done
mkdir $nautilus_path/$temp_folder

#copy the pdf files to the temporary folder
cp *.pdf $temp_folder

# enter the temporary folder
cd $nautilus_path/$temp_folder

# fix filenames with spaces within the temporary folder (replacing with underscores),
# user must manually avoid duplicates
find "." -name "*pdf" -execdir rename 's/ /_/g' {} \; 

# build a list with the available pdf files;
files_list=$(ls)

# process the pdf files before pdftk touches them (necessary because pdftk obeys the 
# owner password flag (when set) and stops the processing);
# bonus: once in a while get smaller pdf files;
# dummy: intermediate file, random numberized name
dummy=$(od -vAn -N4 -tu4 < /dev/urandom | sed 's/^[ \t]*//;s/[ \t]*$//')
for single_file in $files_list
   do
      ps2pdf $single_file $dummy
      rm $single_file
      mv $dummy $single_file      
   done

# ok, lets create the final pdf from the temporary pdfs and store it in the nautilus current folder;
# yes, indeed I chose a very odd file name, but at least if nautilus is sorting by name,
# the file will most likely be placed at the top (or bottom) of the files and can be easily spotted;
# rename this file and move it to wherever you want it to stay;
# ;-> replace my odd name for this file with your very own creative wording;
odd_name=_____0000_____concatenated_pdfs.pdf
pdftk *.pdf cat output $odd_name

# move the final pdf to the nautilus current folder
mv $odd_name ..

# exit the temporary folder
cd ..

# remove the temporary folder and its files
rm -r $temp_folder

# inform the user that the job is finished;
zenity --info --title="     pdf concatenator" --text="==========has just finished=========="

# bye now
exit
[/B]

---

