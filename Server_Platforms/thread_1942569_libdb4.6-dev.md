---
title: "libdb4.6-dev"
date: 2012-03-17
forum: Server Platforms
---

### Post by Nezmin2 on 2012-03-17
Hey guy's,
I am trying to build a ubuntu server using the latest ubuntu server download.

The guide I am using instructed me to install libdb4.6-dev. The issue is that I am receiving a "no installation candidate" error.

Can someone tell me what the problem is or what source list that I can install for 11.10 that will allow me to install it?

Thanks...

---

### Post by Nezmin2 on 2012-03-18
Anyone???:confused:

---

### Post by Holdolin on 2012-03-18
What is it you're trying to do?  That looks to be a database package (or a dependancy of such) but databases have many uses.  What guide are you following?  In short, the more infomation you give us, the better we can help you :)

---

### Post by Nezmin2 on 2012-03-19
> **Holdolin said:**
> What is it you're trying to do?  That looks to be a database package (or a dependancy of such) but databases have many uses.  What guide are you following?  In short, the more infomation you give us, the better we can help you :)

The guide is located here: [http://www.howtoforge.com/perfect-server-ubuntu-natty-narwhal-ubuntu-11.04-ispconfig-2](http://www.howtoforge.com/perfect-server-ubuntu-natty-narwhal-ubuntu-11.04-ispconfig-2)

The Particular section is #11.

Thanks...

---

### Post by Nezmin2 on 2012-03-19
Anybody???](*,)

---

### Post by Nezmin2 on 2012-03-20
Hasn't anyone come across this before? :confused:

How about a way to download it using wget from a cmd line?

---

### Post by RyanRahl on 2012-03-20
here ya go:

[http://www.ubuntuupdates.org/package/core/natty/universe/base/libdb4.6-dev](http://www.ubuntuupdates.org/package/core/natty/universe/base/libdb4.6-dev)

download here

for 32 bit system:

```
wget http://security.ubuntu.com/ubuntu/pool/universe/d/db4.6/libdb4.6-dev_4.6.21-17_i386.deb
```

for 64 bit system

```
wget http://security.ubuntu.com/ubuntu/pool/universe/d/db4.6/libdb4.6-dev_4.6.21-17_amd64.deb
```

---

### Post by Nezmin2 on 2012-03-20
> **RyanRahl said:**
> here ya go:

[http://www.ubuntuupdates.org/package/core/natty/universe/base/libdb4.6-dev](http://www.ubuntuupdates.org/package/core/natty/universe/base/libdb4.6-dev)

download here

for 32 bit system:

```
wget http://security.ubuntu.com/ubuntu/pool/universe/d/db4.6/libdb4.6-dev_4.6.21-17_i386.deb
```

for 64 bit system

```
wget http://security.ubuntu.com/ubuntu/pool/universe/d/db4.6/libdb4.6-dev_4.6.21-17_amd64.deb
```


Thanks Ryan, this worked great except for when I install the deb I receive a lib4.6 required dependency and yet I cannot install this either. Thoughts?

---

### Post by RyanRahl on 2012-03-21
You probably find all of the files you need on the same site I linked but before you go any further I suggest finding out why the tutorial is asking for those packages. If they are no longer present in the latest server version of Ubuntu (11.10) they have likely been replaced by something else for one reason or another since the version in the tutorial (11.04). If you want to build a server like the one described in the tutorial (meant for and ISP type of configuration) I suggest going through the first section and learn about each of the server software packages mentioned in the list (apache, postfix, bind, etc) individually and configure them with the documentation either directly from the home pages of the projects themselves or from the online Ubuntu documentation itself. And even before that I would suggest that you simply ask yourself what you want your server to do and then just go from there. Or you could always install Ubuntu 11.04 and do the tutorial you linked that way, just make sure the "Universe" repository is enabled because that is where most of those packages come from. I would use Ubuntu 11.04 anyway because it is LTS, all the servers I run only get upgraded to LTS versions.

---

### Post by Nezmin2 on 2012-03-21
> **RyanRahl said:**
> I would use Ubuntu 11.04 anyway because it is LTS, all the servers I run only get upgraded to LTS versions.

Hey Ryan, what is a LTS version? I have never heard this acronym before.

---

### Post by RyanRahl on 2012-03-21
Long term support.

---

### Post by Nezmin2 on 2012-03-21
> **Nezmin2 said:**
> Hey Ryan, what is a LTS version? I have never heard this acronym before.

Thanks Ryan...

I originally was setting up this server to host my company website, run my company email (Zimbra), and my company CRM app (SugarCRM). But I have never set up a linux server before and found the HowTo very interesting...

Thanks...I now have everything set up except for the ISPConfig 2 part.

---

### Post by azmyth on 2012-03-21
Don't know if it will work but there's a newer version called libdb4.7-dev. Installing older revs can get tricky as it can bork your system.

---

### Post by raja.genupula on 2012-03-21
> **RyanRahl said:**
> Long term support.

for more info 
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by Nezmin2 on 2012-03-21
> **azmyth said:**
> Don't know if it will work but there's a newer version called libdb4.7-dev. Installing older revs can get tricky as it can bork your system.

I looked into that file and it appears to be different. The file name actually goes a up to 5.1, but there appears to be differences in the files. So, I used wget and downloaded the file and installed it that way and it worked great. Of course I also had to download the libdb4.6 file first. My hope is that if there is a update, then running the apt-get update process should update what is necessary...

---

### Post by Nezmin2 on 2012-03-21
> **raja.genupula said:**
> for more info 
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Thanks Ryan...This is much appreciated.

---

