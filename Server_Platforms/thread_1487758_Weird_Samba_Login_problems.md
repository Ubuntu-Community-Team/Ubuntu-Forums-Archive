---
title: "Weird Samba Login problems"
date: 2010-05-19
forum: Server Platforms
---

### Post by 1serveyou on 2010-05-19
Hi everyone, I'm having a weird problem, when I'm on my windows machine in my network folder I can connect to my Music folder, video folder, and picture folder. It does ask me for a login, but as long as I put just about any name/password it works, although it should only work with a couple of names. I forget what names I put it in that it actually failed, they may have even had symbols in them.

The other problem is, when I use "map a network drive" it asks me for a login, but no login works. It just keeps on coming up with the same window "name of computer"/"user name logged in" and then place to enter in login information.

Any help would greatly be appreciated.

EDIT: Sorry, this is with 9.04, and using samba4.

---

### Post by jd65pl on 2010-05-19
Do you have a samba user for the user you are trying to log in as?

What is the output of
```
sudo pdbedit -w -L | awk -F: '{print $1}'
```

Do you have homes set up or do you specify the directory on the server?
```
grep -A+30 homes /etc/samba/smb.conf
```

---

### Post by 1serveyou on 2010-05-19
> **jd65pl said:**
> Do you have a samba user for the user you are trying to log in as?

What is the output of
```
sudo pdbedit -w -L | awk -F: '{print $1}'
```Do you have homes set up or do you specify the directory on the server?
```
grep -A+30 homes /etc/samba/smb.conf
```

Thanks! I'll try tonight!

---

### Post by 1serveyou on 2010-05-19
> **jd65pl said:**
> Do you have a samba user for the user you are trying to log in as?

What is the output of
```
sudo pdbedit -w -L | awk -F: '{print $1}'
```Do you have homes set up or do you specify the directory on the server?
```
grep -A+30 homes /etc/samba/smb.conf
```


When I try 
```
sudo pdbedit -w -L | awk -F: '{print $1}'
```
It gives me an bash error for awk, and if I take out the awk, then it prints
- my 4 users, there number, then a colon with a bunch of x's after then another colon with a bunch of letters(I'm guessing hidden passwords)


And ```
grep -A+30 homes /etc/samba/smb.conf
```
Doesn't print anything, and I honestly can't remember if I did setup homes on this server, as I set 2 of them up around the same time, and both are the first servers I've ever set up.

---

### Post by jd65pl on 2010-05-20
Are you copying any pasting the awk line or typing it out? There should be no space between "-F" and ":". The line below will put a copy of your samba config in your home directory can you attach it to here? (Use the "Manage Attachments" feature in "Additional Options" below the message input when you reply.


```
cat /etc/samba/smb.conf > ~/smb.txt
```

---

### Post by 1serveyou on 2010-05-21
> **jd65pl said:**
> Are you copying any pasting the awk line or typing it out? There should be no space between "-F" and ":". The line below will put a copy of your samba config in your home directory can you attach it to here? (Use the "Manage Attachments" feature in "Additional Options" below the message input when you reply.


```
cat /etc/samba/smb.conf > ~/smb.txt
```

Sorry about that, I didn't get a chance till last night, but I couldn't get a version that I could copy and paste, as I don't have my home folders setup to be shared. And then when I tried to sudo, I couldn't remember my password I had changed it probably about a month ago as I was going to have someone take a look at it and didn't want them knowing my su password. So now I have to find that out, before I can do anything else I believe, unless I can connect with a ubuntu desktop to it.

---

### Post by X1R1 on 2010-05-21
Im having a similar issue but a bit more complicated, everytime a user that doesnt have a home directory created logs in I have a shell script that creates it and assigns permissions automatically.

I can see the script works because I see the folders created and with the correct permissions. Nevertheless, the user cant connect to the folder, windows complains it cant find the route to access the resource (or something like that, cant remember exact error)

I also manually created a folder that is shared will all domain users and no restrictions at all, weird thing is, it prompts for a username and password, and it doesnt matter what you input here, it wont enter the folder, just keeps prompting for the same info.

This problem is happening on a work environment with active directory integration.

hope someone can help :D

regards

---

### Post by albinootje on 2010-05-21
> **1serveyou said:**
> 
EDIT: Sorry, this is with 9.04, and using samba4.

You do realize that Samba 4 is not yet officially out ?

The version that Ubuntu offers is 4.0.0~alpha6-1ubuntu1

And [http://en.wikipedia.org/wiki/Samba_%28software%29](http://en.wikipedia.org/wiki/Samba_%28software%29) says :
> 
Version 4.0 is planned as a major rewrite that will enable Samba to be an Active Directory domain controller. After three years of development, the first technical preview (4.0.0TP1) was released in January 2006.[15]  Subsequently, new previews and then alphas have followed regularly. The most recent version is 4.0.0-alpha11, released on 10 January 2010.


---

### Post by 1serveyou on 2010-05-22
> **albinootje said:**
> You do realize that Samba 4 is not yet officially out ?

The version that Ubuntu offers is 4.0.0~alpha6-1ubuntu1

And [http://en.wikipedia.org/wiki/Samba_%28software%29](http://en.wikipedia.org/wiki/Samba_%28software%29) says :

Yes, but honestly when I set it up, I couldn't figure out how to get 3 installed :(

---

### Post by albinootje on 2010-05-22
> **1serveyou said:**
> Yes, but honestly when I set it up, I couldn't figure out how to get 3 installed :(

You could backup your /etc/samba/ (Or is it perhaps /etc/samba4 ?),
and then purge the samba4 package(s) with synaptic package manager
or apt-get.

And then install samba 3, which should be as easy as :
```
 sudo apt-get install samba 
```

GL!

---

