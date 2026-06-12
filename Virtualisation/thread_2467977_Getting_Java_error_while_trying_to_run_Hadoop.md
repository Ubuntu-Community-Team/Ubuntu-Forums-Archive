---
title: "Getting Java error while trying to run Hadoop"
date: 2021-10-14
forum: Virtualisation
---

### Post by sir-gareth-of-orkney on 2021-10-14
Hello,

I'm trying to install Hadoop (3.2.1) on my Ubuntu VM and I've been following the instructions here: [How to Install Hadoop with Step by Step Configuration on Linux Ubuntu (guru99.com)]("https://www.guru99.com/how-to-install-hadoop.html")

I think I'm nearly finished, but when I try to run Hadoop with the command $HADOOP_HOME/sbin/start-dfs.sh, I get this error:

[IMG]https://i.imgur.com/f486Inx.jpg[/IMG]

I have verified that Java is installed and that the path is set through these commands:

[IMG]https://i.imgur.com/vjdM7dJ.jpg[/IMG]

I have set the path in /etc/profile:

[IMG]https://i.imgur.com/y2yo1Pm.jpg[/IMG]

I set the path in the ~/.bashrc file:

[IMG]https://i.imgur.com/RB8Ap0H.jpg[/IMG]

And I changed the JAVA_HOME variable in $HADOOP_HOME/etc/hadoop/hadoop-env.sh to this:

[IMG]https://i.imgur.com/AaplPIJ.jpg[/IMG]

I'm not sure what I'm doing wrong. :(

Any help would be greatly appreciated.

---

### Post by MAFoElffen on 2021-10-16
To see where things are on that machine, do like I have done on mine...
```

mafoelffen@ubuntu$ echo $JAVA_HOME
/usr/lib/jvm/default-java
mafoelffen@ubuntu$ which java
/usr/bin/java
mafoelffen@ubuntu$ ls /usr/lib/jvm/default-java
bin  conf  docs  include  jmods  legal  lib  man  release

```

Now I have multiple accounts set up on my machines for me to use with varied permissions, so I set mine up for all users (even though I am the sole user, which many accounts)... So I set it in /etc/profile :
```

export JAVA_HOME="/usr/lib/jvm/default-java" 
export PATH=$JAVA_HOME/bin:$PATH

```
I do it to "default-java", so that, if somewhere down the road, the version of java is changed or updated, then the pointers are still there, and I don't have to update the variable $JAVA_HOME...

---

