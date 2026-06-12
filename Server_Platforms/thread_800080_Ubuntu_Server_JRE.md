---
title: "Ubuntu Server JRE"
date: 2008-05-19
forum: Server Platforms
---

### Post by hwang251 on 2008-05-19
How do I know if the proper JRE is installed on Ubuntu Server? 

And if not, how do I install it?

---

### Post by cdenley on 2008-05-19
I'm not sure which JRE is "proper", but ubuntu desktop seems to come with java-6-openjdk.
```

sudo apt-get install openjdk-6-jre
sudo update-alternatives --config java
java -version

```

---

