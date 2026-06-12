---
title: "Issue of gnome software application on ubuntu studio 16.04.01"
date: 2017-01-13
forum: Ubuntu Studio
---

### Post by sleeper2 on 2017-01-13
Hello, i am a new user of ubuntu studio and i have tried to open the gnome software app and she give an error saying that am not in a network, but i already am, because that i can't access to these app.

Another problem i have noticed is an update issue. In the console i put the command "sudo apt-get update" and give me this error:

[I]"
E: Falhou obter cdrom://Ubuntu-Studio 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)/dists/xenial/main/binary-amd64/Packages  Por favor utilize o apt-cdrom para fazer com que este CD seja reconhecido pelo APT. apt-get update não pode ser utilizado para adicionar novos CDs
E: Falhou obter [http://apt.puredata.info/releases/dists/xenial/main/source/Sources](http://apt.puredata.info/releases/dists/xenial/main/source/Sources)  404  Not Found
E: Falhou o download de alguns ficheiros de índice. Foram ignorados ou os antigos foram usados em seu lugar.
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list:56
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list:57
"
Can anybody help me?

Thanks in advance.
[/I]

---

### Post by howefield on 2017-01-13
> **sleeper2 said:**
> Hello, i am a new user of ubuntu studio and i have tried to open the gnome software app and she give an error saying that am not in a network, but i already am, because that i can't access to these app.

Try opening the software app via the terminal and post back the output, if any.

```
gnome-software
```

or perhaps you mean Ubuntu Software app ?

```
ubuntu-software
```

> Another problem i have noticed is an update issue. In the console i put the command "sudo apt-get update" and give me this error:

```
E: Falhou obter cdrom://Ubuntu-Studio 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)/dists/xenial/main/binary-amd64/Packages  Por favor utilize o apt-cdrom para fazer com que este CD seja reconhecido pelo APT. apt-get update não pode ser utilizado para adicionar novos CDs
E: Falhou obter [http://apt.puredata.info/releases/dists/xenial/main/source/Sources](http://apt.puredata.info/releases/dists/xenial/main/source/Sources)  404  Not Found
E: Falhou o download de alguns ficheiros de índice. Foram ignorados ou os antigos foram usados em seu lugar.
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list:56
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list:55 and /etc/apt/sources.list:57
```

What's the output of 

```
cat /etc/apt/sources.list
```

---

### Post by sleeper2 on 2017-01-13
Thanks for the rapid reply but in the both situations it continues give a error. If i write gnome-software in the console give me this 

```
(gnome-software:15544): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(gnome-software:15544): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(gnome-software:15544): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(gnome-software:15544): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(gnome-software:15544): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(gnome-software:15544): GLib-CRITICAL **: g_dir_read_name: assertion 'dir != NULL' failed


```

if i write ubuntu-software give me 

```
comand not found
```

if i write 
cat /etc/apt/sources.list give me

```
deb cdrom:[Ubuntu-Studio 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://pt.archive.ubuntu.com/ubuntu/ xenial main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu/ xenial restricted multiverse main universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://pt.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu/ xenial-updates restricted multiverse main universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://pt.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://pt.archive.ubuntu.com/ubuntu/ xenial universe
deb http://pt.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://pt.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://pt.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://pt.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://pt.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://pt.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://pt.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://pt.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
deb-src http://security.ubuntu.com/ubuntu xenial-security restricted multiverse main universe
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
deb http://apt.puredata.info/releases xenial main
deb-src http://apt.puredata.info/releases xenial main
deb-src http://apt.puredata.info/releases xenial main
deb-src http://apt.puredata.info/releases xenial main


```


What can i do?

Thanks in advance and sorry for the my noob non knowledge of ubuntu.

---

### Post by howefield on 2017-01-13
Can you disable the last four lines in your sources.list file ?

Easier to do with a terminal and you seem comfortable with using one so..

```
sudo nano /etc/apt/sources.list
```

and cursor down to the last 4 lines and place a # symbol at the start of each of them, then use the Ctrl + O key combination to write out the file, press the enter key and Ctrl + X keys to close out.

Then try a ..

```
sudo apt update
```

does it run successfully ?

---

### Post by sleeper2 on 2017-01-13
Thanks again.

In the console i have put the # in the last four lines of the .list you said.

Than i have wrote sudo apt update and send me

```

Ign:1 cdrom://Ubuntu-Studio 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial InRelease
Err:2 cdrom://Ubuntu-Studio 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial Release
  Por favor utilize o apt-cdrom para fazer com que este CD seja reconhecido pelo APT. apt-get update não pode ser utilizado para adicionar novos CDs
Atingido:3 http://pt.archive.ubuntu.com/ubuntu xenial InRelease
Atingido:4 http://pt.archive.ubuntu.com/ubuntu xenial-updates InRelease                                                                                            
Atingido:5 http://pt.archive.ubuntu.com/ubuntu xenial-backports InRelease                                                                                                                     
Atingido:6 http://security.ubuntu.com/ubuntu xenial-security InRelease                                                                                                                        
Atingido:7 http://archive.canonical.com/ubuntu xenial InRelease                                                    
Atingido:8 http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu xenial InRelease
A ler as listas de pacotes... Pronto                                                  
E: The repository 'cdrom://Ubuntu-Studio 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


```

Some of the words are portuguese but i think that you will understand.

Thanks again.

---

### Post by howefield on 2017-01-13
Ok, also put a # symbol at the start of the first line in your /etc/apt/sources.list so that it reads like..

```
# deb cdrom:[Ubuntu-Studio 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main multiverse restricted universe
```

Then try the sudo apt update again.

---

### Post by sleeper2 on 2017-01-13
I already do it and my system is updated and the problem of the gnome software app is solved to.

Tank you very much for helping me.

Just a rapid question, i like very much of the ubuntu studio distribution and i like to contribute to improve the versions and everything i can help. I'm not a programmer, but I'd like to be a tester for new releases and more. How can I join the Ubuntu studio team?

Thank very much for helping me.

Regards

---

### Post by howefield on 2017-01-13
> **sleeper2 said:**
> I already do it and my system is updated and the problem of the gnome software app is solved to.

Cool, that was the next step, to ensure that your installation had no outstanding package updates which was likely to solve the software application issue. Glad it worked out for you.

> Just a rapid question, i like very much of the ubuntu studio distribution and i like to contribute to improve the versions and everything i can help. I'm not a programmer, but I'd like to be a tester for new releases and more. How can I join the Ubuntu studio team?

That's very cool and you would be welcomed I'm sure.

I'd suggesting heading over to the[ Ubuntu Studio webpage]("http://ubuntustudio.org/") and check out the "*Contribute*" links..

---

### Post by sleeper2 on 2017-01-13
Thanks a lot for the helping and rapid response.

Congrats.

---

