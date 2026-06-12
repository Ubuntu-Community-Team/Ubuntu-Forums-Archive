---
title: "How To Update Transmission To Latest Version"
date: 2012-07-28
forum: Server Platforms
---

### Post by sharif_aly on 2012-07-28
How To Update Transmission To Latest Version ?

My /etc/apt/sources.list 

```

deb http://archive.ubuntu.com/ubuntu precise main restricted universe
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted universe
deb http://security.ubuntu.com/ubuntu precise-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu precise partner

```

My current version of Ubuntu is** Ubuntu 12.04 64 Bit**

---

### Post by BkkBonanza on 2012-07-28
The version in the universe (precise) repo appears to be 2.51. If you want a newer version than that then you can add the Transmission PPA repository and you should be able to get the 2.60 build.

See this page,
[https://launchpad.net/~transmissionbt/+archive/ppa](https://launchpad.net/~transmissionbt/+archive/ppa)

sudo add-apt-repository ppa:transmissionbt/ppa

then the normal,

sudo apt-get update
sudo apt-get upgrade

should show an update you can confirm.

---

### Post by andrew.46 on 2012-07-30
An alternative can be found on the Ubuntu Community Wiki:

CompilingTransmission
[https://help.ubuntu.com/community/CompilingTransmission](https://help.ubuntu.com/community/CompilingTransmission)

Just another way of doing it :).

---

### Post by sharif_aly on 2012-09-14
**> sudo: add-apt-repository: command not found???**

This happen to me when try to add 

Like [BkkBonanza]("http://ubuntuforums.org/member.php?u=550406") said :
> See this page,
[https://launchpad.net/~transmissionbt/+archive/ppa]("https://launchpad.net/%7Etransmissionbt/+archive/ppa")

```
sudo add-apt-repository ppa:transmissionbt/ppa
```

then the normal,
```

apt-get update && apt-get upgrade

```
should show an update you can confirm.


and I fix the add-apt-repository command:

```
sudo apt-get install python-software-properties
```

Also,  I don't think it is usual, in Ubuntu, for people to install software  using this command.  here are two commands I use most in the terminal.   The first lists available packages and the second installs them.  For  instance:

```

sudo apt-cache search java
sudo apt-get install openjdk-6-jre

```

---

### Post by sharif_aly on 2012-10-20
If you do not have install transmission then 
> sudo apt-get install transmission && sudo apt-get install transmission-cli transmission-common transmission-daemon



> killall -HUP transmission-daemon


OK now let's edit the settings (to your liking) and don't forget to save (CTRL+X Y)

> cd ~
nano .config/transmission-daemon/settings.json



And  finally re-run transmission-daemon. It only needs to be run once and  then you can access the web interface on the port you setup.

> transmission-daemon


---

