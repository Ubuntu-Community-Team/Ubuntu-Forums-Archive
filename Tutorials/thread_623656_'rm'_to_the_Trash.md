---
title: "'rm' to the Trash"
date: 2007-11-26
forum: Tutorials
---

### Post by xiota on 2007-11-26
It might save some people some agony to have the 'rm' command move files to the Trash folder instead of deleting files immediately.  The easiest way to do this is to add the following line to '~/.bashrc':

```
alias rm='mv --target-directory ~/.Trash'
```

The above alias command just causes 'mv' to be run instead of 'rm'.  The problem with this is the command will overwrite files with duplicate names.  To avoid overwriting files, the following alias can be used instead:

```
alias rm='mv --verbose -f --backup=numbered --target-directory ~/.Trash/'
```

The problem with this new alias is it will not move files to the trash if there is a directory with the same name, or vice versa.  The solution I use is to make a script '~/bin/trashit' that will move and rename files as necessary.  I did not write this script, which you'll notice if you check the source to make sure it's safe...

```
#!/bin/sh
# trashit

# original script
#    http://www.macosxhints.com/article.php?story=20030217172653485
#    author: Shane Celis <shane (at) gnufoo (dot) org>
#
# Sun, 20-May-2007; 06:47:22 
#    minor changes...

if [ $# -eq 0 ]; then
        echo "usage: trashit <files...>" >&2
        exit 2;
fi

for file in "$@"; do
        # get just file name 
        destfile="`basename \"$file\"`"
        suffix='';
        i=0;

        # If that file already exists, change the name
        while [ -e "$HOME/.Trash/${destfile}${suffix}" ]; do
                suffix=" - copy $i";
                i=`expr $i + 1`
        done

        mv -vi "$file" "$HOME/.Trash/${destfile}${suffix}"
done
```

Remember to give the script execute permissions.  If you don't know how, maybe you shouldn't run scripts you find in forums?  The new alias command to put in '~/.bashrc' becomes:

```
alias rm='~/bin/trashit'
```

You will need to close and restart any terminal windows before the alias will take effect.  You should try creating some files and removing them to make sure the script is working.

```
touch t
rm t
touch t
rm t
touch t
rm t
touch t
rm t
```

In your trash folder, you should find files named:

```
t
t - copy 0
t - copy 1
t - copy 2
```

You might want to tweak the script to your liking.  For instance, you might want to rename files based on the date and time they were deleted.  It might also be useful for the script to detect what partition the files are in so that they can be moved to the partition's trash folder instead of the user's home directory.

Finally some warnings and notes:
[LIST]
[*]The above script and alias will give you some protection from mistakes you might make on the command line if you use bash.  If you use another shell, 'rm' will perform as usual.  Try using 'trashit' instead.

[*]The alias will also not work if you type 'sudo rm'.  If you want to make sure you are sending files to the trash, you may use 'sudo ~/bin/trashit'.

[*]Continue to be careful when running scripts.  They will continue to call the real 'rm' command.  Short of removing or replacing '/bin/rm', I do not know how to prevent scripts from using it.

[*]If you want to use the real rm command, you can type '\rm'.
[/LIST]

---

### Post by ants280 on 2011-01-05
I updated the script to accomodate the trash system Ubuntu uses today.  It creates some metadata in the ~/.local/share/Trash/info folder to help restore the file.  Limited testing.  Use at own risk!

```
#!/bin/sh
# trashit

# original script
#    http://www.macosxhints.com/article.php?story=20030217172653485
#    author: Shane Celis <shane (at) gnufoo (dot) org>
#
# Sun, 20-May-2007; 06:47:22 
#    minor changes...
#
# Tuesday, 04-January-2010:
#    includes "new" trash handling (~/.local/share/Trash),
#    trashinfo.  See http://ubuntuforums.org/showthread.php?t=623656#
#    for more info on how to use.
#
# !!! USE AT OWN RISK !!!

