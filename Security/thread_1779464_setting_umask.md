---
title: "setting umask"
date: 2011-06-10
forum: Security
---

### Post by ClientAlive on 2011-06-10
Hi,

I'm running Ubuntu 10.04 LTS and I was wondering if there is a way to change the default umask _only for a specific directory and all its subdirectories and files._

Thanks in advance for your help. Thanks for taking the time to read my question.


Jake

---

### Post by nrundy on 2011-06-10
I think all you need to do is right-click the folder and select the Permissions tab. There's a trick for making the Permissions tab display the much easier to understand drwxrwxrwx layout but I'd need to look at my notes to tell you how to switch it. Let me know if you're interested.

I'm not on ubuntu at the moment.

---

### Post by ClientAlive on 2011-06-10
> **nrundy said:**
> I think all you need to do is right-click the folder and select the Permissions tab. There's a trick for making the Permissions tab display the much easier to understand drwxrwxrwx layout but I'd need to look at my notes to tell you how to switch it. Let me know if you're interested.

I'm not on ubuntu at the moment.


Thank you friend. But I would much prefer a command line solution. It isn't that I think the gui is unreliable - that would be false. It's that I know the command line is fully featured; and, on a personal level, I trust it more for this type of thing.

I think I read somewhere how to change the default umask (on the command line) but it was talking about for everything, not just a specific directory. It's also been so long I don't recall how that one even went.

I'm reading the man page right now but if you know something that would help I'd sure appreciated it.

Thanks
-----------------

Edit: It just occurred to me that telling what I'm trying to do exactly may help.

I have a folder where I would like it and everything I create in it (other folders and files) to have the following permission:

drwx --- ---

And I don't want to have to chmod every new item I create in it. It would sure be nice if the items were just created with that permission to begin with.

---

### Post by ClientAlive on 2011-06-12
bump

---

### Post by Lars Noodén on 2011-06-12
As far as I know you cannot set the umask for directories.  You can set the permissions with chmod and setting the sticky bit for groups will ensure that files created in that directory will inherit the same group membership.

---

### Post by ClientAlive on 2011-06-12
> **Lars Noodén said:**
> As far as I know you cannot set the umask for directories.  You can set the permissions with chmod and setting the sticky bit for groups will ensure that files created in that directory will inherit the same group membership.


Ok. I remember reading about the sticky bit. So with that approach what one would do is make sure they have one group that only they are a member of? That way they have a way where there are some things only they can access?


Thanks

---

### Post by Morbius1 on 2011-06-12
This can be easy or harder depending on what your real requirement is.

Create a unique group:
```
sudo groupadd xgroup
```Add users to the group:
```
sudo gpasswd -a morbius xgroup
```[COLOR=Blue]*You need to logout and log in again for the group membership to take affect.*[/COLOR]
Change the group of the directory:
```
sudo chown :xgroup /path/to/folder
```Change permissions so only the group has access:
```
sudo chmod 770 /path/to/folder
```Every memeber of xgroup will be able to add to and delet from that directory. They will however only be able to read the contents if they belong to some other user.

You can use the "sitcky bit" to prevent one user from deleting someone else's files by changing the chmod expression to this:
```
sudo chmod 1770 /path/to/directory
```Either way though next time a user adds a file to that folder it will save as:
owner = morbius
group = morbius
mode = 644

Another memeber of xgroup can read but not edit morbius' file. For that a combination of the setgid bit and umask is necessary. Not quite sure by your description of the requirements if that's what you want.

---

### Post by Lars Noodén on 2011-06-12
> **Morbius1 said:**
> 
You can use the "sitcky bit" to prevent one user from deleting someone else's files by changing the chmod expression to this:
```
sudo chmod 1770 /path/to/directory
```

Or you can set the group sticky bit so that the users can share access to the files:
```

sudo chmod 2774 /path/to/directory

#alternately:

sudo chmod u=rwx,g=rwxs,o=rx /path/to/directory


```

---

