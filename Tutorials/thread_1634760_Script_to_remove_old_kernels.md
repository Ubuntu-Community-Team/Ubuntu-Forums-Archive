---
title: "Script to remove old kernels"
date: 2010-11-30
forum: Tutorials
---

### Post by InkyDinky on 2010-11-30
Originally posted here:[http://www.go2linux.org/clean-linux-kernel-images-grub-menu]("http://www.go2linux.org/clean-linux-kernel-images-grub-menu") by Deven
Just too damn good not to share. Especially seeing as how when I attempted to manually remove the old kernels I ended up spending a few hours getting a kernel back on after deleting all of them. :)

```

#/bin/bash
ls /boot/ | grep vmlinuz | sed 's@vmlinuz-@linux-image-@g' | grep -v `uname -r` > /tmp/kernelList
for I in `cat /tmp/kernelList`
do
aptitude remove $I
done
rm -f /tmp/kernelList 
update-grub #not sure if needed 

```
save as cleanKernels.sh
Execute as root or chmod 755 it.
```
sudo bash cleanKernels.sh
```

Yippee you just freed up some disk space!

---

### Post by pixnaps on 2010-12-10
Very cool.  Is there any easy way to modify it so that it also retains your next most recent kernel (in addition to your current one) as backup, and only removes kernels from the third one onwards?

---

### Post by marin123 on 2010-12-10
```
sudo apt-get install grub-customizer
```

you can edit grub menu, change default os, change background picture etc...

---

### Post by InkyDinky on 2010-12-10
I believe this will get the job done for you.
It is UNTESTED since I cleaned out my extra kernels but I'm pretty sure that it works keeping the last entry in the /tmp/kernelList file. This last entry should be the latest due to alphanumeric reporting of ls.
```

#!/bin/bash
counter=1
ls /boot/ | grep vmlinuz | sed 's@vmlinuz-@linux-image-@g' | grep -v `uname -r ` > /tmp/kernelList
numberOfExtraKernels=`wc -l /tmp/kernelList`
for l in `cat /tmp/kernelList`
do
    if [ $counter -lt $numberOfExtraKernels ]
    then 
        aptitude remove $l
        let "counter +=1"
    fi
done
rm -f /tmp/kernelList
updage-grub 

```

---

### Post by oldfred on 2010-12-10
Have not tried it. but minor typo.

updage-grub
s/b
update-grub

---

### Post by oldfred on 2010-12-10
I do not know bash so I had to do a little research.

This worked for me, I had to add the echo to know what was what and remove the file name from the wc command.

```
#!/bin/bash
counter=2
ls /boot/ | grep vmlinuz | sed 's@vmlinuz-@linux-image-@g' | grep -v `uname -r ` > /tmp/kernelList
numberOfExtraKernels=`wc -l /tmp/kernelList | awk '{print $1}'`
for l in `cat /tmp/kernelList`
do
    if [ "$counter" -lt "$numberOfExtraKernels" ]
    echo "$l", "$counter", "$numberOfExtraKernels"
    then 
        aptitude remove $l
        let "counter +=1"
    fi
done
rm -f /tmp/kernelList
update-grub
```

When I ran it with counter =1 it deleted all but 1, so now I cannot test with counter =2.

---

### Post by jawilljr on 2010-12-10
One liner below to remove all but the latest kernel:

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs -p sudo apt-get -y purge
```Jerry

---

### Post by HunterZ on 2010-12-18
> **marin123 said:**
> ```
sudo apt-get install grub-customizer
```you can edit grub menu, change default os, change background picture etc...
No such package in the normal Ubuntu repos. What PPA did you get it from?

---

### Post by marin123 on 2010-12-19
> **HunterZ said:**
> No such package in the normal Ubuntu repos. What PPA did you get it from?

[https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

you have instructions on this link...

---

### Post by ClintEgon on 2011-01-13
```

#! /bin/sh

oldKernelsList=$(ls /boot/ | grep vmlinuz  | grep -v `uname -r` | sed 's/vmlinuz-\(.*\)\(-.*\)$/linux-image-\1\2\nlinux-tools-\1\nlinux-headers-\1\2\nlinux-headers-\1\n/g') && aptitude remove ${oldKernelsList} && update-grub

```

bye

---

### Post by kim-kulak on 2011-10-21
> **oldfred said:**
> I do not know bash so I had to do a little research.

This worked for me, I had to add the echo to know what was what and remove the file name from the wc command.

```
#!/bin/bash
counter=2
ls /boot/ | grep vmlinuz | sed 's@vmlinuz-@linux-image-@g' | grep -v `uname -r ` > /tmp/kernelList
numberOfExtraKernels=`wc -l /tmp/kernelList | awk '{print $1}'`
for l in `cat /tmp/kernelList`
do
    if [ "$counter" -lt "$numberOfExtraKernels" ]
    echo "$l", "$counter", "$numberOfExtraKernels"
    then 
        aptitude remove $l
        let "counter +=1"
    fi
done
rm -f /tmp/kernelList
update-grub
```

When I ran it with counter =1 it deleted all but 1, so now I cannot test with counter =2.


OK, this is useful enough that it could use a little improvement. What I have done in the following script is:
[LIST]
[*]remove the insecure temp file
[*]generate a list of kernels to keep
[*]increase permissions (sudo) only when needed
[/LIST]

I call this script "purge-kernel"

```
#!/bin/bash

# Get a list of the kernels that are installed.
kernelList=$(cd /;ls boot/vmlinuz*)

# Make a list of the kernels to keep. These are the kernels linked to by /vmlinuz,
# /vmlinuz.old, and the currently running kernel.
keepList="$(readlink -q /vmlinuz) $(readlink -q /vmlinuz.old) boot/vmlinuz-$(uname -r)"

# Change the list of file names to list of package names.
kernelPkg=$(sed 's@boot/vmlinuz-@linux-image-@g' <<<$kernelList)
keepPkg=$(sed 's@boot/vmlinuz-@linux-image-@g' <<<$keepList)

# Create a list of packages to purge. This is the list of installed kernels with the kernels
# to keep removed.
purgePkg=${kernelPkg}
for keep in $keepPkg
do
    eval purgePkg=\${purgePkg/$keep}
done

purgePkg=$(echo $purgePkg)  # Remove extra white space

echo "kernels to keep: $keepPkg"

# If there are any kernels to remove then purge them and update grub;
if [ -n "${purgePkg}" ]
then
    tmpfile=$(mktemp)
    chmod +x $tmpfile
    echo "dpkg --purge ${purgePkg};update-grub"
    echo "dpkg --purge ${purgePkg};update-grub" > $tmpfile
    sudo -s $tmpfile
    sleep 1  # following 'rm' fails otherwise.
    rm -f $tmpfile
else
    echo "No kernels to purge."
fi

exit
```

---

### Post by linuxwhitebelt on 2013-03-30
I'm sorri i know this is a veri old post but i'm looking for a script for this job. I 've run this script setting the counter on 6! and it deletes all the kernels but the last one. Could it be the "let" sentence, i dont know its functioning.

---

### Post by schragge on 2013-04-03
May I suggest a much easier [post=12531091]script[/post] for this? It will keep only two latest kernels although.

---

### Post by overdrank on 2013-04-03
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

