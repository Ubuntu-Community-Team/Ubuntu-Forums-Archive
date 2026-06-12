---
title: "Transer from virtual box to shared folder (permissions?)"
date: 2014-03-17
forum: Virtualisation
---

### Post by Chuck_Finley on 2014-03-17
I feel kinda guilty to keep posting on ubuntu forums for help without anything to offer.. but google and documentation just doesnt do it all for me. My problem now is that I am downloading a game on windows 7 virtual box then moving it to a shared folder on ubuntu. Now I dont have permissions to those files. My question is how do I set file permissions for myself?

---

### Post by slooksterpsv on 2014-03-17
First, don't worry about helping others, if you need help, ask, we will try to help you. If you learn enough to where you want to try and help or offer your suggestions go for it. What your asking may be helping someone who has the same question. Even if its a duplicate post, oh well, it happens (probably get pointed to dupe thread then close original thread).

Now to fix your issue, you'll need to open a terminal, if you don't know how to navigate terminal, here's a few things to help get you started:

cd = change directory so let's say your file is in Downloads starting from your home folder
cd Downloads 

Now it is case sensitive. If you want to return to your home type: cd
with nothing after it. If you don't know the file name, but have an idea, you can type in: ls
ls = list
It's like the dir command in dos.

If you're in the current folder where your file is you can put your command and 
**command** ./*filename.ext*

To change permissions try this:

pkexec chown *your_user_name*:*your_user_name* /path/to/file/you/need/permissions/on

That's the simplest way. So for example I'd do this:

```

pkexec chown shawn:shawn /home/shawn/Downloads/Oct17_Pictures.zip

```

---

### Post by Chuck_Finley on 2014-03-18
hey thanks a lot. Big help man.

---

### Post by Chuck_Finley on 2014-03-18
Actually I need to change file permissions to several files with in a few folders. I tried to figure it out myself as shown here [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

user@host:/home/user$ sudo chmod 777 -R /path/to/someDirectory

Whats with the /home/user$ ? Whats the -R? I always get a no directory found  :(

---

### Post by slooksterpsv on 2014-03-18
The /home/user (which stands for ~ (tilde)) just means you're in your home folder for your user.
The -R option on chown means recursive so it goes through each folder and  changes those permissions for all files and folders within that folder and subfolders and subfolders and subfolders and etc... haha

---

### Post by JKyleOKC on 2014-03-19
> **Chuck_Finley said:**
> Actually I need to change file permissions to several files with in a few folders. I tried to figure it out myself as shown here [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

**[COLOR="#FF0000"]user@host:/home/user$ [/COLOR]**sudo chmod 777 -R /path/to/someDirectory

Whats with the /home/user$ ? Whats the -R? I always get a no directory found  :(I've emphasized the entire command-line prompt for you. Where other operating systems use ">" or soimetimes ":" to end the prompt, most Linux districutions use "$" when you operate as a normal user, and "#" when operating as the super user.

It's possible to change this to anything you want, by editing a specific text file, but until you do, consider everything to the left of "$" on the command line as being your prompt.

The "-R" makes the command operate recursively, meaning that the change will be applied to the specified directory **plus** every file in that directory, plus every file in every subdirectory there, **all** the way down. It's a **very** dangerous option, and when such a command is given for the wrong directory, the system can become unusable -- with reinstallation from scratch being the **only** practical way to recover! It's like walking a tightrope without any safety net, so be very careful in its use.

---

### Post by Chuck_Finley on 2014-03-19
Thank you.

---

