---
title: "Samba Auth against Active Directory on 8.04"
date: 2008-07-30
forum: Server Platforms
---

### Post by Cubus on 2008-07-30
Hi Fellows,
the past days I have been searching the net for a good working way to set up a replacement for a windows fileserver with hardy.

I'd like to authenticate against the AD user database.

I found serveral ways, some use Kerberos, some suggest to try likewise-open.

The ones using Kerberos seam not to work on hardy, as far as I see in the forums here.

I tried likewise-open and was able to add the server to the AD but the service regularly crashed and when loggin on to the console I then got "Error" as a message, when using my local user-account.

Can someone please point me to a tutorial or howto that works with hardy?

Thanks in advance :)

---

### Post by Cubus on 2008-07-31
Well, if someone told me, this is not possible right now, I'd be fine aswell...

---

### Post by TreeFinger on 2008-07-31
I think this will help you.

[http://ubuntuforums.org/showthread.php?t=91510](http://ubuntuforums.org/showthread.php?t=91510)

If not, sorry!

---

### Post by likeWiseGuy on 2008-10-02
> **Cubus said:**
> Well, if someone told me, this is not possible right now, I'd be fine aswell...

Hi, Cubus.

Likewise Open appears to be the right solution for your Linux & Active Directory integration. I would suggest trying out the solution and see how it goes. If at any point you need some assistance or more information, post a message - I'll do my best helping you out along the way!

I'm sure you'll have a positive experience.

---

### Post by Cubus on 2008-10-06
Hi likeWiseGuy,
I did try likewise, and, sometimes it did work. Often tho, I got error messages and had to reboot the system. At one point I removed Likewise and lost all access to my box after that.

That was with 8.04, I'll try again with 8.04.1 once I can free up some time :)

Thanks for your support.

---

### Post by kpm on 2008-10-20
Hi, any luck getting Likewise-Open and Samba working??

It seems everyone posting in the forums can enter a Windows Active Directory domain using Likewise-Open, but that is about the extent of it...  The smb.conf file listed shares do not allow anyone, not even root to gain access.  I can't even access the shared directory as root.  When I navigate to \\serverName\var\share on the server I am prompted for a user name and password, but always get a permission denial... even as root.

---

### Post by jamesrfla on 2008-10-20
Maybe this might help
[http://ubuntuforums.org/showthread.php?t=953629](http://ubuntuforums.org/showthread.php?t=953629)
[http://ubuntuforums.org/showthread.php?t=933092](http://ubuntuforums.org/showthread.php?t=933092)
[http://ubuntuforums.org/showthread.php?t=923404](http://ubuntuforums.org/showthread.php?t=923404)

---

