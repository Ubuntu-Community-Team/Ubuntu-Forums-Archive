---
title: "Ubuntu Server HELP... 10.04 lts"
date: 2010-12-18
forum: Server Platforms
---

### Post by jamesgrant on 2010-12-18
Ok so i want and need a  server in my home (file server web server whatever you call it)

I already know what i want, so continue reading.

1. Im going to be using** ubuntu server 10.04 lts**.

2. The server will have all my pictures, music, videos, documents, and computer backups in **separate folders **named accordingly.

3. i want the server to share those files with my windows 7 machines and a ubuntu machine, over my **wireless** network and **wired**. (using _**samba**_)

3. remote management (using _**openSSH**_ and _**putty**_)

4. for the files on the server, i want to have permissions, to allow and  deny certain users access to certain files, password (dont know how to  make that work)

5. and i want to be able to back up the files on my server and it os to a  cd every now and then (i guess using a some sort of backup command  built in to ubuntu?)

now i need to know how to pull it all together.

( how will it look in my windows machine when i go to access the files on my server?

just open network and open server and the files should show up there)

---

### Post by CharlesA on 2010-12-18
Please don't crosspost (post the same thread in different areas).

Your original thread is here: [http://ubuntuforums.org/showthread.php?t=1647595](http://ubuntuforums.org/showthread.php?t=1647595)

There are tons of documentation about how to set up SSH and Samba. Looking [here]("https://help.ubuntu.com/10.04/serverguide/C/index.html") is a good start.

---

### Post by jamesgrant on 2010-12-18
Well i know that but i doesent make any sense to me i need help with this, like step by step instruction on how to configur everything. i know how to install the os and all that jazz that the eazy part.

---

### Post by CharlesA on 2010-12-18
I have a [tutorial]("http://charlesa.net/tutorials/linux/samba.php") on how to set up Samba, if you want to take a look at it.

As for setting up SSH, it's fairly easy, just install the server with:

```
sudo apt-get install openssh-server
```

Then connect.

Just make sure you have a strong password at least 8-15 characters long.

---

### Post by jamesgrant on 2010-12-18
i tell you what, since it look like no one wants to help can i do all these thing from ubuntu desktop 10.04 lts?

 it will probably make it a little easier for me

---

### Post by CharlesA on 2010-12-18
Yes.

Most, if not all, services will run on Ubuntu Desktop without problems.

Are you having a problem with a specific step?

---

### Post by drdos2006 on 2010-12-18
You sound a little impatient. Not everyone is on the forum just because you happen to be.


Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by jamesgrant on 2010-12-19
Thanks it helped a lot^^^^^^^^^^^

---

