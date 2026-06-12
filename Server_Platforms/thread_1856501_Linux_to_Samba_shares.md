---
title: "Linux to Samba shares"
date: 2011-10-08
forum: Server Platforms
---

### Post by kamaji792 on 2011-10-08
Hi all,

I have a little box running as a 10.04 server with Samba on it to act as a server so I have access from Win and Ubuntu boxes.  For the Win boxes everything is fine.  Logging in easy and things generally run smoothly.

As you can guess my problem is with the Ubuntu box.  It is a pain to log in.  I make this harder because I want a system to allows several users to log in to the server (though only I use the Linux box, but you never know).  This is done with a hack that have to be re-implemented each time Samba is updated on the client box.  I also know that the hack will not work with later version of Ubuntu so it has about a 3 year life before I have to find another solution.

That aside I have a permissions issue where I can create files on the server from the Ubuntu box that can't be edited by anyone on the Win boxes.  If I use the same Samba account from a Win box then there is no problem.

So I am wondering could I just connect directly to the Server (I'm guessing NFS) and just manage the groups and permissions so that they merge with what the Samba system needs?

Anyone tried that?

k

---

### Post by capscrew on 2011-10-08
> **kamaji792 said:**
> Hi all,

I have a little box running as a 10.04 server with Samba on it to act as a server so I have access from Win and Ubuntu boxes.  For the Win boxes everything is fine.  Logging in easy and things generally run smoothly.

As you can guess my problem is with the Ubuntu box.  It is a pain to log in.  I make this harder because I want a system to allows several users to log in to the server (though only I use the Linux box, but you never know).  This is done with a hack that have to be re-implemented each time Samba is updated on the client box.  I also know that the hack will not work with later version of Ubuntu so it has about a 3 year life before I have to find another solution.
What's the hack you are referring to?> 

That aside I have a permissions issue where I can create files on the server from the Ubuntu box that can't be edited by anyone on the Win boxes.  If I use the same Samba account from a Win box then there is no problem.

You shouldn't be having these kinds of problems with Samba.  I have Samba working perfectly on both Ubuntu 10.04 Server and 10.04 Desktop along with Windows Vista hosted shares.  Everything can be seen and used from anywhere.

It's impossible to tell where the problems are without seeing your configuration and the underlying file system.  Care to share?> 

So I am wondering could I just connect directly to the Server (I'm guessing NFS) and just manage the groups and permissions so that they merge with what the Samba system needs?


Anyone tried that?

k
Both Samba and NFS mount the remote file system to the local host.  You can you them simultaneously.  As such, you need to manage file system permissions for effective use at all times.

---

### Post by CharlesA on 2011-10-08
I don't know of any "hack" to connect to a Samba share from a linux box.

I just use "connect to server" in Gnome2, or mount it manually via the terminal.

Check to make sure Samba is configured correctly by running this:

```
testparm
```

---

### Post by HermanAB on 2011-10-09
Maybe see this link and make a special group for all the samba users:
[http://www.aeronetworks.ca/howtos/samba-debug-howto.html](http://www.aeronetworks.ca/howtos/samba-debug-howto.html)

---

### Post by kamaji792 on 2011-10-10
Hi all,

Thanks for the replies I am working my way through them.

Just for the record my 'hack' is:

I want an normal user to be able to mount a Samba share. I'll create a script that mounts the users shares, asking for a password.

Now most of you know that a normal user can't use 'mount', even if you SUID it.  However if you SUID 'mount.cifs' a normal user can use that.  That is my 'hack'.  However for versions after 10.04 this does not work, so this hack has a limited life; probably is not a good idea (especially on a work server - I'm just running a home server) and finally each time Samba is updated the hack has to be re-applied (OK it's not a big deal but, being a bear of small brain, I have to remind myself what it is I need to do).

If I get some time today I will post my current setup and you can pick it apart if you want.

Thanks gavin k

PS - I had a look at NFS and have pretty much come to the conclusion that I don't want to go down that path.

---

### Post by kamaji792 on 2011-10-10
Ho hum...how embarrassing.

It appears my main gripe with Samba is not longer causing a problem.  Maybe is was a recent update that cured the problem.

The problem was when I created a document on a share it was not writeable by another user with access to the share because the group permissions were not set to write.  This was only an issue when creating the document from my Ubuntu box.

Good old Samba.

So that just leaves my logging in issues.

Thanks again for everyone who took the time to reply - k

---

