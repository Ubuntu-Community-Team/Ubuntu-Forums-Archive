---
title: "Snappy: Questions"
date: 2015-04-24
forum: Ubuntu, Linux and OS Chat
---

### Post by vtpoet2 on 2015-04-24
Figures, now that I've really gotten a handle on apt-get and am command-line competent, they throw in the wrench. But if it's better, I'm keeping an open mind. And sorry if these ?s have already been asked.  :-)


[LIST=1]
[*]Will Snappy be command-line friendly -- searchable, etc...
[*]Will apt still be usable/operate in parallel? -- or is the plan to remove apt altogether?
[*]Will compiling/building the occasional piece of software still be necessary, as easy, or more complicated (should apt be removed)?
[*]Will Snappy's including all libraries make it less secure/same/more?
[*]Will snappy be DE dependent, or will Kubuntu/Xubuntu/Mint & other Ubuntu spins be able to use it (if they wish)?
[/LIST]

---

### Post by grahammechanical on 2015-04-24
> they throw in the wrench

I do not agree. Snappy Ubuntu Core at the moment is server oriented. There are aspects of the snappy concept that would certainly bring security benefits to Ubuntu desktop. But I have no doubt that users will still be free to break the desktop or put the security of the OS at risk.

[https://developer.ubuntu.com/en/snappy/](https://developer.ubuntu.com/en/snappy/)

[https://wiki.ubuntu.com/SecurityTeam/Specifications/SnappyConfinement](https://wiki.ubuntu.com/SecurityTeam/Specifications/SnappyConfinement)

As far as I can see the choice is not so much between using snappy apps against using deb apps but in regard to getting transactional updates with an automatic roll back if an update fails and using the apt-get method.

did you watch this Q & A. I think some comments were made that relate to this matter. But I cannot say for sure.

[https://www.youtube.com/watch?v=t6IYI1Ax4mA](https://www.youtube.com/watch?v=t6IYI1Ax4mA)

Regards.

---

### Post by vtpoet2 on 2015-04-24
//Snappy Ubuntu Core at the moment is server oriented. //

Yes, but you might be conflating Snappy Core with what I'm asking about -- which would be Snappy (or *Snappy Personal* as they seem to be calling it):

[http://www.webupd8.org/2015/04/ubuntu-desktop-to-eventually-switch-to.html](http://www.webupd8.org/2015/04/ubuntu-desktop-to-eventually-switch-to.html)

//As far as I can see the choice is not so much between using snappy apps against using deb apps//

That's not so clear, hence my questions. It would appear that Snappy Personal might well replace debs altogether, but I'm not certain.

---

### Post by ventrical on 2015-04-27
I installed snappy a couple of  days ago.

[http://www.ubuntu.com/cloud/tools/snappy](http://www.ubuntu.com/cloud/tools/snappy)

It downloads an image file and you are able to run it in terminal. I think it states that it will do away with apt-get but you can still use apt-get for debs  while working off the core. I still have not yet run any 'smart things' but there a a few commands that Mark provides at his blog.

[http://www.markshuttleworth.com/](http://www.markshuttleworth.com/)

Regards..

---

### Post by kostkon on 2015-04-27
> **vtpoet2 said:**
> That's not so clear, hence my questions. It would appear that Snappy Personal might well replace debs altogether, but I'm not certain.
That's the plan, yes. But, I guess it is probably a bit early to be asking definitive answers to your questions.

As you may have realised, many people still don't know about snap(py) packages.

---

### Post by ventrical on 2015-04-27
Here is a helper too..

Edit: graham already put that link.

  


[URL="http://developer.ubuntu.com/en/snappy/start/"]http://developer.ubuntu.com/en/snappy/start/  



[/URL]

---

### Post by ian-weisser on 2015-04-27
The UOS stream next week, where many answers are promised, will be fascinating to watch.

---

### Post by vtpoet2 on 2015-04-27
> **kostkon said:**
> That's the plan, yes. But, I guess it is probably a bit early to be asking definitive answers to your questions.

Yeah, okay, thanks. I'll stay tuned and see what turns up. Sounds like it might be a good system with some advantages, but I might be a little bummed now that I've finally figured out command-line deb-awesomeness. ;)

---

### Post by ventrical on 2015-04-27
> **vtpoet2 said:**
> Yeah, okay, thanks. I'll stay tuned and see what turns up. Sounds like it might be a good system with some advantages, but I might be a little bummed now that I've finally figured out command-line deb-awesomeness. ;)


  There are just switching  'apt-get' to 'snappy'.


```

sudo snappy version-update

```

etc..


 I know it is not the same thing and the downloads are purportedly  more secure and one can roll back to earlier version. It looks fun  but I can only update stuff and do a few commands. There is not much out there as far as man pages and trying 'smart things' on it.

---

### Post by craig10x on 2015-04-27
New article about ubuntu adopting "snappy" packages:
[http://www.webupd8.org/2015/04/ubuntu-desktop-to-eventually-switch-to.html#more](http://www.webupd8.org/2015/04/ubuntu-desktop-to-eventually-switch-to.html#more)

---

### Post by Elfy on 2015-04-27
> **craig10x said:**
> New article about ubuntu adopting "snappy" packages:
[http://www.webupd8.org/2015/04/ubuntu-desktop-to-eventually-switch-to.html#more](http://www.webupd8.org/2015/04/ubuntu-desktop-to-eventually-switch-to.html#more)

ummm - see post #3 

looks the same to me ;)

---

### Post by craig10x on 2015-04-27
Oops...missed that :mrgreen:
Was an interesting read though...that is what is supposed to lead to the 6 month version of ubuntu morphing into a kind of "rolling" ubuntu (that Mark Shuttleworth discussed about a year ago)...apps and stuff updating much like your iphone or android does...

---

