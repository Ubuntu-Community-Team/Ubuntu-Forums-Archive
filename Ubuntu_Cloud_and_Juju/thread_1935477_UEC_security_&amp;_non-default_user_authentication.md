---
title: "UEC security &amp; non-default user authentication"
date: 2012-03-04
forum: Ubuntu Cloud and Juju
---

### Post by TuxVinyards on 2012-03-04
Trying to improve security on an AWS build of 11.10 and avoid the frequently discussed  torrent of brute-force against default users and default ports eg root on port  22  -

Moving to a non-standard SSH port by editing /etc/ssh/sshd_config is straight forward enough.

Ubuntu doesn't permit root login and UEC's don't give desktop recovery  mode as a by-pass, so that covers that. At least I believe it does.

Creating a new admin user and removing the default one of 'ubuntu' seems  to be a different story. This just doesn't seem to be do-able. There  seems to be a sneaky 'belt & braces' method used here which I can't  fathom out. The only reference that I can find is in /etc/sudoers.d in  the config 90-cloudimg-ubuntu. 

With the default user 'ubuntu' everything works without a snag. However, I feel almost as if I'm trying to touch things that I shouldn't because I just can't get my new admin user to https logon (with webmin) or to ssh. 

Also, I don't know if these are connected issues or not (??) but I can't get Webmin/Virtualmin to use a non-standard port  either.  It is documented that you don't have to stick with :10000 (don't know how many people use Webmin). 

[http://www.virtualmin.com/node/6148](http://www.virtualmin.com/node/6148)

The upshot of this is that I find myself stuck with minded people having a head start on brute-forcing  my https logon because the user 'ubuntu' seems almost hard-wired into the distro  and is probably the next most popular user name to 'root'.

There don't seem to be any solutions to this anywhere. Does this mean it's completely  obvious but I just can't see it or is it something else?

---

### Post by Dangertux on 2012-03-04
I'm not terribly experienced with UEC however I would wager some of the typical methods would work.

Have you simply tried to userdel the ubuntu user. Of course making sure you new admin user is a sudoer.

Note : you can insure your new user is an admin by doing the following.

```

sudo usermod -G admin youradminusername

```


```

sudo userdel ubuntu

```Alternatively... If you can't delete it (I wouldn't see why not) you could always just lock the account, again making sure you new user is a sudoer.

```

sudo usermod -L ubuntu

```Third if none of this works remove them from the admin group

```

sudo usermod -G somenonadmingroup ubuntu

```Alternatively if none of these work some good old brute force protection methods like using keys in conjunction with iptables rate limiting (won't stop a brute force but will make it so slow as to be ineffective).

Also... You could probably rename the ubuntu user.

```

sudo usermod -l newusername ubuntu

```Should get you where you want to be.

I'm not too sure about the webmin stuff as I don't use it, but I know many people on here do so I'm sure you'll get an answer to that soon.

Hope this helps.

---

### Post by TuxVinyards on 2012-03-04
Thanks DT.  Excellent check-list.  I am working through it now and have found a couple of anomalies ... Could be the 'something obvious'.

"Have you simply tried to userdel the ubuntu user. Of course making sure you new admin user is a sudoer."  

This is probably the hub of the problem.  Need to get the new user to be a Sudoer first.  

Thought about the third solution, rename  the user 'ubuntu' but have been worried there might be a daemon or something expecting this user to be there.

Anyway, progress made. Will post up later. : )


UPDATE

Solved (kind of):

@dangertux - Sorry, you lose your wager. It's not a case of of simple typo at the CLI. And it's not an Ubuntu specific problem either.  On the AWS forum, I took 'ubuntu' out of the search parameters and found a post relating to this on the Amazon/CentOS distro.

It's to do with the AWS set-up.  There's yet another file to one that I mentioned previously: /etc/cloud/cloud.cfg which plays a role too.  Also you need to manually set up the SSH keys for each extra user. The AWS RAM disk (which does the boot-config) will set up only the default users for you. This is what I meant 'belt and braces' in my first post.

I knew that I had set up a new user and it was in the admin group but when I ran through some of DT's ideas the user settings (following  a re-boot probably) had all gone - the user *didn't* exist when tried usermod ... but then *did* exist when I tried useradd.  I had to use 'rm' with -Rf options to get the home dir to delete. When I finally managed to add the user again I found 'id' wouldn't list a UID. (& just for extra fun, if you turn on user name REGEX filtering in /etc/adduser.conf no usernames will pass at all!)

So, long story short. And for the benefit of anyone else with similar probs. Changing UEC default user just isn't worth the aggro.  I am sticking to the default user but on a non-default port and only having SSH key access, no logons or https. I am removing Virtualmin/WebMin. 

Couple of links here for reading. I won't be following them. I am sure there must be other hidden catches. Just changing the default SSH port is easy and works.

[http://blog.sofasurfer.org/2011/07/16/ubuntu-ec2-add-new-admin-user/](http://blog.sofasurfer.org/2011/07/16/ubuntu-ec2-add-new-admin-user/)

[https://forums.aws.amazon.com/thread.jspa?messageID=238129&#238129](https://forums.aws.amazon.com/thread.jspa?messageID=238129&#238129)   (Amazon/CentOS but same prob as with Ubuntu)

Can't say that I am entirely happy (don't like to see insecure servers out there) but I 'm going to take the line of least resistance, going with the flow on this one ....

---

### Post by TuxVinyards on 2012-03-14
Bit more info on this one -

Seems that 'cloudinit' is an Ubuntu replacement for 'initrd' the Grub2 style boot ramdisk.

Even AWS / Amazon use cloudinit for booting their own CentOS distro.

(quite a few postings around on initrd)

Not the full answer but time to mark this 'solved' now.

8)

---

