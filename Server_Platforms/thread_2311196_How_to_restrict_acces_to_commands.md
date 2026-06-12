---
title: "How to restrict acces to commands"
date: 2016-01-25
forum: Server Platforms
---

### Post by Jake_Simmons on 2016-01-25
Hi, 
I have installed ubuntu server on a computer to allow my classmates to complete a controlled assessment on linux in general. To complete the assessment they need to install an application, and show evidence that they have done it. (the application is called tree). However, after a quick google they found ```
rm -Rf /
``` Is there any way to allow them to be a root user to install tree, but to not allow them to wipe everything? Or even to just remove the rm command etc.
Thanks,
Jake

---

### Post by QDR06VV9 on 2016-01-25
Why don't you just install it yourself??
Maybe I do not understand your request..
```
sudo apt-get install tree
```
Then they should be just able to call it by
```
tree
```
More usage with tree   [http://lintut.com/use-tree-command-in-linux/](http://lintut.com/use-tree-command-in-linux/) 
Kind Regards

---

### Post by matt_symes on 2016-01-25
Hi

> **Jake_Simmons said:**
> Hi, 
I have installed ubuntu server on a computer to allow my classmates to complete a controlled assessment on linux in general. To complete the assessment they need to install an application, and show evidence that they have done it. (the application is called tree). However, after a quick google they found ```
rm -Rf /
``` Is there any way to allow them to be a root user to install tree, but to not allow them to wipe everything? Or even to just remove the rm command etc.
Thanks,
Jake

I think i may have read your post differently than runrickus.

You want to allow you classmates to install tree while disallowing them access to the rm command ?

If this is the case then you have to understand that anybody who knows the sudo password can basically do anything they want on your system.

rm is just one way of deleting a file. There is also the unlink command. The unlink command cannot delete a directory recursively though.

I think you're tackling this the wrong way by trying to blacklist a command. A better solution might be to whitelist the command you want them to run.

That being said, there is a way to do what you want by edit the sudoers file on each machine.

You can disable the rm command but that will mean everyone, yourself included, will not be able to run the rm command. Of course, if a classmate knows the sudo password then they can just edit the sudoers file to remove that restriction and you're back to square one.

Security by obscurity is not security.

Anyway,

```
sudo visudo
```

After the line

```
%sudo   ALL=(ALL:ALL) ALL
```

add this one

```
%sudo ALL = !/bin/rm
```

Save and exit the file.
```

matthew-xu-16-04:/home/matthew:0 % sudo rm -rf /
Sorry, user matthew is not allowed to execute '/bin/rm -rf /' as root on matthew-xu-16-04.
matthew-xu-16-04:/home/matthew:0 
```

However, with the sudo password, they can also just add themselves to the admin group :)

So many ways around this......

Kind regards

---

### Post by QDR06VV9 on 2016-01-25
Yep we read it the same..Albeit you have a more eloquent solution..
Thanks Matt
Best Regards

---

### Post by Jake_Simmons on 2016-01-25
That sounds perfect (i havent tested yet), they wont know to change the config, so its great!
The reason i cant install tree, is that they have to show evidence of them doing it themselves, so i remove it each time, 
Thanks,
Jake

---

### Post by QDR06VV9 on 2016-01-25
> [COLOR=#000000]The reason i cant install tree, is that they have to show evidence of them doing it themselves, so i remove it each time, [/COLOR]
[COLOR=#000000]Thanks,[/COLOR]
Now that makes perfect sense to me now..Thanks to matt_symes for seeing that! :D
Cheers

---

### Post by matt_symes on 2016-01-25
Hi
> 
I think you're tackling this the wrong way by trying to blacklist a command. A better solution might be to whitelist the command you want them to run.

@OP. I don't want to labour the above point, however i though i would mention how you can whitelist unprivileged users to run specific commands.

bert, not a member of the sudo or admin group.

```
matthew-xu-16-04:/home/matthew:1 % groups bert                
bert : bert
```

bert is allowed to run a single command to install tree in the sudoers file.

```
matthew-xu-16-04:/home/matthew:1 % sudo grep bert /etc/sudoers
bert ALL=(ALL) /usr/bin/apt-get install tree
```

Change to the unprivileged user bert

```
matthew-xu-16-04:/home/matthew:1 % sudo -i -u bert  
```          

bert then can install tree using apt-get by entering his password. In the case below, i had already installed it as it's a useful command.

```
bert@matthew-xu-16-04:~$ sudo apt-get install tree
[sudo] password for bert: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tree is already the newest version (1.7.0-3).
0 to upgrade, 0 to newly install, 0 to remove and 259 not to upgrade.
```

That is the only privileged command bert can run and certainly not any dangerous commands such as *sudo rm -rf /*

```
bert@matthew-xu-16-04:~$ sudo rm -rf /
Sorry, user bert is not allowed to execute '/bin/rm -rf /' as root on matthew-xu-16-04.
```

Now bert can be removed which I'll do later.

```
bert@matthew-xu-16-04:~$ exit
logout
matthew-xu-16-04:/home/matthew:1 % 
```

Whitelisting is *the* best technique and your classmates may learn something along with it.

**EDIT:**

Just thought i had better mention that you can white list groups for specific commands and then add each user you want to allow to run that command to that group.

Kind regards

---

