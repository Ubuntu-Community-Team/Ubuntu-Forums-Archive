---
title: "change to a directory after exiting a shell script"
date: 2009-02-17
forum: The Cafe
---

### Post by shmoesus on 2009-02-17
ok hi again, oh im a n3wb at this stuff, im taking a computer course in college and a lot of my classmates and i could not figure out how to change to a different directory other that the one the shell script command was entered. my problem is is that we have made a basic(we made a basic shell script cause were new to this so please bare with me) script to make a promp so when the prompt comes up you can choose 1 -5 and it will show a vim file we have typed to corospoind to it, well number 5 is the exit option and i have
cd /home/shmoesus
but this is not working when i exit i just keep coming back to the directory that i enteded and saved the shell script, dose anyone have a answer (im sure someones reading thisgoing COME ON this is EASY) 
thanks
_shmoesus the anime god_

---

### Post by insineratehymn on 2009-02-17
Post the code... we're not gonna do your homework for you, but if you show us what you are working with we can guide you in the right direction.

---

### Post by shmoesus on 2009-02-17
yah i wouldent expect to have my answers just handed to me then i wouldent learn anything but ok here it is

#! /bin/sh
I have chosen Linux because
echo "1) It was free"
echo "2) It was a assigned OS"
echo "3) Before i come to this calss i was familiar with Linux"
echo "4) I dont know why i chose this OS"
echo "5) quit"

read choice

if [ $choice -eq 1 ] ; then
bash /home/schnellm/Linux/Free
elif [ $choice -eq 2 ] ; then 
bash /home/schnellm/Linux/Class/Assigned
elif [ $choice -eq 3 ] ; then
bash /home/schnellm/Knowledge/Linux
elif [ $choice -eq 4 ] ; then 
bash /home/schnellm/Knowledge/Unknown
else [ $choice -eq 5 ]
cd /home/schnellm
fi


on this script the choices lead to a vim file we have created in the folders as you can tell under the bash commands and when you choose the choices 1 -4 on the viom file you either have a choice 1 and 2 the first choice brings you back to this command that is listed above and the second choie is supposed to exit like choice 5 but all the exit commands are just bringing me to the same friggin directory that i entered the command in. i think its just cause mabey im stupid and i dont understan but mabey you could help me
thanks 
_shmoesu the anime god_

---

### Post by insineratehymn on 2009-02-17
How are you so sure it isn't doing exactly that?

Put some debug code in there at the end, find out what directory you are in prior to the close and then post-close.

---

### Post by shmoesus on 2009-02-17
debug? i am a newb to this stuff sorry, but when i choose 5 it goes to the directory that it is saved in 
this is the directory it keeps coming out to: schnellm@ubuntu:/Linux$
this is where i want it to end up at: schnellm@ubuntu:~$

---

### Post by saulgoode on 2009-02-17
**I have chosen Linux because**

This needs to be echo'd.

**else [ $choice -eq 5 ]**

This syntax is wrong. You want to TEST if the choice was 5; "else" merely executes it.

---

### Post by shmoesus on 2009-02-18
well all the files work but when i want to either exit from the other files that the choices lead to or the 5th coice they all exit just not to the directory i want them to exit to

---

### Post by ssam on 2009-02-18
that code starts a whole new bash process in the directory.

i have tried to find ways to change the director of the current bash, but i dont think it is possible. does anyone know?

---

### Post by bryo21 on 2009-02-20
You have to run the script on the current shell and not as a new child process. Adding a 'dot space' when running the script should do the trick.

```

bossbry21@scl01:~$ pwd
/home/bossbry21
bossbry21@scl01:~$ ls -lrt
total 8
drwxr-xr-x 2 bossbry21 bossbry21 4096 2009-02-21 02:14 dir1
-rwxr-xr-x 1 bossbry21 bossbry21  541 2009-02-21 02:22 main.sh
bossbry21@scl01:~$ **. ./main.sh**
I have chosen Linux because
1) It was free
2) It was a assigned OS
3) Before i come to this calss i was familiar with Linux
4) I dont know why i chose this OS
5) quit
**5**
bossbry21@scl01:~/dir1$ pwd
/home/bossbry21/dir1

```

---

