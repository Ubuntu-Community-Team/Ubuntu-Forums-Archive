---
title: "Commandline Trash Utility"
date: 2008-05-09
forum: The Cafe
---

### Post by ibuclaw on 2008-05-09
Hi all,
   To admins, move this thread elsewhere if you feel that there is a better forum to discuss it.

   To everyone else.
Basically, I've been sitting on a home-made utility for the past month without much thought about what to do with it.

So I've decided that it's probably best to just put it out in the open free for everyone to play with and improve.
I don't really know much of a place where, but here seemed like a good place to me.

As the title says, it's a command line trash app, simply made to replace the "unforgivable" **rm** app for Linux (Or, at least to give yourself a second chance to restore the file).

It is fully written in BASH (with a small sprinkle of Perl now), so it is perfectly integrate-able, just copy the scripts into the /usr/local/bin directory and the names of the commands are in your reach of power.

It's integrated with the Gnome folders, so trash a file/folder in nautilus, and you can restore that file to it's original location with this app in the commandline.
It also comes with other slick little devices to that have helped, at least me, to gain some form of productivity when clearing out unwanted sections of my home folder in the command line.

For those who can read source:
Here is the main jelly, completely usable as is:
Although it's not the complete package, it is what every other script branches into.

The source here is the testing version (**v0.2-4f**) with various fixes that both I have made and people have sent me.
It also is the starting of implementing the FreeDesktop.org specifications for how trash should be handled.
So if anyone has any ideas on what I could add. Please send them.

