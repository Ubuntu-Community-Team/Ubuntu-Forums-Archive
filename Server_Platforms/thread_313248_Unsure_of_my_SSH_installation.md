---
title: "Unsure of my SSH installation"
date: 2006-12-05
forum: Server Platforms
---

### Post by robk86 on 2006-12-05
I just installed ssh on my server using to the guide at ubuntuguide.org.  I did the apt-get command and ran the ssh-keygen program. What I want to know is if the keys are in the correct location.  The guide says: "Install key in default directory (~/.ssh/id_dsa and ~/.ssh/id_dsa.pub)"
I just ran the keygen from the directory that shows up when I log in which is: [my user name]@ubuntu:~$
When I use the ls command here the key files (the name I typed into the keygen and [that name].pub are listed and are the only files there.  If I were to use the directories in the guiede; Which directory starts with the ~/ ? I only can get to ~$ or /$.  Also, I ran PuTTY in Windows and I was able to login; it just said asked if I trusted the machine and said it had to add the key to the cache.  Is this normal?  Also, I tried to use FileZilla and it gets a response but can't connect.

---

### Post by lloyd_b on 2006-12-05
> What I want to know is if the keys are in the correct location. The guide says: "Install key in default directory (~/.ssh/id_dsa and ~/.ssh/id_dsa.pub)"
I just ran the keygen from the directory that shows up when I log in which is: [my user name]@ubuntu:~$
When I use the ls command here the key files (the name I typed into the keygen and [that name].pub are listed and are the only files there. If I were to use the directories in the guiede; Which directory starts with the ~/ ? I only can get to ~$ or /$.

Tilde ("~") translates to "The current user's home directory" - it's a convenience feature built into the shell.

So "~/.ssh/id_dsa.pub" = "/home/{username}/.ssh/id_dsa.pub"

Where {username} is the login name for the current user.

Whenever you open a terminal window, you'll be in your home directory.

Lloyd B.

---

### Post by robk86 on 2006-12-05
So, the key files are in my home directory.  I just figured out that I can use ls -a to see all contents of a directory. The sub-directory .ssh is not in my home directory.  Should I make a .ssh directory or are the files fine where they are?

---

### Post by lloyd_b on 2006-12-05
I'm not an expert on ssh, but I suspect you'll need to manually create a ".ssh" subdirectory in your home directory, and then manually move/copy those key files into it.

Lloyd B.

---

### Post by paul.maddox on 2006-12-06
I think the standard these days for best security is to use RSA keys rather than DSA keys.

To create some RSA keys run the command below.
Accept the default locations it suggests and protect your private key with a strong passphrase when it asks for one.
```

paul.maddox@web1:~$ ssh-keygen -t rsa -C "$(whoami)";

```

***************************************************
This should have automatically created the .ssh folder with the correct permissions and placed the id_rsa and id_rsa.pub files inside, but if it hasn't then perform the following step:

Create the .ssh folder, and make sure only your user has permissions to view the contents. SSH is very strict about permissions and if you don't set them correctly you will not be able to login using the key you created.
```

paul.maddox@web1:/$ cd ~
paul.maddox@web1:~$ mkdir .ssh
paul.maddox@web1:~$ chmod 700 .ssh

```

Now move the generated keys into the .ssh directory. If ssh-keygen did this by default then ignore this step.
```

paul.maddox@web1:~$ mv id_dsa* .ssh/

```

***************************************************

To allow your Windows PC using Putty to login to the server using private/public key authentication you need to create an 'authorized_keys' file in your .ssh folder like so:

```

paul.maddox@web1:~$ cd ~/.ssh
paul.maddox@web1:~$ cat id_rsa.pub >> authorized_keys
paul.maddox@web1:~$ chmod 600 authorized_keys

```


You will now have to download the id_rsa file to your windows computer and convert it to a .ppk file using puttygen, and then load it up into pageant. Now when you try SSH'ing into your server it should work perfectly and not ask for a password.

---

### Post by dannyboy79 on 2006-12-06
> **paul.maddox said:**
> I think the standard these days for best security is to use RSA keys rather than DSA keys.

To create some RSA keys run the command below.
Accept the default locations it suggests and protect your private key with a strong passphrase when it asks for one.
```

paul.maddox@web1:~$ ssh-keygen -t rsa -C "$(whoami)";

```

***************************************************
This should have automatically created the .ssh folder with the correct permissions and placed the id_rsa and id_rsa.pub files inside, but if it hasn't then perform the following step:

Create the .ssh folder, and make sure only your user has permissions to view the contents. SSH is very strict about permissions and if you don't set them correctly you will not be able to login using the key you created.
```

paul.maddox@web1:/$ cd ~
paul.maddox@web1:~$ mkdir .ssh
paul.maddox@web1:~$ chmod 700 .ssh

```

Now move the generated keys into the .ssh directory. If ssh-keygen did this by default then ignore this step.
```

paul.maddox@web1:~$ mv id_dsa* .ssh/

```

***************************************************

To allow your Windows PC using Putty to login to the server using private/public key authentication you need to create an 'authorized_keys' file in your .ssh folder like so:

```

paul.maddox@web1:~$ cd ~/.ssh
paul.maddox@web1:~$ cat id_rsa.pub >> authorized_keys
paul.maddox@web1:~$ chmod 600 authorized_keys

```


You will now have to download the id_rsa file to your windows computer and convert it to a .ppk file using puttygen, and then load it up into pageant. Now when you try SSH'ing into your server it should work perfectly and not ask for a password.

I am sure you're really confussing this guy! First you tell him what to do with his id_dsa file and then later you tell him he should copy the contents of id_rsa.pub into the authorized_keys file, so which is it, id_rsa or id_dsa because you won't be able to authenticate from putty using an encrypted dsa private key if your server has a rsa public key. Also, you forgot to tell him he needs to remove the private key (the one without the .pub on it) from the server!! Protect this file with your life, although I suppose if you used a passpharse even if an intruder got your provate key they still would have to brute-force the file to figure out the passphrase. 

Anyway, to the guy wondering if his openssh installation is correct, I would strongly suggest reading this tut ([http://www.unixwiz.net/techtips/putty-openssh.html)](http://www.unixwiz.net/techtips/putty-openssh.html)), it will square ya away just fine!!!! Post back if you need specific help but I will warn you, I would like for you to completely read and go thru the entire tutorial before you ask anymore questions. I know you can do it, good luck!

---

### Post by stell86 on 2006-12-10
without the bracket:
[http://www.unixwiz.net/techtips/putty-openssh.html]("http://www.unixwiz.net/techtips/putty-openssh.html")

Thanks for the link - working on it now....

---

### Post by robk86 on 2006-12-10
I haven't really been working on this for the last few days, but I went back to it today.
Anyways, I went through that tutorial and found it helpful, but now I have a different problem.  I noticed that the /etc/ssh folder had some sort of keys in it, but people are saying they should be in the ~/.ssh directory. I created the directory and put in the keys, but it didn't work for PuTTY.  I think its because ssh tries to use the ones in the /etc/ssh directory.  I edited the config file and wasn't sure how it was originally so I decided to uninstall and reinstall ssh.  I used 'sudo apt-get remove ssh' followed by 'sudo apt-get install ssh', but the same files were in the /etc/ssh folder, so I deleted the contents as well as the folder and tried again.  I ended up creating the /etc/ssh folder manually but it stays empty. I ran the ssh and ssh-keygen commands without parameters and they seem to be on the system.  How do I get the installation of ssh back to normal?

---

