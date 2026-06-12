---
title: "how do you enable proposed repositories under noble dev?"
date: 2024-03-17
forum: Ubuntu Development Version
---

### Post by Claus7 on 2024-03-17
Hello,

during noble development I have seen that many answers/solutions are found under proposed repositories. In order to enable them under any distribution, I was going to: synaptic->settings->repositories->developer options->pre-released updates *distribution*-proposed.

I'm doing the same thing, yet no different/new package under proposed is found. In order to install a proposed package I have to issue a command:
sudo apt install *package-name* -t *distribution*-proposed

Is there any other way to do so? Sometimes the package name is not exactly known. Is this a new way or synaptic somehow is broken?

Regards!

---

### Post by #&amp;thj^% on 2024-03-17
It is much safer using "sudo apt install package-name -t distribution-proposed"

I show all in synaptic, but have a look in:
```
cd /etc/apt/sources.list.d && less proposed-repositories.list

```
Mine reads as:
```
deb http://archive.ubuntu.com/ubuntu/ noble-proposed restricted main multiverse universe

```
The full source list on mine:
```
inxi -r
Repos:
  Active apt repos in: /etc/apt/sources.list
    1: deb http://us.archive.ubuntu.com/ubuntu/ noble main restricted
    2: deb http://us.archive.ubuntu.com/ubuntu/ noble-updates main restricted
    3: deb http://us.archive.ubuntu.com/ubuntu/ noble universe
    4: deb http://us.archive.ubuntu.com/ubuntu/ noble-updates universe
    5: deb http://us.archive.ubuntu.com/ubuntu/ noble multiverse
    6: deb http://us.archive.ubuntu.com/ubuntu/ noble-updates multiverse
    7: deb http://us.archive.ubuntu.com/ubuntu/ noble-backports main restricted universe multiverse
    8: deb http://security.ubuntu.com/ubuntu noble-security main restricted
    9: deb http://security.ubuntu.com/ubuntu noble-security universe
    10: deb http://security.ubuntu.com/ubuntu noble-security multiverse
  Active apt repos in: /etc/apt/sources.list.d/archive_uri-https_download_sublimetext_com_-noble.list
    1: deb https://download.sublimetext.com/ apt/stable/
  Active apt repos in: /etc/apt/sources.list.d/mozilla.list
    1: deb [signed-by=/etc/apt/keyrings/packages.mozilla.org.asc] https://packages.mozilla.org/apt mozilla main
  Active apt repos in: /etc/apt/sources.list.d/proposed-repositories.list
    1: deb http://archive.ubuntu.com/ubuntu/ noble-proposed restricted main multiverse universe
  Active apt repos in: /etc/apt/sources.list.d/protonvpn-stable.list
    1: deb [arch="all", signed-by=/usr/share/keyrings/protonvpn-stable-archive-keyring.gpg] https://repo.protonvpn.com/debian stable main
  Active apt repos in: /etc/apt/sources.list.d/surfshark.list
    1: deb https://ocean.surfshark.com/debian stretch main
  Active apt repos in: /etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-noble.sources
    1: deb https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/ noble main
  Active apt repos in: /etc/apt/sources.list.d/ubuntu-uefi-team-ubuntu-build-noble.sources
    1: deb https://ppa.launchpadcontent.net/ubuntu-uefi-team/build/ubuntu/ noble main
  Active apt repos in: /etc/apt/sources.list.d/ubuntuhandbook1-ubuntu-conkymanager2-noble.sources
    1: deb https://ppa.launchpadcontent.net/ubuntuhandbook1/conkymanager2/ubuntu/ jammy main

```

You can try to use:
```
software-properties-gtk
```
But there is a bug on that found here:[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2053228](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2053228)

Dang i keep forgetting this method as well:
```
# cat <<EOF >/etc/apt/sources.list.d/ubuntu-$(lsb_release -cs)-proposed.list
# Enable Ubuntu proposed archive
deb http://archive.ubuntu.com/ubuntu/ $(lsb_release -cs)-proposed restricted main multiverse universe
EOF

```
And you may have to trim duplicates after that command.

---

### Post by Claus7 on 2024-03-17
Hello,

