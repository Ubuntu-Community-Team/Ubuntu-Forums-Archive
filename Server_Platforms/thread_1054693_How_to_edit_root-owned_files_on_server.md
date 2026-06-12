---
title: "How to edit root-owned files on server?"
date: 2009-01-29
forum: Server Platforms
---

### Post by MountainX on 2009-01-29
I'm running Ubuntu on my desktop and server. I need to edit some files owned by root with restrictive permissions. Currently I log onto the server using SSH in a terminal and edit the files using "sudo nano file". I would rather connect with Nautilus and edit the files with gedit. How can I do that? Thanks

---

### Post by Canuckelhead on 2009-01-29
In terminal:
gksudo nautilus

---

### Post by wilbbe01 on 2009-01-29
You could try adding a "Y" to your ssh connection.  You would do something like the following.  The Y is to forward X11 stuff.  I think you would need to install gedit on the server though, which would require you to install a bunch of graphical stuff, which would make things less secure.  If you are fine installing the graphical stuff anyway, go ahead and install it on the server and try the following.

```
ssh -Y [youruser@yourserver]
```

then open as you would if it were on your desktop.

```
sudo gedit nameOfFile
```

---

### Post by wilbbe01 on 2009-01-29
> In terminal:
gksudo nautilus

Yes, if you did the ssh using the graphical forwarding.

I just thought of another thing too.  You could use the connect to server option in the places menu to connect via ssh and edit the file using your desktop's gedit.  That might be an easier solution.

---

### Post by MountainX on 2009-01-29
> **wilbbe01 said:**
> Yes, if you did the ssh using the graphical forwarding.

I just thought of another thing too.  You could use the connect to server option in the places menu to connect via ssh and edit the file using your desktop's gedit.  That might be an easier solution.

gksudo nautilus doesn't seem to work. Maybe I don't understand...

On my local machine I open a terminal and type "gksudo nautilus".
That opens nautilus (but without my bookmarks and stuff).
I enter an address like this:
sftp://myuser@6xxx.xxx.xxx.xxx/etc/postfix

And rather than connect, it gives me an error: couldn't find /home/myuser/sftp://myuser@6xxx.xxx.xxx.xxx/etc/postfix.

And connect to server doesn't work when nautilus is started with gksudo.

What I would like to do is this: "use the connect to server option in the places menu to connect via ssh and edit the file using your desktop's gedit." How do I do that? It doesn't seem to work.

