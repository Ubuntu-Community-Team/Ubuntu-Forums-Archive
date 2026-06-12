---
title: "PPA Failure"
date: 2013-11-03
forum: Ubuntu Development Version
---

### Post by Miykel on 2013-11-03
G'Day,  14.04 ..AMD 64   Can any one help me with this problem please,

 Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

Regards Miykel

---

### Post by sanderj on 2013-11-03
Well, easy: go to [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/) and see the latest PPA was for version ... raring. No saucy, no trusty. Just like [https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases) tells you

---

### Post by Miykel on 2013-11-03
Thanks for the reply  				 				 					 						 	[URL="http://ubuntuforums.org/member.php?u=754333"][B][COLOR=#000000]sanderj
[/COLOR][/B][/URL] I appreciate the time, I assume I have to wait till Handbrake catch's up
Reg. Miykel

---

### Post by sanderj on 2013-11-03
Wait, or make handrbrake from source.

---

### Post by cariboo on 2013-11-03
I've been using handbrake from the snapshot raring ppa with zero problems.

---

### Post by Miykel on 2013-11-03
cariboo907, how did you get the raring ppas to load, do you have to do something special
Reg Miykel

---

### Post by sammiev on 2013-11-03
> **Miykel said:**
> G'Day,  14.04 ..AMD 64   Can any one help me with this problem please,

 Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

Regards Miykel

All your ppa's that you are using are trusty. The ones that failed you need to change to raring or saucy. ( which ever one that is supported )

Update: [This]("https://help.ubuntu.com/community/Repositories/Ubuntu") may help as well.

---

### Post by Miykel on 2013-11-04
Thanks so much for the help  				 					[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar628319_2.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=628319") 				 				 					 						 	[**[COLOR=#000000]sammiev[/COLOR]**]("http://ubuntuforums.org/member.php?u=628319")    
   It all worked very well
Rehards  Miykel

---

