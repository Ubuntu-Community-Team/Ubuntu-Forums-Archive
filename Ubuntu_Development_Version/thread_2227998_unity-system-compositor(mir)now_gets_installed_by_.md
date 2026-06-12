---
title: "unity-system-compositor(mir)now gets installed by default?"
date: 2014-06-05
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-06-05
Just noticed (after yesterdays updates) that unity-system-compositor has installed itself, even after I edited it out in the .conf file. Anyone else or am I seeing things ?

Regards..

Edit:

 I know we are suppossed to test unity-sys+ but it has this horrible cursor-delay-bug when trying to edit files in certain cases ..... (not here at ubutunforums though).

---

### Post by rrnbtter on 2014-06-05
Greetings,
@ventrical  What output do you have that indicates mir is running. I have this...
 ps afx | grep unity-system-compositor
 8770 pts/13   S+     0:00          |       \_ grep --color=auto unity-system-compositor

and with this 
ps -e | grep unity-system-compositor
no output.
I am getting some flashing video with the current updates though.

---

### Post by zika on 2014-06-05
> **rrnbtter said:**
> Greetings,
@ventrical  What output do you have that indicates mir is running. I have this...
 ```
ps afx | grep unity-system-compositor
 8770 pts/13   S+     0:00          |       \_ grep --color=auto unity-system-compositor
```

and with this 
```
ps -e | grep unity-system-compositor
```
no output.
I am getting some flashing video with the current updates though.Both outputs mean one thing: no unity-system-compositor active...
First output just gives information that pipe (8770) through grep is working its job as You've ordered it to...
We've had this talk several times before... ;)
```
man ps
```

---

### Post by rrnbtter on 2014-06-05
Greetings,
I am well aware of the meaning of my own results. My question to ventrical as to the source of his implied results stands as stated. Just asking so as to attempt to duplicate his terminal instructions and results.

---

### Post by rrnbtter on 2014-06-05
Greetings,
Well! I just got another update and the screen flashing is gone. Everything back to normal.

---

### Post by craig10x on 2014-06-05
Does this mean that mir is now the default on 14.10?  Was just curious...;)
No more compiz?

---

### Post by Cavsfan on 2014-06-05
It's not installed on my system.
```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy unity-system-compositor
unity-system-compositor:
  Installed: (none)
  Candidate: 0.0.3+14.10.20140529-0ubuntu1
  Version table:
     0.0.3+14.10.20140529-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ utopic/universe amd64 Packages

```

Yet I get this:
```
cavsfan@cavsfan-MS-7529:~$ ps afx | grep unity-system-compositor
30280 pts/0    S+     0:00                  \_ grep --color=auto unity-system-compositor

```

Could it be because I never choose Unity?

---

### Post by Cavsfan on 2014-06-05
Logged into a Unity session, checked for updates and still nothing. The video is ok but if I turn the cube the background video is bad.

---

### Post by fjgaude on 2014-06-05
From what I see you can install mir if you wish... it's in the repositories.

---

### Post by grahammechanical on 2014-06-05
I am on a new install from yesterday. I have not installed unity8 desktop session. Nor, anything to do with Unity8 and Synaptic does not show unity-system-compositor installed. I get this from the first command

> ps afx | grep unity-system-compositor
12191 pts/0    S+     0:00                  \_ grep --color=auto unity-system-compositor

and no output from the second command. Mir is not yet default. Yesterday I reviewed a Ubuntu on Air Q&A session and someone asked about Unity8 and 14.10 and the devs were certain that convergence would not be achieved by the release of 14.10.

They did speak of that special Unity8 desktop ISO image as if it was going to go ahead but it would not become a separate branch of Ubuntu. It would only last as long as it was useful. That usefulness would end, I guess, when Mir and Unity 8 really does become the default for Ubuntu.

---

### Post by ventrical on 2014-06-05
> **rrnbtter said:**
> Greetings,
@ventrical  What output do you have that indicates mir is running. I have this...
 ps afx | grep unity-system-compositor
 8770 pts/13   S+     0:00          |       \_ grep --color=auto unity-system-compositor

and with this 
ps -e | grep unity-system-compositor
no output.
I am getting some flashing video with the current updates though.

I am getting this:

```


ventrical@ventrical-MS-7798:~$ ps afx | grep unity-system-compositor
 1181 tty7     Ssl+   0:00  \_ /usr/sbin/unity-system-compositor --file /tmp/mir_socket --from-dm-fd 10 --to-dm-fd 13 --vt 7
 2785 pts/0    S+     0:00                  \_ grep --color=auto unity-system-compositor
ventrical@ventrical-MS-7798:~$ ps -e | grep unity-system-compositor
ventrical@ventrical-MS-7798:~$ 



```


