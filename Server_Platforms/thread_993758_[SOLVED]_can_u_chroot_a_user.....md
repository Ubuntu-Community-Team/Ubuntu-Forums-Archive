---
title: "[SOLVED] can u chroot a user...."
date: 2008-11-26
forum: Server Platforms
---

### Post by meomike2000 on 2008-11-26
i want to add some users to my server. all of which well be logging in remotely via ftp or ssh. 

i would like to be able to just add these users and when they log in they could only see there home directory and not the whole system. is this possible and how could i accomplish this. 

thanks in advance...... mike

---

### Post by obg123 on 2008-11-26
Please don't allow ftp. Use scp instead (on the same port as ssh). There is an excellent client program for this at [http://www.winscp.org](http://www.winscp.org) for windozers. ftp is just not secure in any way.

I don't think it is possible to completely hide away the rest of the directory tree. After all, they will need to access /bin and /usr/bin at least. What you can do with the simple permissions is to restrict access to certain sub directories, and of course, to take away any kind of write permission.

---

### Post by amac777 on 2008-11-26
Well, as much as it directly conflicts what the previous poster said about ftp, it is very easy to jail users to their home directories only when using ftp.... 

If you use proftpd, you can jail users to their home directory by making sure the Defaultroot is set to ~ like this:

sudo nano /etc/proftpd/proftpd.conf

and then uncomment out this line:
```
# Use this to jail all users in their homes 
DefaultRoot                   ~

```

If you really want to try and jail for ssh, there are some tutorials on these forums for how to do it but it looks complicated to me. Here is one: (there are more)

[http://ubuntuforums.org/showthread.php?t=248724](http://ubuntuforums.org/showthread.php?t=248724)

---

### Post by ilrudie on 2008-11-26
It doesn't really conflict with the previous post.  FTP is still an insecure protocol.  One daemon that implements this insecure protocol allows you to jail a user in their home directory which doesn't really change the security of the system.

---

### Post by Traumadog on 2008-11-26
Hi!

If you're considering using ssh as your method for allowing users to access your server, and you are wanting a good, simple method to chroot them, you might consider using "My Secure Shell".  I've been using it for over a year now with good results.  Users can only see and access their own directories.  

If you'd like, you can explore it further by checking out their website:  [mysecureshell.sourceforge.net]("http://mysecureshell.sourceforge.net/").

Hope this helps.

Best wishes,

Traumadog.

---

### Post by amac777 on 2008-11-26
> **ilrudie said:**
> It doesn't really conflict with the previous post.  FTP is still an insecure protocol.  One daemon that implements this insecure protocol allows you to jail a user in their home directory which doesn't really change the security of the system.

FTP is no less secure than HTTP. Or, said a different way, HTTP is just as bad as FTP. Both transfer all usernames and passwords clear text fully visible to anyone that cares to sniff the connection. 

That said, I would note that probably most people are logging in to this very website using the insecure HTTP protocol, and the people runing this sever accept the limitations of this protocol, yet the security of the ubuntuforums.org system is still quite good.

So it's not a simple matter of never using "insecure protocols".

By the way, if you do choose to give ssh access to users who may or may not be fully trustworthy, the traffic transfered via the protocol is very secure, but then they can crash your server by running any number of weird commands to fork too many processes, or they could install rouge programs on their user accounts that do things you don't want your server doing. Not to mention the problem the OP is asking about that it's quite hard to jail them to a specific area of your system.

Disclaimer: I'm no expert, but simply offer the above from my very limited knowledge for whatever it's worth.

---

### Post by meomike2000 on 2008-11-26
i have looked at the options, i have chosen ftp, i have figured out the jail, as when i log in now i can only see my home directory. how do i add users to my system and allow them to log in to there home directories. i have added a couple of other user that will never be logging in at the machine itself. they will be using ftp. i can add the users with the useradd command. now they have a home directory at /homw/users/"users home".
i can log in as a new user at the machine. but no ftp. how can i fix this.

also, i have to manually create the home directory for each user. i thought that it would just create this for me. i would like for the new users to get a home folder in /home/users/. i created the users directory.

i am still fairly new at this so please be specific.

tia..... mike

---

### Post by meomike2000 on 2008-11-26
just discovered the adduser command vs. the useradd.

i would still like some help with adding a directory inside the new home of a new user with a welcome file in it.
could somebody help point me in the right direction for that...

tia....... mike

---

### Post by amac777 on 2008-11-27
To make a welcome directory in another user's home and and copy a welcome.txt file into that directory: (note: change 'username' to match the user's login name)

```
sudo mkdir /home/username/welcome
sudo cp welcome.txt /home/username/welcome

```

Optionally, if you want the user to be able to erase/modify the welcome directory and file, you can also change the owner on those to the username:

```
sudo chown username:username -R /home/username/welcome
```

Lockdown SSH

By the way, if you are running an ssh server, it's a good idea to specifically allow only yourself (or whoever you want to allow to login via ssh) to prevent all other users from logging in on ssh. Assuming your username is meomike2000, edit sshd_config to add the Allowusers line at the end: (you can add other usernames as well seperated by commas if there is more than one person who needs ssh)

sudo nano /etc/ssh/sshd_config

```
Allowusers meomike2000
```

Then restart ssh by running:

sudo /etc/init.d/ssh restart

Now, the only user that can ever login on ssh will be the users listed on that line. All other users will not be allowed to enter on ssh.

---

