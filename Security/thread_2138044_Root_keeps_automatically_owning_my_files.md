---
title: "Root keeps automatically owning my files"
date: 2013-04-22
forum: Security
---

### Post by coynealan on 2013-04-22
Hi Folks, this is my first time posting on an IT forum. Here goes...

I save many downloaded files everyday but somehow they always save as root or root ends up owning them! I can temporarily solve this problem by pressing Alt + f2, opening up 'gksu nautilus'. This opens up a window and allows me to browse for the file that is owned by root, go into properties, permissions and change the owner from root to myself (alan). However, i then go back to work and download files again and they automatically save or are owned by root. _**What can i do to stop root automatically owning my files?**_ I suspect this may have been a problem from a techie sorting a problem on my laptop recently.

---

### Post by steeldriver on 2013-04-22
Hello and welcome

The only way that should happen is if whatever application you are downloading with is running as root e.g. if you use 'gksudo firefox'. How exactly are you downloading?

---

### Post by m4gnus on 2013-04-22
> **steeldriver said:**
> Hello and welcome

The only way that should happen is if whatever application you are downloading with is running as root e.g. if you use 'gksudo firefox'. How exactly are you downloading?

If I may add to this...may also happen in command line if you're using sudo. 

I.e. ```
sudo wget http://reallysweetdownload
```

---

### Post by Tim Bob on 2013-04-23
Make sure your downloading app is not setuid root.

---

### Post by Impavidus on 2013-04-23
That techie may have used a shortcut to automatically save files as root by setting the Set User ID bit on firefox or any other program you use for your downloads. You can check the permissions for that program. For firefox use```
ls -l /usr/lib/firefox/firefox*
```(/usr/bin/firefox is only a symlink)
The lines it returns should start with "-rwxr-xr-x". If the SUID has been set it will show "-rwsr-xr-x" instead.

---

### Post by coynealan on 2013-04-26
Hi Impdavidus,

Sorry for late reply, i was expecting to get a notification mail about a reply to my post/thread.

Your correct i think and the files owned by root usually are freshly downloaded files.

I just entered the command on terminal that you recommended and i got the below:

-rwxr-xr-x 1 root root 87500 Mar 29 07:07 /usr/lib/firefox/firefox
-rwxr-xr-x 1 root root  2740 Mar 29 06:08 /usr/lib/firefox/firefox.sh


What do you advise?

Thanks again

---

### Post by Impavidus on 2013-04-26
This means the setUID bit is not set on firefox, so Tim Bob's suggestion does not explain why any downloads by firefox become root-owned. Do you use any other programs for downloading? Maybe you can test another program, like wget. And when you start your browser you don't have to type your password, right? Because I assume you would have told us if that were the case.

The nasty thing is, if firefox has the permission to make root-owned files it also has the permission to modify system files, so any security leak in firefox can damage your entire system instead of just your home directory.

---

### Post by clearski on 2013-04-26
1. First of all, I assume you did not login as root, but as a regular user (uid, gid > 1000)
You can check this with the command *id* in a terminal. Please do so just to make sure.

2. Where are you saving the files? Do you download them on your desktop in your /home partition with regular files or do you use another mounted drive for music/movies? You might have some unusual uid/gid settings if you're mounting a partition for downloads. Please go into the same directory where you're saving your downloaded files and write in a terminal:

```
[I]touch testfile
ls -l testfile[/I]
```

You have to be logged in with the same username you're using when you download files. Please post the results.

And please do a* ls -l *on one of the downloaded files, too, just to see the permissions, not only the user and group.

---

### Post by coynealan on 2013-04-30
Hi Clearski,

1. I just ran the *id  *in the terminal and came up with the following:

uid=1000(alan) gid=1000(alan) groups=1000(alan),4(adm),20(dialout),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),113(netdev),124(sambashare)

2. When i download files they automatically save into my 'download directory' on my laptop hard drive (i presume). Let me try to reboot just to check that im logged in as the admin coz my password wasn't asked for in my las few power ups of the laptop. ill then enter that code into terminal and give you the result.

