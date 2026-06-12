---
title: "Xsession: warning: unable to write to /tmp; Xsession may exit with an error"
date: 2021-02-18
forum: Ubuntu/Debian BASED
---

### Post by 4dri4n on 2021-02-18
someome help me i cannot login to my user account because i'm facing a problem in three days ago while i was taking free courses from firefox browser then when i felt that the system was somewhat crashed i opened the CPU graph because i was monitoring the processor traffic and then accidentally pressed my finger on the "kill session" so the screen blackened and when i reboot the machine i couldn't open my user account to access the desktop. so when i type in the username and password technically a window pops out that says: (Xsession: warning: unable to write to / tmp; X session may exit with an error) .. 3 days ago and i've been trying to solve this problem and it didn't work so I got an idea to open the terminal with CTRL + ALT + F1 to copy my stored data on the hard disk to my 4G flash drive to protect from data corruption in case something happens when i type " apt-get clean "my data will be safe

---

### Post by Bashing-om on 2021-02-18
Volunteers: the Aid to copy thread is - [https://ubuntuforums.org/showthread.php?t=2458164](https://ubuntuforums.org/showthread.php?t=2458164)

Here in this thread we focus on restoring the GUI.

4dri4n;

From the terminal show us the results of commands:
```

ls -al .ICEauthority
ls -al .Xauthority
echo $XAUTHORITY
sudo lshw -C display

```

As we start looking for a way forward.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by 4dri4n on 2021-02-18
> **Bashing-om said:**
> Volunteers: the Aid to copy thread is - [https://ubuntuforums.org/showthread.php?t=2458164](https://ubuntuforums.org/showthread.php?t=2458164)

Here in this thread we focus on restoring the GUI.

4dri4n;

From the terminal show us the results of commands:
```

ls -al .ICEauthority
ls -al .Xauthority
echo $XAUTHORITY
sudo lshw -C display

```

As we start looking for a way forward.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

okay wait, are you still here?

---

### Post by Bashing-om on 2021-02-18
4dri4n; Welp - 

I do pop in and about and around .

[INDENT]sometimes you see me
[INDENT][INDENT]sometimes you don't
[/INDENT][/INDENT][/INDENT]

---

### Post by 4dri4n on 2021-02-18
> **Bashing-om said:**
> 4dri4n; Welp - 

I do pop in and about and around .

[INDENT]sometimes you see me
[INDENT][INDENT]sometimes you don't
[/INDENT][/INDENT][/INDENT]

oh thank god you still here, you know im really depressed for this case last 5 minutes i went to the darkweb in the black hat chat (irc) none can have the solution for  /tmp dir and i went to the daniel's chat too and the linuxquestions.org and finally here can't find the solution, i never give up and everyone tells me they don't even know how to copy files to the USB, my computer closed for 3 days ago that's sad

---

### Post by Bashing-om on 2021-02-18
4dri4n; Hey -

Keep focus on one thing at a time - 
here is getting your GUI restored and to that end answer the request in post #2 of this thread. Then we see what there is to do.

[INDENT]like many things
[INDENT][INDENT]garbage in gets garbage out
[/INDENT][/INDENT][/INDENT]

---

### Post by 4dri4n on 2021-02-18
> **Bashing-om said:**
> 4dri4n; Hey -

Keep focus on one thing at a time - 
here is getting your GUI restored and to that end answer the request in post #2 of this thread. Then we see what there is to do.

[INDENT]like many things
[INDENT][INDENT]garbage in gets garbage out
[/INDENT][/INDENT][/INDENT]

thank you for being with me sir :-) 
this is the results and the last command doesn't work: [http://s01.geekpic.net/di-P6OIP9.jpeg](http://s01.geekpic.net/di-P6OIP9.jpeg)

---

### Post by Bashing-om on 2021-02-18
4dri4n; Hummm ...

No return from the command "echo $XAUTHORITY" ??

Then see thread [http://ubuntuforums.org/showthread.php?t=2151518&highlight=xauthority](http://ubuntuforums.org/showthread.php?t=2151518&highlight=xauthority) - post#8 suggest a resolution,

As to lshw - maybe kali does not include the tool in a default install ? But if replacing the user config files fixes, then we not worry about a graphic's driver.


[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by deadflowr on 2021-02-18
*Thread moved to **Ubuntu/Debian BASED***

---

### Post by 4dri4n on 2021-02-19
alright these are advanced commands for me inevitably, anyway i am now browsing the system via the command line and there is no problem with that and as for the graphical interface i think it is fine i can't login with user account thats it but the damaged file is /tmp directory because when i opened the CPU graph and then i killed the session i can't access to the desktop yet

---

### Post by Bashing-om on 2021-02-19
4dri4n - yup

> 
i can't access to the desktop yet


Why you replace the config files per provided instructions,

[INDENT]in the process of learning
[/INDENT]

---

### Post by 4dri4n on 2021-02-19
no i don't, wait check it out here [https://askubuntu.com/questions/20783/how-is-the-tmp-directory-cleaned-up](https://askubuntu.com/questions/20783/how-is-the-tmp-directory-cleaned-up)
as i read the /tmp file is automatically cleaned up every reboots and yesterday i clean it manually by this code: 
sudo rm -r /tmp/*
and still the same issue but how if i try to create a new /tmp file and delete the original one then replace it with the first file, so the system will read it as a normal file! is this work?

---

### Post by Bashing-om on 2021-02-19
4dri4n - nope

Your link reference is pre systemd as the initiate system.
What initiate system do you have on kali ?

consider: Replacing the config files, what have you to loose beside some ignorance ?

one step forward for kali
[INDENT][INDENT]q huge step forward in linux
[/INDENT][/INDENT]

---

### Post by 4dri4n on 2021-02-19
hello i'm back 
finally i solve it :-D ! and i want to thank you again for your help and everything you really a genuis man !

---

### Post by Bashing-om on 2021-02-19
4dri4n; Great !

> 
finally i solve it


Please tell us what the "solve" was - posterity will thank you.

[INDENT][INDENT]it is what it is
[/INDENT][/INDENT]

---

### Post by 4dri4n on 2021-02-19
> **Bashing-om said:**
> 4dri4n; Great !



Please tell us what the "solve" was - posterity will thank you.

[INDENT][INDENT]it is what it is
[/INDENT][/INDENT]

well i don't fix the /tmp directory yet it's pretty complicated but i  found an alternative to transferring files instead of copying them to a USB drive because the space was huge and when i said "i solve it" i mean i find another way to save my data so first i go to the terminal and i type this command:
sudo -i 
i become a root after that 
2) i rebooted my machine and login with root 
3) i open the terminal and change the user by this command:
su -l (username)+(password) 
4) i tab "ls" command" to view all the home directory and it's done
5) i move everything to my /root/Desktop/ by this command:
sudo mv (file name) /root/Desktop/
6) packed the data in one folder and back it up to the google drive
and that's it !

---

### Post by 4dri4n on 2021-02-19
i know you might be wondering if i were backed them up via "rsync" it would have been much easier and even could recovery the deleted at a later time.  i would do it but i used the first trick to be able to access it at any time over the internet and the third trick if i move the files to the apache server then access to it through my local IP by one link and download everything out  there!  so now i will download another distro and burn it then start my new system safely.

---

### Post by Bashing-om on 2021-02-19
4dri4n

Pleased that you saw a way through -
As this matter is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by 4dri4n on 2021-02-19
of course, it is for my pleasure by the way all thanks to you Mr. Bashing-om 
i want to consult you as a beginner in Linux system what do you advise me to start learning anything about it and become a professional like you?

---

### Post by Bashing-om on 2021-02-20
4dri4n; Well -

Just use the system and follow your curiosity - but remain aware linux is fast moving such that old docs may no longer apply. Time and experience will allow you to differentiate.

[INDENT]one learns more
[INDENT][INDENT]in helping others
[/INDENT][/INDENT][/INDENT]

---

### Post by 4dri4n on 2021-02-20
okay sir thanks for the advice :-D 
i wanna ask you something, this website ( [https://samy.pl](https://samy.pl) ) used advanced technique when you press F12 to view the source code it tells you "You found Easter Egg #12" and the same thing for the mouse right click! he even grab your IP address and typing it by such a like unix bash script and the interface like a desktop mac OS! also check the power icon! did you have any idea about that secret?

---

