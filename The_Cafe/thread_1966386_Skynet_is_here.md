---
title: "Skynet is here"
date: 2012-04-27
forum: The Cafe
---

### Post by Red Kelly on 2012-04-27
Hi,

Has anyone eles seen this?
[www.theskynet.org](www.theskynet.org)

Has any one got it working as deamon on ubuntu?

I'd like to help, my server runs Ubuntu 10.4LTS and is way overpowered for a server. I'm not that knowledgeable on Linux so if any one has any pointers it would be appreciated. 
I have found this and am about to try it, I'll update as I go.
[http://ict.icrar.org/store/skynet/](http://ict.icrar.org/store/skynet/)

---

### Post by Red Kelly on 2012-04-27
Ok I think I did it
This is what I did:
```
luke-laptop@laptop:~$ mkdir .skynet
luke-laptop@laptop:~$ cd .skynet/
luke-laptop@laptop:~/.skynet$ wget http://ict.icrar.org/store/skynet/nereus_nix_installer_v1_4.sh
```
This makes dir then downloads install files


```
luke-laptop@laptop:~/.skynet$ chmod a+x nereus_nix_installer_v1_4.sh
```
Makes script executable 


```
luke-laptop@laptop:~/.skynet$ /home/luke-laptop/.skynet/nereus_nix_installer_v1_4.sh -d /home/luke-laptop/.skynet/ -u 106737 -2
```
Will install in dir /home/luke-laptop/.skynet/
106737 is my id number (optional)
-2 will allocate 2gb of ram to skynet


```
luke-laptop@laptop:~/.skynet$ cd nereus/
luke-laptop@laptop:~/.skynet/nereus$ sudo bin/nereus_service.sh start
```
Will start the daemon

It was actually allot easy than I thought :)

I don't know if it will start automatically at boot tho...

---

