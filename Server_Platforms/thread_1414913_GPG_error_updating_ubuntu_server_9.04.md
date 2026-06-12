---
title: "GPG error updating ubuntu server 9.04"
date: 2010-02-24
forum: Server Platforms
---

### Post by FranJPR on 2010-02-24
I receive the following error when running sudo aptitude update: 

Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security Release.gpg
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/multiverse Translation-en_US
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty Release.gpg
Ign [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty/main Translation-en_US
Ign [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty/restricted Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security Release
Ign [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty/universe Translation-en_US
Ign [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty/multiverse Translation-en_US
Get:1 [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty-updates Release.gpg [189B]
Ign [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty-updates/main Translation-en_US
Ign [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty-updates/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty-updates/universe Translation-en_US
Ign [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/main Packages
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty Release
Get:2 [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty-updates Release [57.9kB]
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/restricted Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/main Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/restricted Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/universe Packages
Err [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty-updates Release
 Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/universe Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/multiverse Sources
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty/main Packages
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty/restricted Packages
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty/main Sources
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty/restricted Sources
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty/universe Packages
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty/universe Sources
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty/multiverse Packages
Hit [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty/multiverse Sources
Fetched 190B in 9s (21B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
 W: You may want to run apt-get update to correct these problems

---

### Post by suseendran.rengabashyam on 2010-02-24
Hi,

Go to Applications > Accessories > Terminal, execute these commands:

```
wget http://archive.ubuntu.com/ubuntu/project/ubuntu-archive-keyring.gpg -O- | sudo apt-key add -

sudo apt-key update

sudo apt-key net-update
```

Now try running 'sudo aptitude update' and let me know if you get the same error.

---

### Post by FranJPR on 2010-02-24
After executing,
wget [http://archive.ubuntu.com/ubuntu/project/ubuntu-archive-keyring.gpg](http://archive.ubuntu.com/ubuntu/project/ubuntu-archive-keyring.gpg) -O- | sudo apt-key add -

and

sudo apt-key update
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed 
gpg: Total number processed: 2                                                              
gpg:              unchanged: 2

it seems nothing changed, then, trying the update, I get the same error.

---

### Post by wojox on 2010-02-24
Try:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 437D05B5
```

```
sudo gpg --export --armor 437D05B5 | sudo apt-key add
```

You may also have to try:

```

sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

```

---

### Post by FranJPR on 2010-02-24
Executing serv@server:/var/lib/apt$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 437D05B5, says,

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 437D05B5                                                                                                 
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com                                            
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" 11 new signatures           
gpg: no ultimately trusted keys found                                                                        
gpg: Total number processed: 1                                                                               
gpg:         new signatures: 11   

trying then it fails,

executing, sudo gpg --export --armor 437D05B5 | sudo apt-key add, gives:

serv@server:/var/lib/apt$ sudo gpg --export --armor 437D05B5 | sudo apt-key add                     
gpg: WARNING: unsafe ownership on configuration file `/home/serv/.gnupg/gpg.conf'                        
gpg: WARNING: nothing exported                                                                               
gpg: can't open `': No such file or directory

and it fails again,

executing the rest of the code gives the same error.

---

