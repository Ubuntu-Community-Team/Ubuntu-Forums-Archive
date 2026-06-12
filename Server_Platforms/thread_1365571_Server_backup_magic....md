---
title: "Server backup magic..."
date: 2009-12-27
forum: Server Platforms
---

### Post by jesushero on 2009-12-27
I have been reading about and trying ways of backing up my server, and I have finally identified my needs:

1) I need all the configuration files to be backed up

2) I need all the contect (www, databases, repositories) to be backed up

3) I need all the home folders to be backed up

4) I need all the installed packages to be identified! 

5) I need all the aforementioned on a separate system

This is the backup stuff I need. Then the restore steps:

I need these to happen on ANY computer hardware with ANY same or later version of the same distribution with the same Kernel variant:

1) All the latest versions of the identified packages to be pulled from the repositories and installed.

2) All the configuration files to be put in place

3) All the home folders and content to be put in place

4) The new system to be backed up in the same way


Is there anything out there that will do this or will I have to manually program it? 

I've had a look at SystemImager and similar tools but these only seem to work for creating exact images on identical machines (or not?)..

At the moment I'm using a bash script with tar. Ideally I'd like to save myself the trouble of having to program all this functionality into something, if there's anything already out there that will do that. If not, I guess I'll have to start...

---

### Post by Vegan on 2009-12-27
I wrote a shell script to backup my machine, and put a symbolic link into cron so I could ignore it. Then tar does its job and I can go back 2 sleep.

The downside is I wrote a program to do the work, as I did not see anything existing that was helpful for the CLI.

---

