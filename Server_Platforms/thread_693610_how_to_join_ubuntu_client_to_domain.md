---
title: "how to join ubuntu client to domain?"
date: 2008-02-11
forum: Server Platforms
---

### Post by beaker15 on 2008-02-11
Hi, 
I have an Ubuntu server with samba domain controller running a small network of about 8 Windows XP machines with no problem. Now I want to join an ubuntu client to the domain but I'm not sure how to go about it. I'm thinking how Windows has the splash screen at startup where you enter you're username and password but i'm guessing linux doesn't have one one of these or does it? How can i log in to the domain?

---

### Post by astrotech226 on 2008-02-11
I don't know if there is a graphical way to do this, but it's not too bad on the commandline.  You need to edit your /etc/samba/smb.conf file and set the following:

```
   workgroup = YOURDOMAINNAME
   security = domain
```

Then you need to actually join the domain.

```
net join -W YOURDOMAINNAME -U administrator
```

It should ask for the administrator password.  If everything is set up correctly, your computer is now joined to the domain!

---

### Post by beaker15 on 2008-02-13
hmm...apparantly everything is not setup correctly, I get the message 
[I]
[FONT="Arial"]colin@cycle-12:~$ sudo net join -W CYSOL -U frc
[sudo] password for colin:
Connection failed: NT_STATUS_LOGON_FAILURE
Password:
Could not connect to server SRV-01
The username or password was not correct.
Connection failed: NT_STATUS_LOGON_FAILURE[/FONT]
[/I]

My XP machines also can't connect so I think I'll post a new thread. thanks for answering the question anyway

---

### Post by astrotech226 on 2008-02-13
You might also need to specify the primary domain controller with the "-S" option.  The user needs to be an administrator that is able to add machines to the domain.  You used "frc" and that might not work.  Try this:

```
sudo net join -W CYSOL -S YOURPDC -U administrator
```

---

### Post by harvin on 2008-02-29
Hi,

I tried the above methods to join to a Windows domain but I get an error 'cannot join as standalone machine'. 

any ideas what is wrong here ?

---

### Post by astrotech226 on 2008-02-29
> **harvin said:**
> I tried the above methods to join to a Windows domain but I get an error 'cannot join as standalone machine'. 

Can you post your "net join" command?

---

### Post by harvin on 2008-02-29
sudo net join -W harvinz.com -U administrator

---

### Post by astrotech226 on 2008-02-29
> **harvin said:**
> sudo net join -W harvinz.com -U administrator

Is your Windows domain really harvinz.com?  It's usually single words like "harvinz".

If you go to a windows computer and go to log in, you'll have user, password and domain fields.  In the domain field, does it simply say "harvinz"?  If so, change your line above to:

```
sudo net join -W harvinz -U administrator
```

---

### Post by harvin on 2008-02-29
Ok, I tried harvinz but i still get the same error 'cannot join as standalone machine'.

---

### Post by astrotech226 on 2008-02-29
OK.  There's two lines in your /etc/samba/smb.conf file that need to be set.  Open it up and make sure:

```
workgroup = HARVINZ
security = domain
```

But this is assuming your domain is truly "harvinz".

---

### Post by naja74 on 2008-04-24
I get the same error. Any news?

---

### Post by ebarriosjr on 2008-06-02
I get the same error. Any news? please help me!!!!

---

### Post by naja74 on 2008-06-03
I was able to get it working by following this...

[http://www.bauer-power.net/2008/05/join-ubuntu-804-to-windows-domain.html]("http://www.bauer-power.net/2008/05/join-ubuntu-804-to-windows-domain.html")

---

