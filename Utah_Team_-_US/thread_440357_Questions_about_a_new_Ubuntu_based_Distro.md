---
title: "Questions about a new Ubuntu based Distro?"
date: 2007-05-11
forum: Utah Team - US
---

### Post by moriancumer_12 on 2007-05-11
I'm in the process of developing a new Ubuntu-server based distro. 
Description:
Name:CLIbuntu
A commandline only distro with built-in tutorials for those hesitant to use the commandline. It will allow them to follow the tutorials, which are customized for the distro, and practice and apply the concepts side by side on the same system. Tutorials will include Linux/bash commands, configurations and console applications. I'll enable framebuffer so that you can view video and pictures. I'll develop a rsync script to easily download updated and new tutorials. I've just submitted this project to so sourceforge. 

Questions:
How do I get this project approved to be added to the 3rd party projects in the Ubuntu forum?
What is the process and legality of redesigning the Ubuntu logo?

Also, I would like to show this to the group for constructive feedback, whenever. It still has some work to be done, but I'm new to this whole thing and any advise would be appreciated. 
thanks,
Jared

---

### Post by deepwave on 2007-05-11
I like the idea of commandline tutorials, but I think it would do better to have it as a program rather than an entire distro.  I imagine something like a sandboxed bash environment, with help displayed on using bash or another shell.  I think a good example of something like that would be: vitutor.

---

### Post by moriancumer_12 on 2007-05-11
That's a good idea. I've never heard of vitutor and it seems that the source site seems to be down for me to try it. ([ftp://ftp.mines.edu/pub/tutorials/](ftp://ftp.mines.edu/pub/tutorials/))

Since I haven't seen how an app like vitutor works, how easy would it be for a non-programmer like me to develop a similiar program for another application such as imagemagick. I plan to eventually have possibly hundreds of applications in tutorials. Will a program like vitutor work in demonstrating such programs like mplayer in the console. 

One reason I chose text files is so the enduser can easily make their own notes or other changes within the tutorial itself as to their needs. For example, they might want to add their home network set up with their gateway and various machines names and IP addresses, so they can easily reference it later if they need to set up their network up again.  

I guess I like the idea of having the tutorials rolled up in it's own OS is for three main reasons:

1) The tutorials will be specific to the OS. If the tutorial was separate from the OS, there might be slight differences between distros which may cause some confusion/frustration when trying to follow the tutorial. This guarantees that's the tutorials work exactly as described.

2) If someone walks through a tutorial on setting up procmail, fetchmail and mutt for their pop email account. When they are done with the tutorial they instantly have a properly set up configuration ready to go on the same system. Also, my tutorial on installing software won't apply to rpm and slackware based distros.

3) Consiistency: Everyone will be drawing from the same respositories (unless they mess with sources.list), using the same version of software, same kernel and same system configuration and filesystem layout.


Thanks, so much for your comments. I look forward to trying vitutor, I think it will give some good ideas. 

Are their anymore ideas/suggestions.

---

### Post by Zelut on 2007-11-10
I would agree that a tutorial-based package would make a lot more sense to me.  Much less to package and maintain, and also makes it more flexible so anyone can learn the command line by installing the package vs re-installing the machine to a teaching-based distro.

---

