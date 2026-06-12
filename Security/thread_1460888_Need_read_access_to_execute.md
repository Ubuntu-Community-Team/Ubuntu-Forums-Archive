---
title: "Need read access to execute?"
date: 2010-04-23
forum: Security
---

### Post by amsterdamharu on 2010-04-23
As root I make a script that a normal user can execute impersonating root:
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)
chmod +s myfile

This because I'd like to make a nautilus script to unluck directories in my home folder. To lock them I will take away execute permission from the directory and give ownership to root. To unlock them I will give ownership back and give execute permission on the directory. This so in some weard event I or a malicious process cannot access some important directories in my home dir and destroy important files.

Problem is I did not even get to the point of setting +s in chmod, considor the following:
```

root@lapt:/home/myuser# sudo su
root@lapt:/home/myuser# echo 'whoami' > test.sh
root@lapt:/home/myuser# chmod 710 test.sh
root@lapt:/home/myuser# chown root:myuser test.sh
root@lapt:/home/myuser# ls -l test.sh
-rwx--x--- 1 root myuser 7 2010-04-24 00:32 test.sh
root@lapt:/home/myuser# ./test.sh 
root

```So the group myuser has execute permission of this file but when I try it I get permission denied:
```

myuser@lapt:/home/myuser# exit
exit
myuser@lapt:~$ whoami
myuser
myuser@lapt:~$ ./test.sh 
bash: ./test.sh: Permission denied
[code]

My question is: why do I or my group need read permission to execute the file?


Now I give myself and everyone read and execute permission and set the s (user ID bit) thinking when I run the file as myuser it will have root permission since that is the owner but no luck there either:
[code]
myuser@lapt:~$ sudo su
[sudo] password for myuser: 
root@lapt:/home/myuser# echo 'echo hi > /test' > test.sh
root@lapt:/home/myuser# chown root:root test.sh
root@lapt:/home/myuser# chmod 755 test.sh
root@lapt:/home/myuser# exit
exit
myuser@lapt:~$ ./test.sh 
./test.sh: line 1: /test: Permission denied
myuser@lapt:~$ sudo su
root@lapt:/home/myuser# chmod +s test.sh 
root@lapt:/home/myuser# exit
exit
myuser@lapt:~$ ./test.sh 
./test.sh: line 1: /test: Permission denied
myuser@lapt:~$ ls -l test.sh 
-rwsr-sr-x 1 root root 16 2010-04-24 00:38 test.sh
myuser@lapt:~$ 

```I would like to have root permission for that script without having to sudo and fill in a password and without me or anyone but root being able to read the file. Is that possible? Then I can add it as nautilus script to unlock directories without anyone else or even myself changing the script and or seeing the content.

Thank you for reading through this lengthy post, i will be off to bed now and check if anyone can give me some helpful advice here.

---

### Post by psusi on 2010-04-23
It's a script; it isn't actually executed, instead the shell interprets it.  Because of this it can't be suid and must be readable by the shell.

Try taking the .sh extension off and making sure the first line is:

#!/bin/bash

---

### Post by amsterdamharu on 2010-04-23
Hi, thank you for your reply. It doesn's seem to make any difference or I am doing something wrong. The group or user still needs read permission to execute it and setting suid still doesn't do much. Does this only work for binary files? If so then I have one question left; why do I need read permission to execute a file?


```

sudo su
echo '#!/bin/bash' > test
echo 'whoami' >> test
chmod 710 test
chown root:myuser test
exit
./test
ls -l test

```results in:
./test: Permission denied
ls -l test
-rwx--x--- 1 root myuser 19 2010-04-24 09:24 test

Giving my group read permission solves it but now I can actually see the script (would not want that)
```

sudo su
echo '#!/bin/bash' > test
echo 'whoami' >> test
chmod 750 test
chown root:myuser test
ls -l test
./test 
exit
./test
ls -l test

```results in:
myuser
-rwxr-x--- 1 root myuser 19 2010-04-24 09:27 test

But setting guid still makes it execute as normal user:
```

sudo su
echo '#!/bin/bash' > test
echo 'echo hi > /test.txt' >> test
chmod 750 test
chown root:myuser test
chmod +s test
exit
./test
ls -l test

```Results in:
./test: line 2: /test.txt: Permission denied
-rwsr-s--- 1 root myuser 32 2010-04-24 09:29 test
setting permission here to 710 gives me:
/bin/bash: ./test: Permission denied

I guess this stuff just doesn't work for scripts, maybe only for binary so I guess I'd have to start learning C now to do this.

---

### Post by amsterdamharu on 2010-04-23
Maybe found a way out of it by having sudo not ask for a password when running certain programs:

