---
title: "Installing SUN JAVA"
date: 2012-06-10
forum: Server Platforms
---

### Post by brent1975 on 2012-06-10
I am testing out Server 12.04 and have over come some of the changes from 10.04 to the current releases. I have been doing some searching on how to install java on the server. 

before I would just add the ppa 
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
and run
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre unzipThis clearly does not work with 12.04. and I have been all over google trying to figure out how to get this installed. alot of folks seem to be having an issue with this. 



Anyone have any good notes they wouldn't mind sharing?

---

### Post by Cheesemill on 2012-06-10
If you mean Oracle Java then just use the WebUpd8 team PPA. Oracle Java has been removed from the partner repository due to licensing issues.
```

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by brent1975 on 2012-06-10
> **Cheesemill said:**
> If you mean Oracle Java then just use the WebUpd8 team PPA. Oracle Java has been removed from the partner repository due to licensing issues.
```

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

For some reason when I try and run "sudo add-apt-repository ppa:webupd8team/java" I get an error

"sudo: add-apt-repository: command not found"

---

### Post by steeldriver on 2012-06-10
I haven't tried the ppa but I installed both 6 and 7 a couple of days ago using oab

[https://github.com/flexiondotorg/oab-java6](https://github.com/flexiondotorg/oab-java6) 

(downloadable packaging script + step by step instructions)

Basically it creates a local package repository and builds the deb and everything else you need locally - after that you can install via apt-get etc.

Worked flawlessly for me

---

### Post by Cheesemill on 2012-06-10
> **brent1975 said:**
> For some reason when I try and run "sudo add-apt-repository ppa:webupd8team/java" I get an error

"sudo: add-apt-repository: command not found"

I'm not sure if it is installed by default on a Server installation, you may need to install the package [python-software-properties]("apt://python-software-properties") first.

---

### Post by brent1975 on 2012-06-10
> **Cheesemill said:**
> I'm not sure if it is installed by default on a Server installation, you may need to install the package [python-software-properties]("apt://python-software-properties") first.

Yup that was the issue. Interesting I never had to install that on 10.04

Thanks for the information. It's installing now as I am typing.

---

