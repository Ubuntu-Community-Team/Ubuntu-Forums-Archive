---
title: "Server Ubuntu In Egypt Cant Connect to update"
date: 2019-03-05
forum: Ubuntu/Debian BASED
---

### Post by mcdavinci on 2019-03-05
At first you encounter a problem when updating the system
  > "Some index files failed to download. They have been ignored, or old
> ones used instead ' "
  After searching for solutions I had to change the download server, but when I change it I get an error:
  No internet connection
  I came to put download source manually But he will show me another sin I wrote a lot of Command line Update or upgrade has not been improved delete source file And you made a new and I have searched many forums and found no solution - 

                          
                     
                                                        I was unset proxy and not solving
```

     W: The repository 'http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu xenial Release' does not have a Release file.

N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://deb.torproject.org/torproject.org xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W:  Failed to fetch  [http://archive.linux.duke.edu/ubuntu/dists/xenial/InRelease](http://archive.linux.duke.edu/ubuntu/dists/xenial/InRelease)  Temporary  failure resolving 'archive.linux.duke.edu'
W: Failed to fetch  [http://downloads.metasploit.com/data/releases/metasploit-framework/apt/dists/lucid/InRelease](http://downloads.metasploit.com/data/releases/metasploit-framework/apt/dists/lucid/InRelease)   Temporary failure resolving 'downloads.metasploit.com'
E: Failed to fetch [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
```

---

### Post by oldrocker99 on 2019-03-05
The PPA page does not show Xenial at all. That's why you can't find it. Here's how to get rid of that bad PPA:
[http://ubuntuhandbook.org/index.php/2014/01/graphical-tool-add-remove-purge-ppa/](http://ubuntuhandbook.org/index.php/2014/01/graphical-tool-add-remove-purge-ppa/). Cairo is, as you can tell, in the repositories, and the PPA is old.```
sudo apt-get install cairo-dock
```

---

### Post by mcdavinci on 2019-03-06
But When In All packages "Ignored"
ign:1 source .......
ign:2 source .......
ign:3 source .......
ign:4 source .......
ign:5 source .......

---

### Post by mcdavinci on 2019-03-06
2 weeks To Make A Simple ( Sudo apt-get update ) or sudo apt-get upgrade
was following every Solution

In First
  At first you encounter a problem when updating the system
  > "Some index files failed to download. They have been ignored, or old
> ones used instead ' "
  After searching for solutions I had to change the download server, but when I change it I get an error:
  No internet connection
  I came to put download source manually But he will show me another sin I wrote a lot of Command line Update or upgrade has not been improved delete source file And you made a new and I have searched many forums and found no solution
     

and in last

```
W: GPG error: http://deb.torproject.org/torproject.org xenial InRelease: The following signatures were invalid: KEYEXPIRED 1535644863  KEYEXPIRED 1535644863  KEYEXPIRED 1535644863  KEYEXPIRED 1535644863
W: The repository 'http://deb.torproject.org/torproject.org xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.


```

what should I do now &#1567;
i'm using backbox

---

### Post by howefield on 2019-03-06
Moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by mcdavinci on 2019-03-06
I'm Sorry For The Wrong Forum and thanks to move it ):P

---

### Post by mcdavinci on 2019-03-06
Maybe I should Using Redhat Or Fedora ? :D

---

### Post by QIII on 2019-03-06
You could try removing that PPA from your sources list.  Apparently the maintainer of that PPA does not have a package for your release.

PPAs are not managed by Canonical.  They are Personal Package Archives maintained by random users.

What makes you think that something like this would require switching to a Red Hat family distro?  Do you not think that looking for non-existent repos will be a problem?

---

### Post by QIII on 2019-03-06
Threads merged.

---

### Post by mcdavinci on 2019-03-07
The problem here is not in the conversion from one system to another I have been ubuntu users since three years and I loved it a lot and faced a lot of problems with it and was solved with search and continuity but
At the same time I am Redhat Administrator
But most Ubuntu problems do not end
I deleted the source file and restarted the main server - and the source file was automatically created
However, the problem continues, and I lost hope that I would update the system - so I think a lot more that I go back to the Redhat family

---

### Post by mcdavinci on 2019-03-07
> **QIII said:**
> You could try removing that PPA from your sources list.  Apparently the maintainer of that PPA does not have a package for your release.

PPAs are not managed by Canonical.  They are Personal Package Archives maintained by random users.

What makes you think that something like this would require switching to a Red Hat family distro?  Do you not think that looking for non-existent repos will be a problem?

It is also very difficult to wake up every day of sleep instead of starting your work, start solving the endless problems of **Ubuntu** - at the same time I want to keep the Ubuntu user, but at this last problem **stopped **everything - even the first problem I ask about it because I **failed **About 
:(solving them myself

---

### Post by QIII on 2019-03-07
> **mcdavinci said:**
> 
I deleted the source file and restarted the main server - and the source file was automatically created


Would you explain this?  

What main server?

Did you remove the PPA?  How?

You may be having a problem, but that does not mean it is a problem with Ubuntu.  You added the PPA that is causing the issue, not Ubuntu.

What "endless problems with Ubuntu"?  Have you posted here asking about them?  Somehow most of us manage to use Ubuntu without "endless problems".

Disclaimer:  I also use Red Hat family distros, independent distros, SUSE, etc, and have very little, if any, problem with any of them.

---

