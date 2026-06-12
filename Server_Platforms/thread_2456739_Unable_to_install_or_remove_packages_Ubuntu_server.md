---
title: "Unable to install or remove packages Ubuntu server 20.1"
date: 2021-01-18
forum: Server Platforms
---

### Post by deepakdeshp on 2021-01-18
Hello,

I get error installing or removing packages with apt command as follows. What should I do?

```
sudo apt autoremove                Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cpp-7 g++-9 libasan4 libdns-export1109 libisl19 libmpx2 libstdc++-9-dev
  python-jasmin
0 upgraded, 0 newly installed, 8 to remove and 558 not upgraded.
1 not fully installed or removed.
After this operation, 75.7 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 224264 files and directories currently installed.)
Removing python-jasmin (0.9.27) ...
Failed to stop jasmind.service: Unit jasmind.service not loaded.
dpkg: error processing package python-jasmin (--remove):
 installed python-jasmin package post-removal script subprocess returned error e
xit status 5
dpkg: too many errors, stopping
Errors were encountered while processing:
 python-jasmin
Processing was halted because there were too many errors.



```

---

### Post by CelticWarrior on 2021-01-18
First reinstall the package that is "[COLOR=#000000][FONT=&quot]not fully installed or removed".
Then fully update the system before trying the autoremove again.[/FONT][/COLOR]

---

### Post by deepakdeshp on 2021-01-19
> **CelticWarrior said:**
> First reinstall the package that is "[COLOR=#000000][FONT=&amp]not fully installed or removed".
Then fully update the system before trying the autoremove again.[/FONT][/COLOR]
Thank you. It didnt work. In fact I had tried that earlier.

```
sudo apt install python-jasmin[sudo] password for uma: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-jasmin is already the newest version (0.9.27).
E: Can't find a source to download version '0.9.27' of 'python-jasmin:amd64'
uma@localhost:~$ sudo apt purge python-jasmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  python-jasmin
0 upgraded, 0 newly installed, 1 to remove and 558 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 224264 files and directories currently installed.)
Removing python-jasmin (0.9.27) ...
Failed to stop jasmind.service: Unit jasmind.service not loaded.
dpkg: error processing package python-jasmin (--remove):
 installed python-jasmin package post-removal script subprocess returned error e
xit status 5
dpkg: too many errors, stopping
Errors were encountered while processing:
 python-jasmin
Processing was halted because there were too many errors.
```

---