Plus 'top 'says unity-system-compositor is running

 I am just perplexed as to how it activated itself as it was previously installed.

Regards..

---

### Post by ventrical on 2014-06-05
> **Cavsfan said:**
> It's not installed on my system.
```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy unity-system-compositor
unity-system-compositor:
  Installed: (none)
  Candidate: 0.0.3+14.10.20140529-0ubuntu1
  Version table:
     0.0.3+14.10.20140529-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ utopic/universe amd64 Packages

```

Yet I get this:
```
cavsfan@cavsfan-MS-7529:~$ ps afx | grep unity-system-compositor
30280 pts/0    S+     0:00                  \_ grep --color=auto unity-system-compositor

```

Could it be because I never choose Unity?


I get this:

```
ventrical@ventrical-MS-7798:~$ apt-cache policy unity-system-compositor
unity-system-compositor:
  Installed: 0.0.3+14.10.20140529-0ubuntu1
  Candidate: 0.0.3+14.10.20140529-0ubuntu1
  Version table:
 *** 0.0.3+14.10.20140529-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ utopic/universe amd64 Packages
        100 /var/lib/dpkg/status
ventrical@ventrical-MS-7798:~$ 


```


 Thanks for your help.

---

### Post by ventrical on 2014-06-05
> **grahammechanical said:**
> I am on a new install from yesterday. I have not installed unity8 desktop session. Nor, anything to do with Unity8 and Synaptic does not show unity-system-compositor installed. I get this from the first command


and no output from the second command. Mir is not yet default. Yesterday I reviewed a Ubuntu on Air Q&A session and someone asked about Unity8 and 14.10 and the devs were certain that convergence would not be achieved by the release of 14.10.

They did speak of that special Unity8 desktop ISO image as if it was going to go ahead but it would not become a separate branch of Ubuntu. It would only last as long as it was useful. That usefulness would end, I guess, when Mir and Unity 8 really does become the default for Ubuntu.


Thanks grahammechanical.  I am just curious as to how it activated itself thismorning. I thought perhaps .. this is it.. we are going to be defaulted to mir/unity-system-compositor. It is a total mystery to me as to how it activated itself.

Regards..

---

### Post by ventrical on 2014-06-05
It appears that yesterdays update overwrote 10-unity-system-compositor.conf

```

[SeatDefaults]
type=unity;xlocal
unity-compositor-command=unity-system-compositor.sleep


```

I had the 'type=unity;xlocal' line commented out.

Regards..

---

### Post by Cavsfan on 2014-06-05
> **ventrical said:**
> I get this:

```
ventrical@ventrical-MS-7798:~$ apt-cache policy unity-system-compositor
unity-system-compositor:
  Installed: 0.0.3+14.10.20140529-0ubuntu1
  Candidate: 0.0.3+14.10.20140529-0ubuntu1
  Version table:
 *** 0.0.3+14.10.20140529-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ utopic/universe amd64 Packages
        100 /var/lib/dpkg/status
ventrical@ventrical-MS-7798:~$ 


```


 Thanks for your help.

You are welcome. I try to contribute if I can. 
So are you saying that unity-system-compositor just installed itself on your system?

I tried **sudo apt-get install mir** and that didn't go any where. Not that I want to force anything. If it comes down the pipe that's ok.
It looks like Unity 8 and Mir are tied together from looking at some of the packages.

Judging from this link it doesn't look like it quite ready yet though. [_Unity 8 + Mir Can Now Be Tried On The Ubuntu 14.04 Desktop._]("http://www.phoronix.com/forums/showthread.php?96272-Unity-8-Mir-Can-Now-Be-Tried-On-The-Ubuntu-14-04-Desktop&p=421796")

But it looks like it's close.

---

### Post by ventrical on 2014-06-05
> **Cavsfan said:**
> You are welcome. I try to contribute if I can. 
So are you saying that unity-system-compositor just installed itself on your system?

I tried **sudo apt-get install mir** and that didn't go any where. Not that I want to force anything. If it comes down the pipe that's ok.
It looks like Unity 8 and Mir are tied together from looking at some of the packages.

Judging from this link it doesn't look like it quite ready yet though. [_Unity 8 + Mir Can Now Be Tried On The Ubuntu 14.04 Desktop._]("http://www.phoronix.com/forums/showthread.php?96272-Unity-8-Mir-Can-Now-Be-Tried-On-The-Ubuntu-14-04-Desktop&p=421796")

But it looks like it's close.

 See here.
