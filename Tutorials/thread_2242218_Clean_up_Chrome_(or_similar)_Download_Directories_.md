---
title: "Clean up Chrome (or similar) Download Directories automatically"
date: 2014-08-31
forum: Tutorials
---

### Post by wd5gnr2 on 2014-08-31
I got tired of my download directory being full of random files. So I wrote a simple script that got a little out of control and now it is actually useful. 

[B]Overview
[/B]The script looks at the files you pass it and tries to figure out their type. A configuration file (custom, per user, or system-wide) can tell the tool to ignore certain file types and/or to group certain file types (e.g., mp3 and flac are all music). If you name a mime type in the configuration file, and the file in question has that mime type, that's what the tool will use as the file's type. You can also specify a mime prefix (like audio/ or video/), and if that's the only match, the tool will use that. If the file's mime type doesn't match the configuration file, then the file's extension is used. So by default, all .zip files go to the zip subdirectory, all tar files to the tar subdirectory, etc.

You can run the script manually, but the real value is using incron to watch your browser download directory for renames into. Most browsers will download a file to a temporary file and then renames it when done. The incron daemon will notice this, launch the script, and any rules you've set up will cause the file to be sorted to the right subdirectory.

[B]
Details
[/B]The script is hosted on [github]("https://github.com/wd5gnr/sortbyext"). However, you only need two files: sortbyext and sortbyext.conf. The easiest thing to do is to click Download ZIP (to the right) and get the zip file. If you install git, you can also clone the repo (suggested if you think you will change it and want to push changes back to me).

Unzip the file to somewhere temporary. The install file tells you want to do:
1) Put the sortbyext file somewhere executable (suggest: /usr/local/bin) -- If you are putting it somewhere like /usr/local/bin you have to be root/sudo to do the copy, of course.
Example:

```
sudo cp sortbyext /usr/local/bin

```

2) put the sortbyext.conf file in /usr/local/share/sortbyext  directory (you'll need sudo or root to do this); you can also put it in ~/.config which does not require root but doesn't help other users

Example (3rd line is optional):
```
sudo mkdir /usr/local/share/sortbyext
sudo cp sortbyext.conf /usr/local/share/sortbyext
cp sortbyext.conf ~/.config   

```
That's it for installing it. To make incron work, you may need to install it (sudo apt-get install incron). Then (not as root):
```
incrontab -e

```
This will bring up your editor and probably a blank file unless you've used incron for something else. The text is in incron.txt that you need to add to this file:

```
/home/<USER>/Downloads  IN_MOVED_TO  /usr/local/bin/sortbyext -d $@ $@/$#

```

Obviously, you need to change <USER> and if you put sortbyext somewhere else, fix that too. You do NOT need quotes in the incrontab around $@ or $@/$#! 

[B]Tips
[/B]
If you use the -m flag, things like .tar.gz will be of extension tar.gz instead of .gz. This can cause confusion with names like xyz.1.2.3.tar which is fairly common.

As shown, copy the default conf file into your ~/.config directory if you want to make changes. The file format is documented in the file itself and the README.

If you want to see what is happening from the command line, try -v. If you want to see what incron is doing, add -V /tmp/sortbyextlog.txt to the incrontable line as an argument to the program and then move a file into your watched directory.  The output will go to the /tmp/sortbyextlog.txt file.

If you already have a cluttered directory, you can run the script yourself:
```
cd ~/Downloads
sortbyext *.zip

```

You can even do * if you just want it to try to sort everything. Files with no extension and no matching mime type are left untouched.


Here's the current help message:
```
sortbyext is a bash script to sort a busy directory by file/type extension
It is made to be called by
incron -- or you can manually pass file name to it


Copyright (C) 2014 Al Williams (al.williams@awce.com)


This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.
This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
You should have received a copy of the GNU General Public License along with this program. If not, see http://www.gnu.org/licenses/.


sortbyext by Al Williams (al.williams@awce.com)
Usage:
sortbyext [-d target_directory] [-c config_file] [-m] [-q] [-n] [-v] [-V file] file [file...]
Files with extensions cause a directory to be made
corresponding to the extension and the file moved
there.


-c (--config-file) Sets a configuration file to use; if specified, it must exist or it is an error
-d (--directory) Sets the target directory
-h (--help) Shows this message (or any bad option)
-m (--maximum-extension) Causes the largest extension to be used (e.g., x.tar.gz is a tar.gz file not a gz file)
-n (--no-overwrite) Prevents overwriting an existing file
-v Verbose mode (for debugging)
-V Verbose mode (for debugging) with output to specified file
-q (--quiet) Inhibits output messages


Exclusions, Aliases and Mime Types
The program looks for a file in your home directory:
~/.config/sortbyext.conf
If this is not found, it then looks for
/usr/local/share/sortbyext/sortbyext.conf
If this is not found, it then looks for
/usr/share/sortbyext/sortbyext.conf


If one is found, the following processing occurs on a file
named foo.bar with mime type application/example
1) If the configuration file contains the line -bar, the script skips this file
2) If the configuration file contains the line -application/example, the script skips this file
3) If the configuration file contains the a matching line it will use 
the specified alias name as the directory name. Matching lines for this example
would include:
=test:bar
=test:application/example
=test:application/ 


All of these lines would match the file and cause it to be sorted into
directory test 
4) If there is no match on #3, and the file has a usable extenstion
The program uses the extension name (e.g., pdf) as the sort directory
5) If there is a sort directory set in step 3 or 4, the file is moved into it


You can copy /usr/local/share/sortbyext/sortbyext.conf to your ~/.config directory to customize. Comments in the file will further explain the format.


Home: https://github.com/wd5gnr/sortbyext



```

---

