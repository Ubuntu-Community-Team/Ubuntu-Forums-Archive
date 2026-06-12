---
title: "samba : permission denied on &quot;sub share&quot;"
date: 2016-02-14
forum: Server Platforms
---

### Post by pcouderc on 2016-02-14
It is a very old server now in 14.0 LTS.
SAMBA works since years.
But since a few weeks,  I can no more access "inside" a share, even if I access to first level.
My share points on /.

```

ls -lh /mnt/server

```
 shows many things including :
```

ls: /mnt/server/opt: Permission denied
...
ls: /mnt/server/var: Permission denied
total 0
...
drwxr-xr-x   4 root root  0 Dec  5 15:21 opt
...
drwxr-xr-x  23 root root  0 Apr 23  2015 var
....

```

But :
```

$ls -lh /mnt/server/var
ls: cannot access /mnt/server/var: Permission denied

```


It seems to me that my smb.conf is correct since I access to first level and it has worked for years. Moreover, I access on other shares on same server.
And permissions seem correct too...
It is not a client problem as it is a the same on various different clients.

I am lost.
Thanks all in advance.

PC

---

### Post by MAFoElffen on 2016-02-14
I have been helping a few others with recent Samba share permissions problems. The other users, all were new users trying to declare new shares.

I think your post is the key. Yours has been working and was established. You did not make any changes, but is now not working.

The common theme between these is that there is a parent directory with a share declaration, then a declaration on a sub-directory. I can confirm that this used to work on some of my past shares.

Could you please post a snippet of your share declarations from your smb.conf?

Then could you comment out the share declarations of your sub-directories... restart Samba, and see if your parent-share comes back up?

Then try the opposite... comment out your parent share declaration, un-comment out your child share declarations and see if they come up?

I'm thinking it's an ACL theme problem caused by a recent change with something... we just need to track down where and what that change was. I'm seeing this problem between threads of users. I'm thinking if ID'ed, then we can report to Launchpad as a bug, for them to confirm, and report as a bug upstream to Samba. I'm thinking that this should work as you had declared (has for me in the past), but now does not.

---

### Post by pcouderc on 2016-02-14
Thank you very much for your support.
I am ready to do anything to solve the problem (this is a very bad problem, glad this server is not public).

But I am not sure about your formulation of the problem.
I do not understand what you call "a declaration on sub directory". I have only 1 share :
```

[root]
    comment = root
    writable = yes
    public = yes
    path = /
    valid users = nous

```
So I do not understand what you suggest I comment.
And yes, I agree that there some ACL problem, maybe not in smaba but in some kind of firewall added recently (by whom..?!)

Please note too for completeness that I have dome other shares which work without problem such as :
```

[gestc]
    comment = gestc(S:)
    writable = yes
    public = yes
    path = /var/gestc/
    valid users = nous

```

---

### Post by darkod on 2016-02-14
There was a misunderstanding with the term "sub share" you used. He thought (and myself too), that you have shares defined into other shares.

Why would you need to share the whole / partition? There are many folders inside / that are not available to standard users (users that are not admins). I wouldn't be surprised if there are a lot permission denied messages.

There might have been also a change in samba/ubuntu that does not allow such practice.

Can you simply share only few specific folders? You say those shares are working fine.

PS. Also I wouldn't agree that permissions are correct, as you state in your first post. The root share is defined as writeable, but the permissions example you posted of /mnt/server/opt are rwxr-xr-x and the owner is root:root. That means only root user has write permission on the folder but in your share you say writeable = yes. How is that correct for users that connect over samba? That's a conflict of samba share permissions and linux/ACL permissions, no?

---

### Post by bab1 on 2016-02-14
> **darkod said:**
> There was a misunderstanding with the term "sub share" you used. He thought (and myself too), that you have shares defined into other shares.

Why would you need to share the whole / partition? There are many folders inside / that are not available to standard users (users that are not admins). I wouldn't be surprised if there are a lot permission denied messages.

There might have been also a change in samba/ubuntu that does not allow such practice.

Can you simply share only few specific folders? You say those shares are working fine.

PS. Also I wouldn't agree that permissions are correct, as you state in your first post. The root share is defined as writeable, but the permissions example you posted of /mnt/server/opt are rwxr-xr-x and the owner is root:root. That means only root user has write permission on the folder but in your share you say writeable = yes. How is that correct for users that connect over samba? That's a conflict of samba share permissions and linux/ACL permissions, no?

The problem is [this]("https://bugzilla.samba.org/show_bug.cgi?id=11647").  In my opinion you shouldn't be sharing the root of the file system anyway.

---

### Post by MAFoElffen on 2016-02-14
bab1 just messaged me and pointed out that bug report to me... That would explain what is going on with yours... and is not related to problems others are having with theirs.

---

### Post by pcouderc on 2016-02-14
> **bab1 said:**
> The problem is [this]("https://bugzilla.samba.org/show_bug.cgi?id=11647").  In my opinion you shouldn't be sharing the root of the file system anyway.

Thank you. As you say, the problem is this.
And I see that for this there is a workaround.

In the current case it is an administrative share on a private network, where the access with this share is very limited.
But I want to gently ask you : who are you to say that on my system I should not do something ...?

That was the "moral" point, but more technicallly :
If I ssh on this server as user "nous"and I am able to ls what I want, is it  normal that if I access by a samba share as the same "nous"user, I get less access...? 
I do not think so...

I thank you all for your help,[**[COLOR=#DD4814][B] MAFoElffen**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1044547") 	 , [**[COLOR=#000000]bab1[/COLOR]**]("http://ubuntuforums.org/member.php?u=582150"),[**[COLOR=#DD4814][B]darkod**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=946366") ....

> **darkod said:**
>  Also I wouldn't agree that permissions are correct, as you state in your first post. The root share is defined as writeable, but the permissions example you posted of /mnt/server/opt are rwxr-xr-x and the owner is root:root. That means only root user has write permission on the folder but in your share you say writeable = yes. How is that correct for users that connect over samba? That's a conflict of samba share permissions and linux/ACL permissions, no?

Mmm, I am sorry bur I see no contradiction on that :
The share is writeable, and I cannot write on /mnt/server/opt, but I may write on /mnt/server/opt/myopt if permissions allow it...

---

### Post by bab1 on 2016-02-14
> **pcouderc said:**
> Thank you. As you say, the problem is this.
And I see that for this there is a workaround.

In the current case it is an administrative share on a private network, where the access with this share is very limited.
But I want to gently ask you : who are you to say that on my system I should not do something ...?

I'm not telling what to do.  I'm giving you **my opinion**.
> 

That was the "moral" point, but more technicallly :
If I ssh on this server as user "nous"and I am able to ls what I want, is it  normal that if I access by a samba share as the same "nous"user, I get less access...? 
I do not think so...
This point means...what?

Most of what I respond with is for you and **future readers **of this thread.  Sharing the entire file system is a potential security risk.

---

### Post by pcouderc on 2016-02-15
> **bab1 said:**
> 

This point means...what?



Sorry of not being  clear.

I want to say it seems to me that "ls anything" should give the same result whether you connect as user X by ssh, whether you connect by samba as user X.

And you are right to warn : sharing the entire file system is a potential security risk.

---

