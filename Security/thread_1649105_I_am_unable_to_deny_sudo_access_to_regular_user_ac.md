---
title: "I am unable to deny sudo access to regular user account."
date: 2010-12-19
forum: Security
---

### Post by me12345 on 2010-12-19
Hi,
 
I'm having a security problem with my ubuntu laptop. I made a Desktop User account. When I went on that account, it allowed me to execute sudo as if I was an administrator. I don't know what might be causing this. I do have ufw set up and blocking incoming connections. Do you guys know what might be at the root of this?
 
Also, when I used sudo from the user account (which I shouldn't have been able to do), I provided the password for my admin account.

---

### Post by slooow on 2010-12-19
The quick and dirty method would be to open /etc/group with a text-editor and delete that user from the admin group.
```
sudo gedit /etc/group
```

---

### Post by me12345 on 2010-12-19
Thanks for the advice! I opened up the /etc/group file. Only the administrator is in the admin group. It says:
 
```
admin:x:119:william
```
 
where "william" is the administrator account. I would copy and paste the entire file, but don't want to open a browser yet in my ubunu laptop because I am anxious about security. Before I connected it to the interned, I configured ufw to block incoming connections. I only connected it to the internet to use the Ubuntu Software Center to download java and netbeans, and to do sudo apt-get update, and sudo apt-get install ia32-libs. Those downloads took a long time, because internet was slow. I had a very strange problem with the first user account I made, so I deleted it and created another one - this other one is the one I am having the current permissions problems with.
 
The first user account said - "couldn't edit ICEauthority file". Then it said "sanity check failed." Then it hung and wouldn't load. I gave up and deleted it and made another account.
 
So, it looks like the the account in question is not included within the admin group. It's in the adm group, but from what I know, it's supposed to be there. What would you suggest at this point?

---

### Post by me12345 on 2010-12-19
there is supposed to be a colon and then an x where the smiley face is

---

### Post by CharlesA on 2010-12-19
> **me12345 said:**
> there is supposed to be a colon and then an x where the smiley face is
Added code tags to your post. :)

What happens when they try to use sudo ?

---

### Post by me12345 on 2010-12-19
OK, when I go to system -> administration -> users and groups, and ask to make a systemwide change (such as changing my user account, from that user account, to an admin account), it asks me for the administrators password. If I don't enter password for 15 seconds, it sends me strange message and blocks me. If I type in the password before 15 seconds, it gives me full admin permissions and lets me change myself from a desktop user to an administrator.
 
Sudo, from the command line, blocks me, as it should.

---

### Post by me12345 on 2010-12-19
it looks like i misinterpreted my problem, the sudo is only broken from the GUI side of things.

---

### Post by CharlesA on 2010-12-19
> **me12345 said:**
> it looks like i misinterpreted my problem, the sudo is only broken from the GUI side of things.
Try this:

Hit Alt+F2 and type this:

```
gksu gedit
```

---

### Post by me12345 on 2010-12-19
OK, I did it from the user account. It prompted for password. If I type in the user password, it says sudo denied me. If I type in admin password, it says "wrong password, try again". Either way, it denies me. However "System -> Administration -> Users and Groups" does its own thing still.

---

### Post by CharlesA on 2010-12-19
I think that's because they can manage which groups they are in. I'm not sure tho.

---

### Post by me12345 on 2010-12-19
Hmmm....
 
It does force me to supply the administrator password, even from the user account. Maybe that is just ubuntu's way of enforcing security for the users and groups changing app?
 
Is there a way I can harden the OS so that users cannot manage which groups they are in? Group management, btw, is totally unsecured from the user account on my box.
 
Does other people's ubuntu do this? Does it let others supply an admin password from a user account?
 
And thanks for the code tags and the help.

---