> **1fallen said:**
> It is much safer using "sudo apt install package-name -t distribution-proposed"
it might be, but it is harder if:
1) you do not know which package you want to update
2) why not having all the proposed packages available under one click?

> **1fallen said:**
> 
I show all in synaptic, but have a look in:
```
cd /etc/apt/sources.list.d && less proposed-repositories.list

```

Unfortunately I do not have such a file under the path proposed.

> **1fallen said:**
> 
Mine reads as:
```
deb http://archive.ubuntu.com/ubuntu/ noble-proposed restricted main multiverse universe

```

I would have expected something similar, yet it is not there.

> **1fallen said:**
> 
The full source list on mine:
```
inxi -r
Repos:
  Active apt repos in: /etc/apt/sources.list
    1: deb http://us.archive.ubuntu.com/ubuntu/ noble main restricted
    2: deb http://us.archive.ubuntu.com/ubuntu/ noble-updates main restricted
    3: deb http://us.archive.ubuntu.com/ubuntu/ noble universe
    4: deb http://us.archive.ubuntu.com/ubuntu/ noble-updates universe
    5: deb http://us.archive.ubuntu.com/ubuntu/ noble multiverse
    6: deb http://us.archive.ubuntu.com/ubuntu/ noble-updates multiverse
    7: deb http://us.archive.ubuntu.com/ubuntu/ noble-backports main restricted universe multiverse
    8: deb http://security.ubuntu.com/ubuntu noble-security main restricted
    9: deb http://security.ubuntu.com/ubuntu noble-security universe
    10: deb http://security.ubuntu.com/ubuntu noble-security multiverse
  Active apt repos in: /etc/apt/sources.list.d/archive_uri-https_download_sublimetext_com_-noble.list
    1: deb https://download.sublimetext.com/ apt/stable/
  Active apt repos in: /etc/apt/sources.list.d/mozilla.list
    1: deb [signed-by=/etc/apt/keyrings/packages.mozilla.org.asc] https://packages.mozilla.org/apt mozilla main
  Active apt repos in: /etc/apt/sources.list.d/proposed-repositories.list
    1: deb http://archive.ubuntu.com/ubuntu/ noble-proposed restricted main multiverse universe
  Active apt repos in: /etc/apt/sources.list.d/protonvpn-stable.list
    1: deb [arch="all", signed-by=/usr/share/keyrings/protonvpn-stable-archive-keyring.gpg] https://repo.protonvpn.com/debian stable main
  Active apt repos in: /etc/apt/sources.list.d/surfshark.list
    1: deb https://ocean.surfshark.com/debian stretch main
  Active apt repos in: /etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-noble.sources
    1: deb https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/ noble main
  Active apt repos in: /etc/apt/sources.list.d/ubuntu-uefi-team-ubuntu-build-noble.sources
    1: deb https://ppa.launchpadcontent.net/ubuntu-uefi-team/build/ubuntu/ noble main
  Active apt repos in: /etc/apt/sources.list.d/ubuntuhandbook1-ubuntu-conkymanager2-noble.sources
    1: deb https://ppa.launchpadcontent.net/ubuntuhandbook1/conkymanager2/ubuntu/ jammy main

```

I suppose that this is your full content of the file mentioned above: proposed-repositories.list, which I do not have available. I tried to search for any file under /etc that will have in its name the word proposed, to no avail.

> **1fallen said:**
> 
You can try to use:
```
software-properties-gtk
```
But there is a bug on that found here:[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2053228](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2053228)
this bug was affecting me as well, yet I'm able to launch it. I do not see any change when I click the option proposed.

> **1fallen said:**
> 
Dang i keep forgetting this method as well:
```
# cat <<EOF >/etc/apt/sources.list.d/ubuntu-$(lsb_release -cs)-proposed.list
# Enable Ubuntu proposed archive
deb http://archive.ubuntu.com/ubuntu/ $(lsb_release -cs)-proposed restricted main multiverse universe
EOF

```
And you may have to trim duplicates after that command.

I'm not able to issue the command you propose, even if I run it with sudo in front. It complains: bash: /etc/apt/sources.list.d/ubuntu-noble-proposed.list: Permission denied

All in all thank you for your thorough response. I think I will stick to the regular upgrades and leave aside the proposed ones, even if at this stage they are fixing serious issues. Another option would be to use the command line. Most of the time, proposed updates under development stage are very risky. 

