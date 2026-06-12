---
title: "synaptic security?"
date: 2008-05-26
forum: Security
---

### Post by m9365428 on 2008-05-26
Hey I've been reading up on GPG keys and PGP keys and I had a thought. Does synaptic use any system on data encription or signing to ensure that data packets are not tampered with as you download them or that I'm not downloading a spoof file from a malus server.
I am probably not the first to think of this but I can't find any information on this subject. 

Note: If this topic is taboo I'm sorry but I'm a security freak and I've been dealling with a hacker for the last 8 years and I want to make a super secure machine. If administration removes my post please send me an e-mail with links to relevent information or some information about how I can find out about this topic.

Thanks alot,
M

---

### Post by bwhite82 on 2008-05-26
Yes, trusted repositories provide a signing key. You can view them at System>Administration>Software Sources> and clicking on 'Authentication' tab.

---

### Post by Monicker on 2008-05-26
The debian/ubuntu package management systems use gpg signatures along with several hashes to verify the integrity of a package.

More details can be found here: [https://help.ubuntu.com/community/SecureApt]("https://help.ubuntu.com/community/SecureApt")

---

### Post by m9365428 on 2008-05-26
Okay thanks for the responses but I still don't feel safe. The hacker I've been dealing with will intersept things that I download and put viral installers into the data that allow him access to my system and I need a way to insure that this is not happening with my downloads on the web and with synaptic.

M

---

### Post by bwhite82 on 2008-05-26
SSH tunnel

---

### Post by m9365428 on 2008-05-26
Ok but how do I set that up so that it works automatically. I am still new after all and only know a few things about linux. Any how-to on doing that automatically in synaptic will be very helpful.

M

---

### Post by m9365428 on 2008-05-26
Okay I looked into the System > Admin > Software Sources > Authintification
and I was wondering if synaptic downloaded the keys automatically or if I had to go and download that key myself. If I do have to download this key myself then how do I find these keys on the websites and how do I add a repository to my repository list so that the software will update automatically and securlly. 

If it is possible whould you please provide a how to for the WINE program and its GPG key so I can make sure that I can download the program and the subsicuent updates securly. If you would would you also tell me how you found the apt code line to add to the source.list.

M

---

### Post by cdenley on 2008-05-27
Ubuntu comes secure. The gpg key came with the install cd, and anything in the ubuntu repository should be signed by it.

System>Administration>Software Sources
Make sure the second box (universe) is checked.
```

sudo apt-get update
sudo apt-get install wine

```

If the packages are altered during the download, you will be warned that authentication failed. In that case, choose not to continue with the installation.

If you want a "super secure machine", I wouldn't run anything in wine.

---

### Post by hyper_ch on 2008-05-27
> **m9365428 said:**
> If I do have to download this key myself then how do I find these keys on the websites and how do I add a repository to my repository list so that the software will update automatically and securlly.

the sites will list those keys.

For Medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
> Ubuntu 8.04 "Hardy Heron":
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
Then, add the GPG Key:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```


For using wine repos: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
> 
First, open a terminal window (Applications->Accessories->Terminal). Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

Next, add the repository to your system's list of APT sources:

For Ubuntu Hardy (8.04):
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

For Debian Etch (4.0):
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/etch.list -O /etc/apt/sources.list.d/winehq.list
```

Then update APT's package information by running 'sudo apt-get update'.

Now you can install Wine by clicking this link. Alternatively, you can install by going to Applications->Add/Remove and searching for Wine.

---

