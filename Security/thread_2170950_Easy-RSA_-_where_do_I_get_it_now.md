---
title: "Easy-RSA - where do I get it now"
date: 2013-08-28
forum: Security
---

### Post by flickerfly on 2013-08-28
I was setting up a new server and moving a CA I have to it. I have typically installed openvpn to get easy-rsa, but this time when I ran 'sudo apt-get install openvpn' easy-rsa didn't get installed. I see that openVPN has moved Easy-RSA to its own project. 

If it doesn't get installed with the openvpn package, how do I install it on ubuntu? I'd prefer not to compile it myself from the source on github if that's an option.

---

### Post by deadflowr on 2013-08-28
Have you looked in the package manager for it.
or tried installing via apt-get
Try
```
sudo apt-get install easy-rsa
```
and see.

---

### Post by flickerfly on 2013-08-28
Yes, I've spent some time researching the problem. 

I couldn't find any options on apt-get, google, searching the forums here, etc.

---

### Post by cariboo on 2013-08-28
Easy-rsa is in the repositories, make sure you have the universe enabled, and you will be able to install it.

**Edit:** Doing a quick search of [packages.ubuntu.com]("http://packages.ubuntu.com/"), I see that package is only available for raring and saucy.

---

### Post by flickerfly on 2013-08-28
Yeah, 12.04 LTS seems to be a no go. I should have specified that in my OP, which would seem to represent a degredation if OpenVPN doesn't include it in 12.04 also. 

I think splitting it out is a great idea as I usually don't need the client on the machine that I run easy-rsa, but not removing it is not as great an idea which is why I'm asking because it seems unlikely that it was overlooked.

---

### Post by flickerfly on 2013-08-28
Here are some instructions for using the OpenVPN's own repos. I just did that and it works around it. 

[http://repos.openvpn.net/repos/apt/conf/repos.openvpn.net-precise-stable.txt](http://repos.openvpn.net/repos/apt/conf/repos.openvpn.net-precise-stable.txt)
[http://repos.openvpn.net/repos/apt/conf/repos.openvpn.net-precise-snapshots.txt](http://repos.openvpn.net/repos/apt/conf/repos.openvpn.net-precise-snapshots.txt)

Someone else, after I did that, said to look in /usr/share/doc/openvpn/examples/easy-rsa. Maybe that'll help someone else.

---

### Post by cariboo on 2013-08-29
As often happens in the Ubuntu/Debian way of doing things, it may be that the package maintainer left to do other things, and it took a couple of releases before someone else took on the responsibility to maintaining the the packages.

---

### Post by flickerfly on 2013-08-29
Isn't that contrary to the point of the LTS. If it's in the repos for LTS, isn't it under Ubuntu's responsibility to pick up if it get's dropped?

---

