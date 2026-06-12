---
title: "Java security issue"
date: 2013-04-23
forum: Security
---

### Post by jsvidyad on 2013-04-23
Hello,

  I guess many of you guys had heard about the java security issues that came up during the middle of January 2013. Did that affect just java 7? Or did those issues affect java 6 too? I think I had java 6 on my computer. The command 'java -version' on my system gave the output(at that time):
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) Server VM (build 20.1-b02, mixed mode)

Does that mean I had java 6 on my system? Did those security issues affect java 6 too? Do you think there is any reason for me to worry? 

  When I became aware of those security issues, I ran the command:
sudo apt-get purge sun-java6-jre sun-java6-plugin

Would the above command have removed the plugin with security issues mentioned in those news reports about java security issues?

---

### Post by Lfekey2 on 2013-04-23
You already remove the java package, no need to worry about java security anymore.

---

### Post by jsvidyad on 2013-04-26
> **Lfekey2 said:**
> You already remove the java package, no need to worry about java security anymore.

I'm just worried about the possibility of some security breach before I removed Java. That's why I asked whether the security issues affected only java7 or did it affect java 6 too. I gave the output of 'java -version' command in my first post. I think the output of that means I had java 6 earlier. Is that right?

Also, is the icedtea java more secure?

Also, I purged the packages sun-java6-jre and  sun-java6-plugin from my system. Is this enough to remove the package with the security vulnerabilities mentioned in the news reports?

---

### Post by slickymaster on 2013-04-26
See this:
[USN-1755-2: OpenJDK 7 vulnerabilities]("http://www.ubuntu.com/usn/usn-1755-2/")
[What do I need to know about this Java issue everyone's talking about?]("http://ubuntuforums.org/showthread.php?t=2105734")

---

