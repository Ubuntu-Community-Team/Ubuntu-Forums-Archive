---
title: "Error Converting Samba Users to Linux Users via Webmin"
date: 2015-12-30
forum: Server Platforms
---

### Post by robo731 on 2015-12-30
I've been following [these directions]("http://linuxhomeserverguide.com/server-config/Samba.php"). I've made it up to the point where I convert linux users to samba users. The problem is I get the following error: [IMG]http://i.imgur.com/fmweZFQ.png[/IMG]

I found posts about people who had a similar problem, but I was unable to find any solutions.

---

### Post by bab1 on 2015-12-30
> **robo731 said:**
> I've been following [these directions]("http://linuxhomeserverguide.com/server-config/Samba.php"). I've made it up to the point where I convert linux users to samba users. The problem is I get the following error: [IMG]http://i.imgur.com/fmweZFQ.png[/IMG]

I found posts about people who had a similar problem, but I was unable to find any solutions.
You don't exactly "convert" Linux users; more like you add them to the Samba user database.  Let's see if you really were successful.  Post the output of this terminal command```
sudo pdbdit -L
```

---

### Post by robo731 on 2015-12-30
I tried: ```
sudo pdbdit -L
``` which returned: "pdbdt: command not found."

I then tried: ```
sudo pdbedit -L
``` which returned nothing at all.

---

### Post by bab1 on 2015-12-30
> **robo731 said:**
> I tried: ```
sudo pdbdit -L
``` which returned: "pdbdt: command not found." I then tried ```
sudo pdbedit -L
``` which returned nothing at all.
Sorry for the typo.  You need to add the users manually.  You can do that with this command```
smbpasswd -a <user>
```...substituting your users names for <user>.  You should be prompted for the users password.  Use that users Linux password.

Are you sure that you created Linux users?  You can see that with this command```
getent passwd|grep 100
```...this will show the users that start with 100 (1000 >).

---

### Post by robo731 on 2015-12-30
I mean... I'm not entirely sure lol. The only user that will need access to the server is me. Should I just manually add myself using the code you wrote above?

Here's the [output]("http://paste.ubuntu.com/14303963/") of ```
getent passwd|grep 0
```

I'm not familiar with linux really, but it looks to me like the users before 100 are system defaults or something. Then there's a user besides me beyond 100 which also seems to be some kind of system default. So I guess I'm the only user?

---

### Post by bab1 on 2015-12-30
> **robo731 said:**
> I mean... I'm not entirely sure lol. The only user that will need access to the server is me. Should I just manually add myself using the code you wrote above?

Here's the [output]("http://paste.ubuntu.com/14303963/") of ```
getent passwd|grep 0
```
This should be 100 not 0.> 

I'm not familiar with linux really, but it looks to me like the users before 100 are system defaults or something. Then there's a user besides me beyond 100 which also seems to be some kind of system default. So I guess I'm the only user?
Post the output of ```
getent passwd
```... this will show all the users on the system.

There are 3 types of users in a Linux system.  The root user (uid=0), system users (uid=1 - 999 (on Ubuntu)) and mortal users (humans) from uid=1000 on.

The users we are talking about have a uid of 1000 or greater.  The user that installs Ubuntu is typically assigned the uid of 1000.

If you are trying to set up Samba shares that you want to only be accessible by your user, then you need to have both a Linux (Ubuntu) user (adduser) and a Samba user (smbpasswd -a).

Post the listing of all the users and we can go from there.  Since webmin hasn't worked out for you, why don't we try using the command line to finish this?  It is very simple (not including our typos).  ;-)

[COLOR="#0000FF"]Edit:  Ahhhhh, I just saw your link to pastebin.  Your user is uid=1000.  See ```
robo731:x:1000:1000:Rob,,,:/home/robo731:/bin/bash
```

So yes you just need to add yourself to the Samba database with this ```
smbpasswd -a robo731[/COLOR]
```

---

### Post by robo731 on 2015-12-30
Yeah, I put 0 because I figured that would list all users. Here's the [output]("http://paste.ubuntu.com/14304365/") of ```
getent passwd
```

Thanks for the explanation of the system. I figured it would be something like that.

The command line sounds good.

[COLOR=#0000ff]Edit: I just saw your edit. I'll add myself using [/COLOR]```
smbpasswd -a robo731
```

[COLOR=#ff0000]Edit 2: Awesome, that worked. Thank you for the help. I am able to access the share I've created now. The only issue is that I cannot write to it. Fore example, when I try to create a new txt file, it says access is denied. I've set the share settings according to this [guide]("http://linuxhomeserverguide.com/server-config/Samba.php") I linked earlier, under the "Creating a Samba Share" heading. Not sure why I don't have access to it though.[/COLOR]

---

### Post by bab1 on 2015-12-30
> **robo731 said:**
> 
[COLOR=#ff0000]Edit 2: Awesome, that worked. Thank you for the help. I am able to access the share I've created now. The only issue is that I cannot write to it. Fore example, when I try to create a new txt file, it says access is denied. I've set the share settings according to this [guide]("http://linuxhomeserverguide.com/server-config/Samba.php") I linked earlier, under the "Creating a Samba Share" heading. Not sure why I don't have access to it though.[/COLOR]
That's because the file system permissions are not set correctly.  The Ubuntu file system is what grants you access.  The Samba authentication is for accessing the share not the ability to read or write.

---

### Post by robo731 on 2015-12-30
I ran ```
sudo chmod -R 777 /media
``` That did the trick. Thanks again for your help.

---

### Post by bab1 on 2015-12-30
> **robo731 said:**
> I ran ```
sudo chmod -R 777 /media
``` That did the trick. Thanks again for your help.
Since you are the only mortal user for Samba I guess it is okay.  If you have more users then you need to learn how the user/group ownership and permissions really work.

Please mark this thread as "solved" since we have it working now.

---

### Post by robo731 on 2015-12-30
Yeah, I realize it is sort of a temporary solution.

---

