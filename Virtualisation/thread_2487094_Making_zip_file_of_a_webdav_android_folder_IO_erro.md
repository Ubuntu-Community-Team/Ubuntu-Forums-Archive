---
title: "Making zip file of a webdav android folder I/O error"
date: 2023-05-23
forum: Virtualisation
---

### Post by anmac1789 on 2023-05-23
I am running ubuntu 23.04 legacy version on a vmware virtual machine. I am using webdav server pro for android ([https://play.google.com/store/apps/details?id=com.theolivetree.webdavserverpro&hl=en_CA&gl=US](https://play.google.com/store/apps/details?id=com.theolivetree.webdavserverpro&hl=en_CA&gl=US)) and I have a galaxy s8. I've connected my android phone using webdav under the files app using dav://ipaddress:8080 and I can view all the files. In terminal I changed directories to the sdcard folder at the root level using cd "/run/user/1000/gvfs/dav:host=10.0.0.132,port=8080,ssl=false/sdcard" and then used the following commands to make a zip of a folder using this command ```
find ./Samsung -exec zip -0 -r "/home/username/Documents/test.zip" {} +
``` then I get a message saying "zip I/O error: Bad addresszip error: Output file write failure (write error on zip file)"

If I use ```
find . -exec zip -0 -r "/home/username/Documents/test.zip" Samsung {} +
``` then terminal hangs for a very long time and nothing is being shown. 

What should I do ?

---

### Post by MAFoElffen on 2023-05-23
Wouldn't that rather be:
```

find ./Samsung -exec zip -r "/home/username/Documents/test.zip" {} +

```
But since the find command is just providing the ./Samsung folder, why not just Zip it directly, instead of making it harder and more complex than it really is?
```

zip -r /home/username/Documents/test.zip ./Samsung

```

---

### Post by anmac1789 on 2023-05-23
because the reason is that using a webdav app, hidden files show up and im assuming could also be zipped. connecting just with mtp does not show hidden folders. This is why im trying to find out why making zip files fail when connecting android via webdav in ubuntu

---

### Post by MAFoElffen on 2023-05-23
For webdav connections from Ubuntu 22.04, I just use nautilus > Other Locations... Then at the bottom you will see "Connect To Server" where you type in the connection string in this format:
```

davs://username@IP_Adress:1111/path/to/dir

```
Then it will show up as a mount on the left panel of nautilus, which you can then select to view in the file manager. Copy what you want into a folder on your PC. Then right click on that folder > Select "Compress"...

---

### Post by anmac1789 on 2023-05-23
The problem with that is because it changes the date and is a longer process

wtf.. why is this thread marked as solved when it is not.

---

### Post by anmac1789 on 2023-05-23
> **MAFoElffen said:**
> For webdav connections from Ubuntu 22.04, I just use nautilus > Other Locations... Then at the bottom you will see "Connect To Server" where you type in the connection string in this format:
```

davs://username@IP_Adress:1111/path/to/dir

```
Then it will show up as a mount on the left panel of nautilus, which you can then select to view in the file manager. Copy what you want into a folder on your PC. Then right click on that folder > Select "Compress"...

the current working directory is /run/user/1000/gvfs/dav:host=10.0.0.132,port=8080,ssl=false$
I've done exactly that...except that I used dav://10.0.0.132:8080 as the connection and everytime I used something like this:


find ."/sdcard/DCIM/Screenshots" -exec zip -0 -v -r -u "/home/username/Documents/test.zip" {} + it fails and always gives me zip I/O error

---

### Post by MAFoElffen on 2023-05-24
> **anmac1789 said:**
> the current working directory is /run/user/1000/gvfs/dav:host=10.0.0.132,port=8080,ssl=false$
I've done exactly that...except that I used dav://10.0.0.132:8080 as the connection and everytime I used something like this:


find ."/sdcard/DCIM/Screenshots" -exec [COLOR=#ff0000]zip -0 -v -r -u "/home/username/Documents/test.zip"[/COLOR] {} + it fails and always gives me zip I/O error

I tried to point this out look at your zip commandline arguments...

```

-O output-file
       --output-file output-file
              Process the archive changes as usual, but instead of updating the existing archive,
              output  the  new  archive  to  output-file.  Useful for updating an archive without
              changing the existing archive and the input archive must be a different  file  than
              the output archive.

       -v
       --verbose
              Verbose mode or print diagnostic version info.

              Normally, when applied to real operations, this option enables  the  display  of  a
              progress  indicator  during  compression  (see  -dd  for more on dots) and requests
              verbose diagnostic info about zipfile structure oddities.

              However, when -v is the only command line argument a diagnostic screen  is  printed
              instead.   This  should  now  work even if stdout is redirected to a file, allowing
              easy saving of the information for sending  with  bug  reports  to  Info-ZIP.   The
              version  screen  provides  the  help  screen header with program name, version, and
              release date, some pointers to the Info-ZIP home and distribution sites, and  shows
              information  about  the  target environment (compiler type and version, OS version,
              compilation date  and  the  enabled  optional  features  used  to  create  the  zip
              executable).

       -r
       --recurse-paths
              Travel the directory structure recursively; for example:

                     zip -r foo.zip foo

              or more concisely

                     zip -r foo foo

              In this case, all the files and directories in foo are saved in a zip archive named
              foo.zip, including files with names starting with ".", since the recursion does not
              use  the  shell's  file-name substitution mechanism.  If you wish to include only a
              specific subset of the files in directory foo and its subdirectories,  use  the  -i
              option  to specify the pattern of files to be included.  You should not use -r with
              the name ".*", since that matches ".."  which will attempt to  zip  up  the  parent
              directory (probably not what was intended).

              Multiple source directories are allowed as in

                     zip -r foo foo1 foo2

              which first zips up foo1 and then foo2, going down each directory.

              Note  that  while  wildcards  to  -r  are  typically  resolved while recursing down
              directories in the file system, any  -R,  -x,  and  -i  wildcards  are  applied  to
              internal  archive  pathnames  once  the directories are scanned.  To have wildcards
              apply to files in subdirectories when recursing on Unix and similar  systems  where
              the  shell  does  wildcard  substitution,  either  escape  all wildcards or put all
              arguments with wildcards in quotes.  This lets zip  see  the  wildcards  and  match
              files in subdirectories using them as it recurses.

       -u
       --update
              Replace  (update) an existing entry in the zip archive only if it has been modified
              more recently than the version already in the zip archive.  For example:

                     zip -u stuff *

              will add any new files in the current directory, and update any  files  which  have
              been  modified since the zip archive stuff.zip was last created/modified (note that
              zip will not try to pack stuff.zip into itself when you do this).

              Note that the -u option with no input file arguments acts  like  the  -f  (freshen)
              option.

```
In your command, you use -0 <zero instead of capital O>... And if you did use -O, you have it without an output file specified directly after it. Then you use -r recursive after using find, which is already going to find everything in the world within that directory. Which then in your -exec command is going to populate the braces with everything (directory names and files) then try to act recursively on each one of them. Recursive recursion, ending in an I/O overflow... You see that right? Or do I need to explain that differently?

So the commands for that would actually, logically either be
```

find / -type d -name "Screenshots" -exec zip -r -v -u -O "/home/username/Documents/test.zip" {} + 2> /dev/null

```
or 
```

zip -r -v -u -O "/home/username/Documents/test.zip" /mounted_path_to/sdcard/DCIM/Screenshots 

```
You see that now?

To test your logic in a find command, do something like this
```

find / -type d -name "Screenshots" -print 2> /dev/null

```

---

### Post by anmac1789 on 2023-05-24
> **MAFoElffen said:**
> I tried to point this out look at your zip commandline arguments...

```

-O output-file
       --output-file output-file
              Process the archive changes as usual, but instead of updating the existing archive,
              output  the  new  archive  to  output-file.  Useful for updating an archive without
              changing the existing archive and the input archive must be a different  file  than
              the output archive.

       -v
       --verbose
              Verbose mode or print diagnostic version info.

              Normally, when applied to real operations, this option enables  the  display  of  a
              progress  indicator  during  compression  (see  -dd  for more on dots) and requests
              verbose diagnostic info about zipfile structure oddities.

              However, when -v is the only command line argument a diagnostic screen  is  printed
              instead.   This  should  now  work even if stdout is redirected to a file, allowing
              easy saving of the information for sending  with  bug  reports  to  Info-ZIP.   The
              version  screen  provides  the  help  screen header with program name, version, and
              release date, some pointers to the Info-ZIP home and distribution sites, and  shows
              information  about  the  target environment (compiler type and version, OS version,
              compilation date  and  the  enabled  optional  features  used  to  create  the  zip
              executable).

       -r
       --recurse-paths
              Travel the directory structure recursively; for example:

                     zip -r foo.zip foo

              or more concisely

                     zip -r foo foo

              In this case, all the files and directories in foo are saved in a zip archive named
              foo.zip, including files with names starting with ".", since the recursion does not
              use  the  shell's  file-name substitution mechanism.  If you wish to include only a
              specific subset of the files in directory foo and its subdirectories,  use  the  -i
              option  to specify the pattern of files to be included.  You should not use -r with
              the name ".*", since that matches ".."  which will attempt to  zip  up  the  parent
              directory (probably not what was intended).

              Multiple source directories are allowed as in

                     zip -r foo foo1 foo2

              which first zips up foo1 and then foo2, going down each directory.

              Note  that  while  wildcards  to  -r  are  typically  resolved while recursing down
              directories in the file system, any  -R,  -x,  and  -i  wildcards  are  applied  to
              internal  archive  pathnames  once  the directories are scanned.  To have wildcards
              apply to files in subdirectories when recursing on Unix and similar  systems  where
              the  shell  does  wildcard  substitution,  either  escape  all wildcards or put all
              arguments with wildcards in quotes.  This lets zip  see  the  wildcards  and  match
              files in subdirectories using them as it recurses.

       -u
       --update
              Replace  (update) an existing entry in the zip archive only if it has been modified
              more recently than the version already in the zip archive.  For example:

                     zip -u stuff *

              will add any new files in the current directory, and update any  files  which  have
              been  modified since the zip archive stuff.zip was last created/modified (note that
              zip will not try to pack stuff.zip into itself when you do this).

              Note that the -u option with no input file arguments acts  like  the  -f  (freshen)
              option.

```
In your command, you use -0 <zero instead of capital O>... And if you did use -O, you have it without an output file specified directly after it. Then you use -r recursive after using find, which is already going to find everything in the world within that directory. Which then in your -exec command is going to populate the braces with everything (directory names and files) then try to act recursively on each one of them. Recursive recursion, ending in an I/O overflow... You see that right? Or do I need to explain that differently?

So the commands for that would actually, logically either be
```

find . -name "/sdcard/DCIM/Screenshots" -exec zip -v -u -O "/home/username/Documents/test.zip" {} +

```
or 
```

zip -r -v -u -O "/home/username/Documents/test.zip" /mounted_path_to/sdcard/DCIM/Screenshots 

```
You see that now?

I thought zip -0 (zero) means store files without compression ? This is what I've been using, I did not use -o (the letter o). I used -r because I want hidden subfolders beginning with . (dot) in deeper levels to be included in the archive as well. I specified a particular folder with -r, not to include those folders and files outside the directory I wanted -r to act on. The -r recursive is supposed to be used only with zip command not with find command.

Why do you use / instead of find . ?

---

### Post by MAFoElffen on 2023-05-24
Look at my edit, which will use only one directory name, and be recursive under that... 

Why did I use / instead of .? I didn't know where you started from. If in the tree under the current directory, then use that as the starting point. Yes.

---

### Post by anmac1789 on 2023-05-24
> **MAFoElffen said:**
> Look at my edit, which will use only one directory name, and be recursive under that... 

Why did I use / instead of .? I didn't know where you started from. If in the tree under the current directory, then use that as the starting point. Yes.

[COLOR=#222222][FONT=Verdana]Lets go slowly to make sure that I understand what's happening here. I mounted my android's internal storage using a webdav app right ? okay then I changed the working directory into root folder of the internal storage which I use to make a zip of. So I want to zip the sdcard folder and everything in it. 

[/FONT][/COLOR][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292275&stc=1[/IMG]

Therefore, when I change directory into the root folder, am i supposed to go into the root folder or into the sdcard folder? When I use ubuntu file's "copy location" the path I get is 

/run/user/1000/gvfs/dav:host=10.0.0.132,port=8080,ssl=false <-- this is the root folder

/run/user/1000/gvfs/dav:host=10.0.0.132,port=8080,ssl=false/sdcard <-- this is the sdcard folder under root

when I cd into the root folder for example, the active working directory changes into

username@username-VirtualBox:/run/user/1000/gvfs/dav:host=10.0.0.132,port=8080,ssl=false$ 

This is why I assume that i can use find ./put/any/path/here because I'm thinking the period is like a compressed notation as a starting point to make a zip file. I want to make a zip which has the sdcard folder and all it's contents in a zip file including hidden folders and files with all the date and time preserved.

Hence, when using find ./sdcard/DCIM -print -exec zip -0 -r /path/to/zip/test.zip Screenshots/  {} +

still doesnt work...I want to know why and how


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292276&stc=1[/IMG]

This is another error that I got. I left my computer on overnight and I returned to this.

---

### Post by anmac1789 on 2023-05-25
anyone have suggestions ?

---

### Post by MAFoElffen on 2023-05-25
While ./sdcard is in the directory you are in (as a subdirectory) do
```

pwd

```

---

### Post by anmac1789 on 2023-05-25
> **MAFoElffen said:**
> While ./sdcard is in the directory you are in (as a subdirectory) do
```

pwd

```


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292285&stc=1[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292286&stc=1[/IMG]

I'm trying to use the find command which also includes the sdcard folder which is why I cd into the root of the android. Can you please try it on your end to see if you are getting the same error? I am using a galaxy s8 on android 9 oreo

I got the same error even within the sdcard folder

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292287&stc=1[/IMG]

---

### Post by anmac1789 on 2023-05-26
any suggestions for this ?

---

