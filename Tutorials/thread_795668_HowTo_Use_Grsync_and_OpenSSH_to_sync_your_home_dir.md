---
title: "HowTo: Use Grsync and OpenSSH to sync your /home directory over a network"
date: 2008-05-15
forum: Tutorials
---

### Post by 50words on 2008-05-15
This tutorial will cover three things:

 1) installing rsync, the Grsync GUI for rsync, and OpenSSH;
 2) using rsync over an OpenSSH connection to syncronize your /home directory between two computers; and
 3) excluding files you do not want to sync.

Reason: I use a desktop and a laptop. I want to keep my /home directory on both identical, since I use the same software, etc., on both. OpenSSH provides a secure connection if you are syncing remotely over the internet, and is a really easy way to connect to another computer on your network.

1) Installing rsync, Grsync, and OpenSSH

This is a piece of cake. Copy each of the following lines into the terminal:

```

sudo apt-get install grsync
sudo apt-get install openssh-server

```

2) Now, open up Grsync, which will be in Applications > Internet in Ubuntu, or you can hit Alt+F2 to bring up the run menu and type "grsync".

Click the +Add button and name your new session something like "50words /home" so you can easily get to it again.

In the Source and Destination fields, enter the source--the computer you are going to sync from--in the first field. In my case:

```
/home/50words/
```

Note: you must add the trailing slash if you want to copy the contents of a directory.

In the destination field--the second field--enter the computer you are going to sync to. You have to do this using the computer's IP address. (If you don't know it, use the ifconfig command in a terminal. Or use System > Administration > Network Tools, and select the Network Device to see your IP Address next in the IPv4 row, if you are using Ubuntu.)

Enter it like so:

```
192.168.0.10:/home/50words/
```

Now, in order to get SSH to work, you have to click on the Advanced Options tab in Grsync and enter the following in the Additional options field:

```
-e ssh
```

I also check "Copy symlinks as symlinks", because I want the /home directories to be identical, right down to the links in them.

3) Now, there are almost certainly some files you do not want to sync. For example, it is time-consuming to sync my Firefox cache, so I don't do it; I have a fast internet connection, so it does not really matter to me if it is synced up.

It takes a lot of text to exclude multiple files and folders using the command line. It is easier to use a separate file to identify the files and folders to exclude.

First, in the Additional options field, enter "--exclude" and the text file name in which you will list your files or directories to exclude. For example, here is my path to my exclusion file:

```
--exclude-from=/home/50words/rsync-exclude.txt
```

In that text file, just identify the files or directories you want excluded. Wildcards work. Remember that rsync will navigate relative to the directory in which it starts (the directory you identified as the source directory). Here is an example of the contents of an exclusion file:

```
/home/50words/.mozilla/firefox/*/Cache
/home/50words/.beagle
```

So there you go. Before you sync for real, use the "Simulation" button to make sure you don't get any errors, and take a look at the output to make sure you aren't accidentally deleting everything.

Edit: If you want to do a two-way sync, instead of a one-way sync, give Unison a try. It works just as well over SSH, and does a fantastic job of two-way syncing.

---

### Post by henriquemaia on 2008-07-16
Thanks for this post. In my case I use Grsync to make backups over the netword and I don't have to put the -e ssh to achieve that. Also, I'm trying to make an exclusion list, but Grsync is always insisting in copying the folder I specified. I'm still trying to figure out why.

Anyway, thanks for this howto. Very useful.

---

### Post by henriquemaia on 2008-07-16
> **henriquemaia said:**
> [...] Also, I'm trying to make an exclusion list, but Grsync is always insisting in copying the folder I specified. I'm still trying to figure out why.
hanks for this post. In my case I use Grsync to make backups over the netword and I don't have to put the -e ssh to achieve that.
Anyway, thanks for this howto. Very useful.

I figured out why and thanks to you (my fault in understanding, really). The answer is here:

> Remember that rsync will navigate relative to the directory in which it starts (the directory you identified as the source directory).

So what I was doing wrong was that I wrote the absolute path to the folders I wanted to exclude from the backup. Anyway, it doesn't make much sense to me that rsync can't understand an absolute path, but I'm happy that it works now. 

Thanks for all your help (it was all already there :D).

---

### Post by Marelo on 2008-07-30
I followed your instructions, but I'm getting these erros:

