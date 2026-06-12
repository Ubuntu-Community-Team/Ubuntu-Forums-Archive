---
title: "Detecting changed files recursively in a folder and run a command after detection"
date: 2013-11-18
forum: Server Platforms
---

### Post by sandyd on 2013-11-18
Is there a method to
[LIST]
[*]Recursively detect any changes (updated file, new folder, renamed folder, new file, deleted file, .etc) in a particular folder
[*]If a certain time has passed since the last change without any other additional changes, run a command
[*]Command must only be run once, it does not matter how many changes were made.
[*]
[/LIST]

I currently have setup synced configuration on multiple hosts, and I want a update in configuration to cause the server software to restart.

---

### Post by papibe on 2013-11-18
Hi sandyd.

A few ideas.

If to asses change you are using just time, you could use 'find':
```
find -mmin -5
```
to get files modified in the last 5 minutes.

If as a reference you need another directory, you may use a dry run of rsync:
```
rsync -av --dry-run source/ destination/
```

Another alternative would be to constantly watch the directory using inotifywait (from inotify-tools):
```
#!/bin/bash

while inotifywait -r -e create,modify,attrib,move,delete /path/to/folder
do
    echo "A file or directory was modified."
done

```
Does that help?
Regards.

---

### Post by sandyd on 2013-11-18
hmm, inotifywait seems to be what I want.

I am only transfering small config files accross a gigabit network, and have tested that it will never take longer than 10s for changes to propagate to all servers.

As a result, ive come up with something like this to prevent quick file edits from restarting the server like crazy

```
#!/bin/bash

#This script is run when any file changes are detected

#Check if restart process is in timeout mode

#Process is not in timeout mode, wait for 10s to make sure there are no more files to be synced
if [ ! -f /etc/varnish/sync_wait ]; then
        touch /etc/varnish/sync_wait
        #Default 10s timeout
        timer=10
        while [ $timer -gt 0 ]; do
                sleep 2
                #Check if sync_wait_add is set
                if [ -f /etc/varnish/sync_wait_add ]; then
                        if [ $timer -st 20 ]; then
                            timer=$(( $timer+10 ))
                        fi
                        rm /etc/varnish/sync_wait_add
                fi
                timer=$(( $timer-2 ))
        done
        /etc/init.d/varnish restart
        rm /etc/varnish/sync_wait
else
        #Restart process already queued, add more time
        touch /etc/varnish/sync_wait_add
fi
```

 So far, the script seems to be working, though it (may) need a bit of tuning in the future.

Thanks!

---

