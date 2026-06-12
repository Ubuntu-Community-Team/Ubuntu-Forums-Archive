---
title: "W: An error occurred during the signature verification NO_PUBKEY"
date: 2015-10-10
forum: Ubuntu/Debian BASED
---

### Post by parker-hugh on 2015-10-10
I am using old laptop hp dv5157eu with Zorin OS 9 Lite 32-bit

I am trying to install Kodi and am using following instructions....
```
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get install kodi
```
I got to 'sudo apt-get update' but encountered an error at the end of this process ....
```
margaret@dv5000-zorin9-32bit:~$ sudo apt-get update
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://dl.google.com stable InRelease                                      
Ign http://ppa.launchpad.net trusty InRelease  
...etc...
...etc...
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en_GB             
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en                
Fetched 1,400 kB in 10min 0s (2,331 B/s)                                       
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://deb.opera.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45

W: Failed to fetch http://deb.opera.com/opera/dists/stable/InRelease  

W: Some index files failed to download. They have been ignored, or old ones used instead.
margaret@dv5000-zorin9-32bit:~$ 
```

I am not sure how best to resolve this as I have limited knowledge, although I can use a terminal if I know the correct syntax to enter.

Also I noticed it mentions 'Failed to fetch [http://deb.opera.com/opera/](http://deb.opera.com/opera/)...' but I didn't install Opera so a bit confused. The only browser I can see installed is Firefox. 

I noticed in my sources list there is an entry for 'http://deb.opera.com/opera/' but I think this was already there? so this error is not related to me installing Kodi? 

This is the first time I ran sudo apt-get update as this is a new install today.

Any help would be appreciated

thanks

---

### Post by oldos2er on 2015-10-10
Moved to Other OS Support, Ubuntu/Debian BASED.

When you use the *add-apt-repository* command, the gpg key is automatically added when you press Enter. The terminal output should tell you this.

If you add a repository manually, like I'm assuming you did with the opera repo, you have to add the gpg key manually too. You can do that with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 63F7D4AFF6D61D45
``` Then ```
sudo apt-get update
``` and the warning should be gone. > so this error is not related to me installing Kodi? No.

---

### Post by parker-hugh on 2015-10-10
> **oldos2er said:**
> Moved to Other OS Support, Ubuntu/Debian BASED.

When you use the *add-apt-repository* command, the gpg key is automatically added when you press Enter. The terminal output should tell you this.

If you add a repository manually, like I'm assuming you did with the opera repo, you have to add the gpg key manually too. You can do that with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 63F7D4AFF6D61D45
``` Then ```
sudo apt-get update
``` and the warning should be gone.  No.

Thanks for very quick reply to my post. I just installed zorin today and haven't done anything apart from installing Kodi, so I suspect that opera repo was installed by default during the install process.

I entered the text as suggested in termial and the error has gone. 

Thanks for taking the time to help resolve my problem, it is much appreciated.

---

### Post by oldos2er on 2015-10-10
You're welcome.

---

