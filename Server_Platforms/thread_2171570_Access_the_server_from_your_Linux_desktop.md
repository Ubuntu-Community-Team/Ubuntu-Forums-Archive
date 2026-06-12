---
title: "Access the server from your Linux desktop???"
date: 2013-08-31
forum: Server Platforms
---

### Post by GMHilltop on 2013-08-31
I was working on another problem when I learned [here]("http://ubuntuforums.org/showthread.php?t=2171089&p=12773689#post12773689") that you should be able to access your Ubuntu server (12.04 LTS) from another Linux machine.

I am trying to access it from the same local network & I am using the server as a Proxy using squid3.

I tried in terminal this--> ssh user@serverIP:

sudo ssh ourproxy@192.168.1.6

ourproxy was the user and the static ip of the server was 192.168.1.6

. . . and all it did was hang - nothing happened. I used ctrl + c to quit that.

When I installed the server, I simply did the most basic of installs, no extras, nothing fancy as I wanted to test it out with squid3

Suggestions, ideas are welcome!  Thanks

---

### Post by GMHilltop on 2013-08-31
I've also tried entering this into the file managers Location bar--> sftp://user@serverIP:

. . . in my test case it was

sftp://ourproxy@192.168.1.6

the reply I got was access denied. 

It sounds like the command was correct, but I am missing something on the server.

Question 1:
If the only user on the server is ourproxy can you use that as well to login remotely or do I need to set up another user on the server to do that?

Question 2:
If I do have to set up a separate user, OR, set up remote access permissions - how would I do that on the server?

Thanks

---

### Post by nerdtron on 2013-08-31
On the remote server you want to access, you should install the openssh-server package.
```
sudo apt-get install openssh-server
```

Next on the remote server, there should be a valid user.
On your case, "ourproxy" should be a user account that is active and can log in the server itself.

Then try again on your local desktop:
```
ssh -v ourproxy@192.168.1.6
```

I addred the -v option just to see if there are any problems. Post it here it there are any.

Hope it helps... and keep us posted.


Note: If the ssh works on the terminal, then sftp on the file manager *should* also work.

---

### Post by GMHilltop on 2013-09-01
Hot Damn! Worked like a charm! =D>

```
sftp://ourproxy@192.168.1.6
```

This saves me having to install a desktop on the server yet I can see what I need to see if I need to.

Now, I was wondering - can I access a particular file as "ROOT" via the sftp connection?

I KNOW I should be doing this in command line, but sometimes I don't know how or what to do there and it is just easier via the GUI.
On my local machine I can right click on a file/directory and select "Open as Root", it asks for the password, and I am away.

When I tried it over the sftp connection, the server I was remotely accessing obviously wasn't happy and denied it.
I am not too worried about security as it is in my house (this is not a commercial venture).

Is there something else I need to do on the server that will allow this?

Thanks Again.

---

### Post by nerdtron on 2013-09-01
When you use the file manager for sftp, it is only limited to the user that you logged-in. In your case it is only limited to the priledges of the user "ourproxy".

If you want to log in as root:
1. On the remote server. Set the root password
```
sudo passwd root
```
2. Then try this on your desktop.
```
sftp://root@192.168.1.6
```

That's it. Be careful as you are root in this mode.
You know, I was also doing this when I'm starting to learn Linux administrattion. You'll soon learn some of the disadvantages of this "file manger" method.
- permission can get messed up when you copy and paste from one folder to another.
- opening/editing files can be slow because the file manager has to download/upload the "file" everytime you make an edit.
- security. You're logged in as root!

Just be familiar with it but don't reply on it. Command line is still the best.

---

### Post by GMHilltop on 2013-09-03
I see what you are saying about the root permissions and who gets assigned what.

That's ok, as I have to simply get more comfortable with terminal commands.

The problem I am having is this, I have just reinstalled Ubuntu 12.04 LTS server, done the updates and upgrades. I have installed the openssh-server 

```

sudo apt-get install openssh-server

```

and it is working.  I can get in via terminal using 



for some reason I can login using
```
sudo ssh ourproxy@192.168.1.6
```


but not

```

sftp://ourproxy@192.168.1.6

```

using the location bar ====> I am getting access denied.

Any ideas?

---

### Post by GMHilltop on 2013-09-03
Ok, I don't know what happened, but now it is working for some reason.  For about 10 Minutes there it simply was not letting me in.  Weird.

Now, when accessing the server using the GUI and
```
sftp://ourproxy@192.168.1.6
```

why is it, when I look to see who an owner of a file is that it simply says '0' ?

---

### Post by SeijiSensei on 2013-09-03
User 0 is the root user.  If you list a directory with the -n switch, like "ls -n /", you'll see the numeric user and group IDs rather than the textual names assigned to those numeric IDs.

Now why SFTP gives you numeric IDs, I don't know.

---

### Post by GMHilltop on 2013-09-03
cool thanks

---

