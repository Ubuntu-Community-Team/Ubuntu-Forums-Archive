---
title: "SSH login via scipt"
date: 2009-11-28
forum: Server Platforms
---

### Post by zaksworld on 2009-11-28
I have some web servers that I manage, so I Have to constantly update them.

It is a real pain when I am constantly running scripts and have to type in the root password about 5-10 times per computer per update.

I know there is a way to store my main computer's data on the servers so that I don't have to type the username and password every time, but since I have a bunch of computers, I still have to run the code to get into every computer, so even without typing in the username and password, it is still very time consuming.

All my servers have the same root password, so if there is any line of code I could add to my script (or just a script I could run), so my main computer will login automatically, or if there is any way that I can store my server's data on my main computer, so that my main computer can login to my servers automatically, I would like to know.

Thanks in advance
Zak

---

### Post by JT9161 on 2009-11-28
Use keys

---

### Post by whoop on 2009-11-28
> **JT9161 said:**
> Use keys

He is saying "authenticate using keys" ;)

Still I wouldn't use this to login to an account with elevated privileges, but maybe I'm paranoid.
In any case, using keys is always more secure (if you don't count debian's blunder, that is, but that is solved now)...

---

### Post by kevdog on 2009-11-28
I believe you can do this using expect.  Here are a couple examples:

Sorry I couldnt find better ones:
[http://bash.cyberciti.biz/security/expect-ssh-login-script/](http://bash.cyberciti.biz/security/expect-ssh-login-script/)
[http://www.unix.com/shell-programming-scripting/60545-need-help-expect-shell-script.html](http://www.unix.com/shell-programming-scripting/60545-need-help-expect-shell-script.html)

---

### Post by terbor on 2009-11-28
You can change the name of the folder you store your keys in (so it is not the standard ) and turn off the password access ( If this applies to the way you access your servers now )

---

### Post by iponeverything on 2009-11-28
I think expect is just what your looking for.

I have used it quite a bit in situations like you have described.

Once I had 100 catalyst switches, and had to go though every one and change the enable password and DHCP helper address. 

I added all the IP addresses for the switches to a file and wrote an 20 line expect script.. 

Then, I just sit back and watch. I check the logs I created for errors and move on to something else..

---

### Post by Denbert on 2009-11-29
> **zaksworld said:**
> I have some web servers that I manage, so I Have to constantly update them.

It is a real pain when I am constantly running scripts and have to type in the root password about 5-10 times per computer per update.



Why don't you setup an auto-update job on each server, with a mail report back to you?

[http://www.debianadmin.com/automatic-update-of-packages-using-cron-apt.html](http://www.debianadmin.com/automatic-update-of-packages-using-cron-apt.html)

---

### Post by apmcd47 on 2009-11-29
I think Denbert's suggestion is best. Use cron jobs on the servers.

If not, public key authentication is the way forward. By using expect I imagine you will be putting passwords in a shell-script. A big no-no in my opinion.

I think I would do the following:

1) Set up a new public/private key pair, using, say, rootpriv as the name of the key. 

2) Imagine dave is the name of one of your servers. Copy rootpriv.pub into /root/.ssh/authorized_users on dave.

3) In your account on your normal machine, add the following to ~/.ssh/config:
```
Host root-dave
   Hostname dave
   Username root
   Keyfile rootpriv
```
This is from memory, check the manpage on ssh-config for the actual keywords. But this should mean when you ssh to root-dave you will login to dave as root using rootpriv for authentication. You would do (2) and (3) for the other servers.

4) If you are using ubuntu you will probably be running your desktop inside an ssh-session. Thus running 
```
ssh-add
``` in a shell terminal will prompt you for the passphrase of your default keys and allow you to login to other machines with those keys without prompting for your passphrase. It is possible to remove the key from the session too. When you logout the the session and hence the stored key is lost, so you would need to do this every time you log in.

