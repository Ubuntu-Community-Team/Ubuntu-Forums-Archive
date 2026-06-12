---
title: "Running application with administrator rights"
date: 2010-01-10
forum: Security
---

### Post by Searock on 2010-01-10
I am trying to run eclipse with administrator rights so that it can access any folder on my system.

Every time I have to open up the terminal and then type in these two commands
```

sudo -i
/etc/eclipse/eclipse

```so i tried to create a shell file with the following commands

```

#!/bin/bash
sudo -i
/etc/eclipse/eclipse

```but still, I am not able to access the /var/www folder from eclipse.

Can any one please help me with this issue, and I am not sure if I have posted the topic in correct section.

---

### Post by BkkBonanza on 2010-01-10
On your desktop press Alt-F2 and enter gksudo eclipse. And Ok.
If you want to make it permanent, edit the menu item for it and add the same gksudo prefix. Right-click the Applciations menu to start the menu editor.

---

### Post by Searock on 2010-01-10
> **BkkBonaza said:**
> On your desktop press Alt-F2 and enter gksudo eclipse. And Ok.
If you want to make it permanent, edit the menu item for it and add the same gksudo prefix. Right-click the Applciations menu to start the menu editor.

Thanks a lot :P.Thanks for the quick response.
Its a great relief, I don't have to open the terminal again.

---

### Post by mark bower on 2010-01-15
I have a similar problem.

With Ubu 9.10 I am working with a FreeBasic program called PITHY.bas.  Its function is to operate an A/D card by talking to the card's registers, with the base address set to &H300.  In order to get PITHY to compile and run, I/O permission had to be included as code lines per below.  PITHY has all three permision sets set to rwx.

Declare Function ioperm Cdecl Alias "ioperm" (Byval Portbase As Integer,Byval nPorts As Integer) As Integer 
ioperm(BAD,12,1) 

PITHY runs, but incorrect values are returned when the registers are read.    If  PITHY is executed as root/superuser on the command line, with sudo, the program responds correctly.

So what can be done?  I would very much like to be able to put code into PITHY to allow the program to be executed by any user.  Simply execute the file like any other.  Lest you wonder, I have asked for help @ FreeBasic, but the help ended in a dead end.
 
I also played with what was suggested here; the pop-up used “run” vs “o.k.”, sometimes asked for passwd, and did not execute.

mark

---

### Post by BkkBonanza on 2010-01-15
This probably has something to do with hardware access and thus requiring root. Probably what you need here is to add the setuid bit permissions. This causes the program to run as root for any user. The problem with this is that it is less secure as any program design faults can allow root compromise. There are articles on the web about how to design setuid programs to avoid security breeches. If this program is going to be sold/given to others then it's likely important to consider that aspect.

sudo chmod u+s your_file

---

### Post by mark bower on 2010-01-15
@BkkBonaza, thanks

Sounds like setting the UID attribute is the only way to do this, althoh there are risks?  I looked at man chmod, but a little difficult for me to understand.  I have a couple of books, but they do not cover alpha character use with chmod.  Specifically, what is the meaning in your code line "sudo chmod u+s file"?  Does this set up the file as being run by root?

In the process of working with this, I find I have(somehow) lost super privileges, ie, sudo now gives me the msg "rocky is not in the sudoers file.  This incident will be reported".  So I am now also trying to figure out how to restore my ability to sign on as super. I set up 9.10 with automatic log in where I am "rocky", and passwd is "jup".  So, any help here with cmd lines to restore would be appreciated, then back to the chmod issue.

---

### Post by BkkBonanza on 2010-01-15
You'll have to use visudo to edit the sudoers file so that you have access. You'll need to boot to the recovery console and work there. I've never had to go through that so I'm not sure the exact steps.

"setuid" means "set user id upon execution", where user id we means "owner". It allows an elevation of rights during execution. (This is how programs like passwd allow regular users to change their password, for example.)

Actually my mistake before as I wrote u+s when I meant o+s.

