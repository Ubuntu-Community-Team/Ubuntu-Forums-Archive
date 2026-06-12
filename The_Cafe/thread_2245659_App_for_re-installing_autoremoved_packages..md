---
title: "App for re-installing autoremoved packages."
date: 2014-09-25
forum: The Cafe
---

### Post by sam.nyx on 2014-09-25
use getback for re-install all autoremove packages 

Download this program :KS[URL="http://github.com/codex8/getback"]

http://github.com/codex8/getback[/URL]

---

### Post by vasa1 on 2014-09-25
I came across this thread: [How to re-install all autoremove packages]("http://ubuntuforums.org/showthread.php?t=2245659")

My question is this: is software like that above vetted by anybody?

---

### Post by TheFu on 2014-09-25
github is not vetted in anyway.  It is a place where people, hackers, professionals  store their code. Some extremely well-known projects use github, but it is also used by people like you and me just screwing around with different ideas.  People are generally good and really trying to be helpful, but ... being cautious with any unknown code is always smart, just like being cautious with any unknown website is.  Running code you don't understand is always dangerous, which is why folks here try to educate, not just provide the answer in a vacuum.

You can create a github account and put anything you want there.  It would be available for anyone.  That software could be the greatest thing or malicious.  Use the source, Luke.

---

### Post by coffeecat on 2014-09-25
The thread that vasa1 linked to was posted in “New to Ubuntu”, which is inappropriate. The New to Ubuntu section is for those new to Linux to post their help requests, not for people to promote 3rd party applications. Furthermore, considering the reservations already expressed in the thread vasa1 started here in The Cafe, it would be inappropriate to recommend this app to newcomers without discussion of the pros and cons. In the circumstances I have merged the two threads to make one Cafe thread so that members may discuss relevant issues.

I've also renamed the thread.

@vasa1, apologies, but the timing of the two posts means that the OP of the original New to Ubuntu thread now appears to be the OP of this discussion thread. 

@sam.nyx, please do not post this link anywhere else, but allow members to discuss this application here.

---

### Post by vasa1 on 2014-09-25
> **coffeecat said:**
> ...
@vasa1, apologies, but the timing of the two posts means that the OP of the original New to Ubuntu thread now appears to be the OP of this discussion thread. 
...
No apologies needed. You've addressed the issue and that's what I wanted :)

---

### Post by ian-weisser on 2014-09-25
The github script searches the history file and marks the entire relevant group as 'manually' installed.
This action abuses apt's marking system (admittedly not the only script to do so).
It *does* prevent future erroneous autoremoval, but also prevents future intentional autoremoval of the same packages. For example, uninstalling a chain of PPA dependencies.

Many user of this script seem likely, in my opinion, to be users who don't understand package management, and who are already making unwise choices on the path toward breaking their systems. This script won't help them much, though, since it won't address the package conflict or sources.list conflict that caused the original autoremoval.

A more complex logic, that determines the appropriate top-level packages to restore the entire chain of dependencies, would be more appropriate.

---

### Post by Rob Sayer on 2014-09-26
There's nothing such apps do you couldn't do manually, and I wouldn't use an untrusted 3rd party ppa for anything like this.  I won't even install 3rd party skins let alone something that important.

---

### Post by oldrocker99 on 2014-09-26
Installed packages are likely still on your computer, and can be reinstalled with dpkg, gdebi, or, if you don't mind the slowness, the Ubuntu Software Center.

A quote from superuser.com:

> 
They're stored in:

/var/cache/apt/archives/

unless you've issued a:

apt-get clean

---