### Post by Morbius1 on 2011-06-12
> **Lars Noodén said:**
> Or you can set the group sticky bit so that the users can share access to the files:
```

sudo chmod 2774 /path/to/directory

#alternately:

sudo chmod u=rwx,g=rwxs,o=rx /path/to/directory


```
Setting the setgid bit will force the group of new files to xgroup ( in my example ). So when morbius adds a file to /path/to/directory it will save as:
owner = morbius
group = xgroup
mode = 644

It depends on your definition of "users can share access to the files". User "bill" can read the file but cannot edit the file. For that a umask change is required so that morbius' file will save as 664.

---

### Post by ClientAlive on 2011-06-12
> **Morbius1 said:**
> This can be easy or harder depending on what your real requirement is.

Create a unique group:
```
sudo groupadd xgroup
```Add users to the group:
```
sudo gpasswd -a morbius xgroup
```[COLOR=Blue]*You need to logout and log in again for the group membership to take affect.*[/COLOR]
Change the group of the directory:
```
sudo chown :xgroup /path/to/folder
```Change permissions so only the group has access:
```
sudo chmod 770 /path/to/folder
```Every memeber of xgroup will be able to add to and delet from that directory. They will however only be able to read the contents if they belong to some other user.

You can use the "sitcky bit" to prevent one user from deleting someone else's files by changing the chmod expression to this:
```
sudo chmod 1770 /path/to/directory
```Either way though next time a user adds a file to that folder it will save as:
owner = morbius
group = morbius
mode = 644

Another memeber of xgroup can read but not edit morbius' file. For that a combination of the setgid bit and umask is necessary. Not quite sure by your description of the requirements if that's what you want.


How to do this all makes sense, for the most part, but it raises two important questions for me. I think that if I had the answer to them I could do exactly what I'm shooting for easily and it would be the perfect solution for me.

(1) *So then, if a guy uses this groups and group membership way of addressing the issue - does that mean that you don't have to deal with the file and folder permissions? Because if a person is not a member of that group they can't do anything with them anyway?*

But you said:

> 
Another memeber of xgroup can read but not edit morbius' file.


Which leads me to question #2:

(2) *How do you make it so that anyone outside that group has absolutely no access whatsoever to the things within that folder? So that, to them, it doesn't even exist. They don't see the folder, they don't see the stuff in it, and they definitely don't read or even come close to opening a single thing inside it.*

What I'm trying to do is make a private little space for myself that no one can see or modify. An added issue for me, though, is that some of it's contents will, at times, need to be shared with select people through email and we both may need to modify something in a document.

Precisely what I'm talking about is this:

I'm working on a startup business. I have some files such as images of my signature, that I don't want anyone to do anything with - ever. I have some other original documents that I want to keep as original source documents - such as my non disclosure agreement and my business plan, etc. Then, using an example from the previous sentence, there are documents I will need to pass back and forth so each party can add the relevant information to the document, including signature (such as my non disclosure agreement, among other things). So now I have like 3 different needs going on here. On top of all that, I need to keep all of it under only my control so that average joe has no access whatsoever.

Wheras I am not the least bit scared of doing what I need to to make it happen, I can see that this is pretty invloved; and, while I understand the basics of things like chmod, chown, groups and the like - I have never had to use them on a level like this. I started using Linux about 2 mos ago. I've learned a lot but have only had the chance to dabble around with things, not implement something serious like this.

Now I'm moving forward with this startup in high gear and I don't have time to put my company on hold while I read another half dozen books to get this squared away. I'm pretty confident that if someone were to just point me in the right direction(s) I could get what I need to done pretty painlessly and be able to keep pressing on with business.

What do you think?

---