if [ $# -eq 0 ]; then
        echo "usage: trashit <files...>" >&2
        exit 2;
fi

for file in "$@"; do
        # get just file name 
        destfile="`basename \"$file\"`"
        suffix='';
        i=0;

        # If that file already exists, change the name
        while [ -e "$HOME/.local/share/Trash/files/${destfile}${suffix}" ]; do ### MODIFICATION ###
                suffix=" - copy $i";
                i=`expr $i + 1`
        done

        mv -vi "$file" "$HOME/.local/share/Trash/files/${destfile}${suffix}" ### MODIFICATION ###

        # Create trashinfo so file can be restored from trash to original location
        trashinfo="$HOME/.local/share/Trash/info/`basename ${file}`.trashinfo"
        echo "[Trash Info]" > ${trashinfo}
        echo "Path=`dirname $file`/`basename ${file}`" >> ${trashinfo}
        echo "DeletionDate=`date +%FT%T`" >> ${trashinfo}
done
```

---

### Post by KenJean on 2011-01-05
Just wondering whether you have tried the

**trash-cli**

programme that is in the repositories. It is best explained here: [http://code.google.com/p/trash-cli/](http://code.google.com/p/trash-cli/)

So what I do is define this simple alias:

**alias rm='trash-put'**

and I'm good to go.

It interfaces nicely with the trash-can in Nautilus.

-KJ

---

### Post by shane2peru on 2011-04-06
> **KenJean said:**
> Just wondering whether you have tried the

**trash-cli**

programme that is in the repositories. It is best explained here: [http://code.google.com/p/trash-cli/](http://code.google.com/p/trash-cli/)

So what I do is define this simple alias:

**alias rm='trash-put'**

and I'm good to go.

It interfaces nicely with the trash-can in Nautilus.

-KJ

Old thread, but thanks a bundle for the tip!!!

trash-cli rules.

Shane

---

### Post by zecoelho on 2011-12-01
to run the script effectivelly add the source command to the front, like this:
. trashit

---

### Post by helgesdk on 2011-12-08
The script is flawed:
When file name collisions occur, it will overwrite the previous .trashinfo.

Here's an improved version:

```
#!/bin/bash
# trashit

# original script
#    http://www.macosxhints.com/article.php?story=20030217172653485
#    author: Shane Celis <shane (at) gnufoo (dot) org>
#
# Sun, 20-May-2007; 06:47:22 
#    minor changes...
#
# Tuesday, 04-January-2011:
#    modified by Jacob Patterson <jacob.patterson@gmail.com>
#    includes "new" trash handling (~/.local/share/Trash),
#    trashinfo.  See http://ubuntuforums.org/showthread.php?t=623656#
#    for more info on how to use.
#
# Thursday, 08-December-2011:
#    modified by Helge Willum Larsen <helgesdk@gmail.com>
#    fixed overwriting trashinfo when name collision occurs.
#    rewritten to /bin/bash.
#    added checks for empty file name and orphaned trashinfo.
#
# !!! USE AT OWN RISK !!!

if [[ -z $@ ]]; then
	echo "usage: trashit <files...>" >&2
	exit 2;
fi

for file in "$@"; do
	# get just file name
	destfile=`basename "$file"`
	if [[ -z ${destfile} ]]; then
		echo "empty filename" >&2
		continue
	fi
	unset suffix;
	declare -i i=0;

	# If that file already exists, change the name
	while [[ -e $HOME/.local/share/Trash/files/${destfile}${suffix} ]]; do
		i+=1
		suffix=" - copy $i";
	done

	trashinfo="$HOME/.local/share/Trash/info/${destfile}${suffix}.trashinfo"
	if [[ -e ${trashinfo} ]]; then
		echo "failed to trash: ${file}" >&2
		continue
	fi

	mv -vi "$file" "$HOME/.local/share/Trash/files/${destfile}${suffix}"

	# Create trashinfo so file can be restored from trash to original location
	echo "[Trash Info]" > ${trashinfo}
	echo "Path=`dirname $file`/`basename ${file}`" >> ${trashinfo}
	echo "DeletionDate=`date +%FT%T`" >> ${trashinfo}
done
```

IMHO it is still way better to use trash-cli, as it also handles links, mountpoints etc. sanely.

---