### Post by deadflowr on 2021-01-19
You should run autoremove last after you've installed all updates and fixed any broken packages first.
Currently it shows you have over 500 packages ready to upgrade, and 1 package that is in need of being fixed to install
(Typically when you see the line *1 not fully installed or removed*. it means something's more than likely broken.
Run
```
sudo apt update
sudo apt install -f
```

Post back the output.
(It might be long, as you have 500 packages it will want to update, so you can just post the end of it,
which should give the general summary of it all.)

---

### Post by CelticWarrior on 2021-01-19
And in order to **reinstall **the command is:
```
[COLOR=#000000][FONT=&quot]sudo apt install --reinstall python-jasmin[/FONT][/COLOR]
```
not simply 'install'...

---

### Post by deepakdeshp on 2021-01-20
> **deepakdeshp said:**
> Thank you. It didnt work. In fact I had tried that earlier.

```
sudo apt install python-jasmin[sudo] password for uma: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-jasmin is already the newest version (0.9.27).
E: Can't find a source to download version '0.9.27' of 'python-jasmin:amd64'
uma@localhost:~$ sudo apt purge python-jasmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  python-jasmin
0 upgraded, 0 newly installed, 1 to remove and 558 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 224264 files and directories currently installed.)
Removing python-jasmin (0.9.27) ...
Failed to stop jasmind.service: Unit jasmind.service not loaded.
dpkg: error processing package python-jasmin (--remove):
 installed python-jasmin package post-removal script subprocess returned error e
xit status 5
dpkg: too many errors, stopping
Errors were encountered while processing:
 python-jasmin
Processing was halted because there were too many errors.
```

Last part of sudo apt update
```
Err:12 http://security.ubuntu.com/ubuntu groovy-security InRelease               Temporary failure resolving 'security.ubuntu.com'
Get:13 http://archive.ubuntu.com/ubuntu groovy-updates/restricted amd64 c-n-f Metadata [464 B]
Fetched 12.6 MB in 24s (528 kB/s)                                              


Reading package lists... Done
Building dependency tree       
Reading state information... Done
558 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/groovy-security/InRelease  Temporary failure resolving 'security.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.



```

---

### Post by deepakdeshp on 2021-01-20
> **CelticWarrior said:**
> And in order to **reinstall **the command is:
```
[COLOR=#000000][FONT=&amp]sudo apt install --reinstall python-jasmin[/FONT][/COLOR]
```
not simply 'install'...

```
sudo apt install --reinstall python-jasminReading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of python-jasmin is not possible, it cannot be downloaded.
E: Can't find a source to download version '0.9.27' of 'python-jasmin:amd64'
uma@localhost:~$ 



```

---

### Post by deepakdeshp on 2021-01-20
> **deadflowr said:**
> You should run autoremove last after you've installed all updates and fixed any broken packages first.
Currently it shows you have over 500 packages ready to upgrade, and 1 package that is in need of being fixed to install
(Typically when you see the line *1 not fully installed or removed*. it means something's more than likely broken.
Run
```
sudo apt update
sudo apt install -f
```

Post back the output.
(It might be long, as you have 500 packages it will want to update, so you can just post the end of it,
which should give the general summary of it all.)

After running sudo apt update I ran,
```
sudo apt install -fReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  python-jasmin
0 upgraded, 0 newly installed, 1 to remove and 558 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 224264 files and directories currently installed.)
Removing python-jasmin (0.9.27) ...
Failed to stop jasmind.service: Unit jasmind.service not loaded.
dpkg: error processing package python-jasmin (--remove):
 installed python-jasmin package post-removal script subprocess returned error e
xit status 5
dpkg: too many errors, stopping
Errors were encountered while processing:
 python-jasmin
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

The /var/log/apt/history.log tail command

**Start-Date: 2021-01-20  11:09:28**
**Commandline: apt install -f**
**Requested-By: uma (1000)**
**Remove: python-jasmin:amd64 (0.9.27)**
**Error: Sub-process /usr/bin/dpkg returned an error code (1)**
**End-Date: 2021-01-20  11:09:42**

---

### Post by CelticWarrior on 2021-01-20
Again...

You need to REINSTALL 'python-jasmin' before removing it.

---

### Post by deepakdeshp on 2021-01-20
That was output of apt install -f
Earlier attempt to install python-jasmin had failed.

---

### Post by CelticWarrior on 2021-01-20
> **deepakdeshp said:**
> That was output of apt install -f
Earlier attempt to install python-jasmin had failed.

No, it wasn't.
'apt install -f' tries to REMOVE it and it fails because it's broken.
Again,
```
sudo apt install --reinstall pyhton-jasmin
```
You need the --reinstall argument because it is already partially installed. That's the problem from the start and it shouldn't be necessary to tell you the same thing 3 times already.

---

### Post by deepakdeshp on 2021-01-20
> **CelticWarrior said:**
> No, it wasn't.
'apt install -f' tries to REMOVE it and it fails because it's broken.
Again,
```
sudo apt install --reinstall pyhton-jasmin
```
You need the --reinstall argument because it is already partially installed. That's the problem from the start and it shouldn't be necessary to tell you the same thing 3 times already.
ok . That command also did not work. The server is Ubuntu 20.1 Vmware virtual server if it matters.

```
  sudo apt install --reinstall python-jasmin[sudo] password for uma: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of python-jasmin is not possible, it cannot be downloaded.
E: Can't find a source to download version '0.9.27' of 'python-jasmin:amd64' 
```

---

### Post by deepakdeshp on 2021-01-20
```
sudo apt install python-jasmin    Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-jasmin is already the newest version (0.9.27).
E: Can't find a source to download version '0.9.27' of 'python-jasmin:amd64'
uma@localhost:/etc/apt/sources.list.d$ sudo apt purge python-jasmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  python-jasmin
0 upgraded, 0 newly installed, 1 to remove and 558 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 224264 files and directories currently installed.)
Removing python-jasmin (0.9.27) ...
Failed to stop jasmind.service: Unit jasmind.service not loaded.
dpkg: error processing package python-jasmin (--remove):
 installed python-jasmin package post-removal script subprocess returned error e
xit status 5
dpkg: too many errors, stopping
Errors were encountered while processing:
 python-jasmin
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by CelticWarrior on 2021-01-20
Is the repository still available?
[https://packagecloud.io/jookies/python-jasmin/install](https://packagecloud.io/jookies/python-jasmin/install)

---

### Post by deadflowr on 2021-01-21
Found this: [https://unix.stackexchange.com/questions/491866/unable-to-use-apt-get-because-of-python-jasmine]("https://unix.stackexchange.com/questions/491866/unable-to-use-apt-get-because-of-python-jasmine")

Looks like a known issue.

---

### Post by deepakdeshp on 2021-01-21
> **CelticWarrior said:**
> Is the repository still available?
[https://packagecloud.io/jookies/python-jasmin/install](https://packagecloud.io/jookies/python-jasmin/install)

Thanks. The install was unsuccessful.

```
export dist=groovyuma@localhost:~$ curl -s https://packagecloud.io/install/repositories/jookies/python-jasmin/script.deb.sh | sudo bash
Detected operating system as Ubuntu/groovy.
Checking for curl...
Detected curl...
Checking for gpg...
Detected gpg...
Running apt-get update... done.
Installing apt-transport-https... done.
Installing /etc/apt/sources.list.d/jookies_python-jasmin.list...curl: (22) The requested URL returned error: 404 Not Found




Unable to download repo config from: https://packagecloud.io/install/repositories/jookies/python-jasmin/config_file.list?os=Ubuntu&dist=groovy&source=script


This usually happens if your operating system is not supported by 
packagecloud.io, or this script's OS detection failed.


You can override the OS detection by setting os= and dist= prior to running this script.
You can find a list of supported OSes and distributions on our website: https://packagecloud.io/docs#os_distro_version


For example, to force Ubuntu Trusty: os=ubuntu dist=trusty ./script.sh


If you are running a supported OS, please email support@packagecloud.io and report this.



```

---

### Post by CelticWarrior on 2021-01-21
You should read the error messages, once and for all. This one is quite explicit and comes with specific instructions.
This all started with something you messed up but didn't bother to post about. How exactly we don't know unless you tell us. I suspect that you have been trying to do stuff / install things you don't really understand. That resulted in a partially installed package that now, for the umpteenth time, needs to be reinstalled before it can be removed for good and in order to reinstall you need the repo from where it came from in the first place. That's all and I'm out.

---

### Post by LHammonds on 2021-01-21
> **deadflowr said:**
> Found this: [https://unix.stackexchange.com/questions/491866/unable-to-use-apt-get-because-of-python-jasmine](https://unix.stackexchange.com/questions/491866/unable-to-use-apt-get-because-of-python-jasmine)

Looks like a known issue.
Quoted in case it was missed.

---

### Post by deepakdeshp on 2021-01-25
> **CelticWarrior said:**
> You should read the error messages, once and for all. This one is quite explicit and comes with specific instructions.
This all started with something you messed up but didn't bother to post about. How exactly we don't know unless you tell us. I suspect that you have been trying to do stuff / install things you don't really understand. That resulted in a partially installed package that now, for the umpteenth time, needs to be reinstalled before it can be removed for good and in order to reinstall you need the repo from where it came from in the first place. That's all and I'm out.
Thanks for your time.The forums are to handhold and give help. You advised 3 times to install the package with reinstall switch. I had said other ways of install didn't work. Your method doesn't work too.Advise should help a person. Pontification to read the error messages and to act on that isn't the way. If you don't like my response , you can keep quiet don't try to prove how hopeless I am. On another forum I help am level 18 on that and I follow what I said just now.
Good luck to you. I won't participate in the war you started.

---

### Post by deepakdeshp on 2021-01-25
> **CelticWarrior said:**
> You should read the error messages, once and for all. This one is quite explicit and comes with specific instructions.
This all started with something you messed up but didn't bother to post about. How exactly we don't know unless you tell us. I suspect that you have been trying to do stuff / install things you don't really understand. That resulted in a partially installed package that now, for the umpteenth time, needs to be reinstalled before it can be removed for good and in order to reinstall you need the repo from where it came from in the first place. That's all and I'm out.


Sorry I had missed that. this solution worked.

---

