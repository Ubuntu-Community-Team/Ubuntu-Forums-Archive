---
title: "Prevent Users from reading other users email"
date: 2008-08-18
forum: Security
---

### Post by vorgusa on 2008-08-18
I was looking around the user folders and found the file for Evolution that has all your emails put into one file.  I was curious if I could create another user account that was not an admin and does not have Sudo abilities and view another user's email.  I was a bit surprised that I could... 

I was curious if there was a way to get Evolution to encrypt this file so that a user could not get into another user's mail?

---

### Post by spin2cool on 2008-08-18
Assuming that the other users don't have the admin/sudo password, you just need to change the permissions. 

First, use ls -l make sure the appropriate person owns the file/folder.  If not, do the following:

sudo chown username:username foldername

Then, change the permissions of that folder:
chmod go-rwx foldername

If the other users have root access, though, there's no way to stop them, short of creating a encrypted partition.  There are good instructions for this elsewhere on these forums and the web.

---

### Post by vorgusa on 2008-08-19
I thought about that, but the file I am talking about is inside one of the home folders, shouldn't this be done automatically?  Plus people like to keep their email fairly private, I would think someone out there would want it encrypted.

---

### Post by hyper_ch on 2008-08-19
I just made a little check and a lot of stuff is read-execute for group and world. However stuff like .mozilla has group and world permissions set to nothing... same goes for .kde4.... so I think the "sensitive" data is by default only readable by the current user.

---

### Post by Diggs808 on 2008-08-19
On this subject....

In 8.10 the ability to encrypt folders will be available....

[http://www.ubuntu.com/testing/intrepid/alpha4](http://www.ubuntu.com/testing/intrepid/alpha4)

---

### Post by Nepherte on 2008-08-19
I always chmod the user directories in home to user-only access (0700):
```
sudo chmod -R 0700 /home/user
```

I don't have a reason why multiple user on my computer would need access to eachother's home directory.

---

### Post by vorgusa on 2008-08-19
> **Diggs808 said:**
> On this subject....

In 8.10 the ability to encrypt folders will be available....

[http://www.ubuntu.com/testing/intrepid/alpha4](http://www.ubuntu.com/testing/intrepid/alpha4)

That is actually what made me think about looking into stuff like this.  I did notice that this was originally planned to just encrypt stuff in a specific folder in the Home folder, does anyone know if this could be easily changed to encrypt the whole Home folder?

I am not a paranoid person, just a curious one :-)

---

### Post by Titan8990 on 2008-08-19
> **Nepherte said:**
> I always chmod the user directories in home to user-only access (0700):
```
sudo chmod -R 0700 /home/user
```

I don't have a reason why multiple user on my computer would need access to eachother's home directory.


**You should not do this.** This will make for example your .dmrc file have permissions that it should not. If you run that command then everytime you log in it will complain that .dmrc does not have 644 permissions.

---

### Post by Nepherte on 2008-08-19
Doing this for over 2 years now, it never complained. Can you elaborate on this please? What does .dmrc do? Why are those permissions dangerous? Always willing to learn. The only what's in my .dmrc file is:
```
[Desktop]
Session=gnome
```
I just don't see why that can be dangerous.

---

### Post by Titan8990 on 2008-08-19
It's for custom user paths. You can view your current path with this command:

echo $PATH

Now, I don't know why it specifically wants 644 permissions but that is what it says whenever the permissions are changed.

Have you never received this error? I have had both a Fedora install and a Ubuntu install that has complained about incorrect permissions on the .dmrc file.

---

### Post by Nepherte on 2008-08-19
> **Titan8990 said:**
> 
Have you never received this error? I have had both a Fedora install and a Ubuntu install that has complained about incorrect permissions on the .dmrc file.
Never.

---

### Post by Titan8990 on 2008-08-20
Maybe it's issue is with other people being able to write to it. Try giving it 664 permissions and see if it gives you the error. Either way I personally would not like making my entire home directory executable. Maybe chmod -R 600 ~?

---

### Post by SEMW on 2008-08-22
> **Titan8990 said:**
> Either way I personally would not like making my entire home directory executable. Maybe chmod -R 600 ~?
Wouldn't that make your entire home directory unreadable?  I've always understood that directories have to have both read and execute flags set before you can access them.  Doesn't make much sense, but oh well.  

I think to get what Nepherte's looking for without making everything executable you'd have to do ```
chmod -R u+rwX,go-rwx ~
``` The capital X apparently sets the executable flag for directories and files which had it set already, but not otherwise.  

(And possibly fix permissions on .dmrc afterwards, as you say.)

---

### Post by Nepherte on 2008-08-22
Huh? Do I have a problem? Everything works for me here with 0700 permissions for /home/<username> :p. I'm not sure whether the topic starter's problem is solved though.

---

### Post by SEMW on 2008-08-22
> **Nepherte said:**
> Huh? Do I have a problem? Everything works for me here with 0700 permissions for /home/<username> :p. I'm not sure whether the topic starter's problem is solved though.

No, you're fine -- I was saying I didn't think Titan8990's recommendation of 0**6**00 permissions would work.  S/he made that suggestion because s/he didn't think that it would be a good idea to have every single file in your home directory executable.  Personally, I can't say that bothers me -- any new files you download will still not be initially executable, so there aren't really any security considerations -- but if it did bother someone, my way would not give any files executable permissions that didn't already have them.  (Of course, if your home folder is already completely 0700, then it just won't do anything).

---