It is currently in the middle of being commented on (pure laziness is all thats stopping me :)). So for the moment, you still have to guess what everything does ;)
```

#!/usr/bin/env bash
# License: GPLv3      #
# Author: Iain Buc&#322;aw #
#######################

### Main Variables ###
export uid=$UID
export uname=$USER
export excludefs="-x tmpfs -x fuse.gvfs-fuse-daemon"
export XDG_DATA_HOME=".local/share"
[ ! "$cwd" ] && export cwd=$PWD
###

### Other Variables ###
export Interact="0"
export OutDir=
###

### Functions Section ###
setdir() 
{
    for topdir in $(df $excludefs 2>/dev/null | awk 'FS="% "{print $2}' | tac)
    do export where="${1#$topdir}"
       if [ "$where" != "$1" ]
       then break
       fi
    done

    case $topdir in
        "/home")
           if [ $uname == root ]
           then export Main="/home/.Trash-$uid"
           else export Main="/home/$uname/$XDG_DATA_HOME/Trash"
           fi
           ;;
	   "/")
           if [ $uname == root ]
           then export Main="/root/$XDG_DATA_HOME/Trash"
           else export Main="/tmp/.Trash-$uid"
           fi
           ;;
        *)
	   export Main="$topdir/.Trash-$uid"
           ;;
    esac

    export Files="$Main/files"
    export Info="$Main/info"
    if [ ! -e "$Main" ]
    then mkdir -p "$Main/files/../info"
    fi
}

trash() # Main trash function.
{
    mvtrash() # Sub-function moves file to trash and writes data to info file.
    {
        while [ ! -z "$1" ]
        do if [ "${1: -1}" == "/" ] 
           then export n1="${1%/}"
           else export n1="$1"
           fi; if [ -e "$Files/${n1##*/}" ]
               then export n=2
                    while [ -e "$Files/${n1##*/}.$n" ]
                    do let "n++"
                    done
                    mv "$Path" "$Files/${n1##*/}.$n" 2>/dev/null
                    export exitnum="$?"
                    export n="."$n
               else mv "$Path" "$Files"
                    export exitnum="$?"
                    export n=""
               fi;
           printf "%s\n" "[Trash Info]" > "$Info/${n1##*/}$n.trashinfo" 
           printf "%s\n"  "Path=$Path" >> "$Info/${n1##*/}$n.trashinfo"
           printf "%s\n"  "DeletionDate=$DelDate" >> "$Info/${n1##*/}$n.trashinfo"
           if [ "$exitnum" -eq 0 ]
           then printf "%s\n" " Moved $n1 to Trash..."
           else printf "%s\n" " Cannot Move file. $n1 Copied to Trash..."
           fi
           shift
        done
    }
    
    while [ "$#" -gt "0" ]
    do if [ -e "$1" ]
       then export DelDate=`date +%FT%T`
            if [ ! "${1%%/*}" ] || [ "${1:0:3}" == "../" ]
            then cd "${1%/*}/"
                 export Path="$PWD"/"${1/*\/}"
            else export Path="$cwd"/"$1"
            fi
            setdir "$Path"
            if [ "$Interact" = "0" ]
            then mvtrash "$1"
            else printf "%s" "  Trash Item '$1'? [Y/N]: "
                 read -n 1 input
                 echo
                 case "$input" in
                     y|Y)
                       mvtrash "$1"
                       ;;
                     *)
                       printf "%s\n" " Skipping $1..."
                       ;;
                 esac
            fi
       else printf "%s\n" " Cannot Move $1. File(s) Don't Exist..."
       fi
       shift
    done
}

restore() # Main restore section.
{
    rmain()
    {
        checkpath()
        {
            mvorigin() # Retrieves the origin of the file and restores it.
            {
                export Origin=`grep Path "$Info/$1.trashinfo"` && export Origin="${Origin/Path=/}"
                mkdir -p ${Origin%/*}
                mv "$Files/$1" "$Origin"
                rm "$Info/$1.trashinfo"
            }
            while [ "$#" -gt "0" ]
            do if [ ! $OutDir ]
               then if [ -f "$Info/$1.trashinfo" ]
                    then mvorigin "$1"
                         printf "%s\n" " Restoring $1..."
                    else printf "%s\n" " No Information file for $1. Cannot Restore..."
                    fi
               else mv "$Files/$1" "$OutDir"
                    printf "%s\n" " Restoring $1 to current path..."
               fi
               shift
            done
        }
        while [ "$#" -gt "0" ]
        do for i in `find "$Files" -maxdepth 1 -iname "$1" -exec echo {} \; | sed 's/ /?/g'`
           do if [ "$i" != "$Files" ]
              then export files=1
                   checkpath "$(basename "$i")"
              fi
           done
           [ "$files" ] || printf "%s\n" " $1 is not in Trash..."
           export files=""
           shift
        done
    }
    
    if [ "$1" == "-o" ]
    then export OutDir="$cwd"
         shift
    fi
    
    cd "$Files"
    rmain "$@"
}

list()
{
    lmain()
    {
        export count=0

        for h in .*
        do if [ "$h" != "." ] && [ "$h" != ".." ] && [ "$h" != "*" ]
           then printf "\033[37m %-20s\n" "$h"
                printf "\033[0m"
                let "count++"
           fi
        done

        for i in *
	do if [ "$i" != "*" ]
           then if [ -h "$i" ]
                then printf "\033[1;36m %-20s\n" "$i"
                elif [ -x "$i" ]
                then if [ ! -d "$i" ]
                     then printf "\033[1;32m %-20s\n" "$i"
                     else printf "\033[1;34m %-20s\n" "$i"
                     fi
                else colour "$i" "$i"
                     printf "\n"
                fi
                printf "\033[0m"
                let "count++"
           fi
        done

        if [ $count -eq "0" ]
        then printf "%s\n" " *"
        fi
    }

    lvmain()
    {
        getinfo()
        {
            split()
            {
                export input="$@"
                export Origin=${input#[*=} && export Origin=${Origin% *}
                export DelDate=${input##[*=} && export DelDate="${DelDate:0:10}"
                export DelTime=${input: -8}
            }
            split $(cat "$Info/$1.trashinfo")
            if [ "${Origin: -1}" == "/" ]
            then export Origin="${Origin%/}"
            fi
            export Origin=${Origin/$1/} && export Origin=${Origin%${1/%.*/}}
            export Origin="${Origin##${1##${1/.*/}}}"
            if [ "${#Origin}" -gt "35" ]
            then export Origin="${Origin:0:33}*"
            fi
            printf " %-35s %s\n" "$Origin" "$DelDate | $DelTime"
        }

        for i in `find -maxdepth 1 -exec echo {} \; | sed 's/ /?/g;s/.\///g' | sort`
        do if [ "$i" != "." ]
           then if [ "${#i}" -gt "20" ]
                then export n=17
                     export j="${i:0:$n}*${i##*.}"
                     while [ $n -gt "0" ]
                     do let "n--"
                        if [ "${#j}" -gt "20" ]
                        then export j="${i:0:$n}*${i##*.}"
                        fi
                     done
                     if [ "${#j}" -gt "20" ]
                     then export j="${i:0:19}*"
                     fi
                else export j="$i"
                fi
                 
                if [ -h "$i" ]
                then printf "\033[1;36m %-20s" "$j"
                elif [ -x "$i" ]
                then if [ ! -d "$i" ]
                     then printf "\033[1;32m %-20s" "$j" 
                     else printf "\033[1;34m %-20s" "$j"
                     fi
                else colour "$i" "$j"
                fi
                printf "\033[0m"
                if [ -f "$Info/$i.trashinfo" ]
                then getinfo "$i"
                else printf "%-43s %s\n" " No Information Availiable" "N/A | N/A"
                fi
              let "count++"
           fi
        done

    }
    
    colour()
    {
        case "${1##*.}" in
            7z|ace|arj|bz|bz2|cpio|deb|dz)
               printf "\033[1;31m %-20s" "$2"
               ;;
            gz|jar|lzh|lzma|rar|rpm|rz|svgz)
               printf "\033[1;31m %-20s" "$2"
               ;;
            tar|taz|tbz2|tgz|tz|z|Z|zip|zoo)
               printf "\033[1;31m %-20s" "$2"
               ;;
            bmp|gif|jpeg|jpg|mng|pbm|pcx|pdf)
               printf "\033[1;35m %-20s" "$2"
               ;;
            pgm|ps|png|ppm|svg|tga|tif|tiff|xbm)
               printf "\033[1;35m %-20s" "$2"
               ;;
            desktop|directory)
               printf "\033[1;36m %-20s" "$2"
               ;;
            aac|au|flac|mid|midi|mka|mp3|mpc|ogg|ra|wav)
               printf "\033[1;33m %-20s" "$2"
               ;;
            asf|avi|dl|flc|fli|gl|m2v|m4v|mkv)
               printf "\033[1;33m %-20s" "$2"
               ;;
            mov|mp4|mp4v|mpeg|mpg|nuv|ogm|qt)
               printf "\033[1;33m %-20s" "$2"
               ;;
            rm|rmvb|vob|wmv|xcf|xwd|yuv)
               printf "\033[1;33m %-20s" "$2"
               ;;
            *)
               printf "\033[37m %-20s" "$2"
               ;;
        esac
    }
    export title=0
    export count=0
    for topdir in $(df $excludefs 2>/dev/null | awk 'FS="% "{print $2}')
    do if [ -e "$topdir" ]
       then case "$topdir" in
                "/home")
                   if [ $uname == root ]
                   then export Main="/home/.Trash-$uid"
                   else export Main="/home/$uname/$XDG_DATA_HOME/Trash"
                   fi
                   ;;
                "/")
                   if [ $uname == root ]
                   then export Main="/root/$XDG_DATA_HOME/Trash"
                   else export Main="/tmp/.Trash-$uid"
                   fi
                   ;;
                *)
                   export Main=$(echo "$topdir/.Trash-$uid")
                   ;;
            esac
            if [ -e "$Main" ]
            then export Files="$Main/files"
                 export Info="$Main/info"
                 if [ "$1" == "-v" ]
                 then if [ $title -eq 0 ]
                      then printf " %-20s %-35s %s\n" "Name" "Original-Path" "Deletion-Date & Time"
                      export title=1
                      fi
                      cd "$Files"
                      lvmain
                      else 
                 cd "$Files"
                 printf "\033[1;37m%s" "$Main"
                 printf "\033[0m\n"
                 lmain
                 fi
            fi
       fi
    done
    if [ "$1" == "-v" ]
    then if [ $count -eq 0 ]
         then printf "%-20s %-43s %s\n" " *" " Trash is Empty" "N/A | N/A"
         fi
    fi
}

emptytrash()
{
    printf "%s\n" " Removing Files..."
    rm -rf "$Files"
    if [ "$?" -eq "0" ]
    then rm -rf "$Info"
	 printf "%s\n" " Removing Config..."
	 mkdir -p "$Files"
	 mkdir -p "$Info"
	 printf "%s\n" " Trash is Now Empty."
    else printf "%s\n" "Error, You are not the owner of one or more files..."
	 printf "%s" "To fix this, type in: "
	 printf "%s\n" "cd $Files && sudo chown $user:$user * -R"
	 exit 1
    fi
}

empty()
{
    emain()
    {
        remove()
        {
            rm -rf "$Files/$1"
            rm -rf "$Info/$1.trashinfo"
        }
        
        while [ "$#" -gt "0" ]
        do remove "$1"
           printf "%s\n" " Removing $1..."
           shift
        done
    }
    cd "$Files"
    while [ "$#" -gt "0" ]
    do for i in `find "$Files" -maxdepth 1 -iname "$1" -exec echo {} \; | sed 's/ /?/g'`
       do export files=1
          emain "$(basename "$i")"
          done
          [ "$files" ] || printf "%s\n" " $1 is not in Trash..."
          export files=""
          shift
    done
}

clean() # Main clean function.
{
    mvclean() # Sub-function moves file to trash and writes data to info file.
    {
        while [ ! -z "$1" ]
        do if [ "${1: -1}" == "/" ] # Remove tailing "/" from filename (ie: "test/")
           then export n1="${1%/}"
           else export n1="$1"
           fi; if [ -e "$Files/${n1##/*/}" ] # Checks if file already exists in trash.
               then export n=2
                    while [ -e "$Files/${n1##/*/}.$n" ] # Renames file numerically until it is unique.
                    do let "n++"
                    done
                    mv "$1" "$Files/${n1##/*/}.$n"
                    export n="."$n
               else mv "$1" "$Files"
                    export n=""
               fi; # This section stores recovery info about the file.
           printf "%s\n" "[Trash Info]" > "$Info/${n1##/*/}$n.trashinfo" 
           printf "%s\n"  "Path=$Path" >> "$Info/${n1##/*/}$n.trashinfo"
           printf "%s\n"  "DeletionDate=$DelDate" >> "$Info/${n1##/*/}$n.trashinfo"
           printf "%s\n" " Moved $n1 to Trash..."
           shift
        done
    }
    
    while [ "$#" -gt "0" ]
    do if [ -e "$1" ]
       then export DelDate=`date +%FT%T` # Gets the time of moving the file.
            if [ ! "${1%%/*}" ] # Checks for path of file. If doesn't exist, it is created.
            then export Path="$1"
            else export Path=$cwd/"$1"
            fi
            mvclean "$1"    
       fi
       shift
    done
}

###

### Main Logic Section ###
case "$1" in
    -i)
      export Interact="1"
      shift
      setdir "$cwd"
      trash "$@"
      ;;
    -r)
      shift
      setdir "$cwd" # FIX ME
      restore "$@"
      ;;
    -ra)
      setdir "$cwd" # FIX ME
      restore "*"
      ;;
    -roa)
      setdir "$cwd" # FIX ME
      restore -o "*"
      ;;
    -ro)
      shift
      setdir "$cwd" # FIX ME 
      restore -o "$@"
      ;;
    -l)
      list
      ;;
    -lv)
      list -v
      ;;
    -e)
      shift
      setdir "$cwd" # FIX ME?
      if [ "$#" == "0" ]
      then emptytrash
      else empty "$@"
      fi
      ;;
    -c)
      cd "$cwd"
      setdir "$cwd"
      clean "#"* *~ .*~ *.bak *.log
      ;;
    -ct)
      cd "$cwd"
      setdir "$cwd"
      clean "#"* *~ .*~
      ;;
    -cb)
      cd "$cwd"
      setdir "cwd"
      clean *.bak
      ;;
    -cl)
      cd "$cwd"
      setdir "$cwd"
      clean *.log
      ;;
    *)
      trash "$@"
      ;;
esac
###

exit 0

```

