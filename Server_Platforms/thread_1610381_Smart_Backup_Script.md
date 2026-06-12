---
title: "Smart Backup Script"
date: 2010-10-31
forum: Server Platforms
---

### Post by AntiBodies on 2010-10-31
Hello

Im pretty new to scripting in linux but am keen to learn.

I'm trying to create a backup script similar to a batch script I developed for windows (dos) where the backup is to a usb drive. no problems with the backup process but what I would like to do is automatically remove old files if say less 20 gigabytes (or any hard coded number) is available.

What I did with the windows script was have a if statement check if 20g was available if not remove the oldest backup then check again then remove the oldest again etc. It used goto commands to loop which I know is ugly and there is no equivalent in the linux bash world.

I think i have the core parts of the script down pat which Ill list below but the loop part to go back and check im not sure about. should I be using a for loop?? or something else?

one liner to give me the free space available on usb drive
```
df |grep usb |awk '{print $4}'
```

one liner to remove oldest backup file (tgz file)
```
ls -S *.tgz |tail -n1 |xargs rm
```

one liner to check if space is less than hard code number (or ideally variable) using the above
```
if [ $(df |grep usb |awk '{print $4}') -lt 20000000 ]; then ls -S *.tgz |tail -n1 |xargs rm; fi
```

I know I should be building this all into functions. could someone help with this??

---

### Post by brettg on 2010-10-31
I'm not quite sure what you are asking for here. 

Under what conditions do you intend your script to loop?

---

### Post by AntiBodies on 2010-10-31
basically after ive sent the last command I posted (all in one line command) how do I then say go back and check again

check if 20G available
>> if not go back, remove another file and check again
>> if so, 20G is available carry on and do the backup

I used to use a goto command in the windows batch script I used but this isn't available in BASH.. I know its possible but am just wanting pointers or example scripts on how to loop this

doing it this way is quite nice as then im not reliant on whatever capacity drive a user may put in it will always make space on the device. with a few other checks in place as well.

---

### Post by brettg on 2010-10-31
You need the while iterator.

Here is some psuedocode;

```
while FreeSpace < 20Gb do;
    DeleteOldestFile
done
```

See [while loop]("http://www.cyberciti.biz/faq/bash-while-loop/") for more info.

---

### Post by david.macquigg on 2010-11-03
Shell script languages are really terrible for solving problems like this.  Compared to a real language, like Python, they have very little power, lots of useless complexity, and are not portable to another system.

I need a backup script similar to what you are doing.  Here is what I have so far.  The Python is easy for me.  I'm still struggling with the rsync command - missing files, permission problems, etc. I plan to run this as a cron job, once I get the bugs worked out.  Suggestions are welcome.

```
# rsync_script.py       File System Backup Script       MacQuigg  3-Nov-2010
'''
Python script to do an rsync backup on a list of directories.
~'''
import os          # functions specific to the local OS
cwd = os.getcwd()  # current working directory
print "Dave's rsync script - - cwd:", cwd

from os import popen  # function to run any os command, and pipe the output
                      # back to Python
dirlist = ['bin', 'boot', 'etc', 'lib', 'opt', 'root', 'sbin',
           'selinux', 'srv', 'usr', 'var']   # list of dirs to back up
dest = "/media/sdb/rsync"         # destination for backup copies

tmp = "rsync -a %s " + dest       # template for the rsync command

for d in dirlist:
    cmd = tmp % d                    #  rsync -a  etc  /media/sdb/rsync
    print cmd
    f = popen(cmd)

f.close()


```

---

