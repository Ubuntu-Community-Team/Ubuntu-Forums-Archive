---
title: "environment vars"
date: 2011-03-22
forum: Server Platforms
---

### Post by m.dr on 2011-03-22
A question on Ubuntu's environment vars and where they are placed.

I installed default-jdk and ant.

When I do a java -help OR javac -help OR ant -help it returns the necessary command lists.

However when I do an echo $JAVA_HOME or echo $ANT_HOME it returns nothing!

My question is where are these vars stored. Eg When I download and install Eclipse (not from Ub repo) it seems to find the jdk perfectly and everything works! 

I know where JAVA_HOME is but I would like to know where it and other environment vars are stored.

Also I need to set up a stack of environment vars and I am trying to figure out where would be good place.

Would it be:
/etc/environment
/etc/profile
or a separate file under:
/etc/profile.d

I would prefer a separate file option so I can move it from machine to machine.

Anyway would appreciate your help with the ENV VARS as it is very elusive to me as far a Ubuntu is concerned.

I am used to them being in one place and not look for them in multiple places and would like to see how I can get them to one location - and more importantly where are they?

Thanks for your help!

---

### Post by Daedalus_357 on 2011-03-22
I had to manually set JAVA_HOME as the variable does not exist by default.

however i googled it and came across this:

[QUOTE=http://stackoverflow.com/questions/532155/linux-where-are-environment-variables-stored]   The kernel stores the list of environment  variables and their values for each process, and inherit them to child  processes. They exist at runtime, and are not stored in some file or so.  But there is a virtual file in 

     /proc/<pid>/environ

    Which contains all the environment variables. The kernel makes them  visible by that virtual file. One can list them. For example to view the  variables of process 3940, one can do

     cat /proc/3940/environ | tr '\0' '\n'

    Each variable is delimited by a binary zero from the next one. tr replaces the zero into a newline. 
 [/QUOTE]


if you want to have the variable set each time you boot up linux, i suggest adding it to your .bashrc

---

### Post by m.dr on 2011-03-22
Thanks for the reply. The pid info was very helpful.

I was thinking of adding them to /etc/profile. It seems to be read by all.

I tried /etc/environment but it seemed to be NOT read by processes.

Let's see if I get any more responses. I find it a little perturbing that I can't go to 1 file and put all env vars there.

Thanks again.

---

