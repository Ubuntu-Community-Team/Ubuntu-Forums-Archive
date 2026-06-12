---
title: "home folder security"
date: 2011-11-20
forum: Security
---

### Post by vinterkind on 2011-11-20
hi folks,

Is there anyone who changed their folder permissions to 700 and wondered why he/she can't login anymore ? It's usual in RH-Dists and even Debian supports that. So why do I get Authorization Failures if changing permissions on that folder ? I really do not want anyone even the group-readable bit set on my home folder. It should be restrictive first. Not shared.

Cheers,

---

### Post by Paddy Landau on 2011-11-20
Did you change the permission on */home* or on */home/user*?

If you changed it on */home*, please change it back to 644. You need to change */home/user* instead.

Otherwise, I do not understand why you cannot sign in; I can set mine to 700 without any problems logging in. Are you absolutely sure you made the right change to the right folder?

---

### Post by vinterkind on 2011-11-21
Hi,

Yeah, I'm absolutely sure ^^

I've changed permissions on my /home/<user> Directory to 700. And could not log in.
lightdm threw me out and greeted me again. Nothing In between. :-(
At home the only possible thing I could assign was 750. It is sufficient there. 

But at work even that doesn't work. We've got NIS Accounts and everyone has set the world readable bit to access his/her homefolder (Ubuntu). And I'm sure Debian can do 700!

I would be glad if anyone could explain how I can check authorization on that homefolder.
Some way I could read the PAM-config or simply if it has something to do with the PAM.  

If this is not solveable, I can't use Ubuntu for serious working environments.
It is meager, that you even can't configure NIS or LDAP at Installation. 
Ubuntu is more and more a system for home use only. And it's hardening their position. :(

Have fun,
vk

---

### Post by vinterkind on 2011-11-21
> **Paddy Landau said:**
> 
Otherwise, I do not understand why you cannot sign in; I can set mine to 700 without any problems logging in. Are you absolutely sure you made the right change to the right folder?

Yeah. That is exactly the point! :-)

btw. What Ubuntu version do you run ?
( still Ubuntu 11.04 ? I myself run Ubuntu 11.10 )

---

### Post by Jonathan L on 2011-11-21
> changed permissions on my /home/<user> Directory to 700. And could not log in.Hi Vinterkind

In general it's always a good idea to quote the user and group, otherwise the permissions are meaningless.  Why not just check one more time:
```
ls -ld / /home /home/$USER
```Kind regards,
Jonathan.

---

### Post by vinterkind on 2011-11-21
> **Jonathan L said:**
> Hi Vinterkind

In general it's always a good idea to quote the user and group, otherwise the permissions are meaningless.  Why not just check one more time:
```
ls -ld / /home /home/$USER
```Kind regards,
Jonathan.

Yepp. I've done so. And the problem persists.
Everything is in order. And I even can login on a shell!
But lightdm keeps throwing me out. Maybe it's a lightdm problem ?
Does Ubuntu 11.04 does have lightdm ? 
I know 10.04 don't.

cheers

---

### Post by vinterkind on 2011-11-21
Anyone familiar with accounts-daemon, dbus and polkit ?
How does that fit in ?

lightdm got its configuration in /etc/lightdm. But I did not find a clue.

---

### Post by Paddy Landau on 2011-11-21
I am baffled by your problem. I use 11.04. No way should it prevent you from logging in -- unless there is something screwy with your users or groups.

Jonathan L may be onto something. Please post the results of the following two commands:
```
groups ${USER}
ls -ld /home /home/${USER}
```

---

### Post by vinterkind on 2011-11-21
> **Paddy Landau said:**
> 
Jonathan L may be onto something. Please post the results of the following two commands:


As you wish, here is the outcome

drwxr-xr-x 149 root   root   12288 2011-11-02 11:13 /home
drwxr-x---  54 vk informatics   8192 2011-11-21 14:01 /home/vk/

But, as I said - I can login at shell level.

regards,

---

### Post by vinterkind on 2011-11-21
And since its a corp. account 
I am no member of any ubuntu-group.
Only my personal login group

---

