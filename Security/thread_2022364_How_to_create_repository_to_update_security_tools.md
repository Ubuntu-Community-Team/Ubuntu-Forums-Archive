---
title: "How to create repository to update security tools"
date: 2012-07-10
forum: Security
---

### Post by securitydude on 2012-07-10
I do a lot of security trainings for my clients and have most of tools installed on my Ubuntu machine which are also on BackTrack security distro. Few questions which are bugging my mind:

1. I was thinking to give my students a ubuntu VM with my security toolkit instead of Backtraack. In this case how will the 3rd party security tools like wireshark, nmap, metasploit framework etc updated? Are they updated automatically when students run "apt-get update" or should I consider making my own repo so that everyone who has VM can connect with repo and download the updates? I am willing to take the pain to make sure the security tools in VM are updated.

2. How can I create my own repository? I assume I need one so that if I decide to add new tools, my students who already have my Ubuntu VM can get updates too.

Thanks.

---

### Post by josephmills on 2012-07-10
this is what I do. 
I go though each tool that I need I look to see what is in the Ubuntu repository's (apt-cache) If the tools are in the Ubuntu repo and the versions are not that far out of date I Use them. 
But If there is a program that is not in the repos not in a repo that is comparable to the OS kernel and libs that I am using. Then I have a repo called beta! that I put these tools in. 
[https://launchpad.net/~josephjamesmills/+archive/beta](https://launchpad.net/~josephjamesmills/+archive/beta)

Some other repo's are out there also. Like [backboxs ]("https://launchpad.net/~backbox/+archive/two")on launchpad and backtracks repo's Thou I am not using 11.04 so it is of no use to me. 

Hope this helps

---

### Post by josephmills on 2012-07-10
> **securitydude said:**
> 
2. How can I create my own repository? I assume I need one so that if I decide to add new tools, my students who already have my Ubuntu VM can get updates too.


Ok so 1st thing is first you must make a ssh and gpg keys 
ssh
```
ssh-keygen
```
gpg
```
gpg --gen-key
```

Once both of them are made you need to upload you GPG Key to Ubuntu Servers (so they can id you)
open seahorse
```
seahorse
```
select you gpg key from the list then  go to  
REMOTE==>SYNCH and Publish
select Keyserver and then pick the Ubuntu One then press synch

[img]http://ubuntuforums.org/attachment.php?attachmentid=221038&stc=1&d=1341966343[/img]





then go to launchpad make a account and upload you ssh and gpg keys to there 
[https://help.launchpad.net/Packaging/PPA/](https://help.launchpad.net/Packaging/PPA/)

after that is done Sign the Ubuntu Code OF Conduct 

Then register a PPA then you can upload with dput and any time that our packages get built again on launchpad it also updates all the users packages that are using that PPA meaning your students. 


Hope that this helps.

---

### Post by securitydude on 2012-07-11
Thanks guys. Now I can sleep in peace. :popcorn:

---

### Post by securitydude on 2012-07-11
Another question: Can I create multiple ppa from one launchpad account?

---

### Post by Cheesehead on 2012-07-11
Creating your own repo simply to host software you didn't create leads to a lot of maintenance overhead.

A less-intensive option is to find the packages in Ubuntu and use [AptUrl]("https://wiki.ubuntu.com/AptUrl") links on a web page. This way, the repos update automatically, and you get the benefit for free.

---