(And I don't want to install any GUI stuff on the server.)

---

### Post by Canuckelhead on 2009-01-30
I think you should ssh -X in first then run Gksudo nautilus.  That should give you what you want.  You will get nautilus forwarded to your ssh client...

I'd use SSH -X [youruser@yourserver] from the terminal. Then at the prompt use Gksudo nautilus

---

### Post by wilbbe01 on 2009-01-30
Yeah, I forgot Ubuntu doesn't like root accounts so that might cause a bit of a problem.  How about copy the file from the server using scp, edit it on your desktop, copy it back to the server using scp.  Although, you wouldn't be able to copy the file back to the location after editing it.  You would have to copy it somewhere else first, then ssh into the server and copy it using sudo to the final location.

---

### Post by wilbbe01 on 2009-01-30
> I think you should ssh -X in first then run Gksudo nautilus. That should give you what you want. You will get nautilus forwarded to your ssh client...

I'd use SSH -X [youruser@yourserver] from the terminal. Then at the prompt use Gksudo nautilus

They would need to install graphical stuff on the server.  Also, -Y works better than -X as -Y enables trusted X11 forwarding.  As I stated earlier though, they would need to install graphical stuff on the server, which they have stated they do not want to do.

---

### Post by Canuckelhead on 2009-01-30
right!  Missed that part

---

### Post by MountainX on 2009-01-30
> **Canuckelhead said:**
> I think you should ssh -X in first then run Gksudo nautilus.  That should give you what you want.  You will get nautilus forwarded to your ssh client...

I'd use SSH -X [youruser@yourserver] from the terminal. Then at the prompt use Gksudo nautilus

No luck with that either:

```
myuser@localbox:~$ ssh -X myuser@xxx.xxx.xxx.xxx
myuser@xxx.xxx.xxx.xxx's password: 
Linux ubuntu 2.6.18.8-linode10 #2 SMP Sat Jul 19 20:24:32 EDT 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
No mail.
Last login: Tue Jan 27 10:20:59 2009 from yyy.yyy.yyy.yyy.isp.net
myuser@Linode01:~$ gksudo nautilus
-bash: gksudo: command not found
myuser@Linode01:~$ 
```

---

### Post by MountainX on 2009-01-30
> **wilbbe01 said:**
> Yeah, I forgot Ubuntu doesn't like root accounts so that might cause a bit of a problem.  How about copy the file from the server using scp, edit it on your desktop, copy it back to the server using scp.  Although, you wouldn't be able to copy the file back to the location after editing it.  You would have to copy it somewhere else first, then ssh into the server and copy it using sudo to the final location.

Copying files back and forth is WAY too much trouble. I am editing files all the time. I just want to open in gedit, make a quick change, save and test. Can't I just edit on the server using gedit from my desktop? Don't forget the files are owned by root and have permissions such as 700 or 644 (not 777). Surely there is a simple way to edit files on the server (I hope). Wow, I had no idea this would be so hard.

---

### Post by Canuckelhead on 2009-01-30
Sorry for wasting your time.

I missed that you didn't want any GUI stuff on your server.

Without x windows and nautilus on the server it won't work.

---

### Post by Canuckelhead on 2009-01-30
I'll send a better way when I get home from work

---

### Post by wilbbe01 on 2009-01-30
Copy the file from the server.
first make sure you backup your file

On the desktop run
```
scp -p user@server:/path/to/file /path/on/local/machine
```

Also on the desktop run:
```
gedit /path/on/local/machine
```

Also on the desktop run:
```
scp -p /path/on/local/machine user@server:/a/path/which/is/writable/such/as/the/users/home/folder
```

ssh to the server and once logged in run
```
sudo cp -p /where/you/just/put/the/file /where/it/was/from/in/the/beginning
```

---

### Post by wilbbe01 on 2009-01-30
> Copying files back and forth is WAY too much trouble. I am editing files all the time. I just want to open in gedit, make a quick change, save and test. Can't I just edit on the server using gedit from my desktop? Don't forget the files are owned by root and have permissions such as 700 or 644 (not 777). Surely there is a simple way to edit files on the server (I hope). Wow, I had no idea this would be so hard.

Yeah, install gedit on the server and use the -Y option when you ssh.

---

### Post by Canuckelhead on 2009-01-30
you could look at mounting the location on the server using SSHFS....

I've never used it but I bet that would work nicely.

look here [HTML]http://ubuntuforums.org/showthread.php?t=1051650&highlight=nautilus+connect+to+server[/HTML]

---

### Post by wilbbe01 on 2009-01-30
> you could look at mounting the location on the server using SSHFS....

Yes they could, and in theory that would allow them to use the local sudo user to access what is actually a remote root owned document.

---

### Post by MountainX on 2009-01-30
> **Canuckelhead said:**
> you could look at mounting the location on the server using SSHFS....

I've never used it but I bet that would work nicely.

look here [HTML]http://ubuntuforums.org/showthread.php?t=1051650&highlight=nautilus+connect+to+server[/HTML]

I followed those exact steps. I got the server file system mounted and I connected to it. But when I try to open a file I get a permission denied error.

---

### Post by wilbbe01 on 2009-01-30
> I followed those exact steps. I got the server file system mounted and I connected to it. But when I try to open a file I get a permission denied error.

It still doesn't work when you use sudo right?

---

### Post by Canuckelhead on 2009-01-30
try it once through gksudo nautilus in terminal...

you'll want to give yourself some permissions on the files...

can you view the files?

---

### Post by MountainX on 2009-01-30
I have remote filesystem mounted using sshfs now. I can go to the location in Nautlus and I can open files in a local editor.

However, I get permission errors when I try to save (because files are owned by root an only owner can write).

When I use "gksudo gedit" and then try to open a file in the mounted sshfs, I get permission errors and I cannot even see any files in that location. I think this is due to root squash.

So I cannot save as a non-root user and I also cannot get access to the files as root. 

This sucks.

---

### Post by MountainX on 2009-01-30
> **wilbbe01 said:**
> Yes they could, and in theory that would allow them to use the local sudo user to access what is actually a remote root owned document.

I don't think this will work. I tried it. See my prior post.

---

### Post by Norsefire on 2009-02-05
I too am trying to find a way to do this.

On my desktop when I want to edit a root-owned file I usually open nautilus as root (gksudo nautilus) and then the file is opened as root and thus editable. Only there doesn't seem to be a way to replicate this behaviour over SFTP. At the moment I'm logging in as root over SFTP to do this, which is wholly unsatisfactory, as ideally root access would be disabled (if not completely) over SSH/SFTP.

Any help would be appreciated :D

---

### Post by MountainX on 2009-02-05
> **Norsefire said:**
> I too am trying to find a way to do this.



I'm still searching myself...

root login is in fact disabled on my server, so I can't even do it the less-than-ideal way.

---

### Post by Endwin on 2009-02-05
Looks like a special permissions setup is needed. I am assuming you want certain users who logins you specify can edit those files. What I would do is have those users be part of the same group. There is usually one already setup for root access on most linux boxes. Wheel and adm come to mind. From the looks of it Ubuntu uses adm. For the files you want to edit change the group ownership from root:root to root:adm. Add everyone who needs to edits. Set the permission to write to those files for the group, and you should be able to edit them. 

So for an example....


let us say I want to edit the motd file in etc remotely.

I am myself, endwin. 

I would add myself to the adm group...

```
usermod -a -G adm endwin
```

Then changer the ownership of the file(s) I want to edit.

```
chown root:adm motd
```

Finally change the permission of the file. 

```
chmod 664 motd
```

Now I have write access because I am part of the adm group to edit the motd. 

Give that a shot. You should be good.

---