### Post by vinterkind on 2011-11-21
Ok. I can login with a local user on the GUI.
But that solves nothing here :-(

Any suggestions what in my profile keeps me from logging in ?

cheers,

---

### Post by vinterkind on 2011-11-21
Hi all,

The problem is circled. It is definitely lightdm which keeps me from logging in.
I've installed GDM and everything works fine. So don't update if you don't need to :-)

I'll keep this open, if I come to any solution.

regards,

---

### Post by Paddy Landau on 2011-11-21
> **vinterkind said:**
> As you wish, here is the outcome

drwxr-xr-x 149 root   root   12288 2011-11-02 11:13 /home
drwxr-x---  54 vk informatics   8192 2011-11-21 14:01 /home/vk/

But, as I said - I can login at shell level.

regards,
Right, you didn't post the results of the groups command. In Ubuntu, by default, you belong to the same group as your own name (plus others). So, I have to assume you still do.

Your home folder should belong to you (which it does) and to your personal group (which it does not -- it belongs to group informatics instead). That, possibly, is what is causing the problem, and which is why I needed the results of [FONT=Courier New][SIZE=2]groups ${USER}[/SIZE][/FONT].

I would suggest you issue the following command and try again.
```
sudo chgrp vk /home/vk
```

---

### Post by Jonathan L on 2011-11-21
Hi again Vinterkind

> home folder should belong to you (which it does) and to your personal group (which it does not -- it belongs to group informatics instead). That, possibly, is what is causing the problemIt's possible that Paddy is right, but it looks okay to me or the home directory to have a different group: there's nothing special about the singleton groups.  (Millions of academic staff have home directories in group "undgrad", "postgrad", "faculty" etc.)

I'd take a look at your dot files: many programs are extremely sensitive about the ownership of .*rc and if they are writeable by anybody but yourself your might consider changing them.  I've even seen programs which complain if they're owned by root.

Hope that's helpful.

Kind regards,
Jonathan.

PS.  Of course you checked disk full and such things?

---

### Post by bodhi.zazen on 2011-11-21
> **vinterkind said:**
> hi folks,

Is there anyone who changed their folder permissions to 700 and wondered why he/she can't login anymore ? It's usual in RH-Dists and even Debian supports that. So why do I get Authorization Failures if changing permissions on that folder ? I really do not want anyone even the group-readable bit set on my home folder. It should be restrictive first. Not shared.

Cheers,

permissions of 700 should work fine in Ubuntu, is there anything else unusual about your login (NFS) ?

See also : 

[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive_Home_Directory_Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive_Home_Directory_Access)

[https://wiki.ubuntu.com/SecurityTeam/FAQ](https://wiki.ubuntu.com/SecurityTeam/FAQ)

---

### Post by vinterkind on 2011-11-22
Ok. First off, thank you all for your messages :-)

I'll give you a short, more detailed view on this problem. Maybe you could reproduce it. I may try it in a virtually set up environment. But let's go on.

Installed is Ubuntu 11.10 with lightdm login manager and unity environment.
We've got our accounts stored on a fileserver, which exports all the homes with NFS. 
We've configured autofs and nis to provide the accounts and homes.
That is why I am a member of the informatics group only. And trust me, thats not the problem.
The important thing here is, that on a local system "root" could see my home - even if I have a 700 permission set. On our fileserver / NFS type of network - she can't access folders (root_squash).

We've never had any problems with logins. It firstly appeared when upgraded to 11.10 with lightdm.
There are no problems with nis nor nfs. Everything works fine. Shell level login is possible.
If I replace lightdm with gdm (which I've stated above) - Everything works. No problem at all.

I apologize If I've been too vague before.
Since it is a "lightdm" problem - We should consider a renaming of this thread.

Have fun,
vk

---

### Post by Paddy Landau on 2011-11-22
vinterkind, thank you letting us know how you solved the problem. That could come in handy for others in your situation. It seems that your set-up differs somewhat from the standard, which is perhaps what fooled us.

Please would you [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by vinterkind on 2011-11-22
> **Paddy Landau said:**
> vinterkind, thank you letting us know how you solved the problem. That could come in handy for others in your situation. It seems that your set-up differs somewhat from the standard, which is perhaps what fooled us.

Please would you [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

Ok. Bug report generated. Maybe it gets really solved :-)

---

### Post by Paddy Landau on 2011-11-22
> **vinterkind said:**
> Ok. Bug report generated. Maybe it gets really solved :-)
Excellent.

---

