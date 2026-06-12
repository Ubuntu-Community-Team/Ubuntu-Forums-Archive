---
title: "Updating repositories"
date: 2006-10-24
forum: Repositories &amp; Backports
---

### Post by AndrewS on 2006-10-24
](*,) 

Good evening

I recently started using Ubuntu 6.06 LTS and I'm basically impressed.  I had a few problems with mounting W*****s drives (fixed by editing /etc/pmount.allow) and getting Firefox to access the internet (fixed by editiong /etc/modpeobe.d/blacklist).  Oh, and I couldn't figure how to get Evolution to access my Gmail account, but Thunderbird works fine.

The reason for this post is I can't get the repositories to update.  I get the following error:

[INDENT]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.[/INDENT]

and

[INDENT][http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)[/INDENT]

(sometimes more here, depends how long I wait).

The internet connection works fine.  Am I doing something fundamentally wrong?

TIA  AndrewS

---

### Post by AndrewS on 2006-11-01
Shameless bump!

I really like Ubuntu Linux (it's the first one I can see actually displacing W*****s as the default OS on my PC), but I would like to be able to use the repositories through Synaptic.  Oh, and sound on my old Thinkpad 770E would be nice, but that's for a separate thread!](*,) 

Any help would be appreciated.

TIA

Andrew

---

### Post by Bartender on 2006-11-01
Andrew -
I'm having problems with the u.s. servers.  Same problem at 2 different houses on 2 different PC's.  Weird thing is nobody else is squawking about it!  If your updates were working and aren't now just hang in there.  If your Linux install is brand new there's no reason to think that the repo lists are bad.
EDIT:  If you do a Search for 'updating repositories' there's lots of info but I wouldn't start tweaking your sources.list unless you feel pretty sure something's not right.
ANOTHER EDIT: [aysiu]("http://www.psychocats.net/ubuntu/sources") made a cut-and-paste repository menu if you're up to some command line work...

---

### Post by Roobert on 2006-11-01
Andrew - I haven't been able to update with Synaptic on Ubuntu Dapper at all today. Well, I *did* manage to connect for about 5 minutes, long enough to install a few more packages, but that was about 5 hours ago.

And I'm using a fresh Dapper install, with ***Official*** Ubuntu sources.list!

---

### Post by AndrewS on 2006-11-02
Bartender
Thanks for your reply.  I've _never _been able to get updates to work (either with 6.06 or 6.10), on either of two PCs, with fresh installs.  I'll try the solution suggested by Aysiu.
Andrew

---

### Post by Bartender on 2006-11-02
Andrew -
This whole repository subject is something I know little about.  Did you take a good look at the 2 stickies from ubuntudemon in the top of the "Repositories and Backports" section?  You could paste in his entire sources.list if you wanted.
Make sure to save yours!  If you've made no changes to your sources.list I don't know why it wouldn't work.  Are you absolutely sure your internet connection is working?  Yesterday I saw some posts where guys typed in a really simple command that asked the PC to just ping all the repos in their lists.

---

### Post by Bartender on 2006-11-02
Andrew - 
Have you read [this]("https://help.ubuntu.com/community/Repositories/Ubuntu") from Ubuntu docs?

---

### Post by AndrewS on 2006-11-03
Hi

OK, I followed the instructions in Aysiu's post exactly, even the last bit about (I think) wiping sources.list and starting again.  No joy.  Below: I have posted the contents of the terminal window.  I assume my internet connection is basically OK since I can view web sites, send and receive e-mail etc.  A couple of things that I'm not sure about - what does the ":80" refer to - a port?  Is it the right one? And what is "1.0.0.0" - an IP address?

Thanks again in advance.

Andrew

andrew@ubuntu:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
Reading package lists... Done
andrew@ubuntu:~$ sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
andrew@ubuntu:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
Err [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg                                                                                 
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg                                                                                               
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                                        
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_GB                                                                      
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_GB                                                                                    
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_GB                          
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_GB                              
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_GB                    
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_GB                                
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_GB                      
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_GB
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_GB
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_GB
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_GB
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_GB
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_GB
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_GB
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done        


> **Bartender said:**
> Andrew - 
Have you read [this]("https://help.ubuntu.com/community/Repositories/Ubuntu") from Ubuntu docs?

---

### Post by hyper7 on 2006-11-03
have you tried running the update manager manually?

```
sudo update-manager
```

I've been getting this error for some time now and I don't get why.

```
 warning: could not initiate dbus
```

---

### Post by AndrewS on 2006-11-03
Hello again

I had another browse around the forum, and found a post suggesting that I change the nameserver in /etc/resolv.conf from 192.168.1.1 (the IP of the D-Link router) to 203.8.183.1.  Not sure why, but I certainly downloaded a lot of stuff!

Thanks for all the replies.  Next problem to tackle is lack of sound on the Thinkpad 770E...

Andrew

---

### Post by Zendarin on 2006-11-03
> **hyper7 said:**
> have you tried running the update manager manually?

```
sudo update-manager
```

I've been getting this error for some time now and I don't get why.

```
 warning: could not initiate dbus
```


Hey, I've been getting the same error, but only since I upgraded to "Edgy".

I couldn't install 7 packages, and I've had alot of dependency issues that I'm still sorting out. I think it will be an ongoing process :(

---

### Post by IusedTObeSOMEONEelse on 2006-11-03
~$ sudo update-manager
Password:
warning: could not initiate dbus
could not send the dbus Inhibit signal: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
current dist not found in meta-release file

---

### Post by IusedTObeSOMEONEelse on 2006-11-04
I'm Bumping this as I would like an answer, if not a solution!! Any one? Some one?

---

### Post by tmunro55 on 2006-11-06
I've recently installed Dapper on one of my machines, and I'm getting MD5 checksum errors on security and archive repositories. I have a post in the thread "MD5 Checksum errors" as well.

    I can't seem update the kernel, firefox, openoffice. Two weeks earlier I installed from the same CD on my laptop with no updating issues at all.

:???:

---

### Post by Zendarin on 2006-11-24
> **MustangSallydd said:**
> ~$ sudo update-manager
Password:
warning: could not initiate dbus
could not send the dbus Inhibit signal: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
current dist not found in meta-release file

Ditto.

---

### Post by Ramaddan on 2006-11-29
I also keep having this message from time to time:

> warning: could not initiate dbus

What does it mean? Is something broken?

---

