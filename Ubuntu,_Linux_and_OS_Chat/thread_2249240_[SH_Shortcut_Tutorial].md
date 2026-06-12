---
title: "[SH Shortcut Tutorial]"
date: 2014-10-20
forum: Ubuntu, Linux and OS Chat
---

### Post by Roketteere on 2014-10-20
Open terminal

type: nano ~/.bashrc
Press enter

Go to the end of the text document by hitting page down until you get below all the text

Next press the enter key

----
PAUSE READ AND UNDERSTAND
----

No I have a file called Pycharm.sh

This opens up my Pycharm program

Instead of having to go to terminal and using cd and going into the directory where that file is
and then being able to type ./Pycharm to open it, we will just make it known to terminal its location.

By adding the folder location to where the .sh file is, terminal will look there anytime you execute ./ 
to open a .sh file. 

So here is a common every day life example of simplifying what we are doing.

When the door bell rings

You go to the front door and check who is there

You never check the back door or the basement or the fridge

Yes a few extreme locations but just hang with me

So now I will tell you what is what in this example


Using my program from above:

--Door Bell Ringing => me typing ./Pycharm

--Checking the front door => Terminal looking for the file Pycharm.sh to execute

--back door, basement, fridge => folders where .sh files may be. but my file is in a folder called "Programming" which i created in my home folder

So now we want to change the way we look to see who is ringing the door bell. So we need to make a note and
put it on the front door. Now we can put on the note, "look in the fridge too just in case"

So lets make believe that the fridge is my Programming folder

So now this note is on the door. And every time you go to check the door you will see the note and know to check the fridge too

You can just keep adding more locations to your note and check those locations every time as well.

So we will do this for any .sh file anywhere in our computer that we want to access in terminal without having to go the folders
location everytime we want to open that file
----
END OF PAUSE 
---


Now here is what I typed to set the note for terminal to remember to check this location too whenever I type ./ and then the program/filename

export PATH=/bin:/home/Programming/:$PATH


breakdown:

export (hey create a shortcut to our .sh file)

PATH (Where do we put this shortcut?)

/bin (here in this folder)

:/home/Programming/ (where is the original .sh file?)

:$PATH (ends the file path)

So for you do this:

export PATH=/bin:

then this /home/Programming/ is going to be different for you

put the location for your .sh

remember to not put /location/file.sh just /location/

dont forget to add 

:$PATH

at the end.

When finished, hold the windows button the hit x at the same time

it will as you to save it. save it and now go to terminal

type in your ./filename and it should now open your program/file without having to go directly into that folder anymore

---

