---
title: "About accents in folder names"
date: 2023-08-16
forum: The Cafe
---

### Post by xinuzi on 2023-08-16
Accents, special characters (except underscore and hyphen), spaces in dir (and file) names are Not Done.
Amongst other things because they cause problems with using codes and scripts, the terminal and file transfers.

After an ubuntu installation, accents can appear automatically in directory names,
usually in the case of a non-english language that requires an accent for the plural form or another form of a word.
The system, being set to that foreign language, automatically translates the English folder names and inserts the accent(s).

That happens e.g. with the default folder names in your home dir (Images, Music, Documents, etc).

An example:

The Dutch plural form of Video alas is Video's.

Better change that "Video's" dirname to "Videos" or "Video" or whatever without an accent.

Can be accomplished gui-wise (as a sysadmin) the easiest way by:

1) Activating the view of hidden folders in your file explorer (e.g. PCManFM)
2) Going to the folder .config in your home dir (actually home/you dir)
3) Making this change in the file user-dirs.dirs:
XDG_VIDEOS_DIR="$HOME/Video's" -> XDG_VIDEOS_DIR="$HOME/Videos"

Afterwards, if the system doesn't do it automatically, it can be necessary to manually add an 
appropriate icon to the folder by right clicking its name and then properties.

---

### Post by TheFu on 2023-08-16
I avoid special characters in directory and file names.  But that doesn't mean some automatically processed files don't show up with them.  In that case, knowing how to escape the special characters 100% solves this issue - both in your shell and in scripts.

Special characters are any that are not 7-bit ASCII a-Z or 0-9.

For most people, I suspect it happens with music files where the song title has them.  Some videos and TV recordings also will have those in the name.

So, to prevent special characters screwing with your bash scripts, Always reference a script variable as "${VARIABLE}" , including the quotes.  Of course, if you are going to **echo** the VARIABLE with some other things in the output, then you'll need to escape the quotes too.

```
echo "Today is \"${DAY_OF_WEEK}\" "
```

I find that using the normal IFS of one or more spaces is really, really, handy for scripts that need to process many files.  Bash globbing (that's the technical term, honest), will allow us to let the shell expand the globbed file name pattern, separated by a space.

Call the following "script", make it executable:

```
#!/bin/bash

for filename in "$@"; do
  # Do some things
  echo "Working on ${filename} ..."
done
```


```
$ ./script *mp4
```

It is trivial, but will print each mp4 file in the current directory, provided they don't have spaces.  Any other character is allowed.  Let me make some test files in /tmp/
```
$ ll *4
-rw-rw-r--   1 tf   tf       0 Aug 16 09:07 file$fil&#941;.mp4
-rw-rw-r--   1 tf   tf       0 Aug 16 09:08 file@át.mp4
-rw-rw-r--   1 tf   tf       0 Aug 16 09:19 file"doubleQuote.mp4
-rw-rw-r--   1 tf   tf       0 Aug 16 09:07 file&file.mp4
-rw-rw-r--   1 tf   tf       0 Aug 16 09:08 file.mp4
-rw-rw-r--   1 tf   tf       0 Aug 16 09:07 file?question.mp4
-rw-rw-r--   1 tf   tf       0 Aug 16 09:19 file'singleQuote.mp4
-rw-rw-r--   1 tf   tf       0 Aug 16 09:07  file& space.mp4

```

So, if I run the script:
```
$ ./script *4    # I''m lazy, the "mp" was just wasted characters.
Working on file$fil&#941;.mp4 ...
Working on file@át.mp4 ...
Working on file"doubleQuote.mp4 ...
Working on file&file.mp4 ...
Working on file.mp4 ...
Working on file?question.mp4 ...
Working on file'singleQuote.mp4 ...
Working on  file& space.mp4 ...

```

Note how I put two spaces in the last file?  I'm actually surprised that bash globbing didn't think that was 2 files due to the space. Perhaps newer bashes automatically quote/escape filenames now?  If so, that's very nice.
Anyway, dealing with special characters in bash isn't hard anymore. Be thankful that UTF8 support is the default.

Of course, when in a shell like bash, just use tab-completion for all filenames. This will automatically escape and quote as needed.

---

### Post by xinuzi on 2023-08-19
> **TheFu said:**
> So, to prevent special characters screwing with your bash scripts, Always reference a script variable as "${VARIABLE}" , including the quotes.  Of course, if you are going to **echo** the VARIABLE with some other things in the output, then you'll need to escape the quotes too..

Indeed, I've learned to as good as always place braces around referenced variables too (and to write the variables in CAPITALS for better distinction, and often use double quotes).
Backslash for escaping certain characters, or sometimes putting certain characters in square brackets.

I keep a '0000_Rename_and_Remove_Special_Characters.sh' bash script at hand to do a first (one level) full cleanup of dirs with probably or certainly file names with undesired characters and spaces. 

The code:

```
find . -depth -name "*" -execdir rename -f 's/[\(\)\[\]\,\?\!\;\:\&\@\#\§\$\*\µ\ù\%\£\=\+\<\>\~\|]//g;s/[\ ]/_/g' {} \; 
```

The condition of the code is that the 'rename' utility is installed (it should come with any ubuntu installation, but it doesn't. The 'mv' command could be used as alternative though).
Of course more, other characters can be added.
You won't find a dot in that code, because it's necessary to make the distinction with file extensions.

Talking about video (and subtitle) files..., O.M.G., the Very Bad Habit of many distributors of those files of placing dots between almost each word within the file name before the file extension!
Something like ffmpeg doesn't like it at all (as much as it doesn't like spaces)!
 
Accentuated letters, like in French (é, è), Spanish, Portuguese, German, etc..., can also cause havoc.
Just write those accentuated letters in filenames as unaccentuated ones.
Don't ask me how the Japanese or Chinese or Arabs do it all ;-P

The general public just doesn't realize the trouble its special chars, spaces, dots, accentuated letters in its file names cause for those who like to script, manipulate and automate things.

---

### Post by TheFu on 2023-08-19
> **xinuzi said:**
> 
<snip>
Something like ffmpeg doesn't like it at all (as much as it doesn't like spaces)!
 
Accentuated letters, like in French (é, è), Spanish, Portuguese, German, etc..., can also cause havoc.
Just write those accentuated letters in filenames as unaccentuated ones.
Don't ask me how the Japanese or Chinese or Arabs do it all ;-P

The general public just doesn't realize the trouble its special chars, spaces, dots, accentuated letters in its file names cause for those who like to script, manipulate and automate things.

I haven't had issues with most characters in filenames lately. I use ffmpeg daily and it handles them fine.  I think newer versions of bash which deal with UTF8 correctly resolved many of these issues.  Accented characters haven't mattered that I've noticed in a decade, besides some editors showing them as escaped unicode and not the actual character.  But back in a shell, they are the expected character.  It is only searching the file system that makes them a hassle, since I don't always know how to enter those characters.  I can do it in vim, thanks to digraphs, but wouldn't know how in this web text entry field.

I have a very simple setup - very little GUI stuff. Perhaps the DE is getting in the way?  I stopped using any DE a few years ago. Back to fvwm as my GUI of choice that doesn't change every year because some MS-Windows-centric programmer joined the GTK+ or Qt teams.

---