o+s means give "other" users the right to run this program with "setuid" privileges. This means that when the program runs it runs as the owner, which for you would need to be root. The reason it's unsafe is because if the program is not well written with this in mind then crafty users can manipulate the program to gain root access on the system. If you aren't in a security conscious situation then it's not likely this will be a problem. You wouldn't want to run it on systems with important data and potential hackers. 

o+s in numeric notation is the same as adding a 4 in front, eg. "chmod 4777 file"

There are pages on wikipedia that maybe can explain it better,

[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)
and
[http://en.wikipedia.org/wiki/Setuid](http://en.wikipedia.org/wiki/Setuid)

If you add suitable users to a group then chmod 4770 allows them to run the program with the owners rights. That way you can control who is allowed by adding them to the group. This is better than just wide open o+s (other with setuid).

---

### Post by mark bower on 2010-01-15
thanks for the info, links and your explanation.  i believe i get the jist of most of what is needed and changing the UID attribute for my file.  

first i will work with visudo, if i can, to regain root authority.  just wish i knew the keystrokes that i used which caused the loss.  if all else fails, here comes another reinstall and HD rebuild.  i have had some tricky stuff (for me) in volving WINE and IrfanView, and getting libraries for FB.  however, it gets a little easier each time i do it.

mark

---

### Post by mark bower on 2010-01-16
I got Sudo restored via an excellent "how to" @
          [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)
It was easy for me (a limited knowledge Ubu user), involving restore on boot, and visudo and nano.  I will post again as a thread at a later date.

I used chmod to vary the file permissions to include a user id (setuid), but PITHY still will not access the port correctly.  Specifically, the permissions were set to either rwsrwsrwx or rwsrwxrwx.  Then I executed with ./pithy and incorrect values were returned. I also tried sudo ./pithy and incorrect values were returned.  So what works, which is no change, is to execute sudo ./PITHY with file permissions of rwxrwxrwx.  In other words, the setuid seems to block PITHY from the ability to respond as needed.

In summary, I am still stuck with a program that I cannot get to work properly except to execute on command line with sudo.  The goal is to eliminate the sudo requirement.  more help please.

---

### Post by BkkBonanza on 2010-01-16
When you chmod go+s did you also chown root? Because the setuid only tells it to run as owner and if owner is not root, then still won't be running as root.

---

### Post by mark bower on 2010-01-17
o.k.  a heap of ignorance here.  i installed as rocky with passwd jup.  below is status of file permissions and ownership with ls -l:
-rwsrwsrwx 1 rocky rocky    110616 2010-01-12 14:32 pithy

how do i(what does the cmd line look like) chown root for the file?  my understanding of the above is that PITHY is owned by rocky and rocky belongs to the group rocky, and that rocky is the user.

mark

---

### Post by BkkBonanza on 2010-01-17
You can use,

sudo chown root:rocky pithy

so that root owns it. Then,

sudo chmod 4770 pithy

so that group rocky can run as setuid. This means that even though rocky can run it root privileges will be given.

See how that goes. It should be just as good as running sudo.

ls -l should show,

-rwsrwx---  root rocky pithy

---

### Post by mark bower on 2010-01-17
BkkBonaza - thank you very much for hanging in on this thread.  your "chown" and chmod(setuid) suggestions did the trick!  i can now execute by merely clicking on the file on the desktop; no terminal cmd line requirement!

so, i have learned quite a bit. i may return with more questions after trying to digest(let stuff sink in) more of "man chown" and your notes.  however, i believe i am over the 50% level of understanding on ownerships.

the importance of all this to me is that i have been able to move for my use IrfanView (via WINE) and FreeBasic to Ubuntu.  this makes my transition from XP to Ubu complete.  in the future, i only need to move one last progaram over, ACAD (via WINE). i will go back to the FreeBasic site and update my thread there with your solution credited to you.

mark

---

### Post by BkkBonanza on 2010-01-17
Happy to help. Glad it worked out.

---

