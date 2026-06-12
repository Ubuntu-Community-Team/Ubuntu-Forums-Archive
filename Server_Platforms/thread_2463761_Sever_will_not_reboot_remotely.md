---
title: "Sever will not reboot remotely"
date: 2021-06-17
forum: Server Platforms
---

### Post by irv on 2021-06-17
I have a server running remotely and I did an update and a upgrade and I wanted to reboot it remotely so I issued a command
```
reboot
``` 
This didn't work so I did a
```
shutdown -r
```
With the same result. Here is the message I get.
```
Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up ubuntu-keyring (2012.05.19.1) ...
dpkg: error processing package ubuntu-keyring (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ubuntu-keyring
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Seeing I am not where the server is, is there away to reboot it.
I am running 16.04 and I wanted to upgrade to 18.04 using the command
```
do-release-upgrade
```
But I can do this either because I get the same error as when I try to do just a upgrade.
Any idea how to do to do this?

---

### Post by MAFoElffen on 2021-06-17
It looks like it broke in the middle of that update process...

If you do
```
sudo apt-get install -f

```
That should fix any broken packages and dependencies.
Then if that doesn't also kickstart it back off where it kicked out of that process... Then
```
sudo dpkg --configure -a

```
will configure the yet to be configured packages.

If that does not work, then 
```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade

```
To clean up the recently downloaded packages and redo your upgrades....

---

### Post by irv on 2021-06-18
I did it all but did not do the
```
sudo apt-get dist-upgrade
```
but did the 
```
sudo apt-get upgrade
```
to make sure everything was current. But when I did this I got the same error
```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by LHammonds on 2021-06-18
Make sure you have a good backup BEFORE you do anything.

If the dpkg command and force install did not fix the problem, the next step is to remove the software completely and re-install it.

```
sudo apt remove ubuntu-keyring
```

This command should not remove related configuration files (the --purge option would do that though)

Now clean up the unused packages that are left over:

```
sudo apt clean
sudo apt autoremove
sudo apt update
```

Now install the software again:

```
sudo apt install ubuntu-keyring
```

If that does not fix it, then as a last resort, you may need to be more aggressive in the removal such as including "--purge" and then look into manually removing files by seeing what it installs with this command:

```
sudo ls -l /var/lib/dpkg/info | grep -i ubuntu-keyring
```

On my Ubuntu 18.04 server, I see this as a result:
```

-rw-r--r-- 1 root root     619 Apr  1 06:00 ubuntu-keyring.list
-rw-r--r-- 1 root root     828 Mar 29 09:33 ubuntu-keyring.md5sums
-rwxr-xr-x 1 root root     642 Mar 29 09:33 ubuntu-keyring.postinst

```

I could then manually remove the files with these commands:

```

rm /var/lib/dpkg/info/ubuntu-keyring.list
rm /var/lib/dpkg/info/ubuntu-keyring.md5sums
rm /var/lib/dpkg/info/ubuntu-keyring.postinst

```

Then I would update and re-install the package.

LHammonds

---

### Post by irv on 2021-06-19
Now I am in real trouble.
After doing
```
sudo apt remove ubuntu-keyring
```
I cannot do any 
```
sudo apt clean
sudo apt autoremove
sudo apt update
```
or
```
sudo apt install ubuntu-keyring
```
all it says is
> apt: command not found or apt-get command not found 
if I tried apt-get from an older version of ubuntu.
Once I used the command
```
sudo apt remove ubuntu-keyring
```
it must have removed all the commands. I didn't want to do the purge before you reply to this post.

---

### Post by MAFoElffen on 2021-06-19
That's because it's a vicious dependency issue, the apt-get and apt are dependent on the pubic digital signing key and ubuntu-keyring to work. While installing anything, in specific to what was happening to you "ubuntu-keyring, it uses the old version of the keyring, until the new version of the ubunt-keyring is installed... So the correct was to remove the downloaded new version of that package (which seemed to be broken) and download it again, to install it.

