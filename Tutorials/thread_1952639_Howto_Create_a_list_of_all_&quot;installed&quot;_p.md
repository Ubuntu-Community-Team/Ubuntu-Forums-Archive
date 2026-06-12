---
title: "Howto: Create a list of all &quot;installed&quot; packages by date"
date: 2012-04-04
forum: Tutorials
---

### Post by Jose Catre-Vandis on 2012-04-04
################
NB: This part **grep " \ install\ "**, seems to be not working on my 12.04 install. You can replace with **grep -w install** while I investigate.
################

I've seen a request for this several times on the forum and never really seen a concrete answer: how to list all the packages that have been installed since the OS was installed, by date. Yes, you can get a list by using "dpkg -l", but this doesn't give the whole story.

The answer comes from the dpkg.log files in /var/log. There is the current log (dpkg.log), the previous log (dpkg.log.1) and then the archived logs (dpkg.log.2.gz -> ).

The simple command to grab from the current log is:

```
cat /var/log/dpkg.log | grep " \ install\ "
```

The previous log:

```
cat /var/log/dpkg.log.1 | grep " \ install\ "
```

And archived logs:

```
zcat /var/log/dpkg.log.2.gz | grep " \ install\ "
```

To get the full list of packages installed I wrote a simple bash script. The script I called pkginstalls.sh, put it in my home directory and ensured it was executable:

```
chmod a+x $HOME/pkginstalls.sh
```

Here is the script:

```
#!/bin/bash
#pkginstalls.sh
#creates text file with a list of all packages installed by date

#first append all info from archived logs

i=2
mycount=$(ls -l /var/log/dpkg.log.*.gz | wc -l)
nlogs=$(( $mycount + 1 ))

while [ $i -le $nlogs ]
do
if [ -e /var/log/dpkg.log.$i.gz ]; then
zcat /var/log/dpkg.log.$i.gz | grep "\ install\ " >> $HOME/pkgtmp.txt
fi
i=$(( $i+1 ))

done

#next append all info from unarchived logs

i=1
nulogs=$(ls -l /var/log/dpkg.log.* | wc -l)
nulogs=$(( $nulogs - $nlogs + 1 ))
while [ $i -le $nulogs ]
do
if [ -e /var/log/dpkg.log.$i ]; then
cat /var/log/dpkg.log.$i | grep "\ install\ " >> $HOME/pkgtmp.txt
fi
i=$(( $i+1 ))

done

#next append current log

cat /var/log/dpkg.log | grep "\ install\ " >> $HOME/pkgtmp.txt

#sort text file by date

sort -n $HOME/pkgtmp.txt > $HOME/pkginstalls.txt

rm $HOME/pkgtmp.txt

exit 0
```

Running it:
```
./pkginstalls.sh
```
creates a file in my home directory called pkginstalls.txt that I can then use to examine what was installed and when. Unfortunately it doesn't show meta-packages such as "xubuntu-restricted-extras" but if you are aware of some of the contents of meta-packages you should be able to track down where it happened. 

Delete or rename the pkginstalls.txt file before you run the script again.

If you have been religiously installing via the command line, and you have enabled a long enough history file, you can get similar information (no date, and excluding initial installation) by typing:
```
 history | grep "apt-get install"
```

This script is benign and doesn't affect any part of your system. To remove just delete the script.

[EDIT]

There is also more detailed installation information in /var/log/apt/ in the history.log and history.log.X.gz files and term.log and term.log.X.gz files

---

### Post by arapaho on 2012-05-27
Can you tell how to restrict this command so that it would list only changes from a given day, like from today or from the last two or three days? Or alternatively can you tell me how to scroll up and down this list? When I executed these commands the list was so long that most of it I couldn't see. This would be very helpful when user has a crash and wants to revert changes that might have caused the crash.

I am also looking for commands that are used in Synaptic or Muon to repair broken packages.

---

### Post by Jose Catre-Vandis on 2012-05-28
@ arapaho

You could add | less or | more to the end of the command to enable you to scroll through the output.

To view for a specific day/date you can pipe in another grep e.g.
```
cat /var/log/dpkg.log | grep "\ install\" | grep "2012-05-23"
```

There are many ways you could do this using grep, sed and awk

---

### Post by arapaho on 2012-06-11
```
cat /var/log/dpkg.log |less
```
Works for me perfectly, but this doesn't:
> **Jose Catre-Vandis said:**
> ```
cat /var/log/dpkg.log | grep "\ install\" | grep "2012-05-23"
```
I get only 
>
>
after this command.

```
cat /var/log/dpkg.log | grep " \ install\ "
```
returns nothing.

---

