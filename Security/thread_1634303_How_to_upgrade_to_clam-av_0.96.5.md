---
title: "How to upgrade to clam-av 0.96.5"
date: 2010-11-30
forum: Security
---

### Post by gdiloren on 2010-11-30
New from yesterday, but I can't upgrade from debian. What should I had in APT line? How do you upgrade the engine of clam-av. Seems complicated!:KS

---

### Post by im_an_elf on 2010-11-30
I'm having the same difficulty upgrading to the newer version.  I upgraded from the last version using a signing key.  It has been a while since I last upgraded clamav, my log indicates April 2010.  Unfortunately, I can't find the page that provided the key.
These commands don't work in updating clamav versions.

apt-get update
apt-get upgrade clamav
freshclam


I'm on the lookout for the page.  If I find the solution I'll post here.

---

### Post by gdiloren on 2010-12-01
> **im_an_elf said:**
> I'm having the same difficulty upgrading to the newer version.  I upgraded from the last version using a signing key.  It has been a while since I last upgraded clamav, my log indicates April 2010.  Unfortunately, I can't find the page that provided the key.
These commands don't work in updating clamav versions.

apt-get update
apt-get upgrade clamav
freshclam


I'm on the lookout for the page.  If I find the solution I'll post here.
Thxs, I think it's still too early and it is not yet in the debian repository. We only have to wait. Anyway, there is no virus threat for Linux, so I feel kind of ridiculous asking for upgrading antivirus just released. The .tar.gz file is on clamav.net but I can't understand how to install it on Maverick (too complicated, I need automatic install);)
I upgraded from version 0.96.3 to version 0.96.4 using this (after putting backports as a choice in Upgrade manager and addingdeb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) maverick main in the sourceAPT line ):

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xf80220d0e695a455e651ac4d8ab767895adc2037 
sudo apt-get update
sudo apt-get upgrade
This comes from[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)
It no longer works, I guess the 0.96.5 version is not yet in the repository!!!

---

### Post by gdiloren on 2010-12-02
Yesterday, I surfed this forum and found some help:
I downloaded the clamav-0.96.5.tar.gz file on [www.clamav.net]("http://www.clamav.net") and put it on my desktop
I opened terminal window
I went to my desktop folder
Cant figure out how to install tar.gz
with synaptic, install alien & gdebi

then goto your tar.gz folder and:

sudo alien -k clamav-0.96.5.tar.gz

you get a deb file, doubleclick on it for installation
It opens in Software center usually for installation, but somehow I did not uninstall previous clamav-0.96.4 and it does not show the version of new engine anymore plus it doesn't install all the package (clamdaemon etc...)
Waiting for some tips...:o

---

### Post by cariboo on 2010-12-02
If the file is on your desktop, just double click it, and file-roller will open. and ask you whee you want to extract it. A program build from source will not remove any already installed packages, you'll have to do that yourself

---

### Post by gdiloren on 2010-12-03
New clam-av version 0.96.5 is available from this morning adding the backport on your update manager (after putting backports as a choice in Upgrade manager and adding "deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) maverick main" in the sourceAPT line ).
Simply go to terminal and type:
sudo apt-get update
sudo apt-get upgrade

Then, follow the instruction
It's an automatic process (removes the old version and installs the new updated one)

---

### Post by entertheraptor on 2010-12-12
> **gdiloren said:**
> New clam-av version 0.96.5 is available from this morning adding the backport on your update manager (after putting backports as a choice in Upgrade manager and adding "deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) maverick main" in the sourceAPT line ).
Simply go to terminal and type:
sudo apt-get update
sudo apt-get upgrade

Then, follow the instruction
It's an automatic process (removes the old version and installs the new updated one)

Hi, I'm pretty new to all of this command line business and could use detailed step by step instructions on exactly how to achieve the above.

Running Ubuntu 10.10 server edition and getting the warning that ClamAV has newer version. Currently running 96-3.

Thanks in advance.

---

### Post by cariboo on 2010-12-12
> **entertheraptor said:**
> Hi, I'm pretty new to all of this command line business and could use detailed step by step instructions on exactly how to achieve the above.

Running Ubuntu 10.10 server edition and getting the warning that ClamAV has newer version. Currently running 96-3.

Thanks in advance.

To add a repository, just open your favorite text editor, I use nano. add the the repositoriy **deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) maverick main **to the end of /etc/apt/sources.list:

```
sudo nano /etc/apt/sources.list
```

enter your passowrd when asked. Once the file is open. you can simply copy and paste the ppa address  to the end of the file.

**Note** before making any changes to a configuration file, create a backup, that way you can still go back to the original if you make a mistake. In the case of the above file in a terminal type:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

the above command copies /etc/apt/sources.list to /etc/apt/sources.list.bak

---

### Post by entertheraptor on 2010-12-13
Hey thanks for that, great instructions.

However after I followed them and then ran "apt-get update" I (among other things) got this

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8AB767895ADC2037

---

### Post by cariboo on 2010-12-13
@entertheraptor

Follow the instructions in post #3 to update the key.