### Post by Morbius1 on 2011-06-12
> I have some files such as images of my signature, that I don't want anyone to do anything with - ever.For all the files that are yours and you want no access to anyone else:
```
sudo chown boss /path/to/**my**/folder
``````
sudo chmod 0700 /path/to/**my**/folder
```Only 2 people can access the contents of that folder: boss and root.
> I have some other original documents that I want to keep as original  source documents - such as my non disclosure agreement and my business  plan, etc.I'm assuming you want others to be able to read the contents of this folder but not add, delete, or edit anything. A normal directory under the user "boss" will do that. If boss created a folder by default it will save as:
owner = boss
group = boss
mode = 755
The boss can do anything he want's with it (7)
Everyone else can only read (5)
> there are documents I will need to pass back and forth so each party can add the relevant information to the documentThat's a setgid + umask change:
[1] From my post above:
```
sudo groupadd xgroup
sudo gpasswd -a morbius xgroup
sudo chown :xgroup /path/to/folder
sudo chmod 3770 /path/to/folder
```I changed the chmod to a "3770".
[COLOR=Blue]A "3" is a combination of the "stikey bit" (1) so that no one other than it's creator can delete it [COLOR=Black]**+**[/COLOR] a setgid bit (2) so that it forces the group of the file to xgroup.[/COLOR]

[2] Change the default umask:
Edit /etc/profile as root and change the last line from "umask 022" to:
```
umask 002
```So the flow would be something like this:

"boss" creates a file to /path/to/folder that he wants inputs from all members of xgroup. That file will have as:

owner = boss
group = xgroup
mode = 664

Every memeber of xgroup can edit the file but cannot delete the file. The parent directory has permissions of:
owner = boss
group = xgroup
mode = 3770

Boss can do whatever he wants to it .
Members of xgroup can add to but not delete anyone else's contents.
[COLOR=Blue]**EDIT:**[/COLOR] Didn't state that accurately. Memebers of the group can add a file but not delete any one else's files. All memebers of xgroup can edit the file itself.
Everyone who is not boss or a member of xgroup will see that the directory exists but will not gain even read access to it.

---

### Post by ClientAlive on 2011-06-12
> **Morbius1 said:**
> For all the files that are yours and you want no access to anyone else:
```
sudo chown boss /path/to/**my**/folder
``````
sudo chmod 0700 /path/to/**my**/folder
```Only 2 people can access the contents of that folder: boss and root.
I'm assuming you want others to be able to read the contents of this folder but not add, delete, or edit anything. A normal directory under the user "boss" will do that. If boss created a folder by default it will save as:
owner = boss
group = boss
mode = 755
The boss can do anything he want's with it (7)
Everyone else can only read (5)
That's a setgid + umask change:
[1] From my post above:
```
sudo groupadd xgroup
sudo gpasswd -a morbius xgroup
sudo chown :xgroup /path/to/folder
sudo chmod 3770 /path/to/folder
```I changed the chmod to a "3770".
[COLOR=Blue]A "3" is a combination of the "stikey bit" (1) so that no one other than it's creator can delete it [COLOR=Black]**+**[/COLOR] a setgid bit (2) so that it forces the group of the file to xgroup.[/COLOR]

[2] Change the default umask:
Edit /etc/profile as root and change the last line from "umask 022" to:
```
umask 002
```So the flow would be something like this:

"boss" creates a file to /path/to/folder that he wants inputs from all members of xgroup. That file will have as:

owner = boss
group = xgroup
mode = 664

Every memeber of xgroup can edit the file but cannot delete the file. The parent directory has permissions of:
owner = boss
group = xgroup
mode = 3770

Boss can do whatever he wants to it .
Members of xgroup can add to but not delete anyone else's contents.
[COLOR=Blue]**EDIT:**[/COLOR] Didn't state that accurately. Memebers of the group can add a file but not delete any one else's files. All memebers of xgroup can edit the file itself.
Everyone who is not boss or a member of xgroup will see that the directory exists but will not gain even read access to it.


THERE IT IS!!!

Thank you thank you thank you!

What I'm going to do now is study everything that has been shared with me very carefully and work on implementing it. This may take me some time as I am extremely busy lately - but I know it won't be any-where-near as bad as having to do it on my own/ without the help you've all given me.

My practice, and something I try very hard not to miss, is to post a follow up in the thread I started with a summary, description of what I did, and how it worked/ the results. Maybe the thread is never seen by anyone ever again, I can't vouch for that. If it is though, maybe the person who reads it benefits from everything we wrote in there.

So, I'll work on it; and, if I run into any problems that I can't google for the answer along the way, I'll post here about it. When all is said and done I'll post my follow up.

Thanks guys. I sure appreciate what you're doing for me here.

Jake

---

