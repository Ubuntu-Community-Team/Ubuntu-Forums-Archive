---
title: "[SOLVED] What Codec is this Video?"
date: 2008-12-17
forum: Ubuntu Studio
---

### Post by Kissell on 2008-12-17
I have a directory of videos that have been encoded over the years in different audio and video formats...  unfortunately they were all just labelled with a .avi extension.  

Is there a way I can get a directory listing showing me the stats about all the videos?  Essentially I'd like to get an output like the "ls" command, but have more fields, have it tell me if the video is DivX or XVid, have it tell me if the audio is MP3 or AC3, maybe even telling me the frame pixel heightxwidth would be nice...  anyone know of a way to do this quickly for a whole folder?  command line would be perfect, but gui will work too, whatever works without having to individually click on each file.

---

### Post by kostkon on 2008-12-17
I am pretty sure then that you'll like [*themonospot*]("http://www.integrazioneweb.com/themonospot/")! They offer Ubuntu debs.

---

### Post by Kissell on 2008-12-17
That's pretty cool, except it seems it will only show me info about one video at a time...  that's taking forever, as I've got a long list to go through.

The problem is that some of my videos won't play audio with a media extender, it seems that the ones that have no sound are 6-channel AC3 and the ones that work are 2-channel MP3.  

So what I'd really like is to do a directory listing, have one filename per line, and also list what audio codec it uses on that same line/row...  That way I can quick count of how many of the videos we're talking about here that aren't working, and which ones they are...  and then I'll be able to make a decision if I want to re-encode those or else just get a different media receiver.

---

### Post by nowardev on 2008-12-18
you can use a bash script 

[http://www.cli-apps.org/content/show.php/Fva+(Fuoco+Video+analyzer)?content=89259](http://www.cli-apps.org/content/show.php/Fva+(Fuoco+Video+analyzer)?content=89259)

---

### Post by Kissell on 2008-12-18
Thanks, that got me most of the way!

Except that script's output was too verbose, lots of lines of text.

I modified that script a bit, to create a single line of output.  This allowed me to run the script on every file in the folder and output the results to a text file that was comma field delimited for input into a spreadsheet.  Also stripped out header info and added filename to the output.

I've attached the modified script in case someone else ever needs to do this...  

Also, I had a quick newbie question, I know there's a way to do this I just don't know how...  to get this to work I did a "find . > runme" then edited the runme file in gedit and used file/replace to quickly create a script that ran this videoinfo script once per file in that list.  So that I could do "runme > text.csv" to get the spreadsheet I wanted.  How would I do that quicker from the command line?  without the middle step of creating the runme file?  isn't there an easy way to pipe the directory listing as an argument of a recursively run bash script and output it to a single file from one command line command?  I love ubuntu/linux command line power, but still not an advanced user of it yet.

:guitar:

---

