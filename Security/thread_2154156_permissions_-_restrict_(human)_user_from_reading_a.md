---
title: "permissions - restrict (human) user from reading a file which is required for process"
date: 2013-06-13
forum: Security
---

### Post by kapuze on 2013-06-13
Hello!

At work I have the following situation: I have a computer with an admin account and a user account. The user account has one sole purpose: after login, automatically run a program which can record lectures and upload them to a streaming server. To do so, the program stores the server login name and password - unfortunately in plain text. To make the program available to all users, I put it into /usr/share.

So what I want is the following: on the one hand the user account must be able to read the password file so it can access the server. On the other hand I don't want the person who logs into the user account to be able to read the password.

Is there a way to enable only the recording program? So that users have no way of launching any other process? This would include such basic programs like less or cat or anything which can output a file's content. I guess I could remove all permissions from all other programs. But is this the only way?

Any suggestions or workarounds are welcome!

---

### Post by matt_symes on 2013-06-13
Hi

> **kapuze said:**
> Hello!

At work I have the following situation: I have a computer with an admin account and a user account. The user account has one sole purpose: after login, automatically run a program which can record lectures and upload them to a streaming server. To do so, the program stores the server login name and password - unfortunately in plain text. To make the program available to all users, I put it into /usr/share.

So what I want is the following: on the one hand the user account must be able to read the password file so it can access the server. On the other hand I don't want the person who logs into the user account to be able to read the password.

Is there a way to enable only the recording program? So that users have no way of launching any other process? This would include such basic programs like less or cat or anything which can output a file's content. I guess I could remove all permissions from all other programs. But is this the only way?

Any suggestions or workarounds are welcome!

Here's one idea.

1. Create a new system user with no shell
```
sudo useradd -r -s /bin/false  <User A>
```

2. Make the password file owned by that user
```
sudo chown <User A>: <passwd_file>
```

3. Make the password file readable only by that user
```
sudo chmod 700 <passwd_file>
```

4. Change the owner of the application file. The colon below is important.

```
sudo chown <User A>: application
```

5. Ensure the application has the correct world permissions
```
sudo chmod 755 <application>
```

That way you have locked down the password file to the superuser and the owner (User A) of that file.

That owner will be the application as it will be the only user with that user name.

User B will be able to run the application as it has world execute privileges.

User account B will still be able to use cat etc but not on that password file as only the owner can read it.

Is that what you want ?

BTW: Double check all the switch in the commands i have entered above.
 
EDIT: I had to edit this.

My excuse ? It's been a long week :)

Kind regards

---

### Post by kapuze on 2013-06-13
Hi Matt, thank you for your reply! It looks very much like what I want. Let me summarize to see if I understood correctly:

First I create a new user who has no shell available. So this user is not meant for humans to log into but only exists to launch the program. Only this user can read, write and execute the password file.
Important question: The admin account still has all rights on that file, right? Probably yes, because if he gave rights to the new user, he is still 'superior' to it. (sorry, I'm still getting my grasp on the whole permissions topic)

Next I make the same user the owner of the application. And at the same time I assign 755 to the application, which makes sense. One question though: why does <User A> have to be the owner of the application? Because otherwise it could not read the password file?

So in the end I create 2 users: The one is <User A> who cannot log in but can execute the program (you called it system user, that's the term for a user without a shell, I guess?). The second is the 'human' user, I call him <User B>, who can log in. Ok, since the application has execute rights assigned to <others>, <User B> can also execute the program. But he can't read the password. Nice!

If I understood correctly you really solved my problem! Thank you very much!

Edit: Oh yes, you said that the new user can still use cat and other programs. Following your solution that's perfectly fine. It was only my first intention that anything which outputs text would be a security leak. But since now everything is handled correctly by permissions, I have no problem with that.

---

### Post by matt_symes on 2013-06-13
> **kapuze said:**
> Hi Matt, thank you for your reply! It looks very much like what I want. Let me summarize to see if I understood correctly:

First I create a new user who has no shell available. So this user is not meant for humans to log into but only exists to launch the program. Only this user can read, write and execute the password file.
Important question: The admin account still has all rights on that file, right? Probably yes, because if he gave rights to the new user, he is still 'superior' to it. (sorry, I'm still getting my grasp on the whole permissions topic)

Yes. the admin user can still edit the file using the sudo command.

> Next I make the same user the owner of the application. And at the same time I assign 755 to the application, which makes sense. One question though: why does <User A> have to be the owner of the application? Because otherwise it could not read the password file?

Exactly. The application needs to be able to read the password file.

> So in the end I create 2 users: The one is <User A> who cannot log in but can execute the program (you called it system user, that's the term for a user without a shell, I guess?). The second is the 'human' user, I call him <User B>, who can log in. Ok, since the application has execute rights assigned to <others>, <User B> can also execute the program. But he can't read the password. Nice!

Yep. That's the general idea. A system user is a user with an ID below 1000. It will not appear in the login page when you first log into the desktop.

> 
If I understood correctly you really solved my problem! Thank you very much!

Edit: Oh yes, you said that the new user can still use cat and other programs. Following your solution that's perfectly fine. It was only my first intention that anything which outputs text would be a security leak. But since now everything is handled correctly by permissions, I have no problem with that.

That should stop others reading the file. As long as the application has been written well then it should not leak the password elsewhere.

Kind regards

---

### Post by kapuze on 2013-06-18
Hi,
small problem with this approach: The application is actually simply a python script. So although the script is owned by the system user, the user who launches the python process is still the human user. Thus, the python process cannot open the password file for reading and therefore cannot pass the contents to the application. This prevents the program from running. So it would have to be the system user (we called him userA) who needs to launch python in the first place. How would I do that?

---

### Post by Lars Noodén on 2013-06-18
If they are logging in while physically at the computer, then your might consider [rbash](http://manpages.ubuntu.com/manpages/raring/en/man1/rbash.1.html).  Make a special directory with only that one script in it and then set the value of $PATH to that directory.  Make sure that everything in the home directory is owned by root and otherwise not writable by that user.  

Or you could try making that script be that user's shell.

Both of those assume that you are not using the graphical user interface.

---

### Post by kapuze on 2013-06-18
Hi Lars, Thanks for your suggestions, but as I understand them, they don't address my latest problem. I want to go for the solution posted by matt_symes. However it turns out to be a little trickier than described. See post #5.

---

### Post by Lars Noodén on 2013-06-18
There might be a way to do it using sudo.  Instead of using sudo to run as root, use sudo to run as a user that can read the password file.  The option for that is -u.  Have it call a shell script which reads the password and pipes it to the python script.  You'll need two users, one to read the password and one for the python script.  You'll need two entries in sudoers, one to call the password-reading script as the password-reading user, the other for the password-reading user to call the python script as the unprivileged user. 

It's a little convoluted but I think it does what you are trying.

---

### Post by prodigy_ on 2013-06-18
If something is stored as plaintext on the client machine it **may** leak. I'm sorry to say this but your whole approach is fundamentally flawed. Instead of trying to hide the password on the client side, you want to maintain proper security on the server side. E.g. run the streaming server in a dedicated virtual machine and use iptables to limit network access from inside the VM.

---

### Post by kapuze on 2013-06-18
You're right. But I can't change the program we're using.

---

### Post by Hungry Man on 2013-06-18
Create a new user/group with permissions to that file. Then use Apparmor/SELinux on the shell so that it can only read/execute the process you want it to.

---