Two options I can think of now... 
First would be to use an ISO image to use as a local repo, and use dpkg to install it from that local repo (so it doesn't need to download it), and forcing dpkg to ignore the signing key. But that would assume that the remote server had access somehow to that that locally accessible image. That is not really a good option for something remote.

Second option would to circumvent Apt, by using "get" to download the current package from the repo, and used dpkg to install it, and force it to ignore the signing key for that install. 

I think the second option is your best bet for that.

But what you might do is to also look at a test run of what apt would do, to see if the "why" of the install failure was due to another dependency issue that was not shown in the original error. (maybe due to summary versus verbose messaging)

---

### Post by irv on 2021-06-19
Even the get command is not found
```
sudo: get: command not found
```
After doing some soul searching, I decided to do a complete backup of all my data files, all 29,848 of them (101.7Gbs).
Then I downloaded the latest server version of Ubuntu 20.04.2 iso and will burn a USB and install it fresh. I will have to set up my static IP address and then reinstall all the data files, but that way I will have it all up to date.
I think I got some bad advice from LHammonds, but I think all he was doing was trying to help.
Thank you all for jumping in here.
Irv

---

### Post by MAFoElffen on 2021-06-19
You are welcome. We all try to help. That is the intent. 

To me, helping others is giving back to all those who have mentored and helped me through the years. I still learn something new every day.

---

### Post by LHammonds on 2021-06-20
> **irv said:**
> Now I am in real trouble.I hope you made a backup BEFORE making any changes which was my first and most important suggestion.

> **irv said:**
> apt: command not found or apt-get command not found
"not found" does not mean it isn't there.  It might have just lost where it is located (e.g. path).
```
/usr/bin/apt
```

Not sure what MAFoElffen was talking about regarding "get" because "get" by itself is not a command...maybe "/usr/bin/wget" which will download a file from a URL.  There is a "get" command parameter for "apt" but I don't think that would bypass apt like what was described.

Granted, I have never tried to uninstall / reinstall ubuntu-keyring and fairly ignorant to actual repercussions of doing so.  If I made your situation worse, I did not mean to do so and I'm very sorry.

**EDIT:** PS - Your picture looks exactly like my father.

LHammonds

---

### Post by MAFoElffen on 2021-06-20
Get (functually) using the utility "wget", which does not check digital signing to access a mirror:
```

wget http://ubuntu.mirrors.tds.net/ubuntu/pool/main/u/ubuntu-keyring/ubuntu-keyring_2020.02.11.2_all.deb
sudo dkg -i ./ubuntu-keyring_2020.02.11.2_all.deb

```
Apt uses the GPG keys stored iin the apt keyring file to check and sign packages in repos... The package ubuntu-keyring contains the GPG keys of the Ubuntu archive. Without those GPG keys, Apt cannot access the Ubuntu repos. And that ubuntu package covers the keys for all Ubuntu repos, immaterial of versions or architecture.

Doing it manually, using both commands above, circumvents that process, and requirement. And if for some reason, dpkg balks at not finding or a wrong digital or missing key/signature, then use -force-install in place of -i ... Not something that you would do normally on untrusted, but the mirror is trusted, and it is manually without the matching keys.

You are correct, if the system said apt and apt-get are now "not found" in the command path, then there are other more serious problems. And removing a key-ring package did not cause any problem related to that. And in that case, just re-installing the keyring is not going to fix that.

---

### Post by irv on 2021-06-20
"not found" does not mean it isn't there. It might have just lost where it is located (e.g. path).
Code:
```
/usr/bin/apt
```
Just for the record, I changed the path before doing the following:
```
:/usr/bin$ sudo apt clean
[sudo] password for irv: 
sudo: apt: command not found
irv@wabasha-server:/usr/bin$ 
```
As you can see the sudo and the apt cannot befound.

---

### Post by MAFoElffen on 2021-06-20
LOL. Now I am getting confused. That didn't say that "sudo" was not found, it said that "for" sudo, that command "apt" was not found...

What version of server, so I can spin up an instance...

---

### Post by irv on 2021-06-20
16.04, It has a message when I boot into the server:
> Welcome to Ubuntu 16.04.7 LTS (GNU/Linux 4.4.0-38-generic i686)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

  System information as of Sun Jun 20 07:04:24 CDT 2021

  System load:  0.08                Swap usage:          48%
  Usage of /:   82.7% of 227.14GB   Processes:           194
  Memory usage: 31%                 IP address for p3p1: 192.168.1.105

  Graph this data and manage this system at:
    [https://landscape.canonical.com/](https://landscape.canonical.com/)

203 updates can be applied immediately.
185 of these updates are standard security updates.
To see these additional updates run: apt list --upgradable

New release '18.04.5 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

---

### Post by MAFoElffen on 2021-06-20
Okay... Do this:
```

sudo su
cd /usr/bin/
./apt --help
#should see the apt help text flash by...
ls -l apt
# should show the file details
echo $PATH
# should show that /usr/bin/ is in the command path

```
If it doesn't, then there is something wrong there...

---

### Post by MAFoElffen on 2021-06-20
Then for 16.04
```

cd /etc/apt/
ls

```
At 16.04, before systemd in 18.04, there should be a directory called "trusted". This is the directory that stores the keyring files. At 18.04 and newer, the functional directory that stores the apt keys is called "trusted.gpg.d"...

---

### Post by irv on 2021-06-20
Did not work:
> irv@wabasha-server:~$ sudo su
[sudo] password for irv: 
root@wabasha-server:/home/irv# ./apt --help
root@wabasha-server:/home/irv# ls -l apt
ls: cannot access 'apt': No such file or directory
root@wabasha-server:/home/irv#

---

### Post by MAFoElffen on 2021-06-20
You didn't change the directory to /usr/bin/ before looking for apt in the current directory, so yes it would not find it in your user home directory... (skipped a step)

And on the echo of the $PATH variable?

I PM'ed you... (You have mail)

---

### Post by MAFoElffen on 2021-06-20
The iso is located at: [https://releases.ubuntu.com/16.04/ubuntu-16.04.6-server-i386.iso](https://releases.ubuntu.com/16.04/ubuntu-16.04.6-server-i386.iso)

Transfer it to your server...
```

scp ~/Downloads/ISO/ubuntu-16.04.6-server-i386.iso irv@wabashaw.server.net:~/Downloads/iso/

```

Mount the iso
```
sudo mkdir /mnt/iso 
sudo mount -o loop ~/Downloads/iso/ubuntu-16.04.6-server-i386.iso /mnt/iso

```

Copy over a backup of your sources list:
```
# Backup your sources list 
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old

```

Note: This next command will overwrite your sources list with a one-line pointer to the local mounted repo...
```
sudo echo "deb [trusted=yes] file:/mnt/iso ./" >> /etc/apt/sources.list

```

On just listing directories, apt and the keyring was completely missing...

On the local machine, since the apt package is not installed,  on the remote server, go to the iso image locally and extract the apt package and transfer it to the remote server. Installing manually with dpkg.

Had to do the same with ubuntu.keyring.

Then try to fix things and clean things up in a little more detail than before...
```

sudo rm /var/lib/apt/lists/lock
sudo rm /var/lib/dpkg/lock
sudo rm /var/lib/dpkg/lock-frontend
sudo rm /var/cache/apt/archives/lock
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update --fix-missing
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get upgrade

```

But it still had errors.
[HR][/HR][HR][/HR]What we did was a Zoom call, sharing screens and talking through it...

The process from this was to get the latest of that ISO image, which was then Local. Transferred it over to the remove server, and mounted it as a local repository.

Since the remote no longer had apt and ubuntu-keyring packages installed, I talked him through mounting the local ISO image and copying over the two packages to the remote.

Then using dpkg, installing those two packages manually on the remote server. 

Still had no love, as those two packages installed successfully, but could not be configured, as there were more, further dependencies issues. Apt worked, but not without errors. With the state of the broken Apt system, there was no way to have the apt utilities that usually fix or recommend... available to fix or figure out on the logic nor the logical order on how to repair them manually. I did a quick analysis of potential suspects online. The problem there was that the version is months well past the soured expiration date for support. That and there were major system changes that went on between 16.04 and 18.04 (systemd). The Ubuntu package manager pages for Xenial are not there anymore. By looking at the next supported, I could only guest-a-mate that there were at least 9 other packages, that might have had problems in the tier above, with a myriad of potentials above them (a cascading effect).

After trying to do this manually without success of reviving Apt, a decision was made at that point. The goal was to upgrade to a newer release anyways... That the further investment in time was better investing in doing a clean install with 20.04:
 - That was good time to call it. 
 - Ensure that the data was backed up. 
 - Install a current version of server. 
 - Migrate to that current version of Server.

---

### Post by irv on 2021-06-21
I personally what to thank MAFoElffen for doing a zoom meeting with me and working for three hours+ to try and get my old server going. In the end, I am going to do a fresh install of the 20.04 server and get it up to date. I will try to do this sometime this week and will get back to you to let you know how it goes. I have all my data backed up.

---

