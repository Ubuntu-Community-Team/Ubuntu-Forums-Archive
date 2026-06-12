---
title: "problem with  environment variable"
date: 2018-03-31
forum: Server Platforms
---

### Post by penapisemnet on 2018-03-31
Hello!
I am beginer and i learn ubuntu server
i need to set JAVA_HOME variable  for this i want to find  out the path to java
however when i perform the command 

wish java
i get message 

application-specific initialization failed: no display name and no $DISPLAY environment variable
Error in startup script: couldn't read file "java": no such file or directory

i know exactly that jdk8 was installed - i did it 

the second problem- i installed buckminster but when i lounch it 
without full path it message no such file or directory

i ask for you help to correct this problem

Thank you in advance

---

### Post by steeldriver on 2018-03-31
`wish` is a graphical shell for Tcl/Tk - I suspect the command you really want is

```

which java

```

---

### Post by penapisemnet on 2018-03-31
# wish java


answer

application-specific initialization failed: no display name and no $DISPLAY environment variable
Error in startup script: couldn't read file "java": no such file or directory

---

### Post by SeijiSensei on 2018-03-31
I take it you didn't read the answer above this post.  You need to use the "**which**" command, not "wish."  Or use "locate".

---

### Post by deadflowr on 2018-03-31
*Thread moved to **Server Platforms***

---

### Post by penapisemnet on 2018-03-31
Thank You  It is my mistake. Sorry, English is not my native language, and it is difficult to me.

I corrected this command and got /usr/bin/java

---

### Post by SeijiSensei on 2018-03-31
Hardly any commands in *nix are capitalized, and capitalization matters.  You need to use "export" not "EXPORT".

Also, you don't need to change the PATH.  "/usr/bin" is already in your default path.  

Oh, and "java_home" is not the same as "JAVA_HOME".  

So all that's needed is

```

JAVA_HOME=/usr/bin/java
export JAVA_HOME

```

If you want to make these definitions apply for all users, put them at the end of /etc/profile, not /root/.bashrc.

---

### Post by TheFu on 2018-03-31
JAVA_HOME isn't set to the location of the program.  It is set to the location of the full Java installation.  So, if java is installed in /opt/jdk2/bin/java, then JAVA_HOME would be /opt/jdk2.  There are usually bin/, lib/, docs/, share/ subdirectories to JAVA_HOME.

To set the environment variable, I would do it this way:
```
export JAVA_HOME=/opt/jdk2
```
I'd add that to the bottom of my ~/.bashrc file.  It will work for bash. Other shells will use different files and non-ksh-based shells will have different commands, like setenv for csh/tcsh.

Of course, you have to find the location where the full JDK is installed.   Google is often helpful.  [https://askubuntu.com/questions/175514/how-to-set-java-home-for-java](https://askubuntu.com/questions/175514/how-to-set-java-home-for-java)  Looks like **update-alternatives --config java** shows where it is really installed.  /usr/lib/jvm/java-8-openjdk-i386/jre is the "JAVA_HOME" for my system, based on that output.

---

### Post by penapisemnet on 2018-03-31
Thank you! Your help is a very valuable for me.

---