[http://www.gratisoft.us/sudo/man/sudoers.html#nopasswd_and_passwd](http://www.gratisoft.us/sudo/man/sudoers.html#nopasswd_and_passwd)

last line in /etc/sudoers
myuser ALL=NOPASSWD: ALL /home/myuser/test

When running test it asks me for a password I guess that article doesn't work on Lucid or I am doing something wrong. Giving up on this for now. Maybe check in later.

---

### Post by movieman on 2010-04-23
Setuid scrips are a major security hole, so the bit is ignored.

I believe that when the kernel executes a script it starts the relevant program and passes the script name to it, so if the user can't read the script the shell can't run it.

---

### Post by amsterdamharu on 2010-04-24
Thank you movieman, I read in another forum that scripts cannot be Suid so I've added a line in sudoers just for that script. It is set up now and works ok.

Files in /home/myuser/.gnome2/nautilus-scripts:

lock:
```

#!/bin/bash

OIFS=$IFS; # save the internal seperator
IFS=$'\n';
for file in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
    sudo /bin/lockdir "lock" $file;
done
$IFS=OIFS;

gdialog --title "Done" --msgbox "Done" 200 200

```unlock read is same as lock but the sudo line passes a different first argument:
```

    sudo /bin/lockdir "unlockr" "$file";

```unlock write is same as lock but the sudo line passes a different first argument:
```

    sudo /bin/lockdir "unlockwr" "$file";

```The file /bin/lockdir
```
#!/bin/sh
# This takes 2 parameters $1 is action which is either:
# lock for lock, unlockwr for unlock read and write, unlockr for unlock read only
# $2 is the directory to perform the action uppon, it will perform the action on subfolders as well
# to be called from nautilus scripts. since you have to be root it (only root has execute right on this file) use sudo
#here is an example of an unlock read script:
#!/bin/bash

#OIFS=$IFS; # save the internal seperator
#IFS=$'\n';
#for file in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
#do
#    sudo /bin/lockdir "unlockr" "$file";
#done
#$IFS=OIFS;

#gdialog --title "Done" --msgbox "Done" 200 200

# execute this without asking for a password add the following to etc/sudoers:
# theUser ALL=NOPASSWD: /bin/lockdir

lockIt(){
    chown -R root:root $1;
    chmod -R 000 $1;
}
unLockItr(){
    chown -R root:theUser $1;
    chmod -R 740 $1;
    chmod -R a-x+X $1;
}
unLockItwr(){
    chown -R theUser:theUser $1;
    chmod -R 600 $1;
    chmod -R a-x+X $1;
}
checkOkDir(){
    okDirectoryToUse=0;
    if [ "$1" = "/home/theUser/Videos" ]; then
        okDirectoryToUse=1;
    fi
    if [ "$1" = "/home/theUser/software" ]; then
        okDirectoryToUse=1;
    fi
    if [ "$1" = "/home/theUser/School" ]; then
        okDirectoryToUse=1;
    fi
    if [ "$1" = "/home/theUser/Pictures" ]; then
        okDirectoryToUse=1;
    fi
    if [ "$1" = "/home/theUser/Music" ]; then
        okDirectoryToUse=1;
    fi
    if [ "$1" = "/home/theUser/Documents" ]; then
        okDirectoryToUse=1;
    fi
    if [ "$1" = "/home/theUser/comics" ]; then
        okDirectoryToUse=1;
    fi
    if [ "$1" = "/home/theUser/chinese" ]; then
        okDirectoryToUse=1;
    fi
}
doAction(){
    if [ "$1" = "lock" ]; then
        lockIt $2;
    fi
    if [ "$1" = "unlockr" ]; then
        unLockItr $2;
    fi
    if [ "$1" = "unlockwr" ]; then
        unLockItwr $2;
    fi
}

checkOkDir "$2";
if [ "$okDirectoryToUse" = "1" ]; then
    doAction $1 $2;
else
     gdialog --title "Error" --msgbox "The folder you choose is not in the list of folders to lock $2" 200 200
fi

```last line in sudoers:
myuser ALL=NOPASSWD: /bin/lockdir

NOTE:
If a user needs to run the script with sudo but you don't want them to run any other scripts as sudo then the line above would allow myuser to **only** run the lockdir command but if the user is also member of admin then it can run all commands because in sudoers there is a line:
%admin ALL=(ALL) ALL
stating that anyone from the admin group can run everything. Remove the user from admin group and add them to sudoers?? (not tested).
On my install there is only one user and although I can sudo I am not member of sudoers, maybe members of adm can use sudo as well.

NOTE:
If more users need to use it copy the /bin/lockdir to /bin/lockdiruser1, take the appropriate steps for /etc/sudoers and change paths in /bin/lockdiruser1

---

