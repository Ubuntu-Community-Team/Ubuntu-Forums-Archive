---
title: "Cannot install webmin, its been a week, Ubuntu 15.10"
date: 2016-03-30
forum: Server Platforms
---

### Post by sammy_singh on 2016-03-30
Hi All


I am trying to install webmin for almost a week now, with no success, I have learnt half of linux commands in doing so ..lol. Anyway let me also say that before opening up this thread I have done extensive googling and tried almost everything that was thrown to solve this issue, so bare with with me.


As the title says I am trying to install webmin on ubuntu 15.10, The guide I followed initially was ...


[http://www.ubuntugeek.com/install-webmin-on-ubuntu-15-10-wily-werewolf-server.html]("http://www.ubuntugeek.com/install-we...lf-server.html")


Also before I start I already have installed LAMP and all apachie2 and PHP and MySQL were tested and running


below are my steps that I have tried and output ..


As per guide below steps were done first and were successful

**sudo vi /etc/apt/sources.list**

**deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib**
**deb [http://webmin.mirror.somersettechsol....uk/repository](http://webmin.mirror.somersettechsol....uk/repository) sarge contrib**

**wget [http://www.webmin.com/jcameron-key.asc](http://www.webmin.com/jcameron-key.asc)**

**sudo apt-key add jcameron-key.asc**

**sudo apt-get update**




then starts the nightmare ..

> 
sam9s@homeserver:~$ sudo apt-get install webmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 webmin : Depends: libauthen-pam-perl but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
sam9s@homeserver:~$



I then tried .....

> 
sam9s@homeserver:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
php5-cgi php5-cli php5-common php5-json
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
sam9s@homeserver:~$


I then tried   ..below thinking libauthen-pam-perl is missing

> 
sam9s@homeserver:~$ sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl apt-show-versions
Reading package lists... Done
Building dependency tree
Reading state information... Done
apt-show-versions is already the newest version (0.22.7).
libio-pty-perl is already the newest version (1:1.08-1.1build1).
libnet-ssleay-perl is already the newest version (1.72-1build1).
libpam-runtime is already the newest version (1.1.8-3.2ubuntu2).
perl is already the newest version (5.22.1-9).
openssl is already the newest version (1.0.2g-1+deb.sury.org~xenial+1).
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libauthen-pam-perl : Depends: perlapi-5.20.0
E: Unable to correct problems, you have held broken packages.
sam9s@homeserver:~$


I then tried .....

> 
sam9s@homeserver:~$ sudo apt-get install perlapi-5.20.0
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package perlapi-5.20.0 is a virtual package provided by:
  perl-base 5.20.2-6ubuntu0.2 [Not candidate version]
  perl-base 5.20.2-6 [Not candidate version]


E: Package 'perlapi-5.20.0' has no installation candidate
sam9s@homeserver:~$



After this I am lost and have no idea what to try :confused:.....  please please please assist :(

---

### Post by darkod on 2016-03-30
The guide you linked is no longer available. Not a good sign...

Also, if you took a better look in the repository lines before adding them to /etc/apt/sources.list it says "sarge contrib". Little googling shows that Sarge is very, very old Debian version, dating about a decade ago.

Do not try using repositories that are not maintained and up to date...

In your place, I would comment out the two lines you added related to webmin and then to check if everything is OK with apt try something like:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

If that runs without errors, perfect...

As for webmin, I do not personally use it and do not recommend it, like most other users I guess... It is appealing to users who want to use GUI on linux but I don't know if you are aware in some cases it is not 100% compatible how it managed things and config. That's why it not even a recommended admin tool.

If you insist on using it, try installing it manually unless you can find a more up-to-date repository to use for apt. Personally I suggest you administer your server using ssh and the command line... The basic things to learn are not that difficult, and webmin does not offer any complex administration too. So what ever you can use webmin for, you can learn relatively easy and you are not putting your server in danger.

The version of ubuntu you used is another topic. I don't know if this is just to try ubuntu, but for production use almost no one uses non-LTS releases like 15.10. Either use 14.04 LTS if you can wait, or use the new 16.04 LTS that will come out next month (April).

---

### Post by sammy_singh on 2016-03-30
Hi Darko,

Much thanks for the response, the guide is available bro ..... ([http://www.ubuntugeek.com/install-webmin-on-ubuntu-15-10-wily-werewolf-server.html](http://www.ubuntugeek.com/install-webmin-on-ubuntu-15-10-wily-werewolf-server.html))

However the point you mentioned are pretty valid. The reason I wanted to use webmain was to be able to perform some basic CL tasks like updating fstab file, create directories etc... ...etc. I know how do to this on CLI, but its very tedious, time consuming ... I though webmin will provide me an easy/faster way do to the same. Is there an alternative to webmin or rather is there a way to manage CLI of Ubuntu Server via GUI (not sure if that is even a valid question ... :)).

Coming to ubuntu release I never gave much attention except I thought xx.10 is suppose to be server and xx.04 desktop, am I totally wrong?. I will switch to 16.04 if it is a headless server release (not desktop). But I am already running a truck loads of things on 15.10 (Subsonic, LMS, Plex, minium server, sonar, deluge, NZB Megasearch, couchpotato, headphones). Will I have to reinstall everything with 16.04 or is there a way to upgrade ???

...and thanks for your time in assisting ..

Regards
Sammy

PS :: I forgot to mention, my ubuntu server is a VM running on an ESXi server, hope that does not make a difference .....

---

### Post by darkod on 2016-03-30
This second link works, the first one not (at least not for me)...

Anyway... The numbers do not mean server or desktop. Ubuntu comes out twice a year, in April and October. The LTS comes out every 2 years in April. The version number is in format YEAR.MONTH. That's why the latest version is the (non-LTS) 15.10 from October 2015. The next one now in April will be 16.04 and it will be LTS because it's been 2 years since the last LTS 14.04. The server is always CLI only (headless). For each version there are both desktop and server ISO, plus other types. And you also have both 32-bit and 64-bit, to download what ever you prefer. For example here is the official page for 15.10:
[http://releases.ubuntu.com/wily/](http://releases.ubuntu.com/wily/)

Notice how in the filename you have 'desktop' or 'server' and also i386 or amd64 (32bit and 64bit).

General list of the releases is also here:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

You can notice not only 14.04 LTS but also 12.04 LTS is still offered because officially they have 5 year support which means 12.04 still has support until 2017. And it is offered on the site.

If you want to avoid reinstalling everything you can upgrade to 16.04, after it has been released of course. Since it's a VM on vmware you should probably make a snapshot when the time comes, then upgrade, let it run few days and if you are happy how it's working then integrate the snapshot into the VM (delete it but including the changes in the VM, not descarting them). If you let the VM run long with a snapshot and you have many changes on daily bases, don't forget that the snapshot has separate file and is not including them in the main vmdk file because it doesn't know if you will revert the changes or integrate them. Depending how much free space you have in the datastore, growing snapshots can produce problems for space...

I'm not aware of any GUI tool, honestly I haven't even looked for one in recent years.

---

### Post by sammy_singh on 2016-03-30
Hi Darko,

Thanks again Bro, so you think I should drop the idea of webmin altogether ....... Will update the server to 16.04 when it comes out, one snapshot already taken when I managed to install everything. Thanks for the support and time .. :)

Regards
Sammy

---

### Post by mastablasta on 2016-03-31
drop the webmin idea. it is not supported.

try Ajenti: [http://ajenti.org/](http://ajenti.org/)  (comes with terminal, text editor, file manager... all in browser)
or 
Zentyal (supported by Canonical and community version I free): [http://www.zentyal.com/zentyal-server/](http://www.zentyal.com/zentyal-server/)  --- might be an overkill for you

or if you are willing to move to Debian stable (older stuff bit works well with few bugs) then try Openmediavault: [http://www.openmediavault.org/](http://www.openmediavault.org/)

if you move into red hat there are also: ClearOS (community version is free) or Nethserver (getting better day by day)

---

### Post by SeijiSensei on 2016-03-31
No GUI will be more efficient than the command line for tasks like "updating fstab file, create directories." How often do you need to update fstab anyway?  I might have changed mine once or twice over the past couple of years.  As for creating directories, what could be easier than
```
mkdir -p /path/to/the/new/directory
```

If you have repetitive tasks that you'd like to make more efficient, write scripts.

---

