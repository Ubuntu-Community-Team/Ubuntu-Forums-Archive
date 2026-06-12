---
title: "LFTP question"
date: 2015-12-27
forum: Server Platforms
---

### Post by saitoh183 on 2015-12-27
Hi everyone, 

Im new to the linux world (Another windows guy seeing if the grass is greener on the other side :)) and so far im liking the experience :). 

After 2 days of research i am unable to figure this out...I have a script that uses lftp to bring content of my ftp server over to my local machine. The issue im having is that i cant seem to figure out how to make the script delete the folders once the copy is done. Files isnt a problem with the --Remove-source-files option but no matter what i try from people suggestions and the documentation of lftp i cant get it to work. I dont know if its the location i put the line in the script or what im missing.

here is the script:

```
#!/bin/bash
login="myuser"
pass="mypassword"
host="mywebsite.com"
remote_dir="/media/sdu1/home/saitoh183/private/transfer/"
local_dir="/mnt/sdc2/Remote_server/"


base_name="$(basename "$0")"
lock_file="/tmp/$base_name.lock"
trap "rm -f $lock_file" SIGINT SIGTERM
if [ -e "$lock_file" ]
then
    echo "$base_name is running already."
    exit
else
    touch "$lock_file"
    lftp -p 22 -u "$login","$pass" sftp://"$host" << EOF
   
    set mirror:use-pget-n 5
    mirror --Remove-source-files --verbose -c -P5 --log="/mnt/sdc2/$base_name.log" "$remote_dir" "$local_dir"
    mrm -rf $remote_dir/*
    quit
EOF


    rm -f "$lock_file"    
    trap - SIGINT SIGTERM
    exit
fi

```

Now this script is the one that comes from the FAQ on my seedbox hosting site and the folder deletion portion was not there so i added it. I works if i just put ```
mrm -rf $remote_dir
``` but that ends up also deleting the base folder. When i try ```
mrm -rf $remote_dir/*
``` , I get the output: ```
Usage: rm [-r] [-f] files...
```

I have also tried 
```
rm -r
glob -d rm -r 
```

but i still get ```
Usage: rm [-r] [-f] files...
```

Any help on what i need to change to make this work would be appreciated :)

---

### Post by HermanAB on 2015-12-27
Hmm, wildcard recursive deletes are dangerous.  In my experience, it is best to only delete things manually, not in a script, since it is so easy for a mistake in a script to run away and delete oodles of stuff that you didn't want to delete, or delete things even when the copy process failed, the result being that you are left with nothing. 

That being said, I don't see an error in your script - it should work.  If it doesn't, then there may be something enabled that is trying to protect you against yourself - and the above mentioned.

---

### Post by saitoh183 on 2015-12-27
> **HermanAB said:**
> Hmm, wildcard recursive deletes are dangerous.  In my experience, it is best to only delete things manually, not in a script, since it is so easy for a mistake in a script to run away and delete oodles of stuff that you didn't want to delete, or delete things even when the copy process failed, the result being that you are left with nothing. 

That being said, I don't see an error in your script - it should work.  If it doesn't, then there may be something enabled that is trying to protect you against yourself - and the above mentioned.

I see...but in my case the transferring wont be in any danger because its a copy of the original file that i would be sending so if anything goes wrong i always have a backup. But if the script is alright, what could make it not work when i add the wildcard?

When doing a help on mrm, i get 

> Usage: mrm <files> 
                                                       Removes specified files with wildcard expansion


So i dont understand why it says 

> [COLOR=#000000][FONT=Ubuntu Mono]Usage: rm [-r] [-f] files...[/FONT][/COLOR]

when i try to use * as a wildcard

---

### Post by saitoh183 on 2015-12-27
could the problem be the version of lftp im using? I just got it with ```
apt-get install lftp
```

i tested also with a actual folder name instead of * and it does the deletion but if i try something like t* to that will fail. I know there is a debug mode in lftp but i dont know where to add it to the script in order to see what is going on.

If anyone has any alternatives, im all ears...

What im looking to do is to retrieve the files from my seedbox using a cron script to run a bash file every 1hr. After retrieval, i need the script to delete the files and folders from source. If i cant find a solution, i might have to use my windows VM in vritualbox to do it.

---

### Post by matt_symes on 2015-12-27
Thread moved to **Server Platforms**

This may be a better forum for your query. I've left an expiring redirect in General Help for you as well.

---

### Post by saitoh183 on 2015-12-27
Solved!

I added 

glob -a rm -r $remote_dir/*

and everything works as i want

```
[COLOR=#000000][FONT=Ubuntu Mono]#!/bin/bash[/FONT][/COLOR]login="myuser"
pass="mypassword"
host="mywebsite.com"
remote_dir="/media/sdu1/home/saitoh183/private/transfer/"
local_dir="/mnt/sdc2/Remote_server/"


base_name="$(basename "$0")"
lock_file="/tmp/$base_name.lock"
trap "rm -f $lock_file" SIGINT SIGTERM
if [ -e "$lock_file" ]
then
    echo "$base_name is running already."
    exit
else
    touch "$lock_file"
    lftp -p 22 -u "$login","$pass" sftp://"$host" << EOF
   
    set mirror:use-pget-n 5
    mirror --Remove-source-files --verbose -c -P5 --log="/mnt/sdc2/$base_name.log" "$remote_dir" "$local_dir"
    [FONT=Verdana]glob -a rm -r $remote_dir/*[/FONT]
    quit
EOF


    rm -f "$lock_file"    
    trap - SIGINT SIGTERM
    exit [COLOR=#000000][FONT=Ubuntu Mono]fi[/FONT][/COLOR]
```

---

### Post by coldraven on 2015-12-27
I'm happy that you found an answer but I'm confused how glob solved it. Could you please explain how glob expands the pathname. I cannot find the "glob -a" argument in the man page.

---

### Post by saitoh183 on 2015-12-27
> **coldraven said:**
> I'm happy that you found an answer but I'm confused how glob solved it. Could you please explain how glob expands the pathname. I cannot find the "glob -a" argument in the man page.

[http://www.sanitarium.co.za/delete-multiple-remote-files-and-directories-via-ftp/](http://www.sanitarium.co.za/delete-multiple-remote-files-and-directories-via-ftp/)

[http://lftp.yar.ru/lftp-man.html](http://lftp.yar.ru/lftp-man.html)

> [COLOR=#000000]Glob given patterns containing metacharacters and pass result  to  given  command  or  return[/COLOR]       appropriate exit code.

            -f            plain files (default)
            -d            directories
            -a            all types
            --exist       return zero exit code when the patterns expand to non-empty list [COLOR=#000000]            --not-exist   return zero exit code when the patterns expand to an empty list[/COLOR]

---

