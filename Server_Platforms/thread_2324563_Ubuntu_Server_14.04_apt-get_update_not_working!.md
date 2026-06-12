---
title: "Ubuntu Server 14.04 apt-get update not working!"
date: 2016-05-14
forum: Server Platforms
---

### Post by julakspro on 2016-05-14
Hello. When i try to update my server my download is stuck on 0%.
It says 0% [Connecting to ca.archive.ubuntu.com (91.189.91.23)] [Connecting to security] and stays like that.[ATTACH=CONFIG]269066[/ATTACH]

---

### Post by Bashing-om on 2016-05-14
julakspro; Humm ...

No network connectivity ?
What results :
```

ping -c3 8.8.8.8
ping -c3 ubuntu.com

```
As there is a recent breakage with network-manager .. is a GUI installed that also includes network-manager ?

[INDENT][INDENT]strange things can happen
[/INDENT][/INDENT]

---

### Post by julakspro on 2016-05-14
> **Bashing-om said:**
> julakspro; Humm ...

No network connectivity ?
What results :
```

ping -c3 8.8.8.8
ping -c3 ubuntu.com

```
As there is a recent breakage with network-manager .. is a GUI installed that also includes network-manager ?
[INDENT][INDENT]strange things can happen
[/INDENT]
[/INDENT]


so for the 8.8.8.8 and ubuntu.com the results are
[ATTACH=CONFIG]269068[/ATTACH]
and the network-manager hmm i have no clue if i have it installed how do i check. also im using ubuntu server!

---

### Post by Bashing-om on 2016-05-14
julakspro; Well ..

You do have network connectivity . I can not see that the bug affects you .
As this is a server install, the GUI network-manager will not be installed by default.
You can verify :
```

apt-cache policy network-manager

```

Maybe a problem with the ca mirror ? If still a problem .. have you changed your mirror site . See if that resolves ?

