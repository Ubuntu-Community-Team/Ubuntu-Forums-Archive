---
title: "samba script sudo testparm question"
date: 2010-04-26
forum: Security
---

### Post by Byb on 2010-04-26
Hi
Just found this but it is locked: [http://ubuntuforums.org/showthread.php?t=152179](http://ubuntuforums.org/showthread.php?t=152179)
I'd like to run in a script ```
sudo testparm "-s /etc/samba/smb.conf.master > /etc/samba/smb.conf"
``` but it won't. It just lists the parameters but doesn't write the updated smb.conf
If I remove the quotes I get a bash error permission denied. I have the karmic.
Please help

---

### Post by CharlesA on 2010-04-26
The only thing that testparm does is check to make sure samba.conf is configured correctly.

The -s switch tells it not to prompt you to hit enter before listing the service names (which shares are configured).

What are you trying to do exactly?

---

### Post by cdenley on 2010-04-26
I think they are trying to redirect the output of testparm to create a valid smb.conf file. However, even if he pipes this correctly, if testparm finds an error, redirecting the output to smb.conf would result in an empty smb.conf.

```

testparm -s /etc/samba/smb.conf.master && testparm -s /etc/samba/smb.conf.master|sudo tee /etc/samba/smb.conf

```

This will run testparm, and if it succeeds, it runs again, redirecting the output to smb.conf.

When you redirect the output of the sudo command, the redirection is done as the user the shell is running as, not the root privileges of the command you are running with sudo.

---

### Post by CharlesA on 2010-04-26
Thanks for the info.

---

### Post by Byb on 2010-04-26
Thank you cdenley. Not only you answer my question, but you feature extra bonus (I would not think an error in the .master would blank my .conf, instead leaving it unchanged).
I check this, but I believe you're alright with the redirection, although I don't really understand why when I double-clik my script I am not prompted for the sudo password when there is no quote in the script.
Also what was puzzeling me was these tests:
doubleclick **[B]1 - edit samba conf** [/B][SIZE=1][COLOR=Red]->[/COLOR][/SIZE] Prompted for pw [SIZE=1][COLOR=Red]->[/COLOR][/SIZE] works(gksudo gedit /etc/samba/smb.conf.master)
doubleclick **3 - restart samba **[SIZE=1][COLOR=Red]->[/COLOR][/SIZE] Prompted for pw[SIZE=1][COLOR=Red]->[/COLOR][/SIZE] works (sudo /etc/init.d/samba restart)
Maybe because they are single command scripts
doubleclick **2 - valid samba conf**[SIZE=1][COLOR=Red]->[/COLOR][/SIZE] NOT prompted although I tried to reset the lap time with sudo -k and -K[SIZE=1][COLOR=Red]->[/COLOR][/SIZE] not works, normal cause not prompted (sudo testparm -s /etc/samba/smb.conf.master > /etc/samba/smb.conf)
In terminal: bybeu@Linux:~$ sudo "./Documents/Admin samba/2 - valid samba conf" [SIZE=1][COLOR=Red]->[/COLOR][/SIZE] prompted, works
In terminal: root@Linux:/home/bybeu# "./Documents/Admin samba/2 - valid samba conf" [SIZE=1][COLOR=Red]->[/COLOR][/SIZE] prompted when opening terminal, works
In terminal: root@Linux:/home/bybeu# testparm -s /etc/samba/smb.conf.master > /etc/samba/smb.conf[COLOR=Red]->[/COLOR] idem

Thanks. I try and let you know. At least I'm very happy to have found your benevolent ear and instructive answer.
Just have to learn about tee and how multicommands scripts can "run as"

---

### Post by Byb on 2010-04-26
> **cdenley said:**
> I think they are trying to redirect the output of testparm to create a valid smb.conf file. However, even if he pipes this correctly, if testparm finds an error, redirecting the output to smb.conf would result in an empty smb.conf. ...

First, this is the best practices advice found in the header of the smb.conf.master packaged in the dl'd software.

I just tested the behaviour when I introduce error in the .master then ran from terminal [sudo testparm -s /etc/samba/smb.conf.master > /etc/samba/smb.conf ] : the erroneous parameters are just ignored, the .conf is not wiped, just generated without the erroneous parameters.

---

### Post by cdenley on 2010-04-26
Wow, that is a mess. All those commands and output mixed with comments and no "CODE" tags. Using the "tee" command is a common workaround for not being able to redirect output as root without starting a root shell.
```

sudo tee /path/to/file

```
This command will write standard input to a file as root. Instead of redirecting to a file, you can redirect to the "tee" command if you need root permission to write the file.
```

man tee

```

Also, be careful with spaces when running commands. For example, if you try to write to a file "/path/to/a file", this will not work as expected:
```

tee /path/to/a file

```
since a space is used to separate arguments, the tee command sees 2 arguments: "/path/to/a" and "file". This will result in two new files being written, neither of which are "a file". The correct commands is:
```

tee "/path/to/a file"

```

Enclosing commands and output with "CODE" tags makes it easier for us to read.
[NOPARSE]
```

code goes here

```
[/NOPARSE]
If you clean up your commands, and maybe explain them a little better, I might be able to understand what you're trying to do.

---

### Post by cdenley on 2010-04-26
> **Byb said:**
> First, this is the best practices advice found in the header of the smb.conf.master packaged in the dl'd software.

I just tested the behaviour when I introduce error in the .master then ran from terminal [sudo testparm -s /etc/samba/smb.conf.master > /etc/samba/smb.conf ] : the erroneous parameters are just ignored, the .conf is not wiped, just generated without the erroneous parameters.

First of all, that will fail unless the user you are logged in as has permission to write to /etc/samba/smb.conf, which I would not recommend. Secondly:
```

cdenley@ubuntu:~$ cat smb.conf
[global]
	netbios name = UBUNTU

[share]
	comment = test share
	path = /test
cdenley@ubuntu:~$ cat smb.conf.master
[global]
	netbios name = UBUNTU
[share
	comment = test share
	path = /test
cdenley@ubuntu:~$ testparm -s smb.conf.master>smb.conf
Load smb config files from smb.conf.master
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:Section() - Badly formed line in configuration file: share
Error loading services.
cdenley@ubuntu:~$ cat smb.conf
cdenley@ubuntu:~$

```
It appears a mistake in my smb.conf.master just blanked my smb.conf file!

---

### Post by Byb on 2010-04-26
Sorry cdenley, I was afraid to borre yourself with a too long post.
I was just saying I tryied any idea that went to my mind before asking: as you could see, I think I tryied every combination I could imagine that may work, from within terminal root or just me and with double click just from me. About the quotes around parameters, I'm a bit aware of that, and I tried this also before I found the closed post i quoted at the begenning ([http://ubuntuforums.org/showthread.php?t=152179](http://ubuntuforums.org/showthread.php?t=152179)) . I tought it was the solution as I wouldn't have imagine on my own to put the first quote just before the -s, but I don't know why it worked for this guy and not for me.

The reason why I wrote these 3 scripts is that I'm not very easy with all the things I have to learn to begin to be a beginner with Linux, and as it took me about 2 weeks (not full time, although) to have the samba running, I was afraid to forget the 3 commands, the pathes of the files and all the stuff. e.g. I'm sure in a week I'll have forget the pdbedit command (only 2 users, I and my wife, so no need I hope for a long time).

Thanks again for your help: as i stated above, errors in parameters won't result in wiped .conf, so I first tried your command as is, then I dared trying this one:```
testparm -s /etc/samba/smb.conf.master|sudo tee /etc/samba/smb.conf
```Nice presentation isn't it ;)  ? Simpler too as there is no need to check for success/fail because testparm does the job (always succeeds I believe, even when discarding errors), and last but not least..... it works :).

Thanks once again, I hope i'll have the bravery/guts/courage/nerves to make my honey on my own with your help on tee.

[EDIT] I also hope I'll have not further regrets to have flaged this topic as solved ;)

---

### Post by velbon on 2010-04-26
how can i save changes to a samba script?

---

### Post by Byb on 2010-04-26
How could I help you?

---

### Post by bodhi.zazen on 2010-04-26
FYI : sudo does not allow redirects , so you can use tee as above.

You may also use sudo bash

```
sudo bash -c "echo 'it works' > test.file"
sudo cat test.file
```

Or simply use a root shell

```
sudo -i
```

Just added that information in the event you need to use complex commands (pipes, redirects, etc) as root.

Also, if you are concerned with over writing a file, why not simply append it  (use >> rather then > ) or write to an alternate file first (in the case of large config files)?

Last, if the config file is important to you, back it up. I advise you save the original, unaltered config file and comment any changes you make.

---

### Post by cdenley on 2010-04-26
> **Byb said:**
> 
Thanks again for your help: as i stated above, errors in parameters won't result in wiped .conf, so I first tried your command as is, then I dared trying this one:```
testparm -s /etc/samba/smb.conf.master|sudo tee /etc/samba/smb.conf
```Nice presentation isn't it ;)  ? Simpler too as there is no need to check for success/fail because testparm does the job (always succeeds I believe, even when discarding errors), and last but not least..... it works :).

As I stated twice and demonstrated, an error in smb.conf CAN cause that command to blank smb.conf. If the testparm command fails to parse the file, then the standard output will be empty, so the written file will be empty. Of course if you only have an invalid parameter, this will only result in a warning, and there will still be output. However, if the file is misconfigured so it cannot be parsed, as with my demonstration, then it will result in an empty file.

---

### Post by jamesr on 2010-09-16
Hi Byb etal,

I was the originator of the original question. The reason behind the problem was that the code line ```
testparm -s /etc/samba/smb.conf.master > /etc/samba/smb.conf
```
Note without quotes on my original Debian server (Alpha Server)  because I was not using sudo. But then the Alpha died, hence to the next stage.

The command line ```
sudo testparm "-s /etc/samba/smb.conf.master > /etc/samba/smb.conf"
``` worked with 8.04 LTS.  I did not need to update the smb.conf file in recent memory until now.

But when I upgraded to 10.04 LTS, the command no longer worked so back to google and the forums. I found the new thread that referenced an old problem that had been solved and then broken then re-solved again. Hopefully for good.

It seems that the testparam route is not used very often, at least, when using Ubuntu even though it is a recommendation of the Samba organisation. One assumes that "users" must edit the "smb.conf" directly, with no checking.

Rereading the thread it seems that you use aliases but you do not give examples, at least, I could not see them.

Best Wishes and Thanks 
Note I need to change my signature.

---

### Post by CharlesA on 2010-09-17
What do you mean? The command:

```
sudo testparm "-s /etc/samba/smb.conf.master > /etc/samba/smb.conf"
```

I checked a clean install of Lucid and there isn't a file named "smb.conf.master" 

Anyway, because you are using sudo and using a redirect (>) you will get a permission denied error if the directory you are trying to write to doesn't let you have write permission.

You could need to either redirect it to a place you have write access - your home directory, or use a login to a root shell by using ***sudo -i*** in on order to run that command successfully.

```
testparm "-s /etc/samba/smb.conf > ~/smbs.conf"
``` just dumps the output to the screen.

---

### Post by jamesr on 2010-09-17
Hi Charles,

I was trying to give an explanation of the history of why I believed that the command line code worked in 8.04 and not in Lucid.

> What do you mean? The command:

Code:

sudo testparm "-s /etc/samba/smb.conf.master > /etc/samba/smb.conf"

I checked a clean install of Lucid and there isn't a file named "smb.conf.master"

That command worked in 8.04 and yes I agree that the file smb.conf.master is not available in Lucid. 

What the Samba people used to recommend was to make a copy of the default smb.conf as smb.conf.master.
Edit the file smb.conf.master, and, of course, keeping a copy.
Run the command > 
Code:

testparm -s /etc/samba/smb.conf.master > /etc/samba/smb.conf

 Note I was using a Debian system at the time and this was run as admin ie root.
 The reasoning behind this, was that the abbreviated smb.conf generated by testparm output was faster than the full file with all of the comments, I believe that this in Chapter 1 of the Samba manuals and in the heading of the default smb.conf file,  

But this command did not work in Ubuntu because of sudo and one of your fellow moderators "Iowan" replied that> This may be one of those awkward sudo instances I read about somewhere. I don't remember the specifics, but the solution was to put braces, ticks, quotes, parentheses, or something around the entire command so the shell would interpret the entire line as a sudo instruction. After much googling and trials I found that the command line given above worked.

It was only recently after I installed 10.04 (new install) on my old server that I equally found that the command did not work. As a consequence,  I starting googling and found the new forum entry. This, of course, solved the problem again.

I have further questions and comments about Samba operation and set-up but this will be a separate thread. Equally I will be asking about a possible "testparm" bug in the Samba forums.

My comments were only an explanation to Byb as to why it possibly used to work and also to say thanks for the solution in the new thread. Sorry if that was not very clear.

---

### Post by CharlesA on 2010-09-17
Thanks for the clarification. It all makes sense now. :)

Whenever I do stuff with config files I usually make a copy to a .bk file, so I have a backup incase something goes horribly wrong.

---

