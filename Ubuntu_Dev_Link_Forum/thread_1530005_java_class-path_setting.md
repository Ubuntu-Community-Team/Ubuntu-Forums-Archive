---
title: "java class-path setting"
date: 2010-07-13
forum: Ubuntu Dev Link Forum
---

### Post by aowlad on 2010-07-13
I am new in ubuntu. I am facing this problem below.
Error: JAVA_HOME is not defined correctly.
  We cannot execute /usr/local/jdk/bin/java
THERE are problem in JAVA_HOME class path.how can I solve it?

please help me

---

### Post by lkjoel on 2010-07-18
> **aowlad said:**
> I am new in ubuntu. I am facing this problem below.
Error: JAVA_HOME is not defined correctly.
  We cannot execute /usr/local/jdk/bin/java
THERE are problem in JAVA_HOME class path.how can I solve it?

please help me
Could you show the output of this command for me?
And it would be helpful to use code tags when you display the results.
```
cat ~/.bashrc
```

---

### Post by Rushyang on 2010-08-10
I'm not sure but you export that java dir path into your env variables through terminal. 

> export PATH="$PATH:usr/local/jdk/bin/java"

may that will help you to compile your progs through javac command and execute them.

---

### Post by KdotJ on 2010-08-10
You will need to add the java jdk path to your PATH by adding it to your .bashrc file (or .bash_profile). I'm pretty sure the command given in the post above will work too.

However, how did you install your jdk? If you installed the openJDK via the terminal (or synaptic) it will update the PATH for you.

```
sudo apt-get install openjdk-6-jdk
```

---

