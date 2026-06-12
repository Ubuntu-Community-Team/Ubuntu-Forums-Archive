---
title: "Handy bash script to traverse folders recursively?"
date: 2011-03-24
forum: The Cafe
---

### Post by niki+a on 2011-03-24
Hey guys, so say i have a bash script that is in my path that I can run to do a specific task, like for example, create thumbs of images using mogrify/convert or rename files using tr:

```

#!/bin/bash

#turn images into thumbnails:
#-----------------------------------------------
rm -r thumbs
mkdir thumbs
for i in *.jpg
do
  `convert -resize 162x164 $i "thumbs/thumb_$i"`
  #echo $i;
done
exit 1 
#----------------------------------------------

```Lets say I call the above script: make_thumbs.sh

I need a script that I can use to run the above script recursively...

I tried:

find /my/images/location -type d -exec make_thumbs.sh "{$1}" \;

But I run into trouble because if I include directions to cd in make_thumbs.sh it only does it for top most folder and stops after that...

Does anyone know a way to traverse directories recursively? 

I'm using Ubuntu 10.04 and don't have a bin for cd, do I need to grab one from somewhere and tell my script to use /bin/cd instead of the default one in the kernel or where ever?

---

### Post by nerdopolis on 2011-03-24
You don't need a /bin/cd , as its one of the few commands that are hardcoded in the shell.

The problem is is that for loop is not recursive, the * symbol will give you just that

This is a way to recursively handle files with a script: (in the current directory)
```

foldername="$PWD"
while read "$FILE"
do
#get just the file name
filename=$( echo "$FILE" | rev | awk -F / '{print $1}' | rev )
#get the relative path name
relativefoldername=$( echo "$FILE" | awk -F "/$filename" '{print $1}'  | awk -F "$foldername" '{print $2}' )

mkdir -p "thumbs$relativefoldername"
convert -resize 162x164 "$FILE" "thumbs$relativefoldername/thumb_$filename"
done < "$(find "$PWD" -name "*.jpg" )"
```[FONT=monospace]


This SHOULD work. 
[/FONT]

---

### Post by niki+a on 2011-03-24
> **nerdopolis said:**
> You don't need a /bin/cd , as its one of the few commands that are hardcoded in the shell.

The problem is is that for loop is not recursive, the * symbol will give you just that

This is a way to recursively handle files with a script: (in the current directory)
```

foldername="$PWD"
while read "$FILE"
do
#get just the file name
filename=$( echo "$FILE" | rev | awk -F / '{print $1}' | rev )
#get the relative path name
relativefoldername=$( echo "$FILE" | awk -F "/$filename" '{print $1}'  | awk -F "$foldername" '{print $2}' )

mkdir -p "thumbs$relativefoldername"
convert -resize 162x164 "$FILE" "thumbs$relativefoldername/thumb_$filename"
done < "$(find "$PWD" -name "*.jpg" )"
```[FONT=monospace]


This SHOULD work. 
[/FONT]

That's way too over complicated for what I need. My script works fine if I cd to each folder and run it manually from the shell.

What I was looking for is something like this:

```

find /path/to/folder/with/folders/* -type d -exec sh -c 'cd $1; custom_script.sh' {} {} \;

```

But I cannot get custom_script.sh to play nice with magic characters...

It creates an infinite series of thumbs folders inside thumb folders inside thumbs folders and so on...

Anyone have any way to get these ideas to play nicely with each other?

---

### Post by DaithiF on 2011-03-25
i would pass the path to the script as a parameter, if that path ends in thumbs then do nothing, otherwise cd into the dir within the script and do your converting/mogrifying etc.


```
name=$(basename "$1")
[[ $name == "thumbs" ]] && {echo "thumbs on thumbs is too many thumbs"; exit 0; }

```

---

### Post by koenn on 2011-03-25
```

find /foo/bar -type d |while read D; do cd $D; do_stuff_here; done

```
/foo/bar is the directory you want to start from. Should be an absolute path
do_stuff_here is a script or a program in your $PATH, or an absolute path to an executable file

---

### Post by koenn on 2011-03-25
> **niki+a said:**
> 
It creates an infinite series of thumbs folders inside thumb folders inside thumbs folders and so on...

ah, oh ... didn't pay attention to that

it's probably that 'find' finds the thumbs-folder you create, and recurses into it, and so on. 

maybe you can avoid that with -depth, ie do the lower level directories first
```

find /foo/bar -depth -type d |  ...

```

or try this
```
for D in $(find /foo/bar -type d ); do cd $D; do_stuff_here; done
```
that one is going take up memory if the list of directories is very long; 

you can also use a temp file instead
```

list=$(mktemp)
find /foo/bar -type d >$list
while read D; do cd $D; do_stuff_here; done <$list

```

---

### Post by nerdopolis on 2011-03-25
> **koenn said:**
> that one is going take up memory if the list of directories is very 

I think it also could fail completely with "Argument is too long" if it there are too many files and folders (I think 2097152 chars by default worth of file paths (source: ```
getconf ARG_MAX
``` )) (although you can change it if you want, by increasing the stack size)

---

### Post by sisco311 on 2011-03-25
@OP

If I understand you correctly, you want to run the script in the directory where the file is. Right? Then use the -execdir option:
```
find /path -options -execdir script '{}' \;
```


@anyone

Please check out:
[http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29](http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29)
[http://mywiki.wooledge.org/BashFAQ/020](http://mywiki.wooledge.org/BashFAQ/020) 

In bash, the preferred method would be:
```
shopt -s nullglob globstar
for file in **/*.jpg
do
    dir=${file%/*}
    filename=${file##*/}

    cd "$dir"
    **command**
    cd -
done
```

or:
```
while IFS= read -rd '' file
do
     ...
done < <(find /path -options)
```

---

### Post by niki+a on 2011-03-26
> **koenn said:**
> ```

find /foo/bar -type d |while read D; do cd $D; do_stuff_here; done

```/foo/bar is the directory you want to start from. Should be an absolute path
do_stuff_here is a script or a program in your $PATH, or an absolute path to an executable file


Brilliant. Thank you very much, this is exactly what I was looking for and it worked exactly as I expected when I ran it.

```

find /path/to/files/* -type d |while read D; do cd $D; image_resize.sh; done

```

Where image_resize.sh is

```

#!/bin/bash

#turn images into thumbnails:
#-----------------------------------------------
rm -r thumbs
mkdir thumbs
for i in *.jpg
do
  `convert -resize 162x164 $i "thumbs/thumb_$i"`
  #echo $i;
done
exit 1 
#----------------------------------------------

```

Because I do rm -r thumbs at start of image_resizer.sh I get

```
rm: cannot remove `thumbs': No such file or directory
```

I can ignore the error if I do

```

find /path/to/files/* -type d |while read D; do cd $D; image_resize.sh &>/dev/null; done

```

Thanks guys!

---

