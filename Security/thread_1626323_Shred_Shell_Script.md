---
title: "Shred Shell Script"
date: 2010-11-20
forum: Security
---

### Post by thotheolh on 2010-11-20
Hi. I created a bash script to utilize the built-in 'shred' tool to shred files. This is my first time building a bash script. Below is my bash script:

```

#! /bin/sh

echo "Enter file path:\c"
read filepath

echo "Enter number of overwrites: [recommended >= 10] \c"
read overwriteAmt

echo "Selected file/folder: $filepath"
echo "Num. of overwrites: $overwriteAmt"

if [ -f $filepath ]
    then
        "Selected is a file"
        status = "file"
elif [ -d $filepath ]
    then
        "Selected is a folder"
        status = "folder"

    ## Ask if user wants to delete a child files and folders in the folder
     echo "Do you want all the child files/folders be deleted ? [Y/N]: \c"
     read deleteChildren
fi

if [ status == 'folder' && $deleteChildren == 'Y' ]
    then
        ## delete all childrens in a loop
        for childfile in `dir -d *` ; do
            shred -u -z -n $overwriteAmt $childfile
        done
elif [ status == 'folder' && deleteChildren == 'N' ]
    then
        ## delete the immediate files in the folder
        for childfile in `dir -d *` ; do
            if [ -f childfile ]
                then
                    shred -u -z -n $overwriteAmt $childfile
            fi
        done    
elif [ status == 'file']    
    then
        shred -u -z -n $overwriteAmt $filepath
fi

```But when I run it ... it results in the below ...

```

 ./Shredder.sh 
Enter file path:/home/MyLinux/Desktop/Shred
Enter number of overwrites: [recommended >= 10] 
Selected file/folder: /home/MyLinux/Desktop/Shred
Num. of overwrites: 
./Shredder.sh: 24: Selected is a folder: not found
status: Unknown job: =
Do you want all the child files/folders be deleted ? [Y/N]: Y
[: 44: missing ]
[: 44: missing ]
[: 44: missing ]


```Why is there some "[: 44: missing ]" messages and nothing was shredded ?

By the way, is there a shred tool GUI front end that makes shredding more easily used ?

---

### Post by emiller12345 on 2010-11-20
I made some simple changes to this, one of them effective commentting out the actual shred commands until you get the syntax corrected. you wouldn't want to accidently shred your root dir! This still needs work, but you could check out kgpg.  

```
#!/bin/bash

echo -e "Enter file path:\t\c"
read filepath

echo -e "Enter number of overwrites: [recommended >= 10]\t\c"
read overwriteAmt

echo -e "Selected file/folder: $filepath"
echo -e "Num. of overwrites: $overwriteAmt"

if [ -f $filepath ]; then
        echo -e "Selected is a file"
        status="file"
elif [ -d $filepath ]; then
        echo -e "Selected is a folder"
        status="folder"

    ## Ask if user wants to delete a child files and folders in the folder
     echo -e "Do you want all the child files/folders be deleted ? [Y/N]: \c"
     read deleteChildren
fi

if [ "$status" = "folder" -a "$deleteChildren" = "Y" ]; then
        ## delete all childrens in a loop
        for childfile in `dir -d $filepath/*` ; do
            echo -e "shred -u -z -n $overwriteAmt $childfile"
        done
elif [ "$status" = "folder" -a "$deleteChildren" = "N" ]; then
        ## delete the immediate files in the folder
        for childfile in `dir -d $filepath/*` ; do
            if [ -f $childfile ]
                then
                    echo -e "shred -u -z -n $overwriteAmt $childfile"
            fi
        done    
elif [ "$status" = "file" ]; then
        echo "shred -u -z -n $overwriteAmt $filepath"
fi

```

---

### Post by thotheolh on 2010-11-20
I tried your script and this is the output on a folder with somethings I want to test on called Shred on the Desktop:

```

MyLinux@MyLinux:~$ cd Desktop
MyLinux@MyLinux:~/Desktop$ ./Shredder.sh 
Enter file path:    Shred
Enter number of overwrites: [recommended >= 10]    
Selected file/folder: Shred
Num. of overwrites: 
Selected is a folder
Do you want all the child files/folders be deleted ? [Y/N]: Y
shred -u -z -n  Shred/alienarena7_45
shred -u -z -n  Shred/Apr24_09_IPGSCC_Anchorage\
shred -u -z -n  Declaration.pdf
shred -u -z -n  Shred/Assignment%202%20Answers.doc
shred -u -z -n  Shred/Bruce\
shred -u -z -n  Schneier\
shred -u -z -n  on\
shred -u -z -n  Cyber\
shred -u -z -n  War\
shred -u -z -n  and\
shred -u -z -n  Cyber\
shred -u -z -n  Crime.flv

```

The files that are suppose to be in the Shred folder on the Desktop is: 

[LIST]
[*]alienarena7_45 (a folder containing the alien arena game dlls)
[*]Apr24_09_IPGSCC_Anchorage Declaration.pdf
[*]Assignment 2 Answers.doc (a fake document created to simulate documents)
[*]Shred/Bruce Schneier on Cyber War and Cyber Crime.flv (Video from Youtube)
[/LIST]
I think somehow the loop simply just broke down all the file names with spacing. The '-n' of shred should follow by the amount of number of passes (default is 10).

Is there a gnome utility that uses the shred utility from command line to make it far more simpler to shred ?

---

### Post by bcbc on 2010-11-20
```
for childfile in **"**`dir -d $filepath/*`**"** ; do
   echo -e "shred -u -z -n $overwriteAmt **"**$childfile**"**"
```

You need to escape any variable that contains spaces with "". Also your input path.

---

