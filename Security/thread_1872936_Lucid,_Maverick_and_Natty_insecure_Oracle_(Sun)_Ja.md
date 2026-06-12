---
title: "Lucid, Maverick and Natty: insecure Oracle (Sun) Java JRE in the Partner repo"
date: 2011-10-31
forum: Security
---

### Post by Pjotr123 on 2011-10-31
In Lucid, Maverick and Natty, there's still Oracle (Sun) Java JRE in the Partner repository. This is however 6u26, which is insecure. Only 6u29 is secure:
[http://www.oracle.com/technetwork/java/javase/6u29-relnotes-507960.html](http://www.oracle.com/technetwork/java/javase/6u29-relnotes-507960.html)

I've filed a bug report on Launchpad, and it seems no updates will ever come(!!): [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/884252](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/884252)
(see the replies by Sylvestre Ledru)

IMHO, this requires the following twofold urgent action:

1. A notification (popup from update manager?) to the current users, that they will have to take immediate action themselves. Namely removing 6u26 and either switching to OpenJDK or installing 6u29 by hand.

2. An immediate complete removal of 6u26 from the Partner repo's of Lucid, Maverick and Natty. In order to prevent further damage.

Please help support the bug report on Launchpad, if you are affected. Something must be done, and only the developers can do it.

Note: Oneiric is not involved: there's no Oracle Java in the Partner repo of Oneiric (never has been, either).

For good measure: you can use this how-to for installing Oracle Java 6u29 by hand: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by Paddy Landau on 2011-10-31
I have Natty and I do not have Sun's Java installed; it is OpenJDK. This is default, as I have not changed the Java since installing Natty.

So, I guess it affects 10.04 and 10.10.

---

### Post by Thewhistlingwind on 2011-10-31
BUMP.

This is pretty important.

---

### Post by Pjotr123 on 2011-11-01
@Paddy Landau: OpenJDK is default, but many people have discarded it in  favour of Oracle (Sun) Java JRE. Which is available in the Partner repo of Lucid, Maverick and Natty.

The strange thing is: I have booted into OpenSUSE 11.4 yesterday, and lo and behold, I received an update for Oracle (Sun) Java JRE. The secure 6u29.

Makes me wonder whether the license problem invoked by the Partner developer in the Launchpad thread, really *is* such a problem....

---

### Post by Paddy Landau on 2011-11-01
> **Pjotr123 said:**
> Makes me wonder whether the license problem invoked by the Partner developer in the Launchpad thread, really *is* such a problem....
Yes, it does sound a bit odd, seeing as you can download and install it yourself. I don't suppose that Oracle provides its own PPA for Java?

---

### Post by Pjotr123 on 2011-11-01
> **Paddy Landau said:**
> Yes, it does sound a bit odd, seeing as you can download and install it yourself. I don't suppose that Oracle provides its own PPA for Java?

Unfortunately not. 

The license issue *could* be solved easily anyway, by adopting the same procedure as with Adobe Flash Player: a package with script that downloads Java from the upstream's page and installs it.

This would solve the dangerous insecurity that users of Lucid, Maverick and Natty are facing now (while being unaware of it!). Plus it would offer the choice to Oneiric users and beyond, to install Oracle Java JRE *if they choose to*. And sometimes, they are even forced to, because unfortunately OpenJDK doesn't *always* perform as well as Oracle Java.

But it appears that there are ideological barriers to that. See answer # 2 on this blog page:
[http://sylvestre.ledru.info/blog/sylvestre/2011/08/26/sun_java6_packages_removed_from_debian_u](http://sylvestre.ledru.info/blog/sylvestre/2011/08/26/sun_java6_packages_removed_from_debian_u)

And answer # 5 on this blog page:
[http://sylvestre.ledru.info/blog/sylvestre/2011/10/25/removal_of_sun_java6_from_debian](http://sylvestre.ledru.info/blog/sylvestre/2011/10/25/removal_of_sun_java6_from_debian)

Most regrettable.

---

### Post by Pjotr123 on 2011-11-03
I ask for help.

I've done all I could, to bring this grave security risk to the attention of the developers. But their response has been unsatisfactory, to say the least....
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/884252](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/884252)

Who can help me, to push this very important matter to higher levels of authority? Who has access to somebody in charge? Or you can help me beat the drums, wherever you can....

The best solution would be, if the devs would cease to be ideological about this (sigh...), and offer a secure update for Oracle Java. E.g. by means of a Flash Player-like install script, which is still allowed by the license.

However, if not: 
- the current insecure Oracle Java should be pulled immediately from the partner repo's of Lucid, Maverick and Natty;
- all current users of Oracle Java should get an urgent warning to remove it at once. E.g. by a special popup from Update Manager.

Everything less would be highly irresponsible. Unbelievably so, even.

---

### Post by Paddy Landau on 2011-11-03
I read the security notes, and unfortunately they were too technical for me to understand.

What exactly is the security risk?

---

### Post by Pjotr123 on 2011-11-03
@Paddy Landau:
[http://www.zdnet.com/blog/security/java-update-plugs-20-critical-security-holes/9670](http://www.zdnet.com/blog/security/java-update-plugs-20-critical-security-holes/9670)

This is pretty important....

---

### Post by cariboo on 2011-11-03
@Pjotr123, shouldn't you be talking to the maintainer of the package, instead of some random Debian developer?

If you go here:

[http://packages.ubuntu.com/natty/java-common](http://packages.ubuntu.com/natty/java-common)

you'll see a list of the maintainers on the right side of the page.

---

### Post by Pjotr123 on 2011-11-03
@cariboo907: ordinarily, that would be a promising approach... However, since Oracle Java is in the Partner repo, I'm afraid things are a bit different on the accountability side.

The guys you mention are (most probably) only responsible for the default Java, namely OpenJDK. The Partners are the ones responsible for what's in the Partner repo.

Nevertheless, you made me think.... I may have more luck trying to contact the members of the Ubuntu Security Team directly: [https://launchpad.net/~ubuntu-security/+members#active](https://launchpad.net/~ubuntu-security/+members#active)

I'll see what I can do. And I'll report back here.

---

