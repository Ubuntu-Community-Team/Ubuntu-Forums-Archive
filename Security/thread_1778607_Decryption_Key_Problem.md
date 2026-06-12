---
title: "Decryption Key Problem"
date: 2011-06-09
forum: Security
---

### Post by rodrigr2006 on 2011-06-09
Hello all!....This issue involves a Lenovo Ideapad U330 and Ubuntu 10.04
I was using cryptkeeper to encrypt folders.  I had 3 encrypted folders, 1-in a mountable hard drive partition of the laptop's hard drive; 2-in an SD card; and 3-in a removable hard drive.  In other words none were part of filesystem all were removable.  I upgraded to 10.10 and my internet quit working, went back to 10.04 and now I am only able to open one of the 3 folders (the one in the separate partition in the laptop's hard drive aka #1).  The other 2 folders wont open, the one on the SD card and the one in the removable HD.  I am getting the message "error decoding volume key, password incorrect".  I am not a smart man so I rely on a handful of passwords for ALL my password protected items, I have used the same ones for years so I am 100% certain I am using the correct password.  I can see the encrypted folders and files but of course I cannot read them.  Can anyone explain to me what has happened and does anyone have any idea how I could fix this problem.  Thank you in advance.

---

### Post by rodrigr2006 on 2011-06-10
well....i think i might have found a problem....

am going to post what i have done and what i have found because as i work the problem i am running into some difficulty and i am hoping some kind soul will help me

as i read hundreds of other post i am beginning to think cryptkeeper may be improperly installed.  if that is the case i do not understand why i can open one of my encrypted folders but not the other two.  so rather than using the ubuntu software center, the means which i used to install cryptkeeper, i went to the tom morton website and i am trying to follow these instructions:

  build from source you will need: 
[LIST]
[*]libgtk+ >= 2.8
[*]gconf 2.0
[*]encfs and fuse (I used fuse 2.6.3)
[/LIST]
   On ubuntu you can install encfs like this: 
[INDENT] 	 	sudo aptitude install encfs 	
sudo echo "fuse" >> /etc/modules 	
sudo modprobe fuse 	
sudo addgroup <your username> fuse
[/INDENT]
i wont be building from source but i never did the fuse installation....so i installed fuse-2.8.5 per its website's instructions.  i then began to run into some problems

papi@papi-laptop:/$ sudo echo "fuse" >> /ect/modules
bash: /ect/modules: No such file or directory
papi@papi-laptop:/$ sudo echo fuse >> /ect/modules
bash: /ect/modules: No such file or directory

i did some more reading and i figured the message meant there was no /ect/modules folder so i tried to make one

papi@papi-laptop:~$ sudo mkdir /ect/modules
[sudo] password for papi: 
mkdir: cannot create directory `/ect/modules': No such file or directory
papi@papi-laptop:~$ cd /
papi@papi-laptop:/$ sudo mkdir ect/modules
mkdir: cannot create directory `ect/modules': No such file or directory
papi@papi-laptop:/$ sudo mkdir /ect/modules
mkdir: cannot create directory `/ect/modules': No such file or directory

as you can see i tried to do it different ways

i am not familiar with command lines i have read the official ubuntu documentation which is where i learned the mkdir command...could someone help please

for grins i ran the next command on the list to see what would happen

papi@papi-laptop:/$ sudo modprobe fuse
FATAL: Module fuse not found.

ok, that is what i have done so far any help would be appreciated

---

### Post by JoBangles on 2011-07-21
I could not change to directory (No permission), also encfs would not recognize the USB harddrive even though I could view the files in Nautilus. This happened twice and I found that on both occasions the folder had a slight name change when I viewed details in "Disk Utility". The folder "Linux" had been changed to "Linux__". When I used this name, no problem.

---

### Post by rodrigr2006 on 2011-07-21
Thank you for the reply.  Well concerning the problem of not being able to build the directory, it was pointed out to me that ect should be etc.  Well that has worked and I was able to make the directory.  Still I cant open the encrypted folder. 

Now let me make sure I understand you.  So what you are saying is that you changed the name of the encrypted folder to linux_?  The names of the external drive and the sd card appear to be correct under "disk utility".  The sd card just shows as another hard drive, its not listed in the peripherals.

---

