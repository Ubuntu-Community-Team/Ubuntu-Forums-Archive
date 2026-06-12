---
title: "Finally solved: Inheritable owner and permission on Samba share"
date: 2017-06-13
forum: Server Platforms
---

### Post by mikdima on 2017-06-13
Hi,
   just wanted to share this: In this last month I was getting mad searching for a solution to inherit the owner and the permissions on a Samba share. Especially on folders, the permissions were totally changed from the parent folder. 
I mean, if I create a "A" folder in the shared folder, and I set a owner-permission on that folder, then I create a subfolder "A-A" in the "A" folder, I expect that the permissions on the "A-A" folder were the same as the "A" folder. 
I tried all the options, solutions, I read hundred of posts and so on, but in the end all the solution I found were "force directory mode = xxx" or "force create mode = yyyy" in the Samba configuration, and no one worked with "inherit permissions = yes". 

So, after digging and digging, I gave up setting the permissions on Samba and I created myself a solution as follow:
[LIST]
[*]On Samba I set "inherit owner = yes" and "inherit permissions = yes";
[*]I installed iWatch ([http://iwatch.sourceforge.net/);](http://iwatch.sourceforge.net/);)
[*]I configured iWatch in order to monitor the shared folder on Samba (with recursion enabled), and to start as a service;
[*]I created a script that sets the permissions of the file/folder created exactly as the parent folder.
[/LIST]

In the end, the Samba share config is the following:

```
[Dati]
    admin users = xxxxxxxxxx
    path = /media/dati
    valid users = yyyyyyyy
    delete readonly = yes
    write list = yyyyyyy
    writeable = yes
        inherit owner = yes
        inherit permissions = yes
    map archive = yes
        store dos attributes = yes

```

The iWatch configuration is the following:

```
<?xml version="1.0" ?>
<!DOCTYPE config SYSTEM "/etc/iwatch/iwatch.dtd" >


<config charset="utf-8">
  <guard email="iwatch@localhost" name="iWatch"/>
  <watchlist>
    <title>www permissions</title>
    <contactpoint email="xxx@yyy.it" name="Administrator"/>
    <path type="recursive" 
        alert="off" 
        exec="/etc/iwatch/setfolder '%f' " 
        events="create,isdir">/media/dati/www</path>
  </watchlist>
</config>

```

and the script that is run (/etc/iwatch/setfolder) is the following:

```
#!/bin/bash
CurFolder="$1"
CurFolderParsed=${CurFolder//\\}
CurDate=$(date +"%Y_%m_%d")
CurLogFile="/media/dati/logs/setfolder/$CurDate.log"
echo "===============" >> $CurLogFile
if [[ -d $CurFolderParsed ]]; then
    FolderPerm=$(stat -c "%a" "$CurFolderParsed")
    ParentPerm=$(stat -c "%a" "$CurFolderParsed"/..)
    echo "Current folder: $CurFolderParsed ($FolderPerm), Parent: $ParentPerm" >> $CurLogFile
    if [ $FolderPerm -ne $ParentPerm ]; then
        chmod $ParentPerm "$CurFolderParsed"        
        FolderPerm=$(stat -c "%a" "$CurFolderParsed")
        echo "New permission on directory $CurFolderParsed: $FolderPerm" >> $CurLogFile    
    fi
else
    ParentFolder=$(dirname "${CurFolderParsed}")
    ParentPerm=$(stat -c "%a" "$ParentFolder")
    chmod $ParentPerm "$CurFolderParsed"
    echo "New permission on file $CurFolderParsed in $ParentFolder: $ParentPerm" >> $CurLogFile
fi

```

Of course, you can remove all the log operations from the script in order to keep the disk clean and the script faster, it was just needed during the development/debug of this procedure. 

I hope this will help someone that is trying to achieve the same result. 

Enjoy!

Michele

---

### Post by LHammonds on 2017-06-14
That's a pretty nice solution.  I was thinking of periodically just running chown -R commands but this is much more efficient.  It only runs the commands when needed and is almost instantly corrected.

Thanks for sharing.

LHammonds

---

### Post by mikdima on 2017-06-14
...it was a pleasure to share. ;) 

Just: maybe it is more correct to change in the script the line: 
[COLOR=#000000][FONT=&quot]chmod $ParentPerm "$CurFolderParsed"
[/FONT][/COLOR]with:
[COLOR=#000000][FONT=&quot]chmod [/FONT][/COLOR][COLOR=#000000][FONT=&quot]-R [/FONT][/COLOR][COLOR=#000000][FONT=&quot]$ParentPerm "$CurFolderParsed"
[/FONT][/COLOR]
to include everything if in the while some new file has been created in the new folder. It is just a matter of milliseconds, but the possibility is anyway present. 

Cheers!
Michele

---

