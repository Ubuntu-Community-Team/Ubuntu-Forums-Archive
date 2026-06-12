---
title: "Shantz Copy Basket: Easing out your copy/move woes"
date: 2008-03-17
forum: The Cafe
---

### Post by shantzg001 on 2008-03-17
[http://tech.shantanugoel.com/projects/misc-stuff/shantz-cp-basket](http://tech.shantanugoel.com/projects/misc-stuff/shantz-cp-basket)
Introduction:

I’m sure you have copied/moved files on your computer from one place to another. And I’m sure often you have to do more than just “single-shot” copying that is copy a few files to one place, move a few to another, and copy yet some more to one more location. Well, I had to do this quite a few times (e.g. I ran out of disk space recently on a partition and had to empty out my “Movies” and “Songs” folders to move a few movies/songs each to all other partitions/disks according to the space available). Hence, I wrote this little command line program, which behaves like a basket. 

You can put any number of files from any number of different locations into it in a single shot. It will store their locations and give them an ID. Now, you can copy/move those files to differnet destinations based on their IDs.

Requirements:

The program is multi-platform compatible as I wrote it in Perl and took care of using portable methods only. So, if you have perl installed, you can just download the above perl file and install “File-Copy-Recursive” Module (rest are most probably installed already) and you are good to go.

For people who don’t have perl, I’ve uploaded the stand-alone packages for windows as well as linux users. Download according to your platform and you can use them straight away without any hassles.

For the record, I tested this script as well as the executables on Windows XP SP2 and Ubuntu Feisty Fawn 7.04.

Usage:

shantz-cp [OPTION] [FILE] [DESTPATH]

Options:
    -l, --list           List files in the basket.
                         Doesn't take [FILE]/[DEST] Arguments
    -a, --add        Add file(s) to the basket.
                         Provide absolute/relative path of file(s) as argument
    -r, --remove    Remove file(s) from the basket
                         Provide absolute/relative path of file(s) as argument
    -ri, --removeid Remove file(s) from the basket using their basket id
                         Provide id(s) of file(s) as argument
    -pi, --pasteid   Paste a file from the basket to the given destination
                         Provide file id(s) to be pasted followed by relative/absolute path of destination
    -m, --move      Use this option along with paste option to move the files instead of copy

Arguments:
    [FILE]           Any number of files can be mentioned
                       Paths can be relative to current dir or absolute
                       Cannot use with list option
    [DESTPATH]  Only 1 path can be given
                       Path can be relative to current dir or absolute
                       Can be used only with paste option

Notes:
1. Only 1 option can be used at a time, except for the "move" and "pasteid" combinations
2. For any queries/help/updates, please post a comment here.

Examples: 
```
   shantanu@wtf:~/stuff$ ./shantz-cp -a *
       File /home/shantanu/stuff/conky.sh already exists at ID 1
       File /home/shantanu/stuff/hosts.txt already exists at ID 0
       File /home/shantanu/stuff/movie2mobile.py already exists at ID 2
      Added /home/shantanu/stuff/places_menu.txt at ID 3
      Added /home/shantanu/stuff/rapt at ID 4

      shantanu@wtf:~/stuff$ ./shantz-cp -l
      No of files in basket: 5
      File ID. 0: /home/shantanu/stuff/hosts.txt
      File ID. 1: /home/shantanu/stuff/conky.sh
      File ID. 2: /home/shantanu/stuff/movie2mobile.py
      File ID. 3: /home/shantanu/stuff/places_menu.txt
      File ID. 4: /home/shantanu/stuff/rapt
       
      shantanu@wtf:~/stuff$ ./shantz-cp -ri 2
      Removed /home/shantanu/stuff/movie2mobile.py from basket
       
      shantanu@wtf:~/stuff$ ./shantz-cp -pi 1 3 temp/
      Copied /home/shantanu/stuff/conky.sh to /home/shantanu/stuff/temp/
      Copied /home/shantanu/stuff/places_menu.txt to /home/shantanu/stuff/temp/
       
      shantanu@wtf:~/stuff$ ./shantz-cp -m -pi 0 /home/shantanu
      Moved /home/shantanu/stuff/hosts.txt to /home/shantanu/


```
Free Downloads and support at [Shantz Copy Basket Home Page]("http://tech.shantanugoel.com/projects/misc-stuff/shantz-cp-basket")

---

### Post by shantzg001 on 2008-03-23
Added the windows version to the home page as well.
And yeah, it saves files operations across reboots. yes, the basket will remain intact even if you shutdown the computer and when u log back in, you can continue working on the files.

---