For everyone else, feel free to try it out in the attachment I've added. (Readme guide on usage included). And let me know what you think of it.

Regards
Iain

Download:
[trashapp-0.2-4b.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=72697&stc=1&d=1212431633")

---

### Post by nojjy on 2008-05-11
How about making it follow the Freedesktop trash specification, concerning files that are deleted on file systems that aren't /home ... eg. files deleted on '/media/data' go to '/media/data/.Trash-$USER'.

See:
[http://www.ramendik.ru/docs/trashspec.html](http://www.ramendik.ru/docs/trashspec.html)

Thanks for the useful script!

---

### Post by y-lee on 2008-05-11
Pretty cool utility :)

Thanks :KS

---

### Post by ibuclaw on 2008-05-11
[QUOTE=y-lee]Pretty cool utility[/QUOTE]

Hey, thanks guys. I was wondering whether or not anyone would find it useful. Let alone whether or not someone would actually find this thread!:lolflag:

All this worry has had me thinking on how much I should add to it too.
I've since noticed some things like I'd wanted to change/add to it (ie: It couldn't show hidden files. It only coloured executable files and directories. And I wanted a bit more than that.)

[QUOTE=nojjy]How about making it follow the Freedesktop trash specification, concerning files that are deleted on file systems that aren't /home ... eg. files deleted on '/media/data' go to '/media/data/.Trash-$USER'.[/QUOTE]

Thanks for the ups. I will definitely look into that.
Although, on subject, I was considering adding functionality for accessing the trash folders for external storage devices anyway.

But I think my first priority is slimming down the excess time-consuming tasks by finding more optimal ways of getting data (in the "list" command especially).
Infact, alot of what the script is, is due to the fact that I went out of the way to avoid every external app possible.
Replacing all instances of **sed 's/phrase//'** with **${string##phrase}**.
All **echo $string** with **printf "%s\n" "$string"**.
And by removing all pipes where possible.

I'll post my [initial re-work of it]("http://ubuntuforums.org/attachment.php?attachmentid=70079&d=1210801381").
I feel happier with it now. It feels more lighter (Though that could just be the added colour).

Again. I would love to hear feedback. Get good tips and pointers. I feel very much appreciated by it.

Regards
Iain

---

### Post by kevdog on 2008-05-11
How do I use this app?  Any manual?

---

### Post by saulgoode on 2008-05-11
It doesn't appear that your 'mvtrash' function will handle an absolute path (eg, /home/tinivole/Documents or /tmp/somefile). 

I think the following code would rectify this:

```
while [ "$#" -gt "0" ]
do if [ -d "$1" ] || [ -f "$1" ]
       then export DelDate=`date +%FT%T`
            if [ "${1%%/*}" = "" ]
            then Path="$1"
            else Path=`pwd`/"$1"
            fi

```

---

### Post by ibuclaw on 2008-05-12
> **kevdog said:**
> How do I use this app?  Any manual?

There's a readme with it.

but basically:
[LIST]
[*]**trash foo**
Move foo to trash.
[*]**trash -i foo**
Interactive trashing (ie: Are You Sure?[Y/N]).
[*]**restore foo** (OR) **trash -r foo**
Restore foo to its original location.
[*]**restore -o foo** (OR) **trash -ro foo**
Restore foo to your current working directory (pwd).
[*]**empty foo** (OR) **trash -e foo**
Delete foo from trash.
[*]**empty trash** (OR) **trash -e**
Delete all files/folders from trash.
[*]**list trash** (OR) **trash -l**
Print a list of all files in trash.
[/LIST]
That not the complete list, but that's enough to get started with.

[QUOTE=saulgoode]
It doesn't appear that your 'mvtrash' function will handle an absolute path (eg, /home/tinivole/Documents or /tmp/somefile).

I think the following code would rectify this
[/QUOTE]
Yes, it appears so. Thanks for that.
I also found out that, regardless. The file info doesn't get written anyway!
I tried this:
[PHP]
$ touch ~/foo
$ trash ~/foo
/usr/local/bin/trash: line 42: /home/iain/.local/share/Trash/info//home/iain/foo.trashinfo: No such file or directory
/usr/local/bin/trash: line 43: /home/iain/.local/share/Trash/info//home/iain/foo.trashinfo: No such file or directory
/usr/local/bin/trash: line 44: /home/iain/.local/share/Trash/info//home/iain/foo.trashinfo: No such file or directory
 Moved /home/iain/foo to Trash...
$ list trash -v
 Name                 Original-Path                       Deletion-Date & Time
 foo                  No Information Availiable           N/A | N/A
[/PHP]
The File is moved, but no info file is made (Due to no string chopping).

This fixes it, replace **$1** with **${1##/*/}** in the three "echo" lines:
```

    mvtrash()
    {
        while [ ! -z "$1" ]
        do mv "$1" "$Files"
	    echo "[Trash Info]" > "$Info/${1##/*/}.trashinfo"
           echo "Path=$Path" >> "$Info/${1##/*/}.trashinfo"
           echo "DeletionDate=$DelDate" >> "$Info/${1##/*/}.trashinfo"
           printf "%s\n" " Moved $1 to Trash..."
           shift; done
    }

```
[PHP]
$ touch ~/foo
$ trash ~/foo
 Moved /home/iain/foo to Trash...
$ list trash -v
 Name                 Original-Path                       Deletion-Date & Time
 foo                  /home/iain/                         2008-05-12 | 16:10:45
[/PHP]

Cheers for that! I've put the fix in my two testing versions.

Regards
Iain

---

### Post by ibuclaw on 2008-05-14
Ok, small update.

I will work on the FreeDesktop.Org complaince.
But for the moment, the code is frozen as I begin porting it to Perl.

Thanks for your interest, guys, and as always send whatever errors you find.

Regards
Iain

---

### Post by mykmelez on 2008-05-21
Thanks, this is just what I was looking for!  In 7.10 I used to just |mv <files> ~/.Trash|, but in 8.04 it's more complicated, and it seems better to use a tool that understands GNOME's new trash system.  This is just the ticket.

One issue: when I moved a directory to trash via |trash <dirname>| I got the following output, although the command seemed to succeed:

```
$ trash <dir-name>/
/home/<username>/bin/trash: line 54: /home/<username>/.local/share/Trash/info/<dirname>/.trashinfo: No such file or directory
/home/<username>/bin/trash: line 55: /home/<username>/.local/share/Trash/info/<dirname>/.trashinfo: No such file or directory
/home/<username>/bin/trash: line 56: /home/<username>/.local/share/Trash/info/<dirname>/.trashinfo: No such file or directory

```

-myk

---

### Post by ibuclaw on 2008-05-24
Hi mykmelez.

Sorry for the late reply.

To answer your question. Everything is considered a file in the Linux Command prompt, and I wrote the script thinking no differently.

The main problem you are having is the fact that you put "/" at the end of the name.
Whereas:
```
trash <dir-name>
```
would be a legal way of calling the script, and no errors would be produced from it.

Nonetheless.
I've made a fix (removes the tailing forwardslash from the argument line).

Thanks for pointing that out.

Regards
Iain

---

### Post by ssam on 2008-05-25
is this what gnomevfs-rm does? i can't find any docs for it.

---

### Post by ibuclaw on 2008-05-25
> **ssam said:**
> is this what gnomevfs-rm does? i can't find any docs for it.

gnomevfs-rm is exactly the same as rm, except, it has the ability to remove files on remote filesystems.

Typing it without any arguments gives this:
[PHP]$ gnomevfs-rm
Usage: gnomevfs-rm <uri>
[/PHP]
Where URI is the location of the mount.
ie: **smb:///samba.mount/foo**
or  **file:///home/user/foo**

And the same goes to all the gnomevfs tools too.
[LIST]
[*]gnomevfs-cat = cat
[*]gnomevfs-copy = cp
[*]gnomevfs-df = df
[*]gnomevfs-info = ??? (A CLI version of the "Properties" window in nautilus?)
[*]gnomevfs-ls = ls
[*]gnomevfs-mkdir = mkdir
[*]gnomevfs-monitor = ??? (A list of changes that has been done to the file?)
[*]gnomevfs-mv = mv
[*]gnomevfs-rm = rm
[/LIST]

So the answer to your question would be, no. It is not.

But thanks for mentioning it though, this could be perfect for what I'm looking for!
The ability to work on remote filesystems is in my small list of TODOs.

Thanks.
Regards
Iain

---

### Post by mykmelez on 2008-05-25
> **tinivole said:**
> I've made a fix (removes the tailing forwardslash from the argument line).

Thanks Iain, that worked like a charm!

-myk

---

### Post by minimog on 2008-07-05
thank you for the utility!!

---

### Post by mykmelez on 2008-12-08
Someone should package this up and add it to Ubuntu's packages repository.

---

### Post by ibuclaw on 2008-12-09
Someone beat me to it :)

Though, they've written it in Python... :(

It's found under the **trash-cli** package. It's not quite as verbose as this little bash script, but it does its job to a substantial level. (IMO, I prefer mine ;) )

Though, thanks for the consideration. What I may end up doing is re-writing this, adding bits that I sometimes feel are lacking (such as an interactive mode, the ability to restore files in folders, etc), maybe add a small gui layer using zenity, maybe re-write the whole thing in Perl....
And other things that may help up the antic a bit.

Only then, may I consider perhaps packaging.

Regards
Iain

---

### Post by mykmelez on 2008-12-09
Over time, I've noticed two problems with the utility.

First, it displays several warnings when I trash something in another directory (although the command succeeds):

myk@myk:~$ mkdir foo
myk@myk:~$ touch foo/bar
myk@myk:~$ trash foo/bar
/home/myk/bin/trash: line 57: /home/myk/.local/share/Trash/info/foo/bar.trashinfo: No such file or directory
/home/myk/bin/trash: line 58: /home/myk/.local/share/Trash/info/foo/bar.trashinfo: No such file or directory
/home/myk/bin/trash: line 59: /home/myk/.local/share/Trash/info/foo/bar.trashinfo: No such file or directory
 Moved foo/bar to Trash...

Second, sometimes when I throw away a file I get a message like this, although I don't have a consistent set of steps to reproduce:

mv: cannot overwrite directory `/home/myk/.local/share/Trash/files/bar' with non-directory

-myk

---

### Post by ibuclaw on 2008-12-10
@mykmelez interesting, I don't get that with the version I currently have on my computer.

As for the second error, it looks like it is trying to mv a folder over a file.

Again, I believe I have fixed this a while ago too (files with the same name are renamed sequentially, as with the desktop.org standard)
ie:
foo
foo.2
foo.3
foo.4


what I'll do is re-tarball the script in the next 16-ish hours (need to sleep, then iron out a few things in the script :) ) and I will replace the file download in the first post of this thread.

Regards
Iain

---

### Post by mykmelez on 2008-12-12
Thanks for the update!  I've downloaded the new version, and it no longer displays those warnings.  I'll let you know if I see that error again.

It might be useful (although perhaps only for a small minority of users) to have an option for cleaning up the .orig and .rej files that revision control systems like CVS and Mercurial can leave around (not to mention the patch command).  I currently use the following command (for which I've defined an alias) to do that:

```
find . -regextype posix-extended -regex '\''.*.(orig|rej)$'\'' -exec rm {} \;
```

Also, it would be useful for clean to have a -r|--recursive option that recursively traverses the directory structure from the specified (or current working) directory.

---

### Post by mykmelez on 2009-03-09
> **tinivole said:**
> It's found under the **trash-cli** package. It's not quite as verbose as this little bash script, but it does its job to a substantial level. (IMO, I prefer mine ;) )

One problem I've found with the trash-cli package is that it fails on files in a mounted filesystem whose mount point is not writable by me, since it tries to put trashed files into a subdirectory of the mount point, whereas your script puts all trashed files into the same trash subdirectory of my home directory, so it works on those files.

---

### Post by andreafrancia on 2009-03-14
> **tinivole said:**
> Someone beat me to it :)

Though, they've written it in Python... :(

It's found under the **trash-cli** package. 

Hi, I'm the writer of the trash-cli package. I think your script is a good work and I think that you could ask the packaging in Ubuntu even if there is already the trash-cli package.

I would be also worth if we could collaborate in some manner. I don't know how but it could be nice. Feel free to contact me.

---

