---
title: "Different login actions based on seperate passwords"
date: 2008-08-25
forum: Ubuntu Brainstorm
---

### Post by king vash on 2008-08-25
This may already exist or not be feasible but I think that

[SIZE="3"]Having different profiles(login programs, file access and settings) that were activated based on the users password would be really cool.
[/SIZE]
Problems -
less secure, there is now 2 or 3 valid passwords


Advantages -
when the fbi raids you how you can tell them a password that will runs "sudo rm -rf" (do not run this command it will delete your harddrive) when you login would be nice.

can hide all your "private" files from parents \ spouse \ assorted friends.

faster login on one password, feature full login on the other.

---

### Post by smartboyathome on 2008-08-25
I don't like this idea. Not only is it not feasable, but it would be worse for security (as you point out). In my opinion, security is more important than being able to destroy your computer when you break the law (which you shouldn't do in the first place).

---

### Post by king vash on 2008-08-25
The FBI thing was a joke plus it is quite easy to recover data even when "sudo rm -rf" has been called. I think that it would be useful so that multiple compiz and session settings can be loaded in and out easily. this can be achieved with multiple users but then all your folders and files have to be reshuffled

---

### Post by signifer123 on 2008-08-26
You can have multiple users share a home directory. Just make sure to give them both permissions to it. Then there's no file reshuffling, and you can hide files from the other person without having to write a custom filesystem/bootup script.



But, here's a PAM module that allows for GDM to run a user created script based upon which password was entered. That script will run and also decide if the password allows the user to login. It's a bit confusing to configure probably, so I included a sample filesystem with the files that are modified. 

Read the README for configuration instructions, I tried to keep it from being confusing, but it probably ended up being more so with all the extra instructons.

You'll need g++ and the libpam0g-dev, if you run the install script with sudo, it should install these for you.

Unfortunately the passwords are stored in cleartext, along with the commands that they run. Ease of use and and editing.


Feel free to drop me a PM.

---

### Post by king vash on 2008-08-26
signifer123 thank you so much! did you just write that or was it on the internet and I missed it?

This was just what I was looking for.

---

### Post by signifer123 on 2008-08-26
> **king vash said:**
> signifer123 thank you so much! did you just write that or was it on the internet and I missed it?

This was just what I was looking for.

Just wrote it. You wern't missing it.

---

