---
title: "sudo apt-get install sun-java5-bin"
date: 2006-06-23
forum: Sun Sparc Users
---

### Post by fosinet on 2006-06-23
Hi to all,
I installed the newer  UBUNTU server release 6.0.6 LTS on a SUN Solaris Ultra 60
    2 CPU - 2 Gbyte of RAM
It looks to work great!

Now I want to install the JAVA-JRE virtual machine, because I need ti run some JAVA applications on this "old" machine.
I tried to follow the instructions reported in the link:

    [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

But when I try to execute the command:
   
    sudo apt-get install sun-java5-bin

I always face this output message:

 Reading package lists... Done
    Building dependency tree... Done
    Some packages could not be installed. This may mean that you have
    requested an impossible situation or if you are using the unstable
    distribution that some required packages have not yet been created
    or been moved out of Incoming.

    Since you only requested a single operation it is extremely likely that
    the package is simply not installable and a bug report against
    that package should be filed.
    The following information may help to resolve the situation:

    The following packages have unmet dependencies:
     sun-java5-jre: Depends: sun-java5-bin (= 1.5.0-06-1) but it is not installable or
                          ia32-sun-java5-bin (= 1.5.0-06-1) but it is not installable
 E: Broken packages

Many thanks in advance for any help.

fosinet

---

### Post by joshuapurcell on 2006-06-25
[QUOTE=fosinet]The following packages have unmet dependencies:
     sun-java5-jre: Depends: sun-java5-bin (= 1.5.0-06-1) but it is not installable or
                          ia32-sun-java5-bin (= 1.5.0-06-1) but it is not installable
 E: Broken packages[/QUOTE]Find out what happens when you give this command:

**sudo apt-get install sun-java5-jre**

This may give you more information on what the problem is.

---

### Post by fosinet on 2006-06-26
[QUOTE=joshuapurcell]Find out what happens when you give this command:

**sudo apt-get install sun-java5-jre**

This may give you more information on what the problem is.[/QUOTE]


Unfortunatly I face the same error messages:

folcir@ik2ws203:~$ sudo apt-get install sun-java5-jre
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java5-jre: Depends: sun-java5-bin (= 1.5.0-06-1) but it is not installable or
                          ia32-sun-java5-bin (= 1.5.0-06-1) but it is not installable
E: Broken packages

---

### Post by matoxxx on 2006-06-26
Try installing java from binary package, there is a good howto on wiki.

---

### Post by fosinet on 2006-06-27
[QUOTE=matoxxx]Try installing java from binary package, there is a good howto on wiki.[/QUOTE]

Sorry, but sun-java5-bin is a binary package!
What do you mean ???????:confused:

---

### Post by opensrcrocks on 2006-06-28
[FONT="Georgia"][FONT="Georgia"][COLOR="Blue"]Well, not to state the obvious, but a quick visit to java.sun.com will tell us that there is no package available for Ubuntu Sparc Linux yet. So, unless :-k you are trying to install a x86 version or Solaris Sparc version under this distro, you might have to wait a bit.
-GGR[/COLOR][/FONT][/FONT]

---

### Post by allnameswereout on 2006-06-29
There is no and has never been a Sun JRE/JDK port for Linux/SPARC (nor Ubuntu/SPARC). However, now that Sun has less strict license for Sun JRE/JDK and now that Sun supports Ubuntu/SPARC such port is more likely to exist.

In other words do not confuse
Linux/AMD64
with
Solaris/SPARC64

Sun only support JRE/JDK on Linux and the x86 and AMD64 architectures.

Hence, for now, you'll have to use one of the open source alternatives *or* *or* use a different platform (e.g. Solaris/SPARC64) *or* you need to have patience *or*, if you insist, contact the Ubuntu/SPARC or Sun JRE/JDK guys.

---

### Post by fosinet on 2006-06-30
[QUOTE=allnameswereout]There is no and has never been a Sun JRE/JDK port for Linux/SPARC (nor Ubuntu/SPARC).[/QUOTE]

This is wrong !!!!!
Do you know GENTOO distribution?
Have a look to this link: [http://packages.gentoo.org/search/?sstring=blackdown](http://packages.gentoo.org/search/?sstring=blackdown)

The blackdown package is the Java version for LINUX / SUN SOLARIS.
I hoped to find it also for UBUNTU !

 [QUOTE=However, now that Sun has less strict license for Sun JRE/JDK and now that Sun supports Ubuntu/SPARC such port is more likely to exist.

In other words do not confuse
Linux/AMD64
with
Solaris/SPARC64

Sun only support JRE/JDK on Linux and the x86 and AMD64 architectures.

Hence, for now, you'll have to use one of the open source alternatives *or* *or* use a different platform (e.g. Solaris/SPARC64) *or* you need to have patience *or*, if you insist, contact the Ubuntu/SPARC or Sun JRE/JDK guys.[/QUOTE]

Great idea, can you tell me how to open this kind of request ?

Best Regards

---

### Post by netztier on 2006-06-30
[QUOTE=fosinet]This is wrong !!!!!
Do you know GENTOO distribution?
Have a look to this link: [http://packages.gentoo.org/search/?sstring=blackdown](http://packages.gentoo.org/search/?sstring=blackdown)
[/QUOTE]

Sorry you're wrong. 

There is **NO** [COLOR="DarkOrchid"]**SUN Java**[/COLOR] version for Linux/SPARC. That's what allnameswereout statet, and that is what your first post asked about. The package sun-java5-bin would be such a version of SUN's Java.

*Blackdown Java* however is another story, mainly in *not *being SUN Java, and you are right, there might be such a thing around as Blackdown Java for Linux/SPARC - I just can't verify at this time.

regards

Marc

---

### Post by fosinet on 2006-06-30
[QUOTE=netztier]Sorry you're wrong. 

There is **NO** [COLOR="DarkOrchid"]**SUN Java**[/COLOR] version for Linux/SPARC. That's what allnameswereout statet, and that is what your first post asked about. The package sun-java5-bin would be such a version of SUN's Java.

*Blackdown Java* however is another story, mainly in *not *being SUN Java, and you are right, there might be such a thing around as Blackdown Java for Linux/SPARC - I just can't verify at this time.

regards

Marc[/QUOTE]



Yes you are right. Sorry for my mistake to **allnameswereout**!
In this topic we are discussing about SUN Java.

B.R.

---

### Post by allnameswereout on 2006-06-30
NP.

You're correct when you state that there may be non-open source Java implementations available for Linux/SPARC.

I frankly, due to the differences and incomplete features, find using a non-recent, non-Sun Java implenentation all too confusing and not worth the hassle. YMMV. It really depends on what your needs are. You may be able to get the Gentoo/SPARC Blackdown package working on Ubuntu/SPARC.

As for your last question: I do not know which Sun guys are involved with Ubuntu or wether there are Sun guys involved at all or wether Sun merely endorses the Ubuntu/SPARC initiative. I suggest you search the Ubuntu/SPARC mailinglist to see if theres work done on a Sun Java port and if not, ask for such initiative or ask which Sun people to contact -- but be courteous (since may be a lot of work to port, non-profit probably).

---