[http://ubuntuforums.org/showthread.php?t=2227998&page=2&p=13042297#post13042297](http://ubuntuforums.org/showthread.php?t=2227998&page=2&p=13042297#post13042297)

---

### Post by fjgaude on 2014-06-05
Fellows, try using **unity-system-compositor** in apt-get install.

---

### Post by ventrical on 2014-06-06
> **fjgaude said:**
> Fellows, try using **unity-system-compositor** in apt-get install.

This is not the problem I am speaking of.  As I mentioned in a previous post , the file, '10-unity-system-compositor.conf' was overwritten after an update.

Regards..

---

### Post by ventrical on 2014-06-06
I commented out the line in question and I'll keep an eye on it. As of this mornings updates, it has not overwritten the file.

Regards..

---

### Post by Cavsfan on 2014-06-06
> **Cavsfan said:**
> You are welcome. I try to contribute if I can. 
So are you saying that unity-system-compositor just installed itself on your system?

I tried **sudo apt-get install mir** and that didn't go any where. Not that I want to force anything. If it comes down the pipe that's ok.
It looks like Unity 8 and Mir are tied together from looking at some of the packages.

Judging from this link it doesn't look like it quite ready yet though. [_Unity 8 + Mir Can Now Be Tried On The Ubuntu 14.04 Desktop._]("http://www.phoronix.com/forums/showthread.php?96272-Unity-8-Mir-Can-Now-Be-Tried-On-The-Ubuntu-14-04-Desktop&p=421796")

But it looks like it's close.

> **ventrical said:**
> See here.
[http://ubuntuforums.org/showthread.php?t=2227998&page=2&p=13042297#post13042297](http://ubuntuforums.org/showthread.php?t=2227998&page=2&p=13042297#post13042297)

Woah! Deje vu! That took me a couple of post back and at first I didn't know where I was. :lolflag: 

I guess it was a pretty dumb question in the first place or else how would you have a 10-unity-system-compositor.conf file to edit.
I will take that in the normal updates when it gets there but I'm not going to install it before then.

---

### Post by ventrical on 2014-06-06
> **Cavsfan said:**
> Woah! Deje vu! That took me a couple of post back and at first I didn't know where I was. :lolflag: 

I guess it was a pretty dumb question in the first place or else how would you have a 10-unity-system-compositor.conf file to edit.
I will take that in the normal updates when it gets there but I'm not going to install it before then.

My bad. I should have been more clear in my explanation in the first place. I'm so busy being busy:) .. but that's no excuse either :)


Regards..

---

### Post by rrnbtter on 2014-06-06
Greetings,
@ventrical Thanks for a interesting thread. Actually there  is no way of knowing what the developers have fully functional and  sitting on the sideline. After all we have a perfectly functional  systemd that is being offered as an option when most of the other  mainline systems are using it default. I suspect that unity system  compositor could be waiting for some catch-up in other areas. 
Anyway  its good that at least something is showing up. I think though that I  will defer an install until I have a reason for confidence in it  working.

---

### Post by ventrical on 2014-06-07
> **rrnbtter said:**
> Greetings,
@ventrical Thanks for a interesting thread. Actually there  is no way of knowing what the developers have fully functional and  sitting on the sideline. After all we have a perfectly functional  systemd that is being offered as an option when most of the other  mainline systems are using it default. I suspect that unity system  compositor could be waiting for some catch-up in other areas. 
Anyway  its good that at least something is showing up. I think though that I  will defer an install until I have a reason for confidence in it  working.

@rrnbtter

I had read some links posted by grahamechanical much earlier on concerning mir and unity-system-compositor. In fact we were both early experimenters. During *THIS* cycle I have realized that there is still a major bug that has not been fixed and so I decided to comment out  the line in the .conf so that I would just have xorg. I didn't think that updating would actually overwrite that .conf file.

  I did notice that there were some major updates to unity8 so I may do a log-on and see what has developed there.

  With Ubuntu .. it is so dynamic that decisions are often made on the go. One day we have unity-system-compositor option .. the next day we may have it as default :)

Regards..

---

### Post by ventrical on 2014-06-07
Huge unity8 and mir/unity-system-compositor updates. I'm checking it out :)

---

### Post by ventrical on 2014-06-07
As suspected, the update overwrote the .conf file once again.

Edit:

The major mir/unity-system-co+ bug (cursor lag) has been fixed  as of recent updates.

Bravo!!

---

### Post by Cavsfan on 2014-06-07
> **ventrical said:**
> My bad. I should have been more clear in my explanation in the first place. I'm so busy being busy:) .. but that's no excuse either :)


Regards..

No problemo! It's all good. :)

Guess I'll see if there are any updates out there to be had.

---