REgarding your above ("Please go into the same directory where you're saving your downloaded files and write in a terminal:") 
Sorry but my knowledge of 'directories' is not so good, how do i write a code in terminal in this directory, please explain.

also, i dont understand how to do this "And please do a* ls -l *on one of the downloaded files, too, just to see the permissions, not only the user and group."

thanks

---

### Post by coynealan on 2013-04-30
Hi Impavidus, Yes, i use download helper for downloading youtube and other videos. I also use transmission for torrents. Any advice?

---

### Post by Impavidus on 2013-04-30
> **coynealan said:**
> 
REgarding your above ("Please go into the same directory where you're saving your downloaded files and write in a terminal:") 
Sorry but my knowledge of 'directories' is not so good, how do i write a code in terminal in this directory, please explain.

also, i dont understand how to do this "And please do a* ls -l *on one of the downloaded files, too, just to see the permissions, not only the user and group."

Assuming you download things to the directory named "Downloads" (this is the default), open a terminal (crtl+alt+t if you're using the default desktop, else use the menu) and give the commands:```

cd Downloads
touch testfile
ls -l testfile
ls -l name_of_one_of_your_downloaded_files

```
You can copy-paste all commands to your terminal and hit enter after each of them. Post the results here. The first and second won't give output.

Also, how do you start your firefox, download helper and transmission? I assume from the dash or from an icon on the left side of your screen? Or some different way.

---

### Post by coynealan on 2013-05-20
Hi Clearski,
Do you have any more advice for me on the above please? This root owning all my files is really dragging me down.
thanks

---

### Post by coynealan on 2013-05-20
Hi Impavidus,

Sorry i was late getting back to you, i missed your post. Anyhow, i opened the terminal and entered the commands you said and came up with the below (the final >C command was accidental, i meant to do a copy shortcut)

alan@alan-Inspiron-1525:~/Downloads$ cd Downloads
bash: cd: Downloads: No such file or directory
alan@alan-Inspiron-1525:~/Downloads$ touch testfile
alan@alan-Inspiron-1525:~/Downloads$ ls -l testfile
-rw-rw-r-- 1 alan alan 0 May 21 03:08 testfile
alan@alan-Inspiron-1525:~/Downloads$ ls -l name_of_one_of_your_downloaded_files
ls: cannot access name_of_one_of_your_downloaded_files: No such file or directory
alan@alan-Inspiron-1525:~/Downloads$ ^C

Any ideas/suggestions?

---

### Post by coynealan on 2013-05-20
oh yes, i open transmission from the dashboard while i operate download helper from the icon on firefox browser

---

### Post by coynealan on 2013-05-23
anybody able to help me out? PLease.....

---

### Post by angryfirelord on 2013-05-24
Let's ask a simpler question: When you run one of your applications, does it prompt you for a password?

If not, then the only thing I can think of is that your password is stored in a gnome keyring. However, your applications shouldn't be prompting for a password.

Also, in regards to your command, name_of_one_of_your_downloaded_files isn't a literal name. You're supposed to find a file you downloaded and run it against whatever it's named as.

But as a piece of advice, you have to be very careful when you give out passwords to anyone. I don't know if the current state of your machine is due to something the "techie" did or if you had changed something, but you're putting yourself at risk by letting an application have system-wide access. If you can't remember what you or he did to cause the change, then I would just reformat and start over.

---

### Post by uRock on 2013-05-25
The **history** command may be helpful in searching for a command which may be run to cause this problem. **history** does show sudo commands.
```
urock@urock-VirtualBox:~$ history
    1  sudo adduser urock vboxsf
    2  sudo apt-get install gnome-system-tools
    3  sudo apt-get update && sudo apt-get dist-upgrade
    4  sudo apt-get install htop myunity xchat-gnome bleachbit pyrenamer
    5  htop
```

---

