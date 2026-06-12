---
title: "SSH Access Denied for user"
date: 2006-04-19
forum: Server Platforms
---

### Post by Coruba67 on 2006-04-19
Howdy!

Am having a problem with this SSH logon.  I can logon from my windows XP box using putty if I wanna log onto sudo @ IP....  However if I wanna ssh in using any other user other than sudo I get an access denied error... any idea why?

Cheers

---

### Post by alamba on 2006-04-19
Not clear enough buddy. You're able to log in via ssh, however, if you want to log in as root (sudo??) u're unable too. Firstly, sudo is not a user. Secondly, root is "dormant" in ubuntu. Even if you have enabled your root account you will need to manipulate the ssh configuration file to allow root logins.

A

---

### Post by Coruba67 on 2006-04-19
ok...  I can SSH into the box as sudo by typing

ssh sudo@192.168.0.1

Once in I setup a new user

adduser hoddav
passwd hoddav password

Now from the same box that I previously used putty to get into the box but now to get in I type

ssh hoddav@192.168.0.1
it asks me for the password which I give it

Access Denied...

any idea's?

---

### Post by jazzmuzik on 2006-04-19
sudo is a user?

---

### Post by Iowan on 2006-04-19
Can you log into 192.168.0.1 directly as hoddav - or is the machine inaccessible directly?

---

### Post by Coruba67 on 2006-04-19
Yeah I can log in directly as hoddav.... If I sit directly infront of the box it lets me log in as hoddav no worries...

---

### Post by LordHunter317 on 2006-04-19
I like the others, are greatly confused.  No user named 'sudo' exists unless you created it.  If so, I fail to understand hte problem.

---

### Post by Coruba67 on 2006-04-20
hahaha ok forget the sudo part...

I can log on as any user name that I have created on that box via SSH except the user called hoddav.

---

### Post by FalconV on 2006-04-24
Yeah, I'm having the same problem, but seems to come and go.
I just installed SSH after a clean install of Ubuntu, didn't tweak anything; Then I installed vnc4server following the guide at [http://www.ubuntuforums.org/showthread.php?t=122402](http://www.ubuntuforums.org/showthread.php?t=122402)
I was able to connect via both SSH and realVNC from my XP box, then when I got home and tried it I got the same "access denied" when trying to log in to my user (the only user so far), I also had problems trying to log in to VNC.  The VNC login window would come up, but after I put in the info (that worked fine at work both locally and remotely) nothing comes up.
I tried again when I came in to work this morning, and was able to SSH just fine (VNC still didn't work though, but I'll be happy just getting SSH working again), and then I tried a minute ago, and wasn't able to connect again (access denied)

---

### Post by imagine on 2006-04-25
[QUOTE=Coruba67]hahaha ok forget the sudo part...

I can log on as any user name that I have created on that box via SSH except the user called hoddav.[/QUOTE]
Eh? So if you do the same as above but create a user called hoddav2 you can log in?
Maybe you added hoddav to the denyusers list in sshd_config.

---

### Post by LuisC-SM on 2006-04-25
[QUOTE=Coruba67]hahaha ok forget the sudo part...

I can log on as any user name that I have created on that box via SSH except the user called hoddav.[/QUOTE]
Create the root user> sudo passwd root
su and type> ssh 192.168.0.1
Forget the "sudo" thing. You must have superuser privileges all the time.

Kind Regards

Luis C. Suárez

---

### Post by FalconV on 2006-04-28
ignore my post, turns out my boss had our entire IP range taken up in his single box, so mine and his were fighting for the IP.  When I got Access Denied, I was just trying to log into his, when I didn't was when I was getting through to mine.  We sorted it out ;)

---

