---
title: "Cron &amp; rsync help needed!"
date: 2013-05-10
forum: Server Platforms
---

### Post by adscreen on 2013-05-10
Hi everyone, 

i have an issue with a cron i have setup, the cron actually works fine as it is supposed to but the main problem is with rsync and the perl script that i am running.

simply, it just wont get the files from the server, acts much like a backup, except it happens every 10 minutes.

the script is failing to sync the files from one machine to the other, and i do not know why, i know the script itself works as it will run perfectly through the terminal.

cron code = ```
#min    hour    day    month    dow    user        cmd
*/10    *    *    *    *    adscreen    /var/www/cgi-bin/sys/sys_stream.sh
```

and the script file = ```
#!/bin/sh

#IFS=$'\n'


streamsconfig='/var/www/data/streams.conf'


# check if the config file exists. If not then stop
[ -e $streamsconfig ] || exit


extensions=(.cfg .data .menu)


function getanims
{
    /usr/bin/awk 'BEGIN {
                FS="|"
            }
            {
                if ($2 ~ /\^DU/) next
                for (n=1; n<=NF; n++)
                if ($n ~ /\.(swf|mov|mpg|mpeg|mp4|avi|flv|wmv|SWF|MOV|MPG|MPEG|MP4|AVI|FLV|WMV)/) print $n
            }' $1
}


function getpics
{
    /usr/bin/awk 'BEGIN {
                FS="|"
            }
            {
                if ($2 ~ /\^DU/) next
                for (n=1; n<=NF; n++)
                if ($n ~ /\.(png|jpg|gif|PNG|JPG|GIF)/) print $n
            }' $1
}


conffile=(`cat $streamsconfig`)


# process each line of the config file
for line in ${conffile[@]}; do


    host=`echo $line | cut -d '|' -f 2`
    show=`echo $line | cut -d '|' -f 3`


    # create include string for data files
    include_list=""
    for ext in ${extensions[@]}; do
        include_list="$include_list --include=$show$ext"
    done


    # important to put exclude last
    include_list="$include_list --exclude=*"


    # retrieve the data files
    rsync -uzr $include_list adscreen@$host:/var/www/data/ /var/www/data/


    # create include string for anims and images
    include_list="--include=anims --include=images"


    for ext in ${extensions[@]}; do
        for incl in `getanims /var/www/data/$show$ext | sort -u`; do
            include_list="$include_list --include=anims/$incl"
        done


        for incl in `getpics /var/www/data/$show$ext | sort -u`; do
            include_list="$include_list --include=images/$incl"
        done
    done


    # important to put exclude last
    include_list="$include_list --exclude=*"


    rsync -zcr adscreen@$host:/var/www/html/$show/ /var/www/html/$show/
done
```

can anyone please assist me as i am new to linux stuff

i have searched high and low through forums etc with no luck as to why it wont run

---

### Post by cj13579 on 2013-05-10
Suggest a good place to start would be to look in the cron log (/var/log/cron.log). I once had something similar and it was as simple as I was running the cron job as the "wrong" user which didn't have sufficient permissions to perform the task.

---

### Post by adscreen on 2013-05-10
the guy that made our software states " Streaming
Definition: 
Streaming gives you the ability to move the data that comprises a show from one media player to another media player. To achieve this the destination player has to be set up with the steaming software. The source machine requires on extra pieces of software, its only requirement is the show that is to be streamed. 
Software Installation
Software required: 
&#8226; /var/www/cgi-bin/sys/sys_config.cgi
&#8226; /var/www/cgi-bin/sys/sys_menu.cgi
&#8226; /var/www/cgi-bin/sys/sys_notify.cgi
&#8226; /var/www/cgi-bin/sys/sys_streams.cgi
&#8226; /var/www/cgi-bin/sys/sys_stream.sh
&#8226; /var/www/html/config/index.html
All of these files should have the permissions 0755 (-rwxr-xr-x). 
for backward compatability the following have been left in place until setup scripts have been modified. 
&#8226; /var/www/cgi-bin/sys/config.cgi
&#8226; /var/www/cgi-bin/sys/notify.cgi
Cron Setup
&#8226; /etc/cron.d/stream
#min    hour    day     month   dow     user            cmd
*/10    *       *       *       *       adscreen        /var/www/cgi-bin/sys/sys_stream.sh "

i have set this up as instructed but no luck.

cron log = ```
May 11 01:10:01 mmr171 CROND[31123]: (adscreen) CMD (/var/www/cgi-bin/sys/sys_stream.sh)
May 11 01:10:01 mmr171 CROND[31122]: (root) CMD (   ^I/root/bin/restart_show.sh)
May 11 01:11:01 mmr171 CROND[31214]: (root) CMD (   ^I/root/bin/restart_show.sh)
May 11 01:12:01 mmr171 CROND[31263]: (root) CMD (   ^I/root/bin/restart_show.sh)
May 11 01:12:01 mmr171 CROND[31264]: (adscreen) CMD (/var/www/cgi-bin/sys/sys_stream.sh)
```

i have set it up every 2 mins to try and force it.

and i have also set the cron to root for the actions as well as the script.

if i do the script manually in the terminal, it asks for a password twice...

what am i missing?

---

### Post by rubylaser on 2013-05-10
It sounds like you need to setup [key based SSH login]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys"), so you can rsync without the need for entering a password each time.

---