### Post by Mark_in_Hollywood on 2013-06-13
I have damaged my file system's root or boot. In any case, the OS will not boot. I'm in LiveUSB session and would like some help using this post to make a list of installed packages so after re-installation I may bring my 'puter back to life.

---

### Post by Ricalsin on 2013-07-20
**Thank you for this excellent script!**  :D

---

### Post by Traxster on 2013-08-13
> **Jose Catre-Vandis said:**
> ################
NB: This part **grep " \ install\ "**, seems to be not working on my 12.04 install. You can replace with **grep -w install** while I investigate.
################

I've seen a request for this several times on the forum and never really seen a concrete answer: how to list all the packages that have been installed since the OS was installed, by date. Yes, you can get a list by using "dpkg -l", but this doesn't give the whole story.

The answer comes from the dpkg.log files in /var/log. There is the current log (dpkg.log), the previous log (dpkg.log.1) and then the archived logs (dpkg.log.2.gz -> ).

The simple command to grab from the current log is:

```
cat /var/log/dpkg.log | grep " \ install\ "
```

The previous log:

```
cat /var/log/dpkg.log.1 | grep " \ install\ "
```

And archived logs:

```
zcat /var/log/dpkg.log.2.gz | grep " \ install\ "
```

To get the full list of packages installed I wrote a simple bash script. The script I called pkginstalls.sh, put it in my home directory and ensured it was executable:

```
chmod a+x $HOME/pkginstalls.sh
```

Here is the script:

```
#!/bin/bash
#pkginstalls.sh
#creates text file with a list of all packages installed by date

#first append all info from archived logs

i=2
mycount=$(ls -l /var/log/dpkg.log.*.gz | wc -l)
nlogs=$(( $mycount + 1 ))

while [ $i -le $nlogs ]
do
if [ -e /var/log/dpkg.log.$i.gz ]; then
zcat /var/log/dpkg.log.$i.gz | grep "\ install\ " >> $HOME/pkgtmp.txt
fi
i=$(( $i+1 ))

done

#next append all info from unarchived logs

i=1
nulogs=$(ls -l /var/log/dpkg.log.* | wc -l)
nulogs=$(( $nulogs - $nlogs + 1 ))
while [ $i -le $nulogs ]
do
if [ -e /var/log/dpkg.log.$i ]; then
cat /var/log/dpkg.log.$i | grep "\ install\ " >> $HOME/pkgtmp.txt
fi
i=$(( $i+1 ))

done

#next append current log

cat /var/log/dpkg.log | grep "\ install\ " >> $HOME/pkgtmp.txt

#sort text file by date

sort -n $HOME/pkgtmp.txt > $HOME/pkginstalls.txt

rm $HOME/pkgtmp.txt

exit 0
```

Running it:
```
./pkginstalls.sh
```
creates a file in my home directory called pkginstalls.txt that I can then use to examine what was installed and when. Unfortunately it doesn't show meta-packages such as "xubuntu-restricted-extras" but if you are aware of some of the contents of meta-packages you should be able to track down where it happened. 

Delete or rename the pkginstalls.txt file before you run the script again.

If you have been religiously installing via the command line, and you have enabled a long enough history file, you can get similar information (no date, and excluding initial installation) by typing:
```
 history | grep "apt-get install"
```

This script is benign and doesn't affect any part of your system. To remove just delete the script.

[EDIT]

There is also more detailed installation information in /var/log/apt/ in the history.log and history.log.X.gz files and term.log and term.log.X.gz files

did not work for me. After I set up your script and change permissions like you state, below is the responce I received from bash. I am running 13.04 Desktop (amd64)

```
root@hades:/home# ./pkginstalls.sh
ls: cannot access /var/log/dpkg.log.*.gz: No such file or directory
ls: cannot access /var/log/dpkg.log.*: No such file or directory
root@hades:/home# 

```

---

### Post by deadflowr on 2013-08-13
> **Traxster said:**
> did not work for me. After I set up your script and change permissions like you state, below is the responce I received from bash. I am running 13.04 Desktop (amd64)

```
root@hades:/home# ./pkginstalls.sh
ls: cannot access /var/log/dpkg.log.*.gz: No such file or directory
ls: cannot access /var/log/dpkg.log.*: No such file or directory
root@hades:/home# 

```


It'll only work if have those files
You can find out quickly by running
```
ls /var/log | grep dpkg
```

That'll list all the dpkg log files in /var/log.

Sidenote: You understand there's no need to run this script as root.

---

### Post by Merrattic on 2013-08-15
If you have an SSD on board, you may have edited your fstab to stop writing log files ;)

Also the single commands at the top have an extra space between the " and the \ before install. remove the space if copying these for these commands to work.

---

