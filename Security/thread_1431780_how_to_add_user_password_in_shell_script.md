---
title: "how to add user password in shell script?"
date: 2010-03-17
forum: Security
---

### Post by hrcariagajr on 2010-03-17
Hi All,

I'm currently creating a simple sh file which will copy the contents of a certain directory to / directory. 

in my sh file:

```

 cd "$DIR"
for i in *.*; do
    sudo cp -iv "$i" "$DEST"
done

```

but this requires user password. can i add the user password in my sh file? how? 
I'm trying to do this because I have an application to run the sh file and the application has no way to enter the password.. 

thanks

---

### Post by cdenley on 2010-03-17
> **hrcariagajr said:**
> Hi All,

I'm currently creating a simple sh file which will copy the contents of a certain directory to / directory. 

in my sh file:

```

 cd "$DIR"
for i in *.*; do
    sudo cp -iv "$i" "$DEST"
done

```

but this requires user password. can i add the user password in my sh file? how? 
I'm trying to do this because I have an application to run the sh file and the application has no way to enter the password.. 

thanks

This is possible, but I wouldn't recommend it. You do not want to store your password in plaintext! What you should do is run the shell script with sudo, and if it absolutely cannot prompt for a password, then configure sudo so a password is not required for that script.

---

### Post by bodhi.zazen on 2010-03-17
> **cdenley said:**
> This is possible, but I wouldn't recommend it. You do not want to store your password in plaintext! What you should do is run the shell script with sudo, and if it absolutely cannot prompt for a password, then configure sudo so a password is not required for that script.

To follow up on that ...

any script to be run as root should, IMO, be owned by root, only writable by root, and called with sudo.

---

### Post by hrcariagajr on 2010-03-18
> **cdenley said:**
> This is possible, but I wouldn't recommend it. You do not want to store your password in plaintext! What you should do is run the shell script with sudo, and if it absolutely cannot prompt for a password, then configure sudo so a password is not required for that script.


Storing password in a plain text is not advisable, but i think this is my only way to solve my problem. The sh file is temporary created, perform some task(copying files) then delete the sh file when completed. 

> **cdenley said:**
> 
 What you should do is run the shell script with sudo


My problem here is that my application will run the sh file, and i can't find a way to enter the password when promt. So i want to add the password in the sh file so theres to need to enter the password when using sudo commands.. 

thanks...

---

### Post by cdenley on 2010-03-18
I still think this is a horrible solution, but you can do something like this:
```

echo mypassword|sudo -S mycommand

```

---

### Post by bodhi.zazen on 2010-03-18
> **hrcariagajr said:**
> Storing password in a plain text is not advisable, but i think this is my only way to solve my problem. The sh file is temporary created, perform some task(copying files) then delete the sh file when completed. 

My problem here is that my application will run the sh file, and i can't find a way to enter the password when promt. So i want to add the password in the sh file so theres to need to enter the password when using sudo commands.. 

thanks...

It is not the only way, lol.

You run your script as root , or at least with sudo. You may configure sudo (visudo) such that no password is required for the script.

The script should be owned by root, and writable only by root.

If push comes to shove, you can use expect.

---

### Post by hrcariagajr on 2010-03-18
> **cdenley said:**
> I still think this is a horrible solution, but you can do something like this:
```

echo mypassword|sudo -S mycommand

```


Thanks, this works! Cheers!:)

---

### Post by brucewestfall on 2010-05-13
Please don't anybody blow a fuse on this one, but if my computer is sitting inside my house and everyone who lives in my house already knows my password and is welcome to use my computer...

Why should I not have a password in plain text?

My home folder is not readable via the internet, correct?

Really not trying to be a sarcastic here, just TRULY wondering what the harm would be.

---

### Post by cdenley on 2010-05-13
> **brucewestfall said:**
> 
My home folder is not readable via the internet, correct?


It shouldn't be, but you never know if an attacker may manage to gain local access to your computer. Password cryptography is a layer of security. If all the layers above it never fail (like web browser security), then it will have been unnecessary. It is better to have extra layers and not need it then to need it and not have it. If your system never connects to the internet, and never interacts with any external servers, networks, or data, and anyone who can possibly gain physical access can be trusted, then yes, storing password in plaintext should be fine.

---

### Post by bodhi.zazen on 2010-05-13
> **brucewestfall said:**
> Please don't anybody blow a fuse on this one, but if my computer is sitting inside my house and everyone who lives in my house already knows my password and is welcome to use my computer...

Why should I not have a password in plain text?

My home folder is not readable via the internet, correct?

Really not trying to be a sarcastic here, just TRULY wondering what the harm would be.

There is nothing wrong with that.

---