Add the following lines to the top and bottom of your shellscript:
```
ssh-add ${HOME}/.ssh/rootpriv
ssh-add -d ${HOME}/.ssh/rootpriv
```
You will be prompted for the rootpriv passphrase every time you run the script, but only once during the course of the script. You will also have to change every ssh invocation from eg
```
ssh root@dave ...
``` to ```
ssh root-dave ...
```

The problem with this of course is that the servers are open to anyone with access to your desktop during the time your script is running, so if you leave it unattended, lock it. Alternatively run the script inside its own ssh session (man ssh-session).

Andrew

---

### Post by BkkBonanza on 2009-11-29
You may also want to read up on cluster ssh (google it).
This version of ssh allows you to run commands on multiple servers simultaneously. If your systems are similar enough this may make routine admin work easier.

---

### Post by zaksworld on 2009-11-29
> **Denbert said:**
> Why don't you setup an auto-update job on each server, with a mail report back to you?

[http://www.debianadmin.com/automatic-update-of-packages-using-cron-apt.html](http://www.debianadmin.com/automatic-update-of-packages-using-cron-apt.html)

Haha, well, I've thought about that, but because of other complications, I am not allowed, plus it might not work as well as expected...but thanks for the idea anyways!

> **iponeverything said:**
> I think expect is just what your looking for.

I have used it quite a bit in situations like you have described.

I have thought about using expect, but (because of the same complications) I am not allowed to use it either, but thanks for the idea.

> **apmcd47 said:**
> If not, public key authentication is the way forward. By using expect I imagine you will be putting passwords in a shell-script. A big no-no in my opinion.

I'm trying to avoid using public key authentications, because then I have to go onto each individual server and not only install the updates, but use a bunch of extra time to be able to get all of the keys, and time is money! ha


I did manage to find somewhat of a solution.  It's a program called sshpass
```
apt-get install sshpass
```.  It allows me to run (or write in a script)
```
sshpass -p 'password' ssh -o StrickHostKeyChecking=no user@myipaddress
```
I only need to install this on my main computer (so only one install), and I can write the other computers passwords into a script.

I know some people have a concern about this, but the passwords change often, so even if someone can get the scripts (highly unlikely), then the system is still mostly safe.

Now, I'm going to keep this post open, just in case anyone has any ideas about this, and because I haven't tried the sshpass yet.  Once I test out the sshpass today (and it succeeds), I'll close this post.  

Thanks everyone!
Zak

---

### Post by BkkBonanza on 2009-11-29
I think you're a bit confused about using key authentication. You should be able to use ssh-copy-id to copy your (public) key to each server. Use "man ssh-copy-id" to read how easy that is. 

After that you can login into each of those servers using your key. You won't be prompted for a password then as long as you are logged into your account (having the key). Or you can tell ssh with -i to use a specific identity key. 

It should be that simple to set up for each server. You gain the benefit of a full key against brute force attacks. It doesn't require putting passwords into scripts and it makes all ssh logins quick and easy with no prompts. I use it for all my admin work.

If you need to move from machine to machine and don't want to save the key in your account you can use -i and refer to a key on a usb thumb drive.

Once you have the key copied you can disable password logins if you like for better security - and as long as you won't lose your key.

---

### Post by Lars Noodén on 2009-11-29
> **BkkBonaza said:**
> I think you're a bit confused about using key authentication. You should be able to use ssh-copy-id to copy your (public) key to each server. Use "man ssh-copy-id" to read how easy that is. 


That's very easy, too.  Then you can use ssh-add to load your key into the agent and go about your tasks.  

In kde's terminal it is possible to broadcast your keystrokes to multiple sessions.  That's useful if you're doing the same thing to many machines.  

Choose:
  Edit->Copy Input To ...->
Then select the tabs which shall receive the broadcasted input.
You'll see an asterisk on the tab which is the master.  You can still operate in the recipient tabs independently of eachother and the master.

---

