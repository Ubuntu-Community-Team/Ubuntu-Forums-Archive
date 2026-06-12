---
title: "php5-cli: Depends: php5-common (=5.2.4-2ubuntu5) but 5.2.4-2ubuntu5.1 is to be instal"
date: 2009-08-10
forum: Server Platforms
---

### Post by jonny.milano on 2009-08-10
So I have searched the forums, googled around but still have not found what I'm looking for.. (hmm.. sounds like that REM (or is it U2) song))

Anyways, this issue stems from me trying to install Torrentflux-b4rt. I have got almost everything working but have a "red light". The feild that wants me to enter the path to my PHP binary doesn't like /usr/bin/php. I searched and found that this may be because I don't have the php5-cli package installed. OK, so I go to install that and get: ```
 php5-cli: Depends: php5-common (=5.2.4-2ubuntu5) but 5.2.4-2ubuntu5.1 is to be installed 
``` 

Is there a way to roll PHP back to php5-common (=5.2.4-2ubuntu5) without breaking anything or install the command line package without breaking anything?

Thanks all. I promise that when I actually know what I am doing, I will contribute back to the Ubuntu Formus.

---

### Post by cdenley on 2009-08-10
```

sudo apt-get update
sudo apt-get install php5-cli

```

---

### Post by jonny.milano on 2009-08-10
no dice.... 

```

herb@herb:~$ sudo apt-get update
[sudo] password for herb: 
Hit http://archive.ubuntu.com hardy Release.gpg
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Hit http://archive.canonical.com hardy Release 
Hit http://archive.ubuntu.com hardy Release    
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US  
Hit http://us.archive.ubuntu.com hardy Release                       
Hit http://archive.canonical.com hardy/partner Packages              
Hit http://archive.ubuntu.com hardy/restricted Sources               
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Reading package lists... Done
herb@herb:~$ sudo apt-get install php5-cli
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-cli: Depends: php5-common (= 5.2.4-2ubuntu5) but 5.2.4-2ubuntu5.1 is to be installed
E: Broken packages
herb@herb:~$ 

```

thanks for the help though!

---

### Post by cdenley on 2009-08-11
Maybe...
```

sudo apt-get update
sudo apt-get install php5 php5-common php5-cli

```

If that doesn't work, you can just upgrade everything to ensure you have the right version of php5 to match the most current version of php5-cli.
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install php5-cli

```

---

### Post by jonny.milano on 2009-08-11
Thank you again for the reply. I'm quite sure that I have php5 as I have php web pages served up correctly on the machine. I installed it when I installed the OS. I will try your first idea tonight. However, re your second idea: won't "sudo apt-get upgrade" change my version of Ubuntu? I have 8.04 LTS and would like to stay there. Or, does sudo apt-get upgrade just update packages installed in 8.04? Will this break anything? I have had problems in the past when I change versions and update packages things break. I have this web server in place and I really am nervous about updating it. 

Again, thank you for your help!

---

### Post by cdenley on 2009-08-11
> **jonny.milano said:**
> Thank you again for the reply. I'm quite sure that I have php5 as I have php web pages served up correctly on the machine. I installed it when I installed the OS. I will try your first idea tonight. However, re your second idea: won't "sudo apt-get upgrade" change my version of Ubuntu? I have 8.04 LTS and would like to stay there. Or, does sudo apt-get upgrade just update packages installed in 8.04? Will this break anything? I have had problems in the past when I change versions and update packages things break. I have this web server in place and I really am nervous about updating it. 

Again, thank you for your help!

I never said you didn't have php installed. You clearly do not have the most current version available from the repos (5.2.4-2ubuntu5.6), which is why you have a dependency problem. The php5-cli package depends on php5-common with the same version. You should also upgrade your packages since there are known problems with the version you are using.
[http://www.ubuntu.com/usn/USN-761-1](http://www.ubuntu.com/usn/USN-761-1)
[http://www.ubuntu.com/usn/USN-720-1](http://www.ubuntu.com/usn/USN-720-1)
[http://www.ubuntu.com/usn/usn-628-1](http://www.ubuntu.com/usn/usn-628-1)

Also, the command I posted does not upgrade your ubuntu release, it only upgrades all packages to the most recent version available in the repos for your ubuntu release.

---

### Post by jonny.milano on 2009-08-12
Hey! :P That did the trick! Sorry I was so chicken to update. I've just had it give me headaches in the past (broken packages/dependecies). Thank you for all of the help. Now my Torrentflux install is happy! I LOVE UBUNTU!! and you cdenley!!!!!

---

