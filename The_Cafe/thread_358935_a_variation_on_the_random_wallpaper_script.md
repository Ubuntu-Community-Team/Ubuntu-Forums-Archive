---
title: "a variation on the random wallpaper script"
date: 2007-02-11
forum: The Cafe
---

### Post by cafine-fish on 2007-02-11
i had done allot of searching and couldn't find a random wallpaper script that behaved the way i wanted it to.  so i wrote my own :) and thought i would share it just in case some one else is looking for what i was.  i am also a little proud of this being that i am not really a programmer.

first off i wanted a random wallpaper changer.  there are a number of options out there to do just this.  but i also wanted to be sure that all my wonderful wallpapers had equal screen time.  basically i wanted to make a randomized "play list" of wallpapers to go through one at a time and then reshuffle when the last one was "played".  randomizing the play list was the hard part.  in the end i installed the randomize-lines package.  which does exactly what i needed. so here is the code:
```
#!/bin/bash

#file locations using full path for crontab execution
ImagePath=/home/USERNAME/pictures/wallpaper   #directory of images to use
DataFile=/home/USERNAME/bin/wpc.data          #where to keep the list of images
TempFile=/home/USERNAME/bin/wpc.temp          #temp file to use in removing a line from the list of images

#function to make the randomized list of images
make_list ()
{
  ls $ImagePath > $DataFile  #get a list of images
  rl $DataFile > $TempFile   #mix them all up
  mv $TempFile $DataFile     #make the mixed up list the list to use
}

#function to change the wallpaper, and update the list of images
change_wall ()
{
  ImageFile=$(sed -n '1p' $DataFile)  #get the first line from the list of images
  gconftool -t string -s /desktop/gnome/background/picture_filename "$ImagePath/$ImageFile"  #change the wallpaper
  gconftool -t string -s /desktop/gnome/background/picture_options "centered" #it's how i like my wallpapers
  sed -e '1d' $DataFile > $TempFile  #remove the image we just used
  mv $TempFile $DataFile  #update the image list
}

if test ! -s "$DataFile"  #if the image list doesn't exist we make it
then
make_list
fi

change_wall               #actually change the wallpaper

```
copy and past the code into your text editor of choice.  save it with a unique name! i used wpc(for WallPaper Changer)
be sure to change out the USERNAME to your actual user name, and make sure the directory names are correct.
make it executable by either ```
chmod 754 wpc
``` or ```
chmod +x wpc
```
and set up crontab to run it as you see fit :).  i go with every 10 minutes.  questions? comments? suggestions?  it is a forum so feel free to post a reply.

---

### Post by cmulax on 2007-02-13
Hey, im interested in running your script, but im not really sure how to set it to run every x minutes.  I've tried messing around with crontab but nothings working :(  so... sorry for a noob question but how do you set how often crontab runs a script?

thanks in advance-

---

### Post by cafine-fish on 2007-02-14
noob questions are no problem, every body had to start at the beginning at some point in time.  
to set up crontab you first get to a console and type "crontab -e" 
that should bring up a simple text editor with a line like "# m h dom dow  command".  m is for minutes, h for hours, dom for day of month, dow for d of week, command is the command it will execute.  so to run the script every ten minutes you would type in "*/10 * * * * /home/user/wpc".  the */10 is the important bit that tells crontab to execute /home/user/wpc every minute that is evenly divisible by ten, or 0, 10, 20, ...  if you changed it to */5 it would run at 0,5,10,15, ... though if you set it to just 5 it would run the script at 5 minutes after every hour. 
once you have edited crontab to your liking press ctrl+x then y to exit and save the changes.  
i hope that helps. if not let me know and i will be glad to help you out the best that i can :)

---

### Post by lykeion on 2008-08-26
Thanks for the script. I might add that you need to install package randomize-lines to get the command rl.

---