Or go to [https://launchpad.net/~ubuntu-clamav/+archive/ppa](https://launchpad.net/~ubuntu-clamav/+archive/ppa)

click on the Technical details about this PPA, then click the link under Signing key, click the link beside pub, copy the whole key and paste it into a text file and save it, then go to System->Administration->Synaptic Package Manager->Settings->Repositories->Authentication, Click the Import Key File, and navigate to the file you just created.

---

### Post by entertheraptor on 2010-12-13
Done all except the last part. I'm using the server edition (10.10) so if I need to update any files it has to be done on the command line. I have the key now saved in a text file, so what now?

---

### Post by cariboo on 2010-12-13
did you try the commands in post #3 and what were the results?

---

### Post by entertheraptor on 2010-12-13
In a nutshell I'm still in the same boat.

Are you referring to the commands in the quote or the commands toward the bottom of the post? In any case I ran them all and still have clamAV 96-3

---

### Post by cariboo on 2010-12-14
0.96.3 is the latest available from the ppa, If you want something newer, you'll have to install from source, which you can get [here]("http://www.clamav.net/lang/en/download/sources/").

---

### Post by duceduc on 2010-12-22
I am also trying to upgrade clamav but after running the update and upgrade, there is no new version. I have added the repo and follow thread #3.

Update. I've checked my clamav version and is at 96.3. The lastest recommended veris 96.5.
I've downloaded the 9.6.5.tar but am confused on how to install it on my 10.4 server.

---

### Post by cariboo on 2010-12-22
Untar it, there should be installation instructions inside the tarball.

---

### Post by duceduc on 2010-12-26
I've tried installing from source but am getting errors when I 'make check' I also ignore the message and install it anyways but I don't know the command to run freshclam. I am mainly using this for my mail server.
I guess I will wait for the repo. Thanks for the tip btw.

---

### Post by gdiloren on 2011-01-02
> **gdiloren said:**
> New clam-av version 0.96.5 is available from this morning adding the backport on your update manager (after putting backports as a choice in Upgrade manager and adding "deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) maverick main" in the sourceAPT line ).
Simply go to terminal and type:
sudo apt-get update
sudo apt-get upgrade

Then, follow the instruction
It's an automatic process (removes the old version and installs the new updated one)
May be I have to be clearer: go System/Administration/Software center, click settings and enter your root password, in Other software click add and copy/paste the whole sentence between "deb...maverick main", click add source then go to the updates section and check the unsupported updates ( maverick-backports ). Click Ok then go in the terminal and type
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xf80220d0e695a455e651ac4d8ab767895adc2037  
sudo apt-get update
sudo apt-get upgrade
  After the successful installation, be sure to uncheck (that's very important!)  the maverick-backports in the software center as they are source of viruses. It worked for me.:popcorn:

---

### Post by gdiloren on 2011-01-02
> **cariboo907 said:**
> @entertheraptor

Follow the instructions in post #3 to update the key.

Or go to [https://launchpad.net/~ubuntu-clamav/+archive/ppa]("https://launchpad.net/%7Eubuntu-clamav/+archive/ppa")

click on the Technical details about this PPA, then click the link under Signing key, click the link beside pub, copy the whole key and paste it into a text file and save it, then go to System->Administration->Synaptic Package Manager->Settings->Repositories->Authentication, Click the Import Key File, and navigate to the file you just created.
If my public key doesn't work, then follow the instructions up here... But I updated to the latest edition without going into all this!

---

### Post by duceduc on 2011-01-02
I've added the repo in the sources.list but no new update for clamav shows up.

---

### Post by gdiloren on 2011-01-02
> **duceduc said:**
> I've added the repo in the sources.list but no new update for clamav shows up.
You have to read exactly the last two threads and follow the instructions then use the terminal without forgetting to check the maverick backports in the settings tab of software center. It worked for me about one month ago. Is it possible they took it off suddenly of the repository, and then why???

---

### Post by duceduc on 2011-01-02
I added the repo and the key last week and have deleted since there was no update. I re-added the repo, but this time it didn't prompt me for the key this time. Perform update and upgrade but no new update for clamav. I am at version .93

The second [link](https://launchpad.net/%7Eubuntu-clamav/+archive/ppa) you mentioned said to add these two lines substituting your version of ubuntu.  

> deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) lucid main 

Did i miss something?

---

### Post by gdiloren on 2011-01-02
If you previously tried to upgrade installing the tar.gz file you probably have a bad install of clam-av 96.5. I would suggest to look out for a folder usually in your home directory where the tar.gz might have unzipped the clam-av 96.5 folder: send it to trash and empty it! It might be the source of problem. Have you been asked the yes or no question on whether to upgrade or not? I'm sorry to say I can't help you much further with it, only thing is it worked on my pc a few weeks ago and I'm sorry it no longer works then. Anybody has tried this upgrade? Also of course, If you have Ubuntu 10.10, you use maverick, not lucid in the source...
P.S.: Are you sure you checked the maverick backports in settings button on software center???
Also, you should try what you quoted as the PPAs where updated from the time where I personnally upgraded....

---

### Post by gdiloren on 2011-01-02
> **gdiloren said:**
> If you previously tried to upgrade installing the tar.gz file you probably have a bad install of clam-av 96.5. I would suggest to look out for a folder usually in your home directory where the tar.gz might have unzipped the clam-av 96.5 folder: send it to trash and empty it! It might be the source of problem. Have you been asked the yes or no question on whether to upgrade or not? I'm sorry to say I can't help you much further with it, only thing is it worked on my pc a few weeks ago and I'm sorry it no longer works then. Anybody has tried this upgrade? Also of course, If you have Ubuntu 10.10, you use maverick, not lucid in the source...
P.S.: Are you sure you checked the maverick backports in settings button on software center???
Also, you should try what you quoted as the PPAs where updated from the time where I personnally upgraded....
LAST EDITED: I checked again my backport entry and just performed an upgrade of my already existing one month old 96.5 version, so definitely my method - not even using the terminal- WORKS.

---

### Post by sholdowa on 2011-01-03
I'm not too sure why people are recommending these non-standard repositories to get clamav from. It's already available in your backports, so just enable that and update.

For those running LTS versions, I think it *extremely important* to take care what sources you add. Keep it mainstream (:

---

### Post by duceduc on 2011-01-03
sholdowa,

That was easy. I just uncommented the two existing backports in the sources.list and do an update and upgrade. 
Now, clamav is at 96.5. Thanks.

---

