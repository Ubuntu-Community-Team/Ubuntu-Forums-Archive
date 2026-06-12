---
title: "Forgive the noob pls"
date: 2010-10-28
forum: Security
---

### Post by Stupid_newbie on 2010-10-28
I am playing around with Ubuntu and am having a slight issue with user permissions. I have 3 others who will have access to my machine via lan/network as it has a lot of storage for them.

I am trying to remember/use what I learned in college but that was 10 years ago and I drank way to much to remember..... :)

Here is my concern.

1.) The User Jennifer, her home Directory is /home/jennifer. If I SSH into my box, she has permissions to go where ever the hell she wants to.

 I would like to restrict her movement to the directory she has and that's it... I have tried 
```
chmod 700 /home/
```
once I did this, no user had access to the /home folder?!?!?. I quicky retraced my steps. I then tried:
```
chmod 700 /home/jennifer
```
I then was able to move around all over the place.

If there was a way to confine a person to the home folder supplied, that would be great.

2.)I have another user "stacy". I have set her home directory to: /var/www (as you can guess she is my web admin) and yet, she is able to move about the system to wherever she feels like it. 

I'm sure i'm doing something completely backwards.. I have looked all over, can anyone help me? 

thanks in advance

Stupid Newbie

---

### Post by CharlesA on 2010-10-28
Changing permissions to 700 only lets them full control of anything that they are the owner of. It won't prevent them from accessing other parts of the system.

How are they connecting, SSH?

---

### Post by SeijiSensei on 2010-10-28
If a user can log into the box via SSH, then she'll have all the permissions she'd have as if she logged in from the console.  By default users can browse most of the operating system, though they can only create or modify files for which they have permissions.  Even though jennifer can browse /usr/bin, she can't do anything to the binaries therein.  In general users can create and modify files in their /home directories and ones they write to /tmp.  Using "chmod 0700 /home/jennifer" as you did is a good way to keep Stacy from seeing Jennifer's files.  But you won't be able to keep both Stacy and Jennifer from listing the contents of /usr/bin.  

I think you need to reconsider what your purposes are here.  Perhaps what you really want is a file-sharing solution using Samba for Windows clients and NFS for *nix clients.

---

### Post by FuturePilot on 2010-10-29
> **SeijiSensei said:**
> If a user can log into the box via SSH, then she'll have all the permissions she'd have as if she logged in from the console.  By default users can browse most of the operating system, though they can only create or modify files for which they have permissions.  Even though jennifer can browse /usr/bin, she can't do anything to the binaries therein.  In general users can create and modify files in their /home directories and ones they write to /tmp.  Using "chmod 0700 /home/jennifer" as you did is a good way to keep Stacy from seeing Jennifer's files.  But you won't be able to keep both Stacy and Jennifer from listing the contents of /usr/bin. 

I think you need to reconsider what your purposes are here. Perhaps what you really want is a file-sharing solution using Samba for Windows clients and NFS for *nix clients.

This

---

### Post by Stupid_newbie on 2010-10-29
> **SeijiSensei said:**
>   Using "chmod 0700 /home/jennifer" as you did is a good way to keep Stacy from seeing Jennifer's files.  But you won't be able to keep both Stacy and Jennifer from listing the contents of /usr/bin.  
I think you need to reconsider what your purposes are here.  Perhaps what you really want is a file-sharing solution using Samba for Windows clients and NFS for *nix clients.

Ok, I get it now, i use samba sand cups for file amdbprinter sharing already and have found it works great. I know for a fact that Jennifer will never use ssh so I'll stop worrying about that. 

I'll then focus on Stacy, I want to keep her in /var/www and no lower is there a way for her to only access that folder?

---

### Post by CharlesA on 2010-10-29
Are you allowing Stacy to access to that folder with Samba or with something like FTP?

That would help determine what method you can use to secure it.

---

### Post by SeijiSensei on 2010-10-29
/var/www is a bit tricky since it's owned by root and needs to be readable by the "www-user" account that the Apache webserver runs under.

Here are a couple of alternatives:

1)  Instead of using /var/www as the DirectoryRoot for your website, rewrite the <VirtualHost> declaration to use something like /home/stacy/website.  Then she can place files in a location she can see easily over the network.  You'll need to change a few permissions for this to work:

```

chmod 0711 /home/stacy
mkdir -p /home/stacy/website
chmod 0755 /home/stacy/website

```

2)  Create a [website] share with Samba that Stacy can mount with a couple of important features:

```

[website]
path = /var/www
force user = root
force group = www-data
browseable = no
writable = yes
valid users = stacy
create mode = 0644
directory mode = 0755

```

This lets Stacy mount \\server\website with her credentials and write files in /var/www, but all the files she saves will be owned by root with group www-data.

---

### Post by CharlesA on 2010-10-29
Definite +1 to using a virtualhost. Makes it easier to deal with and you can run muliple sites from the same server.

---

### Post by t.rei on 2010-10-29
Oh dear, I remember being worried about "user lock ins" while back when I was setting up a server for a university project with about 20 ssh/ftw/personal-website users.

I do remember that this was really easy, once I figured it out... something like just editing a single file and setting a user's root or something like that... Maybe this comment pushes someone else in the direction that I should be thinking if I weren't such a tired old fart.

---

### Post by Stupid_newbie on 2010-10-31
I'm going to play it safe and create a Link to var/www in Stacy's home folder, hopefully that will make everyting easy. I can trust her and Im sure she wont screw around with ssh... Thanks all for your suggestions. Once again the Forum has saved the day!!! :)

---

### Post by SeijiSensei on 2010-11-01
> **Stupid_newbie said:**
> I'm going to play it safe and create a Link to var/www in Stacy's home folder, hopefully that will make everyting easy. I can trust her and Im sure she wont screw around with ssh... Thanks all for your suggestions. Once again the Forum has saved the day!!! :)

Just make sure she has read/write access to /var/www.

---

