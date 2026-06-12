---
title: "Active Directory, Likewise and Samba"
date: 2008-04-21
forum: Server Platforms
---

### Post by benne on 2008-04-21
Hello.

I have a Ubuntu 7.10 server and i am using likewise-open to have it inside a Microsoft Active Directory domain to benefit from the directory server. 

That part works fine. But how do I make samba also use Acitve Directory to authenticate users? 

E.g. i want to share /home/%AD-user and make it possible for poeple to mount their home directories through samba and use the AD credidentials for that.

I would also like to autmoaticly mount the users networks drives off the windows server when they log in, like i manually do with "smbmount //server.domain.local/user$ mount-point"

---

### Post by jdieg on 2008-05-06
I am looking for this same information.

Have you figured it out yet?

---

### Post by christianxxx on 2008-05-06
Have a look at this.
Although the guide is written for LDAP/SAMBA in a pure linux environment, I suspect much of the authentication can be transferred to a Windows based AD. Might even be possible to use its solution for mounting home directories.

[http://ubuntuforums.org/showthread.php?t=640760]("http://ubuntuforums.org/showthread.php?t=640760")

---

### Post by jdieg on 2008-05-06
Thanks, Christian.
That info is VERY USEFUL.
But, It seems that the likewise-open agent has all of the info necessary to authenticate a user without the need to set up and configure all of that openLDAP and SAMBA LDAP stuff.
likewise can authenticate me at logon, so it seems that it could help SAMBA to authenticate a user trying to connect to a share.
The likewise-open documentation vaguely mentions that it is "universal", but doesn't give a lot of examples.
Does anyone know of a way to let SAMBA see me as DOMAIN\username and authenticate me against likewise?
Thanks for any help you can give me.

---

### Post by christianxxx on 2008-05-06
Hmm... Samba is much more well-documented, and you'll easily find lots of posts concerning samba. I'd be more than surprised if it was impossible, what you want to achieve.
I've seen some traces on google of discussions regarding the bundling of samba and likewise-open, so at least the developers seem to have this in mind, which would certainly make your setup possible.

I've only read about this, and will try to implement openldap and nfs in my home network, but that won't happen until autumn (yeah, let's get just a little tan, right?).
And even then, I'll wisely keep windows out of the game. So, even though I can't help you further, happy hunting for solutions!

---

### Post by el.b00ty on 2008-05-14
Has anyone been able to make this work yet?  I found some mailing lists talking about how there was something coming in Samba 3.2 that would make this work (I guess Likewise more or less replaces Winbind?), but don't totally understand how all this works so maybe that's not accurate.  In any case, it seems like this shouldn't be that big of a deal - I'm surprised no one has figured it out yet...

---

### Post by jdieg on 2008-05-14
The more I look into this, it seems like pam-mount is a possible solution.
I haven't been able to work with it because I have other fires burning, but what I have seen makes sense.
Has anybody used pam-mount for this type of home drive mapping?
If so, can you help by giving us some config examples?

---

### Post by ic3000 on 2008-06-29
Anyone got this working?

I'm also trying to find a way to mount user documents folder on a w2k3 server on login with ubuntu clients using likewise-open!

Thanks!

---

### Post by ic3000 on 2008-06-30
On a blog i found a link to a possible solution using pam-mount in Fedora!

See point 2 on this page:

[http://forums.fedoraforum.org/showthread.php?t=92804](http://forums.fedoraforum.org/showthread.php?t=92804)

I'm trying to make things work as on that guide but it seems that on ubuntu the files used by pam-mount are not the same as in red-hat!

Anyone knows how o adapt this guide to ubuntu? Can this be a solution to our problem here?

Thanks once more.

---

### Post by ic3000 on 2008-07-01
Sory for bumping this topic again but i have posted on other topics that talk about this subject, asking for about the same thing, that i really think that this could be a very good solution to bring users to linux and until now i havent even one reply!

Is it not possible to do so?

Is it a tabu subject reserved to the comercial support from canonical?

Thanks once again!

---

### Post by scurry7 on 2008-07-02
I am also trying to do this, and not quite there yet.  [This link]("http://devarthur.blogspot.com/2008/05/integrating-ubuntu-hardy-heron-804-with.html") has helped me to get close, but I just cant seem to get it working (the shares are there but I get an access denied for permissions).. Maybe you will have better luck.  
PS follow the link in step 3 (that is the actual smb share stuff)

Post if you figure it out...

this like may interest you also:
[http://www.likewisesoftware.com/resources/user_documentation/Likewise-Samba-Guide.pdf](http://www.likewisesoftware.com/resources/user_documentation/Likewise-Samba-Guide.pdf)

---

### Post by ic3000 on 2008-07-02
Thanks scurry7!

I have a look at the sites you mentioned but i dont think that this is what i'm trying to setup!

I'm trying to get the linux clients from a AD domain to mount or access user own shares like there documents or windows home folder.

Thanks for your reply once again!

---

### Post by scurry7 on 2008-07-02
My apologies, I'm was obviously unclear on what you were looking for....

---

### Post by atimike on 2008-07-14
Thanks for the data - got Samba working perfectly now...
:popcorn:

---

### Post by endfx on 2008-07-16
I actually got this working. I'm using Ubuntu 8.04
I modified the following guide:
[http://chrplunk.blogspot.com/2008/06/allow-windows-clients-in-active.html](http://chrplunk.blogspot.com/2008/06/allow-windows-clients-in-active.html)

Here are the steps I took. If you need more description, please see the link above:

1) $> sudo apt-get install samba winbind
Though you probably have samba installed already.

2) 
$> cd /usr/lib/samba/idmap/
You might have to make the idmap directory
$> sudo ln -s /usr/lib/likewise-open/idmap/lwopen.so

3) Now modify the samba config file, so it contains the following (in addition to whatever else you want)

$> vi /etc/samba/smb.conf
security = ads
workgroup = enter workgroup from /etc/samba/lwiauthd.conf here
realm = enter realm from /etc/samba/lwiauthd.conf here
idmap backend = lwopen
idmap uid = 50-9999999999
idmap gid = 50-9999999999


4)
mv /var/lib/samba/secrets.tdb /var/lib/samba/secrets.tdb.orig
ln –s /etc/samba/secrets.tdb /var/lib/samba/secrets.tdb

5)
$> sudo /etc/init.d/samba restart
$> sudo /etc/init.d/winbind restart

Now, go to a windows box and give it a shot.

Does this help anybody?

---