luiz@aganp:~$ rsync -r -t -v --progress -e ssh /home/luiz/Música/ 10.1.133.161:/home/marelo/Músicas/
ssh: connect to host 10.1.133.161 port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(454) [sender=2.6.9]

Both computers are on the same network and I've shared the "Músicas" folders at the 10.1.133.161 computer with all the permissions granted...

What could be the problem?...
Thanks!

---

### Post by 50words on 2008-07-30
I am not all that sophisticated at troubleshooting networking issues, but it looks like you may have a network problem to solve, first.

---

### Post by RurouniAkira on 2008-08-01
> **Marelo said:**
> I followed your instructions, but I'm getting these erros:

luiz@aganp:~$ rsync -r -t -v --progress -e ssh /home/luiz/Música/ 10.1.133.161:/home/marelo/Músicas/
ssh: connect to host 10.1.133.161 port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(454) [sender=2.6.9]

Both computers are on the same network and I've shared the "Músicas" folders at the 10.1.133.161 computer with all the permissions granted...

What could be the problem?...
Thanks!


Seems that the 10.1.133.161 computer might not have SSH installed... try to ssh on to it without rsync !

---

### Post by arrrghhh on 2008-08-21
Marelo, can you ping 10.1.133.161?  if yes, then that is a good sign.  now you have to ensure there's nothing blocking ssh (ie firewall or router if it's going across the 'net)

---

### Post by Skarpen on 2008-10-10
I'm pretty new to linux, would ssh also work over the internet and not only on the intranet?

---

### Post by 50words on 2008-10-10
> **Skarpen said:**
> I'm pretty new to linux, would ssh also work over the internet and not only on the intranet?

Yup. SSH is at its best over the internet. The internet is just one giant network.

---

### Post by Skarpen on 2008-10-13
Thank you!

---

### Post by ghij505 on 2008-10-13
[runescape](http://www.goldsrunescape.com)The famouse Blog [maple story](http://maplestory-mesos.blog.com)[maple story mesos](http://maplestory.blogs.experienceproject.com/)[Lotro Gold](http://lotro.weblog.com/)[runescape money](http://runescape-money.blog.com)I always read articles from these blog. Very excellent.The blogs about Runescape, Zezima, Loto, Cute Maple Story Online Game.

---

### Post by satellite360 on 2009-03-01
Thanks - just what I was looking for

---

### Post by HandeH on 2010-04-05
> **50words said:**
> 

... Remember that rsync will navigate relative to the directory in which it starts (the directory you identified as the source directory). Here is an example of the contents of an exclusion file:

```
/home/50words/.mozilla/firefox/*/Cache
/home/50words/.beagle
```


I think that code does not work. As you refered, you cannot use absolute paths, so the code should be: 

```
.mozilla/firefox/*/Cache
.beagle
```

Tip: Use separate exclution files for different rsync operations or take care that you don't have a hidden folder called beagle to be rsynced elsewhere.

---

### Post by camrant on 2010-06-06
How can this be done if the user name on the source computer is different than the user name on the dest server

---

### Post by apsot on 2010-11-21
> **camrant said:**
> How can this be done if the user name on the source computer is different than the user name on the dest server

in the post #1 instead of 
```
192.168.0.10:/home/50words/
``` 
you should write
```
username_of_Destination_computer@192.168.0.10:/home/50words/
```

---

### Post by ub-newbie on 2011-09-16
This thread was very useful, but I thought I would post my two cents.
What I was doing: Transfer new songs from XP iTunes to Ubuntu media server.
My user name on XP and Ubuntu are different

On my XP box, in GRSYNC:
Source: ```
C:\Documents and Settings\name1\My Documents\My Music\iTunes\iTunes Media\Music\
```
Destination: ```
192.168.1.3:/home/name2/Music/
```

Then, under "Advance Options":
```
-e "ssh -l name2"
```

When I run GRSYNC, I have to enter my password in the "shell" (also known as the command prompt) window on my XP box.

Seems to be working just fine.  Perhaps when I end up breaking it I can refer back to my own instructions.

---

### Post by cirobr on 2011-11-12
Hello,

Need to specify port 2222 on Grsync to connect over ssh to my Android tablet. May I please ask how to do it? Have tried many options such as:

-p 2222
--port=2222

PS: SSH option works correctly as 

-e ssh

Thanks.

---

