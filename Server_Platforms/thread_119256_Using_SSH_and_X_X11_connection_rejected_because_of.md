---
title: "Using SSH and X: X11 connection rejected because of wrong authentication."
date: 2006-01-19
forum: Server Platforms
---

### Post by joehill on 2006-01-19
Hi,

I've been using ssh to log in from my laptop (running Ubuntu Breezy) to my server (running Kubuntu Breezy) and run various programs remotely in X-windows, but suddenly I'm getting error messages when I try to do that.  If I run a GTK/gnome application it give me this error:

  X11 connection rejected because of wrong authentication.
  X connection to localhost:10.0 broken (explicit kill or server shutdown).

or this one:

  X11 connection rejected because of wrong authentication.
  The application 'gedit' lost its connection to the display localhost:10.0;
  most likely the X server was shut down or you killed/destroyed
  the application.

If I run KDE/Qt applications I get this error:

  X11 connection rejected because of wrong authentication.
  : Fatal IO error: client killed

A while back I tried rebooting the server and everything worked fine again for about a day, and then the problem came back.  I at first thought it was a problem with my home directory but it's the same whether I'm running as root or any other user.

I'd appreciate any help I can get on this.

Thanks, Joe

---

### Post by joehill on 2006-01-19
Well, I ended up rebooting again and it fixed the problem again for now.  After reading a post on another forum by someone who had the same problem because of low disk space, I checked my "/" partition, which was somewhat low on space (down to 330 MB--which I would think is plenty but these days things take a lot of space) and I moved some stuff to another partition and it's been working since then.  I'm crossing my fingers that this was the problem, but we'll see.

Joe

---

### Post by noob_Lance on 2006-01-20
how did you get the C to display? i still cant figure that out for the life of me..

---

### Post by joehill on 2006-01-24
What do you mean by "C"?

---

### Post by noob_Lance on 2006-01-25
sorry.... i ment to hit X

---

### Post by joehill on 2006-01-25
Do you mean how did I get the server to forward X information to the client?  If so, you do "ssh -X [email]me@myhost.mydomain.net[/email]."  That's the option that specifies to forward the X connection and not just the terminal text.  If that doesn't work you can use -Y instead of -X, which is for forwarding over a trusted connection (apparently less secure than -X, I'm not sure exactly what the implications of this are).  Does this answer your question?

---

### Post by kiwigander on 2006-01-25
As an alternative, you can edit the /etc/ssh/ssh_config file on the *client* so it contains the line 

Forward X11  yes

(I believe the stock Ubuntu Breezy installation starts off with that line as 

 # Forward X11 no

 so I assume that the default setting is "no".)

---

### Post by joehill on 2006-01-26
Ok, that's simpler.  Thanks for the pointer.

---

### Post by noob_Lance on 2006-01-27
it is set to yes and even when i tried the -X or -Y it still did not work for me..

---

### Post by MJN on 2006-01-27
It also needs enabling in your server...
 
**X11Forwarding YES**
 
..?

---

### Post by noob_Lance on 2006-01-27
yes it is enabled on my server..

---

### Post by hil on 2006-08-10
I got exactly the same problem here. I can't ssh to the ubuntu 6.06 server

my command: ```
ssh -l h -Y 192.168.12.5
```

X11 connection rejected because of wrong authentication.
The application 'gedit' lost its connection to the display localhost:10.0;
most likely the X server was shut down or you killed/destroyed
the application.

---

### Post by hil on 2006-08-10
I posted a solution to [another page]("http://ubuntuforums.org/showthread.php?p=1361790#post1361790")

Please take a look and see if that helps:confused:

---

### Post by mirak63 on 2006-08-16
I needed to put x11forward yes in /etc/ssh/ssh_config
This allow connecting clients to do ssh forwarding.
I though it would be in sshd_config but it was already on yes.

---

### Post by mohnkern on 2007-06-29
I saw this same problem, and have a different issue.  I thought I'd put it here for documentation.

Somehow my .Xauthority file on my computer on my home box got its ownership changed.

doing:

sudo rm $home/.Xauthority*

and then logging out and back in resolved the issue.

---

### Post by gulincho on 2007-07-03
For me, the problem was:

```
No space left on device (28)
```

I cleaned up /usr/cache/apt/archives.

---

### Post by bankg3 on 2007-08-06
I had a similar problem but my .Xauthority file wasn't the issue.  When I first would ssh into my box I would get this message

sh: /usr/bin/xauth: Permission denied

so I checked my xauth file and the permissions were wrong. 
-rwxr--r--  1 root   root     28K 2006-01-04 22:43 xauth

I changed the permissions "sudo chmod 755 /usr/bin/xauth" so I could execute the file and then everything worked ok.  The next time I logged in a new .Xauthority file was created and everything worked.

---

### Post by dgavenda on 2007-12-20
> **mohnkern said:**
> 
doing:

sudo rm $home/.Xauthority*

and then logging out and back in resolved the issue.


Worked for me too!!

---

### Post by alonsorm77 on 2007-12-27
Hello Guys!

I experimented the same problem, then i realized that i was working with big files, i erased some of them and the problem was corrected.

Is the HD space!

Thanks

---

### Post by jis on 2008-02-03
> **dgavenda said:**
> Worked for me too!!

It worked for me, too. I had three files: .Xauthority, .Xauthority-c and .Xauthority-l. I moved them to a subdirectory in case I need them later. When I logged back, a new .Xauthority file was created with different ownership.

---

### Post by MJN on 2008-02-04
This can often happen (i.e. .XAuthority ownership changes to root) if you start X using sudo.

Mathew

---