[INDENT][INDENT]maybe Yes
[INDENT][INDENT]maybe not so yes[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by julakspro on 2016-05-14
> **Bashing-om said:**
> julakspro; Well ..

You do have network connectivity . I can not see that the bug affects you .
As this is a server install, the GUI network-manager will not be installed by default.
You can verify :
```

apt-cache policy network-manager

```

Maybe a problem with the ca mirror ? If still a problem .. have you changed your mirror site . See if that resolves ?
[INDENT][INDENT]maybe Yes[INDENT][INDENT]maybe not so yes[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


So it says Installed: (none)
Candidate: (none)
Version table:

And the mirror site i tried it many times like the us mirror and the same thing happened :(

---

### Post by Bashing-om on 2016-05-14
julakspro; K,

Then let us try and isolate this to your system's update manager .
As a test, what returns:
```

apt-cache show gedit

```
checking here that we get a response from your mirror .

[INDENT]now this is a thing
[/INDENT]

---

### Post by QIII on 2016-05-14
What other mirror site did you try -- the exact url?

I am getting "unknown host" when I try to ping the mirror you indicate in your image.

What happens if you put [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) into your nav bar on your browser?

---

### Post by julakspro on 2016-05-14
> **Bashing-om said:**
> julakspro; K,

Then let us try and isolate this to your system's update manager .
As a test, what returns:
```

apt-cache show gedit

```
checking here that we get a response from your mirror .
[INDENT]now this is a thing
[/INDENT]

This is what i get
[ATTACH=CONFIG]269073[/ATTACH]

---

### Post by julakspro on 2016-05-14
> **QIII said:**
> What other mirror site did you try -- the exact url?

I am getting "unknown host" when I try to ping the mirror you indicate in your image.

What happens if you put [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) into your nav bar on your browser?

I used this mirror [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
I used this website to generate it! [https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/)

---

### Post by QIII on 2016-05-14
Just realized you said server, so I presume you don't have a gui.

---

### Post by julakspro on 2016-05-14
> **QIII said:**
> Just realized you said server, so I presume you don't have a gui.
Yes

---

### Post by QIII on 2016-05-14
I'm now getting clean results pinging ca.archive.ubuntu.com, the server is showing as keeton.canonical.com

---

### Post by Bashing-om on 2016-05-14
julaksprol Welp;

QIII is hot on this too.
I am presently having my own set of problems . Hard drive being "hot unplugged" and thus my system is crashing. Makes it difficult to respond and keep up !

We know now that you are not talking to the mirror. For some reason .
What are the sources that apt is working with ?
```

cat /etc/apt/sources.list

```

Let's get a tale told.

[INDENT][INDENT]a failure to communicate ??
[/INDENT][/INDENT]

---

### Post by QLee on 2016-05-15
> **Bashing-om said:**
> julakspro; K,

Then let us try and isolate this to your system's update manager .
As a test, what returns:
```

apt-cache show gedit

```
checking here that we get a response from your mirror .

[INDENT]now this is a thing
[/INDENT]

For clarity of  anyone reading this thread, this is a minor point and won't interfere with the solution (since it looks a lot like a mirror that was offline for a bit) but I want to mention that, that command will not require a response from the mirror. It is run on the local system information in the APT library of lists that are downloaded when we do an apt or apt-get update.

---

### Post by julakspro on 2016-05-15
> **Bashing-om said:**
> julaksprol Welp;

QIII is hot on this too.
I am presently having my own set of problems . Had drive being "hot unplugged" and thus my system is crashing. Makes it adifficult to respond and keep up !

We know now that you are not talking to the mirror. For some reason .
What are the sources that apt is working with ?
```

cat /etc/apt/sources.list

```

Let's get a tale told.
[INDENT][INDENT]a failure to communicate ??
[/INDENT]
[/INDENT]


Ok this is what i get when i type in cat /etc/apt/sources.list
[ATTACH=CONFIG]269087[/ATTACH]

---

### Post by QLee on 2016-05-15
This issue may be due to testing or implementation of IPV6 somewhere in the OP's path to the mirror, so even though I can ping the site and QIII can ping it, that might not help the OP. 

I found this, julakspro, see if it applies to your situation with the ca archives:
[http://askubuntu.com/questions/574569/apt-get-stuck-at-0-connecting-to-us-archive-ubuntu-com](http://askubuntu.com/questions/574569/apt-get-stuck-at-0-connecting-to-us-archive-ubuntu-com)

---

### Post by julakspro on 2016-05-15
> **QLee said:**
> This issue may be due to testing or implementation of IPV6 somewhere in the OP's path to the mirror, so even though I can ping the site and QIII can ping it, that might not help the OP. 

I found this, julakspro, see if it applies to your situation with the ca archives:
[http://askubuntu.com/questions/574569/apt-get-stuck-at-0-connecting-to-us-archive-ubuntu-com](http://askubuntu.com/questions/574569/apt-get-stuck-at-0-connecting-to-us-archive-ubuntu-com)

Even after changing it: 
[ATTACH=CONFIG]269088[/ATTACH]

Then when i try to update: 
[ATTACH=CONFIG]269089[/ATTACH]

---

### Post by QLee on 2016-05-16
Sorry that didn't work, it was the link I found that seemed to be most like the problem you told us about. 

You were able to ping both by IP Address and Domain Name on IPV4 but somehow when you tried to update, the ca archive gets translated to IPV6 and fails. I know very little about IPV6, but I would have thought the instructions that you followed from that link would have made the system prefer IPV4. My first guess is still that it could be something in the route to the repository that isn't or wasn't IP6 capable.

Is it still not working today? Just to be sure, how long has this been happening and did you make any changes just before it stopped working?

You can try doing the update with an option for apt-get, try ```
sudo apt-get -o Acquire::ForceIPv4=true update
``` what results do you get? If I understand it correctly, that command will force apt-get to use IPV4 addressing. Maybe the results can give a clue.

---

### Post by howefield on 2016-05-16
Thread moved to the "*Server Platforms*" forum.

---

### Post by julakspro on 2016-05-16
> **QLee said:**
> Sorry that didn't work, it was the link I found that seemed to be most like the problem you told us about. 

You were able to ping both by IP Address and Domain Name on IPV4 but somehow when you tried to update, the ca archive gets translated to IPV6 and fails. I know very little about IPV6, but I would have thought the instructions that you followed from that link would have made the system prefer IPV4. My first guess is still that it could be something in the route to the repository that isn't or wasn't IP6 capable.

Is it still not working today? Just to be sure, how long has this been happening and did you make any changes just before it stopped working?

You can try doing the update with an option for apt-get, try ```
sudo apt-get -o Acquire::ForceIPv4=true update
``` what results do you get? If I understand it correctly, that command will force apt-get to use IPV4 addressing. Maybe the results can give a clue.

Its still now working today.
This has been happening for 3 days now. So i installed the ubuntu server 14.04 and tried to update it and this was the first problem. It was never working correctly.

After typing sudo apt-get -o Acquire::ForceIPv4=true update I got:
It just gets stuck on 0% [Connecting to ca.archive.ubuntu.com (91.189.8 .161 [ Connecting to securit.

Not like before now it just gets stuck on this part and doesnt show any errors!

---

### Post by QLee on 2016-05-16
Well assuming that you just made a typo and you really meant 91.189.88.161, I can ping to that location and it is keeton.canonical.com (91.189.88.161) resolved from ca.archive.ubuntu.com. so that works from here and I have run out of ideas.

The moderator has moved your thread where maybe someone in this subforum has more experience than me with this issue, at least there is a better chance of them seeing it. The others who posted here previously don't appear to be suggesting anything else. I suppose I agree that it appears to be more of a server networking issue.

If I think of anything else to try I will post again, sometimes it happens that troubleshooting ideas pop into my head when I am doing something else unrelated to computers.

Good Luck!

---

### Post by julakspro on 2016-05-16
> **QLee said:**
> Well assuming that you just made a typo and you really meant 91.189.88.161, I can ping to that location and it is keeton.canonical.com (91.189.88.161) resolved from ca.archive.ubuntu.com. so that works from here and I have run out of ideas.

The moderator has moved your thread where maybe someone in this subforum has more experience than me with this issue, at least there is a better chance of them seeing it. The others who posted here previously don't appear to be suggesting anything else. I suppose I agree that it appears to be more of a server networking issue.

If I think of anything else to try I will post again, sometimes it happens that troubleshooting ideas pop into my head when I am doing something else unrelated to computers.

Good Luck!

Sorry but you are wrong i did not make a typo. Here is a screenshot to prove it:
[ATTACH=CONFIG]269120[/ATTACH]

---

### Post by Bashing-om on 2016-05-18
julakspro; Well .. not .

Not much I can add at this point ,, but be nice to know what you can ping:
can you ping your gateway  ?
```

route -n

```
to know the gateway IP .

Can you ping google ?
```

ping -c3 8.8.8.8

```

can you ping ubuntu generically, and resolve DNS ?
```

ping -c3 ubuntu.com

```

Maybe looking at a config issue on your server.

[INDENT][INDENT]strange things can happen
[/INDENT][/INDENT]

---

