---
title: "OpenSSH + Putty Authentication"
date: 2012-03-07
forum: Server Platforms
---

### Post by bubylou on 2012-03-07
I have a nearly fresh install of ubuntu that i would like to be able to remote into from outside my local network. However i need to secure ssh  before i do so but i cannot get the key based authentication to work. I will be using putty as my primary tool for access. I have attempted to get this to work not to long ago but ran no matter what i did it refused to authenticate. I have yet to find a ny guide or forum post to help me solve this problem. If anyone else uses putty i would greatly appreciate if they could help me work this out. Also if needed i could use a linux mint machine to get the key and perhaps import it to putty if thats possible.

---

### Post by kevdog on 2012-03-07
Make sure password works first prior to using keys just to double check that everything is kosher with your server.  Putty and openssh keys are not interchangeable.  Its been a long time since I've used putty, however I believe you can import the private ssh key that was made on the server via openssh, and the puttykeygen program will convert it to a putty key.

---

### Post by bubylou on 2012-03-07
I haven't set up the key authentication yet and have access to it now. I have tried using the server generated keys before. I will give it another try.  I'm mainly looking more for some insight from putty users.

---

### Post by jerome1232 on 2012-03-07
In a very brief nutshell, you need to generate a key pair on the openssh server, then copy the private key to your client, use puttygen to import into putty format, then set putty to use the key under the ssh/authentication section.

```
#to generate key pair
ssh-keygen -t rsa
```

I would provide screenshots but I'm downloading a rather large file atm and can't log out. I'll try and grab some from my windows 8 vm to see if I can show it.

---

### Post by hawkmage on 2012-03-07
You don't have to generate the ssh keys on the server.  Putty should come with a utility puttygen which will allow you to generate the private/public ssh keys with it.  

Here is a decent how to on ssh key auth using putty: [http://www.howtoforge.com/ssh_key_based_logins_putty](http://www.howtoforge.com/ssh_key_based_logins_putty)

---

### Post by bubylou on 2012-03-07
I generated the key on the server. copied it to my machine, used puttygen to cahnge into a .ppk and set putty to use that file but it refuses it.

---

### Post by hawkmage on 2012-03-07
Did you add the id_rsa.pub that you generated on the server into the authorized_keys in the .ssh directory of the account you are trying to authenticate to?

---

### Post by jerome1232 on 2012-03-07
> **hawkmage said:**
> You don't have to generate the ssh keys on the server.  Putty should come with a utility puttygen which will allow you to generate the private/public ssh keys with it.  

Here is a decent how to on ssh key auth using putty: [http://www.howtoforge.com/ssh_key_based_logins_putty](http://www.howtoforge.com/ssh_key_based_logins_putty)

It works either way, you have to have the public key on the server and the private key on the client in the end.

At op, do you have an exact error message? you can output the errors to a log file in putty (under logging) and copy paste them here.

I may have missed a step, make sure to copy the public key into your authorized keys file on the server

```
cat *path/to/pub/key/file* >> ~/.ssh/authorized_keys
```

---

### Post by bubylou on 2012-03-07
Wow i had to laugh at myself for this one. The config file was looking for key in the authorized_keys file when i saved the keys in the authorized_keys2 since in using ssh-2 rsa. Well it works now thanks for all the help.

---

### Post by hawkmage on 2012-03-07
Either authorizes_keys or authorized_keys2 should work.

---

### Post by jerome1232 on 2012-03-07
Glad you got it working, enjoy, and don't forget to mark as solved.

---

### Post by bubylou on 2012-03-08
Will do, thanks again for the quick responses.

---

