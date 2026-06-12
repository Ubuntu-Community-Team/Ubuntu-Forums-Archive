---
title: "encfs: how to preserve ownership on a shared encrypted folder"
date: 2010-03-03
forum: Security
---

### Post by tanoloco on 2010-03-03
Hello,

I would like to create an encrypted folder which can be shared by users included in the users group.
To do so I used encfs:

```
cd somewhere
sudo mkdir encrypted visible
sudo chown root:users encrypted visible
sudo chmod 770 encrypted visible
encfs /somewhere/encrypted /somewhere/visible -o allow_other -o umask='007' -o uid='0'
```Now if a user (included in users) creates a new document in the visible folder, that will be
> -rwxrwx--- 1 root users 0 2010-03-02 14:19 new fileWhile I would like it to be 
> -rwxrwx--- 1 user users 0 2010-03-02 14:19 new file
Mounting encfs without the option uid='0' gives same results with only difference that instead of root the owner is the user who mounted encfs.

Also copying a file  owned by different user rather than root goes to the same:
for example having in my home  a file like
> -rwxr-x--- 1 me users 0 2010-03-02 14:30 myfile
 and trying to copy it to the encrypted  shared folder with
```

sudo cp -a -v ~/myfile /somewhere/visible

```will give something like
> *cp: failed to preserve ownership for `*~/myfile*': Operation **not* *permitted*And the copied file on the shared encrypted folder will be as usual:
> -rwxrwx--- 1 root users 0 2010-03-02 14:30 myfileIs there a way to mount encfs in order to preserve ownership?
Thank you in advance

---

### Post by tanoloco on 2010-05-07
I answer to myself to this my old question, as no one answered me! ::lolflag: 
Hoping that this could help someone else searching the same. ;)

The solution was (as in many cases) inside```
man encfs
```but it's hard sometimes to find something, if you don't know what you are looking for, even if you search in the right place! :)

This "something" was for me the encfs option```
--public
```Here is what I've done step by step:

**[goal] **
to share an encrypted mounted folder between members of the same group

**[how-to]**
**1.** set "user_allow_other" in /etc/fuse.conf. That permits the option allow_other in fusermount to work
```
echo "user_allow_other" | sudo tee -a /etc/fuse.conf
```**2.** create a new group called whatever and add to it all the users you want to access the encrypted folder.
My choice was to use the fuse group but you can create a new group. Just replace fuse with your group
```
sudo adduser fou fuse
```**3.** create the folders you need
```
cd somewhere
sudo mkdir encrypted visible
sudo chown root:fuse encrypted visible
sudo chmod 770 encrypted visible
```**4.** mount
```
sudo encfs /somewhere/encrypted /somewhere/visible -o umask='027' --public
```**5.** switch users
Now if you switch to another user member of the fuse group you can access the mounted encrypted folder and if you create new documents the ownership will be preserved this mens that documents created by userB will be owned by userB and not by userA who mounted the encrypted folder. Of course you can set another mask while mounting. Actually I haven't succeeded in setting the sticky bit on the mounted encfs folder and don't know if this is possible. Does anyone know it? I mean** [COLOR=DarkRed]is it possible to set the sticky bit on a mounted encfs folder?[/COLOR]**

**6**. unmount
```
sudo fusermount -u /somewhere/visible
```Note:
you need sudo to mount and to unmount in order it to work.

That's done. Hoping it can help. 

Cheers  ):P

---

### Post by oremusnix on 2010-08-18
Exactly what I was looking for! Brillant! Thank you!

---

### Post by iconoclast hero on 2011-04-18
Ok, I was following
[http://www.linuxpoweruser.com/?p=281](http://www.linuxpoweruser.com/?p=281)
and when I started transferring my file system with
```
sudo cp -Rax * /mnt/serverr
```as root, I got
```
cp: failed to preserve ownership for `/mnt/server/bin/stty': Invalid argument
cp: failed to preserve ownership for `/mnt/server/bin/chvt': Invalid argument
cp: failed to preserve ownership for `/mnt/server/bin/mv': Invalid argument
cp: failed to preserve ownership for `/mnt/server/bin/ps': Invalid argument
cp: failed to preserve ownership for /mnt/server/bin/netcat: Invalid argument
cp: failed to preserve ownership for `/mnt/server/bin/lsmod': Invalid argument
cp: failed to preserve ownership for `/mnt/server/bin/zfgrep': Invalid argument
.
.
.

```Should following this guide work?

---

