---
title: "fuse filesystem with search results?"
date: 2021-05-16
forum: Ubuntu, Linux and OS Chat
---

### Post by syadnom on 2021-05-16
I'm trying to find a fuse filesystem that would present the results of a search as a filesystem mount

ie, 'find /files -name "*.mkv"' as a mount point /mnt/mkvfiles

ls /mnt/mkvfiles = results of find /files -name "*.mkv"

does such a thing exist?

---

### Post by TheFu on 2021-05-17
No.

I sincerely hope you don't want to make a new file system just for search results.  That would definitely be overkill.
If the files are on the same file system, then using hardlinks can work. If the files are on different file systems, use symlinks instead.   You could create a directory with hard/soft-links inside with some lite scripting.  Depends on what your real goal is. The vague requirements scream, "this is an intermediate step for my true final, need."

There are many existing tools for searching files/metadata for results that can be crazy fast without creating a search-results file system.
You can use **locate**/updatedb to pre-index all files on a system, then the queries are nearly instantaneous.
Or **recoll** to search in the metadata for almost any sorts of files. There is a CLI interface ... or a GUI for recoll.

I have a bash script that knows how to search media files on the system, but there are some caveats in the use because it is only for my system and the naming convention used by my media files.  For example, there is a text DB file that lists media I never need to see again - to prevent uninteresting content from wasting time more than once.  It searches for off-line media using text files that are basically **ls -Rl** files, it searches online files using **recoll** and **locate**.  It filters all the results using **egrep** for more complex regex patterns.  It understand that media files can be local or remote and not limited to a single HDD area.

A smaller, easier, bash script is my Music search tool. I cannot find where I posted that here.  It showed how to build a DB update and search tool for regex pattern searches, then select what should be played from a list of matching m3u playlists.

What would be best would depend on what the final, real, goal is. I bet there is an efficient solution that doesn't have the overhead of thousands of file system objects.

Interesting problem.  If interested, I could post the key parts of my music-search bash script.  The "db" is just a text file:
```
$ ll ~/bin/m3u_files.dat 
-rw-rw---- 1 thefu thefu 27069 May 17 10:16 /home/thefu/bin/m3u_files.dat
```

Anyway, a simple TUI interface with a list isn't hard. If there's only 1 result, it plays immediately.
I just discovered **asciinema** - a tty recording tool that does text/terminal sessions:
[https://asciinema.org/a/NWDyqzB8sFq2TYl2NNtZBvB86](https://asciinema.org/a/NWDyqzB8sFq2TYl2NNtZBvB86)
That link will be removed in 7 days. If you like, download the recording and playback locally using 
```
$ asciinema play {filename}
```
It is just a recording, doesn't DO anything on the local machine except "show" the text as it was typed and displayed in realtime.  And my typing mistakes, of course. ;)

---

### Post by syadnom on 2021-05-17
I need to present a single directory with all of the files for my application, and it needs to look like a directory.
Files are on different file systems, so hardlinks are a no
soft links don't work well.  These are very large files and something seems to reliably break with soft links.  I've already tried this btw.  also, soft links (or hard links) don't vanish if a file is moved which can cause it to look like a corrupt file causing me plenty of issues.

I'm currently using aufs for this by I have to put a LOT of directories in as I'm running a script to append or delete directories that contain the files.  It's hacky.

---

### Post by TheFu on 2021-05-17
Can you not modify the application?  I know that nearly home media servers understand the idea of multiple disks for a single library. I used this with Plex, Kodi, Rygel, and miniDLNA.

If you need to merge multiple disks into a single file system, perhaps LVM would be better? LVM has been used in enterprises since at least 2000.

Hardlinks don't lose access to the data if the other side of the link is removed. With hardlinks, the data is retained until the reference count becomes zero. Only then are the blocks used by a file released to the file system. The lost-link problem **is** an issue with symlinks.  Most tools have special options to follow symlinks. I know samba does (wide links).  rsync has lots of specialized processing around following or retaining symlinks - I don't recall the default.  

I can't recall the last time a GUI program trying to access files was confused by following a symlink, but I know that AppImages **are** confused and don't work. This is because the AppImage unpacking gets confused when trying to determine which directory the file is actually located.  
In scripting, it is easy to figure out which directory the invoked script is in, but if that script is a symlink, it becomes slightly harder  to determine in 1 line which directory the actual file, not the symlink, is located.  The file itself **knows** it is a symlink.  There is a test for that.
```
[ -h $file ]
```
So our code can test for that condition and do different processing based on the result.  Hummm. That could solve a problem I'm having in one of my scripts.  I'm using this:
```
# Determine the directories
SCRIPT_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" >/dev/null 2>&1 && pwd )"
if [ -h "${BASH_SOURCE[0]}" ] ; then
   SCRIPT_DIR=$(/usr/bin/stat  "${BASH_SOURCE[0]}" |/bin/grep  File: | /bin/sed -e 's#^.*-> ##go')
fi
echo $SCRIPT_DIR
```
I think that should work, though it is ugly.  Might need to remove the \n at the end?

---