Regards!

---

### Post by corradoventu on 2024-03-18
Do
```
sudo gted /etc/apt/sources.list.d/ubuntu.sources
```
and add 'noble-proposed' as shown here
```
Types: deb
URIs: http://archive.ubuntu.com/ubuntu/
Suites: noble noble-updates noble-backports noble-proposed
Components: main universe restricted multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
```

Then run ```
sudo apt update
```
and ```
sudo apt install <plan name> -t noble-proposed
```

---

### Post by Claus7 on 2024-03-18
Hello,

> **corradoventu said:**
> Do
```
sudo gted /etc/apt/sources.list.d/ubuntu.sources
```
and add 'noble-proposed' as shown here
```
Types: deb
URIs: http://archive.ubuntu.com/ubuntu/
Suites: noble noble-updates noble-backports noble-proposed
Components: main universe restricted multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
```
...

I did what you mention, without issuing the last command. I wanted to see if synaptic will grab the change. It has somehow. When I choose settings->repositories I'm greeted with the following message:
> The repository information has changed. You have to click the "Reload" button for your changes to take effect

Clicking reload and choosing again repositories, I'm seeing the same message. Seems it needs some refinement there, as synaptic was not working like that.

Regards!

---

### Post by corradoventu on 2024-03-18
You need run ```
sudo apt update
``` otherwise synaptic does know proposed
Then in synaptic go to Preferences -> Distribution and set version from noble-proposed

---

### Post by Claus7 on 2024-03-18
Hello,

> **corradoventu said:**
> You need run ```
sudo apt update
``` otherwise synaptic does know proposed
Then in synaptic go to Preferences -> Distribution and set version from noble-proposed

I see what you are talking about. I came across an enormous amount of upgrades under synaptic, which I won't attempt at the moment. Almost every single package I have was about to get upgraded. I will leave it as is at the moment.

Regards!

---

### Post by #&amp;thj^% on 2024-03-18
> **Claus7 said:**
> Hello,



 Almost every single package I have was about to get upgraded. I will leave it as is at the moment.

Regards!

Wise Choice, 

I "think" corradoventu and I run proposed through out the Dev cycle.

I do it for testing purpose only....I have Three machines running 24.04 and only one has proposed enabled.

Just for your information, and not a suggestion the reason your command failed from my suggestion is sudo is issued in this case as "sudo -i"

But you chose the best plan....Just leave it as is..
Best regards

---

### Post by corradoventu on 2024-03-18
I have 3 partitions with 24.04. on ONE partition i have sometime enabled proposed just for the time needed to install a single package and then DISABLED proposed.

---

### Post by Claus7 on 2024-03-21
Hello,

for some time now, apparmor was one of the few libraries that was found under synaptic in the Installed (local or obsolete) category. I knew that an upcoming version was around the corner, so today I decided to enable anew noble proposed repositories under synaptic: the result was that the new apparmor version became available. I installed it and then disabled the proposed repositories, which made the new version of apparmor obsolete. It seems that synaptic is working as it should. Also, when I first changed the repositories and tried the reload button, I was able to see that it was loading the proposed repositories.

Regards!

---

### Post by corradoventu on 2024-03-21
so which version of apparmor do you have now?
```
apt policy apparmor
```

---

### Post by Claus7 on 2024-03-21
Hello,

> **corradoventu said:**
> so which version of apparmor do you have now?
```
apt policy apparmor
```

$ apt policy apparmor
apparmor:
  Installed: 4.0.0-beta3-0ubuntu2
  Candidate: 4.0.0-beta3-0ubuntu2
  Version table:
 *** 4.0.0-beta3-0ubuntu2 100
        100 /var/lib/dpkg/status
     4.0.0~alpha4-0ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble/main amd64 Packages

Regards!

---

### Post by corradoventu on 2024-03-21
So You have the last version from proposed.

---

### Post by Claus7 on 2024-03-22
Hello,

> **corradoventu said:**
> So You have the last version from proposed.

indeed. This was the way of enabling proposed repositories: using synaptic. In the initial stages of development, enabling proposed repositories that way resulted to a bug, which was related to software-properties-gtk bug. As development progresses it seems that is getting fixed.

Regards!

---

