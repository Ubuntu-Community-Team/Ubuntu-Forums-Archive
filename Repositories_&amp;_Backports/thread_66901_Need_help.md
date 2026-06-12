---
title: "Need help"
date: 2005-09-18
forum: Repositories &amp; Backports
---

### Post by sterilegenie on 2005-09-18
Since ubuntuguide.org cannot be reached for some strange reason, i need to know how to edit my source list to get all of the goodies. Please help

---

### Post by Marinmo on 2005-09-19
[QUOTE=sterilegenie]Since ubuntuguide.org cannot be reached for some strange reason, i need to know how to edit my source list to get all of the goodies. Please help[/QUOTE]
 sudo vim /etc/apt/sources.list
(I assume that you already know where to find those "goodies" because I don't. :))

---

### Post by Xian on 2005-09-19
[QUOTE=sterilegenie]Since ubuntuguide.org cannot be reached for some strange reason, i need to know how to edit my source list to get all of the goodies. Please help[/QUOTE]
It works on my browser: [Ubuntu Guide](http://ubuntuguide.org/).

This is the entry you are looking for:

1. Read General Notes

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```

2. Find this section 

```
...
## Uncomment the following two lines to fetch updated software from the network
# deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu hoary universe
# deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

# deb http://security.ubuntu.com/ubuntu hoary-security main restricted
# deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe
```
3 .Replace with the following lines 

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

4. Save the edited file (sample)

```
sudo apt-get update
```

---

### Post by sterilegenie on 2005-09-20
Im not sure what was going on  but Today I can reach the URL and I have the correct repositories now. Everything is working as expected! Man I love Ubuntu!!!!!!!!

---

